---
category: general
date: 2026-10-07
description: Aspose.Words를 사용하여 C#에서 워드 문서를 만들고 파이 차트를 삽입하는 방법을 배웁니다. 이 가이드는 사용자 지정
  차트 레이블이 포함된 워드 파일을 생성하는 방법도 보여줍니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- generate word file
- customize pie chart
- how to add pie chart
language: ko
lastmod: 2026-10-07
og_description: C#에서 워드 문서를 만들고 파이 차트를 삽입하세요. 완전히 맞춤화된 차트 레이블이 포함된 워드 파일을 생성하는 단계별
  가이드를 따라보세요.
og_image_alt: Screenshot of a Word document that contains a customized pie chart created
  with C#
og_title: C#에서 맞춤형 파이 차트가 포함된 Word 문서 만들기
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to create word document and insert pie chart using Aspose.Words
    in C#. The guide also shows how to generate word file with custom chart labels.
  headline: How to create word document with a customized pie chart in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- Chart
title: C#에서 사용자 지정 파이 차트가 포함된 워드 문서 만드는 방법
url: /ko/net/programming-with-charts/how-to-create-word-document-with-a-customized-pie-chart-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#에서 사용자 정의 파이 차트가 포함된 워드 문서 만들기

프로그램matically **워드 문서 만들기**가 필요하다면, 이 튜토리얼에서는 Aspose.Words for .NET을 사용하여 **파이 차트 삽입** 및 데이터 레이블을 사용자 정의하는 방법을 보여줍니다. 또한 완전히 스타일이 적용된 차트를 포함하는 **워드 파일 생성** 방법을 배우게 되며, 프로젝트 설정부터 최종 문서 저장까지 모든 과정을 다룹니다.

이 가이드는 차트를 추가하고, 레이블 위치를 조정하고, 리더 라인을 활성화한 뒤 최종 결과를 `.docx` 파일로 저장하는 데 필요한 각 단계를 안내합니다. Aspose.Words 라이브러리 외에 별도의 도구가 필요 없으며, 전체 소스 코드를 제공하므로 바로 복사·붙여넣기·실행할 수 있습니다.

## 사전 요구 사항

* .NET 6.0 SDK 또는 그 이후 버전 설치  
* 유효한 Aspose.Words for .NET 라이선스(또는 무료 평가 키)  
* Visual Studio 2022 또는 Visual Studio Code와 같은 IDE  

프로젝트에 다음 NuGet 패키지를 추가해야 합니다:

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.Drawing.Charts
```

이 패키지는 아래 예제에서 사용되는 `Document`, `DocumentBuilder` 및 차트 관련 클래스를 제공합니다.

## 워드 문서 만들기 및 차트 추가

첫 번째 단계는 **워드 문서 만들기**와 콘텐츠 삽입을 가능하게 하는 `DocumentBuilder`를 얻는 것입니다. 빌더는 문서 내부에 위치한 커서처럼 작동합니다.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` 객체는 전체 Word 파일을 나타내며, `DocumentBuilder`는 `InsertChart`와 같이 객체를 문서 흐름에 직접 삽입하는 메서드를 제공합니다.

## 문서에 파이 차트 삽입

빌더가 준비되었으므로, 이제 특정 크기의 **파이 차트 삽입**이 가능합니다. 차트는 빌더의 현재 위치에 추가됩니다.

```csharp
        // Step 3: Insert a pie chart with the desired size (400x300 points)
        Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

        // Populate the chart with sample data
        pieChart.Series.Clear();
        ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                                new[] { 25.0, 35.0, 20.0, 20.0 });
```

`InsertChart`는 추가로 조작할 수 있는 `Chart` 객체를 반환합니다. 샘플 데이터는 분기별 매출을 나타내는 네 개의 슬라이스를 생성합니다.

## 파이 차트 데이터 레이블 사용자 정의

차트를 더 읽기 쉽게 만들기 위해, 종종 **파이 차트** 레이블을 사용자 정의해야 합니다—슬라이스 외부에 위치시키고 리더 라인을 표시합니다. 여기서 `ChartDataLabelCollection`이 활용됩니다.

```csharp
        // Step 4: Get the data label collection of the first series
        ChartDataLabelCollection dataLabels = pieChart.Series[0].DataLabels;

        // Step 5: Position the data labels outside each slice
        dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Step 6: Enable leader lines for clearer label connections
        dataLabels.ShowLeaderLines = true;

        // Optional: Show the actual value and percentage
        dataLabels.ShowValue = true;
        dataLabels.ShowPercentage = true;
```

