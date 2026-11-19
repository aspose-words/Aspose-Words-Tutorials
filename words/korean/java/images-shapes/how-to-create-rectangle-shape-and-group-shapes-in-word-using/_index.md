---
category: general
date: 2026-11-18
description: C#를 사용하여 Word 문서에 사각형 도형을 만드는 방법을 배웁니다. 이 가이드는 도형 크기 설정, 도형 위치 설정 및 Word에서
  도형을 그룹화하는 방법도 다룹니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- set shape size
- group shapes in word
- set shape dimensions
- set shape position
language: ko
lastmod: 2026-11-18
og_description: C#를 사용하여 Word 파일에 사각형 모양을 만들고, 모양 크기 설정, 위치 설정 및 Word에서 모양을 그룹화하는
  방법을 배웁니다.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape created with C#
og_title: C#를 사용해 Word에서 사각형 도형을 만들고 도형을 그룹화하기
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  headline: How to create rectangle shape and group shapes in Word using C#
  type: TechArticle
- description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  name: How to create rectangle shape and group shapes in Word using C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert a group shape
    text: '```csharp // Step 2: Insert a group shape that will hold multiple child
      shapes GroupShape group = builder.InsertGroupShape(); ```'
  - name: Create the rectangle and set its size
    text: '```csharp // Step 3: Create a rectangle shape, set its size, and add it
      to the group Shape rectangle = new Shape(doc, ShapeType.Rectangle); rectangle.Width
      = 100; // set shape size (width) in points rectangle.Height = 50; // set shape
      size (height) in points group.AppendChild(rectangle); ```'
  - name: Create the ellipse, set dimensions, and position it
    text: '```csharp // Step 4: Create an ellipse shape, set its size and position,
      and add it to the group Shape ellipse = new Shape(doc, ShapeType.Ellipse); ellipse.Width
      = 80; // set shape dimensions (width) ellipse.Height = 80; // set shape dimensions
      (height) ellipse.Left = 120; // set shape position rela'
  - name: Save the document
    text: '```csharp // Step 5: Save the document containing the grouped shapes doc.Save("GroupShape.docx");
      Console.WriteLine("Document saved successfully."); } } ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: C#를 사용하여 Word에서 사각형 도형을 만들고 도형을 그룹화하는 방법
url: /ko/java/images-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-using/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word에서 C#을 사용하여 사각형 도형을 만들고 도형을 그룹화하는 방법

Word 문서에 **사각형 도형을 만들**어야 할 경우, 이 튜토리얼은 완전하고 바로 실행할 수 있는 솔루션을 보여줍니다. 도형 크기 설정, 도형 위치 설정, 그리고 Word에서 도형을 그룹화하여 하나의 객체처럼 동작하도록 하는 방법을 확인할 수 있습니다.

프로그래밍 방식으로 보고서, 청구서 또는 다이어그램을 생성할 때 도형 작업은 일반적인 요구 사항입니다. 이 가이드를 끝까지 따라오면 Aspose.Words for .NET을 사용하여 사각형, 타원 및 그룹화된 컨테이너를 포함하는 `.docx` 파일을 생성할 수 있게 됩니다.

## 사전 요구 사항

- .NET 6.0 SDK 또는 그 이후 버전 (코드는 .NET Framework 4.7+에서도 작동합니다)
- Aspose.Words for .NET NuGet 패키지 (`Install-Package Aspose.Words`)
- 코드 편집기 또는 IDE (Visual Studio, VS Code, Rider 등)

추가 라이브러리는 필요하지 않습니다.

## Word에서 사각형 도형을 만들고 도형을 그룹화하는 방법

핵심 단계는 다음과 같습니다:

1. **빈 문서 만들기** 및 `DocumentBuilder` 생성.
2. **`GroupShape` 삽입** – 개별 도형을 보관할 컨테이너.
3. **사각형 도형 만들기**, 크기 설정 및 그룹에 추가.
4. **타원 도형 만들기**, 크기와 위치 설정 후 그룹에 추가.
5. **문서 저장**.

