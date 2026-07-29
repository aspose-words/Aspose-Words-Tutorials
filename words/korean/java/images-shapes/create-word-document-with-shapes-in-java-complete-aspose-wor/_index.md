---
category: general
date: 2026-07-29
description: Aspose.Words를 사용하여 Java에서 워드 문서를 생성합니다. 사각형 도형을 삽입하고, 워드에서 도형을 그룹화하는
  방법을 배우며, 문서를 빠르게 docx 형식으로 저장합니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
- add shapes to word
language: ko
lastmod: 2026-07-29
og_description: Aspose.Words를 사용하여 Java에서 워드 문서를 생성합니다. 사각형 모양을 삽입하고, 워드에서 도형을 그룹화한
  뒤, 몇 분 안에 문서를 docx 형식으로 저장합니다.
og_image_alt: Screenshot showing how to create word document with grouped shapes using
  Java
og_title: 도형이 포함된 Word 문서 만들기 – Java Aspose.Words 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  headline: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  name: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  steps:
  - name: '## Create Word Document with Shapes Using Aspose.Words'
    text: The first thing you need is an empty Word file to work with. Aspose.Words
      makes this a one‑liner.
  - name: '## Insert Rectangle Shape and Other Shapes'
    text: Now we’ll add a blue rectangle and a green ellipse. The rectangle demonstrates
      the **insert rectangle shape** keyword, while the ellipse shows that you can
      mix shape types freely.
  - name: '## Group Shapes in Word for Easy Manipulation'
    text: Having two separate objects is fine, but often you want to move them together.
      That’s where **group shapes in word** shines.
  - name: '## Save Document as DOCX and Verify Output'
    text: Finally, we persist the file. This step fulfills the **save document as
      docx** requirement.
  - name: '## Full Working Example and Common Pitfalls'
    text: Below is the complete, ready‑to‑run Java class. Copy‑paste it into your
      project, adjust the output folder, and hit *Run*.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Java에서 도형이 포함된 Word 문서 만들기 – 완전한 Aspose.Words 가이드
url: /ko/java/images-shapes/create-word-document-with-shapes-in-java-complete-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java에서 도형이 포함된 Word 문서 만들기 – Complete Aspose.Words Guide

프로그래밍으로 **create word document** 를 만들고 커스텀 그래픽을 추가하는 방법이 궁금하셨나요? 당신만 그런 것이 아닙니다. 강조된 섹션이 포함된 보고서를 생성하거나 즉석에서 전단지를 디자인해야 할 때, Word에서 도형을 다루는 방법을 마스터하면 수작업 시간을 크게 절감할 수 있습니다.

이 튜토리얼에서는 Aspose.Words for Java를 사용하여 **create word document** 를 만들고, **insert rectangle shape**, **group shapes in Word**, 그리고 최종적으로 **save document as docx** 하는 정확한 단계를 차근차근 살펴보겠습니다. 끝까지 따라오시면 어떤 프로젝트에든 바로 삽입할 수 있는 완전 실행 가능한 예제를 얻게 됩니다.

## What You’ll Walk Away With

- Java 코드만으로 완전히 새로 생성된 Word 파일.  
- 페이지에 추가된 두 개의 서로 다른 도형(사각형과 타원).  
- **group shapes in word** API를 사용해 하나의 객체처럼 동작하도록 묶인 도형들.  
- 표준 `.docx` 형식으로 디스크에 저장되어 Microsoft Word에서 문제 없이 열리는 파일.  

외부 도구 없이, 복잡한 XML 해킹 없이—깨끗한 타입드 Java와 Aspose.Words만으로 가능합니다.

---

## Prerequisites

시작하기 전에 다음을 준비하세요:

1. **Java Development Kit (JDK) 8 이상** – 코드는 Java 8+을 목표로 합니다.  
2. **Aspose.Words for Java** JAR (Maven Central 저장소에서 최신 버전을 다운로드할 수 있습니다).  
3. 간단한 IDE (IntelliJ IDEA, Eclipse, 혹은 기본 텍스트 에디터).  

