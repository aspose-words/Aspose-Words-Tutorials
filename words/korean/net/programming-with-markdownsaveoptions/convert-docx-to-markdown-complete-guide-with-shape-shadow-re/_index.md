---
category: general
date: 2026-06-30
description: DOCX를 빠르게 Markdown으로 변환하고, 도형에 그림자를 적용하는 방법과 C#에서 손상된 DOCX 파일을 복구하는 방법을
  배워보세요.
draft: false
keywords:
- convert docx to markdown
- apply shadow to shape
- how to recover corrupted docx
- load docx with recovery
- how to set shape shadow
language: ko
og_description: Aspose.Words를 사용해 DOCX를 Markdown으로 변환하고, 도형에 눈에 보이는 그림자를 적용하며, 손상된
  DOCX 파일을 복구하는 모든 과정을 한 튜토리얼에서 제공합니다.
og_title: DOCX를 Markdown으로 변환 – 전체 C# 워크스루
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Convert DOCX to Markdown quickly while learning how to apply shadow
    to shape and recover corrupted DOCX files in C#.
  headline: Convert DOCX to Markdown – Complete Guide with Shape Shadow & Recovery
  type: TechArticle
- questions:
  - answer: Yes, Aspose.Words treats `.doc` the same way as `.docx`. Just change the
      file extension in the `Document` constructor.
    question: Does this work with .doc files?
  - answer: Absolutely. Replace `MarkdownSaveOptions` with `HtmlSaveOptions` and adjust
      the callback accordingly.
    question: Can I export to HTML instead of Markdown?
  - answer: The shadow doesn’t affect the shape’s bounding box. If you notice a shift,
      tweak `OffsetX`/`OffsetY` or set `Blur` to `0`.
    question: What if I need to keep the original shape size after applying the shadow?
  - answer: 'It’s memory‑efficient because it streams the file. However, extremely
      large files (>500 MB) may still need extra RAM; consider processing them page‑by‑page.
      --- ## Wrapping Up We’ve just demonstrated how to **convert DOCX to Markdown**
      while **applying a shadow to shape**, handling **corrupted DOCX*'
    question: Is the recovery mode safe for large documents?
  type: FAQPage
tags:
- Aspose.Words
- C#
- DocumentConversion
title: DOCX를 Markdown으로 변환 – 도형 그림자 및 복구 포함 완전 가이드
url: /ko/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-complete-guide-with-shape-shadow-re/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX를 Markdown으로 변환 – 도형 그림자와 복구 기능 포함 완전 가이드

DOCX를 **Markdown으로 변환**하면서 수식이나 삽입된 이미지 같은 고급 요소를 잃지 않으시나요? 같은 문서에 **도형에 그림자 적용**이 필요하거나, 파일을 열었을 때 …음, 깨진 것처럼 보이는 경우도 있을 겁니다. 이 튜토리얼에서는 복구 모드로 DOCX를 로드하고, 첫 번째 도형에 짙은 회색 그림자를 추가하고, PDF/UA 버전을 저장한 뒤, LaTeX 수식과 사용자 정의 이미지 저장 콜백을 사용해 전체를 Markdown으로 내보내는 과정을 단계별로 안내합니다.

> **왜 중요한가:** 현대 문서 파이프라인은 Markdown을 사실상의 표준으로 사용하지만, 기업에서는 여전히 Word 파일이 주류를 이룹니다. 시각적 일관성을 유지하면서 두 포맷을 연결하는 것은 많은 개발자가 직면하는 현실적인 문제입니다.

이 가이드를 끝까지 따라 하면 **DOCX를 Markdown으로 변환**하고, **도형에 그림자를 적용**하며, **손상된 DOCX 파일을 자동 복구**하는 C# 프로그램을 바로 실행할 수 있게 됩니다.

---

## 준비물

- **Aspose.Words for .NET** (v23.12 이상). 상용 라이브러리이지만 공식 사이트에서 무료 체험판을 받을 수 있습니다.  
- **.NET 6+** (코드는 .NET 6을 기준으로 컴파일되지만 .NET 7/8에서도 동일하게 동작합니다).  
- 최소 하나의 도형(예: 텍스트 상자)과 수식이 포함된 **샘플 DOCX** 파일.  
- 원하는 IDE – Visual Studio, Rider, 혹은 C# 확장 기능이 설치된 VS Code 등.

다른 NuGet 패키지는 필요하지 않으며, 나머지는 모두 Aspose.Words 안에 포함되어 있습니다.

---

## 1단계 – 복구 모드가 활성화된 상태로 DOCX 로드  

Word 파일이 부분적으로 손상되면 기본 로더는 예외를 발생시키고 전체 프로세스를 중단합니다. 이때 **load docx with recovery** 옵션이 빛을 발합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Words.Drawing;
using System;
using System.Drawing;
using System.IO;

// Enable recovery so the library tries to fix broken parts automatically.
LoadOptions loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };

