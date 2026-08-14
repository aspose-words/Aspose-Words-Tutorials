---
category: general
date: 2026-08-14
description: Aspose.Words를 사용하여 Java로 Word에서 파이 차트를 만들고, 차트에 시리즈 데이터를 추가하고 파이 차트 조각을
  몇 줄만으로 회전하는 방법을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart in word
- how to add series data to chart
- rotate pie chart slice
- Aspose.Words chart API
- Java document automation
language: ko
lastmod: 2026-08-14
og_description: Aspose.Words를 사용하여 Java로 Word에서 파이 차트를 만들기. 이 튜토리얼에서는 차트에 시리즈 데이터를
  추가하고 파이 차트 조각을 빠르게 회전하는 방법을 보여줍니다.
og_image_alt: Screenshot of a Word document containing a colorful pie chart generated
  by Java code
og_title: Java로 Word에서 파이 차트 만들기 – 완전 코딩 가이드
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  headline: Create pie chart in Word with Java – step-by-step guide
  type: TechArticle
- description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  name: Create pie chart in Word with Java – step-by-step guide
  steps:
  - name: Why use Aspose.Words?
    text: '* **No Microsoft Office required** – the library works on any server or
      CI environment. * **Full .docx fidelity** – the generated chart looks identical
      to one created manually in Word. * **Single‑file dependency** – just add the
      JAR and you’re ready to go.'
  - name: Expected output
    text: '* A file named **PieChart.docx** appears in the `output` folder. * Opening
      the file in Microsoft Word shows a colorful pie chart with three slices (40
      %, 30 %, 30 %). * The chart is rotated 45° clockwise, so the first slice starts
      slightly to the right of the vertical axis.'
  - name: Tips for production use
    text: '* **Reuse the `DocumentBuilder`** – you can insert multiple charts in the
      same document by calling `insertChart` repeatedly. * **Styling** – use `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);`
      to display percentages directly on the chart. * **Performance** – generate the
      chart on'
  - name: What’s next?
    text: '* Explore other chart types (`ChartType.BAR`, `ChartType.LINE`) to broaden
      your automation toolkit. * Combine chart generation with **mail merge** to produce
      personalized reports for each recipient. * Dive into the **Styling API** (`ChartFormat`,
      `DataLabel`, `ChartTitle`) to match your corporate br'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Java로 Word에서 파이 차트 만들기 – 단계별 가이드
url: /ko/java/using-document-elements/create-pie-chart-in-word-with-java-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java로 Word에서 원형 차트 만들기 – 단계별 가이드

프로그래밍 방식으로 **create pie chart in Word**가 필요하다면, 이 가이드는 Java와 Aspose.Words를 사용하여 정확히 어떻게 수행하는지 보여줍니다. 차트를 삽입하고 데이터 포인트를 추가하며 첫 번째 슬라이스를 회전시키는 전체 워크플로우를 배울 수 있습니다.

`.docx` 파일에 차트를 직접 생성하면 수동 복사‑붙여넣기 과정을 없애고 보고서, 청구서, 대시보드를 자동화할 수 있습니다. 진행하면서 **how to add series data to chart**와 **rotate pie chart slice**를 다루어 시각적 강조를 강화합니다.

## Word에서 원형 차트 만들기 – 개요

Aspose.Words for Java는 차트 객체를 Word 문서에 삽입할 수 있는 유연한 `DocumentBuilder` API를 제공합니다. 선택한 차트 유형에 따라 기본 레이아웃이 결정되며, 시리즈, 색상, 각도 등을 사용자 지정하고 단일 메서드 호출로 도넛 형태로 전환할 수도 있습니다.

### Aspose.Words를 사용하는 이유

* **No Microsoft Office required** – 이 라이브러리는 모든 서버 또는 CI 환경에서 작동합니다.  
* **Full .docx fidelity** – 생성된 차트는 Word에서 수동으로 만든 차트와 동일하게 보입니다.  
* **Single‑file dependency** – JAR 파일만 추가하면 바로 사용할 수 있습니다.

## 차트에 시리즈 데이터 추가하기

데이터가 없는 차트는 단순히 자리표시자에 불과합니다. `Chart` 객체는 `Series` 컬렉션을 노출하며, 각 시리즈는 슬라이스(원형 차트) 또는 포인트(선 차트)에 매핑되는 숫자 값 리스트를 보유합니다. 데이터 추가는 간단합니다:

```java
// Add three values to the first (and only) series of the pie chart
chart.getSeries().get(0).add(40); // 40 % of the whole
chart.getSeries().get(0).add(30); // 30 %
chart.getSeries().get(0).add(30); // remaining 30 %
```

**코드 설명:**  
* `chart.getSeries()`는 `List<ChartSeries>`를 반환합니다.  
* `get(0)`은 첫 번째 시리즈를 선택합니다. 원형 차트는 정의상 하나의 시리즈만 포함하기 때문입니다.  
* `add(double)`은 데이터 포인트를 추가합니다. 값은 차트가 렌더링될 때 자동으로 백분율로 변환되어 총합이 100 %가 됩니다.

> **Pro tip:** 데이터 소스에 세 개 이상의 카테고리가 포함된 경우, 동일한 방식으로 값을 계속 추가하세요. Aspose.Words가 자동으로 추가 슬라이스를 생성합니다.

## 원형 차트 슬라이스 회전하기

특정 슬라이스를 특정 각도에서 시작하도록 설정하면 가장 중요한 구간이 보는 사람을 향하도록 할 수 있습니다. `setFirstSliceAngle(double)` 메서드는 전체 차트를 회전시켜 첫 번째 슬라이스의 시작 위치를 효과적으로 이동시킵니다:

```java
// Rotate the chart so that the first slice starts at 45 degrees
chart.setFirstSliceAngle(45);
```

각도는 수직 축을 기준으로 시계 방향으로 도 단위로 측정됩니다. `0`(기본값)으로 설정하면 첫 번째 슬라이스가 상단에 배치됩니다. 값을 조정하여 슬라이스를 강조하거나 디자인 가이드라인에 맞출 수 있습니다.

> **Common question:** *회전이 데이터 순서에 영향을 줍니까?*  
> 아니요. 데이터 순서는 동일하게 유지되며, 시각적인 시작 위치만 변경됩니다.

## 전체 Java 예제

아래는 원형 차트가 포함된 Word 문서를 생성하고, 시리즈 데이터를 추가하며, 슬라이스를 회전시키고 파일을 저장하는 완전한 실행 가능한 프로그램입니다. 필요한 모든 import가 나열되어 있어 코드를 어떤 IDE에도 복사해 넣을 수 있습니다.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartInWord {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a PIE chart with a width of 400 points and a height of 300 points
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Add data points to the first (and only) series
        chart.getSeries().get(0).add(40); // Slice 1
        chart.getSeries().get(0).add(30); // Slice 2
        chart.getSeries().get(0).add(30); // Slice 3

        // 4️⃣ Rotate the start angle so the first slice begins at 45°
        chart.setFirstSliceAngle(45);

        // 5️⃣ (Optional) If you prefer a doughnut chart, uncomment the next line
        // chart.setHoleSize(0.5); // hole size between 0.0 (pie) and 1.0 (empty)

        // 6️⃣ Save the document – adjust the path as needed
        String outPath = "output/PieChart.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### 예상 출력

* `output` 폴더에 **PieChart.docx** 파일이 생성됩니다.  
* Microsoft Word에서 파일을 열면 세 개의 슬라이스(40 %, 30 %, 30 %)가 있는 다채로운 원형 차트가 표시됩니다.  
* 차트가 시계 방향으로 45° 회전되어 첫 번째 슬라이스가 수직 축 오른쪽 약간에서 시작됩니다.

## 일반적인 함정 및 모범 사례

| 문제 | 발생 원인 | 해결 방법 |
|------|----------|----------|
| **차트가 비어 있음** | 문서가 차트가 완전히 렌더링되기 전에 저장되었습니다. | `doc.save()`를 차트 수정 **후**에 호출합니다. |
| **슬라이스 값이 100 %가 되지 않음** | 백분율을 나타내지 않는 원시 숫자를 추가하면 예상치 못한 스케일링이 발생할 수 있습니다. | 전체 중 부분을 논리적으로 나타내는 값을 제공하거나 Aspose.Words가 자동으로 백분율을 계산하도록 합니다. |
| **회전이 적용되지 않음** | `holeSize`를 설정하지 않은 상태에서 `ChartType.DOUGHNUT`을 사용하면 회전 효과가 보이지 않을 수 있습니다. | 차트를 `PIE`로 유지하거나 각도를 설정한 후 `holeSize`를 조정합니다. |
| **파일 경로 오류** | 상대 경로는 Windows와 Linux에서 다르게 해석될 수 있습니다. | 프로덕션 코드에서는 `Paths.get("output", "PieChart.docx").toString()` 또는 절대 경로를 사용합니다. |

### 프로덕션 사용 팁

* **`DocumentBuilder` 재사용** – `insertChart`를 반복 호출하여 동일 문서에 여러 차트를 삽입할 수 있습니다.  
* **Styling** – `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);`를 사용하여 차트에 직접 백분율을 표시합니다.  
* **Performance** – 차트를 한 번 생성하고 여러 위치에 동일한 차트가 필요할 경우 `chart.deepClone()`으로 복제합니다.

## 원형 차트 슬라이스 회전 – 고급 시나리오

* **Dynamic angle** – 데이터를 기반으로 각도를 계산합니다(예: 가장 큰 슬라이스를 상단에서 시작하도록).  
  ```java
  double maxValue = Collections.max(chart.getSeries().get(0).getDataPoints());
  double total = chart.getSeries().get(0).getDataPoints().stream().mapToDouble(Double::doubleValue).sum();
  double startAngle = 360 * (maxValue / total) / 2; // Center the largest slice
  chart.setFirstSliceAngle(startAngle);
  ```
* **Multiple series** – 원형 차트는 일반적으로 하나의 시리즈만 가지지만, Aspose.Words를 사용하면 스택형 파이 차트를 위해 더 많은 시리즈를 추가할 수 있습니다. 회전은 여전히 첫 번째 시리즈에만 적용됩니다.

## 결론

이제 Java를 사용하여 **create pie chart in Word**하는 방법, **add series data to chart**하는 방법, 그리고 시각적 강조를 위해 **rotate pie chart slice**하는 방법을 알게 되었습니다. 전체 예제는 문서 초기화부터 최종 `.docx` 파일 저장까지 전체 워크플로우를 보여주므로 차트 생성을 모든 자동 보고 파이프라인에 통합할 수 있습니다.

### 다음 단계

* 다른 차트 유형(`ChartType.BAR`, `ChartType.LINE`)을 탐색하여 자동화 도구 키트를 확장하세요.  
* **mail merge**와 차트 생성을 결합하여 각 수신자에게 맞춤형 보고서를 생성합니다.  
* **Styling API**(`ChartFormat`, `DataLabel`, `ChartTitle`)를 깊이 파고들어 기업 브랜딩에 맞추세요.

다양한 데이터 세트, 각도 및 차트 스타일을 자유롭게 실험해 보세요. 즐거운 코딩 되세요!

## 다음에 배워야 할 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료는 단계별 설명과 함께 완전한 작동 코드 예제를 포함하여 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하도록 돕습니다.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}