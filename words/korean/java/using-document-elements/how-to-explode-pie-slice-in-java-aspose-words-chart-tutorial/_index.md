---
category: general
date: 2026-08-07
description: Aspose.Words를 사용하여 Java에서 파이 조각을 분리하는 방법. 파이에 리더 라인을 추가하고, Word 차트를 만들며,
  파이 차트 조각을 사용자 정의하는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode pie slice
- add leader lines to pie
- java create word chart
- customize pie chart slices
language: ko
lastmod: 2026-08-07
og_description: Aspose.Words를 사용하여 Java에서 파이 조각을 분리하는 방법. 이 가이드는 파이에 리더 라인을 추가하고,
  Word 차트를 생성하며, 파이 차트 조각을 맞춤 설정하여 명확한 시각적 효과를 제공하는 방법을 보여줍니다.
og_image_alt: Screenshot of a Word document with an exploded pie chart created using
  Java Aspose.Words
og_title: Java에서 파이 슬라이스를 분리하는 방법 – Aspose.Words 가이드
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to explode pie slice in Java using Aspose.Words. Learn to add leader
    lines to pie, create Word chart, and customize pie chart slices.
  headline: How to explode pie slice in Java – Aspose.Words chart tutorial
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Pie Chart
title: Java에서 파이 조각을 분리하는 방법 – Aspose.Words 차트 튜토리얼
url: /ko/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java에서 파이 슬라이스를 폭발시키는 방법 – Aspose.Words 차트 튜토리얼

Java를 사용하여 Word 문서에서 **파이 슬라이스를 폭발시키는 방법**을 알아야 한다면, 이 튜토리얼이 여러분을 도와드립니다. 또한 **파이 차트에 리더 라인을 추가하는 방법**, **java create word chart** 객체, 그리고 **파이 차트 슬라이스 맞춤 설정**을 보여드려 깔끔한 결과를 얻을 수 있습니다. 이 가이드를 끝까지 읽으면 모든 Java 프로젝트에 삽입할 수 있는 완전한 실행 예제를 얻게 됩니다.

![Java에서 파이 슬라이스를 폭발시키는 방법 – Aspose.Words 차트](/images/pie-chart-exploded.png)

## 사전 요구 사항

* Java Development Kit (JDK) 8 이상.
* Maven 또는 Gradle을 사용한 종속성 관리.
* Aspose.Words for Java 라이선스(무료 평가판은 학습 목적에 사용할 수 있습니다).
* Java 구문 및 객체 지향 개념에 대한 기본적인 이해.

> **Pro tip:** Aspose.Words가 무료 체험을 제공하지만, 라이선스를 구매하면 생성된 문서에서 평가 워터마크가 제거됩니다.

## 이 튜토리얼에서 다루는 내용

* 새 Word 문서를 처음부터 생성하기.  
* `DocumentBuilder`를 사용하여 **pie chart** 삽입하기.  
* 데이터 포인트를 강조하기 위해 **pie slice 폭발시키기**.  
* 라벨링을 명확히 하기 위해 **pie에 leader lines 추가하기**.  
* 색상 및 테두리와 같은 슬라이스 모양 맞춤 설정.  
* 문서를 디스크에 저장하고 결과 확인하기.

---

## Aspose.Words를 사용한 Java에서 파이 슬라이스 폭발 방법

첫 번째 단계는 차트 객체를 설정하고 원하는 슬라이스를 폭발시키는 것입니다. Aspose.Words는 `Shape` 클래스를 통해 차트를 노출하며, 각 슬라이스는 `ChartPoint`입니다. `Explosion` 속성을 설정하면 슬라이스가 얼마나 멀리 이동할지 제어할 수 있습니다.

```java
// Step 1: Create a blank document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a pie chart (400x300 points)
Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
Chart chart = pieChart.getChart();

// Step 3: Explode the first slice (index 0) by 20 points
chart.getSeries().get(0).getPoints().get(0).setExplosion(20);
```

**Why it works:**  
`setExplosion(20)` tells the chart engine to offset the slice by 20 points from the chart’s center. The value is relative; larger numbers create a more dramatic effect. You can explode any slice by changing the index (`get(1)`, `get(2)`, …).

## 라벨을 명확히 하기 위한 파이 차트에 리더 라인 추가

리더 라인은 슬라이스의 라벨을 가장자리와 연결해 주며, 슬라이스가 폭발했을 때나 차트에 작은 섹션이 많이 있을 때 특히 유용합니다. `setLeaderLines(true)` 호출은 전체 시리즈에 대해 이 기능을 활성화합니다.

```java
// Step 4: Enable leader lines for the series
chart.getSeries().get(0).setLeaderLines(true);
```

**Why you need leader lines:**  
When a slice is exploded, the default label may overlap with other elements. Leader lines keep the label readable by drawing a short line from the slice to the text box.

