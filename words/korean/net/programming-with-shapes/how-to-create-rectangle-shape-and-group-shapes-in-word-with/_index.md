---
category: general
date: 2026-09-05
description: Aspose.Words를 사용하여 Word 문서에 사각형 모양을 만든 다음, Word에서 타원 모양을 삽입하고 도형을 그룹화하는
  방법을 배워 보다 풍부한 레이아웃을 구현하세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- how to insert rectangle word
- how to insert ellipse word
- aspose.words create shapes
language: ko
lastmod: 2026-09-05
og_description: Aspose.Words를 사용하여 Word 문서에 사각형 모양을 만든 다음, 복잡한 레이아웃을 위해 Word에서 타원
  모양을 삽입하고 도형을 그룹화하는 방법을 확인하십시오.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with Aspose.Words
og_title: Word에서 사각형 도형 만들기 및 도형 그룹화 – Aspose.Words 가이드
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  headline: How to create rectangle shape and group shapes in Word with Aspose.Words
  type: TechArticle
- description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  name: How to create rectangle shape and group shapes in Word with Aspose.Words
  steps:
  - name: Pro tip
    text: Always add shapes **before** you group them. If you try to group a shape
      that is already part of another group, Aspose.Words throws an `ArgumentException`.
      Building the group in a single method prevents this runtime error.
  - name: Watch out for
    text: '* **Coordinate system** – `Left` and `Top` are measured from the page’s
      left and top margins, not from the document edge. Misunderstanding this can
      place shapes off‑page. * **Licensing** – Without a valid license, the saved
      document will contain a watermark that says “Aspose.Words for .NET Evaluatio'
  - name: What’s next?
    text: '* Explore **aspose.words create shapes** for more complex geometry such
      as `Polygon` or `Freeform`. * Combine grouped shapes with **content controls**
      to build dynamic templates. * Convert the DOCX to PDF or HTML to see how vector
      shapes are rendered across formats.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Aspose.Words를 사용하여 Word에서 사각형 도형을 만들고 도형을 그룹화하는 방법
url: /ko/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words를 사용하여 Word에서 사각형 도형을 만들고 도형을 그룹화하는 방법

Word 문서에 **사각형 도형**을 만들어야 하는 경우, 이 가이드는 Aspose.Words for .NET을 사용한 정확한 단계들을 보여줍니다. 또한 타원 도형을 삽입하고, Word에서 도형을 그룹화하며, 결과를 DOCX 파일로 저장하는 방법도 확인할 수 있습니다. 이 솔루션은 .NET 6 이상 프로젝트에서 작동하며 서버에 Microsoft Office가 설치될 필요가 없습니다.

이 튜토리얼은 프로젝트 설정부터 일반적인 레이아웃 함정 처리까지 모두 다루므로 코드를 복사해 바로 실행할 수 있습니다.

## Prerequisites

시작하기 전에 다음이 준비되어 있는지 확인하세요:

* .NET 6 SDK 이상이 설치되어 있음  
* NuGet을 지원하는 IDE (Visual Studio, Rider, VS Code 등)  
* Aspose.Words for .NET 라이선스(또는 임시 평가 키)  
* C# 및 Word 문서 구조에 대한 기본 지식  

이 항목들은 코드 컴파일과 도형이 올바르게 렌더링되도록 합니다.

## Step 1: Set up the project and add Aspose.Words

새 콘솔 프로젝트를 만들고 Aspose.Words 패키지를 추가합니다:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

패키지는 이 튜토리얼 전반에 걸쳐 사용되는 `Document`, `DocumentBuilder`, `Shape`, `GroupShape` 클래스를 제공합니다.

## Step 2: Initialize a blank document and a builder

`Document` 객체는 전체 Word 파일을 나타내고, `DocumentBuilder`는 프로그래밍 방식으로 콘텐츠를 삽입할 수 있게 해줍니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

Document doc = new Document();                 // creates an empty .docx container
DocumentBuilder builder = new DocumentBuilder(doc);
```

먼저 문서를 생성하면 이후 모든 도형 작업에 유효한 컨테이너가 보장됩니다.

## Step 3: **Create rectangle shape** and set its dimensions

사각형은 텍스트나 이미지를 담는 가장 일반적인 컨테이너입니다. 크기는 포인트 단위(1 pt ≈ 1/72 인치)로 정의합니다.

```csharp
// create a rectangle shape
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;      // 100 pt ≈ 1.39 in
rectangleShape.Height = 50;      // 50 pt ≈ 0.69 in

// optional: give the rectangle a light fill and a thin border
rectangleShape.FillColor = System.Drawing.Color.LightGray;
rectangleShape.Line.Width = 0.5;

// insert the rectangle into the document at the current cursor position
builder.InsertNode(rectangleShape);
```

이 단계가 중요한 이유: `Shape` 클래스는 기하학, 채우기 및 선 속성을 캡슐화합니다. 삽입 전에 `Width`와 `Height`를 설정하면 도형이 예상 크기로 나타납니다.

## Step 4: **How to insert ellipse word** – add an ellipse shape

타원은 아이콘, 마커 또는 장식 요소로 사용할 수 있습니다. 코드는 사각형 생성과 동일하지만 `ShapeType`만 변경됩니다.

```csharp
// create an ellipse shape
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;      // 80 pt ≈ 1.11 in
ellipseShape.Height = 80;     // a perfect circle because width = height

// style the ellipse
ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;

