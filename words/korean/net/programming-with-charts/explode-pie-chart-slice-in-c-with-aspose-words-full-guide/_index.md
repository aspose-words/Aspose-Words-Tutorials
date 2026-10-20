---
category: general
date: 2026-07-19
description: Aspose.Words for C#를 사용하여 파이 차트 조각을 분리하세요. 파이 조각을 분리하고, 도넛 구멍 크기를 조정하며,
  차트 데이터 포인트를 빠르게 변경하는 방법을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- explode pie chart slice
- how to explode pie slice
- adjust doughnut hole size
- change chart data points
language: ko
lastmod: 2026-07-19
og_description: Aspose.Words for C#를 사용하여 파이 차트 조각을 분리합니다. 이 가이드는 파이 조각을 분리하고, 도넛
  구멍 크기를 조정하며, 차트 데이터 포인트를 효율적으로 변경하는 방법을 보여줍니다.
og_image_alt: Screenshot showing an exploded pie chart slice created with Aspose.Words
  in C#
og_title: C#에서 파이 차트 조각 분리하기 – Aspose.Words 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  headline: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  type: TechArticle
- description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  name: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  steps:
  - name: Install and Reference Aspose.Words
    text: 'First things first, add the Aspose.Words package to your project. In the
      Package Manager Console:'
  - name: Load the Word Document Containing the Chart
    text: We need a `Document` object that points at the `.docx` with the chart you
      want to modify.
  - name: Retrieve the First Chart Node
    text: Most examples assume a single chart, so we’ll grab the first one. If you
      have multiple charts, adjust the index accordingly.
  - name: Explode the First Slice of a Pie Chart
    text: Now the star of the show—**how to explode pie slice**. We’ll set the `Exploded`
      property of the first data point.
  - name: Adjust Doughnut Hole Size (If It’s a Doughnut Chart)
    text: If your chart happens to be a doughnut, you might want to **adjust doughnut
      hole size**. The hole size is a percentage of the chart’s radius.
  - name: Change Chart Data Points (Optional)
    text: Sometimes you need to **change chart data points**—maybe you’ve updated
      the underlying numbers and want the visual to reflect that.
  - name: Save the Modified Document
    text: Finally, write the changes back to disk. You can overwrite the original
      or create a new file—up to you.
  - name: What’s Next?
    text: '- **Style the exploded slice** (change fill color, border, or add a data
      label). Search for “Aspose.Words chart formatting”. - **Automate batch processing**
      of multiple documents—loop through a folder, explode slices, and save new versions.
      - **Combine with Aspose.Slides** if you need the same chart'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: C#와 Aspose.Words를 사용한 파이 차트 슬라이스 분리 – 전체 가이드
url: /ko/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#와 Aspose.Words를 사용한 파이 차트 조각 폭발 – 전체 가이드

Word 문서에서 C#로 **파이 차트 조각을 폭발**시키는 방법이 궁금하셨나요? 당신만 그런 것이 아닙니다. 영업 프레젠테이션을 준비하거나 설문 결과를 시각화할 때, 폭발된 조각은 눈길을 정확히 원하는 곳으로 끌어당깁니다. 이 튜토리얼에서는 문서를 로드하고, 차트를 가져와 첫 번째 조각을 폭발시키고, 도넛 차트의 구멍을 조정하며, 차트 데이터 포인트까지 변경하는 전체 과정을 단계별로 안내합니다.

또한 여러분이 찾고 있을 **파이 조각 폭발 방법**, **도넛 구멍 크기 조정**, **차트 데이터 포인트 변경**과 같은 부가 개념도 함께 다룹니다. 불필요한 내용 없이 바로 복사‑붙여넣기 가능한 완전한 솔루션을 제공합니다.

---

## 준비물

시작하기 전에 다음이 준비되어 있는지 확인하세요:

- **Aspose.Words for .NET** (2026‑07‑19 현재 최신 버전). NuGet에서 `Install-Package Aspose.Words` 명령으로 설치할 수 있습니다.
- **.NET 6+** 프로젝트(또는 레거시 환경이라면 .NET Framework 4.7.2+).
- 파이 차트 또는 도넛 차트가 포함된 Word 파일(`Chart.docx`). 없으시다면 Word에서 차트를 하나 만들고 저장하면 됩니다.

