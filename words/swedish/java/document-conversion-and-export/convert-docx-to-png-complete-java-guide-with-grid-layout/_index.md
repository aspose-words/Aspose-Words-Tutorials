---
category: general
date: 2026-06-27
description: Konvertera DOCX till PNG snabbt med Aspose.Words för Java. Lär dig att
  exportera alla sidor som PNG och ställa in rader per sida och kolumner per sida
  på en gång.
draft: false
keywords:
- convert docx to png
- export all pages png
- how to set rows per page
- how to set columns per page
language: sv
og_description: Konvertera DOCX till PNG i Java med Aspose.Words. Denna guide visar
  hur du exporterar alla sidor som PNG och konfigurerar rader per sida och kolumner
  per sida.
og_title: Konvertera DOCX till PNG – Java Grid Export-handledning
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Convert DOCX to PNG quickly using Aspose.Words for Java. Learn to export
    all pages PNG and set rows per page and columns per page in one go.
  headline: Convert DOCX to PNG – Complete Java Guide with Grid Layout
  type: TechArticle
tags:
- Aspose.Words
- Java
- DOCX
- PNG
- Image conversion
title: Konvertera DOCX till PNG – Komplett Java-guide med rutnätslayout
url: /sv/java/document-conversion-and-export/convert-docx-to-png-complete-java-guide-with-grid-layout/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Konvertera DOCX till PNG – Komplett Java‑guide med rutnätlayout

Har du någonsin undrat hur man **konverterar DOCX till PNG** utan att manuellt spara varje sida? Du är inte ensam. Många utvecklare stöter på problem när de behöver en enda bild som visar flera sidor samtidigt, särskilt för förhandsgransknings‑miniatyrer eller snabb delning.  

God nyhet: med Aspose.Words för Java kan du **exportera alla sidor som PNG** i ett enda steg, och du kan dessutom bestämma **hur du anger rader per sida** och **hur du anger kolumner per sida**. I den här handledningen går vi igenom hela processen, från att ladda ett Word‑dokument till att skapa en prydlig rutnätsbild.

## Vad den här handledningen täcker

Vi börjar med att lista förutsättningarna, sedan delar vi upp lösningen i tydliga steg. När du är klar kommer du att kunna:

* Ladda vilken `.docx`‑fil som helst från disk.  
* Konfigurera `ImageSaveOptions` för att exportera **alla sidor som PNG** på en gång.  
* Definiera ett 2 × 2‑rutnät (eller vilket som helst) med **hur du anger rader per sida** och **hur du anger kolumner per sida**.  
* Spara resultatet som en enda PNG‑fil som du kan bädda in var som helst.

Inga externa skript, inga kommandorads‑akrobatik—bara ren Java‑kod som du kan klistra in i ditt projekt.

### Förutsättningar

| Krav | Varför det är viktigt |
|------|-----------------------|
| Java 8 or newer | Aspose.Words 23.9+ kräver minst Java 8. |
| Aspose.Words for Java JAR | Tillhandahåller klasserna `Document` och `ImageSaveOptions`. |
| A `.docx` file to test | Källfilen du ska konvertera. |
| IDE or build tool (Maven/Gradle) | För att kompilera och köra exemplet. |

Om du redan har dessa punkter ikryssade, bra—låt oss dyka in.

## Steg 1: Ställ in ditt projekt och importera Aspose.Words

Först, lägg till Aspose.Words‑beroendet. Om du använder Maven, klistra in detta i din `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

För Gradle ser det ut så här:

```groovy
implementation 'com.aspose:aspose-words:23.9'
```

När biblioteket finns på classpath kan du börja koda. Import‑satsen är enkel:

```java
import com.aspose.words.*;
```

> **Proffstips:** Förvara dina Aspose‑jar‑filer i en `libs/`‑mapp och lägg till dem i byggsökvägen om du inte använder en beroendehanterare.

## Steg 2: Ladda källdokumentet

Att ladda en DOCX är så enkelt som att peka `Document`‑konstruktorn på en filsökväg. Detta är det första konkreta steget i **convert docx to png**.

```java
// Step 2: Load the source document
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

