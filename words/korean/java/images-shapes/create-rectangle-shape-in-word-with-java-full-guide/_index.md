---
category: general
date: 2026-02-15
description: Java를 사용하여 Word 문서에 사각형 모양을 만들기. 모양 그림자 추가 방법, Word 문서 저장 방법, 그리고 Aspose.Words로
  사각형 모양을 추가하는 방법을 배웁니다.
draft: false
keywords:
- create rectangle shape
- save word document
- how to shadow shape
- add shape shadow
- add rectangle shape
language: ko
og_description: Java로 Word 파일에 사각형 모양을 만들기. 이 가이드는 모양 그림자 추가, Word 문서 저장, 사각형 모양 추가를
  단계별로 보여줍니다.
og_title: 사각형 모양 만들기 – Java Aspose.Words 튜토리얼
tags:
- Aspose.Words
- Java
- Document Automation
title: Java로 Word에서 사각형 도형 만들기 – 전체 가이드
url: /ko/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java로 Word에서 사각형 도형 만들기 – 전체 가이드

Word 파일에서 **create rectangle shape**을(를) 만들어야 했지만 어디서 시작해야 할지 몰랐던 적이 있나요? 당신만 그런 것이 아닙니다—많은 개발자들이 보고서나 청구서를 자동화할 때 이 문제에 부딪힙니다. 좋은 소식은? Aspose.Words for Java를 사용하면 사각형을 만들고, 멋진 그림자를 적용한 뒤, 몇 줄의 코드만으로 Word 문서를 저장할 수 있다는 것입니다.

이 튜토리얼에서는 필요한 모든 과정을 단계별로 안내합니다: 빈 문서 초기화부터 그림자 구성, 최종 파일 저장까지. 끝까지 읽으면 **how to shadow shape** 객체, **add shape shadow** 방법, 그리고 생성하는 모든 Word 문서에 **add rectangle shape**를 추가하는 방법을 알게 됩니다. 외부 문서는 필요 없으며 순수하게 실행 가능한 코드만 제공합니다.

## 사전 요구 사항

- Java 8 이상 (API는 Java 11+에서도 작동합니다).  
- Aspose.Words for Java 라이브러리 (버전 23.9 이상).  
- IntelliJ IDEA 또는 Eclipse와 같은 IDE—어느 것이든 상관없습니다.  
- Java 구문에 대한 기본적인 이해.

> **Pro tip:** Maven을 사용 중이라면 `pom.xml`에 Aspose.Words 의존성을 추가하고 IDE가 나머지를 처리하도록 하세요.

---

## Step 1: 새 문서 초기화 – How to **create rectangle shape**  

먼저, 깨끗한 캔버스가 필요합니다. Aspose.Words에서 그 캔버스는 `Document` 객체입니다.

```java
import com.aspose.words.*;

public class ShadowShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

`Document` 클래스는 전체 .docx 파일을 나타냅니다. 나중에 **add rectangle shape**와 그림자를 추가할 노트북이라고 생각하면 됩니다.

## Step 2: 사각형 만들기 – **Add rectangle shape**  

이제 실제로 사각형을 구성합니다. 크기, 레이아웃 및 채우기 색상을 설정합니다.

```java
        // Step 2: Create a rectangle shape and set its size and layout
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);
        rectangleShape.setFillColor(java.awt.Color.LIGHT_GRAY);
```

`INLINE` 래핑은 왜 사용할까요? 이는 도형을 문단처럼 동작하게 하여 간단한 보고서에 적합하기 때문입니다. 나중에 텍스트가 도형 주위에 흐르도록 하려면 `TOPBOTTOM`으로 변경할 수 있습니다.

## Step 3: 그림자 적용 – **How to shadow shape**  

평면 사각형은 다소 밋밋해 보입니다. 그림자를 추가하면 깊이가 생기고 문서가 더욱 다듬어진 느낌을 줍니다. 여기서 우리는 실제로 “**how to shadow shape**”에 대한 답을 제공합니다.

```java
        // Step 3: Configure the shape's shadow appearance
        rectangleShape.getShadowFormat().setVisible(true);
        rectangleShape.getShadowFormat().setColor(java.awt.Color.DARK_GRAY);
        rectangleShape.getShadowFormat().setBlurRadius(5.0);
        rectangleShape.getShadowFormat().setOffsetX(4.0);
        rectangleShape.getShadowFormat().setOffsetY(4.0);
        rectangleShape.getShadowFormat().setTransparency(0.3);
