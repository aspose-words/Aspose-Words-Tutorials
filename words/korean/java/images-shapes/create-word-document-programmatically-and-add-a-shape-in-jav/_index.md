---
category: general
date: 2026-10-26
description: Aspose.Words for Java를 사용하여 Word 문서를 프로그래밍 방식으로 생성하고, 도형을 추가하며, Word에서
  객체를 숨기는 방법을 단계별 가이드로 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to hide shape
- how to add shape
- hide object in word
language: ko
lastmod: 2026-10-26
og_description: Aspose.Words for Java를 사용하여 프로그래밍으로 Word 문서를 만들고, Word에 도형을 추가하고 객체를
  숨기는 방법을 배워보세요. 완전하고 실행 가능한 예제.
og_image_alt: Screenshot of a Word document created programmatically with a hidden
  ellipse shape
og_title: 프로그램으로 Word 문서 만들기 – Java에서 도형 추가 및 숨기기
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document programmatically, add a shape, and
    hide object in Word using Aspose.Words for Java – step‑by‑step guide.
  headline: Create Word document programmatically and add a shape in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Java로 워드 문서를 프로그래밍 방식으로 생성하고 도형 추가하기
url: /ko/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java에서 프로그래밍으로 Word 문서 만들기 및 도형 추가

프로그램으로 **Word 문서를 만들** 필요가 있다면, 이 튜토리얼은 정확히 어떻게 수행하고, 도형을 추가한 뒤 Word에서 객체를 숨기는지 보여줍니다. 보고서 생성기나 자동 계약 시스템을 구축하든, 몇 분 안에 완전하고 바로 실행 가능한 솔루션을 얻을 수 있습니다.

다음 내용을 배울 수 있습니다:

* Aspose.Words for Java를 사용해 Word 문서를 초기화합니다.  
* **how to add shape** 기법을 이용해 타원(또는 다른 도형)을 삽입합니다.  
* **how to hide shape** 질문에 답하듯, 파일을 열 때 도형이 절대 나타나지 않도록 숨깁니다.  

외부 도구는 Aspose.Words 라이브러리만 있으면 충분하며, 코드는 Java 17 이상에서 동작합니다.

## Prerequisites

시작하기 전에 다음이 준비되어 있어야 합니다:

* Java Development Kit (JDK) 17 이상이 설치되어 있어야 합니다.  
* Maven 또는 Gradle을 사용해 의존성을 관리합니다(예제는 Maven 사용).  
* 유효한 Aspose.Words for Java 라이선스(무료 평가판으로 테스트 가능).  

Aspose.Words가 처음이라면 공식 Getting Started 가이드를 참고하세요. 이 튜토리얼을 따라가는 데는 읽을 필요가 없습니다.

## Maven dependency

`pom.xml`에 다음 의존성을 추가합니다:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

> **Pro tip:** 버전 번호를 최신으로 유지하세요. 최신 릴리스에는 도형 처리 버그 수정이 포함됩니다.

## Step 1: Create Word document programmatically – initializing the document

**프로그램으로 Word 문서를 만들** 때 가장 먼저 하는 일은 `Document` 객체를 인스턴스화하는 것입니다. 이 객체는 메모리 내 전체 .docx 파일을 나타냅니다.

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document doc = new Document();

        // Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*이 단계가 중요한 이유*: `Document` 클래스는 모든 워드 프로세싱 작업의 진입점입니다. 이 없이 페이지, 단락, 도형 등을 추가할 수 없습니다.

## Step 2: How to add shape – inserting an ellipse

이제 **how to add shape** 부분을 다룹니다. Aspose.Words는 다양한 도형 타입(Ellipse, Rectangle, TextBox 등)을 지원합니다. 아래 예제에서는 너비와 높이가 50포인트인 타원을 삽입합니다.

```java
        // Insert an ellipse shape of size 50x50 points
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);

        // Position the shape (optional)
        ellipse.setLeft(100);
        ellipse.setTop(100);
```

`insertShape` 메서드는 `Shape` 객체를 반환하며, 색상, 선 스타일, 회전 등 추가 커스터마이징이 가능합니다. 좌표는 포인트(1/72인치) 단위로 측정됩니다.

*도형을 추가하고 싶은 이유*: 도형은 워터마크, 장식 요소, 혹은 나중에 숨기거나 교체할 자리 표시자 등에 유용합니다.

## Step 3: How to hide shape – making the object invisible in Word

**how to hide shape** 질문에 답하려면, 도형의 `Hidden` 속성을 `true`로 설정하면 됩니다. 이렇게 하면 Word는 해당 도형을 숨긴 객체로 처리하여 문서 보기나 인쇄 시 전혀 표시되지 않습니다.

