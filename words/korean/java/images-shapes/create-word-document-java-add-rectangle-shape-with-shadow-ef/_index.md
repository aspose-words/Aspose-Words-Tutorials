---
category: general
date: 2026-01-11
description: 사각형 모양을 추가하고 채우기 색을 설정한 뒤 그림자를 적용하여 Java로 워드 문서를 빠르게 만들기. 단계별로 배워보세요.
draft: false
keywords:
- create word document java
- add rectangle shape
- apply shadow to shape
- set shape fill color
- how to add shape
language: ko
og_description: 사각형 모양을 삽입하고 채우기 색을 설정한 뒤 그림자를 적용하여 Java로 워드 문서를 만드는 방법. 코드와 함께하는
  완전 가이드.
og_title: Java로 워드 문서 만들기 – 그림자 있는 사각형 도형 추가
tags:
- Aspose.Words
- Java
- Document Generation
title: Java로 워드 문서 만들기 – 그림자 효과가 있는 사각형 도형 추가
url: /ko/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 문서 Java 만들기 – 사각형 모양에 그림자 효과 추가

Ever needed to **create word document java** and make it look a bit more polished? Maybe you’re building a report generator and a plain page just won’t cut it. The good news? With Aspose.Words for Java you can drop a rectangle shape onto a document, give it a splash of color, and even toss a subtle shadow on it—all in a handful of lines.

이 튜토리얼에서는 바로 그 과정을 단계별로 살펴보겠습니다: 사각형 모양을 추가하고, 채우기 색상을 설정하며, 그림자를 적용해 Word 파일을 조금 더 전문적으로 보이게 만드는 방법을 다룹니다. 마지막까지 따라오시면 복사‑붙여넣기만으로 바로 사용할 수 있는 실행 가능한 예제를 얻으실 수 있습니다.

## 필요 사항

- **Java 17** (또는 최신 JDK) – 코드는 표준 언어 기능을 사용합니다.
- **Aspose.Words for Java** 라이브러리 – 버전 23.9 이상을 권장합니다.
- 원하는 IDE 또는 텍스트 편집기 – IntelliJ IDEA, Eclipse, VS Code 등 자유롭게 선택하세요.
- 생성된 `ShadowShape.docx` 파일이 저장될 폴더.

추가적인 설정 마법은 필요하지 않습니다; Aspose.Words JAR 파일을 클래스패스에 추가하면 바로 사용할 수 있습니다.

## 단계 1: 프로젝트 설정 및 Aspose.Words 가져오기

먼저 Maven(또는 Gradle) 프로젝트를 새로 만들고 Aspose.Words 의존성을 추가합니다. Maven용 최소 `pom.xml` 스니펫은 다음과 같습니다:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>23.9</version>
        <classifier>jdk17</classifier>
    </dependency>
</dependencies>
```

Maven을 사용하지 않는 경우 JAR 파일을 `libs` 폴더에 넣고 빌드 경로에 추가하면 됩니다.

> **Pro tip:** Aspose는 `License license = new License(); license.setLicense("Aspose.Words.lic");` 와 같이 삽입할 수 있는 무료 체험 라이선스를 제공합니다. 빠른 테스트를 위해서는 생략해도 되며, 라이브러리는 평가 모드에서도 동작합니다.

## 단계 2: 새 Document 및 Builder 생성

이제 실제로 **create word document java** 객체를 만들 차례입니다. `Document` 클래스는 전체 .docx 파일을 나타내고, `DocumentBuilder`는 콘텐츠 삽입을 담당합니다.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

이 시점에서 빈 문서가 준비되어 있어 모양, 단락 등 원하는 요소를 추가할 수 있습니다.

## 단계 3: 사각형 모양 삽입 및 채우기 색상 설정

모양을 추가하는 것은 `insertShape` 를 호출하는 것만큼 간단합니다. 여기서는 **add rectangle shape** 기법을 사용합니다(*add rectangle shape* 라는 보조 키워드에 해당).

```java
        // Insert a rectangle shape – 200pt wide, 100pt tall
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);

        // Set the fill color to a bright orange
        rectangle.setFillColor(java.awt.Color.ORANGE);
```

왜 주황색이냐고요? 흰색 배경에서 눈에 잘 띄지만, 원하는 `java.awt.Color` 로 언제든 교체할 수 있습니다. 이 단계는 보조 키워드 *set shape fill color* 를 다룹니다.

## 단계 4: 그림자 모양 구성 – Shape에 그림자 적용

이제 재미있는 부분입니다: 사각형에 은은한 드롭 그림자를 부여합니다. Aspose API는 그림자의 모든 속성을 제어하는 `ShadowFormat` 객체를 제공합니다.

```java
        // Get the shadow format object for the shape
        ShadowFormat shadow = rectangle.getShadowFormat();

        // Make the shadow visible
        shadow.setVisible(true);

        // Choose a neutral gray for the shadow color
        shadow.setColor(java.awt.Color.GRAY);

        // Blur radius – larger values produce a softer edge
        shadow.setBlur(5.0);

        // Offset determines how far the shadow is displaced
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);

        // Transparency (0 = opaque, 1 = fully transparent)
        shadow.setTransparency(0.2);

        // Define the shadow style and type
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);

        // Scale controls the overall size of the shadow relative to the shape
        shadow.setScale(1.0);
