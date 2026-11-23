---
category: general
date: 2026-11-22
description: Java에서 파이 차트를 만들고 차트 크기 설정, 데이터 레이블 추가, 백분율 표시, 첫 번째 조각 회전을 통해 명확한 시각적
  효과를 얻는 방법을 배우세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- set chart size
- show percentages pie chart
- add data labels pie chart
- rotate pie chart slice
language: ko
lastmod: 2026-11-22
og_description: Java에서 파이 차트를 만든 뒤 차트 크기를 설정하고 데이터 레이블에 백분율을 표시하며 첫 번째 슬라이스를 회전시키는
  모든 과정을 하나의 실행 가능한 예제로 구현합니다.
og_image_alt: Screenshot of a created pie chart showing custom size, percentage labels,
  and a rotated first slice
og_title: Java에서 사용자 정의 크기, 레이블 및 회전이 가능한 파이 차트 만들기
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  headline: Create pie chart with custom size, data labels, and rotation in Java
  type: TechArticle
- description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  name: Create pie chart with custom size, data labels, and rotation in Java
  steps:
  - name: Why each step matters
    text: '| Step | Purpose | How it relates to the keywords | |------|---------|--------------------------------|
      | **Insert chart** | **Create pie chart** – the core object that will render
      the visual. | Directly satisfies the *create pie chart* requirement. | | **Set
      dimensions** | The `addChart(..., 400, 3'
  - name: 1. Insert a pie chart and set chart size
    text: '```java IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50,
      400, 300); ```'
  - name: 2. Populate the chart with data
    text: The demo adds three categories and a single series. Replace the hard‑coded
      numbers with data from a database, CSV, or user input as needed.
  - name: 3. Show percentages on each slice
    text: '```java series.getDataLabelFormat().setShowPercentage(true); ```'
  - name: 4. Add detailed data labels
    text: '```java series.getDataLabelFormat().setShowCategoryName(false); series.getDataLabelFormat().setShowLeaderLines(false);
      ```'
  - name: 5. Rotate the first slice
    text: '```java chart.setFirstSliceAngle(45); ```'
  - name: 6. Save and view the result
    text: 'Running the program produces `output/PieChartDemo.pptx`. Open it in PowerPoint
      or any compatible viewer to see the final pie chart:'
  - name: What’s next?
    text: '* Explore other chart types (Bar, Line, Area) using the same `ChartType`
      enum. * Combine multiple charts on a single slide for dashboards. * Export charts
      to PNG or SVG for use in web applications.'
  type: HowTo
tags:
- Java
- charts
- Aspose.Slides
- data‑visualization
title: Java에서 사용자 지정 크기, 데이터 레이블 및 회전이 포함된 파이 차트 만들기
url: /ko/java/getting-started/create-pie-chart-with-custom-size-data-labels-and-rotation-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java에서 사용자 지정 크기, 데이터 레이블 및 회전이 포함된 파이 차트 만들기

Java에서 **create pie chart**가 필요하다면, 이 가이드는 전체 과정을 안내합니다. **set chart size**를 설정하고, **show percentages pie chart**를 활성화하며, **data labels pie chart**를 추가하고, **rotate pie chart slice**를 수행하여 첫 번째 슬라이스가 45도 각도에서 시작하도록 할 수 있습니다.

예제는 **Aspose.Slides for Java**를 사용합니다. 이는 PowerPoint 파일을 조작하기 위해 널리 사용되는 라이브러리입니다. 동일한 개념은 다른 차트 라이브러리에도 적용되며, API 호출을 해당 툴킷의 동등한 호출로 교체하면 됩니다.

## 사전 요구 사항

* Java 17 이상이 설치되어 있음  
* Maven 3.8+ (또는 Gradle) 의존성 관리  
* Java 구문에 대한 기본 이해  
* Aspose.Slides for Java 바이너리에 대한 접근 권한(공식 사이트에서 무료 체험판을 받을 수 있음)

다음 의존성을 `pom.xml`에 추가하세요:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-slides</artifactId>
    <version>24.9</version> <!-- latest version as of November 2026 -->
</dependency>
```

