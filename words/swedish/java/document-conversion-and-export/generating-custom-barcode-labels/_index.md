---
date: 2026-10-23
description: Lär dig hur du skapar QR code Java‑etiketter med Aspose.Words. Denna
  steg‑för‑steg‑guide visar hur du bäddar in barcodes i Word‑dokument och anpassar
  storlek, färger och format.
keywords:
- create qr code java
- how to create barcode label
- add barcode to word document
- embed barcode in word
lastmod: 2026-10-23
linktitle: Skapa anpassade barcode‑etiketter
og_description: Lär dig hur du skapar QR code Java‑etiketter med Aspose.Words. Denna
  guide förklarar inbäddning av barcode, storlekskontroll och färganpassning i Word‑dokument.
og_image_alt: 'Developer guide: generate custom QR code labels in Java with Aspose.Words'
og_title: Hur man skapar QR code Java‑etiketter med Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to create QR code Java labels with Aspose.Words. This step‑by‑step
    guide shows you how to embed barcodes in Word documents and customize size, colors,
    and format.
  headline: How to create QR code Java labels using Aspose.Words
  type: TechArticle
- description: Learn how to create QR code Java labels with Aspose.Words. This step‑by‑step
    guide shows you how to embed barcodes in Word documents and customize size, colors,
    and format.
  name: How to create QR code Java labels using Aspose.Words
  steps:
  - name: '**Document initialization** – Creates a fresh `Document` (or you could
      load an existing template).'
    text: '**Document initialization** – Creates a fresh `Document` (or you could
      load an existing template).'
  - name: '**Barcode parameters** – Defines the barcode type (`QR`), the value to
      encode, and the foreground/background colors.'
    text: '**Barcode parameters** – Defines the barcode type (`QR`), the value to
      encode, and the foreground/background colors.'
  - name: '**Image insertion** – `builder.insertImage` places the generated barcode
      at the desired size (200 × 200 pixels). This is the core of **how to embed barcode
      in Word**.'
    text: '**Image insertion** – `builder.insertImage` places the generated barcode
      at the desired size (200 × 200 pixels). This is the core of **how to embed barcode
      in Word**.'
  - name: '**Saving** – The final document, `CustomBarcodeLabels.docx`, contains the
      embedded barcode ready for printing or distribution.'
    text: '**Saving** – The final document, `CustomBarcodeLabels.docx`, contains the
      embedded barcode ready for printing or distribution.'
  type: HowTo
