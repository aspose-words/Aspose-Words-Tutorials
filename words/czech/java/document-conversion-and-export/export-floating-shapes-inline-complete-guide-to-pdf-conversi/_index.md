---
category: general
date: 2026-07-03
description: Exportujte plovoucí tvary jako vložené při převodu Wordu do PDF. Naučte
  se, jak nastavit možnosti PDF a uložit Word jako PDF v Javě.
draft: false
keywords:
- export floating shapes inline
- convert word to pdf inline
- how to set pdf options
- save word as pdf options
language: cs
og_description: Exportujte plovoucí tvary jako vložené při převodu dokumentu Word
  do PDF. Tento tutoriál ukazuje, jak nastavit možnosti PDF a uložit Word jako PDF
  s nastavenými možnostmi.
og_title: Exportovat plovoucí tvary inline – Průvodce konverzí PDF v Javě
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
title: Export plovoucích tvarů inline – Kompletní průvodce konverzí do PDF
url: /cs/java/document-conversion-and-export/export-floating-shapes-inline-complete-guide-to-pdf-conversi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Export Floating Shapes Inline – Kompletní průvodce konverzí do PDF

Už jste někdy potřebovali **exportovat plovoucí tvary inline**, když převádíte dokument Word do PDF? Nejste v tom sami – mnoho vývojářů narazí na tento problém, když se jejich diagramy nebo ikony záhadně přesunou na samostatné vrstvy. Dobrou zprávou je, že jediná volba PDF může udržet tyto tvary uvnitř `<span>` značek, čímž zachová rozvržení přesně tak, jak jej vidíte ve Wordu.

V tomto tutoriálu vás provedeme **nastavením PDF možností** v Javě, ukážeme vám přesný kód pro **uložení Wordu jako PDF s možnostmi** a vysvětlíme, proč byste mohli chtít **převádět Word do PDF inline** místo výchozího exportu na úrovni bloků. Na konci budete mít připravený úryvek kódu, který můžete vložit do jakéhokoli Maven nebo Gradle projektu.

## Co se naučíte

- Rozdíl mezi inline `<span>` a block `<div>` exportem pro plovoucí tvary.  
- Jak nakonfigurovat `PdfSaveOptions`, aby vynutil inline vykreslování.  
- Krok‑za‑krokem kód, který načte `.docx`, použije volbu a zapíše PDF.  
- Časté úskalí (chybějící fonty, nepodporované tvary) a jak se jim vyhnout.  
- Tipy na testování výstupu a rozšíření přístupu na další elementy dokumentu.

**Předpoklady** – budete potřebovat Java 8 nebo novější, knihovnu Aspose.Words for Java (nebo jakékoli API, které má třídu `PdfSaveOptions`) a ukázkový Word soubor s plovoucími tvary (v tutoriálu se používá `FloatingShapes.docx`). Žádné další externí nástroje nejsou vyžadovány.

---

## Krok 1: Načtení zdrojového Word dokumentu

První věc, kterou uděláte, je otevřít `.docx`, který chcete převést. Je to jednoduché, ale ujistěte se, že cesta je absolutní nebo správně vyřešená z classpath.

```java
import com.aspose.words.Document;

// Step 1: Load the source Word document
Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");
```

*Proč je to důležité:*  
Pokud se dokument nenačte správně, následná konverze do PDF vyhodí `FileNotFoundException`. Použití `Document` zajistí, že interní objektový model je plně naplněn, včetně všech plovoucích tvarů, které jsou na stránce.

---

## Krok 2: Vytvoření PDF Save Options a nastavení plovoucích tvarů jako inline

Zde se děje kouzlo. Ve výchozím nastavení Aspose.Words exportuje plovoucí tvary jako blok‑úrovňové `<div>` elementy, což může narušit tok v HTML‑založených PDF. Volání `setExportFloatingShapesAsInlineTag(true)` říká enginu, aby každý tvar zabalil do inline `<span>`.

```java
import com.aspose.words.PdfSaveOptions;

// Step 2: Create PDF save options and set floating shapes to be exported as inline <span> elements
PdfSaveOptions pdfOptions = new PdfSaveOptions();
pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → <span>, false → <div>
```

*Proč je to důležité:*  
- **Věrnost rozvržení** – Inline značky udržují tvar zarovnaný s okolním textem, čímž se vyhnou nežádoucím mezerám.  
- **Vyhledatelnost** – Inline elementy jsou pravděpodobně lépe indexovatelné PDF čtečkami.  
- **Kontrola stylování** – Můžete cílit na `<span>` pomocí CSS, pokud později převádíte PDF zpět do HTML.

> **Tip:** Pokud někdy potřebujete staré blokové chování pro konkrétní dokument, jednoduše předáte `false` nebo volání úplně vynecháte.

---

## Krok 3: Uložení dokumentu jako PDF s nakonfigurovanými možnostmi

Nyní spojíte načtený `Document` s `PdfSaveOptions` a soubor zapíšete. Tento jediný řádek vykoná těžkou práci.

```java
// Step 3: Save the document as a PDF using the configured options
doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);
```

