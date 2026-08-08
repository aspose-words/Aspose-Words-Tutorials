---
category: general
date: 2026-08-07
description: Aspose.Words를 사용하여 Word에서 도형을 그룹화하고 C#로 Word 문서에 도형을 추가하는 방법. 깔끔하고 재사용
  가능한 코드를 위한 단계별 가이드를 따라보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- add shapes to word document
language: ko
lastmod: 2026-08-07
og_description: .NET용 Aspose.Words를 사용하여 Word에서 도형을 그룹화하는 방법. 이 튜토리얼에서는 Word 문서에 도형을
  추가하고, 그룹화하며, 명확한 C# 코드로 파일을 저장하는 방법을 보여줍니다.
og_image_alt: Screenshot of a rectangle and ellipse grouped in a Word document created
  with Aspose.Words
og_title: Word에서 도형을 그룹화하는 방법 – 빠른 C# 가이드
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  headline: How to group shapes in Word and add shapes to Word document
  type: TechArticle
- description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  name: How to group shapes in Word and add shapes to Word document
  steps:
  - name: Create a document and a builder
    text: A `Document` object represents the entire DOCX file. `DocumentBuilder` provides
      a convenient API for editing the document.
  - name: Add the rectangle shape
    text: A rectangle is created by specifying `ShapeType.Rectangle`. Width, height,
      and location are set in points (1 pt ≈ 1/72 in).
  - name: Add the ellipse shape
    text: The ellipse uses `ShapeType.Ellipse`. Its size and position are independent
      of the rectangle, which allows you to control the final layout of the group.
  - name: Group the two shapes
    text: '`GroupShape` acts as a container that treats its children as a single object.
      This is the essential operation for **how to group shapes in Word**.'
  - name: Insert the grouped shape into the document
    text: '`DocumentBuilder.InsertNode` places the `GroupShape` at the current cursor
      location. Because we have not moved the builder, the group appears at the start
      of the first page.'
  - name: Save the document
    text: Finally, write the DOCX file to disk. Use a full path that your application
      can write to.
  - name: Expected output
    text: Open `GroupShape.docx`. You will see a single visual object that contains
      a blue rectangle on the left and a green ellipse on the right. Selecting the
      object in Word highlights both shapes simultaneously—proof that **how to group
      shapes in Word** succeeded.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Word에서 도형을 그룹화하고 문서에 도형을 추가하는 방법
url: /ko/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word에서 도형을 그룹화하고 문서에 도형 추가하기

Word에서 **도형을 그룹화하는 방법**이 필요하다면, 이 가이드는 Aspose.Words for .NET을 사용한 전체 과정을 안내합니다. 또한 몇 줄의 C# 코드로 **Word 문서에 도형 추가**하는 방법을 배워, 보고서나 템플릿 시나리오에 바로 활용할 수 있습니다.

이 튜토리얼은 필요한 NuGet 패키지, 전체 소스 파일, 각 단계가 중요한 이유에 대한 설명을 모두 포함합니다. 마지막에는 사각형과 타원을 하나의 그룹 도형으로 결합한 DOCX를 생성할 수 있습니다.

## 전제 조건

시작하기 전에 다음이 설치되어 있는지 확인하세요:

* .NET 6.0 SDK 이상  
* Visual Studio 2022 (또는 .NET을 지원하는 IDE)  
* Aspose.Words for .NET NuGet 패키지(`Aspose.Words`) – 무료 체험판으로 테스트 가능하지만, 라이선스를 적용하면 평가 워터마크가 사라집니다  

이 항목들은 **Word 문서에 도형 추가**를 위한 유일한 외부 종속성입니다.

## Word에서 도형을 그룹화하는 방법

솔루션의 핵심은 개별 도형을 만들고 페이지에 배치한 뒤 `GroupShape`에 감싸는 것입니다. 아래 단계는 코드의 논리적 순서를 그대로 따릅니다.

### 단계 1: 문서와 빌더 생성

`Document` 객체는 전체 DOCX 파일을 나타냅니다. `DocumentBuilder`는 문서를 편집하기 위한 편리한 API를 제공합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create an empty Word document
Document doc = new Document();

