---
category: general
date: 2026-09-21
description: Aspose.Words for C#를 사용하여 Word에서 도형을 그룹화하는 방법을 배웁니다. 이 단계별 가이드는 그룹화된
  도형을 만들고, 위치를 지정하고, 저장하는 내용을 다룹니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in Word
- Aspose.Words shape grouping
- C# Word shape manipulation
- DocumentBuilder insert shape
- GroupShape container
language: ko
lastmod: 2026-09-21
og_description: Aspose.Words for C#를 사용하여 Word에서 도형을 그룹화하십시오. 이 간결한 튜토리얼을 따라 프로그래밍
  방식으로 그룹화된 도형을 만들고, 위치를 지정하고, 저장하세요.
og_image_alt: Screenshot of grouped shapes in Word document created with Aspose.Words
og_title: Aspose.Words를 사용한 Word에서 도형 그룹화 – 완전한 C# 가이드
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  headline: How to group shapes in Word with Aspose.Words for C#
  type: TechArticle
- description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  name: How to group shapes in Word with Aspose.Words for C#
  steps:
  - name: Create a blank document and a `DocumentBuilder`
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert the first rectangle shape
    text: '```csharp // Insert a rectangle that is 100 points wide and 50 points tall.
      Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); ```'
  - name: Insert the second rectangle and offset it
    text: '```csharp // Insert the second rectangle with the same dimensions. Shape
      shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);'
  - name: Create a `GroupShape` large enough for both rectangles
    text: '```csharp // The group must be wide enough to contain both shapes (100
      pt + 120 pt + 100 pt = 320 pt). // We give a little extra margin, so the group
      width is set to 300 pt and height to 100 pt. GroupShape group = new GroupShape(doc,
      300, 100); ```'
  - name: Append the individual shapes to the group
    text: '```csharp group.AppendChild(shape1); group.AppendChild(shape2); ```'
  - name: Insert the grouped shape back into the document
    text: '```csharp // Insert the GroupShape at the current builder position. builder.InsertNode(group);
      ```'
  - name: Save the document
    text: '```csharp // Replace YOUR_DIRECTORY with an absolute or relative path where
      you have write permission. doc.Save("YOUR_DIRECTORY/GroupedShapes.docx"); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: C#용 Aspose.Words로 Word에서 도형을 그룹화하는 방법
url: /ko/net/programming-with-shapes/how-to-group-shapes-in-word-with-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for C#를 사용하여 Word에서 도형 그룹화하는 방법

Word에서 **도형을 프로그래밍 방식으로 그룹화**해야 할 경우, Aspose.Words를 사용하면 간단합니다. 이 튜토리얼에서는 두 개의 사각형 도형을 만들고, 나란히 배치한 뒤, 이를 `GroupShape`로 결합하고 결과를 DOCX 파일로 저장하는 방법을 보여줍니다.

전체 실행 가능한 예제와 각 단계가 중요한 이유에 대한 설명, 겹치는 도형이나 동적 크기와 같은 일반적인 엣지 케이스를 처리하는 팁을 제공합니다. 이 가이드를 끝까지 읽으면 Word 자동화 프로젝트에 도형 그룹화를 손쉽게 통합할 수 있습니다.

## 사전 요구 사항

시작하기 전에 다음을 확인하세요:

* .NET 6.0(이상) 설치 – Aspose.Words는 .NET Standard 2.0+, .NET Core, .NET Framework를 지원합니다.
* 유효한 Aspose.Words for .NET 라이선스(또는 임시 평가 키) – 라이선스 없이도 라이브러리를 사용할 수 있지만 워터마크가 추가됩니다.
* Visual Studio 2022(또는 C# IDE) – 샘플을 컴파일하고 실행하기 위해 필요합니다.

`Aspose.Words` 외에 추가 NuGet 패키지는 필요하지 않습니다.

## Aspose.Words를 사용하여 Word에서 도형을 그룹화하는 방법

솔루션의 핵심은 개별 도형을 담는 컨테이너 역할을 하는 **`GroupShape`** 객체입니다. 아래에서는 과정을 명확한 단계로 나누어 설명합니다.

### 단계 1: 빈 문서와 `DocumentBuilder` 만들기

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty Word document.
Document doc = new Document();

// DocumentBuilder provides convenient methods for inserting content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*왜 이 단계가 필요한가요?*  
`Document`는 전체 DOCX 파일을 나타내고, `DocumentBuilder`는 현재 커서 위치에 새 요소를 자동으로 삽입하는 유창한 메서드(`InsertShape` 등)를 제공합니다.

### 단계 2: 첫 번째 사각형 도형 삽입

```csharp
// Insert a rectangle that is 100 points wide and 50 points tall.
Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

`InsertShape` 호출은 도형을 문서에 추가하고, 추가 구성을 할 수 있는 `Shape` 객체를 반환합니다(색상, 테두리 등). 크기는 포인트 단위이며, 1 pt ≈ 1/72 인치입니다.

### 단계 3: 두 번째 사각형 도형 삽입 및 오프셋 지정

```csharp
// Insert the second rectangle with the same dimensions.
Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Move the second shape 120 points to the right so the two rectangles do not overlap.
shape2.Left = 120; // Horizontal offset from the left edge of the page.
```

`Left` 속성은 페이지 여백을 기준으로 도형의 위치를 지정합니다. 첫 번째 도형의 너비(100 pt)보다 큰 오프셋을 지정해야 겹치지 않으며, 여기서는 작은 간격을 두고 120 pt를 사용합니다.

### 단계 4: 두 사각형을 모두 포함할 수 있는 `GroupShape` 생성

```csharp
// The group must be wide enough to contain both shapes (100 pt + 120 pt + 100 pt = 320 pt).
// We give a little extra margin, so the group width is set to 300 pt and height to 100 pt.
GroupShape group = new GroupShape(doc, 300, 100);
```

`GroupShape`는 소유 `Document`와 컨테이너 크기를 인수로 받습니다. 컨테이너의 너비는 가장 오른쪽 도형의 오른쪽 가장자리를 초과해야 하며, 그렇지 않으면 두 번째 도형이 잘려 보일 수 있습니다.

### 단계 5: 개별 도형을 그룹에 추가

```csharp
group.AppendChild(shape1);
group.AppendChild(shape2);
```

`AppendChild`(또는 해당 메서드) 호출은 도형을 그룹의 내부 컬렉션으로 이동시킵니다. 이 호출 이후 도형은 더 이상 문서 트리에서 독립적인 객체가 아니며, 그룹에 속하게 됩니다.

### 단계 6: 그룹화된 도형을 문서에 다시 삽입

```csharp
// Insert the GroupShape at the current builder position.
builder.InsertNode(group);
```

`InsertNode`는 현재 커서 위치에 전체 `GroupShape`를 배치합니다. 특정 단락에 그룹을 넣고 싶다면, 먼저 `DocumentBuilder`를 해당 단락으로 이동시켜야 합니다.

### 단계 7: 문서 저장

```csharp
// Replace YOUR_DIRECTORY with an absolute or relative path where you have write permission.
doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
```

결과 파일에는 두 개의 사각형이 하나의 객체처럼 동작합니다—Microsoft Word에서 함께 이동, 크기 조정 또는 삭제할 수 있습니다.

## 전체 소스 코드

모든 단계를 합치면 독립 실행형 프로그램이 됩니다:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first rectangle (100 pt × 50 pt).
        Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3️⃣ Insert the second rectangle and offset it horizontally.
        Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        shape2.Left = 120; // Prevent overlap.

        // 4️⃣ Create a GroupShape container large enough for both.
        GroupShape group = new GroupShape(doc, 300, 100);

        // 5️⃣ Add both rectangles to the group.
        group.AppendChild(shape1);
        group.AppendChild(shape2);

        // 6️⃣ Insert the grouped shape back into the document.
        builder.InsertNode(group);

        // 7️⃣ Save the document.
        doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
    }
}
```

**예상 출력:** Microsoft Word에서 *GroupedShapes.docx*를 열면 두 개의 사각형이 나란히 배치되고, 하나의 선택 가능한 객체로 취급됩니다. 그룹을 드래그하면 두 사각형이 함께 이동합니다.

## 일반적인 변형 및 엣지 케이스

| 상황 | 권장 조정 |
|-----------|------------------------|
| **두 개 이상 도형** | 추가 `Shape` 객체를 만들고 적절히 위치시킨 뒤, 각각을 동일한 `GroupShape`에 `AppendChild`합니다. |
| **동적 크기** | 자식 도형들의 최대 `Right`와 `Bottom` 값을 기반으로 그룹의 너비/높이를 계산합니다. |
| **다양한 도형 유형** | `ShapeType.Ellipse`, `ShapeType.Triangle` 등도 동일하게 삽입할 수 있으며, 그룹 컨테이너는 유형에 구애받지 않습니다. |
| **회전된 도형** | `shape.Rotation = 45;`를 `AppendChild` 전에 설정하면 회전 정보가 그룹에 보존됩니다. |
| **PDF로 저장** | `doc.Save("GroupedShapes.pdf");`를 호출하면 그룹이 PDF 렌더링에서도 유지됩니다. |

**팁:** 그룹화 후에도 `group.GetChildNodes(NodeType.Shape, true)`를 통해 개별 도형에 접근할 수 있습니다. 이는 그룹을 깨뜨리지 않고 특정 사각형의 채우기 색상을 변경해야 할 때 유용합니다.

## 프로그래밍 방식으로 그룹화 확인하기

단위 테스트 등에서 도형이 올바르게 그룹화되었는지 확인하려면 문서 노드 계층을 검사합니다:

```csharp
NodeCollection groups = doc.GetChildNodes(NodeType.GroupShape, true);
Console.WriteLine($"Number of groups: {groups.Count}");
Console.WriteLine($"Children in first group: {groups[0].GetChildNodes(NodeType.Shape, true).Count}");
```

출력은 다음과 같아야 합니다:

```
Number of groups: 1
Children in first group: 2
```

이를 통해 **Word에서 도형 그룹화**가 정상적으로 생성되었음을 확인할 수 있습니다.

## 결론

이제 Aspose.Words for C#를 사용하여 **Word에서 도형을 그룹화**하는 방법을 알게 되었습니다. 개별 도형을 만들고, 위치를 지정한 뒤, `GroupShape`에 묶고, 다시 문서에 삽입하는 과정이 핵심입니다. 위의 완전한 예제를 기반으로 도형 수를 늘리거나, 다른 유형을 결합하거나, 텍스트 상자와 이미지와 함께 사용할 수 있습니다.

다음으로 **Aspose.Words 도형 그룹화**, **C# Word 도형 조작**, **DocumentBuilder 삽입 도형** 등 관련 주제를 탐색하여 보다 고급 문서 자동화 시나리오를 구현해 보세요. 동적 크기, 조건부 그룹화, PDF 내보내기 등을 실험하면서 Aspose.Words의 강력한 기능을 최대한 활용하시기 바랍니다.

## 다음에 배워야 할 내용은 무엇인가요?

다음 튜토리얼은 이 가이드에서 다룬 기술을 기반으로 하며, 추가적인 API 기능을 마스터하고 다양한 구현 방식을 탐색할 수 있도록 완전한 코드 예제와 단계별 설명을 제공합니다.

- [Aspose.Words for .NET을 사용하여 Word 문서에 도형 삽입](/words/english/net/working-with-shapes/insert-shape/)
- [Aspose.Words로 Word에서 사각형 도형 만들기 – 단계별 가이드](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words 도형 그림자 튜토리얼 – C#에서 Word 도형에 그림자 추가](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}