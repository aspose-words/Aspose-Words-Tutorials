---
category: general
date: 2026-10-04
description: C#를 사용하여 Word에서 도형을 그룹화하는 방법을 배웁니다. 이 가이드는 사각형 도형 삽입, 여러 도형을 그룹화 및 프로그래밍
  방식으로 빈 Word 파일을 만드는 방법을 보여줍니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- insert rectangle shape
- group multiple shapes
- append child to group
- create blank word file
language: ko
lastmod: 2026-10-04
og_description: C#를 사용하여 Word에서 도형을 그룹화합니다. 이 단계별 가이드를 따라 사각형 도형을 삽입하고, 여러 도형을 그룹화하며,
  DocumentBuilder로 빈 Word 파일을 생성하세요.
og_image_alt: Screenshot of grouped rectangle and ellipse shapes inside a Word document
og_title: C#로 Word에서 도형 그룹화 – 완전한 DocumentBuilder 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  headline: How to group shapes in Word with C# and DocumentBuilder
  type: TechArticle
- description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  name: How to group shapes in Word with C# and DocumentBuilder
  steps:
  - name: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
    text: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
  - name: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
    text: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
  - name: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
    text: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
  - name: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
    text: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
  - name: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
    text: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shape handling
- DocumentBuilder
title: C#와 DocumentBuilder를 사용하여 Word에서 도형을 그룹화하는 방법
url: /ko/java/images-shapes/how-to-group-shapes-in-word-with-c-and-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#와 DocumentBuilder를 사용하여 Word에서 도형 그룹화하는 방법

C# 애플리케이션에서 **Word의 도형을 그룹화**해야 할 경우, 이 튜토리얼에서는 정확한 방법을 보여줍니다. *사각형 도형 삽입* 방법을 보고, 여러 그림을 하나의 그룹으로 결합한 다음, 마지막으로 **그룹화된 객체가 포함된 빈 Word 파일을 생성**하는 과정을 확인할 수 있습니다.

도형 작업은 보고서, 청구서 또는 맞춤 템플릿을 프로그래밍 방식으로 생성할 때 흔히 요구되는 기능입니다. 이 가이드를 마치면 Aspose.Words를 참조하는 모든 .NET 프로젝트에 삽입할 수 있는 재사용 가능한 코드 스니펫을 얻게 됩니다.

## 배울 내용

- 처음부터 빈 Word 문서를 생성합니다.  
- `DocumentBuilder`를 사용하여 사각형 도형과 타원을 삽입합니다.  
- `GroupShape`에 여러 도형을 **그룹화**합니다.  
- 계층 구조를 만들기 위해 **append child to group**을 사용합니다.  
- 파일을 디스크에 저장하고 결과를 확인합니다.

Aspose.Words에 대한 사전 경험은 필요하지 않지만, C# 및 .NET 개발에 대한 기본적인 이해가 있어야 합니다.

## 전제 조건

| Requirement | Reason |
|-------------|--------|
| .NET 6.0 or later | C# 코드 실행을 위한 런타임을 제공합니다. |
| Aspose.Words for .NET (latest version) | `Document`, `DocumentBuilder`, 및 도형 클래스를 제공합니다. |
| An IDE such as Visual Studio 2022 (or VS Code) | 샘플을 컴파일하고 실행하기 쉽게 해줍니다. |
| Write permission to a folder on your machine | `doc.save` 호출에 필요합니다. |

NuGet을 통해 Aspose.Words를 설치합니다:

```bash
dotnet add package Aspose.Words
```

---

## Word에서 도형 그룹화 – 단계별 가이드

아래는 전체 실행 가능한 프로그램입니다. 각 섹션을 자세히 설명하여 코드가 **왜** 이렇게 작성되었는지, **무엇을** 하는지 이해할 수 있도록 합니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

