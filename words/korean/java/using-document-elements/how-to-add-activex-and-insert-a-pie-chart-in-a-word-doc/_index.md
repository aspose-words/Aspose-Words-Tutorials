---
category: general
date: 2026-08-17
description: Aspose.Words를 사용하여 Word 문서에 ActiveX 컨트롤을 추가하고 파이 차트를 삽입하는 방법. 슬라이스를 분리하고
  몇 단계만에 DOCX로 저장합니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert pie chart
- save as docx
- how to insert chart
- explode pie slice
language: ko
lastmod: 2026-08-17
og_description: ActiveX 컨트롤 추가, 원형 차트 삽입, 슬라이스 분리, Aspose.Words로 DOCX 저장 방법 – 완전한
  단계별 가이드.
og_image_alt: Screenshot of a Word document showing an ActiveX button and a pie chart
  with an exploded slice
og_title: Word 문서에 ActiveX를 추가하고 원형 차트를 삽입하는 방법
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to add ActiveX controls and insert a pie chart in a Word doc using
    Aspose.Words. Explode a slice and save as DOCX in a few steps.
  headline: How to add ActiveX and insert a pie chart in a Word doc
  type: TechArticle
tags:
- Aspose.Words
- ActiveX
- Chart
- DOCX
title: Word 문서에 ActiveX를 추가하고 파이 차트를 삽입하는 방법
url: /ko/java/using-document-elements/how-to-add-activex-and-insert-a-pie-chart-in-a-word-doc/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 문서에 ActiveX를 추가하고 파이 차트를 삽입하는 방법

Word 문서에 **ActiveX 추가 방법**과 차트를 삽입하는 방법이 필요하다면, 이 튜토리얼에서 완전하고 실행 가능한 솔루션을 보여줍니다. Aspose.Words를 사용하면 ActiveX CommandButton을 배치하고, 파이 차트를 만든 뒤, 강조를 위해 슬라이스를 분리하고, 마지막으로 **DOCX로 저장**을 몇 줄의 C# 코드만으로 수행할 수 있습니다.

아래 섹션에서는 필요한 모든 import, 전체 코드 목록, 각 단계가 왜 중요한지에 대한 설명을 확인할 수 있습니다. 끝까지 읽으면 프로그래밍 방식으로 생성하는 모든 .docx 파일에 인터랙티브 컨트롤과 시각적 데이터를 통합할 수 있게 됩니다.

## Prerequisites

시작하기 전에 다음이 준비되어 있는지 확인하세요:

* .NET 6.0 이상 (코드는 .NET Framework 4.7+에서도 동작합니다)
* Aspose.Words for .NET 패키지 (NuGet을 통해 제공)
* Visual Studio 2022 또는 VS Code와 같은 개발 환경
* C# 및 Word 객체 모델에 대한 기본 지식

추가 서드파티 차트 라이브러리는 필요하지 않습니다—Aspose.Words가 내장 차트 생성을 지원합니다.

## How to add ActiveX controls with Aspose.Words

ActiveX 컨트롤을 사용하면 Word 파일에 직접 인터랙티브 UI 요소를 삽입할 수 있습니다. 이 가이드에서는 나중에 VBA 코드와 연결할 수 있는 **CommandButton**을 추가합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a group shape to hold the ActiveX control
GroupShape groupShape = builder.InsertGroupShape();

// Step 3: Insert a rectangle shape, hide it, and attach it to the group
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
groupShape.AppendChild(rectangleShape);
rectangleShape.SetHidden(true);

// Step 4: Insert a plain‑text StructuredDocumentTag (optional placeholder)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");

// Step 5: Insert the CommandButton ActiveX control
Forms2OleControl commandButton = builder.InsertForms2OleControl();
commandButton.SetActiveXControlType(Forms2OleControlType.CommandButton);
commandButton.SetCaption("Click Me");

// The CommandButton now appears in the document and can be used in VBA macros.
```

**왜 이렇게 동작하나요:**  
`InsertForms2OleControl`은 Word UI가 ActiveX 컨트롤로 인식하는 OLE 컨테이너를 생성합니다. 컨트롤 유형을 `CommandButton`으로 설정하고 캡션을 지정하면 사용자가 Word에서 파일을 열 때 표준 버튼처럼 동작합니다.

## Insert pie chart and explode a slice

차트는 문서를 떠나지 않고도 데이터를 시각화하는 데 유용합니다. 다음 단계에서는 **차트 삽입 방법**을 보여주며, 특히 첫 번째 슬라이스가 분리된 **파이 차트**를 만들습니다.

```csharp
// Step 6: Insert a pie chart (400 × 300 points)
Chart pieChart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);

// Populate the chart with sample data
pieChart.Series.Clear();
ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                          new[] { 12000, 15000, 9000, 13000 });

// Step 7: Explode the first slice for emphasis
series.SetExplode(0, true);

