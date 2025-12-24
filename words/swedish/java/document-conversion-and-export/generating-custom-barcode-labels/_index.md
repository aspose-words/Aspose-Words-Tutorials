---
date: 2025-12-10
description: Lär dig hur du skapar anpassade streckkodsetiketter med Aspose.Words
  för Java. Denna steg‑för‑steg‑guide visar hur du bäddar in streckkoder i Word‑dokument.
linktitle: Generating Custom Barcode Labels
second_title: Aspose.Words Java Document Processing API
title: Skapa anpassade streckkodsetiketter i Aspose.Words för Java
url: /sv/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Generera anpassade streckkodsetiketter i Aspose.Words för Java

## Introduktion till att generera anpassade streckkoder i Aspose.Words för Java

Streckkoder är oumbärliga i moderna applikationer—oavsett om du hanterar lager, skriver ut biljetter eller skapar ID‑kort. I den här handledningen kommer du att **generera anpassade streckkodsetiketter** och bädda in dem direkt i ett Word‑dokument med hjälp av gränssnittet `IBarcodeGenerator`. Vi går igenom varje steg, från att konfigurera miljön till att infoga streckkodsbilden, så att du kan börja använda streckkoder i dina Java‑projekt omedelbart.

## Snabba svar
- **Vad lär den här handledningen ut?** Hur man genererar anpassade streckkodsetiketter och bäddar in dem i en Word‑fil med Aspose.Words för Java.  
- **Vilken streckkodstyp används i exemplet?** QR‑kod (du kan byta ut den mot vilken stödd typ som helst).  
- **Behöver jag en licens?** En tillfällig licens krävs för obegränsad åtkomst under utveckling.  
- **Vilken Java‑version krävs?** JDK 8 eller högre.  
- **Kan jag ändra streckkodens stor eller färger?** Ja—justera inställningarna i `BarcodeParameters` och `BarcodeGenerator`.

## Förutsättningar

Innan vi börjar koda, se till att du har följande:

