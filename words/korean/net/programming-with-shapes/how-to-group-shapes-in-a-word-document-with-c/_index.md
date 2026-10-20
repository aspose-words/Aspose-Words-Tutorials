---
category: general
date: 2026-08-14
description: C#를 사용하여 Word 문서에서 도형을 그룹화하는 방법. Word 문서 만들기, 사각형 도형 삽입, Word에서 도형 그룹화,
  그리고 문서를 docx 형식으로 저장하는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
language: ko
lastmod: 2026-08-14
og_description: C#를 사용하여 Word 문서에서 도형을 그룹화하는 방법. 이 완전한 튜토리얼을 따라 Word 파일을 만들고, 사각형
  도형을 삽입한 뒤, Word에서 도형을 그룹화하고 결과를 docx로 저장하세요.
og_image_alt: Screenshot showing how to group shapes in a Word document using C#
og_title: C#를 사용하여 Word 문서에서 도형을 그룹화하는 방법 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  headline: How to group shapes in a Word document with C#
  type: TechArticle
- description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  name: How to group shapes in a Word document with C#
  steps:
  - name: Create a new blank document
    text: The first thing you do when you want to **create Word document** programmatically
      is instantiate a `Document` object. This object represents the entire .docx
      file in memory.
  - name: Insert a rectangle shape
    text: To demonstrate **insert rectangle shape**, we use the `InsertShape` method.
      The rectangle will act as the first member of the group.
  - name: Insert an ellipse shape
    text: Next, we **insert ellipse shape** (the API calls it `Ellipse`). This will
      be the second member of the group.
  - name: Group the rectangle and ellipse
    text: Now we answer the central question **how to group shapes** in a Word document.
      Aspose.Words provides `AppendGroupShape` to create a group container, and then
      you call `Group()` on that container.
  - name: Save the document as a DOCX file
    text: The final step is to **save document as docx**. You can choose any path
      you like; the example uses a placeholder `"YOUR_DIRECTORY"` that you should
      replace with a real folder.
  - name: Expected output
    text: When you open `groupedShapes.docx` in Microsoft Word, you will see a light‑blue
      rectangle and a light‑coral ellipse locked together. Clicking either shape selects
      both, allowing you to move or resize them as a single unit.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: C#를 사용하여 Word 문서에서 도형을 그룹화하는 방법
url: /ko/net/programming-with-shapes/how-to-group-shapes-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#를 사용하여 Word 문서에서 도형을 그룹화하는 방법

Word 문서에서 **도형을 그룹화하는 방법**이 필요하다면, 이 가이드는 C#와 Aspose.Words 라이브러리를 사용한 정확한 단계들을 보여줍니다. Word 문서를 생성하고, 사각형 도형을 삽입하고, Word에서 도형을 그룹화하며, 마지막으로 **문서를 docx로 저장**하는 과정을 하나의 실행 가능한 프로그램으로 확인할 수 있습니다.

보고서, 계약서 또는 마케팅 브로셔를 프로그래밍 방식으로 생성할 때 도형을 만들고 조작하는 것은 흔한 요구 사항입니다. 이 튜토리얼을 마치면 .NET 프로젝트 어디에든 넣어 사용할 수 있는 재사용 가능한 코드 스니펫을 얻게 됩니다.

## 사전 요구 사항

시작하기 전에 다음이 설치되어 있는지 확인하세요.

- .NET 6.0 이상 설치  
- Visual Studio 2022 (또는 .NET을 지원하는 IDE)  
- Aspose.Words for .NET 라이선스(또는 무료 평가판)  
- C# 구문에 대한 기본 지식  

추가 NuGet 패키지는 `Aspose.Words` 외에 필요하지 않습니다.

## Word 문서에서 도형을 그룹화하는 방법

솔루션의 핵심은 다섯 단계 프로세스입니다. 각 단계는 자세히 설명되며, 전체 소스 코드는 기사 말미에 제공됩니다.

### 단계 1: 새 빈 문서 만들기

