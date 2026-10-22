---
category: general
date: 2026-08-10
description: Aspose.Words를 사용하여 프로그래밍 방식으로 워드 문서를 생성하고, 워드에서 여러 도형을 그룹화하는 방법을 배우며,
  워드에 사각형을 추가하고, C#에서 그룹 도형을 만드는 방법을 알아보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- group multiple shapes word
- add rectangle to word
- how to create group shape
language: ko
lastmod: 2026-08-10
og_description: Aspose.Words를 사용하여 워드 문서를 프로그래밍 방식으로 생성합니다. 이 가이드에서는 C#을 사용하여 여러 개의
  도형을 그룹화하고, 워드에 사각형을 추가하며, 일반 텍스트 콘텐츠 컨트롤을 삽입하는 방법을 보여줍니다.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and ellipse with
  a plain‑text content control
og_title: 프로그램으로 워드 문서 만들기 – C#에서 도형 그룹화
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  headline: Create word document programmatically and group shapes in C#
  type: TechArticle
- description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  name: Create word document programmatically and group shapes in C#
  steps:
  - name: – Initialize the document and builder
    text: The `Document` object represents the entire DOCX file, while `DocumentBuilder`
      provides a convenient API to add content. Initializing them is the first requirement
      whenever you **create word document programmatically**.
  - name: – Create a group shape container
    text: A `Shape` with `ShapeType.Group` acts as a canvas that can hold other shapes.
      Setting `Width` and `Height` defines the bounding box for the group. This is
      the core of **how to create group shape** in Aspose.Words.
  - name: – Add a rectangle to word
    text: A rectangle is created with `ShapeType.Rectangle`. Its `Left` and `Top`
      properties position it relative to the group’s origin. This step demonstrates
      **add rectangle to word** and shows how you can control exact placement.
  - name: – Add an ellipse (circle) to the group
    text: An ellipse is added the same way as the rectangle, but with `ShapeType.Ellipse`.
      The `Left = 210` moves it to the right of the rectangle, creating a visually
      distinct pair of shapes inside the same group.
  - name: – Insert the completed group shape into the document
    text: '`builder.InsertNode(groupShape)` places the whole group at the current
      cursor location. Because the group already contains its children, you do not
      need additional insert calls for the rectangle or ellipse.'
  - name: – Create a plain‑text StructuredDocumentTag (SDT)
    text: A StructuredDocumentTag is a content control that end users can fill in
      when the document is opened in Word. Setting `Title = "CustomerName"` gives
      the control a meaningful identifier, which is useful for later data extraction.
  - name: – Save the document
    text: '`doc.Save("GroupAndSDT.docx")` writes the file to disk. The resulting DOCX
      contains the grouped shapes and the SDT. Opening the file in Microsoft Word
      will show a rectangle next to a circle, both selectable as a single object,
      followed by a placeholder “Enter name here …”.'
  - name: Using different shape types
    text: You can replace `ShapeType.Rectangle` or `ShapeType.Ellipse` with any other
      `ShapeType` (e.g., `ShapeType.Polygon`, `ShapeType.Line`). The grouping logic
      remains identical.
  - name: Setting fill color and borders
    text: '```csharp rectangleShape.FillColor = System.Drawing.Color.LightBlue; rectangleShape.StrokeColor
      = System.Drawing.Color.DarkBlue; ellipseShape.FillColor = System.Drawing.Color.LightCoral;
      ``` Adding fill and stroke improves visual distinction, especially when the
      document is shared with non‑technical'
  - name: Rotating the entire group
    text: '```csharp groupShape.Rotation = 45; // rotates both shapes together ```
      Rotating the group is more efficient than rotating each child individually.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: C#를 사용하여 워드 문서를 프로그래밍 방식으로 생성하고 도형을 그룹화하기
url: /ko/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 워드 문서를 프로그래밍 방식으로 생성하고 도형 그룹화하기

프로그래밍 방식으로 **워드 문서를 생성**해야 한다면, 이 튜토리얼에서는 Aspose.Words를 사용하여 DOCX 파일을 만드는 방법과 **워드에서 여러 도형을 그룹화**하는 방법을 보여줍니다. 또한 **워드에 사각형 추가**와 **그룹 도형 생성 방법**을 다루며, 사각형과 타원을 모두 포함하고 사용자 입력을 위한 일반 텍스트 StructuredDocumentTag를 포함합니다.

