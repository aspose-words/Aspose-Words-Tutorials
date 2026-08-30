---
category: general
date: 2026-07-26
description: Aspose.Words를 사용하여 Java에서 사각형 도형을 삽입합니다. 도형 크기 설정, 도형 위치 지정 및 DOCX 파일에서
  도형을 그룹화하는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- set shape size
- position shape
- how to group shapes
- how to add rectangle
language: ko
lastmod: 2026-07-26
og_description: Java에서 사각형 모양을 삽입하여 풍부한 DOCX 그래픽을 만들세요. 이 단계별 가이드를 따라 모양 크기 설정, 위치
  지정 및 모양 그룹화를 손쉽게 수행하세요.
og_image_alt: Screenshot showing a rectangle shape inserted and grouped in a Java‑generated
  Word document
og_title: Java에서 사각형 도형 삽입 – 그룹화 및 위치 지정 마스터
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert rectangle shape in Java using Aspose.Words. Learn how to set
    shape size, position shape, and how to group shapes in a DOCX file.
  headline: Insert Rectangle Shape in Java – Group and Position Shapes
  type: TechArticle
tags:
- Aspose.Words
- Java
- Shapes
- DOCX
title: Java에서 사각형 도형 삽입 – 도형 그룹화 및 위치 지정
url: /ko/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java에서 사각형 도형 삽입 – 도형 그룹화 및 위치 지정

Java 코드를 작성하면서 Word 문서에 **insert rectangle shape** 를 삽입해야 했던 적이 있나요? 당신만 그런 것이 아닙니다—보고서, 청구서, 맞춤 템플릿을 만드는 개발자들은 언제나 이 문제에 직면합니다. 좋은 소식은 Aspose.Words for Java 몇 줄만으로 **insert rectangle shape**, **set shape size**, **position shape**, 그리고 **how to group shapes** 를 사용해 도형을 하나의 단위로 움직일 수 있다는 것입니다.

이 가이드에서는 빈 문서를 만든 뒤 두 개의 사각형을 깔끔하게 그룹화한 `.docx` 파일을 저장하는 전체 과정을 단계별로 살펴봅니다. 끝까지 읽으면 **how to add rectangle** 객체를 추가하고, 크기를 제어하며, 정확한 위치에 배치하고, 재사용 가능한 그룹으로 묶는 방법을 알게 됩니다. Aspose.Words 외에 추가 라이브러리는 필요 없으며, 코드는 Java 8 이상에서 동작합니다.

## Prerequisites

- Java 8 이상이 설치되어 있어야 합니다 (저는 JDK 17을 사용하지만 Maven을 지원하는 어느 버전이라도 OK)
- Aspose.Words for Java 23.9 이상 – `pom.xml`에 의존성을 추가하거나 JAR 파일을 다운로드하세요
- Java 문법에 대한 기본 이해 (`main` 메서드만 작성할 수 있으면 충분합니다)
- 선호하는 IDE 또는 텍스트 편집기 (IntelliJ IDEA, Eclipse, VS Code 등)

> **Pro tip:** Maven을 사용한다면 의존성은 다음과 같습니다:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

이제 기본 설정이 끝났으니, 코드로 들어가 보겠습니다.

## Insert Rectangle Shape and Set Its Size

먼저 새로운 `Document`와 `DocumentBuilder`를 생성합니다. Builder는 페이지에 도형을 그리는 “펜” 역할을 합니다. 아래 예시에서는 **insert rectangle shape** 를 수행하고 바로 **set shape size** 를 100 × 80 포인트로 지정합니다.

```java
import com.aspose.words.*;

public class GroupedRectanglesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder to add content
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape(400, 200);
        // The group itself is 400×200 points – adjust as needed

        // ---------- First rectangle ----------
        // Insert rectangle shape
        Shape rectangle1 = new Shape(document, ShapeType.RECTANGLE);
        // Set shape size
        rectangle1.setWidth(100);
        rectangle1.setHeight(80);
        // Position shape inside the group
        rectangle1.setLeft(20);   // 20 points from the left edge of the group
        rectangle1.setTop(30);    // 30 points from the top edge of the group
        // Add the rectangle to the group
        group.appendChild(rectangle1);
```

`setWidth`/`setHeight` 호출이 포인트 단위(1 pt ≈ 1/72 인치)로 **set shape size** 를 설정하는 것을 확인하세요. `setSize` 를 사용해 한 번에 지정할 수도 있지만, 명시적인 호출이 의도를 더 명확히 합니다.

## Position Shape on the Page

첫 번째 사각형을 만든 뒤, 두 번째 사각형이 겹치지 않도록 **position shape** 해야 합니다. 위치 지정은 동일하게 `Left`와 `Top` 속성을 그룹의 원점 기준으로 설정하면 됩니다.

```java
        // ---------- Second rectangle ----------
        Shape rectangle2 = new Shape(document, ShapeType.RECTANGLE);
        rectangle2.setWidth(120);
        rectangle2.setHeight(60);
        // Position this rectangle a bit farther to the right and lower down
        rectangle2.setLeft(150);
        rectangle2.setTop(50);
        group.appendChild(rectangle2);
```

