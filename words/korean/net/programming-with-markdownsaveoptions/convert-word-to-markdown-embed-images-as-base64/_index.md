---
category: general
date: 2026-01-03
description: Word를 한 번에 Markdown으로 변환하고 이미지를 base64로 삽입합니다. Word를 Markdown으로 저장하는
  방법, Word에서 Markdown을 생성하는 방법, 그리고 base64 이미지 데이터 URI를 사용하는 방법을 배워보세요.
draft: false
keywords:
- convert word to markdown
- embed images as base64
- save word as markdown
- base64 image data uri
- generate markdown from word
language: ko
og_description: Word를 Markdown으로 변환하고 이미지를 base64 데이터 URI로 삽입합니다. 이 단계별 튜토리얼에서는 Word를
  Markdown으로 저장하고 Word에서 Markdown을 생성하는 방법을 보여줍니다.
og_title: Word를 Markdown으로 변환 – Base64 이미지 삽입 가이드
tags:
- Aspose.Words
- C#
- Markdown
title: Word를 Markdown으로 변환 – 이미지를 Base64로 삽입
url: /ko/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word를 Markdown으로 변환 – 이미지를 Base64로 삽입

Word를 **markdown으로 변환**해야 할 때 이미지 때문에 계속 막히셨나요? 당신만 그런 것이 아닙니다. Word는 그림을 별도 파일로 저장하는 것을 좋아하지만, markdown은 모든 것을 하나의 파일에 깔끔하게 유지하는 `data:image/...;base64,` 문자열을 선호합니다.  

이 튜토리얼에서는 **Word를 markdown으로 저장**, **이미지를 Base64로 삽입**하고, Aspose.Words for .NET을 사용해 **Word에서 markdown을 생성**하는 완전한 실행 가능한 솔루션을 단계별로 안내합니다. 최종적으로 원본 문서와 똑같이 렌더링되는 단일 `.md` 파일을 얻을 수 있으며, 별도의 이미지 폴더가 필요 없습니다.

## 필요 사항

- **.NET 6.0 이상** (NuGet 패키지를 참조할 수 있는 환경)
- **Aspose.Words for .NET** (무료 체험판으로 테스트 가능)
- 몇 장의 그림이 포함된 간단한 `.docx` 파일 (`input.docx` 라고 부르겠습니다)
- 선호하는 IDE (Visual Studio, Rider, VS Code 등)

이미 준비되어 있다면, 바로 시작합니다. 아직이라면 NuGet 패키지를 설치하는 한 줄 코드가 있습니다:

```bash
dotnet add package Aspose.Words
```

## Step 1: Load the Word Document — the starting point for **convert word to markdown**

먼저 `.docx` 파일을 메모리로 불러와야 합니다. 여기서 변환 마법이 시작됩니다.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word file that contains the images.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

> **Why this matters:**  
> 문서를 로드하면 Aspose가 텍스트, 스타일 및 모든 임베디드 리소스에 완전 접근할 수 있습니다. 이 단계가 없으면 변환할 것이 없습니다.

## Step 2: Set Up MarkdownSaveOptions with a Resource‑Saving Callback

Aspose는 일반적으로 디스크에 저장될 모든 리소스(이미지 등)를 가로챌 수 있게 해줍니다. 사용자 정의 `IResourceSavingCallback`을 제공하면 기본 파일 기반 저장을 **Base64 이미지 데이터 URI**로 대체할 수 있습니다.

```csharp
// Configure Markdown save options so that images become Base64 URIs.
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceHandler()
};
```

### The Custom Handler – Turning images into Base64

아래는 전체 구현 코드입니다. `args.ResourceType == ResourceType.Image` 를 확인한 뒤 다음을 수행합니다:

1. 이미지를 `MemoryStream`에 기록합니다.  
2. 바이트 배열을 Base64 문자열로 변환합니다.  
3. `data:image/jpeg;base64,` URI를 만들고 `args.Uri`에 할당합니다.

```csharp
// Custom handler that converts each image resource to a Base64 data URI.
class MyResourceHandler : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Only process images – leave other resources untouched.
        if (args.ResourceType == ResourceType.Image)
        {
            // Prepare an in‑memory stream for the image.
            using (MemoryStream ms = new MemoryStream())
            {
                // Save the image using default JPEG options.
                args.ResourceData.Save(ms, ImageSaveOptions.DefaultJpeg);
                // Build the Base64 data URI.
                string base64 = Convert.ToBase64String(ms.ToArray());
                args.Uri = $"data:image/jpeg;base64,{base64}";
                // No need to keep the stream open after we set the URI.
                args.KeepResourceStreamOpen = false;
            }
        }
    }
}
```

> **Pro tip:** 소스 Word가 PNG를 사용한다면 `ImageSaveOptions.DefaultJpeg`을 `ImageSaveOptions.DefaultPng`로 교체하고 MIME 타입을 `image/png`로 변경하세요.

## Step 3: Save the Document as Markdown – the final **save word as markdown** step

콜백이 준비되었으니 실제 저장은 한 줄 코드로 끝납니다.

```csharp
// Save the document to a Markdown file. Images are already embedded.
document.Save("YOUR_DIRECTORY/output.md", markdownSaveOptions);
```

`output.md`를 any markdown viewer(VS Code preview, GitHub 등)에서 열면 원본 Word 파일과 동일한 텍스트가 표시되고, 그림은 별도 파일 없이 인라인으로 나타납니다.

## Expected Output

```markdown
# Sample Title

Here’s a paragraph that originally lived in Word.

![Embedded Image](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBxISEhU...
```

