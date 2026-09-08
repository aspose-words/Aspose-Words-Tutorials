---
category: general
date: 2026-09-08
description: DocumentBuilder를 사용해 Word에서 도형을 그룹화하고, 빈 Word 문서를 만든 뒤 C# 코드 몇 줄만으로 사각형
  도형을 삽입하는 방법을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create blank word doc
- insert rectangle shape word
- how to use documentbuilder
language: ko
lastmod: 2026-09-08
og_description: DocumentBuilder를 사용하여 Word에서 도형을 그룹화합니다. 이 튜토리얼에서는 빈 Word 문서를 만들고,
  사각형 도형을 삽입한 다음, 도형들을 GroupShape로 결합하는 방법을 보여줍니다.
og_image_alt: Screenshot of a Word document showing grouped shapes – group shapes
  in Word example
og_title: DocumentBuilder를 사용한 Word에서 도형 그룹화 – 전체 C# 예제
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to group shapes in Word with a DocumentBuilder, create a
    blank Word doc, and insert a rectangle shape in just a few lines of C# code.
  headline: How to group shapes in Word using DocumentBuilder – step‑by‑step guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: DocumentBuilder를 사용하여 Word에서 도형을 그룹화하는 방법 – 단계별 가이드
url: /ko/net/programming-with-shapes/how-to-group-shapes-in-word-using-documentbuilder-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DocumentBuilder를 사용하여 Word에서 도형 그룹화하기 – 단계별 가이드

Word에서 도형을 프로그래밍 방식으로 **그룹화**해야 한다면, 이 튜토리얼에서는 C#을 사용한 완전한 솔루션을 보여줍니다. **빈 Word 문서 만들기**, **DocumentBuilder** 사용, 그리고 **사각형 도형 삽입** 후 이를 타원과 그룹화하는 방법을 확인할 수 있습니다. 결과는 하나의 `GroupShape`이며, 이를 하나의 객체처럼 이동, 크기 조정 또는 스타일링할 수 있습니다.

이 가이드는 Aspose.Words for .NET 라이브러리를 사용하여 그룹화된 그래픽이 포함된 Word 문서를 생성하는 데 필요한 모든 내용을 다룹니다. 기사 마지막까지 읽으면 사각형과 타원을 하나의 도형으로 결합한 `GroupedShapes.docx`를 생성하는 실행 가능한 프로젝트를 갖게 됩니다.

## 사전 요구 사항

- .NET 6.0 이상 (코드는 .NET Framework 4.7.2+에서도 작동합니다)
- Aspose.Words for .NET NuGet 패키지 (`Aspose.Words`) – 버전 23.12 이상
- Visual Studio 2022 또는 Visual Studio Code와 같은 C# IDE
- C# 구문 및 객체 지향 프로그래밍에 대한 기본 지식

> **프로 팁:** 프로젝트를 깔끔하게 유지하려면 명령줄에서 NuGet 패키지를 설치하세요:  
> `dotnet add package Aspose.Words --version 23.12.0`

## 단계 1: 빈 Word 문서 만들기

첫 번째 작업은 빈 Word 파일을 나타내는 `Document` 객체와 콘텐츠를 추가할 수 있는 `DocumentBuilder`를 인스턴스화하는 것입니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Step 1: Create a blank Word document and a DocumentBuilder
        Document document = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(document);
```

**왜 중요한가:** `Document`는 파일 컨테이너를 제공하고, `DocumentBuilder`는 텍스트, 이미지 및 도형 삽입을 위한 유창한 API를 제공합니다. `DocumentBuilder` 없이 문서의 노드 트리를 수동으로 조작해야 하므로 오류가 발생하기 쉽습니다.

## 단계 2: 사각형 도형 삽입

사각형은 다이어그램에서 흔히 사용되는 기본 요소입니다. `InsertShape`와 `ShapeType.Rectangle`을 사용하고 너비와 높이를 포인트 단위로 지정합니다(1 pt ≈ 1/72 인치).

```csharp
        // Step 2: Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;   // distance from the left margin (points)
        rectangleShape.Top = 50;    // distance from the top margin (points)
```

**왜 중요한가:** `Left`와 `Top`을 설정하면 사각형을 페이지에 정확히 배치할 수 있으며, 이는 나중에 다른 도형과 그룹화할 때 필수적입니다. `InsertShape` 메서드는 도형을 현재 단락에 자동으로 추가합니다.

## 단계 3: 타원 도형 삽입

다음으로, 사각형 옆에 배치될 타원을 추가합니다.

```csharp
        // Step 3: Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;
