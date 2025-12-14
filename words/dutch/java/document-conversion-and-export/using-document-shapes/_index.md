---
date: 2025-12-14
description: Leer hoe u **een afbeeldingsvorm kunt invoegen** met Aspose.Words voor
  Java. Deze gids laat zien hoe u vormen toevoegt, tekstvakvormen maakt, vormen in
  tabellen plaatst, de beeldverhouding van vormen instelt en aanroepvormen toevoegt.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Documentvormen gebruiken in Aspose.Words voor Java
url: /nl/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hoe **afbeeldingsvorm invoegen** met Aspose.Words for Java

In deze uitgebreide tutorial ontdek je hoe je **afbeeldingsvorm invoegen** objecten in Word-documenten kunt gebruiken met Aspose.Words for Java. Of je nu rapporten, marketingmateriaal of interactieve formulieren maakt, vormen laten je callouts, knoppen, tekstvakken, watermerken en zelfs SmartArt toevoegen. We lopen elke stap door, leggen uit waarom je een bepaalde vorm zou gebruiken, en bieden kant‑klaar code‑fragmenten.

## Quick Answers
- **Wat is de primaire manier om een vorm toe te voegen?** Gebruik `DocumentBuilder.insertShape` of maak een `Shape`‑instantie aan en voeg deze toe aan de documentboom.  
- **Kan ik een afbeelding als vorm invoegen?** Ja – roep `builder.insertImage` aan en behandel de geretourneerde `Shape` als elke andere.  
- **Hoe houd ik de beeldverhouding van een vorm?** Stel `shape.setAspectRatioLocked(true)` of `false` in, afhankelijk van je behoeften.  
- **Is het mogelijk vormen te groeperen?** Absoluut – plaats ze in een `GroupShape` en voeg de groep als één knooppunt in.  
- **Werken SmartArt‑diagrammen met Aspose.Words?** Ja, je kunt SmartArt‑vormen programmatically detecteren en bijwerken.

## Wat is **afbeeldingsvorm invoegen**?
Een *image shape* is een visueel element dat raster‑ of vector‑graphics bevat binnen een Word‑document. In Aspose.Words wordt een afbeelding weergegeven door een `Shape`‑object, waarmee je volledige controle hebt over grootte, positie, rotatie en omloop.

## Waarom vormen gebruiken in je documenten?
- **Visuele impact:** Vormen trekken de aandacht naar belangrijke informatie.  
- **Interactiviteit:** Knoppen en callouts kunnen worden gekoppeld aan URL's of bladwijzers.  
- **Lay-out flexibiliteit:** Plaats graphics nauwkeurig met absolute of relatieve coördinaten.  
- **Automatisering:** Genereer complexe lay-outs zonder handmatige bewerking.

## Prerequisites
- Java Development Kit (JDK 8 of hoger)  
- Aspose.Words for Java‑bibliotheek (download van de officiële site)  
- Basiskennis van Java en object‑georiënteerd programmeren  

Je kunt de bibliotheek hier downloaden: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

## Hoe **vorm toevoegen** – Een GroupShape invoegen
Een `GroupShape` stelt je in staat meerdere vormen als één eenheid te behandelen. Dit is handig om meerdere elementen samen te verplaatsen of op te maken.

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

## Maak **tekstvakvorm**
Een tekstvak is een container die opgemaakte tekst kan bevatten. Je kunt het ook roteren voor een dynamische uitstraling.

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

## Stel **beeldverhouding van vorm** in
Soms moet een vorm vrij worden uitgerekt, andere keren wil je de oorspronkelijke verhoudingen behouden. Het regelen van de beeldverhouding is eenvoudig.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Plaats **vorm in tabel**
Een vorm in een tabelcel insluiten kan handig zijn voor rapportlay-outs. Het voorbeeld hieronder maakt een tabel en voegt vervolgens een watermerk‑achtige vorm in die de hele pagina beslaat.

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

## Voeg **callout‑vorm** toe
Een callout‑vorm is perfect om notities of waarschuwingen te markeren. Terwijl de bovenstaande code al een `ACCENT_BORDER_CALLOUT_1` laat zien, kun je de `ShapeType` vervangen door een andere callout‑variant die bij je ontwerp past.

## Werken met SmartArt‑vormen

### SmartArt‑vormen detecteren
SmartArt‑diagrammen kunnen programmatically worden geïdentificeerd, zodat je ze kunt verwerken of vervangen indien nodig.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### SmartArt‑tekeningen bijwerken
Zodra ze zijn gedetecteerd, kun je de SmartArt‑graphics vernieuwen om eventuele gegevenswijzigingen weer te geven.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Veelvoorkomende problemen & tips
- **Vorm verschijnt niet:** Zorg ervoor dat de vorm wordt ingevoegd na het doelknooppunt met `builder.insertNode`.  
- **Onverwachte rotatie:** Onthoud dat rotatie wordt toegepast rond het midden van de vorm; pas `setLeft`/`setTop` aan indien nodig.  
- **Beeldverhouding vergrendeld:** Standaard vergrendelen veel vormen hun beeldverhouding; roep `setAspectRatioLocked(false)` aan om vrij te rekken.  
- **SmartArt-detectie mislukt:** Controleer of je een Aspose.Words‑versie gebruikt die SmartArt ondersteunt (v24+).

## Veelgestelde vragen

**Q: Wat is Aspose.Words for Java?**  
A: Aspose.Words for Java is een Java‑bibliotheek die ontwikkelaars in staat stelt Word‑documenten programmatically te maken, wijzigen en converteren. Het biedt een breed scala aan functies en tools voor het werken met documenten in verschillende formaten.

**Q: Hoe kan ik Aspose.Words for Java downloaden?**  
A: Je kunt Aspose.Words for Java downloaden van de Aspose‑website via deze link: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

**Q: Wat zijn de voordelen van het gebruik van documentvormen?**  
A: Documentvormen voegen visuele elementen en interactiviteit toe aan je documenten, waardoor ze aantrekkelijker en informatiever worden. Met vormen kun je callouts, knoppen, afbeeldingen, watermerken en meer maken, wat de algehele gebruikerservaring verbetert.

**Q: Kan ik het uiterlijk van vormen aanpassen?**  
A: Ja, je kunt het uiterlijk van vormen aanpassen door hun eigenschappen zoals grootte, positie, rotatie en vulkleur te wijzigen. Aspose.Words for Java biedt uitgebreide opties voor vormaanpassing.

**Q: Is Aspose.Words for Java compatibel met SmartArt?**  
A: Ja, Aspose.Words for Java ondersteunt SmartArt‑vormen, zodat je kunt werken met complexe diagrammen en graphics in je documenten.

---

**Laatst bijgewerkt:** 2025-12-14  
**Getest met:** Aspose.Words for Java 24.12 (latest)  
**Auteur:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}