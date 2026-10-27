---
category: general
date: 2026-09-18
description: Aspose.Words를 사용하여 빈 문서를 만들고 Word에 도형을 삽입하세요 – 삼각형 도형 추가 방법 및 기타 기능을
  배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- add shapes to word
- how to insert triangle
- add triangle shape
- create word document
language: ko
lastmod: 2026-09-18
og_description: Aspose.Words를 사용하여 Word에서 빈 문서를 만들고 삼각형 도형 삽입, 도형 그룹화 및 기타 그래픽을 배우세요.
  이 완전한 가이드를 따라보세요.
og_image_alt: Screenshot of a Word document showing a grouped shape with a triangle
  inside
og_title: 빈 문서를 만들고 Word에 도형 추가 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document and insert shapes to Word with Aspose.Words –
    learn how to add a triangle shape and more.
  headline: How to create blank document and add shapes to Word
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: 빈 문서를 만들고 Word에 도형을 추가하는 방법
url: /ko/java/images-shapes/how-to-create-blank-document-and-add-shapes-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 빈 문서를 만들고 Word에 도형을 추가하는 방법

If you need to **create blank document** and then enrich it with graphics, this guide shows you exactly how. We'll walk through creating a Word file from scratch and **add shapes to Word**, including **how to insert triangle** shape, using Aspose.Words for Java.

**빈 문서를 만들고** 그래픽을 추가해야 한다면, 이 가이드가 정확히 방법을 보여줍니다. 처음부터 Word 파일을 생성하고 **Word에 도형을 추가**하는 과정을 단계별로 안내하며, Aspose.Words for Java를 사용해 **삼각형 도형을 삽입하는 방법**도 포함합니다.

You’ll finish the tutorial with a ready‑to‑use *.docx* file that contains a grouped shape holding a triangle. The steps cover everything from project setup to saving the final **create word document**. No external tools are required beyond Aspose.Words.

튜토리얼을 마치면 삼각형을 포함한 그룹 도형이 들어 있는 바로 사용할 수 있는 *.docx* 파일을 얻게 됩니다. 단계에서는 프로젝트 설정부터 최종 **create word document** 저장까지 모든 과정을 다룹니다. Aspose.Words 외에 별도의 도구는 필요하지 않습니다.

## 필수 조건

Before you start, make sure you have:

* Java 17 or later installed  
* Maven or Gradle for dependency management  
* An Aspose.Words for Java license (the free evaluation works for this demo)  

시작하기 전에 다음이 설치되어 있는지 확인하세요:

* Java 17 이상
* Maven 또는 Gradle (의존성 관리용)
* Aspose.Words for Java 라이선스 (무료 평가판으로도 이 데모를 실행할 수 있습니다)

If you prefer a different build system, adjust the dependency syntax accordingly. The code works on any platform that supports Java.

다른 빌드 시스템을 선호한다면, 해당에 맞게 의존성 구문을 조정하십시오. 코드는 Java를 지원하는 모든 플랫폼에서 작동합니다.

## Aspose.Words를 사용하여 빈 문서 만들기

The first operation is to **create blank document** in memory. Aspose.Words provides a `Document` class that represents a Word file without any content.

첫 번째 작업은 메모리에서 **빈 문서를 만들기**입니다. Aspose.Words는 내용이 없는 Word 파일을 나타내는 `Document` 클래스를 제공합니다.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank document
```

The `new Document()` constructor builds an empty *.docx* structure, which you can later populate with paragraphs, tables, or graphics. Because the document is blank, you have full control over every element you add.

`new Document()` 생성자는 빈 *.docx* 구조를 만들며, 이후에 단락, 표 또는 그래픽으로 채울 수 있습니다. 문서가 비어 있기 때문에 추가하는 모든 요소를 완전히 제어할 수 있습니다.

## Word에 도형 추가 – 그룹 도형 삽입

A group shape lets you treat several graphics as a single unit. This is useful when you want to move or resize multiple shapes together.

그룹 도형을 사용하면 여러 그래픽을 하나의 단위로 취급할 수 있습니다. 여러 도형을 함께 이동하거나 크기를 조정하려는 경우에 유용합니다.

```java
        // Step 2: Initialize a DocumentBuilder to construct content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a group shape of size 300 × 300 points
        GroupShape group = builder.insertGroupShape(300.0, 300.0);
