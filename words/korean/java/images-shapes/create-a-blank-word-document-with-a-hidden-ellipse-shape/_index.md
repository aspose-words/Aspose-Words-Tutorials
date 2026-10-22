---
category: general
date: 2026-09-18
description: Aspose.Words를 사용하여 빈 Word 문서를 만들고 타원 모양을 숨깁니다. Word에서 모양을 숨기는 방법, 타원을
  삽입하는 방법, 그리고 숨겨진 모양을 빠르게 만드는 방법을 배우세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to hide shape
- how to insert ellipse
- hide shape in word
- create hidden shape
language: ko
lastmod: 2026-09-18
og_description: 빈 Word 문서를 만들고 Word에서 타원 모양을 숨깁니다. 이 가이드는 타원을 삽입하고, Word에서 모양을 숨기며,
  Aspose.Words를 사용하여 숨겨진 모양을 만드는 방법을 단계별로 보여줍니다.
og_image_alt: Screenshot of a blank Word document containing a hidden ellipse shape
  created with Aspose.Words
og_title: 숨겨진 타원 모양이 있는 빈 워드 문서 만들기
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  headline: Create a blank Word document with a hidden ellipse shape
  type: TechArticle
- description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  name: Create a blank Word document with a hidden ellipse shape
  steps:
  - name: Pro tip
    text: If you later need to make the shape visible again, simply set `ellipse.Hidden
      = false;` and save the document.
  - name: What if the shape still appears?
    text: '* Ensure you are using Aspose.Words 23.9 or later – older versions had
      a bug where `Hidden` was ignored for some shape types. * Verify that you are
      not applying any additional formatting (e.g., `WrapType`) that forces the shape
      to occupy layout space.'
  - name: Can I hide other shape types?
    text: Yes. The same `Hidden` property works for `ShapeType.Rectangle`, `ShapeType.Picture`,
      etc. Just replace `ShapeType.Ellipse` with the desired type.
  - name: How to list hidden shapes later?
    text: '```csharp foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
      { if (shape.Hidden) Console.WriteLine($"Hidden shape: {shape.ShapeType}"); }
      ```'
  - name: Next steps
    text: '* Explore **how to hide shape** conditionally based on document content.
      * Learn **how to unhide shape** when generating a final version of the document.
      * Combine hidden shapes with **custom document properties** to embed machine‑readable
      data.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 숨겨진 타원 도형이 있는 빈 Word 문서 만들기
url: /ko/java/images-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 숨겨진 타원 모양이 있는 빈 Word 문서 만들기

레이아웃에 표시되지 않기를 원하는 모양이 포함된 **빈 Word 문서**를 만들어야 하는 경우, 이 가이드에서는 정확한 방법을 보여줍니다. Aspose.Words for .NET을 사용하면 프로그래밍 방식으로 타원을 삽입한 다음 모양을 숨겨 문서는 시각적으로 비어 있지만 모양 데이터는 유지됩니다.

이 튜토리얼에서 배우게 됩니다:

* **빈 Word 문서 만들기** 객체를 만드는 방법,
* `DocumentBuilder`를 사용하여 **타원 삽입** 하는 방법,
* Word에서 **모양 숨기기** 로 페이지에 영향을 주지 않는 방법,
* 나중에 처리하기 위한 **숨겨진 모양 만들기** 객체를 만드는 방법.

이 단계는 .NET 6+ 및 최신 Aspose.Words 버전(작성 시점 23.9)에서 작동합니다. 추가 Office 설치가 필요하지 않습니다.

## 사전 요구 사항

* Visual Studio 2022 (또는 모든 C# IDE)
* .NET 6 SDK 또는 그 이후 버전
* Aspose.Words for .NET NuGet package  
  ```bash
  dotnet add package Aspose.Words
  ```
* C# 및 Word 문서 개념에 대한 기본 지식

## 단계 1: 빈 Word 문서 만들기

먼저 해야 할 일은 `Document` 객체를 인스턴스화하는 것입니다. 이 객체는 빈 `.docx` 파일을 나타내며 이후 모든 작업의 기반이 됩니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document doc = new Document();   // <-- creates a blank Word document in memory
```

**빈 Word 문서**를 만들면 깨끗한 캔버스를 얻을 수 있습니다 – 단락도 없고, 섹션도 없으며, 기본 패키지 구조만 존재합니다. 숨겨진 모양만 필요하고 다른 것이 전혀 없을 때 이상적인 시작점입니다.

## 단계 2: DocumentBuilder 초기화

`DocumentBuilder`는 `Document`에 콘텐츠를 추가하기 위한 편리한 API를 제공합니다. 문서 안을 이동하는 커서와 같은 역할을 합니다.