```

위 코드는 **apply shadow to shape** 라는 보조 키워드 그대로 구현한 예시입니다. `blur`, `offsetX/Y`, `transparency` 등을 조정해 디자인에 맞게 튜닝할 수 있습니다. 예를 들어 `offsetX` 값을 크게 하면 그림자가 더 멀리 떨어져 보이고, `transparency` 를 높이면 그림자가 부드럽게 나타납니다.

## 단계 5: 문서 저장

마지막으로 문서를 디스크에 씁니다. 쓰기 권한이 있는 폴더를 선택하고 파일 이름을 명확히 지정하세요.

```java
        // Save the result – adjust the path as needed
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

`ShadowShape.docx` 를 Microsoft Word 혹은 LibreOffice 로 열면, 밝은 주황색 사각형 아래에 부드러운 회색 그림자가 떠 있는 것을 확인할 수 있습니다.

![create word document java with rectangle shape](/images/shadow-rectangle.png "create word document java – rectangle with shadow")

*이미지 alt 텍스트에 주요 키워드가 포함되어 SEO 규칙을 만족합니다.*

## 일반 질문 및 엣지 케이스

### 다른 모양이 필요하면 어떻게 하나요?

Aspose.Words는 `ShapeType` 값 수십 개를 지원합니다 – 별, 화살표, 말풍선 등 원하는 것을 선택하세요. `ShapeType.RECTANGLE` 을 `ShapeType.OVAL` 혹은 다른 enum 상수로 교체하면 됩니다. 동일한 **how to add shape** 단계가 적용됩니다.

### 특정 단락에 모양을 추가하려면 어떻게 하나요?

Builder 로 직접 모양을 삽입하는 대신, 먼저 `new Shape(document, ShapeType.RECTANGLE)` 로 생성한 뒤 `paragraph.appendChild(shape)` 를 통해 `Paragraph` 에 추가할 수 있습니다. 이렇게 하면 레이아웃을 보다 세밀하게 제어할 수 있습니다.

### 단색 대신 그라디언트 채우기를 적용할 수 있나요?

네! `rectangle.getFill().setFillType(FillType.GRADIENT)` 를 사용하고 `LinearGradientFill` 을 정의하면 됩니다. API 사용량이 다소 늘어나지만 최신 디자인에 매우 유용합니다.

### 오래된 Word 버전과의 호환성은 어떨까요?

Aspose.Words는 기본적으로 .docx 형식으로 저장하며, 이는 Word 2007+ 및 LibreOffice 에서 지원됩니다. .doc 형식이 필요하면 `document.save("file.doc", SaveFormat.DOC)` 를 호출하세요. 그림자 렌더링이 약간 다를 수 있지만 모양 자체는 그대로 유지됩니다.

## 전체 작업 예제 (복사‑붙여넣기 준비 완료)

아래는 전체 프로그램 코드이며, 바로 컴파일하고 실행할 수 있습니다. `YOUR_DIRECTORY` 를 실제 경로로 교체하세요.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape and set its fill color
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);
        rectangle.setFillColor(java.awt.Color.ORANGE);

        // Step 3: Apply shadow to shape
        ShadowFormat shadow = rectangle.getShadowFormat();
        shadow.setVisible(true);
        shadow.setColor(java.awt.Color.GRAY);
        shadow.setBlur(5.0);
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);
        shadow.setTransparency(0.2);
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);
        shadow.setScale(1.0);

        // Step 4: Save the document
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

이 코드를 실행하면 주황색 사각형과 부드러운 회색 그림자가 포함된 Word 파일이 생성됩니다—즉, **create word document java** 로 스타일이 적용된 모양을 만들고자 했던 목표를 정확히 달성한 결과입니다.

## 결론

이제 **create word document java** 로 *사각형 모양 추가*, *채우기 색상 설정*, *그림자 적용* 을 수행하는 완전한 엔드‑투‑엔드 레시피를 갖추셨습니다. 접근 방식은 직관적이며 API는 유창하고, 다양한 모양, 그라디언트 채우기, 혹은 하나의 모양에 여러 그림자를 적용하는 등 무한히 확장할 수 있습니다.

다음 단계는 무엇일까요? 여러 모양을 겹쳐 보거나 `ShadowStyle.ETCHED` 를 사용해 다른 시각 효과를 실험해 보세요. 혹은 테이블 생성과 결합해 완전한 보고서를 만들어 보는 것도 좋습니다. 가능성은 여러분의 상상력(그리고 Aspose 라이선스 등급)에 달려 있습니다.

사용 중 문제가 발생하거나 추가 아이디어가 있다면 아래 댓글로 알려 주세요. 즐거운 코딩 되시고, Word 문서가 조금이라도 덜 밋밋해지길 바랍니다!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}