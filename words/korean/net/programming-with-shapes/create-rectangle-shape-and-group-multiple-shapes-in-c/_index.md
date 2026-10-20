---
category: general
date: 2026-09-18
description: C#를 사용하여 Word 문서에 사각형 모양을 만들고, 여러 모양을 추가하고, 모양을 그룹에 넣으며, Aspose.Words로
  그룹 모양을 삽입하는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add multiple shapes
- add shapes to group
- insert group shape
language: ko
lastmod: 2026-09-18
og_description: C#를 사용하여 Word 파일에 사각형 모양을 만들기. 이 가이드는 여러 모양을 추가하고, 모양을 그룹에 넣으며, Aspose.Words를
  사용해 그룹 모양을 삽입하는 방법을 보여줍니다.
og_image_alt: Grouped rectangle and ellipse shapes displayed in a Word document
og_title: C#에서 사각형 모양을 만들고 도형을 그룹화하기
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create rectangle shape in a Word document using C#. Learn how to add
    multiple shapes, add shapes to a group, and insert group shape with Aspose.Words.
  headline: Create rectangle shape and group multiple shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Shape
- GroupShape
title: C#에서 사각형 모양을 만들고 여러 모양을 그룹화하기
url: /ko/net/programming-with-shapes/create-rectangle-shape-and-group-multiple-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 사각형 모양 만들기 및 여러 모양 그룹화

Word 문서에 **사각형 모양 만들기**가 필요하다면, 이 튜토리얼은 완전한 솔루션을 보여줍니다. **여러 모양 추가**, **그룹에 모양 추가**, 그리고 **그룹 모양 삽입**을 Aspose.Words API for .NET을 사용하여 수행하는 방법을 확인할 수 있습니다.

프로그래밍 방식으로 보고서, 계약서, 마케팅 자료 등을 생성할 때 모양을 다루는 것은 일반적인 요구사항입니다. 이 가이드를 끝까지 따라오면 사각형, 타원, 그리고 두 모양을 포함하는 그룹을 포함한 `.docx` 파일을 생성하는 실행 가능한 C# 콘솔 애플리케이션을 얻게 됩니다.

필수 사전 조건은 최신 .NET SDK(6.0 이상)와 라이선스가 적용된 Aspose.Words for .NET입니다. 추가 도구는 필요하지 않습니다.

## Prerequisites

- .NET 6.0 SDK 또는 최신 버전  
- Aspose.Words for .NET (NuGet 패키지 `Aspose.Words`)  
- C# 구문에 대한 기본적인 이해  

다음 명령으로 패키지를 설치할 수 있습니다:

```bash
dotnet add package Aspose.Words
```

## 1단계: Aspose.Words로 사각형 모양 만들기

첫 번째 단계는 `Rectangle` 유형의 `Shape` 객체를 만드는 것입니다. 이 객체는 문서에 표시될 시각적 사각형을 나타냅니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty document
Document doc = new Document();

// Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape: width = 100 points, height = 50 points
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 100;
rectangle.Height = 50;

// Optional: give the rectangle a fill color and a border
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.StrokeWeight = 1.0;

// Insert the rectangle at the current builder position
builder.InsertNode(rectangle);
```

**왜 중요한가:** `ShapeType.Rectangle`는 Aspose.Words에 기하학적 사각형을 렌더링하도록 지시합니다. `Width`와 `Height`를 설정하면 크기가 포인트 단위(1 포인트 = 1/72 인치)로 정의됩니다. 채우기 색상과 테두리 색상을 추가하면 추가 스타일링 없이도 모양이 보이게 됩니다.

## 2단계: 문서에 여러 모양 추가

사각형을 만든 뒤에는 원하는 만큼 추가 모양을 만들 수 있습니다. 이 예제에서는 **여러 모양 추가**가 어떻게 동작하는지 보여주기 위해 타원을 추가합니다.

```csharp
// Create an ellipse shape: width = 80 points, height = 80 points
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width = 80;
ellipse.Height = 80;

// Style the ellipse
ellipse.FillColor = System.Drawing.Color.LightCoral;
ellipse.StrokeColor = System.Drawing.Color.Maroon;
ellipse.StrokeWeight = 1.0;

// Insert the ellipse after the rectangle
builder.InsertNode(ellipse);
```

**왜 중요한가:** `new Shape`를 호출할 때마다 독립적인 그리기 객체가 생성됩니다. 이를 순차적으로 삽입하면 나중에 그룹화하거나 개별적으로 배치할 수 있는 모양 컬렉션을 구성하게 됩니다.

## 3단계: 모양을 그룹에 추가

모양을 그룹화하면 그룹이 단일 노드처럼 동작하므로 레이아웃 관리가 간소화됩니다. 이 단계에서는 `GroupShape`를 사용하여 **그룹에 모양 추가**하는 방법을 보여줍니다.

```csharp
// Create a GroupShape with a bounding box of 200x200 points
GroupShape group = new GroupShape(doc, 200, 200);

// Move the builder's cursor back to the start of the document
builder.MoveToDocumentStart();

// Insert the empty group into the document
builder.InsertNode(group);

