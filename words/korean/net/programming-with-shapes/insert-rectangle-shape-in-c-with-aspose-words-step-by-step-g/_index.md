---
category: general
date: 2026-08-07
description: Aspose.Words를 사용하여 C#에서 사각형 모양을 삽입하고, 모양을 숨기는 방법, 채우기 색상을 설정하는 방법, 그리고
  사각형 모양을 Word 문서에 효율적으로 추가하는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- how to insert shape
- how to set fill color
- add rectangle shape
language: ko
lastmod: 2026-08-07
og_description: C#를 사용하여 Word 문서에 사각형 도형을 삽입합니다. 도형을 숨기는 방법, 채우기 색상을 설정하는 방법, 그리고
  Aspose.Words를 사용해 사각형 도형을 추가하는 방법을 배워보세요.
og_image_alt: Screenshot showing a hidden yellow rectangle shape inserted into a Word
  document
og_title: C#에서 사각형 도형 삽입 – 완전한 Aspose.Words 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  headline: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  name: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  steps:
  - name: What each step does
    text: '| Step | Reason | |------|--------| | **Create a new document** | Provides
      a clean canvas; you can also load an existing .docx by passing a file path to
      `new Document(path)`. | | **Initialize DocumentBuilder** | `DocumentBuilder`
      is the high‑level helper that lets you insert text, tables, and shapes'
  - name: 1. Making the shape visible again
    text: 'If a later part of your workflow needs to reveal the hidden rectangle,
      you can toggle the flag:'
  - name: 2. Adding a border (stroke)
    text: 'A hidden shape can still have a visible border when you decide to show
      it. Set the `LineColor` and `LineWidth` properties:'
  - name: 3. Positioning the rectangle absolutely
    text: 'For precise layout control, switch the shape’s `WrapType` to `WrapType.Inline`
      (default) or `WrapType.TopBottom` and adjust `Left`/`Top` properties:'
  - name: 4. Using a different measurement unit
    text: 'Aspose.Words works in points (1 pt = 1/72 inch). If you prefer centimeters,
      convert first:'
  - name: Next steps
    text: '* Explore **how to insert shape** inside tables or headers/footers for
      watermarks. * Combine **add rectangle shape** with content controls to create
      dynamic placeholders. * Review Aspose.Words’ **shape manipulation** API for
      advanced features like rotation, gradient fills, and SVG import.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
- document generation
title: Aspose.Words를 사용한 C#에서 사각형 도형 삽입 – 단계별 가이드
url: /ko/net/programming-with-shapes/insert-rectangle-shape-in-c-with-aspose-words-step-by-step-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#와 Aspose.Words를 사용하여 사각형 도형 삽입 – 단계별 가이드

C#에서 Word 문서에 **사각형 도형을 삽입**해야 한다면, 이 가이드가 정확한 방법을 보여줍니다. 채우기 색상을 설정하고, 도형을 숨겨 최종 레이아웃에 나타나지 않게 하며, 파일을 저장하는 방법을 몇 줄의 코드만으로 확인할 수 있습니다.

다음 섹션에서는 사전 요구 사항, 전체 코드 목록, 각 단계에 대한 설명, 도형을 다시 보이게 하거나 다른 색상을 사용하는 등 일반적인 변형에 대한 팁을 모두 다룹니다. 마지막까지 읽으면 **사각형 도형을** 어떤 .docx 파일에도 프로그래밍 방식으로 추가할 수 있게 됩니다.

## 사전 요구 사항

시작하기 전에 다음이 준비되어 있어야 합니다:

* **Aspose.Words for .NET** (버전 23.10 이상). NuGet을 통해 설치할 수 있습니다:

  ```bash
  dotnet add package Aspose.Words
  ```

* .NET 6.0 SDK 이상이 머신에 설치되어 있어야 합니다.
* C#와 Visual Studio(또는 선호하는 IDE)에 대한 기본적인 이해가 필요합니다.

추가 라이브러리는 필요하지 않습니다—도형 관련 API는 핵심 Aspose.Words 패키지에 포함되어 있습니다.

## Aspose.Words로 사각형 도형 삽입

솔루션의 핵심은 빈 문서를 만들고, 사각형을 삽입하고, 색을 지정하고, 숨긴 뒤 파일을 저장하는 짧고 독립적인 프로그램입니다. 아래는 각 라인의 *이유*를 설명하는 인라인 주석이 포함된 전체 소스 코드입니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Required for Color struct

