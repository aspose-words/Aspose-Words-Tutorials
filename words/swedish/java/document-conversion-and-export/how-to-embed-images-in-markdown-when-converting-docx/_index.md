---
category: general
date: 2026-01-11
description: Lär dig hur du bäddar in bilder i Markdown när du konverterar en DOCX‑fil,
  använder Base64 för små bilder och sparar större resurser separat.
draft: false
keywords:
- how to embed images
- convert docx to markdown
- how to convert docx
- embed images as base64
- export word document markdown
language: sv
og_description: Lär dig hur du bäddar in bilder i Markdown när du konverterar en DOCX-fil,
  använder Base64 för små bilder och sparar större resurser separat.
og_title: Hur man bäddar in bilder i Markdown när man konverterar DOCX
tags:
- Aspose.Words
- Java
- Markdown
- Image Embedding
title: Hur man bäddar in bilder i Markdown när man konverterar DOCX
url: /sv/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så här bäddar du in bilder i Markdown vid konvertering av DOCX

Har du någonsin undrat **hur man bäddar in bilder** i en Markdown‑fil som härstammar från ett Word‑dokument? Du är inte ensam. De flesta utvecklare stöter på problem när konverteringen tappar bilder eller lagrar dem på ett sätt som förstör den slutgiltiga layouten.  

I den här guiden går vi igenom ett komplett, färdigt‑att‑köra exempel som visar **hur man bäddar in bilder** som Base64‑data‑URI:er för små grafik, medan större resurser skrivs till en sidomapp. På vägen kommer vi också att täcka **convert docx to markdown**, beröra **how to convert docx** med Aspose.Words, och förklara skillnaden mellan att bädda in bilder som Base64 och att exportera dem som separata filer.  

> **Pro tip:** Om du bara behöver ett snabbt proof‑of‑concept fungerar koden nedan direkt med ett enda Maven‑beroende.

---

## Vad du behöver

- **Java 17** (eller någon nyare JDK) – API:et är Java‑centrerat, men koncepten kan överföras till andra språk.
- **Aspose.Words for Java** – ett kommersiellt bibliotek som stödjer DOCX → Markdown‑konvertering.
- Ett **exempel‑DOCX** som innehåller en blandning av små ikoner och större foton.
- En mapp där du vill att Markdown‑filen och dess resurser ska ligga.

Inga extra ramverk, inga externa skript. Bara ren Java och Aspose.Words.

---

## Steg 1 – Lägg till Aspose.Words i ditt projekt (convert docx to markdown)

Om du använder Maven, släng in följande kodsnutt i din `pom.xml`. Byt gärna ut versionen mot den senaste releasen vid läsningstillfället.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for newer versions -->
</dependency>
```

> **Varför detta är viktigt:** Aspose.Words sköter det tunga arbetet med att parsra DOCX‑strukturen, extrahera bilder och rendera Markdown‑syntax. Att försöka skriva din egen parser skulle vara ett kaninhål du förmodligen inte behöver gå in i.

---

## Steg 2 – Ladda källdokumentet DOCX

Först pekar du API:et på Word‑filen du vill omvandla. `Document`‑konstruktorn gör allt arbete—ingen manuell XML‑parsning krävs.

```java
import com.aspose.words.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Step 2: Load the source DOCX document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Observera att kommentaren förklarar *varför* den här raden är avgörande: utan ett `Document`‑objekt finns det inget att konvertera.

---

## Steg 3 – Förbered MarkdownSaveOptions med en resurs‑sparande återuppringning

Detta är kärnan i **hur man bäddar in bilder** korrekt. Återuppringningen ger dig en krok för varje resurs (bild, stil, osv.) som konverteraren vill skriva.

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

- **Kontroll:** Du bestämmer om en bild blir en inbäddad Base64‑sträng eller en separat fil.
- **Prestanda:** Små ikoner blir en del av Markdown, vilket eliminerar extra HTTP‑förfrågningar.
- **Portabilitet:** Större bilder förblir som externa filer, vilket håller Markdown‑filens storlek rimlig.

---

## Steg 4 – Spara dokumentet som Markdown

Till sist, be Aspose.Words att skriva Markdown‑filen med de alternativ vi just konfigurerade.

```java
        // Step 5: Save the document as Markdown using the configured options
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

När programmet körs produceras två saker:

1. `output.md` – Markdown‑representationen av ditt ursprungliga DOCX.
2. En `markdown_resources`‑mapp som innehåller alla stora bilder som inte bäddades in.

---

## Fullt fungerande exempel (Alla steg på ett ställe)

Nedan är den kompletta källfilen, klar att kopiera‑klistra in i din IDE. Ersätt `YOUR_DIRECTORY` med den faktiska sökvägen på din maskin.

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

**Förväntad output:** Öppna `output.md` i någon Markdown‑visare. Små ikoner visas inbäddade, t.ex.:

```markdown
![Embedded Icon](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
```

Större bilder refereras så här:

```markdown
![Photo](markdown_resources/photo1.jpg)
```

Det är exakt vad du behöver för att **bädda in bilder** samtidigt som du håller filstorleken hanterbar.

---

## Vanliga frågor & kantfall

### Vad händer om en bild är en JPEG istället för PNG?

Återuppringningen ovan prefixar alltid URI:n med `image/png`. För JPEG‑bilder kan du inspektera de första några bytena av `args.getData()` eller använda `args.getFileName()` för att avgöra rätt MIME‑typ:

```java
String mime = args.getFileName().toLowerCase().endsWith(".jpg") ||
              args.getFileName().toLowerCase().endsWith(".jpeg")
              ? "image/jpeg" : "image/png";
args.setUri("data:" + mime + ";base64," + base64);
```

### Kan jag ändra storlekströskeln?

Absolut. Gränsen på `10_000` byte är bara ett exempel. Om du har en generös bandbreddsbudget kan du höja den till 50 KB eller mer. Omvänt, sänk den om du behöver ultralätta Markdown‑filer.

### Fungerar detta med tabeller eller andra Word‑objekt?

Ja. Aspose.Words konverterar automatiskt tabeller, listor och till och med fotnoter till Markdown. Resurs‑callbacken fångar bara bilder, så du behöver ingen extra kod för andra element.

### Vad händer med icke‑ASCII‑filnamn?

API:et kodar säkert Unicode‑filnamn när de skrivs till `markdown_resources`‑mappen. Se bara till att ditt filsystem stödjer UTF‑8 (de flesta moderna OS gör det).

---

## Pro‑tips för en smidig konvertering

- **Håll utmatningsmappen ren.** Kör `Files.createDirectories` bara en gång per konvertering, eller radera mappen före varje körning om du vill ha en fräsch start.
- **Validera Markdown.** Verktyg som `markdownlint` kan fånga felaktiga tecken som introduceras av felaktiga Base64‑strängar.
- **Lås version av Aspose.Words.** En specifik version säkerställer att din kod fortsätter fungera även efter att en större release ändrar standardbeteendet.
- **Use a .gitignore** entry for `markdown_resources/

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}