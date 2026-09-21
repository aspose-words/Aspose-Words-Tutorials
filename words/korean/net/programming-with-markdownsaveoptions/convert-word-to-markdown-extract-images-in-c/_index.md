---
category: general
date: 2026-02-18
description: Aspose.Words를 사용하여 Word를 Markdown으로 변환하고 docx에서 이미지를 추출합니다. 완전한 C# 예제로
  Word에서 Markdown을 생성하는 방법을 배워보세요.
draft: false
keywords:
- convert word to markdown
- extract images from docx
- how to extract images
- generate markdown from word
- how to convert docx to markdown
language: ko
og_description: Aspose.Words를 사용하여 Word를 Markdown으로 변환하고 docx에서 이미지를 추출합니다. 이 가이드는
  Word에서 Markdown을 단계별로 생성하는 방법을 보여줍니다.
og_title: Word를 Markdown으로 변환 – C#에서 이미지 추출
tags:
- C#
- Aspose.Words
- Markdown
- Document Conversion
title: Word를 Markdown으로 변환 – C#에서 이미지 추출
url: /ko/net/programming-with-markdownsaveoptions/convert-word-to-markdown-extract-images-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word를 Markdown으로 변환 – C#에서 이미지 추출

Word 파일을 **convert Word to Markdown** 하면서 `.docx` 파일에 포함된 모든 그림을 추출하는 방법이 궁금하셨나요? 당신만 그런 것이 아닙니다. 많은 개발자들이 Word로 작성된 계약서, 블로그 포스트, 기술 사양서를 깔끔한 markdown 형태로 변환해야 할 때 난관에 부딪히곤 합니다. 좋은 소식은? Aspose.Words for .NET을 사용하면 몇 줄의 코드만으로 이를 구현할 수 있으며, markdown 파일 *과* 원본 이미지가 들어 있는 폴더를 동시에 얻을 수 있습니다.

이 튜토리얼에서는 **Word에서 markdown을 생성**하고, docx에서 이미지를 추출하며, 모든 결과를 디스크에 저장하는 완전한 실행 가능한 C# 프로그램을 단계별로 살펴봅니다. 끝까지 따라오시면 **docx를 markdown으로 변환**하는 방법, **docx에서 이미지를 추출**하는 방법, 그리고 자체 프로젝트에 맞게 프로세스를 조정하는 방법을 정확히 알게 됩니다.

## What You’ll Need

- **Aspose.Words for .NET** (v23.10 이상). `Install-Package Aspose.Words` 명령으로 무료 체험 NuGet 패키지를 받을 수 있습니다.
- .NET 6+ SDK (최근 버전이면 모두 사용 가능).
- 최소 하나의 그림이 포함된 샘플 `input.docx`.
- markdown 파일과 이미지 자산을 저장할 폴더.

다른 서드파티 라이브러리는 필요하지 않습니다. 아래 코드는 필요한 모든 `using` 지시문을 포함하고 있으므로 콘솔 앱에 복사‑붙여넣기만 하면 **F5** 키로 바로 실행할 수 있습니다.

![Word를 Markdown으로 변환 예시](/images/convert-word-to-markdown.png "Word를 Markdown으로 변환")

*Image alt text: Word 파일이 이미지와 함께 Markdown 파일로 변환되는 모습을 보여주는 일러스트레이션.*

---

## Step 1: Load the Source Word Document

Aspose.Words에 변환하고자 하는 파일을 지정하는 것이 첫 번째 단계입니다. `Document` 객체는 `.docx` 내부의 텍스트, 표, 이미지 등 모든 요소에 접근할 수 있는 관문과 같습니다.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 👉 Step 1: Load the Word document that contains images.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document document = new Document(inputPath);
```

> **Why this matters:** 문서를 한 번만 로드하면 메모리 사용량을 낮게 유지하면서 라이브러리가 내부 패키지 구조를 검사할 수 있어 이후 이미지 추출에 필수적입니다.

---

## Step 2: Tell Aspose.Words How to Save as Markdown

Aspose.Words에는 `MarkdownSaveOptions` 클래스가 제공됩니다. 이 클래스를 통해 줄 바꿈 방식부터 외부 리소스(이미지 등)가 저장될 폴더까지 모든 옵션을 제어할 수 있습니다.

```csharp
        // 👉 Step 2: Configure Markdown save options with a resource‑saving callback.
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
        {
            // The callback fires for each external resource (e.g., an image) that needs a file.
            ResourceSavingCallback = new ResourceSavingCallback(args =>
            {
                // 👉 Step 3 inside the callback: decide where and how to store each image.
                string resourceFolder = @"YOUR_DIRECTORY\markdown-resources";
                Directory.CreateDirectory(resourceFolder); // creates if it doesn’t exist

                // Give each image a unique name to avoid collisions.
                string uniqueFileName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.FileName)}";
                args.FileName = Path.Combine(resourceFolder, uniqueFileName);

                // Optional: you could compress PNGs here by manipulating args.Stream.
            })
        };
