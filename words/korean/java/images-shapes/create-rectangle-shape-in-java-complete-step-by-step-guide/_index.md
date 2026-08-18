---
category: general
date: 2026-07-03
description: Java에서 사각형 모양을 만들고, 모양에 그림자를 추가하는 방법, 그림자 효과 적용, 모양 투명도 설정, 그리고 빈 문서를
  빠르게 만드는 방법을 배워보세요.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- set shape transparency
- create blank document
language: ko
og_description: Java에서 그림자와 투명도가 적용된 사각형을 만들고 빈 문서를 사용하세요. 이 가이드를 따라 도형 처리 기술을 마스터하세요.
og_title: Java에서 사각형 모양 만들기 – 전체 프로그래밍 튜토리얼
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  headline: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  name: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  steps:
  - name: What if I want a different shadow color?
    text: 'Simply change the `setColor` call:'
  - name: Can I apply the same shadow to multiple shapes?
    text: 'Yes. Create one `ShadowEffect` instance, configure it, then reuse it:'
  - name: How do I change the shadow blur dynamically?
    text: Expose a UI slider that maps to `setBlurRadius`. Values between `2` and
      `12` are typical; larger numbers produce a “glow” rather than a crisp shadow.
  - name: What if I need the shape to float rather than be inline?
    text: 'Swap the wrap type:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Automation
title: Java에서 사각형 모양 만들기 – 완전 단계별 가이드
url: /ko/java/images-shapes/create-rectangle-shape-in-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java에서 사각형 도형 만들기 – 완전 단계별 가이드

Word 문서에 **사각형 도형**을 Java로 만들고 싶으신가요? 여러분만 그런 것이 아닙니다—개발자들은 종종 기하학적 그래픽을 빠르게 추가하고, 레이아웃을 더 세련되게 보이게 하기 위해 은은한 그림자를 넣어야 합니다. 이 튜토리얼에서는 **빈 문서 만들기**부터 **도형에 그림자 추가**, **그림자 효과 적용**, 그리고 **도형 투명도 설정**까지 전체 과정을 단계별로 안내합니다.

아래 코드 스니펫은 바로 복사‑붙여넣기 할 수 있는 완전한 예제입니다. 별도의 문서는 필요 없으며, 단계와 “왜”를 이해하면 몇 초 만에 그림자가 있는 사각형을 생성할 수 있습니다.

## 배울 내용

- Aspose.Words for Java를 사용해 프로그래밍 방식으로 **사각형 도형 만들기**.
- **도형에 그림자 추가**와 시각적 속성 구성을 위한 정확한 메서드 호출.
- **그림자 효과 적용** 및 오프셋, 블러 반경, 색상 같은 파라미터 조정 방법.
- **도형 투명도 설정**을 통해 보다 부드러운 외관 만들기.
- **빈 문서 만들기**, 도형 삽입, 결과 저장까지 전체 흐름.

> **Pro tip:** 모든 작업은 단일 `Document` 인스턴스에서 수행되므로 중간 파일 입출력에 신경 쓸 필요 없이 메서드를 체인처럼 연결할 수 있습니다.

## 사전 요구 사항

시작하기 전에 다음이 준비되어 있어야 합니다:

- Java 17(또는 최신 JDK) 설치
- 프로젝트에 Aspose.Words for Java 라이브러리 추가 (Maven 좌표: `com.aspose:aspose-words:23.12`)
- Java IDE 또는 간단한 텍스트 편집기—특별한 도구는 필요 없습니다, 컴파일하고 실행할 수만 하면 됩니다.

필요한 것이 없으면 Oracle에서 JDK를 다운로드하고 Maven 또는 Gradle을 통해 Aspose 의존성을 가져오세요. 준비가 끝났다면 바로 시작할 수 있습니다.

## 1단계: **빈 문서 만들기** – 모든 작업의 캔버스

가장 먼저 해야 할 일은 빈 `Document` 객체를 생성하는 것입니다. 이는 마치 새 종이와 같으며, 이 없이는 사각형을 넣을 곳이 없습니다.

```java
// Step 1: Create a new blank document
Document document = new Document();
```

왜 빈 문서부터 시작해야 할까요? 모든 도형은 `Section` 안에 존재하기 때문입니다. 새로 만든 `Document`는 이미 기본 섹션과 본문을 포함하고 있어 노드를 바로 삽입할 수 있습니다. 이 단계를 건너뛰면 나중에 섹션을 직접 만들어야 하므로 복잡도가 증가합니다.

## 2단계: **사각형 도형 만들기** 및 크기 정의

