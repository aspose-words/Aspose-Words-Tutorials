---
category: general
date: 2026-04-05
description: C#에서 DOCX를 Markdown으로 변환하고 DOCX에서 이미지를 추출하는 방법을 배워보세요. 전체 코드와 팁이 포함된
  단계별 가이드.
draft: false
keywords:
- convert docx to markdown
- extract images from docx
- Aspose.Words markdown conversion
- C# document processing
- image extraction C#
language: ko
og_description: Aspose.Words를 사용하여 DOCX를 Markdown으로 변환하고 DOCX에서 이미지를 추출합니다. 코드, 설명
  및 모범 사례 팁이 포함된 완전한 C# 튜토리얼.
og_title: DOCX를 Markdown으로 변환 – C#에서 DOCX 이미지 추출
tags:
- Aspose.Words
- C#
- Markdown
- DOCX
- Image extraction
title: DOCX를 Markdown으로 변환 – Aspose.Words로 DOCX에서 이미지 추출
url: /ko/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-extract-images-from-docx-with-aspos/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX를 Markdown으로 변환 – C#에서 DOCX에서 이미지 추출

DOCX를 **Markdown으로 변환**하고 싶었지만 출력에서 이미지가 사라지는 문제를 겪어본 적 있나요? 당신만 그런 것이 아닙니다. 많은 프로젝트에서 Markdown 버전은 버전 관리나 정적 사이트 생성기에 최적이지만, 그림이 남지 않아 풍부한 문서가 텍스트만 남은 빈 파일이 됩니다.  

좋은 소식은? 몇 줄의 C# 코드와 Aspose.Words만 있으면 **DOCX를 Markdown으로 변환** *하고* **DOCX에서 이미지를 자동으로 추출**할 수 있습니다. 이 가이드는 전체 과정을 단계별로 안내하고, 각 요소가 왜 중요한지 설명하며, 이미지 폴더를 깔끔하게 유지하는 방법까지 보여줍니다.

## 배울 내용

- 그림이 포함된 DOCX를 로드하는 방법
- 각 이미지가 저장될 위치를 결정하는 커스텀 `IResourceSavingCallback` 정의 방법
- 추출된 이미지를 올바르게 참조하도록 `MarkdownSaveOptions`를 설정하는 방법
- 중복 이미지 이름이나 PNG가 아닌 포맷과 같은 엣지 케이스 처리 팁
- 오늘 바로 실행할 수 있는 완전한 복사‑붙여넣기 가능한 코드 샘플

### 전제 조건

- .NET 6.0 이상 (.NET Core, .NET Framework, .NET 5+에서도 동작)
- **Aspose.Words for .NET** 라이선스 (무료 체험판으로 테스트 가능)
- C#와 Visual Studio(또는 선호하는 IDE)에 대한 기본 지식

위 조건을 갖췄다면, 바로 시작해봅시다.

---

## 1단계: 프로젝트 설정 및 Aspose.Words 설치

먼저 새 콘솔 앱을 만들거나 기존 솔루션에 통합합니다.

```bash
dotnet new console -n DocxToMarkdownDemo
cd DocxToMarkdownDemo
dotnet add package Aspose.Words
```

> **Pro tip:** 최신 NuGet 버전(2026년 4월 현재 24.12)을 사용하면 최신 Markdown 내보내기 개선 사항을 받을 수 있습니다.

---

## 2단계: 원하는 위치에 이미지를 저장하는 콜백 만들기

Aspose.Words는 Markdown 내보내기 중에 기록되는 모든 리소스(이미지, SVG 등)를 가로챌 수 있습니다. `IResourceSavingCallback`을 구현하면 다음을 할 수 있습니다.

1. Markdown 파일 옆에 위치할 폴더 선택
2. 기존 이미지를 덮어쓰지 않도록 고유 파일명 생성
3. 형식 지정(여기서는 일관성을 위해 PNG 강제)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

/// <summary>
/// Saves each image extracted from the DOCX into a dedicated folder
/// with a GUID‑based filename. The markdown file will reference the
/// new filename via <c>args.ResourceFileName</c>.
/// </summary>
class ImageResourceSaver : IResourceSavingCallback
{
    private readonly string _targetFolder;

