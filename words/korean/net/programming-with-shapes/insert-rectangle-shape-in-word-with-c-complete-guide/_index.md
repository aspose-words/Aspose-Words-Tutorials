---
category: general
date: 2026-08-10
description: C#를 사용하여 Word에 사각형 도형을 삽입합니다. 도형 숨기기, Word에서 도형 숨기기, 그리고 Aspose.Words로
  숨겨진 도형을 만드는 방법을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- hide shape in word
- create hidden shape
language: ko
lastmod: 2026-08-10
og_description: C#를 사용하여 Word에 사각형 도형 삽입하기. 이 튜토리얼에서는 도형 숨기기, Word에서 도형 숨기기, 전체 코드
  예제를 포함한 숨겨진 도형 만들기에 대해 설명합니다.
og_image_alt: Screenshot showing a hidden rectangle shape inserted into a Word document
  using C#
og_title: C#로 Word에 사각형 모양 삽입 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  headline: Insert rectangle shape in Word with C# – complete guide
  type: TechArticle
- description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  name: Insert rectangle shape in Word with C# – complete guide
  steps:
  - name: Can I hide only the outline but keep the fill visible?
    text: Yes. Instead of setting `Hidden = true`, you can set `rectangle.LineFormat.Visible
      = false` to hide the border while keeping the fill color. This is a variation
      of **how to hide shape** that preserves part of the visual appearance.
  - name: Does the hidden flag work in older Word versions (2003, 2007)?
    text: The hidden attribute is part of the Open XML specification introduced with
      Word 2007. Documents saved in the older binary `.doc` format will not preserve
      the flag. To support legacy formats, save the document as `.docx` and, if needed,
      convert it later using Aspose.Words’ `SaveFormat.Doc`.
  - name: What if I need to hide multiple shapes at once?
    text: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` on each shape that meets your criteria (e.g., a specific
      `ShapeType` or a custom `AlternativeText` value).
  - name: Is there a performance impact when hiding shapes?
    text: The hidden flag adds a tiny XML attribute; it does not affect rendering
      speed. However, a very large number of hidden objects can increase file size
      marginally. Remove shapes you never need to keep the document lean.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: C#로 Word에 사각형 도형 삽입하기 – 완전 가이드
url: /ko/net/programming-with-shapes/insert-rectangle-shape-in-word-with-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#를 사용하여 Word에 사각형 도형 삽입 – 완전 가이드

C#를 사용하여 Word 문서에 **사각형 도형을 삽입**해야 하는 경우, 이 가이드는 정확한 단계들을 보여줍니다. 또한 **도형 숨기기** 방법을 배워 최종 파일에 표시되지 않도록 할 수 있으며, 이는 일반적인 질문인 **Word에서 도형 숨기기**에 대한 답변이자 **숨겨진 도형 만들기**를 프로그래밍 방식으로 시연합니다.

이 튜토리얼은 Aspose.Words SDK 설정부터 도형이 숨겨졌는지 확인하는 과정까지 모두 다룹니다. 기사 끝까지 읽으면 어떤 .NET 프로젝트에도 바로 넣어 사용할 수 있는 재사용 가능한 코드 스니펫을 얻게 됩니다.

## Prerequisites

시작하기 전에 다음이 준비되어 있는지 확인하세요:

- .NET 6.0 이상이 설치되어 있음 (코드는 .NET Framework 4.6+에서도 작동합니다)
- 유효한 Aspose.Words for .NET 라이선스 또는 임시 평가 키
- Visual Studio 2022 (또는 C#을 지원하는 IDE)
- C# 구문 및 Word 파일의 Document Object Model(DOM)에 대한 기본적인 이해

`Aspose.Words` 외에 추가 NuGet 패키지는 필요하지 않습니다.

## Step 1: Create a new blank document and a DocumentBuilder

첫 번째 작업은 `Document` 객체를 인스턴스화하는 것입니다. `DocumentBuilder`는 도형, 단락, 표와 같은 콘텐츠를 삽입하기 위한 편리한 API를 제공합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document document = new Document();

// DocumentBuilder lets you add elements to the document.
DocumentBuilder builder = new DocumentBuilder(document);
```

**Why this matters:** `Document`는 전체 .docx 파일을 나타내고, `DocumentBuilder`는 다음 요소가 배치될 위치를 추적하는 커서를 유지합니다. 두 객체를 초기화하는 것이 모든 Word 자동화 작업의 기반이 됩니다.

## Step 2: Insert rectangle shape

이제 사각형을 삽입합니다. `InsertShape` 메서드는 도형 유형과 크기를 포인트 단위(1 point ≈ 1/72 inch)로 지정해야 합니다. **200 × 100 points** 크기는 대략 2.78 × 1.39 인치에 해당하는 사각형을 만듭니다.