namespace WordShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // -------------------------------------------------
            // Step 1: create a blank Word file
            // -------------------------------------------------
            // The Document constructor creates an empty .docx container.
            Document doc = new Document();

            // -------------------------------------------------
            // Step 2: initialize DocumentBuilder to add content
            // -------------------------------------------------
            // DocumentBuilder is the high‑level API for inserting text,
            // images, tables, and shapes into the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // -------------------------------------------------
            // Step 3: insert individual shapes
            // -------------------------------------------------
            // Insert a rectangle shape – this demonstrates the
            // "insert rectangle shape" keyword in practice.
            Shape rectangle = builder.InsertShape(
                ShapeType.Rectangle,   // shape type
                100,                  // width in points
                50);                  // height in points

            // Position the rectangle a little away from the left margin.
            rectangle.Left = 100;   // points from the left edge
            rectangle.Top = 100;    // points from the top of the page

            // Insert an ellipse shape to accompany the rectangle.
            Shape ellipse = builder.InsertShape(
                ShapeType.Ellipse,
                80,
                80);
            ellipse.Left = rectangle.Left + rectangle.Width + 20; // place right of rectangle
            ellipse.Top = rectangle.Top; // align tops

            // -------------------------------------------------
            // Step 4: create a GroupShape and append children
            // -------------------------------------------------
            // A GroupShape acts like a container; any shape added to it
            // moves together with the group. This fulfills the
            // "group multiple shapes" requirement.
            GroupShape group = builder.InsertGroupShape();

            // The "append child to group" operation builds the hierarchy.
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Optional: give the group a name for later reference.
            group.Name = "MyShapeGroup";

            // -------------------------------------------------
            // Step 5: save the document containing the grouped shapes
            // -------------------------------------------------
            string outputPath = @"GroupedShapes.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### 각 단계가 중요한 이유

1. **빈 Word 파일을 생성** – 깨끗한 문서로 시작하면 숨겨진 서식이 도형 위치에 영향을 주는 것을 방지합니다.  
2. **DocumentBuilder 초기화** – `DocumentBuilder`는 저수준 노드 조작을 추상화하여 레이아웃에 집중할 수 있게 합니다.  
3. **개별 도형 삽입** – 그룹화하기 전에 별개의 객체(`insert rectangle shape`와 타원)가 필요합니다. `Left`와 `Top`을 조정하면 도형이 나란히 배치됩니다.  
4. **여러 도형 그룹화** – `GroupShape`를 만들고 **append child to group**을 사용하면 두 개의 독립된 그림을 하나의 논리적 단위로 합칩니다. 그룹을 이동하거나 크기를 조정하면 두 자식 모두 동시에 영향을 받습니다.  
5. **문서 저장** – 최종 파일 `GroupedShapes.docx`를 Microsoft Word에서 열어 사각형과 타원이 실제로 그룹화되었는지 확인할 수 있습니다(하나를 선택하면 두 도형이 함께 움직입니다).

### 예상 출력

Microsoft Word에서 `GroupedShapes.docx`를 엽니다:

- 사각형과 타원이 나란히 배치된 것을 볼 수 있습니다.  
- 어느 도형을 선택해도 두 도형 모두 강조 표시되어 같은 그룹에 속함을 확인합니다.  
- 그룹을 하나의 객체처럼 끌어다 놓거나, 크기를 조정하거나, 서식을 적용할 수 있습니다.

