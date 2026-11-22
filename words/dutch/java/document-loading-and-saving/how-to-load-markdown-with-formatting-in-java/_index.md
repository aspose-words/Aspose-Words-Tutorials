---
category: general
date: 2026-11-22
description: Leer hoe je markdown met opmaak kunt laden in Java. Deze gids laat zien
  hoe je markdown met opmaak kunt lezen met behulp van LoadOptions en Document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to load markdown
- read markdown with formatting
- Java markdown parsing
- LoadOptions import underline
- Document processing Java
language: nl
lastmod: 2026-11-22
og_description: Hoe markdown met opmaak te laden in Java. Volg deze volledige tutorial
  om markdown met opmaak te lezen, onderstrepingsstijlen te behouden en met Document-objecten
  te werken.
og_image_alt: Java code snippet showing markdown loading with formatting enabled
og_title: Hoe markdown met opmaak te laden in Java – stap‑voor‑stap gids
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
title: Hoe markdown met opmaak te laden in Java
url: /nl/java/document-loading-and-saving/how-to-load-markdown-with-formatting-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe markdown met opmaak te laden in Java

Als je **markdown wilt laden** terwijl je de visuele stijlen behoudt, biedt deze tutorial een kant‑klaar oplossing. Je ziet precies hoe je **markdown met opmaak kunt lezen** zoals onderstreepte tekst, zodat het gerenderde document overeenkomt met de oorspronkelijke bron.

De gids behandelt elke stap, van het configureren van de loader tot het verifiëren dat de opmaak de import heeft overleefd. Er zijn geen externe tools nodig, behalve de standaard GroupDocs.Viewer‑bibliotheek (of een compatibele API die `LoadOptions` en `Document` levert). Aan het einde kun je markdown‑laden integreren in elke Java‑backend, webservice of desktop‑applicatie.

## Vereisten

* Java 17 of nieuwer geïnstalleerd.
* Maven of Gradle voor afhankelijkheidsbeheer.
* Toegang tot de GroupDocs.Viewer (of equivalent) JAR die `LoadOptions` en `Document` bevat.
* Een voorbeeld‑markdown‑bestand (`sample.md`) dat onderstrepings‑markup bevat (bijv. `<u>underlined text</u>` of `_underlined_` afhankelijk van de parser).

## Stap 1: Voeg de vereiste afhankelijkheid toe

Als je Maven gebruikt, voeg dan het volgende toe aan je `pom.xml`. Pas de versie aan naar de nieuwste stabiele release.

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>23.12</version>
</dependency>
```

Gradle‑gebruikers kunnen toevoegen:

```groovy
implementation 'com.groupdocs:groupdocs-viewer:23.12'
```

Het opnemen van de bibliotheek maakt zowel de `LoadOptions`‑ als de `Document`‑klassen beschikbaar tijdens het compileren.

## Stap 2: Configureer LoadOptions om onderstrepings‑opmaak te importeren

Het `LoadOptions`‑object vertelt de parser welke markdown‑functies behouden moeten blijven. Het inschakelen van onderstrepings‑opmaak zorgt ervoor dat de visuele stijl verschijnt in het resulterende `Document`.

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

**Waarom dit belangrijk is:**  
Zonder `setImportUnderlineFormatting(true)` verwijdert de parser onderstrepings‑tags, waardoor platte tekst overblijft. Het inschakelen van de vlag behoudt de stijl, wat essentieel is wanneer de downstream‑consumer (bijv. een PDF‑generator) afhankelijk is van visuele aanwijzingen.

## Stap 3: Laad het markdown‑document met de geconfigureerde opties

Nu kun je het markdown‑bestand lezen. De `Document`‑constructor accepteert het bestandspad en de `LoadOptions` die je zojuist hebt voorbereid.

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

**Waarom dit belangrijk is:**  
Het doorgeven van de `LoadOptions` aan de `Document`‑constructor garandeert dat de parser de onderstrepings‑vlag gedurende het volledige importproces respecteert. Het resulterende `Document`‑object kan worden gerenderd, geconverteerd of geïnspecteerd met volledige opmaak.

## Stap 4: Verifieer dat onderstrepings‑opmaak behouden is gebleven

Een snelle manier om te bevestigen dat de onderstreping aanwezig is, is het document naar HTML te renderen en de output af te drukken. De HTML zal `<u>`‑tags bevatten als de import geslaagd is.

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

Het uitvoeren van het volledige programma moet een HTML‑fragment weergeven dat `<u>underlined text</u>` bevat. Als de tag ontbreekt, controleer dan nogmaals of `setImportUnderlineFormatting(true)` is aangeroepen vóór het laden van het bestand.

## Volledig uitvoerbaar voorbeeld

Alles samengevoegd, hier is een zelfstandige Java‑klasse die je kunt compileren en uitvoeren:

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

**Verwachte output (ingekort voor beknoptheid):**

```
Rendered HTML snippet:
<div class="page">
  <p>This is a <u>underlined text</u> example from the markdown file.</p>
  …
```

Als de `<u>`‑tag verschijnt, is de markdown met behoud van opmaak geladen.

## Veelvoorkomende variaties en randgevallen

| Situatie                              | Wat te wijzigen                                                |
|---------------------------------------|--------------------------------------------------------------|
| **Verschillende markdown‑extensies**   | Gebruik `loadOptions.setImportBoldFormatting(true)` voor **vet**. |
| **Grote bestanden (> 10 MB)**          | Stream het bestand met `FileInputStream` en geef de stream door aan `Document`. |
| **PDF‑output nodig**                  | Na het laden, gebruik `PdfViewOptions` met `Viewer` om een PDF te genereren die onderstrepingsstijlen behoudt. |
| **Uitvoeren in een servlet‑container**| Sla het `Document` op in de request‑scope en render on‑the‑fly naar HTML. |

**Pro tip:** Maak altijd een nieuwe `LoadOptions`‑instantie aan voor elke laad‑operatie. Het hergebruiken van hetzelfde object over threads heen kan leiden tot onverwachte status‑lekken.

## Conclusie

Je weet nu **hoe je markdown met opmaak in Java kunt laden** en hoe je **markdown met opmaak kunt lezen** met behulp van `LoadOptions`. Het volledige voorbeeld toont configuratie, laden en verificatie, zodat je dit patroon kunt integreren in elk Java‑project dat markdown‑bestanden verwerkt.

Vervolgens kun je gerelateerde onderwerpen verkennen, zoals **markdown lezen met afbeeldingen**, **markdown naar PDF converteren**, of **andere stijl‑imports aanpassen** (vet, cursief, doorhalen). Elk van deze uitbreidingen volgt hetzelfde patroon: pas `LoadOptions`‑vlaggen aan, laad het `Document` en render in het gewenste formaat.

Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe markdown‑document te laden in Java met aangepaste importopties](/words/english/java/document-loading-and-saving/how-to-load-markdown-document-in-java-with-custom-import-opt/)
- [Hoe een Markdown‑bestand te lezen en te laden in Java met Aspose.Words](/words/english/java/document-loading-and-saving/how-to-read-markdown-file-java-with-aspose-words/)
- [Hoe Markdown te laden in Java – Complete gids](/words/english/java/document-loading-and-saving/how-to-load-markdown-in-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}