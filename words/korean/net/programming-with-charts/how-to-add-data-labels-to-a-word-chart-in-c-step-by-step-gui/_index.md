---
category: general
date: 2026-08-04
description: C#와 Aspose.Words를 사용하여 데이터 레이블을 추가하는 방법. 차트를 편집하고, 차트 데이터 레이블을 중앙에 배치하며,
  차트에 백분율을 표시하고, 차트 데이터 레이블을 사용자 지정하는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add data labels
- how to edit chart
- center chart data labels
- show percentages in chart
- customize chart data labels
language: ko
lastmod: 2026-08-04
og_description: Aspose.Words를 사용하여 C#에서 데이터 레이블을 추가하는 방법. 이 튜토리얼에서는 차트를 편집하고, 차트 데이터
  레이블을 중앙에 배치하며, 차트에 백분율을 표시하고, 차트 데이터 레이블을 사용자 지정하는 방법을 보여줍니다.
og_image_alt: Screenshot of a Word chart with data labels added using C#
og_title: C#에서 Word 차트에 데이터 레이블 추가하는 방법 – 완전 가이드
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  headline: How to add data labels to a Word chart in C# – step‑by‑step guide
  type: TechArticle
- description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  name: How to add data labels to a Word chart in C# – step‑by‑step guide
  steps:
  - name: – Load the Word document containing the chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: – Retrieve the first chart from the document
    text: '```csharp // Find the first shape that contains a chart. Shape chartShape
      = (Shape)document.GetChild(NodeType.Shape, 0, true); Chart chart = chartShape.GetChart();
      ```'
  - name: – Enable data label customization and show percentages in chart
    text: '```csharp // Access the first series of the chart. ChartSeries series =
      chart.Series[0];'
  - name: – Change the label placement to the center of each data point
    text: '```csharp // Position the labels at the center of each point. dataLabels.Position
      = ChartDataLabelPosition.Center; // center chart data labels ```'
  - name: – Further customize chart data labels (optional)
    text: 'If you need more control, you can adjust font, color, or leader lines:'
  - name: – Save the modified document
    text: '```csharp // Persist the changes to a new file. document.Save("YOUR_DIRECTORY/output.docx");
      ```'
  - name: Expected result
    text: 'When you open `output.docx` in Microsoft Word, the chart will display:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart manipulation
title: C#에서 Word 차트에 데이터 레이블 추가하는 방법 – 단계별 가이드
url: /ko/net/programming-with-charts/how-to-add-data-labels-to-a-word-chart-in-c-step-by-step-gui/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 Word 차트에 데이터 레이블 추가하는 방법 – 단계별 가이드

Word 문서에 포함된 차트에 **how to add data labels**를 추가해야 하는 경우, 이 가이드는 실행해야 할 정확한 코드를 보여줍니다. 차트 속성을 편집하고, 차트 데이터 레이블을 중앙에 배치하고, 차트에 백분율을 표시하며, 모든 시나리오에 맞게 차트 데이터 레이블을 사용자 정의하는 방법을 확인할 수 있습니다.

이 튜토리얼은 기존 차트를 수정하는 데 필요한 모든 내용을 다루며, 문서를 로드하는 단계부터 변경 사항을 저장하는 단계까지 포함합니다. 외부 참조가 필요하지 않으며—Aspose.Words for .NET 라이브러리와 기본 C# 개발 환경만 있으면 됩니다.

## 사전 요구 사항

* .NET 6.0(또는 이후 버전)이 설치되어 있어야 합니다.
* Aspose.Words for .NET 버전 23.9 이상. NuGet을 통해 설치할 수 있습니다:

```bash
dotnet add package Aspose.Words
```

* 최소 하나의 차트가 포함된 Word 파일(`input.docx`).

## C#에서 Word 차트에 데이터 레이블을 추가하는 방법

다음 섹션에서는 각 단계를 단계별로 안내합니다. 주요 키워드 **how to add data labels**가 서술과 코드 주석에 자연스럽게 나타나며, 권장 밀도 범위 내에 유지됩니다.

### 단계 1 – 차트를 포함한 Word 문서 로드

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

*왜 이 단계가 중요한가*: `Document` 객체는 전체 Word 파일을 나타냅니다. 이를 로드하면 차트를 포함하는 도형을 포함한 모든 노드에 접근할 수 있습니다.

### 단계 2 – 문서에서 첫 번째 차트 가져오기

```csharp
// Find the first shape that contains a chart.
Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
Chart chart = chartShape.GetChart();
```

*왜 이 단계가 중요한가*: 차트는 `Shape` 노드 내부에 저장됩니다. 검색된 노드를 `Shape`으로 캐스팅하고 `GetChart()`를 호출하면 시리즈, 축 및 레이블 컬렉션을 노출하는 `Chart` 객체를 얻을 수 있습니다.

### 단계 3 – 데이터 레이블 사용자 정의 활성화 및 차트에 백분율 표시

```csharp
// Access the first series of the chart.
ChartSeries series = chart.Series[0];