## Java create Word chart – 데이터 시리즈 삽입

데이터가 없는 차트는 별로 도움이 되지 않습니다. 카테고리와 값을 사용해 시리즈를 채워야 합니다. 아래에서는 시장 점유율을 나타내는 세 가지 카테고리를 추가합니다.

```java
// Step 5: Populate the chart with data
ChartSeries series = chart.getSeries().get(0);
series.getDataLabel().setShowCategoryName(true); // show labels
series.getDataLabel().setShowPercentage(true);   // show percentages

// Add categories and values
series.getCategories().add("Product A");
series.getCategories().add("Product B");
series.getCategories().add("Product C");

series.getValues().add(45); // Product A = 45%
series.getValues().add(30); // Product B = 30%
series.getValues().add(25); // Product C = 25%
```

**Explanation:**  
`ChartSeries` holds both the categories (the slice names) and the numeric values. Enabling `ShowCategoryName` and `ShowPercentage` makes the chart self‑explanatory, which pairs nicely with the leader lines we added earlier.

## 폭발 외 파이 차트 슬라이스 맞춤 설정

슬라이스를 폭발시키는 것 외에도 색상, 테두리 등을 조정하거나 슬라이스 자체를 완전히 숨기고 싶을 때가 있습니다. 다음 스니펫은 세 가지 일반적인 맞춤 설정을 보여줍니다.

```java
// Step 6: Change slice colors and borders
ChartPoint pointA = series.getPoints().get(0); // Product A
ChartPoint pointB = series.getPoints().get(1); // Product B
ChartPoint pointC = series.getPoints().get(2); // Product C

// Set custom fill colors
pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50")); // green
pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3")); // blue
pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800")); // orange

// Add a thin border to each slice
for (ChartPoint pt : series.getPoints()) {
    pt.getFormat().getLine().setWeight(0.5);
    pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
}

// Optional: hide a slice (e.g., Product C) without removing data
pointC.setIsHidden(true);
```

**Why customize slices:**  
Custom colors make the chart align with corporate branding, while borders improve readability on printed pages. Hiding a slice is useful when you want to keep the data model intact but temporarily omit a category from visual output.

## 문서를 저장하고 결과 확인

마지막으로 문서를 디스크에 씁니다. 생성된 `.docx` 파일은 Microsoft Word, LibreOffice 또는 해당 형식을 지원하는 모든 뷰어에서 열 수 있습니다.

```java
// Step 7: Save the document
String outputPath = "output/PieChartDemo.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

**Expected output:**  
When you open `PieChartDemo.docx`, you’ll see a pie chart where the first slice (Product A) is exploded outward, leader lines point from each slice to its label, and the slices appear in the custom green, blue, and orange colors. The hidden slice (Product C) will not be visible, but the percentages will still sum to 100 % because the data remains in the chart’s series.

## 전체 실행 가능한 예제

아래는 Aspose.Words 의존성을 프로젝트에 추가한 후 복사·붙여넣기·실행할 수 있는 완전한 프로그램입니다.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a pie chart (400x300 points)
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = pieChart.getChart();

        // Explode the first slice to highlight it
        chart.getSeries().get(0).getPoints().get(0).setExplosion(20);

        // Enable leader lines for clearer labeling
        chart.getSeries().get(0).setLeaderLines(true);

        // Populate the chart with data
        ChartSeries series = chart.getSeries().get(0);
        series.getDataLabel().setShowCategoryName(true);
        series.getDataLabel().setShowPercentage(true);

        series.getCategories().add("Product A");
        series.getCategories().add("Product B");
        series.getCategories().add("Product C");

        series.getValues().add(45);
        series.getValues().add(30);
        series.getValues().add(25);

        // Customize slice colors and borders
        ChartPoint pointA = series.getPoints().get(0);
        ChartPoint pointB = series.getPoints().get(1);
        ChartPoint pointC = series.getPoints().get(2);

        pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50"));
        pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3"));
        pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800"));

        for (ChartPoint pt : series.getPoints()) {
            pt.getFormat().getLine().setWeight(0.5);
            pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
        }

        // Hide the third slice (optional)
        pointC.setIsHidden(true);

        // Save the document
        document.save("output/PieChartDemo.docx");
        System.out.println("Pie chart Word document created successfully.");
    }
}
```

**Dependency (Maven)**  

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Use the latest stable version -->
</dependency>
```

## 다음에 배워야 할 내용은?

다음 튜토리얼들은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스는 단계별 설명과 완전한 코드 예제를 포함하고 있어 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [Aspose.Words for Java를 사용하여 열 차트 만드는 방법](/words/english/java/document-conversion-and-export/using-charts/)
- [Aspose.Words Java로 Word 문서 로드하기: 종합 가이드](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Aspose.Words for Java에서 DocumentBuilder를 사용하여 양식 필드 만들기 및 내용 추가](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}