---
date: 2026-01-03
description: Naučte se, jak upravit čísla stránek při vkládání obsahu pomocí Aspose.Words
  pro Java. Přizpůsobte styly obsahu a vytvářejte dokumenty bez námahy.
linktitle: Generating Table of Contents
second_title: Aspose.Words Java Document Processing API
title: Upravit čísla stránek a vygenerovat obsah pomocí Aspose.Words pro Java
url: /cs/java/document-manipulation/generating-table-of-contents/
weight: 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Upravit čísla stránek a vytvořit obsah v Aspose.Words pro Java

V tomto tutoriálu se dozvíte, jak **upravit čísla stránek** a **vložit obsah** (TOC) pomocí Aspose.Words pro Java. Dobře strukturovaný obsah usnadňuje navigaci v dlouhých dokumentech a jemné doladění zarovnání čísel stránek poskytuje čtenářům profesionální zážitek. Provedeme vás vytvořením dokumentu, přizpůsobením stylů obsahu a úpravou tabulátorů tak, aby se čísla stránek zarovnala přesně tam, kde chcete.

## Rychlé odpovědi
- **Co znamená „upravit čísla stránek“?** Úprava tabulátorů, které zarovnávají čísla stránek v obsahu.  
- **Mohu vložit obsah automaticky?** Ano – použijte třídu `FieldToc`.  
- **Potřebuji licenci pro spuštění kódu?** Pro vývoj stačí bezplatná zkušební verze; pro produkci je licence vyžadována.  
- **Která verze Aspose je podporována?** Příklady fungují s nejnovějším vydáním Aspose.Words pro Java.  
- **Lze přizpůsobit styly obsahu?** Rozhodně – můžete měnit písma, tučnost a další vlastnosti.

## Co je obsah v Aspose.Words?
Obsah je pole, které prohledá dokument podle stylů nadpisů (např. Heading 1, Heading 2) a vygeneruje seznam položek s čísly stránek. Aspose.Words vám umožní vložit toto pole programově a plně kontrolovat jeho vzhled.

## Proč upravovat čísla stránek v obsahu?
Úprava tabulátorů vám dává přesnou kontrolu nad tím, kde se čísla stránek zobrazí, což je důležité pro:

- Udržení čistého, sloupcově zarovnaného rozvržení.  
- Dodržení firemních stylových příruček.  
- Zlepšení čitelnosti tištěných i digitálních dokumentů.

## Požadavky
- Aspose.Words pro Java přidaný do vašeho projektu (Maven/Gradle).  
- Základní znalost syntaxe jazyka Java.  

## Průvodce krok za krokem

### Krok 1: Vytvořte nový dokument
Nejprve vytvořte prázdný objekt `Document`, který bude obsahovat váš obsah a obsah.

```java
Document doc = new Document();
```

### Krok 2: Přizpůsobte styly obsahu
Můžete změnit vzhled každé úrovně obsahu. V tomto příkladu uděláme položky první úrovně tučnými, což je častý požadavek na formátování.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

### Krok 3: Přidejte obsah do dokumentu
Vložte nadpisy (např. `Heading1`, `Heading2`) a běžné odstavce. Pole obsahu později automaticky tyto nadpisy zachytí. *(Kód byl vynechán pro stručnost – hlavní je generování obsahu.)*

### Krok 4: Vložte pole obsahu
Umístěte obsah tam, kde ho chcete – typicky na začátek dokumentu.

```java
// Insert a TOC field at the desired location in your document.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

### Krok 5: Uložte dokument
Uložte dokument na disk. Můžete zvolit libovolný podporovaný formát, jako je DOCX, PDF nebo HTML.

```java
doc.save("your_output_path_here");
```

## Přizpůsobení tabulátorů v obsahu (úprava čísel stránek)
Pokud výchozí tabulátor nezarovnává čísla stránek podle vašich potřeb, můžete projít všechny odstavce obsahu a upravit jejich pozice tabulátorů.

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Get the first tab used in this paragraph, which aligns the page numbers.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Remove the old tab.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // Insert a new tab at a modified position (e.g., 50 units to the left).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

Nyní položky obsahu zobrazují čísla stránek přesně tam, kde chcete, a váš dokument získá profesionální vzhled.

## Časté problémy a tipy
- **Chybějící nadpisy v obsahu:** Ujistěte se, že vaše nadpisy používají vestavěné styly (`Heading1`, `Heading2` atd.) nebo mapujte vlastní styly na úrovně obsahu.  
- **Tabulátor se nepoužil:** Ověřte, že odstavec skutečně patří do stylu obsahu (`TOC_1`‑`TOC_9`).  
- **Výkon u velkých dokumentů:** Po vložení obsahu zavolejte `doc.updateFields()`, aby se položky aktualizovaly najednou.

## Často kladené otázky

**Q: Jak změním formátování položek obsahu?**  
A: Použijte `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`, kde *X* je úroveň (1‑9), a upravte písmo, barvu nebo nastavení odstavce.

**Q: Jak přidám více úrovní do obsahu?**  
A: Upravit přepínač `FieldToc` `\o "1-3"` (například) tak, aby zahrnoval další úrovně nadpisů, a poté aktualizovat odpovídající styly `TOC_X`.

**Q: Můžu změnit pozice tabulátorů pro konkrétní položky obsahu?**  
A: Ano – projděte odstavce, jak je ukázáno v sekci „Přizpůsobení tabulátorů“, a upravte každý tabulátor individuálně.

**Q: Lze vygenerovat obsah v PDF výstupu?**  
A: Rozhodně. Uložte dokument jako PDF (`doc.save("output.pdf")`) po vygenerování obsahu; pole se automaticky vykreslí.

**Q: Musím volat `updateFields()` ručně?**  
A: Když vložíte `FieldToc`, Aspose.Words jej aktualizuje při uložení, ale volání `doc.updateFields()` poskytne okamžité výsledky pro ladění.

## Závěr
Naučili jste se, jak **upravit čísla stránek**, **vložit obsah** a **přizpůsobit styly obsahu** pomocí Aspose.Words pro Java. Tyto techniky vám umožní vytvářet čisté, snadno navigovatelné a profesionálně formátované dokumenty, které splňují jakékoli publikační standardy.

---  

**Poslední aktualizace:** 2026-01-03  
**Testováno s:** Aspose.Words pro Java (nejnovější vydání)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}