---
category: general
date: 2026-09-11
description: Aspose.Words를 사용하여 워드 문서를 만들고, 사각형 도형을 추가하며, 도형 크기를 설정하는 방법을 배웁니다. 정밀한
  도형 크기 조정을 위한 단계별 C# 가이드.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- set shape size
- create shapes in word
- set shape dimensions
language: ko
lastmod: 2026-09-11
og_description: C#에서 Aspose.Words를 사용하여 워드 문서를 생성합니다. 이 가이드는 사각형 도형을 추가하고, 도형 크기를
  설정하며, 프로그래밍 방식으로 도형 치수를 관리하는 방법을 보여줍니다.
og_image_alt: Screenshot of a rectangle shape inside a grouped shape in a newly created
  Word document
og_title: 도형이 포함된 Word 문서 만들기 – Aspose.Words C# 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document, add rectangle shape, and set shape
    dimensions with Aspose.Words. Step‑by‑step C# guide for precise shape sizing.
  headline: How to create word document with shapes using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: C#에서 Aspose.Words를 사용하여 도형이 포함된 Word 문서 만들기
url: /ko/net/programming-with-shapes/how-to-create-word-document-with-shapes-using-aspose-words-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words를 사용하여 C#에서 도형이 포함된 워드 문서 만들기

맞춤형 그래픽이 포함된 **워드 문서**를 생성해야 한다면 코딩만으로 가능합니다. 이 튜토리얼에서는 Word 파일을 만들고, 사각형 도형을 추가하며, 도형의 모든 차원을 제어하는 방법을 단계별로 안내합니다. 최종적으로 .NET 프로젝트 어디에든 삽입할 수 있는 재사용 가능한 스니펫을 얻을 수 있습니다.

**사각형 도형 추가**, **도형 크기 설정**, **도형 차원 설정**을 그룹 컨테이너 안에서 수행하는 방법을 배웁니다. 예제는 Aspose.Words 13.9를 사용하지만, 이후 버전에도 동일하게 적용됩니다. Aspose drawing API에 대한 사전 지식은 필요 없으며, 기본적인 C# 지식만 있으면 됩니다.

## Prerequisites