- Java Development Kit (JDK): Version 8 eller senare.  
- Aspose.Words för Java‑biblioteket: [Ladda ner här](https://releases.aspose.com/words/java/).  
- Aspose.BarCode för Java‑biblioteket: [Ladda ner här](https://releases.aspose.com/).  
- Integrerad utvecklingsmiljö (IDE): IntelliJ IDEA, Eclipse eller någon annan IDE du föredrar.  
- Tillfällig licens: Skaffa en [tillfällig licens](https://purchase.aspose.com/temporary-license/) för obegränsad åtkomst.

## Importera paket

Vi kommer att använda Aspose.Words‑ och Aspose.BarCode‑biblioteken. Importera följande paket i ditt projekt:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Dessa importeringar ger oss åtkomst till API‑et för streckkodsgenerering samt Word‑dokumentklasserna vi behöver.

## Steg 1: Skapa en hjälparklass för streckkodoperationer

För att hålla huvudkoden ren kapslar vi vanliga hjälpfunktioner—såsom **konvertera twips till pixlar** och **hex‑färgkonvertering**—i en hjälparklass.

### Kod

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

- `twipsToPixels` – Word mäter dimensioner i **twips**; den här metoden konverterar dem till skärm‑pixlar, vilket är praktiskt när du behöver ange streckkodens bildstorlek exakt.  
- `convertColor` – Omvandlar en hexadecimal sträng (t.ex. `"FF0000"` för röd) till ett `java.awt.Color`‑objekt, så att du kan **infoga streckkod** med anpassade förgrunds‑ och bakgrundsfärger.

## Steg 2: Implementera den anpassade streckkodsgeneratorn

Nu implementerar vi gränssnittet `IBarcodeGenerator`. Denna klass ansvarar för att **generera QR‑kod‑bilder** som Aspose.Words kan bädda in.

### Kod

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

- `getBarcodeImage` skapar en instans av `BarcodeGenerator`, tillämpar färgerna som anges via `BarcodeParameters` och returnerar slutligen en `BufferedImage`.  
- Metoden hanterar även fel genom att returnera en platshållarbild, så att skapandet av Word‑dokumentet aldrig kraschar.

## Steg 3: Generera en streckkod och **bädda in streckkod i Word**

Med generatorn klar kan vi nu producera en streckkodsbild och **infoga den i ett Word‑dokument**.

### Kod

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

1. **Dokumentinitialisering** – Skapar ett nytt `Document` (eller så kan du ladda en befintlig mall).  
2. **Streckkodparametrar** – Definierar streckkodstyp (`QR`), värdet som ska kodas samt förgrunds‑/bakgrundsfärger.  
3. **Bildinfogning** – `builder.insertImage` placerar den genererade streckkoden i önskad storlek (200 × 200 pixlar). Detta är kärnan i **hur man infogar streckkod** i en Word‑fil.  
4. **Spara** – Det slutgiltiga dokumentet, `CustomBarcodeLabels.docx`, innehåller den inbäddade streckkoden, klar för utskrift eller distribution.

## Varför generera anpassade streckkodsetiketter med Aspose.Words?

- **Full kontroll** över streckkodens utseende (typ, storlek, färger).  
- **Sömlös integration** – ingen behov av mellanfiler; streckkoden genereras i minnet och infogas direkt.  
- **Plattformsoberoende** – fungerar på alla OS som stödjer Java, vilket gör den idealisk för server‑sidig dokumentgenerering.  
- **Skalbar** – du kan loopa över en datakälla för att skapa hundratals personliga etiketter i ett enda körning.

## Vanliga problem & felsökning

| Symptom | Trolig orsak | Åtgärd |
|---------|--------------|--------|
| Streckkoden visas tom | `BarcodeParameters`‑färgerna är identiska (t.ex. svart på svart) | Kontrollera värdena för `foregroundColor` och `backgroundColor`. |
| Bilden blir förvrängd | Fel pixel‑dimensioner skickade till `insertImage` | Justera bredd‑/höjdförhållandena eller använd `twipsToPixels`‑konvertering för exakt storlek. |
| Fel: ej stöd för streckkodstyp | En typ som inte känns igen av `CustomBarcodeGeneratorUtils.getBarcodeEncodeType` | Säkerställ att streckkodstyp‑strängen matchar en av de stödda `EncodeTypes` (t.ex. `"QR"`, `"CODE128"`). |

## Vanliga frågor

**Q: Kan jag använda Aspose.Words för Java utan licens?**  
A: Ja, men då finns vissa begränsningar. Skaffa en [tillfällig licens](https://purchase.aspose.com/temporary-license/) för full funktionalitet.

**Q: Vilka typer av streckkoder kan jag generera?**  
A: Aspose.BarCode stödjer QR, Code 128, EAN‑13 och många andra format. Se [dokumentationen](https://reference.aspose.com/words/java/) för en komplett lista.

**Q: Hur kan jag ändra streckkodens storlek?**  
A: Justera bredd‑ och höjdförhållandena i `builder.insertImage`, eller använd `twipsToPixels` för att konvertera Word‑måttenheter till pixlar.

**Q: Är det möjligt att använda anpassade teckensnitt för streckkodstexten?**  
A: Ja, du kan anpassa textens teckensnitt via `CodeTextParameters`‑egenskapen i `BarcodeGenerator`.

**Q: Vart kan jag få hjälp om jag stöter på problem?**  
A: Besök [supportforumet](https://forum.aspose.com/c/words/8/) för hjälp från Aspose‑gemenskapen och ingenjörer.

## Slutsats

Genom att följa stegen ovan vet du nu hur du **genererar anpassade streckkodsbilder** och **bäddar in streckkod i Word**‑dokument med Aspose.Words för Java. Denna teknik är flexibel nog för lageretiketter, evenemangsbiljetter eller alla scenarier där en streckkod måste vara en del av ett genererat dokument. Experimentera med olika streckkodstyper och stilalternativ för att anpassa dem efter dina specifika affärsbehov.

---

**Senast uppdaterad:** 2025-12-10  
**Testat med:** Aspose.Words för Java 24.12, Aspose.BarCode för Java 24.12  
**Författare:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}