---
category: general
date: 2026-08-07
description: C#에서 파이 차트를 빠르게 만들기. 파이 차트를 삽입하고, 데이터 레이블을 추가하고, 백분율 차트를 표시하며, 차트 데이터
  레이블을 사용자 정의하는 방법을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- show percentage chart
- add data labels pie
- insert pie chart
- customize chart data labels
language: ko
lastmod: 2026-08-07
og_description: C#와 Aspose.Words를 사용하여 워드에 파이 차트를 만들기. 이 튜토리얼에서는 파이 차트를 삽입하고, 데이터
  레이블을 추가하며, 차트 데이터 레이블을 사용자 정의하면서 백분율 차트를 표시하는 방법을 보여줍니다.
og_image_alt: Word document displaying a pie chart with percentage labels outside
  each slice
og_title: C#에서 파이 차트 만들기 – 완전 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  headline: Create pie chart word in C# – step‑by‑step guide
  type: TechArticle
- description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  name: Create pie chart word in C# – step‑by‑step guide
  steps:
  - name: Call `chart.Series.Add()` for each additional series.
    text: Call `chart.Series.Add()` for each additional series.
  - name: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
    text: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
  - name: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
    text: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
  type: HowTo
tags:
- pie chart
- C#
- Aspose.Words
- chart customization
title: C#에서 파이 차트 워드 만들기 – 단계별 가이드
url: /ko/net/programming-with-charts/create-pie-chart-word-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 파이 차트 워드 만들기 – 단계별 가이드

C#에서 **create pie chart word** 문서를 만들어야 한다면, 이 가이드는 완전하고 바로 실행할 수 있는 솔루션을 제공합니다. **insert pie chart**, **add data labels pie**, **show percentage chart**를 수행하고 **customize chart data labels**를 통해 깔끔한 모양을 만드는 방법을 확인할 수 있습니다.

프로그래밍 방식으로 차트를 생성하면 수동 편집을 피할 수 있어, 특히 보고서나 대시보드를 자동으로 생성해야 할 때 유용합니다. 아래 섹션에서는 Aspose.Words for .NET을 사용해 Word 파일에 완전하게 레이블이 지정된 파이 차트를 삽입하는 데 필요한 모든 내용을 배웁니다.

## Prerequisites and setup

시작하기 전에 다음이 설치되어 있는지 확인하세요:

