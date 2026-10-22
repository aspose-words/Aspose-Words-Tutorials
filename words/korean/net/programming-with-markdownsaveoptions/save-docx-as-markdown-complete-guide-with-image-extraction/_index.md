---
category: general
date: 2026-05-29
description: Aspose.Words를 사용해 docx를 markdown으로 저장하고, 단일 워크플로우에서 docx에서 이미지를 추출하는
  방법을 배워보세요. 단계별 코드와 팁.
draft: false
keywords:
- save docx as markdown
- extract images from docx
- convert word to markdown
- convert docx to markdown
- how to extract images
language: ko
og_description: Aspose.Words를 사용하여 docx를 markdown으로 저장합니다. Word를 markdown으로 변환하면서
  docx에서 이미지를 추출하는 방법을 배우고, 전체 코드를 포함합니다.
og_title: docx를 markdown으로 저장하기 – 이미지 추출 포함 전체 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-05-29'
  description: Save docx as markdown using Aspose.Words and learn how to extract images
    from docx in a single workflow. Step‑by‑step code and tips.
  headline: Save docx as markdown – Complete Guide with Image Extraction
  type: TechArticle
- description: Save docx as markdown using Aspose.Words and learn how to extract images
    from docx in a single workflow. Step‑by‑step code and tips.
  name: Save docx as markdown – Complete Guide with Image Extraction
  steps:
  - name: – Load the source document
    text: First we need a `Document` object that points at the Word file we want to
      transform.
  - name: – Define a callback that extracts images from docx
    text: The magic lives in `IResourceSavingCallback`. Aspose.Words calls `ResourceSaving`
      for every external resource (images, fonts, etc.) it needs to write out. By
      providing our own implementation we gain total control over the file name, folder,
      and even the stream used.
  - name: – Wire the callback into Markdown save options
    text: Now we create a `MarkdownSaveOptions` instance and assign our custom saver.
  - name: – Save the document as markdown
    text: Finally, we ask Aspose.Words to write out the markdown file. The images
      are saved automatically by the callback we just hooked.
  type: HowTo
tags:
- Aspose.Words
- C#
- Document Conversion
title: docx를 markdown으로 저장하기 – 이미지 추출 포함 완전 가이드
url: /ko/net/programming-with-markdownsaveoptions/save-docx-as-markdown-complete-guide-with-image-extraction/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# docx를 markdown으로 저장 – 이미지 추출 포함 완전 가이드

Word 파일 안에 숨겨진 그림을 잃지 않고 **docx를 markdown으로 저장**하는 방법이 궁금하셨나요? 당신만 그런 것이 아닙니다. 많은 개발자들이 풍부한 텍스트 문서를 깔끔한 markdown으로 변환하려다 이미지 링크가 깨지는 문제에 부딪히곤 합니다.  

이 튜토리얼에서는 **docx를 markdown으로 변환**할 뿐만 아니라 **docx에서 이미지를 자동으로 추출**하는 실용적인 솔루션을 단계별로 살펴봅니다. 마지막까지 진행하면 바로 실행 가능한 C# 스니펫, 몇 가지 모범 사례 팁, 그리고 코드를 실행했을 때 기대할 수 있는 결과를 명확히 파악할 수 있습니다.

## 배울 내용

- Aspose.Words for .NET을 설정하여 Word‑to‑markdown 변환을 처리합니다.  
- 임베드된 각 그림을 원하는 폴더에 저장하는 커스텀 `IResourceSavingCallback`을 구현합니다.  
- 콜백이 왜 중요한지, 그리고 생성된 markdown에서 이미지 참조를 어떻게 유지하는지 이해합니다.  
- 전체 실행 가능한 예제와 얻을 수 있는 정확한 markdown 출력물을 확인합니다.  

**Prerequisites** – .NET 6(또는 최신 .NET 버전), Visual Studio 2022(또는 VS Code), 그리고 활성화된 Aspose.Words for .NET 라이선스(무료 체험판으로 테스트 가능)가 필요합니다. 다른 서드‑파티 라이브러리는 필요하지 않습니다.

---

## How to save docx as markdown using Aspose.Words

아래는 우리가 따를 고수준 흐름입니다:

1. 이미지를 포함하고 있는 원본 `.docx`를 로드합니다.  
2. 추출된 각 이미지를 어디에 기록할지 결정하는 콜백 클래스를 정의합니다.  
3. 콜백을 `MarkdownSaveOptions`에 연결합니다.  
4. 문서를 저장합니다 – markdown은 디스크에 기록되고, 이미지는 지정한 폴더에 저장됩니다.

각 단계는 자세히 설명되며, 설명 바로 뒤에 코드가 표시됩니다.

### Step 1 – Load the source document

