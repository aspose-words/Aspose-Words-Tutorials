---
category: general
date: 2026-07-29
description: Aspose.Words for Java를 사용하여 파이 차트를 삽입하고, 도넛 차트 생성, 파이 차트 서식 지정, Word
  차트 서식 지정 및 차트 크기 사용자 지정 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- generate doughnut chart
- format pie chart
- format chart word
- customize chart size
language: ko
lastmod: 2026-07-29
og_description: Aspose.Words for Java를 사용해 파이 차트를 삽입하고 도넛 차트 생성, 파이 차트 서식 지정, 차트 서식
  지정(Word), 차트 크기 맞춤을 빠르게 배워 전문 문서를 작성하세요.
og_image_alt: Screenshot showing a Word document with an inserted pie chart created
  by Aspose.Words Java API
og_title: Java에서 파이 차트 삽입 – Aspose.Words 완전 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Insert pie chart using Aspose.Words for Java and learn how to generate
    doughnut chart, format pie chart, format chart Word, and customize chart size.
  headline: Insert pie chart in Java with Aspose.Words – Full Guide
  type: TechArticle
- questions:
  - answer: The evaluation version works fine for testing, but it adds a watermark.
      Drop your `aspose.words.lic` file in the classpath for a clean output.
    question: Do I need a license?
  - answer: 'Absolutely. Add the following dependency to your `pom.xml`:'
    question: Can I use this with Maven?
  - answer: Loop over `pieChart.getSeries()` and apply `setExplosion`, `setFillColor`,
      or other formatting per series. That’s the way to **format pie chart** for multi‑dimensional
      data.
    question: What if I have more than one series?
  - answer: Yes—once saved, you can open the document and manually adjust colors,
      fonts, or even convert the pie to a bar chart if you need to.
    question: Is the chart editable in Word after generation?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Chart
- Document Generation
- Word Automation
title: Aspose.Words를 사용한 Java에서 파이 차트 삽입 – 전체 가이드
url: /ko/java/using-document-elements/insert-pie-chart-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insert pie chart in Java with Aspose.Words – Complete Guide

Java 코드에서 Word 문서에 **insert pie chart**를 삽입하는 방법이 궁금하셨나요? 여러분만 그런 것이 아닙니다—데이터를 빠르게 프로그래밍 방식으로 시각화해야 할 때 많은 개발자들이 이 문제에 부딪힙니다. 좋은 소식은? Aspose.Words for Java를 사용하면 몇 줄만으로도 가능하고, 동시에 **generate doughnut chart**, **format pie chart**, **format chart Word**, **customize chart size** 등을 통해 브랜드에 맞게 차트를 맞춤 설정할 수 있습니다.

이 튜토리얼에서는 빈 문서를 만든 뒤 파이 차트를 삽입하고, 몇 가지 시각적 속성을 조정한 뒤 파일을 저장하는 실제 예제를 단계별로 살펴봅니다. 끝까지 따라오시면 차트 자동화가 필요한 모든 Java 프로젝트에 붙여넣을 수 있는 재사용 가능한 코드 조각을 얻게 됩니다. 추가 라이브러리 없이, Office interop을 수동으로 다루지 않아도 되며, 깔끔하게 컴파일된 Java만으로 구현됩니다.

## What You’ll Need

- **Java 17** (또는 최신 JDK; API는 이전 버전과도 호환됩니다)
- **Aspose.Words for Java** 22.12 이상 – Maven 아티팩트나 Aspose 사이트에서 제공되는 .jar 파일을 다운로드하세요.
- 간단한 IDE (IntelliJ IDEA, Eclipse, VS Code 등) – `main` 메서드를 실행할 수 있는 환경이면 충분합니다.
- 선택 사항: 평가판 워터마크를 제거하고 싶다면 라이선스 파일을 준비하세요.

위 항목들을 준비했으면 바로 코드로 넘어갑시다.

## Step 1: Insert pie chart with Aspose.Words