```csharp
// Insert a rectangle of 200x100 points.
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**Why this matters:** 반환된 `Shape` 객체는 색상, 테두리, 텍스트 및 가시성 등 모든 속성을 문서를 저장하기 전에 자유롭게 구성할 수 있습니다.

## Step 3: Hide the shape

사각형이 화면에 표시되거나 인쇄되지 않도록 하려면 `Hidden` 속성을 `true` 로 설정합니다. 이 속성은 Word의 “Hidden” 속성과 직접 매핑되며, Word는 보기와 인쇄 모드 모두에서 이를 존중합니다.

```csharp
// Hide the shape so it never appears.
rectangle.Hidden = true;
```

**Why this matters:** `Hidden` 설정은 **Word에서 도형 숨기기**를 구현하는 표준 방법이며, 도형을 문서 구조에서 제거하지 않고도 숨길 수 있습니다. 이렇게 하면 코드에서 여전히 도형에 접근할 수 있어 조건부 서식이나 데이터 기반 가시성 전환과 같은 후속 작업이 가능합니다.

## Step 4: Save the document

마지막으로 문서를 디스크에 저장합니다. 원하는 폴더를 선택하면 되며, 예제에서는 실제 경로로 교체해야 하는 자리표시자 경로를 사용합니다.

```csharp
// Save the document with the hidden rectangle.
document.Save(@"C:\Temp\HiddenShape.docx");
```

**Why this matters:** 저장 과정에서 파일이 최종화되고 숨김 플래그가 기본 Open XML에 기록됩니다. Microsoft Word에서 문서를 열면 사각형이 보이지 않아 **숨겨진 도형 만들기**에 성공했음을 확인할 수 있습니다.

## Step 5: Verify the hidden shape

생성된 `HiddenShape.docx` 파일을 Microsoft Word에서 엽니다:

1. **File → Options → Display** 로 이동하여 *“Show hidden text”* 옵션이 **체크 해제**되어 있는지 확인합니다.  
2. 어떤 페이지에서도 사각형이 보이지 않아야 합니다.  
3. 다시 확인하려면 *“Show hidden text”* 를 활성화하면, 사각형이 옅은 점선 윤곽선으로 나타나 도형이 존재하지만 숨겨져 있음을 증명합니다.

사각형이 여전히 보인다면 `Hidden = true` 로 설정한 후 파일을 저장했는지, 그리고 올바른 파일을 열었는지 다시 확인하세요.

## Full runnable example

아래는 바로 복사·붙여넣기·실행할 수 있는 전체 프로그램 예시입니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape of 200x100 points.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Step 3: Hide the shape so it does not appear when viewed or printed.
        rectangle.Hidden = true;

        // Step 4: Save the document with the hidden shape.
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
        Console.WriteLine("Open the file in Word to verify that the rectangle is hidden.");
    }
}
```

**Expected output:** 콘솔에 파일 경로와 간단한 알림이 출력됩니다. Word에서 파일을 열면 숨김 텍스트가 활성화되지 않은 한 사각형이 보이지 않습니다.

## Common questions and edge cases

### Can I hide only the outline but keep the fill visible?

예. `Hidden = true` 대신 `rectangle.LineFormat.Visible = false` 로 설정하면 테두리만 숨기고 채우기 색상은 유지할 수 있습니다. 이는 **도형 숨기기**의 변형으로 시각적 요소의 일부만 보이게 합니다.

### Does the hidden flag work in older Word versions (2003, 2007)?

숨김 속성은 Word 2007에 도입된 Open XML 사양의 일부입니다. 오래된 바이너리 `.doc` 형식에서는 플래그가 보존되지 않습니다. 레거시 형식을 지원하려면 문서를 `.docx` 로 저장하고 필요 시 Aspose.Words의 `SaveFormat.Doc` 를 사용해 변환하세요.

### What if I need to hide multiple shapes at once?

`Document.GetChildNodes(NodeType.Shape, true)` 컬렉션을 순회하면서 조건에 맞는 각 도형에 `Hidden = true` 를 설정하면 됩니다(예: 특정 `ShapeType` 이나 사용자 정의 `AlternativeText` 값).

```csharp
foreach (Shape shp in document.GetChildNodes(NodeType.Shape, true))
{
    if (shp.AlternativeText == "HideMe")
        shp.Hidden = true;
}
```

### Is there a performance impact when hiding shapes?

숨김 플래그는 아주 작은 XML 속성을 추가할 뿐이며 렌더링 속도에 영향을 주지 않습니다. 다만 매우 많은 수의 숨김 객체가 있을 경우 파일 크기가 약간 증가할 수 있습니다. 불필요한 도형은 제거해 문서를 가볍게 유지하세요.

## Tips and best practices

- **Give the shape a meaningful name** using `rectangle.Name = "MyHiddenRectangle"`; this helps when you later search for the shape in the DOM.  
- **Set `AlternativeText`** to a custom tag (e.g., `"HiddenShape"`). This allows you to locate the shape without relying on its index.  
- **Wrap the code in a try‑catch block** to handle licensing errors or I/O exceptions gracefully.  
- **Dispose of the Document** after saving if you are processing many files in a loop to free unmanaged resources: `document.Dispose();`.

## Conclusion

이제 C#로 Word 문서에 **사각형 도형을 삽입**하고, **Word에서 도형 숨기기** 및 **숨겨진 도형 만들기** 방법을 알게 되었습니다. 완전한 실행 예제는 문서 생성부터 검증까지 전체 흐름을 보여줍니다.

다음 단계로는 사용자 입력에 따라 **도형 숨기기**를 구현하거나, 숨겨진 도형을 콘텐츠 컨트롤과 결합해 동적 문서 생성을 시도해 볼 수 있습니다. 또한 타원, 화살표, 사용자 정의 그림 등 다른 도형 유형에도 동일한 기법을 적용할 수 있습니다.

다양한 크기, 색상 및 가시성 설정을 실험해 보세요. 문제가 발생하면 위 단계를 다시 검토하거나 Aspose.Words 문서를 참고해 API 세부 정보를 확인하십시오. 즐거운 코딩 되세요!

## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 배운 기술을 기반으로 하며, 단계별 코드 예제와 자세한 설명을 포함하고 있어 추가 API 기능을 마스터하고 다양한 구현 방식을 탐색하는 데 도움이 됩니다.

- [C#를 사용하여 Word에 사각형 도형 만들기 – 단계별 가이드](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words를 사용하여 Word에 사각형 도형 만들기 – 단계별 가이드](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words 도형 그림자 튜토리얼 – C#에서 Word 도형에 그림자 추가](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}