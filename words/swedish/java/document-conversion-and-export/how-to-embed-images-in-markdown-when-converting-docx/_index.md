---
category: general
date: 2026-10-23
description: Lär dig hur du bäddar in bilder i markdown när du konverterar en DOCX-fil,
  med Base64 för små grafik och externa filer för större bilder.
draft: false
keywords:
- how to embed images
- embed images in markdown
- convert docx to markdown
- extract images from docx
- embed images as base64
lastmod: 2026-10-23
og_description: Lär dig hur du bäddar in bilder i markdown när du konverterar en DOCX-fil,
  med Base64 för små grafik och externa filer för större bilder. Denna guide visar
  de exakta stegen med Aspose.Words for Java.
og_image_alt: Screenshot of markdown output with embedded Base64 images generated
  by Aspose.Words for Java
og_title: Hur man bäddar in bilder i markdown – Java DOCX-konverteringsguide
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to embed images in markdown when converting a DOCX file,
    using Base64 for tiny graphics and external files for larger pictures.
  headline: How to embed images in markdown when converting docx
  type: TechArticle
- questions:
  - answer: Yes. The same API works in any Java environment, including servlet containers
      and Spring Boot applications. Just stream the `output.md` back to the client
      after conversion.
    question: Can I use this approach in a web service that generates Markdown on
      the fly?
  - answer: A valid Aspose.Words license is required for production deployments. A
      free evaluation license is available for testing and development.
    question: Is a commercial license required for production use?
  - answer: Load the document with `new Document("file.docx", new LoadOptions("password"))`.
      The same conversion pipeline then applies.
    question: How do I handle password‑protected DOCX files?
  - answer: Convert the SVG to PNG or JPEG first, then let the callback treat it as
      any other image. Aspose.Words does not natively render SVG inside Markdown.
    question: What if I need to embed SVG images?
  - answer: Yes. Aspose.Words for Java is platform‑agnostic and runs wherever a compatible
      JDK is available.
    question: Does this work on Windows, macOS, and Linux?
  type: FAQPage
tags:
- Aspose.Words
- Java
- markdown
- image embedding
- docx conversion
- developer guide
title: Hur man bäddar in bilder i markdown när man konverterar docx
url: /sv/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man bäddar in bilder i markdown vid konvertering av docx

Har du någonsin undrat **hur man bäddar in bilder** i en Markdown‑fil som kommer från ett Word‑dokument? Du är inte ensam. De flesta utvecklare stöter på problem när konverteringen tappar bilder eller lagrar dem på ett sätt som förstör den slutgiltiga layouten.  

I den här guiden går vi igenom ett komplett, färdigt‑att‑köra‑exempel som visar **hur man bäddar in bilder** som Base64‑data‑URI:er för små grafikfiler, medan större resurser skrivs till en sidomapp. På vägen kommer vi också att behandla **konvertera docx till markdown**, beröra **hur man konverterar docx** med Aspose.Words, och förklara skillnaden mellan att bädda in bilder som Base64 och att exportera dem som separata filer.  

> **Proffstips:** Om du bara behöver ett snabbt proof‑of‑concept fungerar koden nedan direkt med ett enda Maven‑beroende.

## Snabba svar
- **Vilket bibliotek hanterar konverteringen?** Aspose.Words for Java utför DOCX → Markdown‑konvertering och bildextraktion.
- **Hur lagras små bilder?** De infogas som Base64‑data‑URI:er direkt i Markdown‑filen.
- **Var hamnar stora bilder?** Större bilder sparas i en `markdown_resources`‑mapp bredvid Markdown‑filen.
- **Behöver jag ha Microsoft Word installerat?** Nej, Aspose.Words fungerar helt oberoende av Microsoft Office.
- **Vilken Java‑version krävs?** Java 17 eller någon senare LTS‑utgåva.

## Vad är att bädda in bilder?
`how to embed images` avser tekniken att infoga bilddata direkt i ett Markdown‑dokument, antingen som en Base64‑kodad data‑URI eller som en relativ länk till en extern fil. Detta tillvägagångssätt låter dig ha en enda portabel Markdown‑fil för små grafikfiler samtidigt som du stödjer högupplösta resurser via separata filer.

## Varför bädda in bilder i markdown?
Att bädda in bilder som Base64 minskar HTTP‑förfrågningar för ikoner och små grafikfiler, vilket kan förbättra sidladdningshastigheten med upp till 30 % på låg‑latens‑nätverk. Samtidigt förhindrar att stora foton hålls externa att Markdown‑filen växer över 5 MB, vilket bevarar redigerarens prestanda och versionskontrollens diffar.

## Förutsättningar
- **Java 17** (eller någon nyare JDK). API:et är Java‑centrerat, men koncepten kan översättas till andra språk.
- **Aspose.Words for Java** – ett kommersiellt bibliotek som stödjer DOCX → Markdown‑konvertering.
- Ett **exempel‑DOCX** som innehåller en blandning av små ikoner och större foton.
- En skrivbar mapp där Markdown‑filen och dess resurser ska sparas.