각 단계는 아래에서 설명되며, 전체 소스 코드는 설명 뒤에 제공합니다.

### 단계 1: 문서 및 빌더 초기화

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document`는 전체 Word 파일을 나타내고, `DocumentBuilder`는 내용을 삽입하기 위한 유창한 API를 제공합니다. 도형을 추가하기 전에 이들을 초기화하는 것이 필수입니다.

### 단계 2: 그룹 도형 삽입

```csharp
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape group = builder.InsertGroupShape();
```

`GroupShape`는 컨테이너처럼 동작하며, 모든 자식 도형이 함께 이동합니다. 이동, 회전 또는 삭제와 같은 집합 변환이 필요할 때 Word에서 **도형을 그룹화**하는 권장 방법입니다.

### 단계 3: 사각형 만들기 및 크기 설정

```csharp
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle);
```

여기서는 `Width`와 `Height`를 할당하여 **사각형 도형을 만들**고 **도형 크기를 설정**합니다. Aspose.Words에서 크기는 포인트 단위(1 pt ≈ 1/72 in)로 표현됩니다. 차원을 명시적으로 설정하면 사각형이 정확히 원하는 대로 표시됩니다.

### 단계 4: 타원 만들기, 차원 설정 및 위치 지정

```csharp
        // Step 4: Create an ellipse shape, set its size and position, and add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position relative to the group
        group.AppendChild(ellipse);
```

타원의 **도형 차원 설정**은 너비와 높이가 동일하여 완벽한 원을 만듭니다. `Left` 속성은 **도형 위치 설정**을 보여줍니다: 타원은 그룹 원점에서 오른쪽으로 120 pt 시작하므로 사각형과 겹치지 않습니다.

### 단계 5: 문서 저장

```csharp
        // Step 5: Save the document containing the grouped shapes
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document saved successfully.");
    }
}
```

저장은 Word 파일을 디스크에 기록합니다. Microsoft Word에서 `GroupShape.docx`를 열어 사각형과 타원이 올바르게 그룹화되고 위치했는지 확인할 수 있습니다.

## 도형 차원 및 크기 설정 – 자세히 살펴보기

- **포인트와 인치**: 72 pt = 1 in. 인치를 선호한다면 72를 곱합니다(예: 2.5 in은 `2.5 * 72`).
- **자동 스케일링**: `Width` 또는 `Height`를 생략하면 도형은 기본 크기를 사용합니다. 레이아웃 예기치를 방지하려면 명시적으로 **도형 크기 설정**을 하세요.
- **종횡비**: `Ellipse`와 같은 도형에서는 `Width`와 `Height`를 동일하게 유지하면 원 형태가 유지됩니다.

## Word에서 도형 위치 지정

`Left`와 `Top` 속성은 도형이 컨테이너(그룹 또는 페이지) 내부에서 이동하는 오프셋을 제어합니다. 양수 값은 도형을 오른쪽/아래로 이동시키고, 음수 값은 왼쪽/위로 이동시킵니다. 그룹화할 경우 위치는 그룹 원점에 상대적이므로 레이아웃 계산이 간단해집니다.

## Aspose.Words를 사용한 Word 도형 그룹화

그룹화는 여러 도형을 하나의 단위로 동작하게 하고자 할 때 필수적입니다. `GroupShape` 객체:

- `AppendChild`를 지원하여 모든 `Shape`(사각형, 타원, 이미지 등)를 추가할 수 있습니다.
- 한 번의 호출로 전체 그룹을 이동, 회전 또는 삭제할 수 있습니다.
- 자식 도형 위치를 그룹에 상대적으로 유지하여 복잡한 다이어그램 관리가 쉬워집니다.

**팁:** 모든 자식 도형을 추가한 후, 그룹의 `Width`, `Height`, `Left`, `Top`을 조정하면 전체 컬렉션을 한 번에 재배치할 수 있습니다.

## 전체 실행 가능한 예제

아래는 복사·붙여넣기·실행할 수 있는 전체 프로그램입니다. 모든 `using` 지시문, `Main` 메서드 및 각 줄을 설명하는 주석이 포함되어 있습니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape to hold child shapes
        GroupShape group = builder.InsertGroupShape();

        // 3️⃣ Create a rectangle, set its dimensions, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle); // add rectangle to the group

        // 4️⃣ Create an ellipse, set size and position, then add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position inside the group
        group.AppendChild(ellipse); // add ellipse to the group

        // 5️⃣ Save the document
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document 'GroupShape.docx' created with a rectangle and an ellipse grouped together.");
    }
}
```