*Proč je to důležité:*  
Metoda `save` respektuje každou vlajku, kterou jste nastavili na `pdfOptions`. Zapomenutí předat možnosti vrátí výchozí blokový export, čímž zruší účel **exportu plovoucích tvarů inline**.

---

## Kompletní funkční příklad

Sestavením všeho dohromady získáte kompaktní program, který můžete právě teď zkompilovat a spustit. Nahraďte `YOUR_DIRECTORY` skutečnou cestou na vašem počítači.

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

**Očekávaný výstup** – Po spuštění programu otevřete `FloatingShapes.pdf`. Měli byste vidět tvary těsně u textu, žádné extra bílé místo a HTML reprezentace (pokud prozkoumáte vnitřní strukturu PDF) bude obsahovat `<span>` značky kolem každého tvaru.

![Export floating shapes inline example](https://example.com/export-inline.png "Screenshot showing floating shapes rendered inline in the PDF")

*Alt text obrázku:* **export floating shapes inline** screenshot PDF s inline tvary.

---

## Časté otázky a okrajové případy

### 1. „Co když můj dokument obsahuje složitý SmartArt?“

SmartArt je zpracován jako kreslicí objekt. Inline příznak funguje pro většinu vektorových tvarů, ale velmi komplikovaný SmartArt může být stále renderován jako obrázek. V takových případech zvažte před konverzí v Wordu zploštění SmartArtu, nebo použijte `pdfOptions.setExportSmartArtAsImage(true)`, aby se vynutil export jako obrázek.

### 2. „Mohu kombinovat inline a block exporty ve stejném dokumentu?“

Bohužel API aplikuje nastavení globálně. Pokud potřebujete smíšené chování, rozdělte dokument na sekce, exportujte každou sekci zvlášť s různými možnostmi a poté sloučte PDF pomocí `PdfMerger`.

### 3. „Ovlivňuje to vkládání fontů?“

Ne. Vkládání fontů řídí `pdfOptions.setEmbedFullFonts(true)` (výchozí). Můžete jej bezpečně zapnout nebo vypnout, aniž byste zasahovali do příznaku inline tvarů.

### 4. „Jak ověřím, že tvary jsou opravdu `<span>`?“

Otevřete výsledné PDF v nástroji jako **PDF.js** nebo **Adobe Acrobat** → **Edit PDF** → **Object Inspector**. Uvidíte tvar zabalený v `<span>` elementu v podkladovém XML. Pokud uvidíte `<div>`, volba nebyla aplikována.

---

## Rozšíření přístupu – související možnosti

Zatímco jste zde, možná budete chtít prozkoumat i další „knoflíky“ pro konverzi PDF:

| Možnost | Co dělá | Typické použití |
|--------|----------|-----------------|
| `setCompressImages(true)` | Snižuje velikost obrázků | Rychlejší stahování |
| `setUseHighQualityRendering(true)` | Zlepšuje vykreslování vektorů | PDF připravené k tisku |
| `setExportDocumentStructure(true)` | Přidává strukturální značky pro přístupnost | Soulad s WCAG |
| `setSaveFormat(SaveFormat.PDF)` | Explicitně nastaví formát (zřídka potřeba) | Víceformátové pipeline |

Tyto nastavení se dobře doplňují k **convert word to pdf inline** scénářům, kde potřebujete jak věrnost rozvržení, tak výkon.

---

## Testování vaší konverze

1. **Vizuální kontrola** – Otevřete PDF ve dvou prohlížečích (Chrome a Adobe Reader) a ověřte, že se tvary zarovnaly.  
2. **Automatizovaný diff** – Použijte knihovnu jako `pdfbox` k extrakci XML a ověřte přítomnost `<span>` značek.  
3. **Benchmark výkonu** – Změřte čas s a bez `setCompressImages`, abyste viděli kompromis.

Rychlý JUnit příklad:

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

## Závěr

Nyní máte robustní end‑to‑end řešení pro **export plovoucích tvarů inline**, když **převádíte Word do PDF inline**. Konfigurací `PdfSaveOptions` řídíte HTML značku použité pro každý tvar, čímž udržujete PDF přehledná a vyhledatelná. Nezapomeňte výstup otestovat, upravit související volby jako kompresi obrázků a řešit okrajové případy jako složitý SmartArt.

Jste připraveni na další krok? Vyzkoušejte stejnou techniku pro **export plovoucích tabulek inline** nebo experimentujte s PDF stylovanými pomocí CSS pomocí `HtmlSaveOptions` od Aspose. Stejný vzor – načíst, nakonfigurovat, uložit – platí pro téměř každý scénář převodu dokumentu do PDF.

Máte další otázky ohledně **jak nastavit pdf možnosti** nebo potřebujete pomoc s **save word as pdf options** pro jinou knihovnu? Zanechte komentář a šťastné kódování!

## Co se naučíte dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční kódové příklady s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [Convert Word to PDF with Aspose.Words for Java](/words/english/java/document-converting/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Export Word Document Structure to PDF Document](/words/english/net/programming-with-pdfsaveoptions/export-document-structure/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}