## 파이 차트 만들기 – 전체 예제

다음 프로그램은 사용자 지정 크기, 백분율 데이터 레이블, 회전된 첫 번째 슬라이스를 포함한 파이 차트를 가진 PowerPoint 슬라이드를 생성합니다.

```java
package com.example.piechart;

import com.aspose.slides.*;
import com.aspose.slides.charts.*;

public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a presentation
        Presentation pres = new Presentation();

        // 2️⃣ Add a blank slide
        ISlide slide = pres.getSlides().addEmptySlide(pres.getLayoutSlides().get_Item(0));

        // 3️⃣ Insert a pie chart (create pie chart)
        IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
        // The dimensions above also demonstrate set chart size

        // 4️⃣ Populate the chart with sample data
        IChartDataWorkbook workbook = chart.getChartData().getChartDataWorkbook();

        // Clear the default series & categories
        chart.getChartData().getSeries().clear();
        chart.getChartData().getCategories().clear();

        // Add categories (slices)
        chart.getChartData().getCategories().add(workbook.getCell(0, "A1", "Category A"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A2", "Category B"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A3", "Category C"));

        // Add a series and assign values
        IChartSeries series = chart.getChartData().getSeries().add(
                workbook.getCell(0, "B1", "Series 1"),
                chart.getType());

        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B1", 30));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B2", 45));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B3", 25));

        // 5️⃣ Enable percentage display on data labels (show percentages pie chart)
        series.getDataLabelFormat().setShowPercentage(true);
        series.getDataLabelFormat().setShowCategoryName(false);
        series.getDataLabelFormat().setShowLegendKey(false);
        series.getDataLabelFormat().setShowSeriesName(false);
        series.getDataLabelFormat().setShowValue(false);
        series.getDataLabelFormat().setShowLeaderLines(false);

        // 6️⃣ Rotate the chart so the first slice starts at 45 degrees (rotate pie chart slice)
        chart.setFirstSliceAngle(45);

        // 7️⃣ Save the presentation
        String outPath = "output/PieChartDemo.pptx";
        pres.save(outPath, SaveFormat.Pptx);
        System.out.println("Presentation saved to " + outPath);
    }
}
```

### 각 단계가 중요한 이유

| 단계 | 목적 | 키워드와의 연관성 |
|------|------|-------------------|
| **Insert chart** | **Create pie chart** – 시각화를 렌더링하는 핵심 객체입니다. | 직접적으로 *create pie chart* 요구 사항을 충족합니다. |
| **Set dimensions** | `addChart(..., 400, 300)` 호출은 **set chart size**를 보여줍니다. | 너비(400 px)와 높이(300 px)를 제어합니다. |
| **Show percentages** | `setShowPercentage(true)`는 차트가 각 슬라이스에 **show percentages pie chart**를 표시하도록 합니다. | 사용자는 종종 원시 값 대신 백분율을 필요로 합니다. |
| **Add data labels** | `DataLabelFormat` 설정은 원하는 가시성을 가진 **data labels pie chart**를 추가합니다. | 레이블은 가독성을 향상시키며 사용자 정의가 가능합니다. |
| **Rotate slice** | `setFirstSliceAngle(45)`는 차트를 회전시켜 첫 번째 슬라이스가 45도 각도에서 시작하도록 하며, **rotate pie chart slice**를 만족합니다. | 특정 슬라이스에 대한 시각적 강조를 개선합니다. |

## 단계별 상세 설명

### 1. 파이 차트를 삽입하고 차트 크기 설정

```java
IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
```

*`addChart` 메서드는 차트를 생성하고 동시에 **set chart size**를 400 × 300 포인트로 설정합니다.*  
다른 크기가 필요하면 마지막 두 인자를 조정하세요.

### 2. 차트에 데이터 채우기

데모는 세 개의 카테고리와 하나의 시리즈를 추가합니다. 필요에 따라 하드코딩된 숫자를 데이터베이스, CSV, 또는 사용자 입력에서 가져온 데이터로 교체하세요.

