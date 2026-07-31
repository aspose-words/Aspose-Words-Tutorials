---
category: general
date: 2026-07-29
description: Aspose.Words를 사용하여 사각형 워드를 그립니다. 사각형 도형 추가, 선 도형 추가 및 하나의 문서에서 여러 도형을
  관리하는 방법을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle word
- add rectangle shape
- add line shape
- how to add shapes
- multiple shapes word
language: ko
lastmod: 2026-07-29
og_description: Aspose.Words로 사각형 워드를 그리세요. 이 단계별 가이드를 따라 사각형 도형을 추가하고, 선 도형을 추가하며,
  여러 도형을 손쉽게 워드에서 작업하세요.
og_image_alt: Screenshot showing a Word document with a grouped rectangle and line
  shape – draw rectangle word example
og_title: Word에서 사각형 그리기 – Word에서 도형 추가 마스터
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: draw rectangle word using Aspose.Words. Learn how to add rectangle
    shape, add line shape, and manage multiple shapes word in a single document.
  headline: draw rectangle word – Add Shapes in Word with Aspose
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: 사각형 그리기 – Aspose로 Word에 도형 추가
url: /ko/net/programming-with-shapes/draw-rectangle-word-add-shapes-in-word-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# draw rectangle word – Word에서 도형 추가 완전 가이드

UI를 매번 열지 않고도 **draw rectangle word** 문서를 만들 수 있는 방법이 궁금하셨나요? 당신만 그런 것이 아닙니다. 많은 개발자들이 실시간으로 Word 파일을 생성해야 하는데, 가장 쉬운 방법은 라이브러리가 무거운 작업을 대신하도록 하는 것입니다. 이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 **how to add shapes**—특히 사각형과 선—를 정확히 구현하는 방법을 보여드리며, *draw rectangle word* 라는 구문에 초점을 맞춰 혼동되지 않도록 하겠습니다.

코드 안에 살아 있는 작은 미술 스튜디오라고 생각하면 됩니다. 끝까지 따라오시면 **add rectangle shape**, **add line shape**를 추가하고 이를 **multiple shapes word** 그룹으로 결합할 수 있게 됩니다. UI도 없고, 수동 조작도 없으며, 깔끔하고 반복 가능한 C# 코드만 있으면 됩니다.

## 배울 내용

- Aspose.Words를 사용해 새 Word 문서를 설정합니다.  
- 여러 객체를 담을 수 있는 **GroupShape**을 생성합니다.  
- 그룹 안에 **add rectangle shape**와 **add line shape**를 추가합니다.  
- 그룹화된 도형을 문서 본문에 삽입합니다.  
- 파일을 저장하고 결과를 즉시 확인합니다.  

기본 C#에 익숙하고 Aspose.Words 사본이 있다면 바로 시작할 수 있습니다. 핵심 라이브러리 외에 추가 NuGet 패키지는 필요하지 않습니다.

> **Pro tip:** Aspose.Words는 .NET 6, .NET 7 및 .NET Framework 4.6+와 호환됩니다. 프로젝트에 맞는 런타임을 선택하세요.

