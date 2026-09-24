---
category: general
date: 2026-09-24
description: Aspose.Words for Java를 사용하여 DOCX에 파이 차트 워드를 삽입합니다. 구멍 크기 설정, 파이 조각 폭발,
  파이 차트 조각 강조, 그리고 손쉽게 DOCX 차트를 만드는 방법을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart word
- set hole size
- explode pie slice
- highlight pie chart slice
- create docx chart
language: ko
lastmod: 2026-09-24
og_description: Aspose.Words for Java를 사용하여 DOCX에 파이 차트를 삽입합니다. 구멍 크기 설정, 파이 조각 분리,
  파이 차트 조각 강조 및 몇 분 안에 DOCX 차트를 만들 수 있습니다.
og_image_alt: Screenshot of a Word document displaying a formatted pie chart created
  with Java
og_title: Java에서 파이 차트 삽입 – 단계별 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  headline: Insert pie chart word in Java – complete guide
  type: TechArticle
- description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  name: Insert pie chart word in Java – complete guide
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well) * Aspose.Words
      for Java library (version 23.9 or newer) * An IDE or build tool (Maven/Gradle)
      that can resolve the Aspose.Words dependency'
  - name: Why this matters
    text: '`Document` represents the whole Word file, while `DocumentBuilder` is the
      high‑level API that lets you insert paragraphs, tables, and charts without dealing
      with low‑level XML. Starting with a clean document ensures that the chart you
      add is the only content, which is perfect for learning or for gen'
  - name: Practical tip
    text: If you later decide to switch to a doughnut chart, simply change the `holeSize`
      value to a percentage (e.g., `30`). The same API works for both chart types.
  - name: Why explode?
    text: An exploded slice draws the reader’s eye to the most important data point—perfect
      for dashboards or executive summaries. The value `20` means 20 % of the radius;
      you can adjust it between `0` (no explosion) and `100` (fully detached).
  - name: Expert note
    text: Changing the fill color of a specific slice requires accessing the `DataPoint`
      object. If you have multiple series, iterate through `series.getDataPoints()`
      and apply styles conditionally.
  - name: Pro tip
    text: Always call `setHoleSize(0)` **after** `insertChart`. If you set it before
      insertion, Aspose.Words will revert to the default doughnut size once the chart
      is created.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart formatting
title: Java에서 파이 차트 삽입 – 완전 가이드
url: /ko/java/using-document-elements/insert-pie-chart-word-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java에서 파이 차트 단어 삽입 – 완전 가이드

DOCX 파일에 **파이 차트 단어 삽입**이 필요하다면, 이 튜토리얼에서는 Aspose.Words for Java를 사용하여 정확히 수행하는 방법을 보여줍니다. 문서 생성부터 차트 조정까지 전체 워크플로우를 확인할 수 있으며, 슬라이스를 폭발시키고, 구멍 크기를 0으로 설정하고, 슬라이스를 강조하는 방법을 다룹니다.

Word 문서에서 차트를 다루는 것은 일반 텍스트 처리와 별개의 작업처럼 느껴질 수 있지만, Aspose.Words는 두 작업을 통합합니다. 아래 단계에서는 Microsoft Word, Google Docs 또는 기타 DOCX‑호환 뷰어에서 열 수 있는 **docx 차트 생성** 파일을 만드는 방법도 배울 수 있습니다.

## 달성 목표

* **파이 차트 단어 삽입**을 빈 문서에 삽입  
* **구멍 크기 설정**으로 차트를 전체 파이(도넛 없음)로 전환  
* **파이 슬라이스 폭발**로 특정 구간에 주목  
* **파이 차트 슬라이스 강조**를 사용자 지정 형식으로  
* **docx 차트 생성**을 통해 공유하거나 추가 편집 가능  

### 사전 요구 사항

* Java 17 이상 (코드는 Java 8에서도 컴파일 가능)  
* Aspose.Words for Java 라이브러리 (버전 23.9 이상)  
* Aspose.Words 의존성을 해결할 수 있는 IDE 또는 빌드 도구(Maven/Gradle)  

```xml
<!-- Example Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

---

## Aspose.Words를 사용하여 DOCX에 파이 차트 단어 삽입하는 방법

첫 번째 단계는 새 빈 문서를 만들고 `DocumentBuilder`를 얻는 것입니다. 빌더를 사용하면 문서의 콘텐츠 스트림에 직접 접근할 수 있어 **파이 차트 단어 삽입**이 간단해집니다.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

### 왜 중요한가
`Document`는 전체 Word 파일을 나타내고, `DocumentBuilder`는 저수준 XML을 다루지 않고도 단락, 표, 차트를 삽입할 수 있는 고수준 API입니다. 깨끗한 문서에서 시작하면 추가하는 차트가 유일한 콘텐츠가 되므로 학습이나 템플릿 기반 보고서 생성에 이상적입니다.

## 구멍 크기를 설정하여 전체 파이 만들기

기본적으로 Aspose.Words는 파이 차트를 요청하면 도넛 차트를 생성합니다. 차트를 진정한 원형으로 만들려면 **구멍 크기 설정**을 `0`으로 해야 합니다. 이렇게 하면 내부 구멍이 제거되어 클래식 파이 모양이 됩니다.

```java
        // Step 2: Insert a pie chart with a specific size
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Step 4: Ensure the chart is a full pie (no doughnut hole)
        pieChart.getChart().setHoleSize(0);   // set hole size to zero
