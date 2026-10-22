---
category: general
date: 2026-09-18
description: Aspose.Words for Java를 사용하여 Word 문서를 만들고 파이 차트를 삽입하는 방법을 배웁니다. 파이 차트
  회전 및 Word 파일 생성 단계가 포함됩니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- rotate pie chart
- generate word file
- how to create pie chart
language: ko
lastmod: 2026-09-18
og_description: Java를 사용하여 Word 문서를 만들고 파이 차트를 삽입하세요. 이 가이드를 따라 파이 차트를 회전하고, 슬라이스를
  분리하며, Word 파일을 생성하세요.
og_image_alt: Screenshot showing a Word document containing a pie chart created with
  Java
og_title: 파이 차트가 포함된 Word 문서 만들기 – 단계별 Java 가이드
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  headline: How to create a Word document with a pie chart in Java
  type: TechArticle
- description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  name: How to create a Word document with a pie chart in Java
  steps:
  - name: Expected output
    text: 'After running the program, open `output/PieChart.docx`. You should see:'
  - name: Inserting multiple charts
    text: 'If you need more than one chart, call `builder.insertChart` again after
      moving the cursor:'
  - name: Changing chart colors
    text: 'You can customize slice colors via the series'' `getPoints()` collection:'
  - name: Handling large datasets
    text: For datasets with more than 10 slices, consider using a doughnut chart (`ChartType.DOUGHNUT`)
      to keep the visual clear.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Java에서 파이 차트가 포함된 Word 문서 만드는 방법
url: /ko/java/images-shapes/how-to-create-a-word-document-with-a-pie-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java에서 파이 차트가 포함된 Word 문서 만들기

데이터를 시각화하는 **Word 문서**를 만들어야 한다면, 이 가이드는 Aspose.Words for Java를 사용하여 수행하는 방법을 보여줍니다. 파이 차트를 삽입하고, 슬라이스를 분리하고, 차트를 회전하는 방법을 배우며, 마지막으로 Microsoft Word에서 열 수 있는 **Word 파일**을 **생성**하게 됩니다.

텍스트와 차트를 결합한 보고서를 만드는 데 별도의 그래픽 도구가 필요하지 않습니다. 이 튜토리얼을 마치면 완전하게 구성된 파이 차트를 포함하는 .docx 파일을 생성하는 완전한 실행 가능한 프로그램을 얻게 됩니다.

## 사전 요구 사항

- Java 17 이상 (코드는 Java 8+에서도 컴파일됩니다)
- Maven 또는 Gradle을 사용한 종속성 관리
- Aspose.Words for Java 라이선스 (무료 체험판으로도 이 예제에 사용 가능)
- Java 구문에 대한 기본적인 이해

## 1단계: Maven 프로젝트 설정

새 Maven 프로젝트를 생성하고 `pom.xml`에 Aspose.Words 의존성을 추가합니다:

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-pie-chart</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.12</version>
        </dependency>
    </dependencies>
</project>
```

> **팁:** 버전 번호를 최신 상태로 유지하세요; 최신 릴리스에서는 차트 유형 개선 및 버그 수정이 포함됩니다.

## 2단계: 새 Word 문서 만들기

프로그램matically **Word 문서를 만들 때** 첫 번째 작업은 `Document` 객체를 인스턴스화하는 것입니다. 이 객체는 메모리 내에서 전체 .docx 파일을 나타냅니다.

```java
import com.aspose.words.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a blank document
        Document doc = new Document();

        // Continue with chart insertion...
```

`Document` 클래스는 모든 Word‑processing 기능의 진입점입니다. 이 시점에서는 파일이 디스크에 기록되지 않으며, `save`를 호출할 때까지 모든 작업이 RAM에서 이루어집니다.

## 3단계: 파이 차트 삽입 방법

`DocumentBuilder`를 사용하면 문서에 콘텐츠를 추가할 수 있습니다. `insertChart`를 사용하면 **파이 차트** 객체를 직접 **삽입**할 수 있습니다.

```java
        // Step 3: Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with width=400pt, height=300pt
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

`ChartType.PIE`는 Aspose.Words에 파이 차트를 만들도록 지시합니다. 치수는 포인트 단위로 표현됩니다 (1 pt ≈ 1/72 in). 이 호출 후 차트가 새 단락에 나타납니다.

## 4단계: 차트에 데이터 채우기

