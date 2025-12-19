---
category: general
date: 2025-12-18
description: Word 문서를 Markdown으로 변환하면서 이미지를 이름 바꾸는 방법을 배우고, docx를 Markdown으로 변환하고
  효율적으로 내보내는 단계별 안내를 제공합니다.
draft: false
keywords:
- how to rename images
- convert word to markdown
- export docx to markdown
- how to convert docx
- how to extract images
language: ko
og_description: Word를 Markdown으로 변환하는 과정에서 이미지를 이름 바꾸는 방법을 알아보고, docx를 Markdown으로
  내보내고 이미지를 추출하는 전체 코드 예제를 확인하세요.
og_title: 이미지 이름 바꾸는 방법 – Word에서 Markdown으로 변환 가이드
tags:
- Aspose.Words
- C#
- Markdown conversion
title: Word를 Markdown으로 변환할 때 이미지 이름 바꾸는 방법 – 완전 가이드
url: /ko/java/document-conversion-and-export/how-to-rename-images-when-converting-word-to-markdown-comple/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 이미지 이름 바꾸기 – Word를 Markdown으로 변환하는 전체 튜토리얼

Word .docx를 깔끔한 Markdown으로 변환할 때 **이미지 이름을 바꾸는 방법**을 궁금해 본 적 있나요? 당신만 그런 것이 아닙니다. 많은 개발자들이 기본 이미지 이름이 GUID의 뒤죽박죽된 문자열이 되어 최종 Markdown을 읽고 유지보수하기 어렵게 되는 문제에 부딪힙니다.  

이 가이드에서는 **이미지 이름을 바꾸는 방법**뿐만 아니라 **Word를 Markdown으로 변환하는 방법**, **DOCX를 Markdown으로 내보내는 방법**, 그리고 별도로 처리하기 위한 **이미지 추출 방법**까지 보여주는 완전하고 실행 가능한 솔루션을 단계별로 안내합니다. 끝까지 따라오면 모든 작업을 수행하는 단일 C# 스크립트를 얻게 됩니다—추가 도구 없이, 수동으로 이름을 바꾸지 않아도 됩니다.

> **빠른 미리보기:** Aspose.Words for .NET를 사용하고 `MarkdownSaveOptions` 콜백을 설정하여 각 삽입된 이미지를 고유하고 사람이 읽기 쉬운 파일명으로 바꿉니다. 모든 코드는 복사‑붙여넣기 할 준비가 되어 있습니다.

---

## 배울 내용

- **이미지 이름을 바꾸는 이유** – 가독성, SEO, 버전 관리.
- **Aspose.Words를 사용한 Word를 Markdown으로 변환하는 방법**.
- **맞춤형 리소스 처리를 통한 DOCX를 Markdown으로 내보내는 방법**.
- **DOCX에서 이미지를 추출하여 원하는 폴더에 저장하는 방법**.
- 실용적인 팁, 엣지 케이스 처리, 그리고 완전한 실행 예제.

**Prerequisites**

- .NET 6.0 이상 (코드는 .NET Core와 .NET Framework 모두에서 동작합니다).
- Aspose.Words for .NET 라이브러리 (무료 체험판 또는 정식 라이선스).
- 기본 C# 지식 – `Console.WriteLine`을 쓸 수만 하면 충분합니다.

---

## How to Rename Images During Word to Markdown Conversion

이것이 튜토리얼의 핵심입니다. `MarkdownSaveOptions.ResourceSavingCallback`은 모든 삽입 리소스(이미지, 오디오 등)에 대한 후크를 제공합니다. 콜백 내부에서 새 파일명을 생성하고 스트림을 디스크에 쓰며, Aspose에 새 이름을 알려줍니다.

![이미지 이름 바꾸기 예시 – 이름이 바뀐 이미지 파일의 스크린샷](/images/how-to-rename-images-example.png "변환 중 이미지 이름 바꾸기")

### 단계 1: Aspose.Words 설치

프로젝트에 NuGet 패키지를 추가합니다:

```bash
dotnet add package Aspose.Words
```

또는 Package Manager Console을 통해:

```powershell
Install-Package Aspose.Words
```

### 단계 2: 이름 바꾸기 콜백이 포함된 MarkdownSaveOptions 준비

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Define the folder where images will be saved
string imageFolder = Path.Combine(Environment.CurrentDirectory, "myImages");
Directory.CreateDirectory(imageFolder);