`![Embedded Image]` 라인은 **Base64 이미지 데이터 URI**이며, 이미지 전체가 바로 그곳에 인코딩됩니다. 별도 폴더도 없고, 깨진 링크도 없습니다.

## Edge Cases & How to Handle Them

| 상황 | 해결 방법 |
|-----------|------------|
| **대용량 이미지** – Base64는 크기를 약 33% 증가시킴 | 변환 전에 리사이즈를 고려하세요: `args.ResourceData.Save(ms, new ImageSaveOptions { ImageResolution = 72 })`. |
| **Non‑JPEG 이미지** (PNG, GIF) | `args.ResourceData.ImageType`으로 원본 포맷을 감지하고 올바른 MIME 타입(`image/png`, `image/gif`)을 설정합니다. |
| **매우 긴 문서** (수백 개 이미지) | 메모리 사용량을 주시하세요; RAM이 부족하면 각 이미지를 일시적으로 디스크에 스트리밍할 수 있습니다. |
| **별도 이미지 파일 필요** (정적 사이트 등) | 파일로 유지하고 싶은 이미지에 대해 콜백에서 `false`를 반환하고, Aspose가 폴더에 저장하도록 합니다. |

## Common Questions (Answered Up Front)

- **Does this work with .doc files?** 예—Aspose.Words는 레거시 `.doc` 파일도 `.docx`와 동일하게 로드할 수 있습니다. `new Document("myfile.doc")`만 지정하면 됩니다.
- **What about tables and footnotes?** 테이블과 각주 모두 Markdown 익스포터에서 완전 지원됩니다. 테이블은 markdown 표로, 각주는 인라인 참조로 변환됩니다.
- **Can I change the markdown flavor?** `MarkdownSaveOptions`에는 `MarkdownVersion` 속성(CommonMark, GitHub 등)이 있습니다. 특정 문법이 필요하면 저장 전에 해당 속성을 설정하세요.

## Full, Ready‑to‑Run Sample

아래는 콘솔 앱에 복사‑붙여넣기 할 수 있는 전체 프로그램입니다. 모든 using 문, 핸들러 클래스, 오류 처리까지 포함되어 있습니다.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToMarkdownDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            try
            {
                // 1️⃣ Load the source Word document.
                Document doc = new Document("YOUR_DIRECTORY/input.docx");

                // 2️⃣ Prepare Markdown options with our custom image handler.
                MarkdownSaveOptions options = new MarkdownSaveOptions
                {
                    ResourceSavingCallback = new MyResourceHandler()
                };

                // 3️⃣ Save as Markdown – images become Base64 URIs.
                string outputPath = "YOUR_DIRECTORY/output.md";
                doc.Save(outputPath, options);

                Console.WriteLine($"✅ Success! Markdown saved to {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Conversion failed: {ex.Message}");
            }
        }
    }

    // Custom callback that embeds images as Base64 data URIs.
    class MyResourceHandler : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            if (args.ResourceType == ResourceType.Image)
            {
                using (MemoryStream ms = new MemoryStream())
                {
                    // Preserve original format if you prefer PNG/GIF.
                    args.ResourceData.Save(ms, ImageSaveOptions.DefaultJpeg);
                    string base64 = Convert.ToBase64String(ms.ToArray());
                    args.Uri = $"data:image/jpeg;base64,{base64}";
                    args.KeepResourceStreamOpen = false;
                }
            }
        }
    }
}
```

프로그램을 실행하고 생성된 `output.md`를 열면 Word 파일의 완벽한 markdown 복제본을 확인할 수 있습니다—**convert word to markdown**이 이렇게 쉬웠던 적은 없습니다.

## Recap

우리는 **convert word to markdown**하면서 이미지를 인라인으로 유지하는 문제로 시작했습니다. 문서를 로드하고, `MarkdownSaveOptions` 콜백을 구성한 뒤 파일을 저장함으로써 **save word as markdown** 솔루션을 구현했고, 이는 **Base64 이미지 데이터 URI** 문자열을 생성합니다. 이제 **이미지를 Base64로 삽입**하는 방법, 다양한 상황에 대한 처리법, 이미지 타입별 튜닝 방법까지 모두 알게 되었습니다.

## What’s Next?

- **Generate HTML instead of markdown** – `MarkdownSaveOptions`를 `HtmlSaveOptions`로 교체하고 동일한 콜백을 재사용합니다.  
- **Batch convert multiple files** – 폴더를 `foreach` 루프로 순회하도록 로직을 감쌉니다.  
- **Integrate into a CI pipeline** – 정적 사이트용 문서 생성을 자동화합니다.  

실험해 보고, 이미지 품질을 조정하거나 자체 리소스 처리(예: CDN에 업로드하고 URL 삽입)를 추가해 보세요. Aspose.Words와 약간의 C# 창의성을 결합하면 가능성은 무한합니다.

Happy coding, and may your markdown always render perfectly! 

![Diagram showing convert word to markdown flow – embed images as base64](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNjAwIiBoZWlnaHQ9IjQwMCIgdmlld0JveD0iMCAwIDYwMCA0MDAiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+PHJlY3Qgd2lkdGg9IjYwMCIgaGVpZ2h0PSI0MDAiIGZpbGw9IiNmZmYiIHN0cm9rZT0iI2NjYyIgLz48dGV4dCB4PSI1MCIgeT0iMjAwIiBmb250LXNpemU9IjM2IiBmaWxsPSIjMDAwIj5JbWFnZSBJbWFnZSBJbWFnZSBJbWFnZTwvdGV4dD48L3N2Zz4= "convert word to markdown flow diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}