---
category: general
date: 2026-10-13
description: Java를 사용하여 Word에서 그룹화된 도형을 만드는 방법을 배워보세요. 이 가이드는 그룹 도형을 삽입하고, 그룹에 선을
  추가하며, Word 전체에서 여러 도형을 그룹화하는 방법을 보여줍니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create grouped shapes
- add line to group
- group multiple shapes word
- insert group shape
language: ko
lastmod: 2026-10-13
og_description: Java를 사용해 Word에서 그룹화된 도형을 만들세요. 그룹 도형 삽입, 그룹에 선 추가, 여러 도형을 그룹화하는 전체
  튜토리얼을 따라보세요.
og_image_alt: Screenshot of a Word document showing created grouped shapes
og_title: Java로 Word에서 그룹화된 도형 만들기 – 단계별 가이드
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to create grouped shapes in Word with Java. This guide shows
    you how to insert group shape, add line to group, and group multiple shapes word‑wide.
  headline: How to create grouped shapes in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Java를 사용해 Word 문서에 그룹화된 도형을 만드는 방법
url: /ko/java/images-shapes/how-to-create-grouped-shapes-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java를 사용하여 Word 문서에서 그룹화된 도형 만들기

Java에서 Microsoft Word 파일에 **그룹화된 도형을 만들**어야 한다면, 이 튜토리얼이 전체 과정을 안내합니다. **그룹 도형 삽입** 방법, 같은 컨테이너에 사각형과 선을 배치하는 방법, 그리고 마지막으로 그룹화된 그래픽이 포함된 문서를 저장하는 방법을 확인할 수 있습니다.

도형을 그룹화하면 여러 개의 그리기 객체를 하나의 단위로 이동, 크기 조정 또는 스타일링하기가 쉬워집니다—다이어그램, 흐름도, 맞춤 페이지 장식에 이상적입니다. 이 가이드를 끝까지 읽으면 **그룹에 선 추가**하고, **Word 문서에서 여러 도형을 그룹화**하는 방법을 익히게 되며, 동일한 기술을 원하는 만큼의 도형에 재사용할 수 있습니다.

## 사전 요구 사항

- Java 17 이상이 개발 머신에 설치되어 있어야 합니다.  
- Aspose.Words for Java 라이선스(또는 무료 평가판)가 필요합니다.  
- Aspose.Words 의존성을 추가할 수 있는 Maven 또는 Gradle 프로젝트가 필요합니다:

```xml
<!-- Maven example -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

추가 라이브러리는 필요하지 않습니다.

## 1단계: 그룹 도형 컨테이너 삽입

첫 번째 단계는 문서에 **그룹 도형을 삽입**하는 것입니다. 이 컨테이너는 이후에 추가되는 모든 도형을 담게 됩니다.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // The rest of the code will add shapes to this group
```

`builder.insertGroupShape()`는 `GROUPSHAPE` 유형의 빈 `Shape` 객체를 생성합니다. 다른 그리기 객체를 담을 수 있는 투명 캔버스로 생각하면 됩니다.

## 2단계: 그룹에 사각형 추가

사각형은 종종 도형 그룹의 시각적 배경 역할을 합니다.

```java
        // Create a rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        rectangleShape.setLeft(0);      // X‑coordinate inside the group
        rectangleShape.setTop(0);       // Y‑coordinate inside the group

        // Append the rectangle to the group container
        groupShape.appendChild(rectangleShape);
```

`Left`와 `Top`을 `0`으로 설정하면 사각형이 그룹의 좌상단에 배치됩니다. 이 값을 변경하여 그룹 내에서 도형의 위치를 ​​조정할 수 있습니다.

## 3단계: **그룹에 선 추가** – 선 도형 만들기

이제 **그룹에 선을 추가**합니다. 선은 사각형 아래에 표시됩니다.

```java
        // Create a line shape
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);   // length of the line
        lineShape.setTop(60);      // vertical position (60 points down)

        // Append the line to the same group
        groupShape.appendChild(lineShape);
```

`Top` 속성은 선을 사각형 아래 60포인트 위치시켜 간단한 스택 레이아웃을 만듭니다. 가로 오프셋이 필요하면 `Left`도 설정할 수 있습니다.

## 4단계: 그룹화된 도형을 포함한 문서 저장

