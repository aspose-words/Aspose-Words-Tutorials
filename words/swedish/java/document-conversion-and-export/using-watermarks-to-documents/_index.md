---
date: 2025-12-18
description: Lär dig hur du lägger till vattenstämpel i dokument med Aspose.Words
  för Java, inklusive exempel på bildvattenstämpel, ändra vattenstämpelns färg, ställ
  in vattenstämpelns transparens och ta bort vattenstämpel från dokumentet.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Hur man lägger till vattenstämpel i dokument med Aspose.Words för Java
url: /sv/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hur man lägger till vattenstämpel i dokument med Aspose.Words för Java

## Introduktion till att lägga till vattenstämplar i dokument med Aspose.Words för Java

I den här handledningen kommer du att lära dig **hur man lägger till vattenstämpel** i Word-dokument med Aspose.Words för Java. Vattenstämplar är ett snabbt sätt att märka en fil som konfidentiell, utkast eller godkänd, och de kan vara textbaserade eller bildbaserade. Vi kommer att gå igenom hur du installerar biblioteket, skapar text- och bildvattenstämplar, anpassar deras utseende (inklusive att ändra vattenstämpelns färg och ställa in vattenstämpelns transparens), och även tar bort en vattenstämpel från ett dokument när den inte längre behövs.

## Snabba svar
- **Vad är en vattenstämpel?** Ett halvtransparent lager (text eller bild) som visas bakom dokumentets huvudinnehåll.  
- **Kan jag lägga till flera vattenstämplar?** Ja – skapa flera `Shape`-objekt och lägg till var och en i önskade sektioner.  
- **Hur ändrar jag vattenstämpelns färg?** Justera `Color`-egenskapen i `TextWatermarkOptions`.  
- **Finns det ett exempel på bildvattenstämpel?** Se avsnittet “Adding Image Watermarks” nedan.  
- **Behöver jag en licens för att ta bort en vattenstämpel?** En giltig Aspose.Words-licens krävs för produktionsanvändning.

## Installera Aspose.Words för Java

Innan vi börjar lägga till vattenstämplar i dokument måste vi installera Aspose.Words för Java. Följ dessa steg för att komma igång:

1. Ladda ner Aspose.Words för Java från [here](https://releases.aspose.com/words/java/).  
2. Lägg till Aspose.Words för Java-biblioteket i ditt Java-projekt.  
3. Importera de nödvändiga klasserna i din Java-kod.

Nu när vi har biblioteket installerat kan vi gå vidare till själva skapandet av vattenstämpeln.

## Lägga till textvattenstämplar

Textvattenstämplar är ett vanligt val när du vill lägga till textinformation i dina dokument. Så här kan du lägga till en textvattenstämpel med Aspose.Words för Java:

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

**Varför detta är viktigt:** Genom att justera `setFontFamily`, `setFontSize` och `setColor` kan du **ändra vattenstämpelns färg** för att matcha ditt varumärke, och `setSemitransparent(true)` låter dig **ställa in vattenstämpelns transparens** för en subtil effekt.

## Lägga till bildvattenstämplar

Förutom textvattenstämplar kan du också lägga till bildvattenstämplar i dina dokument. Nedan är ett **exempel på bildvattenstämpel** som visar hur du bäddar in en PNG‑logotyp eller stämpel:

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

Du kan upprepa detta block med olika bilder eller positioner för att **lägga till flera vattenstämplar** i en enda fil.

## Anpassa vattenstämplar

Du kan anpassa vattenstämplar genom att justera deras utseende och position. För textvattenstämplar kan du ändra teckensnitt, storlek, färg och layout. För bildvattenstämplar kan du ändra storlek, rotation och justering som demonstrerats i de tidigare exemplen.

## Ta bort vattenstämplar

Om du behöver **ta bort vattenstämpelns** innehåll i ett dokument, itererar följande kod genom alla former och tar bort de som identifieras som vattenstämplar:

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

## Vanliga användningsområden & tips

- **Konfidentiella utkast:** Applicera en halvtransparent textvattenstämpel som “CONFIDENTIAL”.  
- **Varumärkesprofilering:** Använd en bildvattenstämpel som innehåller ditt företagslogotyp.  
- **Sektion‑specifika vattenstämplar:** Loopa igenom `doc.getSections()` och lägg till en vattenstämpel endast i de sektioner du väljer.  
- **Prestandatips:** Återanvänd samma `TextWatermarkOptions`-instans när du applicerar samma vattenstämpel på många dokument.

## Vanliga frågor

### Hur kan jag ändra teckensnittet för en textvattenstämpel?

För att ändra teckensnittet för en textvattenstämpel, modifiera `setFontFamily`-egenskapen i `TextWatermarkOptions`. Till exempel:

```java
options.setFontFamily("Times New Roman");
```

### Kan jag lägga till flera vattenstämplar i ett enda dokument?

Ja, du kan lägga till flera vattenstämplar i ett dokument genom att skapa flera `Shape`-objekt med olika inställningar och lägga till dem i dokumentet.

### Är det möjligt att rotera en vattenstämpel?

Ja, du kan rotera en vattenstämpel genom att sätta `setRotation`-egenskapen i `Shape`-objektet. Positiva värden roterar vattenstämpeln medurs, och negativa värden roterar den moturs.

### Hur kan jag göra en vattenstämpel halvtransparent?

För att göra en vattenstämpel halvtransparent, sätt `setSemitransparent`-egenskapen till `true` i `TextWatermarkOptions`.

### Kan jag lägga till vattenstämplar i specifika sektioner av ett dokument?

Ja, du kan lägga till vattenstämplar i specifika sektioner av ett dokument genom att iterera genom sektionerna och lägga till vattenstämpeln i de önskade sektionerna.

---

**Senast uppdaterad:** 2025-12-18  
**Testat med:** Aspose.Words för Java 24.12  
**Författare:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}