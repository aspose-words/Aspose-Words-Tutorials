---
category: general
date: 2026-10-04
description: Word 차트에서 슬라이스를 분리하는 방법, 파이 차트 슬라이스를 분리하고 도넛 차트 크기를 변경하는 방법을 단계별 Java
  예제로 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode slice
- modify chart in word
- explode pie chart slice
- change doughnut chart size
- customize pie chart word
language: ko
lastmod: 2026-10-04
og_description: Word 차트에서 슬라이스를 분리하고 Java로 파이 차트 또는 도넛 차트를 사용자 정의하는 방법. Word에서 차트를
  수정하는 전체 예제를 따라보세요.
og_image_alt: Screenshot showing an exploded pie chart slice inside a Word document
og_title: Word 차트에서 슬라이스를 분리하는 방법 – 전체 Java 가이드
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to explode slice in a Word chart, explode pie chart slice
    and change doughnut chart size with a step‑by‑step Java example.
  headline: How to explode slice in a Word chart and customize its appearance
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Word 차트에서 슬라이스를 분리하고 외관을 맞춤 설정하는 방법
url: /ko/java/document-styling/how-to-explode-slice-in-a-word-chart-and-customize-its-appea/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 차트에서 슬라이스를 폭발시키고 모양을 사용자 지정하는 방법

Word 차트에서 **슬라이스를 폭발시키는 방법**이 필요하다면, 이 가이드는 정확히 어떻게 하는지 보여줍니다. 영업 프레젠테이션이나 재무 보고서를 준비하든, 파이 차트 슬라이스를 폭발시키거나 도넛 구멍을 조정하면 가장 중요한 데이터를 돋보이게 할 수 있습니다. 다음 섹션에서는 Aspose.Words for Java를 사용하여 **Word에서 차트 수정**, **파이 차트 슬라이스 폭발**, **도넛 차트 크기 변경**, 그리고 **파이 차트 워드 문서 사용자 지정** 방법도 배울 수 있습니다.

이 튜토리얼을 마치면 `.docx` 파일을 로드하고, 파이 차트의 첫 번째 슬라이스를 폭발시키며, 도넛 구멍 크기를 변경하고, 결과를 저장하는 완전한 실행 가능한 Java 프로그램을 얻게 됩니다. 외부 스크립트나 수동 편집이 전혀 필요하지 않습니다.

## 필수 조건

- 개발 머신에 Java 17 이상이 설치되어 있어야 합니다.  
- Maven 3.6+ (또는 Gradle)으로 종속성을 관리합니다.  
- Aspose.Words for Java 라이브러리 (무료 평가판으로 개발 가능).  
- 하나 이상의 차트(파이 또는 도넛)를 포함하고 있는 Word 문서(`input.docx`).

## 1단계: 프로젝트에 Aspose.Words 추가

Maven을 사용하는 경우 `pom.xml`에 다음 종속성을 추가합니다:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

Gradle을 사용하는 경우 `build.gradle`에 다음을 넣습니다:

```groovy
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro tip:** 라이브러리 버전을 최신 상태로 유지하세요. 최신 릴리스는 추가 차트 유형을 지원하고 성능을 향상시킵니다.

## 2단계: 차트를 포함한 Word 문서 로드

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // Path to the source .docx file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – this step is required before any chart manipulation.
        Document doc = new Document(inputPath);
```

**왜 중요한가:** 문서를 로드하면 Aspose.Words가 탐색할 수 있는 메모리 내 표현이 생성됩니다. 이 객체가 없으면 차트 노드에 접근할 수 없습니다.

## 3단계: 문서에서 첫 번째 차트 가져오기

```java
        // Locate the first Shape node that contains a chart.
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);

        // Cast the Shape to a Chart object.
        Chart chart = chartShape.getChart();
```

> **Explanation:** `NodeType.SHAPE`은 차트를 포함한 모든 그리기 객체를 포괄합니다. `true` 인자는 Aspose가 재귀적으로 검색하도록 하여 차트가 테이블 안에 중첩돼 있더라도 첫 번째 차트를 찾을 수 있게 합니다.

## 4단계: 파이 차트의 첫 번째 슬라이스 폭발시키기

```java
        // Verify the chart type before exploding.
        if (chart.getChartType() == ChartType.PIE) {
            // Explode the first series (slice) by 20 points.
            chart.getSeries().get(0).setExplosion(20);
        } else {
            System.out.println("The first chart is not a pie chart; explosion skipped.");
        }
```

**How it works:** `setExplosion` 메서드는 슬라이스가 중심에서 얼마나 멀리 이동할지를 결정하는 숫자 값을 받습니다. `20` 값은 차트 레이아웃을 깨뜨리지 않으면서 시각적으로 눈에 띕니다.

## 5단계: 도넛 차트의 도넛 구멍 크기 조정

```java
        // If the chart is a doughnut, change the hole size.
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            // Set the doughnut hole size to 40% of the chart radius.
            chart.setDoughnutHoleSize(40);
        } else {
            System.out.println("The first chart is not a doughnut chart; hole size unchanged.");
        }
```