```

**왜 중요한가:** 다른 `ShapeType`을 사용함으로써 동일한 `DocumentBuilder` API로 다양한 그래픽을 만들 수 있음을 보여줍니다. 타원을 사각형과 겹치게 배치하면 그룹화 효과가 명확해집니다.

## 단계 4: 두 도형 그룹화

`GroupShape`은 컨테이너 역할을 합니다. 사각형과 타원을 자식으로 추가하면 두 도형이 하나의 객체처럼 동작합니다.

```csharp
        // Step 4: Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        // Define the bounding rectangle that encloses all child shapes
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Insert the group into the document body
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);
```

**왜 중요한가:** `Bounds` 속성은 그룹이 페이지에서 어디에 위치하는지 Word에 알려줍니다. 자식 도형을 추가함으로써 개별 서식을 유지하면서도 전체 변환(이동, 회전, 크기 조정)을 가능하게 합니다.

## 단계 5: 문서 저장

마지막으로, 문서를 디스크에 저장합니다. 경로는 원하는 폴더로 변경할 수 있습니다.

```csharp
        // Step 5: Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

`GroupedShapes.docx`를 Microsoft Word에서 열면 사각형과 타원이 함께 그룹화된 것을 볼 수 있습니다. 그룹을 선택하면 두 도형이 모두 강조 표시되어 하나의 단위처럼 끌거나 크기를 조정할 수 있습니다.

### 예상 출력

- **GroupedShapes.docx**라는 이름의 Word 파일
- 첫 페이지에 위치 (50, 50)에서 **사각형** (100 pt × 50 pt) 포함
- 위치 (200, 70)에서 **타원** (80 pt × 80 pt) 포함
- 두 도형 모두 **GroupShape**의 일부이며 경계 상자는 300 pt × 200 pt

## 일반적인 변형 및 엣지 케이스

| Scenario | Adjustment |
|----------|------------|
| **다른 페이지 크기** | `document.Sections[0].PageSetup.PageWidth`와 `PageHeight`를 도형을 삽입하기 전에 설정합니다. |
| **두 개 이상의 도형** | 추가 `Shape` 객체를 생성하고 각각에 대해 `groupShape.AppendChild(newShape)`를 호출합니다. |
| **채우기 색상 적용** | `rectangleShape.FillColor = System.Drawing.Color.LightBlue;` |
| **그룹 회전** | `groupShape.Rotation = 45;` (degrees) |
| **PDF로 내보내기** | DOCX를 저장한 후 `document.Save("GroupedShapes.pdf");`를 호출합니다. |

## 전체 소스 코드 (즉시 실행 가능)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Create a blank Word document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;
        rectangleShape.Top = 50;

        // Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;

        // Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);

        // Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

코드를 새 콘솔 프로젝트에 복사하고 Aspose.Words NuGet 패키지를 복원한 뒤 실행하세요. 콘솔에 파일 위치가 확인되고, 파일을 열면 그룹화된 그래픽이 표시됩니다.

## 결론

이제 Aspose.Words `DocumentBuilder`를 사용하여 Word에서 **도형을 그룹화하는 방법**을 알게 되었습니다. 튜토리얼에서는 **빈 Word 문서 만들기**, **사각형 도형 삽입**, 타원 추가 및 이를 `GroupShape`로 결합하는 과정을 단계별로 살펴보았습니다. 이 기반을 바탕으로 C#에서 직접 더 풍부한 다이어그램, 흐름도 또는 맞춤형 그래픽을 만들 수 있습니다.

### 다음 단계는?

- **DocumentBuilder**를 사용하여 표, 머리글 및 바닥글을 만드는 방법을 탐색하세요.
- **insert rectangle shape Word** 기술을 텍스트 상자와 결합하여 주석이 있는 다이어그램을 만들세요.
- **create blank word doc**를 자동 보고서 생성 템플릿으로 사용하세요.

색상, 그라디언트 및 추가 도형을 자유롭게 실험해 보세요. 즐거운 코딩 되세요!

## 다음에 배워야 할 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 단계별 설명과 함께 완전한 작동 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Aspose.Words for .NET을 사용하여 Word 문서에 그룹 도형 만들기](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words for .NET을 사용하여 Word 문서에 도형 삽입하기](/words/english/net/working-with-shapes/insert-shape/)
- [C#을 사용하여 Word에 사각형 도형 만들기 – 단계별 가이드](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}