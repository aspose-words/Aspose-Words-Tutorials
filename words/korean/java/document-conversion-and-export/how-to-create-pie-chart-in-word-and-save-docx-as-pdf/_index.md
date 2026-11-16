---
category: general
date: 2026-11-15
description: Java를 사용하여 Word 문서에 파이 차트를 만들고 docx를 PDF로 저장하는 방법을 배웁니다. 이 가이드는 Word를
  PDF로 변환하는 방법과 차트를 추가하는 방법도 다룹니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save docx as pdf
- convert word to pdf
- how to add chart
- how to create chart
language: ko
lastmod: 2026-11-15
og_description: Java를 사용하여 Word 파일에 파이 차트를 만들고 docx를 PDF로 저장합니다. 워드를 PDF로 변환하고 차트를
  추가하는 단계별 튜토리얼을 따라보세요.
og_image_alt: Screenshot showing a pie chart created in a Word document
og_title: Word에서 파이 차트를 만들고 docx를 PDF로 저장 – Java 가이드
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to create pie chart in a Word document and save docx as PDF
    using Java. This guide also covers convert word to pdf and how to add chart.
  headline: How to create pie chart in Word and save docx as PDF
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- PDF
title: Word에서 파이 차트를 만들고 docx를 PDF로 저장하는 방법
url: /ko/java/document-conversion-and-export/how-to-create-pie-chart-in-word-and-save-docx-as-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word에서 파이 차트를 만들고 docx를 PDF로 저장하는 방법

Word 문서 안에 **pie chart**를 만들고 **docx를 PDF로 저장**해야 한다면, 이 튜토리얼이 정확히 방법을 보여줍니다. 파이 차트를 삽입한 상태에서 .docx 파일을 PDF로 변환하는 완전하고 실행 가능한 예제를 확인할 수 있어, “차트 추가 방법”을 찾아 헤매지 않아도 됩니다.

이 가이드에서는 다음을 배웁니다:

* 기존 *.docx* 파일 로드(또는 새 파일 시작)  
* Aspose.Words for Java를 사용하여 **pie chart**를 만들고 데이터를 채우기  
* 차트가 올바르게 렌더링된 상태로 **docx를 PDF로 저장**  
* 차트가 포함된 경우 **convert word to pdf**의 미묘한 차이 이해하기  

이 단계는 Aspose.Words 2024‑x.x와 Java 17에서 작동하지만, Word 차트 조작을 지원하는 모든 라이브러리에 적용할 수 있는 개념입니다.

## 사전 요구 사항

시작하기 전에 다음을 확인하세요:

| 요건 | 이유 |
|------|------|
| Java 17 (또는 그 이상) | 최신 Aspose.Words JAR에 필요합니다 |
| Maven 또는 Gradle 빌드 도구 | 의존성 관리를 단순화합니다 |
| Aspose.Words for Java (최신 버전) | `Document`, `Chart`, `ChartType` 클래스를 제공합니다 |
| 입력 **.docx** 파일 (또는 빈 문서) | 차트가 이 파일에 삽입됩니다 |

Maven의 `pom.xml` 또는 Gradle의 `build.gradle`에 Aspose.Words 의존성을 추가하세요. Maven 예시:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## Step 1: Word 문서 로드(또는 새 문서 생성)

첫 번째 작업은 `Document` 인스턴스를 얻는 것입니다. 템플릿이 이미 있다면 경로를 전달하고, 그렇지 않으면 빈 문서를 생성합니다.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Load an existing .docx or create a new blank document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // If you prefer a new file, uncomment the next line:
        // Document doc = new Document();
```

*Why this step?* `Document` 객체는 차트를 포함한 모든 Word 콘텐츠의 컨테이너입니다. 기존 파일을 로드하면 주변 텍스트와 스타일을 유지하면서 새로운 시각 요소를 추가할 수 있습니다.

## Step 2: **pie chart 만들기** – “how to create chart”의 핵심

이제 `ChartType.PIE`와 함께 `Chart` 객체를 인스턴스화합니다. 이렇게 하면 나중에 데이터를 채울 수 있는 파이 차트 자리표시자가 자동으로 생성됩니다.

```java
        // Step 2: Insert a pie chart into the document
        Chart chart = new Chart(doc, ChartType.PIE);
        // Place the chart at the end of the document body
        doc.getFirstSection().getBody().appendChild(chart);
```

*Explanation*: `ChartType.PIE`는 Aspose.Words에 파이 차트 템플릿을 사용하도록 지시합니다. 차트는 문서 본문에 추가되므로 필요한 위치에 나타납니다. 이는 단일 호출로 “how to add chart” 요구 사항을 충족합니다.

## Step 3: 차트에 데이터 채우기 – “how to add chart”에 대한 답변

파이 차트는 시리즈 데이터가 없으면 의미가 없습니다. `Series` 컬렉션을 사용해 카테고리와 값을 추가합니다.

```java
        // Step 3: Populate the chart with sample data
        chart.getSeries().add("Category A", 40);
        chart.getSeries().add("Category B", 30);
        chart.getSeries().add("Category C", 30);