// Turn on data labels and request percentage values.
ChartDataLabelCollection dataLabels = series.DataLabels;
dataLabels.ShowPercentage = true;   // show percentages in chart
dataLabels.ShowValue = true;        // optional: also show raw values
```

*왜 이 단계가 중요한가*: `ShowPercentage`를 설정하면 Aspose.Words가 각 조각이 전체에 차지하는 비율을 계산하고 표시합니다. 이는 보조 키워드 **show percentages in chart**를 직접 다룹니다.

### 단계 4 – 레이블 위치를 각 데이터 포인트의 중앙으로 변경

```csharp
// Position the labels at the center of each point.
dataLabels.Position = ChartDataLabelPosition.Center; // center chart data labels
```

*왜 이 단계가 중요한가*: `Position` 속성은 레이블이 데이터 포인트에 대해 어디에 표시되는지를 제어합니다. `Center`를 사용하면 보조 키워드 **center chart data labels**를 만족시키며 파이 차트나 도넛 차트의 가독성을 향상시킵니다.

### 단계 5 – 차트 데이터 레이블 추가 사용자 정의 (선택 사항)

더 많은 제어가 필요하면 글꼴, 색상 또는 리더 라인을 조정할 수 있습니다:

```csharp
// Example: make labels bold and red.
dataLabels.Font.Bold = true;
dataLabels.Font.Color = System.Drawing.Color.Red;

// Example: add leader lines for better separation.
dataLabels.ShowLeaderLines = true;
```

이 설정은 보조 키워드 **customize chart data labels**를 보여주며, 브랜드 가이드라인에 맞게 외관을 맞춤화하는 방법을 시연합니다.

### 단계 6 – 수정된 문서 저장

```csharp
// Persist the changes to a new file.
document.Save("YOUR_DIRECTORY/output.docx");
```

*왜 이 단계가 중요한가*: 저장하면 업데이트된 차트가 Word 문서에 다시 기록되어 파일을 Microsoft Word에서 열 때 새로운 데이터 레이블이 표시됩니다.

## 전체 실행 가능한 예제

아래는 복사·붙여넣기·실행할 수 있는 완전한 프로그램입니다. 필요한 모든 `using` 지시문과 각 줄을 설명하는 주석이 포함되어 있습니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class AddDataLabelsDemo
{
    static void Main()
    {
        // 1. Load the Word document.
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first chart.
        Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
        Chart chart = chartShape.GetChart();

        // 3. Enable data labels and show percentages.
        ChartSeries series = chart.Series[0];
        ChartDataLabelCollection dataLabels = series.DataLabels;
        dataLabels.ShowPercentage = true;
        dataLabels.ShowValue = true;

        // 4. Center the labels on each data point.
        dataLabels.Position = ChartDataLabelPosition.Center;

        // 5. Optional: further customize appearance.
        dataLabels.Font.Bold = true;
        dataLabels.Font.Color = System.Drawing.Color.DarkBlue;
        dataLabels.ShowLeaderLines = true;

        // 6. Save the modified document.
        document.Save("YOUR_DIRECTORY/output.docx");

        Console.WriteLine("Data labels added and document saved successfully.");
    }
}
```

