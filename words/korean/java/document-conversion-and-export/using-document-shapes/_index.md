---
title: Java용 Aspose.Words에서 문서 모양 사용
linktitle: 문서 모양 사용
second_title: Aspose.Words Java 문서 처리 API
description: Aspose.Words for Java에서 문서 모양의 힘을 잠금 해제하세요. 단계별 예제를 통해 시각적으로 매력적인 문서를 만드는 방법을 배우세요.
weight: 14
url: /ko/java/document-conversion-and-export/using-document-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java용 Aspose.Words에서 문서 모양 사용


## Aspose.Words for Java에서 문서 모양 사용 소개

이 포괄적인 가이드에서는 Aspose.Words for Java에서 문서 모양의 세계를 탐구해 보겠습니다. 모양은 시각적으로 매력적이고 대화형 문서를 만드는 데 필수적인 요소입니다. 콜아웃, 버튼, 이미지 또는 워터마크를 추가해야 하는지 여부에 관계없이 Aspose.Words for Java는 이를 효율적으로 수행할 수 있는 도구를 제공합니다. 소스 코드 예제를 통해 이러한 모양을 단계별로 사용하는 방법을 살펴보겠습니다.

## 문서 모양 시작하기

 코드로 넘어가기 전에 환경을 설정해 보겠습니다. Aspose.Words for Java가 프로젝트에 통합되어 있는지 확인하세요. 아직 통합되어 있지 않다면 Aspose 웹사이트에서 다운로드할 수 있습니다.[Aspose.Words for Java 다운로드](https://releases.aspose.com/words/java/)

## 문서에 모양 추가

### 그룹 모양 삽입

 에이`GroupShape` 여러 모양을 함께 그룹화할 수 있습니다. 다음은 모양을 만들고 삽입하는 방법입니다.`GroupShape`:

```java
Document doc = new Document();
doc.ensureMinimum();

GroupShape groupShape = new GroupShape(doc);
Shape accentBorderShape = new Shape(doc, ShapeType.ACCENT_BORDER_CALLOUT_1);
accentBorderShape.setWidth(100.0);
accentBorderShape.setHeight(100.0);

groupShape.appendChild(accentBorderShape);

Shape actionButtonShape = new Shape(doc, ShapeType.ACTION_BUTTON_BEGINNING);
actionButtonShape.setLeft(100.0);
actionButtonShape.setWidth(100.0);
actionButtonShape.setHeight(200.0);

groupShape.appendChild(actionButtonShape);

groupShape.setWidth(200.0);
groupShape.setHeight(200.0);
groupShape.setCoordSize(new Dimension(200, 200));

DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertNode(groupShape);

doc.save("Your Directory Path" + "WorkingWithShapes.AddGroupShape.docx");
```

### 텍스트 상자 모양 삽입

 텍스트 상자 모양을 삽입하려면 다음을 사용할 수 있습니다.`insertShape` 아래 예시와 같은 방법:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertShape(ShapeType.TEXT_BOX, RelativeHorizontalPosition.PAGE, 100.0,
    RelativeVerticalPosition.PAGE, 100.0, 50.0, 50.0, WrapType.NONE);

shape.setRotation(30.0);
builder.writeln();

shape = builder.insertShape(ShapeType.TEXT_BOX, 50.0, 50.0);
shape.setRotation(30.0);

OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);

doc.save("Your Directory Path" + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## 모양 속성 조작

### 종횡비 관리

도형의 종횡비를 잠글지 여부를 제어할 수 있습니다. 도형의 종횡비를 잠금 해제하는 방법은 다음과 같습니다.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

### 테이블 셀에 모양 배치

테이블 셀 내부에 모양을 배치해야 하는 경우 다음 코드를 사용하여 이를 구현할 수 있습니다.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

builder.startTable();
builder.getRowFormat().setHeight(100.0);
builder.getRowFormat().setHeightRule(HeightRule.EXACTLY);

for (int i = 0; i < 31; i++) {
    if (i != 0 && i % 7 == 0)
        builder.endRow();

    builder.insertCell();
    builder.write("Cell contents");
}

builder.endTable();

Shape watermark = new Shape(doc, ShapeType.TEXT_PLAIN_TEXT);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
watermark.isLayoutInCell(true); // 셀에 배치될 경우 표 셀 외부에 모양을 표시합니다.
watermark.setWidth(300.0);
watermark.setHeight(70.0);
watermark.setHorizontalAlignment(HorizontalAlignment.CENTER);
watermark.setVerticalAlignment(VerticalAlignment.CENTER);
watermark.setRotation(-40);
watermark.setFillColor(Color.GRAY);
watermark.setStrokeColor(Color.GRAY);
watermark.getTextPath().setText("watermarkText");
watermark.getTextPath().setFontFamily("Arial");
watermark.setName("WaterMark_{Guid.NewGuid()}");
watermark.setWrapType(WrapType.NONE);

Run run = (Run) doc.getChildNodes(NodeType.RUN, true).get(doc.getChildNodes(NodeType.RUN, true).getCount() - 1);
builder.moveTo(run);
builder.insertNode(watermark);

doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010);
doc.save("Your Directory Path" + "WorkingWithShapes.LayoutInCell.docx");
```

## SmartArt 도형 작업

### SmartArt 모양 감지

다음 코드를 사용하여 문서에서 SmartArt 모양을 감지할 수 있습니다.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### SmartArt 도면 업데이트

문서 내에서 SmartArt 그림을 업데이트하려면 다음 코드를 사용하세요.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## 결론

이 가이드에서는 Aspose.Words for Java에서 문서 모양의 세계를 살펴보았습니다. 문서에 다양한 모양을 추가하고, 속성을 조작하고, SmartArt 모양으로 작업하는 방법을 배웠습니다. 이러한 지식을 바탕으로 시각적으로 매력적이고 대화형 문서를 쉽게 만들 수 있습니다.

## 자주 묻는 질문

### Java용 Aspose.Words란 무엇인가요?

Aspose.Words for Java는 개발자가 Word 문서를 프로그래밍 방식으로 만들고, 수정하고, 변환할 수 있는 Java 라이브러리입니다. 다양한 형식의 문서 작업을 위한 광범위한 기능과 도구를 제공합니다.

### Aspose.Words for Java를 어떻게 다운로드할 수 있나요?

 다음 링크를 따라 Aspose 웹사이트에서 Aspose.Words for Java를 다운로드할 수 있습니다.[Aspose.Words for Java 다운로드](https://releases.aspose.com/words/java/)

### 문서 모양을 사용하면 어떤 이점이 있나요?

문서 모양은 문서에 시각적 요소와 상호 작용을 추가하여 더욱 매력적이고 유익한 정보를 제공합니다. 모양을 사용하면 콜아웃, 버튼, 이미지, 워터마크 등을 만들어 전반적인 사용자 경험을 향상시킬 수 있습니다.

### 모양의 모양을 사용자 정의할 수 있나요?

네, 크기, 위치, 회전, 채우기 색상과 같은 속성을 조정하여 모양의 모양을 사용자 정의할 수 있습니다. Aspose.Words for Java는 모양 사용자 정의를 위한 광범위한 옵션을 제공합니다.

### Aspose.Words for Java는 SmartArt와 호환됩니까?

네, Aspose.Words for Java는 SmartArt 도형을 지원하므로 문서에서 복잡한 다이어그램과 그래픽을 작업할 수 있습니다.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
