---
category: general
date: 2026-06-02
description: Aspose.Words를 사용하여 DOCX에서 PDF를 저장하고, 도형을 인라인 span 태그로 내보내며, 몇 단계만으로 Word를
  PDF로 변환하는 방법.
draft: false
keywords:
- how to save pdf
- save docx as pdf
- convert word to pdf
- how to export shapes
- inline span tags
language: ko
og_description: Aspose.Words를 사용하여 Word 문서에서 PDF를 저장하는 방법, 부동형 도형을 인라인 span 태그로 내보내어
  깔끔한 Word‑to‑PDF 변환 결과를 얻는 방법.
og_title: Word에서 PDF 저장 방법 – 인라인 도형 내보내기 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
    span tags, and convert Word to PDF in just a few steps.
  headline: How to Save PDF from Word with Inline Shape Export – Complete Guide
  type: TechArticle
- description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
    span tags, and convert Word to PDF in just a few steps.
  name: How to Save PDF from Word with Inline Shape Export – Complete Guide
  steps:
  - name: What if my document contains **SmartArt** or **Charts**?
    text: SmartArt and charts are treated as drawing objects. The `ExportFloatingShapesAsInlineTag`
      flag will still wrap them in `<span>` tags, but complex graphics may lose some
      fidelity. In those cases, consider exporting the chart as an image first (`Chart.ToImage()`)
      and then inserting it inline.
  - name: Can I **preserve hyperlinks** and **bookmarks**?
    text: Absolutely. Those elements are not affected by the `ExportFloatingShapesAsInlineTag`
      setting. Aspose.Words retains all hyperlink and bookmark information automatically.
  - name: How do I **change PDF compression** or **embed fonts**?
    text: '`PdfSaveOptions` offers many additional properties:'
  type: HowTo
tags:
- Aspose.Words
- C#
- PDF conversion
title: 인라인 도형 내보내기로 워드에서 PDF 저장하는 방법 – 완전 가이드
url: /ko/net/programming-with-pdfsaveoptions/how-to-save-pdf-from-word-with-inline-shape-export-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word에서 인라인 도형 내보내기로 PDF 저장하는 방법 – 완전 가이드

Word 파일에서 **PDF를 저장하는 방법**을 고민해 본 적 있나요? 모든 떠다니는 도형을 텍스트 흐름에 깔끔히 맞춰서 저장하고 싶다면 당신만 그런 것이 아닙니다. 많은 엔터프라이즈 애플리케이션에서 *Word를 PDF로 변환*할 때 이미지가 제자리에서 벗어나거나 그림 객체가 흩어지는 문제를 피해야 합니다. 좋은 소식은? Aspose.Words가 이 과정을 손쉽게 만들어 주며, 라이브러리에 **도형을 인라인 `<span>` 태그로 내보내도록** 지정할 수 있어 PDF가 원본 DOCX와 똑같이 보입니다.

이 튜토리얼에서는 DOCX를 로드하고, `PdfSaveOptions`를 조정한 뒤, 깔끔한 PDF를 저장하는 전체 과정을 단계별로 안내합니다. 끝까지 읽으면 **PDF 저장 방법**, **docx를 pdf로 저장하는 방법**, 그리고 *인라인 span 태그*를 사용해 **도형을 내보내는 방법**을 알게 됩니다.

## 준비물

