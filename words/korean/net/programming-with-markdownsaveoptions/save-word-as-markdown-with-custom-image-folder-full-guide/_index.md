---
category: general
date: 2026-04-07
description: 콜백을 사용하여 Word를 Markdown으로 저장하고 docx에서 이미지를 추출합니다. 콜백을 활용해 마크다운 이미지 폴더를
  효율적으로 저장하는 방법을 배워보세요.
draft: false
keywords:
- save word as markdown
- extract images from docx
- how to use callback
- markdown images folder
language: ko
og_description: 콜백을 사용하여 Word를 Markdown으로 저장하고 docx에서 이미지를 추출합니다. 이 가이드는 콜백을 사용해 마크다운
  이미지 폴더를 만드는 방법을 보여줍니다.
og_title: Word를 Markdown으로 저장하기 – 완전한 단계별 가이드
tags:
- Aspose.Words
- C#
- Markdown
- Image Extraction
title: 맞춤 이미지 폴더로 워드 파일을 마크다운으로 저장하기 – 전체 가이드
url: /ko/net/programming-with-markdownsaveoptions/save-word-as-markdown-with-custom-image-folder-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word를 Markdown으로 저장 – 완전 단계별 가이드

Word를 **Markdown으로 저장**해야 했지만 삽입된 그림을 어떻게 할지 몰랐던 적이 있나요? 당신만 그런 것이 아닙니다. 많은 프로젝트에서 markdown 출력은 보기 좋지만—*그때* 파일이 Word 패키지를 떠나지 않아 이미지 링크가 깨진 것을 깨닫게 됩니다.  

좋은 소식은 Aspose.Words가 **extract images from docx**를 깔끔하게 수행하고 원하는 위치에 배치할 수 있는 **callback**을 제공한다는 것입니다. 이 콜백을 사용하면 markdown 이미지 폴더를 제어할 수 있습니다. 이 튜토리얼에서는 `.docx` 파일을 로드하는 것부터 PNG(또는 사용 중인 다른 형식)의 정돈된 폴더와 해당 이미지를 가리키는 markdown 파일을 만드는 전체 과정을 단계별로 안내합니다.

이 가이드를 끝까지 따라하면 다음을 할 수 있습니다:

* 한 줄의 코드만으로 Word 문서를 Markdown으로 변환합니다.  
* 모든 그림을 전용 `images` 하위 폴더에 자동으로 덤프합니다.  
* 파일 이름을 맞춤 설정하여 소스에 수십 개의 그림이 있어도 충돌하지 않게 합니다.  

외부 스크립트 없이, 수동 복사‑붙여넣기 없이—순수 C#와 Aspose.Words만으로 가능합니다.

## Prerequisites

시작하기 전에 다음을 준비하세요:

* **Aspose.Words for .NET** (최신 안정 버전; 작성 시점 기준 24.9).  
* .NET 개발 환경 (Visual Studio, Rider, 또는 `dotnet` CLI).  
* 최소 하나의 이미지를 포함하고 있는 Word 문서(`.docx`)—예: `DocWithImages.docx`.  

Aspose.Words를 처음 사용한다면 걱정하지 마세요. 이 라이브러리는 완전 관리형이며 COM 인터옵이 필요 없고 .NET 6+와 .NET Framework 4.8 모두에서 동작합니다.

## Step 1 – Set Up the Project and Install the Package

새 콘솔 앱을 만들거나 기존 프로젝트에 코드를 추가합니다.

```bash
dotnet new console -n WordToMarkdownDemo
cd WordToMarkdownDemo
dotnet add package Aspose.Words
```

> **Pro tip:** .NET 6을 대상으로 하는 경우 기본 `Program.cs`가 이미 top‑level statements를 사용하므로 샘플이 간결합니다.

## Step 2 – Create a Callback to Control Image Saving