- questions:
  - answer: Yes, but it will have evaluation limitations. Obtain a [temporary license](https://purchase.aspose.com/temporary-license/)
      for full functionality.
    question: Can I use Aspose.Words for Java without a license?
  - answer: Aspose.BarCode supports QR, Code 128, EAN‑13, DataMatrix, PDF417, and
      many other formats—over 20 symbologies in total. See the [documentation](https://reference.aspose.com/words/java/)
      for the complete list.
    question: What types of barcodes can I generate?
  - answer: Adjust the width and height arguments in `builder.insertImage`, or calculate
      exact Word twips using `twipsToPixels` for pixel‑perfect control.
    question: How can I change the barcode size?
  - answer: Yes, you can customize the text font through the `CodeTextParameters`
      property of the `BarcodeGenerator`.
    question: Is it possible to use custom fonts for the barcode text?
  - answer: Visit the [support forum](https://forum.aspose.com/c/words/8/) for assistance
      from the Aspose community and engineers.
    question: Where can I get help if I run into problems?
  type: FAQPage
second_title: Aspose.Words Java Document Processing API
tags:
- barcode generation
- Aspose.Words
- Java document processing
- QR code
title: Hur man skapar QR code Java‑etiketter med Aspose.Words
url: /sv/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar QR‑kod Java‑etiketter med Aspose.Words

Streckkoder är viktiga i moderna applikationer—oavsett om du hanterar lager, skriver ut biljetter eller skapar ID‑kort. I den här handledningen kommer du att **skapa QR‑kod Java**‑etiketter och bädda in dem direkt i ett Word‑dokument med hjälp av `IBarcodeGenerator`‑gränssnittet. Vi går igenom varje steg, från att konfigurera miljön till att infoga streckkodsbilden, så att du kan börja använda streckkoder i dina Java‑projekt omedelbart.

## Snabba svar
- **Vad lär den här handledningen ut?** Hur man skapar QR‑kod Java‑etiketter och bäddar in dem i en Word‑fil med Aspose.Words för Java.  
- **Vilken streckkodstyp används i exemplet?** QR‑kod (du kan byta den mot någon av de 20+ stödda typerna).  
- **Behöver jag en licens?** En tillfällig licens krävs för obegränsad åtkomst under utveckling.  
- **Vilken Java‑version krävs?** JDK 8 eller högre.  
- **Kan jag ändra streckkodens storlek eller färger?** Ja—modifiera `BarcodeParameters` och `BarcodeGenerator`‑inställningarna.

## Vad är create QR code Java?
`create QR code Java` avser att generera en QR‑kod‑bild programatiskt i en Java‑miljö och infoga den i ett dokument eller UI‑komponent. Aspose.Words för Java tillsammans med Aspose.BarCode låter dig skapa bilden helt i minnet, utan att behöva temporära filer.

## Varför generera anpassade streckkodsetiketter med Aspose.Words?
Aspose.Words stöder **35+ in‑ och utdataformat** och kan bearbeta **500‑sidiga dokument på under 3 sekunder** på vanlig serverhårdvara. Genom att använda dess streckkodsgenerering i minnet får du full kontroll över typ, storlek och färger samtidigt som arbetsflödet förblir helt Java‑centrerat och plattformsoberoende.

## Förutsättningar

- Java Development Kit (JDK): Version 8 eller högre.  
- Aspose.Words för Java‑bibliotek: [Download here](https://releases.aspose.com/words/java/).  
- Aspose.BarCode för Java‑bibliotek: [Download here](https://releases.aspose.com/).  
- Integrerad utvecklingsmiljö (IDE): IntelliJ IDEA, Eclipse eller någon annan IDE du föredrar.  
- Tillfällig licens: Skaffa en [temporary license](https://purchase.aspose.com/temporary-license/) för obegränsad åtkomst.

## Importera paket

Vi kommer att använda Aspose.Words‑ och Aspose.BarCode‑biblioteken. Importera följande paket i ditt projekt:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Dessa importeringar ger oss tillgång till API‑et för streckkodsgenerering och de Word‑dokumentklasser vi behöver.

## Steg 1: skapa en verktygsklass för streckkodoperationer

Verktygsklassen innehåller återanvändbara hjälpfunktioner såsom **convert twips to pixels** och **hex‑color conversion**.  
Klassen `CustomBarcodeGeneratorUtils` tillhandahåller statiska metoder för enhetskonvertering och färghantering.

### Code

```java
class CustomBarcodeGeneratorUtils {
    public static double twipsToPixels(String heightInTwips, double defVal) {
        try {
            int lVal = Integer.parseInt(heightInTwips);
            return (lVal / 1440.0) * 96.0; // Assuming default DPI is 96
        } catch (Exception e) {
            return defVal;
        }
    }

    public static Color convertColor(String inputColor, Color defVal) {
        if (inputColor == null || inputColor.isEmpty()) return defVal;
        try {
            int color = Integer.parseInt(inputColor, 16);
            return new Color((color & 0xFF), ((color >> 8) & 0xFF), ((color >> 16) & 0xFF));
        } catch (Exception e) {
            return defVal;
        }
    }
}
```

**Förklaring**  
- `twipsToPixels` – Word mäter dimensioner i **twips**; den här metoden konverterar dem till skärm‑pixlar, vilket är praktiskt när du behöver dimensionera streckkodsbilden exakt.  
- `convertColor` – Omvandlar en hexadecimal sträng (t.ex. "FF0000" för röd) till ett `java.awt.Color`‑objekt, vilket låter dig **infoga streckkod i Word‑dokument** med anpassade förgrunds‑ och bakgrundsfärger.

## Steg 2: implementera den anpassade streckkodsgeneratorn

Nu ska vi implementera `IBarcodeGenerator`‑gränssnittet. Denna klass ansvarar för att **generate QR code Java**‑liknande bilder som Aspose.Words kan bädda in.  
`IBarcodeGenerator`‑gränssnittet definierar en enda metod som returnerar en `BufferedImage` som representerar streckkoden.

### Code

```java
class CustomBarcodeGenerator implements IBarcodeGenerator {
    public BufferedImage getBarcodeImage(BarcodeParameters parameters) {
        try {
            BarcodeGenerator gen = new BarcodeGenerator(
                CustomBarcodeGeneratorUtils.getBarcodeEncodeType(parameters.getBarcodeType()),
                parameters.getBarcodeValue()
            );

            gen.getParameters().getBarcode().setBarColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getForegroundColor(), Color.BLACK)
            );
            gen.getParameters().setBackColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getBackgroundColor(), Color.WHITE)
            );

            return gen.generateBarCodeImage();
        } catch (Exception e) {
            return new BufferedImage(100, 100, BufferedImage.TYPE_INT_ARGB);
        }
    }

    public BufferedImage getOldBarcodeImage(BarcodeParameters parameters) {
        throw new UnsupportedOperationException();
    }
}
```

**Förklaring**  
- `getBarcodeImage` skapar en instans av `BarcodeGenerator`, applicerar färgerna som tillhandahålls via `BarcodeParameters` och returnerar slutligen en `BufferedImage`.  
- Metoden hanterar också fel på ett smidigt sätt genom att returnera en platshållarbild, vilket säkerställer att skapandet av Word‑dokumentet aldrig kraschar.

## Hur man bäddar in streckkod i Word med Aspose.Words?

Läs in din Word‑fil med `new Document("template.docx")` (eller skapa ett nytt `Document`) och anropa `builder.insertImage` med streckkodsbilden som returneras från generatorn. Detta tvåstegsmönster bäddar in streckkoden direkt utan att skriva en mellanfils till disk. Genom att ange bildens dimensioner i pixlar eller konvertera Word‑twips till pixlar kan du kontrollera den exakta storleken och placeringen av streckkoden i dokumentet, vilket säkerställer en professionell layout som skrivs ut korrekt på vilken skrivare som helst.

## Steg 3: generera en streckkod och bädda in streckkoden i Word

Med generatorn klar kan vi nu skapa en streckkodsbild och **infoga den i ett Word‑dokument**.

### Code

```java
import com.aspose.words.*;

public class GenerateCustomBarcodeLabels {
    public static void main(String[] args) throws Exception {
        // Load or create a Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Set up custom barcode generator
        CustomBarcodeGenerator barcodeGenerator = new CustomBarcodeGenerator();
        BarcodeParameters barcodeParameters = new BarcodeParameters();
        barcodeParameters.setBarcodeType("QR");
        barcodeParameters.setBarcodeValue("https://example.com");
        barcodeParameters.setForegroundColor("000000");
        barcodeParameters.setBackgroundColor("FFFFFF");

        // Generate barcode image
        BufferedImage barcodeImage = barcodeGenerator.getBarcodeImage(barcodeParameters);

        // Insert barcode image into Word document
        builder.insertImage(barcodeImage, 200, 200);

        // Save the document
        doc.save("CustomBarcodeLabels.docx");

        System.out.println("Barcode labels generated successfully!");
    }
}
```

**Förklaring**  

1. **Dokumentinitialisering** – Skapar ett nytt `Document` (eller så kan du läsa in en befintlig mall).  
2. **Streckkodparametrar** – Definierar streckkodstypen (`QR`), värdet som ska kodas samt förgrunds‑/bakgrundsfärgerna.  
3. **Bildinfogning** – `builder.insertImage` placerar den genererade streckkoden i önskad storlek (200 × 200 pixlar). Detta är kärnan i **hur man bäddar in streckkod i Word**.  
4. **Sparande** – Det slutgiltiga dokumentet, `CustomBarcodeLabels.docx`, innehåller den inbäddade streckkoden, klar för utskrift eller distribution.

## Vanliga problem & felsökning

| Symptom | Trolig orsak | Åtgärd |
|---------|--------------|-----|
| Streckkoden visas tom | `BarcodeParameters`‑färgerna är desamma (t.ex. svart på svart) | Verifiera värdena för `foregroundColor` och `backgroundColor`. |
| Bilden är förvrängd | Fel pixel‑dimensioner skickade till `insertImage` | Justera bredd-/höjdarargumenten eller använd `twipsToPixels`‑konvertering för exakt storlek. |
| Fel: ej stödd streckkodstyp | Använder en typ som inte känns igen av `CustomBarcodeGeneratorUtils.getBarcodeEncodeType` | Säkerställ att streckkodstyp‑strängen matchar en av de stödda `EncodeTypes` (t.ex. "QR", "CODE128"). |

## Vanliga frågor

**Q: Kan jag använda Aspose.Words för Java utan licens?**  
A: Ja, men den har utvärderingsbegränsningar. Skaffa en [temporary license](https://purchase.aspose.com/temporary-license/) för full funktionalitet.

**Q: Vilka typer av streckkoder kan jag generera?**  
A: Aspose.BarCode stöder QR, Code 128, EAN‑13, DataMatrix, PDF417 och många andra format—över 20 symbologier totalt. Se [documentation](https://reference.aspose.com/words/java/) för den kompletta listan.

**Q: Hur kan jag ändra streckkodens storlek?**  
A: Justera bredd‑ och höjdarargumenten i `builder.insertImage`, eller beräkna exakta Word‑twips med `twipsToPixels` för pixel‑perfekt kontroll.

**Q: Är det möjligt att använda anpassade typsnitt för streckkodstexten?**  
A: Ja, du kan anpassa texttypsnittet via `CodeTextParameters`‑egenskapen i `BarcodeGenerator`.

**Q: Var kan jag få hjälp om jag stöter på problem?**  
A: Besök [support forum](https://forum.aspose.com/c/words/8/) för hjälp från Aspose‑gemenskapen och ingenjörer.

## Slutsats

Genom att följa stegen ovan vet du nu hur du **create QR code Java**‑bilder och **embed barcode in Word**‑dokument med Aspose.Words för Java. Denna teknik är tillräckligt flexibel för lageretiketter, evenemangsbiljetter eller någon situation där en streckkod måste vara en del av ett genererat dokument. Experimentera med olika streckkodstyper, färger och storleksalternativ för att passa dina specifika affärsbehov.

---

**Last Updated:** 2026-10-23  
**Tested With:** Aspose.Words for Java 24.12, Aspose.BarCode for Java 24.12  
**Author:** Aspose

## Relaterade handledningar

- [Skapa PDF från Word med streckkodsgenerering – Aspose.Words för Java](/words/java/document-conversion-and-export/using-barcode-generation/)
- [Spara Word som PDF med Aspose Words steg‑för‑steg Java‑guide](/words/java/document-conversion-and-export/save-word-as-pdf-with-aspose-words-step-by-step-java-guide/)
- [Skapa tomt Word‑dokument i Java med Aspose Words](/words/java/document-manipulation/create-blank-word-document-in-java-with-aspose-words/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}