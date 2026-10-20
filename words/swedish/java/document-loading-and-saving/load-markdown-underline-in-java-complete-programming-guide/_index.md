---
category: general
date: 2026-08-04
description: Läs in markdown‑understrykning i Java och bevara markdown‑formatering
  när du laddar markdown i dokumentet. Följ den här steg‑för‑steg‑handledningen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- load markdown underline
- load markdown into document
- preserve markdown formatting
language: sv
lastmod: 2026-08-04
og_description: Läs in markdown‑understrykning i Java och bevara markdown‑formatering.
  Lär dig hur du laddar markdown i ett dokument med fullt stöd för understrykning.
og_image_alt: Diagram showing load markdown underline process
og_title: Ladda markdown‑understreck i Java – steg‑för‑steg‑guide
schemas:
- author: GroupDocs
  dateModified: '2026-08-04'
  description: Load markdown underline in Java and preserve markdown formatting while
    loading markdown into document. Follow this step‑by‑step tutorial.
  headline: Load markdown underline in Java – complete programming guide
  type: TechArticle
- description: Load markdown underline in Java and preserve markdown formatting while
    loading markdown into document. Follow this step‑by‑step tutorial.
  name: Load markdown underline in Java – complete programming guide
  steps:
  - name: Create `LoadOptions` for the document
    text: '`LoadOptions` lets you customize how the library parses the source file.
      Creating a fresh instance gives you a clean slate for later settings.'
  - name: Enable detection of underline formatting while loading
    text: By default the viewer may ignore underline tags because they are less common
      in Markdown. Enabling this flag tells the parser to keep underline spans intact.
  - name: Load the Markdown file using the configured options
    text: Now you can load the file. Pass the `loadOptions` object to the `Document`
      constructor so the parser respects the underline flag.
  - name: Verify that underline formatting is preserved
    text: A quick sanity check helps you confirm that **preserve markdown formatting**
      worked. The following snippet prints the text of each paragraph and marks underlined
      fragments with a tilde (`~`) for visibility.
  type: HowTo
tags:
- markdown
- Java
- document-processing
title: Ladda markdown‑understrykning i Java – komplett programmeringsguide
url: /sv/java/document-loading-and-saving/load-markdown-underline-in-java-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ladda markdown‑understrykning i Java – komplett programmeringsguide

Om du behöver **ladda markdown‑understrykning** när du konverterar en Markdown‑fil till ett `Document`‑objekt, visar den här guiden exakt hur du gör det. Du får också lära dig hur du **laddar markdown i dokument** utan att förlora någon understrykningsstil, så att den ursprungliga Markdown‑formateringen bevaras helt.

Tutorialen täcker allt du behöver veta: nödvändiga bibliotek, varje konfigurationssteg och hur du verifierar att understrykningsformatet överlevde importen. I slutet har du ett återanvändbart kodexempel som du kan klistra in i vilket Java‑projekt som helst.

## Förutsättningar

Innan du börjar, se till att du har:

- Java 17 eller senare installerat (exemplet använder det moderna modulsystemet)
- Den senaste versionen av **GroupDocs.Viewer** (eller ett kompatibelt bibliotek som tillhandahåller `LoadOptions` och `Document`)
- En Markdown‑fil (`sample.md`) som innehåller understruken text, t.ex. `<u>underlined</u>` eller GitHub‑flavored‑syntaxen `__underlined__`
- En IDE som IntelliJ IDEA eller VS Code, även om vilken textredigerare som helst fungerar

Dessa krav garanterar att koden körs utan ytterligare konfiguration.

## Ladda markdown‑understrykning – steg‑för‑steg‑guide

Processen består av tre huvudåtgärder: skapa en `LoadOptions`‑instans, aktivera understrykningsdetektering och slutligen ladda Markdown‑filen med dessa alternativ. Varje steg förklaras nedan.

### Steg 1: Skapa `LoadOptions` för dokumentet

`LoadOptions` låter dig anpassa hur biblioteket parsar källfilen. Att skapa en ny instans ger dig en ren grund för senare inställningar.

```java
import com.groupdocs.viewer.options.LoadOptions;

// Step 1: Create load options for the document
LoadOptions loadOptions = new LoadOptions();
```

`LoadOptions`‑objektet är ingångspunkten för alla importrelaterade justeringar. Du kommer att använda det i nästa steg för att slå på understrykningsdetektering.

### Steg 2: Aktivera detektering av understrykningsformat vid inläsning

Som standard kan visaren ignorera understryknings‑taggar eftersom de är mindre vanliga i Markdown. Att aktivera detta flagga talar om för parsern att behålla understryknings‑spännvidder intakta.

```java
// Step 2: Enable detection of underline formatting while loading
loadOptions.setImportUnderlineFormatting(true);
```

Genom att anropa `setImportUnderlineFormatting(true)` säkerställer du att varje `<u>`‑HTML‑tagg eller GitHub‑flavored‑understrykningssyntax översätts till `Document`‑modellen som en understrykningsstil. Detta är den nyckelåtgärd som får **load markdown underline** att fungera som förväntat.

### Steg 3: Ladda Markdown‑filen med de konfigurerade alternativen

Nu kan du ladda filen. Skicka `loadOptions`‑objektet till `Document`‑konstruktorn så att parsern respekterar understryknings‑flaggan.

