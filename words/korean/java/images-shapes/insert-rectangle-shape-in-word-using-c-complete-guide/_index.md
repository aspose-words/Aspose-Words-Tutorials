---
category: general
date: 2026-08-04
description: C#를 사용하여 Word 문서에 사각형 도형을 삽입합니다. Word에서 도형을 그룹화하는 방법, 문서를 docx 형식으로 저장하는
  방법, 그리고 고급 레이아웃을 위해 DocumentBuilder를 사용하는 방법을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to group shapes
- group shapes in word
- save document as docx
- how to use builder
language: ko
lastmod: 2026-08-04
og_description: C#를 사용하여 Word 파일에 사각형 도형을 삽입하고, 고급 레이아웃을 위해 도형을 그룹화합니다. 이 튜토리얼에서는
  문서를 docx 형식으로 저장하고 DocumentBuilder를 효율적으로 사용하는 방법도 다룹니다.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with C# DocumentBuilder
og_title: Word에 사각형 도형 삽입 – C# 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Insert rectangle shape in a Word document with C#. Learn how to group
    shapes in Word, save document as docx, and use DocumentBuilder for advanced layouts.
  headline: Insert rectangle shape in Word using C# – complete guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: C#를 사용하여 Word에 사각형 도형 삽입하기 – 완전 가이드
url: /ko/java/images-shapes/insert-rectangle-shape-in-word-using-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#를 사용하여 Word에 사각형 도형 삽입 – 완전 가이드

Word 문서에 **사각형 도형을 삽입**해야 할 경우, 이 튜토리얼에서 정확한 방법을 보여드립니다. 또한 **Word에서 도형을 그룹화**하는 방법, **문서를 docx로 저장**하는 방법, 그리고 **Builder**를 사용해 깔끔하고 유지보수 가능한 코드를 작성하는 방법도 배울 수 있습니다.

도형 작업은 보고서, 증명서, 맞춤 레이아웃 등을 프로그래밍으로 생성할 때 흔히 요구되는 기능입니다. 이 가이드를 끝까지 따라오시면 사각형을 만들고, 타원을 추가하고, 두 도형을 그룹화한 뒤 DOCX 파일로 저장하는 완전 실행 가능한 예제를 얻을 수 있습니다.

## 사전 요구 사항

시작하기 전에 다음이 설치되어 있는지 확인하세요:

