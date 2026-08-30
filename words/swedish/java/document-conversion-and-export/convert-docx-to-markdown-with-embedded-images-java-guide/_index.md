---
category: general
date: 2026-06-27
description: Konvertera docx till markdown med Aspose.Words för Java. Lär dig hur
  du bäddar in bilder som base64 och exporterar Word-dokument till markdown utan ansträngning.
draft: false
keywords:
- convert docx to markdown
- embed images as base64
- how to embed images markdown
- export word document to markdown
- convert docx to markdown with images
language: sv
og_description: convert docx to markdown with Aspose.Words for Java. This tutorial
  shows how to embed images as base64 and export Word document to markdown in a single
  flow.
og_title: konvertera docx till markdown med inbäddade bilder – Java‑guide
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: convert docx to markdown using Aspose.Words for Java. Learn how to
    embed images as base64 and export Word document to markdown effortlessly.
  headline: convert docx to markdown with embedded images – Java guide
  type: TechArticle
- description: convert docx to markdown using Aspose.Words for Java. Learn how to
    embed images as base64 and export Word document to markdown effortlessly.
  name: convert docx to markdown with embedded images – Java guide
  steps:
  - name: Read the image file into a byte array (`Files.readAllBytes`).
    text: Read the image file into a byte array (`Files.readAllBytes`).
  - name: Encode with `Base64.getEncoder().encodeToString`.
    text: Encode with `Base64.getEncoder().encodeToString`.
  - name: 'Insert the data URI into your Markdown string: `![alt](data:image/png;base64,${base64})`.'
    text: 'Insert the data URI into your Markdown string: `![alt](data:image/png;base64,${base64})`.'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Conversion
title: konvertera docx till markdown med inbäddade bilder – Java‑guide
url: /sv/java/document-conversion-and-export/convert-docx-to-markdown-with-embedded-images-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# konvertera docx till markdown med inbäddade bilder – Java‑guide

Har du någonsin behövt **convert docx to markdown** men stött på problem när bilder försvann eller blev trasiga länkar? Du är inte ensam. I många projekt—statisk‑sidgeneratorer, dokumentations‑pipelines eller snabba förhandsgranskningar—är det ett måste att bevara dessa bilder, och de vanliga konverterarna släpper ofta bort dem.  

Lyckligtvis ger Aspose.Words for Java oss ett rent sätt att **embed images as base64** direkt i Markdown, så att utdatafilen blir riktigt portabel. I den här guiden går vi igenom hela processen: läsa in en Word‑fil, konfigurera Markdown‑spara‑alternativen, hantera bildresurser och slutligen spara resultatet. I slutet vet du exakt **how to embed images markdown**‑stil och du har ett färdigt kodexempel som du kan klistra in i vilket Maven‑ eller Gradle‑projekt som helst.

## Vad du behöver

- Java 17 eller nyare (API‑et fungerar även med äldre versioner, men 17 är den optimala).
- Aspose.Words for Java‑biblioteket (du kan hämta den senaste JAR‑filen från Maven Central: `com.aspose:aspose-words:23.12`).
- En `.docx`‑fil som du vill omvandla (vi kallar den `Report.docx`).
- En bra IDE (IntelliJ IDEA, Eclipse eller till och med VS Code med Java‑tillägg).

Inga extra bild‑behandlingsverktyg behövs—biblioteket sköter allt under huven.

## Steg 1: Läs in Word‑dokumentet – **convert docx to markdown**‑grund

Det första vi gör är att skapa en `Document`‑instans som pekar på källfilen. Tänk på detta objekt som den minnes‑representation av din Word‑fil, komplett med stycken, tabeller och naturligtvis bilder.

```java
import com.aspose.words.*;

public class DocxToMarkdown {
    public static void main(String[] args) throws Exception {
        // Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/Report.docx");
        // … we’ll configure options next
    }
}
```

> **Pro tip:** Om du läser docx‑filen från en ström (t.ex. en uppladdad fil) kan du skicka ett `InputStream` till `Document`‑konstruktorn—perfekt för webb‑appar.

## Steg 2: Konfigurera MarkdownSaveOptions – **embed images as base64**‑magik