캔버스를 확보했으니 이제 **사각형 도형 만들기**를 진행합니다. `Shape` 클래스는 문서 참조와 `ShapeType`을 인수로 받습니다. 여기서는 `RECTANGLE`을 선택하고, 너비·높이를 포인트 단위(1 pt ≈ 1/72 인치)로 설정합니다.

```java
// Step 2: Insert a rectangle shape and define its size and layout
Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
rectangleShape.setWidth(200);   // 200 pt ≈ 2.78 inches
rectangleShape.setHeight(100);  // 100 pt ≈ 1.39 inches
rectangleShape.setWrapType(WrapType.INLINE);
```

왜 `WrapType.INLINE`을 설정할까요? 인라인 래핑은 도형을 문단 내 문자처럼 동작하게 하여 주변 텍스트와 함께 이동하도록 합니다. 떠 있는 형태가 필요하면 `WrapType.SQUARE` 또는 `WrapType.TOP_BOTTOM`으로 바꾸면 됩니다.

## 3단계: **그림자 효과 적용** – 사각형에 깊이 부여

평면 사각형은… 글쎄요, 평면입니다. 그림자를 추가하면 입체감이 살아납니다. `ShadowEffect` 인스턴스를 만든 뒤 시각적 속성을 조정해 **그림자 효과 적용**을 수행합니다.

```java
// Step 3: Create a shadow effect and configure its visual properties
ShadowEffect shadowEffect = new ShadowEffect();
shadowEffect.setColor(Color.getGray(0.5));   // medium gray
shadowEffect.setOffsetX(5);                  // horizontal offset (points)
shadowEffect.setOffsetY(5);                  // vertical offset (points)
shadowEffect.setBlurRadius(8);               // softness of the shadow
shadowEffect.setTransparency(0.3);           // 30 % transparent
```

조금 살펴보면:

- **Color** – `Color.getGray(0.5)`는 50 % 회색을 반환하며, 대부분 배경에 중립적입니다.
- **OffsetX/Y** – 양수 값은 그림자를 오른쪽·아래로 이동시키고, 음수 값은 왼쪽·위로 이동시킵니다.
- **BlurRadius** – 값이 클수록 부드럽고 퍼진 그림자가 됩니다.
- **Transparency** – `0`은 불투명, `1`은 완전 투명. 여기서는 `0.3`을 선택해 은은한 효과를 줍니다.

## 4단계: **도형에 그림자 추가** – 효과 연결

효과를 만든 것만으로는 부족합니다. `ShadowEffect` 객체를 사각형에 할당해 **도형에 그림자 추가**를 해야 합니다.

```java
// Step 4: Apply the shadow effect to the rectangle shape
rectangleShape.setShadowEffect(shadowEffect);
```

이 호출은 Word가 그림자를 렌더링하는 데 사용하는 OpenXML 마크업(`<w:shdw>`)을 업데이트합니다. 저장된 `.docx` 파일을 열어 보면 설정한 파라미터가 `<w:effect>` 요소에 반영된 것을 확인할 수 있습니다.

## 5단계: **도형 투명도 설정** – 선택 사항이지만 유용

때때로 사각형 자체를 반투명하게 만들어 배경 텍스트가 비쳐 보이게 하고 싶을 때가 있습니다. `Shape` 클래스의 `setFillColor`와 `setFillTransparency`를 사용합니다. 아래 예제는 사각형을 40 % 투명하게 만듭니다.

```java
// Optional: make the rectangle partially transparent
rectangleShape.setFillColor(Color.getWhite());
rectangleShape.setFillTransparency(0.4); // 40 % transparent
```

왜 이렇게 할까요? 워터마크나 강조 표시용 호출 박스처럼, 아래 내용이 읽히면서도 도형이 눈에 띄게 하고 싶을 때 유용합니다. 디자인에 맞게 투명도 값을 조정하세요.

## 6단계: 도형을 문서에 삽입

이제 사각형을 만들고, 그림자를 추가하고(선택적으로) 투명도를 설정했으니 **도형을 문서의 첫 번째 섹션에 추가**합니다.

```java
// Step 5: Add the shape to the first section of the document
document.getFirstSection().getBody().appendChild(rectangleShape);
```

도형을 본문에 추가하면 첫 번째 문단 끝에 배치됩니다. 특정 위치에 삽입하려면 대상 `Paragraph`를 가져와 `insertBefore` 또는 `insertAfter`를 사용하면 됩니다.

## 7단계: 문서 저장 – 결과 확인

모든 작업은 한 번의 `save` 호출로 마무리됩니다. 환경에 맞는 경로를 지정하세요.

```java
// Step 6: Save the document with the shadowed shape
document.save("YOUR_DIRECTORY/ShadowShape.docx");
```

