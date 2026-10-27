---
category: general
date: 2026-10-16
description: Java를 사용하여 Word에서 도형을 그룹화하는 방법을 배웁니다. 이 튜토리얼에서는 사각형 도형을 추가하고, 도형의 크기와
  치수를 설정하며, 문서를 저장하는 방법을 보여줍니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- set shape dimensions
- rectangle shape code
language: ko
lastmod: 2026-10-16
og_description: Java를 사용하여 Word에서 도형을 그룹화합니다. 사각형 도형을 추가하고, 도형의 크기와 치수를 설정하며, 프로그래밍
  방식으로 전문 문서를 생성합니다.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Java로 Word에서 도형 그룹화 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  headline: How to group shapes in Word with Java – complete guide
  type: TechArticle
- description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  name: How to group shapes in Word with Java – complete guide
  steps:
  - name: Expected output
    text: '- A file named **GroupShapeDemo.docx** appears in the project folder. -
      Opening the file in Word shows two shapes (a rectangle and an ellipse) that
      are grouped together. - Dragging either shape moves the whole group, confirming
      that **group shapes in word** works as intended.'
  - name: Pro tip
    text: 'When you need to **set shape dimensions** based on dynamic data (e.g.,
      a barcode length), calculate the width/height in points first:'
  - name: What’s next?
    text: '- Explore **add rectangle shape** variations such as rounded corners (`ShapeType.RECTANGLE`
      with `setCornerRadius`). - Combine **group shapes in word** with tables or charts
      for richer documents. - Look into the Aspose.Words API for **text wrapping**
      (`shape.setWrapType(WrapType.SQUARE)`) to control'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Java로 Word에서 도형을 그룹화하는 방법 – 완전 가이드
url: /ko/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word에서 Java로 도형 그룹화하기 – 완전 가이드

프로그래밍 방식으로 **Word에서 도형을 그룹화**해야 한다면, 이 튜토리얼은 바로 실행할 수 있는 솔루션을 제공합니다. **사각형 도형 추가** 방법, 크기 조정, 도형 크기 설정, 그리고 마지막으로 그룹화된 사각형과 타원이 포함된 DOCX 파일을 저장하는 과정을 확인할 수 있습니다.

Word에서 도형을 그룹화하면 복잡한 다이어그램을 만들거나 재사용 가능한 그래픽 구성 요소를 생성하거나, 문서를 나중에 편집할 때 관련 객체들을 함께 유지하는 데 유용합니다. 이 코드는 Aspose.Words for Java 라이브러리를 사용하며, 최신 JDK와 호환되고 Microsoft Word를 설치할 필요가 없습니다.

## 사전 요구 사항

| 요구 사항 | 이유 |
|-------------|--------|
| Java 17 (또는 그 이후 버전) | 이 라이브러리는 최신 Java 런타임을 대상으로 합니다. |
| Aspose.Words for Java (latest version) | 예제에서 사용되는 `Document`, `DocumentBuilder`, `GroupShape`, `Shape` 클래스를 제공합니다. |
| IDE 또는 빌드 도구 (Maven/Gradle) | 샘플을 컴파일하고 실행하기 위해 필요합니다. |
| Java 구문에 대한 기본 지식 | 코드 흐름을 이해하는 데 필요합니다. |

프로젝트에 Aspose.Words 의존성을 추가하세요. Maven의 경우:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version> <!-- Use the latest version -->
</dependency>
```

Gradle의 경우:

```gradle
implementation 'com.aspose:aspose-words:23.10'
```

## 솔루션 개요

이 튜토리얼은 명확한 **문제 → 해결책 → 설명** 패턴을 따릅니다:

1. **새 Word 문서 만들기** 및 `DocumentBuilder` 얻기.  
2. **여러 도형을 담을 `GroupShape` 컨테이너 삽입**.  
3. **사각형 추가**, 너비/높이 설정 (**set shape size** 단계) 및 그룹에 연결.  
4. **타원 추가**, 동일 그룹 내에 배치하고 차원도 설정.  
5. **문서 저장** 디스크에.

각 단계에는 코드 뒤에 있는 **이유**가 포함되어 있어 API가 무엇을 하는지, 그리고 다른 시나리오에 어떻게 적용할 수 있는지 이해할 수 있습니다.

## 단계 1: 문서 및 DocumentBuilder 만들기

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to work with it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**왜 중요한가:** `Document`는 전체 DOCX 파일을 나타내며, `DocumentBuilder`는 저수준 노드 관리를 직접 다루지 않고도 콘텐츠를 삽입할 수 있게 해 주는 도우미입니다. 먼저 이를 생성하면 이후 모든 도형 작업을 위한 깨끗한 캔버스를 확보하게 됩니다.

## 단계 2: GroupShape 컨테이너 삽입

```java
        // Step 2: Insert a GroupShape container that will hold multiple shapes
        GroupShape groupShape = builder.insertGroupShape();
```

`GroupShape`는 그리기 객체를 위한 **폴더**와 같은 역할을 합니다. 그룹을 이동, 회전 또는 삭제하면 모든 자식 도형이 자동으로 따라갑니다. 이것이 **Word에서 도형 그룹화**의 핵심입니다.

## 단계 3: 사각형 도형 추가 – 사각형 도형 코드

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape width in points
        rectangleShape.setHeight(50);   // set shape height in points
        groupShape.appendChild(rectangleShape);
```

