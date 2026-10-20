---
category: general
date: 2026-05-04
description: Aspose.Words를 사용하여 DOCX를 Markdown으로 변환하면서 이미지를 저장하는 방법을 배웁니다. 이 가이드는
  Word에서 이미지를 추출하고 Word를 Markdown으로 저장하는 방법도 보여줍니다.
draft: false
keywords:
- how to save images
- convert docx to markdown
- extract images from word
- how to convert docx
- save word as markdown
language: ko
og_description: Aspose.Words를 사용하여 DOCX를 Markdown으로 변환하면서 이미지를 저장하는 방법. 전체 C# 코드가
  포함된 단계별 가이드.
og_title: 이미지 저장 방법 – Aspose.Words를 사용하여 DOCX를 마크다운으로 변환
tags:
- Aspose.Words
- C#
- Markdown conversion
title: 이미지 저장 방법 – Aspose.Words를 사용하여 DOCX를 Markdown으로 변환
url: /ko/net/programming-with-markdownsaveoptions/how-to-save-images-convert-docx-to-markdown-with-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 이미지 저장 방법 – Aspose.Words 로 DOCX 를 Markdown 으로 변환

Ever wondered **how to save images** when you need to turn a Word file into Markdown? You're not the only one. Many developers hit a wall when the conversion drops pictures into a mess of broken links, or worse—loses them entirely. The good news is that Aspose.Words gives you fine‑grained control, so you can extract images from Word, decide where they go, and still get clean Markdown output.

이 튜토리얼에서는 `.docx` 를 `.md` 로 변환하면서 전용 폴더에 **how to save images** 를 보여주는 완전하고 바로 실행 가능한 C# 예제를 단계별로 살펴보겠습니다. 진행하면서 **convert docx to markdown**, **extract images from word**, 그리고 **how to convert docx** 와 같은 주제와 **save word as markdown** 를 수행하면서 자산을 잃지 않는 방법에 대해서도 다룰 것입니다.

## 사전 요구 사항

- .NET 6.0 이상 (API는 .NET Framework 4.7+에서도 동일하게 작동합니다)
- 활성화된 Aspose.Words 라이선스 또는 무료 체험판 (무료 버전은 출력에 워터마크를 추가하지만 코드 동작은 동일합니다)
- 이미지를 포함하고 있는 Word 문서 (예: `DocWithImages.docx`)
- C# 프로젝트를 빌드할 수 있는 Visual Studio 2022 또는 기타 편집기

> **Pro tip:** 체험판을 사용 중이라도 이미지 저장 로직을 테스트할 수 있습니다; 단 최종 PDF/MD 에는 체험판 워터마크가 포함된다는 점을 기억하세요.

## 솔루션 개요

전체적인 흐름은 다음과 같습니다:

1. `Document` 로 소스 `.docx` 를 로드합니다.
2. `MarkdownSaveOptions` 객체를 생성하고 `IResourceSavingCallback` 을 연결합니다.
3. 콜백에서 각 이미지의 폴더와 파일명을 결정합니다.
4. 문서를 Markdown 으로 저장합니다; 콜백이 각 이미지를 디스크에 기록합니다.

이것이 변환 중 **how to save images** 의 핵심입니다. 동일한 패턴은 다른 리소스 유형(폰트, CSS 등)에도 적용할 수 있습니다.

## Step 1 – 이미지가 포함된 DOCX 로드

먼저 변환하려는 Word 파일을 가리키는 `Document` 인스턴스가 필요합니다. 특별한 점은 없으며, 단순히 생성자를 호출하면 됩니다.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Adjust the path to where your .docx lives
string sourcePath = @"C:\Docs\DocWithImages.docx";

Document sourceDoc = new Document(sourcePath);
```

> **Why this matters:** 문서를 로드하는 단계는 Aspose 가 Word XML 을 파싱하는 유일한 시점이므로, 누락된 폰트나 손상된 부분이 있으면 이미지 저장을 시작하기 전인 바로 예외가 발생합니다.

## Step 2 – Image‑Saving 콜백과 함께 MarkdownSaveOptions 설정

`MarkdownSaveOptions` 클래스는 `ResourceSavingCallback` 을 통해 저장 과정에 연결할 수 있게 해줍니다. 이 콜백은 Aspose 가 작성해야 하는 각 외부 리소스(이미지, CSS 등)에 대해 `ResourceSavingArgs` 객체를 전달받습니다.

```csharp
// Define where the Markdown file will be written
string markdownPath = @"C:\Docs\Doc.md";