프로그램matically **Word 문서 생성**을 원할 때 가장 먼저 하는 일은 `Document` 객체를 인스턴스화하는 것입니다. 이 객체는 메모리 내 전체 .docx 파일을 나타냅니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Obtain a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:** `DocumentBuilder`는 텍스트, 표 및 도형을 삽입할 때 기본 노드 트리를 수동으로 다루지 않아도 되는 고수준 도우미입니다.

### 단계 2: 사각형 도형 삽입

**insert rectangle shape**를 시연하기 위해 `InsertShape` 메서드를 사용합니다. 사각형은 그룹의 첫 번째 구성원이 됩니다.

```csharp
// Insert a rectangle (100x50 points) at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Optional: set a fill color so the shape is visible
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

**Why this matters:** 도형은 삽입 지점을 기준으로 배치됩니다. 채우기 색을 지정하면 결과 문서를 열었을 때 도형을 쉽게 확인할 수 있습니다.

### 단계 3: 타원 도형 삽입

다음으로 **insert ellipse shape**(API에서는 `Ellipse`라고 부릅니다)를 삽입합니다. 이는 그룹의 두 번째 구성원이 됩니다.

```csharp
// Insert an ellipse (80x40 points) right after the rectangle
Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

**Why this matters:** 타원을 사각형 바로 뒤에 삽입하면 두 도형이 동일한 단락에 들어가게 되어 나중에 그룹화가 간단해집니다.

### 단계 4: 사각형과 타원 그룹화

이제 Word 문서에서 **도형을 그룹화하는 방법**이라는 핵심 질문에 답합니다. Aspose.Words는 그룹 컨테이너를 만들기 위해 `AppendGroupShape`를 제공하며, 그 컨테이너에서 `Group()`을 호출합니다.

```csharp
// Get the first paragraph of the document (where the shapes live)
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;

// Create a group shape that contains the rectangle and ellipse
Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });

// Turn the container into a true group – the shapes will move and scale together
groupedShape.Group();
```

**Why this matters:** 그룹화가 되면 `groupedShape`에 적용되는 모든 변환(이동, 크기 조정, 회전)이 자동으로 사각형과 타원 모두에 적용됩니다. 이는 생성된 문서에서 레이아웃 일관성을 유지하는 데 필수적입니다.

### 단계 5: 문서를 DOCX 파일로 저장

마지막 단계는 **문서를 docx로 저장**하는 것입니다. 원하는 경로를 선택할 수 있으며, 예제에서는 `"YOUR_DIRECTORY"`라는 자리 표시자를 사용합니다. 실제 폴더 경로로 교체하세요.

```csharp
// Define the output path (ensure the directory exists)
string outputPath = @"C:\Temp\groupedShapes.docx";

// Save the document in DOCX format
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

**Why this matters:** DOCX 형식으로 저장하면 그룹 메타데이터가 보존되어 Microsoft Word에서 파일을 열면 사각형과 타원이 하나의 객체로 표시됩니다.

## 전체 실행 가능한 예제

아래는 다섯 단계를 모두 결합한 완전한 프로그램입니다. 새 콘솔 프로젝트에 복사하고, Aspose.Words NuGet 패키지를 복원한 뒤 실행하세요.

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
            // Step 1: Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a rectangle shape (100x50 points)
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangleShape.FillColor = System.Drawing.Color.LightBlue;

            // Step 3: Insert an ellipse shape (80x40 points)
            Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
            ellipseShape.FillColor = System.Drawing.Color.LightCoral;

            // Step 4: Group the rectangle and ellipse
            Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
            Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });
            groupedShape.Group();

            // Step 5: Save the document as DOCX
            string outputPath = @"C:\Temp\groupedShapes.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"Document saved successfully to {outputPath}");
        }
    }
}
```

### 예상 출력