```

`DocumentBuilder` is the primary API for adding content. The `insertGroupShape` call creates a container that is 300 × 300 points (approximately 4 × 4 inches). After this call the cursor is positioned *inside* the group, ready for additional shapes.

`DocumentBuilder`는 콘텐츠를 추가하기 위한 주요 API입니다. `insertGroupShape` 호출은 300 × 300 포인트(약 4 × 4 인치) 크기의 컨테이너를 생성합니다. 이 호출 이후 커서는 그룹 *내부*에 위치하게 되며, 추가 도형을 삽입할 준비가 됩니다.

### 그룹 도형을 사용하는 이유는?

Grouping keeps related graphics aligned and makes it easier to apply uniform formatting. If you later decide to move the triangle, the whole group moves together, preserving layout.

그룹화는 관련 그래픽을 정렬된 상태로 유지하고 일관된 서식을 적용하기 쉽게 합니다. 나중에 삼각형을 이동시키기로 하면, 전체 그룹이 함께 이동해 레이아웃이 유지됩니다.

## 그룹 내부에 삼각형 도형 삽입 방법

Now we address **how to insert triangle** shape. The triangle is one of the built‑in `ShapeType` values.

이제 **삼각형 도형을 삽입하는 방법**을 다룹니다. 삼각형은 내장 `ShapeType` 값 중 하나입니다.

```java
        // Step 4: Move the cursor into the group's first paragraph
        builder.moveTo(group.getFirstParagraph());

        // Step 5: Insert a triangle shape of size 60 × 60 points inside the group
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);
```

The `moveTo` call ensures the builder’s insertion point is the first paragraph of the group. `insertShape` then adds a triangle that is 60 × 60 points. Because the cursor is inside the group, the triangle becomes a child of the group shape.

`moveTo` 호출은 빌더의 삽입 지점을 그룹의 첫 번째 단락으로 설정합니다. 그 다음 `insertShape`는 60 × 60 포인트 크기의 삼각형을 추가합니다. 커서가 그룹 내부에 있기 때문에 삼각형은 그룹 도형의 자식이 됩니다.

**삼각형 도형 추가** 팁:

* The size is measured in points; 72 points equal one inch. Adjust the dimensions to suit your layout.  
  크기는 포인트 단위이며, 72 포인트는 1인치에 해당합니다. 레이아웃에 맞게 크기를 조정하세요.
* If you need a different orientation, use `builder.getCurrentParagraph().getParagraphFormat().setAlignment()` to align the shape within the group.  
  다른 방향이 필요하면 `builder.getCurrentParagraph().getParagraphFormat().setAlignment()`를 사용해 그룹 내에서 도형을 정렬합니다.
* The triangle inherits the group’s fill and line styles unless you override them with `shape.getFillColor()` or `shape.getStrokeColor()`.  
  삼각형은 별도로 `shape.getFillColor()` 또는 `shape.getStrokeColor()`로 재정의하지 않는 한 그룹의 채우기 및 선 스타일을 상속합니다.

## 문서 저장 – create word document

After constructing the graphics, you save the file. This step finalizes the **create word document** operation.

그래픽을 구성한 후 파일을 저장합니다. 이 단계에서 **create word document** 작업이 완료됩니다.

```java
        // Step 6: Save the document with the extended group shape
        doc.save("ExtendedGroup.docx");               // create word document
    }
}
```

`doc.save` writes the in‑memory representation to disk as a standard Word document. You can open `ExtendedGroup.docx` in Microsoft Word, LibreOffice, or any viewer that supports the OOXML format. The file will display a grouped shape containing a triangle, exactly as built by the code.

`doc.save`는 메모리상의 표현을 표준 Word 문서로 디스크에 기록합니다. `ExtendedGroup.docx` 파일은 Microsoft Word, LibreOffice 또는 OOXML 형식을 지원하는 모든 뷰어에서 열 수 있습니다. 파일에는 코드가 만든 대로 삼각형이 포함된 그룹 도형이 표시됩니다.

## 전체 실행 가능한 예제

Putting all pieces together, here is the complete program you can copy, compile, and run:

모든 부분을 합치면, 복사하고 컴파일하여 실행할 수 있는 전체 프로그램은 다음과 같습니다:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Prepare a builder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a group shape (300 × 300 points)
        GroupShape group = builder.insertGroupShape(300.0, 300.0);

        // 4. Position the cursor inside the group
        builder.moveTo(group.getFirstParagraph());

        // 5. Insert a triangle shape (60 × 60 points)
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);

        // 6. Save the file – this creates the final Word document
        doc.save("ExtendedGroup.docx");
    }
}
```

