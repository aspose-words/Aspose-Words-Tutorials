---
category: general
date: 2025-12-23
description: 손상된 docx 파일을 복구하는 방법, 복구 모드를 사용하는 방법, 방정식을 LaTeX로 내보내는 방법, 그리고 C#에서 고유한
  이미지 이름을 생성하는 방법을 배웁니다. 단계별 코드와 설명이 포함되어 있습니다.
draft: false
keywords:
- recover corrupted docx
- how to use recovery mode
- export equations to latex
- generate unique image names
language: ko
og_description: 손상된 docx 파일을 복구하고, 복구 모드를 사용하며, 수식을 LaTeX로 내보내고, Aspose.Words를 사용하여
  C#에서 고유한 이미지 이름을 생성합니다.
og_title: 손상된 docx 복구 – 완전한 C# 튜토리얼
tags:
- Aspose.Words
- C#
- Document Recovery
title: 손상된 docx 복구 – 복구에 대한 완전 가이드, 수학을 LaTeX로 내보내기 및 고유 이미지 이름 생성
url: /ko/net/programming-with-officemath/recover-corrupted-docx-full-guide-to-repair-export-math-to-l/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 손상된 docx 복구 – 복구 전체 가이드, 수학을 LaTeX로 내보내기 및 고유 이미지 이름 생성

손상되어 로드되지 않는 **.docx** 파일을 열어본 적이 있나요? 당신만 그런 것이 아닙니다. 많은 실제 프로젝트에서 손상된 Word 파일은 전체 워크플로우를 중단시킬 수 있지만, 좋은 소식은 **손상된 docx** 파일을 프로그래밍 방식으로 **복구**할 수 있다는 것입니다.  

이 튜토리얼에서는 **손상된 docx 복구** 단계, **복구 모드 사용 방법** 소개, **수식을 LaTeX로 내보내는 방법** 시연, 그리고 Markdown으로 저장할 때 **고유 이미지 이름 생성** 방법을 차례대로 설명합니다. 마지막까지 따라오면 모든 작업을 한 번에 처리할 수 있는 실행 가능한 C# 프로그램을 얻게 됩니다.

## 사전 요구 사항

- .NET 6 이상 (코드는 .NET Framework 4.6+에서도 동작합니다).  
- Aspose.Words for .NET (무료 체험판 또는 정식 라이선스). NuGet을 통해 설치:

```bash
dotnet add package Aspose.Words
```

- C# 및 파일 I/O에 대한 기본 지식.  
- 테스트용 `corrupt.docx` 파일 (유효한 파일을 잘라서 손상시켜도 됩니다).

> **Pro tip:** 시작하기 전에 원본 파일을 백업해 두세요—복구 작업은 원본을 덮어쓸 경우에만 파괴적입니다.

## Step 1 – 복구 모드를 사용해 손상된 DOCX 복구

먼저 Aspose.Words에 들어오는 파일이 손상될 가능성이 있음을 알려야 합니다. 여기서 **복구 모드 사용 방법**이 중요한 역할을 합니다.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // Step 1: Load a possibly corrupted document using recovery mode
        // -----------------------------------------------------------------
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc;

        try
        {
            doc = new Document(@"YOUR_DIRECTORY\corrupt.docx", loadOptions);
            Console.WriteLine("✅ Document loaded successfully – recovery mode applied.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
            return;
        }

        // ---------------------------------------------------------------
        // Subsequent steps go here...
        // ---------------------------------------------------------------
    }
}
```

**왜 중요한가:**  
`RecoveryMode.Recover`를 활성화하면 Aspose.Words가 내부 문서 트리를 재구성하려 시도하면서 읽을 수 없는 부분은 건너뛰고 가능한 한 많은 콘텐츠를 보존합니다. 이 옵션이 없으면 `Document` 생성자가 예외를 발생시켜 파일을 복구할 기회를 잃게 됩니다.

> **파일이 복구 불가능한 경우는?**  
> 라이브러리는 여전히 `Document` 객체를 반환하지만 일부 노드가 누락될 수 있습니다. `doc.GetChildNodes(NodeType.Any, true).Count`를 확인하여 살아남은 요소 수를 파악하세요.

## Step 2 – Markdown 저장 시 Office Math 수식을 LaTeX로 내보내기

많은 기술 문서에 Office Math로 작성된 수식이 포함됩니다. 이러한 수식을 LaTeX 형태로 필요하다면(예: 과학 블로그에 게시) Aspose.Words에 변환을 요청할 수 있습니다.

```csharp
        // -----------------------------------------------------------------
        // Step 2: Export Office Math equations to LaTeX in a Markdown file
        // -----------------------------------------------------------------
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };

        string markdownPath = @"YOUR_DIRECTORY\out.md";
        doc.Save(markdownPath, markdownMathOptions);
        Console.WriteLine($"✅ Markdown with LaTeX equations saved to: {markdownPath}");