* .NET 6.0 SDK 이상  
* 유효한 Aspose.Words for .NET 라이선스(또는 임시 평가 키)  
* Visual Studio 2022(또는 C#을 지원하는 IDE)  

프로젝트에 Aspose.Words NuGet 패키지를 추가합니다:

```bash
dotnet add package Aspose.Words
```

> **팁:** 많은 차트를 생성할 계획이라면 성능 향상을 위해 **Free‑Form Drawing** 모드(`DocumentBuilder.UseFreeFormDrawing = true`)를 활성화하세요.

## Create pie chart word with Aspose.Words

첫 번째 주요 단계는 빈 Word 문서와 `DocumentBuilder`를 만드는 것입니다. 이 객체가 이후 모든 삽입 작업을 담당합니다.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new blank document and a DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*왜 중요한가*: `Document`는 전체 `.docx` 파일을 나타내고, `DocumentBuilder`는 단락, 표, 차트를 추가하기 위한 유창한 API를 제공합니다. 깨끗한 문서에서 시작하면 숨겨진 서식이 차트 레이아웃에 영향을 주는 것을 방지할 수 있습니다.

## Insert pie chart into the document

이제 원하는 크기의 파이 차트를 배치합니다. `InsertChart` 메서드는 추가 구성을 할 수 있는 `Chart` 객체를 반환합니다.

```csharp
// Step 2: Insert a pie chart of the desired size
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

*왜 중요한가*: `ChartType.Pie` 플래그는 Aspose.Words에 원형 차트를 생성하도록 지시합니다. 너비(`400`)와 높이(`300`)는 포인트 단위로 지정되어 시각적 영역을 정확히 제어할 수 있습니다.

## Populate the chart with data

파이 차트에는 최소 하나의 수치 시리즈가 필요합니다. 여기서는 “Apples”, “Bananas”, “Cherries” 세 카테고리를 추가합니다.

```csharp
// Populate the first series with sample data
chart.Series[0].AddCategory("Apples", 40);
chart.Series[0].AddCategory("Bananas", 35);
chart.Series[0].AddCategory("Cherries", 25);
```

*왜 중요한가*: 각 `AddCategory` 호출은 하나의 슬라이스를 생성합니다. 숫자 값이 슬라이스 크기를 결정하고, 레이블은 데이터 레이블을 켰을 때 표시되는 카테고리 이름이 됩니다.

## Add data labels pie and show percentage chart

차트를 정보 전달형으로 만들기 위해 데이터 레이블을 활성화하고 슬라이스 외부에 배치한 뒤, 카테고리 이름과 백분율을 모두 표시하도록 Aspose.Words에 요청합니다.

```csharp
// Step 3: Access the first series' data label collection
ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;

// Step 4: Position labels outside the slices and show useful information
labels.Position = ChartDataLabelPosition.OutsideEnd; // places label outside each slice
labels.ShowCategoryName = true;                     // displays "Apples", "Bananas", …
labels.ShowPercentage = true;                       // displays "40%" etc.
```

*왜 중요한가*: `Position`을 `OutsideEnd`로 설정하면 슬라이스가 작을 때도 가독성이 향상됩니다. `ShowCategoryName`과 `ShowPercentage`를 켜면 **show percentage chart** 요구 사항을 충족하고 **add data labels pie** 목표를 달성합니다.

## Customize chart data labels further (optional)

폰트를 변경하거나 리더 라인을 추가하고, 레전드를 숨기고 싶을 수 있습니다. 다음 스니펫은 일반적인 사용자 지정 예시를 보여줍니다:

```csharp
// Optional: customize label font and leader lines
labels.Font.Size = 10;
labels.Font.Color = System.Drawing.Color.DarkBlue;
labels.ShowLeaderLines = true;

// Optional: hide the default legend because labels already contain the needed info
chart.HasLegend = false;
```

*왜 중요한가*: 레이블 외관을 맞춤 설정하면 차트가 문서 스타일 가이드와 일치합니다. 레전드를 제거하면 데이터 레이블이 이미 동일한 정보를 제공하므로 시각적 혼잡을 줄일 수 있습니다.

## Save the document with the customized chart

마지막으로 문서를 디스크에 저장합니다. 쓰기 권한이 있는 경로를 선택하세요.

```csharp
// Step 5: Save the document with the customized chart
doc.Save("YOUR_DIRECTORY/ChartWithCustomLabels.docx");
```

`ChartWithCustomLabels.docx`를 Microsoft Word에서 열면 각 슬라이스가 카테고리 이름과 백분율로 레이블이 지정되고, 슬라이스 외부에 배치되며, 사용자 지정 폰트 설정이 적용된 파이 차트를 확인할 수 있습니다.

### Expected output

| 조각   | 값 | 백분율 | Word에 표시되는 레이블 |
|--------|----|--------|------------------------|
| Apples | 40 | 40 %   | Apples – 40 %         |
| Bananas| 35 | 35 %   | Bananas – 35 %        |
| Cherries| 25| 25 %   | Cherries – 25 %       |

차트는 아래 일러스트와 유사하게 표시됩니다:

![Word 문서에 각 슬라이스 외부에 백분율 레이블이 표시된 파이 차트가 포함된 모습](pie-chart-word.png "Create pie chart word example")

*이미지 alt 텍스트는 SEO를 위해 주요 키워드를 포함합니다.*

## Handling multiple series and edge cases

기본 예시는 단일 시리즈를 사용합니다. 이는 파이 차트에 일반적입니다. 여러 시리즈(예: 두 연도 비교)를 표시하려면 다음을 수행해야 합니다:

1. 각 추가 시리즈에 대해 `chart.Series.Add()`를 호출합니다.  
2. 모든 시리즈가 동일한 카테고리를 사용하도록 합니다. 그렇지 않으면 Aspose.Words가 `ArgumentException`을 발생시킵니다.  
3. 필요에 따라 `labels.ShowSeriesName = true`를 설정해 슬라이스를 구분합니다.

```csharp
// Adding a second series (e.g., sales in 2025)
chart.Series.Add("2025");
chart.Series[1].AddCategory("Apples", 45);
chart.Series[1].AddCategory("Bananas", 30);
chart.Series[1].AddCategory("Cherries", 25);
```

여러 시리즈가 존재하면 차트는 자동으로 **clustered pie**(일명 “pie of pies”) 형태로 렌더링됩니다. 레이블이 가독성을 유지하는지 출력 결과를 확인하세요.

## Common pitfalls and how to avoid them

| 문제 | 원인 | 해결 방법 |
|------|------|-----------|
| 레이블이 슬라이스와 겹침 | 차트 영역이 작거나 카테고리가 많음 | 차트 크기(`InsertChart(width, height)`)를 늘리거나 `Position`을 `InsideEnd`로 전환 |
| 백분율이 100 %에 합산되지 않음 | 데이터의 반올림 오류 | `labels.ShowPercentage = true`를 사용하면 Aspose.Words가 자동으로 정규화 |
| Word에서 차트가 빈 상태로 표시 | 라이선스 누락 또는 평가 기간 만료 | 문서를 만들기 전에 유효한 Aspose.Words 라이선스를 로드 |
| 폰트 색상이 Word 테마와 다름 | 코드에서 사용자 지정 폰트 설정 | 사용자 지정 폰트 설정을 제거하거나 Word 테마 색상(`System.Drawing.Color.Black`)에 맞춤 |

## Full source code (runnable)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Load license (optional for evaluation)
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a pie chart
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 3. Add data to the first series
        chart.Series[0].AddCategory("Apples", 40);
        chart.Series[0].AddCategory("Bananas", 35);
        chart.Series[0].AddCategory("Cherries", 25);

        // 4. Configure data labels
        ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;
        labels.Position = ChartDataLabelPosition.OutsideEnd;
        labels.ShowCategoryName = true;
        labels.ShowPercentage = true;

        // Optional: further customization
        labels.Font.Size = 10;
        labels.Font.Color = Color.DarkBlue;
        labels.ShowLeaderLines = true;
        chart.HasLegend = false;

        // 5. Save the document
        doc.Save("ChartWithCustomLabels.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

프로그램을 실행하면 `ChartWithCustomLabels.docx`가 생성되며, 여기에는 **create pie chart word** 예제가 포함되어 튜토리얼에 명시된 모든 요구 사항을 충족합니다.

## Conclusion

이제 Aspose.Words를 사용해 C#에서 **create pie chart word** 문서를 만드는 방법을 알게 되었습니다. 가이드는 파이 차트 삽입, **add data labels pie**, **show percentage chart**, 그리고 **customize chart data labels**를 통해 전문적인 데이터 기반 Word 파일을 만드는 과정을 다루었습니다.

다음 단계로는 기존 단락에 **insert pie chart**를 삽입하거나 **bar**·**line** 차트를 생성하고, 다양한 데이터 세트를 사용해 배치 보고서를 자동화하는 등 관련 주제를 탐색해 보세요. 레이블 위치, 폰트 스타일, 다중 시리즈 구성을 자유롭게 실험해 보고 보고 요구 사항에 맞게 출력물을 맞춤 설정하십시오.

Happy charting!

## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하며, 단계별 설명과 완전한 코드 예제를 포함합니다.

- [차트 데이터 레이블 사용자 지정](/words/english/net/programming-with-charts/chart-data-label/)
- [차트에서 데이터 레이블 기본 옵션 설정](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Word 문서에 열 차트 삽입](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}