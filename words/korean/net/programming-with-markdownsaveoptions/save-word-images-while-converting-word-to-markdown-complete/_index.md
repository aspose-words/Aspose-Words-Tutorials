---
category: general
date: 2026-02-20
description: C#에서 워드 이미지를 저장하고 워드를 마크다운으로 변환하는 방법을 배워보세요. 이 단계별 가이드는 워드에서 이미지를 추출하고
  이미지를 포함한 마크다운을 내보내는 방법도 보여줍니다.
draft: false
keywords:
- save word images
- convert word to markdown
- extract images from word
- convert docx to md
- export markdown with images
language: ko
og_description: 이 가이드에서는 Aspose.Words를 사용하여 워드 이미지 저장 및 워드를 마크다운으로 변환하는 방법을 보여줍니다.
  이미지를 포함한 마크다운을 내보내는 단계를 따라하세요.
og_title: Word를 Markdown으로 변환하면서 Word 이미지 저장 – 전체 C# 튜토리얼
tags:
- Aspose.Words
- C#
- Markdown
title: Word를 Markdown으로 변환하면서 워드 이미지 저장 – 완전 C# 가이드
url: /ko/net/programming-with-markdownsaveoptions/save-word-images-while-converting-word-to-markdown-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word를 Markdown으로 변환하면서 이미지 저장하기 – 완전한 C# 가이드

Word 문서를 Markdown으로 변환할 때 **워드 이미지 저장**이 필요했던 적이 있나요? 당신만 그런 것이 아닙니다—개발자들은 이미지가 사라지는 문제에 자주 직면합니다, 간단한 `convert docx to md` 후에 말이죠. 이 튜토리얼에서는 **워드 이미지 저장**, **워드를 Markdown으로 변환**을 깔끔하고 프로덕션 수준으로 수행하는 방법을 단계별로 안내하고, 모든 그림이 표시되는 Markdown 파일을 얻는 과정을 보여드립니다.

`input.docx` 라는 사용자 매뉴얼이 있고 이를 정적 사이트에 게시하고 싶다고 가정해 보세요. 텍스트는 Markdown 형태가 필요하지만, 스크린샷, 다이어그램, 로고 등도 정확히 제 위치에 나타나야 합니다. 바로 이 문제를 해결합니다—외부 도구 없이, 수동 복사‑붙여넣기 없이, C# 몇 줄과 Aspose.Words만으로 가능합니다.

이 가이드를 마치면 다음을 할 수 있게 됩니다:

* Aspose.Words 로 `.docx` 파일을 로드합니다.  
* `MarkdownSaveOptions` 를 구성하여 변환 시 **워드에서 이미지 추출**이 이루어지도록 합니다.  
* 각 이미지를 고유한 이름으로 지정된 폴더에 저장하는 콜백을 구현합니다.  
* 생성된 `.md` 파일이 이미지를 올바르게 참조하는지 확인합니다, 즉 **이미지가 포함된 Markdown 내보내기**에 성공했는지 검증합니다.

> **Prerequisites** – .NET 6+ (또는 .NET Framework 4.6+), 유효한 Aspose.Words 라이선스(무료 평가판 사용 가능), 그리고 C#에 대한 기본 이해가 필요합니다. Aspose를 처음 사용한다면 걱정하지 마세요; API는 직관적이며 아래 코드는 완전하게 독립적입니다.

---

## Word를 Markdown으로 변환하면서 워드 이미지를 저장하는 방법

첫 번째 단계는 변환 과정 중 **워드 이미지 저장**을 수행하는 것입니다. Aspose.Words 는 외부 리소스(그림, 차트, SVG 등)마다 호출되는 `ResourceSavingCallback` 을 제공합니다. 자체 구현을 연결하면 각 이미지가 디스크에 저장되는 위치를 정확히 지정할 수 있습니다.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Load the source Word document
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Configure Markdown save options and attach a callback that will handle external resources
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // This callback will be invoked for every image, letting us control the file name and folder
    ResourceSavingCallback = new MyResourceCallback()
};

// Save the document as Markdown; the callback will store images in a custom folder
document.Save("YOUR_DIRECTORY/output.md", markdownOptions);

