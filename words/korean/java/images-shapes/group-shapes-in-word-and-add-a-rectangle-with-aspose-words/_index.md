---
category: general
date: 2026-09-11
description: Word에서 도형을 그룹화하고 Aspose.Words for Java를 사용하여 사각형 도형을 추가합니다. 도형 크기 설정,
  객체 그룹화 및 문서 저장 방법을 배워보세요.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- how to group shapes
- how to add rectangle
language: ko
lastmod: 2026-09-11
og_description: Word에서 도형을 그룹화하고 Aspose.Words for Java를 사용하여 사각형 도형을 추가합니다. 이 튜토리얼에서는
  도형 크기 설정, 도형 그룹화 및 문서 내보내는 방법을 보여줍니다.
og_image_alt: Screenshot showing grouped shapes in a Word document
og_title: Word에서 도형 그룹화 – Aspose.Words로 사각형 추가
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  headline: Group shapes in Word and add a rectangle with Aspose.Words
  type: TechArticle
- description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  name: Group shapes in Word and add a rectangle with Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17 or later installed. * Maven or Gradle to manage dependencies.
      * A valid Aspose.Words for Java license (or a free evaluation key). * An image
      file (`sample.png`) placed in a known directory (replace `YOUR_DIRECTORY` with
      your actual path).'
  - name: Add a group shape
    text: A group shape is a container that can hold other shapes. Think of it as
      a folder for drawing objects.
  - name: How to add rectangle
    text: The code above demonstrates **how to add rectangle** by creating a `Shape`
      instance with `ShapeType.RECTANGLE` and then appending it to the `GroupShape`.
      This pattern works for any other shape type (e.g., `ELLIPSE`, `POLYLINE`).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Word에서 도형 그룹화 및 Aspose.Words로 사각형 추가
url: /ko/java/images-shapes/group-shapes-in-word-and-add-a-rectangle-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word에서 도형을 그룹화하고 Aspose.Words로 사각형 추가

프로그래밍 방식으로 사각형을 추가하면서 **Word에서 도형을 그룹화**해야 하는 경우, 이 가이드는 완전하고 바로 실행할 수 있는 솔루션을 제공합니다. 그룹 도형을 삽입하고, 사각형 도형을 추가하고, 도형 크기를 설정한 다음, 문서를 저장하여 즉시 결과를 확인하는 방법을 정확히 보여줍니다.

Word 문서를 다룰 때는 종종 여러 객체—그림, 차트 또는 간단한 기하학적 도형—를 하나의 논리적 단위로 배열해야 합니다. 이러한 객체를 그룹화하면 함께 이동, 회전 또는 스타일을 적용하기가 쉬워집니다. 이 튜토리얼에서는 **사각형 추가 방법**과 **도형 크기 설정**을 다루어 완벽한 레이아웃 제어를 구현합니다.

## 배울 내용

* Aspose.Words for Java를 사용하여 새 Word 문서를 만드는 방법.  
* **도형을 그룹화**하여 단일 객체처럼 동작하도록 하는 방법.  
* 그룹에 **사각형 도형을 추가**하고 동일한 그룹에 이미지를 삽입하는 방법.  
* 사각형과 이미지 모두에 **도형 크기 설정**하는 방법.  
* 문서를 저장하고 Microsoft Word에서 열어 결과를 확인하는 방법.

### 사전 요구 사항

* Java 17 이상이 설치되어 있어야 합니다.  
* Maven 또는 Gradle을 사용하여 종속성을 관리합니다.  
* 유효한 Aspose.Words for Java 라이선스(또는 무료 평가 키).  
* 알려진 디렉터리에 이미지 파일(`sample.png`)을 배치합니다(`YOUR_DIRECTORY`를 실제 경로로 교체).

---

## Aspose.Words를 사용하여 Word에서 도형을 그룹화하는 방법

첫 번째 단계는 `Document`와 `DocumentBuilder`를 생성하는 것입니다. 빌더는 도형, 텍스트 및 기타 요소를 삽입하기 위한 편리한 API를 제공합니다.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Initialize the document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **왜 중요한가:** `DocumentBuilder`는 기본 `Document` 객체와 직접 작동하여 저수준 노드 컬렉션을 수동으로 처리하지 않고도 도형을 삽입할 수 있게 합니다.

### 그룹 도형 추가

그룹 도형은 다른 도형을 담을 수 있는 컨테이너입니다. 이를 그림 객체를 위한 폴더라고 생각하면 됩니다.

```java
        // Insert an empty group shape – this will hold the rectangle and the picture
        GroupShape group = builder.insertGroupShape();
```

`insertGroupShape()` 메서드는 `GroupShape` 노드를 생성하고 반환하므로 이후에 자식 도형을 추가할 수 있습니다.  

---

## 그룹에 사각형 도형 추가

이제 앞서 만든 그룹에 **사각형 도형을 추가**합니다. 사각형은 그림의 배경이나 테두리 역할을 합니다.

```java
        // Create a rectangle shape with a specific size
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points
        rectangle.setHeight(50.0);   // height in points
        rectangle.setFillColor(java.awt.Color.LIGHT_GRAY);
        rectangle.setStrokeColor(java.awt.Color.DARK_GRAY);
        rectangle.setStrokeWeight(1.0);
        // Append the rectangle to the group
        group.appendChild(rectangle);
```