Byt ut `YOUR_DIRECTORY` mot den faktiska mappen där din Word‑fil finns. Om filen inte hittas kastar Aspose ett `FileNotFoundException`, så se till att sökvägen är korrekt.

## Steg 3: Skapa Image Save Options för PNG

Nu talar vi om för Aspose att vi vill ha PNG‑utdata. Klassen `ImageSaveOptions` låter oss finjustera konverteringen, inklusive den avgörande flaggan **export all pages png**.

```java
// Step 3: Create image save options for PNG format
ImageSaveOptions pngOptions = new ImageSaveOptions(SaveFormat.PNG);
```

Vid detta tillfälle är options‑objektet klart, men vi har ännu inte sagt *hur* vi ska hantera flera sidor.

## Steg 4: Exportera alla sidor som PNG

Som standard skulle Aspose spara varje sida som en separat fil. För att samla dem i en fil, sätt `pageCount` till `0`. I Aspose‑terminologi betyder `0` “alla sidor”.

```java
// Step 4: Export all pages (0 means all pages)
pngOptions.setPageCount(0);
```

Nu vet biblioteket att du avser att **export all pages PNG** på en gång. Om du bara ville ha de första tre sidorna skulle du använda `pngOptions.setPageCount(3);`.

## Steg 5: Ordna sidor i ett rutnätslayout

Här kommer magin med **how to set rows per page** och **how to set columns per page** in i spel. Vi ber Aspose att lägga ut sidorna i ett rutnät, liknande ett kontaktark.

```java
// Step 5: Arrange pages in a grid layout
pngOptions.setPageLayout(ImageSaveOptions.PageLayout.GRID);
```

`GRID`‑layouten instruerar motorn att mosaikera sidor horisontellt och vertikalt enligt de dimensioner vi kommer att ange härnäst.

## Steg 6: Definiera rutnätsdimensioner (Rader × Kolumner)

Du kan välja vilken kombination som helst som passar dina behov. Exemplet nedan skapar ett 2 × 2‑rutnät, men du kan enkelt byta till 3 × 4 eller till och med en enda rad.

```java
// Step 6: Define the grid dimensions (2 rows × 2 columns)
pngOptions.setRowsPerPage(2);      // how to set rows per page
pngOptions.setColumnsPerPage(2);   // how to set columns per page
```

Om du har fler sidor än celler kommer Aspose automatiskt att fortsätta på nästa rad. Om du har färre sidor förblir de tomma cellerna transparenta.

## Steg 7: Spara dokumentet som en enda PNG‑bild

Till sist instruerar vi Aspose att skriva den kombinerade bilden till disk. Filnamnet kan vara vad du vill; behåll bara `.png`‑ändelsen.

```java
// Step 7: Save the document as a single PNG image using the grid layout
document.save("YOUR_DIRECTORY/Grid.png", pngOptions);
```

När programmet är klart hittar du `Grid.png` i samma mapp. Öppna den, så bör du se de första fyra sidorna i `input.docx` ordnade i ett snyggt 2 × 2‑rutnät.

### Förväntat resultat

| Sida | Position i rutnät |
|------|-------------------|
| 1    | Överst‑vänster |
| 2    | Överst‑höger |
| 3    | Nederst‑vänster |
| 4    | Nederst‑höger |

Om ditt källdokument har fler än fyra sidor, kommer den femte sidan att börja på en ny rad (om du ökar `rowsPerPage`) eller utelämnas (om du behåller rutnätet på 2 × 2). PNG‑filen behåller de ursprungliga sidornas dimensioner, så den slutliga bildstorleken blir `rows × pageHeight` gånger `columns × pageWidth`.

## Fullständigt fungerande exempel

Nedan är det kompletta, färdiga Java‑programmet. Kopiera‑klistra in det i en klass som heter `DocxToPngGrid.java`, justera sökvägarna och kör.

