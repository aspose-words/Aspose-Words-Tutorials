---
date: 2026-02-16
description: Aspose.Words for Java를 사용하여 텍스트 상자를 만들고, 워터마크 단어를 추가하고, 여러 도형을 그룹화하고,
  도형의 가로세로 비율을 설정하며, 도형을 표 셀에 배치하는 방법을 배웁니다.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java에서 텍스트 상자를 만들고 문서 도형을 사용하는 방법
url: /ko/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java에서 문서 도형 사용하기

## Aspose.Words for Java에서 문서 도형 사용 소개

이 포괄적인 가이드에서는 **you’ll learn how to create text box** 객체와 Aspose.Words for Java의 다른 강력한 도형을 만드는 방법을 배웁니다. 도형을 사용하면 워드 문서에 콜아웃, 버튼, 워터마크, SmartArt 등을 추가하여 시각적으로 매력적이고 인터랙티브하게 만들 수 있습니다. 간단한 텍스트 상자를 삽입하는 것부터 여러 도형을 그룹화하고, 가로세로 비율을 설정하며, 표 셀 안에 도형을 배치하는 실제 예제를 단계별로 살펴보겠습니다.

## 빠른 답변
- **텍스트 상자를 추가하는 기본 방법은 무엇인가요?** Use `DocumentBuilder.insertShape(ShapeType.TEXT_BOX, …)`.
- **도형을 함께 그룹화할 수 있나요?** Yes – create a `GroupShape` and append child shapes.
- **도형의 가로세로 비율을 잠그거나 풀려면 어떻게 하나요?** Call `shape.setAspectRatioLocked(true/false)`.
- **도형으로 워터마크를 추가할 수 있나요?** Absolutely – insert a `Shape` with `TEXT_PLAIN_TEXT` and set its fill/stroke.
- **SmartArt 다이어그램을 Aspose.Words에서 사용할 수 있나요?** Yes – detect with `shape.hasSmartArt()` and update via `shape.updateSmartArtDrawing()`.

## 텍스트 상자란 무엇이며 왜 텍스트 상자 도형을 만들어야 하나요?

텍스트 상자는 서식이 적용된 텍스트, 이미지 또는 다른 도형을 담을 수 있는 컨테이너입니다. 자동화에서 **create text box**를 사용하면 페이지 어디에든 떠 있는 콘텐츠를 배치할 수 있어 주석, 콜아웃 또는 장식 요소를 문서 본문의 흐름을 변경하지 않고 삽입하기에 적합합니다.

## 도형 추가 방법

코드 작성을 시작하기 전에 프로젝트에 Aspose.Words for Java가 참조되어 있는지 확인하십시오. 아직 추가하지 않았다면 공식 사이트에서 라이브러리를 다운로드하십시오:

[Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### 문서에 도형 추가

## 여러 도형을 그룹화하는 방법

`GroupShape`은 여러 개별 도형을 하나의 단위로 취급할 수 있게 해 주며, 함께 이동하거나 회전할 때 유용합니다.

### GroupShape 삽입

아래는 그룹을 생성하고 두 개의 서로 다른 도형을 추가한 뒤, 해당 그룹을 문서에 삽입하는 전체 예제입니다.

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

## 텍스트 상자 만들기 (create text box)

### 텍스트 상자 도형 삽입

`insertShape` 메서드는 텍스트 상자를 쉽게 추가할 수 있게 해 줍니다. 아래 예제는 텍스트 상자를 배치하고 회전하는 두 가지 방법을 보여줍니다.

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

## 도형 가로세로 비율 설정

### 가로세로 비율 관리

때때로 도형을 원래 비율을 유지하지 않고 늘려야 할 때가 있습니다. 다음 코드 조각은 이미지 도형의 가로세로 비율 잠금을 해제하는 방법을 보여줍니다.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## 표 셀에 도형 배치

### 표 셀 안에 도형 배치

아래는 표를 만든 뒤 페이지에 상대적으로 배치되지만 셀 안에도 넣을 수 있는 워터마크 도형을 삽입하는 단계별 예제입니다.

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
watermark.isLayoutInCell(true); // Display the shape outside of the table cell if it will be placed into a cell.
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

### SmartArt 도형 감지

`hasSmartArt()` 메서드를 사용하여 문서에서 SmartArt 객체를 프로그래밍 방식으로 찾을 수 있습니다.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### SmartArt 도면 업데이트

SmartArt 도형을 찾은 후에는 `updateSmartArtDrawing()`을 사용해 내부 도면 데이터를 새로 고칠 수 있습니다.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## 결론

이 가이드에서는 **create text box** 객체를 만들고, 여러 도형을 그룹화하며, 가로세로 비율을 조정하고, 표 셀 안에 도형을 삽입하고, 워터마크를 추가하고, Aspose.Words for Java를 사용해 SmartArt 다이어그램을 다루는 방법을 다루었습니다. 이러한 기술을 통해 프로그래밍 방식으로 풍부하게 서식이 지정된 인터랙티브 워드 문서를 만들 수 있습니다.

## FAQ

### Aspose.Words for Java란 무엇인가요?

Aspose.Words for Java는 개발자가 워드 문서를 프로그래밍 방식으로 생성, 수정 및 변환할 수 있도록 해 주는 Java 라이브러리입니다. 다양한 형식의 문서를 다루기 위한 광범위한 기능과 도구를 제공합니다.

### Aspose.Words for Java를 어떻게 다운로드하나요?

다음 링크를 통해 Aspose 웹사이트에서 Aspose.Words for Java를 다운로드할 수 있습니다: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### 문서 도형을 사용하면 어떤 이점이 있나요?

문서 도형은 시각적 요소와 인터랙티브성을 추가하여 문서를 보다 매력적이고 유용하게 만듭니다. 도형을 사용하면 콜아웃, 버튼, 이미지, 워터마크 등을 만들 수 있어 전체 사용자 경험을 향상시킵니다.

### 도형의 외관을 커스터마이즈할 수 있나요?

예, 도형의 크기, 위치, 회전, 채우기 색상 등 속성을 조정하여 외관을 커스터마이즈할 수 있습니다. Aspose.Words for Java는 도형 커스터마이징을 위한 다양한 옵션을 제공합니다.

### Aspose.Words for Java가 SmartArt와 호환되나요?

예, Aspose.Words for Java는 SmartArt 도형을 지원하므로 문서에서 복잡한 다이어그램과 그래픽을 다룰 수 있습니다.

## 자주 묻는 질문

**Q: 같은 도형 안에 텍스트 상자와 이미지를 결합할 수 있나요?**  
A: Yes. Insert an image into the text box shape using `builder.insertImage()` after creating the shape, then adjust its layout as needed.

**Q: 워터마크가 문서의 모든 콘텐츠 뒤에 표시되도록 하려면 어떻게 해야 하나요?**  
A: Set the shape’s `WrapType` to `NONE` and adjust its `RelativeHorizontalPosition` and `RelativeVerticalPosition` to `PAGE`. This positions the watermark behind the main flow.

**Q: Word에서 그룹화된 도형에 애니메이션을 적용할 수 있나요?**  
A: While Aspose.Words can create and group shapes, animation features are not supported because they rely on Word’s UI capabilities.

**Q: SmartArt 지원을 위해 필요한 Aspose.Words 버전은 무엇인가요?**  
A: SmartArt detection and updating are available starting from Aspose.Words 20.9 for Java and later.

**Q: 많은 도형이 포함된 대용량 문서를 효율적으로 처리할 수 있나요?**  
A: Yes. Use `doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010)` or higher to improve performance on documents with many shapes.

---

**마지막 업데이트:** 2026-02-16  
**테스트 환경:** Aspose.Words for Java 24.12  
**작성자:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}