// -----------------------------------------------------------------
// Callback implementation – stores each image in a dedicated folder with a unique name
class MyResourceCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Define the folder where resources will be saved
        string resourceFolder = "YOUR_DIRECTORY/MarkdownResources";
        Directory.CreateDirectory(resourceFolder);

        // Generate a unique file name while preserving the original extension
        string uniqueFileName = $"{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";

        // Tell Aspose.Words where to write the resource
        args.ResourceFileName = Path.Combine(resourceFolder, uniqueFileName);
    }
}
```

이것이 전체 솔루션입니다—실행하면 `output.md` 와 이미지 파일이 가득한 `MarkdownResources` 폴더가 생성됩니다. Markdown에는 `![](MarkdownResources/7f3c2a1e-...png)` 와 같은 링크가 포함되며, 이는 **워드 이미지 저장**과 **이미지가 포함된 Markdown 내보내기**가 한 번에 성공했음을 의미합니다.

---

## docx를 md로 변환하기 위한 Markdown 옵션 구성

콜백을 왜 사용해야 할까요? 기본적으로 Aspose.Words 는 이미지를 Base‑64 문자열로 Markdown에 삽입합니다. 이는 파일 크기를 늘리고 버전 관리가 복잡해집니다. `ResourceSavingCallback` 을 설정하면 라이브러리가 **docx를 md** 로 변환하면서 각 그림을 인라인 대신 디스크에 저장하도록 지시합니다.

### 조정할 수 있는 주요 속성

| Property | Typical value | When to change |
|----------|---------------|----------------|
| `ExportImagesAsBase64` | `false` (default) | 이미지를 별도 파일로 유지합니다. |
| `ImagesFolder` | `null` (ignored when callback is used) | 동적 이름 지정이 필요 없으면 정적 폴더를 설정할 수 있습니다. |
| `ExportHeadersFooters` | `true` | 이미지가 포함될 수 있는 머리글/바닥글 내용을 보존합니다. |
| `EncodeUrls` | `true` | 경로에 공백이나 비ASCII 문자가 포함된 경우 필요합니다. |

> **Pro tip:** 여러 언어로 문서를 생성한다면 `resourceFolder` 에 언어 코드를 추가하세요(예: `MarkdownResources/en`). 이렇게 하면 이미지 경로가 깔끔하게 유지됩니다.

---

## 워드에서 이미지를 추출하기 위한 리소스 콜백 구현

이전 코드 블록의 콜백이 핵심 작업을 수행하지만, 조금 더 자세히 살펴보겠습니다. `IResourceSavingCallback` 은 외부 리소스마다 `ResourceSavingArgs` 객체를 전달받습니다. 가장 중요한 필드는 다음과 같습니다:

* `ResourceFileName` – 파일이 기록될 경로.  
* `ResourceFileExtension` – 원본 확장자 (`.png`, `.jpg` 등).  
* `ResourceType` – 이미지, 차트 등 리소스 유형을 알려줍니다.

이미지에만 관심 있다면 비이미지 리소스를 필터링할 수 있습니다:

```csharp
public void ResourceSaving(ResourceSavingArgs args)
{
    // Skip non‑image resources – we only want to save pictures
    if (args.ResourceType != ResourceType.Image)
        return;

    string resourceFolder = "YOUR_DIRECTORY/MarkdownResources";
    Directory.CreateDirectory(resourceFolder);

    string uniqueFileName = $"{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";
    args.ResourceFileName = Path.Combine(resourceFolder, uniqueFileName);
}
```

### 예외 상황 처리

1. **Duplicate images** – 동일한 그림이 여러 번 나타나면 콜백은 각 발생마다 새 파일을 씁니다. 중복 제거를 원한다면 이미지 바이트의 해시를 기존 파일 이름에 매핑하는 `Dictionary<string, string>` 을 유지하세요.  
2. **Unsupported formats** – Aspose.Words 는 PNG, JPEG, GIF, BMP, TIFF 를 내보낼 수 있습니다. 이 외 포맷을 만나면 직접 변환해야 합니다(예: `System.Drawing` 사용).  
3. **Large documents** – 대용량 PDF 또는 DOCX 의 경우 메모리 고갈을 방지하기 위해 스트리밍 출력을 고려하세요. `MarkdownSaveOptions` 는 `SaveOptions.UseMemoryCache = false` 를 지원합니다.

---

## 문서를 저장하고 이미지가 포함된 Markdown 내보내기 확인

코드를 실행한 뒤 `output.md` 를 텍스트 편집기로 열어보세요. 다음과 같은 내용이 보일 것입니다:

```markdown
# Chapter 1

