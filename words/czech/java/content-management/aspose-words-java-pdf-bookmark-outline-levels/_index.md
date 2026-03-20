---
date: '2026-03-20'
description: Naučte se, jak vytvořit vnořené záložky a generovat PDF se záložkami
  pomocí Aspose.Words pro Javu, čímž zlepšíte čitelnost a navigaci.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
title: Vytvořte vnořené záložky v PDF pomocí Aspose.Words pro Java
url: /cs/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření vnořených záložek v PDF pomocí Aspose.Words Java

## Úvod
Pokud jste se někdy potýkali s organizací záložek v PDF po převodu dokumentu Word, nejste sami. V tomto tutoriálu **vytvoříte vnořené záložky** a naučíte se **generovat PDF se záložkami**, které jsou snadno ovladatelné. Provedeme vás nastavením Aspose.Words, vytvořením hierarchie záložek, přiřazením úrovní osnovy a nakonec exportem čistého PDF.

**Co se naučíte**
- Jak nastavit Aspose.Words pro Java
- Jak **vytvořit vnořené záložky** v dokumentu Word
- Jak nakonfigurovat úrovně osnovy záložek pro přehlednou navigaci v PDF
- Jak **generovat PDF se záložkami**, které odrážejí definovanou hierarchii

### Rychlé odpovědi
- **Jaká je hlavní třída pro tvorbu dokumentů?** `DocumentBuilder`
- **Která metoda přidává záložku?** `startBookmark(String name)`
- **Jak nastavíte úroveň osnovy pro záložku?** `outlineLevels.add(name, level)`
- **Potřebuji licenci pro produkci?** Ano, zakoupená licence odemkne všechny funkce.
- **Mohu to použít s Maven nebo Gradle?** Rozhodně – oba jsou podporovány.

### Požadavky
Než se pustíme dál, ujistěte se, že máte:
- **Aspose.Words pro Java** (verze 25.3 nebo novější).  
- Nainstalovaný JDK a IDE, jako je IntelliJ IDEA nebo Eclipse.  
- Základní znalosti Javy a zkušenosti s Maven nebo Gradle.

## Co znamená „vytvořit vnořené záložky“?
Vytvoření vnořených záložek znamená umístění jedné záložky uvnitř druhé, čímž vzniká hierarchie rodič‑potomek. Když je dokument uložen jako PDF, tyto vztahy se zobrazí jako sbalitelné položky v panelu záložek PDF, což usnadňuje procházení velkých dokumentů.

## Proč používat úrovně osnovy při generování PDF se záložkami?
Úrovně osnovy definují vizuální hierarchii záložek v prohlížeči PDF. Záložka úrovně 1 se zobrazí jako položka nejvyšší úrovně, úroveň 2 jako podřízená a tak dále. Správné úrovně osnovy převádějí plochý seznam záložek na strukturovaný obsah, což je zvláště užitečné u právních smluv, technických zpráv a e‑knih.

## Nastavení Aspose.Words
Add the library to your project using Maven or Gradle.

**Maven:**
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Gradle:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Získání licence
Aspose.Words je komerční produkt, ale můžete začít s bezplatnou zkušební verzí.