Aspose.Words levereras med en `MarkdownSaveOptions`‑klass som låter oss finjustera hur konverteringen beter sig. Nyckeln till att behålla bilder är `IResourceSavingCallback`. Inuti callbacken avlyssnar vi varje bildström, omvandlar den till en Base64‑sträng och skriver om resursnamnet till en data‑URI.

```java
import java.io.ByteArrayOutputStream;
import java.util.Base64;
import com.aspose.words.*;

MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions();

// Embed images directly as Base64 data URIs
markdownOptions.setResourceSavingCallback(new IResourceSavingCallback() {
    @Override
    public void resourceSaving(ResourceSavingArgs args) throws Exception {
        // Only act on image resources
        if (args.getResourceType() == ResourceType.IMAGE) {
            // Copy the image stream to a byte array
            ByteArrayOutputStream baos = new ByteArrayOutputStream();
            args.getStream().copyTo(baos);
            // Encode the bytes as Base64
            String base64 = Base64.getEncoder().encodeToString(baos.toByteArray());
            // Build a data URI (png assumed, adjust if needed)
            args.setResourceFileName("data:image/png;base64," + base64);
            // Close the original stream – we no longer need it
            args.setKeepResourceStreamOpen(false);
        }
    }
});
```

Varför gå igenom detta extra steg? För utan en callback skulle **export word document to markdown** dumpa bilder i en separat mapp och referera till dem med relativa sökvägar. Dessa sökvägar går sönder när du flyttar Markdown‑filen, särskilt i CI‑pipelines. Genom att bädda in bilden som en Base64‑sträng blir Markdown‑filen ett enda, självständigt artefakt—perfekt för GitHub‑README‑filer eller statiska‑sidgeneratorer som inte stödjer externa resurser.

### Hantera olika bildformat

Kodsnutten ovan antar PNG (`image/png`). Om ditt Word‑dokument innehåller JPEG‑bilder kan du inspektera den ursprungliga innehållstypen:

```java
String mime = args.getContentType(); // e.g., "image/jpeg"
args.setResourceFileName("data:" + mime + ";base64," + base64);
```

Den lilla justeringen säkerställer att den resulterande Markdown‑filen renderas korrekt oavsett originalformat.

## Steg 3: Spara filen – **export word document to markdown**‑slutsteg

Nu när alternativen är klara anropar vi helt enkelt `document.save`, med målvägen och de konfigurerade `MarkdownSaveOptions`. Biblioteket gör det tunga arbetet: det traverserar dokumentträdet, konverterar stycken till Markdown‑syntax och injicerar våra Base64‑bilder där de hör hemma.

```java
// Save the document as Markdown with embedded Base64 images
document.save("YOUR_DIRECTORY/Report.md", markdownOptions);
System.out.println("Conversion complete! Check Report.md");
```

När du öppnar `Report.md` i någon Markdown‑visare (VS Code, GitHub, typora osv.) ser du bilderna renderade inline, utan extra filer.

## Steg 4: Fullt, körbart exempel – **convert docx to markdown with images** på ett ställe

När vi sätter ihop allt, här är det kompletta programmet som du kan kopiera‑klistra, kompilera och köra:

```java
import com.aspose.words.*;
import java.io.*;
import java.util.Base64;

public class DocxToMarkdown {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/Report.docx");

        // 2️⃣ Set up Markdown save options with Base64 image embedding
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions();
        markdownOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) throws Exception {
                if (args.getResourceType() == ResourceType.IMAGE) {
                    ByteArrayOutputStream baos = new ByteArrayOutputStream();
                    args.getStream().copyTo(baos);
                    String base64 = Base64.getEncoder().encodeToString(baos.toByteArray());
                    String mime = args.getContentType(); // Preserve original MIME type
                    args.setResourceFileName("data:" + mime + ";base64," + base64);
                    args.setKeepResourceStreamOpen(false);
                }
            }
        });

        // 3️⃣ Save as Markdown – this is where we **export word document to markdown**
        document.save("YOUR_DIRECTORY/Report.md", markdownOptions);
        System.out.println("✅ convert docx to markdown with embedded images finished.");
    }
}
```

