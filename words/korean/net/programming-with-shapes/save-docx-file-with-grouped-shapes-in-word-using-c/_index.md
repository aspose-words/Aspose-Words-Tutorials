---
category: general
date: 2026-08-04
description: Word에서 사각형 도형과 그룹 도형을 추가하면서 프로그래밍으로 docx 파일을 저장합니다. 도형 크기를 설정하고 텍스트 상자를
  프로그래밍으로 만드는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx file
- add rectangle shape
- group shapes word
- set shape dimensions
- create textbox programmatically
language: ko
lastmod: 2026-08-04
og_description: C#를 사용하여 사각형 도형을 추가하고, Word에서 도형을 그룹화하고, 도형 크기를 설정하며, 프로그래밍 방식으로 텍스트
  상자를 만들어 docx 파일을 저장합니다.
og_image_alt: Screenshot of a saved docx file that contains a grouped rectangle and
  textbox
og_title: Word에서 그룹화된 도형이 포함된 docx 파일 저장 – C# 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  headline: Save docx file with grouped shapes in Word using C#
  type: TechArticle
- description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  name: Save docx file with grouped shapes in Word using C#
  steps:
  - name: 1. Create a new document and a builder
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing; using Aspose.Words.Drawing.Shapes;'
  - name: 2. Add rectangle shape to a group
    text: '```csharp // Create a group container that will hold all shapes. GroupShape
      group = new GroupShape(doc) { Width = 400, // Set shape dimensions for the group.
      Height = 200 };'
  - name: 3. Group shapes in Word document
    text: The `GroupShape` class aggregates multiple drawing objects. Grouping is
      useful when you want to treat several objects as a single unit (e.g., moving,
      rotating, or copying them together).
  - name: 4. Set shape dimensions for precise layout
    text: Both the group and its child shapes need explicit dimensions; otherwise
      Word applies default sizes that may not match your design.
  - name: 5. Create textbox programmatically inside the group
    text: '```csharp // Add a textbox shape with custom text. Shape textBox = new
      Shape(doc, ShapeType.TextBox) { Width = 180, Height = 100, Left = 210, // Position
      relative to the group’s coordinate system. Top = 10 };'
  - name: 6. Insert group shape and **save docx file**
    text: '```csharp // Insert the completed group into the document at the current
      cursor position. builder.InsertNode(group);'
  - name: Expected output
    text: '* A file named **GroupShape.docx** appears in the output directory. * Opening
      the file shows a rectangular shape on the left and a textbox containing “Grouped
      text” on the right, both locked together. * Selecting either shape moves the
      entire group, confirming that **group shapes word** functionalit'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: C#를 사용하여 Word에서 그룹화된 도형이 포함된 docx 파일 저장
url: /ko/net/programming-with-shapes/save-docx-file-with-grouped-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#를 사용하여 Word에서 그룹화된 도형으로 docx 파일 저장하기

여러 개의 도형을 함께 배치한 **save docx file**이 필요하다면, 이 가이드는 C#로 구현하는 방법을 보여줍니다. **add rectangle shape** 방법, Word 문서에서 여러 도형을 그룹화하는 방법, **set shape dimensions** 설정 방법, 그리고 **create textbox programmatically** 만드는 방법을 배울 수 있습니다. 이 솔루션은 최신 Aspose.Words for .NET과 호환되며 .NET 6 이상에서 실행됩니다.

이 튜토리얼은 프로젝트 설정부터 최종 `doc.Save` 호출까지 모든 단계를 자세히 안내합니다. 끝까지 진행하면 콘솔이나 ASP.NET 프로젝트에 그대로 붙여넣을 수 있는 재사용 가능한 코드 스니펫을 얻게 됩니다. 외부 스크립트나 DOCX 파일을 수동으로 편집할 필요가 없습니다.

## 사전 요구 사항

* .NET 6 SDK(또는 최신 버전)가 설치되어 있어야 합니다.
* **Aspose.Words for .NET**에 대한 유효한 라이선스(무료 체험판으로 테스트 가능).
* Visual Studio 2022, VS Code 또는 .NET 프로젝트를 빌드할 수 있는 모든 IDE.

코드는 Aspose.Words 네임스페이스만 사용하므로 추가 NuGet 패키지는 필요하지 않습니다.

## Word에서 그룹화된 도형으로 docx 파일 저장하기

솔루션의 핵심은 사각형과 텍스트 상자를 포함하는 `GroupShape`를 만든 뒤, 이를 문서에 삽입하고 `doc.Save`를 호출하는 것입니다. 다음 섹션에서는 이 과정을 단계별로 나누어 설명합니다.

### 1. 새 문서와 빌더 만들기

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // Initialize a blank document.
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for editing the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this step matters* – 새 `Document` 객체는 빈 *.docx* 파일을 나타냅니다. `DocumentBuilder`는 `InsertNode`와 같은 고수준 메서드를 제공하며, 이를 사용해 그룹 도형을 배치합니다.

### 2. 그룹에 사각형 도형 추가

```csharp
        // Create a group container that will hold all shapes.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,   // Set shape dimensions for the group.
            Height = 200
        };

        // Add a rectangle shape that will be part of the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,   // Set shape dimensions for the rectangle.
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);
```

*Why this step matters* – **add rectangle shape** 작업은 정확한 크기와 위치를 가진 시각 요소를 정의하는 방법을 보여줍니다. 사각형은 `group` 내부에 존재하므로, 나중에 그룹을 이동하면 사각형도 자동으로 이동합니다.

### 3. Word 문서에서 도형 그룹화