* .NET 6.0 이상  
* Visual Studio 2022 (또는 C#를 지원하는 IDE)  
* **Aspose.Words for .NET** 라이브러리 (NuGet을 통해 제공)

다음 명령으로 라이브러리를 추가할 수 있습니다:

```bash
dotnet add package Aspose.Words
```

## DocumentBuilder로 사각형 도형 삽입

첫 번째 단계는 새 `Document`와 `DocumentBuilder`를 만드는 것입니다. Builder는 도형을 포함한 콘텐츠 삽입을 위한 유창한 API를 제공합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document.
        Document document = new Document();

        // Initialize the builder that will edit the document.
        DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder` 인스턴스는 **사각형 도형을 삽입**하고 다른 요소들을 추가할 때 핵심이 되는 객체입니다. 현재 문서 내 커서 위치를 추적하므로 삽입이 정확히 필요한 위치에 이루어집니다.

## 사각형 도형 삽입 방법

Builder가 준비되면 `InsertShape`를 호출합니다. `ShapeType`, 너비, 높이를 포인트 단위(1 pt ≈ 1/72 in)로 지정합니다.

```csharp
        // Insert a rectangle of 100 pt width and 50 pt height.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
```

*왜 중요한가*: `FillColor`와 `StrokeColor`를 설정하면 사각형이 시각적으로 구분되어 나중에 다른 도형과 그룹화할 때 도움이 됩니다.

## Word에서 도형을 그룹화하는 방법

도형을 그룹화하면 여러 객체를 하나의 엔터티처럼 이동, 회전, 서식 지정할 수 있습니다. 사각형을 삽입한 뒤, 예시와 같이 또 다른 도형(타원)을 추가하고 `GroupShape`를 생성합니다.

```csharp
        // Insert an ellipse of 80 pt diameter.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // Insert an empty group container.
        GroupShape groupShape = builder.InsertGroupShape();

        // Add the rectangle and ellipse to the group.
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
```

`InsertGroupShape` 호출은 자식 도형을 任意 개수 담을 수 있는 자리표시자를 생성합니다. 사각형과 타원을 추가함으로써 **Word에서 도형을 그룹화**하게 됩니다. 그룹은 단일 도형처럼 동작하므로 위치를 재조정하거나 테두리를 적용하거나 크기를 조정해도 각 자식 도형의 내부 레이아웃은 영향을 받지 않습니다.

### 전문가 팁

그룹화 후 페이지 기준으로 그룹 위치를 변경할 수 있습니다:

```csharp
        // Move the whole group 150 pt right and 100 pt down.
        groupShape.Left = 150;
        groupShape.Top = 100;
```

## 문서를 docx로 저장

도형 배치가 완료되면 파일을 영구히 저장해야 합니다. `Document.Save` 메서드는 파일 확장자를 기반으로 형식을 자동 결정합니다. **문서를 docx로 저장**하려면 경로를 `.docx`로 끝나게 하면 됩니다.

```csharp
        // Save the document to the output folder.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

프로그램을 실행하면 `output.docx`가 생성됩니다. Microsoft Word에서 파일을 열면 연한 파란색 사각형과 연한 코랄 색 타원이 함께 그룹화된 모습을 확인할 수 있습니다. 그룹을 클릭하면 하나의 객체처럼 이동할 수 있습니다.

## DocumentBuilder를 효과적으로 사용하는 방법

`DocumentBuilder`는 도형 삽입뿐 아니라 텍스트, 표, 머리글, 바닥글도 처리합니다. 도형 생성과 텍스트 삽입을 결합할 때는 다른 위치에 콘텐츠를 삽입해야 한다면 커서를 재설정하는 것을 기억하세요:

```csharp
        // Move the cursor to a new paragraph after the group.
        builder.Writeln(); // Inserts a line break.
        builder.Font.Size = 12;
        builder.Writeln("Shapes have been added and grouped successfully.");
```

Builder의 상태를 명시적으로 관리하면 의도치 않은 덮어쓰기를 방지하고 코드 유지보수가 쉬워집니다.

## 엣지 케이스 및 변형

| 상황 | 권장 접근 방식 |
|-----------|----------------------|
| **두 개 이상 도형** | 각 도형을 삽입한 뒤 저장하기 전에 모든 도형에 대해 `AppendChild`를 호출합니다. |
| **중첩 그룹** | 그룹을 만든 뒤 도형을 추가하고, 그 그룹을 다른 `GroupShape`에 삽입합니다. |
| **다른 측정 단위** | 픽셀 단위가 있다면 `builder.ConvertPixelsToPoints`를 사용합니다. |
| **구버전 Word와 호환** | 확장자를 `.doc`로 바꿔 저장하면 대부분의 도형 기능이 여전히 동작합니다. |

## 완전한 작동 예제

아래는 새 콘솔 프로젝트에 복사‑붙여넣기 할 수 있는 전체 프로그램입니다. 추가 스니펫은 필요하지 않습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;

        // 3️⃣ Insert an ellipse shape.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // 4️⃣ Create a group shape and add both shapes.
        GroupShape groupShape = builder.InsertGroupShape();
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Optional: reposition the group.
        groupShape.Left = 150;
        groupShape.Top = 100;

        // 5️⃣ Add a caption below the group.
        builder.Writeln();
        builder.Font.Size = 12;
        builder.Writeln("Grouped rectangle and ellipse created with DocumentBuilder.");

        // 6️⃣ Save the document as DOCX.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

**예상 결과**: `output.docx`를 열면 연한 파란색 사각형과 연한 코랄 색 타원이 함께 그룹화되어 왼쪽 여백에서 150 pt, 위쪽에서 100 pt 위치에 표시됩니다. 캡션은 그룹 아래에 나타납니다.

## 결론

이제 C#를 사용해 Word 파일에 **사각형 도형을 삽입**하고, **Word에서 도형을 그룹화**하며, Aspose.Words `DocumentBuilder`를 이용해 **문서를 docx로 저장**하는 방법을 알게 되었습니다. 이 단계들을 마스터하면 코드만으로 복잡한 레이아웃—증명서, 보고서, 맞춤 양식 등을 완전히 구축할 수 있습니다.

다음으로 **텍스트 상자 추가**, **표 작업**, **PDF로 내보내기**와 같은 관련 주제를 탐색해 보세요. 각각은 방금 연습한 `DocumentBuilder` 기본기를 기반으로 합니다.

Word 문서 자동화가 준비되셨나요? 예제를 확장해 더 많은 도형을 추가하고, 그라데이션을 적용하거나, 데이터를 순회해 한 번에 전체 보고서를 생성해 보세요. 즐거운 코딩 되세요!


## 다음에 배워야 할 내용


다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접하게 관련된 주제를 다룹니다. 각 리소스에는 단계별 설명과 완전한 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}