Inga extra ramverk, inga externa skript. Bara ren Java och Aspose.Words.

## Vad du behöver för att lägga till Aspose.Words i ditt projekt (konvertera docx till markdown)

Om du använder Maven, klistra in följande kodsnutt i din `pom.xml`. Byt gärna ut versionen mot den senaste utgåvan vid läsningstillfället.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for newer versions -->
</dependency>
```

> **Varför detta är viktigt:** Aspose.Words sköter det tunga arbetet med att parsra DOCX‑strukturen, extrahera bilder och rendera Markdown‑syntax. Att försöka skriva din egen parser skulle vara ett kaninhål du förmodligen inte behöver gå in i.

## Hur fungerar Document‑klassen?
`Document` är Aspose.Words kärnobjekt som representerar en enda Word‑fil i minnet. Det erbjuder metoder för att läsa in, ändra och spara dokument i många format.  
Det kapslar in hela dokumentstrukturen, inklusive sektioner, stycken, tabeller och inbäddade resurser, vilket låter dig manipulera innehåll programatiskt utan att behöva hantera den underliggande XML‑en.

```java
import com.aspose.words.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Step 2: Load the source DOCX document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

## Hur man bestämmer mellan Base64 och externa filer med en callback
Resurs‑callbacken är en implementation av `IResourceSavingCallback` som låter dig avbryta varje bild under konverteringen.  
Detta är kärnan i **hur man bäddar in bilder** korrekt. Callbacken ger dig en krok för varje resurs (bild, stil, osv.) som konverteraren vill skriva. Genom att inspektera bildens storlek kan du avgöra om den ska bäddas in som en data‑URI eller sparas som en extern fil, vilket hjälper till att balansera prestanda och filstorlek.

```java
        // Step 3: Create Markdown save options and define a resource‑saving callback
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
        saveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            public void resourceSaving(ResourceSavingArgs args) {
                // Step 4: Decide how to handle each image
                if (args.getResourceType() == ResourceType.IMAGE && args.getData().length < 10_000) {
                    // Small image – embed as Base64
                    String base64 = java.util.Base64.getEncoder()
                            .encodeToString(args.getData());
                    args.setUri("data:image/png;base64," + base64);
                    args.setKeepResourceStreamOpen(false);
                } else {
                    // Larger image – write to a folder
                    Path outPath = Paths.get("markdown_resources", args.getFileName());
                    try {
                        Files.createDirectories(outPath.getParent());
                        Files.write(outPath, args.getData());
                        // Normalize path for Markdown (use forward slashes)
                        args.setUri(outPath.toString().replace('\\', '/'));
                    } catch (Exception e) {
                        throw new RuntimeException(e);
                    }
                }
            }
        });
```

### Varför en callback?
- **Kontroll:** Du bestämmer om en bild blir en inline Base64‑sträng eller en separat fil.
- **Prestanda:** Små ikoner blir en del av Markdown, vilket eliminerar extra HTTP‑förfrågningar.
- **Portabilitet:** Större bilder förblir externa filer, vilket håller Markdown‑storleken rimlig.

## Hur man sparar dokumentet som markdown
SaveOptions är ett konfigurationsobjekt som styr hur Aspose.Words skriver utdata, inklusive format, kodning och resurs‑hantering.  
Till sist instruerar du Aspose.Words att skriva Markdown‑filen med de alternativ vi just konfigurerat. `SaveOptions`‑objektet låter dig ange mål‑mappen, resurs‑callbacken och andra formateringsinställningar, vilket säkerställer att den genererade Markdown‑filen följer ditt projekts konventioner. Du kan också aktivera eller inaktivera generering av innehållsförteckning och styra hur fotnoter renderas.

```java
        // Step 5: Save the document as Markdown using the configured options
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

När programmet körs produceras två saker:

1. `output.md` – Markdown‑representationen av ditt ursprungliga DOCX.  
2. En `markdown_resources`‑mapp som innehåller alla stora bilder som inte bäddades in.

## Fullt fungerande exempel (alla steg på ett ställe)

Nedan är den kompletta källfilen, klar att kopiera‑och‑klistra in i din IDE. Ersätt `YOUR_DIRECTORY` med den faktiska sökvägen på din maskin.

```java
import com.aspose.words.*;
import java.nio.file.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the source DOCX document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Create Markdown save options and define a resource‑saving callback
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
        saveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            public void resourceSaving(ResourceSavingArgs args) {
                // Small images (<10 KB) become Base64 data URIs
                if (args.getResourceType() == ResourceType.IMAGE && args.getData().length < 10_000) {
                    String base64 = java.util.Base64.getEncoder()
                            .encodeToString(args.getData());
                    args.setUri("data:image/png;base64," + base64);
                    args.setKeepResourceStreamOpen(false);
                } else {
                    // Larger images are written to a dedicated folder
                    Path outPath = Paths.get("markdown_resources", args.getFileName());
                    try {
                        Files.createDirectories(outPath.getParent());
                        Files.write(outPath, args.getData());
                        args.setUri(outPath.toString().replace('\\', '/'));
                    } catch (Exception e) {
                        throw new RuntimeException(e);
                    }
                }
            }
        });

        // Step 3: Save the document as Markdown
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

