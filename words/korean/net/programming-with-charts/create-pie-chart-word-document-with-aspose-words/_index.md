---
category: general
date: 2026-08-10
description: Aspose.Words를 사용하여 파이 차트가 포함된 Word 문서를 만들기. 차트를 삽입하고 파이 차트 색상을 사용자 정의하며
  C#에서 파이 조각 색상을 변경하는 방법을 배우세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- customize pie chart colors
- how to style pie
- how to insert chart
- change pie slice color
language: ko
lastmod: 2026-08-10
og_description: Aspose.Words를 사용하여 파이 차트가 포함된 Word 문서를 만들기. 이 가이드는 차트를 삽입하고, 파이 차트
  색상을 사용자 정의하며, C# 애플리케이션에서 파이 조각 색상을 변경하는 방법을 설명합니다.
og_image_alt: Screenshot of a Word document containing a styled pie chart generated
  by Aspose.Words
og_title: 파이 차트 Word 문서 만들기 – Aspose.Words 가이드
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create pie chart Word document using Aspose.Words. Learn how to insert
    chart, customize pie chart colors, and change pie slice color in C#.
  headline: Create pie chart Word document with Aspose.Words
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, .NET
      6, and later. Just reference the same NuGet package.
    question: Does this work with .NET Core?
  - answer: Replace `ChartType.Pie` with `ChartType.Doughnut`. The same styling APIs
      (`Explosion`, `ForeColor`) apply.
    question: What if I need a donut chart instead of a pie?
  - answer: Open the existing file with `new Document("Existing.docx")`, create a
      `DocumentBuilder` for that document, and call `InsertChart` at the desired cursor
      position.
    question: Can I insert the chart into an existing document?
  - answer: 'Pie charts are best for a limited number of categories (typically < 10).
      For many categories, consider a bar or column chart instead. ## Full source
      code recap Below is the complete program in one block for easy copy‑paste: ```csharp
      using System; using System.Drawing; using Aspose.Words; using Aspo'
    question: How do I handle large datasets?
  type: FAQPage
tags:
- Aspose.Words
- C#
- pie chart
title: Aspose.Words로 파이 차트 워드 문서 만들기
url: /ko/net/programming-with-charts/create-pie-chart-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words를 사용하여 파이 차트 Word 문서 만들기

프로그램matically **파이 차트 Word 문서**를 만들어야 한다면, 이 튜토리얼이 정확히 어떻게 하는지 보여줍니다. 우리는 차트를 삽입하고, **파이 차트 색상 맞춤** 및 **파이 슬라이스 색상 변경**을 Aspose.Words for .NET을 사용하여 단계별로 안내합니다.

전체 실행 가능한 예제를 확인할 수 있으며, 이를 Visual Studio에 복사해 실행하고 바로 생성된 *.docx* 파일을 열어 스타일이 적용된 파이 차트를 확인할 수 있습니다. 외부 문서는 필요 없으며—필요한 모든 내용이 이 가이드에 포함되어 있습니다.

## 사전 요구 사항

* .NET 6.0 SDK 또는 그 이후 버전이 설치되어 있어야 합니다  
* 유효한 Aspose.Words for .NET 라이선스(또는 임시 평가 키)  
* Visual Studio 2022(또는 기타 C# IDE)  

코드에서는 `Aspose.Words`와 `Aspose.Words.Drawing.Charts` 네임스페이스만 사용하므로, Aspose.Words 라이브러리를 제외한 추가 NuGet 패키지는 필요하지 않습니다.

## 파이 차트 Word 문서 만들기 – 전체 예제

다음 C# 프로그램은 새 Word 문서를 생성하고, 파이 차트를 삽입하며, 처음 두 슬라이스에 스타일을 적용하고 파일을 저장합니다. 각 단계가 자세히 설명됩니다.

```csharp
using System;
using System.Drawing;                // For Color
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Initialize a blank document and a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a pie chart of size 400x300 points.
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            // Step 3: Populate the chart with sample data (optional but makes the chart visible).
            // Aspose.Words creates an empty series by default; we add a series with three values.
            chart.Series.Clear(); // Remove the default empty series.
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30); // Slice 1
            series.DataPoints.Add(45); // Slice 2
            series.DataPoints.Add(25); // Slice 3

            // Step 4: Explode the first slice to emphasize it.
            series.Points[0].Explosion = 20; // 20% explosion makes the slice pop out.

            // Step 5: **Customize pie chart colors** – set the first two slices.
            series.Points[0].Format.Fill.ForeColor = Color.Orange; // Slice 1 color
            series.Points[1].Format.Fill.ForeColor = Color.Green;  // Slice 2 color

            // Step 6: **Change pie slice color** for any additional slices if needed.
            // Example: set the third slice to a custom blue.
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            // Step 7: Save the document containing the styled pie chart.
            string outputPath = @"PieChartStyled.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### 각 단계 설명

