---
category: general
date: 2026-01-05
description: 마크다운을 저장하고 Word에서 이미지를 추출하면서 docx를 마크다운으로 변환하는 방법을 배웁니다. 리소스 폴더 생성 단계별
  포함.
draft: false
keywords:
- how to save markdown
- convert docx to markdown
- extract images from word
- how to extract images
- create resources folder
language: ko
og_description: Aspose.Words를 사용하여 C#에서 DOCX 파일의 마크다운을 저장하고, 이미지를 추출하며, 리소스 폴더를 만드는
  방법.
og_title: Word에서 마크다운을 저장하는 방법 – 전체 튜토리얼
tags:
- Aspose.Words
- C#
- Markdown
title: Word에서 마크다운을 저장하는 방법 – 완전 가이드
url: /ko/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-word-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word에서 Markdown 저장하기 – 완전 가이드

Word 문서에서 **Markdown을 직접 저장**하면서 삽입된 그림을 잃지 않으려면 어떻게 해야 할지 궁금하셨나요? 여러분만 그런 것이 아닙니다. 많은 프로젝트에서 **docx를 markdown으로 변환**하고, 이미지를 추출한 뒤 전용 폴더에 깔끔하게 정리해야 합니다. 이 튜토리얼에서는 Aspose.Words for .NET을 사용한 깨끗하고 재현 가능한 솔루션을 단계별로 안내합니다.

우리는 `.docx` 로드, 이미지 추출, **resources 폴더** 생성, 그리고 최종적으로 markdown 파일 쓰기까지 필요한 모든 과정을 다룰 것입니다. 끝까지 따라오시면 C# 콘솔이나 웹 앱에 바로 넣어 사용할 수 있는 코드 스니펫을 얻게 됩니다.

## 필수 조건

시작하기 전에 다음이 준비되어 있는지 확인하세요:

* .NET 6.0 이상 (코드는 .NET Framework 4.6+에서도 동작합니다).  
* **Aspose.Words for .NET** 라이선스 사본 – 무료 체험판으로도 테스트 가능.  
* 하나 이상의 이미지가 포함된 Word 파일 (`input.docx`).  
* C#와 Visual Studio(또는 선호하는 IDE)에 대한 기본 지식.

Aspose.Words 외에 추가 NuGet 패키지는 필요하지 않습니다.

## 1단계 – 원본 문서 불러오기

먼저 Word 파일을 `Aspose.Words.Document` 객체로 읽어와야 합니다. 이 객체를 통해 문서 내용 전체에 접근할 수 있으며, 이후에 추출할 이미지도 포함됩니다.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Adjust the path to point at your .docx file
string sourcePath = Path.Combine("YOUR_DIRECTORY", "input.docx");

