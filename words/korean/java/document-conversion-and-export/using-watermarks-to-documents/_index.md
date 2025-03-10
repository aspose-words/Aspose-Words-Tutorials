---
title: Java용 Aspose.Words에서 문서에 워터마크 사용
linktitle: 문서에 워터마크 사용
second_title: Aspose.Words Java 문서 처리 API
description: Aspose.Words for Java에서 문서에 워터마크를 추가하는 방법을 알아보세요. 전문적인 문서에 맞게 텍스트와 이미지 워터마크를 사용자 지정하세요.
weight: 15
url: /ko/java/document-conversion-and-export/using-watermarks-to-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java용 Aspose.Words에서 문서에 워터마크 사용


## Aspose.Words for Java에서 문서에 워터마크 추가 소개

이 튜토리얼에서는 Aspose.Words for Java API를 사용하여 문서에 워터마크를 추가하는 방법을 살펴보겠습니다. 워터마크는 문서에 텍스트나 그래픽으로 레이블을 지정하여 상태, 기밀성 또는 기타 관련 정보를 표시하는 데 유용한 방법입니다. 이 가이드에서는 텍스트와 이미지 워터마크를 모두 다룹니다.

## Java용 Aspose.Words 설정

문서에 워터마크를 추가하기 전에 Aspose.Words for Java를 설정해야 합니다. 시작하려면 다음 단계를 따르세요.

1.  Aspose.Words for Java를 다운로드하세요[여기](https://releases.aspose.com/words/java/).
2. Java 프로젝트에 Aspose.Words for Java 라이브러리를 추가합니다.
3. Java 코드에 필요한 클래스를 가져옵니다.

이제 라이브러리를 설정했으니 워터마크를 추가해 보겠습니다.

## 텍스트 워터마크 추가

텍스트 워터마크는 문서에 텍스트 정보를 추가하고 싶을 때 일반적으로 선택하는 옵션입니다. Aspose.Words for Java를 사용하여 텍스트 워터마크를 추가하는 방법은 다음과 같습니다.

```java
// 문서 인스턴스 생성
Document doc = new Document("Document.docx");

// TextWatermarkOptions 정의
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

//워터마크 텍스트 및 옵션 설정
doc.getWatermark().setText("Test", options);

// 워터마크를 사용하여 문서를 저장합니다.
doc.save("DocumentWithWatermark.docx");
```

## 이미지 워터마크 추가

텍스트 워터마크 외에도 문서에 이미지 워터마크를 추가할 수도 있습니다. 이미지 워터마크를 추가하는 방법은 다음과 같습니다.

```java
// 문서 인스턴스 생성
Document doc = new Document("Document.docx");

// 워터마크에 대한 이미지를 로드합니다
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// 워터마크 크기와 위치 설정
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// 문서에 워터마크를 추가합니다
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// 워터마크를 사용하여 문서를 저장합니다.
doc.save("DocumentWithImageWatermark.docx");
```

## 워터마크 사용자 정의

워터마크의 모양과 위치를 조정하여 워터마크를 사용자 지정할 수 있습니다. 텍스트 워터마크의 경우 글꼴, 크기, 색상 및 레이아웃을 변경할 수 있습니다. 이미지 워터마크의 경우 이전 예에서 보여준 대로 크기와 위치를 수정할 수 있습니다.

## 워터마크 제거

문서에서 워터마크를 제거하려면 다음 코드를 사용하면 됩니다.

```java
// 문서 인스턴스 생성
Document doc = new Document("DocumentWithWatermark.docx");

// 워터마크를 제거하세요
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// 워터마크 없이 문서를 저장합니다.
doc.save("DocumentWithoutWatermark.docx");
```


## 결론

이 튜토리얼에서는 Aspose.Words for Java를 사용하여 문서에 워터마크를 추가하는 방법을 알아보았습니다. 텍스트나 이미지 워터마크를 추가해야 할 때 Aspose.Words는 이를 효율적으로 사용자 지정하고 관리할 수 있는 도구를 제공합니다. 더 이상 필요하지 않을 때 워터마크를 제거하여 문서가 깨끗하고 전문적이 되도록 할 수도 있습니다.

## 자주 묻는 질문

### 텍스트 워터마크의 글꼴을 어떻게 변경할 수 있나요?

 텍스트 워터마크의 글꼴을 변경하려면 다음을 수정하세요.`setFontFamily` 에 있는 재산`TextWatermarkOptions`. 예를 들어:

```java
options.setFontFamily("Times New Roman");
```

### 하나의 문서에 워터마크를 여러 개 추가할 수 있나요?

 네, 여러 개의 워터마크를 생성하여 문서에 여러 개의 워터마크를 추가할 수 있습니다.`Shape` 다양한 설정을 가진 객체를 문서에 추가합니다.

### 워터마크를 회전할 수 있나요?

 예, 워터마크를 설정하여 회전할 수 있습니다.`setRotation` 에 있는 재산`Shape` 객체. 양수 값은 워터마크를 시계 방향으로 회전시키고, 음수 값은 반시계 방향으로 회전시킵니다.

### 워터마크를 반투명하게 만들려면 어떻게 해야 하나요?

 워터마크를 반투명하게 만들려면 다음을 설정하세요.`setSemitransparent`재산에`true` 에서`TextWatermarkOptions`.

### 문서의 특정 섹션에 워터마크를 추가할 수 있나요?

네, 문서의 특정 섹션에 워터마크를 추가할 수 있습니다. 섹션을 반복하면서 원하는 섹션에 워터마크를 추가하면 됩니다.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
