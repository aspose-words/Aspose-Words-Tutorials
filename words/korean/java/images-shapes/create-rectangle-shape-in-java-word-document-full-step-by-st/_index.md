---
category: general
date: 2026-05-26
description: Java Word 문서에 사각형 모양을 만들고 그림자 효과를 적용합니다. 모양 그림자를 추가하고 그림자 거리를 설정하며 파일을
  저장하는 방법을 배웁니다.
draft: false
keywords:
- create rectangle shape
- apply shadow effect
- create word document java
- add shape shadow
- set shadow distance
language: ko
og_description: Java Word 문서에서 사각형 모양을 만들고, 그림자 효과를 적용하며, 모양 그림자를 추가하고, Aspose.Words를
  사용하여 그림자 거리를 설정합니다.
og_title: Java 워드 문서에서 사각형 도형 만들기 – 완전 가이드
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create rectangle shape in a Java Word document and apply shadow effect.
    Learn how to add shape shadow, set shadow distance, and save the file.
  headline: Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in a Java Word document and apply shadow effect.
    Learn how to add shape shadow, set shadow distance, and save the file.
  name: Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide
  steps:
  - name: “Can I use a different shape?”
    text: Absolutely. Replace `ShapeType.RECTANGLE` with `ShapeType.OVAL`, `ShapeType.LINE`,
      or any other supported enum. The rest of the shadow code stays the same.
  - name: “What if I need multiple shadows?”
    text: Aspose.Words only supports a single shadow per shape. To simulate multiple
      shadows, duplicate the shape, offset each copy, and adjust the transparency.
  - name: “Is the shadow visible in LibreOffice?”
    text: Yes—Aspose.Words writes standard OOXML, which LibreOffice interprets correctly.
      The shadow may look slightly different due to rendering engines, but the effect
      persists.
  - name: “How do I change the shadow color to match my brand?”
    text: Just swap `java.awt.Color.GRAY` with any `java.awt.Color` you prefer, such
      as `new java.awt.Color(0, 120, 215)` for a corporate blue.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word Automation
title: Java 워드 문서에서 사각형 도형 만들기 – 전체 단계별 가이드
url: /ko/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java Word 문서에서 사각형 도형 만들기 – 전체 단계별 가이드

Java Word 문서에서 **사각형 도형 만들기**가 필요했지만 어디서 시작해야 할지 몰랐던 적이 있나요? 여러분만 그런 것이 아닙니다—많은 개발자들이 보고서나 청구서를 프로그래밍으로 생성할 때 이 문제에 부딪힙니다. 이 튜토리얼에서는 **사각형 도형 만들기** 방법, 세련된 그림자 적용, 그리고 그림자 거리를 미세 조정하여 결과를 전문적으로 보이게 하는 과정을 단계별로 안내합니다.

우리는 Microsoft Office가 설치되지 않아도 Word 파일을 조작할 수 있는 강력한 라이브러리인 Aspose.Words for Java를 사용할 것입니다. 이 가이드를 마치면 **create word document java** 프로젝트에서 **add shape shadow**, **apply shadow effect**, **set shadow distance**를 몇 줄의 코드만으로 구현할 수 있게 됩니다.

---

## 만들게 될 것

- 시안 색상의 사각형이 포함된 새 `.docx` 파일.
- 흐림, 각도, 부분 투명도가 적용된 현실적인 드롭 섀도우.
- 그림자와 도형 사이 거리의 전체 제어.
- Maven 또는 Gradle 프로젝트에 바로 넣어 실행할 수 있는 준비된 Java 클래스.

외부 도구 없이, 수동 UI 단계 없이—오직 순수 코드만 사용합니다.

---

## 사전 요구 사항

- Java 8 이상 (코드는 Java 11, Java 17 등에서도 작동합니다).
- Aspose.Words for Java 라이브러리 (Maven Central에서 제공).
- 선호하는 IDE 또는 텍스트 편집기 (IntelliJ IDEA, Eclipse, VS Code 등).
- Java 구문에 대한 기본적인 이해.

Maven 의존성을 한 번도 추가해 본 적이 없다면, 아래 간단한 스니펫을 참고하세요:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

