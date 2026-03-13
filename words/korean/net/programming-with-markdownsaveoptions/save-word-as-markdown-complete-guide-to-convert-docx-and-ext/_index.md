---
category: general
date: 2026-03-13
description: Word를 Markdown으로 저장하고 이미지를 추출하면서 DOCX를 Markdown으로 변환합니다. C#에서 Aspose.Words를
  사용하여 DOCX에서 이미지를 추출하는 방법을 배워보세요.
draft: false
keywords:
- save word as markdown
- convert docx to markdown
- extract images from docx
- how to extract images
- extract embedded images word
language: ko
og_description: C#에서 Word를 Markdown으로 저장하기. 이 가이드는 DOCX를 Markdown으로 변환하고 이미지를 추출하는
  방법을 보여주며, 바로 실행할 수 있는 솔루션을 제공합니다.
og_title: 워드를 마크다운으로 저장 – DOCX 변환 및 이미지 추출
tags:
- Aspose.Words
- C#
- Markdown
title: Word를 마크다운으로 저장 – DOCX 변환 및 이미지 추출 완전 가이드
url: /ko/net/programming-with-markdownsaveoptions/save-word-as-markdown-complete-guide-to-convert-docx-and-ext/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word를 Markdown으로 저장 – DOCX 변환 및 이미지 추출 완전 가이드

Word를 **markdown으로 저장**해야 할 때, 그림을 그대로 유지하는 방법을 몰라 고민한 적 있나요? 혼자가 아닙니다. 많은 개발자들이 DOCX 파일에 포함된 그래픽을 처리할 때, 간단한 변환기가 깨진 링크들을 많이 만들어 내는 상황에 부딪히곤 합니다.  

이 튜토리얼에서는 **DOCX를 markdown으로 변환** **하고** 모든 이미지를 직접 제어할 수 있는 폴더로 추출하는 실용적인 솔루션을 단계별로 살펴봅니다. 최종적으로 깔끔한 `.md` 파일, 정돈된 `markdown_resources` 디렉터리, 그리고 콜백 방식을 사용해야 가장 안정적으로 리소스를 처리할 수 있는 이유를 확실히 이해하게 될 것입니다.

> **Pro tip:** 동일한 패턴은 CSS, 폰트 또는 Aspose.Words가 저장 작업 중에 내보낼 수 있는 모든 외부 리소스에도 적용됩니다.

![Word를 Markdown으로 저장 변환 흐름도](conversion-diagram.png "변환 흐름도")

## 배울 내용

- Aspose.Words for .NET을 사용하여 **Word를 markdown으로 저장**하는 방법
- 이미지를 보존하면서 **docx를 markdown으로 변환**하는 정확한 단계
- 이미지 추출을 담당하는 재사용 가능한 `IResourceSavingCallback` 구현
- 흔히 발생하는 함정(예: 중복 파일명, 폴더 누락)과 이를 피하는 방법
- 생성된 markdown이 어떻게 보이며 이미지가 어디에 저장되는지

최근 버전의 **Aspose.Words for .NET**(가이드에서는 24.12 버전 기준)과 .NET 6+ 런타임이 필요합니다. 다른 서드파티 라이브러리는 필요하지 않습니다.

---

## 사전 요구 사항

| Requirement | Why it matters |
|-------------|----------------|
| Aspose.Words for .NET (NuGet `Aspose.Words`) | `Document` 클래스와 `MarkdownSaveOptions`를 제공합니다. |
| .NET 6 or later | `using` 문과 같은 최신 언어 기능을 추가적인 설정 없이 사용할 수 있습니다. |
| 이미지가 포함된 DOCX 파일(예: `Images.docx`) | 변환하고 이미지 추출을 수행할 원본 파일입니다. |
| 출력 폴더에 대한 쓰기 권한 | 콜백이 이미지 파일을 기록하므로 권한이 없으면 예외가 발생합니다. |

이미 모두 준비되었다면, 좋습니다—바로 시작해 봅시다.

---

## Step 1: Load the Source DOCX – The Starting Point for Save Word as Markdown

