---
category: general
date: 2026-09-18
description: Java를 사용하여 Word 문서에 방사형 차트를 만드는 방법을 배우고, 차트 데이터 레이블을 추가하며, 전체 코드 예제로
  시리즈 데이터를 삽입하는 방법을 알아보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- add chart data labels
- add series data
- create blank word
- how to insert chart
language: ko
lastmod: 2026-09-18
og_description: Java를 사용해 Word 문서에 방사형 차트를 만들고, 차트 데이터 레이블을 추가하며, 하나의 튜토리얼에서 시리즈 데이터를
  삽입합니다.
og_image_alt: Radial chart displayed inside a generated Word document
og_title: Java로 Word에서 방사형 차트 만들기 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn how to create radial chart in a Word document using Java, add
    chart data labels, and insert series data with a complete code example.
  headline: How to create radial chart in a Word document with Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- Word automation
title: Java로 Word 문서에 방사형 차트 만드는 방법
url: /ko/java/using-document-elements/how-to-create-radial-chart-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 문서에서 Java로 방사형 차트 만들기

Word 문서에 방사형 차트를 만들어야 한다면, 이 가이드는 정확한 단계들을 보여줍니다. 또한 차트 데이터 레이블을 추가하고 시리즈 데이터를 삽입하는 방법을 배워 차트를 프레젠테이션에 바로 사용할 수 있게 됩니다.

프로그램matically 차트를 생성하면 수동 서식 작업을 없애고 보고서 전반에 걸쳐 일관성을 보장합니다. 이 튜토리얼은 기본적인 Java 지식과 최신 버전의 Aspose.Words for Java 라이브러리가 설치되어 있다고 가정합니다.

## 필요 사항

* Java 17 이상  
* Aspose.Words for Java (버전 23.12 이상)  
* Maven/Gradle 의존성을 해결할 수 있는 IDE 또는 빌드 도구  

이러한 전제 조건이 설치되어 있으면 추가 설정 없이 예제를 실행할 수 있습니다.

## Word 문서에서 방사형 차트 만들기

첫 번째 단계는 차트를 삽입할 빈 Word 파일을 만드는 것입니다. 빈 문서는 깨끗한 캔버스를 제공하고 원치 않는 스타일 적용을 방지합니다.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

/* Step 1: Create a new blank Word document */
Document doc = new Document();

/* Step 2: Open a builder to add content */
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document`는 전체 .docx 파일을 나타내며, `DocumentBuilder`는 단락, 표, 차트와 같은 요소를 삽입하는 메서드를 제공합니다.

## 차트 삽입 방법

다음으로 차트 자체를 삽입합니다. `insertChart` 메서드는 차트 객체를 생성하고 빌더의 현재 커서 위치에 배치합니다.

```java
import com.aspose.words.Chart;
import com.aspose.words.ChartType;

/* Step 3: Insert a polar (radial) chart with a width of 400 pt and height of 300 pt */
Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);
```

극좌표 차트는 데이터 포인트를 중심 축을 중심으로 배치하여 순환 정보를 표시하는 데 이상적입니다. 차원의 단위는 포인트(1 pt ≈ 1/72 인치)로 표현됩니다.

## 차트에 시리즈 데이터 추가

시리즈 데이터가 없는 차트는 비어 있습니다. 시리즈를 수동으로 추가하거나 데이터 소스에 바인딩할 수 있습니다. 아래 예제는 세 개의 데이터 포인트를 가진 단일 시리즈를 추가합니다.

```java
import com.aspose.words.ChartSeries;
import java.util.Arrays;

/* Step 4: Add a series and populate it with values */
ChartSeries series = chart.getSeries().add("Sample Series",
        Arrays.asList("Jan", "Feb", "Mar"),
        Arrays.asList(30.0, 45.0, 25.0));
