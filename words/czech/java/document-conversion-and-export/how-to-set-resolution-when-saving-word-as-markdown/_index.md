---
category: general
date: 2026-05-04
description: Jak nastavit rozlišení při exportu Markdownu z Wordu. Naučte se rozlišení
  obrázků v markdownu, jak exportovat rovnice a uložit Word jako markdown v Javě.
draft: false
keywords:
- how to set resolution
- markdown image resolution
- how to use markdown
- how to export equations
- save word as markdown
language: cs
og_description: Jak nastavit rozlišení pro export do Markdownu z Wordu. Tento průvodce
  ukazuje rozlišení obrázků v Markdownu, export rovnic a ukládání Wordu jako Markdown.
og_title: Jak nastavit rozlišení při ukládání Wordu jako Markdown
tags:
- Aspose.Words
- Java
- Markdown
- Document Export
title: Jak nastavit rozlišení při ukládání Wordu jako Markdown
url: /cs/java/document-conversion-and-export/how-to-set-resolution-when-saving-word-as-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak nastavit rozlišení při ukládání Wordu jako Markdown

Už jste se někdy zamýšleli **jak nastavit rozlišení** pro obrázky, které se objevují v Markdown souboru vygenerovaném z dokumentu Word? Nejste v tom sami. Mnoho vývojářů narazí na problém, když výchozí rasterizované matematické obrázky vypadají rozmazaně, zejména na obrazovkách s vysokým DPI.

V tomto tutoriálu projdeme přesně kroky, jak ovládat *markdown image resolution*, zároveň ukážeme **jak exportovat rovnice** jako LaTeX a nakonec **jak uložit Word jako markdown** pomocí Aspose.Words for Java. Na konci budete mít ostrý, připravený pro produkci Markdown soubor, který čistě vykresluje rovnice a obrázky v požadované kvalitě.

## Prerequisites

- Java 17 (nebo jakýkoli aktuální JDK)  
- Aspose.Words for Java 23.6 nebo novější – můžete jej získat z Maven Central  
- Dokument Word (`.docx`), který obsahuje objekty OfficeMath (rovnice) a případně rastrové obrázky  
- Základní znalost Maven/Gradle a IDE (IntelliJ IDEA, Eclipse, VS Code, atd.)

Žádné další knihovny nejsou potřeba; vše ostatní zajišťuje Aspose.Words.

---

## How to Set Resolution for Markdown Export

**Tip:** Rozlišení, které zvolíte, přímo ovlivňuje velikost souboru generovaných obrázků. Hodnota **300 dpi** je dobrá rovnováha pro většinu webových Markdown prohlížečů.

```java
// Step 1: Load the source Word document containing equations
Document doc = new Document("YOUR_DIRECTORY/Math.docx");

// Step 2: Create Markdown save options to control the export behavior
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();

// Step 3: Export OfficeMath objects as LaTeX expressions
saveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

// Step 4 (optional): Set image resolution for any rasterized Math images
saveOptions.setImageResolution(300);   // <-- this is where we set the resolution

// Step 5: Save the document as a Markdown file using the configured options
doc.save("YOUR_DIRECTORY/MathExport.md", saveOptions);
```

Volání `setImageResolution(int dpi)` je jádrem **jak nastavit rozlišení**. Říká Aspose.Words, aby rasterizoval jakékoli záložní obrázky (např. když nelze rovnici vyjádřit čistým LaTeXem) s uvedeným počtem bodů na palec. Pokud tuto řádku vynecháte, knihovna použije výchozí 220 dpi, což může na Retina displejích vypadat rozmazaně.

### Why Use LaTeX for Equations?

Když exportujete rovnice jako LaTeX (`OfficeMathExportMode.LATEX`), výsledný Markdown obsahuje surový LaTeX kód vložený do `$…$` nebo `$$…$$`. Většina moderních Markdown rendererů (GitHub, GitLab, MkDocs s MathJax) je vykreslí jako ostrou, škálovatelnou vektorovou grafiku – žádné starosti s rozlišením. Nastavení rozlišení má smysl jen pro **markdown image resolution** jakýchkoli rasterových záložních obrázků, jako jsou vložené grafy nebo obrázky, které nejsou v Markdownu nativně podporovány.

## How to Use Markdown Image Resolution Effectively

Pokud potřebujete vložit běžné obrázky (např. snímky obrazovky) do vašeho Word souboru, Aspose.Words je převede na PNG. Stejná metoda `setImageResolution` se použije, aby tyto PNG zdědily DPI, které zadáte. Zde je rychlý kontrolní seznam:

1. **Zvolte DPI, které odpovídá vaší cílové platformě** – 72 dpi pro starší web, 150 dpi pro standardní displeje, 300 dpi pro PDF v tiskové kvalitě.  
2. **Otestujte výstup** – otevřete vygenerovaný soubor `.md` ve svém oblíbeném prohlížeči a přibližte, abyste ověřili ostrost.  
3. **Zvažte velikost souboru** – vyšší DPI vede k větším PNG; pokud je šířka pásma problém, vyzkoušejte 200 dpi a porovnejte.

