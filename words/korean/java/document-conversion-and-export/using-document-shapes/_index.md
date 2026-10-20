---
date: 2025-12-14
description: Aspose.Words for Java를 사용하여 **이미지 모양 삽입** 방법을 배워보세요. 이 가이드는 모양을 추가하고,
  텍스트 상자 모양을 만들고, 표에 모양을 배치하고, 모양 비율을 설정하고, 말풍선 모양을 추가하는 방법을 보여줍니다.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Java에서 문서 도형 사용
url: /ko/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java로 **이미지 도형 삽입**하는 방법

이 포괄적인 튜토리얼에서는 Aspose.Words for Java를 사용하여 Word 문서에 **이미지 도형** 객체를 삽입하는 방법을 알아봅니다. 보고서, 마케팅 자료, 인터랙티브 폼을 만들든, 도형을 사용하면 호출 상자, 버튼, 텍스트 상자, 워터마크, 심지어 SmartArt까지 추가할 수 있습니다. 각 단계를 차근차근 살펴보고, 특정 도형을 사용해야 하는 이유를 설명하며, 바로 실행 가능한 코드 스니펫을 제공합니다.

## 빠른 답변
- **도형을 추가하는 기본 방법은?** `DocumentBuilder.insertShape`를 사용하거나 `Shape` 인스턴스를 생성해 문서 트리에 추가합니다.  
- **이미지를 도형으로 삽입할 수 있나요?** 예 – `builder.insertImage`를 호출한 뒤 반환된 `Shape`를 다른 도형처럼 사용하면 됩니다.  
- **도형의 가로세로 비율을 유지하려면?** 필요에 따라 `shape.setAspectRatioLocked(true)` 또는 `false`를 설정합니다.  
- **도형을 그룹화할 수 있나요?** 물론 – 도형들을 `GroupShape`에 묶어 하나의 노드로 삽입합니다.  
- **SmartArt 다이어그램을 Aspose.Words에서 사용할 수 있나요?** 예, SmartArt 도형을 프로그래밍 방식으로 감지하고 업데이트할 수 있습니다.

## **이미지 도형 삽입**이란?
*이미지 도형*은 Word 문서 안에 래스터 또는 벡터 그래픽을 담는 시각 요소입니다. Aspose.Words에서는 이미지가 `Shape` 객체로 표현되며, 크기, 위치, 회전, 텍스트 래핑 등을 완벽히 제어할 수 있습니다.

## 문서에서 도형을 사용하는 이유
- **시각적 효과:** 도형은 핵심 정보를 강조합니다.  
- **인터랙티브:** 버튼 및 호출 상자를 URL이나 북마크에 연결할 수 있습니다.  
- **레이아웃 유연성:** 절대 좌표 또는 상대 좌표로 그래픽을 정확히 배치합니다.  
- **자동화:** 수동 편집 없이 복잡한 레이아웃을 프로그램matically 생성합니다.

## 사전 준비 사항
- Java Development Kit (JDK 8 이상)  
- Aspose.Words for Java 라이브러리 (공식 사이트에서 다운로드)  
- Java 및 객체 지향 프로그래밍에 대한 기본 지식  

라이브러리는 여기서 다운로드할 수 있습니다: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

## **도형 추가** 방법 – GroupShape 삽입
`GroupShape`를 사용하면 여러 도형을 하나의 단위로 취급할 수 있어, 여러 요소를 동시에 이동하거나 서식 지정할 때 유용합니다.

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

## **텍스트 상자 도형** 만들기
텍스트 상자는 서식이 적용된 텍스트를 담을 수 있는 컨테이너이며, 동적인 효과를 위해 회전시킬 수도 있습니다.

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

## **도형 가로세로 비율** 설정
때로는 도형을 자유롭게 늘리고 싶고, 때로는 원래 비율을 유지하고 싶을 때가 있습니다. 가로세로 비율 제어는 매우 간단합니다.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## **테이블 안에 도형** 배치
테이블 셀 안에 도형을 삽입하면 보고서 레이아웃을 구성할 때 편리합니다. 아래 예시는 테이블을 만든 뒤 페이지 전체에 걸치는 워터마크 스타일 도형을 삽입합니다.

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

## **호출 상자 도형** 추가
호출 상자 도형은 메모나 경고를 강조할 때 적합합니다. 위 코드에서는 `ACCENT_BORDER_CALLOUT_1`을 사용했지만, 디자인에 맞게 `ShapeType`을 다른 호출 상자 변형으로 교체하면 됩니다.

## SmartArt 도형 작업

### SmartArt 도형 감지
SmartArt 다이어그램을 프로그래밍 방식으로 식별하면 필요에 따라 처리하거나 교체할 수 있습니다.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### SmartArt 그림 업데이트
감지된 SmartArt를 업데이트하여 데이터 변경 사항을 반영할 수 있습니다.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## 일반적인 문제 및 팁
- **도형이 보이지 않음:** `builder.insertNode`를 사용해 대상 노드 뒤에 도형을 삽입했는지 확인하세요.  
- **예상치 못한 회전:** 회전은 도형 중심을 기준으로 적용됩니다. 필요하면 `setLeft`/`setTop`을 조정하세요.  
- **가로세로 비율 고정:** 기본적으로 많은 도형이 비율을 고정합니다. 자유롭게 늘리려면 `setAspectRatioLocked(false)`를 호출하세요.  
- **SmartArt 감지 실패:** 사용 중인 Aspose.Words 버전이 SmartArt를 지원하는지 확인하세요 (v24 이상).

## 자주 묻는 질문

**Q: Aspose.Words for Java란?**  
A: Aspose.Words for Java는 개발자가 프로그램matically Word 문서를 생성, 수정, 변환할 수 있게 해 주는 Java 라이브러리입니다. 다양한 형식의 문서를 다루는 폭넓은 기능과 도구를 제공합니다.

**Q: Aspose.Words for Java를 어떻게 다운로드하나요?**  
A: 다음 링크를 통해 Aspose 웹사이트에서 다운로드할 수 있습니다: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

**Q: 문서 도형을 사용하면 어떤 이점이 있나요?**  
A: 도형을 사용하면 문서에 시각적 요소와 인터랙티브 기능을 추가해 더욱 매력적이고 정보 전달이 효과적인 문서를 만들 수 있습니다. 호출 상자, 버튼, 이미지, 워터마크 등을 손쉽게 구현할 수 있습니다.

**Q: 도형의 외관을 커스터마이즈할 수 있나요?**  
A: 예, 도형의 크기, 위치, 회전, 채우기 색상 등 다양한 속성을 조정하여 외관을 자유롭게 커스터마이즈할 수 있습니다. Aspose.Words for Java는 도형 맞춤 설정을 위한 풍부한 옵션을 제공합니다.

**Q: Aspose.Words for Java가 SmartArt를 지원하나요?**  
A: 예, Aspose.Words for Java는 SmartArt 도형을 지원하므로 복잡한 다이어그램과 그래픽을 문서에서 작업할 수 있습니다.

---

**마지막 업데이트:** 2025-12-14  
**테스트 환경:** Aspose.Words for Java 24.12 (최신)  
**작성자:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}