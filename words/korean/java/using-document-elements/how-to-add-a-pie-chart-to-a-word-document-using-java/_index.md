---
category: general
date: 2026-11-15
description: Aspose.Words for Java를 사용하여 Word 문서에 파이 차트를 추가하는 방법을 배웁니다. 도넛 변환, 폭발된
  조각, 전체 코드 샘플이 포함됩니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart to word document
- Aspose.Words chart example
- Java pie chart tutorial
- create doughnut chart in Word
- explode pie slice Java
language: ko
lastmod: 2026-11-15
og_description: Aspose.Words for Java를 사용하여 Word 문서에 파이 차트를 추가합니다. 이 튜토리얼에서는 슬라이스를
  분리하고 차트를 도넛 형태로 변환하는 방법을 보여줍니다.
og_image_alt: Screenshot of a Word document containing an exploded pie chart transformed
  into a doughnut
og_title: Java로 워드 문서에 파이 차트 추가 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  headline: How to add a pie chart to a Word document using Java
  type: TechArticle
- description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  name: How to add a pie chart to a Word document using Java
  steps:
  - name: Expected output
    text: 'Open `final-pie-doughnut.docx` in Microsoft Word:'
  - name: Adding multiple series
    text: 'If you need several series (e.g., stacked doughnut), add them sequentially:'
  - name: Custom colors
    text: 'You can assign a color to each slice via `ChartDataPoint.setFillFormat().setSolidFillColor()`:'
  - name: Working with an existing chart
    text: 'If the document already contains a chart and you only want to modify it,
      locate the chart shape:'
  - name: License handling
    text: 'Aspose.Words requires a license for production use. Place your `Aspose.Words.lic`
      file in the classpath and load it at application start:'
  - name: What to explore next
    text: '* **add bar chart to Word document** – similar steps but use `ChartType.BAR`.
      * **customize chart legends and titles** – use `pieChart.getTitle().setText("...")`
      and `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`. * **export the
      Word document as PDF** – change the `SaveFormat` to `PDF` for'
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Java를 사용하여 Word 문서에 파이 차트를 추가하는 방법
url: /ko/java/using-document-elements/how-to-add-a-pie-chart-to-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 문서에 파이 차트 추가 – 완전 Java 가이드

프로그램matically **Word 문서에 파이 차트를 추가**해야 할 경우, 이 튜토리얼에서는 Aspose.Words for Java를 사용해 정확히 어떻게 수행하는지 보여줍니다. 전체 워크플로우를 확인할 수 있습니다: DOCX 로드, 파이 차트 생성, 첫 번째 슬라이스 폭발(엑스플로드), 그리고 구멍 크기를 설정해 차트를 도넛 형태로 변환하기.

이 가이드는 다중 시리즈 추가, 색상 커스터마이징, 이미 차트가 포함된 문서 처리와 같은 일반적인 변형도 다루므로 자동 보고서 생성이나 동적 프레젠테이션 같은 실제 프로젝트에 코드를 적용할 수 있습니다.

## Prerequisites

시작하기 전에 다음을 준비하세요:

* Java 17 이상 (코드는 JDK 11+에서도 컴파일됩니다)
* Maven 3.6+ 또는 Gradle (의존성 관리용)
* Aspose.Words for Java 라이선스 (무료 체험판으로 테스트 가능)
* Java 문법 및 Maven 프로젝트 구조에 대한 기본 이해

## Step 1: Set up the Maven project and import Aspose.Words

새 Maven 프로젝트를 만들거나 기존 프로젝트에 추가하고 Aspose.Words 의존성을 포함합니다:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-chart-demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest stable at time of writing -->
        </dependency>
    </dependencies>
</project>
```

> **Pro tip:** Gradle을 사용하는 경우 동등한 항목은 `implementation 'com.aspose:aspose-words:24.9'` 입니다.

이 의존성은 차트를 조작하는 데 필요한 `Document`, `Chart`, `ChartType` 클래스를 가져옵니다.

## Step 2: Load the target document

기존 `.docx` 파일에서 시작하거나 새 빈 문서를 만들 수 있습니다. 아래 예제는 `src/main/resources` 폴더에 있는 `input.docx` 템플릿을 로드합니다:

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load the Word document that will receive the chart
        Document doc = new Document("src/main/resources/input.docx");
        // Continue with chart creation...
    }
}
```

