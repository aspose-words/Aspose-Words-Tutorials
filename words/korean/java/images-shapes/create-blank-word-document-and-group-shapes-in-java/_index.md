---
category: general
date: 2026-08-23
description: Aspose.Words for Java를 사용해 빈 Word 문서를 만들고, 도형을 그룹화하고 사각형 도형에 색을 입히는 방법을
  배우며, 몇 분 안에 문서를 docx 형식으로 저장하세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- save document as docx
- how to group shapes
- color rectangle shape
language: ko
lastmod: 2026-08-23
og_description: Aspose.Words for Java를 사용해 빈 Word 문서를 만든 후, 도형을 그룹화하고 사각형 도형에 색을 입히는
  방법을 확인하고, 문서를 효율적으로 docx 형식으로 저장합니다.
og_image_alt: Screenshot of a blank Word document containing grouped colored rectangle
  shapes
og_title: Java에서 빈 Word 문서를 만들고 도형을 그룹화하기 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create blank Word document with Aspose.Words for Java, learn how to
    group shapes, color rectangle shape, and save document as docx in minutes.
  headline: Create blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Java에서 빈 Word 문서를 만들고 도형을 그룹화하기
url: /ko/java/images-shapes/create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 빈 Word 문서 만들기 및 Java에서 도형 그룹화

프로그램matically 빈 Word 문서를 **create blank Word document** 해야 한다면, Aspose.Words for Java가 간단하게 해줍니다. 이 튜토리얼에서는 **create blank Word document**, **group shapes in Word** 삽입, **color rectangle shape** 적용, 그리고 최종적으로 **save document as docx** 하는 방법을 정확히 보여줍니다. 끝까지 읽으면 Java 프로젝트 어디에든 넣을 수 있는 재사용 가능한 코드 스니펫을 얻게 됩니다.

배우게 될 내용:

* Aspose.Words에 필요한 Maven/Gradle 종속성.
* `DocumentBuilder`와 빈 문서를 인스턴스화하는 방법.
* `GroupShape` 내부에서 **how to group shapes** 하는 정확한 단계.
* 사각형 도형에 채우기 색상을 설정하는 방법.
* **save document as docx**에 대한 모범 사례와 출력 파일 위치.

사전 경험이 필요하지 않지만, 기본 Java 개발에 익숙하고 JDK 8 이상 설치되어 있어야 합니다.

---

## Prerequisites

| 요구 사항 | 버전 / 상세 |
|-------------|-------------------|
| Java 개발 키트 | 8 이상 |
| 빌드 도구 | Maven 3+ 또는 Gradle 6+ |
| Aspose.Words for Java | 23.12 이상 (작성 시 최신 버전) |
| IDE (선택 사항) | IntelliJ IDEA, Eclipse, VS Code, 또는 Java‑호환 편집기 |

---

## 단계 1: 프로젝트에 Aspose.Words 추가

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

### Gradle

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **팁:** 기업 프록시를 사용하는 경우, 공식 문서에 설명된 대로 Maven/Gradle이 Aspose 저장소에서 패키지를 가져오도록 구성하십시오.

---

## 단계 2: 빌더를 사용하여 **Create blank Word document**

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new blank document
        Document doc = new Document();               // <-- create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` 생성자는 메모리 내에 빈 `.docx` 컨테이너를 생성합니다. `DocumentBuilder`는 도형을 포함한 콘텐츠를 추가할 수 있는 유창한 API를 제공합니다.

---

## 단계 3: **group shapes in Word** 컨테이너 삽입

```java
        // Step 3.1: Insert a GroupShape that will hold individual shapes
        // Width = 300 points, Height = 200 points
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

`GroupShape`는 미니 캔버스처럼 동작합니다. 여기에 추가된 모든 도형은 함께 이동하며, 이는 레이아웃 일관성을 위한 **how to group shapes**와 정확히 일치합니다.

---

## 단계 4: 첫 번째 **color rectangle shape** (red) 추가

```java
        // Step 4.1: Create the first rectangle and set its fill color to red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        // Append the rectangle to the group
        groupShape.appendChild(redRectangle);
