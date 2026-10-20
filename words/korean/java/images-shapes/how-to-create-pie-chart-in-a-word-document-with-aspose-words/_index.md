---
category: general
date: 2026-10-20
description: Aspose.Words를 사용하여 Word 문서에 파이 차트를 만들기 – 색상 설정, 슬라이스 분리 및 Word 문서 저장
  방법을 단계별로 안내하는 가이드.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save word document
- how to create chart
- how to explode slice
- how to set color
language: ko
lastmod: 2026-10-20
og_description: Aspose.Words를 사용하여 Word 문서에 파이 차트를 만들고, 색상 설정, 슬라이스 분리 및 Word 문서 저장을
  하나의 실행 가능한 예제로 배워보세요.
og_image_alt: Screenshot of a Word document containing a customized pie chart with
  an exploded red slice
og_title: Word 문서에 파이 차트 만들기 – 전체 C# 가이드
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create pie chart in a Word document using Aspose.Words – step‑by‑step
    guide that shows how to set color, explode slice, and save Word document.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart automation
title: Aspose.Words를 사용하여 Word 문서에 파이 차트를 만드는 방법
url: /ko/java/images-shapes/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words를 사용하여 Word 문서에 파이 차트 만들기

Word 파일 안에 **파이 차트 만들기**가 필요하다면, 이 가이드는 정확한 방법을 보여줍니다. 사용자 지정 색상 설정, 강조를 위한 슬라이스 분리, 그리고 차트가 삽입된 **Word 문서 저장**까지 확인할 수 있습니다.

프로그래밍으로 차트를 생성하면 Word를 열어 차트를 삽입하고 모양을 조정하는 수동 작업을 없앨 수 있습니다. 이 튜토리얼을 마치면 파이 차트를 만들고, 사용자 지정하고, 결과를 디스크에 저장하는 완전한 C# 콘솔 애플리케이션을 얻게 됩니다.

## 사전 요구 사항

시작하기 전에 다음이 설치되어 있는지 확인하세요:

* .NET 6.0 SDK 이상  
* 유효한 Aspose.Words for .NET 라이선스(또는 무료 평가 키)  
* Visual Studio 2022 또는 VS Code와 같은 IDE  

`Aspose.Words` 외에 추가 NuGet 패키지는 필요하지 않습니다.

## Word 문서에 파이 차트 만들기

첫 번째 단계는 `Document`와 `DocumentBuilder`를 인스턴스화하는 것입니다. 빌더를 사용하면 차트 삽입을 포함한 고수준 Word 기능에 접근할 수 있습니다.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a blank document and a builder.
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Step 2: Insert a 400x300‑point pie chart.
            Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data.
            // Series 0, Category 0‑2 correspond to three slices.
            pieChart.Series[0].DataPoints.Clear();
            pieChart.Series[0].DataPoints.Add(30); // Slice A
            pieChart.Series[0].DataPoints.Add(45); // Slice B
            pieChart.Series[0].DataPoints.Add(25); // Slice C

            // The chart is now part of the document; further customization follows.
```

이 시점에서 문서에는 기본 파이 차트가 이미 포함되어 있습니다. 다음 섹션에서는 **슬라이스 분리 방법**, **색상 설정 방법**, 그리고 **Word 문서 저장 방법**을 설명합니다.

## 강조를 위한 슬라이스 분리 방법

슬라이스를 분리하면 파이 차트의 나머지 부분과 떨어져 보이게 되어 독자의 시선을 끕니다. Aspose.Words API에서는 포인트 단위의 분리 거리를 지정할 수 있습니다.

```csharp
            // Step 3: Explode the first slice (index 0) by 20 points.
            // This moves the slice outward while keeping the rest of the chart intact.
            pieChart.Series[0].SetExplosion(0, 20);
```

왜 슬라이스를 분리할까요? “베스트셀러 제품”과 같이 특정 카테고리를 강조하는 보고서에서는 시각적 구분이 데이터 포인트를 즉시 인식하게 합니다.

## 차트 슬라이스에 색상 지정하기

맞춤 색상은 브랜드 일관성과 가독성을 높여줍니다. 특정 데이터 포인트에 `System.Drawing.Color`를 할당할 수 있습니다.

```csharp
            // Step 4: Apply a red fill to the same slice we just exploded.
            // The Fill property controls the interior color of the slice.
            pieChart.Series[0].DataPoints[0].Fill.ForeColor = Color.Red;
```

미리 정의된 색상에 제한되지 않으며, `Color.FromArgb` 값을 사용해 정확한 색조를 만들 수 있습니다.

## 차트가 포함된 Word 문서 저장하기

차트 모양이 만족스럽다면 파일을 저장하는 과정은 간단합니다. `Document.Save` 메서드는 지정한 형식으로 문서를 저장합니다—여기서는 기본 `.docx` 형식을 사용합니다.

```csharp
            // Step 5: Save the document to the desired location.
            string outputPath = @"C:\Temp\PieChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

