---
category: general
date: 2026-05-26
description: Infoga bilder som base64 när du konverterar docx till markdown med Aspose.Words
  för Java. Lär dig att konvertera Word till markdown, spara Word som markdown och
  hantera bilder.
draft: false
keywords:
- embed images as base64
- convert docx to markdown
- convert word to markdown
- convert images to base64
- save word as markdown
language: sv
og_description: Bädda in bilder som base64 när du konverterar docx till markdown med
  Aspose.Words för Java. Komplett guide för att konvertera Word till markdown och
  spara Word som markdown.
og_title: Bädda in bilder som Base64 vid konvertering av DOCX till Markdown
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Embed images as base64 while you convert docx to markdown with Aspose.Words
    for Java. Learn to convert word to markdown, save word as markdown, and handle
    images.
  headline: Embed Images as Base64 When Converting DOCX to Markdown
  type: TechArticle
- description: Embed images as base64 while you convert docx to markdown with Aspose.Words
    for Java. Learn to convert word to markdown, save word as markdown, and handle
    images.
  name: Embed Images as Base64 When Converting DOCX to Markdown
  steps:
  - name: 'H3: Why Use `setSaveToMemory(true)`?'
    text: 'When `saveToMemory` is true, Aspose writes the image bytes to a memory
      stream instead of a file. The Markdown exporter then converts that stream to
      a Base64 string and inserts it directly into the Markdown image tag:'
  - name: Troubleshooting Checklist
    text: '| Issue | Likely Cause | Fix | |-------|--------------|-----| | Image appears
      as a broken link | `setSaveToMemory` was omitted | Ensure `args.setSaveToMemory(true);`
      is inside the callback | | Base64 string is truncated | Output file encoding
      mismatch | Save the Markdown using UTF‑8 (default for Asp'
  - name: Convert Only Selected Images
    text: 'If you only want to embed certain images (e.g., those larger than 100 KB),
      add a size check:'
  - name: Use a Different Image Format
    text: The `ResourceSavingArgs` gives you the raw bytes, so you could re‑encode
      JPEGs as PNGs before embedding—useful when the target Markdown consumer prefers
      PNG.
  type: HowTo
tags:
- Aspose.Words
- Java
- Markdown
- Base64
title: Bädda in bilder som Base64 vid konvertering av DOCX till Markdown
url: /sv/java/document-conversion-and-export/embed-images-as-base64-when-converting-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bädda in bilder som Base64 när du konverterar DOCX till Markdown

Har du någonsin funderat på hur man **bäddar in bilder som base64** medan du **konverterar docx till markdown**? Du är inte ensam—utvecklare frågar ständigt hur man behåller bilder inline utan att hantera separata filer. Den goda nyheten är att Aspose.Words for Java gör det enkelt: du kan konvertera ett Word-dokument till Markdown och automatiskt bädda in varje bild som en Base64-sträng.

I den här handledningen går vi igenom hela processen—från att läsa in en `.docx` som innehåller bilder, till att konfigurera en `MarkdownSaveOptions`-callback som gör det tunga arbetet, och slutligen spara resultatet som en ren `.md`-fil. När du är klar vet du exakt hur du **konverterar word till markdown**, **konverterar bilder till base64**, och **sparar word som markdown** utan att lämna kvar lösa bildmappar. Inga externa verktyg, ingen manuell efterbehandling—bara ren Java‑kod som du kan släppa in i vilket projekt som helst.

## Vad du behöver

- **Java 17** (eller någon nyare JDK) – koden använder lambda‑syntax, men du kan anpassa den till äldre versioner.
- **Aspose.Words for Java**-biblioteket (senaste versionen 2026). Lägg till Maven‑beroendet eller JAR‑filen i din classpath.
- En exempel **DOCX**‑fil som innehåller minst en bild.  
- En IDE eller en enkel textredigerare—Visual Studio Code, IntelliJ IDEA, eller till och med `vim` fungerar.

Om du redan har detta, bra—låt oss dyka rakt in.

## Steg 1: Läs in Word‑dokumentet

Först skapar vi en `Document`‑instans som pekar på källfilen. Detta är samma steg oavsett om du **konverterar docx till markdown** eller bara läser filen för andra ändamål.

```java
import com.aspose.words.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Load the source DOCX that contains images
        Document doc = new Document("YOUR_DIRECTORY/doc-with-images.docx");
```

> **Varför detta är viktigt:** `Document`‑objektet är startpunkten för varje Aspose‑operation. Det innehåller hela Word‑strukturen—inklusive bilder, tabeller och stilar—så att den senare callbacken kan inspektera varje resurs.

## Steg 2: Skapa MarkdownSaveOptions och registrera en Resource‑Saving‑callback

Magin finns i `MarkdownSaveOptions`. Genom att fästa en `IResourceSavingCallback` får vi kontroll över hur varje extern resurs (som en bild) skrivs.

```java
        // Configure Markdown save options
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();

        // Register the callback that will embed images as Base64
        mdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            @Override
            public void resourceSaving(ResourceSavingArgs args) {
                // The callback fires for every resource Aspose wants to write
                if (args.getResourceType() == ResourceType.IMAGE) {
                    // Tell Aspose we don’t want a separate image file
                    args.setKeepResourceOriginalName(false);
                    // Give the image a predictable name (optional)
                    args.setResourceFileName("image_" + args.getResourceFileName());
                    // Force in‑memory saving – this triggers Base64 embedding
                    args.setSaveToMemory(true);
                }
            }
        });
```

### H3: Varför använda `setSaveToMemory(true)`?

När `saveToMemory` är true skriver Aspose bildbytarna till ett minnesström istället för en fil. Markdown‑exportören konverterar sedan det strömmen till en Base64‑sträng och infogar den direkt i Markdown‑bildtaggen:

```markdown
![image_image1.png](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
```

Det är kärnan i **bädda in bilder som base64**.

## Steg 3: Spara dokumentet som Markdown

Nu när callbacken är på plats är det sista steget helt enkelt att anropa `save`. Det är här vi faktiskt **konverterar word till markdown** och, på grund av callbacken, också **konverterar bilder till base64**.

```java
        // Save the document as Markdown – this triggers the callback
        doc.save("YOUR_DIRECTORY/out.md", mdOptions);
    }
}
```

> **Resultat:** `out.md` innehåller Markdown‑text med varje bild representerad som en `data:`‑URI. Inga extra bildfiler skapas på disk, så mappen förblir prydlig.

## Steg 4: Verifiera resultatet och vanliga fallgropar

Öppna den genererade `out.md` i någon Markdown‑visare (VS Code, GitHub eller en statisk webbplatsgenerator). Du bör se något liknande:

```markdown
# Sample Document

Here is an inline image:

![image_image1.png](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
```

### Felsökningschecklista

| Problem | Trolig orsak | Åtgärd |
|-------|--------------|-----|
| Bild visas som en trasig länk | `setSaveToMemory` utelämnades | Säkerställ att `args.setSaveToMemory(true);` finns i callbacken |
| Base64‑sträng är avklippt | Fel kodning på utdatafil | Spara Markdown med UTF‑8 (standard för Aspose) |
| Oväntade filnamn | `setKeepResourceOriginalName(true)` | Håll den `false` för att tvinga den anpassade namngivningslogiken |

## Steg 5: Avancerade varianter (valfritt)

### Konvertera endast utvalda bilder

Om du bara vill bädda in vissa bilder (t.ex. de som är större än 100 KB), lägg till en storlekskontroll:

```java
if (args.getResourceType() == ResourceType.IMAGE) {
    if (args.getResourceData().length > 100_000) {
        args.setSaveToMemory(true);
    }
}
```

### Använd ett annat bildformat

`ResourceSavingArgs` ger dig de råa bytarna, så du kan åter‑koda JPEG‑bilder som PNG innan du bäddar in dem—användbart när mål‑Markdown‑klienten föredrar PNG.

```java
if (args.getResourceFileName().endsWith(".jpg")) {
    // Convert JPEG bytes to PNG bytes (requires an image library)
    byte[] pngBytes = convertJpegToPng(args.getResourceData());
    args.setResourceData(pngBytes);
    args.setResourceFileName(args.getResourceFileName().replace(".jpg", ".png"));
    args.setSaveToMemory(true);
}
```

Dessa justeringar visar hur flexibel **bädda in bilder som base64**‑metoden är när du **konverterar docx till markdown**.

## Slutsats

Du har precis lärt dig hur du **bäddar in bilder som base64** medan du **konverterar docx till markdown** med Aspose.Words for Java. Genom att koppla en enkel `IResourceSavingCallback` sköter biblioteket allt tungt arbete: det **konverterar word till markdown**, **konverterar bilder till base64**, och slutligen **sparar word som markdown** med ett enda `save`‑anrop.  

Känn dig fri att experimentera—prova olika bildfiltreringsregler, byt till HTML‑utmatning, eller kedja detta steg med en statisk webbplatsgenerator. Samma mönster fungerar för andra format (HTML, EPUB) också, så du kan återanvända callbacken där du behöver inline‑resurser.

**Nästa steg:**  
- Utforska `HtmlSaveOptions` för HTML‑med‑Base64‑bilder.  
- Kombinera detta med en CI‑pipeline för att automatisera dokumentationsgenerering.  
- Fördjupa dig i Aspose’s `DocumentVisitor` om du behöver ännu finare kontroll över konverteringsprocessen.

Lycka till med kodandet, och njut av dina rena, självständiga Markdown‑filer!

## Relaterade handledningar

- [Hur man bäddar in bilder i Markdown när man konverterar DOCX](/words/english/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/)
- [Konvertera docx till markdown – Exportera matematiska ekvationer till LaTeX med Aspose.Words](/words/english/java/document-conversion-and-export/convert-docx-to-markdown-export-math-equations-to-latex-with/)
- [Spara bilder från Word – Aspose.Words för Java‑guide](/words/english/java/document-loading-and-saving/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}