먼저 변환하려는 Word 파일을 가리키는 `Document` 객체가 필요합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Load the source .docx that contains images.
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **왜 중요한가:** Aspose.Words는 DOCX 패키지를 파싱하고 내부 객체 모델을 구축하여 모든 단락, 표, 이미지를 접근 가능하게 합니다. 파일을 로드하지 못하면 파이프라인의 나머지 단계가 실행되지 않습니다.

### Step 2 – Define a callback that extracts images from docx

마법은 `IResourceSavingCallback`에 있습니다. Aspose.Words는 외부 리소스(이미지, 폰트 등)를 기록할 때마다 `ResourceSaving`을 호출합니다. 자체 구현을 제공하면 파일 이름, 폴더, 심지어 스트림까지 완전히 제어할 수 있습니다.

```csharp
// Step 2: Define a callback that stores each extracted image in a sub‑folder
// and gives it a unique name.
class MyResourceSaver : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Create (or reuse) a folder for the images.
        string folder = "YOUR_DIRECTORY/markdown_images";
        Directory.CreateDirectory(folder);

        // Build a new file name like "img_0.png", "img_1.jpg", etc.
        string newName = Path.Combine(folder,
            $"img_{args.Index}{Path.GetExtension(args.ResourceFileName)}");

        // Tell Aspose.Words where to write the image.
        args.ResourceFileName = newName;
        args.Stream = new FileStream(newName, FileMode.Create, FileAccess.Write);

        // Allow the default saving process to continue.
        args.Cancel = false;
    }
}
```

> **팁:** `args.Index`는 0부터 시작하며 두 이미지가 동일한 원본 파일 이름을 공유하더라도 고유성을 보장합니다. 이를 통해 변환을 여러 번 실행할 때 발생할 수 있는 “중복 파일 이름” 오류를 방지할 수 있습니다.

### Step 3 – Wire the callback into Markdown save options

이제 `MarkdownSaveOptions` 인스턴스를 만들고 커스텀 saver를 할당합니다.

```csharp
// Step 3: Configure Markdown save options to use the custom resource saver.
MarkdownSaveOptions opts = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceSaver()
};
```

> **왜 이것이 필수적인가:** 콜백이 없으면 Aspose.Words는 기본 설정에 따라 이미지를 markdown 내부에 base‑64 문자열로 삽입하거나 아예 삭제합니다. 우리의 콜백은 파일 기반의 깔끔한 참조를 강제하여 모든 정적 사이트 생성기와 호환됩니다.

### Step 4 – Save the document as markdown

마지막으로 Aspose.Words에 markdown 파일을 기록하도록 요청합니다. 이미지는 방금 연결한 콜백에 의해 자동으로 저장됩니다.

```csharp
// Step 4: Save the document as Markdown; images will be written to the folder above.
doc.Save("YOUR_DIRECTORY/output.md", opts);
```

코드 실행이 끝나면 다음을 확인할 수 있습니다:

- `output.md` – 원본 Word 파일의 markdown 표현입니다.  
- `markdown_images/` – `img_0.png`, `img_1.jpg`, … 와 같이 DOCX에 포함된 모든 그림을 담은 폴더입니다.

#### Expected markdown snippet

```markdown
# Sample Title

Here is some introductory text.

![Image 1](markdown_images/img_0.png)

More text after the picture.
```

이미지 링크는 2단계에서 저장한 파일을 가리키므로, 어떤 markdown 뷰어에서도 그림이 올바르게 렌더링됩니다.

---

## Extract images from docx while converting to markdown

이미지 **추출 방법**만이 목표라면 markdown을 저장하지 않아도 동일한 콜백을 재사용할 수 있습니다. `doc.Save("dummy.md", opts)`를 호출하거나 `doc.GetChildNodes(NodeType.Shape, true)`를 사용해 이미지를 열거하면 됩니다. 콜백은 각 이미지마다 실행되어 원하는 위치에 저장할 수 있게 해줍니다.

```csharp
// Example: extract images only – we still need a save call to trigger the callback.
doc.Save("YOUR_DIRECTORY/placeholder.md", opts);
```

> **Note:** 추출이 끝난 후에는 자리표시자 markdown 파일을 삭제해도 됩니다; 콜백이 이미 이미지를 디스크에 기록했기 때문입니다.

---

## Convert Word to markdown with custom image handling

**convert word to markdown**라는 구문은 “포맷 유지”와 함께 자주 검색됩니다. Aspose.Words는 제목, 리스트, 표, 코드 블록 등을 훌륭히 보존합니다. 유일하게 주의해야 할 점은 이미지 스케일링입니다. 기본적으로 생성된 markdown은 원본 이미지 크기를 사용합니다. 썸네일이 필요하면 콜백을 수정해 이미지를 저장하기 전에 크기를 조정하면 됩니다(예: `System.Drawing` 또는 `ImageSharp` 사용).