왜 `setX` 대신 `setLeft` 를 사용하는지 궁금하다면, Aspose.Words가 고전 Windows GDI 좌표계를 따르기 때문입니다—`Left`는 가로 오프셋, `Top`은 세로 오프셋을 의미합니다. 이 값을 조정하면 표나 단락을 건드리지 않고도 레이아웃을 미세 조정할 수 있습니다.

## How to Group Shapes

“그룹을 만들 필요가 있을까?” 라고 생각할 수 있습니다. 도형을 함께 이동시키거나, 한 번에 회전시키거나, 공통 스타일을 적용하고 싶을 때 그룹화가 유용합니다. 위 코드 조각에서는 `builder.insertGroupShape` 로 `GroupShape` 를 이미 생성했습니다. 이 객체는 본질적으로 컨테이너이며, 다른 도형 파일을 담는 폴더와 같은 역할을 합니다.

> **Why this matters:** 나중에 캡션을 추가하거나 전체 다이어그램을 회전하고 싶을 때, 각각의 사각형을 수정할 필요 없이 그룹만 수정하면 됩니다.

## How to Add Rectangle to a Group

**how to add rectangle** 를 그룹에 추가하는 방법은 간단히 `group.appendChild(rectangle)` 를 호출하는 것입니다. 내부적으로 Aspose.Words가 그룹의 컬렉션을 업데이트하고 경계 상자를 자동으로 재계산해 선언된 너비와 높이에 맞게 유지합니다.

```java
        // At this point the group already contains both rectangles.
        // You can also set the group’s border or fill if you like.
        group.getShapeStyle().setLineColor(Color.BLACK);
        group.getShapeStyle().setFillColor(Color.LIGHTGRAY);
```

다른 `ShapeType`—예: `ShapeType.ELLIPSE`, `ShapeType.TRIANGLE` 등—도 실험해 볼 수 있으며, 동일한 `appendChild` 패턴이 그대로 적용됩니다.

## Save the Document

마지막으로 문서를 디스크에 저장합니다. 경로는 절대 경로나 상대 경로나 상관없으며, 폴더가 존재하는지 확인만 하면 됩니다.

```java
        // Step 5: Save the document containing the grouped shapes
        String outPath = "output/GroupShape.docx";
        document.save(outPath);
        System.out.println("Document saved to: " + outPath);
    }
}
```

`GroupShape.docx` 를 Microsoft Word에서 열면, 두 개의 사각형이 나란히 배치되고 연한 회색 상자 안에 고정된 모습을 볼 수 있습니다. 회색 상자를 선택하면 두 사각형이 동시에 강조 표시됩니다—**how to group shapes** 가 실제로 작동한다는 증거입니다.

![Word 문서의 그룹화된 사각형](placeholder-image.png){: .center-image alt="Java‑생성 DOCX 파일에서 두 개의 사각형이 그룹화된 예시"}

*Image alt text (SEO):* **Java‑생성 DOCX 파일에서 두 개의 사각형이 그룹화된 예시**.

## Expected Output

- `output` 폴더에 위치한 `GroupShape.docx` 파일
- 문서 내부: 400 × 200 pt 크기의 그룹 안에 두 개의 사각형(100 × 80 pt 및 120 × 60 pt)이 각각 (20, 30)과 (150, 50) 위치에 배치됨
- 그룹은 얇은 검은색 테두리와 연한 회색 채우기를 가지고 있어 그룹화가 시각적으로 명확함

파일을 열어 회색 상자를 드래그해 보세요—두 사각형이 함께 움직여야 합니다. 움직이지 않으면 각 도형에 대해 `group.appendChild` 를 호출했는지 다시 확인하세요.

## Common Pitfalls & Edge Cases

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| **Rectangles appear outside the page** | `Left`/`Top` 값이 그룹 크기를 초과 | `insertGroupShape(width, height)` 로 그룹 크기를 늘리거나 오프셋을 줄이세요 |
| **Group disappears after saving** | 그룹의 `Width`/`Height` 가 0으로 설정 | `insertGroupShape` 호출 시 0이 아닌 크기를 지정하세요 |
| **Shape colors look wrong** | 기본 채우기가 투명해 Word에서 흰색으로 표시될 수 있음 | `setFillColor` 를 명시적으로 설정하거나 `ShapeStyle` 사용 |
| **Exception `ArgumentOutOfRangeException`** | 음수 좌표 사용 | `Left`와 `Top` 값을 음수가 되지 않도록 유지 |

이러한 문제를 초기에 해결하면 “왜 내 도형이 사라졌지?” 라는 흔한 고민을 피할 수 있습니다.

## Recap & Next Steps

우리는 Java에서 **insert rectangle shape** 의 전체 수명 주기를 다루었습니다: 문서 생성, **set shape size**, **position shape**, **how to group shapes**, 그리고 **how to add rectangle** 를 그룹에 추가하는 과정까지. 완전한 실행 예제는 위 코드 블록에 포함되어 있으며, Maven 프로젝트에 바로 붙여넣어 결과를 확인할 수 있습니다.

다음은 무엇을 해볼까요? 다음을 시도해 보세요:

- 각 사각형 안에 텍스트 추가하기

## What Should You Learn Next?

다음 튜토리얼들은 이 가이드에서 다룬 기술을 기반으로 하는 관련 주제를 다룹니다. 각각의 리소스에는 완전한 코드 예제와 단계별 설명이 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용하는 데 도움이 됩니다.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}