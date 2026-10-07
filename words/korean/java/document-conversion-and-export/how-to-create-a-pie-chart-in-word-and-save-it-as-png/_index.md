---
category: general
date: 2026-10-07
description: Word에서 파이 차트를 만드는 방법, 데이터 시리즈를 추가하는 방법, 그리고 Java를 사용해 차트를 PNG로 저장하는 방법을
  배워보세요. 빠른 결과를 위해 단계별 가이드를 따라하세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add data series
- save chart as png
- generate pie chart in word
- save word chart as image
language: ko
lastmod: 2026-10-07
og_description: 'Word에서 파이 차트를 빠르게 만들기: 이 튜토리얼에서는 데이터 시리즈를 추가하고 차트를 생성하며 Word 차트를
  이미지(PNG)로 저장하는 방법을 보여줍니다. 전체 코드 예제를 따라하세요.'
og_image_alt: Screenshot of a create pie chart result in a Word document
og_title: Word에서 파이 차트를 만들고 PNG로 내보내기 – 가이드
schemas:
- author: GroupDocs
  dateModified: '2026-10-07'
  description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  headline: How to create a pie chart in Word and save it as PNG
  type: TechArticle
- description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  name: How to create a pie chart in Word and save it as PNG
  steps:
  - name: Load the source document
    text: You must open the Word file that will host the chart. The `Document` class
      reads the `.docx` content into memory.
  - name: Add data series to the chart
    text: Creating a **pie chart** starts with a `Chart` instance. The constructor
      receives the parent `Document` and the chart type (`ChartType.PIE`). After the
      chart object exists, you populate it with numeric values and optional labels.
  - name: Save chart as PNG
    text: Once the chart is part of the document, you can export the visual representation.
      The `save` method on the underlying chart object writes a PNG file to the file
      system.
  type: HowTo
tags:
- Java
- Word automation
- Chart generation
title: Word에서 파이 차트를 만들고 PNG로 저장하는 방법
url: /ko/java/document-conversion-and-export/how-to-create-a-pie-chart-in-word-and-save-it-as-png/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word에서 파이 차트를 만들고 PNG로 저장하는 방법

Microsoft Word 파일 안에 **파이 차트** 객체를 만들어야 할 경우, 이 가이드는 Java를 사용해 정확히 어떻게 하는지 보여줍니다. 또한 **데이터 시리즈를 추가**하고 **차트를 PNG로 저장**하는 방법도 배울 수 있어, 시각화를 Word 외부에서도 재사용할 수 있습니다.

문서 안에서 직접 차트를 생성하면 별도의 그래픽 도구로 데이터를 내보낼 필요가 없습니다. 이 튜토리얼을 끝까지 따라 하면 파이 차트가 포함된 완전한 Word 파일과 디스크에 저장된 PNG 이미지가 준비됩니다.

## Prerequisites

시작하기 전에 다음이 준비되어 있는지 확인하세요:

* Java 17 이상이 설치되어 있어야 합니다.
* **GroupDocs.Viewer for Java**(또는 `Document`, `Chart`, `ChartType`, `ImageSaveOptions` 클래스를 제공하는 호환 라이브러리).
* 라이브러리 의존성을 추가할 수 있는 Maven 또는 Gradle 프로젝트.
* 코드에서 참조할 수 있는 폴더에 위치한 입력 Word 문서(`input.docx`).

Maven을 사용한다면, 의존성을 추가하세요( `VERSION`을 최신 릴리스 버전으로 교체):

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>VERSION</version>
</dependency>
```

## How to create pie chart in Word

솔루션의 핵심은 다음 세 가지 작업에 있습니다:

1. 소스 `.docx` 파일을 로드합니다.
2. `PIE` 유형의 새 `Chart` 객체에 **데이터 시리즈를 추가**합니다.
3. **차트를 PNG로 저장**하여 Word 문서 옆에 이미지 파일을 생성합니다.

각 단계는 아래에서 자세히 설명하고, 필요한 정확한 Java 코드를 제공합니다.

### Step 1: Load the source document

차트를 삽입할 Word 파일을 열어야 합니다. `Document` 클래스가 `.docx` 내용을 메모리로 읽어들입니다.

```java
// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*왜 중요한가*: 문서를 로드하면 변경 가능한 모델이 생성됩니다. 이후의 모든 차트 작업은 이 메모리 상의 표현을 수정하며, 최종적으로 디스크에 다시 저장됩니다.