// Append the previously created rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

**왜 중요한가:** `GroupShape`는 컨테이너 역할을 합니다. 그룹을 이동, 회전 또는 크기 조정하면 모든 자식 모양이 자동으로 따라갑니다. 경계 상자(200 × 200 포인트)는 자식 모양의 좌표 공간을 정의합니다.

## 4단계: 문서에 그룹 모양 삽입

이제 그룹에 사각형과 타원이 포함되었으므로 원하는 위치에 **그룹 모양 삽입**이 필요합니다. Builder가 이미 빈 그룹을 배치했지만 필요에 따라 다른 위치에 삽입할 수도 있습니다.

```csharp
// Position the group at a specific location (optional)
group.Left = 50;   // 50 points from the left margin
group.Top = 100;   // 100 points from the top margin

// Save the document with the grouped shapes
doc.Save("GroupShapeExample.docx");
```

**왜 중요한가:** `Left`와 `Top`을 조정하면 페이지 내에서 전체 그룹이 이동합니다. 문서를 저장하면 모양 계층 구조가 `.docx` 파일에 기록되어 Microsoft Word, LibreOffice 또는 호환 가능한 뷰어에서 열 수 있습니다.

## 전체 실행 가능한 예제

아래는 모든 단계를 결합한 전체 프로그램입니다. 코드를 새 콘솔 프로젝트에 복사하고 실행하면 `GroupShapeExample.docx`가 생성됩니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize a DocumentBuilder for editing the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 100;
            rectangle.Height = 50;
            rectangle.FillColor = Color.LightBlue;
            rectangle.StrokeColor = Color.DarkBlue;
            rectangle.StrokeWeight = 1.0;

            // Step 4: Create an ellipse shape
            Shape ellipse = new Shape(doc, ShapeType.Ellipse);
            ellipse.Width = 80;
            ellipse.Height = 80;
            ellipse.FillColor = Color.LightCoral;
            ellipse.StrokeColor = Color.Maroon;
            ellipse.StrokeWeight = 1.0;

            // Step 5: Create a GroupShape that will hold both shapes
            GroupShape group = new GroupShape(doc, 200, 200);
            group.Left = 50;   // optional positioning
            group.Top = 100;   // optional positioning

            // Add the rectangle and ellipse to the group
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Insert the group into the document at the current builder position
            builder.InsertNode(group);

            // Step 6: Save the document containing the grouped shapes
            doc.Save("GroupShapeExample.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**예상 출력:**  
`GroupShapeExample.docx`를 열면 연한 파란색 사각형과 연한 코랄 색 타원을 포함하는 단일 그룹이 표시되며, 두 모양 모두 200 × 200 포인트 컨테이너 안에 배치됩니다. 그룹은 Word에서 하나의 객체로 선택할 수 있어 **그룹에 모양 추가**가 성공했음을 확인할 수 있습니다.

## 일반적인 변형 및 엣지 케이스

| 상황 | 권장 조정 |
|-----------|------------------------|
| 다른 모양 유형(예: `ShapeType.Line`) | 원하는 `ShapeType`으로 모양을 생성하고 해당 기하학을 적절히 설정합니다. |
| 모양을 회전해야 함 | 그룹에 추가하기 전에 `shape.Rotation = 45;`(도) 를 사용합니다. |
| 그룹이 많은 대형 문서 | 단일 `DocumentBuilder` 인스턴스를 재사용하고, 각 그룹마다 새 Builder를 만들지 않아 메모리 오버헤드를 줄입니다. |
| DOCX 대신 PDF로 저장 | 그룹이 삽입된 후 `doc.Save("output.pdf", SaveFormat.Pdf);`를 호출합니다. |

**프로 팁:** 정밀한 배치가 필요할 때는 항상 그룹에 명시적인 `Left`와 `Top` 값을 설정하세요. 이를 생략하면 그룹이 Builder의 현재 커서 위치를 상속받아 예상치 못한 레이아웃 결과가 발생할 수 있습니다.

## 결론

이제 C#를 사용하여 Word 문서에서 **사각형 모양 만들기**, **여러 모양 추가**, **그룹에 모양 추가**, 그리고 **그룹 모양 삽입**하는 방법을 알게 되었습니다. 전체 예제는 문서 생성부터 최종 파일 저장까지의 전체 워크플로우를 보여줍니다.  

다음으로 **텍스트에 대한 모양 위치 지정**, **텍스트 래핑 적용**, **그룹화된 모양을 PDF로 내보내기**와 같은 관련 주제를 살펴보세요. 이러한 확장을 통해 Aspose.Words로 복잡하고 프로그래밍 방식의 문서 레이아웃을 구축할 수 있습니다.

## 다음에 배울 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 단계별 설명과 함께 완전한 동작 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [C#를 사용하여 Word에서 사각형 모양 만들기 – 단계별 가이드](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words for .NET을 사용하여 Word 문서에 그룹 모양 만들기](/words/english/net/working-with-shapes/add-group-shape/)
- [그림자 사각형 모양이 있는 빈 Word 문서 만들기 – 단계별 가이드](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}