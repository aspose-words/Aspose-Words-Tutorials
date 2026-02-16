---
date: 2026-02-16
description: Lär dig hur du skapar textruta, lägger till ett vattenstämpelord, grupperar
  flera former, ställer in formens bildförhållande och placerar formen i en tabellcell
  med Aspose.Words för Java.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Hur man skapar en textruta och använder dokumentformer i Aspose.Words för Java
url: /sv/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

's" heading maybe keep same but translate.

Let's produce final content.{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Använda dokumentformer i Aspose.Words för Java

## Introduktion till att använda dokumentformer i Aspose.Words för Java

I den här omfattande guiden **kommer du att lära dig hur du skapar textlåda**‑objekt och andra kraftfulla former med Aspose.Words för Java. Former låter dig berika Word‑dokument med pratbubblor, knappar, vattenstämplar, SmartArt och mer—vilket gör dem visuellt tilltalande och interaktiva. Vi går igenom verkliga exempel, från att infoga en enkel textlåda till att gruppera flera former, ställa in bildförhållanden och placera former i tabellceller.

## Snabba svar
- **Vad är det primära sättet att lägga till en textlåda?** Använd `DocumentBuilder.insertShape(ShapeType.TEXT_BOX, …)`.
- **Kan jag gruppera former tillsammans?** Ja – skapa en `GroupShape` och lägg till underordnade former.
- **Hur låser eller låser jag upp en forms bildförhållande?** Anropa `shape.setAspectRatioLocked(true/false)`.
- **Är det möjligt att lägga till en vattenstämpel med en form?** Absolut – infoga en `Shape` med `TEXT_PLAIN_TEXT` och sätt dess fyllning/linje.
- **Fungerar SmartArt‑diagram med Aspose.Words?** Ja – upptäck med `shape.hasSmartArt()` och uppdatera via `shape.updateSmartArtDrawing()`.

## Vad är en textlåda och varför skapa textlåda‑former?

En textlåda är en behållare som kan innehålla formaterad text, bilder eller andra former. Genom att **skapa textlåda** i din automatisering kan du placera flytande innehåll var som helst på en sida, perfekt för anteckningar, pratbubblor eller dekorativa element utan att ändra huvuddokumentets flöde.

## Hur man lägger till en form

Innan vi dyker ner i koden, se till att Aspose.Words för Java är refererad i ditt projekt. Om du ännu inte har lagt till det, ladda ner biblioteket från den officiella webbplatsen:

[Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### Lägga till former i dokument

## Hur man grupperar flera former

En `GroupShape` låter dig behandla flera enskilda former som en enda enhet—användbart för att flytta eller rotera dem tillsammans.

### Infoga en GroupShape

Nedan är ett komplett exempel som skapar en grupp, lägger till två olika former och infogar gruppen i dokumentet.

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

## Hur man skapar en textlåda (create text box)

### Infoga en textlåda‑form

Metoden `insertShape` gör det enkelt att lägga till en textlåda. Exemplet nedan visar två sätt att positionera och rotera en textlåda.

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

## Hur man ställer in bildförhållandet för en form

### Hantera bildförhållande

Ibland behöver du en form som sträcks utan att bevara sina ursprungliga proportioner. Följande kodsnutt demonstrerar hur du låser upp bildförhållandet för en bildform.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Hur man placerar en form i en tabellcell

### Placera en form i en tabellcell

Nedan är ett steg‑för‑steg‑exempel som bygger en tabell, sedan infogar en vattenstämpelform som är positionerad relativt sidan men också kan placeras i en cell.

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

## Arbeta med SmartArt‑former

### Upptäcka SmartArt‑former

Du kan programatiskt hitta SmartArt‑objekt i ett dokument med metoden `hasSmartArt()`.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Uppdatera SmartArt‑ritningar

När du har lokaliserat SmartArt‑former kan du uppdatera deras interna ritningsdata med `updateSmartArtDrawing()`.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Slutsats

I den här guiden har vi gått igenom hur du **skapar textlåda**‑objekt, grupperar flera former, justerar bildförhållanden, bäddar in former i tabellceller, lägger till vattenstämplar och arbetar med SmartArt‑diagram med Aspose.Words för Java. Dessa tekniker ger dig möjlighet att programatiskt bygga rikt formatterade, interaktiva Word‑dokument.

## Vanliga frågor

### Vad är Aspose.Words för Java?

Aspose.Words för Java är ett Java‑bibliotek som låter utvecklare skapa, modifiera och konvertera Word‑dokument programatiskt. Det erbjuder ett brett utbud av funktioner och verktyg för att arbeta med dokument i olika format.

### Hur kan jag ladda ner Aspose.Words för Java?

Du kan ladda ner Aspose.Words för Java från Aspose‑webbplatsen via följande länk: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### Vilka är fördelarna med att använda dokumentformer?

Dokumentformer lägger till visuella element och interaktivitet i dina dokument, vilket gör dem mer engagerande och informativa. Med former kan du skapa pratbubblor, knappar, bilder, vattenstämplar och mer, vilket förbättrar den totala användarupplevelsen.

### Kan jag anpassa utseendet på former?

Ja, du kan anpassa utseendet på former genom att justera deras egenskaper såsom storlek, position, rotation och fyllningsfärg. Aspose.Words för Java erbjuder omfattande alternativ för form‑anpassning.

### Är Aspose.Words för Java kompatibel med SmartArt?

Ja, Aspose.Words för Java stödjer SmartArt‑former, vilket gör att du kan arbeta med komplexa diagram och grafik i dina dokument.

## Vanliga frågor och svar

**Q: Kan jag kombinera en textlåda med en bild i samma form?**  
A: Ja. Infoga en bild i textlåda‑formen med `builder.insertImage()` efter att du skapat formen, och justera sedan layouten efter behov.

**Q: Hur säkerställer jag att en vattenstämpel visas bakom allt dokumentinnehåll?**  
A: Sätt formens `WrapType` till `NONE` och justera dess `RelativeHorizontalPosition` och `RelativeVerticalPosition` till `PAGE`. Detta placerar vattenstämpeln bakom huvudflödet.

**Q: Är det möjligt att animera en grupperad form i Word?**  
A: Även om Aspose.Words kan skapa och gruppera former, stöds inte animationsfunktioner eftersom de bygger på Word‑gränssnittets möjligheter.

**Q: Vilken version av Aspose.Words krävs för SmartArt‑stöd?**  
A: Upptäckt och uppdatering av SmartArt är tillgängligt från Aspose.Words 20.9 för Java och senare.

**Q: Hanterar biblioteket stora dokument med många former effektivt?**  
A: Ja. Använd `doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010)` eller högre för att förbättra prestanda i dokument med många former.

---

**Senast uppdaterad:** 2026-02-16  
**Testad med:** Aspose.Words för Java 24.12  
**Författare:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}