Aspose.Words는 이미지, CSS 등 외부 리소스를 쓸 때마다 `IResourceSavingCallback.ResourceSaving`을 호출합니다. 이 인터페이스를 구현하면 **how the markdown images folder**를 완전히 제어할 수 있습니다.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

/// <summary>
/// Handles the saving of resources (e.g., images) when a document is converted to Markdown.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    // Folder where we want to dump the images.
    private readonly string _imageFolder;

    public MyMarkdownResourceCallback(string imageFolder)
    {
        _imageFolder = imageFolder;
        // Ensure the folder exists before the first write.
        Directory.CreateDirectory(_imageFolder);
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build a unique filename: img_<guid>.<originalExtension>
        string uniqueName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.FileName)}";

        // Full path where the image will be saved.
        string fullPath = Path.Combine(_imageFolder, uniqueName);
        args.ResourceFileName = fullPath;

        // Copy the incoming stream to our file.
        using (FileStream outStream = File.OpenWrite(fullPath))
            args.Stream.CopyTo(outStream);

        // Tell Aspose we’ve handled the write; skip its default behavior.
        args.Cancel = true;
    }
}
```

### Why use a callback?

* **Granular control** – 폴더 구조와 파일 명명 방식을 직접 결정합니다.  
* **Performance** – 스트림을 한 번만 쓰므로 라이브러리의 이중 쓰기 fallback을 피합니다.  
* **Flexibility** – 이 시점에 로깅, 이미지 최적화, 혹은 클라우드 스토리지 업로드까지 추가할 수 있습니다.

## Step 3 – Load the Word Document

콜백이 준비되었으니 이제 Aspose.Words에 원본 파일을 지정하면 됩니다.

```csharp
// Path to the source .docx (adjust as needed).
string sourcePath = Path.Combine("YOUR_DIRECTORY", "DocWithImages.docx");

// Load the document into memory.
Document doc = new Document(sourcePath);
```

> **What if the file isn’t found?**  
> `Document`는 `FileNotFoundException`을 발생시킵니다. 동적 경로를 사용할 경우 `try/catch`로 로드를 감싸세요.

## Step 4 – Wire Up the MarkdownSaveOptions

`MarkdownSaveOptions` 클래스를 사용해 방금 만든 콜백을 연결합니다. 또한 이미지가 markdown 파일을 기준으로 저장될 폴더를 지정합니다.

```csharp
// Define where we want the images folder to sit.
string markdownFolder = Path.Combine("YOUR_DIRECTORY", "markdown-output");
string imagesSubFolder = Path.Combine(markdownFolder, "images");

// Ensure the markdown output directory exists.
Directory.CreateDirectory(markdownFolder);

// Create the save options and attach the callback.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // This callback will be invoked for every image.
    ResourceSavingCallback = new MyMarkdownResourceCallback(imagesSubFolder),

    // Optional: keep image references relative to the markdown file.
    ImagesFolder = "images"
};
```

`ImagesFolder` 속성은 Aspose가 `![Alt text](images/img_123.png)`와 같은 markdown 링크를 생성하도록 합니다. 콜백 안에서 `ResourceFileName`을 설정했기 때문에 실제 파일도 정확히 그 위치에 저장됩니다.

## Step 5 – Save as Markdown and Verify the Result

이제 markdown 파일을 저장합니다. 콜백이 이미 `images` 하위 폴더를 채워 두었습니다.

```csharp
// Destination markdown file.
string markdownPath = Path.Combine(markdownFolder, "Doc.md");

// Save the document.
doc.Save(markdownPath, mdOptions);

// Quick sanity check – list the generated files.
Console.WriteLine("Markdown saved to: " + markdownPath);
Console.WriteLine("Extracted images:");
foreach (var img in Directory.GetFiles(imagesSubFolder))
{
    Console.WriteLine("  • " + Path.GetFileName(img));
}
```

### Expected output

프로그램을 실행하면 다음과 비슷한 내용이 출력됩니다:

```
Markdown saved to: C:\Project\markdown-output\Doc.md
Extracted images:
  • img_5c2a1f8b-3e7b-4d9a-9c1f-2b6e5f9d9a3c.png
  • img_a7d4c9e2-1f55-4c2b-8f6a-9e1b2c3d4e5f.jpg