// Create the Document instance – this is where the magic starts
Document document = new Document(sourcePath);
```

> **Why this matters:** 파일을 `Document` 로 로드하면 복잡한 OOXML 구조를 추상화해 이미지, 표, 단락 등 고수준 객체를 손쉽게 다룰 수 있습니다.

## 2단계 – 리소스 절약 콜백 구현

Aspose.Words는 `IResourceSavingCallback`을 통해 저장 프로세스에 훅을 걸 수 있습니다. 이를 이용해 추출된 각 이미지가 저장될 위치를 제어합니다. 콜백은 원본 문서 이름을 딴 **resources 폴더**를 만들고 그 안에 이미지 파일을 씁니다.

```csharp
// Step 2: Define a callback that decides where each resource (image) is stored
class ResourceSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build a folder path like: YOUR_DIRECTORY/Resources/input.docx
        string resourcesFolder = Path.Combine("YOUR_DIRECTORY", "Resources", args.DocumentName);
        Directory.CreateDirectory(resourcesFolder); // Guarantees the folder exists

        // Combine folder path with the original file name (e.g., image001.png)
        string resourcePath = Path.Combine(resourcesFolder, args.ResourceFileName);

        // Override the default name and supply a stream that writes the file
        args.ResourceFileName = resourcePath;
        args.Stream = new FileStream(resourcePath, FileMode.Create);
    }
}
```

> **Pro tip:** 모든 이미지를 하나의 폴더에 넣고 싶다면 `Path.Combine(..., args.DocumentName)` 를 고정된 폴더 이름으로 바꾸면 됩니다.

## 3단계 – 마크다운 저장 옵션 구성

이제 Aspose.Words에 Markdown을 출력 형식으로 지정하고 콜백을 연결합니다. 이 단계에서 **docx를 markdown으로 변환** 작업이 실제로 수행됩니다.

```csharp
// Step 3: Prepare the MarkdownSaveOptions and attach the callback
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // This tells Aspose.Words to invoke our callback for every resource
    ResourceSavingCallback = new ResourceSavingCallback()
};
```

> **What’s happening under the hood?** 라이브러리는 문서를 순회하면서 단락, 표, 기타 요소를 Markdown 구문으로 변환하고, 이미지 저장은 우리가 제공한 콜백에 위임합니다.

## 4단계 – 문서를 마크다운으로 저장

마지막으로 markdown 파일을 디스크에 씁니다. 이미지 파일은 앞 단계에서 만든 폴더에 이미 저장되어 있습니다.

```csharp
// Step 4: Save the markdown file alongside the resources folder
string markdownPath = Path.Combine("YOUR_DIRECTORY", "WithImages.md");
document.Save(markdownPath, markdownOptions);

Console.WriteLine($"✅ Markdown saved to: {markdownPath}");
Console.WriteLine("🖼️ Images extracted to the Resources folder.");
```

### 예상 결과

* `WithImages.md` – 모든 이미지 참조가 `![Image](Resources/input.docx/image001.png)` 형태인 깔끔한 markdown 파일.  
* `Resources/input.docx/` – 추출된 모든 이미지(PNG, JPEG 등)가 들어 있는 하위 폴더.

markdown 파일을 VS Code, GitHub, MkDocs 등 어떤 뷰어에서 열어도 원본 Word 파일과 동일한 위치에 그림이 표시됩니다.

## 마크다운으로 변환하지 않고 이미지 추출하는 방법 (보너스)

때때로 markdown이 필요 없고 이미지만 추출하고 싶을 때가 있습니다. 같은 콜백 로직을 재사용하되 `document.Save` 를 `SaveFormat.Html` 같은 다른 형식으로 호출하면 됩니다. 이미지 파일은 동일한 폴더에 저장되고, HTML 파일은 필요에 따라 삭제하면 됩니다.

```csharp
HtmlSaveOptions htmlOptions = new HtmlSaveOptions
{
    ResourceSavingCallback = new ResourceSavingCallback()
};

document.Save(Path.Combine("YOUR_DIRECTORY", "temp.html"), htmlOptions);
```

> **Why this works:** HTML 저장 역시 리소스 콜백을 트리거하므로 별도 코딩 없이 “이미지 추출” 기능을 바로 얻을 수 있습니다.

## 일반적인 문제점 및 해결 방법

| 문제 | 발생 원인 | 해결 방법 |
|-------|----------------|-----|
| 이미지 파일 이름이 중복됨 | Word 파일 내에서 여러 이미지가 동일한 원본 파일 이름을 공유함 | 콜백 함수에 GUID 또는 증가하는 카운터를 추가하세요(`args.ResourceFileName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";`). |
| 마크다운 링크가 존재하지 않는 폴더를 가리킴 | `Resources` 폴더 경로가 마크다운 파일에 대해 잘못됨 | 상대 경로를 계산하려면 `Path.GetRelativePath`를 사용하거나, 위에서처럼 마크다운 파일 옆에 폴더를 두세요. |
| Aspose.Words에서 `FileNotFoundException` 예외가 발생합니다. | 소스 `.docx` 경로가 올바르지 않습니다. | `Document`를 생성하기 전에 `Path.GetFullPath`를 사용하여 절대 경로를 확인하세요. |
| 대용량 문서로 인해 메모리 부족 오류가 발생합니다. | 라이브러리가 전체 문서를 메모리에 로드합니다. | `ReadOnly` 모드의 `FileStream`을 매개변수로 받는 `Document.Load` 오버로드를 사용하여 문서를 스트리밍하세요. |