// Create Markdown save options
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();

// Set up the callback that runs for each embedded resource
mdOptions.ResourceSavingCallback = (resource, stream) =>
{
    // Only act on images – other resources (like audio) are left untouched
    if (resource.Type == ResourceType.Image)
    {
        // Generate a friendly, unique name: img_<guid>.png
        string newFileName = $"img_{Guid.NewGuid():N}.png";

        // Build the full path and copy the stream
        string fullPath = Path.Combine(imageFolder, newFileName);
        using (FileStream file = new FileStream(fullPath, FileMode.Create, FileAccess.Write))
        {
            stream.CopyTo(file);
        }

        // Tell Aspose the new filename so the Markdown reference is correct
        resource.FileName = newFileName;
    }
};
```

**이것이 동작하는 이유:**

- 콜백은 `ResourceSavingArgs` 객체(`resource`)와 `Stream`을 받습니다.  
- `resource.Type == ResourceType.Image`를 확인함으로써 이미지가 아닌 리소스를 건드리는 것을 방지합니다.  
- `Guid.NewGuid():N`은 대시 없이 32자 길이의 16진수 문자열을 제공해 고유성을 보장합니다.  
- `resource.FileName`을 업데이트하면 Markdown 이미지 링크(`![](img_…png)`)가 새 파일명으로 바뀝니다.

### 단계 3: DOCX 로드 후 Markdown으로 저장

```csharp
// Path to the source Word document
string docxPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document
Document doc = new Document(docxPath);

// Export to Markdown, applying our custom resource handling
string markdownPath = Path.Combine(Environment.CurrentDirectory, "output.md");
doc.Save(markdownPath, mdOptions);

Console.WriteLine($"Conversion complete! Markdown saved to {markdownPath}");
Console.WriteLine($"Images saved to {imageFolder}");
```

이것으로 끝입니다. 프로그램을 실행하면 다음과 같은 결과가 생성됩니다:

- `output.md` – `![](img_1a2b3c4d5e6f7g8h9i0j1k2l3m4n5o6p.png)`와 같은 이미지 참조가 포함된 깔끔한 Markdown.  
- `myImages` 폴더에 친숙한 이름으로 저장된 각 이미지 파일이 들어 있습니다.

---

## Word를 Markdown으로 변환 – 전체 예제

단일 파일 스크립트를 선호한다면, 아래 코드를 `Program.cs`에 복사하고 실행하세요:

```csharp
// Program.cs
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // ---------- Configuration ----------
        string inputDocx = "YOUR_DIRECTORY/input.docx";
        string outputMd = "YOUR_DIRECTORY/output.md";
        string imagesDir = Path.Combine("YOUR_DIRECTORY", "myImages");
        Directory.CreateDirectory(imagesDir);

        // ---------- Step 1: Set up Markdown options ----------
        var mdOptions = new MarkdownSaveOptions();
        mdOptions.ResourceSavingCallback = (resource, stream) =>
        {
            if (resource.Type == ResourceType.Image)
            {
                string uniqueName = $"img_{Guid.NewGuid():N}.png";
                string destPath = Path.Combine(imagesDir, uniqueName);
                using (var file = new FileStream(destPath, FileMode.Create, FileAccess.Write))
                    stream.CopyTo(file);
                resource.FileName = uniqueName;
            }
        };

        // ---------- Step 2: Load DOCX ----------
        var doc = new Document(inputDocx);

        // ---------- Step 3: Save as Markdown ----------
        doc.Save(outputMd, mdOptions);

        Console.WriteLine($"✅ Done! Markdown at {outputMd}");
        Console.WriteLine($"🖼️ Images saved in {imagesDir}");
    }
}
```

**각 블록 설명**

| 블록 | 목적 |
|-------|---------|
| **구성** | 경로를 한 곳에 모아 한 번만 수정하면 됩니다. |
| **단계 1** | `MarkdownSaveOptions`와 이름 바꾸기 콜백을 생성합니다. |
| **단계 2** | `.docx`를 Aspose `Document` 객체에 로드합니다. |
| **단계 3** | 맞춤 옵션으로 `Save`를 호출해 Markdown과 이름이 바뀐 이미지를 모두 저장합니다. |

다음 명령으로 실행:

```bash
dotnet run
```

두 개의 콘솔 메시지가 성공을 확인하는 것을 볼 수 있습니다.

---

## DOCX를 Markdown으로 내보내기 – 이 접근법이 수동 도구보다 뛰어난 이유

- **자동화** – Word를 열고 복사‑붙여넣기하거나 파일을 수동으로 이름 바꾸는 작업이 필요 없습니다.  
- **일관성** – 모든 이미지가 예측 가능하고 고유한 이름을 갖게 되어 버전 관리에 유리합니다(Git이 GUID이 바뀐 것만으로 파일이 변경된 것으로 인식하지 않음).  
- **확장성** – 수십 개에서 수백 개의 이미지가 있는 문서에서도 동작하며, 콜백이 각 리소스마다 자동으로 호출됩니다.  
- **이식성** – 생성된 Markdown은 이미지 링크가 상대 경로이며 깔끔하기 때문에 모든 정적 사이트 생성기(Jekyll, Hugo, MkDocs)에서 동작합니다.

---

## DOCX 파일에서 이미지 추출하기 (보너스)

때때로 Markdown 파일이 아니라 원시 이미지만 필요할 때가 있습니다. 동일한 콜백을 재사용하거나 Aspose의 `Document` API를 직접 사용할 수 있습니다:

```csharp
using Aspose.Words;
using System.IO;

