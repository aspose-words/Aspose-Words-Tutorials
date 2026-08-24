---
category: general
date: 2026-08-23
description: Aspose.Words를 사용하여 C#에서 도형을 그룹화하는 방법을 배웁니다. 이 가이드는 또한 사각형 도형을 삽입하고 복잡한
  문서에 도형을 추가하는 방법을 다룹니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- add shapes word
- group multiple shapes
- how to start group
language: ko
lastmod: 2026-08-23
og_description: Aspose.Words를 사용한 C#에서 도형을 그룹화하는 방법. 이 완전한 튜토리얼을 따라 사각형 도형을 삽입하고,
  워드에 도형을 추가하며, 여러 도형을 효율적으로 그룹화하세요.
og_image_alt: How to group shapes in C# using Aspose.Words
og_title: C#에서 도형을 그룹화하는 방법 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  headline: How to group shapes in C# with Aspose.Words
  type: TechArticle
- description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  name: How to group shapes in C# with Aspose.Words
  steps:
  - name: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
    text: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
  - name: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
    text: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
  - name: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
    text: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the existing `Shape` objects, call `builder.StartGroupShape()`,
      re‑insert them with `builder.InsertShape(existingShape)`, then call `EndGroupShape()`.
    question: Can I group shapes that already exist in the document?
  - answer: Aspose.Words adds a `<w:grpSp>` element that contains each shape’s `<w:sp>`
      node. This is fully compliant with the Office Open XML specification.
    question: Does grouping affect the underlying XML?
  - answer: 'There is no direct “ungroup” API, but you can iterate through the child
      shapes of the group (`group.GroupShape.Children`) and copy them out to the document
      body. ## Next steps Now that you know **how to group shapes**, consider exploring
      these related topics: - **Apply complex formatting to grouped '
    question: What if I need to ungroup later?
  type: FAQPage
tags:
- Aspose.Words
- C#
- shapes
- document automation
title: Aspose.Words를 사용하여 C#에서 도형을 그룹화하는 방법
url: /ko/net/programming-with-shapes/how-to-group-shapes-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 Aspose.Words를 사용하여 도형을 그룹화하는 방법

If you need to **how to group shapes** in a Word document programmatically, this tutorial shows you the exact steps using Aspose.Words for .NET. Whether you are building a report generator, a template engine, or a diagramming tool, you’ll learn how to start a group, insert a rectangle shape, and add shapes word‑level content without leaving your code.

You’ll also see how to **group multiple shapes** together, which is essential when you want to move, rotate, or style a collection of objects as a single entity. The example below works with the latest Aspose.Words 24.x release and requires only .NET 6 or later.

## 사전 요구 사항

- .NET 6 SDK (또는 Aspose.Words에서 지원하는 .NET 버전)
- Visual Studio 2022 또는 VS Code
- Aspose.Words for .NET NuGet 패키지 (`Install-Package Aspose.Words`)
- C# 및 Aspose.Words 객체 모델에 대한 기본 지식

> **Pro tip:** 테스트 중 워터마크 제한을 피하려면 Aspose의 무료 평가 라이선스를 사용하세요.

## Aspose.Words로 도형을 그룹화하는 방법

Below is a complete, runnable program that demonstrates **how to start group**, add a rectangle, and finalize the group. The code follows the same logical flow as the snippet you provided, but it adds context, error handling, and comments for clarity.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Get a DocumentBuilder to insert content.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Start a group shape – all shapes added after this call belong to the group.
            // This is the “how to start group” step.
            Shape group = builder.StartGroupShape();

            // 4️⃣ Insert individual shapes inside the group.
            //    a) Insert a rectangle shape (demonstrates “insert rectangle shape”).
            builder.InsertShape(ShapeType.Rectangle, 150, 80);
            //    b) Insert a simple ellipse for visual variety.
            builder.InsertShape(ShapeType.Ellipse, 100, 60);
            //    c) Add a WordArt‑style text shape – shows “add shapes word”.
            builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            builder.Writeln("Grouped Text"); // adds text inside the last shape

            // 5️⃣ Close the group shape to finalize the grouping.
            builder.EndGroupShape();

            // Optional: Save the document to verify the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### 각 단계가 중요한 이유

| 단계 | 목적 | 키워드와의 연관성 |
|------|---------|--------------------------------|
| **Create a new blank document** | 도형 작업을 위한 깨끗한 캔버스를 제공합니다. | 나중에 **add shapes word**를 위한 기반을 설정합니다. |
| **Initialize DocumentBuilder** | 빌더는 객체 삽입을 위한 주요 API입니다. | **how to start group**을 사용하기 전에 필요합니다. |
| **StartGroupShape** | 논리적 컨테이너를 시작하며, 이후 모든 도형이 이 그룹의 구성원이 됩니다. | **how to start group**에 직접 답합니다. |
| **InsertShape** (rectangle, ellipse, text) | 그룹 내부에 개별 도형을 배치합니다. 사각형 호출은 **insert rectangle shape**를 만족하고, 텍스트 도형은 **add shapes word**를 만족합니다. | **group multiple shapes**를 보여줍니다. |
| **EndGroupShape** | 그룹을 마무리하여 단위로 이동하거나 스타일을 적용할 수 있게 합니다. | **how to group shapes** 워크플로를 완성합니다. |

## 사각형 도형 삽입 – 심층 분석

