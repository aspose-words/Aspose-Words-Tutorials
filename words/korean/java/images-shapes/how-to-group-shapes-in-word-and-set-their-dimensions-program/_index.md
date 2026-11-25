---
category: general
date: 2026-11-25
description: Java를 사용하여 Word에서 도형을 그룹화하는 방법 및 Aspose.Words를 사용해 DOCX 파일에서 도형 크기를 설정하는
  방법.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- how to set shape dimensions
- set shape size word
language: ko
lastmod: 2026-11-25
og_description: Aspose.Words Java API를 사용하여 Word에서 도형을 그룹화하고 도형 크기를 빠르게 설정하는 방법. 전체
  단계별 솔루션을 확인하세요.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Word에서 도형을 그룹화하고 크기를 설정하는 방법 – Java 가이드
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  headline: How to group shapes in Word and set their dimensions programmatically
  type: TechArticle
- description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  name: How to group shapes in Word and set their dimensions programmatically
  steps:
  - name: Expected output
    text: '* A Word document (`GroupShape.docx`) with one page. * A `GroupShape` containing
      a 100 × 50 pt rectangle and an 80 × 80 pt ellipse. * Selecting either shape
      selects the whole group.'
  - name: How to change the position of the grouped shapes?
    text: 'After creating the `GroupShape`, you can set its `left` and `top` properties:'
  - name: What if I need to add more than two shapes?
    text: '`GroupShape` works like any other container node. Call `groupShape.appendChild(yourShape)`
      for each additional shape. The API does not limit the number of children.'
  - name: Can I apply style (fill color, line weight) to individual shapes?
    text: 'Yes. Each `Shape` object exposes formatting properties:'
  - name: Does the code work with older Aspose.Words versions?
    text: The `insertGroupShape` method was introduced in version 24.9. If you are
      on an earlier version, you’ll need to create a `GroupShape` manually via the
      node tree, which is more involved. Upgrading is the recommended path.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- shapes
title: Word에서 도형을 그룹화하고 프로그래밍으로 크기를 설정하는 방법
url: /ko/java/images-shapes/how-to-group-shapes-in-word-and-set-their-dimensions-program/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word에서 도형을 그룹화하고 프로그래밍 방식으로 크기 설정하기

Word에서 **도형을 그룹화하는 방법**과 정확한 크기를 제어해야 한다면, 이 가이드는 완전하고 실행 가능한 솔루션을 보여줍니다. Aspose.Words for Java를 사용하면 사각형과 타원을 만들고 이를 `GroupShape`에 추가한 다음, 너비와 높이와 같은 **도형 크기 설정 방법**을 단일 DOCX 파일에서 수행할 수 있습니다.

다음 내용을 배울 수 있습니다:

* 처음부터 새로운 Word 문서를 생성합니다.  
* `GroupShape`를 삽입합니다 (버전 24.9에서 추가된 새로운 API).  
* 사각형과 타원을 그룹에 추가합니다.  
* `setWidth`와 `setHeight`를 사용해 **Word에서 도형 크기 설정**을 정확히 수행합니다.  
* 문서를 디스크에 저장합니다.

외부 도구는 필요하지 않습니다—Java 17+, Maven, 그리고 Aspose.Words for Java 라이브러리만 있으면 됩니다.

## Prerequisites

* Java Development Kit 17 이상.  
* Maven(또는 Gradle) – 의존성 관리용.  
* Aspose.Words for Java 24.9 이상 (`GroupShape` API가 24.9에 도입됨).  
* Java 구문 및 객체‑지향 개념에 대한 기본 지식.

아직 프로젝트에 Aspose.Words를 추가하지 않았다면, 다음 Maven 의존성을 포함하세요:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Step 1: Create a new document and a DocumentBuilder

`Document` 클래스는 전체 Word 파일을 나타내며, `DocumentBuilder`는 콘텐츠를 추가하는 편리한 방법을 제공합니다.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this step?*  
새로운 `Document`를 만들면 깨끗한 캔버스를 얻을 수 있습니다. `DocumentBuilder`는 단락, 표, 그리고 이 경우에는 도형을 삽입할 수 있게 해 주는 고수준 헬퍼입니다.

## Step 2: Insert a GroupShape (new API in version 24.9)

`GroupShape`는 컨테이너 역할을 하며, 추가하는 모든 도형이 동일한 시각적 그룹의 일부가 됩니다.

```java
        // Step 2: Insert a GroupShape (new API in version 24.9)
        GroupShape groupShape = builder.insertGroupShape();
```

*Why use `GroupShape`?*  
도형을 그룹화하면 여러 객체를 한 번에 이동, 회전 또는 서식 적용하기가 쉬워집니다. 이 API는 24.9에서 추가되었으므로 이전 버전에서는 이 코드를 컴파일할 수 없습니다.

## Step 3: Create a rectangle, set its size, and add it to the group

