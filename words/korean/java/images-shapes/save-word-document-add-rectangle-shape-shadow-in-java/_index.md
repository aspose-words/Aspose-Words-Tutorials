---
category: general
date: 2026-06-20
description: Java에서 Aspose.Words를 사용해 사각형 모양을 추가하고 그림자를 적용하면서 Word 문서를 저장합니다. 단계별로
  모양 삽입 방법을 배워보세요.
draft: false
keywords:
- save word document
- add rectangle shape
- apply shadow to shape
- how to add shadow
- how to insert shape
language: ko
og_description: Aspose.Words Java를 사용하여 Word 문서를 저장합니다. 이 가이드는 사각형 도형을 추가하고 그림자를 적용한
  뒤, 이를 단락에 삽입하는 방법을 보여줍니다.
og_title: 워드 문서 저장 – Java에서 사각형 도형 및 그림자 추가
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Save Word document using Aspose.Words in Java while adding a rectangle
    shape and applying a shadow. Learn how to insert shape step‑by‑step.
  headline: Save Word Document – Add Rectangle Shape & Shadow in Java
  type: TechArticle
- description: Save Word document using Aspose.Words in Java while adding a rectangle
    shape and applying a shadow. Learn how to insert shape step‑by‑step.
  name: Save Word Document – Add Rectangle Shape & Shadow in Java
  steps:
  - name: '**Compile** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`'
    text: '**Compile** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`'
  - name: '**Execute** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`'
    text: '**Execute** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`'
  - name: '**Open** `shadow.docx` in Microsoft Word or LibreOffice. You should see
      the rectangle with a soft black shadow anchored at the start of the first paragraph.'
    text: '**Open** `shadow.docx` in Microsoft Word or LibreOffice. You should see
      the rectangle with a soft black shadow anchored at the start of the first paragraph.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the target `Section` or `PageSetup` and insert the shape
      into a paragraph located on that page.
    question: Can I add the shape to a specific page?
  - answer: Absolutely. Aspose.Words abstracts the format, so the same code **saves
      a Word document** whether it’s `.doc` or `.docx`.
    question: Does this work with .doc files?
  - answer: 'Replace `ShapeType.RECTANGLE` with `ShapeType.ELLIPSE`. All shadow properties
      remain the same. --- ## Conclusion You now know how to **save a Word document**
      while **adding a rectangle shape**, **applying a shadow**, and **inserting the
      shape** into the first paragraph—all with a handful of clean Ja'
    question: What if I need a different shape, like an ellipse?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word Automation
title: Word 문서 저장 – Java에서 사각형 도형 및 그림자 추가
url: /ko/java/images-shapes/save-word-document-add-rectangle-shape-shadow-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 문서 저장 – 사각형 도형 및 그림자 추가 (Java)

레이아웃을 커스터마이징한 후 **Word 문서를 저장**하는 방법이 궁금하셨나요? 혼자만 그런 것이 아닙니다—대부분의 개발자는 프로그래밍으로 DOCX 파일을 풍부하게 만들 때 이 문제에 부딪힙니다. 좋은 소식은 Aspose.Words for Java를 사용하면 **Word 문서를 저장**하고, 원하는 위치에 사각형 도형을 삽입하며, 그 도형에 은은한 그림자를 줄 수 있다는 것입니다.

이 튜토리얼에서는 전체 과정을 단계별로 살펴봅니다: 기존 파일 로드, **사각형 도형 추가**, **그림자 설정**, 도형을 첫 번째 단락에 삽입, 그리고 최종적으로 **Word 문서 저장**. 끝까지 따라오시면 수동으로 조정할 필요 없이 깔끔한 `shadow.docx` 파일을 생성하는 실행 가능한 Java 프로그램을 얻게 됩니다.

> **필요한 준비물**  
> * Java 17 (또는 최신 JDK)  
> * Aspose.Words for Java 라이브러리 (Maven/Gradle 또는 JAR)  
> * 알려진 폴더에 있는 입력 DOCX 파일 (`input.docx`)  

위 준비물이 모두 갖춰졌다면, 바로 시작해 보겠습니다.

---

## Word 문서 저장 – 전체 Java 예제

