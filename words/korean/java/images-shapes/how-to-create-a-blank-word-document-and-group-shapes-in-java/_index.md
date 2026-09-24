---
category: general
date: 2026-09-24
description: Java에서 빈 Word 문서를 만드는 방법과 Aspose.Words를 사용하여 사각형 및 선과 같은 도형을 그룹화하는 방법을
  배웁니다. 단계별 코드가 포함되어 있습니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shapes
- add rectangle shape
- group shapes in word
- set shape size
language: ko
lastmod: 2026-09-24
og_description: Java에서 빈 Word 문서를 만들고 Aspose.Words를 사용하여 도형을 그룹화하고, 사각형 도형을 추가하며,
  도형 크기를 설정하는 방법을 배웁니다.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: 빈 Word 문서를 만들고 Java에서 도형을 그룹화하기 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create a blank Word document in Java and group shapes
    like rectangles and lines using Aspose.Words. Includes step‑by‑step code.
  headline: How to create a blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Java에서 빈 Word 문서를 만들고 도형을 그룹화하는 방법
url: /ko/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java에서 빈 Word 문서를 만들고 도형을 그룹화하는 방법

**빈 Word 문서를 만들고** 여러 개의 그리기 개체를 정리해야 할 때, 이 가이드는 정확한 방법을 보여줍니다. Aspose.Words for Java를 사용하면 그룹 도형을 삽입하고, 사각형 도형을 추가하고, 선을 그리며, 각 도형의 크기와 위치를 제어할 수 있는 단일 실행 가능한 프로그램을 만들 수 있습니다.

문서를 초기화하는 단계부터 최종 `.docx` 파일을 저장하는 단계까지 모든 과정을 차근차근 따라가 보세요. 끝까지 진행하면 **도형을 그룹화하는 방법**, **사각형 도형 추가**, **도형 크기 설정**을 이해하게 되어 Word 파일을 원하는 대로 만들 수 있습니다.

## 사전 요구 사항

- Java 17 이상 (코드는 최신 JDK에서 컴파일됩니다)
- Aspose.Words for Java 라이브러리 ( [Aspose 웹사이트](https://products.aspose.com/words/java) 에서 다운로드)
- Aspose.Words JAR를 클래스패스에 추가할 수 있는 IDE 또는 빌드 도구 (Maven/Gradle)
- Java 문법에 대한 기본 지식

> **Pro tip:** 의존성 관리를 위해 Maven을 사용하세요; `pom.xml`에 `com.aspose:aspose-words:23.12` (또는 최신 버전)를 추가합니다.

## 1단계: 빈 Word 문서 만들기

첫 번째 작업은 **빈 Word 문서를 만드는 것**입니다. 이렇게 하면 나중에 도형을 삽입할 수 있는 깨끗한 캔버스를 확보할 수 있습니다.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document document = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(document);
```

*왜 중요한가:* `Document` 객체는 전체 `.docx` 파일을 나타냅니다. 빈 문서에서 시작하면 추가되는 도형에 숨겨진 서식이 방해되지 않습니다.

## 2단계: 그룹 도형 삽입 – 여러 객체를 담는 컨테이너

**그룹 도형**은 여러 도형을 한 번에 이동, 크기 조정 또는 회전할 수 있게 해 주는 컨테이너 역할을 합니다. 이것이 Word에서 **도형을 그룹화하는 방법**의 핵심입니다.

```java
        // Insert a group shape of width 300 points and height 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

*설명:* `insertGroupShape` 메서드는 `GroupShape` 객체를 생성하고 현재 커서 위치에 배치합니다. 이후 `appendChild` 로 이 그룹에 추가되는 모든 도형은 하나의 단위로 취급됩니다.

## 3단계: 사각형 도형 추가 및 크기 설정

이제 **사각형 도형을 그룹에 추가하고** **도형 크기를 정확히 설정**합니다.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);   // set shape width
        rectangle.setHeight(100.0);  // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Add the rectangle to the group
        group.appendChild(rectangle);
```

*왜 크기를 설정해야 하는가:* 너비와 높이는 페이지에 사각형이 어떻게 보일지를 결정합니다. `setLeft` 와 `setTop` 메서드는 사각형을 그룹의 원점에 상대적으로 배치해 픽셀 단위의 레이아웃 제어를 가능하게 합니다.

## 4단계: 선 도형 추가 및 치수 구성

선은 또 다른 일반적인 그리기 개체입니다. 우리는 **사각형 도형**과 동일한 논리를 선에도 적용해 동일한 크기 원칙이 적용된다는 것을 보여줍니다.

```java
        // Create a line shape
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);   // line length
        line.setHeight(0.0);    // height is zero for a horizontal line
        line.setLeft(20.0);
        line.setTop(130.0);

        // Add the line to the same group
        group.appendChild(line);