### Förväntad utdata

Öppna `Report.md` så bör du se något liknande:

```markdown
# Sample Report

Here is an introductory paragraph.

![Image](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...==)

Another paragraph follows.
```

Den långa Base64‑strängen representerar bilddata. De flesta redigerare trunkerar den i UI‑tillståndet, men bilden renderas perfekt vid förhandsgranskning.

## Vanliga fallgropar och hur du undviker dem

| Problem | Varför det händer | Lösning |
|------|----------------|-----|
| Bilder visas som trasiga länkar | Callbacken kördes inte eftersom `ResourceType`‑kontrollen saknades. | Se till att `if (args.getResourceType() == ResourceType.IMAGE)` omger din logik. |
| Utdatafilen är stor | Base64 ökar datamängden med ~33 %. | Acceptera kompromissen för portabilitet, eller byt till externa bilder om storleken är ett problem. |
| Fel bildformat | Hårdkodad `image/png` för JPEG‑bilder. | Använd `args.getContentType()` för att bevara den ursprungliga MIME‑typen. |
| Out‑of‑memory för stora dokument | Laddar ett enormt DOCX‑dokument i minnet. | Processa dokumentet i delar eller öka JVM‑heapen (`-Xmx2g`). |

## När du behöver **how to embed images markdown** i andra sammanhang

Om du inte använder Aspose.Words men ändå vill bädda in Base64‑bilder, är principen densamma:

1. Läs in bildfilen till en byte‑array (`Files.readAllBytes`).
2. Koda med `Base64.getEncoder().encodeToString`.
3. Infoga data‑URI:n i din Markdown‑sträng: `![alt](data:image/png;base64,${base64})`.

Biblioteket automatiserar bara detta för varje bild det stöter på, så du slipper skriva en loop.

## Nästa steg – utöka konverteringen

Nu när du behärskar **convert docx to markdown with images**, överväg dessa förbättringar:

- **Stilbevarande**: Använd `HtmlSaveOptions` först, konvertera sedan HTML till Markdown med ett verktyg som flexmark‑java för rikare formatering.
- **Tabellhantering**: Aspose konverterar redan tabeller, men du kan finjustera kolumnjustering via `markdownOptions.setTableAlignment`.
- **Batch‑bearbetning**: Packa in koden ovan i en katalog‑skanner för att automatiskt konvertera dussintals rapporter.
- **Integration med CI**: Lägg till JAR‑filen i din bygg‑pipeline och generera dokumentation vid varje commit.

Varje av dessa idéer bygger på samma grundkoncept som vi gick igenom, så du kommer känna dig bekväm med att anpassa koden.

## Slutsats

Vi har just gått igenom en komplett, end‑to‑end‑lösning för **convert docx to markdown** samtidigt som vi säkerställer att varje bild förblir inbäddad som en Base64‑sträng. Nyckelstegen—ladda dokumentet, konfigurera `MarkdownSaveOptions` med en anpassad `IResourceSavingCallback`, och spara filen—är enkla, och koden fungerar direkt med Aspose.Words for Java.  

Beväpnad med denna kunskap kan du nu automatisera dokumentations‑pipelines, generera portabla Markdown‑rapporter, eller helt enkelt behålla en ren, en‑fil‑version av ditt Word‑innehåll. Om du är nyfiken på ytterligare justeringar—som att hantera SVG‑filer eller anpassa rubriknivåer—utforska Aspose.Words API‑dokumentationen; den är full av exempel som kompletterar det vi byggt här.

Lycka till med kodandet, och må din Markdown alltid vara bild‑rik!  

![konvertera docx till markdown diagram](convert-docx-to-markdown.png "konvertera docx till markdown")

---

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Hur man bäddar in bilder i Markdown vid konvertering av DOCX](/words/english/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/)
- [Hur man exporterar Markdown med Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-markdown/)
- [Konvertera docx till markdown – Exportera matematiska ekvationer till LaTeX med Aspose.Words](/words/english/java/document-conversion-and-export/convert-docx-to-markdown-export-math-equations-to-latex-with/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}