**Why this helps:** 데이터 포인트가 많을 때 큰 도넛 구멍은 가독성을 높여줍니다. `setDoughnutHoleSize` 메서드는 백분율(0‑100)을 기대합니다.

## 6단계: 수정된 문서 저장

```java
        // Path for the output document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";

        // Save the changes – the file now contains the exploded slice and updated doughnut size.
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

### 예상 출력

- 첫 번째 파이 차트의 첫 번째 슬라이스가 외부로 이동하여 돋보이게 됩니다.  
- 차트가 도넛인 경우, 중앙 구멍이 차트 반경의 40 %까지 확대됩니다.  
- 결과 파일 `PieChart.docx`는 Microsoft Word, LibreOffice 또는 호환 가능한 뷰어에서 열 수 있으며, 프로그래밍 방식으로 적용한 시각적 변화를 확인할 수 있습니다.

## 전체 실행 가능한 예제

아래는 전체 프로그램을 하나의 블록에 넣은 예시입니다. `ChartExploder.java`에 복사하고 파일 경로를 조정한 뒤 `mvn compile exec:java`(또는 IDE 실행 구성)로 실행하세요.

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source document
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Find the first chart shape
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        if (chartShape == null) {
            System.out.println("No chart found in the document.");
            return;
        }

        // 3️⃣ Cast to Chart
        Chart chart = chartShape.getChart();

        // 4️⃣ Explode the first slice if it is a pie chart
        if (chart.getChartType() == ChartType.PIE) {
            chart.getSeries().get(0).setExplosion(20);
            System.out.println("Exploded first slice of the pie chart.");
        }

        // 5️⃣ Change doughnut hole size if it is a doughnut chart
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            chart.setDoughnutHoleSize(40);
            System.out.println("Set doughnut hole size to 40%.");
        }

        // 6️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Modified document saved as " + outputPath);
    }
}
```

이 코드를 실행하면 **Word에서 차트 수정**, **파이 차트 슬라이스 폭발**, 그리고 **도넛 차트 크기 변경**이 자동으로 이루어집니다.

## 일반적인 질문 및 엣지 케이스

| Question | Answer |
|----------|--------|
| *문서에 차트가 여러 개 포함되어 있으면 어떻게 하나요?* | 샘플은 **첫 번째** 차트(`NodeType.SHAPE, 0`)를 대상으로 합니다. 다른 차트를 다루려면 인덱스를 변경하거나 `doc.getChildNodes(NodeType.SHAPE, true)`를 반복하면서 `shape.getChart() != null`인 항목을 필터링하세요. |
| *첫 번째가 아닌 다른 슬라이스도 폭발시킬 수 있나요?* | 가능합니다. 원하는 시리즈에 `chart.getSeries().get(seriesIndex)`로 접근한 뒤 `setExplosion(value)`를 호출하면 됩니다. 인덱스는 0부터 시작합니다. |
| *Word 2007‑2021 파일에서도 작동하나요?* | Aspose.Words는 `.doc`, `.docx`, `.dot`, `.dotx`를 지원합니다. 라이브러리가 파일 형식을 추상화하기 때문에 동일한 코드가 모든 버전에서 동작합니다. |
| *차트가 막대형이나 선형 차트인 경우는요?* | `setExplosion`과 `setDoughnutHoleSize`는 파이형 차트에만 적용됩니다. 차트 유형이 다르면 해당 연산을 안전하게 건너뛰도록 코드가 처리합니다. |
| *Aspose.Words 라이선스가 필요합니까?* | 무료 평가 라이선스는 30일 제한을 없애지만 워터마크가 추가됩니다. 프로덕션에서는 워터마크를 제거하고 전체 기능을 사용하려면 라이선스를 구매하세요. |

## 결론

이제 Aspose.Words for Java를 사용하여 Word 차트에서 **슬라이스를 폭발시키는 방법**, **차트를 수정하는 방법**, 그리고 **도넛 차트 크기를 변경하는 방법**을 알게 되었습니다. 전체 예제는 문서 로드, 차트 찾기, 시각적 조정 적용, 결과 저장까지의 전체 워크플로우를 보여주므로, 이 단계를 어떤 보고서나 문서 생성 파이프라인에도 쉽게 통합할 수 있습니다.

**다음 단계**

- 색상 변경, 데이터 레이블 추가, 차트 유형 전환(`chart.setChartType(ChartType.BAR_CLUSTERED)`) 등 다른 차트 사용자 지정 옵션을 탐색해 보세요.  
- 이 로직을 Aspose.PDF와 결합하여 동일한 보고서의 PDF 버전을 생성하세요.  
- 디렉터리 내 파일을 순회하면서 배치 처리하도록 자동화하세요.

디자인 가이드라인에 맞게 다양한 폭발 값이나 도넛 구멍 비율을 실험해 보세요. 즐거운 코딩 되시길 바랍니다!

## 다음에 배워야 할 내용은?

다음 튜토리얼들은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함하고 있어, 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [Aspose.Words for Java를 사용하여 열 차트 만들기](/words/english/java/document-conversion-and-export/using-charts/)
- [Word 문서에서 차트 축 숨기기](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Word 문서에 버블 차트 삽입](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}