```java
import com.groupdocs.viewer.Document;

// Step 3: Load the Markdown file using the configured options
Document markdownDoc = new Document("YOUR_DIRECTORY/sample.md", loadOptions);
```

När konstruktorn är klar innehåller `markdownDoc` en fullständig in‑minnet‑representation av Markdown‑källan, komplett med understryknings‑runs.

### Steg 4: Verifiera att understrykningsformatet bevaras

En snabb kontroll hjälper dig bekräfta att **preserve markdown formatting** fungerade. Följande kodsnutt skriver ut texten i varje stycke och markerar understrukna fragment med en tilde (`~`) för synlighet.

```java
import com.groupdocs.viewer.contents.Page;
import com.groupdocs.viewer.contents.Paragraph;
import com.groupdocs.viewer.contents.TextFragment;

for (Page page : markdownDoc.getPages()) {
    for (Paragraph paragraph : page.getParagraphs()) {
        StringBuilder line = new StringBuilder();
        for (TextFragment fragment : paragraph.getTextFragments()) {
            if (fragment.isUnderline()) {
                line.append("~").append(fragment.getText()).append("~");
            } else {
                line.append(fragment.getText());
            }
        }
        System.out.println(line.toString());
    }
}
```

**Förväntad output** (förutsatt att `sample.md` innehåller `This is __underlined__ text`):

```
This is ~underlined~ text
```

Tildes indikerar att understrykningsstilen överlevde importen, vilket bekräftar att **load markdown into document**‑operationen bevarade den ursprungliga formateringen.

## Vanliga fallgropar och hur du undviker dem

| Symtom | Orsak | Lösning |
|---|---|---|
| Understrykning försvinner efter inläsning | `setImportUnderlineFormatting` lämnades på standardvärdet `false` | Se till att anropa `loadOptions.setImportUnderlineFormatting(true)` innan du skapar `Document`. |
| Endast en del av texten är understruken | Blandad Markdown‑syntax (t.ex. HTML `<u>` blandat med `__underline__`) | Biblioteket stöder båda; verifiera att källfilen använder en konsekvent understrykningsmarkör. |
| Dokumentet går inte att läsa in | Felaktig filsökväg eller saknade biblioteksberoenden | Använd en absolut sökväg eller placera `sample.md` relativt till arbetskatalogen; inkludera viewer‑JAR‑filerna på classpath. |

**Proffstips:** Om du också behöver behålla fet eller kursiv stil, aktivera dem med `setImportBoldFormatting(true)` respektive `setImportItalicFormatting(true)`. Att kombinera dessa flaggor ger dig en fullt trogen import av de vanligaste Markdown‑stilarna.

## Fullt körbart exempel

Nedan är ett självständigt Java‑program som sätter ihop allt. Kopiera koden till en fil med namnet `LoadMarkdownUnderlineDemo.java`, justera filsökvägen och kör den med `java LoadMarkdownUnderlineDemo`.

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.contents.Page;
import com.groupdocs.viewer.contents.Paragraph;
import com.groupdocs.viewer.contents.TextFragment;
import com.groupdocs.viewer.options.LoadOptions;

public class LoadMarkdownUnderlineDemo {

    public static void main(String[] args) {
        // 1️⃣ Create load options
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Enable underline detection
        loadOptions.setImportUnderlineFormatting(true);

        // 3️⃣ Load the Markdown file
        Document markdownDoc = new Document("YOUR_DIRECTORY/sample.md", loadOptions);

        // 4️⃣ Print each paragraph, marking underlined text with ~
        for (Page page : markdownDoc.getPages()) {
            for (Paragraph paragraph : page.getParagraphs()) {
                StringBuilder line = new StringBuilder();
                for (TextFragment fragment : paragraph.getTextFragments()) {
                    if (fragment.isUnderline()) {
                        line.append("~").append(fragment.getText()).append("~");
                    } else {
                        line.append(fragment.getText());
                    }
                }
                System.out.println(line.toString());
            }
        }
    }
}
```

När programmet körs skrivs dokumentets innehåll ut med understrykningsmarkörer, vilket bevisar att **load markdown underline**‑funktionen fungerar och att du kan **preserve markdown formatting** genom hela importkedjan.

## Slutsats

Du vet nu hur du **laddar markdown‑understrykning** i Java, hur du **laddar markdown i dokument** samtidigt som du behåller den ursprungliga stilen, och hur du verifierar att understrykningsformatet är intakt. Detta tillvägagångssätt fungerar med de senaste GroupDocs.Viewer‑utgåvorna och kan utökas för att stödja ytterligare Markdown‑funktioner som fet, kursiv och tabeller.

Utforska sedan relaterade ämnen som **preserve markdown formatting for tables**, **render Markdown to PDF**, eller **custom styling of imported Markdown elements**. Justera `LoadOptions`‑flaggorna så att de matchar exakt de formateringskrav din applikation har, och du får fin‑granulär kontroll över varje importsteg. Lycka till med kodningen!

## Vad bör du lära dig härnäst?

De följande handledningarna täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Behärska Markdown Load Options med Aspose.Words för Java](/words/english/java/document-operations/master-markdown-load-options-aspose-words-java/)
- [Behärska Markdown Load Options Aspose Words Java](/words/german/java/document-operations/master-markdown-load-options-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}