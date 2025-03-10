---
title: 문서 워터마킹 및 페이지 설정
linktitle: 문서 워터마킹 및 페이지 설정
second_title: Aspose.Words Java 문서 처리 API
description: Aspose.Words for Java로 워터마크를 적용하고 페이지 구성을 설정하는 방법을 알아보세요. 소스 코드가 포함된 포괄적인 가이드입니다.
weight: 13
url: /ko/java/document-styling/document-watermarking-page-setup/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 문서 워터마킹 및 페이지 설정

## 소개

문서 조작의 영역에서 Aspose.Words for Java는 강력한 도구로 자리 잡고 있어 개발자가 문서 처리의 모든 측면을 제어할 수 있습니다. 이 포괄적인 가이드에서는 Aspose.Words for Java를 사용하여 문서 워터마킹 및 페이지 설정의 복잡한 내용을 살펴보겠습니다. 노련한 개발자이든 Java 문서 처리의 세계에 막 발을 들인 사람이든 이 단계별 가이드는 필요한 지식과 소스 코드를 제공합니다.

## 문서 워터마킹

### 워터마크 추가

문서에 워터마크를 추가하는 것은 브랜딩이나 콘텐츠 보안에 매우 중요할 수 있습니다. Aspose.Words for Java는 이 작업을 간단하게 만듭니다. 방법은 다음과 같습니다.

```java
// 문서를 로드합니다
Document doc = new Document("document.docx");

// 워터마크 만들기
Shape watermark = new Shape(doc, ShapeType.TEXT_PLAIN_TEXT);
watermark.getTextPath().setText("Confidential");
watermark.setWidth(300);
watermark.setHeight(100);

// 워터마크 위치 지정
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
watermark.setWrapType(WrapType.NONE);
watermark.setVerticalAlignment(VerticalAlignment.CENTER);
watermark.setHorizontalAlignment(HorizontalAlignment.CENTER);

// 워터마크를 삽입하세요
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// 문서를 저장하세요
doc.save("document_with_watermark.docx");
```

### 워터마크 사용자 정의

글꼴, 크기, 색상 및 회전을 조정하여 워터마크를 더욱 사용자 정의할 수 있습니다. 이러한 유연성 덕분에 워터마크가 문서의 스타일과 완벽하게 일치합니다.

## 페이지 설정

### 페이지 크기 및 방향

페이지 설정은 문서 서식 지정에서 핵심입니다. Aspose.Words for Java는 페이지 크기와 방향을 완벽하게 제어할 수 있습니다.

```java
// 문서를 로드합니다
Document doc = new Document("document.docx");

// 페이지 크기를 A4로 설정하세요
doc.getFirstSection().getPageSetup().setPageWidth(595.0);
doc.getFirstSection().getPageSetup().setPageHeight(842.0);

// 페이지 방향을 가로로 변경하세요
doc.getFirstSection().getPageSetup().setOrientation(Orientation.LANDSCAPE);

// 수정된 문서를 저장합니다
doc.save("formatted_document.docx");
```

### 여백 및 페이지 번호 매기기

전문적인 문서에는 여백과 페이지 번호에 대한 정확한 제어가 필수적입니다. Aspose.Words for Java로 이를 달성하세요.

```java
// 문서를 로드합니다
Document doc = new Document("document.docx");

// 여백 설정
doc.getFirstSection().getPageSetup().setLeftMargin(72.0);
doc.getFirstSection().getPageSetup().setRightMargin(72.0);
doc.getFirstSection().getPageSetup().setTopMargin(72.0);
doc.getFirstSection().getPageSetup().setBottomMargin(72.0);

// 페이지 번호 매기기 활성화
doc.getFirstSection().getPageSetup().setDifferentFirstPageHeaderFooter(true);
HeaderFooter firstPageHeader = doc.getFirstSection().getHeadersFooters().getByHeaderFooterType(HeaderFooterType.HEADER_FIRST);
firstPageHeader.appendParagraph("First Page Header");

// 포맷된 문서를 저장합니다
doc.save("formatted_document.docx");
```

## 자주 묻는 질문

### 문서에서 워터마크를 제거하려면 어떻게 해야 하나요?

문서에서 워터마크를 제거하려면 문서의 모양을 반복하고 워터마크를 나타내는 모양을 제거하면 됩니다. 다음은 스니펫입니다.

```java
Document doc = new Document("document_with_watermark.docx");

for (Shape shape : doc.getChildNodes(NodeType.SHAPE, true).<Shape>toArray()) {
    if (shape.getText().contains("Confidential")) {
        shape.remove();
    }
}

doc.save("document_without_watermark.docx");
```

### 하나의 문서에 워터마크를 여러 개 추가할 수 있나요?

네, 추가 Shape 객체를 만들고 필요에 따라 위치를 조정하면 문서에 여러 개의 워터마크를 추가할 수 있습니다.

### 가로 방향의 페이지 크기를 법적으로 변경하려면 어떻게 해야 합니까?

가로 방향으로 페이지 크기를 Legal로 설정하려면 다음과 같이 페이지 너비와 높이를 수정하세요.

```java
doc.getFirstSection().getPageSetup().setPageWidth(842.0);
doc.getFirstSection().getPageSetup().setPageHeight(595.0);
```

### 워터마크의 기본 글꼴은 무엇입니까?

워터마크의 기본 글꼴은 Calibri이고 글꼴 크기는 36입니다.

### 특정 페이지부터 페이지 번호를 추가하려면 어떻게 해야 하나요?

다음과 같이 문서의 시작 페이지 번호를 설정하면 됩니다.

```java
doc.getFirstSection().getPageSetup().setPageStartingNumber(5);
```

### 헤더나 푸터의 텍스트를 가운데 정렬하려면 어떻게 해야 하나요?

머리글이나 바닥글 내의 Paragraph 개체에서 setAlignment 메서드를 사용하여 머리글이나 바닥글의 텍스트를 가운데 정렬할 수 있습니다.

## 결론

이 광범위한 가이드에서 우리는 Aspose.Words for Java를 사용하여 문서 워터마킹 및 페이지 설정의 기술을 살펴보았습니다. 제공된 소스 코드 조각과 통찰력을 무장하고, 이제 문서를 정교하게 조작하고 서식을 지정할 수 있는 도구를 갖추게 되었습니다. Aspose.Words for Java를 사용하면 정확한 사양에 맞게 조정된 전문적이고 브랜드화된 문서를 만들 수 있습니다.

문서 조작을 마스터하는 것은 개발자에게 귀중한 기술이며, Aspose.Words for Java는 이 여정에서 신뢰할 수 있는 동반자입니다. 오늘부터 멋진 문서를 만들어보세요!
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
