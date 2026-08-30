---
category: general
date: 2026-07-26
description: Aspose.Words를 사용하여 Word 문서에 원형 차트를 삽입합니다. 차트를 추가하고, 슬라이스를 분리하며, 백분율을
  표시하는 방법을 몇 단계만에 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to add chart
- how to explode slice
- add chart to word
- how to show percentages
language: ko
lastmod: 2026-07-26
og_description: Aspose.Words를 사용하여 Word 파일에 파이 차트를 삽입합니다. 이 가이드를 따라 차트를 추가하고, 슬라이스를
  분리하며, 백분율을 빠르게 표시하는 방법을 배워보세요.
og_image_alt: Screenshot illustrating insert pie chart in a Word document
og_title: Word에 파이 차트 삽입 – 단계별 Aspose.Words 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert pie chart into a Word document using Aspose.Words. Learn how
    to add chart, explode slice, and show percentages in just a few steps.
  headline: Insert Pie Chart in Word with Aspose.Words – Complete Guide
  type: TechArticle
- questions:
  - answer: Just add additional `ChartSeries` objects to `chart.Series`. Each series
      can have its own data set, colors, and explode settings.
    question: What if I need more than one series?
  - answer: Yes. Each `ChartPoint` has a `Format.Fill.ForeColor` property you can
      set to any `System.Drawing.Color`.
    question: Can I change the chart’s colors?
  - answer: The `ChartType` enum includes bar, line, doughnut, and many more. Swap
      `ChartType.Pie` for whichever visual you need.
    question: What about different chart types?
  - answer: Absolutely. Word treats the chart as a native Office chart, so users can
      double‑click it to open the built‑in chart editor.
    question: Is the chart editable in Word after insertion?
  type: FAQPage
tags:
- Aspose.Words
- Chart Automation
- .NET Development
title: Aspose.Words를 사용하여 Word에 파이 차트 삽입 – 완전 가이드
url: /ko/java/using-document-elements/insert-pie-chart-in-word-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words를 사용하여 Word에 파이 차트 삽입 – 완전 가이드

Word 보고서에 **파이 차트**를 삽입해야 했지만 어디서 시작해야 할지 몰랐던 적이 있나요? 당신만 그런 것이 아닙니다. 많은 비즈니스 앱에서 파이 차트의 시각적 효과는 데이터를 즉시 이해하기 쉽게 만들며, Aspose.Words는 몇 줄의 코드만으로 이를 가능하게 합니다.

이 튜토리얼에서는 **add chart to Word**(Word에 차트 추가)하는 정확한 단계와 강조를 위한 슬라이스 폭발, 데이터 레이블에 백분율 표시 방법을 살펴보겠습니다. 끝까지 진행하면 .NET 프로젝트에 바로 넣어 실행할 수 있는 예제를 얻게 됩니다.

---

## 필수 조건

- .NET 6.0 이상 (코드는 .NET Core와 .NET Framework에서도 작동합니다)
- The Aspose.Words for .NET NuGet package installed  
  ```bash
  dotnet add package Aspose.Words
  ```
- C# 구문에 대한 기본 이해—특별한 지식은 필요 없습니다
- 원하는 IDE (Visual Studio, Rider, 또는 VS Code)

이것으로 준비되었습니다. 이제 직접 해봅시다.

---

## Word 문서에 파이 차트 삽입

먼저 필요한 것은 새 `Document` 객체와 `DocumentBuilder`입니다. Builder를 Word 캔버스에 직접 쓰는 펜이라고 생각하면 됩니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
using Aspose.Words.Charts;

// Step 1: Create a new document and a builder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **왜 중요한가:** `Document`는 전체 .docx 파일을 나타내며, `DocumentBuilder`는 차트, 표, 텍스트와 같은 요소를 삽입할 수 있는 편리한 API를 제공합니다. 이는 모든 **how to add chart** 작업의 기반이 됩니다.

---

## Word에 차트 추가 방법

Builder가 준비되었으니 이제 실제로 **insert pie chart**(파이 차트 삽입)할 수 있습니다. `insertChart` 메서드는 차트 유형과 포인트 단위의 원하는 크기(1 포인트 = 1/72 인치)를 입력받습니다.

```csharp
// Step 2: Insert a pie chart of size 400x300 points
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

> **팁:** 다른 크기가 필요하면 너비와 높이 값을 조정하면 됩니다. 차트는 페이지 여백에 맞게 자동으로 크기가 조정됩니다.

---

## 강조를 위한 슬라이스 폭발 방법

일반적인 시각적 조정으로 슬라이스를 “폭발”시켜 원 밖으로 튀어나오게 할 수 있습니다. 이렇게 하면 독자의 시선이 가장 중요한 구간으로 집중됩니다.

```csharp
// Step 3: Access the first series (the data set)
ChartSeries series = chart.Series[0];