// Load the document
Document doc = new Document("YOUR_DIRECTORY/input.docx");

// Iterate over all shapes (including inline images)
int imgCount = 0;
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.HasImage)
    {
        imgCount++;
        string imgPath = Path.Combine("YOUR_DIRECTORY/extractedImages", $"extracted_{imgCount}.png");
        shape.ImageData.Save(imgPath);
    }
}
Console.WriteLine($"{imgCount} images extracted.");
```

**핵심 포인트**

- `NodeType.Shape`은 플로팅 이미지와 인라인 이미지를 모두 포착합니다.  
- `shape.ImageData.Save`는 바이너리 이미지를 직접 디스크에 저장합니다.  
- 두 출력이 모두 필요하면 이 스니펫을 Markdown 변환과 결합할 수 있습니다.

---

## 실용적인 팁 및 흔히 발생하는 함정

- **이름 충돌:** GUID를 사용하면 충돌이 사실상 없지만, 사람이 읽을 수 있는 이름(`chapter1_figure2.png` 등)이 필요하면 `resource.Name`이나 주변 문단 텍스트에서 이름을 유도할 수 있습니다.  
- **대용량 문서:** 스트림이 바로 디스크에 복사됩니다; 매우 큰 파일의 경우 버퍼링하거나 임시 위치에 먼저 쓰는 것을 고려하세요.  
- **PNG가 아닌 이미지:** 위 콜백은 `.png` 확장자를 강제합니다. 원본 이미지가 JPEG인 경우 원래 형식을 유지하려면 `Path.GetExtension(resource.FileName)` 또는 `resource.ContentType`을 사용하세요.  
- **성능:** 콜백은 동기적으로 실행됩니다. 여러 문서를 병렬로 처리한다면 변환을 `Task.Run`으로 감싸거나 스레드 풀을 사용해 UI 차단을 피하세요.  
- **라이선스:** Aspose.Words는 평가 모드에서도 동작하지만 출력에 워터마크가 추가됩니다. 깨끗한 결과를 원한다면 라이선스 파일(`Aspose.Words.lic`)을 설치하세요.

---

## 결론

Word 문서를 Markdown으로 변환할 때 **이미지 이름을 바꾸는 방법**을 다루었고, 전체 **Word를 Markdown으로 변환** 워크플로우를 보여주었으며, 맞춤형 리소스 처리를 통한 **DOCX를 Markdown으로 내보내는 방법**을 시연하고, DOCX 파일에서 **이미지를 추출하는 방법**까지 설명했습니다. 코드는 독립적이며 최신식이고, 프로덕션에 바로 사용할 수 있습니다.

한 번 실행해 보세요—`.docx` 파일을 폴더에 넣고 스크립트를 실행하면 깔끔한 Markdown과 정돈된 이미지 파일이 생성됩니다. 이후 Markdown을 정적 사이트 생성기에 넣거나, 이미지를 Git에 커밋하거나, 문서 파이프라인에 출력물을 전달할 수 있습니다.

엣지 케이스에 대한 질문이 있거나 이를 ASP.NET Core 서비스에 통합하고 싶다면 댓글을 남겨 주세요. 함께 해당 시나리오를 살펴보겠습니다. 변환을 즐기세요!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}