### Step 2: Add data series to the chart

**파이 차트**를 만들려면 `Chart` 인스턴스를 생성합니다. 생성자에 부모 `Document`와 차트 유형(`ChartType.PIE`)을 전달합니다. 차트 객체가 생성된 후, 숫자 값과 선택적 레이블을 채워 넣습니다.

```java
// Step 2: Create a pie chart and configure its data series
Chart chart = new Chart(doc, ChartType.PIE);

// Example: add a data series (replace with your actual data)
double[] values = { 30, 20, 50 };
String[] categories = { "A", "B", "C" };
chart.getSeries().add(values, categories);
```

*왜 중요한가*: `add` 메서드는 차트에 **데이터 시리즈를 추가**합니다. `values`의 각 항목은 파이 조각이 되고, `categories`는 범례 레이블을 제공합니다. 포인트 수에 제한이 없으며, 라이브러리가 자동으로 조각 각도를 계산합니다.

### Step 3: Save chart as PNG

차트가 문서에 포함되면 시각적 표현을 내보낼 수 있습니다. 기본 차트 객체의 `save` 메서드는 PNG 파일을 파일 시스템에 기록합니다.

```java
// Step 3: Save the chart as a PNG image (graduations are added automatically)
chart.getChartShape()
     .getChart()
     .save("YOUR_DIRECTORY/radial.png",
           ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

*왜 중요한가*: 차트를 PNG로 저장하면 원본 Word 파일 없이도 웹 페이지, 이메일, 보고서 등에 삽입할 수 있는 래스터 이미지가 생성됩니다. `ImageSaveOptions` 객체를 사용해 형식, 해상도 및 기타 내보내기 설정을 제어할 수 있습니다.

## Generate pie chart in Word – customizing the look

기본 단계 외에도 색상, 제목, 데이터 레이블 등을 커스터마이징하고 싶을 수 있습니다. 대부분의 라이브러리는 `ChartOptions`와 같은 객체를 제공합니다. 아래 예시는 제목을 추가하고 조각 색상을 변경하는 방법을 보여줍니다:

```java
chart.getChart().setTitle("Sales Distribution Q1");

// Set custom colors (RGB format)
chart.getSeries().get(0).setColors(new int[] {
    0xFF5733, // slice A – orange
    0x33FF57, // slice B – green
    0x3357FF  // slice C – blue
});
```

이러한 커스터마이징은 선택 사항이지만, **Word에서 파이 차트를 생성**하면서 브랜드에 맞게 스타일을 적용하는 방법을 보여줍니다.

## Save Word chart as image – alternative approaches

이미지만 필요하고 문서 안에 차트를 삽입할 필요가 없다면, 차트 형태를 Word 파일에 추가하는 단계를 건너뛰고 차트를 만든 직후 `save` 메서드를 호출하면 됩니다. 코드는 동일하며, 문서 본문에 차트를 추가하는 단계만 생략하면 됩니다.

```java
// Directly save the chart without embedding it in the document
chart.getChart().save("YOUR_DIRECTORY/pie_only.png",
                      ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

이 방법은 배치 프로세스로 많은 차트를 생성하고 PNG 출력만 필요할 때 유용합니다.

## Full runnable example

아래 클래스를 프로젝트에 복사하고 파일 경로를 조정한 뒤 실행하세요. 프로그램은 다음을 수행합니다:

1. `input.docx`를 로드합니다.
2. **파이 차트를 생성**, **데이터 시리즈를 추가**하고 문서에 삽입합니다.
3. **차트를 PNG**(`radial.png`)로 저장합니다.
4. 수정된 Word 파일을 `output.docx`로 저장합니다.



## What Should You Learn Next?

다음 튜토리얼들은 이 가이드에서 다룬 기술을 기반으로 하는 관련 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함해 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용할 수 있도록 돕습니다.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}