- **Aspose.Words for .NET** (작성 시점 최신 버전 24.x).  
- **.NET 6.0** 이상 – 코드는 .NET Framework 4.7.2에서도 동작하지만 .NET 6이 가장 권장됩니다.  
- 최소 하나 이상의 떠다니는 도형(이미지, 텍스트 상자, 도형)이 포함된 간단한 Word 문서.  
- 원하는 IDE(Visual Studio, Rider, VS Code + C# 확장)  

이것만 있으면 됩니다—추가 NuGet 패키지나 복잡한 COM 인터옵 필요 없습니다. 준비됐나요? 바로 시작합니다.

## 1단계: 프로젝트 설정 및 Aspose.Words 추가

먼저 콘솔 앱을 만들거나 기존 서비스에 코드를 통합합니다.

```bash
dotnet new console -n WordToPdfDemo
cd WordToPdfDemo
dotnet add package Aspose.Words
```

> **Pro tip:** Visual Studio를 사용한다면 NuGet 패키지 관리자 UI에서 *Aspose.Words*를 검색해 추가하면 됩니다.

## 2단계: 원본 문서 로드

라이브러리를 참조했으니 이제 DOCX를 로드합니다. 이것이 **PDF 저장 방법** 중 첫 번째 실질적인 동작이며, 파일을 메모리로 불러오는 과정입니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Step 2: Load the source document
        // Replace YOUR_DIRECTORY with the actual path on your machine.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded successfully.");
```

**왜 중요한가요:** 파일을 로드하면 경로가 올바른지, Aspose가 Word 구조를 정상적으로 파싱할 수 있는지 검증됩니다. 파일에 떠다니는 도형이 포함돼 있다면 `Document` 객체의 노드 트리에 포함됩니다.

## 3단계: PDF 저장 옵션 구성 – 도형을 인라인 태그로 내보내기

여기가 **도형 내보내기** 핵심 부분입니다. 기본적으로 Aspose.Words는 떠다니는 도형을 PDF에서 별도 객체로 렌더링해 레이아웃이 어긋날 수 있습니다. `ExportFloatingShapesAsInlineTag`를 `true`로 설정하면 엔진이 각 도형을 인라인 `<span>` 요소로 감싸 흐름에 맞게 배치합니다.

```csharp
        // Step 3: Configure PDF save options to export floating shapes as inline <span> tags
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true,
            // Optional: keep the original page size
            PageMode = PdfPageMode.UseTrimBox
        };
        Console.WriteLine("PDF save options configured – shapes will be inline.");
```

**이 플래그를 켜야 하는 이유:** 예를 들어 서명 상자가 텍스트 위에 떠 있다면, 이 설정 없이 변환하면 상자가 다른 페이지에 나타날 수 있습니다. 인라인 `<span>` 태그는 도형을 주변 문단에 고정시켜 원본과 동일한 시각적 복제본을 제공합니다.

## 4단계: 문서를 PDF로 저장

이제 앞서 만든 옵션을 사용해 `doc.Save`를 호출합니다. 바로 **docx를 pdf로 저장**하는 순간입니다.

```csharp
        // Step 4: Save the document as a PDF using the configured options
        string outputPath = @"YOUR_DIRECTORY\output.pdf";
        doc.Save(outputPath, pdfOpts);
        Console.WriteLine($"PDF saved successfully to: {outputPath}");
    }
}
```

프로그램을 실행(`dotnet run`)하고 `output.pdf`를 확인하세요. 떠다니던 도형이 인라인으로 렌더링되어 Word와 동일하게 보일 것입니다.

## 5단계: 결과 검증 – 빠른 체크리스트

1. **모든 텍스트가 존재** – 누락된 단락이 없습니다.  
2. **떠다니는 도형이 올바른 위치에** – 이제 텍스트 흐름의 일부가 되었습니다.  
3. **PDF 크기가 적절** – 인라인 태그로 내보내면 별도 이미지 스트림보다 파일 부피가 보통 감소합니다.  

문제가 있다면 원본 DOCX가 실제로 *떠다니는* 도형을 사용했는지 확인하세요(우클릭 → 레이아웃 → “텍스트와 같은 줄” vs “사각형/텍스트 뒤”). 변환 전에 도형을 “텍스트와 같은 줄”로 바꾸는 방법도 있지만, 인라인‑태그 옵션을 사용하면 원본 파일을 수정하지 않고 제어할 수 있습니다.

## 엣지 케이스 및 흔히 묻는 질문

### 문서에 **SmartArt** 또는 **차트**가 포함돼 있으면 어떻게 되나요?

SmartArt와 차트는 그림 객체로 처리됩니다. `ExportFloatingShapesAsInlineTag` 플래그는 여전히 `<span>` 태그로 감싸지만, 복잡한 그래픽은 일부 품질이 떨어질 수 있습니다. 이런 경우 차트를 먼저 이미지(`Chart.ToImage()`)로 변환한 뒤 인라인으로 삽입하는 방법을 고려하세요.

### **하이퍼링크**와 **북마크**를 **보존**할 수 있나요?

물론 가능합니다. 해당 요소들은 `ExportFloatingShapesAsInlineTag` 설정의 영향을 받지 않으며, Aspose.Words가 하이퍼링크와 북마크 정보를 자동으로 유지합니다.

### **PDF 압축**이나 **폰트 임베드**를 어떻게 바꾸나요?

`PdfSaveOptions`에는 다양한 추가 속성이 있습니다:

```csharp
pdfOpts.JpegQuality = 90;               // Adjust image compression
pdfOpts.FontEmbeddingMode = FontEmbeddingMode.EmbedAll; // Embed all used fonts
```

다운스트림 요구사항(예: PDF/A 준수)에 맞게 해당 설정을 자유롭게 조정하세요.

## 전체 작업 예제 (복사‑붙여넣기 가능)

아래는 `Program.cs`에 바로 복사해 넣을 수 있는 완전한 프로그램입니다. `YOUR_DIRECTORY`를 실제 폴더 경로로 바꾸세요.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Load the source DOCX (contains floating shapes)
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded.");

        // Configure PDF save options – export shapes as inline <span> tags
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true,
            PageMode = PdfPageMode.UseTrimBox,
            // Optional tweaks
            JpegQuality = 90,
            FontEmbeddingMode = FontEmbeddingMode.EmbedAll
        };
        Console.WriteLine("PDF options set – shapes will be inline.");

        // Save as PDF
        string outputPath = @"YOUR_DIRECTORY\output.pdf";
        doc.Save(outputPath, pdfOpts);
        Console.WriteLine($"PDF saved to {outputPath}");
    }
}
```

