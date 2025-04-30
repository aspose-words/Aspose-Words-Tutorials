---
"description": "Odblokuj moc kształtów dokumentów w Aspose.Words dla Java. Naucz się tworzyć wizualnie angażujące dokumenty dzięki przykładom krok po kroku."
"linktitle": "Korzystanie z kształtów dokumentów"
"second_title": "Aspose.Words API przetwarzania dokumentów Java"
"title": "Korzystanie z kształtów dokumentów w Aspose.Words dla Java"
"url": "/pl/java/document-conversion-and-export/using-document-shapes/"
"weight": 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Korzystanie z kształtów dokumentów w Aspose.Words dla Java


## Wprowadzenie do korzystania z kształtów dokumentów w Aspose.Words dla Java

tym kompleksowym przewodniku zagłębimy się w świat kształtów dokumentów w Aspose.Words for Java. Kształty są niezbędnymi elementami, jeśli chodzi o tworzenie wizualnie atrakcyjnych i interaktywnych dokumentów. Niezależnie od tego, czy musisz dodać objaśnienia, przyciski, obrazy lub znaki wodne, Aspose.Words for Java zapewnia narzędzia, aby zrobić to wydajnie. Przyjrzyjmy się, jak używać tych kształtów krok po kroku na przykładach kodu źródłowego.

## Rozpoczęcie pracy z kształtami dokumentów

Zanim przejdziemy do kodu, skonfigurujmy nasze środowisko. Upewnij się, że masz Aspose.Words for Java zintegrowane z projektem. Jeśli jeszcze tego nie zrobiłeś, możesz pobrać je ze strony internetowej Aspose [Pobierz Aspose.Words dla Java](https://releases.aspose.com/words/java/)

## Dodawanie kształtów do dokumentów

### Wstawianie GroupShape

A `GroupShape` pozwala na grupowanie wielu kształtów razem. Oto jak możesz utworzyć i wstawić `GroupShape`:

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

### Wstawianie kształtu pola tekstowego

Aby wstawić kształt pola tekstowego, możesz użyć `insertShape` metodę pokazano w poniższym przykładzie:

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

## Manipulowanie właściwościami kształtu

### Zarządzanie współczynnikiem proporcji

Możesz kontrolować, czy współczynnik proporcji kształtu jest zablokowany, czy nie. Oto jak odblokować współczynnik proporcji kształtu:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

### Umieszczanie kształtu w komórce tabeli

Jeśli chcesz umieścić kształt w komórce tabeli, możesz to zrobić za pomocą następującego kodu:

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
watermark.isLayoutInCell(true); // Wyświetl kształt poza komórką tabeli, jeśli będzie on umieszczony w komórce.
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

## Praca z kształtami SmartArt

### Wykrywanie kształtów SmartArt

Możesz wykryć kształty SmartArt w dokumencie, korzystając z następującego kodu:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Aktualizowanie rysunków SmartArt

Aby zaktualizować rysunki SmartArt w dokumencie, użyj następującego kodu:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Wniosek

W tym przewodniku zbadaliśmy świat kształtów dokumentów w Aspose.Words for Java. Nauczyłeś się, jak dodawać różne kształty do dokumentów, manipulować ich właściwościami i pracować z kształtami SmartArt. Dzięki tej wiedzy możesz z łatwością tworzyć atrakcyjne wizualnie i interaktywne dokumenty.

## Najczęściej zadawane pytania

### Czym jest Aspose.Words dla języka Java?

Aspose.Words for Java to biblioteka Java, która umożliwia programistom programowe tworzenie, modyfikowanie i konwertowanie dokumentów Word. Zapewnia szeroki zakres funkcji i narzędzi do pracy z dokumentami w różnych formatach.

### Jak mogę pobrać Aspose.Words dla Java?

Możesz pobrać Aspose.Words for Java ze strony internetowej Aspose, korzystając z tego łącza: [Pobierz Aspose.Words dla Java](https://releases.aspose.com/words/java/)

### Jakie są korzyści ze stosowania kształtów dokumentów?

Kształty dokumentów dodają elementy wizualne i interaktywność do dokumentów, dzięki czemu stają się bardziej angażujące i informacyjne. Za pomocą kształtów możesz tworzyć objaśnienia, przyciski, obrazy, znaki wodne i inne, ulepszając ogólne wrażenia użytkownika.

### Czy mogę dostosować wygląd kształtów?

Tak, możesz dostosować wygląd kształtów, dostosowując ich właściwości, takie jak rozmiar, położenie, obrót i kolor wypełnienia. Aspose.Words for Java zapewnia rozbudowane opcje dostosowywania kształtów.

### Czy Aspose.Words dla Java jest kompatybilny ze SmartArt?

Tak, Aspose.Words for Java obsługuje kształty SmartArt, co umożliwia pracę ze złożonymi diagramami i grafikami w dokumentach.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}