코드를 실행한 후에는 사용자가 이름을 입력할 수 있는 콘텐츠 컨트롤과 그룹화된 사각형‑타원 도형이 포함된 바로 사용할 수 있는 워드 파일이 완성됩니다. 워드에서 수동 편집이 필요하지 않습니다.

## 필요 사항

- .NET 6.0 또는 이후 버전 (샘플은 .NET 6을 대상으로 하지만 최신 .NET 버전이면 모두 작동합니다)
- 무료 체험판으로 테스트 가능한 Aspose.Words for .NET 라이선스
- Visual Studio 2022 또는 선호하는 C# IDE
- C# 구문에 대한 기본적인 이해

## 프로그래밍 방식으로 워드 문서 생성 – 전체 워크플로우

프로세스는 세 가지 논리적 단계로 구성됩니다:

1. **Initialize** a `Document`와 `DocumentBuilder`를 초기화합니다 – 생성하는 모든 워드 파일의 기반입니다.
2. **Build a group shape**를 사용해 사각형과 타원을 포함하는 그룹 도형을 만듭니다 – **group multiple shapes word**와 **how to create group shape**를 보여줍니다.
3. **Insert a StructuredDocumentTag (SDT)** – 최종 사용자가 데이터를 입력할 수 있는 일반 텍스트 콘텐츠 컨트롤이며, 전체 문서 레이아웃의 일부로 **add rectangle to word**를 보여줍니다.