```csharp
// Inside ResourceSaving, you could resize before saving:
using (var original = Image.Load(args.Stream))
{
    var thumbnail = original.Clone(ctx => ctx.Resize(new ResizeOptions
    {
        Size = new Size(300, 0),
        Mode = ResizeMode.Max
    }));
    thumbnail.Save(newName);
}
```

*(위 스니펫은 ImageSharp을 사용합니다 – 해당 경로를 선택한다면 NuGet 패키지를 추가해야 합니다.)*

---

## Common pitfalls when you convert docx to markdown

| 문제점 | 발생 원인 | 해결 방법 |
|---------|----------------|-----------------|
| 이미지가 **base64** 문자열로 변환됨 | 기본 `ResourceSavingCallback`이 설정되지 않음 | 항상 커스텀 `IResourceSavingCallback`을 제공 |
| markdown 파일을 이동한 뒤 링크가 깨짐 | 상대 경로가 존재하지 않는 폴더를 가리킴 | `markdown_images` 폴더를 `.md` 파일 옆에 두거나 `MarkdownSaveOptions.ImageFolder` 경로를 조정 |
| 이미지 이름 중복 | 두 그림이 동일한 원본 이름을 가짐 | `args.Index`(예시와 같이) 또는 GUID를 파일 이름에 사용 |
| 대용량 문서에서 메모리 초과 | 스트리밍 없이 큰 이미지를 저장 | `args.Stream = new FileStream(..., FileMode.Create, FileAccess.Write, FileShare.None, 4096, FileOptions.SequentialScan)`을 사용해 효율적으로 스트리밍 |

---

## How to extract images – advanced scenarios

때때로 markdown 없이 이미지만 필요할 수 있습니다(예: 머신러닝 모델에 입력). 이 경우 다음과 같이 할 수 있습니다:

1. `opts.SaveFormat = SaveFormat.Png`(또는 원하는 이미지 포맷)으로 설정해 이미지 전용 내보내기를 강제합니다.  
2. 혹은 동일한 `MyResourceSaver`를 재사용하되 `doc.Save("dummy.docx", SaveFormat.Docx)`를 호출해 콜백만 트리거합니다.

두 접근법 모두 동일한 로직을 재사용하게 해 주며, 코드를 DRY(Don’t Repeat Yourself)하게 유지합니다.

---

## Full, runnable example

아래는 콘솔 앱에 복사‑붙여넣기 할 수 있는 전체 프로그램입니다. `YOUR_DIRECTORY`를 머신에 존재하는 절대 경로나 상대 경로로 교체하세요.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

namespace DocxToMarkdownDemo
{
    // Step 2 – custom callback that saves each image.
    class MyResourceSaver : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            string folder = "YOUR_DIRECTORY/markdown_images";
            Directory.CreateDirectory(folder);

            string newName = Path.Combine(folder,
                $"img_{args.Index}{Path.GetExtension(args.ResourceFileName)}");

            args.ResourceFileName = newName;
            args.Stream = new FileStream(newName, FileMode.Create, FileAccess.Write);
            args.Cancel = false;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Step 1 – load the .docx.
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Step 3 – set up save options with our callback.
            MarkdownSaveOptions opts = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new MyResourceSaver()
            };

            // Step 4 – save as markdown; images will be extracted automatically.
            doc.Save("YOUR_DIRECTORY/output.md", opts);

            System.Console.WriteLine("Conversion complete! Check output.md and the markdown_images folder.");
        }
    }
}
```

**실행 후 기대되는 결과:**  

- `output.md`에 `![Image](markdown_images/img_0.png)`와 같은 이미지 링크가 포함된 markdown 텍스트가 들어 있습니다.  
- `markdown_images` 폴더에 임베드된 각 그림마다 하나씩 파일이 생성됩니다.

---

## Conclusion

이제 **docx를 markdown으로 저장**하면서 **docx에서 이미지를 깔끔히 추출**하는 견고한 엔드‑투‑엔드 레시피를 갖추었습니다. 핵심은 각 그림이 어디에, 어떻게 저장될지를 완전히 제어할 수 있게 해 주는 `IResourceSavingCallback`입니다.  

여기서 할 수 있는 일:

- 콜백을 조정해 파일명을 의미 있는 제목(예: alt‑text 기반)으로 바꾸기.  
- 정적 사이트 생성기와 함께 markdown을 HTML로 변환하는 후처리 추가하기(예: static...

## What Should You Learn Next?

- [DOCX 변환 시 Markdown에 이미지 삽입하는 방법](/words/english/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/)
- [Word 이미지 저장 – Aspose로 Word를 Markdown으로 변환](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)
- [DOCX를 Markdown으로 변환할 때 이미지 이름 바꾸는 방법](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}