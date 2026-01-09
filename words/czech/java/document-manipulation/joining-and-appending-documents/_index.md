---
date: 2026-01-09
description: Naučte se, jak sloučit dokumenty pomocí Aspose.Words pro Javu při zachování
  formátování, propojení záhlaví a zápatí a dalších funkcí.
linktitle: Joining and Appending Documents
second_title: Aspose.Words Java Document Processing API
title: Jak sloučit dokumenty pomocí Aspose.Words pro Javu
url: /cs/java/document-manipulation/joining-and-appending-documents/
weight: 30
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jak sloučit dokumenty pomocí Aspose.Words pro Java

Programatické sloučení souborů Word může být bolestí hlavy – zejména když potřebujete zachovat styly, číslování stránek a záhlaví/patičky beze změny. V tomto tutoriálu objevíte **jak sloučit dokumenty** pomocí knihovny Aspose.Words pro Java, krok za krokem. Pokryjeme jednoduché připojování, pokročilé možnosti importu, zpracování různých nastavení stránek a triky, které potřebujete k **zachování formátování při sloučení** výsledků v různých reálných scénářích.

## Rychlé odpovědi
- **Jaký je nejjednodušší způsob, jak sloučit dokumenty Word?** Použijte `Document.appendDocument` s `ImportFormatMode.KEEP_SOURCE_FORMATTING`.  
- **Mohu zachovat původní styly každého zdrojového souboru?** Ano – nastavte `ImportFormatMode.USE_DESTINATION_STYLES` nebo povolte Smart Style Behavior.  
- **Jak udržet správné číslování stránek po sloučení?** Převěďte pole `NUMPAGES` na odkazy na stránky a zavolejte `updatePageLayout()`.  
- **Zůstávají záhlaví a patičky automaticky propojené?** Můžete je propojit nebo odpojit pomocí `linkToPrevious(true/false)`.  
- **Co potřebuji před začátkem?** Přidat Aspose.Words pro Java do vašeho projektu a mít připravené zdrojové soubory `.docx`.

## Úvod do spojování a připojování dokumentů v Aspose.Words pro Java

V tomto tutoriálu prozkoumáme, jak spojovat a připojovat dokumenty pomocí knihovny Aspose.Words pro Java. Naučíte se, jak plynule sloučit více dokumentů při zachování formátování a struktury.

## Požadavky

Než začneme, ujistěte se, že máte v Java projektu nastavené API Aspose.Words pro Java.

## Možnosti spojování dokumentů

### Jednoduché připojení

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Připojení s možnostmi importu formátu

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

### Připojení do prázdného dokumentu

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document();
dstDoc.removeAllChildren();
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Připojení s konverzí číslování stránek

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
convertNumPageFieldsToPageRef(dstDoc); // Convert NUMPAGES fields
dstDoc.updatePageLayout(); // Update page layout for correct numbering
```

## Zpracování různých nastavení stránek

Při připojování dokumentů s různými nastaveními stránek:

```java
srcDoc.getFirstSection().getPageSetup().setSectionStart(SectionStart.CONTINUOUS);
srcDoc.getFirstSection().getPageSetup().setRestartPageNumbering(true);
// Ensure page setup settings match the destination document
```

## Spojování dokumentů s různými styly

```java
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES);
```

## Chování Smart Style

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setSmartStyleBehavior(true);
builder.insertDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

## Vkládání dokumentů pomocí DocumentBuilder

```java
DocumentBuilder builder = new DocumentBuilder(dstDoc);
builder.insertDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Zachování číslování zdroje

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Zpracování textových polí

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setIgnoreTextBoxes(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Správa záhlaví a patiček

### Propojení záhlaví a patiček

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Odpojení záhlaví a patiček

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Proč je to důležité pro projekty „merge word documents java“

Když potřebujete **sloučit word dokumenty java**‑styl, zachování vzhledu a pocitu každého souboru je zásadní pro právní, vydavatelské nebo reportovací pracovní postupy. Použití výše uvedených technik zajišťuje, že:
* Styly z každého zdroje zůstávají beze změny (nebo jsou sjednoceny, podle vašeho výběru).  
* Číslování stránek a koncové zlomky sekcí se chovají předvídatelně.  
* Záhlaví a patičky mohou být propojeny nebo zůstávat nezávislé jedním řádkem kódu.  

## Časté úskalí a tipy

| Problém | Proč k tomu dochází | Jak opravit |
|-------|----------------|------------|
| Ztráta číslování po sloučení | `NUMPAGES` pole stále odkazují na původní sekce | Zavolejte `convertNumPageFieldsToPageRef` a `updatePageLayout()` |
| Styly se střetávají | Použití `KEEP_SOURCE_FORMATTING` s konfliktními styly | Přepněte na `USE_DESTINATION_STYLES` nebo povolte Smart Style Behavior |
| Objevují se prázdné stránky | Různé hodnoty `SectionStart` | Nastavte `SectionStart.CONTINUOUS` na zdrojových sekcích před připojením |

## Často kladené otázky

**Q: Jak mohu bez problémů spojit dokumenty s různými styly?**  
A: Použijte `ImportFormatMode.USE_DESTINATION_STYLES` při připojování, nebo povolte `SmartStyleBehavior` pro chytřejší sloučení.

**Q: Mohu zachovat číslování stránek při připojování dokumentů?**  
A: Ano, převěďte pole `NUMPAGES` na odkazy na stránky pomocí `convertNumPageFieldsToPageRef` a poté zavolejte `updatePageLayout()`.

**Q: Co je Smart Style Behavior?**  
A: Automaticky mapuje styly ze zdroje na styly v cíli, pokud je to možné, což pomáhá udržet jednotný vzhled napříč sloučeným obsahem.

**Q: Jak zacházet s textovými poli při připojování dokumentů?**  
A: Nastavte `importFormatOptions.setIgnoreTextBoxes(false)`, aby textová pole byla během sloučení zachována.

**Q: Co když chci propojit nebo odpojit záhlaví a patičky mezi dokumenty?**  
A: Použijte `linkToPrevious(true)` pro propojení, nebo `linkToPrevious(false)` pro jejich oddělení před voláním `appendDocument`.

## Závěr

Aspose.Words pro Java poskytuje flexibilní a výkonné nástroje pro **jak sloučit dokumenty**, ať už potřebujete zachovat přesné formátování, zpracovat různé nastavení stránek nebo řídit propojení záhlaví/patiček. Experimentujte s výše uvedenými úryvky kódu, aby odpovídaly vašemu konkrétnímu workflow zpracování dokumentů, a budete schopni **sloučit word dokumenty java**‑styl s jistotou.

---

**Poslední aktualizace:** 2026-01-09  
**Testováno s:** Aspose.Words for Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}