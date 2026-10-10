---
category: general
date: 2026-10-10
description: Word 파일에서 차트를 회전하고, Word에서 차트를 수정하여 도넛 차트 크기를 변경하는 방법을 전체 Java 예제로 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to rotate chart
- modify chart in word
- change doughnut chart size
- Aspose.Words chart manipulation
- Java chart API
language: ko
lastmod: 2026-10-10
og_description: Aspose.Words for Java를 사용하여 Word 파일에서 차트를 회전하고 도넛 차트 크기를 변경하는 방법.
og_image_alt: Screenshot showing a rotated doughnut chart after applying how to rotate
  chart steps
og_title: Word 문서에서 차트 회전 방법 – 단계별 Java 가이드
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Learn how to rotate chart in a Word file and modify chart in Word to
    change doughnut chart size with a complete Java example.
  headline: How to rotate chart in a Word document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Aspose.Words를 사용하여 Word 문서에서 차트를 회전하는 방법
url: /ko/java/document-manipulation/how-to-rotate-chart-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words를 사용하여 Word 문서에서 차트 회전하는 방법

Microsoft Word 파일 안에서 **차트를 회전하는 방법**이 필요하다면, 이 가이드는 정확한 단계를 보여줍니다. 또한 **Word에서 차트 수정**을 **도넛 차트 크기 변경**과 함께 Java 코드를 벗어나지 않고 배울 수 있습니다.

Word 자동화는 종종 서로 연결되지 않은 API 호출들의 연속처럼 느껴지지만, Aspose.Words를 사용하면 차트를 다른 문서 노드와 동일하게 취급할 수 있습니다. 이 튜토리얼이 끝날 때쯤에는 기존 `.docx` 파일을 로드하고, 도넛 차트를 45° 회전시키며, 구멍을 반경의 50 %로 줄이고, 결과를 새 파일로 저장하는 실행 가능한 프로그램을 갖게 됩니다.

## 사전 요구 사항

* Java 17 이상이 설치되어 있어야 합니다.
* Maven(또는 Gradle)으로 종속성을 관리합니다.
* 이미 도넛 차트가 포함된 입력 Word 문서(`input.docx`)가 필요합니다.
* 유효한 Aspose.Words for Java 라이선스(또는 평가 모드 사용)입니다.

## 단계 1: Maven 프로젝트 설정

새 Maven 프로젝트를 만들거나 기존 `pom.xml`에 다음 종속성을 추가하십시오:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version available -->
</dependency>
```

`mvn clean install`을 실행하면 라이브러리를 다운로드하고 클래스가 클래스패스에 사용 가능해집니다.

## 단계 2: 차트가 포함된 Word 문서 로드

첫 번째 작업은 기존 문서를 여는 것입니다. `Document` 클래스는 전체 파일을 나타냅니다.

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

파일을 로드해도 **수정되지** 않으며, 단순히 메모리 내 표현을 생성하여 조회하고 편집할 수 있게 합니다.

## 단계 3: 탐색을 위한 DocumentBuilder 생성

`DocumentBuilder`는 문서 트리를 탐색할 수 있는 커서와 같은 API를 제공합니다. 이를 사용하여 첫 번째 차트 도형을 찾겠습니다.

```java
        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

빌더는 문서 시작 부분에서 시작하지만, 필요에 따라 나중에 원하는 노드로 이동할 수 있습니다.

## 단계 4: 첫 번째 차트 도형 가져오기

차트는 `Shape` 노드로 저장됩니다. `NodeType.SHAPE` 유형의 자식 노드를 필터링하여 차트 객체를 추출할 수 있습니다.

```java
        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();
```

문서에 차트가 여러 개 포함된 경우, `getChildNodes`를 반복하고 각 `Shape`에 대해 `hasChart()`를 확인한 후 캐스팅할 수 있습니다.

## 단계 5: 차트 회전 (차트 회전 방법)

도넛 차트는 본질적으로 구멍이 있는 파이 차트입니다. 회전하면 첫 번째 조각의 시작 각도가 변경됩니다.

```java
        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);
```

`setStartAngle` 메서드는 각도를 나타내는 double 값을 기대합니다. 양수 값은 시계 방향으로 회전하고, 음수 값은 반시계 방향으로 회전합니다.

## 단계 6: 도넛 구멍 크기 변경 (도넛 차트 크기 변경)

구멍 크기는 차트 반경의 비율로 표현됩니다. `0.5` 값은 구멍이 전체 반경의 50 %를 차지함을 의미합니다.

```java
        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);
```

**팁:** 유효 범위는 `0.0`(구멍 없음, 즉 일반 파이)부터 `0.9`(매우 얇은 링)까지입니다. 이 범위를 벗어난 값은 `IllegalArgumentException`을 발생시킵니다.

