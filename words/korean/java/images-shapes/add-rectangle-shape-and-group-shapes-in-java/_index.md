---
category: general
date: 2026-11-22
description: Java를 사용해 Word 문서에 사각형 도형을 추가하고, 도형 크기를 설정하며, 여러 도형을 그룹화하고, 도형을 그룹에 효율적으로
  추가합니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add rectangle shape
- set shape size
- group multiple shapes
- set shape dimensions
- append shape to group
language: ko
lastmod: 2026-11-22
og_description: Java를 사용하여 Word 문서에 사각형 도형을 추가하고, 도형 크기를 설정한 뒤 여러 도형을 그룹화하고, 그룹에 도형을
  추가하는 작업을 하나의 워크플로우로 수행합니다.
og_image_alt: Screenshot showing a rectangle shape added and grouped in a Word document
  using Java
og_title: Java에서 사각형 도형 추가 및 도형 그룹화 – 전체 가이드
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  headline: Add rectangle shape and group shapes in Java
  type: TechArticle
- description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  name: Add rectangle shape and group shapes in Java
  steps:
  - name: Insert the rectangle shape
    text: The rectangle is the first visual element we want to place inside the document.
      By using the `Shape` constructor with `ShapeType.RECTANGLE`, you get a fully
      editable object.
  - name: Set shape size and dimensions
    text: Set shape size and dimensions
  - name: Create a group shape container
    text: '```java // Step 6: Create a group shape that will hold the rectangle and
      other shapes GroupShape groupShape = builder.insertGroupShape(); ```'
  - name: Append shape to group
    text: Append shape to group
  - name: Save the document
    text: '```java // Save the result to a new file doc.save("output.docx"); } } ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shape manipulation
title: Java에서 사각형 도형을 추가하고 도형을 그룹화하기
url: /ko/java/images-shapes/add-rectangle-shape-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java에서 사각형 모양 추가 및 모양 그룹화

Word 문서에 **사각형 모양을 추가**해야 할 때, 이 가이드는 정확한 단계별 절차를 안내합니다. 또한 **모양 크기 설정**, **여러 모양을 그룹화**, **그룹에 모양 추가**하는 방법을 IDE를 떠나지 않고 배울 수 있습니다.

DOCX 파일 내부에서 벡터 그래픽을 다루는 것은 종종 별도 API를 오가며 작업하는 것처럼 느껴집니다. 이 튜토리얼을 마치면 사각형, 타원 및 필요에 따라 추가적인 모양을 생성하고, 이를 하나의 객체로 묶어 함께 이동할 수 있는 단일, 독립 실행형 프로그램을 만들 수 있습니다. Aspose.Words for Java 외에 별도의 도구는 필요하지 않습니다.

## Prerequisites

시작하기 전에 다음이 준비되어 있는지 확인하세요:

* Java 17 이상이 설치되어 있어야 합니다.
* Maven 3.8+ (또는 Gradle) 를 사용해 종속성을 관리합니다.
* 유효한 Aspose.Words for Java 라이선스(평가판도 테스트용으로 사용 가능)​.
* IntelliJ IDEA 또는 VS Code와 같은 IDE(텍스트 편집기라도 무방).

이 요구 사항은 코드를 현대적인 개발 환경 어디서든 컴파일하고 실행할 수 있게 해 줍니다.

## Step 1: Set up the Maven project

새 Maven 프로젝트를 만들거나 기존 `pom.xml`에 Aspose.Words 종속성을 추가합니다:

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>shape‑demo</artifactId>
  <version>1.0.0</version>

  <dependencies>
    <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.12</version>
    </dependency>
  </dependencies>
</project>
```

이 종속성은 `Document`, `DocumentBuilder`, `Shape`, `GroupShape` 등 문서 조작에 필요한 모든 클래스를 포함합니다. `mvn compile`을 실행하면 Maven이 JAR 파일을 자동으로 다운로드합니다.

## Step 2: Load the document and create a DocumentBuilder

`DocumentBuilder`는 콘텐츠 삽입을 위한 유창한 API를 제공합니다. 기존 DOCX 파일을 로드하거나 빈 문서에서 시작합니다:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document or create a new one
        Document doc = new Document("input.docx");          // replace with your path
        DocumentBuilder builder = new DocumentBuilder(doc);
```

빌더를 일찍 생성하면 문서 시작 부분에 커서가 위치해 모양 삽입 준비가 됩니다.

## Add rectangle shape to a Word document

### Step 3: Insert the rectangle shape

문서 안에 배치하려는 첫 번째 시각 요소가 사각형입니다. `Shape` 생성자에 `ShapeType.RECTANGLE`을 사용하면 완전히 편집 가능한 객체를 얻을 수 있습니다.

```java
        // Step 3: Insert a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        // The shape is not yet sized; we will set its dimensions next.
```

이 시점에 사각형을 추가해도 크기가 정의되고 컨테이너에 추가되기 전까지 레이아웃에 영향을 주지 않습니다.

### Set shape size and dimensions

#### Step 4: Define width and height

모양의 차원을 설정하면 페이지에 표시되는 방식이 결정됩니다. 너비와 높이 값은 포인트 단위(1 pt = 1/72 in)로 측정됩니다.