// Create the options object and attach the callback
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // This is the heart of how to save images
    ResourceSavingCallback = new ImageSavingCallback()
};
```

### 콜백 구현

아래는 `ImageSavingCallback` 의 전체 구현입니다. 이 구현은 Markdown 파일 옆에 `Images` 하위 폴더를 만들고, 각 그림에 순차적인 이름(`img_0.png`, `img_1.jpg`, …)을 부여하며, 필요에 따라 이미지를 다른 곳(예: 클라우드 버킷)으로 스트리밍할 수도 있습니다.

```csharp
class ImageSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Only handle images; other resources (like CSS) are ignored here
        if (args.ResourceType != ResourceType.Image)
            return;

        // Build a folder called "Images" right next to the markdown file
        string markdownDir = Path.GetDirectoryName(args.DestinationFileName);
        string imagesFolder = Path.Combine(markdownDir, "Images");
        Directory.CreateDirectory(imagesFolder);

        // Compose a safe file name: img_<index>.<original extension>
        string newFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";
        args.FileName = Path.Combine(imagesFolder, newFileName);

        // If you wanted to push the image to a remote store, you could replace args.Stream here.
        // For now we just let Aspose write to the local file system.
    }
}
```

> **How this helps you:** `args.FileName` 을 커스터마이즈함으로써 **how to save images** 를 정확히 제어할 수 있습니다—단일 폴더, 날짜 기반 계층 구조, 혹은 데이터베이스 BLOB 등 어디에 저장할지 결정합니다. 콜백은 모든 이미지에 대해 실행되므로 나중에 Markdown 파일을 별도로 후처리할 필요가 없습니다.

## Step 3 – 문서를 Markdown 으로 저장

옵션과 콜백이 준비되었으니 실제 변환은 한 줄 코드로 수행됩니다.

```csharp
// Save the document; the callback will fire for each image automatically
sourceDoc.Save(markdownPath, markdownOptions);
```

When the line finishes, you’ll have:

- `Doc.md` – Word 콘텐츠의 Markdown 표현입니다.
- `Images\img_0.png`, `Images\img_1.jpg`, … – 원본 DOCX 에서 추출된 모든 그림 파일입니다.

## 전체, 바로 실행 가능한 예제

모든 코드를 합치면, 새 C# 프로젝트에 복사·붙여넣기 할 수 있는 독립형 콘솔 앱 예제가 아래에 있습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

namespace DocxToMarkdownDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -----------------------------------------------------------------
            // 1️⃣ Load the source DOCX that contains images
            // -----------------------------------------------------------------
            string sourcePath = @"C:\Docs\DocWithImages.docx";
            Document sourceDoc = new Document(sourcePath);

            // -----------------------------------------------------------------
            // 2️⃣ Prepare Markdown options with a custom image‑saving callback
            // -----------------------------------------------------------------
            string markdownPath = @"C:\Docs\Doc.md";
            MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new ImageSavingCallback()
            };

            // -----------------------------------------------------------------
            // 3️⃣ Perform the conversion – this is where we actually learn
            //     how to save images while converting docx to markdown
            // -----------------------------------------------------------------
            sourceDoc.Save(markdownPath, markdownOptions);

            Console.WriteLine("Conversion complete!");
            Console.WriteLine($"Markdown file: {markdownPath}");
            Console.WriteLine("Images folder: " + Path.Combine(Path.GetDirectoryName(markdownPath), "Images"));
        }
    }

    // -----------------------------------------------------------------
    // 4️⃣ Callback that decides where each image ends up
    // -----------------------------------------------------------------
    class ImageSavingCallback : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            if (args.ResourceType != ResourceType.Image)
                return;

            string markdownDir = Path.GetDirectoryName(args.DestinationFileName);
            string imagesFolder = Path.Combine(markdownDir, "Images");
            Directory.CreateDirectory(imagesFolder);

            string newFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";
            args.FileName = Path.Combine(imagesFolder, newFileName);

            // Optional: redirect the image stream elsewhere (e.g., cloud storage)
            // args.Stream = new MemoryStream(); // your custom stream here
        }
    }
}
```

