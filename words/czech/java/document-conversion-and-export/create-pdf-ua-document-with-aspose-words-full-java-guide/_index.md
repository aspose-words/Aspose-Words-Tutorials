---
category: general
date: 2026-04-28
description: Vytvořte PDF UA dokument pomocí Aspose.Words pro Javu. Naučte se načíst
  soubor DOCX s obnovou, exportovat rovnice do LaTeXu, uložit markdown z Wordu a získat
  chybějící písma.
draft: false
keywords:
- create PDF UA document
- retrieve missing fonts
- export equations to LaTeX
- save markdown from Word
- load docx with recovery
language: cs
og_description: Vytvořte PDF UA dokument pomocí Aspose.Words pro Java. Podrobný návod
  krok za krokem zahrnující načítání obnovy, export do LaTeXu, ukládání do Markdownu
  a získávání chybějících fontů.
og_title: Vytvořte PDF UA dokument – Kompletní Java tutoriál
tags:
- Aspose.Words
- Java
- PDF/UA
title: Vytvořte PDF UA dokument pomocí Aspose.Words – kompletní průvodce pro Javu
url: /cs/java/document-conversion-and-export/create-pdf-ua-document-with-aspose-words-full-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření PDF UA dokumentu – Kompletní Java tutoriál

Potřebujete **vytvořit PDF UA dokument** z Word souboru a zároveň řešit poškozený obsah? V tomto tutoriálu vás provedeme načtením DOCX v režimu obnovy, exportem rovnic do LaTeXu, uložením Markdownu z Wordu a získáním chybějících fontů – vše pomocí Aspose.Words pro Java.  

Pokud jste někdy narazili na poškozený .docx a přemýšleli, proč váš PDF není přístupný, jste na správném místě. Na konci budete mít plně vyhovující PDF/UA 1 soubor, verzi v Markdownu s LaTeX rovnicemi a přehled všech substitucí fontů, ke kterým došlo během načítání.

## Co budete potřebovat

- **Aspose.Words pro Java** (nejnovější verze k roku 2026) – přidejte Maven/Gradle závislost nebo JAR do classpath.  
- Java 17 nebo novější (API používá streamy, takže se doporučuje aktuální JDK).  
- Ukázkový soubor `input.docx`, který může obsahovat poškozené sekce, Office Math rovnice a plovoucí tvary.  

Žádné další knihovny nejsou potřeba; vše je součástí Aspose.Words.

---

## Krok 1 – Načtení DOCX v režimu obnovy  

Když je dokument částečně poškozený, výchozí načítač vyhodí výjimku. Povolením režimu obnovy řeknete Aspose.Words, aby pokračoval a místo toho vrátil varování.

```java
import com.aspose.words.*;

public class LatestFeaturesDemo {

    public static void main(String[] args) throws Exception {

        // 1️⃣ Load the document with recovery to gracefully handle corruption
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

*Proč je to důležité:* Režim obnovy zabrání přerušení celého pipeline kvůli jedné špatné odstavci. Také naplní `doc.getWarnings()`, takže později můžete **získat chybějící fonty** a další problémy.

---

## Krok 2 – Export rovnic do LaTeXu uvnitř Markdown souboru  

Většina vývojářů miluje Markdown pro dokumentaci, ale vestavěné rovnice ve Wordu jsou obtížně kopírovatelné. Aspose.Words je dokáže přímo převést do LaTeXu.

```java
        // 2️⃣ Configure Markdown export with LaTeX for Office Math
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

        // Store images in a sub‑folder so the Markdown stays tidy
        mdOptions.setResourceSavingCallback(resourceInfo -> {
            if (resourceInfo.getResourceType() == ResourceType.IMAGE) {
                resourceInfo.setResourceFileName("imgs/" + resourceInfo.getResourceFileName());
            }
        });

        // Save the Markdown file
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);
```

*Tip:* Callback zajistí, že každá extrahovaná obrázková data budou uložena pod `imgs/`. To napodobuje způsob, jakým GitHub renderuje Markdown – čistý a přenosný.

---

## Krok 3 – Vytvoření PDF / UA dokumentu s korektním označením  

PDF/UA (Universal Accessibility) kompatibilita je povinná pro mnoho veřejných projektů. Následující volby zajistí, že Aspose.Words správně označí plovoucí tvary a nastaví příznak PDF/UA kompatibility.

```java
        // 3️⃣ Prepare PDF/UA export options
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);          // Enforce PDF/UA‑1
        pdfOptions.setExportFloatingShapesAsInlineTag(true);      // Tag floating shapes

        // Save the accessible PDF
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);
```

*Co uvidíte:* Otevřením `output.pdf` v Adobe Acrobat Pro se v vlastnostech dokumentu zobrazí „PDF/UA‑1 compliant“. Všechny plovoucí tvary (textové rámečky, obrázky) budou mít odpovídající tagy pro čtečky obrazovky.

---

## Krok 4 – Úprava stínu tvaru (volitelné stylování)  

I když to není nutné pro přístupnost, úprava vizuálních aspektů může být užitečná pro interní zprávy.

```java
        // 4️⃣ Grab the first shape and modify its shadow
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        ShadowFormat shadow = firstShape.getShadowFormat();
        shadow.setBlurRadius(4);
        shadow.setDistanceX(2);
        shadow.setDistanceY(2);
        shadow.setColor(java.awt.Color.GRAY);
