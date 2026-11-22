---
category: general
date: 2026-11-22
description: Aspose.Words for Java를 사용하여 Word에 도형을 추가하는 방법을 배우세요 – 사각형을 삽입하고 프로그래밍으로
  숨기는 방법.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shape to word
- how to insert shape
- how to hide shape
- hide shape in word
language: ko
lastmod: 2026-11-22
og_description: Aspose.Words for Java를 사용하여 Word에 도형을 추가합니다. 이 튜토리얼에서는 사각형을 삽입하고,
  도형을 숨기며, 문서를 저장하는 방법을 보여줍니다.
og_image_alt: Screenshot of Java code that adds and hides a shape in a Word document
og_title: Aspose.Words를 사용하여 Word에 도형 추가 – Java 가이드
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  headline: How to add shape to Word documents with Aspose.Words for Java
  type: TechArticle
- description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  name: How to add shape to Word documents with Aspose.Words for Java
  steps:
  - name: Expected output
    text: '* The file `output.docx` opens without any visible shapes. * If you inspect
      the document with Aspose.Words (e.g., `doc.getChildNodes(NodeType.SHAPE, true).size()`),
      the shape count will be **1**, confirming that the shape exists but is hidden.'
  - name: 1. Creating a shape in a fresh document
    text: 'If you start from scratch, replace the load line with:'
  - name: 2. Positioning the shape precisely
    text: 'By default, `insertShape` places the shape at the current cursor location.
      To position it absolutely:'
  - name: 3. Controlling visibility per output format
    text: 'If you need the shape visible in the Word UI but hidden when exporting
      to PDF, use `Shape.setWrapType(WrapType.NONE)` together with `Hidden`:'
  - name: 4. Adding text inside the shape
    text: 'A rectangle can contain a text frame:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape handling
title: Aspose.Words for Java를 사용하여 Word 문서에 도형 추가하는 방법
url: /ko/java/images-shapes/how-to-add-shape-to-word-documents-with-aspose-words-for-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java를 사용하여 Word 문서에 도형 추가하는 방법

프로그래밍 방식으로 **Word에 도형을 추가**해야 할 경우, Aspose.Words for Java를 사용하면 간단합니다. 이 가이드에서는 **도형 삽입 방법**, 도형의 가시성 제어, 그리고 **도형 숨기기** 방법을 배워 최종 파일이 기대한 대로 보이도록 할 수 있습니다.

전체 실행 가능한 예제를 통해 기존 `.docx` 파일을 로드하고, 사각형을 삽입한 뒤 숨기고, 결과를 저장하는 과정을 단계별로 살펴봅니다. 외부 스크립트나 수동 작업이 필요 없으며, 새 문서를 처음부터 만들거나 인쇄 시에만 도형을 숨기는 등 일반적인 변형 사례도 다룹니다.

## Prerequisites

시작하기 전에 다음이 준비되어 있는지 확인하세요:

* Java 17 (또는 그 이상) – 이전 버전도 동작하지만 최신 LTS가 더 나은 성능을 제공합니다.  
* Maven 3.8+ – 의존성 관리를 위해 필요합니다.  
* 유효한 Aspose.Words for Java 라이선스 (무료 평가판으로 학습 가능).  
* 원하는 IDE 또는 텍스트 편집기 (예: IntelliJ IDEA, VS Code).

## Step 1: Add Aspose.Words to your Maven project

`pom.xml`에 다음 의존성을 추가합니다. 이는 최신 안정 버전(2026년 11월 기준)을 가져옵니다.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

> **Pro tip:** 자체 라이선스 로직과 함께 JAR를 배포할 경우 `<scope>provided</scope>` 구문을 사용하세요.

## Add shape to Word – initializing the document

첫 번째 기능 단계는 `Document` 객체를 얻는 것입니다. 기존 파일을 로드하거나 새 파일을 만들 수 있습니다.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document (or create a new one)
        Document doc = new Document("input.docx");   // <-- replace with your path
        // If you prefer a blank document, use:
        // Document doc = new Document();
```

*Why this matters*: `Document` 클래스는 모든 Word 조작의 진입점입니다. 기존 파일을 로드하면 스타일, 머리글, 바닥글이 보존되고, 새 문서는 깨끗한 상태에서 시작할 수 있습니다.

## How to insert shape in a Word document

다음으로 `DocumentBuilder`를 생성하여 문서 내용을 수정합니다. 빌더를 통해 텍스트, 표, 그리고 **도형**을 삽입하는 메서드를 사용할 수 있습니다.

```java
        // Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape with a width of 100 points and height of 50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
```

`insertShape` 호출은 `Shape` 객체를 반환하며, 이를 통해 색상, 테두리, 텍스트 등 추가 설정이 가능합니다. 크기는 포인트 단위(1 pt = 1/72 in)로 표시됩니다.

*Why you might use a rectangle*: 사각형은 주석, 워터마크, 자리표시자 등 가장 흔히 사용되는 컨테이너입니다. 필요에 따라 `ShapeType.RECTANGLE`을 `ShapeType.ELLIPSE`, `ShapeType.LINE` 등으로 교체해 다양한 시각적 요구를 충족할 수 있습니다.

## How to hide shape in Word

때때로 레이아웃 계산을 위해 도형이 존재해야 하지만 최종 렌더링에서는 보이지 않게 해야 할 경우가 있습니다. Aspose.Words는 `setHidden(true)` 메서드를 제공하여 이를 구현합니다.

```java
        // Hide the shape so it does not appear when the document is opened
        rectangle.setHidden(true);