// place the ellipse after the rectangle
builder.InsertNode(ellipseShape);
```

`FillColor`와 `Line.Color` 속성은 외부 이미지 없이 외관을 커스터마이징하는 방법을 보여줍니다.

## Step 5: **Group shapes in Word** – combine rectangle and ellipse

그룹화하면 여러 도형을 하나의 단위로 이동, 크기 조정 또는 회전할 수 있습니다. 이는 복합 그래픽(예: 라벨이 있는 아이콘)이 필요할 때 필수적입니다.

```csharp
// create a group shape container
GroupShape groupShape = new GroupShape(doc);

// add the previously created shapes to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// optional: set the group's position on the page
groupShape.Left = 150;   // distance from the left margin in points
groupShape.Top = 100;    // distance from the top margin in points

// insert the grouped shape into the document
builder.InsertNode(groupShape);
```

`AppendChild`를 호출하면 원래 도형이 문서 흐름에서 제거되고 `GroupShape`의 자식이 됩니다. 그룹은 단일 도형처럼 동작하므로 이후 레이아웃 조정이 간편해집니다.

## Step 6: Save the document

마지막으로 문서를 디스크에 저장합니다. 지원되는 형식(`.docx`, `.pdf`, `.html` 등) 중 원하는 것을 선택할 수 있습니다. 이 튜토리얼에서는 기본 Word 형식을 유지합니다.

```csharp
// replace "YOUR_DIRECTORY" with an absolute or relative path you control
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

프로그램을 실행한 후 Microsoft Word에서 *GroupShape.docx*를 열면 사각형과 타원이 함께 그룹화되어 지정한 좌표에 배치된 것을 확인할 수 있습니다.

## Common variations and edge cases

| 상황 | 변경 내용 | 이유 |
|-----------|----------------|--------|
| **다른 크기 단위** | 인치를 사용할 경우 `ConvertUtil.InchToPoint(2.5)`, 밀리미터는 `ConvertUtil.MillimeterToPoint(30)` 사용 | 포인트가 아닌 단위로 작업할 때 코드를 읽기 쉽게 유지합니다. |
| **사각형 안에 텍스트 추가** | `Paragraph` 노드를 만들고 `Text` 속성을 설정한 뒤 `rectangleShape.AppendChild`로 추가 | 별도의 텍스트 상자 없이 도형에 라벨을 붙일 수 있습니다. |
| **그룹 회전** | `groupShape.Rotation = 45;` (도) 설정 | 대각선 배지나 워터마크를 만들 때 유용합니다. |
| **PDF로 저장** | `doc.Save("GroupShape.pdf");` 호출 | Aspose.Words가 PDF 출력 시 벡터 도형을 자동으로 래스터화합니다. |
| **여러 그룹** | 추가 `GroupShape` 인스턴스를 만들고 삽입/추가 단계를 반복 | 여러 독립적인 복합 요소가 있는 복잡한 페이지 레이아웃을 구현합니다. |

### Pro tip

도형을 **그룹화하기 전에** 반드시 추가하세요. 이미 다른 그룹에 속한 도형을 다시 그룹화하려 하면 Aspose.Words가 `ArgumentException`을 발생시킵니다. 하나의 메서드에서 그룹을 구성하면 이러한 런타임 오류를 방지할 수 있습니다.

### Watch out for

* **좌표 시스템** – `Left`와 `Top`은 페이지의 왼쪽·위쪽 여백을 기준으로 측정되며, 문서 가장자리를 기준으로 하지 않습니다. 이를 오해하면 도형이 페이지 밖에 배치될 수 있습니다.
* **라이선스** – 유효한 라이선스가 없으면 저장된 문서에 “Aspose.Words for .NET Evaluation” 워터마크가 삽입됩니다. 코드 초기에 라이선스를 적용하세요(`License license = new License(); license.SetLicense("Aspose.Words.lic");`)  

## Full source code (runnable)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Create rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
        rectangleShape.Width = 100;
        rectangleShape.Height = 50;
        rectangleShape.FillColor = System.Drawing.Color.LightGray;
        rectangleShape.Line.Width = 0.5;
        builder.InsertNode(rectangleShape);

        // 3️⃣ Create ellipse shape
        Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
        ellipseShape.Width = 80;
        ellipseShape.Height = 80;
        ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
        ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;
        builder.InsertNode(ellipseShape);

        // 4️⃣ Group rectangle and ellipse
        GroupShape groupShape = new GroupShape(doc);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.Left = 150;
        groupShape.Top = 100;
        builder.InsertNode(groupShape);

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

이 프로그램을 실행하면 설명대로 그룹화된 도형이 포함된 *GroupShape.docx*가 생성됩니다.

## Conclusion

이제 Aspose.Words를 사용해 **사각형 도형을 만들고**, **타원 도형을 삽입하며**, **Word에서 도형을 그룹화**하는 방법을 알게 되었습니다. 전체 예제는 문서 초기화부터 최종 파일 저장까지의 전체 워크플로를 보여주므로, 자동 보고서나 문서 생성 솔루션에 도형 처리를 쉽게 통합할 수 있습니다.

### What’s next?

* 더 복잡한 기하학(예: `Polygon` 또는 `Freeform`)을 위해 **aspose.words create shapes**를 탐색하세요.  
* 그룹화된 도형을 **content controls**와 결합해 동적 템플릿을 구축하세요.  
* DOCX를 PDF 또는 HTML로 변환해 벡터 도형이 다양한 포맷에서 어떻게 렌더링되는지 확인하세요.  

다양한 크기, 색상, 회전을 실험해 보세요. 도형 그룹화를 마스터하면 Word 문서 안에서 정교한 다이어그램, 배지, 맞춤 UI 요소 등을 직접 만들 수 있습니다.

## What Should You Learn Next?

다음 튜토리얼들은 이 가이드에서 다룬 기술을 기반으로 하는 관련 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함하여 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하도록 돕습니다.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}