위 항목을 모두 갖추셨다면, 바로 시작해 보겠습니다.

---

## Step‑by‑Step Implementation

아래에서는 과정을 작은 단계로 나누어 설명합니다. 각 단계마다 코드 스니펫, 간단한 설명, 그리고 공식 문서에는 없는 팁을 제공합니다.

### ## Create Word Document with Shapes Using Aspose.Words

먼저 작업할 빈 Word 파일이 필요합니다. Aspose.Words는 이를 한 줄 코드로 처리합니다.

```java
// Step 1: Initialise a blank document and a DocumentBuilder
Document doc = new Document();                 // Represents the Word file
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:**  
`Document`는 텍스트, 표, 이미지, 도형 등 모든 요소를 담는 컨테이너입니다. `DocumentBuilder`는 저수준 객체를 직접 다루지 않고도 콘텐츠를 추가할 수 있게 해 주는 친절한 도우미이며, 페이지에 바로 쓰는 펜과 같습니다.

> **Pro tip:** 템플릿(예: 회사 레터헤드)에서 시작하려면 `new Document()` 대신 `new Document("template.docx")` 로 교체하세요.

### ## Insert Rectangle Shape and Other Shapes

이제 파란색 사각형과 초록색 타원을 추가합니다. 사각형은 **insert rectangle shape** 키워드를 보여주고, 타원은 다양한 도형 유형을 자유롭게 혼합할 수 있음을 보여줍니다.

```java
// Step 2: Insert a rectangle shape (100x50 points) and set its appearance
Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
rect.setLeft(50);                               // X‑coordinate in points
rect.setTop(50);                                // Y‑coordinate in points
rect.getFill().setColor(java.awt.Color.BLUE);  // Fill color

// Step 3: Insert an ellipse shape (80x80 points) and configure it
Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
ellipse.setLeft(180);
ellipse.setTop(30);
ellipse.getFill().setColor(java.awt.Color.GREEN);
```

**What’s happening under the hood?**  
`insertShape` 호출마다 `Shape` 객체가 생성되고 현재 단락에 자동으로 추가됩니다. `setLeft`/`setTop` 메서드는 페이지 여백을 기준으로 도형을 위치시키며, 단위는 포인트(1 pt = 1/72 in)입니다. 이 값을 조정하면 원하는 어디든 도형을 배치할 수 있습니다.

> **Common question:** *Can I add a picture instead of a solid color?*  
> 물론입니다—채우기 색을 이미지로 교체하려면 `shape.getFill().setImage("path/to/image.png")` 를 사용하면 됩니다.

### ## Group Shapes in Word for Easy Manipulation

두 개의 개별 객체도 괜찮지만, 보통은 함께 이동시키고 싶을 때가 많습니다. 바로 **group shapes in word** 가 빛을 발합니다.

```java
// Step 4: Create a GroupShape container and add the two shapes
GroupShape group = builder.insertGroupShape(); // Starts an empty group
group.appendChild(rect);
group.appendChild(ellipse);