Here is a diagram:

![](MarkdownResources/2c7f9a3e-9b4d-4f6a-8d12-5e9f2c7a1b3c.png)

And another screenshot:

![](MarkdownResources/7a1d4e2f-3c9b-4a5d-9e8f-6b2c3d4e5f6a.jpg)
```

이미지 링크가 올바르게 보이면, VS Code 프리뷰, GitHub, 혹은 정적 사이트 생성기 등에서 Markdown 파일을 열어보세요. 그림이 자동으로 렌더링되어 **워드 이미지 저장**과 **이미지가 포함된 Markdown 내보내기**에 성공했음을 확인할 수 있습니다.

### 빠른 검증 스크립트

검사를 자동화하고 싶다면, 아래 스니펫이 생성된 Markdown에서 누락된 파일을 스캔합니다:

```csharp
using System;
using System.IO;
using System.Text.RegularExpressions;

string mdPath = "YOUR_DIRECTORY/output.md";
string mdFolder = Path.GetDirectoryName(mdPath)!;
string[] lines = File.ReadAllLines(mdPath);

foreach (var line in lines)
{
    var match = Regex.Match(line, @"!\[.*?\]\((.+?)\)");
    if (match.Success)
    {
        string imgPath = Path.Combine(mdFolder, match.Groups[1].Value);
        if (!File.Exists(imgPath))
            Console.WriteLine($"Missing image: {imgPath}");
    }
}
Console.WriteLine("Verification complete.");
```

변환 후 실행하면 누락된 이미지가 콘솔에 출력됩니다.

---

## 워드를 Markdown으로 변환할 때 흔히 발생하는 함정 및 모범 사례

| Pitfall | Why it hurts | Fix |
|---------|--------------|-----|
| **Images end up with long GUID names** | 소스 컨트롤에서 읽기 어렵습니다. | `args.ResourceFileName` 등 원본 이름을 기반으로 의미 있는 파일명으로 폴더를 후처리하세요. |
| **Relative paths break after moving the Markdown file** | `![]()` 링크가 `.md` 위치를 기준으로 상대 경로이기 때문입니다. | 이미지 폴더를 Markdown 파일 옆에 두거나 정적 사이트 설정에서 일관된 기본 경로를 사용하세요. |
| **Missing images when `ExportImagesAsBase64` is `true`** | 이미지가 인라인되므로 콜백이 호출되지 않습니다. | `ExportImagesAsBase64 = false` 로 설정하세요(기본값). |
| **Large documents cause `OutOfMemoryException`** | Aspose 가 전체 문서를 RAM에 로드하기 때문입니다. | `LoadOptions` 에 `LoadFormat.Docx` 를 지정하고 가능한 경우 `MemoryOptimization` 플래그를 사용하세요. |
| **Non‑ASCII file names break on some platforms** | URL 인코딩이 실패할 수 있습니다. | ASCII 문자만 사용하거나 `EncodeUrls = true` 로 설정하세요. |

---

## 정리

우리는 Aspose.Words 를 사용해 **워드 이미지 저장**하면서 **워드를 Markdown으로 변환**하는 데 필요한 모든 것을 다루었습니다. 핵심 아이디어는 간단합니다: `ResourceSavingCallback` 을 연결하고, 제어 가능한 폴더를 지정한 뒤 라이브러리가 나머지를 처리하도록 하면 됩니다. 실행 후에는 깔끔한 `.md` 파일과 정돈된 이미지 자산이 생성되어 게시나 버전 관리에 최적화됩니다.

다른 목적(예: 갤러리 생성)으로 **워드에서 이미지 추출**이 필요하다면 Markdown 저장 단계를 제외하고 콜백 코드를 재사용하면 됩니다. 마찬가지로 **docx를 md** 로 변환하는 배치 작업에서도 동일한 패턴을 적용해 디렉터리의 `.docx` 파일들을 순회하며 로직을 호출하면 됩니다.

**Next steps** you might explore:

* ASP.NET Core API에 변환 로직을 통합하여 사용자가 DOCX를 업로드하고 다운로드 가능한 Markdown 패키지를 받을 수 있게 합니다.  
* 테이블 지원 및 

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}