```

`add`는 시리즈 이름, 카테고리 레이블 목록, 그리고 해당 숫자 값 목록을 받습니다. 이 블록을 반복하여 추가 시리즈(`addSeriesData`)를 추가할 수 있습니다.

## 첫 번째 시리즈에 차트 데이터 레이블 추가

데이터 레이블은 포인트 위에 마우스를 올리지 않아도 차트를 읽을 수 있게 합니다. 다음 라인은 첫 번째 시리즈에 값 레이블을 활성화합니다.

```java
/* Step 5: Show the numeric values as data labels */
chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);
```

`showValue`를 `true`로 설정하면 각 포인트의 값이 차트에 직접 표시됩니다. 동일한 `DataLabelFormat` 객체를 통해 카테고리 이름, 백분율 또는 리더 라인도 활성화할 수 있습니다.

## Word 파일 저장

차트 구성이 완료되면 문서를 디스크에 저장합니다. 애플리케이션이 접근할 수 있는 위치를 선택하세요.

```java
/* Step 6: Save the document containing the radial chart */
doc.save("output/RadialChart.docx");
```

`RadialChart.docx` 파일에 이제 데이터 레이블이 포함된 완전한 방사형 차트가 들어 있습니다.

## 전체 작업 예제

아래는 복사하고 컴파일하여 실행할 수 있는 독립형 프로그램입니다. 빈 Word 문서를 만든 뒤 데이터 레이블이 포함된 방사형 차트를 저장하는 전체 워크플로우를 보여줍니다.

```java
import com.aspose.words.*;

import java.util.Arrays;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank Word document
        Document doc = new Document();

        // Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a polar (radial) chart with the desired dimensions
        Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);

        // Add a series and populate it with sample data
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                Arrays.asList("Q1", "Q2", "Q3", "Q4"),
                Arrays.asList(15000.0, 23000.0, 18000.0, 21000.0));

        // Show the numeric values as data labels for the first series
        chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);

        // Save the document containing the chart
        doc.save("output/RadialChart.docx");
    }
}
```

**예상 결과**

Microsoft Word에서 `output/RadialChart.docx`를 열면 *Quarterly Sales*라는 제목의 방사형 차트를 볼 수 있습니다. 각 포인트는 마커 옆에 숫자 값(예: “15000”)을 표시합니다.

## 일반적인 변형 및 엣지 케이스

| 상황 | 권장 변경 사항 |
|-----------|--------------------|
| 다른 차트 유형이 필요함 | `ChartType.POLAR`를 다른 `ChartType` 열거값(예: `ChartType.COLUMN`)으로 교체합니다. |
| 차트가 외부 Excel 범위를 사용해야 함 | 차트를 만든 후 워크북을 로드한 뒤 `chart.setDataRange("Sheet1!A1:B5")`를 사용합니다. |
| 범례를 숨기고 싶음 | `chart.getLegend().setVisible(false);` |
| 문서를 PDF로 저장해야 함 | `doc.save("RadialChart.pdf");`를 호출합니다 – Aspose.Words가 차트를 자동으로 변환합니다. |

이러한 조정은 핵심 로직을 유지하면서 출력물을 특정 요구사항에 맞게 조정합니다.

## 전문가 팁

* **빌더 재사용** – `builder.insertChart`를 반복 호출하여 동일 문서에 여러 차트를 삽입할 수 있습니다.
* **성능** – 많은 차트를 생성할 때는 단일 `DocumentBuilder` 인스턴스를 생성하고 재사용하여 객체 할당 오버헤드를 줄입니다.
* **스타일링** – 차트 외관(색상, 선 두께)은 `Chart` 객체의 `getSeries().get(i).getFormat()` 메서드를 통해 제어됩니다. 기업 브랜딩에 맞게 이러한 설정을 실험해 보세요.

## 결론

이제 Java로 Word 문서에 방사형 차트를 만들고, 시리즈 데이터를 추가하며, 파일을 저장하기 전에 차트 데이터 레이블을 추가하는 방법을 알게 되었습니다. 전체 예제는 추가 시리즈, 사용자 정의 스타일 또는 다른 출력 형식을 처리하도록 확장할 수 있습니다.

외부 데이터 소스에서 **차트 삽입 방법**, 미리 정의된 템플릿으로 **빈 Word 문서 만들기**, 데이터베이스에서 동적으로 **시리즈 데이터 추가**와 같은 관련 주제를 탐색해 보세요. 다양한 차트 유형을 실험하여 데이터 전달에 가장 적합한 시각화를 찾아보세요.

## 다음에 배워야 할 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 단계별 설명과 함께 완전한 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Aspose.Words for Java를 사용하여 열 차트 만들기](/words/english/java/document-conversion-and-export/using-charts/)
- [Java로 Word 문서 만들기 – 그림자 효과가 있는 사각형 도형 추가](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [차트에서 데이터 레이블 기본 옵션 설정](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}