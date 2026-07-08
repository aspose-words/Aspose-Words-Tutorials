---
category: general
date: 2026-07-03
description: Exporteer zwevende vormen inline tijdens het converteren van Word naar
  PDF inline. Leer hoe je PDF‑opties instelt en Word opslaat als PDF‑opties in Java.
draft: false
keywords:
- export floating shapes inline
- convert word to pdf inline
- how to set pdf options
- save word as pdf options
language: nl
og_description: Exporteer zwevende vormen inline wanneer je een Word‑document naar
  PDF converteert. Deze tutorial laat zien hoe je PDF‑opties instelt en Word opslaat
  als PDF.
og_title: Exporteer zwevende vormen inline – Java PDF-conversiegids
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  headline: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  type: TechArticle
- description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  name: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  steps:
  - name: 1. “What if my document contains complex SmartArt?”
    text: SmartArt is treated as a drawing object. The inline flag works for most
      vector shapes, but very intricate SmartArt may still be rendered as an image.
      In those cases, consider flattening the SmartArt in Word before conversion,
      or use `pdfOptions.setExportSmartArtAsImage(true)` to force image export.
  - name: 2. “Can I combine inline and block exports in the same document?”
    text: Unfortunately the API applies the setting globally. If you need mixed behavior,
      split the document into sections, export each section separately with different
      options, then merge the PDFs using `PdfMerger`.
  - name: 3. “Does this affect font embedding?”
    text: No. Font embedding is controlled by `pdfOptions.setEmbedFullFonts(true)`
      (default). You can safely enable or disable it without touching the inline shape
      flag.
  - name: 4. “How do I verify that shapes are really `<span>`?”
    text: Open the resulting PDF in a tool like **PDF.js** or **Adobe Acrobat** →
      **Edit PDF** → **Object Inspector**. You’ll see the shape wrapped in a `<span>`
      element in the underlying XML. If you see `<div>`, the option wasn’t applied.
  type: HowTo
tags:
- Java
- PDF
- Aspose.Words
title: Exporteren van zwevende vormen inline – Complete gids voor PDF-conversie
url: /nl/java/document-conversion-and-export/export-floating-shapes-inline-complete-guide-to-pdf-conversi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vlot zwevende vormen inline exporteren – Complete gids voor PDF-conversie

Heb je ooit **export floating shapes inline** moeten doen wanneer je een Word‑document naar PDF converteert? Je bent niet de enige—veel ontwikkelaars lopen tegen dit probleem aan wanneer hun diagrammen of pictogrammen mysterieus naar aparte lagen verschuiven. Het goede nieuws is dat één enkele PDF‑optie die vormen netjes binnen `<span>`‑tags kan houden, waardoor de lay‑out exact behouden blijft zoals je die in Word ziet.

In deze tutorial lopen we stap voor stap door **hoe je PDF‑opties instelt** in Java, laten we je de exacte code zien om **save Word as PDF options** toe te passen, en leggen we uit waarom je **convert Word to PDF inline** zou willen gebruiken in plaats van de standaard blok‑niveau export. Aan het einde heb je een kant‑klaar fragment dat je in elk Maven‑ of Gradle‑project kunt plaatsen.

## Wat je zult leren

- Het verschil tussen inline `<span>` en block `<div>` export voor zwevende vormen.  
- Hoe je `PdfSaveOptions` configureert om inline rendering af te dwingen.  
- Stapsgewijze code die een `.docx` laadt, de optie toepast en een PDF wegschrijft.  
- Veelvoorkomende valkuilen (ontbrekende lettertypen, niet‑ondersteunde vormen) en hoe je ze vermijdt.  
- Tips voor het testen van de output en het uitbreiden van de aanpak naar andere documentelementen.

**Prerequisites** – je hebt Java 8 of nieuwer nodig, de Aspose.Words for Java‑bibliotheek (of een API die zijn `PdfSaveOptions`‑klasse nabootst), en een voorbeeld‑Word‑bestand met zwevende vormen (de tutorial gebruikt `FloatingShapes.docx`). Andere externe tools zijn niet vereist.

---

## Stap 1: Laad het bron‑Word‑document