```

*Why this matters*: `add` 호출마다 파이 조각이 하나 생성됩니다. 첫 번째 인자는 레이블, 두 번째 인자는 숫자 값입니다. 데이터베이스나 CSV 파일에서 동적으로 가져온 값으로 교체할 수 있습니다.

### 선택 사항: 외관 맞춤 (필수는 아니지만 유용함)

```java
        // Set a title for the chart
        chart.setTitle("Sales Distribution Q1");
        // Change the legend position
        chart.getLegend().setPosition(LegendPosition.RIGHT);
```

이러한 조정은 Java 코드를 떠나지 않고도 **how to create chart**를 전문적인 모습으로 만들 수 있음을 보여줍니다.

## Step 4: **docx를 PDF로 저장** – “convert word to pdf”의 최종 단계

차트가 삽입되면 문서를 PDF로 내보냅니다. Aspose.Words는 차트를 벡터 그래픽으로 렌더링하여 품질을 유지합니다.

```java
        // Step 4: Save the document as PDF – the chart will be rendered with graduations
        doc.save("YOUR_DIRECTORY/output.pdf", SaveFormat.PDF);
    }
}
```

*Key point*: `save` 메서드는 Word 파일을 자동으로 PDF로 변환하며 차트 래스터화, 글꼴 포함, 페이지 레이아웃을 처리합니다. 이는 **save docx as pdf** 목표를 달성하고 차트가 포함된 경우 **convert word to pdf**를 신뢰할 수 있게 수행하는 방법을 보여줍니다.

### 예상 출력

프로그램을 실행하면 다음을 포함하는 `output.pdf`가 생성됩니다:

* `input.docx`의 원본 내용(있는 경우)  
* *Sales Distribution Q1*이라는 제목의 완전하게 렌더링된 파이 차트  
* 데이터와 일치하는 정확한 슬라이스 비율 (40 %, 30 %, 30 %)

PDF를 아무 뷰어에서 열어보면 Word 파일에서 보는 것과 동일한 선명한 파이 차트를 확인할 수 있습니다.

## 흔히 발생하는 문제와 회피 방법

| 문제 | 원인 | 해결 방법 |
|------|------|----------|
| PDF에서 차트가 비어 있음 | 글꼴 또는 차트 렌더링 설정 누락 | 최신 Aspose.Words 버전을 사용하고 있는지 확인하세요; 필요한 렌더링 라이브러리가 포함되어 있습니다. |
| 데이터 값이 잘못 반올림됨 | 큰 정수값을 사용함 | `double` 값을 제공하거나 시리즈에 추가하기 전에 숫자를 스케일링하세요. |
| 출력 PDF 파일이 너무 큼 | 고 DPI로 이미지가 삽입됨 | 이미지를 삽입하는 경우 `PdfSaveOptions.setImageCompressionLevel(CompressionLevel.MAXIMUM)`를 설정하세요. |
| “convert word to pdf” 실행 시 `UnsupportedOperationException` 발생 | Java 버전이 오래됨 (< 11) | Aspose.Words 24.x가 요구하는 Java 17 이상으로 업그레이드하세요. |

## 전문가 팁: 차트 생성 로직 재사용

동일 문서에 여러 차트를 추가해야 한다면 차트 생성 코드를 헬퍼 메서드로 추출하세요:

```java
private static Chart createPieChart(Document doc, Map<String, Double> data, String title) {
    Chart chart = new Chart(doc, ChartType.PIE);
    data.forEach(chart.getSeries()::add);
    chart.setTitle(title);
    return chart;
}
```

이제 각 데이터셋에 대해 `doc.getFirstSection().getBody().appendChild(createPieChart(...));`를 호출하면 코드를 DRY(Don’t Repeat Yourself)하게 유지할 수 있습니다.

## 결론

이제 Java를 사용해 Word 문서 안에 **pie chart**를 만들고 데이터를 채우며 **docx를 PDF로 저장**하는 방법을 알게 되었습니다. 이 엔드‑투‑엔드 예제는 전체 **convert word to pdf** 워크플로우를 다루고, **how to add chart**에 답변하며, 프로그래밍 방식으로 **how to create chart**를 구현하는 방법을 보여줍니다.

다음과 같은 주제로 확장해 볼 수 있습니다:

* 막대 차트 또는 라인 차트 추가 (`ChartType.BAR`, `ChartType.LINE`) – 또 다른 **how to create chart** 시나리오.  
* PNG 또는 HTML과 같은 다른 형식으로 내보내기 (`SaveFormat.PNG`, `SaveFormat.HTML`).  
* 차트를 삽입하기 전에 표나 플레이스홀더가 포함된 입력 문서를 동적으로 생성하기.

다양한 데이터 세트, 스타일 옵션, 혹은 페이지당 여러 차트 삽입 등을 자유롭게 실험해 보세요. Happy coding!

## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하며, 밀접하게 관련된 주제를 다룹니다. 각 자료에는 단계별 설명과 완전한 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에 적용할 수 있는 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Java를 사용하여 Word 문서에 파이 차트 삽입하기](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [Java에서 Word를 PDF로 저장하고 접근 가능한 PDF 만들기](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-docx-in-java-full-guide/)
- [Java와 Aspose.Words를 사용하여 Word에서 차트 만들기](/words/english/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}