![draw rectangle word example](https://example.com/placeholder-image.png "draw rectangle word – grouped shapes in a Word file")

## draw rectangle word – 문서 설정

먼저 **draw rectangle word**를 수행하려면 깨끗한 캔버스가 필요합니다. `Document` 클래스가 바로 그 캔버스이며, `DocumentBuilder`가 우리의 브러시 역할을 합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document doc = new Document();

// DocumentBuilder lets us insert nodes, paragraphs, tables, etc.
DocumentBuilder builder = new DocumentBuilder(doc);
```

위 두 줄은 메모리 상에 새 `.docx` 파일을 생성합니다. 아직 디스크에 기록되지 않으므로 파일 시스템을 어지럽히지 않고 실험할 수 있습니다.

## How to Add Shapes – Creating a GroupShape Container

여러 개의 도형을 **multiple shapes word**가 하나의 단위처럼 동작하게 하려면—함께 이동하고, 함께 회전하도록—`GroupShape`에 감싸야 합니다. 그룹은 다른 도형들을 담는 폴더와 같습니다.

```csharp
// Define a GroupShape that will act as a container for other shapes.
// Width = 300 pts, Height = 200 pts (roughly 4.2" x 2.8").
GroupShape group = new GroupShape(doc, 300, 200)
{
    Left = 100,   // Position from the left margin.
    Top  = 100    // Position from the top margin.
};
```

왜 그룹을 쓰나요? 나중에 **add rectangle shape**와 **add line shape**를 추가하고 한 번에 이동시키고 싶을 때 필요합니다. 그룹이 없으면 각 도형을 개별적으로 재배치해야 합니다.

## add rectangle shape – 그룹 안에 사각형 삽입

컨테이너가 준비되었으니, 이제 **add rectangle shape**를 해보겠습니다. 사각형은 `Shape`이며 `ShapeType`이 `Rectangle`인 형태입니다.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 120,   // 120 points ≈ 1.67 inches.
    Height = 80,    // 80 points ≈ 1.11 inches.
    Left   = 10,    // Offset inside the group.
    Top    = 10
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

`Left`와 `Top` 값은 페이지가 아니라 그룹의 원점을 기준으로 합니다. 따라서 도형을 정확히 정렬하기가 쉽습니다. 사각형은 그룹의 좌상단 근처에 나타납니다.

## add line shape – 같은 그룹에 선 추가

선도 또 다른 `Shape`이지만 `ShapeType`이 `Line`입니다. 우리는 이 선을 사각형 아래에 배치할 것입니다.

```csharp
// Create a line shape.
Shape line = new Shape(doc, ShapeType.Line)
{
    Width  = 150,   // Length of the line.
    Height = 0,     // Height is zero for a straight line.
    Left   = 10,
    Top    = 110    // Position it a bit lower than the rectangle.
};

// Append the line to the group.
group.AppendChild(line);
```

선의 높이가 0이기 때문에 `Top` 속성이 선이 수직으로 위치하는 지점을 결정합니다. `Width`는 선이 가로로 얼마나 길게 뻗을지를 제어합니다.

## multiple shapes word – 그룹을 문서 본문에 삽입

이제 **add rectangle shape**와 **add line shape**를 담고 있는 그룹이 준비되었습니다. 마지막 단계는 이 전체 그룹을 문서에 삽입하는 것입니다.

```csharp
// Insert the completed group into the document body at the current cursor position.
builder.InsertNode(group);
```

`InsertNode`는 현재 `DocumentBuilder`가 위치한 정확한 지점에 그룹을 배치합니다. 특정 단락에 넣고 싶다면 먼저 `builder.MoveToParagraph(index)`로 빌더 위치를 이동시키세요.

## Saving the Result – draw rectangle word 출력 확인

```csharp
// Save the document to disk. Change the path to a location that exists on your machine.
doc.Save("C:/Temp/GroupShape.docx");
```

생성된 파일을 Microsoft Word에서 열면 사각형과 선이 포함된 하나의 그룹을 확인할 수 있습니다. 그룹을 클릭해 드래그하거나 크기를 조절하면 모든 도형이 함께 움직입니다. 이것이 **multiple shapes word**의 힘입니다.

### Expected Output

- `GroupShape.docx`라는 이름의 `.docx` 파일이 생성됩니다.  
- 페이지 상단 좌측에 그룹화된 사각형(120 × 80 pt)이 배치됩니다.  
- 사각형 바로 아래에 가로선(길이 150 pt)이 위치합니다.  
- 두 도형 모두 하나의 객체로 선택할 수 있습니다.

그룹을 더블 클릭하면 Word가 각 도형을 개별적으로 편집할 수 있게 해 주어 미세 조정에 적합합니다.

## Common Questions & Edge Cases

**두 개 이상 도형이 필요하면 어떻게 하나요?**  
추가 도형마다 `group.AppendChild(yourShape)`를 호출하면 됩니다. 그룹은 원하는 만큼 많은 도형을 담을 수 있어 복잡한 다이어그램에 이상적입니다.

**사각형의 채우기 색을 바꿀 수 있나요?**  
물론입니다. 사각형을 만든 뒤 `rectangle.FillColor = System.Drawing.Color.LightBlue;`와 같이 설정하면 됩니다. 채우기를 지원하는 모든 도형에 적용됩니다.

**선에 `Height = 0`을 설정해야 하나요?**  
네, 수평 선의 경우 높이는 0이어야 합니다. 수직 선을 만들려면 `Width = 0`으로 두고 `Height`에 양수를 지정하면 됩니다.

**.doc 파일(Word 97‑2003)에서도 동작하나요?**  
Aspose.Words는 오래된 `.doc` 형식으로 저장할 수 있지만, 최신 도형 기능 중 일부는 제한될 수 있습니다. 전체 기능을 사용하려면 `.docx`를 권장합니다.

**전체 그룹을 회전하려면 어떻게 하나요?**  
삽입하기 전에 `group.Rotation = 45;`(도)와 같이 설정하면 그룹에 포함된 모든 자식 도형이 회전합니다.

## Recap – Word에서 프로그래밍으로 도형 추가하기

- **draw rectangle word**는 `Document`와 `DocumentBuilder` 생성으로 시작합니다.  
- **multiple shapes word**를 담을 **GroupShape**를 구축합니다.  
- 그룹에 **add rectangle shape**와 **add line shape**를 추가합니다.  
- `builder.InsertNode`로 그룹을 본문에 삽입합니다.  
- 파일을 저장하고 열어 시각적 결과를 확인합니다.

이것이 전체 워크플로우이며, 한 눈에 보기 쉬운 코드 예제로 정리되었습니다.

## Next Steps & Related Topics

이제 **how to add shapes**를 알았으니 다음 주제들을 탐색해 보세요:

- `ShapeType.Rectangle`에 `CornerRadius`를 추가해 **add rectangle shape**를 둥근 모서리로 만들기.  
- `line.LineFormat.DashStyle`을 활용해 다양한 대시 패턴으로 선 스타일링하기.  
- 도형과 함께 이미지를 삽입해 보고서를 더욱 풍부하게 만들기.  
- **multiple shapes word**를 사용해 플로우차트나 간단한 UML 다이어그램 만들기.  

이러한 주제들은 여기서 다룬 기본을 바탕으로 자연스럽게 확장되며, 도형 생성 → 설정 → 필요 시 그룹화라는 동일한 패턴을 따릅니다.

---

Happy coding! 문제가 발생하거나 멋진 활용 사례가 있다면 아래에 댓글을 남겨 주세요. 여러분의 피드백은 모두가 **draw rectangle word**와 그 너머의 기술을 마스터하는 데 큰 도움이 됩니다.

## What Should You Learn Next?

다음 튜토리얼들은 이 가이드에서 시연한 기술을 기반으로 하여 밀접하게 연관된 주제를 다룹니다. 각 자료에는 완전한 코드 예제와 단계별 설명이 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}