Het eerste wat je doet is het `.docx`‑bestand openen dat je wilt transformeren. Dit is eenvoudig, maar zorg ervoor dat het pad absoluut is of correct wordt opgelost vanuit je classpath.

```java
import com.aspose.words.Document;

// Step 1: Load the source Word document
Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");
```

*Waarom dit belangrijk is:*  
Als het document niet correct wordt geladen, zal de daaropvolgende PDF‑conversie een `FileNotFoundException` veroorzaken. Het gebruik van `Document` zorgt ervoor dat het interne objectmodel volledig wordt gevuld, inclusief alle zwevende vormen die zich op de pagina bevinden.

---

## Stap 2: Maak PDF‑opslaan‑opties aan en stel zwevende vormen in op inline

Hier gebeurt de magie. Standaard exporteert Aspose.Words zwevende vormen als blok‑niveau `<div>`‑elementen, wat de stroom in HTML‑gebaseerde PDF’s kan breken. Het instellen van `setExportFloatingShapesAsInlineTag(true)` vertelt de engine elke vorm in een inline `<span>` te wikkelen.

```java
import com.aspose.words.PdfSaveOptions;

// Step 2: Create PDF save options and set floating shapes to be exported as inline <span> elements
PdfSaveOptions pdfOptions = new PdfSaveOptions();
pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → <span>, false → <div>
```

*Waarom dit belangrijk is:*  
- **Layout‑getrouwheid** – Inline‑tags houden de vorm uitgelijnd met de omringende tekst, waardoor ongewenste gaten worden voorkomen.  
- **Zoekbaarheid** – Inline‑elementen worden eerder correct geïndexeerd door PDF‑lezers.  
- **Stijl‑controle** – Je kunt het `<span>` met CSS targeten als je later de PDF terug naar HTML converteert.

> **Pro tip:** Als je ooit het oude blok‑gedrag voor een specifiek document nodig hebt, geef dan simpelweg `false` door of laat de aanroep weg.

---

## Stap 3: Sla het document op als PDF met de geconfigureerde opties

Nu combineer je het geladen `Document` met de `PdfSaveOptions` en schrijf je het bestand weg. Deze ene regel doet het zware werk.

```java
// Step 3: Save the document as a PDF using the configured options
doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);
```

*Waarom dit belangrijk is:*  
De `save`‑methode respecteert elke vlag die je op `pdfOptions` hebt gezet. Als je de opties vergeet door te geven, valt de export terug op de standaard blok‑export, waardoor het doel van **export floating shapes inline** teniet wordt gedaan.

---

## Volledig werkend voorbeeld

Alles bij elkaar, hier is een compact programma dat je nu kunt compileren en uitvoeren. Vervang `YOUR_DIRECTORY` door een daadwerkelijk pad op jouw machine.