파일이 존재하지 않으면, `new Document()`를 파일 이름 없이 호출했을 때 Aspose.Words가 자동으로 새 빈 문서를 생성합니다.

## Step 3: Create a pie chart and insert it into the document

Aspose.Words는 차트를 단락이 나타날 수 있는 어디에든 배치할 수 있는 도형으로 취급합니다. 다음 코드는 **파이 차트**를 만들고, 단일 데이터 시리즈를 추가한 뒤, 첫 번째 단락 뒤에 차트를 삽입합니다:

```java
import com.aspose.words.*;
import java.util.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        Document doc = new Document("src/main/resources/input.docx");

        // Create a new chart of type PIE
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // Prepare data for the series: categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // Add a new series to the chart
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // Insert the chart into the document after the first paragraph
        Paragraph firstParagraph = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);
        firstParagraph.appendChild(pieChart);
        
        // Save the document to verify the result
        doc.save("output/add-pie-chart.docx", SaveFormat.DOCX);
    }
}
```

**Why this step matters:**  
* `ChartType.PIE`는 Aspose.Words에게 전통적인 파이 차트를 렌더링하도록 지시합니다.  
* 카테고리 레이블과 숫자 값을 모두 포함하는 시리즈를 추가하면 슬라이스가 자동으로 채워집니다.  
* `Paragraph`의 자식으로 차트를 삽입하면 문서 흐름이 유지됩니다.

## Step 4: Explode the first slice to highlight it

*폭발된 슬라이스*는 특정 데이터 포인트에 주목하게 합니다. API는 `ChartSeries` 객체에 `setExplode(boolean)` 메서드를 제공합니다. 첫 번째 시리즈(인덱스 0)에 설정하면 첫 번째 슬라이스가 튀어나옵니다:

```java
// Explode the first slice (index 0) of the first series
pieChart.getSeries().get(0).setExplode(true);
```

> **Common question:** *What if I have multiple series?*  
> 두 번째 시리즈와 같이 특정 시리즈를 대상으로 하려면 인덱스를 사용하면 됩니다. 예: `pieChart.getSeries().get(1).setExplode(true)`

## Step 5: Convert the pie chart into a doughnut by setting a hole size

도넛 차트는 중앙이 비어진 파이 차트와 동일합니다. Aspose.Words에서는 차트 반경에 대한 비율로 구멍 크기를 정의할 수 있습니다:

```java
// Turn the pie chart into a doughnut with a 30% hole size
pieChart.setHoleSize(30);
```

`setHoleSize` 메서드는 **0**(일반 파이)부터 **100**(완전 비어 있음)까지의 값을 허용합니다. **30‑40** 정도가 시각적으로 균형 잡힌 도넛을 만듭니다.

## Step 6: Save and verify the result

모든 수정이 끝났으면 문서를 저장합니다. 아래 코드는 파일을 `output` 폴더에 기록합니다:

```java
doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);
```

### Expected output

Microsoft Word에서 `final-pie-doughnut.docx`를 열면:

* 첫 번째 단락이 있던 위치에 도넛 차트가 표시됩니다.
* “Apples” 슬라이스가 폭발되어(다른 슬라이스와 약간 분리) 강조됩니다.
* 차트에는 *Apples*, *Bananas*, *Cherries*, *Dates* 라벨과 제공한 비율이 표시됩니다.

PDF 출력이 필요하면 `SaveFormat`을 `SaveFormat.PDF`로 변경하면 됩니다.

## Handling edge cases and variations

### Adding multiple series

여러 시리즈(예: 스택형 도넛)가 필요하면 순차적으로 추가합니다:

```java
double[] values2022 = {20, 30, 25, 25};
double[] values2023 = {25, 20, 30, 25};

ChartSeries s2022 = pieChart.getSeries().add("2022", categories, values2022);
ChartSeries s2023 = pieChart.getSeries().add("2023", categories, values2023);
```

### Custom colors

각 슬라이스에 색상을 지정하려면 `ChartDataPoint.setFillFormat().setSolidFillColor()`를 사용합니다:

```java
ChartDataPoint point = series.getDataPoints().get(0); // first slice
point.getFillFormat().setSolidFillColor(java.awt.Color.RED);
```

### Working with an existing chart

문서에 이미 차트가 포함되어 있고 이를 수정하려는 경우 차트 도형을 찾아야 합니다:

```java
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
for (Node shapeNode : (Iterable<Node>) shapes) {
    Shape shape = (Shape) shapeNode;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart existingChart = shape.getChart();
        // Apply explode/holeSize changes here
    }
}
```

### License handling

Aspose.Words는 제품 환경에서 라이선스가 필요합니다. `Aspose.Words.lic` 파일을 클래스패스에 두고 애플리케이션 시작 시 로드합니다:

```java
License license = new License();
license.setLicense("Aspose.Words.lic");
```

라이선스를 설정하지 않으면 생성된 문서에 워터마크가 추가됩니다.

## Full, runnable example

아래는 앞서 논의한 모든 단계를 포함한 완전한 Java 클래스입니다. `src/main/java/com/example/AddPieChart.java`에 복사하고 `mvn compile exec:java`를 실행하세요.

```java
package com.example;

import com.aspose.words.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load license (optional for trial)
        // new License().setLicense("Aspose.Words.lic");

        // 1️⃣ Load the base document
        Document doc = new Document("src/main/resources/input.docx");

        // 2️⃣ Create a pie chart
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // 3️⃣ Define categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // 4️⃣ Add a series with the data
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // 5️⃣ Explode the first slice
        pieChart.getSeries().get(0).setExplode(true);

        // 6️⃣ Convert to doughnut (30% hole)
        pieChart.setHoleSize(30);

        // 7️⃣ Insert the chart after the first paragraph
        Paragraph firstPara = (Paragraph) doc.getFirstSection()
                .getBody()
                .getChild(NodeType.PARAGRAPH, 0, true);
        firstPara.appendChild(pieChart);

        // 8️⃣ Save the final document
        doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);

        System.out.println("Chart added successfully. Check output/final-pie-doughnut.docx");
    }
}
```

프로그램을 실행하면 앞서 설명한 도넛 차트가 생성됩니다. `categories`, `values`, `holeSize` 등을 데이터에 맞게 조정하면 됩니다.

## Conclusion

이제 Java와 Aspose.Words를 사용해 **Word 문서에 파이 차트를 추가**하는 방법을 알게 되었습니다. 튜토리얼에서는 문서 로드, 파이 차트 생성, 슬라이스 폭발, 차트를 도넛으로 변환, 다중 시리즈, 사용자 정의 색상, 기존 차트 처리와 같은 일반적인 변형을 다뤘습니다. 이 기반을 바탕으로 자동 보고서 도구를 구축하거나, 동적 프레젠테이션을 생성하거나, Word 파일에 풍부한 시각화를 직접 삽입할 수 있습니다.

### What to explore next

* **add bar chart to Word document** – 유사한 단계이지만 `ChartType.BAR`를 사용합니다.  
* **customize chart legends and titles** – `pieChart.getTitle().setText("...")`와 `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`를 활용합니다.  
* **export the Word document as PDF** – 배포용 파일을 만들려면 `SaveFormat`을 `PDF`로 변경합니다.  
* **populate chart data from a database** – 정적 배열 대신 JDBC 쿼리 결과로 데이터를 채웁니다.

다양한 차트 유형, 데이터 소스, 스타일 옵션을 실험해 보세요. Happy coding!

## What Should You Learn Next?

다음 튜토리얼들은 이 가이드에서 다룬 기술을 확장하는 데 도움이 되는 밀접한 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 제공하여 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용할 수 있도록 돕습니다.

- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide](/words/english/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}