- .NET 6.0 이상 설치  
- Aspose.Words for .NET NuGet 패키지 (`Install-Package Aspose.Words`)  
- Visual Studio 2022와 같은 IDE (C#를 지원하는 편집기라면 모두 가능)  

위 도구들을 준비하면 추가 설정 없이 바로 코드를 실행할 수 있습니다.

## Step 1: Initialize the document and builder – create word document basics

첫 번째 작업은 `Document` 객체와 `DocumentBuilder`를 인스턴스화하는 것입니다. `Document`는 파일 자체를 나타내고, `DocumentBuilder`는 콘텐츠 삽입을 위한 유창한 API를 제공합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Create a new, empty Word document
        Document doc = new Document();

        // DocumentBuilder gives us a cursor to insert nodes
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:**  
문서를 미리 생성하면 깨끗한 캔버스를 확보할 수 있습니다. 빌더의 커서는 첫 번째 단락에 위치하므로, 이후 **create shapes in word** 작업을 여기서 수행하게 됩니다.

## Step 2: Build a GroupShape to hold multiple graphics

`GroupShape`는 컨테이너 역할을 하며, 전체 그룹을 하나의 단위로 이동, 회전 또는 크기 조정할 수 있습니다. 여기서는 컨테이너의 너비와 높이를 포인트 단위(1 pt ≈ 1/72 in)로 정의합니다.

```csharp
        // Define a group that is 300 pt wide and 200 pt high
        GroupShape group = new GroupShape(doc, 300, 200);

        // Position the group 50 pt from the left and top margins
        group.Left = 50;
        group.Top  = 50;
```

**Why this matters:**  
도형을 그룹화하면 레이아웃 관리가 간편해집니다. 나중에 원이나 텍스트 상자와 같은 추가 도형을 넣어도 그룹의 위치와 스케일을 그대로 상속받습니다.

## Step 3: Create a rectangle shape and configure its dimensions

이제 실제 사각형을 추가합니다. `Shape` 생성자는 문서 참조와 도형 유형을 필요로 합니다. 생성 후 **set shape size**와 **set shape dimensions**를 명시적으로 지정합니다.

```csharp
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);

        // Set the rectangle’s width to 100 pt and height to 50 pt
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height

        // Position the rectangle 10 pt from the group’s left/top edges
        rectangle.Left = 10;
        rectangle.Top  = 10;
```

**Why this matters:**  
너비, 높이, left, top을 지정하면 도형을 픽셀 단위로 정확히 제어할 수 있습니다. 이는 문서가 디자인 사양이나 인쇄 양식과 일치해야 할 때 필수적입니다.

## Step 4: Assemble the group by appending the rectangle

사각형을 `GroupShape`에 추가하면 자식 노드가 됩니다. 그룹을 문서에 삽입하기 전에 필요한 만큼 자식을 추가할 수 있습니다.

```csharp
        // Add the rectangle to the group
        group.AppendChild(rectangle);
```

**Tip:** 두 번째 도형을 추가하려면 같은 방식으로 만들고 `group.AppendChild(secondShape)`를 호출하면 됩니다. 모든 자식은 그룹의 좌표 시스템을 공유합니다.

## Step 5: Insert the grouped shape into the document and save

그룹 구성이 완료되면 현재 단락에 삽입합니다. 빌더의 `CurrentParagraph` 속성을 사용하면 기본 노드 트리에 직접 접근할 수 있습니다.

```csharp
        // Insert the group into the first paragraph of the document
        builder.CurrentParagraph.AppendChild(group);

        // Save the document to disk (adjust the path as needed)
        doc.Save("GroupShape.docx");

        // Optional: open the file automatically (Windows only)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Why this matters:**  
그룹을 단락에 추가하면 도형이 텍스트 흐름에 인라인으로 표시됩니다. 문서를 저장함으로써 **create word document** 작업이 최종 완료됩니다.

## Common variations and edge cases

| Scenario | Adjustment |
|----------|------------|
| **Different page orientation** | `doc.FirstSection.PageSetup.Orientation = Orientation.Landscape;`를 그룹을 만들기 전에 설정합니다. |
| **Multiple rectangles** | 추가 `Shape` 객체를 만들고 각각 `group.AppendChild(newRect)`를 호출합니다. |
| **Dynamic size based on content** | 이미지 크기나 텍스트 메트릭을 계산한 뒤 `rectangle.Width` / `rectangle.Height`에 할당합니다. |
| **Export to PDF** | `doc.Save` 후 `doc.Save("GroupShape.pdf", SaveFormat.Pdf);`를 호출합니다. |
| **Compatibility with older Word versions** | Word 97‑2003 호환을 위해 `SaveFormat.Doc`로 저장합니다. |

이러한 변형을 통해 동일한 핵심 로직을 다양한 실제 요구 사항에 맞게 조정할 수 있습니다.

## Full, runnable example

아래는 복사·붙여넣기만 하면 바로 실행할 수 있는 전체 프로그램입니다. 모든 `using` 지시문, `Main` 진입점, 각 라인을 설명하는 주석이 포함되어 있습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Define a group shape (300 pt × 200 pt) positioned at (50, 50)
        GroupShape group = new GroupShape(doc, 300, 200);
        group.Left = 50;
        group.Top  = 50;

        // 3️⃣ Create a rectangle (100 pt × 50 pt) positioned at (10, 10) inside the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height
        rectangle.Left = 10;
        rectangle.Top  = 10;

        // 4️⃣ Add the rectangle to the group
        group.AppendChild(rectangle);

        // 5️⃣ Insert the group into the first paragraph and save the file
        builder.CurrentParagraph.AppendChild(group);
        doc.Save("GroupShape.docx");

        // Open the resulting file automatically (optional)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Expected output:**  
*GroupShape.docx*를 열면 첫 페이지에 왼쪽/위쪽 여백으로부터 50 pt 떨어진 위치에 회색 테두리 사각형이 표시됩니다. 사각형 자체는 그룹 안에서 10 pt 만큼 오프셋되어 있으며, 차원은 코드에 지정한 값과 일치합니다.

## Conclusion

이제 Aspose.Words를 사용해 **워드 문서 생성**, **사각형 도형 추가**, 그리고 **도형 크기 설정** 및 **도형 차원 설정**을 정확히 수행하는 방법을 알게 되었습니다. 그룹형 도형 접근 방식은 레이아웃을 유연하게 유지하면서 추가 그래픽이나 텍스트 상자를 쉽게 확장할 수 있게 해줍니다.

다음으로 **create shapes in word**와 같은 주제로 원, 화살표, 맞춤 SVG 경로 등을 탐색하고, **set shape fill color** 또는 **apply rotation**을 배우세요. 다양한 측정 단위를 실험해 Word가 포인트와 센티미터를 어떻게 렌더링하는지 확인하고, 코드를 더 큰 문서 생성 파이프라인에 통합해 보세요.

행복한 코딩 되시길 바라며, 자동 보고서나 양식 작성 시 이 패턴을 자유롭게 적용해 보세요!

## What Should You Learn Next?

다음 튜토리얼들은 이 가이드에서 다룬 기술을 기반으로 하며, 단계별 코드 예제와 자세한 설명을 제공합니다.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}