1. **Free Trial** – Stáhněte ze [stránky vydání Aspose](https://releases.aspose.com/words/java/) a vyzkoušejte plné možnosti.  
2. **Temporary License** – Požádejte na [stránce dočasné licence Aspose](https://purchase.aspose.com/temporary-license/) pro krátkodobé hodnocení.  
3. **Purchase** – Získejte trvalou licenci na [portálu nákupu Aspose](https://purchase.aspose.com/buy).

Po získání souboru `.lic` jej načtěte ve svém kódu, aby se odemkly všechny funkce.

## Průvodce implementací
Níže je podrobný návod krok za krokem, jak vytvořit dokument, přidat vnořené záložky, přiřadit úrovně osnovy a uložit výsledek jako PDF.

### Krok 1: Inicializace dokumentu a builderu
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
Tím se vytvoří prázdný dokument Word a objekt builder, který použijete k vkládání textu a záložek.

### Krok 2: Vytvoření první (rodičovské) záložky
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```
Volání `startBookmark` otevře novou záložku s názvem **Bookmark 1**. Vše, co napíšete po tomto volání, bude patřit k této záložce, dokud ji neuzavřete.

### Krok 3: Vnoření druhé záložky do první
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```
Protože je tato záložka zahájena **po** první a uzavřena **před** první, stane se potomkem **Bookmark 1**.

### Krok 4: Uzavření rodičovské záložky
```java
builder.endBookmark("Bookmark 1");
```
Nyní hierarchie vypadá takto:

- Bookmark 1 (úroveň 1)  
  - Bookmark 2 (úroveň 2)

### Krok 5: Přidání samostatné třetí záložky
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```
Tato záložka leží na nejvyšší úrovni, oddělená od prvních dvou.

### Krok 6: Konfigurace úrovní osnovy pro export do PDF
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```
Objekt `PdfSaveOptions` vám umožňuje řídit, jak se záložky zobrazí v konečném PDF.

```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 1);
```
Zde přiřazujeme úroveň 1 hlavním záložkám a úroveň 2 vnořené záložce.

### Krok 7: Uložení dokumentu jako PDF
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```
Výsledné PDF zobrazí čistý, sbalitelný panel záložek, který odráží definovanou hierarchii.

## Časté problémy a řešení
- **Chybějící záložky** – Každý `startBookmark` musí mít odpovídající `endBookmark`. Zapomenutí jednoho způsobí, že záložka bude v PDF ignorována.  
- **Nesprávné úrovně osnovy** – Dvakrát zkontrolujte názvy, které předáváte do `outlineLevels.add`. překlep znamená, že úroveň nebude použita.  
- **Velké dokumenty** – U velmi velkých souborů zavolejte `doc.removeMacros()` nebo vymažte nepoužívané styly před uložením, aby velikost PDF zůstala rozumná.

## Praktické aplikace
1. **Legal Contracts** – Rychle přejděte mezi ustanoveními a podustanoveními.  
2. **Technical Reports** – Navigujte mezi sekcemi, tabulkami a obrázky bez posouvání.  
3. **E‑Learning Material** – Poskytněte studentům klikací obsah.

## Tipy pro výkon
- Odstraňte nepoužívané zdroje (obrázky, styly) před uložením.  
- Používejte streamingové API, pokud zpracováváte PDF větší než 100 MB, aby byl nízký odběr paměti.

## Závěr
Nyní víte, jak **vytvořit vnořené záložky**, přiřadit úrovně osnovy a **generovat PDF se záložkami**, které jsou funkční a uživatelsky přívětivé. Experimentujte s hlubšími hierarchiemi nebo integrujte tuto logiku do vašeho pipeline pro generování dokumentů pro ještě větší automatizaci.

## Často kladené otázky

**Q: Jak nainstaluji Aspose.Words pro Java?**  
A: Přidejte Maven nebo Gradle závislost uvedenou výše a poté načtěte soubor licence za běhu.

**Q: Mohu používat záložky bez nastavení úrovní osnovy?**  
A: Ano, ale PDF zobrazí plochý seznam, který může být obtížné v komplexních dokumentech navigovat.

**Q: Existuje limit, jak hluboko může vnoření záložek jít?**  
A: Technicky ne, ale udržujte hierarchii rozumnou (3‑4 úrovně) pro zachování čitelnosti.

**Q: Jak Aspose zachází s velmi velkými dokumenty?**  
A: Streamuje obsah a nabízí nástroje pro správu paměti; přesto byste měli odstraňovat nepoužívané prvky.

**Q: Mohu upravit záložky po vytvoření PDF?**  
A: Rozhodně – použijte Aspose.PDF pro Java k úpravě názvů záložek, cílů nebo úrovní osnovy po generování.

## Zdroje
- [Dokumentace Aspose.Words](https://reference.aspose.com/words/java/)
- [Stáhnout nejnovější vydání](https://releases.aspose.com/words/java/)
- [Zakoupit licenci](https://purchase.aspose.com/buy)
- [Bezplatná zkušební verze](https://releases.aspose.com/words/java/)
- [Žádost o dočasnou licenci](https://purchase.aspose.com/temporary-license/)
- [Fórum podpory Aspose](https://forum.aspose.com/c/words/10)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Poslední aktualizace:** 2026-03-20  
**Testováno s:** Aspose.Words for Java 25.3  
**Autor:** Aspose