// Step 5: Reposition the whole group as a single entity
group.setLeft(100);
group.setTop(150);
```

**Why group?**  
도형을 그룹화하면 이동, 회전, 크기 조정 등 모든 변환이 전체 컬렉션에 적용됩니다. 이는 Word UI에서 여러 도형을 선택하고 *Group* 버튼을 누르는 동작과 동일합니다. 또한 이후 코드를 단순화할 수 있어, 여러 객체를 개별적으로 조정할 필요가 없습니다.

> **Edge case:** 나중에 그룹을 해제해야 한다면 `group.getParentNode().removeChild(group)` 를 호출하고 자식들을 개별적으로 다시 삽입하면 됩니다.

### ## Save Document as DOCX and Verify Output

마지막으로 파일을 저장합니다. 이 단계가 **save document as docx** 요구사항을 충족합니다.

```java
// Step 6: Write the document to disk as a .docx file
String outputPath = "output/GroupShapeExample.docx";
doc.save(outputPath, SaveFormat.DOCX);
System.out.println("Document saved successfully to " + outputPath);
```

**What to expect:**  
생성된 `GroupShapeExample.docx` 를 Microsoft Word에서 열면 파란 사각형과 초록 타원이 깔끔하게 그룹화된 모습을 확인할 수 있습니다. 그룹을 드래그하면 두 도형이 함께 움직이며 UI와 동일한 동작을 보여줍니다.

> **Tip:** PDF가 필요하면 `SaveFormat.PDF` 를 사용하면 됩니다; 코드 변경 없이 바로 동작합니다.

### ## Full Working Example and Common Pitfalls

아래는 완전한 실행 가능한 Java 클래스입니다. 프로젝트에 복사‑붙여넣기하고 출력 폴더만 조정한 뒤 *Run* 하면 됩니다.

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle shape and set its position and fill color
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rect.setLeft(50);
        rect.setTop(50);
        rect.getFill().setColor(java.awt.Color.BLUE);

        // Step 3: Insert a second ellipse shape and configure its position and fill color
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
        ellipse.setLeft(180);
        ellipse.setTop(30);
        ellipse.getFill().setColor(java.awt.Color.GREEN);

        // Step 4: Group the two shapes together using the new GroupShape API
        GroupShape group = builder.insertGroupShape();
        group.appendChild(rect);
        group.appendChild(ellipse);

        // Step 5: Optionally reposition the entire group as a single object
        group.setLeft(100);
        group.setTop(150);

        // Step 6: Save the document containing the grouped shapes
        String outPath = "output/GroupShapeExample.docx";
        doc.save(outPath, SaveFormat.DOCX);
        System.out.println("Document saved successfully to " + outPath);
    }
}
```

#### Common Pitfalls & How to Avoid Them

| Issue | Why It Happens | Fix |
|-------|----------------|-----|
| **`NullPointerException` on `builder`** | `Document` 생성 후 `DocumentBuilder` 를 인스턴스화하지 않아 발생합니다. | `new DocumentBuilder(doc)` 를 도형 삽입 전에 반드시 실행하세요. |
| **Shapes appear off‑page** | 포인트 대신 픽셀 값을 사용하거나 여백을 고려하지 않았기 때문입니다. | Aspose.Words는 포인트 단위를 사용합니다; 72 pt = 1 in. `setLeft`/`setTop` 값을 이에 맞게 조정하세요. |
| **Group disappears after save** | 그룹을 만든 뒤 파일을 저장하고 다시 도형을 그룹에 추가했기 때문입니다. | `doc.save()` 호출 전에 반드시 그룹화를 완료하세요. |
| **File not found on save** | 출력 디렉터리가 존재하지 않음. | 프로그램matically 디렉터리를 생성(`new File("output").mkdirs();`)하거나 기존 경로를 사용하세요. |

---

## Conclusion

우리는 **create word document** 를 처음부터 만들고, **add shapes to word**, **insert rectangle shape**, **group shapes in word**, 그리고 최종적으로 **save document as docx** 하는 전체 과정을 몇 줄의 Java 코드만으로 구현했습니다. Aspose.Words의 강점은 명확한 객체 모델에 있으며, Word 파일을 캔버스로 취급해 도형으로 그림을 그리고 원하는 형식으로 내보낼 수 있습니다.

좀 더 도전해 보고 싶나요? 사각형을 별 모양으로 바꾸고, `Shape.getTextBox()` 로 도형 안에 텍스트를 넣거나, `shape.setRotationAngle(45)` 로 회전시켜 보세요. API는 풍부하고 가능성은 사실상 무한합니다.

북마크에 도형을 연결하거나 임베디드 폰트가 포함된 PDF로 내보내는 등 고급 시나리오에 대한 질문이 있으면 아래 댓글로 남겨 주세요. 함께 더 깊이 파고들겠습니다. Happy coding!

## What Should You Learn Next?

다음 튜토리얼들은 이 가이드에서 다룬 기술을 기반으로 하며, 단계별 설명과 완전한 코드 예제를 포함하고 있어 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}