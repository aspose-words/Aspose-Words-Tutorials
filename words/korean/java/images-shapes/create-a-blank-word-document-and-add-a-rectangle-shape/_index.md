---
category: general
date: 2026-10-23
description: Aspose.Words를 사용하여 빈 Word 문서를 만들고, 사각형 도형을 추가한 뒤, Word에서 해당 도형을 숨깁니다.
  .NET 개발자를 위한 단계별 코드.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- how to insert shape
- hide shape word
language: ko
lastmod: 2026-10-23
og_description: 빈 Word 문서를 만든 다음 사각형 도형을 추가하고, Aspose.Words를 사용해 Word에서 해당 도형을 숨깁니다.
  전체 C# 예제를 따라 보세요.
og_image_alt: Screenshot of a Word document containing a hidden rectangle shape
og_title: 빈 Word 문서를 만들고 숨겨진 사각형 모양을 추가하세요
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create a blank Word document, add a rectangle shape, and hide the shape
    in Word using Aspose.Words. Step‑by‑step code for .NET developers.
  headline: Create a blank Word document and add a rectangle shape
  type: TechArticle
tags:
- Aspose.Words
- .NET
- Word automation
title: 빈 워드 문서를 만들고 사각형 도형을 추가하기
url: /ko/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 빈 Word 문서를 만들고 사각형 도형 추가하기

If you need to **create a blank Word document**, this guide shows you how to do it with Aspose.Words for .NET. You’ll also learn **how to insert shape**—specifically a rectangle—and **hide shape word** so it doesn’t affect the layout.

The tutorial walks through every line of code, explains why each step matters, and covers common pitfalls such as hidden‑shape visibility in different Word view modes. By the end you will have a fully functional `.docx` file that contains a hidden rectangle shape you can later reveal or manipulate programmatically.

## 사전 요구 사항

- .NET 6.0 이상 (코드는 .NET Framework 4.6+에서도 작동합니다)
- Aspose.Words for .NET NuGet 패키지 (`Install-Package Aspose.Words`)
- Visual Studio 2022 또는 C# 확장이 설치된 VS Code와 같은 개발 환경
- C# 구문 및 Word 문서 개념에 대한 기본적인 이해

No additional Office installation is required because Aspose.Words works completely in memory.

## 빈 Word 문서 만들기

The first step is to instantiate an empty `Document` object. This object represents a Word file that contains no sections, paragraphs, or content yet.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

**왜 중요한가:**  
A blank `Document` gives you a clean canvas. If you start from an existing template, hidden shapes could inherit unwanted styles. Starting from scratch ensures the rectangle shape you add later is the only content you control.

## 문서에 사각형 도형 추가하기

Next, we need a `DocumentBuilder` to place content into the document. The builder’s `InsertShape` method is the standard way **to insert shape** objects, such as rectangles, circles, or custom drawings.