아래는 전체 실행 가능한 코드와 단계별 설명입니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1 – Initialize the document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2 – Create a group shape container
            Shape groupShape = new Shape(doc, ShapeType.Group)
            {
                Width = 400,
                Height = 200
            };

            // Step 3 – Add a rectangle to the group
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 0,
                Top = 0
            };
            groupShape.GroupShape.AddChild(rectangleShape);

            // Step 4 – Add an ellipse (circle) to the group
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse)
            {
                Width = 100,
                Height = 100,
                Left = 210, // Position next to the rectangle
                Top = 0
            };
            groupShape.GroupShape.AddChild(ellipseShape);

            // Step 5 – Insert the completed group shape into the document
            builder.InsertNode(groupShape);

            // Step 6 – Create a plain‑text StructuredDocumentTag for user input
            StructuredDocumentTag sdtTag = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Block)
            {
                Title = "CustomerName"
            };
            builder.InsertNode(sdtTag);
            builder.Writeln("Enter name here …");

            // Step 7 – Save the document
            doc.Save("GroupAndSDT.docx");
            Console.WriteLine("Document created successfully.");
        }
    }
}
```

### 단계 1 – 문서와 빌더 초기화
`Document` 객체는 전체 DOCX 파일을 나타내며, `DocumentBuilder`는 콘텐츠를 추가하기 위한 편리한 API를 제공합니다. 이를 초기화하는 것은 **프로그래밍 방식으로 워드 문서를 생성**할 때 첫 번째 요구 사항입니다.

> **Pro tip:** 여러 작업에서 동일한 문서를 재사용하려면 불필요한 객체 생성을 방지하기 위해 단일 `DocumentBuilder` 인스턴스를 유지하세요.

### 단계 2 – 그룹 도형 컨테이너 만들기
`ShapeType.Group`을 가진 `Shape`는 다른 도형을 담을 수 있는 캔버스 역할을 합니다. `Width`와 `Height`를 설정하면 그룹의 경계 상자를 정의합니다. 이것이 Aspose.Words에서 **how to create group shape**의 핵심입니다.

> **Edge case:** 그룹의 너비가 자식 도형들의 전체 너비보다 작으면 자식 도형이 잘립니다. 항상 모든 자식 도형을 포함할 수 있을 만큼 충분히 크게 설정하세요.

### 단계 3 – 워드에 사각형 추가
`ShapeType.Rectangle`로 사각형을 생성합니다. `Left`와 `Top` 속성으로 그룹 원점에 대한 위치를 지정합니다. 이 단계는 **add rectangle to word**를 보여주며 정확한 배치를 제어하는 방법을 나타냅니다.

> **Common mistake:** `Left`/`Top`을 설정하지 않으면 사각형이 그룹의 기본 원점(0,0)에 나타나 다른 자식과 겹칠 수 있습니다.

### 단계 4 – 그룹에 타원(원) 추가
타원은 사각형과 동일한 방식으로 추가하지만 `ShapeType.Ellipse`를 사용합니다. `Left = 210`은 사각형 오른쪽으로 이동시켜 같은 그룹 내에서 시각적으로 구분되는 두 도형을 만듭니다.

> **Why use a group?** 그룹화하면 나중에 두 도형을 한 번에 이동, 회전 또는 크기 조정할 수 있어 상대적인 레이아웃을 유지합니다.

### 단계 5 – 완성된 그룹 도형을 문서에 삽입
`builder.InsertNode(groupShape)`는 현재 커서 위치에 전체 그룹을 삽입합니다. 그룹에 이미 자식이 포함되어 있으므로 사각형이나 타원을 별도로 삽입할 필요가 없습니다.

### 단계 6 – 일반 텍스트 StructuredDocumentTag (SDT) 만들기
StructuredDocumentTag는 문서를 Word에서 열었을 때 최종 사용자가 입력할 수 있는 콘텐츠 컨트롤입니다. `Title = "CustomerName"`을 설정하면 컨트롤에 의미 있는 식별자가 부여되어 이후 데이터 추출에 유용합니다.

> **Why a plain‑text SDT?** 입력을 일반 텍스트로 제한하여 의도치 않은 서식이 하위 처리에 영향을 주는 것을 방지합니다.

### 단계 7 – 문서 저장
`doc.Save("GroupAndSDT.docx")`은 파일을 디스크에 저장합니다. 결과 DOCX에는 그룹화된 도형과 SDT가 포함됩니다. Microsoft Word에서 파일을 열면 사각형 옆에 원이 표시되고 두 도형을 하나의 객체로 선택할 수 있으며, 그 아래에 “Enter name here …”라는 자리 표시자가 있는 콘텐츠 컨트롤이 나타납니다.

#### 예상 출력
- 실행 폴더에 **GroupAndSDT.docx**라는 파일이 생성됩니다.
- Word에서 사각형 + 타원으로 구성된 그룹 도형이 하나의 단위로 이동 가능합니다.
- 그룹 바로 아래에 회색 음영의 콘텐츠 컨트롤이 표시되어 사용자가 이름을 입력하도록 안내합니다.

## 추가 변형 및 모범 사례

### 다른 도형 유형 사용
`ShapeType.Rectangle` 또는 `ShapeType.Ellipse`를 다른 `ShapeType`(예: `ShapeType.Polygon`, `ShapeType.Line`)으로 교체할 수 있습니다. 그룹화 로직은 동일하게 유지됩니다.

### 채우기 색상 및 테두리 설정
```csharp
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```
채우기와 스트로크를 추가하면 시각적 구분이 향상되며, 특히 비기술적인 이해관계자와 문서를 공유할 때 유용합니다.

### 전체 그룹 회전
```csharp
groupShape.Rotation = 45; // rotates both shapes together
```
그룹을 회전하는 것이 각 자식을 개별적으로 회전하는 것보다 효율적입니다.

### PDF로 내보내기
PDF 버전이 필요하면 간단히 호출하면 됩니다:
```csharp
doc.Save("GroupAndSDT.pdf", SaveFormat.Pdf);
```
모든 그룹 도형과 SDT(텍스트 필드로 렌더링됨)가 PDF에 표시됩니다.

## 일반적인 함정 및 회피 방법

| 증상 | 원인 | 해결책 |
|---------|-------|---------|

## 다음에 배워야 할 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 리소스에는 전체 작동 코드 예제와 단계별 설명이 포함되어 있어 추가 API 기능을 마스터하고 자체 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Aspose.Words for .NET을 사용하여 워드 문서에 그룹 도형 만들기](/words/english/net/working-with-shapes/add-group-shape/)
- [C#를 사용하여 워드에 사각형 도형 만들기 – 단계별 가이드](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [그림자 사각형 도형이 있는 빈 워드 문서 만들기 – 단계별 가이드](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}