```

*Proč to dělat?* Pokud je PDF také marketingovým materiálem, jemný stín dodá rozvržení profesionální vzhled, aniž by porušil kompatibilitu.

---

## Krok 5 – Získání chybějících fontů a dalších varování  

Během načítání v režimu obnovy Aspose.Words zaznamená všechny substituce fontů. Jejich výpis vám pomůže rozhodnout, zda vložit správný font nebo akceptovat náhradní.

```java
        // 5️⃣ Enumerate font‑substitution warnings
        System.out.println("=== Font Substitution Report ===");
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsw = (FontSubstitutionWarning) warning;
                System.out.println("Missing: " + fsw.getMissingFontName() +
                                   " → substituted: " + fsw.getSubstitutedFontName());
            }
        }

        // You can also handle other warning types here (e.g., content loss)
    }
}
```

*Typický výstup* (vaše konzole zobrazí něco jako):

```
=== Font Substitution Report ===
Missing: Calibri → substituted: Arial
Missing: Times New Roman → substituted: Liberation Serif
```

Pokud uvidíte kritické chybějící fonty, zvažte jejich instalaci na server nebo vložení pomocí `PdfSaveOptions.setEmbedFullFonts(true)`.

---

## Kompletní funkční příklad  

Níže je kompletní, připravená Java třída. Vložte ji do svého IDE, upravte cesty a spusťte **Run**.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to:
 *  • load a DOCX with recovery,
 *  • export equations to LaTeX inside Markdown,
 *  • create a PDF/UA‑1 compliant PDF,
 *  • modify shape shadows,
 *  • and list any font‑substitution warnings.
 */
public class LatestFeaturesDemo {
    public static void main(String[] args) throws Exception {

        // ---- Step 1: Load DOCX with recovery ----
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // ---- Step 2: Export equations to LaTeX in Markdown ----
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        mdOptions.setResourceSavingCallback(resourceInfo -> {
            if (resourceInfo.getResourceType() == ResourceType.IMAGE) {
                resourceInfo.setResourceFileName("imgs/" + resourceInfo.getResourceFileName());
            }
        });
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);

        // ---- Step 3: Save as PDF/UA with proper tagging ----
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);

        // ---- Step 4: Optional – adjust the first shape’s shadow ----
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        ShadowFormat shadow = firstShape.getShadowFormat();
        shadow.setBlurRadius(4);
        shadow.setDistanceX(2);
        shadow.setDistanceY(2);
        shadow.setColor(Color.getGray());

        // ---- Step 5: List any missing‑font warnings ----
        System.out.println("=== Font Substitution Report ===");
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsw = (FontSubstitutionWarning) warning;
                System.out.println("Missing: " + fsw.getMissingFontName()
                                   + " → substituted: " + fsw.getSubstitutedFontName());
            }
        }
    }
}
```

**Očekávané výsledky**

| Výstup | Popis |
|--------|-------|
| `output.md` | Markdown soubor, kde se každá Office Math rovnice objeví jako LaTeX (`$…$`). Obrázky jsou uloženy pod `imgs/`. |
| `output.pdf` | PDF/UA‑1 kompatibilní dokument; otevřete v Acrobat a uvidíte „PDF/UA‑1“ v Soubor → Vlastnosti → Standardy. |
| Konzole | Seznam chybějících fontů, např. „Missing: Calibri → substituted: Arial“. |

---

## Často kladené otázky (FAQ)

**Q: Funguje to se staršími verzemi Aspose.Words?**  
A: Enumy `RecoveryMode`, `OfficeMathExportMode.LATEX` a `PdfCompliance.PDF_UA_1` byly zavedeny ve verzi 22.8. Pokud používáte starší verzi, aktualizujte – funkce přístupnosti nejsou zpětně portovány.

**Q: Co když potřebuji vložit původní fonty místo substituce?**  
A: Nastavte `pdfOptions.setEmbedFullFonts(true)` a ujistěte se, že soubory fontů jsou dostupné v cestě fontů JVM.

**Q: Můžu exportovat do jiných značkovacích formátů (např. HTML) a zachovat LaTeX rovnice?**  
A: Ano. Použijte `HtmlSaveOptions` a nastavte `setOfficeMathExportMode(OfficeMathExportMode.LATEX)` – stejný enum funguje napříč formáty.

**Q: Můj DOCX obsahuje mnoho plovoucích tvarů; budou všechny označeny?**  
A: S `setExportFloatingShapesAsInlineTag(true)` Aspose.Words zabalí každý plovoucí tvar do tagu `<Figure>` pro PDF/UA, což vyhovuje většině kontrol čteček obrazovky.

---

## Závěr  

Ukázali jsme vám, jak **vytvořit PDF UA dokument** ze zdroje Word, zároveň **načíst docx s obnovou**, **exportovat rovnice do LaTeXu**, **uložit markdown z Wordu** a **získat chybějící fonty**. Kód je zcela samostatný, běží na jakémkoli prostředí Java 17+ a vytváří výstupy připravené jak pro audity přístupnosti, tak pro vývojáře.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}