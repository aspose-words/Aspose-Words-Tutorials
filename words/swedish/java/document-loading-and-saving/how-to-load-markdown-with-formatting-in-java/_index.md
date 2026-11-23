---
category: general
date: 2026-11-22
description: Lär dig hur du laddar markdown med formatering i Java. Den här guiden
  visar hur du läser markdown med formatering med hjälp av LoadOptions och Document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to load markdown
- read markdown with formatting
- Java markdown parsing
- LoadOptions import underline
- Document processing Java
language: sv
lastmod: 2026-11-22
og_description: Hur man laddar markdown med formatering i Java. Följ den här kompletta
  handledningen för att läsa markdown med formatering, bevara understrykningar och
  arbeta med Document-objekt.
og_image_alt: Java code snippet showing markdown loading with formatting enabled
og_title: Hur man laddar markdown med formatering i Java – steg‑för‑steg‑guide
schemas:
- author: GroupDocs
  dateModified: '2026-11-22'
  description: Learn how to load markdown with formatting in Java. This guide shows
    you how to read markdown with formatting using LoadOptions and Document.
  headline: How to load markdown with formatting in Java
  type: TechArticle
tags:
- markdown
- java
- document-processing
title: Hur man laddar markdown med formatering i Java
url: /sv/java/document-loading-and-saving/how-to-load-markdown-with-formatting-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man laddar markdown med formatering i Java

Om du behöver **how to load markdown** medan du behåller dess visuella stilar, ger den här handledningen dig en färdig‑att‑köra lösning. Du kommer att se exakt hur du **read markdown with formatting** såsom understruken text, så att det renderade dokumentet matchar originalkällan.

Guiden täcker varje steg från att konfigurera laddaren till att verifiera att formateringen överlevde importen. Inga externa verktyg krävs förutom det standardbiblioteket GroupDocs.Viewer (eller någon kompatibel API som tillhandahåller `LoadOptions` och `Document`). I slutet kan du integrera markdown‑laddning i vilken Java‑backend, webbtjänst eller skrivbordsapp som helst.

## Förutsättningar

Innan du börjar, se till att du har:

* Java 17 eller nyare installerat.
* Maven eller Gradle för beroendehantering.
* Tillgång till GroupDocs.Viewer (eller motsvarande) JAR som innehåller `LoadOptions` och `Document`.
* En exempel‑markdown‑fil (`sample.md`) som innehåller understrykning (t.ex. `<u>underlined text</u>` eller `_underlined_` beroende på parsern).

## Steg 1: Lägg till det erforderliga beroendet

Om du använder Maven, lägg till följande i din `pom.xml`. Justera versionen till den senaste stabila releasen.

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>23.12</version>
</dependency>
```

Gradle‑användare kan lägga till:

```groovy
implementation 'com.groupdocs:groupdocs-viewer:23.12'
```

Att inkludera biblioteket gör både `LoadOptions` och `Document`‑klasserna tillgängliga vid kompilering.

## Steg 2: Konfigurera LoadOptions för att importera understrykning

`LoadOptions`‑objektet talar om för parsern vilka markdown‑funktioner som ska bevaras. Att aktivera understrykning säkerställer att den visuella stilen visas i det resulterande `Document`.

```java
import com.groupdocs.viewer.options.LoadOptions;

/**
 * Creates a LoadOptions instance with underline import enabled.
 *
 * @return configured LoadOptions
 */
private static LoadOptions createLoadOptions() {
    LoadOptions loadOptions = new LoadOptions();
    // Preserve underline markup when the markdown is parsed.
    loadOptions.setImportUnderlineFormatting(true);
    return loadOptions;
}
```

**Varför detta är viktigt:**  
Utan `setImportUnderlineFormatting(true)` tar parsern bort understrykningstaggarna och lämnar ren text. Att aktivera flaggan behåller stilen intakt, vilket är avgörande när den efterföljande konsumenten (t.ex. en PDF‑generator) förlitar sig på visuella ledtrådar.

## Steg 3: Ladda markdown‑dokumentet med de konfigurerade alternativen

Nu kan du läsa markdown‑filen. `Document`‑konstruktorn accepterar filsökvägen och de `LoadOptions` du just förberett.

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.options.LoadOptions;

/**
 * Loads a markdown file while preserving formatting.
 *
 * @param markdownPath absolute or relative path to the .md file
 * @param options      LoadOptions with formatting flags
 * @return Document representing the parsed markdown
 */
private static Document loadMarkdown(String markdownPath, LoadOptions options) {
    return new Document(markdownPath, options);
}
```

**Varför detta är viktigt:**  
Att skicka `LoadOptions` till `Document`‑konstruktorn garanterar att parsern respekterar understrykning‑flaggan under hela importprocessen. Det resulterande `Document`‑objektet kan renderas, konverteras eller inspekteras med full formatering.

## Steg 4: Verifiera att understrykning överlevde