// DocumentBuilder lets you insert nodes, text, and shapes
DocumentBuilder builder = new DocumentBuilder(doc);
```

*왜 중요한가*: `Document`는 모든 Word 요소의 컨테이너입니다. `DocumentBuilder`는 현재 커서 위치를 추적하는데, 이는 나중에 그룹 도형을 삽입할 때 필요합니다.

### 단계 2: 사각형 도형 추가

`ShapeType.Rectangle`을 지정하여 사각형을 생성합니다. 너비, 높이, 위치는 포인트 단위(1 pt ≈ 1/72 in)로 설정합니다.

```csharp
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;               // 100 pt wide
rectangleShape.Height = 50;               // 50 pt tall
rectangleShape.Left = 0;                  // X‑coordinate
rectangleShape.Top = 0;                   // Y‑coordinate
rectangleShape.StrokeColor = Color.Blue; // Outline color
```

*왜 중요한가*: `StrokeColor`를 설정하면 문서를 열었을 때 도형이 보이게 됩니다. 실내 색이 필요하면 `FillColor`로 채울 수도 있습니다.

### 단계 3: 타원 도형 추가

타원은 `ShapeType.Ellipse`를 사용합니다. 크기와 위치는 사각형과 독립적이어서 그룹 레이아웃을 자유롭게 조정할 수 있습니다.

```csharp
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;
ellipseShape.Height = 80;
ellipseShape.Left = 120;                  // Placed to the right of the rectangle
ellipseShape.Top = 0;
ellipseShape.StrokeColor = Color.Green;
```

*왜 중요한가*: 타원의 `Left = 120` 위치를 지정하면 사각형과 겹치지 않아 그룹이 시각적으로 구분됩니다.

### 단계 4: 두 도형을 그룹화

`GroupShape`는 자식들을 하나의 객체로 취급하는 컨테이너 역할을 합니다. 이것이 **Word에서 도형을 그룹화하는 방법**의 핵심 작업입니다.

```csharp
GroupShape groupShape = new GroupShape(doc);
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);
```

*왜 중요한가*: 그룹화하면 두 도형을 동시에 이동, 크기 조정, 회전할 수 있습니다. `groupShape`에 적용된 모든 변형이 자식 도형에 전파됩니다.

### 단계 5: 그룹 도형을 문서에 삽입

`DocumentBuilder.InsertNode`는 현재 커서 위치에 `GroupShape`를 배치합니다. 빌더를 이동하지 않았기 때문에 그룹은 첫 페이지 시작 부분에 나타납니다.

```csharp
builder.InsertNode(groupShape);
```

*왜 중요한가*: 별도의 단락이나 표 셀 없이 노드를 직접 삽입하면 그룹이 문서 흐름의 일부가 됩니다.

### 단계 6: 문서 저장

마지막으로 DOCX 파일을 디스크에 기록합니다. 애플리케이션이 쓸 수 있는 전체 경로를 사용하세요.

```csharp
doc.Save(@"C:\Temp\GroupShape.docx");
```

*왜 중요한가*: `doc.Save`가 모든 변경 사항을 최종화합니다. 생성된 파일은 Microsoft Word, LibreOffice 또는 DOCX를 지원하는 모든 뷰어에서 열 수 있습니다.

## 전체 소스 파일

아래 코드를 새 콘솔 프로젝트(`dotnet new console`)에 복사하고 실행하세요. 프로그램은 `GroupShape.docx`라는 파일을 생성하며, 여기에는 그룹화된 사각형과 타원이 포함됩니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeGrouping
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Define a rectangle shape
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
            rectangleShape.Width = 100;
            rectangleShape.Height = 50;
            rectangleShape.Left = 0;
            rectangleShape.Top = 0;
            rectangleShape.StrokeColor = Color.Blue;

            // Step 3: Define an ellipse shape
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
            ellipseShape.Width = 80;
            ellipseShape.Height = 80;
            ellipseShape.Left = 120;
            ellipseShape.Top = 0;
            ellipseShape.StrokeColor = Color.Green;

            // Step 4: Group the two shapes together
            GroupShape groupShape = new GroupShape(doc);
            groupShape.AppendChild(rectangleShape);
            groupShape.AppendChild(ellipseShape);

            // Step 5: Insert the grouped shape into the document
            builder.InsertNode(groupShape);

            // Step 6: Save the document
            doc.Save(@"C:\Temp\GroupShape.docx");
        }
    }
}
```

### 예상 결과

`GroupShape.docx`를 열면 왼쪽에 파란 사각형, 오른쪽에 초록 타원이 포함된 하나의 시각 객체를 확인할 수 있습니다. Word에서 해당 객체를 선택하면 두 도형이 동시에 강조 표시되어 **Word에서 도형을 그룹화하는 방법**이 성공했음을 증명합니다.

## 자주 묻는 질문 및 예외 상황

* **두 개 이상 도형을 추가할 수 있나요?**  
  네. 그룹에 삽입하기 전에 추가 `Shape`마다 `groupShape.AppendChild`를 호출하면 됩니다.

* **그룹을 회전하려면 어떻게 하나요?**  
  그룹이 완성된 뒤 `groupShape.RotationAngle = 45;`(각도는 도) 를 설정하면 됩니다.

* **`doc.UpdatePageLayout()`을 호출해야 하나요?**  
  이 시나리오에서는 필요 없습니다. 문서를 저장하면 레이아웃이 자동으로 업데이트됩니다.

* **라이선스가 코드에 어떤 영향을 미치나요?**  
  유효한 Aspose.Words 라이선스(`License license = new License(); license.SetLicense("Aspose.Words.lic");`)를 적용하면 생성된 문서에 평가 워터마크가 나타나지 않습니다.

## 결론

이제 Aspose.Words for .NET을 사용해 **Word에서 도형을 그룹화하는 방법**과 **Word 문서에 도형을 추가하는 방법**을 알게 되었습니다. 튜토리얼에서는 문서 생성, 개별 도형 정의, 그룹화, 삽입, 저장 순으로 진행했습니다.

다음 단계로 시도해 볼 수 있는 내용:

* 그룹에 텍스트 상자나 그림 추가  
* 채우기 색, 선 스타일, 그림자 효과 변경  
* 표나 헤더 내부에 도형 그룹화  

이러한 확장을 통해 코드를 깔끔하게 유지하면서 복잡한 Word 템플릿을 프로그래밍 방식으로 만들 수 있습니다. 즐거운 코딩 되세요!


## 다음에 배워야 할 내용은?


다음 튜토리얼은 이 가이드에서 다룬 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 제공하여 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용할 수 있도록 돕습니다.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Word Document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}