이제 시작해 봅시다.

---

## 단계 1: Word 문서에서 사각형 도형 만들기

먼저 필요한 것은 빈 문서와 `DocumentBuilder`입니다. Builder를 문서에 쓰는 펜이라고 생각하면 됩니다. 이를 확보하면 단 한 번의 메서드 호출로 **create rectangle shape**를 할 수 있습니다.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape of 150x80 points.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
        // Make the shape visible by filling it with cyan.
        rectangleShape.setFillColor(java.awt.Color.CYAN);
```

> **왜 중요한가:** `insertShape` 메서드는 기하학적 형태를 생성할 뿐만 아니라 도형을 문서의 내부 컬렉션에 추가하므로 바로 스타일링을 시작할 수 있습니다.

---

## 단계 2: 도형에 그림자 효과 적용

이제 사각형이 페이지에 존재하므로 **apply shadow effect**를 적용합니다. 그림자는 깊이를 부여해 도형이 페이지에서 떠 있는 듯한 느낌을 주며, 보고서 가독성을 높이는 미묘한 UI 개선 효과가 있습니다.

```java
        // Retrieve the shadow format object.
        ShadowFormat shadowFormat = rectangleShape.getShadowFormat();

        // Enable the shadow and configure its appearance.
        shadowFormat.setVisible(true);          // Turn the shadow on.
        shadowFormat.setBlur(5.0);              // Soft blur radius.
        shadowFormat.setAngle(45.0);            // Direction of the shadow.
        shadowFormat.setColor(java.awt.Color.GRAY); // Shadow color.
        shadowFormat.setTransparency(0.3);     // 30% transparent.
```

> **프로 팁:** `5.0`의 블러 값은 대부분 화면에 표시되는 문서에 자연스럽게 보입니다. 인쇄할 경우 흐릿해 보이지 않도록 약간 낮은 값을 사용할 수 있습니다.

---

## 단계 3: 그림자 거리 설정 – 위치 미세 조정

그림자는 블러뿐만 아니라 올바른 오프셋도 필요합니다. 여기서 **set shadow distance**를 수행합니다. `7.0` 포인트의 거리는 눈에 띄지만 과하지 않은 적당한 오프셋을 만들어 줍니다.

```java
        // Define how far the shadow sits from the shape.
        shadowFormat.setDistance(7.0); // Distance in points.
```

> **더 큰 오프셋이 필요하면?** 값을 늘리고, 더 촘촘한 느낌을 원하면 줄이세요. 거리 값은 각도와 함께 작동해 그림자를 정확히 배치한다는 점을 기억하세요.

---

## 단계 4: 문서 저장 – 작업 내용 영구 저장

마지막으로 문서를 디스크에 저장합니다. 파일이 저장될 경로를 원하는 위치로 변경하세요.

```java
        // Save the document with the rectangle and its shadow.
        doc.save("YOUR_DIRECTORY/shadow.docx");
    }
}
```

클래스를 실행하면 `shadow.docx` 파일이 생성되며, Microsoft Word 또는 LibreOffice에서 열면 45° 각도로 기울어지고 7 포인트 오프셋된 부드러운 회색 그림자가 있는 시안 색 사각형이 표시됩니다.

---

## 전체 작동 예제

아래는 복사‑붙여넣기 바로 사용할 수 있는 전체 코드입니다. 모든 import, 주석, 최종 `save` 호출이 포함되어 있습니다.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape of the desired size.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
        // Step 3: Apply a fill color to make the shape visible.
        rectangleShape.setFillColor(java.awt.Color.CYAN);

        // Step 4: Configure the shape's shadow effect.
        ShadowFormat shadowFormat = rectangleShape.getShadowFormat();
        shadowFormat.setVisible(true);          // Enable the shadow.
        shadowFormat.setBlur(5.0);              // Set the blur radius.
        shadowFormat.setDistance(7.0);          // Define how far the shadow is from the shape.
        shadowFormat.setAngle(45.0);            // Set the direction of the shadow.
        shadowFormat.setColor(java.awt.Color.GRAY); // Choose the shadow color.
        shadowFormat.setTransparency(0.3);      // Make the shadow partially transparent.

        // Step 5: Save the document with the shaped shadow.
        doc.save("YOUR_DIRECTORY/shadow.docx");
    }
}
```

