---
category: general
date: 2026-08-20
description: Aspose.Words for Java를 사용하여 도형을 그룹화하고, 도형 크기를 설정하고, 문서에 이미지를 삽입하고, 그룹에
  그림을 추가하고, 사각형 도형을 만드는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert image into document
- set shape size
- add picture to group
- create rectangle shape
language: ko
lastmod: 2026-08-20
og_description: Aspose.Words를 사용하여 Word 문서에서 도형을 그룹화하는 방법. 도형 크기 설정, 문서에 이미지 삽입, 그룹에
  그림 추가, 사각형 도형 만들기를 단계별 Java 튜토리얼로 따라해 보세요.
og_image_alt: Diagram showing how to group shapes in a Word document
og_title: Aspose.Words를 사용하여 Word 문서에서 도형을 그룹화하는 방법 – Java 가이드
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  headline: How to group shapes in a Word document using Aspose.Words
  type: TechArticle
- description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  name: How to group shapes in a Word document using Aspose.Words
  steps:
  - name: Create a new document and a `DocumentBuilder`
    text: A `Document` represents the Word file, while `DocumentBuilder` provides
      convenient methods for inserting content.
  - name: Insert a group shape that will hold multiple child shapes
    text: A group shape acts like a container. Its dimensions define the bounding
      box for all child shapes.
  - name: Create a rectangle shape, set its size, and add it to the group
    text: Setting the exact size of a shape is essential when you want precise layout
      control.
  - name: Insert an image, then add the picture shape to the same group
    text: Inserting an image is the core of the **insert image into document** requirement.
      The returned `Shape` is a picture shape that can be grouped like any other shape.
  - name: Position the entire group on the page
    text: After adding all child shapes, you can move, rotate, or hide the whole group.
      Positioning uses the **add picture to group** concept indirectly, because the
      group now contains the picture.
  - name: Save the document
    text: Finally, write the file to disk. You can open the resulting `.docx` in Word
      to verify the grouping.
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Automation
title: Aspose.Words를 사용하여 Word 문서에서 도형을 그룹화하는 방법
url: /ko/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words를 사용하여 Word 문서에서 도형을 그룹화하는 방법

Word 파일에서 **도형을 그룹화하는 방법**이 필요하다면, 이 튜토리얼은 전체 Java 솔루션을 보여줍니다. **도형 크기 설정**, **문서에 이미지 삽입**, **그룹에 그림 추가**, **사각형 도형 만들기**를 확인할 수 있으며, 모두 명확한 설명과 실행 가능한 코드 샘플이 포함되어 있습니다.

도형을 그룹화하면 레이아웃 관리가 간소화되고, 여러 객체를 하나의 단위로 이동하거나 회전할 수 있으며, 문서를 깔끔하게 유지할 수 있습니다. 아래 단계에서는 사각형과 그림을 포함하는 그룹을 만든 다음, 페이지에 배치합니다.

## 전제 조건

* Java 17 이상이 설치되어 있어야 합니다.
* Aspose.Words for Java (버전 23.9 이상)를 프로젝트의 클래스패스에 추가해야 합니다.
* `YOUR_DIRECTORY/sample.jpg` 경로에 샘플 JPEG 이미지가 있어야 합니다 (`YOUR_DIRECTORY`를 실제 경로로 교체).

Aspose.Words를 Maven을 통해 추가할 수 있습니다:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Aspose.Words로 도형을 그룹화하는 방법

다음 섹션에서는 **도형을 그룹화하는 방법**에 필요한 각 작업을 단계별로 안내합니다. 주요 H2 헤더에 핵심 키워드가 포함되어 SEO 규칙을 만족합니다.

### 1단계: 새 문서와 `DocumentBuilder` 만들기

`Document`는 Word 파일을 나타내며, `DocumentBuilder`는 콘텐츠 삽입을 위한 편리한 메서드를 제공합니다.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this matters*: 새 `Document`로 시작하면 만든 그룹이 기존 요소와 충돌하지 않게 됩니다.

### 2단계: 여러 자식 도형을 보관할 그룹 도형 삽입

그룹 도형은 컨테이너 역할을 합니다. 그 크기는 모든 자식 도형의 경계 상자를 정의합니다.

```java
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

*Tip*: 너비(`300`)와 높이(`200`)는 포인트 단위(1 pt = 1/72 인치)이며, 추가하려는 도형 크기에 따라 조정하세요.

### 3단계: 사각형 도형을 만들고, 크기를 설정한 뒤 그룹에 추가하기

정확한 도형 크기를 설정하는 것은 정밀한 레이아웃 제어에 필수적입니다.

```java
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape size – width
        rectangleShape.setHeight(50);   // set shape size – height
        // Optionally set a fill color for visibility
        rectangleShape.getFillColor().setRGB(0xFF, 0xCC, 0x00);
        groupShape.appendChild(rectangleShape);
```

*Why we set shape size*: `setWidth`와 `setHeight` 메서드는 **set shape size** 보조 키워드와 일치하며, 사각형 외관을 픽셀 단위로 정확하게 제어할 수 있게 합니다.

### 4단계: 이미지를 삽입하고, 같은 그룹에 그림 도형 추가

이미지 삽입은 **insert image into document** 요구사항의 핵심입니다. 반환된 `Shape`는 다른 도형처럼 그룹화할 수 있는 그림 도형입니다.

```java
        // Step 4: Insert an image, then add the picture shape to the same group
        Shape pictureShape = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        // Resize the picture if needed (example: 120 pt wide, maintain aspect ratio)
        pictureShape.setWidth(120);
        // Add the picture to the previously created group
        groupShape.appendChild(pictureShape);