```

`Doc.md`를任意의 markdown 뷰어에서 열면 이미지 링크가 `images` 폴더를 올바르게 가리키는 것을 확인할 수 있습니다.

---

## Frequently Asked Questions (FAQ)

### How to **extract images from docx** without converting to markdown?

같은 `MyMarkdownResourceCallback`을 재사용하되 `doc.Save("images.zip", SaveFormat.Zip)`에 전달하면 됩니다. 콜백은 각 이미지마다 여전히 호출되어 원하는 위치에 저장할 수 있습니다.

### What if I need **different image formats**?

`args.FileName`에는 이미 원본 확장자(`.png`, `.jpg` 등)가 포함되어 있습니다. 모든 이미지를 단일 형식으로 변환해야 한다면 `ResourceSaving` 내부에서 스트림을 쓰기 전에 변환 단계를 추가하면 됩니다.

### Can I **customize the markdown images folder** per document?

물론입니다. 콜백은 생성자에서 폴더 경로를 받으므로 배치 처리 시 각 문서마다 다른 폴더를 지정해 새로운 콜백 인스턴스를 만들면 됩니다.

### Does this work with **large documents** (hundreds of images)?

예. 콜백은 이미지를 직접 디스크에 스트리밍하므로 메모리 사용량이 낮습니다. 대상 드라이브에 충분한 여유 공간이 있는지, OS 파일 핸들 제한에 걸리지 않는지만 확인하면 됩니다.

## Full Working Example

아래는 복사‑붙여넣기만 하면 바로 실행 가능한 전체 프로그램입니다. `YOUR_DIRECTORY`를 환경에 맞는 절대 경로나 상대 경로로 바꾸세요.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class MyMarkdownResourceCallback : IResourceSavingCallback
{
    private readonly string _imageFolder;

    public MyMarkdownResourceCallback(string imageFolder)
    {
        _imageFolder = imageFolder;
        Directory.CreateDirectory(_imageFolder);
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        string uniqueName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.FileName)}";
        string fullPath = Path.Combine(_imageFolder, uniqueName);
        args.ResourceFileName = fullPath;

        using (FileStream outStream = File.OpenWrite(fullPath))
            args.Stream.CopyTo(outStream);

        args.Cancel = true;
    }
}

class Program
{
    static void Main()
    {
        // Adjust these paths.
        string baseDir = Path.Combine(Environment.CurrentDirectory, "demo");
        string sourceDoc = Path.Combine(baseDir, "DocWithImages.docx");
        string markdownDir = Path.Combine(baseDir, "markdown-output");
        string imagesDir = Path.Combine(markdownDir, "images");
        string markdownFile = Path.Combine(markdownDir, "Doc.md");

        // Load the document.
        Document doc;
        try
        {
            doc = new Document(sourceDoc);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // Configure save options with our callback.
        var mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new MyMarkdownResourceCallback(imagesDir),
            ImagesFolder = "images"
        };

        // Ensure output folder exists.
        Directory.CreateDirectory(markdownDir);

        // Save as markdown.
        doc.Save(markdownFile, mdOptions);

        Console.WriteLine($"✅ Markdown saved to: {markdownFile}");
        Console.WriteLine("🖼️ Extracted images:");
        foreach (var file in Directory.GetFiles(imagesDir))
            Console.WriteLine($"   - {Path.GetFileName(file)}");
    }
}
```

프로그램을 실행(`dotnet run`)하면 `Doc.md`와 함께 `images` 하위 폴더가 생성되고, 그 안에 이미지 파일들이 들어 있습니다.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}