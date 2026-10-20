---
category: general
date: 2026-07-16
description: Aspose.Words를 사용하여 Java에서 파이 차트를 만들기. 리더 라인을 추가하고 차트 범례를 표시하며 슬라이스를 분리하는
  방법을 하나의 튜토리얼에서 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add leader lines
- show chart legend
- how to explode slice
- how to add legend
language: ko
lastmod: 2026-07-16
og_description: Aspose.Words를 사용하여 Java에서 파이 차트를 만들세요. 이 가이드는 리더 라인을 추가하고 차트 범례를 표시하며
  슬라이스를 분리하는 방법을 보여주어 몇 분 만에 깔끔한 시각화를 제공합니다.
og_image_alt: Screenshot of a Java‑generated pie chart with an exploded slice and
  visible legend
og_title: Aspose.Words Java로 파이 차트 만들기 – 완전한 서식 지정 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  headline: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  name: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  steps:
  - name: Java 17 (or later) installed.
    text: Java 17 (or later) installed.
  - name: Aspose.Words for Java JAR on your classpath.
    text: Aspose.Words for Java JAR on your classpath.
  - name: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
    text: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart Formatting
- Data Visualization
title: Aspose.Words Java로 파이 차트 만들기 – 전체 단계별 가이드
url: /ko/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java로 파이 차트 만들기 – 전체 단계별 가이드

Java에서 저수준 그리기 API와 씨름하지 않고 프로그래밍 방식으로 **파이 차트**를 만드는 방법이 궁금하셨나요? 당신만 그런 것이 아닙니다. 많은 개발자들이 보고서, 대시보드 또는 자동화된 문서에 빠른 시각화를 필요로 하며, 무거운 작업을 처리해 주는 Aspose.Words를 사용합니다.

이 튜토리얼에서는 **파이 차트**를 만들 뿐만 아니라 **리더 라인 추가**, **차트 범례 표시**, 그리고 강조를 위해 **슬라이스를 분리**하는 방법까지 보여주는 완전하고 바로 실행 가능한 예제를 단계별로 살펴보겠습니다. 마지막에는 클라이언트를 감동시킬 만큼 깔끔한 `.docx` 파일을 얻게 됩니다.

> **빠른 성공:** 아래 코드 스니펫은 Aspose.Words for Java 23.9(또는 최신 버전)와 바로 사용할 수 있습니다. 추가 종속성 없이 JAR만 있으면 됩니다.

## 배울 내용

- `DocumentBuilder`를 사용하여 빈 Word 문서를 설정합니다.
- 맞춤 크기의 **파이 차트**를 삽입합니다.
- **슬라이스 분리** 기능을 사용하여 데이터 포인트를 강조합니다.
- **리더 라인**을 활성화하여 분리된 슬라이스가 레이블에 연결되도록 합니다.
- **차트 범례**를 켜서 독자가 각 슬라이스를 즉시 식별할 수 있게 합니다.
- 결과를 Microsoft Word 또는 LibreOffice에서 열 수 있는 `.docx` 파일로 저장합니다.

**전제 조건 – 필요합니다:**

1. Java 17(이상) 설치
2. 클래스패스에 Aspose.Words for Java JAR
3. 기본 IDE 또는 텍스트 편집기—IntelliJ IDEA, Eclipse, VS Code 등 원하는 것을 사용하세요.

자, 시작해봅시다.

## 단계 1: 문서 및 빌더 초기화 – **파이 차트 만들기** 준비

먼저, 깨끗한 문서 캔버스가 필요합니다. `Document`는 전체 Word 파일을 나타내며, `DocumentBuilder`는 콘텐츠를 추가할 수 있게 도와주는 도우미입니다.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();               // the container for our Word file
        DocumentBuilder builder = new DocumentBuilder(doc); // convenient API for adding elements
```

> **왜 중요한가:** 새 `Document`로 시작하면 차트 렌더링을 방해할 수 있는 숨겨진 스타일이나 남은 객체가 없음을 보장합니다.

## 단계 2: **파이 차트** 삽입 – 크기가 중요합니다

Aspose.Words는 차트 삽입을 한 줄 코드로 처리합니다. 여기서는 400 × 300 포인트(대략 일반 화면에서 5.5 × 4.2인치)의 파이 차트를 요청합니다.

```java
        // Step 2: Insert a pie chart of size 400x300 points
        Shape chartShape = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = chartShape.getChart(); // the underlying chart object we will format
```

> **전문가 팁:** 다른 크기가 필요하면 두 숫자 인자를 변경하면 됩니다. API는 포인트 단위이며, 72 포인트 = 1 인치입니다.

## 단계 3: **슬라이스 분리 방법** – 핵심 데이터 포인트 강조

슬라이스를 분리하면 파이의 나머지 부분에서 떨어져 나와 독자의 시선을 끕니다. `setExplosion` 메서드는 거리(포인트)를 나타내는 정수를 받습니다.

```java
        // Step 3: Explode the first slice to emphasize it
        chart.getSeries().get(0).setExplosion(10); // 10 points outward
```

> **시리즈가 여러 개라면?** `setExplosion`을 원하는 시리즈 인덱스(`get(1)`, `get(2)`, …)에 호출하여 다른 슬라이스를 분리할 수 있습니다.

## 단계 4: **리더 라인 추가** 및 **차트 범례 표시** – 점 연결하기

슬라이스가 분리되면 레이블이 멀어질 수 있습니다. 리더 라인은 레이블을 연결해 가독성을 유지합니다. 동시에 범례는 모든 슬라이스에 대한 빠른 키를 제공합니다.

```java
        // Step 4: Enable leader lines for the exploded slice and show the legend
        chart.getSeries().get(0).setLeaderLines(true); // draws a line from slice to its label
        chart.setShowLegend(true);                     // makes the legend visible below the chart