![Diagram of grouped rectangle and ellipse inside a Word document](https://example.com/grouped-shapes.png){: .center-image alt="Word 문서 내부에 그룹화된 사각형과 타원의 다이어그램"}

*스크린샷은 최종 그룹화된 도형을 보여줍니다.*

---

## 사각형 도형 삽입 – 크기 및 스타일 사용자 지정

특정 채우기 색상이나 테두리를 가진 사각형이 필요하면, 삽입 후 `Shape` 객체를 수정합니다:

```csharp
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.LineWidth = 2.0; // points
```

`Shape` 클래스의 이러한 속성은 모든 도형 유형에 적용되며, 사각형에만 국한되지 않습니다. **append child to group**을 호출하기 전에 스타일을 조정하면 그룹이 설정한 시각적 속성을 상속합니다.

---

## 여러 도형 그룹화 – 두 개 이상의 객체 처리

예제에서는 사각형과 타원을 그룹화하지만, 원하는 만큼의 도형을 추가할 수 있습니다:

```csharp
// Create additional shapes as needed
Shape triangle = builder.InsertShape(ShapeType.Triangle, 60, 60);
triangle.Left = ellipse.Left + ellipse.Width + 20;
triangle.Top = ellipse.Top;

// Append the new shape to the existing group
group.AppendChild(triangle);
```

**팁:** 복잡한 그룹을 만든 후에는 레이아웃을 잠궈 실수로 변경되는 것을 방지할 수 있습니다:

```csharp
group.LockAspectRatio = true;
group.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
group.RelativeVerticalPosition = RelativeVerticalPosition.Margin;
```

---

## Append child to group – 순서가 중요합니다

`AppendChild`를 호출하는 순서가 Z‑order(어떤 도형이 위에 표시되는지)를 정의합니다. 샘플에서는 사각형을 먼저 추가하고 그 다음에 타원을 추가하므로, 두 도형이 겹칠 경우 타원이 사각형 위에 표시됩니다. 순서를 바꾸려면 `RemoveChild`를 호출한 뒤 다시 추가하면 됩니다:

```csharp
group.RemoveChild(ellipse);
group.AppendChild(ellipse); // now ellipse is on top
```

---

## 빈 Word 파일 생성 – 재사용 가능한 도우미 메서드

애플리케이션에서 새 문서가 자주 필요한다면, 생성 로직을 캡슐화하세요:

```csharp
/// <summary>
/// Returns a new empty Document with a single section.
/// </summary>
static Document CreateBlankWordFile()
{
    Document emptyDoc = new Document();
    // Optionally set default page size, margins, etc.
    emptyDoc.FirstSection.PageSetup.PageWidth = 595;  // A4 width in points
    emptyDoc.FirstSection.PageSetup.PageHeight = 842; // A4 height in points
    return emptyDoc;
}
```

그런 다음 메인 프로그램의 `new Document()` 라인을 `CreateBlankWordFile()`로 교체할 수 있습니다. 이렇게 하면 **빈 Word 파일 생성** 개념을 재사용 가능한 방식으로 보여줍니다.

---

## 흔히 발생하는 문제와 회피 방법

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| 도형이 페이지 밖에 표시됨 | `Left`/`Top` 기본값이 0이어서 도형이 여백에 배치됩니다. | 삽입 후 `Left`와 `Top`을 명시적으로 설정합니다. |
| 그룹이 서식을 잃음 | 그룹에 추가된 후 자식 도형을 변경하면 그룹 레이아웃이 깨질 수 있습니다. | `AppendChild` 호출 **전**에 모든 시각적 속성을 적용합니다. |
| 저장된 파일이 비어 있음 | `DocumentBuilder`가 노드를 추가하지 않았거나, `doc.Save`가 다른 `Document` 인스턴스에 호출되었습니다. | 작성한 동일한 `Document`를 저장하고 있는지 확인합니다. |
| Word에서 호환성 경고 | 지원되지 않는 최신 도형 기능을 사용함 |  |

## 다음에 배울 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 전체 코드 예제와 단계별 설명이 포함되어 있어 추가 API 기능을 숙달하고 프로젝트에서 대체 구현 방법을 탐색하는 데 도움이 됩니다.

- [Aspose.Words for .NET을 사용하여 Word 문서에 그룹 도형 만들기](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words for .NET을 사용하여 Word 문서에 도형 삽입](/words/english/net/working-with-shapes/insert-shape/)
- [C#를 사용하여 Word에 사각형 도형 만들기 – 단계별 가이드](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}