```java
        // Step 4: Set shape size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

디자인 요구사항에 맞게 숫자를 조정할 수 있습니다. 동일한 메서드는 모든 `Shape` 인스턴스에 적용되므로 원, 화살표 또는 사용자 정의 그림에도 재사용할 수 있습니다.

#### Step 5: Insert the rectangle into the document

이제 사각형에 크기가 지정되었으니 페이지에 배치합니다. `DocumentBuilder`의 `insertShape` 메서드는 현재 커서 위치에 모양을 추가합니다.

```java
        // Insert the rectangle at the builder’s current position
        builder.insertShape(rectangle);
```

이 단계에서 사각형은 페이지에 단독으로 나타납니다. 다음 단계에서는 다른 모양과 결합하는 방법을 보여줍니다.

## Group multiple shapes together

모양을 그룹화하면 하나의 단위로 이동, 회전 또는 크기 조정이 가능합니다. 복잡한 다이어그램을 만들 때 특히 유용합니다.

### Step 6: Create a group shape container

```java
        // Step 6: Create a group shape that will hold the rectangle and other shapes
        GroupShape groupShape = builder.insertGroupShape();
```

`insertGroupShape` 호출은 문서에 빈 컨테이너를 추가합니다. 이 컨테이너에 추가된 모든 모양은 그룹의 일부가 됩니다.

### Append shape to group

#### Step 7: Add the rectangle to the group

```java
        // Append the previously created rectangle to the group
        groupShape.appendChild(rectangle);
```

추가하면 사각형이 문서 본문에서 그룹의 내부 컬렉션으로 이동합니다. 이제 사각형은 그룹 변환을 따릅니다.

#### Step 8: Add an ellipse for demonstration

```java
        // Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(80);
        ellipse.setHeight(80);
        groupShape.appendChild(ellipse);
```

타원은 사각형과 동일한 좌표 공간을 공유하므로 필요에 따라 `setLeft`와 `setTop` 속성을 조정해 시각적으로 정렬할 수 있습니다.

### Step 9: Save the document

```java
        // Save the result to a new file
        doc.save("output.docx");
    }
}
```

프로그램을 실행하면 `output.docx`가 생성됩니다. Microsoft Word 또는 LibreOffice에서 파일을 열면 사각형과 타원이 함께 그룹화된 것을 확인할 수 있습니다. 두 모양 중 하나를 선택하면 전체 그룹이 강조 표시되어 **그룹에 모양 추가**가 성공했음을 보여줍니다.

![Add rectangle shape example in Java](image.png){alt="Java에서 사각형 모양 추가 예시"}

*스크린샷은 하나의 그룹 안에 사각형과 타원이 포함되어 공동으로 조작할 수 있음을 보여줍니다.*

## Why this approach matters

* **Single source of truth** – 그룹을 만들기 전에 모든 모양 속성을 설정하므로 레이아웃 오류를 방지합니다.
* **Reusability** – 동일한 `setWidth`/`setHeight` 메서드가 모든 모양에 적용되므로 화살표, 별, 사용자 정의 SVG 등으로 예제를 확장할 수 있습니다.
* **Performance** – 그룹화는 Word 렌더러가 처리해야 할 그리기 객체 수를 줄여 대형 문서의 열기 속도를 향상시킵니다.
* **Maintainability** – 모양 생성과 그룹화 로직을 함께 유지함으로써 향후 개발자가 차원이나 새로운 모양을 추가할 때 관련 코드를 일일이 찾을 필요가 없습니다.

## Common variations and edge cases

| Scenario | Adjustment |
|----------|------------|
| **Different units** | `PointsToPixels` 변환을 사용하거나 인라인 배치를 위해 `Shape.setWrapType(WrapType.INLINE)`을 설정합니다. |
| **Rotating the group** | `groupShape.setRotation(45);`를 호출해 모든 자식 모양을 45° 회전시킵니다. |
| **Adding text to a shape** | 크기 설정 후 `Shape.setText("Label");`을 사용합니다. |
| **Dynamic sizing** | `doc.getFirstSection().getPageSetup().getPageWidth()` 로 페이지 크기를 가져와 비례적으로 모양 크기를 계산합니다. |

이러한 변형은 핵심 패턴—**사각형 모양 추가**, **모양 크기 설정**, **여러 모양 그룹화**, **그룹에 모양 추가**—가 다양한 실무 요구에 어떻게 적용될 수 있는지를 보여줍니다.

## Conclusion

이제 Java를 사용해 Word 문서에 **사각형 모양을 추가**, **모양 크기 설정**, **여러 모양을 그룹화**, 그리고 **그룹에 모양 추가**하는 방법을 깔끔하고 유지보수하기 쉬운 방식으로 알게 되었습니다. 전체 예제는 단일 실행 가능한 클래스로 컴파일되며, 생성된 DOCX 파일은 기대한 결과를 보여줍니다.

다음 단계로 할 수 있는 일:

* 각 모양에 텍스트 레이블이나 하이퍼링크 추가
* 계층형 다이어그램 작성을 위해 그룹을 중첩
* 모양 그룹을 유지한 채 문서를 PDF로 내보내기

다양한 차원, 색상 및 추가 모양 유형을 실험해 보세요. 모양 조작을 마스터하면 자동 보고서 생성, 동적 다이어그램, 풍부한 문서 경험을 Java 코드만으로 구현할 수 있는 문을 열게 됩니다.

## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스는 완전한 작동 코드 예제와 단계별 설명을 포함해 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하도록 돕습니다.

- [Insert Rectangle Shape in Java – Group and Position Shapes](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [How to create and insert ellipse and rectangle shapes inside a group shape in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Create rectangle shape in a Word document using Java](/words/english/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}