### 예상 결과

프로그램을 실행한 후:

- 어떤 텍스트 편집기로 `C:\Docs\Doc.md` 를 열면 `![](Images/img_0.png)` 와 같은 Markdown 이미지 링크가 보일 것입니다.
- `Images` 폴더에는 추출된 각 그림이 순차적인 이름으로 저장됩니다.
- Markdown 파일은 로컬 이미지를 지원하는 모든 뷰어(VS Code 미리보기, GitHub 등)에서 올바르게 렌더링됩니다.

## 자주 묻는 질문 (FAQs)

### 다른 이미지 형식(SVG, TIFF)도 작동하나요?

예. `Path.GetExtension(args.FileName)` 은 원래 확장자를 그대로 유지하므로 SVG, TIFF, BMP, 심지어 EMF 도 변경 없이 저장됩니다. 단, 일부 Markdown 렌더러는 SVG 를 인라인으로 표시하지 못할 수 있으며, 이 경우 SVG 를 미리 PNG 로 변환해야 할 수도 있습니다.

### 이미지를 별도 파일이 아닌 Base64 로 임베드해야 하면 어떻게 하나요?

`ResourceSaving` 내부에서 물리 파일 쓰기를 메모리 스트림으로 교체하고 Markdown 링크를 수동으로 수정할 수 있습니다. Aspose 는 직접적인 “Base64 로 임베드” 옵션을 제공하지 않지만, 콜백을 통해 `args.Stream` 에 대한 전체 제어가 가능합니다.

### 내장 `ExportImages` 메서드와는 어떻게 다른가요?

`ExportImages` 는 모든 이미지를 폴더에 추출하지만 Markdown 은 생성하지 **않습니다**. 우리의 콜백은 두 작업을 결합하여 이미지 파일 이름이 `.md` 내부의 참조와 일치하도록 보장합니다. 이러한 정렬이 변환 중 **how to save images** 를 올바르게 수행하는 핵심입니다.

### 여러 DOCX 파일을 일괄 변환할 수 있나요?

물론 가능합니다. 핵심 로직을 `foreach (var file in Directory.GetFiles(..., "*.docx"))` 루프로 감싸고 출력 경로를 조정한 뒤 동일한 `ImageSavingCallback` 을 재사용하면 됩니다. 다만 문서마다 새로운 `MarkdownSaveOptions` 를 생성해야 하는데, 이는 `args.DestinationFileName` 이 각 반복마다 달라지기 때문입니다.

## 엣지 케이스 및 모범 사례

| Situation | What to Watch Out For | Recommended Fix |
|-----------|----------------------|-----------------|
| **대용량 DOCX (수백 MB)** | 로드 중 메모리 압박 | 부분 스트리밍 로드를 위해 `LoadOptions` 를 `LoadFormat.Docx` 로 설정하고 `LoadOptions.LoadFormat = LoadFormat.Docx` 를 사용하세요 |
| **이미지 이름 충돌** | 대상 폴더에 이미 `img_0.png` 가 존재하면 덮어쓸 수 있습니다 | GUID 를 추가하세요: `newFileName = $"img_{args.Index}_{Guid.NewGuid():N}{Path.GetExtension(args.FileName)}"` |
| **읽기 전용 출력 폴더** | 저장 시 `UnauthorizedAccessException` 예외 발생 | 프로세스가 적절한 권한으로 실행되는지 확인하거나 쓰기 가능한 경로를 선택하세요 |
| **이미지가 아닌 리소스(CSS, 폰트)** | 콜백이 이들도 수신합니다 | `if (args.ResourceType != ResourceType.Image) return;` 로 방어하세요(이미 예시됨) |
| **Unicode 파일 이름** | 일부 파일 시스템이 문자를 제대로 처리하지 못합니다 | 할당 전에 `Path.GetInvalidFileNameChars()` 를 사용해 `args.FileName` 을 정리하세요 |

## 다음에 살펴볼 수 있는 관련 주제

- **convert docx to markdown** 를 사용자 정의 헤딩 스타일과 함께 사용 (인라인 이미지를 위해 `MarkdownSaveOptions.ExportImagesAsBase64` 사용)
- **extract images from word** 를 `Document.GetChildNodes(NodeType.Shape,` 로 사용

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}