### 예상 결과

When you open `ExtendedGroup.docx`, you will see a single group shape occupying the center of the page. Inside that group, a small triangle appears at the default position. The triangle can be selected and moved as part of the group, confirming that **add shapes to word** worked as intended.

`ExtendedGroup.docx`를 열면 페이지 중앙에 단일 그룹 도형이 표시됩니다. 그 그룹 안에 기본 위치에 작은 삼각형이 나타납니다. 삼각형은 그룹의 일부로 선택 및 이동할 수 있어 **add shapes to word**가 의도대로 작동했음을 확인할 수 있습니다.

## 자주 묻는 질문 및 예외 상황

| Question | Answer |
|----------|--------|
| *그룹 안에 두 개 이상의 도형을 추가할 수 있나요?* | 예. 삼각형을 삽입한 후 커서를 그룹 내부에 유지하고 다른 `ShapeType`을 사용해 `builder.insertShape`를 다시 호출하십시오. |
| *삼각형을 빨간색으로 만들려면 어떻게 해야 하나요?* | `insertShape`가 반환한 `Shape`을 가져와 `shape.getFillColor().setColor(Color.RED)`를 호출하십시오. |
| *이 방법이 오래된 .doc 파일에서도 작동하나요?* | Aspose.Words는 지정한 형식으로 저장합니다. 레거시 Word 문서를 만들려면 `doc.save("file.doc", SaveFormat.DOC)`를 사용하십시오. |
| *그룹의 테두리를 어떻게 변경하나요?* | 테두리를 맞춤 설정하려면 `group.getStrokeColor().setColor(Color.BLUE)`와 `group.setLineWeight(2.0)`을 사용하십시오. |
| *삼각형을 회전시킬 방법이 있나요?* | 각도를 도(degree)로 설정하려면 `shape.getRotation()`을 호출하십시오. |

## 전문가 팁

* **Reuse the builder** – creating a new `DocumentBuilder` for each shape adds overhead. Keep a single builder per document.  
  **Reuse the builder** – 각 도형마다 새로운 `DocumentBuilder`를 생성하면 오버헤드가 발생합니다. 문서당 하나의 빌더를 유지하십시오.
* **Unit conversion** – if you work with millimeters, convert them to points (`points = mm * 2.83465`).  
  **Unit conversion** – 밀리미터 단위로 작업하는 경우 포인트로 변환하십시오(`points = mm * 2.83465`).
* **Performance** – for large documents, call `doc.updatePageLayout()` only once after all shapes are added.  
  **Performance** – 큰 문서의 경우 모든 도형을 추가한 뒤 `doc.updatePageLayout()`을 한 번만 호출하십시오.

## 결론

You now know how to **create blank document**, **add shapes to Word**, and specifically **how to insert triangle** shape using Aspose.Words for Java. The complete example demonstrates the full workflow from an empty file to a saved **create word document** that contains a grouped triangle.

이제 **빈 문서를 만들고**, **Word에 도형을 추가**하며, 특히 Aspose.Words for Java를 사용해 **삼각형 도형을 삽입하는 방법**을 알게 되었습니다. 전체 예제는 빈 파일에서 그룹화된 삼각형이 포함된 저장된 **create word document**까지의 전체 워크플로를 보여줍니다.

From here you can explore additional `ShapeType` values, apply custom styling, or combine multiple groups to build complex diagrams. Experiment with different sizes, colors, and positions to master Word automation in Java.

여기서부터 추가 `ShapeType` 값을 탐색하고, 사용자 정의 스타일을 적용하거나 여러 그룹을 결합해 복잡한 다이어그램을 만들 수 있습니다. 다양한 크기, 색상 및 위치를 실험하면서 Java에서 Word 자동화를 마스터하십시오.

--- 

*다음 보고서를 자동화할 준비가 되셨나요? 예제를 복제하고, 크기를 조정한 뒤 코드를 여러분의 애플리케이션에 바로 통합해 보세요.*

## 다음에 배울 내용은?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 전체 작동 코드 예제와 단계별 설명이 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Aspose.Words for .NET을 사용하여 Word 문서에 그룹 도형 만들기](/words/english/net/working-with-shapes/add-group-shape/)
- [그림자 사각형 도형이 있는 빈 Word 문서 만들기 – 단계별 가이드](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words를 사용하여 Word에 사각형 도형 만들기 – 단계별 가이드](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}