```java
import com.aspose.words.*;

public class DocxToPngGrid {
    public static void main(String[] args) {
        try {
            // 1️⃣ Load the DOCX file
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // 2️⃣ Prepare PNG save options
            ImageSaveOptions pngOptions = new ImageSaveOptions(SaveFormat.PNG);
            pngOptions.setPageCount(0);                     // export all pages PNG
            pngOptions.setPageLayout(ImageSaveOptions.PageLayout.GRID);

            // 3️⃣ Configure grid (2 rows × 2 columns)
            pngOptions.setRowsPerPage(2);   // how to set rows per page
            pngOptions.setColumnsPerPage(2); // how to set columns per page

            // 4️⃣ Save the combined image
            document.save("YOUR_DIRECTORY/Grid.png", pngOptions);

            System.out.println("Conversion complete! Check Grid.png.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

Kör det med:

```bash
javac -cp "path/to/aspose-words-23.9.jar" DocxToPngGrid.java
java -cp ".:path/to/aspose-words-23.9.jar" DocxToPngGrid
```

Du bör se `Conversion complete!` skrivet i konsolen, och en `Grid.png`‑fil dyka upp i mål‑mappen.

## Vanliga frågor & kantfall

**Vad händer om jag behöver ett annat bildformat?**  
Byt ut `SaveFormat.PNG` mot `SaveFormat.JPEG` eller `SaveFormat.TIFF`. Resten av koden förblir oförändrad.

**Kan jag styra bildkvaliteten?**  
Ja. För JPEG kan du anropa `pngOptions.setJpegQuality(90);`. PNG har ingen kvalitetsinställning eftersom den är förlustfri.

**Hur är det med stora dokument?**  
När du hanterar många sidor kan den resulterande PNG‑filen bli enorm (minnesmässigt). Överväg att öka `rowsPerPage`/`columnsPerPage` eller dela upp utdata i flera bilder.

**Behöver jag en licens?**  
Aspose.Words fungerar i evalueringsläge utan licens, men den genererade PNG‑filen kommer att innehålla ett vattenmärke. Köp en licens för att ta bort det.

## Proffstips för produktionsanvändning

* **Återanvänd `ImageSaveOptions`** – Om du konverterar många dokument i en batch, skapa options‑objektet en gång och återanvänd det för att undvika extra objektallokering.  
* **Strömma utdata** – Istället för att spara till en fil kan du skriva till en `ByteArrayOutputStream` och skicka PNG‑filen via HTTP.  
* **Trådsäkerhet** – `Document`‑instanser är inte trådsäkra, så skapa en ny `Document` per tråd.  
* **Minnesprofilering** – För PDF‑filer med över 100 sidor, övervaka heap‑användning; du kan behöva öka JVM‑flaggan `-Xmx`.

## Slutsats

Vi har just gått igenom ett praktiskt sätt att **convert docx to png** med Aspose.Words för Java, och täckt allt från att ladda filen till att konfigurera **export all pages png**, samt visa **how to set rows per page** och **how to set columns per page** för ett rutnätslayout. Den slutgiltiga enkla PNG‑filen ger dig en kompakt visuell ögonblicksbild av ett flersidigt Word‑dokument—perfekt för förhandsgranskningar, e‑postbilagor eller snabb delning.

Redo för nästa utmaning? Prova att lägga till ett vattenmärke på varje sida, eller experimentera med olika rutnätsstorlekar för att passa din UI‑design. Du kan också kedja denna konvertering med en PDF‑generator för att producera flermålsrapporter i en pipeline.

Om du stöter på problem, lämna en kommentar nedan—lycka till med kodandet!  

![exempel på konvertering av docx till png](placeholder.png){alt="exempel på konvertering av docx till png"}

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Cómo convertir DOCX a PNG en Java – Aspose.Words](/words/spanish/java/document-converting/converting-documents-images/)
- [Wie man DOCX in PNG in Java konvertiert – Aspose.Words](/words/german/java/document-converting/converting-documents-images/)
- [Comment convertir DOCX en PNG en Java – Aspose.Words](/words/french/java/document-converting/converting-documents-images/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}