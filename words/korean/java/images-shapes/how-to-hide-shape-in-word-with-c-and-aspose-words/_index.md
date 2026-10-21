---
category: general
date: 2026-09-11
description: C#를 사용하여 Word에서 도형을 숨기는 방법을 배웁니다. 이 가이드는 또한 사각형 도형을 삽입하고 Aspose.Words를
  사용해 Word 문서에 도형을 삽입하는 방법을 보여줍니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape in word
- insert rectangle shape
- insert shape into word document
language: ko
lastmod: 2026-09-11
og_description: C#와 Aspose.Words를 사용하여 Word에서 도형을 숨기는 방법. 단계별 튜토리얼을 따라 사각형 도형을 삽입하고
  Word 문서에서 도형을 관리하세요.
og_image_alt: Screenshot showing how to hide shape in Word document using C#
og_title: Word에서 도형 숨기기 – 완전 C# 가이드
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  headline: How to hide shape in Word with C# and Aspose.Words
  type: TechArticle
- description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  name: How to hide shape in Word with C# and Aspose.Words
  steps:
  - name: Explanation of each step
    text: 1. **Create a new document** – `Document` represents the Word file in memory.
      `DocumentBuilder` provides a fluent API for inserting content. 2. **Insert rectangle
      shape** – `InsertShape` creates a drawing object of type `Rectangle`. The dimensions
      are expressed in points (1 pt ≈ 1/72 in). This satis
  - name: Expected result
    text: 'Open `output.docx` in Microsoft Word:'
  - name: Manually adding the hidden attribute (fallback)
    text: '```csharp // Fallback for Aspose.Words versions prior to 24.10 Shape shape
      = builder.InsertShape(ShapeType.Rectangle, 100, 50); shape.FillColor = System.Drawing.Color.LightGray;'
  type: HowTo
- questions:
  - answer: No. Hidden shapes are ignored by the layout engine, so they do not consume
      space. This is useful for placeholder content that should not affect page breaks.
    question: Does hiding a shape affect pagination?
  - answer: Yes. The same `Hidden` property works on shapes located anywhere in the
      document tree, including headers, footers, and even inside tables.
    question: Can I hide a shape that is part of a header or footer?
  - answer: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` for each target shape. ```csharp foreach (Shape s in
      doc.GetChildNodes(NodeType.Shape, true)) { if (s.ShapeType == ShapeType.Rectangle)
      s.Hidden = true; } ```
    question: What if I need to hide multiple shapes at once?
  - answer: 'When converting to PDF, hidden shapes are omitted by default, matching
      Word’s rendering behavior. If you need them in the PDF, you must unhide them
      before conversion. ## Tips and pitfalls * **Pro tip:** Set `shape.WrapType =
      WrapType.None` before hiding if you later plan to unhide the shape without '
    question: Is the hidden attribute preserved when converting to PDF?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: C#와 Aspose.Words를 사용하여 Word에서 도형 숨기기
url: /ko/java/images-shapes/how-to-hide-shape-in-word-with-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#와 Aspose.Words를 사용하여 Word에서 도형 숨기기

Word에서 도형을 숨기면서 문서 구조에 도형을 유지해야 하는 경우, 이 튜토리얼에서는 정확한 방법을 보여줍니다. Aspose.Words for .NET을 사용하면 사각형 도형을 삽입하고 숨길 수 있으며, 나중에 처리할 수 있도록 위치를 유지할 수 있습니다.

Word 자동화에서는 템플릿 생성, 보고서 준비 또는 문서 편집 서비스를 구축하는 등 도형에 대한 세밀한 제어가 종종 필요합니다. 이 가이드를 끝까지 읽으면 다음을 수행할 수 있습니다:

* Word 문서에 사각형 도형 삽입 (`insert rectangle shape`).
* 도형을 삭제하지 않고 숨기기 (`how to hide shape in word`).
* 결과를 저장하고 숨겨진 도형이 렌더링된 뷰에 나타나지 않는지 확인 (`insert shape into word document`).

이 예제는 Aspose.Words 24.10 이상에서 작동하며 .NET 6.0+을 대상으로 하지만, 개념은 이전 버전에도 적용됩니다.

## 전제 조건

* **Aspose.Words for .NET** ≥ 24.10. Aspose 웹사이트에서 무료 임시 라이선스를 얻을 수 있습니다.
* **.NET SDK** 6.0 이상이 머신에 설치되어 있어야 합니다.
* Visual Studio 2022, VS Code, Rider와 같은 개발 환경.
* C# 및 Word Open XML 개념에 대한 기본적인 이해(선택 사항이지만 도움이 됨).

## Aspose.Words를 사용하여 Word에서 도형 숨기기

아래는 전체 워크플로우를 보여주는 완전한 실행 가능한 프로그램입니다—문서 생성부터 사각형 도형 삽입, 최종적으로 숨기기까지.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShapeDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape (100 × 50 points) at the current cursor position.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        // Optional: give the shape a visible fill so you can see it before hiding.
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Hide the shape without removing it from the document.
        // The Hidden property is available starting with Aspose.Words 24.10.
        rectangle.Hidden = true;

        // Step 4: Save the document to disk.
        string outputPath = "output.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}. The rectangle shape is hidden.");
    }
}
```

