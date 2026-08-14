---
category: general
date: 2026-08-14
description: Aspose.Words를 사용하여 Java로 Word에서 도형을 그룹화합니다. 사각형 도형을 만들고, 도형 크기를 설정하며,
  빈 Word 문서에서 여러 도형을 그룹화하는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create rectangle shape
- set shape dimensions
- group multiple shapes
- build blank word document
language: ko
lastmod: 2026-08-14
og_description: Aspose.Words for Java를 사용하여 Word에서 도형을 그룹화합니다. 빈 Word 문서를 만든 뒤 사각형
  도형을 생성하고 도형 크기를 설정하면 몇 분 안에 여러 도형을 그룹화할 수 있습니다.
og_image_alt: Screenshot showing grouped rectangle shapes in a Word document created
  with Java
og_title: Word에서 도형 그룹화 – 개발자를 위한 Java 예제
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to create
    rectangle shape, set shape dimensions, and group multiple shapes in a blank Word
    document.
  headline: Group shapes in Word – complete programming guide
  type: TechArticle
- questions:
  - answer: Overlap is allowed; Word will render them in the order they were added.
      Use `setZOrder` if you need explicit stacking.
    question: What if the shapes overlap?
  - answer: No. A `GroupShape` is confined to a single page because its coordinate
      system is page‑relative.
    question: Can I group shapes across different pages?
  - answer: Each child keeps its own formatting (fill color, line style). To apply
      a uniform style, iterate over `groupShape.getChildNodes()` and set properties
      programmatically.
    question: Do grouped shapes inherit formatting?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Word에서 도형 그룹화 – 완전 프로그래밍 가이드
url: /ko/java/images-shapes/group-shapes-in-word-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word에서 도형 그룹화 – 완전 프로그래밍 가이드

Word에서 **도형을 그룹화**해야 할 경우, 이 튜토리얼은 Java와 Aspose.Words를 사용한 전체 과정을 단계별로 안내합니다. **빈 Word 문서 만들기**, **직사각형 도형 생성**, **도형 크기 설정**, 그리고 마지막으로 **여러 도형을 그룹화**하여 하나의 객체처럼 동작하도록 하는 방법을 배울 수 있습니다.

Word 파일에서 도형을 다루는 것은 마치 캔버스에 그림을 그리지만 붓이 없는 느낌일 수 있습니다. 이 가이드를 끝까지 따라 하면 보고서, 청구서, 맞춤 템플릿 등 어떤 Java 프로젝트에도 바로 삽입할 수 있는 재사용 가능한 코드 스니펫을 얻게 됩니다.

## 준비 사항

- Java 8 이상
- Aspose.Words for Java (최신 버전, 예: 24.9)
- IntelliJ IDEA 또는 Eclipse 같은 IDE
- 객체‑지향 프로그래밍에 대한 기본 지식

위 모든 사전 조건은 무료로 설치할 수 있으며, 아래 코드는 단일 Maven 의존성만으로 컴파일됩니다:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## 1단계: 빈 Word 문서 만들고 빌더 초기화

먼저 **빈 Word 문서를 만들**어야 합니다. 이렇게 하면 나중에 도형을 삽입할 수 있는 깨끗한 캔버스를 확보하게 됩니다.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder lets you add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document`는 전체 *.docx* 파일을 나타내고, `DocumentBuilder`는 단락, 표, 도형 등을 삽입하는 도우미 역할을 합니다. 두 객체를 초기화하는 것이 모든 Word 자동화 작업의 기본이 됩니다.

## 2단계: 그룹 도형 컨테이너 삽입

**그룹 도형**은 다른 도형들을 담을 수 있는 폴더와 같은 역할을 합니다. 먼저 고정 크기 400 pt × 200 pt인 컨테이너를 생성합니다.

```java
        // Insert a group shape that will hold other shapes (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);
```

`insertGroupShape` 메서드는 `GroupShape` 객체를 반환합니다. 이후 단일 단위로 다루고 싶은 모든 도형은 이 객체에 `appendChild` 해야 합니다.

## 3단계: 직사각형 도형 생성 및 크기 설정

이제 **직사각형 도형** 객체를 만들고, 크기를 지정한 뒤 그룹 안에 배치합니다. 이 단계에서는 **도형 크기 설정**을 정확히 하는 방법도 보여줍니다.

```java
        // ---- First rectangle -------------------------------------------------
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);   // set shape dimensions: width = 150 pt
        rectangle1.setHeight(100);  // set shape dimensions: height = 100 pt
        rectangle1.setTop(20);      // vertical offset inside the group
        rectangle1.setLeft(20);     // horizontal offset inside the group
        groupShape.appendChild(rectangle1); // add to the group

        // ---- Second rectangle ------------------------------------------------
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);    // place it beside the first rectangle
        groupShape.appendChild(rectangle2);