먼저 Word 문서를 엽니다. Aspose.Words는 파일을 메모리로 읽어 들이며, 모든 내부 구조(단락, 표, 이미지 등)를 그대로 보존합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Load the DOCX that contains images.
Document sourceDoc = new Document("YOUR_DIRECTORY/Images.docx");
```

> **Why this matters:** 파일을 일찍 로드하면 `sourceDoc.GetChildNodes(NodeType.Shape, true)`와 같이 내용물을 검사할 수 있어, 이미지가 누락되는 경우 디버깅에 도움이 됩니다.

---

## Step 2: Configure Markdown Save Options with an Image‑Saving Callback

Aspose.Words가 markdown 파일을 쓸 때 이미지와 같은 외부 리소스를 저장해야 할 수 있습니다. `ResourceSavingCallback`을 연결하면 파일이 저장되는 위치와 이름을 완전히 제어할 수 있습니다.

```csharp
// Prepare markdown options and tell Aspose.Words to use our callback.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // The callback fires for every image, CSS file, etc.
    ResourceSavingCallback = new ImageSavingCallback()
};
```

> **How to extract images:** 콜백은 이미지 스트림, 원본 파일명, 인덱스를 포함하는 `ResourceSavingArgs` 인스턴스를 전달받습니다. 이를 통해 파일명을 바꾸거나, 이동하거나, 저장 자체를 건너뛸 수도 있습니다.

---

## Step 3: Save the Document as Markdown – The Core of Save Word as Markdown

이제 `Document.Save`를 호출합니다. 라이브러리는 각 이미지마다 콜백을 호출하고, 지정한 위치에 이미지 파일을 기록한 뒤, 올바른 `![]()` 링크가 포함된 markdown 파일을 출력합니다.

```csharp
// Execute the conversion. The markdown file will reference the extracted images.
sourceDoc.Save("YOUR_DIRECTORY/DocWithImages.md", mdOptions);
```

이 시점에서 `YOUR_DIRECTORY` 안에 다음 두 항목이 보일 것입니다:

1. `DocWithImages.md` – 원본 Word 파일을 markdown 형태로 변환한 결과.
2. `markdown_resources` 폴더 – `img_0.png`, `img_1.jpg` 등으로 구성된 이미지 컬렉션.

---

## Step 4: Implement the Image‑Saving Callback – How to Extract Images from DOCX

아래는 전체 콜백 클래스 구현입니다. 필요 시 폴더를 생성하고, 고유 파일명을 만들며, 이미지 스트림을 기록한 뒤 `args.FileName`을 설정해 Aspose.Words가 해당 파일명을 사용하도록 하고, 기본 저장을 건너뛰기 위해 `args.Stream = null`을 지정합니다.

```csharp
public class ImageSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Ensure the resources folder exists.
        string resourcesFolder = "YOUR_DIRECTORY/markdown_resources";
        Directory.CreateDirectory(resourcesFolder);

        // 2️⃣ Build a unique name – img_0.png, img_1.jpg, etc.
        string imageFileName = Path.Combine(
            resourcesFolder,
            $"img_{args.ImageIndex}{Path.GetExtension(args.FileName)}");

        // 3️⃣ Write the image stream to disk.
        using (FileStream fileStream = new FileStream(imageFileName, FileMode.Create))
        {
            args.Stream.CopyTo(fileStream);
        }

        // 4️⃣ Tell the markdown writer to reference the new name.
        args.FileName = Path.GetFileName(imageFileName);
        args.Stream = null; // Prevent default saving – we already handled it.
    }
}
```

### 왜 이렇게 작동하나요

- **Deterministic filenames** – `args.ImageIndex`를 사용하면 원본 DOCX에 중복 파일명이 있더라도 고유성을 보장합니다.
- **Folder isolation** – 모든 추출된 자산이 `markdown_resources` 아래에 모여 프로젝트가 깔끔하게 유지됩니다.
- **Performance** – 스트림을 직접 복사하므로 추가 버퍼링이나 이미지 처리가 없으며, 변환 속도가 빠릅니다.

---

## Step 5: Verify the Output – What the Markdown Looks Like

`DocWithImages.md`를 원하는 편집기에서 열어보세요. 다음과 같은 내용이 표시될 것입니다:

```markdown
# Sample Document

Here is an illustration:

![](markdown_resources/img_0.png)

Another picture appears below:

![](markdown_resources/img_1.jpg)
```

상대 경로를 인식하는 뷰어(VS Code 미리보기, GitHub 등)에서 파일을 열면 이미지가 정상적으로 렌더링됩니다.

### 빠른 검증

```bash
# On Linux/macOS
cat YOUR_DIRECTORY/DocWithImages.md | grep -E '\!\[.*\]\(markdown_resources/img_.*\)'
```

이미지당 한 줄씩 표시되어야 하며, 라인 수는 원본 `Images.docx`에 포함된 그림 수와 일치해야 합니다.

---

## Common Questions & Edge Cases

### DOCX에 SVG 또는 EMF 그래픽이 포함되어 있으면 어떻게 되나요?

Aspose.Words는 대부분의 벡터 포맷을 자동으로 PNG로 변환합니다. 콜백은 여전히 스트림을 받으며 파일 확장자는 `.png`가 됩니다. 별도의 코드는 필요하지 않습니다.

### 출력 폴더 이름을 바꾸려면 어떻게 해야 하나요?

`ImageSavingCallback` 내부의 `resourcesFolder` 변수를 원하는 이름으로 수정하면 됩니다. markdown 링크가 올바르게 유지되도록 `args.FileName = Path.GetFileName(imageFileName)` 부분도 동일하게 유지하세요.

### 특정 이미지(예: 매우 큰 파일)를 저장하지 않으려면 어떻게 하나요?

콜백 안에서 `args.Stream.Length`를 검사하면 됩니다. 임계값을 초과하면 파일명을 플레이스홀더로 바꾸거나 `args.Cancel = true`를 설정해 완전히 제외할 수 있습니다.

```csharp
if (args.Stream.Length > 5 * 1024 * 1024) // >5 MB
{
    args.Cancel = true; // Image will be omitted from markdown.
    return;
}
```

### CSS와 같은 다른 리소스 타입에도 이 방법이 적용되나요?

물론입니다. 콜백은 모든 외부 리소스에 대해 호출됩니다. `args.ContentType`을 기준으로 CSS, 폰트, 비디오 등을 별도로 처리하도록 분기하면 됩니다.

---

## Full Working Example – Copy‑Paste Ready

아래는 콘솔 앱에 바로 붙여넣을 수 있는 완전한 예제 프로그램입니다. `YOUR_DIRECTORY` 자리에는 본인 환경에 맞는 절대 경로나 상대 경로를 입력하세요.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

namespace DocxToMarkdownDemo
{
    class Program
    {
        static void Main()
        {
            // ① Load the source DOCX that contains images.
            Document sourceDoc = new Document("YOUR_DIRECTORY/Images.docx");

            // ② Configure markdown options with our callback.
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new ImageSavingCallback()
            };

            // ③ Save as markdown – images will be stored by the callback.
            sourceDoc.Save("YOUR_DIRECTORY/DocWithImages.md", mdOptions);

            // ④ Inform the user.
            System.Console.WriteLine("Conversion complete! Check the markdown file and the markdown_resources folder.");
        }
    }

    // ⑤ Callback that extracts each image to a custom folder.
    public class ImageSavingCallback : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            string resourcesFolder = "YOUR_DIRECTORY/markdown_resources";
            Directory.CreateDirectory(resourcesFolder);

            string imageFileName = Path.Combine(
                resourcesFolder,
                $"img_{args.ImageIndex}{Path.GetExtension(args.FileName)}");

            using (FileStream fileStream = new FileStream(imageFileName, FileMode.Create))
            {
                args.Stream.CopyTo(fileStream);
            }

            args.FileName = Path.GetFileName(imageFileName);
            args.Stream = null; // Skip default saving.
        }
    }
}
```

프로그램을 실행하고 생성된 markdown을 열면 원본 Word 파일에 있던 모든 그림이 정확히 동일한 위치에 표시되는 것을 확인할 수 있습니다.

---

## Conclusion

우리는 **Word를 markdown으로 저장**하면서 **docx에서 이미지를 추출**하는 방법을 깔끔한 콜백 패턴을 통해 살펴보았습니다. 핵심 포인트는 `IResourceSavingCallback`을 사용하면 모든 외부 파일을 완전히 제어할 수 있어, 어떤 프로덕션 파이프라인에서도 변환을 신뢰할 수 있다는 점입니다.

단일 복사‑붙여넣기 예제에서 우리는:

1. 그림이 포함된 DOCX를 로드했습니다.
2. 커스텀 `ImageSavingCallback`을 설정한 `MarkdownSaveOptions`를 구성했습니다.
3. 콜백이 각 이미지를 `markdown_resources`에 기록하도록 하면서 문서를 markdown으로 저장했습니다.
4. 출력 결과를 검증하고, 다양한 상황에 맞게 프로세스를 조정하는 방법을 논의했습니다.

다음 단계로는:

- 디렉터리를 순회하며 **docx를 markdown으로 일괄 변환**하기
- 원본 캡션을 기반으로 이미지명을 바꿔 **SEO 최적화**하기
- **Hugo, Jekyll** 등 정적 사이트 생성기에 markdown 폴더를 옮겨 **통합**하기
- 필요에 따라 콜백을 확장해 임베디드 폰트나 CSS까지 추출하기

실험해 보세요—예를 들어 이미지 명명 방식을 GUID로 바꾸어 절대적인 고유성을 확보하거나, 저장된 각 리소스를 로깅하는 라인을 추가하는 등 자유롭게 확장할 수 있습니다. 마크다운이 언제나 올바른 그림과 함께 렌더링되길 바랍니다!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}