> **팁:** `FillColor`와 `StrokeColor`를 설정하면 최종 문서에서 사각형이 보이게 됩니다. 이 속성을 생략하면 도형이 투명하게 표시될 수 있습니다.

### 사각형 추가 방법

위 코드는 `ShapeType.RECTANGLE`으로 `Shape` 인스턴스를 생성하고 이를 `GroupShape`에 추가함으로써 **사각형을 추가하는 방법**을 보여줍니다. 이 패턴은 다른 도형 유형(`ELLIPSE`, `POLYLINE` 등)에도 적용됩니다.

---

## 사각형 및 이미지에 대한 도형 크기 설정

적절한 크기 설정은 사각형과 그림이 올바르게 정렬되도록 보장합니다. 여기서는 다음에 삽입할 이미지에 대해서도 **도형 크기 설정**을 수행합니다.

```java
        // Insert an image and set its size
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.png");
        picture.setWidth(100.0);   // match rectangle width
        picture.setHeight(50.0);   // match rectangle height
        // Append the picture to the same group
        group.appendChild(picture);
```

이제 사각형과 그림은 동일한 크기(100 × 50 포인트)를 공유합니다. 같은 그룹에 속해 있기 때문에 그룹을 이동하거나 회전하면 두 도형이 함께 영향을 받습니다.

> **왜 크기를 맞추나요?** 치수를 맞추면 이미지가 사각형 안에 깔끔하게 들어가 “액자 그림” 효과를 만들 수 있습니다.

---

## 문서를 저장하고 결과 보기

마지막으로 문서를 디스크에 저장합니다. Microsoft Word에서 파일을 열면 그룹화된 도형이 하나의 선택 가능한 객체로 표시됩니다.

```java
        // Save the document – the group will appear as one object in Word
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved successfully.");
    }
}
```

`output.docx`를 열면 이미지가 들어간 사각형을 볼 수 있습니다. 도형을 클릭하면 사각형과 그림이 모두 선택되는데, 이는 두 도형이 **그룹화**되어 있기 때문입니다.

![Word에서 그룹 도형 예시](https://example.com/images/group-shapes-word.png "Word에서 그룹 도형 예시")

*이미지 대체 텍스트:* *Word에서 그룹 도형 예시* – 그룹화된 사각형과 그림을 보여주는 Word 문서.

---

## 일반적인 질문 및 엣지 케이스 처리

| Question | Answer |
|----------|--------|
| **이미지 크기를 다르게 지정해야 하면 어떻게 하나요?** | `picture.setWidth()`와 `picture.setHeight()`를 삽입 후 조정합니다. 사각형은 원래 크기를 유지하거나, 필요에 따라 크기를 맞출 수 있습니다. |
| **같은 그룹에 더 많은 도형을 추가할 수 있나요?** | 예. 추가 `Shape` 객체가 있으면 `group.appendChild(newShape)`를 호출합니다. |
| **전체 그룹을 회전하려면 어떻게 하나요?** | `group.setRotationAngle(double angleInRadians)`를 사용합니다. 회전은 모든 자식 도형에 적용됩니다. |
| **이미지 파일이 없으면 어떻게 하나요?** | `insertImage`는 `FileNotFoundException`을 발생시킵니다. 호출을 try‑catch 블록으로 감싸고 대체용 플레이스홀더 도형을 제공합니다. |
| **나중에 그룹 해제가 가능한가요?** | 자식들을 분리하려면 `group.removeAllChildren()`를 호출한 뒤, 각각을 문서에 개별적으로 삽입합니다. |

---

## 결론

이제 **Word에서 도형을 그룹화하는 방법**, **사각형 도형 추가**, **도형 크기 설정**, 그리고 Aspose.Words for Java를 사용한 **문서 저장**을 보여주는 완전하고 실행 가능한 예제가 준비되었습니다. 사각형과 그림을 그룹화하면 하나의 단위로 이동, 크기 조정 또는 회전할 수 있어 많은 문서 자동화 시나리오에서 요구되는 바로 그 기능을 제공합니다.

다음 단계로 다음을 탐색해 볼 수 있습니다:

* 같은 그룹에 텍스트 상자 추가 (`how to add rectangle` 스타일 텍스트).  
* 다른 채우기 패턴이나 그라디언트 적용 (`set shape size`와 스타일링 결합).  
* 차트, 표, SmartArt 등을 그룹화하는 동일한 기법 사용 (`how to group shapes`를 다른 객체 유형에 적용).

다른 도형 유형, 색상 및 레이아웃 옵션을 자유롭게 실험해 보세요. 즐거운 코딩 되세요!

## 다음에 배울 내용은?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 단계별 설명과 함께 완전한 동작 코드 예제가 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에서 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Word 문서 만들기 Java – 그림자 효과가 있는 사각형 도형 추가](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words for Java에서 DocumentBuilder를 사용해 양식 필드 생성 및 내용 추가 방법](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.Words for Java를 사용해 Word를 PDF로 변환하는 방법](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}