---
category: general
date: 2026-09-27
description: Java에서 빈 Word 문서를 만들고 Aspose.Words를 사용하여 도형을 그룹화합니다. 도형 크기 설정, 도형 채우기
  색상 설정, 그리고 자식을 그룹에 추가하는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- set shape size
- set shape fill color
- append child to group
language: ko
lastmod: 2026-09-27
og_description: Aspose.Words를 사용하여 Java에서 빈 워드 문서를 생성합니다. 이 튜토리얼에서는 Word에서 도형을 그룹화하고,
  도형 크기를 설정하며, 도형 채우기 색상을 지정하고, 그룹에 자식을 추가하는 방법을 보여줍니다.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Java에서 빈 Word 문서를 만들고 도형을 그룹화하기 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create a blank Word document in Java and group shapes using Aspose.Words.
    Learn to set shape size, set shape fill color, and append child to group.
  headline: How to create blank word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Java에서 빈 워드 문서를 만들고 도형을 그룹화하는 방법
url: /ko/java/images-shapes/how-to-create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java에서 빈 워드 문서를 만들고 도형을 그룹화하는 방법

프로그램matically **빈 워드 문서를 만들**어야 한다면, 이 가이드는 Aspose.Words for Java를 사용하여 정확히 어떻게 하는지 보여줍니다. 또한 **워드에서 도형을 그룹화**하고, 각 도형의 크기를 설정하고, 채우기 색을 적용하며, **그룹에 자식 추가**하여 객체가 하나의 단위로 동작하도록 하는 방법을 배울 수 있습니다.

코드로 Word 파일을 다루면 수동 포맷팅을 피할 수 있고, 보고서, 계약서, 마케팅 브로셔 등을 자동으로 생성할 수 있습니다. 이 튜토리얼을 마치면 파란색 사각형과 이미지가 함께 그룹화된 `.docx` 파일을 생성하는 실행 가능한 Java 프로그램을 얻게 됩니다.

## Prerequisites

시작하기 전에 다음이 준비되어 있는지 확인하세요:

- Java 17(또는 최신 JDK) 설치
- Maven 또는 Gradle을 사용하여 종속성 관리
- Aspose.Words for Java 라이선스(무료 평가판을 테스트에 사용할 수 있음)
- 코드에서 참조할 수 있는 폴더에 배치된 샘플 이미지 파일(예: `sample.jpg`)

> **Pro tip:** 이미지 파일을 `resources` 디렉터리에 보관하고 `ClassLoader.getResourceAsStream`으로 로드하면 절대 경로를 하드코딩하는 일을 피할 수 있습니다.

## Step 1: Create a blank word document and add a GroupShape

첫 번째 단계는 빈 Word 파일을 나타내는 새로운 `Document` 객체를 인스턴스화하고, 그 다음 `GroupShape`를 삽입하는 것입니다. 이 그룹은 이후에 추가할 모든 도형의 컨테이너 역할을 합니다.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();                     // create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape();     // group shapes in word
```

*Why this matters:* `GroupShape`를 사용하면 여러 도형을 함께 이동, 회전 또는 서식 지정할 수 있어 다이어그램이나 워터마크와 같은 복잡한 레이아웃에 필수적입니다.

## Step 2: Insert a rectangle and **set shape size**

다음으로 사각형을 만들고, 크기를 정의한 뒤 그룹에 추가합니다. 이는 **set shape size** 작업을 보여줍니다.

```java
        // Step 2: Create a rectangle shape, configure its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);                         // set shape size – width 100 points
        rectangle.setHeight(50.0);                         // set shape size – height 50 points
        rectangle.setFillColor(java.awt.Color.BLUE);      // set shape fill color to blue
        group.appendChild(rectangle);                     // append child to group
```

*Explanation:* `setWidth`와 `setHeight`는 도형의 정확한 크기를 포인트 단위(1 포인트 = 1/72 인치)로 제어합니다. 레이아웃 요구에 맞게 값을 조정하세요.

## Step 3: **Set shape fill color** for the rectangle

`setFillColor`를 사용해 사각형 배경을 파란색으로 설정합니다. `java.awt.Color` 상수를 사용하거나 사용자 정의 RGB 색을 만들 수 있습니다.

```java
        // The fill color was already applied in the previous step.
        // If you need a different color later, just call setFillColor again:
        // rectangle.setFillColor(new java.awt.Color(255, 165, 0)); // orange