```

### 실용적인 팁
나중에 도넛 차트로 전환하고 싶다면 `holeSize` 값을 백분율(예: `30`)로 변경하면 됩니다. 동일한 API가 두 차트 유형 모두에 적용됩니다.

## 파이 슬라이스 폭발로 구간 강조

슬라이스를 폭발시키면 시각적으로 돋보이게 됩니다. **파이 슬라이스 폭발** 작업은 선택한 슬라이스를 차트 반경의 일정 비율만큼 바깥쪽으로 이동시킵니다.

```java
        // Step 3: Explode the first slice to highlight it
        pieChart.getChart().getSeries().get(0).setExplosion(20); // explode pie slice
```

### 왜 폭발시키나요?
폭발된 슬라이스는 독자의 시선을 가장 중요한 데이터 포인트로 끌어당겨 대시보드나 요약 보고서에 적합합니다. 값 `20`은 반경의 20 %를 의미하며, `0`(폭발 없음)과 `100`(완전히 분리) 사이에서 조정할 수 있습니다.

## 사용자 지정 서식으로 파이 차트 슬라이스 강조

폭발 외에도 채우기 색상이나 테두리를 변경하여 **파이 차트 슬라이스 강조**를 할 수 있습니다. 데모 코드는 폭발에 초점을 맞추지만, 다음과 같이 확장할 수 있습니다:

```java
        // Optional: Change fill color of the exploded slice
        ChartSeries series = pieChart.getChart().getSeries().get(0);
        series.getDataPoints().get(0).getFormat().setFillColor(java.awt.Color.RED);
```

### 전문가 팁
특정 슬라이스의 채우기 색상을 변경하려면 `DataPoint` 객체에 접근해야 합니다. 시리즈가 여러 개 있는 경우 `series.getDataPoints()`를 반복하면서 조건에 따라 스타일을 적용하세요.

## 생성된 docx 차트 저장 및 검증

마지막으로 `Document`를 저장하여 **docx 차트 생성**을 완료합니다. 생성된 파일은 Microsoft Word에서 열어 서식이 적용된 파이 차트를 확인할 수 있습니다.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartFormatted.docx");
    }
}
```

#### 예상 출력
`PieChartFormatted.docx`를 열면 단일 파이 차트가 표시됩니다:

* 차트가 400 × 300 pt 영역을 차지합니다.  
* 구멍 크기가 `0`이므로 차트는 전체 파이입니다.  
* 첫 번째 슬라이스가 20 % 폭발되어 빨간색으로 표시됩니다(옵션 서식을 추가한 경우).  

이제 **docx 차트 생성**을 통해 배포하거나 이메일에 삽입하거나 프로그래밍으로 추가 편집할 수 있는 차트를 갖게 되었습니다.

## 일반적인 변형 및 엣지 케이스

| 시나리오 | 코드 적용 방법 |
|----------|----------------------|
| **다중 시리즈** | `pieChart.getChart().getSeries()`를 반복하고 시리즈별로 `Explosion` 또는 `FillColor`를 설정합니다. |
| **동적 데이터** | 차트를 생성하기 전에 데이터베이스 또는 CSV에서 값을 가져와 시리즈에 채워 `setExplosion`을 호출합니다. |
| **다른 차트 크기** | `insertChart(ChartType.PIE, width, height)`의 너비/높이 인수를 변경합니다. |
| **PDF로 내보내기** | DOCX 저장 후 `doc.save("output.pdf")`를 호출하여 동일 차트의 PDF 버전을 생성합니다. |
| **현지화** | 라벨에 로케일별 숫자 형식을 적용하려면 `DocumentBuilder.insertChart`를 사용합니다. |

### 전문가 팁
`setHoleSize(0)`은 항상 `insertChart` **후에** 호출하세요. 삽입 전에 설정하면 차트가 생성될 때 Aspose.Words가 기본 도넛 크기로 되돌립니다.

## 요약

이제 Java를 사용해 Word 문서에 **파이 차트 단어 삽입**하는 방법, 전체 파이 모양을 위한 **구멍 크기 설정**, 주목을 끌기 위한 **파이 슬라이스 폭발**, 사용자 지정 색상으로 **파이 차트 슬라이스 강조**하는 방법을 알게 되었습니다. 전체 예제는 배포 준비가 된 **docx 차트 생성** 파일을 만드는 방법도 보여줍니다.

## 다음 단계

* `ChartType`을 사용해 다른 차트 유형(`BAR`, `LINE`, `SCATTER`)을 탐색하세요.  
* 차트 생성과 메일 병합을 결합해 개인화된 보고서를 만들 수 있습니다.  
* 생성된 DOCX를 요청 시 파일을 반환하는 웹 서비스에 통합하세요.  

문제가 발생하면 호환 가능한 Aspose.Words 버전을 사용하고 출력 디렉터리가 존재하며 쓰기 가능한지 확인하세요.

코딩 즐겁게 하세요!

## 다음에 배워야 할 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 단계별 설명과 함께 완전한 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Aspose.Words for Java를 사용한 열 차트 만들기](/words/english/java/document-conversion-and-export/using-charts/)
- [Word 차트 API 사용하기](/words/english/net/programming-with-charts/)
- [.NET용 Aspose.Words를 사용한 워드에 버블 차트 삽입](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}