**예상 출력:** 프로그램을 실행하면 실행 폴더에 `GroupShape.docx`가 생성됩니다. Word에서 열면 왼쪽에 사각형(100 pt × 50 pt)과 오른쪽에 120 pt 떨어진 위치에 배치된 타원(80 pt × 80 pt)이 단일 그룹 객체 안에 있는 것을 확인할 수 있습니다.

![그룹화된 사각형 및 타원 도형이 포함된 Word 문서](grouped_shapes.png){: .center alt="C#으로 만든 그룹화된 사각형 및 타원 도형을 보여주는 Word 문서 스크린샷" }

*위 이미지는 최종 결과를 보여줍니다; 사각형과 타원을 하나의 그룹으로 선택할 수 있습니다.*

## 일반적인 질문 및 엣지 케이스

| 질문 | 답변 |
|----------|--------|
| **두 개 이상의 도형을 추가할 수 있나요?** | 예. 추가 도형마다 `group.AppendChild(yourShape)`를 호출하면 됩니다. |
| **그룹을 회전해야 하면 어떻게 하나요?** | 모든 자식을 추가한 후 `group.RotationAngle = 45;`(도) 를 사용합니다. |
| **그룹의 배경색을 어떻게 변경하나요?** | `group.FillColor = System.Drawing.Color.LightGray;` 로 설정합니다. |
| **.doc 파일에서도 작동하나요?** | Aspose.Words는 `.doc`와 `.docx`를 지원합니다. 동일한 코드가 작동하므로 `Save`에서 파일 확장자만 변경하면 됩니다. |
| **많은 도형을 그룹화하면 메모리 영향을 미치나요?** | 그룹화 자체는 최소한의 오버헤드만 추가합니다. 주요 고려 사항은 도형 총 개수이며, 대용량 문서에서는 적절히 유지해야 합니다. |

## 결론

이 튜토리얼에서는 C#을 사용하여 Word 파일에 **사각형 도형을 만들**는 방법, **도형 크기 설정**, **도형 차원 설정**, **도형 위치 설정**, 그리고 Aspose.Words를 이용해 **Word에서 도형을 그룹화**하는 방법을 배웠습니다. 전체 예제는 더 복잡한 다이어그램, 차트 또는 사용자 정의 그래픽으로 확장할 수 있는 깔끔하고 유지 보수 가능한 접근 방식을 보여줍니다.

다음으로 살펴볼 수 있는 내용:

- 도형 내부에 텍스트 추가 (`Shape.TextPath.Text = "Hello"`).
- `GroupShape`에 이미지 삽입.
- `doc.Save("output.pdf")`를 사용해 그룹화된 도형을 PDF로 내보내기.

프로젝트 요구에 맞게 다양한 크기, 위치 및 추가 도형 유형을 자유롭게 실험해 보세요. 즐거운 코딩 되세요!

## 다음에 배울 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 단계별 설명과 함께 완전한 동작 코드 예제가 포함되어 있어 추가 API 기능을 숙달하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Aspose.Words를 사용하여 Word에서 사각형 도형을 만들고 도형을 그룹화하는 방법](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [Aspose.Words for .NET을 사용해 Word 문서에 그룹 도형 만들기](/words/english/net/working-with-shapes/add-group-shape/)
- [C#을 사용해 Word에서 사각형 도형 만들기 – 단계별 가이드](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}