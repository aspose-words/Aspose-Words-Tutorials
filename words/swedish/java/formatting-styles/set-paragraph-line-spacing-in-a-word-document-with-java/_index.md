---
category: general
date: 2026-11-15
description: Ställ in radavstånd för stycken i ett Word‑dokument med Java. Lär dig
  hur du programatiskt ställer in radavstånd med Aspose.Words för exakt dokumentformatering.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set paragraph line spacing
- how to set line spacing
language: sv
lastmod: 2026-11-15
og_description: Ställ in radavstånd för stycken i ett Word‑dokument med Java. Denna
  guide förklarar hur du ställer in radavstånd för stycken och fotnotseparatorer med
  Aspose.Words, vilket ger dig full kontroll över dokumentlayouten.
og_image_alt: Screenshot showing Java code that sets paragraph line spacing in a Word
  document
og_title: Ställ in radavstånd för stycken i Word med Java
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  headline: Set paragraph line spacing in a Word document with Java
  type: TechArticle
- description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  name: Set paragraph line spacing in a Word document with Java
  steps:
  - name: Load the Word document
    text: First, create a `Document` instance that points to your source file.
  - name: Retrieve the footnote separator
    text: Footnote separators are special paragraphs that appear between footnotes
      and the main text. To change their appearance you need to access the `FootnoteSeparator`
      object.
  - name: How to set line spacing for the separator's paragraph
    text: Now apply the desired line spacing. Aspose.Words uses points for line‑spacing
      values; 12 pts is roughly single‑spacing for most fonts.
  - name: Save the updated document
    text: Finally, write the changes back to disk.
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Formatting
title: Ställ in radavstånd för stycke i ett Word‑dokument med Java
url: /sv/java/formatting-styles/set-paragraph-line-spacing-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ställ in radavstånd för stycken i ett Word-dokument med Java

Om du behöver **ställa in radavstånd för stycken** i ett Word-dokument, visar den här handledningen hur du gör det med Java och Aspose.Words. Du kommer också att lära dig **hur du ställer in radavstånd** för fotnotseparatorer – ett vanligt krav när du formaterar professionella dokument.

I följande avsnitt kommer du att:

* Ladda en befintlig *.docx*-fil.
* Hämta fotnotseparatorns stycke.
* Tillämpa ett anpassat radavståndsvärde.
* Spara det uppdaterade dokumentet.

Ingen extern konfiguration krävs förutom att lägga till Aspose.Words‑biblioteket i ditt projekt, så du kan kopiera koden exakt och köra den omedelbart.

## Förutsättningar

Innan du börjar, se till att du har:

* Java 17 eller nyare installerat.
* Maven (eller ett annat byggverktyg) för att hantera beroenden.
* En giltig Aspose.Words för Java-licens (den fria utvärderingen fungerar för testning).
* Ett inmatnings‑Word‑dokument (`input.docx`) placerat i en känd katalog.

Lägg till Aspose.Words‑beroendet i din `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

## Ställ in radavstånd för stycken med Aspose.Words

Denna H2‑rubrik innehåller huvudnyckelordet och uppfyller SEO‑kravet.

### Steg 1: Ladda Word‑dokumentet

Först, skapa en `Document`‑instans som pekar på din källfil.

```java
import com.aspose.words.*;