```

숨김 플래그는 Microsoft Word의 **Hidden** 서식 옵션과 동일하게 동작합니다: 도형은 시각적 레이아웃에서 제외되지만 문서 객체 모델에는 여전히 존재합니다. 이는 다음과 같은 상황에 유용합니다:

* 애플리케이션이 나중에 읽을 메타데이터 또는 마커를 저장할 때.  
* 게시 직전에 제거되는 자리표시자를 만들 때.  
* 다양한 출력 형식에 따라 가시성을 제어할 때(예: HTML에서는 숨기고 PDF에서는 유지).

> **Note:** 숨긴 도형은 기본적으로 PDF로 내보낼 때도 포함됩니다. PDF에서도 제외하려면 `rectangle.getWrapType() = WrapType.NONE`으로 설정하고 `Hidden` 속성을 적절히 조정하세요.

## Step 4: Save the modified document

마지막으로 변경 사항을 새 파일에 저장합니다.

```java
        // Save the document with the hidden rectangle
        doc.save("output.docx");   // <-- replace with your desired output path
    }
}
```

`output.docx`를 Microsoft Word에서 열면 사각형이 보이지 않지만 문서 트리에는 여전히 존재합니다. 파일을 다시 로드하고 `Shape.isHidden()`을 확인하면 프로그래밍적으로 존재 여부를 검증할 수 있습니다.

### Expected output

* `output.docx` 파일을 열었을 때 보이는 도형이 없습니다.  
* Aspose.Words로 문서를 검사하면(`doc.getChildNodes(NodeType.SHAPE, true).size()`), 도형 개수가 **1**로 표시되어 도형이 존재하지만 숨겨져 있음을 확인합니다.

## Advanced variations and edge cases

### 1. Creating a shape in a fresh document

처음부터 시작한다면 로드 라인을 다음으로 교체하세요:

```java
Document doc = new Document();          // creates an empty Word file
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Report Title");        // add a title before the shape
```

### 2. Positioning the shape precisely

기본적으로 `insertShape`는 현재 커서 위치에 도형을 배치합니다. 절대 위치를 지정하려면:

```java
rectangle.setLeft(72);   // 1 inch from the left margin
rectangle.setTop(144);   // 2 inches from the top of the page
rectangle.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangle.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
```

### 3. Controlling visibility per output format

Word UI에서는 도형을 보이게 하고 PDF로 내보낼 때는 숨기고 싶다면 `Shape.setWrapType(WrapType.NONE)`와 `Hidden` 속성을 함께 사용하세요:

```java
rectangle.setHidden(false);                 // visible in Word
rectangle.getParagraph().getParagraphFormat()
        .setPageBreakBefore(true);          // ensure it stays on its own line
// When converting to PDF, hide it programmatically:
if (exportingToPdf) {
    rectangle.setHidden(true);
}
```

### 4. Adding text inside the shape

사각형 안에 텍스트 프레임을 포함시킬 수 있습니다:

```java
Shape textBox = builder.insertShape(ShapeType.TEXT_BOX, 200, 50);
textBox.getTextBox().setInternalMarginLeft(5);
textBox.getTextBox().setInternalMarginTop(5);
builder.moveTo(textBox.getFirstParagraph());
builder.write("Confidential");
```

그 후 동일한 `setHidden(true)` 호출로 텍스트 상자를 숨길 수 있습니다.

## Common pitfalls and how to avoid them

| Symptom | Cause | Fix |
|---------|-------|-----|
| Shape appears even after `setHidden(true)` | The document was saved before the hidden flag was set. | Ensure you call `setHidden(true)` **before** `doc.save()`. |
| Shape size looks distorted | Points vs. pixels confusion on high‑DPI screens. | Use points (72 pt = 1 in) for consistent sizing across platforms. |
| Hidden shape still prints | Some printers ignore the hidden flag. | Set `Shape.setWrapType(WrapType.NONE)` and also clear the `Shape.getParagraph().getParagraphFormat().setPageBreakBefore(false)`. |

## Conclusion

이제 Aspose.Words for Java를 사용하여 **Word 문서에 도형을 추가**하고, **도형 삽입 방법**과 **도형 숨기기** 방법을 익혔습니다. 위 예제는 파일을 로드하고, 사각형을 삽입한 뒤 숨기고, 결과를 저장하는 전체 흐름을 보여주며 일반적인 사용 사례와 여러 엣지 케이스를 모두 다룹니다.

앞으로는 **맞춤 채우기 색상으로 도형 삽입**, **조건부 인쇄를 위한 도형 숨기기**, 혹은 Aspose.Words를 활용한 대량 문서 자동화와 같은 관련 주제를 탐색해 보세요. 다양한 `ShapeType` 값, 위치 지정 옵션, 가시성 플래그를 실험하여 자신의 워크플로에 맞게 최적화할 수 있습니다.

Happy coding, and enjoy the flexibility that programmatic Word manipulation brings to your Java applications!

## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 다룬 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함하여 추가 API 기능을 마스터하고 프로젝트에 적용할 수 있도록 돕습니다.

- [Create a Word document programmatically, add and hide a shape in Java using Aspose.Words](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [How to hide shape in a Word document using Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Create a blank .docx Word document and add a hidden rectangle shape with Aspose.Words](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}