프로그램을 실행하면 `PieChart.docx`가 생성됩니다. Microsoft Word에서 파일을 열면 첫 번째 슬라이스가 분리되고 빨간색으로 채워진 파이 차트를 확인할 수 있습니다.

### 예상 결과

* `C:\Temp`에 **PieChart.docx**라는 이름의 Word 파일이 생성됩니다.  
* 문서에는 크기 400 × 300 포인트인 파이 차트가 하나 포함됩니다.  
* 슬라이스 0은 20 포인트만큼 오프셋되고 빨간색으로 채워지며, 다른 슬라이스는 기본 색상을 유지합니다.  

Word에서 차트를 선택하고 슬라이스 속성을 확인하면 분리와 색상을 검증할 수 있습니다.

## 전문가 팁 및 흔히 발생하는 실수

* **전문가 팁:** 차트 제목이나 범례를 변경해야 할 경우, 저장하기 전에 `pieChart.Title.Text`와 `pieChart.Legend` 속성을 사용하세요.  
* **주의점:** 기본 데이터 포인트를 지우지 않으면 원하지 않는 추가 슬라이스가 생길 수 있습니다. 자체 데이터를 추가하기 전에 항상 `Series[0].DataPoints.Clear()`를 호출하세요.  
* **성능 팁:** 큰 문서에서는 여러 빌더를 생성하기보다 단일 `DocumentBuilder` 인스턴스를 재사용하면 메모리 사용량을 줄일 수 있습니다.

## Aspose.Words를 사용한 차트 만들기 (추가 내용)

`InsertChart` 메서드는 파이 차트 외에도 열 차트, 라인 차트, 영역 차트 등 다양한 차트 유형을 지원합니다. 다른 유형으로 전환하려면 `ChartType.Pie`를 원하는 열거값으로 교체하면 됩니다(예: `ChartType.Column`). 슬라이스 분리, 색상 설정 등 나머지 커스터마이징 단계는 동일하게 적용되지만, 모든 차트 유형이 “폭발” 속성을 제공하는 것은 아닙니다.

## 다른 차트 유형에서 슬라이스 분리하기

`SetExplosion` 메서드는 파이 차트 전용입니다. 막대 차트 등에 적용하면 API가 `ArgumentException`을 발생시킵니다. 이런 경우 데이터 레이블이나 호출선을 사용해 특정 막대를 강조하는 방법을 고려하세요.

## 단일 슬라이스가 아닌 시리즈 전체에 색상 지정하기

시리즈의 모든 슬라이스에 동일한 색상을 적용하려면 데이터 포인트를 순회하면 됩니다:

```csharp
foreach (ChartDataPoint point in pieChart.Series[0].DataPoints)
{
    point.Fill.ForeColor = Color.Blue;
}
```

여러 차트에 일관된 색상 스키마가 필요할 때 유용합니다.

## 다른 형식으로 Word 문서 저장하기

Aspose.Words는 PDF, HTML 등 다양한 형식으로 내보낼 수 있습니다. `Save` 메서드의 파일 확장자를 변경하고 필요에 따라 `SaveOptions` 객체를 전달하면 됩니다:

```csharp
document.Save(@"C:\Temp\PieChart.pdf", SaveFormat.Pdf);
```

차트 렌더링 엔진이 자동으로 차트를 대상 형식으로 변환하며 색상 및 폭발 설정을 유지합니다.

## 결론

이제 Word 문서에 **파이 차트 만들기**, **슬라이스 분리** 및 **색상 지정**을 통해 외형을 커스터마이징하고, 차트가 삽입된 **Word 문서 저장**까지 수행하는 방법을 알게 되었습니다. 이 엔드‑투‑엔드 예제는 보고서 자동 생성, 대시보드 구축, 혹은 프로그래밍 방식으로 시각 데이터를 삽입해야 하는 모든 시나리오의 탄탄한 기반이 됩니다.

### 다음 단계

* 다른 차트 유형(`ChartType.Column`, `ChartType.Line`)을 탐색해 보고서 도구 상자를 확장하세요.  
* 하나의 문서에 여러 차트를 결합해 포괄적인 대시보드를 구축하세요.  
* `ChartDataLabel`을 사용해 슬라이스에 백분율이나 값을 직접 표시해 보세요.  

코드를 자신의 데이터 소스에 맞게 조정해 보세요—데이터베이스, API, CSV 파일 등 어디서 가져오든 동일한 Aspose.Words 워크플로우를 적용할 수 있습니다. 차트 작성, 즐겁게 하세요!

### 다음에 배울 내용

다음 튜토리얼은 이 가이드에서 다룬 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스는 단계별 설명과 완전한 코드 예제를 포함하고 있어 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [Explode Pie Chart Slice in C# with Aspose.Words – Full Guide](/words/english/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/)
- [Insert Custom Column Chart in Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/insert-custom-chart/)
- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}