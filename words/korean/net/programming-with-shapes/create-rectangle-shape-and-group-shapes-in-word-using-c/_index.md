---
category: general
date: 2026-09-08
description: C#를 사용하여 Word 문서에 사각형 도형을 만들기. 도형 크기 설정, 여러 도형을 그룹화하고, 프로그래밍으로 빈 Word
  문서를 만드는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- set shape size
- group multiple shapes
- create blank word document
language: ko
lastmod: 2026-09-08
og_description: C#를 사용하여 Word 문서에 사각형 모양을 만들기. 이 가이드는 모양 크기 설정, 여러 모양을 그룹화 및 프로그래밍
  방식으로 빈 Word 문서를 만드는 방법을 보여줍니다.
og_image_alt: Screenshot showing how to create rectangle shape in a Word document
  using C#
og_title: C#를 사용하여 Word에서 사각형 도형을 만들고 도형을 그룹화하기
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Create rectangle shape in a Word document with C#. Learn to set shape
    size, group multiple shapes, and create blank Word document programmatically.
  headline: Create rectangle shape and group shapes in Word using C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: C#를 사용하여 Word에서 사각형 도형을 만들고 도형을 그룹화하기
url: /ko/net/programming-with-shapes/create-rectangle-shape-and-group-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#를 사용하여 Word에서 사각형 모양 만들기 및 모양 그룹화

Word 파일 안에 **사각형 모양 만들기**가 필요하다면, 이 튜토리얼은 완전하고 바로 실행할 수 있는 솔루션을 제공합니다. 모양 크기 설정, 여러 모양을 그룹화하고, 처음부터 빈 Word 문서를 만드는 방법을 Aspose.Words for .NET 라이브러리를 사용해 보여드립니다.

프로그램matically Word 문서를 다루는 일은 종종 작은 디테일을 많이 다루는 것처럼 느껴집니다. 이 가이드를 끝까지 따라오면 사각형과 타원이 함께 그룹화된 `.docx` 파일을 생성하는 단일 메서드를 얻게 되며, 이후 추가 편집이나 인쇄에 바로 사용할 수 있습니다.

## Prerequisites

시작하기 전에 다음이 준비되어 있는지 확인하세요:

* .NET 6.0 이상 (.NET Framework 4.6+에서도 동작)
* **Aspose.Words for .NET** 라이선스 사본 (무료 평가 키 사용 가능)
* Visual Studio 2022 또는 Visual Studio Code 같은 IDE
* C# 문법에 대한 기본적인 이해

`Aspose.Words` 외에 추가 NuGet 패키지는 필요하지 않습니다.

## Step 1: Create a blank Word document

첫 번째 단계는 모양을 담을 빈 문서를 만드는 것입니다. 이는 *빈 Word 문서 만들기* 요구 사항을 충족합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty Word document
Document doc = new Document();

// The document already contains one section and one empty paragraph
// You can add additional sections later if needed
```

빈 문서를 만들면 깨끗한 캔버스를 얻을 수 있습니다. `Document` 객체는 전체 `.docx` 파일을 나타내며, `FirstSection.Body.FirstParagraph`는 새 노드를 삽입할 기본 위치입니다.

## Step 2: Create rectangle shape

이제 사각형을 추가합니다. 여기서 **사각형 모양 만들기** 작업이 수행됩니다.

```csharp
// Initialize a DocumentBuilder to simplify node insertion
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape instance
Shape rectangle = new Shape(doc, ShapeType.Rectangle);

// Set the rectangle's size (width and height) and position
rectangle.Width  = 100;   // points; 1 point = 1/72 inch
rectangle.Height = 50;
rectangle.Left   = 10;    // distance from the left edge of the container
rectangle.Top    = 20;    // distance from the top edge of the container

// Optional: give the rectangle a visible border
rectangle.StrokeColor = Color.Blue;
rectangle.FillColor   = Color.LightGray;
```

크기를 직접 지정함으로써 **모양 크기 설정** 키워드에 답합니다. 모든 크기 값은 포인트 단위이며, 최종 문서에서 모양이 어떻게 보일지 정확하게 제어할 수 있습니다.

## Step 3: Create an additional shape (ellipse)

일반적인 사용 사례는 여러 모양을 결합하는 것입니다. 여기서는 나중에 같은 컨테이너에 넣을 타원을 추가합니다.

```csharp
// Create an ellipse shape instance
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width  = 80;
ellipse.Height = 80;
ellipse.Left   = 120;   // Position it to the right of the rectangle
ellipse.Top    = 30;

// Give the ellipse a distinct border and fill
ellipse.StrokeColor = Color.DarkGreen;
ellipse.FillColor   = Color.LightYellow;
```

두 모양은 아직 독립적인 상태입니다. 다음 단계에서는 **여러 모양 그룹화** 방법을 보여줍니다.

## Step 4: Group shapes in Word

모양을 그룹화하면 하나의 단위로 이동, 크기 조정 또는 서식 지정이 가능합니다. 이는 **Word에서 모양 그룹화** 및 **여러 모양 그룹화** 요구 사항을 충족합니다.

```csharp
// Create a GroupShape container that will hold the rectangle and ellipse
GroupShape group = new GroupShape(doc);