첫 번째 단계는 **insert pie chart**를 새 문서에 삽입하는 것입니다. 이 단계가 모든 작업의 기반이 되며, 차트 객체를 통해 시리즈, 데이터 포인트 및 시각적 조정을 할 수 있게 됩니다.

```java
import com.aspose.words.*;

public class PieChartFormatting {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with a specific size (500x400 points)
        Chart pieChart = builder.insertChart(ChartType.PIE, 500, 400);
```

> **Why this matters:** `DocumentBuilder.insertChart`는 차트를 생성할 뿐만 아니라 조작 가능한 `Chart` 객체를 반환합니다. 생성 시 너비와 높이 인수를 지정하면 **customize chart size**를 바로 적용할 수 있어, 나중에 별도로 크기를 조정할 필요가 없습니다.

## Step 2: Generate doughnut chart (optional)

디자인에 가운데 구멍이 필요하다면—전형적인 도넛 차트를 생각해 보세요—Aspose에서는 한 줄로 구현할 수 있습니다. 동일한 `Chart` 인스턴스를 `ChartType.DONUT`으로 전환하고 구멍 크기만 조정하면 됩니다.

```java
        // Optional: Turn the pie into a doughnut by setting the hole size (0‑100%)
        pieChart.getChartData().setHoleSize(30); // 30% hole makes it a doughnut chart
```

> **Tip:** 구멍 크기는 `ChartType.DONUT`에만 적용됩니다. 타입을 `PIE`로 유지하면 해당 호출은 무시되니, 자유롭게 실험해 보세요.

## Step 3: Format pie chart slices

시각적으로 강조하고 싶은 슬라이스가 있다면, 첫 번째 슬라이스를 20포인트만큼 튀어나오게 **format pie chart**할 수 있습니다. 이렇게 하면 가장 중요한 데이터 포인트에 눈길이 집중됩니다.

```java
        // Explode the first slice to emphasize it
        pieChart.getSeries().get(0).setExplosion(20);
```

> **Pro tip:** 여러 시리즈가 있는 경우 `pieChart.getSeries()`를 순회하면서 개별 색상, 테두리, 데이터 레이블 등을 설정할 수 있습니다. 이것이 **format chart Word** 문서에 풍부한 스타일을 적용하는 방법입니다.

## Step 4: Add data to the chart

데이터가 없는 차트는 단순한 장식 형태에 불과합니다. 여기서는 간단한 데이터 세트—예를 들어 분기별 매출 수치—를 입력해 보겠습니다.

```java
        // Populate the chart with sample data
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataLabels().setShowCategoryName(true);
        series.getDataLabels().setShowValue(true);

        // Clear any default points and add our own
        series.getPoints().clear();
        series.getPoints().add(new ChartPoint(30)); // Q1
        series.getPoints().add(new ChartPoint(45)); // Q2
        series.getPoints().add(new ChartPoint(15)); // Q3
        series.getPoints().add(new ChartPoint(10)); // Q4
```

> **Why we do this:** `ChartPoint` 객체를 명시적으로 추가하면 차트가 비즈니스 로직을 정확히 반영합니다. `setShowCategoryName` 및 `setShowValue` 호출은 **formatting the pie chart**의 일환으로 레이블과 값을 모두 표시하도록 합니다.

## Step 5: Fine‑tune appearance (customize chart size & style)

초기 차원 외에도 범례, 제목, 데이터 레이블에 사용되는 폰트 등을 조정하고 싶을 수 있습니다. 이러한 모든 작업은 **customize chart size**와 전반적인 포맷팅에 포함됩니다.

```java
        // Set a title for the chart
        ChartTitle title = pieChart.getTitle();
        title.setText("Quarterly Sales Distribution");
        title.getFont().setSize(14);
        title.getFont().setBold(true);

        // Move the legend to the right side
        ChartLegend legend = pieChart.getLegend();
        legend.setPosition(LegendPosition.RIGHT);
        legend.getFont().setSize(10);

        // Adjust the overall chart size again if needed
        pieChart.setWidth(600);   // width in points
        pieChart.setHeight(450);  // height in points
```