Microsoft Word에서 `groupedShapes.docx`를 열면 연한 파란색 사각형과 연한 코랄 색 타원이 함께 고정된 모습을 볼 수 있습니다. 두 도형 중 하나를 클릭하면 둘 다 선택되어 단일 객체처럼 이동하거나 크기를 조정할 수 있습니다.

## 일반적인 질문 및 엣지 케이스

| Question | Answer |
|----------|--------|
| **두 개 이상의 도형을 그룹화할 수 있나요?** | 예. `AppendGroupShape`에 원하는 만큼의 `Shape` 객체를 전달하면 됩니다. 메서드는 배열을 받으므로 컬렉션을 동적으로 구성할 수 있습니다. |
| **그룹을 표 셀에 고정해야 하면 어떻게 해야 하나요?** | 셀의 단락 안에 도형을 삽입한 뒤 해당 단락에서 `AppendGroupShape`를 호출합니다. 그룹은 셀의 고정을 자동으로 상속합니다. |
| **그룹화가 기본 XML에 영향을 미치나요?** | Aspose.Words는 자식 도형을 포함하는 `<w:grpSp>` 요소를 작성합니다. Word는 이를 그룹으로 인식하여 상대 위치를 보존합니다. |
| **나중에 그룹을 해제하려면 어떻게 하나요?** | `groupedShape.Ungroup()`을 호출하면 개별 도형을 반환하므로 별도로 조작할 수 있습니다. |
| **많은 도형을 그룹화하면 성능에 영향을 주나요?** | 그룹 자체는 비용이 적지만, 수백 개의 도형이 포함된 대형 그룹을 렌더링하면 파일 크기가 증가할 수 있습니다. 크기가 문제가 될 경우 이미지를 평면화하는 것을 고려하세요. |

## 전문가 팁

- **명시적 위치 설정** (`Left`, `Top`)을 사용하면 그룹화 전에 정확한 정렬이 필요할 때 유용합니다.  
- **`Shape.WrapType = WrapType.Inline`**을 사용하면 그룹이 떠 있는 객체가 아니라 단락 요소처럼 동작합니다.  
- **그룹에 선 스타일 적용** (`groupedShape.LineFormat`)을 통해 전체 컬렉션에 테두리를 부여합니다.  
- **그룹 재사용**: `Group()` 호출 후 `groupedShape`를 복제하여 문서의 다른 위치에 삽입할 수 있습니다.

## 다음 단계

이제 **도형을 그룹화하는 방법**을 알게 되었으니 다음과 같은 관련 주제를 탐색해 보세요.

- **Insert rectangle shape**를 사용해 도형 안에 사용자 정의 텍스트나 이미지를 삽입합니다.  
- **Create complex diagrams**를 위해 그룹을 중첩(그룹 안에 그룹)합니다.  
- **Export the document as PDF**를 사용해 도형 그룹화를 유지하면서 문서를 PDF로 내보냅니다 (`doc.Save("output.pdf", SaveFormat.Pdf)`).  

이러한 내용은 여기서 다룬 기본 원리를 기반으로 하므로 Word 자동화 도구 키트를 확장하는 데 큰 도움이 됩니다.

## 결론

이 튜토리얼은 C#를 사용하여 Word 문서에서 **도형을 그룹화하는 방법**을 시연했습니다. **Word 문서 생성**, **사각형 도형 삽입**, **Word에서 도형 그룹화**, 그리고 **문서를 docx로 저장**하는 과정을 배웠습니다. 완전한 실행 예제와 실용적인 팁을 통해 어떤 문서 생성 워크플로에도 도형 그룹화를 손쉽게 통합할 수 있습니다. 즐거운 코딩 되세요!

## 다음에 배워야 할 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스에는 완전한 코드 예제와 단계별 설명이 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [Aspose.Words for .NET를 사용하여 Word 문서에서 그룹 도형 만들기](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words for .NET를 사용하여 Word 문서에 도형 삽입하기](/words/english/net/working-with-shapes/insert-shape/)
- [C#를 사용하여 Word에서 사각형 도형 만들기 – 단계별 가이드](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}