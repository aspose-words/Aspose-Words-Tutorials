---
category: general
date: 2026-11-15
description: Java를 사용하여 Word에 사각형 모양을 만들고, Word에 도형을 추가하는 방법, 도형 크기를 설정하는 방법, 그리고
  Word 문서를 효율적으로 저장하는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add shapes to word
- save word document
- set shape dimensions
- define shape size
language: ko
lastmod: 2026-11-15
og_description: Java를 사용하여 Word 문서에 사각형 모양을 만들기. Word에 도형을 추가하고, 도형 크기를 설정하며, 몇 분
  안에 Word 문서를 저장하는 방법을 배우세요.
og_image_alt: Screenshot showing a rectangle shape inside a group shape in a Word
  document
og_title: Java로 Word에서 사각형 도형 만들기 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  headline: Create rectangle shape in a Word document using Java
  type: TechArticle
- description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  name: Create rectangle shape in a Word document using Java
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well). * Aspose.Words
      for Java 23.10 or newer – you can obtain it from Maven Central. * A basic understanding
      of Java syntax and object‑oriented concepts.'
  - name: Expected output
    text: '* A Word file named `RectangleShapeDemo.docx`. * Inside the first paragraph,
      a group shape containing a 100 pt × 50 pt rectangle. * No text is added, so
      the rectangle appears on a blank page.'
  - name: What’s next?
    text: '* Explore **add shapes to Word** by inserting circles, arrows, or text
      boxes. * Combine multiple shapes into a single `GroupShape` and apply transformations
      (rotate, flip). * Generate reports that embed charts as shapes, then **save
      Word document** as PDF for sharing.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Java를 사용하여 Word 문서에 사각형 도형 만들기
url: /ko/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java를 사용하여 Word 문서에 사각형 모양 만들기

Word 파일 안에 **사각형 모양을 만들**어야 할 경우, 이 가이드는 Java로 정확히 어떻게 하는지 보여줍니다. **Word에 도형을 추가**하는 방법, **도형 크기 설정**을 제어하는 방법, 그리고 IDE를 떠나지 않고 **Word 문서 저장**하는 방법을 확인할 수 있습니다.

다음 섹션에서는 완전한 실행 가능한 예제, 각 라인에 대한 설명, 크기 문제와 문서 호환성 같은 일반적인 함정에 대한 팁을 제공합니다. 외부 참고 자료는 필요하지 않으며, Aspose.Words for Java 라이브러리만 있으면 됩니다.

## 배울 내용

* `Document`와 `DocumentBuilder` 초기화 방법
* **그룹 도형**을 삽입하고 그 안에 사각형을 배치하는 방법
* `setWidth`와 `setHeight`를 사용해 **도형 크기 정의**하는 방법
* `.docx` 형식으로 **Word 문서 저장**하는 방법
* 다양한 페이지 크기와 DPI 설정에 대한 예외 처리

### 전제 조건

* Java 17 이상 (코드는 Java 8에서도 컴파일됩니다)
* Aspose.Words for Java 23.10 이상 – Maven Central에서 얻을 수 있습니다
* Java 문법 및 객체‑지향 개념에 대한 기본 이해

> **Pro tip:** 나중에 원형이나 텍스트 상자 같은 다른 도형을 추가할 계획이라면 동일한 `GroupShape` 안에 보관하세요. 이렇게 하면 전체 컬렉션을 이동·회전·서식 지정하기가 훨씬 쉬워집니다.

## 1단계: 문서와 빌더 초기화

첫 번째 단계는 빈 Word 파일과 내용을 쓸 수 있는 `DocumentBuilder`를 만드는 것입니다.  

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*왜 중요한가:* `Document`는 전체 파일을 나타내고, `DocumentBuilder`는 텍스트, 표, **도형**을 삽입하기 위한 고수준 메서드를 제공합니다. 빌더가 없으면 저수준 노드를 직접 조작해야 합니다.

## 2단계: 여러 도형을 담을 그룹 도형 삽입

**그룹 도형**은 컨테이너 역할을 하며, 여러 도형을 추가하고 나중에 하나의 객체처럼 다룰 수 있습니다(예: 함께 이동·회전).

```java
        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();
```

*그룹 도형을 사용하는 이유* 사후에 화살표, 원, 레이블 등을 사각형 주변에 추가하고 싶다면, 그룹이 모든 요소를 정렬된 상태로 유지합니다. 또한 새로운 도형마다 `appendChild`를 한 번만 호출하면 되므로 **Word에 도형 추가** 작업 흐름이 단순해집니다.

## 3단계: 사각형 도형 만들기

이제 그룹 안에 들어갈 실제 사각형을 생성합니다. `Shape` 생성자는 소유 `Document`와 원하는 도형 유형을 필요로 합니다.

```java
        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
```

*왜 사각형인가?* `ShapeType.RECTANGLE`은 섹션 강조, 자리 표시자 생성, 간단한 UI 목업 등을 Word 안에서 직접 그릴 때 가장 흔히 사용하는 기본 도형입니다.

## 4단계: 사각형 크기 정의

크기를 설정하는 것이 바로 **도형 크기 설정**이 중요한 부분입니다. Aspose.Words가 지원하는 모든 측정 단위를 사용할 수 있으며, 기본 단위는 포인트(1 pt = 1/72 인치)입니다.