```java
import com.aspose.words.*;

public class ExportFloatingShapesInlineDemo {
    public static void main(String[] args) {
        try {
            // Load the source Word document
            Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");

            // Configure PDF options to export floating shapes as inline <span>
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true);

            // Save as PDF with the above options
            doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);

            System.out.println("PDF created successfully with inline floating shapes.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Verwachte output** – Na het uitvoeren van het programma, open `FloatingShapes.pdf`. Je zou de vormen direct naast de tekst moeten zien, zonder extra witruimte, en de HTML‑representatie (als je de interne structuur van de PDF inspecteert) zal `<span>`‑tags rond elke vorm bevatten.

![Export floating shapes inline example](https://example.com/export-inline.png "Screenshot showing floating shapes rendered inline in the PDF")

*Afbeeldings‑alt‑tekst:* **export floating shapes inline** screenshot van PDF met inline‑vormen.

---

## Veelgestelde vragen & randgevallen

### 1. “Wat als mijn document complexe SmartArt bevat?”

SmartArt wordt behandeld als een tekenobject. De inline‑vlag werkt voor de meeste vectorvormen, maar zeer ingewikkelde SmartArt kan nog steeds als afbeelding worden gerenderd. Overweeg in dat geval de SmartArt in Word te flattenen vóór conversie, of gebruik `pdfOptions.setExportSmartArtAsImage(true)` om afbeeldingsexport af te dwingen.

### 2. “Kan ik inline‑ en blok‑export combineren in hetzelfde document?”

Helaas wordt de instelling globaal toegepast door de API. Als je gemengd gedrag nodig hebt, splits je het document in secties, exporteer je elke sectie afzonderlijk met verschillende opties, en voeg je vervolgens de PDF’s samen met `PdfMerger`.

### 3. “Heeft dit invloed op het insluiten van lettertypen?”

Nee. Het insluiten van lettertypen wordt geregeld door `pdfOptions.setEmbedFullFonts(true)` (standaard). Je kunt dit veilig in- of uitschakelen zonder de inline‑vormvlag aan te passen.

### 4. “Hoe verifieer ik dat vormen echt `<span>` zijn?”

Open de resulterende PDF in een tool zoals **PDF.js** of **Adobe Acrobat** → **Edit PDF** → **Object Inspector**. Je ziet de vorm gewikkeld in een `<span>`‑element in de onderliggende XML. Als je `<div>` ziet, is de optie niet toegepast.

---

## De aanpak uitbreiden – Gerelateerde opties

Terwijl je hier bent, wil je misschien ook andere PDF‑conversie‑knoppen verkennen:

| Optie | Wat het doet | Typisch gebruiks‑scenario |
|--------|--------------|---------------------------|
| `setCompressImages(true)` | Vermindert de afbeeldingsgrootte | Snellere downloads |
| `setUseHighQualityRendering(true)` | Verbetert vector‑rendering | Print‑klare PDF’s |
| `setExportDocumentStructure(true)` | Voegt structurele tags toe voor toegankelijkheid | WCAG‑conformiteit |
| `setSaveFormat(SaveFormat.PDF)` | Stelt expliciet het formaat in (zeldzaam) | Multi‑format pipelines |

Deze instellingen passen goed bij **convert word to pdf inline** scenario’s waar je zowel layout‑getrouwheid als prestaties nodig hebt.

---

## Je conversie testen

1. **Visuele controle** – Open de PDF in twee viewers (Chrome en Adobe Reader) om te bevestigen dat vormen correct uitgelijnd zijn.  
2. **Geautomatiseerde diff** – Gebruik een bibliotheek zoals `pdfbox` om de XML te extraheren en assert dat `<span>`‑tags aanwezig zijn.  
3. **Prestatie‑benchmark** – Meet de tijd met en zonder `setCompressImages` om de afweging te zien.

Een kort JUnit‑voorbeeld:

```java
@Test
public void testInlineExport() throws Exception {
    Document doc = new Document("src/test/resources/FloatingShapes.docx");
    PdfSaveOptions opts = new PdfSaveOptions();
    opts.setExportFloatingShapesAsInlineTag(true);
    ByteArrayOutputStream out = new ByteArrayOutputStream();
    doc.save(out, opts);
    String pdfXml = new String(out.toByteArray(), StandardCharsets.UTF_8);
    assertTrue(pdfXml.contains("<span"));
}
```

---

## Conclusie

Je beschikt nu over een solide, end‑to‑end oplossing voor **export floating shapes inline** wanneer je **convert Word to PDF inline**. Door `PdfSaveOptions` te configureren bepaal je welke HTML‑tag voor elke vorm wordt gebruikt, waardoor je PDF’s netjes en doorzoekbaar blijven. Vergeet niet de output te testen, gerelateerde opties zoals beeldcompressie aan te passen, en randgevallen zoals complexe SmartArt af te handelen.

Klaar voor de volgende stap? Probeer dezelfde techniek toe te passen op **export floating tables inline** of experimenteer met CSS‑gestylede PDF’s via Aspose’s `HtmlSaveOptions`. Hetzelfde patroon—laden, configureren, opslaan—geldt voor bijna elk document‑naar‑PDF‑scenario.

Heb je meer vragen over **how to set pdf options** of heb je hulp nodig met **save word as pdf options** voor een andere bibliotheek? Laat een reactie achter, en happy coding!


## Wat moet je hierna leren?


De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑features onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Convert Word to PDF with Aspose.Words for Java](/words/english/java/document-converting/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Export Word Document Structure to PDF Document](/words/english/net/programming-with-pdfsaveoptions/export-document-structure/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}