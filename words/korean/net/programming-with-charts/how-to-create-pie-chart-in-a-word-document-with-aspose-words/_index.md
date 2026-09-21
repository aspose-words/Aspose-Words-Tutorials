---
category: general
date: 2026-09-21
description: Aspose.Words를 사용하여 파이 차트를 만들고 Word에 차트를 삽입하는 방법, 파이 차트에 데이터 레이블을 추가하고
  파이 차트에 백분율을 표시하는 방법을 몇 단계만에 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- insert chart into word
- add data labels to pie chart
- show percentages on pie chart
- how to display percentages in chart
language: ko
lastmod: 2026-09-21
og_description: Aspose.Words를 사용하여 Word에서 파이 차트를 만들고, 차트를 Word에 삽입하며, 파이 차트에 데이터 레이블을
  추가하고, 파이 차트에 백분율을 표시합니다—모두 명확한 코드 예제로.
og_image_alt: Screenshot of a Word document containing a pie chart with percentage
  data labels displayed outside each slice
og_title: Aspose.Words를 사용하여 Word에서 파이 차트 만들기 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
- description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  name: How to create pie chart in a Word document with Aspose.Words
  steps:
  - name: Expected output
    text: 'When you open the generated document, you should see:'
  - name: Adding a title to the chart
    text: '```csharp chart.Title.Text = "Sales Distribution Q1"; chart.Title.Show
      = true; ```'
  - name: Changing slice colors
    text: '```csharp series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
      series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen; ```'
  - name: Handling an empty series
    text: 'If your data source might be empty, guard against `IndexOutOfRangeException`:'
  - name: Exporting to PDF instead of Word
    text: '```csharp doc.Save("PieChart.pdf", SaveFormat.Pdf); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- charting
- Word automation
title: Aspose.Words를 사용하여 Word 문서에 파이 차트 만들기
url: /ko/net/programming-with-charts/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words를 사용하여 Word 문서에 파이 차트 만들기

프로그래밍 방식으로 **파이 차트 만들기**가 필요하다면 Aspose.Words가 간단하게 처리해 줍니다. 이 튜토리얼에서는 **Word에 차트 삽입**, 시리즈 구성, **파이 차트에 데이터 레이블 추가**, 그리고 **파이 차트에 백분율 표시**하는 방법을 보여줍니다. 마지막에는 .NET 프로젝트에 바로 넣어 실행할 수 있는 완전한 예제가 제공됩니다.

이 가이드는 필요한 NuGet 패키지, 전체 C# 소스, 각 API 호출이 중요한 이유에 대한 설명, 차트 커스터마이징 팁을 모두 다룹니다. 별도의 외부 문서는 필요 없으며, 복사하고 실행하고 필요에 맞게 수정하면 됩니다.

## Prerequisites

시작하기 전에 다음이 준비되어 있는지 확인하세요:

* .NET 6.0 SDK 이상이 설치되어 있어야 합니다.  
* Visual Studio 2022(또는 .NET을 지원하는 IDE).  
* Aspose.Words for .NET 라이선스(무료 체험판도 테스트에 사용 가능).  
* C# 및 Word 문서 구조에 대한 기본 지식.

위 항목이 모두 준비되었다면 바로 코드 단계로 넘어갈 수 있습니다.

## Step 1: 프로젝트 설정 및 Aspose.Words 가져오기

새 콘솔 프로젝트를 만들고 Aspose.Words NuGet 패키지를 추가합니다:

```bash
dotnet new console -n PieChartDemo
cd PieChartDemo
dotnet add package Aspose.Words
```

패키지에는 `Aspose.Words.Drawing.Charts` 네임스페이스가 포함되어 있으며, 여기서 `Chart`와 `ChartSeries` 클래스를 사용할 수 있습니다.

> **팁:** 라이선스 파일(`Aspose.Words.lic`)을 프로젝트 루트에 두고 시작 시 로드하면 평가 워터마크를 방지할 수 있습니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: Apply your license
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");
```

## Step 2: 빈 문서와 DocumentBuilder 만들기

`Document`는 Word 파일을 나타내고, `DocumentBuilder`는 콘텐츠 삽입을 위한 유창한 API를 제공합니다.

```csharp
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder will let us add a chart
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**왜 중요한가:** `DocumentBuilder`는 현재 삽입 위치를 유지하므로 차트가 문서 흐름에서 정확히 원하는 위치에 나타납니다.

## Step 3: Word 문서에 파이 차트 삽입

이제 **Word에 차트 삽입**을 수행합니다. `InsertChart` 메서드는 차트 유형, 너비, 높이(포인트)를 인수로 받습니다.

```csharp
        // Insert a pie chart of size 400x300 points
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

이 시점에서 차트에는 기본 데이터 시리즈가 (25, 25, 25, 25)라는 자리 표시값으로 들어 있습니다. 필요에 따라 나중에 교체할 수 있습니다.

## Step 4: 첫 번째 시리즈에 접근하고 데이터 레이블 커스터마이징

파이 차트는 일반적으로 하나의 시리즈만 가집니다. **파이 차트에 데이터 레이블 추가**를 위해 시리즈를 가져와 백분율 표시를 활성화합니다.

```csharp
        // Access the first (and only) series of the chart
        ChartSeries series = chart.Series[0];

        // Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // Position the labels outside the slices for readability
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