이것만 있으면 됩니다—추가 라이브러리나 COM 인터옵 없이 순수 관리 코드만으로 가능합니다.

---

## 파이 차트 조각 폭발 – 단계별 구현

아래에서는 작업을 작은 단계로 나누어 설명합니다. 각 섹션에는 명확한 제목, 코드 스니펫, 그리고 *왜* 그렇게 하는지에 대한 짧은 설명이 포함됩니다.

### Step 1: Install and Reference Aspose.Words

먼저, Aspose.Words 패키지를 프로젝트에 추가합니다. 패키지 관리자 콘솔에서:

```powershell
Install-Package Aspose.Words
```

> **Pro tip:** Visual Studio 내장 NuGet UI를 사용한다면 “Aspose.Words”를 검색하고 Install을 클릭하세요. 최신 버그 수정과 차트 지원을 바로 받을 수 있습니다.

### Step 2: Load the Word Document Containing the Chart

수정하려는 차트가 들어 있는 `.docx` 파일을 가리키는 `Document` 객체가 필요합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document
Document doc = new Document(@"C:\Charts\Chart.docx");

// Verify that the document actually contains a chart
if (doc.GetChildNodes(NodeType.Chart, true).Count == 0)
{
    throw new InvalidOperationException("No chart found in the specified document.");
}
```

> **Why this matters:** `Document`는 Aspose.Words의 모든 작업 진입점입니다. 차트를 미리 확인하면 나중에 조각을 폭발시킬 때 NullReference 오류를 방지할 수 있습니다.

### Step 3: Retrieve the First Chart Node

대부분 예제는 차트가 하나라고 가정하므로 첫 번째 차트를 가져옵니다. 차트가 여러 개라면 인덱스를 조정하세요.

```csharp
// Grab the first chart in the document (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

> **Note:** 차트가 존재함을 확인한 뒤 `Chart`로 캐스팅하는 것은 안전합니다. 이 객체를 통해 시리즈, 데이터 포인트 및 차트 유형별 설정에 접근할 수 있습니다.

### Step 4: Explode the First Slice of a Pie Chart

이제 핵심인 **파이 조각 폭발 방법**을 살펴보겠습니다. 첫 번째 데이터 포인트의 `Exploded` 속성을 설정합니다.

```csharp
// Ensure the chart is a Pie (or Pie3D) before exploding
if (chart.ChartType == ChartType.Pie || chart.ChartType == ChartType.Pie3D)
{
    // Explode the first slice (index 0)
    chart.PieChartData.Series[0].DataPoints[0].Exploded = true;
}
else
{
    Console.WriteLine("The chart is not a pie chart; skipping explode operation.");
}
```

> **Why this works:** `Exploded` 속성은 Word에게 해당 조각을 중심에서 떨어뜨리도록 지시합니다. 불리언 값이므로 `true`로 설정하면 클래식한 “폭발 파이” 효과가 나타납니다.

### Step 5: Adjust Doughnut Hole Size (If It’s a Doughnut Chart)

차트가 도넛 형태라면 **도넛 구멍 크기 조정**이 필요할 수 있습니다. 구멍 크기는 차트 반경의 백분율로 지정됩니다.

```csharp
// Check for Doughnut chart type and modify the hole size
if (chart.ChartType == ChartType.Doughnut)
{
    // Set the hole size to 30% (range: 0–100)
    chart.DoughnutChartData.HoleSize = 30;
}
```

> **What the number means:** `30`이라는 값은 내부 원이 전체 반경의 30 %를 차지한다는 의미이며, 외부 링이 더 두꺼워집니다.

### Step 6: Change Chart Data Points (Optional)

때때로 **차트 데이터 포인트를 변경**해야 할 때가 있습니다—예를 들어 기본 숫자가 업데이트되어 시각화에도 반영하고 싶을 때 말이죠.

```csharp
// Example: Update the second data point's value to 75
if (chart.PieChartData?.Series?.Count > 0 && chart.PieChartData.Series[0].DataPoints.Count > 1)
{
    chart.PieChartData.Series[0].DataPoints[1].Value = 75;
}
```