아래는 바로 실행 가능한 전체 소스 코드입니다. IDE에 복사하고 경로를 조정한 뒤 **Run**을 눌러 주세요.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class ShadowShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the existing document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Create a rectangle shape (the core of add rectangle shape step)
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);
        rectangle.setHeight(50.0);

        // 3️⃣ Apply shadow to shape – how to add shadow in Aspose.Words
        rectangle.getShadow().setVisible(true);
        rectangle.getShadow().setColor(java.awt.Color.BLACK);
        rectangle.getShadow().setBlurRadius(5.0);
        rectangle.getShadow().setOffsetX(4.0);
        rectangle.getShadow().setOffsetY(4.0);
        rectangle.getShadow().setTransparency(0.3);

        // 4️⃣ Insert shape into the first paragraph – how to insert shape
        Paragraph firstPara = doc.getFirstSection().getBody().getParagraphs().get(0);
        firstPara.appendChild(rectangle);

        // 5️⃣ Save the modified document – the final save word document step
        doc.save("YOUR_DIRECTORY/shadow.docx");
        System.out.println("Document saved successfully as shadow.docx");
    }
}
```

**예상 결과:** 프로그램 실행 후 `shadow.docx`를 열면 원본 내용에 100 × 50 pt 크기의 검은색 사각형이 부드러운 그림자와 함께 첫 번째 단락 시작 부분에 삽입된 것을 확인할 수 있습니다.

---

## Word 문서에 사각형 도형 추가

사각형 도형을 왜 사용할까요? 시각적 앵커 역할을 하며, 콜아웃, 자리 표시자 또는 간단한 그래픽에 적합합니다. Aspose.Words에서 `Shape` 클래스는 모든 그리기 객체를 추상화하고, `ShapeType.RECTANGLE`은 추가 설정 없이 깔끔한 박스를 제공합니다.

**사각형 도형 추가 시 핵심 포인트**

- **단위는 포인트** (1 pt = 1/72 in). 레이아웃에 맞게 `setWidth`/`setHeight`를 조정하세요.  
- 도형은 문서의 노드 트리 안에 존재하므로 `Paragraph`나 `Run`이 허용되는 어디에든 삽입할 수 있습니다.  
- 그림자를 적용하기 전에 도형의 스타일(채우기, 선 색 등)을 지정할 수 있습니다.

> **프로 팁:** 투명 채우기가 필요하면 `rectangle.getFill().setTransparent(true);`를 호출하세요.

---

## 도형에 그림자 적용

그림자는 깊이감을 줍니다. `Shape`에 연결된 `Shadow` 객체는 Word UI 옵션에 직접 매핑되는 속성을 제공합니다.

| Property | What it does | Typical value |
|----------|--------------|---------------|
| `setVisible(true)` | 그림자를 켭니다 | `true` |
| `setColor(Color.BLACK)` | 그림자 색상 | `Color.BLACK` |
| `setBlurRadius(5.0)` | 가장자리 부드러움 | `5.0` |
| `setOffsetX(4.0)` / `setOffsetY(4.0)` | 가로/세로 이동량 | 각각 `4.0` |
| `setTransparency(0.3)` | 불투명도 (0 = 불투명, 1 = 투명) | `0.3` |

**그림자 적용 방법**은 바로 이 여섯 가지 속성을 조정하는 것입니다. 오프셋을 크게 하면 “떠 있는” 느낌을, 블러 반경을 높이면 더 퍼진 그림자를 얻을 수 있습니다.

> **흔한 실수:** `setVisible(true)`를 빼먹으면 다른 속성을 설정해도 그림자가 보이지 않습니다.

---

## 도형을 단락에 삽입하는 방법

도형 삽입은 마법이 아니라 노드 조작입니다. `appendChild` 메서드는 도형을 해당 단락의 마지막 자식 노드에 배치합니다. 텍스트 앞에 도형이 필요하면 `insertBefore`를 사용하면 됩니다.

```java
Paragraph para = doc.getFirstSection().getBody().getParagraphs().get(0);
para.insertBefore(rectangle, para.getFirstChild());
```

이 작은 변경만으로 **도형을 삽입하는 방법**을 정확히 제어할 수 있습니다—기존 런 앞, 헤딩 뒤, 혹은 테이블 셀 내부(먼저 해당 `Cell` 노드를 가져와야 함) 등 어디든 말이죠.

---

## 코드 실행 및 결과 확인

1. **컴파일** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`  
2. **실행** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`  
3. **열기** `shadow.docx`를 Microsoft Word 또는 LibreOffice에서 확인합니다. 첫 번째 단락 시작 부분에 부드러운 검은 그림자가 적용된 사각형이 보일 것입니다.

도형이 나타나지 않을 경우 다음을 점검하세요:

- 입력 파일 경로가 정확한지.  
- 최신 버전의 Aspose.Words를 사용하고 있는지 (API가 20.12 이전에 약간 변경됨).  
- 문서에 최소 하나 이상의 단락이 존재하는지 (`getParagraphs().get(0)`이 IndexOutOfBoundsException을 발생시키지 않도록).

---

## 자주 묻는 질문 (FAQ)

**Q: 특정 페이지에 도형을 추가할 수 있나요?**  
A: 가능합니다. 대상 `Section` 또는 `PageSetup`을 가져와 해당 페이지에 위치한 단락에 도형을 삽입하면 됩니다.

**Q: .doc 파일에도 적용되나요?**  
A: 물론입니다. Aspose.Words는 형식을 추상화하므로 동일한 코드로 **Word 문서를 저장**할 수 있습니다—`.doc`이든 `.docx`이든 상관없습니다.

**Q: 타원 같은 다른 도형이 필요하면 어떻게 하나요?**  
A: `ShapeType.RECTANGLE`을 `ShapeType.ELLIPSE`로 교체하면 됩니다. 그림자 속성은 그대로 사용할 수 있습니다.

---

## 결론

이제 **Word 문서를 저장**하면서 **사각형 도형을 추가**, **그림자를 적용**, 그리고 **도형을 첫 번째 단락에 삽입**하는 방법을 알게 되었습니다—모두 몇 줄의 깔끔한 Java 코드로 구현됩니다. 이 패턴은 도형 종류를 바꾸거나, 그림자 설정을 조정하거나, 테이블·헤더에 도형을 배치하는 등 다양한 상황에 확장할 수 있습니다. 여러분의 문서 자동화 요구에 맞춰 무한히 활용해 보세요.

다음 도전 과제는? 여러 도형을 겹쳐 놓거나, 사각형 안에 텍스트를 넣거나, 차트와 워터마크가 포함된 전체 보고서를 생성해 보세요. 여기서 다룬 기본 원리를 기반으로 하면 어느 정도는 이미 준비된 셈입니다.

행복한 코딩 되시고, Word 자동화가 버그 없는 그림자와 함께 하길 바랍니다!

## 다음에 배울 내용은?

다음 튜토리얼들은 이 가이드에서 다룬 기술을 확장하는 주제들을 다룹니다. 각 리소스는 완전한 코드 예제와 단계별 설명을 제공하여 추가 API 기능을 마스터하고 프로젝트에 다양한 구현 방식을 적용할 수 있도록 돕습니다.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [How to save word as pcl with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pcl-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}