```java
        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

> **Note:** 밀리미터 단위를 선호한다면 `rectangle.setWidth(ConversionUtil.inchesToPoints(1.39));`와 같이 호출하세요. 여기서 `1.39 in ≈ 35 mm`이며, **도형 크기 정의**의 유연성을 보여줍니다.

## 5단계: 사각형을 그룹 도형에 추가

앞서 만든 그룹에 사각형을 추가하면 문서에 나타납니다.

```java
        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);
```

이 시점에서 사각형은 그룹의 좌상단에 배치됩니다. 정확한 위치가 필요하면 `rectangle.setLeft(...)`와 `rectangle.setTop(...)`로 나중에 이동할 수 있습니다.

## 6단계: (선택) 결과 확인을 위해 문서 저장

마지막으로 문서를 디스크에 기록합니다. 이것이 **Word 문서 저장** 단계이며, `.docx` 파일을 생성해 Microsoft Word, LibreOffice, Google Docs 등에서 열 수 있습니다.

```java
        // Step 6: Save the document (optional but recommended for verification)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

프로그램을 실행하면 `RectangleShapeDemo.docx`가 생성되고, 그룹 도형 안에 사각형 하나가 들어갑니다. 파일을 열면 흰색 사각형이 정확히 정의한 크기로 표시됩니다.

### 예상 출력

* `RectangleShapeDemo.docx`라는 이름의 Word 파일
* 첫 번째 단락 안에 100 pt × 50 pt 사각형을 포함한 그룹 도형
* 텍스트가 없으므로 사각형이 빈 페이지에 표시됨

## 일반적인 변형 및 예외 상황

| 상황 | 코드 적용 방법 |
|-----------|-----------------------|
| **다른 페이지 크기** (예: A4) | 도형을 삽입하기 전에 `document.getFirstSection().getPageSetup().setPaperSize(PaperSize.A4);` 호출 |
| **인쇄용 높은 DPI** | 원하는 DPI 비율만큼 너비·높이를 곱함, 예: `rectangle.setWidth(200 * 2);` (두 배 해상도) |
| **사각형 안에 텍스트 레이블 추가** | `TEXT_BOX` 유형의 `Shape`를 만들고, `setWidth`/`setHeight`를 사각형과 동일하게 맞춘 뒤 같은 `GroupShape`에 추가 |
| **사각형 회전** | `rectangle.setRotationAngle(45);` 로 시계 방향 45도 회전 |
| **DOCX 대신 PDF로 저장** | `document.save("output.docx");` 를 `document.save("output.pdf");` 로 교체 – 동일 API가 PDF에도 적용되어 사각형을 보존 |

## 견고한 구현을 위한 Pro 팁

1. **빌더 재사용** – 그룹 도형을 삽입한 뒤 새 빌더 인스턴스를 만들 필요 없이 단락이나 표를 계속 추가할 수 있습니다.
2. **리소스 해제** – Java 가비지 컬렉터가 대부분을 처리하지만, 스트림을 사용할 경우 `document.close();` 를 명시적으로 호출해 파일 핸들 누수를 방지하세요.
3. **크기 검증** – `setWidth`/`setHeight` 호출 전에 값이 양수인지 확인하세요. 음수 값은 `IllegalArgumentException`을 발생시킵니다.
4. **버전 호환성** – 코드는 Aspose.Words 23.x 이상에서 동작합니다. 이전 버전에서는 개별 세터 대신 `Shape.setSize(width, height)`를 사용해야 할 수 있습니다.

## 전체 실행 가능한 예제

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();

        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);

        // Optional: set a light gray fill to make it visible in Word
        rectangle.getFillColor() .setRGB(200, 200, 200);

        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);

        // Step 6: Save the document (you can also save as PDF)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

> **결과 확인:** `output/RectangleShapeDemo.docx`를 Microsoft Word에서 열어 보세요. 지정한 크기의 사각형이 첫 페이지 상단 중앙에 표시됩니다. 사각형이 너무 작게 보이면 `setWidth`와 `setHeight`에 전달하는 값을 조정하면 됩니다.

## 결론

이제 Java를 사용해 Word 파일에 **사각형 모양을 만들**고, `GroupShape`를 통해 **Word에 도형 추가**하며, **도형 크기 설정**과 **도형 크기 정의**를 수행하고, 최종적으로 **Word 문서 저장**하는 방법을 알게 되었습니다. 동일한 패턴을 다른 도형 유형에도 적용해 프로그래밍 방식으로 복잡한 다이어그램을 만들 수 있습니다.

### 다음 단계는?

* 원, 화살표, 텍스트 상자 등을 삽입해 **Word에 도형 추가**를 탐색
* 여러 도형을 하나의 `GroupShape`에 결합하고 변환(회전, 뒤집기) 적용
* 차트를 도형으로 삽입한 보고서를 생성한 뒤 **Word 문서**를 PDF로 저장해 공유

차원, 색상, 위치 등을 자유롭게 실험해 보세요. 즐거운 코딩 되세요!


## 다음에 배워야 할 내용


다음 튜토리얼은 이 가이드에서 다룬 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 포함해 추가 API 기능을 마스터하고 프로젝트에 적용할 수 있는 대체 구현 방식을 탐색하도록 돕습니다.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide](/words/english/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/)
- [Create word document java – hide shape and set fill color](/words/english/java/images-shapes/create-word-document-java-hide-shape-and-set-fill-color/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}