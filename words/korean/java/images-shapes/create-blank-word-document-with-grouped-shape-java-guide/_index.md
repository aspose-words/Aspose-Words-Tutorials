---
category: general
date: 2026-07-20
description: Aspose.Words를 사용하여 Java에서 빈 워드 문서를 생성합니다. 그룹을 만들고, 사각형 도형을 삽입하며, 도형에
  이미지를 삽입하는 방법을 배웁니다.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create group
- add image word document
- insert rectangle shape
- embed image in shape
language: ko
lastmod: 2026-07-20
og_description: Java와 Aspose.Words를 사용하여 빈 워드 문서를 생성합니다. 이 가이드는 그룹을 만들고, 사각형 도형을 삽입하며,
  동적 워드 파일을 위해 도형에 이미지를 삽입하는 방법을 보여줍니다.
og_image_alt: Screenshot of a blank Word document containing a grouped shape with
  a rectangle and an embedded image
og_title: 그룹화된 도형이 포함된 빈 워드 문서 만들기 – Java 가이드
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  headline: Create blank word document with grouped shape – Java guide
  type: TechArticle
- description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  name: Create blank word document with grouped shape – Java guide
  steps:
  - name: '`output.docx` appears in the project folder.'
    text: '`output.docx` appears in the project folder.'
  - name: Opening the file shows a single page with a grouped shape.
    text: Opening the file shows a single page with a grouped shape.
  - name: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
    text: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
  - name: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
    text: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: 그룹화된 도형이 포함된 빈 워드 문서 만들기 – Java 가이드
url: /ko/java/images-shapes/create-blank-word-document-with-grouped-shape-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 그룹화된 도형이 포함된 빈 워드 문서 만들기 – Java 가이드

빈 워드 문서에 이미 깔끔하게 그룹화된 도형이 포함된 **create blank word document** 를 만들고 싶으신가요? 보고서 템플릿을 만들거나 로고와 캡션을 위한 자리 표시자가 필요할 수도 있습니다. 어느 경우든 흔히 겪는 문제는 다음과 같습니다: 빈 파일을 만든 뒤 그룹을 추가하고, 그 안에 사각형을 넣고, 마지막으로 이미지를 삽입해야 합니다—모두 프로그래밍 방식으로.

이 튜토리얼에서는 바로 실행 가능한 완전한 Java 예제를 단계별로 살펴보겠습니다. **how to create group**, **insert rectangle shape**, **add image word document** 를 같은 그룹 안에 넣는 방법을 배웁니다. 최종적으로는 맞춤형 템플릿처럼 보이는 Word 파일을 얻게 됩니다.

> **What you’ll get:** 완전한 Java 클래스, 단계별 설명, 파일 경로 처리 팁, 예상 출력 미리보기. 외부 문서는 필요 없습니다—필요한 모든 것이 여기 있습니다.

---

## Create blank word document – Step‑by‑Step Overview

먼저 진정한 빈 Word 파일이 필요합니다. Aspose.Words 를 사용하면 매우 간단합니다: 기본 생성자를 사용해 `Document` 클래스를 인스턴스화하면 됩니다. 이렇게 하면 Word에서 **New → Blank document** 를 클릭한 것과 동일한 깨끗한 캔버스를 얻을 수 있습니다.

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Why start with a blank document?**  
> 빈 문서는 나중에 추가할 도형에 영향을 줄 수 있는 숨겨진 스타일이나 섹션이 없음을 보장합니다. 또한 파일 크기를 최소화하여 배치 작업에서 수십 개의 파일을 생성할 때 유용합니다.

---

## How to create group and add shapes

**group shape** 은 본질적으로 여러 자식 도형을 담을 수 있는 컨테이너이며, 그림 객체를 위한 폴더와 같습니다. 그룹화하면 전체 세트를 한 번에 이동, 크기 조정 또는 회전할 수 있습니다.

```java
        // 2️⃣ Insert a group shape 200x200 points
        GroupShape group = builder.insertGroupShape(200.0, 200.0);
```

`insertGroupShape` 메서드는 사각형과 이미지를 위한 부모 역할을 할 `GroupShape` 객체를 반환합니다. 크기는 포인트 단위(1 포인트 = 1/72 인치)로 표현되며, 200 포인트는 대략 2.78 × 2.78 인치 상자를 의미합니다.

> **Pro tip:** 그룹을 투명하게 만들려면 생성 후 `group.setFillColor(Color.getWhite());` 를 설정하세요.

그룹이 생성되었으니 이제 빌더에게 다음 도형을 어디에 배치할지 알려야 합니다. 빌더의 커서는 그룹의 첫 번째 단락 안에 위치해야 합니다.

```java
        // Move the cursor to the first paragraph of the group
        builder.moveTo(group.getFirstParagraph());
```

---

## Insert rectangle shape inside the group

사각형은 텍스트 자리 표시자나 시각적 힌트로 자주 사용됩니다. 이를 그룹의 **first child** 로 추가하면 이후 이미지보다 뒤에 배치됩니다.

```java
        // 3️⃣ Insert a rectangle (100x50 points) as the first child
        builder.insertShape(ShapeType.RECTANGLE, 100.0, 50.0);
```

사각형은 그룹의 좌표계를 상속하므로 100 × 50 포인트 크기가 기본적으로 중앙에 배치됩니다. 반환된 `Shape` 객체에 접근해 테두리 추가, 채우기 색 변경, 그림자 적용 등으로 스타일을 더할 수 있습니다.