// Define the container's bounding box – it must be large enough for all children
group.Bounds = new RectangleF(0, 0, 300, 200);

// Append the group to the document's first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(group);

// Add the rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

`GroupShape.Bounds` 속성은 자식 모양들의 좌표계를 결정합니다. 사각형과 타원을 동일한 `GroupShape` 안에 배치하면 나중에 하나의 호출로 함께 이동하거나 회전시킬 수 있습니다.

## Step 5: Save the document

마지막으로 문서를 디스크에 저장합니다. 파일에는 방금 만든 그룹화된 모양이 포함됩니다.

```csharp
// Choose an output path – ensure the directory exists and you have write permission
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");

// Save the document in DOCX format
doc.Save(outputPath);
```

프로그램을 실행한 후 `GroupedShapes.docx`를 Microsoft Word에서 열어보세요. 사각형과 타원이 함께 그룹화된 것을 확인할 수 있으며, 하나의 모양을 선택하면 다른 모양도 함께 선택됩니다. 이는 그룹화가 성공했음을 의미합니다.

## Full source code

다음 전체 프로그램을 새 콘솔 앱 프로젝트에 복사하고 실행하세요. 추가 코드는 필요하지 않습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
using System.Drawing;
using System.IO;

class Program
{
    static void Main()
    {
        // Step 1: create a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: create rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 100,
            Height = 50,
            Left   = 10,
            Top    = 20,
            StrokeColor = Color.Blue,
            FillColor   = Color.LightGray
        };

        // Step 3: create ellipse shape
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width  = 80,
            Height = 80,
            Left   = 120,
            Top    = 30,
            StrokeColor = Color.DarkGreen,
            FillColor   = Color.LightYellow
        };

        // Step 4: group the shapes
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new RectangleF(0, 0, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);
        group.AppendChild(rectangle);
        group.AppendChild(ellipse);

        // Step 5: save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Expected output

프로그램을 실행하면 `GroupedShapes.docx`가 생성됩니다. Word에서 파일을 열면 다음과 같이 표시됩니다:

* 파란색 테두리와 연회색 채우기를 가진 **사각형** (100 pt × 50 pt)
* 짙은 녹색 테두리와 연노란색 채우기를 가진 **타원** (80 pt × 80 pt)
* 두 모양이 하나의 그룹 안에 있어 하나를 이동하면 다른 것도 함께 이동합니다.

## Common questions and edge cases

| 질문 | 답변 |
|----------|--------|
| **두 개 이상의 모양을 그룹에 추가할 수 있나요?** | 네. 추가 `Shape` 객체를 만들고 각각 `group.AppendChild(yourShape)`를 호출하면 됩니다. |
| **그룹을 회전하려면 어떻게 해야 하나요?** | `group.RotationAngle = 45;` (도) 로 설정합니다. 모든 자식 모양이 함께 회전합니다. |
| **문서를 저장한 뒤에 모양을 그룹화할 수 있나요?** | 저장하기 전에 문서 구조를 수정해야 합니다. 저장 후에는 파일을 다시 로드하고 모양을 찾아 새 그룹을 만들어야 합니다. |
| **객체를 직접 해제해야 하나요?** | Aspose.Words는 자체 리소스를 관리하지만, 스트림을 직접 열 경우 `FileStream` 객체는 해제해 주어야 합니다. |
| **코드가 .doc(바이너리) 형식에서도 동작하나요?** | 네, `doc.Save("output.doc")` 로 변경하면 됩니다. 그룹화 동작은 동일합니다. |

## Conclusion

이제 C#를 사용해 Word 파일 안에서 **사각형 모양 만들기**, **모양 크기 설정**, **여러 모양 그룹화**를 수행하는 방법을 알게 되었습니다. 이 접근법을 통해 복잡한 다이어그램, 워터마크, 템플릿 기반 보고서를 수동 편집 없이 프로그래밍으로 생성할 수 있습니다.

### Next steps

* **Word에서 모양 그룹화**를 더 탐구하여 텍스트 상자나 이미지를 같은 그룹에 추가해 보세요.
* `SetShapeSize` 패턴을 활용해 페이지 레이아웃에 따라 동적으로 크기를 계산해 보세요.
* 이 기술을 메일 병합 필드와 결합해 대규모 개인화 문서를 자동으로 생성해 보세요.

다양한 모양 종류, 색상, 그룹 변환을 실험해 보세요. 즐거운 코딩 되세요!


## What Should You Learn Next?

다음 튜토리얼들은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함하고 있어 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [Aspose.Words for .NET을 사용하여 Word 문서에 그룹 모양 만들기](/words/english/net/working-with-shapes/add-group-shape/)
- [그림자 사각형 모양이 있는 빈 Word 문서 만들기 – 단계별 가이드](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [그림자 사각형이 포함된 Word 문서 만들기 – 단계별 가이드](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}