```java
        // Hide the shape so it does not appear in the rendered document
        ellipse.setHidden(true);
```

특정 사용자나 조건에 따라 **Word에서 객체 숨기기**가 필요하면, 비즈니스 로직에 따라 런타임에 이 속성을 토글할 수 있습니다.

> **Note:** 숨긴 도형은 여전히 문서 XML 구조의 일부입니다. `setHidden(false)`를 호출하면 나중에 다시 표시할 수 있습니다.

## Step 4: Save the document

도형을 추가하고 숨긴 뒤, 문서를 디스크에 저장합니다.

```java
        // Save the document as a .docx file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

`HiddenShapeDemo.docx`를 Microsoft Word에서 열면 타원이 숨겨져 있기 때문에 빈 페이지가 보입니다. 그 외의 동작은 일반 Word 파일과 동일합니다.

## Full working example

모든 코드를 합치면 다음과 같은 완전한 실행 프로그램이 됩니다:

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a document programmatically
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: How to add shape – insert an ellipse (50x50 points)
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);
        ellipse.setLeft(100);
        ellipse.setTop(100);

        // Step 3: How to hide shape – hide the ellipse so it never appears
        ellipse.setHidden(true);

        // Step 4: Save the file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

**Expected output**

```
Document created successfully.
```

`HiddenShapeDemo.docx`를 열면 빈 페이지가 표시되고, 숨겨진 타원이 렌더링되지 않아 **Word에서 객체 숨기기** 작업이 성공했음을 확인할 수 있습니다.

## Edge cases and variations

| 상황 | 변경 내용 | 이유 |
|-----------|----------------|-----|
| 타원 대신 사각형을 숨기고 싶을 때 | `insertShape`에서 `ShapeType.RECTANGLE` 사용 | 다른 시각적 자리 표시자 |
| 여러 도형을 한 번에 숨기고 싶을 때 | `doc.getChildNodes(NodeType.SHAPE, true)`를 순회하면서 `setHidden(true)` 호출 | 대량 처리에 유용 |
| 인쇄 보기에서만 도형을 보이게 하고 싶을 때 | `shape.setVisible(false)`와 `shape.setPrint(true)` 설정 | 화면과 인쇄 가시성을 구분 |
| 다른 측정 단위를 사용하고 싶을 때 | `builder.getDocument().getCompatibilityOptions().setMeasureUnit(MeasureUnit.INCHES)` 호출 | 레이아웃 요구사항에 맞춤 |

## Common pitfalls

* **`setHidden(true)` 호출을 잊음** – 도형이 정상적으로 표시됩니다.  
* **도형을 숨기기 전에 문서를 저장** – 순서가 중요합니다; 먼저 숨기고, 그 다음 저장하세요.  
* **구버전 Aspose.Words 사용** – 오래된 릴리스에는 `setHidden` API가 없을 수 있습니다.  

생성된 파일을 대상 Microsoft Word 버전에서 테스트해 숨김 상태가 기대대로 동작하는지 항상 확인하세요.

## Conclusion

이 가이드에서는 **프로그램으로 Word 문서를 만들**, **도형을 추가**, 그리고 Aspose.Words for Java를 사용해 **Word에서 객체를 숨기는** 방법을 배웠습니다. 전체 예제는 문서 초기화부터 도형이 절대 나타나지 않는 파일 저장까지 정확한 단계를 보여줍니다.

이제 다음을 시도해 볼 수 있습니다:

* 다른 도형 타입(`ShapeType.LINE`, `ShapeType.TEXT_BOX`) 실험하기.  
* 숨긴 도형을 북마크와 결합해 동적 템플릿 만들기.  
* `setVisible` 및 `setPrint` 속성을 활용해 객체 가시성을 보다 세밀하게 제어하기.

코딩을 즐기시고 Word 문서 자동화에 성공하시길 바랍니다!

## What Should You Learn Next?

다음 튜토리얼들은 이 가이드에서 다룬 기술을 기반으로 하는 관련 주제를 다룹니다. 각 리소스는 단계별 설명과 완전한 코드 예제를 제공하여 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용할 수 있도록 도와줍니다.

- [Aspose.Words for Java로 빈 Word 문서 만들기](/words/english/java/document-manipulation/how-to-create-blank-word-document-with-aspose-words-for-java/)
- [Java를 사용해 Word 문서에서 도형 숨기기](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Java Word Document – 그림자 효과가 있는 사각형 도형 추가](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}