```

**작동 원리:**  
`OfficeMathExportMode.LaTeX`는 저장 시 각 `OfficeMath` 노드를 LaTeX 표현식으로 교체하고, 인라인은 `$…$`, 디스플레이는 `$$…$$`로 감쌉니다. 이렇게 생성된 Markdown 파일은 Hugo나 Jekyll 같은 정적 사이트 생성기에 바로 사용할 수 있습니다.

> **예외 상황:** 원본 문서에 복잡한 수식 객체(예: 행렬)가 포함된 경우 LaTeX 변환이 여러 줄 출력으로 생성될 수 있습니다. 생성된 `.md` 파일을 검토하여 원하는 형식인지 확인하세요.

## Step 3 – PDF 저장 시 플로팅 도형 태그 제어

동일 문서의 PDF 버전이 필요하지만, 플로팅 도형(그림, 텍스트 상자)의 접근성 태그도 신경 써야 할 때가 있습니다. `ExportFloatingShapesAsInlineTag` 플래그를 사용하면 이를 제어할 수 있습니다.

```csharp
        // -----------------------------------------------------------------
        // Step 3: Save as PDF with custom floating‑shape tagging
        // -----------------------------------------------------------------
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true // true → <Figure>, false → <Div>
        };

        string pdfPath = @"YOUR_DIRECTORY\out.pdf";
        doc.Save(pdfPath, pdfOptions);
        Console.WriteLine($"✅ PDF saved with inline tags to: {pdfPath}");
```

**이 플래그를 전환하는 이유:**  
- `true` → 플로팅 도형이 `<Figure>` 태그로 변환되어 많은 화면 판독기가 캡션이 있는 별도 이미지로 인식합니다.  
- `false` → 도형이 일반 `<Div>` 태그로 감싸져 보조 기술에 무시될 수 있습니다. 접근성 요구 사항에 맞게 선택하세요.

## Step 4 – 사용자 정의 이미지 처리와 고유 이미지 이름 생성으로 Markdown 내보내기

Word 문서를 Markdown으로 저장하면 모든 삽입 이미지가 디스크에 기록됩니다. 기본적으로 원본 파일 이름을 그대로 사용하므로 같은 폴더에 여러 문서를 처리할 경우 충돌이 발생할 수 있습니다. 저장 과정에 후크를 걸어 **고유 이미지 이름을 자동으로 생성**하도록 해봅시다.

```csharp
        // -----------------------------------------------------------------
        // Step 4: Export to Markdown with custom image naming
        // -----------------------------------------------------------------
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = resourceInfo =>
            {
                // Create a sub‑folder for markdown images if it doesn't exist
                string imageFolder = @"YOUR_DIRECTORY\md_images";
                Directory.CreateDirectory(imageFolder);

                // Build a GUID‑based filename preserving the original extension
                string uniqueName = Guid.NewGuid().ToString() + Path.GetExtension(resourceInfo.Name);
                return Path.Combine(imageFolder, uniqueName);
            }
        };

        string markdownPath2 = @"YOUR_DIRECTORY\out2.md";
        doc.Save(markdownPath2, markdownImageOptions);
        Console.WriteLine($"✅ Markdown with uniquely named images saved to: {markdownPath2}");
