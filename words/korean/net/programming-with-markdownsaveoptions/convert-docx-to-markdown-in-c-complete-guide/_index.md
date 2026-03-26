---
category: general
date: 2026-03-25
description: Aspose.Words를 사용하여 Word에서 이미지를 추출하면서 DOCX를 빠르게 Markdown으로 변환합니다. 전체 코드를
  포함한 단계별 학습.
draft: false
keywords:
- convert docx to markdown
- extract images from word
language: ko
og_description: Aspose.Words를 사용하여 DOCX를 Markdown으로 변환하고 Word에서 이미지를 추출하세요. 바로 실행
  가능한 솔루션을 위한 완전한 튜토리얼을 따라보세요.
og_title: C#에서 DOCX를 Markdown으로 변환하기 – 단계별 가이드
tags:
- Aspose.Words
- C#
- Markdown
title: C#에서 DOCX를 Markdown으로 변환하기 – 완전 가이드
url: /ko/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words 로 DOCX를 Markdown으로 변환하기

**DOCX를 markdown으로 변환**하면서 삽입된 그림을 그대로 유지하는 방법을 찾고 계셨나요? 혼자가 아닙니다—많은 개발자들이 Word 콘텐츠를 정적 사이트 생성기나 문서 저장소로 옮기려 할 때 이 문제에 부딪힙니다.  
좋은 소식은 Aspose.Words for .NET이 이 작업을 대신 해줄 수 있으며, 작은 콜백을 추가하면 **Word 파일에서 이미지를 추출**할 수도 있다는 점입니다.

이 튜토리얼에서는 `.docx` 파일을 로드하고, Markdown 파일로 저장하며, 모든 이미지를 전용 폴더에 기록하는 실제 예제를 단계별로 살펴보겠습니다. 최종적으로 .NET 프로젝트에 바로 넣어 실행할 수 있는 콘솔 앱을 만들 수 있습니다.

> **Pro tip:** 텍스트만 필요하고 이미지가 필요 없으면 `ResourceSavingCallback`을 완전히 생략해도 됩니다 – 코드가 여전히 깔끔한 Markdown을 생성합니다.

## 준비 사항

- **Aspose.Words for .NET** (최신 버전, 예: 24.12). NuGet에서 가져올 수 있습니다: `Install-Package Aspose.Words`.
- **.NET 6.0** 이상 (API는 .NET Framework에서도 동작하지만, .NET 6이 가장 좋은 성능을 제공합니다).
- 간단한 콘솔 프로젝트 또는 선호하는 C# 호스트.
- 하나 이상의 그림이 포함된 입력 Word 파일 (`input.docx`) – 추출 과정을 확인하기 위해 필요합니다.

그게 전부입니다—추가 라이브러리나 복잡한 명령줄 도구가 필요 없습니다. 바로 시작해 보겠습니다.

![convert docx to markdown example](images/convert-docx-to-markdown.png)

*이미지 대체 텍스트: convert docx to markdown example*

## 1단계 – 프로젝트 설정 및 Aspose.Words 추가

정리를 위해 새 콘솔 앱을 생성합니다:

```bash
dotnet new console -n DocxToMarkdownDemo
cd DocxToMarkdownDemo
dotnet add package Aspose.Words
```

`Program.cs`를 열고 자동 생성된 코드를 모두 지웁니다. 전체 솔루션은 나중에 붙여넣을 것이니, 현재는 프로젝트가 빌드되는지 확인만 하면 됩니다.

## 2단계 – 원본 DOCX 로드

먼저 Aspose.Words에 Word 파일을 읽도록 지시합니다. 이 작업은 **빠릅니다**—라이브러리가 Word 자체를 열지 않고 문서 구조만 파싱합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Path to your source document
string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");

// Load the DOCX into a Document object
Document doc = new Document(inputPath);
```

왜 `Path.Combine`으로 경로를 감싸는 걸까요? Windows, macOS, Linux 어디서든 코드를 이식 가능하게 해 주기 때문입니다—CI 파이프라인으로 프로젝트를 옮길 때 큰 도움이 됩니다.

## 3단계 – 리소스 콜백이 포함된 Markdown 저장 옵션 구성

Aspose.Words에 Markdown으로 저장하도록 요청하면 기본적으로 이미지를 Base64 문자열로 삽입합니다. 작은 아이콘에는 괜찮지만, 큰 사진은 파일 크기를 급격히 늘립니다. 대신 **리소스 저장 콜백**을 연결해 각 이미지를 디스크에 저장하고 Markdown 링크를 업데이트합니다.

```csharp
// Define where the Markdown and resources will live
string outputDir = Path.Combine("YOUR_DIRECTORY", "Output");
string resourcesDir = Path.Combine(outputDir, "Resources");

// Ensure directories exist
Directory.CreateDirectory(outputDir);
Directory.CreateDirectory(resourcesDir);