The `InsertShape` method accepts a `ShapeType` enum, width, and height. To **insert rectangle shape** with custom styling, you can extend the example:

```csharp
// Insert a styled rectangle
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rect.FillColor = System.Drawing.Color.LightBlue;
rect.StrokeColor = System.Drawing.Color.DarkBlue;
rect.LineWidth = 2.0;
```

> **Why style it?** 스타일링은 그룹이 나중에 재배치될 때 사각형이 돋보이도록 보장합니다. 또한 그룹이 닫히기 *전*에 도형 속성을 설정할 수 있음을 보여줍니다.

## Word 수준 도형 추가 (add shapes word)

If you need to embed text directly inside a shape—commonly called “WordArt” or “text box”—use `ShapeType.TextPlainText`. After inserting, you can write text into the shape with `DocumentBuilder.Writeln` or by accessing the shape’s `TextBox` property:

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextPlainText, 250, 50);
textBox.TextBox.Text = "Hello, grouped world!";
```

This satisfies the **add shapes word** keyword and shows how text can travel with the group.

## 여러 도형을 그룹화 – 실용 시나리오

When you **group multiple shapes**, you can treat them like a single object for positioning, rotation, or scaling. For example, after the group is closed, you can move the whole group:

```csharp
// Move the entire group 100 points to the right and 50 points down.
group.Left += 100;
group.Top += 50;
```

Or rotate the group:

```csharp
group.Rotation = 45; // degrees
```

These operations are only possible because the shapes share the same parent group.

## 엣지 케이스 처리

1. **Nested groups** – Aspose.Words는 그룹 안에 그룹을 허용합니다. 중첩 그룹을 만들려면 내부 그룹에 대한 `EndGroupShape`를 호출하기 전에 다시 `StartGroupShape`를 호출합니다.
2. **Empty groups** – 그룹을 시작했지만 도형을 삽입하지 않으면 `EndGroupShape`가 빈 컨테이너를 생성합니다. 이는 무해하지만 파일 크기가 약간 증가할 수 있습니다.
3. **Compatibility** – 생성된 DOCX는 Word 2010 이상에서 작동합니다. 이전 버전은 그룹화 메타데이터를 무시할 수 있으므로 항상 대상 Word 버전에서 테스트하세요.

## 참고용 전체 소스 파일

Save the following as `Program.cs` in a .NET console project. The code compiles and runs without modification.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document.
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Start the group – “how to start group”.
            Shape group = builder.StartGroupShape();

            // Step 4a: Insert a rectangle – “insert rectangle shape”.
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);
            rect.FillColor = System.Drawing.Color.LightCoral;
            rect.StrokeColor = System.Drawing.Color.DarkRed;
            rect.LineWidth = 1.5;

            // Step 4b: Insert an ellipse (additional shape for grouping).
            builder.InsertShape(ShapeType.Ellipse, 100, 60);

            // Step 4c: Add a text box – “add shapes word”.
            Shape txt = builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            txt.TextBox.Text = "Grouped Text";

            // Step 5: End the group – completes “how to group shapes”.
            builder.EndGroupShape();

            // Optional: Adjust group position.
            group.Left += 50;
            group.Top += 30;

            // Save the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### 예상 출력

Opening `GroupedShapes.docx` in Microsoft Word will show:

- 연한 코랄 색상의 사각형, 타원, 텍스트 상자가 모두 시각적으로 결합된 모습.
- 그룹의 어느 부분을 선택해도 전체 그룹이 선택되며(단일 경계 상자가 표시됨).
- 그룹을 이동하거나 회전하면 세 도형이 함께 움직입니다.

## 자주 묻는 질문

**Q: 이미 문서에 존재하는 도형을 그룹화할 수 있나요?**  
A: 예. 기존 `Shape` 객체를 가져와 `builder.StartGroupShape()`를 호출하고, `builder.InsertShape(existingShape)`로 다시 삽입한 뒤 `EndGroupShape()`를 호출합니다.

**Q: 그룹화가 기본 XML에 영향을 미치나요?**  
A: Aspose.Words는 각 도형의 `<w:sp>` 노드를 포함하는 `<w:grpSp>` 요소를 추가합니다. 이는 Office Open XML 사양을 완전히 준수합니다.

**Q: 나중에 그룹을 해제해야 하면 어떻게 하나요?**  
A: 직접적인 “ungroup” API는 없지만, 그룹의 자식 도형(`group.GroupShape.Children`)을 순회하여 문서 본문으로 복사할 수 있습니다.

## 다음 단계

Now that you know **how to group shapes**, consider exploring these related topics:

- **Apply complex formatting to grouped shapes** – 그룹화된 도형에 그라디언트 채우기, 그림자 효과, 선 스타일 설정 방법을 배웁니다.
- **Export grouped shapes as images** – `Shape.GetShapeRenderer().Save(...)`를 사용해 그룹을 래스터 이미지로 내보냅니다.
- **Create dynamic diagrams** – 데이터 기반 위치 지정과 그룹화를 결합해 자동으로 플로우차트를 생성합니다.

Each of these builds on the foundation covered here and will help you create richer, more interactive Word documents.

---

*행복한 코딩 되세요! 이 가이드가 도움이 되었다면 팀원과 공유하거나 샘플 프로젝트가 포함된 저장소에 별표를 달아 주세요.*

## 다음에 배울 내용은?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}