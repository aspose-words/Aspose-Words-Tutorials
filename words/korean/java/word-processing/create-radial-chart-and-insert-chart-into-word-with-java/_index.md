---
category: general
date: 2026-09-27
description: Java에서 방사형 차트를 만들고 차트를 Word에 삽입합니다. 차트 크기 설정, 데이터 시리즈 추가, 빈 Word 문서 생성
  방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- insert chart into word
- create blank word document
- how to set chart size
- add data series chart
language: ko
lastmod: 2026-09-27
og_description: Java에서 방사형 차트를 만든 다음 차트를 Word에 삽입합니다. 이 가이드는 차트 크기 설정, 데이터 시리즈 추가
  및 빈 Word 문서 만들기를 보여줍니다.
og_image_alt: Screenshot showing a radial chart inserted into a Word document created
  with Java
og_title: Java로 방사형 차트를 만들고 차트를 Word에 삽입하기
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create radial chart in Java and insert chart into Word. Learn how to
    set chart size, add data series, and generate a blank Word document.
  headline: Create radial chart and insert chart into Word with Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart generation
title: Java로 방사형 차트를 만들고 Word에 차트를 삽입하기
url: /ko/java/word-processing/create-radial-chart-and-insert-chart-into-word-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create radial chart and insert chart into Word with Java

Java를 사용하여 Word 파일에 **radial chart**를 **생성**하려면, 이 튜토리얼을 따라 하면 됩니다. **Word에 차트 삽입**, 차트 크기 설정, **빈 Word 문서**를 처음부터 만드는 방법을 확인할 수 있습니다.

문서 초기화부터 데이터 시리즈 추가, 최종 `.docx` 저장까지 모든 필수 단계를 차근차근 살펴보겠습니다. 끝까지 진행하면 radial chart가 포함된 완전한 Word 파일을 얻을 수 있으며, **차트 크기 설정** 및 **데이터 시리즈 차트 추가** 방법을 이해하게 됩니다.

## Prerequisites

* Java 17 이상 (코드는 최신 JDK에서 컴파일됩니다)
* Aspose.Words for Java 24.9 이상 – `setShowGraduations` 메서드는 이 버전부터 제공됩니다
* Aspose.Words JAR를 포함할 수 있는 IDE 또는 빌드 도구 (Maven/Gradle)
* Java 문법 및 Maven/Gradle 의존성 관리에 대한 기본 지식

> **Pro tip:** Maven을 사용한다면 `pom.xml`에 다음을 추가하세요:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Step 1: Create a blank Word document

빈 문서는 차트가 배치될 캔버스 역할을 합니다. `Document` 클래스는 전체 `.docx` 파일을 나타냅니다.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank Word document
```

빈 문서를 만들면 기존 내용이 차트 레이아웃에 방해되지 않습니다.

## Step 2: Initialise a DocumentBuilder

`DocumentBuilder`는 문서에 객체, 텍스트 및 기타 요소를 삽입하기 위한 편리한 메서드를 제공합니다.

```java
        // Step 2: Initialise a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

이 빌더는 나중에 **Word에 차트 삽입**에 사용됩니다.

## Step 3: Build the radial chart

Aspose.Words는 다양한 차트 유형을 지원합니다; `ChartType.RADIAL`은 radial (polar) 차트를 생성합니다.

```java
        // Step 3: Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);
```

이 시점에서 차트가 존재하지만 데이터, 크기, 시각 옵션이 없습니다.

## Step 4: Add a data series to the chart

데이터 시리즈가 없는 차트는 비어 있습니다. `add` 메서드는 시리즈 이름과 값 배열을 받습니다.

```java
        // Step 4: Add a data series to the chart
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});
```

`add`를 반복 호출하면 여러 시리즈를 추가할 수 있습니다. 이는 **데이터 시리즈 차트 추가** 요구사항을 충족합니다.

## Step 5: Enable graduations (optional)

Graduations는 가독성을 높여주는 radial 그리드 라인입니다. 이 기능은 24.9 버전부터 제공됩니다.

```java
        // Step 5: Enable graduations on the chart (available from version 24.9)
        chart.getChartObject().setShowGraduations(true);
```

구버전 Aspose.Words를 사용하면 이 라인이 예외를 발생시키므로, 먼저 라이브러리 버전을 확인하세요.

## Step 6: Set the chart’s dimensions

차트 크기를 제어하면 페이지 여백에 잘 맞게 배치할 수 있습니다. 이는 **차트 크기 설정 방법**을 다룹니다.