```

> **Why a callback?** `ResourceSavingCallback`을 사용하면 추출된 각 이미지의 파일 이름과 위치를 완전히 제어할 수 있습니다. 콜백을 지정하지 않으면 Aspose가 모든 이미지를 동일한 폴더에 일반적인 이름으로 덤프하게 되며, 프로젝트 규모가 커질수록 관리가 어려워집니다.

---

## Step 3: Save the Document as Markdown

옵션 설정이 끝났다면 저장은 한 줄 코드로 마무리됩니다. 라이브러리가 단락, 헤딩, 리스트, 표 등을 변환하고, 콜백 덕분에 각 그림을 지정한 폴더에 기록합니다.

```csharp
        // 👉 Step 4: Save the document as a Markdown file.
        string outputPath = @"YOUR_DIRECTORY\output.md";
        document.Save(outputPath, markdownOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown saved to: {outputPath}");
        Console.WriteLine($"Images extracted to: {Path.GetDirectoryName(outputPath)}\\markdown-resources");
    }
}
```

### Expected Result

- `output.md` 파일에 markdown 구문이 포함됩니다(예: `![Image](markdown-resources/img_1234.png)`).
- `markdown-resources` 폴더에 원본 Word 파일에 있던 모든 이미지가 고유한 이름으로 저장됩니다.

`output.md`를 VS Code, GitHub, 혹은 정적 사이트 생성기 등任意의 markdown 뷰어에서 열면 원본 Word 레이아웃과 동일한 텍스트와 이미지를 확인할 수 있습니다—단, 훨씬 가볍고 웹 친화적인 형식으로 변환된 것입니다.

---

## Step 4: Common Variations & Edge Cases

### 4.1 Handling Existing Resource Folders

변환을 여러 번 실행하면 오래된 이미지가 남을 수 있습니다. 실행 전 폴더를 정리하는 간단한 가드 절을 추가하면 이를 방지할 수 있습니다:

```csharp
if (Directory.Exists(resourceFolder))
{
    foreach (var file in Directory.GetFiles(resourceFolder))
        File.Delete(file);
}
else
{
    Directory.CreateDirectory(resourceFolder);
}
```

### 4.2 Changing Image Formats

웹 최적화를 위해 모든 이미지를 JPEG 형식으로 변환해야 할 때가 있습니다. 콜백 내부에서 스트림을 재인코딩하면 됩니다:

```csharp
using (var img = System.Drawing.Image.FromStream(args.Stream))
{
    var jpegStream = new MemoryStream();
    img.Save(jpegStream, System.Drawing.Imaging.ImageFormat.Jpeg);
    jpegStream.Position = 0;
    args.Stream = jpegStream;
    args.FileName = Path.ChangeExtension(args.FileName, ".jpg");
}
```

> **Pro tip:** `System.Drawing.Common`은 Windows에서 동작합니다; Linux/macOS 환경에서는 크로스‑플랫폼 안전성을 위해 `ImageSharp` 사용을 권장합니다.

### 4.3 Preserving Table Styles

Word 문서가 테이블 서식에 크게 의존한다면 `MarkdownSaveOptions`를 조정해 테이블 스타일을 보존할 수 있습니다:

```csharp
markdownOptions.ExportTableColumnWidths = true;   // keeps column widths
markdownOptions.ExportTableBorders = true;       // adds markdown border syntax
```

### 4.4 Using a Different Output Directory

`Save` 메서드는 절대 경로나 상대 경로 어느 것이든 받아들입니다. CI 파이프라인에서는 임시 빌드 폴더를 지정해 사용할 수 있습니다:

```csharp
document.Save(Path.Combine(Path.GetTempPath(), "doc.md"), markdownOptions);
```

---

## Frequently Asked Questions

**Q: Does this work with `.doc` (binary) files?**  
A: Yes. `new Document("file.doc")`가 자동으로 형식을 감지하므로 동일한 코드로 `.doc`와 `.docx` 모두 처리할 수 있습니다.

**Q: What if the Word file contains embedded SVG images?**  
A: Aspose.Words는 SVG를 원본 형식 그대로 추출합니다. 래스터 버전이 필요하다면 콜백 내부에서 SVG 스트림을 변환해야 합니다(예: `Svg.Skia` 사용).

**Q: Can I skip the image extraction altogether?**  
A: `markdownOptions.ExportImagesAsBase64 = true;` 로 설정하면 이미지를 data URI 형태로 markdown에 직접 삽입할 수 있습니다—단일 파일 README 생성에 유용합니다.

---

## Recap & Next Steps

지금까지 **Word를 Markdown으로 변환**하는 전체 흐름을 살펴보았습니다:

1. `.docx` 로드
2. `ResourceSavingCallback`이 포함된 `MarkdownSaveOptions` 구성
3. 문서를 저장하고 콜백이 각 그림을 전용 폴더에 기록하도록 함

이 모든 작업은 50줄 이하의 C# 코드로 구현됩니다.

다음 단계로 고려해볼 수 있는 내용:

- **Generating a static site**: Hugo나 Jekyll 같은 정적 사이트 생성기에 markdown을 전달
- **Batch processing**: `foreach` 루프로 여러 파일을 자동으로 처리
- **Advanced image handling**: 콜백에서 이미지 리사이즈, 워터마크 삽입, 포맷 변환 등 실시간 처리

코드를 자유롭게 실험해 보세요—콜백 로직을 교체하거나 저장 옵션을 조정하거나 더 큰 문서 파이프라인에 통합해도 좋습니다. 이제 **generate markdown from word** 프로젝트를 위한 견고한 기반이 마련되었습니다.

Happy coding, and may your markdown always be clean and your images always found!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}