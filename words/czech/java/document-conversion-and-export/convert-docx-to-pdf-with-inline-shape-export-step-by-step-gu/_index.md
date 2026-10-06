---
category: general
date: 2026-02-18
description: Naučte se, jak převést DOCX na PDF a uložit Word jako PDF při zachování
  plovoucích tvarů. Tento průvodce ukazuje, jak správně exportovat tvary.
draft: false
keywords:
- convert docx to pdf
- save word as pdf
- how to export shapes
language: cs
og_description: Převést DOCX na PDF a naučte se, jak exportovat tvary. Sledujte tento
  kompletní návod, jak uložit Word jako PDF se správným označováním.
og_title: Převod DOCX na PDF – Průvodce exportem vložených tvarů
tags:
- Aspose.Words
- Java
- PDF conversion
title: Převod DOCX do PDF s exportem vložených tvarů – krok za krokem
url: /cs/java/document-conversion-and-export/convert-docx-to-pdf-with-inline-shape-export-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Převod DOCX na PDF – Průvodce exportem vložených tvarů

Už jste někdy potřebovali **převést DOCX na PDF**, ale obávali se, že vaše plovoucí obrázky nebo textová pole zmizí nebo se posunou? Nejste v tom sami. V mnoha projektech – například automatizovaných generátorech zpráv nebo dávkových zpracovacích pipelinech – je zachování přesného rozvržení dokumentu Word naprosto nezbytné.  

Dobrá zpráva? Několik řádků kódu vám umožní **uložit Word jako PDF** a řídit, zda se tyto plovoucí tvary exportují jako inline značky nebo zůstanou jako blokové elementy. Níže uvidíte přesně **jak exportovat tvary** tak, jak chcete, a také několik tipů, které vás ochrání před běžnými úskalími.

---

## Co se naučíte

* Načíst soubor `.docx` z disku.  
* Nakonfigurovat `PdfSaveOptions`, aby plovoucí tvary byly exportovány jako inline značky.  
* Zapsat výsledné PDF do složky dle vašeho výběru.  
* Pochopit, proč je důležitý příznak `setExportFloatingShapesAsInlineTag` a kdy jej můžete přepnout.  

Žádné externí služby, žádné magické „klikni‑pro‑stažení“ UI – jen čistý Java kód, který můžete vložit do libovolného Maven nebo Gradle projektu.

---

## Požadavky

| Požadavek | Proč je důležitý |
|-------------|----------------|
| **Aspose.Words for Java** (v23.12 nebo novější) | Poskytuje třídy `Document` a `PdfSaveOptions` použité v příkladu. |
| **JDK 8+** | Knihovna je zkompilována pro Java 8 a novější; starší runtime vyhodí `UnsupportedClassVersionError`. |
| **DOCX soubor** s alespoň jedním plovoucím tvarem (obrázek, textové pole, WordArt) | Aby bylo vidět, jak funguje volba exportu tvarů, potřebujete dokument, který skutečně obsahuje plovoucí objekty. |

Pokud už máte všechny tyto součásti, skvěle – pojďme na to.

---

## Krok 1 – Načtení zdrojového dokumentu  

Nejprve vytvoříme instanci `Document`, která ukazuje na `.docx`, který chcete převést. Konstruktor načte soubor do paměti, rozparsuje OpenXML balíček a připraví interní objektový model.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

// Adjust the path to your environment
String inputPath = "YOUR_DIRECTORY/input.docx";

Document doc = new Document(inputPath);
```

> **Pro tip:** Pokud zpracováváte mnoho souborů v cyklu, znovu použijte jediný objekt `Document` až po volání `doc.close()` (nebo nechte ošetřit garbage collectorem). Tím zabráníte únikům souborových handle na Windows.

---

## Krok 2 – Nastavení PDF Save Options pro export tvarů  

Srdce tutoriálu je zde. `PdfSaveOptions` vám umožní určit, jak se konverze chová. Nastavení `setExportFloatingShapesAsInlineTag(true)` vynutí, aby každý plovoucí tvar byl v PDF strukturován jako *inline* element. To znamená, že čtečky obrazovky přečtou tvar ve stejném pořadí jako okolní text, což je často vyžadováno pro splnění přístupnosti.

```java
import com.aspose.words.PdfSaveOptions;

PdfSaveOptions pdfOptions = new PdfSaveOptions();
// true → inline tagging (shape behaves like a character)
// false → block‑level tagging (shape sits in its own block)
pdfOptions.setExportFloatingShapesAsInlineTag(true);
```

**Kdy byste to nastavili na `false`?**  
Pokud je vaše PDF určeno jen pro tisk a chcete, aby tvary zachovaly původní pozicování bez ovlivnění logického pořadí čtení, můžete upřednostnit blokové tagování. Výchozí hodnota je `false`, takže pro tento tutoriál explicitně povolujeme inline chování.

---

## Krok 3 – Uložení dokumentu jako PDF  

Jakmile jsou možnosti připraveny, zavolejte `save` s cílovým názvem souboru a objektem možností. Knihovna provede těžkou práci: layout engine, vložení fontů a generování tagů.

```java
String outputPath = "YOUR_DIRECTORY/shapes.pdf";
doc.save(outputPath, pdfOptions);
```

Po dokončení volání najdete `shapes.pdf` ve zvolené složce. Otevřete jej v Adobe Acrobat nebo jiném PDF prohlížeči, který zobrazuje tagy (obvykle pod **File → Properties → Tags**) a uvidíte, že plovoucí tvar je označen jako inline tag.

---

## Kompletní, spustitelný příklad  

Spojíme vše dohromady – zde je samostatná Java třída, kterou můžete zkompilovat a spustit. Ujistěte se, že je Aspose.Words JAR na classpath.

```java
import com.aspose.words.*;