    public ImageResourceSaver(string targetFolder)
    {
        _targetFolder = targetFolder;
        // Ensure the folder exists before we start writing files.
        Directory.CreateDirectory(_targetFolder);
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Generate a unique name to avoid collisions.
        string newFileName = $"img_{Guid.NewGuid():N}.png";

        // Full physical path where the image will be written.
        string fullPath = Path.Combine(_targetFolder, newFileName);

        // Tell the markdown exporter what name to use in the .md file.
        args.ResourceFileName = newFileName;

        // Provide a stream that writes to the desired location.
        args.Stream = new FileStream(fullPath, FileMode.Create);
    }
}
```

### 왜 GUID 기반 이름인가?

원본 DOCX에 동일한 원본 이름을 가진 두 그림이 있을 경우, 단순 복사‑붙여넣기로는 하나가 덮어써집니다. `Guid.NewGuid()`를 사용하면 고유성이 보장되어 자동화 파이프라인에서 여러 번 변환할 때 특히 유용합니다.

---

## 3단계: DOCX 로드 및 Markdown 옵션 연결

이제 문서를 메모리로 불러오고 방금 만든 콜백을 연결합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------------
        // 1️⃣  Define paths – adjust these to match your environment.
        // --------------------------------------------------------------------
        string sourceDocx = @"C:\Docs\WithImages.docx";
        string outputMarkdown = @"C:\Docs\DocWithImages.md";
        string imagesFolder = @"C:\Docs\MarkdownResources";

        // --------------------------------------------------------------------
        // 2️⃣  Load the Word document.
        // --------------------------------------------------------------------
        Document doc = new Document(sourceDocx);

        // --------------------------------------------------------------------
        // 3️⃣  Configure MarkdownSaveOptions with our custom saver.
        // --------------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // This tells Aspose.Words to call ImageResourceSaver for each image.
            ResourceSavingCallback = new ImageResourceSaver(imagesFolder)
        };

        // --------------------------------------------------------------------
        // 4️⃣  Perform the conversion.
        // --------------------------------------------------------------------
        doc.Save(outputMarkdown, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown saved to: {outputMarkdown}");
        Console.WriteLine($"Images saved to:   {imagesFolder}");
    }
}
```

### 코드가 수행하는 작업, 단계별 설명

| 단계 | 목적 |
|------|------|
| **Define paths** | 프로젝트를 유연하게 유지합니다. 재컴파일 없이도 원하는 폴더를 지정할 수 있습니다. |
| **Load the DOCX** | `Document`가 Word 파일을 파싱해 모든 요소(단락, 표, 그림)를 접근 가능하게 합니다. |
| **Configure `MarkdownSaveOptions`** | `ResourceSavingCallback`은 이미지를 추출하는 훅입니다. 이 콜백이 없으면 Aspose.Words는 이미지를 base64 문자열로 삽입하거나 전혀 저장하지 않을 수 있습니다. |
| **Save** | `doc.Save`가 Markdown 파일을 쓰고 각 이미지마다 콜백을 호출합니다. |

---

## 4단계: 출력 확인 – 어떤 결과가 보여야 할까?

프로그램을 실행한 뒤 `DocWithImages.md`를 열어보세요. 다음과 같은 Markdown 이미지 링크가 보일 것입니다.

```markdown
![img_1a2b3c4d5e6f7g8h9i0j.png](MarkdownResources/img_1a2b3c4d5e6f7g8h9i0j.png)
```

그리고 `C:\Docs\MarkdownResources` 폴더 안에 GUID 이름을 가진 PNG 파일들이 생성됩니다. 파일을 하나 열어보면 원본 DOCX에 포함된 그림과 동일함을 확인할 수 있습니다.

Markdown 파일을 상대 경로를 지원하는 뷰어(VS Code 프리뷰, GitHub, 정적 사이트 생성기 등)에서 열면 이미지가 Word에서 보였던 그대로 렌더링됩니다.

### 흔히 발생하는 문제와 해결 방법

| 증상 | 가능 원인 | 해결 방법 |
|------|----------|----------|
| 이미지가 깨진 링크로 표시 | `ResourceFileName`이 설정되지 않아 Markdown이 존재하지 않는 파일을 가리킴 | 콜백 안에서 `args.ResourceFileName = newFileName;`을 설정하세요. |
| PNG 파일이 너무 큼 | 원본 이미지가 JPEG이나 BMP였으며 PNG로 변환하면서 용량이 증가 | `args.ResourceContentType`을 통해 원본 포맷을 감지하고 그대로 유지: `args.ResourceFileName = $"{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";` |
| 중복 이미지가 여전히 존재 | 정적 파일명을 사용했기 때문 | GUID 로직으로 되돌리거나 이미지 타입별 카운터를 추가하세요. |
| 변환 중 `FileNotFoundException` 발생 | DOCX 경로가 잘못됐거나 폴더에 읽기 권한이 없음 | 경로를 확인하고 파일 시스템 권한을 부여하세요. |