| 단계 | 무엇을 수행하는가 | 왜 중요한가 |
|------|----------------|------------|
| **1** | 새로운 `Document`와 `DocumentBuilder`를 생성합니다. | `DocumentBuilder`는 차트와 같은 콘텐츠를 Word 파일에 삽입하기 위한 유창한 메서드를 제공합니다. |
| **2** | `ChartType.Pie`와 고정 크기를 사용하여 `InsertChart`를 호출합니다. | `InsertChart`는 **차트 삽입 방법** 메서드이며, 너비/높이를 지정하면 차트가 페이지에 잘 맞게 됩니다. |
| **3** | 세 개의 카테고리와 숫자 값을 가진 데이터 시리즈를 추가합니다. | 데이터가 없는 파이 차트는 보이지 않으므로, 데이터를 채워 스타일링 단계를 보여줍니다. |
| **4** | 첫 번째 포인트에 `Explosion`을 설정합니다. | 슬라이스를 분리하면 특정 구간에 주목을 끌 수 있어 핵심 데이터를 강조할 때 유용합니다. |
| **5** | 처음 두 포인트에 `ForeColor`를 설정합니다. | 이것이 **파이 차트 색상 맞춤**의 핵심이며, `System.Drawing.Color`를 사용하면 됩니다. |
| **6** | 추가 슬라이스에 대해 **파이 슬라이스 색상 변경** 방법을 보여줍니다. | 스타일링이 처음 두 슬라이스에만 국한되지 않으며, 각 슬라이스를 개별적으로 색칠할 수 있음을 보여줍니다. |
| **7** | 문서를 `PieChartStyled.docx`로 저장합니다. | 최종 출력은 Microsoft Word, Google Docs 또는 호환 가능한 뷰어에서 열 수 있습니다. |

#### 예상 출력

`PieChartStyled.docx`를 열면 400 × 300 pt 파이 차트가 포함된 단일 페이지가 표시됩니다:

* 슬라이스 1 (오렌지) 은 외부로 분리됩니다.  
* 슬라이스 2 (녹색) 은 분리된 슬라이스 옆에 표시됩니다.  
* 슬라이스 3 (스틸 블루) 은 나머지 구간을 채웁니다.

차트는 데이터 값 (30, 45, 25) 및 정의한 사용자 지정 색상을 반영합니다.

## 파이 스타일링 방법 – 추가 팁

* **테마 색상 사용** – `Color.Orange`를 하드코딩하는 대신 문서 테마에서 색상을 가져올 수 있습니다:  
  ```csharp
  chart.Series[0].Points[0].Format.Fill.ForeColor = doc.Theme.ColorScheme.Accent1;
  ```
* **데이터 레이블 추가** – 차트에 백분율을 표시하고 싶다면:  
  ```csharp
  chart.HasDataLabel = true;
  chart.DataLabel.NumberFormat = "#%";
  ```
* **동적으로 크기 조정** – 페이지 여백을 기준으로 차트 크기를 계산합니다:  
  ```csharp
  double width = doc.PageSetup.PageWidth - doc.PageSetup.LeftMargin - doc.PageSetup.RightMargin;
  double height = width * 0.75; // 4:3 aspect ratio
  builder.InsertChart(ChartType.Pie, width, height);
  ```

이러한 변형은 기본 예제를 넘어 **파이 스타일링 방법**의 유연성을 보여줍니다.

## 자주 묻는 질문

**Q: 이것이 .NET Core에서 작동합니까?**  
A: 예. Aspose.Words for .NET은 .NET Core, .NET 5, .NET 6 및 이후 버전과 호환됩니다. 동일한 NuGet 패키지를 참조하면 됩니다.

**Q: 파이 차트 대신 도넛 차트가 필요하면 어떻게 해야 하나요?**  
A: `ChartType.Pie`를 `ChartType.Doughnut`으로 교체하면 됩니다. 동일한 스타일링 API(`Explosion`, `ForeColor`)가 적용됩니다.

**Q: 기존 문서에 차트를 삽입할 수 있나요?**  
A: `new Document("Existing.docx")` 로 기존 파일을 열고, 해당 문서에 대한 `DocumentBuilder`를 만든 뒤, 원하는 커서 위치에서 `InsertChart`를 호출하면 됩니다.

**Q: 대용량 데이터 세트를 어떻게 처리하나요?**  
A: 파이 차트는 카테고리 수가 제한된 경우(보통 < 10) 가장 적합합니다. 카테고리가 많을 경우 막대 차트나 컬럼 차트를 고려하세요.

## 전체 소스 코드 요약

아래는 복사‑붙여넣기하기 쉬운 하나의 블록에 포함된 전체 프로그램입니다:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            chart.Series.Clear();
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30);
            series.DataPoints.Add(45);
            series.DataPoints.Add(25);

            series.Points[0].Explosion = 20;
            series.Points[0].Format.Fill.ForeColor = Color.Orange;
            series.Points[1].Format.Fill.ForeColor = Color.Green;
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            doc.Save("PieChartStyled.docx");
            Console.WriteLine("Document saved as PieChartStyled.docx");
        }
    }
}
```

이 코드를 실행하면 앞서 설명한 스타일이 적용된 파이 차트 Word 문서가 생성됩니다.

## 결론

이제 Aspose.Words를 사용하여 **파이 차트 Word** 문서를 **생성**, **파이 차트 색상 맞춤**, 그리고 **파이 슬라이스 색상 변경**을 프로그래밍 방식으로 수행하는 방법을 알게 되었습니다. 이 가이드에서는 차트 삽입, 데이터 채우기, 슬라이스 분리, 사용자 지정 색상 적용, 그리고 결과 저장까지 다루었습니다.

이제 여기서 파이 외의 **차트 삽입 방법** 유형, 범례 추가, 여러 차트가 포함된 다중 페이지 보고서 생성 등 관련 주제를 탐색할 수 있습니다. 다양한 색 구성표와 데이터 세트를 실험하여 보고 요구에 맞게 조정해 보세요.

코딩 즐겁게 하세요!

## 다음에 배울 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 단계별 설명과 함께 완전한 작동 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Aspose.Words for .NET을 사용하여 Word에 열 차트 삽입](/words/english/net/working-with-charts/insert-column-chart/)
- [Aspose.Words for .NET을 사용하여 Word 문서에 영역 차트 삽입](/words/english/net/working-with-charts/insert-area-chart/)
- [Aspose.Words for .NET을 사용하여 Word 산점도 차트 만들기](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}