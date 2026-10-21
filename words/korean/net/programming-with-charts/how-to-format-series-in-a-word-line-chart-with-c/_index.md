---
category: general
date: 2026-09-21
description: C#를 사용하여 Word 라인 차트의 시리즈를 서식 지정하는 방법. Word 문서를 만들고, 라인 차트를 삽입하며, 사용자
  지정 숫자 형식을 적용하는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format series
- create word document
- insert line chart
- add chart to word
- apply custom number format
language: ko
lastmod: 2026-09-21
og_description: C#를 사용하여 Word 라인 차트의 시리즈를 서식 지정하는 방법. 이 튜토리얼에서는 Word 문서를 만들고, 라인 차트를
  삽입하며, 사용자 지정 숫자 서식을 적용하는 방법을 보여줍니다.
og_image_alt: Screenshot of a Word document showing a line chart with percentage‑formatted
  Y‑axis values
og_title: C#를 사용하여 Word 라인 차트에서 시리즈 서식 지정하는 방법 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to format series in a Word line chart using C#. Learn to create
    a Word document, insert a line chart, and apply a custom number format.
  headline: How to format series in a Word line chart with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart
- Word automation
title: C#로 Word 라인 차트의 시리즈 서식 지정하는 방법
url: /ko/net/programming-with-charts/how-to-format-series-in-a-word-line-chart-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#를 사용하여 Word 라인 차트에서 시리즈 서식 지정하는 방법

Word 라인 차트에서 **시리즈 서식 지정**이 필요하다면, 이 가이드는 완전하고 바로 실행할 수 있는 솔루션을 제공합니다. **Word 문서 만들기**, **라인 차트 삽입**, 그리고 Y‑값에 **사용자 정의 숫자 서식 적용**을 Aspose.Words for .NET으로 어떻게 하는지 확인할 수 있습니다.

차트 객체 모델을 이해하면 Word 자동화가 간단해집니다. 이 튜토리얼을 마치면 데이터 시리즈가 소수점 두 자리 백분율로 표시되는 라인 차트를 포함한 Word 파일을 얻을 수 있습니다.

## 달성 목표

* 프로그래밍 방식으로 빈 `.docx` 파일을 생성합니다.  
* 크기 400 × 300 포인트인 라인 차트를 추가합니다.  
* 차트의 첫 번째 데이터 시리즈에 접근합니다.  
* 포맷 코드 `#,##0.00%`를 적용하여 Y‑값을 백분율로 표시합니다.  

Aspose.Words NuGet 패키지 외에 별도의 도구가 필요하지 않습니다.

## 사전 요구 사항