`GroupShape` 클래스는 여러 그리기 객체를 하나로 모읍니다. 그룹화는 여러 객체를 하나의 단위로 취급하고 싶을 때 유용합니다(예: 함께 이동, 회전, 복사).

```csharp
        // The group now contains the rectangle; we will add more shapes next.
```

*Why we group* – 그룹화를 하면 레이아웃 복잡성이 감소합니다. 각 도형을 개별적으로 배치하는 대신, 그룹의 `Left`, `Top`, `Width`, `Height`를 한 번만 조정하면 됩니다.

### 4. 정확한 레이아웃을 위한 도형 크기 설정

그룹과 그 하위 도형 모두 명시적인 크기가 필요합니다. 그렇지 않으면 Word가 기본 크기를 적용하여 디자인과 일치하지 않을 수 있습니다.

```csharp
        // Example of adjusting the group’s overall size.
        group.Width = 400;   // Overall width of the grouped area.
        group.Height = 200;  // Overall height of the grouped area.
```

*Why we set dimensions* – 정확한 측정은 사각형과 텍스트 상자가 의도치 않게 겹치지 않도록 하고, 최종 **save docx file**이 원하는 레이아웃과 일치하도록 보장합니다.

### 5. 그룹 내부에 프로그래밍 방식으로 텍스트 상자 만들기

```csharp
        // Add a textbox shape with custom text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,   // Position relative to the group’s coordinate system.
            Top = 10
        };

        // Populate the textbox with a paragraph containing a run.
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);

        // Append the textbox to the same group.
        group.AppendChild(textBox);
```

*Why this step matters* – **create textbox programmatically** 부분은 도형 안에 풍부한 텍스트를 삽입하는 방법을 보여줍니다. `Paragraph`와 `Run`을 사용하면 이후 서식을 완전히 제어할 수 있습니다.

### 6. 그룹 도형 삽입 및 **save docx file**

```csharp
        // Insert the completed group into the document at the current cursor position.
        builder.InsertNode(group);

        // Save the document to the file system.
        doc.Save("GroupShape.docx");   // The file now contains a rectangle and a textbox grouped together.
    }
}
```

*Why this final step matters* – `InsertNode` 호출은 빌더 커서가 위치한 정확한 위치에 그룹화된 도형을 삽입합니다. `doc.Save` 메서드는 **save docx file** 작업을 수행하여 완전한 Word 문서를 디스크에 저장합니다.

> **결과:** Microsoft Word에서 *GroupShape.docx*를 열면 왼쪽에 사각형이, 오른쪽에 텍스트 상자가 표시되며 두 도형은 하나의 그룹으로 함께 고정됩니다. 그룹을 단위로 이동하거나 크기를 조정하고 추가 서식을 적용할 수 있습니다.

## 전체 실행 가능한 예제

아래 코드를 새 콘솔 프로젝트(`dotnet new console`)에 복사하고 `dotnet run`을 실행하세요. 프로그램은 프로젝트 출력 폴더에 `GroupShape.docx`를 생성합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a group shape container.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,
            Height = 200
        };

        // 3. Add rectangle shape.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);

        // 4. Add textbox shape with text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,
            Top = 10
        };
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);
        group.AppendChild(textBox);

        // 5. Insert the group into the document.
        builder.InsertNode(group);

        // 6. Save the document.
        doc.Save("GroupShape.docx");
    }
}
```

### 예상 출력

* 출력 디렉터리에 **GroupShape.docx** 파일이 생성됩니다.
* 파일을 열면 왼쪽에 사각형 도형이, 오른쪽에 “Grouped text”가 들어 있는 텍스트 상자가 표시되며 두 도형이 함께 고정됩니다.
* 어느 하나의 도형을 선택하면 전체 그룹이 이동하여 **group shapes word** 기능이 정상적으로 작동함을 확인할 수 있습니다.

## 일반적인 변형 및 엣지 케이스

| Situation | Recommendation |
|-----------|----------------|
| 두 개 이상의 도형이 필요함 | `builder.InsertNode`를 호출하기 전에 `group`에 추가 `Shape` 객체를 추가합니다. |
| 그룹을 특정 페이지에 표시하고 싶음 | `builder.MoveToDocumentEnd()` 또는 `builder.MoveToPage(pageNumber)`를 사용해 빌더 커서를 이동합니다. |
| 다른 단위가 필요함(예: 센티미터) | Word가 기대하는 단위인 포인트로 변환하기 위해 `ConvertUtil.InchToPoint(1.0)`을 사용합니다. |
| 텍스트 상자가 텍스트를 감싸도록 하고 싶음 | 텍스트 상자를 만든 후 `textBox.TextBoxWrap = TextBoxWrapType.Square`를 설정합니다. |
| 이전 .NET Framework 버전 사용 | 같은 API가 .NET Framework 4.7 이상에서도 작동하지만, 올바른 Aspose.Words 버전을 참조해야 합니다. |

**팁:** 모든 하위 도형을 추가한 *후에* 그룹의 `Width`와 `Height`를 설정하세요. 이렇게 하면 그룹이 내용 전체를 완전히 둘러싸게 되어 Word에서 문서를 열 때 클리핑이 방지됩니다.

## 결론

이제 Aspose.Words for .NET을 사용하여 **save docx file**하면서 **add rectangle shape**, **group shapes word**, **set shape dimensions**, **create textbox programmatically**를 수행하는 방법을 알게 되었습니다. 전체 예제는 차트, 이미지 등 보다 복잡한 레이아웃에 적용할 수 있는 깔끔하고 반복 가능한 패턴을 보여줍니다.

## 다음에 배워야 할 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 단계별 설명과 함께 완전한 코드 예제가 포함되어 있어 추가 API 기능을 숙달하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}