## 단계 7: 수정된 문서 저장

마지막으로 변경 사항을 디스크에 저장합니다.

```java
        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");
    }
}
```

`DoughnutFormatted.docx`를 Microsoft Word에서 열면, 도넛 차트가 45° 회전하고 구멍이 원래 크기의 절반으로 줄어든 것을 확인할 수 있습니다.

## 전체 실행 가능한 예제

모든 요소를 합치면, IDE에 복사‑붙여넣기 할 수 있는 완전한 프로그램이 아래에 있습니다:

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Ensure the shape actually contains a chart
        if (!chartShape.hasChart()) {
            System.out.println("No chart found in the first shape.");
            return;
        }

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();

        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);

        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);

        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");

        System.out.println("Chart rotated and doughnut size changed successfully.");
    }
}
```

### 예상 출력

프로그램을 실행하면 다음과 같이 출력됩니다:

```
Chart rotated and doughnut size changed successfully.
```

`DoughnutFormatted.docx`를 열면 첫 번째 조각이 45° 위치에서 시작하고 내부 반경이 외부 반경의 절반을 차지하는 도넛 차트를 볼 수 있습니다.

## 일반적인 변형 및 엣지 케이스

| 상황 | 조정 내용 | 왜 중요한가 |
|-----------|----------------|----------------|
| **여러 차트** | `getChildNodes(NodeType.SHAPE, true)`를 반복하고 각 `shape.hasChart()`를 확인합니다 | 첫 번째 차트가 아니라 의도한 차트를 수정한다는 것을 보장합니다 |
| **막대형 또는 선형 차트** | `setStartAngle`은 적용되지 않으며, 다른 시각적 조정을 위해 `chart.getSeries().get(0).setFillFormat(...)`를 사용합니다 | 모든 차트 유형이 회전을 지원하는 것은 아니며, 도넛/파이 차트만 시작 각도를 가집니다 |
| **도넛 구멍이 없는 차트** | `setDoughnutHoleSize`를 건너뛰거나 먼저 `chart.setChartType(ChartType.DONUT)`를 통해 차트 유형을 도넛으로 변환합니다 | 도넛이 아닌 차트에서 구멍 크기를 변경하면 예외가 발생합니다 |
| **대용량 문서** | 대상 탐색을 위해 `DocumentBuilder.moveToDocumentStart()`와 `builder.moveToNode(chartShape)`를 사용합니다 | 관련 없는 노드 전체를 탐색하지 않아 성능이 향상됩니다 |

## 안정적인 차트 조작을 위한 전문가 팁

* **차트 참조 캐시** – 여러 속성을 수정할 계획이라면 `chartShape.getChart()`를 반복 호출하는 대신 로컬 `Chart` 변수를 유지하십시오.
* **입력 값 검증** – `setStartAngle` 또는 `setDoughnutHoleSize`를 호출하기 전에 범위를 확인하여 런타임 오류를 방지합니다.
* **라이선스 사용** – 평가 모드는 첫 페이지에 워터마크를 삽입합니다. 라이선스를 적용하면 (`License license = new License(); license.setLicense("Aspose.Words.lic");`) 워터마크가 제거됩니다.

## 다음 단계

이제 **차트 회전 방법**과 **도넛 차트 크기 변경**을 알게 되었으니, 다른 **Word에서 차트 수정** 시나리오를 탐색할 수 있습니다:

* `chart.getSeries().get(0).getDataPoints().get(i).getFillFormat().setForeColor(Color.getRed())`를 사용하여 조각 색상을 변경합니다.
* `chart.getSeries().get(0).setHasDataLabel(true)`를 호출하여 데이터 레이블을 추가합니다.
* `chart.toImage(300, 300, ImageType.PNG)`를 사용하여 차트를 이미지로 내보냅니다.

이러한 확장 기능은 모두 동일한 패턴을 따릅니다: `Chart` 객체를 얻고, 적절한 setter를 호출한 뒤, 문서를 저장합니다.

**Java를 사용하여 Word에서 도넛 차트를 회전하고 크기를 조정하는 방법을 이제 마스터했습니다.** 다른 차트 유형에 맞게 코드를 조정하거나, 더 큰 문서 생성 파이프라인에 통합하거나, PowerPoint 자동화를 위해 Aspose.Slides와 결합해도 좋습니다. 코딩을 즐기세요!

## 다음에 배울 내용

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 단계별 설명과 함께 완전한 작동 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Aspose.Words for Java를 사용하여 열 차트 만드는 방법](/words/english/java/document-conversion-and-export/using-charts/)
- [Word 문서에서 차트 축 숨기기](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Word 문서에 버블 차트 삽입](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}