```csharp
// Step 2: Initialise a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

빌더는 자동으로 기본 첫 번째 섹션과 단락을 생성하므로 섹션을 수동으로 추가하지 않고도 바로 모양을 삽입할 수 있습니다.

## 단계 3: 타원 모양 삽입

이제 `InsertShape` 메서드를 사용하여 **타원 삽입**을 합니다. 이 메서드는 `ShapeType` 열거형, 너비 및 높이(포인트 단위)를 매개변수로 받습니다.

```csharp
// Step 3: Insert an ellipse shape with a width of 100 points and a height of 50 points
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
```

왜 타원일까요? 타원은 주변 텍스트 흐름에 영향을 주지 않고 숨길 수 있는 벡터 모양입니다. 너비 100 pt와 높이 50 pt는 임의값이며, 이후 처리 요구에 맞게 조정할 수 있습니다.

## 단계 4: 레이아웃에 표시되지 않도록 모양 숨기기

Word에서 **모양 숨기기**를 하려면 `Shape` 객체의 `Hidden` 속성을 `true`로 설정합니다. 문서를 Microsoft Word에서 열면 모양이 보이지 않으며 레이아웃에서 공간을 차지하지 않습니다.

```csharp
// Step 4: Hide the shape so it does not appear in the layout
ellipse.Hidden = true;   // <-- this hides the shape in Word
```

`Hidden` 플래그는 모양의 XML(` <w:hidden/>`)에 저장됩니다. Word는 렌더링 시 이 속성을 존중하므로 모양이 존재함에도 문서는 완전히 빈 것처럼 보입니다.

### 팁

나중에 모양을 다시 보이게 해야 한다면, `ellipse.Hidden = false;` 로 설정하고 문서를 저장하면 됩니다.

## 단계 5: 숨겨진 모양이 포함된 문서 저장

마지막으로 문서를 디스크에 저장합니다. 파일은 일반 `.docx` 형식이며 모든 워드 프로세서에서 열 수 있습니다.

```csharp
// Step 5: Save the document with the hidden shape
doc.Save(@"C:\Temp\HiddenEllipse.docx");
```

저장된 파일 `HiddenEllipse.docx`는 숨겨진 타원을 포함한 **빈 Word 문서 만들기** 예시입니다. Microsoft Word에서 열면 빈 페이지가 표시되지만, 모양은 Open XML 구조에 여전히 존재합니다.

## 전체 작업 예제

아래는 복사·붙여넣기 후 실행할 수 있는 완전한 독립형 프로그램입니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();

            // 2️⃣ Initialise DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse shape (width: 100pt, height: 50pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the shape so it does not affect layout
            ellipse.Hidden = true;

            // 5️⃣ Save the result
            string outputPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**예상 출력**

* `HiddenEllipse.docx`라는 파일이 `C:\Temp`에 생성됩니다.
* 파일을 Microsoft Word에서 열면 완전히 빈 페이지가 표시됩니다.
* Open XML SDK 또는 zip 뷰어로 문서를 검사하면 문서 파트 안에 `<w:shape>` 요소와 `<w:hidden/>`가 포함되어 있음을 확인할 수 있습니다.

## 일반적인 질문 및 엣지 케이스

### 모양이 여전히 표시되면 어떻게 하나요?

* Aspose.Words 23.9 이상을 사용하고 있는지 확인하십시오 – 이전 버전에서는 일부 모양 유형에 대해 `Hidden`이 무시되는 버그가 있었습니다.
* 모양이 레이아웃 공간을 차지하도록 하는 추가 서식(예: `WrapType`)을 적용하지 않았는지 확인하십시오.

### 다른 모양 유형도 숨길 수 있나요?

예. 동일한 `Hidden` 속성이 `ShapeType.Rectangle`, `ShapeType.Picture` 등에도 적용됩니다. 원하는 유형으로 `ShapeType.Ellipse`를 교체하면 됩니다.

### 나중에 숨겨진 모양을 나열하려면?

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.Hidden)
        Console.WriteLine($"Hidden shape: {shape.ShapeType}");
}
```

이 스니펫은 모든 모양을 순회하면서 숨겨진 모양을 출력합니다. 이는 나중에 처리하거나 다시 보이게 해야 하는 **숨겨진 모양 만들기** 워크플로에 유용합니다.

## 결론

이제 **빈 Word 문서 만들기**, **타원 삽입**, 그리고 **Word에서 모양 숨기기**를 통해 독자에게 보이지 않는 **숨겨진 모양 만들기**를 구현하는 방법을 알게 되었습니다. 이 기술은 문서의 시각적 모습을 바꾸지 않고 메타데이터, 북마크 또는 사용자 정의 XML을 저장하는 데 유용합니다.

### 다음 단계

* 문서 내용에 따라 **모양 숨기기**를 조건부로 탐색해 보세요.
* 최종 문서를 생성할 때 **모양 보이기** 방법을 배우세요.
* 숨겨진 모양을 **사용자 정의 문서 속성**과 결합하여 기계가 읽을 수 있는 데이터를 삽입하세요.

다양한 모양 유형, 크기 및 숨김 상태 로직을 실험하여 자동화 시나리오에 맞게 적용해 보세요. 즐거운 코딩 되세요!

## 다음에 배워야 할 내용은?

다음 튜토리얼들은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료는 단계별 설명과 함께 완전한 코드 예제를 제공하여 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색할 수 있도록 돕습니다.

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}