```java
        // Step 6: Define the chart's dimensions
        chart.setWidth(400);   // width in points (≈5.5 inches)
        chart.setHeight(300);  // height in points (≈4.2 inches)
```

레이아웃 요구에 맞게 너비와 높이 값을 조정하세요. 1 포인트는 약 1/72 인치에 해당합니다.

## Step 7: Insert the chart into the Word document

이제 차트를 배치할 준비가 되었습니다. `DocumentBuilder`의 `insertChart` 메서드가 삽입을 담당합니다.

```java
        // Step 7: Insert the chart into the document
        builder.insertChart(chart);
```

이것이 **Word에 차트 삽입** 작업의 핵심입니다.

## Step 8: Save the document

마지막으로 문서를 디스크에 저장합니다. 파일에는 방금 만든 radial chart가 포함됩니다.

```java
        // Step 8: Save the document with the chart
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

프로그램을 실행하면 프로젝트 작업 디렉터리에 `RadialChart.docx`가 생성됩니다. Microsoft Word에서 파일을 열면 세 개의 데이터 포인트와 보이는 graduations가 포함된 radial chart가 표시됩니다.

### Expected output

* `RadialChart.docx`라는 이름의 Word 파일
* 파일 내부에 400 × 300 포인트 크기의 radial chart가 포함된 단일 페이지
* 차트에 **Series 1**이라는 시리즈가 표시되고 값은 **10, 20, 30**
* 차트 주변에 graduations(방사형 그리드 라인)가 보임

## Common variations and edge cases

| Situation | What to change | Reason |
|-----------|----------------|--------|
| **Multiple series** | `chart.getSeries().add(...)`를 시리즈마다 호출 | 비교 데이터 시각화 가능 |
| **Different chart type** | `ChartType.RADIAL`을 `ChartType.COLUMN`(또는 다른 유형)으로 교체 | 데이터에 가장 적합한 차트 유형 사용 |
| **Custom colors** | `chart.getSeries().get(i).getFormat().getFill().setForeColor(Color)` 사용 | 시각적 브랜딩 향상 |
| **Older Aspose.Words version** | `setShowGraduations` 라인을 생략하거나 라이브러리 업그레이드 | `NoSuchMethodError` 방지 |
| **Saving to a different format** | `doc.save("RadialChart.pdf", SaveFormat.PDF)` 사용 | DOCX 대신 PDF 생성 |

## Full runnable example

아래는 완전하고 독립적인 Java 프로그램 전체 코드입니다. `RadialChartExample.java`라는 파일에 복사하고, Aspose.Words 의존성을 추가한 뒤 실행하세요.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank Word document
        Document doc = new Document();

        // 2. Initialise a DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);

        // 4. Add a data series (add data series chart)
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});

        // 5. Enable graduations (requires Aspose.Words 24.9+)
        chart.getChartObject().setShowGraduations(true);

        // 6. Set chart size (how to set chart size)
        chart.setWidth(400);
        chart.setHeight(300);

        // 7. Insert the chart into the document (insert chart into word)
        builder.insertChart(chart);

        // 8. Save the document (create blank word document with chart)
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

## Conclusion

이제 **radial chart**를 프로그래밍 방식으로 **생성**, **데이터 시리즈 차트 추가**, **차트 크기 설정 방법** 제어, 그리고 **Word에 차트 삽입**을 **빈 Word 문서**에서 시작하는 방법을 알게 되었습니다. 예제는 Aspose.Words for Java 24.9를 사용했지만, 유사한 API를 제공하는 다른 차트 라이브러리에도 동일한 개념을 적용할 수 있습니다.

### Next steps

* 다른 차트 유형(`ChartType.PIE`, `ChartType.LINE` 등) 탐색 – 이는 부수 키워드 **insert chart into word**와 연결됩니다.
* 축 레이블, 범례, 색상을 브랜드 가이드라인에 맞게 커스터마이징.
* 데이터베이스 쿼리 또는 CSV 파일에서 동적으로 차트 생성.
* 결과 `.docx`를 PDF로 변환하여 배포(`doc.save("output.pdf", SaveFormat.PDF)`).

차원, 시리즈 데이터, 스타일 옵션을 자유롭게 실험하여 원하는 정확한 시각화를 만들어 보세요. 즐거운 코딩 되세요!


## What Should You Learn Next?


다음 튜토리얼들은 이 가이드에서 다룬 기술을 기반으로 하며, 밀접하게 관련된 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 제공하여 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용할 수 있도록 돕습니다.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Insert Area Chart Into A Word Document](/words/english/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}