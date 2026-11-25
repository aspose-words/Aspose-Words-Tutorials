---
category: general
date: 2026-11-25
description: Java에서 파이 차트를 만드는 방법, 파이 차트를 Word 문서에 삽입하는 방법, 파이 조각을 분리하고 차트 방향을 변경하는
  방법을 명확한 코드 예제로 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- change chart orientation
- explode pie slice
- insert pie chart
- rotate pie chart
language: ko
lastmod: 2026-11-25
og_description: Java에서 파이 차트를 만들고, 파이 차트를 문서에 삽입하며, 파이 조각을 분리하고 단계별 코드로 차트 방향을 변경합니다.
og_image_alt: Screenshot of a created pie chart with an exploded slice and rotated
  orientation
og_title: Java에서 파이 차트 만들기 – 삽입, 조각 분리, 회전
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a pie chart in Java, insert pie chart into a Word
    document, explode pie slice and change chart orientation with clear code examples.
  headline: How to create a pie chart, insert it, and customize orientation in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Charting
title: Java에서 파이 차트를 만들고 삽입하며 방향을 사용자 정의하는 방법
url: /ko/java/document-manipulation/how-to-create-a-pie-chart-insert-it-and-customize-orientatio/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java에서 파이 차트를 만들고, 삽입하고, 방향을 사용자 지정하는 방법

Word 문서 안에 **파이 차트 만들기**가 필요하다면, 이 가이드는 정확한 방법을 보여줍니다. **파이 차트 삽입**, 강조를 위해 슬라이스를 폭발시키기, 그리고 간단한 회전을 통해 **차트 방향 변경**을 확인할 수 있습니다.

이 튜토리얼은 Aspose.Words for Java 라이브러리를 설정하는 것부터 회전되고 폭발된 파이 차트를 표시하는 최종 `.docx` 파일을 생성하는 것까지 필요한 모든 내용을 다룹니다. 외부 문서는 필요 없으며, 단계만 따라하고 코드를 실행하면 됩니다.

## 사전 요구 사항

시작하기 전에 다음이 설치되어 있는지 확인하십시오:

* Java 17 이상이 설치되어 있어야 합니다.
* Maven 또는 Gradle을 사용하여 종속성을 관리합니다.
* 유효한 Aspose.Words for Java 라이선스(또는 무료 평가 모드)를 사용합니다.

Maven(`pom.xml`) 또는 Gradle(`build.gradle`)에 Aspose.Words 종속성을 추가합니다. Maven 예시:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

> **Pro tip:** 라이브러리 버전을 최신 상태로 유지하십시오; 작성 시점 최신 릴리스(24.10)에는 차트 렌더링 버그 수정이 포함되어 있습니다.

## 단계 1: 파이 차트 만들기 및 문서에 삽입하기