```

각 속성은 특정한 역할을 합니다:

- `setVisible(true)`는 그림자를 켭니다.  
- `setColor`는 은은한 효과를 위해 짙은 회색을 선택합니다.  
- `setBlurRadius`는 가장자리의 부드러움을 제어합니다.  
- `setOffsetX/Y`는 그림자를 오른쪽과 아래쪽으로 이동시켜 광원을 흉내냅니다.  
- `setTransparency`는 약간 투명하게 만들어 도형이 주인공으로 남게 합니다.

> **Note:** 색상 그림자가 필요하면 `setColor`에 다른 `java.awt.Color`를 전달하면 됩니다.

## Step 4: 도형을 문서에 삽입하기  

사각형과 그림자가 준비되면 문서의 첫 번째 섹션에 삽입합니다.

```java
        // Step 4: Add the shape to the first section of the document
        document.getFirstSection().getBody().appendChild(rectangleShape);
```

본문에 추가하면 새로운 문단이 들어가는 위치에 도형이 배치됩니다. 사각형을 특정 위치에 두고 싶다면 `insertBefore`를 사용하거나 `Paragraph` 컬렉션을 조작할 수 있습니다.

## Step 5: **Save Word document** – 작업 저장하기  

마지막 단계는 파일을 디스크에 쓰는 것입니다. 바로 이 순간에 **save Word document**를 수행합니다.

```java
        // Step 5: Save the document with the shadowed shape
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

`YOUR_DIRECTORY`를 머신의 절대 경로나 상대 경로로 교체하세요. 프로그램을 실행한 후 Microsoft Word에서 `ShadowShape.docx`를 열면 연한 회색 사각형에 부드러운 어두운 그림자가 표시됩니다.

![Aspose.Words를 사용해 만든 그림자가 있는 사각형 도형을 보여주는 다이어그램](https://example.com/rectangle-shadow.png "그림자가 있는 사각형 도형 만들기")

---

## 일반적인 질문 및 예외 상황  

### 여러 개의 사각형이 필요하면 어떻게 하나요?

**Step 2**와 **Step 3**을 루프에서 반복하고 각 반복마다 `setWidth`, `setHeight`, `setFillColor`를 조정하면 됩니다. 각 도형에 고유한 변수명을 부여하거나 리스트에 저장하는 것을 기억하세요.

### DOCX 대신 PDF로 내보낼 수 있나요?

물론 가능합니다. 도형을 추가한 후 `document.save("output.pdf")`를 호출하면 됩니다. Aspose.Words가 변환을 처리하며 그림자를 유지합니다.

### 오래된 Word 버전은 어떻게 하나요?

`document.save("file.doc", SaveFormat.DOC)` 오버로드를 사용하세요. API가 자동으로 기능을 낮추지만, 일부 그림자 스타일은 레거시 형식에서 약간 다르게 보일 수 있습니다.

### 그림자 방향을 어떻게 바꾸나요?

`setOffsetX`와 `setOffsetY`를 조작합니다. X가 양수이면 그림자가 오른쪽으로 이동하고, 음수이면 왼쪽으로 이동합니다. Y가 양수이면 아래로, 음수이면 위로 이동합니다. 이러한 값을 조정해 원하는 각도에서 오는 광원을 시뮬레이션하세요.

## 도형 작업 팁  

- **Group shapes**: 사각형 옆에 레이블이 필요하면 `GroupShape`를 생성하고 사각형과 `TextBox`를 모두 추가합니다.  
- **Z‑order matters**: `shape.moveToFront()` 또는 `shape.moveToBack()`을 사용해 어떤 도형이 위에 표시될지 제어합니다.  
- **Performance**: 수백 개의 도형을 추가하면 느릴 수 있습니다. 하나의 섹션에 배치한 뒤 마지막에 `document.updatePageLayout()`을 한 번 호출하세요.

## 요약  

Java를 사용해 Word 문서에 **create rectangle shape**하는 방법, **add shape shadow**하는 방법, 그리고 결과물을 **save Word document**하는 방법을 다루었습니다. 완전한 실행 가능한 코드는 위의 스니펫에 포함되어 있으며, 이제 각 속성 뒤에 숨은 “왜”를 이해했으므로 색상, 블러, 오프셋 등을 원하는 디자인에 맞게 조정할 수 있습니다.

다음 도전에 준비되셨나요? 사각형을 차트와 결합하거나 파일을 PDF로 내보내 그림자가 어떻게 렌더링되는지 확인해 보세요. 또한 표 안에 **add rectangle shape**를 활용해 멋진 보고서 레이아웃을 탐색해 볼 수 있습니다.

코딩을 즐기세요, 그리고 여러분의 문서가 코드만큼이나 깔끔하게 보이길 바랍니다!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}