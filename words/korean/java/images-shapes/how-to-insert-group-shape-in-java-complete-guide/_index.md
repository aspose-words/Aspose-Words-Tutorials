---
category: general
date: 2026-07-16
description: Aspose.Words를 사용하여 Java에서 그룹 도형을 삽입하는 방법 – 사각형 도형 추가, 도형 크기 설정, 그리고 색상이
  있는 사각형과 원 만들기.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert group
- add rectangle shape
- set shape dimensions
- create colored rectangle
- create colored circle
language: ko
lastmod: 2026-07-16
og_description: 'Java에서 그룹 도형 삽입 방법: 사각형 도형 추가, 도형 크기 설정, 그리고 Aspose.Words를 사용해 색상
  사각형 및 원 만들기 실전 가이드.'
og_image_alt: Screenshot showing a grouped blue rectangle and red circle in a Java‑generated
  Word document
og_title: Java에서 그룹 도형 삽입 – 전체 Aspose.Words 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  headline: how to insert group shape in Java – Complete Guide
  type: TechArticle
- description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  name: how to insert group shape in Java – Complete Guide
  steps:
  - name: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
    text: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
  - name: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
    text: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
  - name: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
    text: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
  - name: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
    text: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
  - name: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
    text: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shapes
- Document Automation
- Group Shapes
title: Java에서 그룹 도형을 삽입하는 방법 – 완전 가이드
url: /ko/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java에서 그룹 도형 삽입 방법 – 완전 가이드

Java를 사용하여 Word 문서에 **그룹 도형을 삽입하는 방법**을 궁금해 본 적이 있나요? 당신만 그런 것이 아닙니다. 보고서 생성기나 동적 전단지 제작기를 만들고 있든, 도형을 그룹화하면 레이아웃이 깔끔해지고 코드 관리가 쉬워집니다.

이 튜토리얼에서는 Aspose.Words 라이브러리를 사용하여 **직사각형 도형 추가**, **도형 크기 설정**, **색상 직사각형 만들기** 및 **색상 원 만들기**의 정확한 단계를 안내합니다. 마지막에는 파란색 직사각형과 빨간색 원이 그룹 안에 깔끔하게 묶인 .docx 파일을 생성하는 실행 가능한 프로그램을 얻을 수 있습니다.

## 필수 조건

- Java 17(또는 최신 JDK) 설치 및 설정
- Maven 또는 Gradle을 사용하여 종속성 관리
- Aspose.Words for Java 23.9 이상 – Maven Central에서 다운로드할 수 있습니다.
- Java 구문에 대한 기본 이해 – 특별한 지식은 필요 없습니다

필요한 항목이 부족하다면 Oracle 사이트에서 JDK를 다운로드하고 `pom.xml`에 Aspose.Words 종속성을 추가하세요:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

이제 기본 준비가 끝났으니, 직접 해봅시다.

## 그룹 도형 삽입 방법 – 개요

핵심 아이디어는 간단합니다: `Document`를 만들고, `DocumentBuilder`를 연 뒤, **그룹 도형**을 삽입하고, 그 그룹 안에 개별 도형(직사각형과 원)을 배치합니다. 그룹은 컨테이너 역할을 하므로 나중에 이동하면 내부 모든 도형이 함께 이동해 복잡한 레이아웃에 이상적입니다.

아래는 완전한 실행 가능한 코드입니다. `InsertGroupShapeDemo`라는 새 Java 클래스에 복사‑붙여넣기 하면 됩니다.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to insert a group shape, add a rectangle and a circle,
 * set their dimensions, and apply colors using Aspose.Words for Java.
 */