```

두 직사각형은 동일한 크기를 가지지만 `left` 속성이 달라 나란히 표시됩니다. `setTop`과 `setLeft` 값을 변경하면 원하는 레이아웃을 자유롭게 구성할 수 있습니다.

## 4단계: 그룹화된 직사각형이 포함된 문서 저장

도형을 그룹에 넣은 후에는 `Document`를 저장하기만 하면 됩니다. 결과 파일을 열면 선택했을 때 두 직사각형이 함께 움직이는 것을 확인할 수 있습니다.

```java
        // Save the document to disk
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

프로그램을 실행하면 작업 디렉터리에 `GroupShape.docx`가 생성됩니다. Microsoft Word에서 파일을 열고 하나의 직사각형을 선택하면 전체 그룹이 하나의 단위로 이동하는 것을 볼 수 있습니다.

![Group shapes in Word example](group-shapes.png){alt="Word에서 그룹 도형 예시"}

*그림: Word 문서에서 두 개의 직사각형 도형이 함께 그룹화된 모습.*

## 팁: 동일한 그룹 도형 재사용하기

추후에 원형, 텍스트 상자 등 추가 도형을 넣어야 한다면 `groupShape`에 대한 참조를 유지하고 계속해서 `appendChild`를 호출하세요. 이렇게 하면 컨테이너를 다시 만들 필요가 없으며 모든 구성원이 동기화된 상태를 유지합니다.

```java
        // Example: add a third shape later
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(120);
        ellipse.setHeight(80);
        ellipse.setTop(130);
        ellipse.setLeft(140);
        groupShape.appendChild(ellipse);
```

## 엣지 케이스 및 흔히 묻는 질문

- **도형이 겹치면 어떻게 되나요?** 겹침은 허용됩니다. Word는 추가된 순서대로 렌더링합니다. 명시적인 쌓임 순서가 필요하면 `setZOrder`를 사용하세요.
- **다른 페이지에 있는 도형도 그룹화할 수 있나요?** 아니요. `GroupShape`는 좌표계가 페이지‑기준이므로 하나의 페이지에만 제한됩니다.
- **그룹화된 도형이 서식을 상속받나요?** 각 자식은 자체 서식(채우기 색, 선 스타일)을 유지합니다. 일관된 스타일을 적용하려면 `groupShape.getChildNodes()`를 순회하면서 프로그래밍적으로 속성을 설정하면 됩니다.

## 전체 소스 코드 (참고용)

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // 1. Build blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert group shape container (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);

        // 3. Create first rectangle and set shape dimensions
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);
        rectangle1.setHeight(100);
        rectangle1.setTop(20);
        rectangle1.setLeft(20);
        groupShape.appendChild(rectangle1);

        // 4. Create second rectangle and set shape dimensions
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);
        groupShape.appendChild(rectangle2);

        // 5. Save the document containing the grouped rectangles
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

프로그램을 실행하면 두 직사각형이 **그룹화**된 DOCX 파일이 생성됩니다. 어느 하나를 선택해도 두 도형이 함께 움직이며, **여러 도형을 그룹화**하는 데 성공했음을 확인할 수 있습니다.

## 결론

이제 Java를 사용해 **Word에서 도형을 그룹화**하는 방법을 알게 되었습니다. **빈 Word 문서 만들기**, **직사각형 도형 생성**, **도형 크기 설정**, 그리고 **여러 도형을 하나의 이동 가능한 객체로 그룹화**하는 전체 흐름을 익혔습니다. 이 패턴은 도형 수에 관계없이 확장 가능하며, 텍스트, 이미지, 차트와 결합해 풍부한 프로그래밍 문서를 만들 수 있습니다.

### 다음 단계는?

- **여러 도형을 그룹화**하면서 서로 다른 유형(타원, 화살표, 텍스트 상자)도 시도해 보세요.
- `shape.getFillColor()`와 `shape.getLine().setColor()`를 호출해 채우기 색이나 테두리 색을 적용해 보세요.
- 구조화된 보고서를 위해 테이블 셀에 그룹 도형을 삽입해 보세요.
- 메일 병합과 결합해 브랜드 그래픽이 포함된 개인화 계약서를 자동 생성해 보세요.

자유롭게 실험하고, 크기를 조정하거나 추가 콘텐츠를 삽입해 보세요. 그룹화를 마스터하면 Word 자동화 스크립트가 훨씬 유연하고 유지 보수가 쉬워집니다. 즐거운 코딩 되세요!

## 다음에 배워야 할 내용은?

다음 튜토리얼들은 이 가이드에서 다룬 기술을 기반으로 하며, 단계별 설명과 완전한 코드 예제를 제공합니다. 이를 통해 추가 API 기능을 마스터하고 다양한 구현 방식을 탐색할 수 있습니다.

- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}