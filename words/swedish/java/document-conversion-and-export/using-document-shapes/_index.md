---
date: 2025-12-14
description: Lär dig hur du **infogar bildform** med Aspose.Words för Java. Den här
  guiden visar hur du lägger till former, skapar textruteformer, placerar former i
  tabeller, ställer in formens bildförhållande och lägger till pratbubblor.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Använda dokumentformer i Aspose.Words för Java
url: /sv/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hur man **infoga bildform** med Aspose.Words för Java

I den här omfattande handledningen kommer du att upptäcka hur du **infogar bildform**‑objekt i Word-dokument med hjälp av Aspose.Words för Java. Oavsett om du bygger rapporter, marknadsföringsmaterial eller interaktiva formulär, låter former dig lägga till förklarande textrutor, knappar, textrutor, vattenstämplar och till och med SmartArt. Vi går igenom varje steg, förklarar varför du skulle använda en viss form och tillhandahåller färdiga kodexempel.

## Snabba svar
- **Vad är det primära sättet att lägga till en form?** Använd `DocumentBuilder.insertShape` eller skapa en `Shape`‑instans och lägg till den i dokumentträdet.  
- **Kan jag infoga en bild som en form?** Ja – anropa `builder.insertImage` och behandla sedan den returnerade `Shape` som vilken annan som helst.  
- **Hur behåller jag en forms bildförhållande?** Sätt `shape.setAspectRatioLocked(true)` eller `false` beroende på dina behov.  
- **Är det möjligt att gruppera former?** Absolut – omslut dem i en `GroupShape` och infoga gruppen som en enda nod.  
- **Fungerar Smart-diagram med Aspose.Words?** Ja, du kan upptäcka och uppdatera SmartArt‑former programatiskt.

## Vad är **infoga bildform**?
En *bildform* är ett visuellt element som innehåller raster‑ eller vektorgrafik i ett Word‑dokument. I Aspose.Words representeras en bild av ett `Shape`‑objekt, vilket ger dig full kontroll över storlek, position, rotation och omslag.

## Varför använda former i dina dokument?
- **Visuell effekt:** Former drar uppmärksamhet till viktig information.  
- **Interaktivitet:** Knappar och förklarande textrutor kan länkas till URL:er eller bokmärken.  
- **Layoutflexibilitet:** Positionera grafik exakt med absoluta eller relativa koordinater.  
- **Automation:** Generera komplexa layouter utan manuell redigering.

## Förutsättningar
- Java Development Kit (JDK 8 eller högre)  
- Aspose.Words för Java‑biblioteket (ladda ner från den officiella webbplatsen)  
- Grundläggande kunskap om Java och objektorienterad programmering  

Du kan ladda ner biblioteket här: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

## Hur man **lägger till form** – Infogar en GroupShape
En `GroupShape` låter dig behandla flera former som en enhet. Detta är användbart för att flytta eller formatera flera element tillsammans.

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

## Skapa **textruteform**
En textruta är en behållare som kan innehålla formaterad text. Du kan också rotera den för ett dynamiskt utseende.

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

## Ställ in **formens bildförhållande**
Ibland behöver du att en form sträcks fritt, andra gånger vill du behålla dess ursprungliga proportioner. Att kontrollera bildförhållandet är enkelt.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Placera **form i tabell**
Att bädda in en form i en tabellcell kan vara praktiskt för rapportlayouter. Exemplet nedan skapar en tabell och infogar sedan en vattenstämpel‑liknande form som sträcker sig över hela sidan.

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

## Lägg till **förklarande textruteform**
En förklarande textruteform är perfekt för att markera anteckningar eller varningar. Medan koden ovan redan visar en `ACCENT_BORDER_CALLOUT_1`, kan du byta `ShapeType` till någon annan förklarande variant för att passa din design.

## Arbeta med SmartArt-former

### Upptäck SmartArt-former
SmartArt-diagram kan identifieras programatiskt, vilket gör att du kan bearbeta eller ersätta dem efter behov.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Uppdatera SmartArt-ritningar
När de har upptäckts kan du uppdatera SmartArt-grafiken för att återspegla eventuella dataförändringar.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Vanliga problem & tips
- **Formen visas inte:** Se till att formen infogas efter mål‑noden med `builder.insertNode`.  
- **Oväntad rotation:** Kom ihåg att rotation appliceras kring formens centrum; justera `setLeft`/`setTop` vid behov.  
- **Bildförhållande låst:** Som standard låser många former sitt bildförhållande; anropa `setAspectRatioLocked(false)` för att sträcka fritt.  
- **SmartArt-upptäckt misslyckas:** Verifiera att du använder en Aspose.Words-version som stödjer SmartArt (v24+).

## Vanliga frågor

**Q: Vad är Aspose.Words för Java?**  
A: Aspose.Words för Java är ett Java‑bibliotek som låter utvecklare skapa, modifiera och konvertera Word‑dokument programatiskt. Det erbjuder ett brett utbud av funktioner och verktyg för att arbeta med dokument i olika format.

**Q: Hur kan jag ladda ner Aspose.Words för Java?**  
A: Du kan ladda ner Aspose.Words för Java från Aspose‑webbplatsen genom att följa denna länk: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

**Q: Vilka är fördelarna med att använda dokumentformer?**  
A: Dokumentformer lägger till visuella element och interaktivitet i dina dokument, vilket gör dem mer engagerande och informativa. Med former kan du skapa förklarande textrutor, knappar, bilder, vattenstämplar och mer, vilket förbättrar den övergripande användarupplevelsen.

**Q: Kan jag anpassa utseendet på former?**  
A: Ja, du kan anpassa utseendet på former genom att justera deras egenskaper såsom storlek, position, rotation och fyllningsfärg. Aspose.Words för Java erbjuder omfattande alternativ för anpassning av former.

**Q: Är Aspose.Words för Java kompatibel med SmartArt?**  
A: Ja, Aspose.Words för Java stödjer SmartArt‑former, vilket gör att du kan arbeta med komplexa diagram och grafik i dina dokument.

---

**Senast uppdaterad:** 2025-12-14  
**Testad med:** Aspose.Words för Java 24.12 (senaste)  
**Författare:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}