public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape that will contain other shapes.
        Shape group = builder.insertGroupShape();

        // Step 3: Create a blue rectangle, set its size and position, and add it to the group.
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);          // set shape dimensions – width
        rectangle.setHeight(50.0);          // set shape dimensions – height
        rectangle.setLeft(20.0);            // X‑coordinate inside the group
        rectangle.setTop(20.0);             // Y‑coordinate inside the group
        rectangle.getFill().setForeColor(Color.BLUE); // create colored rectangle
        group.appendChild(rectangle);       // add rectangle shape to the group

        // Step 4: Create a red circle, set its size and position, and add it to the same group.
        Shape circle = new Shape(doc, ShapeType.ELLIPSE);
        circle.setWidth(60.0);              // set shape dimensions – width (diameter)
        circle.setHeight(60.0);             // set shape dimensions – height (diameter)
        circle.setLeft(150.0);              // X‑coordinate inside the group
        circle.setTop(20.0);                // Y‑coordinate inside the group
        circle.getFill().setForeColor(Color.RED); // create colored circle
        group.appendChild(circle);          // add circle shape to the group

        // Step 5: Save the document with the grouped shapes.
        doc.save("GroupShapeDemo.docx");
        System.out.println("Document saved successfully.");
    }
}
```

> **Pro tip:** `setLeft`와 `setTop` 값은 페이지가 아니라 그룹의 원점을 기준으로 합니다. 따라서 전체 그룹을 재배치하는 것이 훨씬 쉬워집니다.

### 무슨 일이 일어났나요?

1. **Document & Builder** – 빈 Word 파일과 콘텐츠 삽입을 담당하는 `DocumentBuilder`를 생성합니다.  
2. **Group Shape** – `builder.insertGroupShape()`가 컨테이너를 만듭니다. 그림 객체를 담는 폴더와 같은 역할입니다.  
3. **Blue Rectangle** – `RECTANGLE` 타입의 `Shape`를 인스턴스화하고, 크기와 위치를 지정한 뒤 파란색으로 채웁니다 – 이것이 **색상 직사각형 만들기** 단계입니다.  
4. **Red Circle** – 동일한 패턴을 사용하지만 `ELLIPSE`를 이용해 완전한 원을 만들고 빨간색으로 채웁니다 – 이것이 **색상 원 만들기** 단계입니다.  
5. **Saving** – 마지막으로 모든 내용을 `GroupShapeDemo.docx`에 저장합니다.

프로그램을 실행(`mvn compile exec:java -Dexec.mainClass=InsertGroupShapeDemo`)하고 결과 파일을 열어 보세요. 왼쪽에 파란색 직사각형, 오른쪽에 빨간색 원이 하나의 그룹 상자 안에 고정된 것을 확인할 수 있습니다.

## 직사각형 도형 추가

그룹 없이 단순히 직사각형만 필요하다면 `insertGroupShape()` 호출을 건너뛰고 직사각형을 문서 본문에 바로 추가하면 됩니다. 하지만 그룹을 사용하면 여러 도형을 한 번에 이동, 회전 또는 삭제할 수 있는 유연성을 얻을 수 있습니다.

```java
Shape rect = new Shape(doc, ShapeType.RECTANGLE);
rect.setWidth(120);
rect.setHeight(70);
rect.getFill().setForeColor(Color.GREEN);
builder.insertNode(rect);
```

여기서는 **직사각형 도형 추가** 로직을 사용했습니다. 직사각형은 페이지에 독립적인 객체로 나타납니다. 실제 프로젝트에서는 상대 위치를 유지하기 위해 그룹을 사용하는 것이 일반적입니다.

## 도형 크기 설정

`setWidth`와 `setHeight` 같은 메서드를 볼 때는 **포인트**(1/72 인치) 단위임을 기억하세요. 밀리미터 단위를 선호한다면 먼저 변환해야 합니다:

```java
double mmToPoints = 72.0 / 25.4;
double widthInMm = 50; // 50 mm
rectangle.setWidth(widthInMm * mmToPoints);
rectangle.setHeight(30 * mmToPoints);
```

이 스니펫은 단위 변환과 함께 **도형 크기 설정**을 보여줍니다 – 디자인 사양이 UI 목업에서 미터법을 사용할 때 유용합니다.

## 색상 직사각형 만들기

도형에 색을 입히는 것은 `getFill().setForeColor()`를 호출하는 것만큼 간단합니다. `java.awt.Color` 객체를 아무거나 전달할 수 있습니다. 그라데이션이 필요하면 시작 색은 `setForeColor`, 끝 색은 `setBackColor`를 사용하세요.

```java
rectangle.getFill().setForeColor(Color.MAGENTA);
rectangle.getFill().setBackColor(Color.YELLOW);
rectangle.getFill().setFillType(FillType.GRADIENT);
```

이렇게 하면 **색상 직사각형 만들기**를 단색 대신 그라데이션 채우기로 빠르게 구현할 수 있습니다.

## 색상 원 만들기

원은 가로와 세로가 같은 타원에 불과합니다. 색상 적용 로직은 동일합니다:

```java
circle.getFill().setForeColor(new Color(255, 165, 0)); // orange
```

투명 채우기가 필요하면 알파 채널을 설정하세요:

```java
circle.getFill().setForeColor(new Color(0, 0, 255, 128)); // semi‑transparent blue
```

이제 **색상 원 만들기** 기술을 완전히 마스터했습니다.

## 문서 저장

Aspose.Words는 DOCX, PDF, HTML, PNG 등 다양한 포맷으로 출력할 수 있습니다. 이번 데모에서는 벡터 도형을 완벽히 보존하는 DOCX 형식을 사용합니다.

```java
doc.save("GroupShapeDemo.pdf", SaveFormat.PDF);
```

`SaveFormat`만 바꾸면 동일한 그룹 아트워크를 PDF 버전으로도 손쉽게 생성할 수 있습니다.

## 일반적인 함정 및 회피 방법

- **도형을 그룹에 추가하는 것을 잊었나요?** 도형은 페이지에 표시되지만 그룹과 함께 움직이지 않습니다. 항상 `group.appendChild(yourShape)`를 호출하세요.

## 다음에 배울 내용은?

다음 튜토리얼은 이 가이드에서 다룬 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스에는 단계별 설명과 완전한 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}