```csharp
// Step 2: Initialize a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(document);

// Step 3: Insert a rectangle shape of size 200x100 points
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**왜 중요한가:**  
`InsertShape` returns a `Shape` object that you can further configure (color, line style, etc.). The dimensions are given in points (1 point = 1/72 inch), which matches Word’s internal measurement system.

### 선택 사항: 사각형 스타일 지정 (선택 사항)

If you want the rectangle to have a visible border when you later un‑hide it, you can set its line weight and color:

```csharp
rectangleShape.LineWeight = 0.5;               // Thin border
rectangleShape.LineColor = System.Drawing.Color.Blue;
```

These lines are optional because the shape will be hidden in the next step.

## Word에서 도형 숨기기

Word allows shapes to be hidden from the layout while still being part of the document’s object model. Setting the `Hidden` property to `true` makes the shape invisible in normal view but still selectable via the API.

```csharp
// Step 4: Hide the shape so it does not appear in the layout
rectangleShape.Hidden = true;
```

**왜 중요한가:**  
A hidden shape is useful for storing metadata, placeholders for later processing, or conditional content that you reveal only under certain circumstances (e.g., when generating a final report). The shape remains in the file, so you can programmatically unhide it later with `rectangleShape.Hidden = false;`.

## 문서 저장하기

Finally, write the document to disk. The file extension determines the Word format; `.docx` is the modern Open XML format.

```csharp
// Step 5: Save the document with the hidden shape
string outputPath = @"C:\Temp\HiddenShape.docx";
document.Save(outputPath);
```

**결과:**  
Opening `HiddenShape.docx` in Microsoft Word shows an otherwise empty page. The rectangle is not visible, but if you go to **Home → Select → Selection Pane**, you will see the shape listed and can toggle its visibility.

## 전체 작동 예제

Below is the complete program you can copy, paste, and run. It includes all necessary `using` statements and comments.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for content insertion
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape (200x100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Optional styling (comment out if not needed)
        rectangleShape.LineWeight = 0.5;
        rectangleShape.LineColor = System.Drawing.Color.Blue;

        // Hide the shape so it does not appear in the layout
        rectangleShape.Hidden = true;

        // Save the document
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**예상 출력:**  

- 콘솔에 저장 경로가 출력됩니다.  
- `HiddenShape.docx`가 Word에서 빈 페이지로 열립니다.  
- 사각형 도형은 존재하지만 숨겨져 있습니다; *Selection Pane*에서 확인하거나 프로그래밍 방식으로 `Hidden = false`를 설정한 뒤 파일을 다시 열어 확인할 수 있습니다.

## 일반적인 질문 및 엣지 케이스

| Question | Answer |
|----------|--------|
| **다른 도형 유형도 숨길 수 있나요?** | 예. 모든 `Shape`(예: `ShapeType.Ellipse`, `ShapeType.Picture`)는 `Hidden` 속성을 지원합니다. |
| **숨겨진 도형이 파일 크기를 증가시킬까요?** | 증가는 미미합니다(몇 킬로바이트 수준) 왜냐하면 도형 데이터가 `.docx` 패키지 내 XML로 저장되기 때문입니다. |
| **도형을 인쇄 보기에서만 표시하고 싶다면?** | `Hidden` 대신 `Shape.IsPrint` 속성을 사용합니다. `IsPrint = false`로 설정하면 인쇄 출력에서는 도형이 숨겨지지만 화면에서는 보입니다. |
| **나중에 도형을 어떻게 다시 표시하나요?** | 문서를 로드하고 도형을 찾은 뒤(예: `Shape.Name`으로), `shape.Hidden = false;`를 설정하고 저장합니다. |
| **이 방법이 .doc(바이너리) 형식에서도 작동하나요?** | 예, Aspose.Words는 `document.Save("file.doc");`를 사용해 `.doc` 형식으로 저장할 수 있습니다. 숨김 플래그가 유지됩니다. |

## 전문가 팁

- **도형에 이름을 지정하세요**: `rectangleShape.Name = "PlaceholderRectangle";`를 사용하면 `document.GetChildNodes(NodeType.Shape, true).Cast<Shape>().FirstOrDefault(s => s.Name == "PlaceholderRectangle")`와 같이 나중에 쉽게 찾을 수 있습니다.
- **배치 처리**: 여러 문서에 숨겨진 도형을 추가해야 할 경우, 코드를 메서드로 감싸고 `DocumentBuilder` 인스턴스를 재사용하세요.
- **성능**: 도형 생성은 비용이 적지만, 큰 문서를 자주 저장하면 I/O가 병목이 될 수 있습니다. 중간 처리에 `MemoryStream` 사용을 고려하세요.

## 결론

You now know how to **create a blank Word document**, **add a rectangle shape**, and **hide shape word** using Aspose.Words for .NET. This technique lets you embed invisible placeholders that you can reveal or manipulate later, a pattern useful for dynamic report generation, conditional content, and document templating.

다음 단계로 살펴볼 수 있는 내용:

- `ShapeType.Picture`를 사용해 사각형을 그림이나 차트로 교체하기.
- 머리글/바닥글 섹션에 **도형 삽입 방법**을 사용해 워터마크 스타일 자리표시자를 만들기.
- 숨겨진 도형을 **사각형 도형 추가** 기반 데이터 검증과 결합하기(예: 도형의 `AlternativeText` 속성에 JSON 저장).

코딩을 즐기세요, 그리고 문서 자동화 요구에 맞게 다른 도형 유형과 가시성 옵션을 자유롭게 실험해 보세요!

## 다음에 배워야 할 내용은?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Word 문서 만들기 – 사각형 도형 및 그림자 추가 방법](/words/english/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/)
- [Aspose.Words for .NET을 사용한 Word 문서에서 그룹 도형 만들기](/words/english/net/working-with-shapes/add-group-shape/)
- [숨겨진 타원 도형이 있는 빈 Word 문서 만들기 – 전체 C# 가이드](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}