## 전체 작동 예제 (복사-붙여넣기)

아래는 **전체** 프로그램 코드이며, 그대로 복사해 컴파일하고 실행할 수 있습니다. `YOUR_DIRECTORY` 를 실제 존재하는 폴더 경로로 바꾸세요.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

namespace DocxToMarkdown
{
    // Callback that saves each image to a resources folder
    class ResourceSavingCallback : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            string resourcesFolder = Path.Combine("YOUR_DIRECTORY", "Resources", args.DocumentName);
            Directory.CreateDirectory(resourcesFolder);

            string resourcePath = Path.Combine(resourcesFolder, args.ResourceFileName);
            args.ResourceFileName = resourcePath;
            args.Stream = new FileStream(resourcePath, FileMode.Create);
        }
    }

    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the DOCX
            string docPath = Path.Combine("YOUR_DIRECTORY", "input.docx");
            Document document = new Document(docPath);

            // 2️⃣ Set up Markdown options with our callback
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new ResourceSavingCallback()
            };

            // 3️⃣ Save as Markdown – images are extracted automatically
            string mdPath = Path.Combine("YOUR_DIRECTORY", "WithImages.md");
            document.Save(mdPath, mdOptions);

            Console.WriteLine($"✅ Markdown saved to: {mdPath}");
            Console.WriteLine("🖼️ Images extracted to the Resources folder.");
        }
    }
}
```

프로그램을 실행(`dotnet run` 또는 Visual Studio에서 **F5**)하면 콘솔에 성공 메시지가 표시됩니다.

## 출력 테스트

`WithImages.md` 를 markdown 미리보기에서 열어보세요:

```markdown
# Sample Heading

Here is an image extracted from the original Word file:

![Image](Resources/input.docx/image001.png)
```

그림이 정상적으로 보이면 **Word에서 markdown을 저장하면서 시각적 콘텐츠를 보존**하는 데 성공한 것입니다. 보이지 않으면 콘솔에 출력된 상대 경로를 다시 확인하세요.

## 솔루션 확장

* **Batch conversion** – `.docx` 파일이 들어 있는 디렉터리를 순회하면서 동일한 콜백 로직을 재사용합니다.  
* **Custom image formats** – 콜백 안에서 모든 이미지를 WebP 로 변환해 파일 크기를 줄입니다.  
* **Parallel processing** – 대량 변환 시 `Parallel.ForEach` 를 사용하되 파일 시스템 경쟁에 주의합니다.

이 모든 변형은 핵심 질문에 답합니다: **Word에서 markdown을 저장**하고 **resources 폴더**를 깔끔하게 만드는 방법.

## 결론

이제 Aspose.Words를 이용해 **Word 문서에서 markdown을 저장**, **docx를 markdown으로 변환**, 그리고 **이미지를 추출**하는 방법을 알게 되었습니다. 핵심은 `IResourceSavingCallback` 으로, 각 이미지가 저장될 위치를 완전히 제어할 수 있어 프로젝트 레이아웃에 맞는 **resources 폴더** 구조를 손쉽게 만들 수 있습니다.

한 번 실행해 보고, 폴더 명명 규칙을 여러분의 컨벤션에 맞게 조정하면 문서, 정적 사이트 생성기, 혹은 markdown과 이미지가 함께 있어야 하는 모든 시나리오에 강력한 파이프라인을 구축할 수 있습니다.

---

*Happy coding! 문제가 발생하면 아래 댓글을 남기거나 GitHub에서 저에게 ping 주세요 – 빠른 디버깅을 도와드리겠습니다.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}