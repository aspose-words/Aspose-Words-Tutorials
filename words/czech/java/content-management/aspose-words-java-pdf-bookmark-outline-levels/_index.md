---
date: '2026-04-02'
description: Naučte se, jak vytvořit vnořené záložky, nastavit úrovně osnovy záložek
  a uložit dokumenty Word jako PDF pomocí Aspose.Words pro Javu.
keywords:
- create nested bookmarks
- how to set bookmark
- save word pdf bookmarks
title: Vytvořte vnořené záložky a nastavte úrovně osnov v PDF pomocí Aspose.Words
  pro Javu
url: /cs/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření vnořených záložek a nastavení úrovní osnovy v PDF pomocí Aspose.Words pro Java

## Úvod
Máte potíže se správou záložek při převodu dokumentů Word do PDF? **Tento tutoriál vám ukáže, jak vytvořit vnořené záložky**, nastavit jejich úrovně osnovy a uložit výsledek jako čistý, snadno navigovatelný PDF pomocí Aspose.Words pro Java. Na konci tohoto průvodce budete mít profesionálně vypadající PDF, kde čtenáři mohou přejít přímo na potřebné sekce.

**Co se naučíte**
- Nastavit Aspose.Words pro Java ve vašem projektu  
- **Vytvořit vnořené záložky** v dokumentu Word  
- **Jak nastavit úrovně osnovy záložek** pro přehlednou hierarchii  
- **Uložit záložky Word PDF** se správnou strukturou  

### Rychlé odpovědi
- **Jaká je hlavní třída pro tvorbu dokumentů?** `DocumentBuilder`  
- **Která metoda přidává úroveň osnovy záložky?** `BookmarksOutlineLevels.add()`  
- **Potřebuji licenci pro export PDF?** Licence je vyžadována pro produkční použití; bezplatná zkušební verze funguje pro hodnocení.  
- **Mohu vnořovat záložky libovolně hluboko?** Ano, ale udržujte hierarchii čitelnou pro koncové uživatele.  
- **Jaká verze Aspose.Words je vyžadována?** Verze 25.3 nebo novější.

## Co je „vytvoření vnořených záložek“?
Vnořené záložky jsou záložky umístěné uvnitř jiných záložek, tvořící hierarchii rodič‑potomek. V PDF se zobrazují jako rozbalitelné položky v panelu záložek, což čtenářům umožňuje sbalit nebo rozbalit sekce podle potřeby.

## Proč nastavit úrovně osnovy záložek?
Úrovně osnovy definují vizuální pořadí vnoření v panelu záložek PDF. Správné úrovně zlepšují navigaci, zejména v dlouhých právních smlouvách, technických zprávách nebo e‑knihách, kde uživatelé potřebují rychle najít informace.

## Předpoklady
- **Knihovny a závislosti**: Aspose.Words pro Java (verze 25.3 nebo novější).  
- **Prostředí**: JDK 8+ a IDE jako IntelliJ IDEA nebo Eclipse.  
- **Znalosti**: Základy Javy, znalost Maven nebo Gradle.

### Nastavení Aspose.Words
Přidejte knihovnu do svého projektu pomocí Maven nebo Gradle.

**Maven**
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Gradle**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Získání licence
Aspose.Words je komerční produkt, ale můžete začít s bezplatnou zkušební verzí.

1. **Free Trial** – Stáhněte z [Aspose's release page](https://releases.aspose.com/words/java/) a vyzkoušejte všechny funkce.  
2. **Temporary License** – Požádejte na [Aspose’s temporary license page](https://purchase.aspose.com/temporary-license/), pokud potřebujete krátkodobý klíč.  
3. **Purchase** – Zakupte trvalou licenci přes [Aspose’s purchasing portal](https://purchase.aspose.com/buy).

Inicializujte soubor licence ve svém kódu před použitím jakýchkoli Aspose API, aby se odemkly všechny funkce.

## Průvodce implementací

### Jak vytvořit vnořené záložky v dokumentu Word
Vytvoříme jednoduchý dokument a přidáme tři záložky, z nichž jedna obsahuje další záložku.

#### Krok 1: Inicializace dokumentu a builderu
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

#### Krok 2: Vložení první (rodičovské) záložky
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

#### Krok 3: Vnoření druhé záložky do první
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

#### Krok 4: Uzavření vnější záložky
```java
builder.endBookmark("Bookmark 1");
```

#### Krok 5: Přidání nezávislé třetí záložky
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### Jak nastavit úrovně osnovy záložek pro export do PDF
Nyní nakonfigurujeme hierarchii osnovy, která se objeví ve finálním PDF.

#### Krok 1: Připravte `PdfSaveOptions`
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

#### Krok 2: Přiřaďte úrovně osnovy každé záložce
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

#### Krok 3: Uložte dokument jako PDF s nakonfigurovanými záložkami
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

## Časté problémy a řešení
- **Chybějící záložky** – Ověřte, že každý `startBookmark` má odpovídající `endBookmark`.  
- **Nesprávná hierarchie** – Zkontrolujte přiřazená čísla úrovní; nižší číslo znamená vyšší (rodičovskou) úroveň.  
- **Licence nebyla aplikována** – Pokud záložky zmizí, ujistěte se, že soubor licence je načten před jakýmkoli zpracováním dokumentu.  

## Praktické aplikace
1. **Legal contracts** – Rychle přejděte na články, podčlánky a přílohy.  
2. **Technical reports** – Navigujte sekce, tabulky a obrázky bez posouvání.  
3. **E‑learning material** – Umožněte studentům rozbalovat kapitoly a sbalit příklady podle potřeby.

## Tipy pro výkon
- Odstraňte nepoužité sekce nebo obrázky před uložením, aby byla velikost PDF malá.  
- U velmi velkých dokumentů zavolejte `doc.cleanup()` nebo zpracovávejte soubor po částech, aby se snížil tlak na paměť.

## Často kladené otázky

**Q: Jak nainstaluji Aspose.Words pro Java?**  
A: Přidejte Maven nebo Gradle závislost uvedenou výše, poté umístěte soubor licence do projektu a inicializujte jej v kódu.

**Q: Mohu použít záložky bez nastavení úrovní osnovy?**  
A: Ano, ale bez úrovní osnovy bude panel záložek PDF zobrazovat plochý seznam, což ztíží navigaci.

**Q: Existuje limit, jak hluboko mohou být záložky vnořeny?**  
A: Technicky ne, ale udržujte hierarchii rozumnou (3‑4 úrovně) pro čitelnost uživatele.

**Q: Jak Aspose zachází s velmi velkými soubory Word?**  
A: Knihovna streamuje obsah a nabízí metody jako `Document.optimizeResources()`, aby udržela nízkou spotřebu paměti.

**Q: Mohu upravit záložky po vygenerování PDF?**  
A: Ano, můžete použít Aspose.PDF pro Java k úpravě názvů záložek, cílů nebo hierarchie po vytvoření.

## Zdroje
- [Dokumentace Aspose.Words](https://reference.aspose.com/words/java/)
- [Stáhnout nejnovější verze](https://releases.aspose.com/words/java/)
- [Zakoupit licenci](https://purchase.aspose.com/buy)
- [Bezplatná zkušební verze](https://releases.aspose.com/words/java/)
- [Žádost o dočasnou licenci](https://purchase.aspose.com/temporary-license/)
- [Fórum podpory Aspose](https://forum.aspose.com/c/words/10)

---

**Poslední aktualizace:** 2026-04-02  
**Testováno s:** Aspose.Words 25.3 pro Java  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}