### 각 단계 설명

1. **Create a new document** – `Document`는 메모리 내의 Word 파일을 나타냅니다. `DocumentBuilder`는 콘텐츠 삽입을 위한 유창한 API를 제공합니다.
2. **Insert rectangle shape** – `InsertShape`는 `Rectangle` 유형의 그리기 객체를 생성합니다. 크기는 포인트 단위(1 pt ≈ 1/72 in)로 표현됩니다. 이는 `insert rectangle shape` 요구사항을 충족합니다.
3. **Hide the shape** – `Shape.Hidden = true` 설정은 Word 마크업(` <w:hidden/>`)에서 도형을 숨김으로 표시합니다. 도형은 문서 트리의 일부로 남아 있어 나중에 숨김을 해제하거나 프로그래밍 방식으로 참조할 수 있습니다. 이는 `how to hide shape in word`의 핵심입니다.
4. **Save the file** – 문서는 `output.docx`에 기록됩니다. Microsoft Word에서 열면 사각형이 보이지 않지만 XML에 존재하며 ZIP 뷰어 또는 Open XML SDK로 검사할 수 있습니다.

### 예상 결과

Microsoft Word에서 `output.docx`를 엽니다:

* 문서는 비어 있는 것처럼 보이며—보이는 도형이 없습니다.
* 기본 XML(`word/document.xml`)을 검사하면 `<w:pict>` 요소 안에 `<w:hidden/>` 속성이 있는 것을 확인할 수 있으며, 이는 도형이 존재하지만 숨겨져 있음을 의미합니다.

```xml
<w:pict>
  <v:shape id="Shape0" style="position:absolute; ...">
    <v:fillcolor>#ADD8E6</v:fillcolor>
    <w:hidden/>
  </v:shape>
</w:pict>
```

숨겨진 도형은 `Hidden = false`로 설정하고 문서를 다시 저장하면 다시 표시할 수 있습니다.

## Word 문서에 사각형 도형 삽입

주된 목표는 도형을 숨기는 것이지만, 많은 상황에서 먼저 도형을 삽입하는 것으로 시작합니다. `InsertShape` 메서드는 `Rectangle`, `Ellipse`, `Line`, 사용자 지정 이미지 등을 포함한 다양한 `ShapeType` 값을 지원합니다.

```csharp
// Example: Insert an ellipse shape and keep it visible.
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
ellipse.FillColor = System.Drawing.Color.Pink;
```

**왜 사각형을 사용하나요?**  
사각형은 텍스트, 이미지 또는 다른 중첩 도형을 담을 수 있는 깔끔하고 축에 정렬된 컨테이너를 제공합니다. 표나 차트와 같은 동적 콘텐츠의 자리 표시자로 자주 사용됩니다. 사각형을 먼저 삽입하면 나중에 숨기더라도 레이아웃 일관성을 유지할 수 있습니다.

## Word 문서에 도형 삽입 – 모범 사례

`insert shape into word document` 할 때 다음을 고려하세요:

* **Set explicit dimensions** – 자동 크기에 의존하지 말고, 포인트 단위로 너비와 높이를 지정하여 플랫폼 간 일관된 레이아웃을 보장하세요.
* **Define positioning** – 기본적으로 도형은 현재 단락에 고정됩니다. `builder.MoveTo` 또는 `builder.StartBookmark`를 사용해 정확히 배치하세요.
* **Apply styling early** – 채우기 색, 선 스타일, 텍스트 래핑은 최종 모양에 영향을 줍니다. 숨겨진 도형도 마크업이 변경되지 않으므로 적절한 스타일링이 필요합니다.
* **Version compatibility** – `Hidden` 속성은 Aspose.Words 24.10부터 제공됩니다. 이전 버전을 대상으로 하는 경우 `Node` API를 사용해 `<w:hidden/>` 속성을 수동으로 추가할 수 있습니다.

