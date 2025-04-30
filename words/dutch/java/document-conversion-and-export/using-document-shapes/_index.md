---
"description": "Ontdek de kracht van documentvormen in Aspose.Words voor Java. Leer hoe u visueel aantrekkelijke documenten maakt met stapsgewijze voorbeelden."
"linktitle": "Documentvormen gebruiken"
"second_title": "Aspose.Words Java Documentverwerking API"
"title": "Documentvormen gebruiken in Aspose.Words voor Java"
"url": "/nl/java/document-conversion-and-export/using-document-shapes/"
"weight": 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Documentvormen gebruiken in Aspose.Words voor Java


## Inleiding tot het gebruik van documentvormen in Aspose.Words voor Java

In deze uitgebreide handleiding duiken we in de wereld van documentvormen in Aspose.Words voor Java. Vormen zijn essentiële elementen bij het maken van visueel aantrekkelijke en interactieve documenten. Of u nu tekstballonnen, knoppen, afbeeldingen of watermerken wilt toevoegen, Aspose.Words voor Java biedt de tools om dit efficiënt te doen. Laten we stap voor stap bekijken hoe u deze vormen kunt gebruiken met behulp van broncodevoorbeelden.

## Aan de slag met documentvormen

Voordat we aan de slag gaan met de code, gaan we onze omgeving opzetten. Zorg ervoor dat je Aspose.Words voor Java in je project hebt geïntegreerd. Als je dat nog niet hebt gedaan, kun je het downloaden van de Aspose-website. [Download Aspose.Words voor Java](https://releases.aspose.com/words/java/)

## Vormen toevoegen aan documenten

### Een GroupShape invoegen

A `GroupShape` Hiermee kunt u meerdere vormen groeperen. Hier leest u hoe u een `GroupShape`:

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

### Een tekstvakvorm invoegen

Om een tekstvakvorm in te voegen, kunt u de `insertShape` methode zoals getoond in het onderstaande voorbeeld:

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

## Vormeigenschappen manipuleren

### Het beheren van de beeldverhouding

Je kunt bepalen of de beeldverhouding van een vorm al dan niet vergrendeld is. Zo ontgrendel je de beeldverhouding van een vorm:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

### Een vorm in een tabelcel plaatsen

Als u een vorm in een tabelcel moet plaatsen, kunt u dit doen met de volgende code:

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
watermark.isLayoutInCell(true); // Geef de vorm buiten de tabelcel weer als deze in een cel wordt geplaatst.
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

## Werken met SmartArt-vormen

### SmartArt-vormen detecteren

U kunt SmartArt-vormen in een document detecteren met behulp van de volgende code:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### SmartArt-tekeningen bijwerken

Gebruik de volgende code om SmartArt-tekeningen in een document bij te werken:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Conclusie

In deze handleiding hebben we de wereld van documentvormen in Aspose.Words voor Java verkend. Je hebt geleerd hoe je verschillende vormen aan je documenten toevoegt, hun eigenschappen bewerkt en met SmartArt-vormen werkt. Met deze kennis kun je eenvoudig visueel aantrekkelijke en interactieve documenten maken.

## Veelgestelde vragen

### Wat is Aspose.Words voor Java?

Aspose.Words voor Java is een Java-bibliotheek waarmee ontwikkelaars programmatisch Word-documenten kunnen maken, wijzigen en converteren. Het biedt een breed scala aan functies en tools voor het werken met documenten in verschillende formaten.

### Hoe kan ik Aspose.Words voor Java downloaden?

U kunt Aspose.Words voor Java downloaden van de Aspose-website door deze link te volgen: [Download Aspose.Words voor Java](https://releases.aspose.com/words/java/)

### Wat zijn de voordelen van het gebruik van documentvormen?

Documentvormen voegen visuele elementen en interactiviteit toe aan uw documenten, waardoor ze aantrekkelijker en informatiever worden. Met vormen kunt u toelichtingen, knoppen, afbeeldingen, watermerken en meer maken, wat de algehele gebruikerservaring verbetert.

### Kan ik het uiterlijk van vormen aanpassen?

Ja, u kunt het uiterlijk van vormen aanpassen door hun eigenschappen aan te passen, zoals grootte, positie, rotatie en opvulkleur. Aspose.Words voor Java biedt uitgebreide opties voor het aanpassen van vormen.

### Is Aspose.Words voor Java compatibel met SmartArt?

Ja, Aspose.Words voor Java ondersteunt SmartArt-vormen, zodat u met complexe diagrammen en afbeeldingen in uw documenten kunt werken.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}