---
date: 2026-02-19
description: Aspose.Words for Java를 사용하여 워터마크가 포함된 문서를 만드는 방법과 전문적인 문서를 위한 이미지 워터마크
  추가 방법을 배워보세요.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java를 사용하여 워터마크가 있는 문서 만들기
url: /ko/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java를 사용하여 워터마크가 포함된 문서 만들기

이 튜토리얼에서는 Aspose.Words for Java API를 사용하여 **워터마크가 포함된 문서 만들기**를 소개합니다. 텍스트든 이미지든 워터마크는 파일을 기밀, 초안, 승인 등으로 표시하는 데 도움이 되며, 프로그래밍 방식으로 모든 Word 문서에 적용할 수 있습니다. 라이브러리 설정, 텍스트 및 이미지 워터마크 추가, 외관 커스터마이징, 필요 없을 때 제거하는 과정을 단계별로 안내합니다.

## Quick Answers
- **워터마크는 무엇을 하나요?** 각 페이지에 텍스트 또는 이미지를 겹쳐서 상태나 브랜드를 표시합니다.  
- **Java에서 워터마크를 추가하는 라이브러리는?** Aspose.Words for Java가 기본 워터마크 지원을 제공합니다.  
- **이미지 워터마크를 추가할 수 있나요?** 예—`Shape` 클래스를 사용하고 `add image watermark java` 방식을 적용합니다.  
- **워터마크를 반투명하게 할 수 있나요?** 텍스트 워터마크의 경우 `setSemitransparent` 로 불투명도를 제어할 수 있습니다.  
- **라이선스가 필요하나요?** 무료 체험판으로 테스트 가능하지만, 상용 환경에서는 상업용 라이선스가 필요합니다.

## 워터마크란 무엇이며 왜 사용하나요?

워터마크는 문서의 각 페이지에 추가되는 희미한 오버레이(텍스트 또는 그래픽)입니다. 일반적으로 **기밀**, **초안 상태**, **브랜딩** 등을 표시하기 위해 사용되며, 문서 내용 자체를 변경하지 않습니다. 프로그래밍 방식으로 워터마크를 적용하면 대량 파일에 일관성을 유지하면서 수동 편집에 비해 시간을 크게 절약할 수 있습니다.

## Aspose.Words for Java 설정하기

워터마크 추가를 시작하기 전에 프로젝트에 라이브러리가 준비되어 있는지 확인하세요:

1. [여기](https://releases.aspose.com/words/java/)에서 Aspose.Words for Java를 다운로드합니다.  
2. 다운로드한 JAR 파일(또는 Maven/Gradle 의존성)을 프로젝트의 classpath에 추가합니다.  
3. Java 소스 파일에 필요한 클래스를 import 합니다:

```java
import com.aspose.words.*;
import java.awt.Color;
import java.nio.file.*;
```

라이브러리 설정이 완료되었으니, 실제 워터마크 코드를 살펴보겠습니다.

## 텍스트 워터마크 추가 방법

텍스트 워터마크는 문서를 “CONFIDENTIAL” 또는 “DRAFT”와 같이 라벨링할 때 이상적입니다. 아래 예제는 `TextWatermarkOptions` 를 사용하여 **워터마크가 포함된 문서 만들기**를 간결하게 구현한 코드입니다.

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

### 텍스트 워터마크 커스터마이징
- **폰트 종류 및 크기** – `setFontFamily` 와 `setFontSize` 를 변경합니다.  
- **색상** – 원하는 `java.awt.Color` 를 사용합니다.  
- **레이아웃** – `HORIZONTAL`, `DIAGONAL` 등 중 선택합니다.  
- **투명도** – `setSemitransparent(true)` 로 밝은 효과를 적용합니다.

## 이미지 워터마크 추가 방법 (add image watermark java)

이미지 워터마크는 로고나 맞춤 그래픽에 적합합니다. 아래는 각 페이지 중앙에 PNG 이미지를 삽입하는 **add image watermark java** 예제입니다.

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

### 이미지 워터마크 팁
- **크기 조정** – `setWidth` / `setHeight` 로 페이지에 맞게 조절합니다.  
- **위치** – `RelativeHorizontalPosition` / `RelativeVerticalPosition` 을 사용해 중앙 정렬하거나 원하는 여백에 맞출 수 있습니다.  
- **투명도** – 로드하기 전에 이미지의 알파 채널을 조정하여 적용합니다.

## 워터마크 제거 방법

문서에 더 이상 워터마크가 필요하지 않을 경우 프로그래밍 방식으로 삭제할 수 있습니다. 아래 코드는 모든 Shape을 순회하면서 이름에 “Watermark”가 포함된 객체를 제거합니다.

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

## 흔히 발생하는 문제와 해결 방법

- **저장 후 워터마크가 사라짐** – 워터마크를 설정한 뒤 `doc.save()` 를 호출했는지 확인합니다.  
- **이미지가 표시되지 않음** – 이미지 경로가 올바른지, 지원되는 포맷(PNG, JPEG, BMP)인지 확인합니다.  
- **투명도가 적용되지 않음** – `setSemitransparent(true)` 은 텍스트 워터마크에만 적용됩니다. 이미지의 경우 PNG 알파 채널을 직접 편집해야 합니다.  
- **여러 섹션** – 문서에 섹션이 여러 개 있는 경우 각 섹션의 body에 워터마크를 추가하거나 `doc.getWatermark().setText(...)` 로 전역 적용합니다.

## Frequently Asked Questions

**Q: 텍스트 워터마크의 폰트를 어떻게 변경하나요?**  
A: `TextWatermarkOptions` 의 `setFontFamily` 속성을 수정합니다. 예: `options.setFontFamily("Times New Roman");`.

**Q: 하나의 문서에 여러 워터마크를 추가할 수 있나요?**  
A: 예. 이미지용 `Shape` 객체를 여러 개 만들거나, 각각 다른 옵션으로 `doc.getWatermark().setText(...)` 를 호출합니다.

**Q: 워터마크를 회전시킬 수 있나요?**  
A: 이미지 워터마크는 `Shape` 객체의 `watermark.setRotation(angle)` 로 회전시킬 수 있습니다. 텍스트 워터마크는 `setLayout` 속성(예: `WatermarkLayout.DIAGONAL`)을 사용합니다.

**Q: 워터마크를 반투명하게 만들려면 어떻게 하나요?**  
A: 텍스트 워터마크는 `TextWatermarkOptions` 에서 `options.setSemitransparent(true)` 로 설정합니다. 이미지의 경우 로드하기 전에 이미지 자체의 불투명도를 조정합니다.

**Q: 문서의 특정 섹션에만 워터마크를 추가할 수 있나요?**  
A: 예. `doc.getSections()` 를 순회하면서 원하는 섹션에만 워터마크를 추가하면 됩니다.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Last Updated:** 2026-02-19  
**Tested With:** Aspose.Words for Java 24.12 (latest)  
**Author:** Aspose