```java
        // Optional styling (commented out for brevity)
        // Shape rect = builder.getCurrentShape();
        // rect.setFillColor(Color.getLightGray());
        // rect.setStrokeColor(Color.getBlack());
```

---

## Add image word document – embedding image in shape

이제 재미있는 부분: **embed image in shape**. 동일한 그룹의 두 번째 자식으로 JPEG 이미지를 삽입합니다. 커서가 아직 그룹 안에 있기 때문에 이미지는 자동으로 자식 노드가 됩니다.

```java
        // 4️⃣ Insert an image (make sure the path is correct)
        builder.insertImage("sample.jpg");   // <-- replace with your image path
```

이미지 파일을 찾을 수 없으면 Aspose.Words 가 `FileNotFoundException` 을 발생시킵니다. 이를 방지하려면 `sample.jpg` 를 프로젝트 작업 디렉터리에 두거나 절대 경로를 사용하세요.

> **What if you need a different image format?**  
> Aspose.Words 는 PNG, BMP, GIF, TIFF, 그리고 SVG 도 지원합니다. 파일 확장자를 바꾸기만 하면 라이브러리가 변환을 처리합니다.

---

## Save the document and see the result

마지막으로 메모리 상의 문서를 디스크에 저장합니다. 결과 `.docx` 파일에는 사각형과 이미지가 모두 포함된 단일 페이지가 들어갑니다.

```java
        // 5️⃣ Save the document to verify the output
        doc.save("output.docx");
    }
}
```

`output.docx` 를 Microsoft Word 로 열면 왼쪽 상단에 200 × 200 포인트 그룹이 표시됩니다. 그룹 안에는 밝은 회색 사각형이 위에 놓이고, 바로 아래에 지정한 사진이 완벽히 정렬되어 나타납니다.

![Grouped shape example](grouped-shape.png){:alt="그룹화된 도형이 포함된 빈 워드 문서의 스크린샷(직사각형과 삽입된 이미지 포함)"}

---

## Common variations and edge‑case handling

| Scenario | What to change | Why it matters |
|----------|----------------|----------------|
| **다른 그룹 크기** | `insertGroupShape(width, height)` 의 매개변수를 조정합니다 | 더 큰 그룹은 더 복잡한 레이아웃을 수용할 수 있습니다. |
| **여러 이미지** | `builder.insertImage()` 를 반복 호출하고 매번 그룹의 단락으로 이동합니다 | 각 호출은 새로운 자식을 추가합니다; `Shape.setLeft()` / `setTop()` 으로 위치를 지정할 수도 있습니다. |
| **동적 이미지 경로** | `String.format("images/%s.jpg", imageName)` 을 사용합니다 | 배치 처리에 코드를 재사용 가능하게 합니다. |
| **PDF로 저장** | `doc.save("output.pdf")` 로 교체합니다 | Aspose.Words는 실시간 변환이 가능해 직접 PDF를 생성할 수 있습니다. |
| **그룹 회전** | `group.setRotation(45);` | 장식용 워터마크나 스타일 헤더에 유용합니다. |

---

## Expected output and verification

클래스를 실행한 후:

1. `output.docx` 가 프로젝트 폴더에 생성됩니다.  
2. 파일을 열면 그룹화된 도형이 있는 단일 페이지가 표시됩니다.  
3. 그룹 안에서 직사각형은 좌상단에 배치되고, 이미지가 바로 아래에 위치합니다.  
4. Word에서 그룹을 선택하면 두 자식 객체가 모두 강조 표시되어 실제로 그룹화되었음을 확인할 수 있습니다.

이 단계 중 하나라도 실패하면 이미지 경로를 다시 확인하고 Aspose.Words JAR 가 클래스패스에 포함되어 있는지 확인하세요.

---

## Conclusion

이제 **create blank word document** 를 만들고, 사각형과 삽입된 이미지를 포함하는 그룹화된 도형으로 풍부하게 할 수 있습니다. **how to create group**, **insert rectangle shape**, **add image word document** 를 마스터하면 수동 조정 없이 코드만으로 정교한 Word 템플릿을 구축할 수 있습니다.

다음 도전 과제가 준비되셨나요? 같은 그룹 안에 텍스트 상자를 추가하거나 기업 브랜딩에 맞게 다양한 도형 스타일을 실험해 보세요. 이 레이아웃으로 시작하는 전체 보고서 라이브러리를 생성할 수도 있습니다.

행복한 코딩 되세요, 그리고 아래 댓글에 여러분만의 변형을 자유롭게 공유해 주세요!

## What Should You Learn Next?

다음 튜토리얼은 이 가이드에서 시연한 기술을 기반으로 하는 밀접한 관련 주제를 다룹니다. 각 자료에는 완전한 코드 예제와 단계별 설명이 포함되어 있어 추가 API 기능을 마스터하고 프로젝트에 적용할 수 있는 대체 구현 방식을 탐색하는 데 도움이 됩니다.

- [Java 워드 문서 만들기 – 그림자 효과가 있는 직사각형 도형 추가](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words for Java에서 DocumentBuilder를 사용하여 양식 필드 생성 및 콘텐츠 추가 방법](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aspose.Words for Java로 PDF 문서 만들기 | 문서 처리 API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}