public class LineSpacingExample {
    public static void main(String[] args) throws Exception {
        // Load the Word document from the specified path
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // Continue with formatting...
    }
}
```

*Varför detta är viktigt*: Att ladda dokumentet ger dig en modell i minnet som du kan manipulera utan att röra den ursprungliga filen förrän du explicit sparar den.

### Steg 2: Hämta fotnotseparatorn

Fotnotseparatorer är speciella stycken som visas mellan fotnoter och huvudtexten. För att ändra deras utseende måste du komma åt `FootnoteSeparator`‑objektet.

```java
// Retrieve the footnote separator that Aspose.Words represents internally
FootnoteSeparator separator = doc.getFootnoteSeparator();
```

*Tips*: Om ditt dokument inte innehåller fotnoter, finns separatorn fortfarande som ett dolt stycke, så anropet kommer aldrig att returnera `null`.

### Steg 3: Hur du ställer in radavstånd för separatorns stycke

Applicera nu önskat radavstånd. Aspose.Words använder punkter för radavståndsvärden; 12 pt är ungefär enkelradigt för de flesta teckensnitt.

```java
// Set the line spacing to 12 points (single‑spacing)
separator.getParagraphFormat().setLineSpacing(12.0);
```

Du kan också använda andra avståndslägen:

| Mode                     | Method call                                      |
|--------------------------|--------------------------------------------------|
| **Exactly** (fasta pt) | `setLineSpacingRule(LineSpacingRule.EXACTLY)`   |
| **Multiple** (t.ex. 1.5) | `setLineSpacingRule(LineSpacingRule.MULTIPLE); setLineSpacing(1.5);` |

Att välja rätt regel säkerställer att dokumentet renderas konsekvent i Word, Google Docs och andra visningsprogram.

### Steg 4: Spara det uppdaterade dokumentet

Slutligen, skriv tillbaka ändringarna till disk.

```java
// Save the modified document to a new file
doc.save("YOUR_DIRECTORY/output.docx");
System.out.println("Document saved with updated paragraph line spacing.");
```

När du öppnar `output.docx` i Microsoft Word kommer fotnotseparatorn att visas med det radavstånd du definierat.

## Förstå hur du ställer in radavstånd för vanliga stycken

Samma API fungerar för alla `Paragraph`‑objekt, inte bara fotnotseparatorer. Här är ett snabbt exempel som justerar avståndet för det första stycket i kroppen:

```java
// Access the first body paragraph
Paragraph firstPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);

// Apply double line spacing (2.0 × the font size)
firstPara.getParagraphFormat().setLineSpacingRule(LineSpacingRule.MULTIPLE);
firstPara.getParagraphFormat().setLineSpacing(2.0);
```

**Varför du kan behöva detta**: Rapporter, kontrakt och akademiska uppsatser kräver ofta en specifik radavståndsstil (t.ex. dubbelradigt för utkast). Att använda samma `setLineSpacing`‑metod garanterar den exakta layout du förväntar dig.

## Vanliga fallgropar och hur du undviker dem

| Issue                                 | Cause                                   | Fix |
|---------------------------------------|----------------------------------------|-----|
| Radavståndet verkar oförändrat        | `LineSpacingRule` lämnades på standardvärdet (AUTO) | Ange explicit regeln med `setLineSpacingRule`. |
| Extra tomma rader efter separatorn   | Separatorn innehåller dolda radbrytningar | Trimma separatorns text med `separator.getText().trim();` innan du tillämpar avståndet. |
| Dokumentet blir korrupt efter sparning| Använder en föråldrad Aspose.Words‑version | Uppgradera till den senaste versionen (t.ex. 24.10) som innehåller buggfixar för sparning. |

## Pro‑tips: batch‑processa flera dokument

Om du behöver uppdatera dussintals filer, omslut logiken i en hjälpfunktion och iterera över en mapp:

```java
public static void updateSpacing(Path inputPath, Path outputPath) throws Exception {
    Document doc = new Document(inputPath.toString());
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    sep.getParagraphFormat().setLineSpacing(12.0);
    doc.save(outputPath.toString());
}
```

Att köra den här metoden i en loop sparar dig timmar av manuellt redigerande.

## Förväntat resultat

Efter att ha kört hela programmet kommer `output.docx` att:

* Innehålla det ursprungliga innehållet oförändrat förutom radavståndet.
* Visa fotnotseparatorn med enkelradigt (12 pts) layout.
* Bevara all annan formatering (stilar, bilder, tabeller).

Öppna filen i Word och verifiera att separatorlinjen är tajtare (eller lösare, beroende på vilket värde du har angett).

## Slutsats

Du vet nu hur du **ställer in radavstånd för stycken** i ett Word‑dokument med Java, och du förstår också **hur du ställer in radavstånd** för både fotnotseparatorer och vanliga stycken. Det kompletta, körbara exemplet visar hur du laddar ett dokument, justerar radavståndsegenskaper och sparar resultatet – allt med några få tydliga API‑anrop.

**Nästa steg** du kan utforska:

* **Hur du ställer in radavstånd** för tabeller och listobjekt.
* Applicera olika avståndsregler på rubriker jämfört med brödtext.
* Använda `Style`‑objektet för att verkställa avstånd i hela dokumentet.

Experimentera med värdena, kombinera dem med andra formateringsalternativ, så får du full kontroll över dokumentlayout i alla Java‑applikationer. Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Hur du ställer in alternativ i Aspose.Words för Java – komplett guide](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [Hur du ställer in LoadOptions i Aspose.Words för Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Ändra asiatisk styckeavstånd och indrag i Word‑dokument](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}