```java
        // Save the document to a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

Microsoft Word에서 `GroupShapeDemo.docx`를 열면 사각형과 선이 모두 포함된 하나의 그룹을 볼 수 있습니다. 그룹을 선택하면 두 도형을 함께 이동할 수 있어 **Word에서 여러 도형을 그룹화**에 성공했음을 보여줍니다.

## 전체 실행 가능한 예제

아래는 모든 import와 오류 처리를 포함한 완전한 프로그램입니다. IDE에 복사하고 `YOUR_DIRECTORY`를 기존 폴더 경로로 바꾼 뒤 실행하세요.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // Step 3: Add a rectangle to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);
        rectangleShape.setHeight(50);
        rectangleShape.setLeft(0);
        rectangleShape.setTop(0);
        groupShape.appendChild(rectangleShape);

        // Step 4: Add a line to the group
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);
        lineShape.setTop(60);
        groupShape.appendChild(lineShape);

        // Step 5: Save the document
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

### 예상 출력

- 대상 폴더에 `GroupShapeDemo.docx` 파일이 생성됩니다.  
- Word에서 파일을 열면 상단에 사각형, 하단에 선이 포함된 하나의 그룹 객체가 표시됩니다.  
- 그룹을 드래그하면 두 도형이 함께 이동하여 **그룹화된 도형을 성공적으로 만들었음**을 확인할 수 있습니다.

## 팁 및 일반적인 함정

- **전문가 팁:** 그룹 내부의 개별 도형을 회전하거나 스타일링해야 할 경우, 그룹에 추가하기 전에 해당 setter(`setRotation`, `getFill().setForeColor` 등)를 호출하세요. 그룹은 이러한 시각적 속성을 유지합니다.  
- **주의:** 선의 `Top` 속성을 설정하지 않으면 사각형과 겹쳐서 그룹이 어수선해 보일 수 있습니다.  
- **예외 상황:** 두 개 이상의 도형을 추가할 때는 각 자식의 좌표가 그룹의 원점(0,0)을 기준한다는 점을 기억하고 레이아웃을 계획하세요.  
- **성능 참고:** 수백 개와 같은 많은 도형을 그룹화하면 파일 크기가 약간 증가할 수 있지만, Word에서 이후 편집을 단순화합니다.

## 프로그래밍 방식으로 **Word 문서에서 여러 도형을 그룹화**하는 방법

위에서 보여준 패턴—그룹 컨테이너 생성, 각 자식 도형 설정, 추가—은 원, 그림, 텍스트 상자 등 어떤 도형에도 적용됩니다. `doc.save()`를 호출하기 전에 “도형 생성 → 속성 설정 → 추가” 단계를 반복하면 됩니다.

그룹에 이미 다른 도형이 포함된 상태에서 **그룹에 선을 추가**해야 한다면, 다음과 같이 기존 그룹을 가져올 수 있습니다:

```java
Shape existingGroup = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                                 .stream()
                                 .filter(s -> ((Shape) s).getShapeType() == ShapeType.GROUPSHAPE)
                                 .findFirst()
                                 .orElseThrow(() -> new IllegalStateException("No group found"));
existingGroup.appendChild(lineShape);
```

이는 문서 생명 주기의 어느 시점에서도 그룹을 수정할 수 있음을 보여줍니다.

## 결론

이제 Java와 Aspose.Words를 사용해 Word 문서에서 **그룹화된 도형을 만들**는 방법을 알게 되었습니다. **그룹 도형 삽입**, **그룹에 선 추가**, **Word에서 여러 도형을 그룹화**를 통해 복잡한 그림을 하나의 객체처럼 동작하도록 만들 수 있으며, 이는 다이어그램, 템플릿, 자동 보고서 생성에 이상적입니다.

다음으로, 관련 주제를 살펴보세요:

- **그룹화된 도형에 스타일 적용** – 모든 자식에게 한 번에 채우기 색, 테두리 및 효과를 설정하는 방법을 배웁니다.  
- **그룹화된 도형을 PDF로 내보내기** – 문서를 변환할 때 동일한 그룹이 유지되는 방식을 확인합니다.  
- **VBA로 도형 애니메이션** – Java로 생성한 그룹을 Word 매크로와 결합해 인터랙티브 문서를 만들 수 있습니다.

다양한 도형 유형, 크기 및 위치를 자유롭게 실험해 보세요. 그룹화는 여러 객체를 하나처럼 다룰 수 있는 유연성을 제공하여 코드와 사용자 상호작용을 모두 단순화합니다. 즐거운 코딩 되세요!

## 다음에 배울 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 단계별 설명과 함께 완전한 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Word 문서 만들기 Java – 그림자 효과가 있는 사각형 도형 추가](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Java로 Word에 사각형 도형 만들기 – 전체 가이드](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [.NET용 Aspose.Words를 사용해 Word 문서에 그룹 도형 만들기](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}