> **Edge case:** 나중에 문서를 PDF로 내보내면 차트의 벡터 데이터가 포인트 단위로 정의되어 있기 때문에 픽셀 기반이 아닌 선명한 상태를 유지합니다. 이는 **format chart Word**와 후속 포맷에 모두 유리합니다.

## Step 6: Save and view the document

마지막 단계는 `doc.save`를 호출하는 것만큼 간단합니다. 이렇게 하면 Microsoft Word, LibreOffice 또는 OpenXML을 지원하는 모든 뷰어에서 열 수 있는 `.docx` 파일이 생성됩니다.

```java
        // Save the document containing the formatted chart
        doc.save("YOUR_DIRECTORY/PieChart.docx");
    }
}
```

> **Result:** `PieChart.docx`를 열면 폭발된 슬라이스와 제목, 오른쪽에 배치된 범례가 포함된 깔끔한 파이(또는 도넛) 차트를 확인할 수 있습니다—UI를 전혀 건드리지 않고 자동으로 생성된 결과입니다.

### Expected Output

| Element | What you’ll see |
|---------|-----------------|
| Chart type | Pie chart (or doughnut if `holeSize` > 0) |
| Slice explosion | First slice offset by 20 pts |
| Legend | Positioned on the right |
| Title | “Quarterly Sales Distribution” in bold 14 pt |
| Data labels | Category name and value shown on each slice |
| Document | A standard Word `.docx` file ready for sharing |

## Common Questions & Gotchas

- **Do I need a license?**  
  평가판 버전은 테스트에 충분하지만 워터마크가 추가됩니다. 깨끗한 출력이 필요하면 클래스패스에 `aspose.words.lic` 파일을 배치하세요.

- **Can I use this with Maven?**  
  물론입니다. `pom.xml`에 다음 의존성을 추가하면 됩니다:

  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>22.12</version>
  </dependency>
  ```

- **What if I have more than one series?**  
  `pieChart.getSeries()`를 순회하면서 `setExplosion`, `setFillColor` 등 개별 포맷을 적용하면 됩니다. 이것이 다중 시리즈 데이터를 위한 **format pie chart** 방법입니다.

- **Is the chart editable in Word after generation?**  
  네. 저장된 문서를 열면 색상, 폰트 등을 수동으로 조정하거나 필요에 따라 파이를 막대 차트로 변환할 수도 있습니다.

## Wrap‑Up

우리는 Aspose.Words for Java를 사용해 Word 문서에 **insert pie chart**를 삽입하고, **generate doughnut chart**를 만들며, 여러 방법으로 **format pie chart**를 적용하고, **format chart Word** 모범 사례를 다루고, **customize chart size**를 통해 깔끔한 외관을 구현했습니다. 위의 완전한 실행 예제는 어떤 Java 프로젝트에도 바로 삽입할 수 있어 COM interop이나 Office 설치 없이 즉시 차트 자동화를 구현할 수 있습니다.

다음 단계는 무엇일까요? 데이터 소스를 실시간 데이터베이스로 교체하거나, 임계값에 따라 조건부 색상을 적용하거나, 동일한 문서를 PDF로 내보내어 인쇄용 보고서를 만들 수 있습니다. 각각의 단계는 우리가 만든 기반 위에 자연스럽게 쌓아올릴 수 있습니다.

코드 사용 중 문제가 발생하거나 추가 아이디어(예: 누적 막대 차트나 라인 차트)가 있다면 아래 댓글로 알려 주세요. 즐거운 차트 작성 되세요!

## What Should You Learn Next?

다음 튜토리얼들은 이 가이드에서 다룬 기술을 확장하여 추가 API 기능을 마스터하고, 프로젝트에 다양한 구현 방식을 적용할 수 있도록 도와줍니다.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Number Format For Axis In A Chart](/words/english/net/programming-with-charts/number-format-for-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}