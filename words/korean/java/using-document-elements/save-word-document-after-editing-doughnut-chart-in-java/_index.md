---
category: general
date: 2026-09-11
description: Aspose.Words for Java를 사용하여 도넛 차트를 편집한 후 Word 문서를 저장합니다. 도넛 구멍 크기 변경,
  도넛 차트 회전 및 도넛 차트 속성 편집 방법을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word document
- rotate doughnut chart
- edit doughnut chart
- change doughnut hole
- change chart hole size
language: ko
lastmod: 2026-09-11
og_description: Aspose.Words for Java를 사용하여 도넛 차트를 편집한 후 Word 문서를 저장합니다. 이 튜토리얼에서는
  도넛 구멍 크기를 변경하고, 도넛 차트를 회전하며, 차트 모양을 사용자 정의하는 방법을 보여줍니다.
og_image_alt: Java code editing a doughnut chart before saving Word document
og_title: 도넛 차트 편집 후 Word 문서 저장 – Java 가이드
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Save Word document after editing a doughnut chart with Aspose.Words
    for Java. Learn how to change doughnut hole size, rotate doughnut chart, and edit
    doughnut chart properties.
  headline: Save Word document after editing doughnut chart in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word
- Chart
- Doughnut
title: Java에서 도넛 차트를 편집한 후 Word 문서 저장
url: /ko/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java에서 도넛 차트 편집 후 Word 문서 저장

맞춤형 도넛 차트가 포함된 **Word 문서**를 저장해야 한다면, 이 가이드는 정확히 어떻게 하는지 보여줍니다. 몇 줄의 Java 코드만으로 도넛 구멍을 변경하고, 도넛 차트를 회전한 뒤 결과를 디스크에 다시 쓸 수 있습니다.

Aspose.Words for Java를 사용한 완전하고 실행 가능한 예제를 확인할 수 있으며, 여러 차트를 처리하고, 노드 유형을 확인하며, 일반적인 함정을 피하는 팁도 제공합니다. 외부 참조는 필요하지 않으며, 필요한 모든 것이 포함되어 있습니다.

## 사전 요구 사항

- Java 17 이상이 설치되어 있음
- Maven 또는 Gradle을 사용하여 종속성 관리
- Aspose.Words for Java (버전 23.9 이상)가 프로젝트에 추가됨  
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.9</version>
  </dependency>
  ```
- 단일 도넛 차트가 포함된 Word 파일 (`input.docx`)

## 1단계: Word 문서 로드

첫 번째 단계는 소스 파일을 여는 것입니다. 이 단계는 모든 후속 작업이 메모리 내 `Document` 객체에서 수행되기 때문에 필수적입니다.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // Load the Word document that contains a doughnut chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **왜?** 문서를 로드하면 도형, 표, 차트를 탐색할 수 있는 DOM 표현이 생성됩니다. 파일을 열 수 없으면 Aspose.Words가 예외를 발생시키므로 경로가 잘못되었음을 즉시 알 수 있습니다.

## 2단계: 도넛 차트 도형 찾기

차트는 `Shape` 노드 안에 저장됩니다. 차트를 포함하는 첫 번째 도형을 가져와 그 렌더러를 `Chart`로 캐스팅합니다.

```java
        // Find the first shape that contains a chart
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        // Ensure the shape actually holds a chart
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        // Get the Chart object for further manipulation
        Chart chart = chartShape.getChart();
```

> **왜?** `isChart()`를 확인하면 차트 앞에 이미지나 다른 도형이 있는 경우 `ClassCastException`을 방지할 수 있습니다. 이는 혼합된 콘텐츠가 있는 문서에서도 코드를 견고하게 만듭니다.

## 3단계: 도넛 구멍 크기 변경  

이제 도넛 구멍을 편집합니다. `setHoleSize` 메서드는 차트 반경의 백분율(10 – 90)을 기대합니다.

```java
        // Adjust the size of the doughnut hole (percentage of the chart radius)
        chart.setHoleSize(30);   // The hole occupies 30 % of the radius
```

> **왜?** 도넛 구멍(`change doughnut hole` / `change chart hole size`)을 변경하면 중앙 영역을 강조하거나 강조를 줄일 수 있습니다. 10‑90 % 범위를 벗어난 값은 API에서 무시됩니다.

## 4단계: 도넛 차트 회전  

첫 번째 조각이 시작되는 위치를 제어하려면 첫 조각 각도를 설정합니다. 이렇게 하면 **도넛 차트를 회전**할 수 있습니다.

```java
        // Rotate the chart so that the first slice starts at a custom angle
        chart.setFirstSliceAngle(45);   // Starts the first slice at 45 degrees
```

> **왜?** 차트를 회전하면 특정 조각을 상단에 표시하거나 디자인 사양에 맞출 때 유용합니다.

## 5단계: 업데이트된 문서 저장  

마지막으로 변경 사항을 새 파일에 기록합니다. 여기서 **편집된 차트가 포함된 Word 문서를 저장**하게 됩니다.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **예상 결과:** `output.docx`는 원본 내용을 포함하지만, 도넛 차트는 이제 30 % 구멍을 가지고 첫 조각이 45 °에서 시작합니다. Microsoft Word에서 파일을 열면 변형된 차트가 표시됩니다.

## 전체 작업 예제

아래는 IDE에 복사‑붙여넣기 할 수 있는 완전한 프로그램입니다. 여기에는 **도넛 차트 편집** 및 **Word 문서 저장**에 필요한 모든 import와 오류 처리 코드가 포함되어 있습니다.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Locate the first chart shape
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        Chart chart = chartShape.getChart();

        // 3. Change the doughnut hole size
        chart.setHoleSize(30); // 30 % hole

        // 4. Rotate the doughnut chart
        chart.setFirstSliceAngle(45); // start at 45°

        // 5. Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### 예상 출력

`output.docx`를 열면:

- 도넛 차트의 중앙 구멍이 차트 반경의 약 1/3을 차지합니다.  
- 첫 번째 조각이 45도 위치에서 시작하여 차트 전체가 시계 방향으로 이동합니다.  

두 시각적 변화가 Word에서 즉시 반영됩니다.

## 일반적인 변형 및 엣지 케이스

| 상황 | 처리 방법 |
|-----------|----------------|
| **Multiple charts** | `doc.getChildNodes(NodeType.SHAPE, true)`를 반복하고 `shape.isChart()`로 필터링합니다; 각 `Chart`에 `setHoleSize` / `setFirstSliceAngle`를 적용합니다. |
| **Chart is not a doughnut** | `chart.getType()`을 확인합니다; `chart.getType() == ChartType.DOUGHNUT`인 경우에만 `setHoleSize`를 호출합니다. |
| **Need to change hole size dynamically** | 데이터 값을 기반으로 원하는 백분율을 계산한 다음 `setHoleSize(computedValue)`를 호출합니다. |
| **Saving to a stream** | Use |

## 다음에 배울 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 단계별 설명과 함께 완전한 작동 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Aspose.Words for Java를 사용하여 열 차트 만들기](/words/english/java/document-conversion-and-export/using-charts/)
- [Aspose.Words for Java로 문서를 PDF로 저장하는 방법](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Aspose.Words for Java를 사용하여 비밀번호로 Word 저장](/words/english/java/document-loading-and-saving/advance-saving-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}