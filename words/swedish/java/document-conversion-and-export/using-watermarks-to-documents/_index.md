---
date: 2026-02-19
description: Lär dig hur du skapar dokument med vattenstämpel med Aspose.Words för
  Java och lägger till bildvattenstämpel i Java för professionellt utseende dokument.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Skapa dokument med vattenstämpel med Aspose.Words för Java
url: /sv/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Skapa dokument med vattenstämpel med Aspose.Words för Java

I den här handledningen kommer du att **skapa dokument med vattenstämpel** med hjälp av Aspose.Words for Java API. Vattenstämplar—oavsett om de är text eller bilder—hjälper dig att märka en fil som konfidentiell, utkast eller godkänd, och de kan appliceras programatiskt på vilket Word‑dokument som helst. Vi går igenom hur du installerar biblioteket, lägger till både text‑ och bildvattenstämplar, anpassar deras utseende och till och med tar bort dem när de inte längre behövs.

## Snabba svar
- **Vad gör en vattenstämpel?** Den lägger över text eller en bild på varje sida för att förmedla status eller varumärke.  
- **Vilket bibliotek lägger till vattenstämplar i Java?** Aspose.Words for Java erbjuder inbyggt stöd för vattenstämplar.  
- **Kan jag lägga till en bildvattenstämpel?** Ja—använd `Shape`‑klassen och `add image watermark java`‑metoden.  
- **Är vattenstämpeln halvgenomskinlig?** Du kan kontrollera opaciteten via `setSemitransparent` för textvattenstämplar.  
- **Behöver jag en licens?** En gratis provversion fungerar för testning; en kommersiell licens krävs för produktion.

## Vad är en vattenstämpel och varför använda den?

En vattenstämpel är ett svagt överlägg—textuell eller grafisk—som läggs till på varje sida i ett dokument. Den används ofta för att indikera **konfidentialitet**, **utkaststatus** eller **varumärkesprofilering** utan att ändra det underliggande innehållet. Att lägga till vattenstämplar programatiskt säkerställer konsistens över stora mängder filer och sparar tid jämfört med manuell redigering.

## Konfigurera Aspose.Words för Java

Innan vi börjar lägga till vattenstämplar, se till att biblioteket är redo i ditt projekt:

1. Ladda ner Aspose.Words for Java från [här](https://releases.aspose.com/words/java/).  
2. Lägg till den nedladdade JAR‑filen (eller Maven/Gradle‑beroendet) i ditt projekts classpath.  
3. Importera de nödvändiga klasserna i din Java‑källfil:

```java
import com.aspose.words.*;
import java.awt.Color;
import java.nio.file.*;
```

Nu när biblioteket är installerat, låt oss dyka ner i den faktiska vattenstämpelkoden.

## Så lägger du till en textvattenstämpel

Textvattenstämplar är idealiska för att märka ett dokument som ”CONFIDENTIAL” eller ”DRAFT”. Följande kodsnutt visar ett enkelt sätt att **skapa dokument med vattenstämpel** med `TextWatermarkOptions`.

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

### Anpassa textvattenstämpeln
- **Teckensnittsfamilj & storlek** – ändra `setFontFamily` och `setFontSize`.  
- **Färg** – använd valfri `java.awt.Color`.  
- **Layout** – välj `HORIZONTAL`, `DIAGONAL` osv.  
- **Transparens** – slå på `setSemitransparent(true)` för en ljusare effekt.

## Så lägger du till en bildvattenstämpel (add image watermark java)

Bildvattenstämplar är perfekta för logotyper eller anpassade grafik. Nedan är **add image watermark java**‑exemplet som infogar en PNG i mitten av varje sida.

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

### Tips för bildvattenstämplar
- **Ändra storlek** med `setWidth` / `setHeight` för att passa sidan.  
- **Position** kan centreras eller justeras till någon marginal med `RelativeHorizontalPosition` / `RelativeVerticalPosition`.  
- **Transparens** kan tillämpas genom att justera bildens alfa‑kanal innan den laddas.

## Så tar du bort vattenstämplar

När ett dokument inte längre behöver en vattenstämpel kan du ta bort den programatiskt. Koden nedan itererar genom alla former och tar bort de som innehåller ”Watermark” i sitt namn.

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

## Vanliga fallgropar och felsökning

- **Vattenstämpel saknas efter sparning** – se till att du anropar `doc.save()` efter att ha ställt in vattenstämpeln.  
- **Bild visas inte** – verifiera att bildsökvägen är korrekt och att filen är i ett stödformat (PNG, JPEG, BMP).  
- **Transparens tillämpas inte** – `setSemitransparent(true)` fungerar endast för textvattenstämplar; för bilder, redigera PNG‑filens alfa‑kanal.  
- **Flera sektioner** – om ditt dokument har flera sektioner, lägg till vattenstämpeln i varje sektionens kropp eller använd `doc.getWatermark().setText(...)` som applicerar globalt.

## Vanliga frågor

**Q: Hur kan jag ändra teckensnittet för en textvattenstämpel?**  
A: Ändra `setFontFamily`‑egenskapen i `TextWatermarkOptions`, t.ex. `options.setFontFamily("Times New Roman");`.

**Q: Kan jag lägga till flera vattenstämplar i ett enda dokument?**  
A: Ja. Skapa flera `Shape`‑objekt (för bilder) eller anropa `doc.getWatermark().setText(...)` med olika alternativ för varje vattenstämpel.

**Q: Är det möjligt att rotera en vattenstämpel?**  
A: För bildvattenstämplar, sätt rotationen på `Shape`‑objektet med `watermark.setRotation(angle)`. För textvattenstämplar, använd `setLayout`‑egenskapen (t.ex. `WatermarkLayout.DIAGONAL`).

**Q: Hur kan jag göra en vattenstämpel halvgenomskinlig?**  
A: Ställ in `options.setSemitransparent(true)` i `TextWatermarkOptions`. För bilder, justera bildens opacitet innan den laddas.

**Q: Kan jag lägga till vattenstämplar i specifika sektioner av ett dokument?**  
A: Ja. Iterera genom `doc.getSections()` och lägg till vattenstämpeln endast i de önskade sektionerna.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Senast uppdaterad:** 2026-02-19  
**Testat med:** Aspose.Words for Java 24.12 (latest)  
**Författare:** Aspose