```

`ShapeType.RECTANGLE` 상수는 간단한 사각형을 생성합니다. `getFill().setForeColor(...)`를 호출하면 **color rectangle shape**을 제어할 수 있습니다. `java.awt.Color.RED`를 원하는 `java.awt.Color` 상수나 사용자 정의 RGB 값으로 교체할 수 있습니다.

---

## 단계 5: 두 번째 **color rectangle shape** (green) 추가 및 위치 지정

```java
        // Step 5.1: Create a second rectangle, color it green, and offset it inside the group
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // Horizontal offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);
```

`setLeft`(또는 `setTop`)를 설정하면 **group shapes in Word** 컨테이너의 좌상단 모서리를 기준으로 도형이 이동합니다. 이는 정확한 위치 지정과 함께 **how to group shapes**를 보여줍니다.

---

## 단계 6: **Save document as docx** 및 결과 확인

```java
        // Step 6.1: Persist the document to the file system
        String outputPath = "output/GroupShapeDemo.docx";
        doc.save(outputPath);          // <-- save document as docx
        System.out.println("Document saved to: " + outputPath);
    }
}
```

`save` 메서드는 파일 확장자가 `.docx`이므로 자동으로 `.docx` 파일을 작성합니다. 다른 형식(예: PDF)이 필요하면 해당 `SaveFormat` 열거형을 전달하면 됩니다.

> **팁:** 대상 디렉터리(`output/` 예시)가 존재하는지 확인하거나 `new File("output").mkdirs();`를 사용해 프로그래밍 방식으로 생성하십시오.

---

## 빠른 복사를 위한 전체 소스 코드

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document
        Document doc = new Document();               // create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape (the container for grouped shapes)
        GroupShape groupShape = builder.insertGroupShape(300, 200);

        // 3️⃣ First rectangle – red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        groupShape.appendChild(redRectangle);

        // 4️⃣ Second rectangle – green, positioned next to the red one
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);

        // 5️⃣ Save the file as DOCX
        String outPath = "output/GroupShapeDemo.docx";
        doc.save(outPath);          // save document as docx
        System.out.println("Document saved to: " + outPath);
    }
}
```

**예상 출력:** Microsoft Word에서 `GroupShapeDemo.docx`를 열면 왼쪽에 빨간색, 오른쪽에 초록색 두 개의 색상 사각형이 포함된 단일 페이지가 표시되며, 그룹을 선택하면 함께 이동합니다.

---

## 일반적인 질문 및 엣지 케이스 처리

| 질문 | 답변 |
|----------|--------|
| *같은 그룹에 두 개 이상의 도형을 추가할 수 있나요?* | 예. 추가 도형마다 `groupShape.appendChild(yourShape)`를 호출하십시오. 그룹은 자동으로 가장 멀리까지 확장되도록 크기가 조정되며, 필요하면 직접 너비/높이를 조정할 수도 있습니다. |
| *다른 도형 유형(예: 타원)이 필요하면 어떻게 하나요?* | `ShapeType.RECTANGLE`을 `ShapeType.ELLIPSE`로 교체하십시오. 동일한 채우기 색상 로직이 적용됩니다. |
| *`Document` 객체를 해제해야 하나요?* | Aspose.Words는 내부적으로 네이티브 리소스를 관리합니다. JVM이 종료되면 리소스가 해제됩니다. 장기 실행 애플리케이션의 경우 **Aspose.Words for Java (Native)** 버전을 사용한다면 `doc.dispose();`를 호출하십시오. |
| *Z‑order를 변경하여 한 사각형을 위에 표시하려면 어떻게 해야 하나요?* | `groupShape.insertAfter(shape, referenceShape);` 또는 `groupShape.insertBefore(shape, referenceShape);`를 사용하여 그룹 내 자식들의 순서를 재배열하십시오. |
| *다른 섹션에 걸쳐 도형을 그룹화할 수 있나요?* | 아니요. `GroupShape`는 단일 단락 또는 도형 컨테이너 내에 있어야 합니다. 섹션을 넘어 그룹화하려면 각 섹션에 별도의 그룹을 생성하십시오. |

---

## 결론

이제 Aspose.Words for Java를 사용하여 **create blank Word document**, **group shapes in Word**, **color rectangle shape** 스타일을 적용하고 **save document as docx** 하는 방법을 알게 되었습니다. 이 패턴은 더 복잡한 레이아웃에도 확장할 수 있으며, 추가 도형을 삽입하고 오프셋을 조정하며 필요에 따라 그룹 내부에 텍스트, 이미지 또는 하이퍼링크를 설정하면 됩니다.

**다음 단계**를 탐색해 볼 수 있습니다:

* **group shapes in Word**를 사용하여 플로우차트 또는 UI 목업을 구축합니다.
* **save document as docx**와 PDF 변환(`doc.save("out.pdf")`)을 결합해 실험합니다.
* **color rectangle shape**에 그라디언트 또는 패턴을 적용하여 시각적 디자인을 풍부하게 합니다.
* 그룹화된 도형을 표나 차트와 결합하여 고급 보고서 문서를 만듭니다.

프로젝트 브랜드에 맞게 크기, 색상 또는 도형 유형을 자유롭게 수정하십시오. 즐거운 코딩 되세요!

## 다음에 배울 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 완전한 작동 코드 예제와 단계별 설명이 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Java로 Word 문서 만들기 – 그림자 효과가 있는 사각형 도형 추가](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words for Java로 문서를 PDF로 저장하는 방법](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Aspose.Words for Java에서 문서 도형 사용](/words/english/java/document-conversion-and-export/using-document-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}