```

**내부 동작 설명:**  
`ResourceSavingCallback`은 저장 중 외부 리소스(이미지, SVG 등)마다 호출됩니다. 전체 경로를 반환하면 파일이 저장되는 위치와 이름을 직접 지정할 수 있습니다. GUID를 사용하면 **고유 이미지 이름을 생성**할 수 있어 별도 관리가 필요 없습니다.

> **팁:** 이미지 alt 텍스트 기반 등 결정적인 네이밍이 필요하면 `Guid.NewGuid()` 대신 `resourceInfo.Name`의 해시값을 사용하세요.

## 전체 작동 예제

모든 내용을 종합한 완전한 프로그램을 아래에 제공합니다. 콘솔 앱에 복사·붙여넣기 하면 바로 실행할 수 있습니다.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -------------------------------------------------------------
        // Load the possibly corrupted document (Recovery Mode)
        // -------------------------------------------------------------
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc;

        try
        {
            doc = new Document(@"YOUR_DIRECTORY\corrupt.docx", loadOptions);
            Console.WriteLine("✅ Document loaded with recovery mode.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Unable to load document: {ex.Message}");
            return;
        }

        // -------------------------------------------------------------
        // Export equations to LaTeX in Markdown
        // -------------------------------------------------------------
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
        string mdMathPath = @"YOUR_DIRECTORY\out.md";
        doc.Save(mdMathPath, markdownMathOptions);
        Console.WriteLine($"✅ Markdown (LaTeX) saved: {mdMathPath}");

        // -------------------------------------------------------------
        // Save as PDF with inline floating‑shape tags
        // -------------------------------------------------------------
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true
        };
        string pdfPath = @"YOUR_DIRECTORY\out.pdf";
        doc.Save(pdfPath, pdfOptions);
        Console.WriteLine($"✅ PDF saved: {pdfPath}");

        // -------------------------------------------------------------
        // Export Markdown with unique image names
        // -------------------------------------------------------------
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = resourceInfo =>
            {
                string imgFolder = @"YOUR_DIRECTORY\md_images";
                Directory.CreateDirectory(imgFolder);
                string uniqueFile = Guid.NewGuid() + Path.GetExtension(resourceInfo.Name);
                return Path.Combine(imgFolder, uniqueFile);
            }
        };
        string mdImgPath = @"YOUR_DIRECTORY\out2.md";
        doc.Save(mdImgPath, markdownImageOptions);
        Console.WriteLine($"✅ Markdown with unique images saved: {mdImgPath}");
    }
}
```

### 예상 출력

프로그램을 실행하면 다음과 유사한 콘솔 메시지가 표시됩니다.

```
✅ Document loaded with recovery mode.
✅ Markdown (LaTeX) saved: YOUR_DIRECTORY\out.md
✅ PDF saved: YOUR_DIRECTORY\out.pdf
✅ Markdown with unique images saved: YOUR_DIRECTORY\out2.md
```

세 개의 파일이 생성됩니다:

| 파일 | 용도 |
|------|------|
| `out.md` | 모든 Office Math 수식이 LaTeX(`$…$` 또는 `$$…$$`) 형태로 표시된 Markdown |
| `out.pdf` | 플로팅 도형이 `<Figure>` 태그로 지정된 PDF 버전(접근성 향상) |
| `out2.md` + `md_images\*` | 고유 이름(GUID 기반)으로 저장된 이미지 파일이 포함된 Markdown 및 이미지 폴더 |

## Frequently Asked Questions & Edge Cases

| 질문 | 답변 |
|------|------|
| **손상된 파일에 복구 가능한 내용이 전혀 없으면 어떻게 되나요?** | Aspose.Words는 여전히 `Document` 객체를 반환하지만 비어 있을 수 있습니다. 진행 전에 `doc.GetChildNodes(NodeType.Paragraph, true).Count`를 확인하세요. |
| **LaTeX 구분자를 변경할 수 있나요?** | 예—`markdownMathOptions.MathDelimiter = "$$"`로 설정하면 디스플레이 스타일 구분자를 강제할 수 있습니다. |
| **`Document` 객체를 직접 해제해야 하나요?** | `Document` 클래스는 `IDisposable`을 구현합니다. 여러 파일을 처리할 경우 `using` 블록으로 감싸서 네이티브 리소스를 즉시 해제하세요. |
| **원본 이미지 파일명을 유지하려면 어떻게 하나요?** | 콜백 내부에서 `Path.Combine(imageFolder, resourceInfo.Name)`을 반환하면 됩니다. 다만 파일명 충돌 위험을 염두에 두세요. |
| **GUID 방식이 버전 관리 저장소에 안전한가요?** | GUID는 실행마다 안정적이지만 사람이 읽기 어렵습니다. 재현 가능한 이름이 필요하면 원본 이름에 프로젝트 전역 솔트를 더해 해시를 사용하세요. |

## Conclusion

우리는 **손상된 docx** 파일을 **복구**하는 방법과 **복구 모드 사용 방법**을 시연했으며,  

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}