여기서는 사각형에 대해 **도형 크기 설정 방법**을 보여줍니다.

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);   // height in points
        groupShape.appendChild(rectangle);
```

*Why set width and height explicitly?*  
Word는 도형 크기를 포인트 단위로 저장합니다. `setWidth`와 `setHeight`를 호출하면 정확한 시각적 영역을 제어할 수 있어, 정밀한 레이아웃이 필요하거나 PDF로 내보낼 때 필수적입니다.

## Step 4: Create an ellipse, set its size, and add it to the same group

같은 **Word에서 도형 크기 설정** 기술을 모든 도형 유형에 적용할 수 있습니다.

```java
        // Step 4: Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(document, ShapeType.ELLIPSE);
        ellipse.setWidth(80.0);
        ellipse.setHeight(80.0);
        groupShape.appendChild(ellipse);
```

*Why add the ellipse to the same `GroupShape`?*  
두 도형이 하나의 단위로 함께 이동합니다. 이는 아이콘, 로고 또는 정렬이 유지되어야 하는 복잡한 다이어그램을 만들 때 유용합니다.

## Step 5: Save the document with the grouped shapes

마지막으로 DOCX 파일을 디스크에 저장합니다.

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShape.docx");
    }
}
```

이 프로그램을 실행하면 **GroupShape.docx**라는 파일이 생성되며, 사각형과 타원이 함께 그룹화된 상태로 포함됩니다. Microsoft Word에서 파일을 열면 두 도형이 하나의 객체처럼 동작하여 함께 드래그, 크기 조정 또는 회전할 수 있습니다.

### Expected output

* 한 페이지로 구성된 Word 문서(`GroupShape.docx`).  
* 100 × 50 pt 사각형과 80 × 80 pt 타원을 포함하는 `GroupShape`.  
* 어느 하나의 도형을 선택하면 전체 그룹이 선택됩니다.

## Common questions and edge cases

### How to change the position of the grouped shapes?

`GroupShape`를 만든 후, `left`와 `top` 속성을 설정할 수 있습니다:

```java
groupShape.setLeft(150.0);
groupShape.setTop(200.0);
```

이 좌표 역시 포인트 단위로 측정됩니다.

### What if I need to add more than two shapes?

`GroupShape`는 다른 컨테이너 노드와 동일하게 동작합니다. 추가 도형마다 `groupShape.appendChild(yourShape)`를 호출하면 됩니다. 자식 수에 제한은 없습니다.

### Can I apply style (fill color, line weight) to individual shapes?

가능합니다. 각 `Shape` 객체는 서식 속성을 제공합니다:

```java
rectangle.getFillColor().setColor(Color.BLUE);
ellipse.getStroke().setWeight(2.0);
```

### Does the code work with older Aspose.Words versions?

`insertGroupShape` 메서드는 버전 24.9에서 도입되었습니다. 이전 버전을 사용 중이라면 노드 트리를 통해 `GroupShape`를 직접 생성해야 하며, 작업이 더 복잡합니다. 업그레이드가 권장됩니다.

## Pro tips

* **포인트 단위 사용** – Word 내부 단위는 포인트(1/72 인치)입니다. 픽셀이나 센티미터에서 변환할 경우 예상치 못한 크기가 발생할 수 있습니다.  
* **배치 전에 그룹화** – 모든 자식을 추가한 뒤에 `GroupShape`의 위치를 지정하세요; 그렇지 않으면 오프셋을 다시 계산해야 할 수 있습니다.  
* **DocumentBuilder 재사용** – `builder.moveTo`를 사용해 커서를 이동한 뒤 각 `insertGroupShape` 호출 전에 여러 그룹을 동일 문서에 삽입할 수 있습니다.

## Conclusion

이제 Aspose.Words for Java를 사용해 **Word에서 도형을 그룹화하는 방법**과 **도형 크기 설정 방법**을 완전하게 구현한 예제를 보유하게 되었습니다. 튜토리얼에서는 문서 생성, `GroupShape` 삽입, 사각형 및 타원 추가, 정확한 크기 지정, 그리고 결과 저장까지 다루었습니다.

다음과 같은 작업을 탐색해 보세요:

* 동일 그룹에 텍스트 상자나 그림 추가하기.  
* API를 통해 Word의 스마트 아트 기능으로 그룹화된 도형에 애니메이션 적용하기.  
* 그룹화된 도형을 PDF 또는 SVG로 내보내 웹에서 활용하기.

다양한 도형 유형, 크기, 위치를 실험해 보세요—그룹화는 Word 문서에서 복잡한 레이아웃을 강력하게 제어할 수 있게 해 줍니다.

## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 다룬 기술을 기반으로 하는 관련 주제를 다룹니다. 각 자료에는 단계별 설명과 완전한 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [How to create a blank Word document and group shapes in Java](/words/english/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/)
- [How to group shapes in Word with Java – complete guide](/words/english/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}