첫 번째 단계는 **파이 차트 만들기** 객체를 생성하고 이를 Word 파일에 삽입하는 것입니다. 아래 코드는 간단한 문서를 만들고, 차트 자리표시자를 추가한 뒤, 크기 400 × 300 픽셀인 파이 차트를 삽입합니다.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new Document and DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a pie chart of size 400x300
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Populate the chart with sample data
        chart.getSeries().clear(); // remove default series
        ChartSeries series = chart.getSeries().add("Sales", new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Save the document so far (optional)
        doc.save("Step1_InsertPieChart.docx");
    }
}
```

**Why this matters:** `builder.insertChart`는 문서가 저장될 때 Aspose.Words가 자동으로 OOXML 차트로 변환하는 차트 자리표시자를 생성합니다. `ChartType.PIE` 인자는 라이브러리에게 파이 차트를 렌더링하도록 지시하여 **파이 차트 삽입** 요구 사항을 만족시킵니다.

## 단계 2: 파이 슬라이스 폭발시켜 구간 강조하기

슬라이스를 폭발시키면 특정 데이터 포인트에 주목을 끌 수 있습니다. 다음 라인은 첫 번째 슬라이스(인덱스 0)를 10 포인트만큼 폭발시킵니다:

```java
// 4️⃣ Explode the first slice (index 0) by 10 points
chart.getSeries().get(0).setExplode(0, 10);
```

인덱스를 변경하여 다른 슬라이스를 대상으로 하거나, 폭발 거리를 조정해 더 미묘한 효과를 만들 수 있습니다. 슬라이스를 폭발시키는 것은 Aspose.Words에서 **파이 슬라이스 폭발**하는 표준 방법입니다.

## 단계 3: 차트 회전으로 방향 변경하기

차트를 회전하면 새로운 시각적 관점을 제공합니다. `setRotationAngle`을 사용하여 전체 차트를 시계 방향으로 회전시킵니다(각도는 도 단위).

```java
// 5️⃣ Rotate the entire chart by 45 degrees
chart.setRotationAngle(45);
```

위 호출은 **파이 차트 회전** 및 **차트 방향 변경** 요구 사항을 만족합니다. 0 도부터 360 도 사이의 모든 각도가 허용됩니다.

## 전체 실행 가능한 예제

모든 내용을 종합하면, 파이 차트를 만들고, 슬라이스를 폭발시키며, 차트를 회전시키는 완전하고 독립적인 프로그램이 됩니다. IDE에서 실행하거나 명령줄에서 `java -cp <classpath> PieChartDemo`로 실행하십시오.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300 pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Prepare data series (Sales per quarter)
        chart.getSeries().clear(); // remove default placeholder
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Explode the first slice (Q1) by 10 points
        chart.getSeries().get(0).setExplode(0, 10);

        // Rotate the chart 45 degrees clockwise
        chart.setRotationAngle(45);

        // Save the final document
        doc.save("CreatePieChartDemo.docx");
        System.out.println("Document created successfully: CreatePieChartDemo.docx");
    }
}
```

### 예상 출력

* 작업 디렉터리에 **CreatePieChartDemo.docx** 파일이 생성됩니다.
* Microsoft Word에서 파일을 열면 400 × 300 픽셀 파이 차트가 표시됩니다.
* 첫 번째 슬라이스(Q1)가 10 포인트만큼 바깥쪽으로 이동하여 **파이 슬라이스 폭발** 효과가 나타납니다.
* 전체 차트가 45 도 기울어져 **차트 방향 변경** 및 **파이 차트 회전**을 시연합니다.

## 일반적인 변형 및 예외 상황

| Situation | How to adapt the code |
|-----------|-----------------------|
| **Different chart size** | `insertChart`의 `400, 300` 인자를 원하는 크기로 변경합니다. |
| **Multiple series** | `chart.getSeries()`에 더 많은 `ChartSeries` 객체를 추가합니다. |
| **Explode a different slice** | 원하는 `sliceIndex`와 함께 `setExplode(sliceIndex, distance)`를 사용합니다. |
| **No rotation needed** | `setRotationAngle` 호출을 생략하거나 각도를 `0`으로 설정합니다. |
| **Export to PDF instead of DOCX** | 문서 생성 후 `doc.save("output.pdf")`를 PDF 형식으로 호출합니다. |

> **Watch out for:** 음수 폭발 거리를 사용하면 `IllegalArgumentException`이 발생합니다. 항상 음수가 아닌 값을 제공하십시오.

## 성능 팁

루프에서 많은 차트를 생성해야 할 경우, 단일 `DocumentBuilder`를 재사용하고 각 반복마다 `insertChart`만 호출하십시오. 이렇게 하면 메모리 사용량이 감소하고 처리 속도가 빨라집니다.

## 결론

이제 Aspose.Words for Java를 사용하여 **파이 차트 만들기**, **파이 차트 삽입**, **파이 슬라이스 폭발**, **파이 차트 회전**을 수행하는 방법을 알게 되었습니다. 완전한 예제는 문서 초기화부터 회전되고 폭발된 파이 차트를 시각화하는 파일 저장까지 전체 워크플로우를 보여줍니다.

다음으로 3‑D 효과를 적용해 **차트 방향 변경**을 더 깊이 탐구하거나 **Bar** 또는 **Line**과 같은 다른 차트 유형을 실험해 볼 수 있습니다. 동일한 API 패턴이 적용되므로 이 튜토리얼을 확장하는 것은 간단합니다.

데이터, 슬라이스 인덱스 또는 회전 각도를 자유롭게 수정하여 자체 보고 요구에 맞추고, 커뮤니티와 결과를 공유하십시오!

## 다음에 배울 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스에는 단계별 설명과 함께 완전한 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [How to insert a pie chart into a Word document using Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}