**`ShowPercentage`를 설정하는 이유:** 이 플래그는 Aspose.Words에게 각 조각의 비율을 계산하고 백분율로 렌더링하도록 지시합니다. `Position` 속성은 레이블이 조각과 겹치지 않도록 하여 가독성을 높여줍니다—특히 조각이 작을 때 유용합니다.

## Step 5: (선택) 자리 표시 데이터 교체

특정 값을 사용하려면 기본 포인트를 교체합니다:

```csharp
        // Clear existing points
        series.Points.Clear();

        // Add custom data points
        series.Points.Add(new ChartPoint(40)); // 40%
        series.Points.Add(new ChartPoint(30)); // 30%
        series.Points.Add(new ChartPoint(20)); // 20%
        series.Points.Add(new ChartPoint(10)); // 10%
```

표시되는 백분율은 새 값에 맞게 자동으로 조정됩니다.

## Step 6: 문서 저장

마지막으로 문서를 디스크에 씁니다. 파일 확장자가 형식을 결정하며, `.docx`는 최신 Word 파일을 생성합니다.

```csharp
        // Save the document containing the pie chart
        doc.Save("PieChart.docx");
    }
}
```

프로그램을 실행하면 **PieChart.docx**라는 파일이 출력 폴더에 생성됩니다. Microsoft Word에서 열면 각 조각에 백분율 레이블이 외부에 표시된 파이 차트를 확인할 수 있습니다.

### Expected output

생성된 문서를 열면 다음과 같은 내용이 보여야 합니다:

* 크기 400 × 300 pt인 파이 차트 하나.  
* 네 개의 조각(또는 추가한 포인트 수만큼).  
* “40 %”, “30 %” 등과 같은 백분율 레이블이 각 조각 외부에 표시됨.

레이블이 조각 내부에 표시된다면 `ChartDataLabelPosition.OutsideEnd`가 올바르게 설정되었는지 다시 확인하세요.

## Step 7: 일반적인 변형 및 엣지 케이스

### 차트에 제목 추가

```csharp
chart.Title.Text = "Sales Distribution Q1";
chart.Title.Show = true;
```

### 조각 색상 변경

```csharp
series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen;
```

### 빈 시리즈 처리

데이터 소스가 비어 있을 수 있다면 `IndexOutOfRangeException`을 방지하세요:

```csharp
if (series.Points.Count == 0)
{
    // Provide a fallback to avoid runtime errors
    series.Points.Add(new ChartPoint(100));
}
```

### Word 대신 PDF로 내보내기

```csharp
doc.Save("PieChart.pdf", SaveFormat.Pdf);
```

차트 렌더링 로직은 동일하며, Aspose.Words가 Word 레이아웃을 자동으로 PDF로 변환합니다.

## Full source listing

아래는 완전한 실행 가능한 프로그램 전체 코드입니다. `Program.cs`에 복사하고 `dotnet run`을 실행하세요.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: apply your license to remove evaluation watermarks
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Create a DocumentBuilder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a pie chart (400x300 points)
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 4. Access the first series
        ChartSeries series = chart.Series[0];

        // 5. Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // 6. Position data labels outside the slices
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Optional: replace placeholder data with custom values
        series.Points.Clear();
        series.Points.Add(new ChartPoint(40));
        series.Points.Add(new ChartPoint(30));
        series.Points.Add(new ChartPoint(20));
        series.Points.Add(new ChartPoint(10));

        // Optional: add a title
        chart.Title.Text = "Quarterly Sales Breakdown";
        chart.Title.Show = true;

        // 7. Save the document
        doc.Save("PieChart.docx"); // Change extension to .pdf for PDF output
    }
}
```

## Conclusion

이제 Aspose.Words를 사용해 Word 파일에 **파이 차트 만들기**, **Word에 차트 삽입**, **파이 차트에 데이터 레이블 추가**, **파이 차트에 백분율 표시**하는 방법을 알게 되었습니다. 예제는 프로젝트 설정부터 최종 문서까지 전체 워크플로우를 보여주므로 대시보드, 보고서, 자동 청구서 생성 등에 적용할 수 있습니다.

다음으로는 **차트 범례에 백분율 표시**, 차트 색상 커스터마이징, Word 문서를 PDF로 변환하여 배포하기 등 관련 주제를 탐색해 보세요. 동일한 `InsertChart` 메서드를 사용해 바 차트, 라인 차트 등 다양한 차트 유형을 시도해 자동화 역량을 확장해 보시기 바랍니다.

Happy charting!


## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 다룬 기술을 기반으로 하는 밀접한 주제들을 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 제공하여 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용할 수 있도록 돕습니다.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}