- **add rectangle shape** – `Shape` 생성자는 `ShapeType.RECTANGLE`을 받으며, 이는 Aspose.Words에게 사각형 윤곽을 그리도록 지시합니다.  
- **set shape size** – `setWidth`와 `setHeight`는 포인트 단위(1 pt = 1/72 인치)로 **도형 크기**를 정의합니다. 이는 시각적 크기를 제어하는 가장 일반적인 방법입니다.  
- **Why we use `appendChild`** – 사각형을 `GroupShape`에 연결하여 그룹과 함께 이동하도록 합니다.

## 단계 4: 타원 추가 및 그룹 내 위치 지정

```java
        // Step 4: Create an ellipse, set its size and position inside the group, then add it
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);      // set shape width
        ellipseShape.setHeight(80);     // set shape height (making it a circle)
        ellipseShape.setLeft(120);      // position relative to the group container
        groupShape.appendChild(ellipseShape);
```

타원은 단순한 사각형을 넘어 **set shape dimensions**를 보여줍니다. `setLeft`를 호출하여 그룹 내 수평 오프셋을 제어할 수 있으며, 이는 여러 객체를 배치할 때 유용합니다.

## 단계 5: 문서 저장

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

Microsoft Word에서 *GroupShapeDemo.docx*를 열면 하나의 그룹 안에 사각형과 타원이 함께 고정된 것을 볼 수 있습니다. 어느 하나의 도형을 선택하면 전체 그룹이 선택됩니다—이는 **Word에서 도형 그룹화** 시 기대하는 바로 그 동작입니다.

## 전체 실행 가능한 예제

모든 부분을 합치면, IDE에 복사해 사용할 수 있는 전체 소스 파일은 다음과 같습니다:

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will hold the rectangle and ellipse
        GroupShape groupShape = builder.insertGroupShape();

        // Add a rectangle (add rectangle shape) and define its size (set shape size)
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        groupShape.appendChild(rectangleShape);

        // Add an ellipse, set its dimensions, and position it inside the group
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);
        ellipseShape.setHeight(80);
        ellipseShape.setLeft(120);      // horizontal offset relative to the group
        groupShape.appendChild(ellipseShape);

        // Save the document to the local file system
        document.save("GroupShapeDemo.docx");
    }
}
```

### 예상 출력

- **GroupShapeDemo.docx**라는 파일이 프로젝트 폴더에 생성됩니다.  
- Word에서 파일을 열면 두 개의 도형(사각형과 타원)이 함께 그룹화된 것을 볼 수 있습니다.  
- 어느 하나의 도형을 끌면 전체 그룹이 이동하여 **Word에서 도형 그룹화**가 정상적으로 작동함을 확인할 수 있습니다.

## 일반적인 변형 및 경계 상황

| 시나리오 | 변경 내용 | 이유 |
|----------|----------------|-----|
| **다른 도형 유형** (예: 삼각형) | `Shape`를 생성할 때 `ShapeType.TRIANGLE` 또는 다른 enum 값을 사용합니다. | 보다 복잡한 다이어그램을 만들 수 있습니다. |
| **채우기 색상 설정** | 도형을 만든 후 `shape.getFillColor().setColor(Color.BLUE);`를 호출합니다. | 그룹화에 영향을 주지 않으면서 시각적 외관을 개선합니다. |
| **그룹 회전** | `groupShape.setRotationAngle(45);` | 모든 자식 도형을 함께 회전시켜 아이콘 등에 유용합니다. |
| **도형 내부에 텍스트 추가** | `shape.appendChild(new Paragraph(document));`를 호출한 뒤 텍스트가 포함된 `Run`을 추가합니다. | 도형을 라벨이나 말풍선처럼 사용할 수 있습니다. |
| **스트림에 저장** | `ByteArrayOutputStream out = new ByteArrayOutputStream(); document.save(out, SaveFormat.DOCX);` | 문서를 직접 반환하는 웹 서비스에 유용합니다. |

### 전문가 팁

동적 데이터(예: 바코드 길이)를 기반으로 **set shape dimensions**가 필요할 때는 먼저 포인트 단위로 너비/높이를 계산합니다:

```java
double inches = 2.5;
int points = (int)(inches * 72); // 1 inch = 72 points
shape.setWidth(points);
```

## 결론

이제 Java를 사용해 **Word에서 도형을 그룹화**하는 방법, **사각형 도형 추가** 방법, 그리고 간결하고 실무에 바로 사용할 수 있는 코드로 **set shape size**와 **set shape dimensions**를 설정하는 방법을 알게 되었습니다. 위 단계들을 따라 하면 재사용 가능한 그래픽 그룹을 만들고, 자동화된 보고서에 삽입하거나, Word를 직접 열지 않고도 맞춤형 다이어그램 도구를 구축할 수 있습니다.

### 다음 단계는?

- **add rectangle shape**의 변형을 탐색해 보세요. 예: 둥근 모서리(`ShapeType.RECTANGLE`와 `setCornerRadius` 사용).  
- **Word에서 도형 그룹화**를 표나 차트와 결합해 더 풍부한 문서를 만들어 보세요.  
- Aspose.Words API에서 **text wrapping**(`shape.setWrapType(WrapType.SQUARE)`)을 살펴보아 주변 텍스트가 그룹화된 그래픽과 어떻게 상호 작용하는지 제어하세요.

자유롭게 실험하고, **사각형 도형 코드**를 적용해 보며, 결과를 공유하세요


## 다음에 배워야 할 내용은?

다음 튜토리얼들은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 자료는 단계별 설명과 함께 완전한 동작 코드 예제를 포함하여 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움을 줍니다.

- [Word 문서 만들기 Java – 그림자 효과가 있는 사각형 도형 추가](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Java로 Word에서 사각형 도형 만들기 – 전체 가이드](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [.NET용 Aspose.Words를 사용한 Word 문서에서 그룹 도형 만들기](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}