## How to Export Equations as LaTeX

Řádek `saveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);` říká Aspose.Words, aby přeložil každý objekt OfficeMath do LaTeXu. Toto je doporučený přístup, protože:

- **Škálovatelnost** – LaTeX se vykresluje v jakékoli velikosti bez ztráty kvality.  
- **Upravitelnost** – Můžete později přímo upravit LaTeX v Markdown souboru.  
- **Kompatibilita** – Většina generátorů statických stránek a nástrojů pro dokumentaci již podporuje vykreslování LaTeXu.

Pokud někdy potřebujete starý záložní obrázek, stačí přepnout na `OfficeMathExportMode.IMAGE`. V takovém případě se nastavené rozlišení stává ještě důležitějším.

## Save Word as Markdown – Full End‑to‑End Example

Níže je kompletní, spustitelný úryvek Maven projektu, který demonstruje celý proces, od deklarace závislostí po spuštění.

```xml
<!-- pom.xml -->
<project xmlns="http://maven.apache.org/POM/4.0.0" ...>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>markdown-export</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.6</version>
        </dependency>
    </dependencies>
</project>
```

```java
// src/main/java/com/example/MarkdownMathExport.java
package com.example;

import com.aspose.words.*;

public class MarkdownMathExport {
    public static void main(String[] args) throws Exception {
        // Load the source Word document containing equations and images
        Document doc = new Document("src/main/resources/Math.docx");

        // Configure Markdown export options
        MarkdownSaveOptions options = new MarkdownSaveOptions();
        options.setOfficeMathExportMode(OfficeMathExportMode.LATEX); // export equations as LaTeX
        options.setImageResolution(300); // set resolution for rasterized images

        // Save as Markdown
        doc.save("output/MathExport.md", options);

        System.out.println("✅ Markdown export complete! Check output/MathExport.md");
    }
}
```

**Očekávaný výsledek:** `MathExport.md` bude obsahovat LaTeX bloky pro každou rovnici a všechny vložené obrázky se objeví jako PNG odkazy s DPI 300. Otevřete soubor v Markdown prohlížeči, který podporuje MathJax (např. VS Code s rozšířením Markdown Preview Enhanced) a měli byste vidět dokonale ostré rovnice i obrázky.

## Common Questions & Edge Cases

### What if I need a different DPI for only one image?

Aspose.Words aplikuje DPI globálně pomocí `setImageResolution`. Pro nastavení DPI jen pro jeden obrázek byste museli po‑zpracovat vygenerovaný Markdown: nahradit PNG soubory verzemi s vyšším rozlišením a ručně upravit odkazy na obrázky. Není to ideální, ale proveditelné pro několik speciálních případů.

### Does this work on Linux/macOS?

Ano. Knihovna je čistě Java, takže stejný kód běží kdekoliv, kde je JDK. Jen se ujistěte, že cesty k souborům používají dopředná lomítka nebo `Paths.get(...)` pro platformově nezávislé zpracování.

### What about SVG output?

Pokud dáváte přednost vektorovým obrázkům pro grafy, můžete nastavit `saveOptions.setExportImagesAsSvg(true);`. SVG ignorují DPI, takže problém **markdown image resolution** zmizí. Nicméně ne všechny Markdown renderery SVG dobře zvládají, proto nejprve otestujte cílovou platformu.

### Can I embed the generated Markdown into a static site generator?

Ano. Výstup je prostý `.md` se standardní syntaxí Markdown a LaTeX oddělovači. Většina generátorů (Jekyll, Hugo, MkDocs) jej přijme bez úprav. Jen nezapomeňte povolit MathJax nebo KaTeX v konfiguraci vašeho webu.

## Conclusion

Probrali jsme **jak nastavit rozlišení** pro obrázky při **ukládání Wordu jako markdown**, prozkoumali nuance **markdown image resolution**, ukázali **jak exportovat rovnice** jako LaTeX a představili kompletní Java implementaci. Úpravou `setImageResolution` a výběrem správného `OfficeMathExportMode` získáte přesnou kontrolu nad vizuální věrností i velikostí souboru.

Jste připraveni na další krok? Zkuste kombinovat tento přístup s Aspose.PDF pro přímou konverzi stejného Word zdroje do PDF, nebo experimentujte s `setExportImagesAsSvg(true)` pro vektorovou grafiku. Techniky, které jste se zde naučili, jsou stavebními kameny pro jakýkoli automatizovaný dokumentační pipeline.

Pokud vám tento návod přišel užitečný, dejte mu hvězdičku na GitHubu, sdílejte ho s kolegy nebo zanechte komentář níže s vašimi tipy. Šťastné kódování!  

![Příklad nastavení rozlišení](resolution.png "Jak nastavit rozlišení při ukládání Wordu jako Markdown")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}