public class DocxToPdfWithShapes {
    public static void main(String[] args) {
        try {
            // 1️⃣ Load the source DOCX
            String inputPath = "YOUR_DIRECTORY/input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Configure PDF options – export floating shapes as inline tags
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → inline tagging

            // 3️⃣ Save as PDF
            String outputPath = "YOUR_DIRECTORY/shapes.pdf";
            doc.save(outputPath, pdfOptions);

            System.out.println("✅ Conversion complete! PDF saved to: " + outputPath);
        } catch (Exception e) {
            System.err.println("❌ Something went wrong: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Očekávaný výsledek:**  
- PDF soubor obsahuje stejný textový obsah jako původní DOCX.  
- Veškeré plovoucí obrázky nebo textová pole jsou nyní označeny *inline*, což znamená, že se objevují v pořadí čtení místo samostatných bloků.  
- Pokud otevřete panel **Tags** v PDF, uvidíte element `<Figure>` vložený do `<Paragraph>` – přesně to, co `setExportFloatingShapesAsInlineTag(true)` zaručuje.

---

## Často kladené otázky a okrajové případy  

### 1️⃣ Funguje to s dokumenty DOCX chráněnými heslem?  
Ano – stačí před načtením zadat heslo:

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setPassword("mySecret");
Document doc = new Document(inputPath, loadOptions);
```

### 2️⃣ Co když Word soubor obsahuje SVG nebo EMF obrázky?  
Aspose.Words automaticky rasterizuje vektorovou grafiku při ukládání do PDF. Pokud potřebujete, aby zůstaly vektorové, nastavte:

```java
pdfOptions.setRasterizeTransformedElements(false);
```

### 3️⃣ Jak zachovat hypertextové odkazy při konverzi?  
Odkazy jsou zachovány ve výchozím nastavení. Pokud však vypnete tagy (`pdfOptions.setSaveFormat(SaveFormat.PDF)` bez možností), můžete ztratit logickou strukturu. Uchovejte objekt `PdfSaveOptions`, aby byly zachovány jak tagy, tak odkazy.

### 4️⃣ Můžu dávkově zpracovat složku DOCX souborů?  
Určitě. Zabalte logiku `DocxToPdfWithShapes` do cyklu, který iteruje přes `Files.list(Paths.get("YOUR_DIRECTORY"))`. Nezapomeňte ošetřit výjimky pro každý soubor, aby jeden špatný dokument nezastavil celý běh.

---

## Tipy z praxe  

* **Dávejte pozor na chybějící fonty.** Pokud zdrojový DOCX používá vlastní font, který není nainstalován na serveru, PDF použije náhradní, což může rozbít rozvržení. Použijte `pdfOptions.setFontEmbeddingMode(FontEmbeddingMode.EMBED_ALL)`, aby se všechny fonty vložily.  
* **Testování přístupnosti.** Po konverzi spusťte **Accessibility Checker** v Acrobat. Inline tagování obvykle zlepšuje skóre, ale může být potřeba ručně doplnit alternativní text k obrázkům.  
* **Tip pro výkon:** U velkých dokumentů (100+ stran) povolte `pdfOptions.setMemoryOptimization(true)`, aby se snížila spotřeba haldy.

---

## Vizuelní potvrzení  

Níže je rychlý snímek PDF otevřeného v Adobe Acrobat, zobrazující inline‑tagovaný tvar zvýrazněný v panelu **Tags**.

![Convert DOCX to PDF example output](image.png)

*Alt text: příklad výstupu převodu docx na pdf zobrazující inline tagy tvarů.*

---

## Závěr  

Nyní víte **jak převést DOCX na PDF** a zároveň řídit, jak jsou exportovány plovoucí objekty. Přepínáním `setExportFloatingShapesAsInlineTag` rozhodujete, zda se tvary stanou součástí pořadí čtení nebo zůstanou jako nezávislé bloky – klíčové jak pro přístupnost, tak pro vizuální věrnost.  

Odtud můžete:

* **Ukládat Word jako PDF** hromadně pro archivaci.  
* Experimentovat s dalšími `PdfSaveOptions`, jako je `setCompliance(PdfCompliance.PDF_A_1B)` pro dlouhodobou archivaci.  
* Prohloubit **export tvarů** prozkoumáním kompletní dokumentace Aspose.Words nebo vyzkoušením příznaku `setExportDocumentStructure(true)` pro bohatší strom tagů.

Vyzkoušejte to, upravte možnosti a nechte své PDF vypadat přesně tak, jak potřebujete. Šťastné kódování!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}