---
category: general
date: 2026-09-27
description: Aspose.Words를 사용하여 C#에서 그룹 도형이 포함된 Word 문서를 프로그래밍 방식으로 생성합니다. 이 단계별 가이드를
  따라 파일을 생성하고 유용한 팁을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- how to create group shape word
- Aspose.Words group shape
- C# Word automation
- StructuredDocumentTag example
language: ko
lastmod: 2026-09-27
og_description: Aspose.Words를 사용하여 그룹 도형이 포함된 Word 문서를 프로그래밍 방식으로 생성합니다. 이 튜토리얼은 전체
  C# 코드를 단계별로 안내하고, 각 단계를 설명하며 최종 결과물을 보여줍니다.
og_image_alt: Screenshot of a Word document containing a group shape with a text placeholder
og_title: 그룹 도형이 포함된 Word 문서를 프로그래밍 방식으로 만들기 – C# 가이드
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  headline: Programmatically create a Word document with a group shape
  type: TechArticle
- description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  name: Programmatically create a Word document with a group shape
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works with .NET Framework 4.7+). - Aspose.Words
      for .NET NuGet package (`Install-Package Aspose.Words`). - A C# IDE such as
      Visual Studio 2022 or VS Code with the C# extension.'
  - name: Expected output screenshot (conceptual)
    text: '``` +-----------------------------------------------------------+ | ┌───────────────────────────────────────────────┐
      | | │ [Enter text here] │ | | └───────────────────────────────────────────────┘
      | +-----------------------------------------------------------+ ```'
  - name: Adding more child shapes
    text: 'You can enrich the group by appending additional drawing objects, such
      as pictures or text boxes:'
  - name: Controlling wrapping style
    text: 'If you need the group shape to stay behind text or to have tight wrapping,
      set the `WrapType` property:'
  - name: 'Edge case: Empty group shape'
    text: A `GroupShape` without children renders as an invisible placeholder. Always
      verify that at least one child (e.g., an SDT or a picture) is added; otherwise
      Word may drop the group during saving.
  - name: Compatibility note
    text: Aspose.Words 23.10+ fully supports `GroupShape` and `StructuredDocumentTag`.
      If you target older versions, the `AppendChild` method may behave differently,
      and you might need to call `UpdatePageLayout` after saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 그룹 도형이 포함된 Word 문서를 프로그래밍 방식으로 만들기
url: /ko/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 그룹 도형이 포함된 Word 문서를 프로그래밍 방식으로 생성하기

Word 문서에 그룹 도형이 포함된 **Word 문서를 프로그래밍 방식으로 생성**해야 하는 경우, 이 가이드는 Aspose.Words for .NET을 사용하여 정확히 수행하는 방법을 보여줍니다. 계약 생성기, 보고서 빌더, 혹은 양식 채우기 도구를 구축하든, 전체 C# 코드, 각 API 호출이 중요한 이유, 그리고 일반적인 엣지 케이스를 처리하는 방법을 배울 수 있습니다.

Word에서 그룹 도형을 만드는 것은 Word 객체 모델이 그룹 도형을 다른 그리기 객체들의 컨테이너로 취급하기 때문에 까다롭게 느껴질 수 있습니다. 이 튜토리얼은 **그룹 도형 Word 문서를 만드는 방법**에 대한 답변을 제공할 뿐만 아니라, 그룹 내부에 일반 텍스트 StructuredDocumentTag (SDT)를 삽입하여 도형이 편집 가능한 내용을 보유하도록 하는 방법도 보여줍니다.

## 달성할 내용

- `Document`와 `DocumentBuilder`를 사용하여 새 빈 Word 문서를 초기화합니다.
- 현재 커서 위치에 `GroupShape`를 삽입합니다.
- 그룹 도형에 일반 텍스트 `StructuredDocumentTag` (SDT)를 추가합니다.
- Microsoft Word에서 열 수 있는 `.docx` 파일로 저장합니다.
- 향후 확장을 위해 `GroupShape`와 `StructuredDocumentTag`의 주요 속성을 이해합니다.

### 사전 요구 사항

- .NET 6.0 이상 (코드는 .NET Framework 4.7+에서도 작동합니다).
- Aspose.Words for .NET NuGet 패키지 (`Install-Package Aspose.Words`).
- Visual Studio 2022 또는 C# 확장이 포함된 VS Code와 같은 C# IDE.

---

## 프로그래밍 방식으로 Word 문서 생성 – 프로젝트 설정

1. **새 콘솔 프로젝트 만들기**  
   ```bash
   dotnet new console -n WordGroupShapeDemo
   cd WordGroupShapeDemo
   dotnet add package Aspose.Words
   ```
2. **IDE에서 프로젝트 열기**하고 `Program.cs`의 내용을 다음 섹션에 표시된 코드로 교체합니다.

> **팁:** 프로젝트 폴더를 깔끔하게 유지하세요; 절대 경로를 제공하지 않으면 Aspose.Words가 출력 파일을 작업 디렉터리에 씁니다.

## 단계 1: 문서와 빌더 초기화

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

// Create a new blank document.
Document doc = new Document();

// DocumentBuilder gives you a cursor to insert nodes.
DocumentBuilder builder = new DocumentBuilder(doc);

// Optional: set the page size or margins if your shape must fit a specific area.
builder.PageSetup.PageWidth = 595;   // A4 width in points
builder.PageSetup.PageHeight = 842;  // A4 height in points
```