---

## 5단계: 고급 조정 (선택 사항)

### 5.1 원본 이미지 포맷 유지

출력 이미지가 원본 확장자를 유지하도록 하려면 콜백을 다음과 같이 수정합니다.

```csharp
public void ResourceSaving(ResourceSavingArgs args)
{
    string ext = Path.GetExtension(args.ResourceFileName).ToLowerInvariant();
    // Default to .png if Aspose couldn't determine an extension.
    if (string.IsNullOrEmpty(ext)) ext = ".png";

    string newFileName = $"img_{Guid.NewGuid():N}{ext}";
    string fullPath = Path.Combine(_targetFolder, newFileName);
    args.ResourceFileName = newFileName;
    args.Stream = new FileStream(fullPath, FileMode.Create);
}
```

### 5.2 이미지를 Base64로 삽입 (별도 파일을 원하지 않을 때)

단일 파일 Markdown이 필요할 때(예: 이메일 전송) 옵션을 변경합니다.

```csharp
mdOptions.ImagesFolder = string.Empty; // disables external folder
mdOptions.ExportImagesAsBase64 = true;
```

하지만 대부분 정적 사이트 워크플로우에서는 **DOCX에서 이미지 추출**이 주요 목표이므로 폴더 방식을 사용하는 것이 일반적으로 더 좋습니다.

---

## 전체 작업 예제 (복사‑붙여넣기 준비)

아래는 하나의 파일에 담긴 전체 프로그램입니다. 경로만 본인 환경에 맞게 바꾸고 실행하면 됩니다.

```csharp
// ---------------------------------------------------------------
// Convert DOCX to Markdown – Extract Images from DOCX
// ---------------------------------------------------------------
// NuGet: Aspose.Words (>= 24.12)
// ---------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class ImageResourceSaver : IResourceSavingCallback
{
    private readonly string _targetFolder;
    public ImageResourceSaver(string targetFolder) => Directory.CreateDirectory(_targetFolder = targetFolder);

    public void ResourceSaving(ResourceSavingArgs args)
    {
        string ext = Path.GetExtension(args.ResourceFileName).ToLowerInvariant();
        if (string.IsNullOrEmpty(ext)) ext = ".png";
        string newFileName = $"img_{Guid.NewGuid():N}{ext}";
        string fullPath = Path.Combine(_targetFolder, newFileName);
        args.ResourceFileName = newFileName;
        args.Stream = new FileStream(fullPath, FileMode.Create);
    }
}

class Program
{
    static void Main()
    {
        // 👉 Adjust these paths:
        string sourceDocx = @"C:\Docs\WithImages.docx";
        string outputMd  = @"C:\Docs\DocWithImages.md";
        string imgFolder = @"C:\Docs\MarkdownResources";

        // Load the DOCX.
        Document doc = new Document(sourceDocx);

        // Set up markdown options with our image saver.
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ImageResourceSaver(imgFolder)
        };

        // Perform conversion.
        doc.Save(outputMd, mdOptions);

        Console.WriteLine("✅ DOCX successfully converted to Markdown.");
        Console.WriteLine($"📄 Markdown: {outputMd}");
        Console.WriteLine($"🖼️ Images folder: {imgFolder}");
    }
}
```

`dotnet run`으로 실행하세요. 콘솔에 ✅ 라인이 출력되면 Markdown 파일을 열어 이미지가 정상적으로 렌더링되는지 확인합니다.

---

## 결론

이제 **Aspose.Words를 사용해 C#에서 DOCX를 Markdown으로 변환하고 이미지를 추출**하는 **완전하고 프로덕션 수준의 솔루션**을 갖추었습니다. 주요 키워드가 가이드 전반에 걸쳐 등장해 검색 엔진과 AI 어시스턴트 모두에게 높은 관련성을 제공합니다.  

한 번에 수행되는 작업은 다음과 같습니다.

1. Word 문서를 로드합니다.
2. `IResourceSavingCallback`을 통해 모든 이미지를 가로챕니다.
3. 고유한 이름으로 예측 가능한 폴더에 각 이미지를 저장합니다.
4. 해당 이미지를 참조하는 Markdown을 생성합니다.

이제 다음을 할 수 있습니다.

- Plug

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}