### 3. 각 슬라이스에 백분율 표시

```java
series.getDataLabelFormat().setShowPercentage(true);
```

*`setShowPercentage(true)`를 활성화하면 차트가 **show percentages pie chart**를 자동으로 계산하여 각 슬라이스의 전체 비율을 표시합니다.*

### 4. 상세 데이터 레이블 추가

```java
series.getDataLabelFormat().setShowCategoryName(false);
series.getDataLabelFormat().setShowLeaderLines(false);
```

다른 레이블 옵션(`setShowValue`, `setShowSeriesName` 등)을 토글하여 **add data labels pie chart** 경험을 맞춤 설정할 수 있습니다.

### 5. 첫 번째 슬라이스 회전

```java
chart.setFirstSliceAngle(45);
```

*`setFirstSliceAngle(45)`를 호출하면 **rotate pie chart slice**가 적용되어 첫 번째 세그먼트가 45도 각도에서 시작되어 강조됩니다.*

### 6. 결과 저장 및 보기

프로그램을 실행하면 `output/PieChartDemo.pptx`가 생성됩니다. PowerPoint 또는 호환 가능한 뷰어에서 열어 최종 파이 차트를 확인하세요:

![Create pie chart example](images/pie_chart_example.png){.align-center alt="사용자 지정 크기, 백분율 레이블 및 회전된 첫 번째 슬라이스가 포함된 생성된 파이 차트의 스크린샷"}

위 이미지는 **create pie chart** 결과를 보여주며, 크기, 레이블, 백분율 및 회전이 올바르게 적용되었음을 확인시켜 줍니다.

## 일반적인 변형 및 엣지 케이스

| 상황 | 조정 |
|------|------|
| **Different chart dimensions** | `addChart`에서 너비/높이 매개변수를 변경합니다. |
| **Multiple series** | 추가 `IChartSeries` 객체를 추가합니다; 각 시리즈는 자체 레이블 설정을 가질 수 있습니다. |
| **Custom label format** | `series.getDataLabelFormat().setNumberFormat("0.0%")`를 사용하여 소수점 자리수를 제어합니다. |
| **Rotating to another angle** | `setFirstSliceAngle`에 0‑360 사이의 정수를 전달합니다. |
| **Export as image** | 저장 후 `chart.writeAsSvg(outPath)` 또는 `chart.writeAsPng(outPath)`를 호출하여 래스터 버전으로 내보냅니다. |

> **Pro tip:** 루프에서 많은 차트를 생성할 계획이라면 동일한 `Presentation` 객체를 재사용하고 차트 데이터만 교체하세요. 이렇게 하면 메모리 오버헤드가 감소하고 처리 속도가 빨라집니다.

## 결론

이제 Java에서 **create pie chart**를 만들고, **set chart size**를 설정하며, **show percentages pie chart**를 활성화하고, **add data labels pie chart**를 추가하고, **rotate pie chart slice**를 수행하여 시각적 강조를 강화하는 방법을 알게 되었습니다. 완전하고 실행 가능한 예제는 초기화부터 최종 PowerPoint 파일 저장까지 모든 단계를 보여줍니다.

### 다음 단계는?

* 같은 `ChartType` 열거형을 사용하여 다른 차트 유형(Bar, Line, Area)을 탐색하세요.  
* 대시보드를 위해 하나의 슬라이드에 여러 차트를 결합하세요.  
* 웹 애플리케이션에서 사용하기 위해 차트를 PNG 또는 SVG로 내보내세요.  

색상, 범례, 애니메이션 효과 등을 자유롭게 실험해 보세요—데이터 시각화는 상상력만이 제한입니다. 차트 만들기를 즐기세요!

## 다음에 배워야 할 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료는 단계별 설명과 함께 완전한 작동 코드 예제를 포함하여 추가 API 기능을 숙달하고 프로젝트에서 대체 구현 방식을 탐색하도록 돕습니다.

- [how to insert pie chart in Word – add data label percent](/words/english/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/)
- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Insert Pie Chart in Java – Explode, Rotate & Highlight Slices](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}