생성된 `ShadowShape.docx`를 Microsoft Word 또는 LibreOffice에서 열면, 부드러운 회색 그림자가 있는 선명한 사각형이 보이며, 선택 단계에서 투명도를 적용했다면 약간 투명해진 모습을 확인할 수 있습니다. 화면에 나타나는 모습은 코드에서 정의한 파라미터와 일치합니다.

---

![Word 문서에서 그림자가 있는 사각형 도형 만들기](https://example.com/images/rectangle-shadow.png "그림자가 있는 사각형 도형 만들기")

*이미지 설명:* **create rectangle shape with shadow** – 최종 출력의 시각적 표현.

## 자주 묻는 질문 및 예외 상황

### 다른 그림자 색상을 원한다면?

`setColor` 호출만 바꾸면 됩니다:

```java
shadowEffect.setColor(Color.getRed()); // bright red shadow
```

과도하게 선명한 그림자는 비전문적으로 보일 수 있으니, 은은한 톤을 권장합니다.

### 여러 도형에 같은 그림자를 적용할 수 있나요?

가능합니다. `ShadowEffect` 인스턴스를 하나 만든 뒤 재사용하면 됩니다:

```java
Shape circle = new Shape(document, ShapeType.OVAL);
circle.setShadowEffect(shadowEffect); // same effect as rectangle
```

다른 도형에 이미 연결한 뒤 `ShadowEffect`를 수정하면 모든 도형에 동시에 적용되니, 의도하지 않은 경우에는 수정하지 않도록 주의하세요.

### 그림자 블러를 동적으로 바꾸려면?

UI 슬라이더를 만들어 `setBlurRadius`에 연결합니다. 일반적으로 `2`~`12` 사이 값이 적당하며, 값이 클수록 그림자가 “글로우”처럼 보입니다.

### 도형을 인라인이 아니라 떠 있게 하려면?

래핑 타입을 교체합니다:

```java
rectangleShape.setWrapType(WrapType.SQUARE);
rectangleShape.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangleShape.setHorizontalAlignment(HorizontalAlignment.CENTER);
```

떠 있는 도형은 레이아웃 자유도가 높지만, 위치 지정 로직을 추가로 구현해야 합니다.

## 전체 작업 예제

아래는 앞서 설명한 모든 단계를 포함한 복사‑붙여넣기 가능한 완전한 프로그램입니다. 일반 Java 애플리케이션으로 실행하면 됩니다.

```java
import com.aspose.words.*;

public class ShadowRectangleDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank document
        Document document = new Document();

        // 2. Build the rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);

        // 3. Configure shadow effect
        ShadowEffect shadowEffect = new ShadowEffect();
        shadowEffect.setColor(Color.getGray(0.5));
        shadowEffect.setOffsetX(5);
        shadowEffect.setOffsetY(5);
        shadowEffect.setBlurRadius(8);
        shadowEffect.setTransparency(0.3);

        // 4. Apply shadow to the rectangle
        rectangleShape.setShadowEffect(shadowEffect);

        // 5. (Optional) Make rectangle semi‑transparent
        rectangleShape.setFillColor(Color.getWhite());
        rectangleShape.setFillTransparency(0.4);

        // 6. Insert shape into the document
        document.getFirstSection().getBody().appendChild(rectangleShape);

        // 7. Save the file
        document.save("ShadowShape.docx");
    }
}
```

**예상 결과:** `ShadowShape.docx`를 열면 첫 번째 문단 중앙에 200 × 100 pt 크기의 흰색 사각형이 나타나며, 5 pt 오프셋, 반경 8의 중간 회색 그림자와 30 % 투명도가 적용됩니다. 사각형 자체는 40 % 투명해 배경 텍스트가 살짝 비칩니다.

## 마무리

우리는 **빈 문서 만들기**를 기반으로 **사각형 도형 만들기**, **도형에 그림자 추가**, **그림자 효과 적용**, 그리고 **도형 투명도 설정**까지 모두 수행했습니다. 접근 방식은 간단하고 Aspose.Words의 유창한 API를 활용하며, 원형, 별, 사용자 정의 다각형 등으로 확장할 수 있습니다.

다음에 시도해 볼 것은 무엇인가요? `ShapeType.RECTANGLE`을 `ShapeType.OVAL`로 바꿔 그림자가 있는 원을 만들거나, 그라디언트 채우기로 색상을 실험해 보세요.


## 다음에 배울 내용은?


다음 튜토리얼들은 이 가이드에서 배운 기술을 기반으로 하여 추가적인 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용할 수 있도록 완전한 코드 예제와 단계별 설명을 제공합니다.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}