`Position`을 `OutsideEnd`로 설정하면 각 레이블이 슬라이스 가장자리 바깥으로 이동하고, `ShowLeaderLines`는 레이블을 슬라이스에 연결하는 선을 그립니다. 선택적 플래그 `ShowValue`와 `ShowPercentage`는 독자에게 원시 숫자와 상대 비율을 모두 제공합니다.

**팁:** 레이블 폰트를 형식화해야 한다면 `dataLabels.Font`를 사용해 크기, 색상 및 스타일을 설정하세요. 이렇게 하면 차트가 기업 브랜드와 일치합니다.

## 워드 파일 저장 및 생성

차트 구성이 완료되면 `Document` 인스턴스를 디스크에 저장하여 **워드 파일 생성**을 할 수 있습니다. 최신 Word 버전과 최대 호환성을 위해 `.docx` 형식을 선택하세요.

```csharp
        // Step 7: Save the document with the customized chart
        string outputPath = @"C:\Temp\CustomPieChart.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

`CustomPieChart.docx`를 열면 네 개의 슬라이스가 있는 파이 차트를 볼 수 있으며, 각 슬라이스 외부에 레이블이 표시되고 리더 라인으로 연결되며 값과 비율이 모두 표시됩니다.

![C#로 만든 사용자 정의 파이 차트가 포함된 워드 문서 스크린샷](image-placeholder.png)

*이미지는 **워드 문서 만들기** 튜토리얼의 최종 결과를 보여줍니다.*

## 일반적인 변형 및 엣지 케이스

| 시나리오 | 코드 적용 방법 |
|----------|----------------------|
| **다중 시리즈** | `pieChart.Series`에 추가 `ChartSeries` 객체를 추가합니다. 각 시리즈는 독립적인 스타일링을 위해 자체 `DataLabels` 컬렉션을 가질 수 있습니다. |
| **다른 차트 크기** | `InsertChart(width, height)`의 너비와 높이 매개변수를 변경합니다. 값은 포인트 단위이며 (1 pt ≈ 1/72 in) 입니다. |
| **차트 제목** | 설명적인 제목을 추가하려면 `pieChart.Title.Text = "Quarterly Sales"`를 사용합니다. |
| **PDF로 내보내기** | 차트가 완성된 후 `document.Save("Report.pdf", SaveFormat.Pdf);`를 호출합니다. |
| **라이선스 처리** | 라이선스 파일(`Aspose.Words.lic`)을 애플리케이션 폴더에 두고, 문서를 만들기 전에 `new License().SetLicense("Aspose.Words.lic");` 로 로드합니다. |

이러한 변형을 통해 간단한 보고서부터 복잡한 대시보드까지 다양한 실제 시나리오에서 **파이 차트 추가 방법**에 답할 수 있습니다.

## 결론

이제 Aspose.Words for .NET을 사용하여 **워드 문서 만들기**, **파이 차트 삽입**, 그리고 **파이 차트** 레이블을 **사용자 정의**하는 방법을 알게 되었습니다. 전체 예제는 문서 초기화, 차트 추가, 데이터 레이블 위치 조정, 리더 라인 활성화, 그리고 마지막으로 **워드 파일 생성**하여 누구와도 공유할 수 있는 깔끔한 워크플로를 보여줍니다.

다양한 차트 유형(`ChartType.Column`, `ChartType.Line`)을 실험하거나 브랜드에 맞는 사용자 정의 색상 팔레트를 적용하여 이 튜토리얼을 확장해 보세요. 문제가 발생하면 Aspose.Words 문서를 참고하거나 다중 시리즈 및 동적 데이터 소스를 활용한 “파이 차트 추가 방법”과 같은 관련 주제를 살펴보세요.

코딩을 즐기세요, 결과를 공유하거나 댓글에 추가 질문을 자유롭게 남겨 주세요!

## 다음에 배울 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료는 단계별 설명과 함께 완전한 작동 코드 예제를 포함하여 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하도록 돕습니다.

- [워드 문서에 열 차트 삽입](/words/english/net/programming-with-charts/insert-column-chart/)
- [워드 문서에 영역 차트 삽입](/words/english/net/programming-with-charts/insert-area-chart/)
- [워드 문서에 산점도 차트 삽입](/words/english/net/programming-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}