```

> **왜 리더 라인을 활성화하나요?** 리더 라인이 없으면 레이블이 떠 있는 것처럼 보여 어떤 슬라이스에 속하는지 사용자를 혼란스럽게 할 수 있습니다.  
> **맞춤 범례 위치가 필요합니까?** `chart.getLegend().setPosition(LegendPosition.TOP)` 또는 다른 enum 값을 사용하세요.

## 단계 5: 문서 저장 – 최종 **파이 차트 만들기** 단계

마지막으로 문서를 디스크에 저장합니다. 쓰기 권한이 있는 폴더 경로로 조정하세요.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartDemo.docx");
    }
}
```

프로그램을 실행하고 생성된 `PieChartDemo.docx`를 열면 첫 번째 슬라이스가 분리되고 리더 라인과 보이는 범례가 포함된 깔끔하게 포맷된 파이 차트를 확인할 수 있습니다.

![분리된 슬라이스와 범례를 보여주는 파이 차트 예시](pie-chart-example.png){: .center-image alt="분리된 슬라이스, 리더 라인 및 범례가 포함된 파이 차트 예시 만들기"}

### 예상 출력

Word 파일을 열면 차트는 대략 다음과 같이 보입니다:

- 400 × 300 pt 파이 차트.
- 첫 번째 슬라이스가 10 pt 만큼 오프셋됩니다.
- 얇은 리더 라인이 분리된 슬라이스와 레이블을 연결합니다.
- 차트 아래 범례에 각 시리즈 이름이 나열됩니다.

리더 라인이 보이지 않으면 `setLeaderLines(true)`가 폭발 설정 *후에* 호출되었는지 다시 확인하세요—순서가 중요합니다.

## 흔히 발생하는 문제와 해결 방법

| 문제 | 발생 원인 | 해결 방법 |
|------|----------|----------|
| **범례가 표시되지 않음** | `setShowLegend(true)`가 누락되었거나 잘못된 차트 객체에 호출되었습니다. | `chart.setShowLegend(true)`를 **shape에서 Chart를 가져온 후** 호출했는지 확인하세요. |
| **리더 라인 누락** | 슬라이스가 분리되지 않았거나 차트 유형이 리더 라인을 지원하지 않습니다. | `ChartType.PIE`(또는 `PIE_3D`)만 리더 라인을 지원합니다. 먼저 `setExplosion`을 호출하고, 그 다음 `setLeaderLines(true)`를 호출하세요. |
| **슬라이스가 움직이지 않음** | 폭발 값이 너무 낮음(0‑2 pt). | 정수를 늘리세요, 예: `setExplosion(10)` 또는 더 큰 값으로 설정하면 더 눈에 띄는 효과를 얻을 수 있습니다. |
| **차트가 왜곡됨** | 정사각형이 아닌 크기(너비 ≠ 높이)를 사용하면 파이가 눌릴 수 있습니다. | 너비와 높이를 동일하거나 비슷하게 유지하세요; 400 × 300도 작동하지만 400 × 400이면 완벽한 원이 됩니다. |

## 고급 조정 (옵션)

기본을 넘어가고 싶다면 다음을 고려하세요:

- **사용자 정의 색상**: `chart.getSeries().get(0).getDataPoints().get(i).getFormat().getFill().setForeColor(Color.RED);`
- **데이터 레이블**: `chart.getSeries().get(0).setDataLabelType(ChartDataLabelType.CATEGORY);`
- **3‑D 효과**: `ChartType.PIE`를 `ChartType.PIE_3D`로 교체합니다.

이 옵션들을 사용하면 시각을 기업 브랜드 가이드라인에 맞게 세밀하게 조정할 수 있습니다.

## 요약 – 달성한 내용

우리는 빈 Word 문서에서 시작해 **파이 차트를 만들고**, **첫 번째 슬라이스를 분리하고**, **리더 라인을 추가하고**, **차트 범례를 표시**했습니다. 전체 흐름은 간결한 `main` 메서드에 들어가 있어 더 큰 보고 파이프라인에 쉽게 삽입할 수 있습니다.

## 다음 단계

- **시리즈 추가**: 데이터베이스 또는 CSV에서 실제 데이터를 차트에 채워 넣습니다.
- **PDF로 내보내기**: `doc.save("output.pdf", SaveFormat.PDF);`를 사용해 PDF 버전을 생성합니다.
- **다른 도형과 결합**: 전체 보고서를 위해 표, 이미지 또는 추가 차트를 삽입합니다.

다른 차트 유형(컬럼, 바, 라인)에 관심이 있다면 `ChartType.PIE`를 해당 enum으로 교체하고 동일한 포맷 단계에 따라 진행하면 됩니다.

*즐거운 차트 만들기!* 기대대로 동작하지 않는 부분이 있으면 댓글을 남겨 주세요, 또는 범례 위치를 어떻게 커스터마이징했는지 공유해 주세요. 여러분의 피드백은 더 나은 자동 문서를 만드는 데 도움이 됩니다.

## 다음에 배울 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료는 전체 작동 코드 예제와 단계별 설명을 포함하여 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방법을 탐색하는 데 도움을 줍니다.

- [Aspose.Words for Java를 사용하여 컬럼 차트 만드는 방법](/words/english/java/document-conversion-and-export/using-charts/)
- [Aspose.Words for Java로 PDF 문서 만들기 | Document Processing API](/words/english/java/)
- [Aspose.Words for Java를 사용하여 문서에 워터마크 추가](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}