**왜 중요한가:**  
`Document`는 전체 Word 파일을 나타내며, `DocumentBuilder`는 노드 트리를 수동으로 탐색하지 않고도 새 요소의 위치를 지정할 수 있게 해줍니다. 페이지 크기를 미리 설정하면 그룹 도형이 페이지를 넘치지 않게 할 수 있습니다.

## 단계 2: 현재 커서 위치에 GroupShape 삽입

```csharp
// Create an empty GroupShape container.
GroupShape groupShape = new GroupShape(doc)
{
    // Give the group a size that comfortably holds its children.
    Width = 300,
    Height = 150,

    // Position the group relative to the page (you can also use RelativeHorizontalPosition).
    Left = 100,
    Top = 100
};

// Insert the group shape into the document where the builder is currently positioned.
builder.InsertNode(groupShape);
```

**설명:**  
`GroupShape`는 다른 도형, 그림 또는 텍스트 상자를 포함할 수 있는 그리기 객체입니다. `Width`, `Height`, `Left`, `Top`을 설정하여 페이지 상에서 정확한 위치를 제어합니다. `InsertNode` 메서드는 도형을 메인 문서 흐름에 배치하며, 플로팅 객체처럼 동작합니다.

## 단계 3: 그룹 내부에 일반 텍스트 StructuredDocumentTag (SDT) 추가

```csharp
// Create a plain‑text SDT that will act as a content placeholder.
StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Provide a helpful tag title that appears as a tooltip in Word.
    Title = "GroupShapeText",
    // Set default placeholder text.
    PlaceholderName = "Enter text here"
};

// Append the SDT to the group shape's child collection.
groupShape.AppendChild(sdtTag);
```

**왜 SDT를 사용할까?**  
StructuredDocumentTag는 Word의 기본 콘텐츠 컨트롤입니다. 사용자가 저장된 문서에서 텍스트를 직접 편집할 수 있게 하며, 이후 프로그래밍 방식으로 데이터 추출에 접근할 수 있습니다. 그룹 도형 내부에 SDT를 배치하면 시각적 그룹화와 편집 가능한 콘텐츠를 결합할 수 있습니다.

## 단계 4: 문서 저장

```csharp
// Define the output path – replace with your desired directory.
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShapeDemo.docx");

// Save the document in DOCX format.
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to: {outputPath}");
```

**결과:**  
Microsoft Word에서 `GroupShapeDemo.docx`를 열면 텍스트 자리표시자 “Enter text here”가 들어 있는 플로팅 사각형(그룹 도형)이 표시됩니다. 사용자는 도형 내부를 클릭해 직접 입력할 수 있습니다.

### 예상 출력 스크린샷 (개념적)

```
+-----------------------------------------------------------+
|   ┌───────────────────────────────────────────────┐   |
|   │  [Enter text here]                               │   |
|   └───────────────────────────────────────────────┘   |
+-----------------------------------------------------------+
```

외부 상자는 `GroupShape`이며, 내부 회색 영역이 `StructuredDocumentTag`입니다.

---

## 그룹 도형 Word 문서 생성 – 추가 고려 사항

### 추가 자식 도형 추가

그룹에 그림이나 텍스트 상자와 같은 추가 그리기 객체를 추가하여 풍부하게 만들 수 있습니다:

```csharp
// Example: add a picture inside the same group.
Shape picture = new Shape(doc, ShapeType.Image)
{
    ImageData = ImageData.FromFile("logo.png"),
    Width = 100,
    Height = 50,
    Left = 10,
    Top = 80
};
groupShape.AppendChild(picture);
```

### 래핑 스타일 제어

그룹 도형을 텍스트 뒤에 두거나 타이트 래핑이 필요하면 `WrapType` 속성을 설정합니다:

```csharp
groupShape.WrapType = WrapType.Inline; // Makes the shape behave like a paragraph.
```

### 엣지 케이스: 빈 그룹 도형

`GroupShape`에 자식이 없으면 보이지 않는 자리표시자로 렌더링됩니다. 최소 하나의 자식(예: SDT 또는 그림)이 추가되었는지 항상 확인하세요; 그렇지 않으면 저장 시 Word가 그룹을 삭제할 수 있습니다.

### 호환성 참고

Aspose.Words 23.10+은 `GroupShape`와 `StructuredDocumentTag`를 완전히 지원합니다. 이전 버전을 대상으로 하는 경우 `AppendChild` 메서드가 다르게 동작할 수 있으며, 저장 후 `UpdatePageLayout`을 호출해야 할 수도 있습니다.

## 완전 실행 예제

`Program.cs`에 아래 전체 코드를 복사하고 프로젝트를 실행하세요. 코드는 위의 모든 단계를 하나의 독립 실행형 프로그램에 포함합니다.



## 다음에 배워야 할 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 단계별 설명과 함께 완전한 작동 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 자체 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Aspose.Words for .NET을 사용하여 Word 문서에 그룹 도형 만들기](/words/english/net/working-with-shapes/add-group-shape/)
- [C#을 사용해 Word에서 사각형 도형 만들기 – 단계별 가이드](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words로 빈 Word 문서 만들기 – 단계별 가이드](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}