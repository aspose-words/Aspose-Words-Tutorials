---
category: general
date: 2026-11-15
description: Aspose.Words DocumentBuilder를 사용하여 Word 문서에 도형을 삽입하고 여러 도형을 그룹화하는 방법을
  배웁니다. 사각형 도형 삽입 및 여러 도형 삽입 예제가 포함됩니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert shape
- group multiple shapes
- insert multiple shapes
- insert rectangle shape
language: ko
lastmod: 2026-11-15
og_description: Aspose.Words를 사용하여 Word 파일에 도형을 삽입하는 방법. 이 가이드는 여러 도형을 그룹화하고, 사각형
  도형을 삽입하며, 여러 도형을 효율적으로 추가하는 방법을 다룹니다.
og_image_alt: Screenshot showing how to insert shape and group multiple shapes in
  a Word document using DocumentBuilder
og_title: DocumentBuilder로 도형 삽입 및 여러 도형 그룹화하는 방법
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  headline: How to insert shape and group multiple shapes using DocumentBuilder in
    C#
  type: TechArticle
- description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  name: How to insert shape and group multiple shapes using DocumentBuilder in C#
  steps:
  - name: Why use a group?
    text: '* **Single‑point transformation** – rotate or resize the whole group with
      one call. * **Logical organization** – the Word document tree reflects the grouping,
      making later edits easier. * **Consistent layout** – moving the group keeps
      the relative positions of its children intact.'
  - name: Adding more shapes – extending **insert multiple shapes** inside the group
    text: 'You can keep calling `InsertShape` while the cursor remains inside the
      `GroupShape`. For example, to add a triangle:'
  - name: Expected output
    text: '* **First two shapes** – a rectangle and an ellipse placed independently
      on the page. * **Grouped block** – a rectangle, an ellipse, and a triangle that
      move together when you click any of them in Word.'
  type: HowTo
tags:
- Aspose.Words
- C#
- DocumentBuilder
- Shape handling
title: C#에서 DocumentBuilder를 사용하여 도형을 삽입하고 여러 도형을 그룹화하는 방법
url: /ko/net/add-content-using-document-builder/how-to-insert-shape-and-group-multiple-shapes-using-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 DocumentBuilder를 사용하여 도형 삽입 및 여러 도형 그룹화 방법

Aspose.Words를 사용하여 Word 문서에 **how to insert shape**을(를) 알아야 한다면, 이 가이드는 정확한 단계들을 보여줍니다. 또한 **group multiple shapes**를 통해 여러 도형을 단일 객체처럼 동작하도록 하는 방법과 **insert rectangle shape**를 다른 그래픽과 함께 삽입하는 방법도 배울 수 있습니다.

문서 자동화에서는 차트, 로고, 콜아웃 등 여러 그래픽을 추가하면서도 정리를 유지해야 할 때가 많습니다. 이 튜토리얼을 마치면 **insert multiple shapes**를 수행하고, 이를 그룹 안에 배치하며, 깔끔하고 재사용 가능한 레이아웃을 저장할 수 있게 됩니다.

## 사전 요구 사항

* .NET 6.0 이상이 설치되어 있음  
* Visual Studio 2022(또는 기타 C# IDE)  
* Aspose.Words for .NET 라이선스 또는 무료 평가 키  
* C# 및 Aspose.Words `DocumentBuilder` 클래스에 대한 기본 지식  

다른 서드파티 라이브러리는 **필요하지** 않으며, 필요한 모든 것이 Aspose.Words에 포함되어 있습니다.

## 단계 1: NuGet을 통해 Aspose.Words 설치

Visual Studio에서 프로젝트를 열고 패키지 관리자 콘솔에 다음 명령을 실행합니다:

```powershell
Install-Package Aspose.Words
```

이 패키지에는 이 튜토리얼 전반에 걸쳐 사용되는 `DocumentBuilder`, `Shape`, `GroupShape` 클래스가 포함되어 있습니다.

## 단계 2: DocumentBuilder 인스턴스 생성 – **how to insert shape**의 기반

첫 번째 실행 가능한 코드는 `DocumentBuilder`를 생성하는 것입니다. 이 객체를 통해 문서 트리에 직접 접근하여 원하는 위치에 도형을 정확히 배치할 수 있습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Initialise a new blank document
        Document doc = new Document();
        // Create a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // The rest of the tutorial inserts and groups shapes here …
    }
}
```

*왜 중요한가*: `DocumentBuilder`는 커서(“삽입 지점”)를 유지합니다. 이후의 모든 `Insert...` 호출은 이 커서를 사용하므로, 나중에 모든 도형을 함께 유지하기 위해 커서를 `GroupShape` 안으로 이동시킵니다.

## 단계 3: **Insert rectangle shape** – 추가할 첫 번째 그래픽

사각형은 표, 이미지, 콜아웃 등의 일반적인 자리 표시자입니다. `ShapeType.Rectangle`와 함께 `InsertShape`를 사용하고, 너비와 높이를 포인트 단위로 지정합니다(1 pt ≈ 1/72 in).

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

사각형은 현재 커서 위치에 나타납니다. 필요에 따라 나중에 채우기, 선 스타일 또는 텍스트를 사용자 지정할 수 있습니다.

## 단계 4: 또 다른 도형 삽입 – 시각적 다양성을 위한 타원

두 개 이상의 도형을 추가하면 **insert multiple shapes**를 시연할 수 있습니다. 타원은 문서 흐름에서 사각형 뒤에 배치됩니다.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

이 시점에서 문서에는 두 개의 독립적인 도형이 포함됩니다. 커서를 이동하거나 텍스트를 추가해도 도형은 삽입된 위치에 그대로 남습니다.

## 단계 5: **Group multiple shapes** – 단일 단위로 동작하도록 그룹화

여러 그래픽을 함께 이동, 회전 또는 서식 지정해야 할 때 그룹화가 필수적입니다. 아래 코드는 `GroupShape`를 생성하고, 빌더의 커서를 그 안으로 이동한 뒤 동일한 도형을 다시 삽입합니다—이번에는 도형이 그룹의 자식이 됩니다.

```csharp
// 1️⃣ Create a GroupShape and add it to the document tree
GroupShape group = new GroupShape(builder.Document);
builder.InsertNode(group);