// Step 4: Explode the first slice to emphasize it
series.Points[0].Exploded = true;
```

> **왜 슬라이스를 폭발시키나요?** 특정 카테고리(예: 재무 보고서의 “Q1 매출”)를 강조하고 싶을 때, 슬라이스를 폭발시키면 별도의 텍스트 없이도 즉시 눈에 띄게 됩니다.

---

## 데이터 레이블에 백분율 표시 방법

대부분의 파이 차트는 각 슬라이스가 백분율을 표시할 때 더 보기 좋습니다. Aspose.Words는 단일 속성으로 이를 활성화할 수 있게 해줍니다.

```csharp
// Step 5: Show percentages on the data labels of the first series
series.DataLabelFormat.ShowPercentage = true;
```

> **간단한 참고:** `ShowPercentage` 플래그는 시리즈의 모든 포인트에 적용되므로 슬라이스별로 설정할 필요가 없습니다.

---

## 차트가 포함된 문서 저장

마지막으로 문서를 디스크에 저장합니다. 원하는 폴더를 선택하면 되며, 경로가 존재하는지 확인하세요.

```csharp
// Step 6: Save the document containing the chart
doc.Save(@"C:\Temp\PieChart.docx");
```

Microsoft Word에서 `PieChart.docx`를 열면 첫 번째 슬라이스가 폭발되고 백분율이 표시된 완벽하게 렌더링된 파이 차트를 볼 수 있습니다—정교한 비즈니스 보고서에서 기대하는 바로 그 모습입니다.

---

## 전체 작업 예제

아래는 완전한 복사‑붙여넣기 가능한 프로그램입니다. 콘솔 앱으로 실행하고 출력 파일을 확인하세요.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a pie chart (400x300 points)
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data
            ChartSeries series = chart.Series[0];
            series.Name = "Sales Q1";
            series.Add(30); // Product A
            series.Add(45); // Product B
            series.Add(25); // Product C

            // Explode the first slice (Product A)
            series.Points[0].Exploded = true;

            // Show percentages on data labels
            series.DataLabelFormat.ShowPercentage = true;

            // Save the document
            string outputPath = @"C:\Temp\PieChart.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**예상 결과:** 생성된 `PieChart.docx`를 열면 “Sales Q1”이라는 제목의 3개 슬라이스 파이 차트가 표시됩니다. 첫 번째 슬라이스가 튀어나와 있고 각 슬라이스는 “30 %”, “45 %”, “25 %”로 라벨링됩니다. 시각적 결과는 입력한 데이터와 일치합니다.

---

## 자주 묻는 질문 및 예외 상황

- **시리즈가 하나 이상 필요하면 어떻게 하나요?**  
  `chart.Series`에 추가 `ChartSeries` 객체를 추가하면 됩니다. 각 시리즈는 자체 데이터 세트, 색상 및 폭발 설정을 가질 수 있습니다.

- **차트 색상을 변경할 수 있나요?**  
  예. 각 `ChartPoint`에는 원하는 `System.Drawing.Color`로 설정할 수 있는 `Format.Fill.ForeColor` 속성이 있습니다.

- **다른 차트 유형은 어떻게 하나요?**  
  `ChartType` 열거형에는 막대, 선, 도넛 등 다양한 유형이 포함됩니다. 필요에 따라 `ChartType.Pie`를 원하는 차트 유형으로 교체하면 됩니다.

- **삽입 후 Word에서 차트를 편집할 수 있나요?**  
  물론 가능합니다. Word는 차트를 기본 Office 차트로 취급하므로 사용자는 차트를 더블클릭하여 내장 차트 편집기를 열 수 있습니다.

---

## 결론

이제 Aspose.Words를 사용하여 Word 문서에 **insert pie chart**(파이 차트 삽입)하는 방법, **how to add chart to word**, **how to explode slice**, 그리고 데이터 레이블에 **how to show percentages**(백분율 표시)하는 방법을 정확히 알게 되었습니다. 위의 전체 예제는 바로 실행할 수 있으며, 사용자 정의 데이터, 스타일링 또는 추가 시리즈로 확장할 수 있습니다.

다음 단계가 준비되셨나요? 파이를 도넛 차트로 바꾸어 보거나, 다양한 데이터 세트로 자동으로 여러 보고서를 생성해 보세요. 다른 시각화에 관심이 있다면 막대 및 선 그래프에 대한 **how to add chart** 가이드를 확인하거나, 더 깊은 커스터마이징을 위해 **add chart to word** API 레퍼런스를 살펴보세요.

코딩을 즐기세요, 그리고 여러분의 문서가 완벽하게 썰린 파이처럼 언제나 명확하기를 바랍니다!

## 다음에 배워야 할 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 단계별 설명과 함께 완전한 작업 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Aspose.Words for .NET을 사용하여 Word에 열 차트 삽입](/words/english/net/working-with-charts/insert-column-chart/)
- [Aspose.Words for .NET | Word 문서에 영역 차트 삽입](/words/english/net/working-with-charts/insert-area-chart/)
- [Aspose.Words for .NET을 사용하여 Word 산점도 차트 만들기](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}