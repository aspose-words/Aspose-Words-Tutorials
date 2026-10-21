---
category: general
date: 2026-09-27
description: Java를 사용해 Word 문서에 파이 차트를 삽입하고, Word에서 파이 차트를 생성하며, 파이 차트에 백분율을 표시하여
  명확한 데이터 인사이트를 얻는 방법을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- create pie chart in word
- show percentages on pie chart
- add chart to word document
- how to add leader lines
language: ko
lastmod: 2026-09-27
og_description: Java를 사용하여 Word 문서에 파이 차트를 삽입하는 방법. 이 가이드는 Word에서 파이 차트를 만드는 방법, 파이
  차트에 백분율을 표시하는 방법, 그리고 리더 라인을 추가하는 방법을 보여줍니다.
og_image_alt: Screenshot of a formatted pie chart inserted into a Word document
og_title: Java를 사용하여 Word 문서에 파이 차트를 삽입하는 방법
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  headline: How to insert a pie chart into a Word document using Java
  type: TechArticle
- description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  name: How to insert a pie chart into a Word document using Java
  steps:
  - name: Expected output
    text: '![Formatted pie chart in Word](/images/pie-formatted.png){: .center-image
      alt="Formatted pie chart inserted into a Word document"}'
  - name: Changing slice values
    text: 'If you need custom data, replace the default series values:'
  - name: Multiple series (donut chart)
    text: While a simple pie chart has one series, Aspose.Words also supports donut
      charts with multiple series. Switch `ChartType.PIE` to `ChartType.DONUT` and
      repeat the series‑configuration steps.
  - name: Exporting to PDF
    text: If your downstream workflow requires PDF, call `doc.save("output/PieFormatted.pdf");`
      after the chart is built. The visual layout remains identical.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word automation
- Chart
title: Java를 사용하여 Word 문서에 파이 차트를 삽입하는 방법
url: /ko/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java를 사용하여 Word 문서에 파이 차트 삽입하는 방법

Word 파일에 **how to insert pie chart**를 삽입해야 한다면, 이 가이드는 전체 과정을 단계별로 안내합니다. **create pie chart in Word**를 수행하고, 각 조각에 백분율을 표시하며, 깔끔한 모양을 위해 리더 라인을 추가하는 방법을 확인할 수 있습니다.

Word 자동화는 종종 무겁게 느껴지지만, Aspose.Words for Java를 사용하면 프로그래밍 방식으로 완전하게 서식이 지정된 문서를 생성할 수 있습니다. 이 튜토리얼을 마치면 스타일이 적용된 파이 차트가 포함된 Word 문서를 생성하는 실행 가능한 Java 코드 스니펫을 얻게 됩니다.

## 사전 요구 사항

- Java 17 이상이 설치되어 있음
- Maven 또는 Gradle을 사용하여 종속성 관리
- Aspose.Words for Java (버전 23.11 이상) 프로젝트에 추가
- Java 구문에 대한 기본적인 이해

차트 API에 대한 사전 경험이 필요하지 않습니다; 아래 단계는 프로젝트 설정부터 최종 출력까지 모든 것을 다룹니다.

## 단계 1: Maven 종속성 설정

`pom.xml`에 Aspose.Words 라이브러리를 추가합니다. 이 단일 종속성을 통해 `Document`, `DocumentBuilder`, 차트 클래스를 사용할 수 있습니다.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.11</version>
</dependency>
```

Gradle을 사용하는 경우, 동일한 내용은 다음과 같습니다:

```groovy
implementation 'com.aspose:aspose-words:23.11'
```

> **Pro tip:** 최신 안정 버전을 사용하여 버그 수정 및 새로운 차트 기능을 활용하세요.

## 단계 2: 새 문서와 빌더 생성

`Document` 객체는 Word 파일을 나타내며, `DocumentBuilder`는 콘텐츠 삽입을 가능하게 합니다. 이는 **add chart to word document**의 기반이 됩니다.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

이제 빌더는 문서 내 어디에든 객체를 배치할 준비가 되었습니다.

## 단계 3: 파이 차트 삽입

Aspose.Words는 여러 차트 유형을 지원합니다; 여기서는 `ChartType.PIE`를 선택합니다. 크기는 포인트 단위로 표시됩니다 (1 포인트 = 1/72 인치).

```java
        // Step 3: Insert a pie chart with a size of 400x300 points
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

이 단계에서 차트는 기본 데이터 시리즈와 자리표시자 값을 포함합니다. 필요에 따라 나중에 해당 값을 교체할 수 있습니다.

## 단계 4: 차트 시리즈 접근

파이 차트는 조각 값을 보유하는 단일 시리즈를 가집니다. 포맷을 적용하기 위해 이를 가져옵니다.

```java
        // Step 4: Get the first (and only) series
        ChartSeries series = chart.getSeries().get(0);
```

## 단계 5: 첫 번째 조각 분리