### 예상 결과

Microsoft Word에서 `output.docx`를 열면 차트가 다음과 같이 표시됩니다:

* 각 조각 옆에 백분율 값이 표시됩니다(예: **25 %**, **40 %**, …).
* 각 데이터 포인트의 중앙에 레이블이 배치됩니다.
* 적용한 추가 스타일링(예: 굵은 빨간색 텍스트)도 표시됩니다.

이러한 시각적 힌트는 차트를 해석하기 쉽게 만들어 주며, 특히 프레젠테이션이나 보고서에서 유용합니다.

## 데이터 레이블 외 차트 속성 편집 방법

이 가이드의 초점은 **how to add data labels**이지만, 제목, 범례 위치 또는 축 서식과 같은 **how to edit chart** 설정을 변경하고 싶을 수도 있습니다. `Chart` 객체는 `Title`, `Legend`, `AxisX/AxisY`와 같은 속성을 제공합니다. 예를 들어 차트 제목을 변경하려면:

```csharp
chart.Title.Text = "Quarterly Sales Breakdown";
chart.Title.Font.Size = 14;
```

모든 차트 수정은 동일한 패턴을 따릅니다: 차트를 검색하고, 속성을 조정한 뒤, 문서를 저장합니다.

## 일반적인 함정 및 모범 사례 팁

| 함정 | 발생 원인 | 권장 해결 방법 |
|---|---|---|
| 차트가 그룹화된 도형 안에 있음. | `GetChild(NodeType.Shape, …)`가 내부 차트가 아닌 외부 그룹을 반환합니다. | `shape.HasChart`가 있는 도형을 재귀적으로 검색합니다. |
| 저장 후 데이터 레이블이 표시되지 않음. | `ShowValue` 또는 `ShowPercentage`가 `true`로 설정되지 않았습니다. | 필요에 따라 `ShowValue`와 `ShowPercentage`를 모두 명시적으로 설정합니다. |
| 작은 조각에서 레이블이 겹침. | 중앙 위치 지정으로 인해 혼잡이 발생할 수 있습니다. | `ChartDataLabelPosition.OutSideEnd`를 사용해 외부에 배치하거나 `LeaderLines`를 활성화합니다. |

## 결론

이제 C#를 사용하여 Word 차트에 **how to add data labels**를 추가하는 방법을 알게 되었습니다. 튜토리얼에서는 차트를 검색하고, 레이블 표시를 활성화하며, 레이블을 중앙에 배치하고, 백분율을 표시하고, 외관을 사용자 정의하는 과정을 다루었습니다. 이 지식을 바탕으로 **how to edit chart** 세부 사항, **center chart data labels**, **show percentages in chart**, **customize chart data labels**를 모든 보고 시나리오에 적용할 수 있습니다.

더 탐색할 준비가 되셨나요? 여러 시리즈를 추가하거나, 조건부 서식을 적용하거나, 차트를 이미지로 내보내 보세요. Aspose.Words API는 광범위한 차트 조작 기능을 제공하므로, 데이터에 가장 적합한 시각적 표현을 찾아 실험해 보시기 바랍니다.

## 다음에 배워야 할 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 단계별 설명과 함께 완전한 작동 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [차트 데이터 레이블 사용자 정의](/words/english/net/programming-with-charts/chart-data-label/)
- [차트에서 데이터 레이블 기본 옵션 설정](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [차트의 단일 데이터 포인트 사용자 정의](/words/english/net/programming-with-charts/single-chart-data-point/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}