// Create Markdown options and plug in the callback
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceSaver(resourcesDir)
};
```

`resourcesDir`을 콜백 생성자에 전달하는 것을 눈여겨 보세요—이렇게 하면 경로 로직이 콜백 내부에 섞이지 않아 클래스를 재사용하기 쉬워집니다.

## 4단계 – 리소스 저장 콜백 구현

콜백은 `IResourceSavingCallback`을 구현합니다. Aspose.Words가 각 이미지를 저장하려 할 때마다 `ResourceSavingArgs` 객체를 전달합니다. 우리는 **파일을 저장할 위치**를 결정하고, 고유한 이름을 부여한 뒤 엔진에게 기본 저장 동작을 건너뛰도록 지시합니다.

```csharp
class MyResourceSaver : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyResourceSaver(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build a unique, deterministic file name
        string ext = Path.GetExtension(args.FileName);          // e.g., ".png"
        string fileName = $"img_{args.Index}{ext}";            // img_0.png, img_1.jpg, …

        // Full path on disk
        string filePath = Path.Combine(_resourcesFolder, fileName);

        // Write the image bytes
        using (FileStream fs = new FileStream(filePath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Update the Markdown URI so it points to the saved image
        args.Uri = $"Resources/{fileName}";

        // Tell Aspose.Words we handled the saving
        args.Cancel = true;
    }
}
```

**왜 중요한가요:** `args.Uri`를 설정함으로써 최종 `.md` 파일에서 이미지가 어떻게 참조될지 정확히 제어할 수 있습니다. 상대 경로 `Resources/img_0.png`는 VS Code, GitHub, 정적 사이트 생성기 등 어디서든 동일하게 동작합니다.

## 5단계 – 문서를 Markdown으로 저장

이제 마지막 단계: Aspose.Words에 Markdown 파일 작성을 요청합니다. 앞서 연결한 콜백이 각 이미지마다 자동으로 실행됩니다.

```csharp
// Destination Markdown file
string markdownPath = Path.Combine(outputDir, "output.md");

// Perform the conversion
doc.Save(markdownPath, mdOptions);
```

위 코드가 끝나면 다음이 생성됩니다:

- `output.md` – 원본 Word 내용이 깔끔하게 변환된 Markdown 파일.
- `Resources/` 폴더 – DOCX에서 추출된 모든 그림이 들어 있습니다.

## 전체 작업 예제

아래는 **복사‑붙여넣기만 하면 되는** 전체 프로그램입니다. `YOUR_DIRECTORY`를 `input.docx`가 위치한 절대 경로나 상대 경로로 교체하세요.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

class Program
{
    static void Main()
    {
        // ------------------------------------------------------------
        // 1️⃣  Define paths
        // ------------------------------------------------------------
        string baseDir = Path.Combine(Environment.CurrentDirectory, "DemoFiles");
        string inputPath = Path.Combine(baseDir, "input.docx");
        string outputDir = Path.Combine(baseDir, "Output");
        string resourcesDir = Path.Combine(outputDir, "Resources");

        // Create folders if they don't exist
        Directory.CreateDirectory(outputDir);
        Directory.CreateDirectory(resourcesDir);

        // ------------------------------------------------------------
        // 2️⃣  Load the DOCX
        // ------------------------------------------------------------
        Document doc = new Document(inputPath);

        // ------------------------------------------------------------
        // 3️⃣  Prepare Markdown options with a resource callback
        // ------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new MyResourceSaver(resourcesDir)
        };

        // ------------------------------------------------------------
        // 4️⃣  Save as Markdown
        // ------------------------------------------------------------
        string markdownPath = Path.Combine(outputDir, "output.md");
        doc.Save(markdownPath, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown file: {markdownPath}");
        Console.WriteLine($"Images folder: {resourcesDir}");
    }
}

// -----------------------------------------------------------------
// Callback that writes each image to the Resources folder
// -----------------------------------------------------------------
class MyResourceSaver : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyResourceSaver(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Create a deterministic file name like img_0.png
        string extension = Path.GetExtension(args.FileName);
        string fileName = $"img_{args.Index}{extension}";
        string filePath = Path.Combine(_resourcesFolder, fileName);

        // Persist the image bytes
        using (FileStream fs = new FileStream(filePath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Update the Markdown link to point to the saved image
        args.Uri = $"Resources/{fileName}";

        // Cancel default saving because we already wrote the file
        args.Cancel = true;
    }
}
```

### 예상 출력

`Output/output.md`를 어떤 Markdown 뷰어에서 열면 다음과 비슷한 내용이 보일 것입니다:

```markdown
# My Sample Document

Here is a paragraph that came from Word.

![Image 1](Resources/img_0.png)

Another paragraph with **bold** text.
```

`Resources` 폴더에는 `img_0.png`, `img_1.jpg` 등 원본 `input.docx`에 삽입된 그림과 동일한 파일들이 들어 있습니다.

## 자주 묻는 질문 (FAQ)

**.doc 파일도 동작하나요?**  
네. Aspose.Words는 `.doc`, `.docx`, `.rtf` 등 다양한 형식을 로드할 수 있습니다. `inputPath`의 파일 확장자를 바꾸기만 하면 됩니다.

**이미지에 절대 URL을 사용하려면 어떻게 하나요?**  
`args.Uri = $"Resources/{fileName}";`를 `args.Uri = $"https://mycdn.com/docs/{fileName}";`와 같이 바꾸면 됩니다. Markdown은 이제 원격 위치를 참조합니다.

**이미지 품질이나 포맷을 제어할 수 있나요?**  
콜백은 원본 이미지 스트림을 제공합니다. PNG를 JPEG로 변환하고 싶다면 스트림을 `System.Drawing.Image`로 로드한 뒤 재인코딩하고, 새로운 바이트를 쓰고 `args.Uri`를 설정하면 됩니다.

**`ResourceSavingCallback`은 스레드‑안전한가요?**  
Aspose.Words는 각 리소스에 대해 콜백을 순차적으로 호출하므로

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}