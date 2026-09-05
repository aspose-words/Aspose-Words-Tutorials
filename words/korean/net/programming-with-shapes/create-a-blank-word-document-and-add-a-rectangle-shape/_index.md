---
category: general
date: 2026-09-05
description: Aspose.Words를 사용하여 C#에서 빈 워드 문서를 만들고 숨길 수 있는 사각형 모양을 추가하는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- add rectangle shape
- how to hide shape
- hide shape word
- create hidden shape
language: ko
lastmod: 2026-09-05
og_description: Aspose.Words를 사용한 빈 워드 문서 생성 및 숨겨진 사각형 도형 삽입 – C# 개발자를 위한 단계별 가이드.
og_image_alt: Screenshot of a blank Word document with a hidden rectangle shape created
  by Aspose.Words in C#
og_title: 숨겨진 사각형 모양이 있는 빈 워드 문서 만들기
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  headline: Create a blank word document and add a rectangle shape
  type: TechArticle
- description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  name: Create a blank word document and add a rectangle shape
  steps:
  - name: Expected result
    text: 'Open `HiddenRectangle.docx` in Word:'
  - name: Can I hide multiple shapes at once?
    text: Yes. Create each shape, set `Hidden = true`, and insert them sequentially.
      The hidden flag works per node, so mixing hidden and visible shapes in the same
      document is supported.
  - name: What if I need the shape to be hidden only in the print view?
    text: 'Word distinguishes between **display** and **print** visibility through
      the `DisplayWhen` property. Aspose.Words does not expose a direct API for that
      flag, but you can modify the underlying XML:'
  - name: Does the hidden shape affect file size?
    text: A hidden shape adds the same XML payload as a visible one, so the file size
      increase is identical. However, because the shape
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: 빈 워드 문서를 만들고 사각형 도형을 추가하기
url: /ko/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 빈 Word 문서를 만들고 사각형 도형 추가하기

레이아웃에 표시되지 않도록 도형이 포함된 **blank word document**를 생성해야 할 때, 이 가이드는 Aspose.Words for .NET을 사용하여 정확히 수행하는 방법을 보여줍니다. 새 문서를 만들고, 사각형 도형을 추가하고, 해당 도형을 숨긴 뒤 파일을 저장하는 완전한 실행 예제를 확인할 수 있습니다—추가 도구는 필요 없습니다.

이 튜토리얼은 프로젝트 설정부터 일반적인 함정 해결까지 모든 과정을 다룹니다. 최종적으로 독자에게는 비어 보이지만 숨겨진 메타데이터를 포함하는 Word 파일을 생성할 수 있게 되며, 이는 워터마크, 사용자 정의 XML 저장소, 레이아웃 앵커 등 다양한 용도에 유용합니다.

## Prerequisites

시작하기 전에 다음이 준비되어 있는지 확인하세요:

* .NET 6.0 SDK 이상 (코드는 .NET Framework 4.7+에서도 동작합니다)
* Visual Studio 2022 (또는 C#을 지원하는 IDE)
* 활성 **Aspose.Words** NuGet 라이선스 (무료 체험판으로 테스트 가능)
* C# 및 문서 노드 개념에 대한 기본 지식

다음 CLI 명령으로 라이브러리를 설치할 수 있습니다:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Aspose.Words 버전을 최신 상태로 유지하세요; 이 튜토리얼에서 사용된 API는 버전 23.10 기준으로 안정적입니다.

## How to create a blank word document with Aspose.Words

첫 번째 단계는 `Document` 객체를 인스턴스화하는 것입니다. 새 `Document`는 빈 **blank word document**를 나타냅니다—단락도, 섹션도 없으며 파일 컨테이너만 존재합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, empty Word document
Document document = new Document();
```

> **Why this matters:** 깨끗한 문서에서 시작하면 나중에 추가할 숨겨진 도형이 기존 콘텐츠나 스타일에 방해되지 않음을 보장합니다.

## Add a rectangle shape to the document

다음으로 사각형 도형을 생성합니다. Aspose.Words에서 도형은 문서 트리 어디에든 배치할 수 있는 노드이며, 크기, 채우기, 선 스타일 및 가시성을 설정할 수 있습니다.

```csharp
// Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Define a rectangle shape (the "add rectangle shape" step)
Shape rectangle = new Shape(document, ShapeType.Rectangle)
{
    Width = 150,   // Width in points (1 point = 1/72 inch)
    Height = 80,   // Height in points
    FillColor = System.Drawing.Color.LightGray,
    StrokeColor = System.Drawing.Color.DarkGray,
    StrokeWeight = 0.5
};
```

위 코드는 보이는 사각형을 생성합니다. 이 시점에서 `builder.InsertNode(rectangle)`을 사용해 문서에 삽입할 수 있습니다. 하지만 도형을 숨겨 두고 싶으므로 삽입하기 전에 `Hidden` 속성을 조정합니다.

## How to hide shape in a Word document

Word는 도형 노드에 `Hidden` 속성을 제공합니다. 이를 `true`로 설정하면 도형이 페이지 레이아웃에 표시되지 않지만 문서 XML의 일부로 남아 있습니다. 이것이 **how to hide shape** 요구 사항의 핵심입니다.

```csharp
// Hide the shape so it won't be displayed
rectangle.Hidden = true;
```

> **Explanation:** `Hidden = true`를 설정하면 도형 XML에 `<w:hide>` 속성이 추가됩니다. 워드 프로세서는 렌더링 시 도형을 무시하지만, 프로그래밍 방식이나 Word XML 뷰어를 통해 여전히 접근할 수 있습니다.

## Insert the hidden shape into the blank document

이제 숨겨진 사각형을 문서 트리에 배치합니다. 문서가 아직 비어 있기 때문에 도형은 메인 스토리의 첫 번째 노드가 됩니다.

```csharp
// Insert the hidden rectangle at the current cursor position
builder.InsertNode(rectangle);
```

Microsoft Word에서 결과 파일을 열면 겉보기에는 빈 페이지가 보입니다. 도형은 존재하지만 보이지 않습니다.

## Save the document

마지막으로 문서를 디스크에 저장합니다. 지원되는 형식(`.docx`, `.pdf`, `.odt` 등) 중 원하는 것을 선택할 수 있습니다. 이 튜토리얼에서는 최신 DOCX 형식을 사용합니다.

```csharp
// Save the file – adjust the path as needed
string outputPath = Path.Combine(Environment.CurrentDirectory, "HiddenRectangle.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

### Expected result

Word에서 `HiddenRectangle.docx`를 열면:

* 문서는 빈 것처럼 보입니다(보이는 도형이나 텍스트가 없음).
* **Open XML SDK** 또는 **Word XML Viewer**와 같은 도구로 파일을 검사하면 `hidden` 속성을 가진 `<w:pict>` 요소 안에 사각형이 포함된 것을 확인할 수 있습니다.

![blank word document with hidden rectangle shape](image.png){: .align-center alt="blank word document with hidden rectangle shape"}

## Full, runnable example

아래는 콘솔 애플리케이션에 복사‑붙여넣기 할 수 있는 전체 프로그램입니다. 필요한 `using` 지시문, 오류 처리 및 주석이 모두 포함되어 있습니다.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Prepare a DocumentBuilder to manipulate the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Define a rectangle shape (add rectangle shape)
        Shape rectangle = new Shape(document, ShapeType.Rectangle)
        {
            Width = 150,
            Height = 80,
            FillColor = System.Drawing.Color.LightGray,
            StrokeColor = System.Drawing.Color.DarkGray,
            StrokeWeight = 0.5,
            // 4️⃣ Hide the shape (how to hide shape)
            Hidden = true
        };

        // 5️⃣ Insert the hidden shape into the blank document
        builder.InsertNode(rectangle);

        // 6️⃣ Save the document (create hidden shape)
        string outputPath = Path.Combine(
            Environment.CurrentDirectory, "HiddenRectangle.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

프로그램을 실행(`dotnet run`)하고 출력 파일을 확인하세요. 콘솔에 저장 위치가 표시됩니다.

## Common questions and edge cases

### Can I hide multiple shapes at once?

예. 각 도형을 생성하고 `Hidden = true`로 설정한 뒤 순차적으로 삽입하면 됩니다. 숨김 플래그는 노드별로 적용되므로 같은 문서에 숨긴 도형과 보이는 도형을 혼합해 사용할 수 있습니다.

### What if I need the shape to be hidden only in the print view?

Word는 **display**와 **print** 가시성을 `DisplayWhen` 속성을 통해 구분합니다. Aspose.Words에서는 해당 플래그에 직접적인 API를 제공하지 않지만, 기본 XML을 수정하여 구현할 수 있습니다:

```csharp
rectangle.GetShapeRenderer().GetShapeXml()
    .SetAttribute("w:display", "print");
```

프린트 전용 가시성이 필요할 때만 사용하세요.

### Does the hidden shape affect file size?

숨겨진 도형은 보이는 도형과 동일한 XML 페이로드를 추가하므로 파일 크기 증가량도 동일합니다. 다만 도형 자체가


## What Should You Learn Next?

다음 튜토리얼들은 이 가이드에서 시연한 기술을 기반으로 한 밀접한 주제를 다룹니다. 각 리소스는 단계별 설명과 완전한 코드 예제를 포함하여 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용할 수 있도록 돕습니다.

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}