### 숨김 속성을 수동으로 추가하기 (대체 방법)

```csharp
// Fallback for Aspose.Words versions prior to 24.10
Shape shape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
shape.FillColor = System.Drawing.Color.LightGray;

// Access the underlying OpenXml node.
var shapeNode = shape.GetChildNodes(NodeType.Any, true)[0];
shapeNode.GetAttributes().Add("w:hidden", "true");
```

## 완전한 엔드‑투‑엔드 예제

모든 것을 종합한 단일 프로그램은 다음과 같습니다:

1. 사각형 도형 삽입.
2. 도형 숨기기.
3. 대비를 위해 보이는 타원 삽입.
4. 문서 저장.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class FullDemo
{
    static void Main()
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert and hide a rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 120, 60);
        rect.FillColor = System.Drawing.Color.LightGreen;
        rect.Hidden = true; // core of how to hide shape in word

        // Insert a visible ellipse to show the difference.
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.FillColor = System.Drawing.Color.Coral;

        // Save the output.
        string filePath = "demo_output.docx";
        doc.Save(filePath);
        Console.WriteLine($"Demo document saved to {filePath}");
    }
}
```

프로그램을 실행하면 `demo_output.docx`가 생성됩니다. 열었을 때 코랄 색 타원만 보이며, 녹색 사각형은 XML에 존재하지만 화면에는 숨겨져 있습니다.

## 일반적인 질문 및 엣지 케이스

**Q: 도형을 숨기면 페이지 매김에 영향을 줍니까?**  
A: 아니요. 숨겨진 도형은 레이아웃 엔진에 의해 무시되므로 공간을 차지하지 않습니다. 이는 페이지 구분에 영향을 주지 않아야 하는 자리 표시자 콘텐츠에 유용합니다.

**Q: 헤더 또는 푸터에 포함된 도형을 숨길 수 있나요?**  
A: 예. 동일한 `Hidden` 속성이 문서 트리 어디에든 위치한 도형에 적용되며, 헤더, 푸터 및 테이블 내부에도 적용됩니다.

**Q: 여러 도형을 한 번에 숨겨야 하면 어떻게 해야 하나요?**  
A: `Document.GetChildNodes(NodeType.Shape, true)` 컬렉션을 순회하면서 각 대상 도형에 `Hidden = true`를 설정합니다.

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Rectangle)
        s.Hidden = true;
}
```

**Q: PDF로 변환할 때 숨김 속성이 유지되나요?**  
A: PDF로 변환할 때 기본적으로 숨겨진 도형은 제외되어 Word의 렌더링 동작과 일치합니다. PDF에 포함하려면 변환 전에 도형을 다시 표시해야 합니다.

## 팁 및 함정

* **Pro tip:** 숨기기 전에 `shape.WrapType = WrapType.None`을 설정하면 나중에 도형을 다시 표시할 때 주변 텍스트가 방해받지 않습니다.
* **Older Aspose.Words 버전에 주의:** 24.10 이전에서는 `Hidden` 속성이 `NotSupportedException`을 발생시킵니다. 이 경우 수동 XML 방식을 사용하세요.
* **Testing:** 생성된 `.docx`를 Word에서 열고 “Show XML markup”(개발자 탭)을 사용해 `<w:hidden/>` 속성이 존재하는지 확인하세요.

## 결론

이제 C#와 Aspose.Words를 사용하여 Word에서 도형을 숨기는 방법과 사각형 도형을 삽입하고 Word 문서에 도형을 삽입하여 가시성을 완전히 제어하는 방법을 알게 되었습니다. `Hidden` 속성을 활용하면 도형을 문서 모델에 유지하면서 최종 사용자에게는 깔끔한 뷰를 제공할 수 있습니다.

다음으로 **런타임에 도형 속성 업데이트**, **숨겨진 도형을 이미지로 변환**, 또는 **Open XML SDK를 사용해 숨긴 요소를 직접 조작**과 같은 관련 주제를 탐색해 보세요. 이러한 확장은 이해를 더욱 깊게 할 것입니다.

## 다음에 배워야 할 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료는 단계별 설명과 함께 완전한 코드 예제를 제공하여 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하도록 돕습니다.

- [Aspose.Words for .NET을 사용하여 Word 문서에 도형 삽입](/words/english/net/working-with-shapes/insert-shape/)
- [C#를 사용하여 Word에 사각형 도형 만들기 – 단계별 가이드](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words for .NET을 사용하여 Word 문서에 그룹 도형 만들기](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}