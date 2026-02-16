---
date: 2026-02-16
description: Leer hoe u een tekstvak maakt, een watermerkwoord toevoegt, meerdere
  vormen groepeert, de beeldverhouding van een vorm instelt en een vorm in een tabelcel
  plaatst met Aspose.Words voor Java.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Hoe een tekstvak te maken en Document Shapes te gebruiken in Aspose.Words voor
  Java
url: /nl/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Documentvormen gebruiken in Aspose.Words voor Java

## Introductie tot het gebruiken van documentvormen in Aspose.Words voor Java

In deze uitgebreide gids **je leert hoe je een tekstvak maakt** objecten en andere krachtige vormen maakt met Aspose.Words voor Java. Vormen stellen je in staat Word‑documenten te verrijken met bijschriften, knoppen, watermerken, SmartArt en meer—waardoor ze visueel aantrekkelijk en interactief worden. We lopen door praktijkvoorbeelden, van het invoegen van een eenvoudig tekstvak tot het groeperen van meerdere vormen, het instellen van beeldverhoudingen en het plaatsen van vormen in tabelcellen.

## Snelle antwoorden
- **Wat is de primaire manier om een tekstvak toe te voegen?** Gebruik `DocumentBuilder.insertShape(ShapeType.TEXT_BOX, …)`.
- **Kan ik vormen groeperen?** Ja – maak een `GroupShape` en voeg kindvormen toe.
- **Hoe vergrendel of ontgrendel ik de beeldverhouding van een vorm?** Roep `shape.setAspectRatioLocked(true/false)` aan.
- **Is het mogelijk om een watermerk toe te voegen met een vorm?** Absoluut – voeg een `Shape` met `TEXT_PLAIN_TEXT` in en stel de vulling/omtrek in.
- **Werken SmartArt‑diagrammen met Aspose.Words?** Ja – detecteer met `shape.hasSmartArt()` en werk bij via `shape.updateSmartArtDrawing()`.

## Wat is een tekstvak en waarom tekstvak‑vormen maken?

Een tekstvak is een container die opgemaakte tekst, afbeeldingen of andere vormen kan bevatten. Het gebruik van **create text box** in je automatisering stelt je in staat zwevende inhoud overal op een pagina te plaatsen, perfect voor annotaties, bijschriften of decoratieve elementen zonder de hoofd‑documentstroom te wijzigen.

## Hoe een vorm toe te voegen

Voordat we in de code duiken, zorg ervoor dat Aspose.Words voor Java in je project is opgenomen. Als je het nog niet hebt toegevoegd, download dan de bibliotheek van de officiële site:

[Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### Vormen toevoegen aan documenten

## Hoe meerdere vormen te groeperen

Een `GroupShape` stelt je in staat meerdere individuele vormen als één eenheid te behandelen—handig om ze samen te verplaatsen of te roteren.

### Een GroupShape invoegen

Hieronder staat een volledig voorbeeld dat een groep maakt, twee verschillende vormen toevoegt en de groep in het document invoegt.

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

## Hoe een tekstvak te maken (create text box)

### Een tekstvakvorm invoegen

De `insertShape`‑methode maakt het eenvoudig om een tekstvak toe te voegen. Het voorbeeld hieronder toont twee manieren om een tekstvak te positioneren en te roteren.

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

## Hoe de beeldverhouding van een vorm in te stellen

### Beeldverhouding beheren

Soms moet een vorm worden uitgerekt zonder de oorspronkelijke verhoudingen te behouden. Het volgende fragment toont hoe je de beeldverhouding van een afbeeldingvorm kunt ontgrendelen.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Hoe een vorm in een tabelcel te plaatsen

### Een vorm in een tabelcel plaatsen

Hieronder staat een stapsgewijs voorbeeld dat een tabel opbouwt, en vervolgens een watermerkvorm invoegt die relatief ten opzichte van de pagina is gepositioneerd maar ook in een cel kan worden geplaatst.

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

## Werken met SmartArt‑vormen

### SmartArt‑vormen detecteren

Je kunt programmatisch SmartArt‑objecten in een document vinden met de `hasSmartArt()`‑methode.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### SmartArt‑tekeningen bijwerken

Zodra je SmartArt‑vormen hebt gevonden, kun je hun interne tekeningsgegevens vernieuwen met `updateSmartArtDrawing()`.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Conclusie

In deze gids hebben we behandeld hoe je **create text box** objecten maakt, meerdere vormen groepeert, beeldverhoudingen aanpast, vormen in tabelcellen embedt, watermerken toevoegt en werkt met SmartArt‑diagrammen met Aspose.Words voor Java. Deze technieken stellen je in staat om programmatically rijk opgemaakte, interactieve Word‑documenten te bouwen.

## Veelgestelde vragen

### Wat is Aspose.Words voor Java?

Aspose.Words voor Java is een Java‑bibliotheek die ontwikkelaars in staat stelt Word‑documenten programmatically te maken, te wijzigen en te converteren. Het biedt een breed scala aan functies en tools voor het werken met documenten in verschillende formaten.

### Hoe kan ik Aspose.Words voor Java downloaden?

Je kunt Aspose.Words voor Java downloaden van de Aspose‑website via deze link: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### Wat zijn de voordelen van het gebruiken van documentvormen?

Documentvormen voegen visuele elementen en interactiviteit toe aan je documenten, waardoor ze boeiender en informatiever worden. Met vormen kun je bijschriften, knoppen, afbeeldingen, watermerken en meer maken, wat de algehele gebruikerservaring verbetert.

### Kan ik het uiterlijk van vormen aanpassen?

Ja, je kunt het uiterlijk van vormen aanpassen door hun eigenschappen te wijzigen, zoals grootte, positie, rotatie en vulkleur. Aspose.Words voor Java biedt uitgebreide opties voor vormaanpassing.

### Is Aspose.Words voor Java compatibel met SmartArt?

Ja, Aspose.Words voor Java ondersteunt SmartArt‑vormen, waardoor je kunt werken met complexe diagrammen en grafische elementen in je documenten.

## Veelgestelde vragen

**Q: Kan ik een tekstvak combineren met een afbeelding binnen dezelfde vorm?**  
A: Ja. Voeg een afbeelding toe aan de tekstvakvorm met `builder.insertImage()` nadat je de vorm hebt gemaakt, en pas vervolgens de lay-out naar behoefte aan.

**Q: Hoe zorg ik ervoor dat een watermerk achter alle documentinhoud verschijnt?**  
A: Stel de `WrapType` van de vorm in op `NONE` en pas `RelativeHorizontalPosition` en `RelativeVerticalPosition` aan naar `PAGE`. Dit positioneert het watermerk achter de hoofd‑stroom.

**Q: Is het mogelijk om een gegroepeerde vorm in Word te animeren?**  
A: Hoewel Aspose.Words vormen kan maken en groeperen, worden animatiefuncties niet ondersteund omdat ze afhankelijk zijn van de UI‑mogelijkheden van Word.

**Q: Welke versie van Aspose.Words is vereist voor SmartArt‑ondersteuning?**  
A: Detectie en bijwerken van SmartArt zijn beschikbaar vanaf Aspose.Words 20.9 voor Java en later.

**Q: Handelt de bibliotheek grote documenten met veel vormen efficiënt?**  
A: Ja. Gebruik `doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010)` of hoger om de prestaties te verbeteren bij documenten met veel vormen.

---

**Laatst bijgewerkt:** 2026-02-16  
**Getest met:** Aspose.Words voor Java 24.12  
**Auteur:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}