// 2️⃣ Position the cursor inside the group so new inserts go into it
builder.MoveTo(group);

// 3️⃣ Insert a rectangle shape inside the group
builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Insert an ellipse shape inside the same group
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

### 그룹을 사용하는 이유

* **Single‑point transformation** – 한 번의 호출로 전체 그룹을 회전하거나 크기 조정합니다.  
* **Logical organization** – Word 문서 트리가 그룹화를 반영하여 이후 편집이 쉬워집니다.  
* **Consistent layout** – 그룹을 이동해도 자식들의 상대 위치가 유지됩니다.

### 더 많은 도형 추가 – 그룹 내에서 **insert multiple shapes** 확장

커서가 `GroupShape` 안에 있는 동안 `InsertShape`를 계속 호출할 수 있습니다. 예를 들어 삼각형을 추가하려면:

```csharp
builder.InsertShape(ShapeType.Triangle, 60, 60);
```

각 호출은 그룹 컨텍스트를 유지하므로 삼각형이 자동으로 동일한 그룹 세트에 포함됩니다.

## 단계 6: 문서 저장 및 결과 확인

모든 도형을 배치한 후, 문서를 `.docx` 파일로 저장합니다. Microsoft Word(또는 호환 뷰어)에서 파일을 열면 두 개의 개별 도형 뒤에 동일한 사각형, 타원, 삼각형을 포함하는 그룹이 표시됩니다.

```csharp
// Save the document
doc.Save("GroupedShapesDemo.docx");
```

### 예상 출력

* **First two shapes** – 페이지에 독립적으로 배치된 사각형과 타원.  
* **Grouped block** – Word에서 어느 하나를 클릭하면 함께 이동하는 사각형, 타원, 삼각형.

그룹 내부의 도형을 선택하여 그룹화를 테스트할 수 있습니다; Word가 전체 컬렉션을 강조 표시하면 **group multiple shapes** 작업이 성공했음을 확인할 수 있습니다.

## 일반적인 함정 및 전문가 팁

| 문제 | 발생 원인 | 해결 방법 |
|-------|----------------|-----|
| 도형이 의도한 페이지 밖에 나타남 | `Insert`하기 전에 빌더의 커서를 `GroupShape` 안으로 이동하지 않음. | 그룹에 속하는 모든 `InsertShape` 호출 **앞에** `builder.MoveTo(group)`을 항상 호출합니다. |
| 저장 후 그룹이 사라짐 | 그룹이 문서 노드 컬렉션에 추가되지 않은 상태로 삽입됨. | `GroupShape` 생성 직후 `builder.InsertNode(group)`을 사용합니다. |
| 문서 DPI로 인한 예상치 못한 크기 | Aspose.Words는 포인트를 사용하므로 픽셀 단위로 생각하면 크기가 맞지 않을 수 있습니다. | 픽셀을 포인트로 변환(`points = pixels * 72 / 96`)하거나 직접 포인트 단위로 작업합니다. |
| 도형이 의도치 않게 겹침 | 명시적인 위치 지정이 없으며 Word가 순차적으로 배치함. | 삽입 후 `Shape.Left`와 `Shape.Top`을 설정하여 정확한 위치를 제어합니다. |

**전문가 팁:** 그룹화 후에는 그룹의 `Shapes` 컬렉션(`group.Shapes`)을 가져와 반복, 이름 변경 또는 일괄 서식 적용을 할 수 있습니다.

## 단계 7: 예제 확장 – 다음은?

이제 **how to insert shape**, **insert rectangle shape**, **group multiple shapes**를 알게 되었으니 다음을 탐색할 수 있습니다:

* **Animating grouped shapes** – 그룹에 회전 또는 뒤집기 속성을 설정합니다.  
* **Applying styles** – `Shape.FillColor`, `Shape.LineFormat`, `Shape.TextBox`를 사용해 레이블을 추가합니다.  
* **Exporting to PDF** – `doc.Save("output.pdf")`를 호출하면 동일한 그룹 레이아웃이 올바르게 렌더링됩니다.  

이 모든 확장은 동일한 `DocumentBuilder` 워크플로를 재사용하므로 코드를 깔끔하고 유지 보수하기 쉽게 합니다.

## 결론

이 튜토리얼에서는 Aspose.Words를 사용하여 Word 문서에 **how to insert shape**를 수행하고, **insert rectangle shape**를 삽입하며, **group multiple shapes**를 통해 단일 객체처럼 동작하도록 하는 방법을 보여주었습니다. 단계별 코드를 따라 하면 **insert multiple shapes**를 안정적으로 수행하고, 이를 그룹으로 정리하여 프로페셔널 수준의 문서를 프로그래밍 방식으로 생성할 수 있습니다.

다양한 도형 유형, 색상 및 그룹 변환을 자유롭게 실험해 보세요. 준비가 되면 이 패턴을 더 큰 보고서나 템플릿 솔루션에 통합하여 복잡한 문서 레이아웃을 자동화하십시오. 즐거운 코딩 되세요!

## 다음에 배울 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 전체 코드 예제와 단계별 설명이 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [How to create and insert ellipse and rectangle shapes inside a group shape in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [How to group shapes in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}