Ett snabbt sätt att bekräfta att understrykningen finns är att rendera dokumentet till HTML och skriva ut resultatet. HTML‑koden kommer att innehålla `<u>`‑taggar om importen lyckades.

```java
import com.groupdocs.viewer.options.HtmlViewOptions;
import com.groupdocs.viewer.Viewer;

/**
 * Renders the loaded Document to HTML and prints the first page.
 *
 * @param doc Document loaded from markdown
 */
private static void renderAndPrint(Document doc) {
    // Create a Viewer instance for rendering.
    Viewer viewer = new Viewer(doc);
    // Render the first page as HTML.
    HtmlViewOptions viewOptions = HtmlViewOptions.forEmbeddedResources();
    viewer.view(viewOptions, 1);
    String html = viewOptions.getHtmlContent();

    System.out.println("Rendered HTML snippet:");
    System.out.println(html.substring(0, Math.min(html.length(), 500)));
}
```

Att köra hela programmet bör visa ett HTML‑snutt som inkluderar `<u>underlined text</u>`. Om taggen saknas, dubbelkolla att `setImportUnderlineFormatting(true)` anropades innan filen laddades.

## Fullständigt körbart exempel

När allt sätts ihop, här är en fristående Java‑klass som du kan kompilera och köra:

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.Viewer;
import com.groupdocs.viewer.options.HtmlViewOptions;
import com.groupdocs.viewer.options.LoadOptions;

/**
 * Demonstrates how to load markdown with formatting in Java.
 * The program reads a markdown file, preserves underline markup,
 * renders the first page to HTML, and prints a snippet.
 */
public class MarkdownLoader {

    public static void main(String[] args) {
        // Path to the markdown file – adjust as needed.
        String markdownPath = "sample.md";

        // Step 1: create LoadOptions with underline support.
        LoadOptions options = createLoadOptions();

        // Step 2: load the markdown document.
        Document doc = loadMarkdown(markdownPath, options);

        // Step 3: render the document to HTML and verify formatting.
        renderAndPrint(doc);
    }

    private static LoadOptions createLoadOptions() {
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setImportUnderlineFormatting(true);
        return loadOptions;
    }

    private static Document loadMarkdown(String path, LoadOptions options) {
        return new Document(path, options);
    }

    private static void renderAndPrint(Document doc) {
        Viewer viewer = new Viewer(doc);
        HtmlViewOptions viewOptions = HtmlViewOptions.forEmbeddedResources();
        viewer.view(viewOptions, 1); // render first page
        String html = viewOptions.getHtmlContent();

        System.out.println("Rendered HTML snippet:");
        System.out.println(html.substring(0, Math.min(html.length(), 500)));
    }
}
```

**Förväntad output (avkortad för korthet):**

```
Rendered HTML snippet:
<div class="page">
  <p>This is a <u>underlined text</u> example from the markdown file.</p>
  …
```

Om `<u>`‑taggen visas, har markdown laddats med formatering intakt.

## Vanliga variationer och specialfall

| Situation                              | What to change                                                |
|----------------------------------------|--------------------------------------------------------------|
| **Olika markdown‑extensioner**         | Använd `loadOptions.setImportBoldFormatting(true)` för **bold**. |
| **Stora filer (> 10 MB)**              | Strömma filen med `FileInputStream` och skicka strömmen till `Document`. |
| **Behöver PDF‑output**                 | Efter laddning, använd `PdfViewOptions` med `Viewer` för att generera en PDF som behåller understrykning‑stilar. |
| **Kör i en servlet‑container**         | Lagra `Document` i request‑scope och rendera till HTML i farten. |

**Pro tip:** Skapa alltid en ny `LoadOptions`‑instans för varje laddningsoperation. Att återanvända samma objekt över trådar kan leda till oväntad tillståndsläckage.

## Slutsats

Du vet nu **how to load markdown with formatting in Java** och hur du **read markdown with formatting** med `LoadOptions`. Det fullständiga exemplet visar konfiguration, laddning och verifiering, så att du kan bädda in detta mönster i vilket Java‑projekt som helst som bearbetar markdown‑filer.

Nästa steg, utforska relaterade ämnen såsom **reading markdown with images**, **converting markdown to PDF**, eller **customizing other style imports** (bold, italic, strikethrough). Varje av dessa extensioner följer samma mönster: justera `LoadOptions`‑flaggor, ladda `Document` och rendera i önskat format.

Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker nära besläktade ämnen som bygger på teknikerna som demonstreras i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Hur man laddar markdown‑dokument i Java med anpassade importalternativ](/words/english/java/document-loading-and-saving/how-to-load-markdown-document-in-java-with-custom-import-opt/)
- [Hur man läser och laddar en Markdown‑fil i Java med Aspose.Words](/words/english/java/document-loading-and-saving/how-to-read-markdown-file-java-with-aspose-words/)
- [Hur man laddar Markdown i Java – Komplett guide](/words/english/java/document-loading-and-saving/how-to-load-markdown-in-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}