**콘솔에 출력되는 예상 내용:**

```
Document loaded.
PDF options set – shapes will be inline.
PDF saved to C:\MyDocs\output.pdf
```

`output.pdf`를 열면 원본 레이아웃이 그대로 유지되고, 모든 떠다니는 도형이 텍스트 흐름 안에 깔끔히 배치된 것을 확인할 수 있습니다.

## 결론

Word 문서에서 PDF를 저장하면서 떠다니는 도형을 인라인 `<span>` 태그로 변환하는 **방법**을 살펴보았습니다. DOCX를 로드하고, `PdfSaveOptions`를 구성한 뒤 `doc.Save`를 호출하면 레이아웃 문제가 없는 **docx를 pdf로 저장**하고 **Word를 PDF로 변환**할 수 있습니다.

다음 단계는? 아카이브용 **PDF/A** 준수를 적용하거나, `foreach` 루프를 사용해 폴더에 있는 여러 DOCX 파일을 일괄 처리해 보세요. 또한 Aspose.Words의 `DocumentVisitor` API를 활용해 **맞춤 렌더링**(예: 워터마크 추가)도 탐색해 볼 수 있습니다.

도형 처리, 폰트 임베드, 성능 튜닝 등에 대해 더 궁금한 점이 있으면 아래 댓글에 남겨 주세요. 즐거운 코딩 되세요!

## 다음에 배워야 할 내용은?

다음 튜토리얼들은 이 가이드에서 다룬 기술을 기반으로 하며, 단계별 코드 예제와 상세 설명을 제공해 API 기능을 더욱 깊이 있게 마스터하고 다양한 구현 방식을 탐색할 수 있도록 도와줍니다.

- [Aspose.Words for Java로 문서를 PDF로 저장하는 방법](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Aspose.Words for Java로 Word를 PDF로 변환하기](/words/english/java/document-converting/exporting-documents-to-pdf/)
- [aspose word to pdf – Java에서 DOCX를 PDF로 변환](/words/english/java/document-conversion-and-export/aspose-word-to-pdf-convert-docx-to-pdf-in-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}