> **Why you’d do this:** 데이터 포인트 값을 변경하면 슬라이스 비율이 자동으로 재계산되어 Word에서 수동으로 편집할 필요 없이 차트가 정확하게 유지됩니다.

### Step 7: Save the Modified Document

마지막으로 변경 사항을 디스크에 저장합니다. 원본을 덮어쓰거나 새 파일을 만들 수 있습니다—선택은 자유입니다.

```csharp
// Save the document with the exploded slice and adjusted doughnut hole
doc.Save(@"C:\Charts\FormattedChart.docx");

// Quick confirmation
Console.WriteLine("Document saved successfully with exploded pie chart slice.");
```

> **Tip:** `SaveFormat.Docx`를 명시적으로 사용해도 되지만, `Save(string)`은 파일 확장자를 기준으로 형식을 자동 감지합니다.

---

## Expected Result

`FormattedChart.docx`를 Microsoft Word에서 열면 다음과 같은 결과를 확인할 수 있습니다:

- 파이 차트의 첫 번째 조각이 **폭발**되어 바깥쪽으로 이동합니다.
- 차트가 도넛인 경우, 중앙 구멍이 이제 반경의 **30 %**를 차지합니다.
- 수정한 모든 데이터 포인트가 새로운 값으로 반영됩니다.

아래는 폭발된 조각이 어떻게 보이는지에 대한 모형 이미지(예시)입니다.

![Exploded pie chart slice created with Aspose.Words in C#](exploded-pie-slice.png)

*Alt text:* **exploded pie chart slice** 워드 문서에서 분리된 조각을 보여줍니다.

---

## Common Questions & Edge Cases

**차트가 파이 차트나 도넛 차트가 아닌 경우는?**  
코드는 `ChartType`을 확인한 뒤 `Exploded` 또는 `HoleSize`를 적용합니다. 막대, 선, 영역 차트에는 해당 속성이 없으므로 로직이 안전하게 건너뛰게 됩니다.

**여러 조각을 동시에 폭발시킬 수 있나요?**  
물론 가능합니다. `chart.PieChartData.Series[0].DataPoints`를 순회하면서 원하는 인덱스의 `Exploded = true`를 설정하면 됩니다.

**문화권별 숫자 형식에 신경 써야 하나요?**  
Aspose.Words는 숫자를 double 형태로 저장하므로 로케일에 관계없이 콤마와 점 문제에서 자유롭습니다.

**헤더/푸터에 삽입된 차트는 어떻게 처리하나요?**  
`doc.GetChildNodes(NodeType.Chart, true)`를 사용해 모든 차트를 가져온 뒤 각 노드의 `ParentNode`를 검사하면 차트가 위치한 영역을 확인할 수 있습니다. 동일한 폭발 로직을 그대로 적용하면 됩니다.

---

## Conclusion

이제 C#와 Aspose.Words를 사용해 **파이 차트 조각을 폭발**시키는 완전한 복사‑붙여넣기 솔루션을 갖추게 되었습니다. 문서 로드, 차트 가져오기, 조각 폭발, **도넛 구멍 크기 조정**, **차트 데이터 포인트 변경**까지 전체 워크플로우를 다루었으며 최종적으로 파일을 저장하는 방법까지 설명했습니다.

다양하게 실험해 보세요: 다른 조각을 폭발시키거나 구멍 크기를 45 %로 조정하거나 여러 데이터 포인트를 한 번에 업데이트해 보세요. Aspose.Words API 덕분에 이러한 조정이 손쉽게 이루어지며, Word 파일을 열면 즉시 변경 사항이 반영됩니다.

---

### What’s Next?

- **Style the exploded slice** (change fill color, border, or add a data label). Search for “Aspose.Words chart formatting”.
- **Automate batch processing** of multiple documents—loop through a folder, explode slices, and save new versions.
- **Combine with Aspose.Slides** if you need the same chart in a PowerPoint deck.

더 많은 차트 조작 질문이 있거나 다른 차트 유형에 대해 깊이 파고들고 싶다면 아래 댓글로 알려 주세요. 즐거운 코딩 되세요!

## What Should You Learn Next?

다음 튜토리얼에서는 이번 가이드에서 배운 기술을 확장할 수 있는 관련 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함하여 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용할 수 있도록 돕습니다.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}