**예상 출력:** `shadow.docx`를 열면 첫 페이지 중앙에 시안 색 사각형이 표시되고, 오른쪽 아래로 약간 오프셋된 미묘한 회색 그림자가 드리워집니다. 그림자의 블러와 투명도가 자연스러운 조명처럼 보이게 합니다.

---

## 자주 묻는 질문 및 엣지 케이스

### “다른 도형을 사용할 수 있나요?”

물론 가능합니다. `ShapeType.RECTANGLE`을 `ShapeType.OVAL`, `ShapeType.LINE` 또는 지원되는 다른 enum으로 교체하면 됩니다. 나머지 그림자 코드는 동일하게 유지됩니다.

### “여러 개의 그림자가 필요하면 어떻게 하나요?”

Aspose.Words는 도형당 하나의 그림자만 지원합니다. 여러 그림자를 시뮬레이션하려면 도형을 복제하고 각 복제본을 오프셋한 뒤 투명도를 조정하세요.

### “LibreOffice에서도 그림자가 보이나요?”

네—Aspose.Words는 표준 OOXML을 작성하므로 LibreOffice가 올바르게 해석합니다. 렌더링 엔진 차이로 그림자가 약간 다르게 보일 수 있지만 효과는 유지됩니다.

### “브랜드에 맞게 그림자 색을 바꾸려면 어떻게 하나요?”

`java.awt.Color.GRAY`를 원하는 `java.awt.Color`로 교체하면 됩니다. 예를 들어 기업용 파란색은 `new java.awt.Color(0, 120, 215)`와 같이 사용할 수 있습니다.

---

## 이미지 일러스트레이션

![Java Word 문서에서 사각형 도형 만들기](https://example.com/images/rectangle-shadow.png)

*Alt text:* **create rectangle shape** 일러스트레이션으로, Word 문서에 시안 색 사각형과 회색 드롭 섀도우가 표시됩니다.

---

## 요약 및 다음 단계

우리는 Aspose.Words for Java를 사용하여 **create rectangle shape**, **apply shadow effect**, **add shape shadow**, **set shadow distance**를 구현하는 방법을 다루었습니다. 코드는 독립적이며 최신 JDK에서 실행되고 배포 준비가 된 깔끔한 `.docx` 파일을 생성합니다.

더 나아가고 싶나요? 다음을 시도해 보세요:

- `builder.moveTo(rectangleShape.getAbsolutePosition())`를 사용해 사각형 안에 텍스트 추가하기.
- 도형 테이블을 만들어 다이어그램 구성하기.
- 문서를 PDF로 내보내기 (`doc.save("output.pdf", SaveFormat.PDF);`).

이러한 작업은 방금 살펴본 기본 원칙을 기반으로 하므로 예제를 확장하는 데 익숙해질 것입니다.

---

## 최종 생각

**create word document java**와 같은 도형 및 그림자 작업을 마스터하면 보고서, 계약서, 마케팅 자료 등을 자동화할 때 큰 경쟁력을 얻을 수 있습니다. 여기서 제시한 방법은 깔끔하고 유지보수가 쉬우며, 무엇보다도 필요한 시각 스타일에 맞게 쉽게 조정할 수 있습니다.

코드를 실행해 보고, 블러, 각도, 거리 값을 조정해 보세요. 그러면 문서가 평범함에서 세련됨으로 변하는 것을 확인할 수 있습니다. 문제가 발생하면 아래에 댓글을 남겨 주세요. 기꺼이 도와드리겠습니다.

행복한 코딩 되세요!

## 관련 튜토리얼

- [Word 문서 Java 만들기 – 그림자 효과가 있는 사각형 도형 추가](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words for Java에서 DocumentBuilder를 사용해 폼 필드 생성 및 내용 추가 방법](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Word에서 바코드 생성으로 PDF 만들기 – Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-barcode-generation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}