파이 차트에는 값 시리즈가 필요합니다. 여기서는 “Apples”, “Bananas”, “Cherries” 세 가지 카테고리를 추가합니다.

```java
        // Create a data series
        chart.getSeries().add("Fruits", new String[]{"Apples", "Bananas", "Cherries"},
                new double[]{30, 45, 25});
```

`add` 메서드는 시리즈를 구축하고 자동으로 범례 항목을 생성합니다. 이 패턴은 모든 숫자 데이터셋에 재사용할 수 있습니다.

## 5단계: 첫 번째 슬라이스 강조

슬라이스를 분리하면 특정 값에 주목하게 됩니다. 첫 번째 슬라이스(인덱스 0)는 20 포인트만큼 분리됩니다.

```java
        // Step 5: Explode the first slice
        chart.getSeries().get(0).setExplode(20);
```

시리즈에 `explode`를 설정하면 전체 차트에 영향을 주지만, 첫 번째 데이터 포인트만 오프셋됩니다.

## 6단계: 파이 차트 회전 방법

차트를 회전하면 시각적 균형이 향상되며, 특히 가장 큰 슬라이스가 상단에 없을 때 유용합니다. `setRotationAngle` 메서드는 각도를 도 단위로 받습니다.

```java
        // Step 6: Rotate the chart 45 degrees
        chart.setRotationAngle(45);
```

45° 회전은 시작 각도를 시계 방향으로 이동시켜, 다양한 레이아웃에서 차트를 더 쉽게 읽을 수 있게 합니다.

## 7단계: 문서를 저장하고 Word 파일 생성

마지막으로 문서를 디스크에 씁니다. 이 단계는 Microsoft Word, LibreOffice 또는 기타 호환 뷰어에서 열 수 있는 **Word 파일을 생성**합니다.

```java
        // Step 7: Save the document
        String outputPath = "output/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

`save` 메서드는 .docx 확장자를 자동으로 감지하고 Word‑호환 패키지를 씁니다. `output` 폴더가 존재해야 하며, 없을 경우 프로그램matically 생성할 수 있습니다.

### 예상 출력

프로그램을 실행한 후 `output/PieChart.docx`를 엽니다. 다음과 같이 표시됩니다:

- 400 × 300 pt 파이 차트가 포함된 단일 페이지.
- “Apples” 슬라이스가 20 pt 외부로 분리됨.
- 전체 차트가 시계 방향으로 45° 회전됨.
- 세 과일 카테고리에 맞는 범례.

## 일반적인 변형 및 엣지 케이스

### 여러 차트 삽입

차트를 하나 이상 삽입해야 하면, 커서를 이동한 뒤 `builder.insertChart`를 다시 호출합니다:

```java
builder.writeln();               // Add a line break
Chart secondChart = builder.insertChart(ChartType.PIE, 300, 200);
```

### 차트 색상 변경

시리즈의 `getPoints()` 컬렉션을 통해 슬라이스 색상을 사용자 정의할 수 있습니다:

```java
chart.getSeries().get(0).getPoints().get(0).getFormat().getFill().setForeColor(Color.RED);
```

### 대용량 데이터셋 처리

10개 이상의 슬라이스가 있는 데이터셋의 경우, 시각적 명확성을 위해 도넛 차트(`ChartType.DOUGHNUT`) 사용을 고려하세요.

## 결론

이제 Aspose.Words for Java를 사용하여 **Word 문서 만들기**, **파이 차트 삽입**, **파이 차트 회전**, 그리고 **Word 파일 생성** 방법을 알게 되었습니다. 전체 솔루션은 문서 초기화부터 최종 파일 출력까지의 전체 워크플로를 보여주며, 각 단계의 “방법”과 “이유”를 모두 다룹니다.

다음으로, 데이터베이스에서 **파이 차트 데이터 생성** 방법, 데이터 레이블 추가, 차트를 이미지로 내보내기 등 관련 주제를 탐색해 보세요. 다양한 차트 유형(막대, 선, 도넛)을 실험하여 Word 자동화 툴킷을 확장하십시오.

## 다음에 배워야 할 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 리소스에는 단계별 설명이 포함된 완전한 작동 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Aspose.Words for Java를 사용하여 열 차트 만들기](/words/english/java/document-conversion-and-export/using-charts/)
- [Java Word 문서 만들기 – 그림자 효과가 있는 사각형 모양 추가](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Java를 사용한 Word 문서 변경 추적: 문서 개정에 대한 완전 가이드](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}