// Replace "YOUR_DIRECTORY/input.docx" with the actual path to your file.
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**무슨 일이 일어나나요?**  
- `RecoveryMode.Recover`는 Aspose.Words에게 비핵심 오류(누락된 부분, 깨진 관계 등)를 무시하고 로드를 계속하도록 지시합니다.  
- 파일이 *완전히* 읽을 수 없을 경우 라이브러리는 여전히 예외를 발생시키지만, 대부분의 “손상된” Word 파일은 이 플래그로 복구 가능합니다.  

> **팁:** `try / catch` 블록으로 로드를 감싸고 `DocumentLoadingException` 세부 정보를 로그에 남기세요 – 이를 통해 중단할지 계속 진행할지 판단할 수 있습니다.

---

## 2단계 – 첫 번째 도형에 눈에 보이는 짙은 회색 그림자 적용  

문서가 메모리 상에 로드되었으니, 이제 **도형에 그림자 설정**을 해보겠습니다. 아래 예시는 문서 트리에서 가장 첫 번째 도형을 대상으로 합니다.

```csharp
// Grab the first Shape node (could be a text box, picture, etc.).
Shape firstShape = (Shape)document.GetChild(NodeType.Shape, 0, true);

// Make the shadow visible and set its colour.
firstShape.ShadowFormat.Visible = true;
firstShape.ShadowFormat.Color = Color.DarkGray;

// Optional: tweak offset, blur, and transparency for a richer look.
firstShape.ShadowFormat.OffsetX = 5;   // points to the right
firstShape.ShadowFormat.OffsetY = 5;   // points down
firstShape.ShadowFormat.Transparency = 0.2; // 20 % transparent
```

**왜 그림자를 추가하나요?**  
미묘한 그림자는 떠 있는 텍스트 상자가 PDF/UA로 렌더링될 때 혹은 이후에 Markdown‑생성 HTML 미리보기를 볼 때 돋보이게 합니다. 또한 도형 조작 코드가 실제로 실행됐는지 빠르게 확인할 수 있는 방법이기도 합니다.

> **흔한 실수:** 문서에 도형이 하나도 없으면 `GetChild`가 `null`을 반환하고 형변환 시 예외가 발생합니다. 확실하지 않을 경우 항상 `null` 체크를 하세요.

---

## 3단계 – PDF/UA 버전 저장 (선택 사항이지만 유용)

주 목표는 Markdown이지만, 많은 팀이 접근성 PDF도 필요로 합니다. **ExportFloatingShapesAsInlineTag** 옵션을 설정하면 방금 그림자를 적용한 도형이 PDF/UA에 올바르게 표시됩니다.

```csharp
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfUa1,
    ExportFloatingShapesAsInlineTag = true
};

document.Save("YOUR_DIRECTORY/output.pdf", pdfOptions);
```

**이 옵션이 하는 일**  
- `PdfCompliance.PdfUa1`은 파일이 PDF/UA(Universal Accessibility) 표준을 만족하도록 강제합니다.  
- `ExportFloatingShapesAsInlineTag` 플래그는 렌더러에게 떠 있는 도형을 인라인 객체로 취급하도록 지시해 시각적 순서를 보존합니다.

Markdown만 필요하다면 이 단계를 건너뛸 수 있지만, PDF를 통해 결과를 검증하는 습관은 좋습니다.

---

## 4단계 – LaTeX 수식 및 이미지 콜백과 함께 Markdown으로 내보내기  

튜토리얼의 핵심: **docx를 markdown으로 변환**하면서 수식과 이미지를 깔끔하게 처리합니다.

```csharp
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // Export Office Math objects as LaTeX so they render nicely on GitHub, MkDocs, etc.
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // This callback is invoked for every external resource (images, OLE objects).
    ResourceSavingCallback = info =>
    {
        // Create a folder next to the markdown file for all extracted images.
        string imageFolder = "YOUR_DIRECTORY/md_res";
        Directory.CreateDirectory(imageFolder);

        // Build a unique filename to avoid collisions.
        string fileName = Path.Combine(imageFolder, $"{Guid.NewGuid()}{info.Extension}");
        info.FileName = fileName;

        // Returning true tells Aspose.Words that we handled the saving.
        return true;
    }
};

document.Save("YOUR_DIRECTORY/output.md", markdownOptions);
```

### 생성된 Markdown 예시

원본 DOCX에 간단한 수식 `y = mx + b`가 들어 있었다면, 생성된 Markdown은 다음과 같이 포함됩니다.

```markdown
$$y = mx + b$$
```

그리고 삽입된 사진은 다음과 같은 형태가 됩니다.

```markdown
![](md_res/3f9c2e0a-1b4d-4a6e-9d2f-7a8b9c0d1e2f.png)
```

콜백은 모든 이미지를 `md_res/` 폴더에 저장하도록 보장해, Markdown 파일이 깔끔하게 유지됩니다.

---

## 엣지 케이스 및 팁 (생각하지 못했던 상황들)