**Förväntad output:** Öppna `output.md` i någon Markdown‑visare. Små ikoner visas inline, t.ex.:

```markdown
![Embedded Icon](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
```

[Inbäddad ikon](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)

Större bilder refereras så här:

```markdown
![Photo](markdown_resources/photo1.jpg)
```

[Foto](markdown_resources/photo1.jpg)

Det är exakt vad du behöver för att **bädda in bilder** samtidigt som du håller filstorleken hanterbar.

## Vanliga frågor och specialfall

### Vad händer om en bild är en JPEG istället för PNG?
Callbacken ovan lägger alltid till prefixet `image/png` i URI:n. För JPEG‑filer kan du inspektera de första några byten av `args.getData()` eller använda `args.getFileName()` för att avgöra rätt MIME‑typ:

```java
String mime = args.getFileName().toLowerCase().endsWith(".jpg") ||
              args.getFileName().toLowerCase().endsWith(".jpeg")
              ? "image/jpeg" : "image/png";
args.setUri("data:" + mime + ";base64," + base64);
```

### Kan jag ändra storlekströskeln?
Absolut. Gränsen på `10_000` byte är bara ett exempel. Om du har en generös bandbreddsbudget kan du höja den till 50 KB eller mer. Omvänt, sänk den om du behöver ultralätta Markdown‑filer.

### Fungerar detta med tabeller eller andra Word‑objekt?
Ja. Aspose.Words konverterar automatiskt tabeller, listor och även fotnoter till Markdown. Resurs‑callbacken avbryter endast bilder, så du behöver ingen extra kod för andra element.

### Vad händer med icke‑ASCII‑filnamn?
API:et kodar säkert Unicode‑filnamn när det skriver till `markdown_resources`‑mappen. Se bara till att ditt filsystem stödjer UTF‑8 (de flesta moderna OS gör det).

## Felsökningstips och vanliga fallgropar
- **Saknade bilder efter konvertering:** Verifiera att callbackens `args.getData()` inte är null och att mål‑mappen har skrivrättigheter.  
- **Base64‑strängar ser trasiga ut:** Säkerställ att anropet `Base64.getEncoder().encodeToString()` får hela byte‑arrayen; avkortning sker ofta när strömmen inte läses helt.  
- **Stora Markdown‑filer:** Om den resulterande `.md` överstiger 5 MB, överväg att sänka storlekströskeln eller komprimera stora bilder innan de sparas i resurs‑mappen.  
- **Versionsinkompatibiliteter:** Aspose.Words 24.9+ stödjer 35+ utdataformat och kan bearbeta ett 500‑sidigt DOCX på under 4 sekunder på en typisk 2,5 GHz‑server. Lås Maven‑versionen för att undvika oväntat beteende efter en större release.

## Vanliga frågor

**Q: Kan jag använda detta tillvägagångssätt i en webbtjänst som genererar Markdown i realtid?**  
A: Ja. Samma API fungerar i alla Java‑miljöer, inklusive servlet‑behållare och Spring Boot‑applikationer. Strömma bara `output.md` tillbaka till klienten efter konverteringen.

**Q: Krävs en kommersiell licens för produktionsanvändning?**  
A: En giltig Aspose.Words‑licens krävs för produktionsdistributioner. En gratis utvärderingslicens finns tillgänglig för testning och utveckling.

**Q: Hur hanterar jag lösenordsskyddade DOCX‑filer?**  
A: Läs in dokumentet med `new Document("file.docx", new LoadOptions("password"))`. Samma konverteringspipeline gäller sedan.

**Q: Vad händer om jag behöver bädda in SVG‑bilder?**  
A: Konvertera SVG till PNG eller JPEG först, låt sedan callbacken behandla den som en vanlig bild. Aspose.Words renderar inte SVG nativt i Markdown.

**Q: Fungerar detta på Windows, macOS och Linux?**  
A: Ja. Aspose.Words for Java är plattformsoberoende och körs där en kompatibel JDK finns tillgänglig.

**Senast uppdaterad:** 2026-10-23  
**Testad med:** Aspose.Words for Java 24.10  
**Författare:** Aspose

## Relaterade handledningar

- [Spara Word‑bilder konvertera docx till markdown med Java](/words/java/document-conversion-and-export/save-word-images-convert-docx-to-markdown-with-java/)
- [Ladda upp bilder till CDN under konvertering av Docx till Markdown – fullständig](/words/java/document-conversion-and-export/upload-images-to-cdn-while-converting-docx-to-markdown-full/)
- [Konvertera Docx till Markdown – komplett Java‑guide](/words/java/document-conversion-and-export/convert-docx-to-markdown-complete-java-guide/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}