// 1️⃣ Create a new, empty Word document.
Document document = new Document();

// 2️⃣ Obtain a DocumentBuilder – the primary API for editing the document.
DocumentBuilder builder = new DocumentBuilder(document);

// 3️⃣ Insert a rectangle shape of 100 × 50 points.
//    ShapeType.Rectangle tells Aspose.Words to create a simple rectangular drawing object.
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Set the shape's fill color to yellow.
//    The FillColor property accepts a System.Drawing.Color value.
rectangleShape.FillColor = Color.Yellow;

// 5️⃣ Hide the shape so it does not appear in the rendered document.
//    When Hidden = true, the shape is stored in the file but omitted from layout.
//    This is useful for placeholders, bookmarks, or metadata.
rectangleShape.Hidden = true;

// 6️⃣ Save the document to disk.
//    Change the path to a folder you have write access to.
document.Save(@"C:\Temp\HiddenRectangleShape.docx");
```

### 각 단계가 수행하는 작업

| 단계 | 이유 |
|------|--------|
| **Create a new document** | 깨끗한 캔버스를 제공합니다; `new Document(path)`에 파일 경로를 전달하면 기존 .docx를 로드할 수도 있습니다. |
| **Initialize DocumentBuilder** | `DocumentBuilder`는 텍스트, 표, 도형을 낮은 수준의 노드 트리를 직접 다루지 않고 삽입할 수 있게 해 주는 고수준 도우미입니다. |
| **Insert rectangle shape** | `InsertShape` 메서드는 추가 커스터마이징(크기, 위치, 테두리 등)이 가능한 `Shape` 객체를 반환합니다. |
| **Set fill color** | `FillColor` 속성은 내부 색상을 제어합니다; `Color.Red`, `Color.FromArgb(255, 0, 255, 0)` 등 어떤 `Color` 값도 사용할 수 있습니다. |
| **Hide the shape** | `Hidden = true`는 레이아웃 시 Word가 도형을 무시하도록 하면서도 문서 XML에는 그대로 남깁니다. 이는 보이지 않는 객체를 저장하는 표준 방법입니다. |
| **Save the document** | 변경 사항을 .docx 파일에 영구 저장합니다. 저장된 파일에는 숨겨진 사각형 도형이 포함됩니다. |

## 도형의 채우기 색상 설정 방법

채우기 색상을 변경하는 것은 `FillColor` 속성에 `System.Drawing.Color`를 할당하는 것만큼 간단합니다. 사용자 정의 색상이 필요하면 `Color.FromArgb`를 사용하세요:

```csharp
// Example: set a semi‑transparent teal fill
rectangleShape.FillColor = Color.FromArgb(128, 0, 128, 128);
```

*Why this matters*: 채우기 색상은 도형의 XML(`\<w:fill\>` 속성)에 저장됩니다. 도형이 숨겨져 있어도 색상은 존재하므로(예: 색상 코드를 기반으로 메타데이터 추출) 후속 처리에 유용할 수 있습니다.

## 최종 문서에서 도형 숨기기

`Hidden` 플래그는 `Shape` 클래스의 부울 속성입니다. 이를 `true`로 설정하면 Word 레이아웃 엔진이 도형을 무시합니다.

```csharp
rectangleShape.Hidden = true;
```

**Common pitfalls**  
* **Hidden vs. Visible** – 나중에 도형을 표시해야 하면 간단히 `Hidden = false`로 설정하면 됩니다.  
* **Compatibility** – Word 구버전(2007 이전)은 숨겨진 그리기 객체를 다르게 처리할 수 있습니다. Aspose.Words는 해당 플래그를 적절한 OOXML 요소에 저장하여 호환성을 유지합니다.

## 프로그래밍 방식으로 도형 삽입하기

예제는 사각형을 사용하지만 동일한 `InsertShape` 메서드로 다른 많은 도형(타원, 삼각형, 선 등)도 삽입할 수 있습니다. 첫 번째 인자는 `ShapeType` 열거형 값입니다:

```csharp
// Insert an ellipse with the same dimensions
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
ellipse.FillColor = Color.LightBlue;
```

**Tip**: 페이지의 특정 위치에 도형을 배치해야 한다면 `InsertShape`를 호출하기 전에 `builder.MoveTo`를 사용해 삽입 지점을 설정하세요.

## 기존 문서에 사각형 도형 추가하기

대부분 템플릿을 확장하는 경우가 많으며, 처음부터 시작하지 않을 수도 있습니다. 단계 1을 다음과 같이 교체합니다:

```csharp
// Load an existing .docx file
Document document = new Document(@"C:\Templates\ReportTemplate.docx");
```

그 이후 단계는 모두 동일하게 유지되며, 도형은 빌더 커서가 위치한 곳(보통 문서 끝)에 추가됩니다.

## 엣지 케이스 및 변형 처리

### 1. 도형을 다시 보이게 만들기

워크플로우의 이후 단계에서 숨겨진 사각형을 표시해야 하면 플래그를 토글하면 됩니다:

```csharp
rectangleShape.Hidden = false;   // Shape will now be rendered
```

### 2. 테두리(스트로크) 추가하기

숨겨진 도형이라도 표시할 때는 눈에 보이는 테두리를 가질 수 있습니다. `LineColor`와 `LineWidth` 속성을 설정하세요:

```csharp
rectangleShape.LineColor = Color.Black;
rectangleShape.LineWeight = 1.5; // points
```

### 3. 사각형을 절대 위치에 배치하기

정밀 레이아웃 제어를 위해 도형의 `WrapType`을 `WrapType.Inline`(기본) 또는 `WrapType.TopBottom`으로 전환하고 `Left`/`Top` 속성을 조정합니다:

```csharp
rectangleShape.WrapType = WrapType.TopBottom;
rectangleShape.Left = 72;   // 1 inch from the left margin
rectangleShape.Top = 144;   // 2 inches from the top margin
```

### 4. 다른 측정 단위 사용하기

Aspose.Words는 포인트 단위(1 pt = 1/72 인치)로 작업합니다. 센티미터를 선호한다면 먼저 변환하세요:

```csharp
float cmToPoints = 28.3465f; // 1 cm ≈ 28.3465 pt
float width = 5 * cmToPoints;   // 5 cm wide
float height = 2 * cmToPoints;  // 2 cm tall
Shape cmRectangle = builder.InsertShape(ShapeType.Rectangle, width, height);
```

## 전체 실행 가능한 예제

아래는 복사·붙여넣기·실행할 수 있는 *전체* 프로그램입니다. 필요한 모든 `using` 지시문이 포함되어 있으며, 환경에 맞게 절대 경로를 조정해야 합니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class InsertRectangleShapeDemo
{
    static void Main()
    {
        // Create a blank document.
        Document doc = new Document();

        // Use DocumentBuilder to edit the document.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 100 × 50 pt rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // Set the fill color to yellow.
        rect.FillColor = Color.Yellow;

        // Hide the shape so it does not affect layout.
        rect.Hidden = true;

        // Save the result.
        string outputPath = @"C:\Temp\HiddenRectangleShape.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Expected result**: 파일 `HiddenRectangleShape.docx`를 Microsoft Word에서 열면 *보이는 도형이 없지만*, 숨겨진 사각형이 문서 XML에 존재합니다. `.docx`를 zip 아카이브로 열어 `word/document.xml`에서 `w:fill="yellow"` 및 `w:hidden="true"` 속성을 가진 `<w:shape>` 요소를 확인하면 존재를 검증할 수 있습니다.

## 결론

이제 C#과 Aspose.Words를 사용해 Word 문서에 **사각형 도형을 삽입**, **채우기 색상을 설정**, 그리고 **도형을 숨겨** 최종 레이아웃에 보이지 않게 하는 방법을 알게 되었습니다. 동일한 패턴을 다른 도형 유형, 사용자 정의 색상, 기존 템플릿에도 적용할 수 있습니다. 테두리, 절대 위치 지정, 다양한 측정 단위를 실험해 보면서 요구 사항에 정확히 맞는 도형을 만들 수 있습니다.

### 다음 단계

* 표나 머리글/바닥글 내부에 **도형 삽입**을 탐색해 워터마크를 만들기.  
* **사각형 도형 추가**와 콘텐츠 컨트롤을 결합해 동적 플레이스홀더 생성하기.  
* 회전, 그라디언트 채우기, SVG 가져오기와 같은 고급 기능을 위해 Aspose.Words의 **도형 조작** API를 검토하기.

코드를 자신의 프로젝트에 자유롭게 적용하고, 다음에 해결한 도형 관련 과제가 무엇인지 댓글로 알려 주세요!

## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 다룬 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스는 완전한 동작 코드 예제와 단계별 설명을 포함해 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용할 수 있도록 돕습니다.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}