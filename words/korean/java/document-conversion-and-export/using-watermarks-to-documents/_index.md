---
date: 2025-12-18
description: Aspose.Words for Java를 사용하여 문서에 워터마크를 추가하는 방법을 배우세요. 이미지 워터마크 예제, 워터마크
  색상 변경, 워터마크 투명도 설정 및 워터마크 제거를 포함합니다.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java를 사용하여 문서에 워터마크 추가하는 방법
url: /ko/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java를 사용하여 문서에 워터마크 추가하는 방법

## Aspose.Words for Java에서 문서에 워터마크를 추가하기 위한 소개

이 튜토리얼에서는 Aspose.Words for Java를 사용하여 Word 문서에 **워터마크를 추가하는 방법**을 배웁니다. 워터마크는 파일을 기밀, 초안, 승인 등으로 표시하는 빠른 방법이며, 텍스트 기반 또는 이미지 기반일 수 있습니다. 라이브러리 설정, 텍스트 및 이미지 워터마크 생성, 워터마크 색상 변경 및 투명도 설정 등 외관을 맞춤화하는 방법, 필요 없을 때 워터마크를 제거하는 방법까지 단계별로 안내합니다.

## 빠른 답변
- **워터마크란?** 본문 내용 뒤에 표시되는 반투명 오버레이(텍스트 또는 이미지)입니다.  
- **여러 개의 워터마크를 추가할 수 있나요?** 예 – 여러 `Shape` 객체를 생성하고 원하는 섹션에 각각 추가하면 됩니다.  
- **워터마크 색상을 어떻게 변경하나요?** `TextWatermarkOptions`의 `Color` 속성을 조정합니다.  
- **이미지 워터마크 예제가 있나요?** 아래 “이미지 워터마크 추가” 섹션을 참고하세요.  
- **워터마크를 제거하려면 라이선스가 필요하나요?** 프로덕션 사용을 위해서는 유효한 Aspose.Words 라이선스가 필요합니다.

## Aspose.Words for Java 설정하기

문서에 워터마크를 추가하기 전에 Aspose.Words for Java를 설정해야 합니다. 다음 단계에 따라 시작하세요:

1. [here](https://releases.aspose.com/words/java/)에서 Aspose.Words for Java를 다운로드합니다.  
2. Aspose.Words for Java 라이브러리를 Java 프로젝트에 추가합니다.  
3. Java 코드에서 필요한 클래스를 import합니다.

이제 라이브러리 설정이 완료되었으니 실제 워터마크 생성으로 들어갑니다.

## 텍스트 워터마크 추가하기

텍스트 워터마크는 문서에 텍스트 정보를 삽입하고자 할 때 일반적으로 사용됩니다. 아래는 Aspose.Words for Java를 사용해 텍스트 워터마크를 추가하는 방법입니다:

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Define TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Set the watermark text and options
doc.getWatermark().setText("Test", options);

// Save the document with the watermark
doc.save("DocumentWithWatermark.docx");
```

**왜 중요한가요:** `setFontFamily`, `setFontSize`, `setColor`를 조정하면 **워터마크 색상**을 브랜드에 맞게 변경할 수 있고, `setSemitransparent(true)`를 사용하면 **워터마크 투명도**를 설정해 은은한 효과를 줄 수 있습니다.

## 이미지 워터마크 추가하기

텍스트 워터마크 외에도 이미지 워터마크를 문서에 삽입할 수 있습니다. 아래는 PNG 로고나 스탬프를 삽입하는 **이미지 워터마크 예제**입니다:

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Load the image for the watermark
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Set the watermark size and position
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Add the watermark to the document
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Save the document with the watermark
doc.save("DocumentWithImageWatermark.docx");
```

다른 이미지나 위치로 이 블록을 반복하면 **여러 개의 워터마크**를 하나의 파일에 추가할 수 있습니다.

## 워터마크 맞춤 설정

워터마크는 외관과 위치를 조정하여 맞춤 설정할 수 있습니다. 텍스트 워터마크의 경우 글꼴, 크기, 색상, 레이아웃을 변경할 수 있고, 이미지 워터마크는 크기, 회전, 정렬을 앞서 소개한 예제와 같이 수정할 수 있습니다.

## 워터마크 제거하기

워터마크가 더 이상 필요하지 않을 경우, 다음 코드를 사용해 모든 `Shape` 객체를 순회하면서 워터마크로 식별된 항목을 삭제할 수 있습니다:

```java
// Create a Document instance
Document doc = new Document("DocumentWithWatermark.docx");

// Remove the watermark
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Save the document without the watermark
doc.save("DocumentWithoutWatermark.docx");
```

## 일반적인 사용 사례 및 팁

- **기밀 초안:** “CONFIDENTIAL”과 같은 반투명 텍스트 워터마크를 적용합니다.  
- **브랜딩:** 회사 로고가 포함된 이미지 워터마크를 사용합니다.  
- **섹션별 워터마크:** `doc.getSections()`를 순회하면서 원하는 섹션에만 워터마크를 추가합니다.  
- **성능 팁:** 동일한 워터마크를 여러 문서에 적용할 때는 동일한 `TextWatermarkOptions` 인스턴스를 재사용합니다.

## 자주 묻는 질문

### 텍스트 워터마크의 글꼴을 어떻게 변경하나요?

텍스트 워터마크의 글꼴을 변경하려면 `TextWatermarkOptions`의 `setFontFamily` 속성을 수정하면 됩니다. 예시:

```java
options.setFontFamily("Times New Roman");
```

### 하나의 문서에 여러 워터마크를 추가할 수 있나요?

예, 서로 다른 설정을 가진 여러 `Shape` 객체를 생성하고 문서에 추가하면 하나의 문서에 여러 워터마크를 적용할 수 있습니다.

### 워터마크를 회전시킬 수 있나요?

예, `Shape` 객체의 `setRotation` 속성을 설정하면 워터마크를 회전시킬 수 있습니다. 양수 값은 시계 방향, 음수 값은 반시계 방향으로 회전합니다.

### 워터마크를 반투명하게 만들려면 어떻게 하나요?

워터마크를 반투명하게 만들려면 `TextWatermarkOptions`에서 `setSemitransparent` 속성을 `true`로 설정하면 됩니다.

### 문서의 특정 섹션에만 워터마크를 추가할 수 있나요?

예, 섹션을 순회하면서 원하는 섹션에만 워터마크를 추가하면 특정 섹션에만 워터마크를 적용할 수 있습니다.

---

**Last Updated:** 2025-12-18  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}