```

*Pro tip*: 원본 종횡비를 유지해야 하면 하나의 차원(`setWidth` 또는 `setHeight`)만 설정하세요. Aspose.Words가 다른 차원을 자동으로 스케일합니다.

### 5단계: 페이지에 전체 그룹 위치 지정

모든 자식 도형을 추가한 후에는 전체 그룹을 이동, 회전 또는 숨길 수 있습니다. 위치 지정은 **add picture to group** 개념을 간접적으로 사용합니다. 이제 그룹에 그림이 포함되어 있기 때문입니다.

```java
        // Step 5: Position the entire group on the page (it can also be rotated, hidden, etc.)
        groupShape.setLeft(50);   // distance from the left margin
        groupShape.setTop(100);   // distance from the top margin
        // Optional: rotate the group 15 degrees
        groupShape.setRotation(15);
```

*Explanation*: `setLeft`와 `setTop`은 페이지 여백을 기준으로 그룹을 배치합니다. 그룹을 회전하면 모든 자식 도형이 변환을 상속받습니다.

### 6단계: 문서 저장

마지막으로 파일을 디스크에 기록합니다. 생성된 `.docx` 파일을 Word에서 열어 그룹화가 정상인지 확인할 수 있습니다.

```java
        // Step 6: Save the document
        doc.save("GroupShapesDemo.docx");
    }
}
```

프로그램을 실행하면 사각형과 이미지가 함께 묶인 **GroupShapesDemo.docx**가 생성됩니다. Word에서 어느 하나의 도형을 선택하면 다른 도형도 함께 선택되어 **도형을 그룹화하는 방법**을 성공적으로 배웠음을 확인할 수 있습니다.

---

## 예상 출력

Microsoft Word에서 *GroupShapesDemo.docx*를 열면:

* 그룹 왼쪽에 사각형(골든 채우기)이 표시됩니다.
* 사각형 오른쪽에 제공한 그림이 표시됩니다.
* 두 객체는 그룹을 드래그하면 함께 이동합니다.
* 그룹은 왼쪽 여백에서 50 pt, 위쪽 여백에서 100 pt 떨어진 위치에 배치되고 15° 회전됩니다.

이미지가 표시되지 않으면 `insertImage`의 파일 경로를 다시 확인하세요. Aspose.Words는 파일을 찾을 수 없을 때 `IOException`을 발생시킵니다.

---

## 일반적인 질문 및 엣지 케이스 처리

| Question | Answer |
|----------|--------|
| **Can I add more than two shapes?** | Yes. Call `groupShape.appendChild(otherShape)` for each additional shape. |
| **What if I need a transparent background for the rectangle?** | Use `rectangleShape.getFillColor().setRGB(255, 255, 255); rectangleShape.setFillTransparent(true);` |
| **Is grouping supported in older Word formats (e.g., `.doc`)?** | Grouping works for `.docx` and `.doc` but some older viewers may ignore the group metadata. Save as `.docx` for full fidelity. |
| **How do I ungroup later?** | Retrieve the child nodes via `groupShape.getChildNodes(NodeType.ANY, true)` and move them to the document body, then remove the group. |
| **Can I group shapes across different sections?** | No. A `GroupShape` must reside within a single `Story` (usually the main document body). |

## 견고한 도형 처리를 위한 전문가 팁

* **Use absolute positioning sparingly** – relative positioning (`builder.moveToDocumentEnd()`) often yields more responsive layouts.
* **Cache the `DocumentBuilder`** – creating a new builder for each operation can degrade performance on large documents.
* **Set `PictureFillMode`** when you need the image to stretch or tile inside the shape: `pictureShape.setPictureFillMode(PictureFillMode.STRETCH);`
* **Validate image dimensions** before insertion to avoid unexpected scaling that can affect the group’s bounding box.

## 다음 단계

이제 **도형을 그룹화하는 방법**을 알았으니, 다음을 탐색해 보세요:

* **Insert image into document** with advanced options like cropping (`pictureShape.setCropTop(...)`).
* **Set shape size** dynamically based on page dimensions (`doc.getFirstSection().getPageSetup().getPageWidth()`).
* **Add picture to group** together with text boxes for captioned graphics.
* **Create rectangle shape** with rounded corners (`rectangleShape.setCornerRadius(5);`).

이러한 주제는 동일한 API를 기반으로 하며, 복잡하고 프로그래밍 방식의 Word 보고서를 만드는 데 도움이 됩니다.

## 결론

이 튜토리얼에서는 Aspose.Words for Java를 사용하여 Word 문서에서 **도형을 그룹화하는 방법**을 배웠습니다. 문서 생성, 그룹 삽입, **사각형 도형 만들기**, **set shape size**, **insert image into document**, **add picture to group**, 그리고 그룹 위치 지정이라는 여섯 단계를 따라 복잡한 레이아웃 시나리오에 재사용 가능한 패턴을 확보했습니다. 추가 자식 도형, 다양한 회전, 조건부 그룹화 로직 등을 실험하여 애플리케이션 요구에 맞게 활용해 보세요.

즐거운 코딩 되세요!

## 다음에 배워야 할 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 리소스에는 완전한 코드 예제와 단계별 설명이 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에 적용할 수 있는 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}