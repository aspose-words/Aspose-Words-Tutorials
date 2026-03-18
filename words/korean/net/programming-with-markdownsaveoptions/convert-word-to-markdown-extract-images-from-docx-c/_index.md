---
category: general
date: 2026-03-17
description: C#에서 DOCX의 이미지를 추출하면서 Word를 Markdown으로 변환합니다. 이미지 추출 방법, 콜백 설정, 그리고 assets
  폴더와 함께 마크다운을 저장하는 방법을 배워보세요.
draft: false
keywords:
- convert word to markdown
- extract images from docx
- how to extract images
- how to convert docx
language: ko
og_description: C#에서 Word를 Markdown으로 변환하고 DOCX에서 이미지를 추출하는 방법을 배워보세요. 단계별 코드, 설명
  및 원활한 변환을 위한 팁.
og_title: Word를 Markdown으로 변환하고 DOCX에서 이미지 추출하기 (C#) – 전체 가이드
tags:
- Aspose.Words
- C#
- Markdown
- Document Conversion
title: Word를 Markdown으로 변환하고 DOCX에서 이미지 추출 (C#)
url: /ko/net/programming-with-markdownsaveoptions/convert-word-to-markdown-extract-images-from-docx-c/
---

(Copy‑Paste Ready)".

Now ensure we preserve markdown formatting.

Let's produce final output.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word를 Markdown으로 변환하고 DOCX에서 이미지 추출하기 (C#)

Word를 **Markdown으로 변환**하려고 했는데 이미지가 사라지는 문제에 직면한 적 있나요? 당신만 그런 것이 아닙니다. 실제 프로젝트—정적 사이트 생성기, 문서 파이프라인, 헤드리스 CMS 등—에서는 Markdown 텍스트 **와** 원본 이미지를 *assets* 폴더에 깔끔하게 보관해야 합니다.  

이 튜토리얼에서는 Aspose.Words for .NET을 사용해 **docx를 Markdown으로 변환하면서 이미지도 추출**하는 방법을 정확히 보여드립니다. 리소스 저장 콜백을 설정하고, 파일명 중복 처리와 같은 엣지 케이스를 다루며, 정적 사이트 빌더에 바로 사용할 수 있는 깔끔한 폴더 구조를 만드는 과정을 단계별로 안내합니다.  

## 배울 내용

- `.docx` 파일을 로드하고 변환 준비하기.  
- `IResourceSavingCallback`을 구현해 **DOCX에서 이미지 추출**하기.  
- `MarkdownSaveOptions`를 구성해 Markdown이 assets를 올바르게 참조하도록 설정하기.  
- 코드를 실행하고 `.md` 파일과 이미지 폴더가 기대대로 생성되는지 확인하기.  

**전제 조건** – .NET 6+ (또는 .NET Framework 4.7.2+)와 Aspose.Words 라이선스가 필요합니다(무료 체험판으로도 데모 가능). C# 및 파일 I/O에 대한 기본 지식이 있으면 더 수월하지만, 이 가이드는 독립적으로 구성되어 있습니다.

![Word를 Markdown으로 변환한 폴더 레이아웃](https://example.com/convert-word-to-markdown.png "Word를 Markdown으로 변환한 폴더 레이아웃")

*변환 후 폴더 레이아웃 – Markdown 파일은 모든 추출된 이미지를 담은 `assets` 폴더 옆에 위치합니다.*

---

## Step 1: 소스 문서 로드 (convert word to markdown)

먼저 변환하려는 `.docx` 파일을 읽습니다. Aspose.Words는 저수준 OPC 포맷을 추상화하므로 한 줄만으로 작업을 수행할 수 있습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

// Adjust these paths to match your environment.
string inputPath  = Path.Combine("YOUR_DIRECTORY", "input.docx");
string outputDir  = Path.Combine("YOUR_DIRECTORY", "output");

// Ensure the output folder exists.
Directory.CreateDirectory(outputDir);

// Load the DOCX file.
Document document = new Document(inputPath);
```

*왜 중요한가:* 문서를 일찍 로드하면 텍스트 콘텐츠 **와** 삽입된 리소스(이미지, 차트 등)를 모두 포함하는 `Document` 객체를 얻을 수 있습니다. 이 단계가 없으면 나중에 **이미지를 추출하는 방법**을 수행할 수 없습니다.

---

## Step 2: DOCX에서 **이미지를 추출하는 방법**에 대한 콜백 만들기

Aspose.Words는 리소스를 쓸 때마다 `IResourceSavingCallback`을 호출합니다. 자체 구현을 제공하면 파일이 저장되는 **위치**와 Markdown이 해당 파일을 **참조하는 방식**을 직접 결정할 수 있습니다.

```csharp
/// <summary>
/// Saves each extracted resource (image, video, etc.) into an "assets" sub‑folder
/// and rewrites the markdown reference to point at that relative path.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    private readonly string _outputDirectory;

    public MyMarkdownResourceCallback(string outputDirectory)
    {
        _outputDirectory = outputDirectory;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Build the assets folder path.
        string assetsFolder = Path.Combine(_outputDirectory, "assets");
        Directory.CreateDirectory(assetsFolder);

        // 2️⃣ Resolve potential filename collisions.
        string safeFileName = GetUniqueFileName(assetsFolder, args.ResourceFileName);

        // 3️⃣ Write the resource stream to disk.
        string assetPath = Path.Combine(assetsFolder, safeFileName);
        using (FileStream fs = new FileStream(assetPath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // 4️⃣ Tell the markdown writer the *relative* path it should embed.
        args.ResourceFileName = Path.Combine("assets", safeFileName);
        args.KeepResourceStreamOpen = false; // we already closed it
    }

    // Helper: ensure we don't overwrite an existing file.
    private string GetUniqueFileName(string folder, string originalName)
    {
        string filePath = Path.Combine(folder, originalName);
        if (!File.Exists(filePath))
            return originalName;

        string nameWithoutExt = Path.GetFileNameWithoutExtension(originalName);
        string ext = Path.GetExtension(originalName);
        int counter = 1;

        while (File.Exists(filePath))
        {
            string candidate = $"{nameWithoutExt}_{counter}{ext}";
            filePath = Path.Combine(folder, candidate);
            counter++;
        }

        return Path.GetFileName(filePath);
    }
}
```

**핵심 포인트**  

- **왜 assets 하위 폴더인가?** 이미지와 `.md` 파일을 분리하면 대부분의 정적 사이트 생성기가 기대하는 레이아웃과 일치합니다.  
- **충돌 처리**는 동일한 이미지가 여러 번 나타날 때 발생하는 “파일이 이미 존재합니다” 예외를 방지합니다.  
- `args.KeepResourceStreamOpen = false` 설정은 스트림을 우리가 직접 관리했음을 Aspose에 알려 메모리 누수를 방지합니다.

---

## Step 3: **MarkdownSaveOptions**에 콜백 연결하기

이제 Aspose.Words가 리소스를 쓸 때마다 우리 콜백을 사용하도록 지정합니다. 이것이 **docx를 변환하면서 미디어를 보존**하는 핵심입니다.

```csharp
// Instantiate the callback with the output directory.
var resourceCallback = new MyMarkdownResourceCallback(outputDir);

// Configure markdown options.
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // The callback does the heavy lifting for image extraction.
    ResourceSavingCallback = resourceCallback,

    // Optional: make the markdown more GitHub‑friendly.
    ExportImagesAsBase64 = false, // we want separate files, not embedded data URIs.
    ExportHeadersFooters = true,
    ExportDocumentProperties = false
};
```

*`ExportImagesAsBase64 = false`를 설정한 이유:* Base64‑인코딩된 이미지는 Markdown 파일을 부풀리고 깨끗한 `assets` 폴더를 유지하려는 목적에 반합니다. 이를 비활성화하면 Markdown에 `![](assets/image.png)`와 같은 간단한 참조가 들어갑니다.

---

## Step 4: 문서를 Markdown으로 저장

모든 준비가 끝났으니, 한 줄 코드로 `.md` 파일과 이미지들을 동시에 생성합니다.

```csharp
string markdownPath = Path.Combine(outputDir, "output.md");

// Save the document.
document.Save(markdownPath, markdownOptions);
Console.WriteLine($"✅ Conversion complete! Markdown saved to: {markdownPath}");
Console.WriteLine($"📁 Extracted images are in: {Path.Combine(outputDir, "assets")}");
```

**예상 결과**  

- `output.md` 파일에 각 이미지 태그가 `assets/<image_name>`을 가리키는 Markdown 텍스트가 포함됩니다.  
- `assets` 폴더에 원본 `input.docx`에 삽입된 PNG, JPEG, GIF 파일이 채워집니다.  

`output.md`를 VS Code, GitHub, MkDocs 등 어떤 Markdown 뷰어에서 열어도 Word 문서에 있던 이미지가 그대로 렌더링됩니다.

---

## 흔히 발생하는 문제 처리 (FAQ)

### DOCX에 중복 이미지 이름이 있을 경우?
`GetUniqueFileName` 헬퍼가 증분 접미사(`image_1.png`, `image_2.png`, …)를 추가해 파일이 덮어씌워지는 일을 방지합니다.

### Aspose.Words에 라이선스가 필요할까?
체험판으로 실험은 충분히 가능하지만, 프로덕션에서는 평가 워터마크를 제거하고 최적 성능을 얻기 위해 라이선스를 구매해야 합니다.

### 여러 Word 파일을 한 번에 변환할 수 있나요?
물론입니다. `foreach (var file in Directory.GetFiles(sourceFolder, "*.docx"))` 루프 안에 로드·저장 코드를 넣고, 동일한 `MyMarkdownResourceCallback` 인스턴스를 재사용하거나 파일당 새 인스턴스를 만들어 독립된 assets 폴더를 만들 수 있습니다.

### 이미지가 아닌 리소스(예: 삽입된 PDF)는 어떻게 처리하나요?
콜백은 **모든** 리소스 타입을 받습니다. `args.ResourceType`을 검사해 유지, 무시, 이름 변경 등을 자유롭게 결정할 수 있습니다.

### .NET Core와 호환되나요?
예. 위 코드는 .NET 6을 목표로 하지만 프로젝트 파일을 조정하면 .NET Framework 4.7.2에서도 동작합니다. Aspose.Words는 두 런타임을 모두 지원합니다.

---

## 전문가 팁 & 모범 사례

- **assets 폴더 정리** – 배치 변환 후, 빈 자리표시자 때문에 생성된 0바이트 파일을 삭제하는 간단 스크립트를 실행하세요.  
- **의미 있는 파일명 사용** – 사람이 읽기 쉬운 이미지 이름이 필요하면 `args.ResourceFileName`에 포함된 원본 `AltText`(존재하는 경우)를 추출해 파일명에 반영하세요.  
- **버전 관리** – 레포에는 Markdown만 저장하고, assets 폴더는 CI 파이프라인에서 자동 생성하도록 하면 저장소가 가볍게 유지됩니다.  
- **성능** – 대용량 문서의 경우 `markdownOptions.SaveFormat = SaveFormat.Markdown;`을 설정하고 `MemoryStream`에 먼저 쓰는 방식을 고려하세요.

---

## 전체 작업 예제 (복사‑붙여넣기 바로 사용)

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

/// <summary>
/// Demonstrates converting a DOCX to Markdown while extracting images into an assets folder.
/// </summary>
class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1️⃣ Paths – adjust these to your environment.
        // -----------------------------------------------------------------
        string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");
        string outputDir = Path.Combine("YOUR_DIRECTORY", "output");
        Directory.CreateDirectory(outputDir);

        // -----------------------------------------------------------------
        // 2️⃣ Load the source document.
        // -----------------------------------------------------------------
        Document doc = new Document(inputPath);

        // -----------------------------------------------------------------
        // 3️⃣ Set up the resource‑saving callback.
        // -----------------------------------------------------------------
        var callback = new MyMarkdownResourceCallback(outputDir);

        // -----------------------------------------------------------------
        // 4️⃣ Configure Markdown options.
        // -----------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = callback,
            ExportImagesAsBase64 = false,
            ExportHeadersFooters = true,
            ExportDocumentProperties = false
        };

        // -----------------------------------------------------------------
        // 5️⃣ Save as Markdown.
        // -----------------------------------------------------------------
        string markdownFile = Path

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}