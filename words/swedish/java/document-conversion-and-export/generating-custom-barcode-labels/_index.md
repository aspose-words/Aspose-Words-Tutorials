---
date: 2026-02-09
description: Skapa anpassade streckkodsetiketter med Aspose Barcode Java i Aspose.Words
  för Java. Lär dig hur du bäddar in streckkoder i Word-dokument och genererar QR‑kodexempel
  i Java.
linktitle: Generating Custom Barcode Labels
second_title: Aspose.Words Java Document Processing API
title: Skapa anpassade streckkodsetiketter med Aspose Barcode Java
url: /sv/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

.

Make sure to keep **bold**.

Also tables: translate headers and content.

Let's craft.

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Skapa anpassade streckkodsetiketter med Aspose Barcode Java

## Introduktion till att skapa anpassade streckkodsetiketter i Aspose.Words för Java

Streckkoder är avgörande i moderna applikationer, och **Aspose Barcode Java** gör det enkelt att skapa dem direkt i Word‑dokument. Oavsett om du behöver **embed barcode in Word**, generera en QR‑kod för en URL eller konvertera måttenheter, så guidar den här handledningen dig genom allt du behöver. Klar att dyka ner? Låt oss börja!

## Snabba svar
- **Vilket bibliotek skapar streckkoder i Java?** Aspose Barcode Java i kombination med Aspose.Words för Java.  
- **Vilken streckkodstyp demonstreras?** QR‑kod (generate qr code java).  
- **Hur konverterar jag twips till pixlar?** Använd den medföljande `twipsToPixels`‑metoden.  
- **Kan jag lägga till streckkod i en befintlig Word‑fil?** Ja – använd bara `DocumentBuilder.insertImage`‑metoden.  
- **Behöver jag en licens?** En tillfällig licens tar bort utvärderingsbegränsningarna.

## Vad är Aspose Barcode Java?
Aspose Barcode Java är ett kraftfullt API som låter utvecklare programatiskt generera ett brett spektrum av 1D‑ och 2D‑streckkoder (inklusive QR‑koder). När det kombineras med Aspose.Words för Java kan du **embed barcode in Word**‑dokument utan att lämna ditt Java‑miljö.

## Varför använda Aspose Barcode Java med Aspose.Words?
- **Full kontroll** över streckkodens utseende (färger, storlek, format).  
- **Sömlös integration** – streckkodsbilden kan infogas direkt i ett Word‑dokument.  
- **Plattformsoberoende** – fungerar på alla Java‑kompatibla plattformar.  
- **Utbyggbart** – du kan skapa hjälparklasser för att återanvända streckkodlogik i flera projekt.

## Förutsättningar

Innan vi börjar koda, se till att du har följande:

- Java Development Kit (JDK): Version 8 eller högre.  
- Aspose.Words för Java‑bibliotek: [Download here](https://releases.aspose.com/words/java/).  
- Aspose.BarCode för Java‑bibliotek: [Download here](https://releases.aspose.com/).  
- Integrated Development Environment (IDE): IntelliJ IDEA, Eclipse eller någon annan IDE du föredrar.  
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

Dessa importeringar gör att vi kan utnyttja streckkodsgenereringsfunktioner och integrera dem i Word‑dokument.

Låt oss dela upp uppgiften i hanterbara steg.

## Steg 1: Skapa en hjälparklass för streckkodoperationer

För att förenkla streckkod‑relaterade operationer skapar vi en hjälparklass med metoder för vanliga uppgifter som färgkonvertering och **convert twips to pixels**.

### Kod:

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

- `twipsToPixels` konverterar måttenheten som Word använder (twips) till skärm‑pixlar – en praktisk hjälpfunktion när du behöver exakt storlek.  
- `convertColor` översätter en hexadecimal färgsträng (t.ex. “FF0000”) till ett Java `Color`‑objekt, så att du kan anpassa streckkodens förgrund och bakgrund.

## Steg 2: Implementera den anpassade streckkodsgeneratorn

Vi implementerar `IBarcodeGenerator`‑gränssnittet så att Aspose.Words kan begära en streckkodsbild när den stöter på ett streckkodsfält.

### Kod:

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

- `getBarcodeImage` bygger en `BarcodeGenerator` med den **generate qr code java**‑typ du anger (QR i vårt exempel).  
- Den applicerar förgrunds‑ och bakgrundsfärger via hjälparmetoderna och returnerar den renderade bilden.  
- Fallback‑bilden säkerställer att programmet fortsätter även om streckkodsgenereringen misslyckas.

## Steg 3: Generera en streckkod och lägg till den i ett Word‑dokument

Nu sätter vi ihop allt: skapa ett dokument, generera en streckkod och **how to add barcode** till Word‑filen.

### Kod:

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

1. **Dokumentinitialisering** – skapar ett nytt `Document` (eller så kan du ladda ett befintligt .docx).  
2. **Streckkodparametrar** – definierar typen (`QR`), värdet och färgerna, vilket demonstrerar **generate qr code java**‑användning.  
3. **Bildinfogning** – `builder.insertImage` placerar streckkoden där du behöver den, vilket tydligt visar **how to add barcode** till en Word‑fil.  
4. **Spara** – det slutgiltiga dokumentet (`CustomBarcodeLabels.docx`) innehåller den inbäddade streckkoden, redo för utskrift eller distribution.

## Vanliga problem och lösningar

| Problem | Orsak | Åtgärd |
|-------|-------|-----|
| Streckkoden visas tom | Ogiltig färgsträng eller ej‑stödd streckkodstyp | Kontrollera hex‑färgformatet och använd en stödd typ (t.ex. QR, Code128). |
| Bildstorleken är fel | Felaktig pixelkonvertering | Använd `twipsToPixels` för att beräkna exakta dimensioner baserat på Words layout. |
| Licensundantag | Ingen giltig Aspose‑licens | Applicera en tillfällig eller köpt licens innan du kör koden. |

## Vanliga frågor

**Q: Kan jag använda Aspose.Words för Java utan licens?**  
A: Ja, men du får evalueringsbegränsningar. Skaffa en [temporary license](https://purchase.aspose.com/temporary-license/) för full funktionalitet.

**Q: Vilka typer av streckkoder kan jag generera?**  
A: Aspose.BarCode stödjer QR, Code 128, EAN‑13 och många fler. Se den officiella [documentation](https://reference.aspose.com/words/java/) för hela listan.

**Q: Hur kan jag ändra streckkodens storlek?**  
A: Justera bredd‑/höjdpunkterna i `builder.insertImage` eller ändra `XDimension` och `BarHeight`‑egenskaperna på `BarcodeGenerator`‑objektet.

**Q: Kan jag använda egna teckensnitt för den mänskligt läsbara delen av streckkoden?**  
A: Absolut. Använd egenskapen `CodeTextParameters` för att ange teckensnittsfamilj, storlek och stil.

**Q: Var kan jag få hjälp med Aspose.Words?**  
A: Besök [support forum](https://forum.aspose.com/c/words/8/) för community‑stöd och officiell support.

---

**Senast uppdaterad:** 2026-02-09  
**Testat med:** Aspose.Words för Java 24.12, Aspose.BarCode för Java 24.12  
**Författare:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}