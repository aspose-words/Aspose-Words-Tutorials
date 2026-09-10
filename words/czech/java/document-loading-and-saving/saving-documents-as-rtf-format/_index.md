---
date: 2025-12-24
description: Naučte se, jak převést Word na RTF pomocí Aspose.Words pro Javu. Tento
  krok‑za‑krokem návod ukazuje načtení souboru DOCX, nastavení možností uložení RTF
  a uložení jako formát rich text.
linktitle: Saving Documents as RTF Format
second_title: Aspose.Words Java Document Processing API
title: Převod Wordu na RTF pomocí tutoriálu Aspose.Words pro Java
url: /cs/java/document-loading-and-saving/saving-documents-as-rtf-format/
weight: 23
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Převod Wordu do RTF pomocí Aspose.Words pro Java

V tomto tutoriálu se naučíte **jak převést Word do RTF** rychle a spolehlivě pomocí Aspose.Words pro Java. Převod DOCX do formátu bohatého textu RTF je běžná potřeba, když potřebujete širokou kompatibilitu se staršími textovými procesory, e‑mailovými klienty nebo systémy pro archivaci dokumentů. Provedeme vás načtením Word dokumentu v Javě, úpravou možností uložení RTF (včetně ukládání obrázků jako WMF) a nakonec zápisem výstupního souboru.

## Rychlé odpovědi
- **Co znamená „convert word to rtf“?** Převádí soubor DOCX/Word do formátu Rich Text Format při zachování textu, stylů a volitelně obrázků.  
- **Potřebuji licenci?** Bezplatná zkušební verze funguje pro vývoj; pro produkci je vyžadována komerční licence.  
- **Která verze Javy je podporována?** Aspose.Words pro Java podporuje Java 8 a vyšší.  
- **Mohu při převodu zachovat obrázky?** Ano – použijte možnost `saveImagesAsWmf` pro vložení obrázků jako WMF do RTF.  
- **Jak dlouho převod trvá?** Obvykle méně než sekunda pro standardní dokumenty; větší soubory mohou trvat několik sekund.

## Co je „convert word to rtf“?
Převod Word dokumentu do RTF vytvoří platformově nezávislý soubor, který ukládá text, formátování a volitelně obrázky v textovém značkovacím jazyce. To umožňuje zobrazit dokument téměř v jakémkoli textovém procesoru bez ztráty rozvržení.

## Proč použít Aspose.Words pro Java k uložení jako rich text?
- **Full fidelity** – Všechny funkce Wordu (styly, tabulky, záhlaví/patičky) jsou zachovány.  
- **No Microsoft Office required** – Není vyžadov Microsoft Office – funguje na jakémkoli serveru nebo cloudovém prostředí.  
- **Fine‑grained control** – Detailní kontrola – možnosti uložení vám umožní rozhodnout, jak jsou obrázky uloženy, jaké kódování použít a další.

## Požadavky
1. **Aspose.Words for Java Library** – Stáhněte a přidejte JAR do svého projektu z [zde](https://releases.aspose.com/words/java/).  
2. **Zdrojový soubor Word** – Například `Document.docx`, který chcete uložit jako RTF.  
3. **Vývojové prostředí Java** – JDK 8+ a vaše oblíbené IDE.

## Krok 1: Načtení Word dokumentu (load word document java)
Nejprve načtěte existující DOCX do objektu `Document`. Toto je základ pro jakýkoli převod.

```java
import com.aspose.words.Document;

// Load the source document (e.g., Document.docx)
Document doc = new Document("path/to/Document.docx");
```

> **Tip:** Používejte absolutní cesty nebo zdroje ve class‑path, abyste se vyhnuli `FileNotFoundException`.

## Krok 2: Nastavení možností uložení RTF (save images as wmf)
Aspose.Words nabízí třídu `RtfSaveOptions` pro jemné doladění výstupu. V tomto příkladu povolíme **save images as WMF**, což je preferovaný formát pro soubory RTF.

```java
import com.aspose.words.RtfSaveOptions;

// Create an instance of RtfSaveOptions
RtfSaveOptions saveOptions = new RtfSaveOptions();

// Set the option to save images as WMF
saveOptions.setSaveImagesAsWmf(true);
```

Můžete také upravit další nastavení, například `saveOptions.setEncoding(Charset.forName("UTF-8"))`, pokud potřebujete konkrétní kódování znaků.

## Krok 3: Uložení dokumentu jako RTF (save docx as rtf)
Nyní zapište dokument pomocí nakonfigurovaných možností. Tento krok **uloží DOCX jako RTF**, čímž vytvoří soubor rich‑text připravený k distribuci.

```java
// Save the document in RTF format

doc.save("path/to/output.rtf", saveOptions);
```

## Kompletní zdrojový kód pro převod Wordu do RTF
Níže je kompaktní verze, kterou můžete zkopírovat a vložit do třídy Java. Ukazuje **uložení jako rich text** s možností WMF obrázku v jednom bloku.

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
RtfSaveOptions saveOptions = new RtfSaveOptions(); { saveOptions.setSaveImagesAsWmf(true); }
doc.save("Your Directory Path" + "WorkingWithRtfSaveOptions.SavingImagesAsWmf.rtf", saveOptions);
```

## Časté problémy a řešení
| Problém | Příčina | Řešení |
|-------|--------|-----|
| Výstupní RTF je prázdný | Zdrojový soubor nebyl nalezen nebo nebyl načten | Ověřte cestu v `new Document(...)` |
| Chybějící obrázky | `saveImagesAsWmf` nastaveno na `false` | Povolte `saveOptions.setSaveImagesAsWmf(true)` |
| Poškozené znaky | Špatné kódování | Nastavte `saveOptions.setEncoding(Charset.forName("UTF-8"))` |

## Často kladené otázky

**Q: Jak mohu změnit další možnosti uložení RTF?**  
A: Použijte třídu `RtfSaveOptions` – poskytuje vlastnosti pro kompresi, písma a další. Viz dokumentace Aspose.Words Java API pro úplný seznam.

**Q: Mohu uložit RTF dokument v jiném kódování?**  
A: Ano. Zavolejte `saveOptions.setEncoding(Charset.forName("UTF-8"))` (nebo jakékoli podporované kódování) před uložením.

**Q: Je možné uložit RTF dokument bez obrázků?**  
A: Rozhodně. Nastavte `saveOptions.setSaveImagesAsWmf(false)`, aby se obrázky z výstupu vynechaly.

**Q: Jak mám zacházet s výjimkami během převodu?**  
A: Zabalte volání načtení a uložení do bloku try‑catch, který zachytí `Exception`. Zalogujte chybu a případně znovu vyhoďte vlastní výjimku pro vaši aplikaci.

**Q: Funguje to i pro soubory Word chráněné heslem?**  
A: Načtěte dokument pomocí objektu `LoadOptions`, který obsahuje heslo, a poté pokračujte stejnými kroky uložení.

## Závěr
Nyní máte kompletní, připravenou metodu pro **převod Wordu do RTF** pomocí Aspose.Words pro Java. Načtením DOCX, nastavením `RtfSaveOptions` (včetně **save images as WMF**) a voláním `doc.save(...)` můžete generovat vysoce kvalitní soubory rich‑text, které fungují všude. Neváhejte prozkoumat další možnosti uložení a přizpůsobit výstup přesně vašim potřebám.

---

**Poslední aktualizace:** 2025-12-24  
**Testováno s:** Aspose.Words for Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}