* .NET 6.0 SDK 이상.  
* Visual Studio 2022 (또는 기타 C# IDE).  
* Aspose.Words for .NET 23.10 이상 – `dotnet add package Aspose.Words` 명령으로 설치합니다.  

Aspose.Words는 플랫폼에 구애받지 않으므로 코드는 Windows, Linux, macOS에서 모두 동작합니다.

## Aspose.Words로 Word 문서 만들기

첫 번째 단계는 `Document` 객체를 인스턴스화하는 것입니다. 이 객체는 메모리 내 전체 Word 파일을 나타냅니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document.
        Document doc = new Document();

        // The document currently has no content.
        // We will add a chart in the next step.
```

*왜 중요한가*: `Document`는 모든 Word 처리 작업의 진입점입니다. 이것 없이는 단락, 표, 차트를 추가할 수 없습니다.

## 문서에 라인 차트 삽입

`DocumentBuilder`는 `Document`에 내용을 기록합니다. `InsertChart`를 호출하면 현재 페이지에 차트 도형이 생성됩니다.

```csharp
        // Step 2: Initialize a DocumentBuilder to construct the document content.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a line chart with the desired size (400 × 300 points).
        Chart chart = builder.InsertChart(ChartType.Line, 400, 300);
```

*왜 중요한가*: `InsertChart`는 `Chart` 객체를 반환하며, 이를 통해 시리즈, 축, 서식 등을 완전히 제어할 수 있습니다. 크기 매개변수는 포인트 단위(1 포인트 = 1/72 인치)로 표현됩니다.

## 첫 번째 데이터 시리즈에 접근하기

각 차트는 하나 이상의 `ChartSeries`를 포함합니다. 첫 번째 시리즈는 인덱스 0에 있습니다.

```csharp
        // Step 4: Access the first data series of the chart.
        ChartSeries series = chart.Series[0];
```

*왜 중요한가*: `ChartSeries` 객체는 라인 차트에서 단일 라인의 Y‑값, X‑값 및 서식 옵션을 보유합니다. 이 객체를 수정하면 데이터의 시각적 표현이 변경됩니다.

## 시리즈에 사용자 정의 숫자 서식 적용하기

`FormatCode` 속성은 숫자 값이 표시되는 방식을 제어합니다. 이를 `#,##0.00%`로 설정하면 Word가 값을 소수점 두 자리 백분율로 처리합니다.

```csharp
        // Step 5: Apply a custom number format to the Y‑values.
        // This displays the numbers as percentages with two decimals.
        series.YValues.FormatCode = "#,##0.00%";

        // Optional: Populate the series with sample data.
        series.YValues.Add(0.15);
        series.YValues.Add(0.30);
        series.YValues.Add(0.45);
        series.YValues.Add(0.60);
```

*왜 중요한가*: 사용자 정의 서식이 없으면 Word는 원시 소수점 숫자(예: `0.15`)를 표시합니다. 포맷 코드는 이를 `15.00%`로 변환하며, 이는 비즈니스 보고서에서 흔히 요구되는 형식입니다.

## 문서 저장 및 결과 확인

```csharp
        // Save the document to the file system.
        string outputPath = "FormattedSeriesLineChart.docx";
        doc.Save(outputPath);
        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

`FormattedSeriesLineChart.docx`를 Microsoft Word에서 열면 Y‑축 레이블이 `15.00%`, `30.00%`, `45.00%`, `60.00%`로 표시된 라인 차트를 볼 수 있습니다. 차트 크기는 `InsertChart`에 제공된 치수와 일치합니다.

### 예상 출력 스크린샷

> *이미지: 백분율 서식이 적용된 Y‑축 값을 가진 라인 차트가 표시된 Word 문서 페이지.*  
> *(Alt text: 백분율 서식이 적용된 Y‑축 값을 가진 라인 차트가 표시된 Word 문서의 스크린샷)*

## 일반적인 변형 및 엣지 케이스

| 상황 | 조정 |
|-----------|------------|
| **다중 시리즈** | `chart.Series`를 반복하면서 각 시리즈에 `FormatCode`를 설정합니다. |
| **다른 차트 유형** | `ChartType.Line`을 `ChartType.Column`, `ChartType.Pie` 등으로 교체합니다. |
| **지역별 구분 기호** | `CultureInfo`를 고려한 포맷 문자열을 사용합니다. 예: 프랑스 로케일의 경우 `"# ##0,00 %"`. |
| **동적 데이터 소스** | 포맷을 적용하기 전에 데이터베이스 또는 CSV 파일에서 `series.YValues`를 채웁니다. |

**팁:** Y‑값을 추가한 **후에** 항상 서식을 적용하세요. 먼저 서식을 변경하고 값을 추가해도 동작하지만, 나중에 적용하면 최종 데이터 세트에 서식이 보장됩니다.

## 요약

이제 C#를 사용하여 Word 라인 차트에서 **시리즈 서식 지정** 방법을 알게 되었습니다. 튜토리얼에서 다룬 내용:

* Word 문서 만들기 (`create word document`).  
* 라인 차트 삽입 (`insert line chart`, `add chart to word`).  
* 차트의 첫 번째 시리즈에 접근하기.  
* 백분율 표시를 위한 사용자 정의 숫자 서식 (`apply custom number format`) 적용하기.

## 다음 단계

* 다른 `ChartType` 값을 실험하여 다양한 시각화가 어떻게 동작하는지 확인합니다.  
* `chart.Title`, `chart.AxisX.Title`, `chart.AxisY.Title`을 사용해 제목, 축 레이블, 범례를 추가합니다.  
* `chart.Save`와 `SaveFormat.Png`를 이용해 차트를 이미지로 내보내 웹 보고서에 활용합니다.

이 패턴을 대시보드, 재무 보고서 또는 프로그래밍 방식 차트가 필요한 모든 문서 생성에 자유롭게 적용하세요. 즐거운 코딩 되세요!

## 다음에 배울 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함하여 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 탐색하도록 돕습니다.

- [Aspose.Words for .NET을 사용하여 Word에서 라인 차트 만들기](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Word 문서에 열 차트 삽입](/words/english/net/programming-with-charts/insert-column-chart/)
- [Word 문서에 영역 차트 삽입 | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}