| 상황 | 해결 방법 |
|-----------|------------|
| **문서에 도형이 없음** | 그림자 적용 단계를 건너뛰거나 `if (firstShape != null) { … }` 로 감싸세요. |
| **수식 내보내기 실패** | DOCX가 실제로 Office Math(삽입 → 수식)을 사용했는지 확인하세요. 이미지 형태의 수식이라면 일반 이미지 태그가 생성됩니다. |
| **큰 이미지로 메모리 압박** | `ResourceSavingCallback`에서 `System.Drawing`을 이용해 저장 전에 이미지 크기를 축소하세요. |
| **LaTeX 대신 인라인 HTML이 필요** | `OfficeMathExportMode`를 `OfficeMathExportMode.MathML` 또는 `OfficeMathExportMode.Image` 로 변경하세요. |
| **복구된 문서에서 일부 내용이 사라짐** | 복구는 최선 노력 방식입니다. `DocumentLoadingException` 세부 정보를 로그에 남기고, 경우에 따라 원본 DOCX를 수동으로 수정할 수 있습니다. |

---

## 전체 작업 예제 (복사‑붙여넣기 바로 사용)

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using System;
using System.Drawing;
using System.IO;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load with recovery ----------
        LoadOptions loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // ---------- Step 2: Apply shadow to first shape ----------
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape != null)
        {
            shape.ShadowFormat.Visible = true;
            shape.ShadowFormat.Color = Color.DarkGray;
            shape.ShadowFormat.OffsetX = 5;
            shape.ShadowFormat.OffsetY = 5;
            shape.ShadowFormat.Transparency = 0.2;
        }

        // ---------- Step 3: Save PDF/UA (optional) ----------
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            Compliance = PdfCompliance.PdfUa1,
            ExportFloatingShapesAsInlineTag = true
        };
        doc.Save("YOUR_DIRECTORY/output.pdf", pdfOpts);

        // ---------- Step 4: Export to Markdown ----------
        MarkdownSaveOptions mdOpts = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX,
            ResourceSavingCallback = info =>
            {
                string imgFolder = "YOUR_DIRECTORY/md_res";
                Directory.CreateDirectory(imgFolder);
                info.FileName = Path.Combine(imgFolder, $"{Guid.NewGuid()}{info.Extension}");
                return true;
            }
        };
        doc.Save("YOUR_DIRECTORY/output.md", mdOpts);

        Console.WriteLine("Conversion completed successfully!");
    }
}
```

**예상 출력**  
- `output.pdf` – 도형 그림자를 반영한 접근성 PDF.  
- `output.md` – 수식은 LaTeX 블록으로, 이미지가 `md_res/`에 저장된 Markdown 파일.  

MathJax를 지원하는 뷰어(GitHub, VS Code 미리보기, MkDocs 등)에서 Markdown을 열면 수식이 아름답게 렌더링됩니다.

---

## 자주 묻는 질문

**Q: .doc 파일에도 적용할 수 있나요?**  
A: 네, Aspose.Words는 `.doc`을 `.docx`와 동일하게 처리합니다. `Document` 생성자에서 파일 확장자만 바꾸면 됩니다.

**Q: HTML로 내보내고 싶다면?**  
A: 물론 가능합니다. `MarkdownSaveOptions` 대신 `HtmlSaveOptions` 로 교체하고 콜백도 그에 맞게 조정하면 됩니다.

**Q: 그림자를 적용한 뒤 원래 도형 크기를 유지하려면?**  
A: 그림자는 도형의 경계 상자를 변경하지 않습니다. 위치가 어긋난다면 `OffsetX`/`OffsetY` 를 조정하거나 `Blur` 를 `0` 으로 설정하세요.

**Q: 복구 모드가 큰 문서에도 안전한가요?**  
A: 스트리밍 방식이라 메모리 효율이 좋지만, 500 MB 이상 초대형 파일은 여전히 RAM이 많이 필요할 수 있습니다. 페이지 단위로 처리하는 방안을 고려하세요.

---

## 마무리  

우리는 **DOCX를 Markdown으로 변환**하면서 **도형에 그림자 적용**, **손상된 DOCX 복구**, 그리고 **PDF/UA 백업**까지 구현하는 방법을 살펴보았습니다. 코드는 간결하고 개념은 명확하며, 배치 처리나 웹 서비스 통합 등 여러분의 파이프라인에 맞게 각 단계를 자유롭게 확장할 수 있습니다.

다음에 시도해볼 수 있는 단계:

- **배치 변환** – 디렉터리를 순회하며 모든 파일에 적용하기

## 다음에 배워야 할 내용은?


다음 튜토리얼들은 이 가이드에서 다룬 기술을 기반으로 하며, 각각 완전한 코드 예제와 단계별 설명을 제공해 추가 API 기능을 마스터하고 다양한 구현 방식을 탐색할 수 있도록 돕습니다.

- [Recover Corrupted DOCX & Convert Word to Markdown](/words/english/python-net/document-conversion/recover-corrupted-docx-convert-word-to-markdown/)
- [how to recover docx – C# guide for corrupted Word files](/words/english/net/programming-with-loadoptions/how-to-recover-docx-c-guide-for-corrupted-word-files/)
- [Convert docx to markdown – Step‑by‑Step C# Guide](/words/english/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-step-by-step-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}