// Optional: Customize colors or labels here if needed
```

**슬라이스를 분리하는 이유:**  
`SetExplode(0, true)`를 호출하면 Aspose.Words가 첫 번째 데이터 포인트를 오프셋하여 시청자의 시선을 해당 구간으로 끌어옵니다. 이는 프레젠테이션에서 핵심 값을 강조하는 일반적인 기법입니다.

## Save as DOCX

ActiveX 버튼과 차트를 추가한 후, 문서를 디스크에 저장합니다. 이 단계에서는 표준 메서드를 사용한 **DOCX로 저장**을 보여줍니다.

```csharp
// Step 8: Save the document in DOCX format
document.Save("Output.docx", SaveFormat.Docx);
```

파일 `Output.docx`에는 이제 인터랙티브 버튼, 분리된 슬라이스가 있는 파이 차트가 포함되며, 추가 플러그인 없이 Microsoft Word에서 열 수 있습니다.

## Full runnable example

모든 내용을 하나로 모아, 콘솔 애플리케이션에 복사해 바로 실행할 수 있는 독립형 프로그램을 제공합니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert group shape and hidden rectangle (required for ActiveX positioning)
        GroupShape group = builder.InsertGroupShape();
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        group.AppendChild(rect);
        rect.SetHidden(true);

        // Optional placeholder tag
        builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");

        // Insert CommandButton ActiveX control
        Forms2OleControl button = builder.InsertForms2OleControl();
        button.SetActiveXControlType(Forms2OleControlType.CommandButton);
        button.SetCaption("Click Me");

        // Insert pie chart and explode first slice
        Chart chart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);
        chart.Series.Clear();
        ChartSeries series = chart.Series.Add("Revenue", new[] { "Jan", "Feb", "Mar" },
                                               new[] { 5000, 7000, 3000 });
        series.SetExplode(0, true); // explode pie slice

        // Save the document
        doc.Save("Output.docx", SaveFormat.Docx);

        Console.WriteLine("Document created successfully: Output.docx");
    }
}
```

**예상 결과:**  
Word에서 `Output.docx`를 열면 *Click Me* 라는 레이블이 붙은 버튼과 첫 번째 슬라이스(1월)가 나머지와 떨어진 파이 차트가 표시됩니다. 버튼은 VBA 이벤트 처리에 사용할 수 있으며, 차트는 Word 내장 차트 도구로 편집할 수 있습니다.

## Common questions and edge cases

* **다른 ActiveX 유형을 추가할 수 있나요?**  
  네. `Forms2OleControlType.CommandButton`을 `Forms2OleControlType` 열거형의 다른 값(예: `CheckBox`, `OptionButton`)으로 교체하면 됩니다. 삽입 패턴은 동일합니다.

* **다른 차트 유형이 필요하면 어떻게 하나요?**  
  `InsertChart` 호출에서 `ChartType.Bar`, `ChartType.Line` 등으로 교체하면 됩니다. **차트 삽입 방법** 단계는 동일하게 유지되며, 열거형 값만 바뀝니다.

* **분리된 슬라이스의 크기를 제어하려면?**  
  현재 Aspose.Words는 이진 explode 플래그(true/false)만 지원합니다. 보다 정밀한 제어(예: 오프셋 거리)가 필요하면 저장 후 기본 OOXML을 직접 편집해야 합니다.

* **문서가 오래된 Word 버전과 호환되나요?**  
  DOCX로 저장하면 Word 2007 이후 버전과 호환됩니다. Word 2003용으로는 `SaveFormat.Doc`으로 변경할 수 있지만, 해당 형식에서는 ActiveX 지원이 제한됩니다.

* **`System.Drawing`을 참조해야 하나요?**  
  필요 없습니다. 모든 그리기 객체는 Aspose.Words가 제공하므로 필요한 NuGet 패키지는 `Aspose.Words` 하나뿐입니다.

## Conclusion

이제 **ActiveX 추가 방법**, **파이 차트 삽입**, **파이 슬라이스 분리**, **DOCX로 저장**을 Aspose.Words for .NET을 사용해 구현하는 방법을 알게 되었습니다. 전체 예제는 문서 생성부터 최종 저장까지 모든 단계를 다루며, 각 API 호출 뒤에 숨은 이유를 설명합니다.

다음에 탐색해 볼 내용:

* CommandButton 클릭에 반응하는 VBA 매크로 추가 (**차트 삽입 방법** 및 데이터 자동 업데이트)
* 차트 외관 맞춤(색상, 데이터 레이블)으로 기업 브랜드와 일치시키기
* **ComboBox** 또는 **ListBox**와 같은 추가 ActiveX 컨트롤을 삽입해 보다 풍부한 양식 만들기

코드를 자유롭게 실험하고, 샘플 데이터를 교체하며, 자체 문서 생성 파이프라인에 통합해 보세요. 즐거운 코딩 되세요!

## What Should You Learn Next?

다음 튜토리얼에서는 이 가이드에서 다룬 기술을 기반으로 한 관련 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 제공하여 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용할 수 있도록 돕습니다.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}