```

*Why it’s useful:* 채우기 색은 객체를 시각적으로 구분하는 데 도움이 되며, 특히 문서를 PDF로 내보내거나 인쇄할 때 유용합니다.

## Step 4: Insert an image and **append child to group**

이제 같은 `GroupShape`에 이미지를 추가합니다. 이미지는 `DocumentBuilder.insertImage`를 통해 삽입한 뒤 그룹에 추가되어 사각형과 함께 움직입니다.

```java
        // Step 4: Insert an image and add it to the same group
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        group.appendChild(picture);                       // append child to group
```

*Edge case:* 이미지 경로가 잘못되면 Aspose.Words가 `FileNotFoundException`을 발생시킵니다. 상대 경로를 사용하거나 리소스에서 이미지를 로드하여 문제를 방지하세요.

## Step 5: **Save the document with the grouped shapes**

마지막으로 문서를 디스크에 저장합니다. 결과 파일에는 사각형과 이미지가 함께 그룹화되어 들어갑니다.

```java
        // Step 5: Save the document with the grouped shapes
        doc.save("YOUR_DIRECTORY/GroupShape.docx");       // creates the blank word document with grouped shapes
    }
}
```

### Expected output

- 지정된 디렉터리에 `GroupShape.docx`라는 파일이 생성됩니다.
- Microsoft Word에서 파일을 열면 파란 사각형과 선택한 이미지가 하나의 객체로 선택된 빈 페이지가 표시됩니다(함께 이동하거나 크기 조정 가능).

![그룹화된 도형이 포함된 빈 워드 문서 만들기](/images/grouped-shapes.png "그룹화된 도형이 포함된 빈 워드 문서 만들기")

*위 스크린샷은 새로 만든 Word 문서 안에 최종 그룹화된 도형이 어떻게 표시되는지 보여줍니다.*

## Common variations and additional tips

| 상황 | 처리 방법 |
|-----------|-----------------|
| **여러 이미지** | 각 이미지를 `builder.insertImage`로 삽입하고 `group.appendChild(picture)`를 각각 호출합니다. |
| **다양한 도형 유형** | `Shape` 객체를 만들 때 `ShapeType.OVAL`, `ShapeType.LINE` 등 원하는 타입을 사용합니다. |
| **그룹 위치 변경** | 모든 자식을 추가한 뒤 `group.setLeft(x)`와 `group.setTop(y)`를 설정해 전체 그룹을 이동합니다. |
| **PDF로 내보내기** | 그룹화 후 `doc.save("output.pdf")`를 호출하면 PDF에서도 그룹이 유지됩니다. |
| **라이선스 적용** | 평가판을 사용하면 워터마크가 표시됩니다. 정식 라이선스를 설치하면 제거됩니다. |

## Conclusion

이제 Aspose.Words for Java를 사용해 **빈 워드 문서를 만들**, **GroupShape**을 삽입하고, **set shape size**, **set shape fill color**, **append child to group**을 수행하는 방법을 알게 되었습니다. 이 패턴을 활용하면 복잡한 프로그래밍 레이아웃을 구축하고, 나중에 Word에서 편집하거나 다른 형식으로 내보낼 수 있습니다.

다음 단계로 **워드에서 도형을 그룹화**하고 텍스트 상자를 추가하거나 도형에 하이퍼링크를 삽입하고, 다페이지 보고서 자동 생성을 시도해 보세요. 원리는 동일합니다—추가 도형을 만들고 속성을 설정한 뒤 같은 그룹에 추가하면 됩니다.

Happy coding!

## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 다룬 기술을 기반으로 하는 밀접한 주제를 다룹니다. 각 자료에는 완전한 코드 예제와 단계별 설명이 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에 적용할 수 있는 다양한 구현 방법을 탐색할 수 있습니다.

- [Java로 Word에서 사각형 도형 만들기 – 전체 가이드](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Java로 Word 문서 만들기 – 그림자 효과가 있는 사각형 도형 추가](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [.NET용 Aspose.Words를 사용하여 Word 문서에 그룹 도형 만들기](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}