조각을 분리하면 특정 데이터 포인트에 주목하게 됩니다. 핵심 지표를 강조하고자 할 때 흔히 사용하는 시각적 효과입니다.

```java
        // Step 5: Explode the first slice
        series.setExploded(true);
```

## 단계 6: 각 조각에 백분율 표시

차트에 직접 백분율을 표시하면 데이터 인사이트가 향상됩니다. 이는 **show percentages on pie chart** 요구사항을 충족합니다.

```java
        // Step 6: Show percentages on each slice
        series.setShowPercentage(true);
```

## 단계 7: 레이블 명확성을 위한 리더 라인 추가

리더 라인은 조각 레이블을 해당 섹션에 연결하여 모호성을 없앱니다. 이는 **how to add leader lines**를 만족합니다.

```java
        // Step 7: Add leader lines so labels are clearly connected
        series.setShowLeaderLines(true);
```

## 단계 8: 문서 저장

마지막으로, 문서를 디스크에 저장합니다. 쓰기 권한이 있는 폴더를 선택하면 됩니다.

```java
        // Step 8: Save the document with the formatted pie chart
        doc.save("output/PieFormatted.docx");
    }
}
```

프로그램을 실행하면 `output/PieFormatted.docx`가 생성됩니다. Microsoft Word에서 파일을 열면 다음과 같은 파이 차트를 확인할 수 있습니다:

- 첫 번째 조각이 분리됩니다.
- 각 조각에 백분율 값이 표시됩니다.
- 리더 라인이 백분율에서 해당 조각으로 연결됩니다.

### 예상 출력

![Formatted pie chart in Word](/images/pie-formatted.png){: .center-image alt="Formatted pie chart inserted into a Word document"}

스크린샷(alt 텍스트는 주요 키워드를 사용함)은 최종 모습을 보여줍니다: 보고서, 제안서 또는 대시보드에 사용할 수 있는 깔끔하고 데이터 기반의 파이 차트입니다.

## 일반적인 변형 및 엣지 케이스

### 조각 값 변경

맞춤 데이터를 원한다면, 기본 시리즈 값을 교체하십시오:

```java
double[] values = {30, 45, 25};
String[] categories = {"Apples", "Bananas", "Cherries"};
series.getDataLabelCollection().clear(); // remove placeholder labels

for (int i = 0; i < values.length; i++) {
    series.getData().add(values[i]);
    series.getCategory().add(categories[i]);
}
```

### 다중 시리즈 (도넛 차트)

단순 파이 차트는 하나의 시리즈를 가지지만, Aspose.Words는 다중 시리즈를 갖는 도넛 차트도 지원합니다. `ChartType.PIE`를 `ChartType.DONUT`으로 변경하고 시리즈 구성 단계를 반복하십시오.

### PDF로 내보내기

다운스트림 워크플로에서 PDF가 필요하다면, 차트가 생성된 후 `doc.save("output/PieFormatted.pdf");`를 호출하십시오. 시각적 레이아웃은 동일하게 유지됩니다.

## 전체 소스 코드

아래는 IDE에 복사‑붙여넣기 할 수 있는 완전하고 독립적인 Java 파일입니다.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300‑point pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Access the single series in the pie chart
        ChartSeries series = chart.getSeries().get(0);

        // Explode the first slice for emphasis
        series.setExploded(true);

        // Show percentages on each slice
        series.setShowPercentage(true);

        // Add leader lines for clear label connections
        series.setShowLeaderLines(true);

        // Save the document
        doc.save("output/PieFormatted.docx");
    }
}
```

`mvn compile exec:java -Dexec.mainClass=PieChartExample`(또는 동등한 Gradle 명령)으로 프로그램을 컴파일하고 실행하십시오. 생성된 Word 파일에는 완전하게 서식이 지정된 파이 차트가 포함됩니다.

## 결론

이제 Java를 사용하여 Word 문서에 **how to insert pie chart**를 삽입하고, **create pie chart in Word**를 만들며, **show percentages on pie chart**를 표시하고, 리더 라인이 포함된 **add chart to word document**를 추가하는 방법을 알게 되었습니다. 전체 예제는 각 단계를 시연하고, 코드가 그렇게 작성된 이유를 설명하며, 사용자 정의를 위한 팁을 제공합니다.

다음에 탐색해 볼 수 있습니다:

- 사용자 정의 폰트가 적용된 데이터 레이블 추가 (**show percentages on pie chart** 변형)
- 하나의 문서에 여러 차트 결합 (**add chart to word document** 사용 사례)
- 표와 차트를 함께 사용하여 보고서 자동화

색상, 조각 순서, PDF 내보내기 등을 자유롭게 실험해 보세요. 즐거운 코딩 되세요!

## 다음에 배울 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료는 단계별 설명과 함께 완전한 동작 코드 예제를 포함하여 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하도록 돕습니다.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Create a Line Chart in Word using Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}