```

*핵심 포인트:* 선은 높이가 없지만 `setWidth` 로 길이를 정의합니다. 위치 지정(`setLeft`, `setTop`)은 다른 도형과 동일한 좌표계를 사용합니다.

## 5단계: 그룹화된 도형을 포함한 문서 저장

마지막으로 문서를 저장해 변경 사항을 영구히 기록합니다. 이렇게 하면 Microsoft Word에서 결과를 확인할 수 있는 `.docx` 파일이 생성됩니다.

```java
        // Save the document to disk
        document.save("GroupShapeDemo.docx");
    }
}
```

**예상 결과:** `GroupShapeDemo.docx` 를 열면 빈 페이지에 그룹화된 사각형과 선이 표시됩니다. 어느 하나를 선택하면 전체 그룹이 선택되어 함께 이동할 수 있습니다.

## 흔히 묻는 질문 및 엣지 케이스 처리

| Question | Answer |
|----------|--------|
| *Can I add more than two shapes to the group?* | Yes. Call `group.appendChild(yourShape)` for each additional shape. |
| *What if I need a different unit (e.g., centimeters) for size?* | Aspose.Words uses points (1 point = 1/72 inch). Convert using `Points = centimeters * 28.3465`. |
| *Will the group retain its layout when the document is opened on another machine?* | Absolutely. All size and position data are stored in the `.docx` file, making the layout portable. |
| *How do I ungroup shapes later?* | Retrieve the `GroupShape` object, then iterate over `group.getChildNodes(NodeType.SHAPE, true)` and move each child out of the group. |
| *What if I need to rotate the whole group?* | Use `group.setRotationAngle(double angleInDegrees)` before saving. |

## 전체 실행 가능한 예제

아래는 IDE에 복사‑붙여넣기 할 수 있는 완전한 프로그램입니다. 필요한 모든 import와 주석이 포함되어 있습니다.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape (container)
        GroupShape group = builder.insertGroupShape(300.0, 200.0);

        // Step 3: Add a rectangle shape and set its size
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);
        rectangle.setHeight(100.0);
        rectangle.setLeft(20.0);
        rectangle.setTop(20.0);
        group.appendChild(rectangle);

        // Step 4: Add a line shape and configure its dimensions
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);
        line.setHeight(0.0);
        line.setLeft(20.0);
        line.setTop(130.0);
        group.appendChild(line);

        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

프로그램을 실행하고 Microsoft Word에서 `GroupShapeDemo.docx` 를 열면 설명대로 그룹화된 도형이 정확히 표시됩니다.

## 결론

이제 **빈 Word 문서를 만들고**, **Word에서 도형을 그룹화하며**, **사각형 도형을 추가하고**, **도형 크기를 설정**하는 방법을 Aspose.Words for Java를 이용해 알게 되었습니다. 도형을 `GroupShape` 안에 넣으면 전체 위치, 크기, 회전을 한 번에 제어할 수 있어 다이어그램, 흐름도, 맞춤형 그래픽을 자동 보고서에 삽입할 때 매우 유용합니다.

**다음 단계:**  
- 사진이나 텍스트 상자와 같은 더 복잡한 객체와 **도형을 그룹화하는 방법**을 탐색해 보세요.  
- `setRotationAngle` 을 사용해 전체 그룹을 회전시켜 보세요.  
- 이 기법을 메일 병합과 결합해 브랜드 그래픽이 포함된 개인화 문서를 자동 생성해 보세요.

코드를 자유롭게 프로젝트에 적용하고, 결과를 댓글로 공유해 주세요!


## 다음에 배워야 할 내용은?


다음 튜토리얼들은 이 가이드에서 다룬 기술을 기반으로 하며, 관련 주제를 깊이 있게 다룹니다. 각 리소스에는 단계별 설명과 완전한 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 다양한 구현 방식을 탐색하는 데 도움이 됩니다.

- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}