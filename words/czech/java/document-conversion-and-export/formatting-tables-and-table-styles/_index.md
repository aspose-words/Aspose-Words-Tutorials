---
date: 2025-11-28
description: Naučte se, jak měnit okraje buněk a formátovat tabulky pomocí Aspose.Words
  pro Javu. Tento krok‑za‑krokem průvodce zahrnuje nastavení okrajů, použití stylu
  první sloupce, automatické přizpůsobení obsahu tabulky a aplikaci stylů tabulky.
linktitle: How to Change Cell Borders in Tables – Aspose.Words for Java
second_title: Aspose.Words Java Document Processing API
title: Jak změnit okraje buněk v tabulkách – Aspose.Words pro Java
url: /cs/java/document-conversion-and-export/formatting-tables-and-table-styles/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jak změnit ohraničení buněk v tabulkách – Aspose.Words pro Java

## Úvod

Pokud jde o formátování dokumentů, tabulky hrají zásadní roli a **znalost toho, jak změnit ohraničení buněk**, je nezbytná pro vytváření přehledných, profesionálních rozvržení. Pokud vyvíjíte v Javě s Aspose.Words, máte již po ruce výkonný nástroj. V tomto tutoriálu projdeme kompletní proces formátování tabulek, změny ohraničení buněk, použití *stylu první sloupce* a *automatického přizpůsobení obsahu tabulky*, aby vaše dokumenty vypadaly uhlazeně.

## Rychlé odpovědi
- **Jaká třída je primární pro vytváření tabulek?** `DocumentBuilder` vytváří tabulky a buňky programově.  
- **Jak změním tloušťku ohraničení jedné buňky?** Použijte `builder.getCellFormat().getBorders().getLeft().setLineWidth(value)`.  
- **Mohu použít předdefinovaný styl tabulky?** Ano – zavolejte `table.setStyleIdentifier(StyleIdentifier.YOUR_STYLE)`.  
- **Jaká metoda automaticky přizpůsobí tabulku jejímu obsahu?** `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)`.  
- **Potřebuji licenci pro produkční nasazení?** Platná licence Aspose.Words je vyžadována pro ne‑zkušební použití.

## Co znamená „jak změnit ohraničení buněk“ v Aspose.Words?

Změna ohraničení buněk znamená přizpůsobení vizuálních čar, které buňky oddělují – barva, šířka a styl čáry. Aspose.Words poskytuje bohaté API, které vám umožní upravit tyto vlastnosti na úrovni tabulky, řádku nebo jednotlivé buňky, čímž získáte detailní kontrolu nad vzhledem vašich dokumentů.

## Proč používat Aspose.Words pro Java při stylování tabulek?

- **Konzistentní vzhled napříč platformami** – stejný kód pro stylování funguje na Windows, Linuxu i macOS.  
- **Bez závislosti na Microsoft Word** – generujte nebo upravujte dokumenty na serveru.  
- **Bohatá knihovna stylů** – vestavěné styly tabulek (např. *styl první sloupce*) a plné možnosti automatického přizpůsobení.  

## Požadavky

1. **Java Development Kit (JDK) 8+** – ujistěte se, že `java` je v PATH.  
2. **IDE** – IntelliJ IDEA, Eclipse nebo jakýkoli editor dle vašeho výběru.  
3. **Aspose.Words pro Java** – stáhněte nejnovější JAR z [oficiálního webu](https://releases.aspose.com/words/java/).  
4. **Základní znalost Javy** – měli byste umět vytvořit Maven/Gradle projekt a přidat externí JAR soubory.

## Import balíčků

Pro práci s tabulkami potřebujete základní třídy Aspose.Words:

```java
import com.aspose.words.*;
```

Tento jediný import vám poskytne přístup k `Document`, `DocumentBuilder`, `Table`, `StyleIdentifier` a mnoha dalším utilitám.

## Jak změnit ohraničení buněk

Níže vytvoříme jednoduchou tabulku, změníme její celkové ohraničení a poté přizpůsobíme jednotlivé buňky.

### Krok 1: Načtení nového dokumentu

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Krok 2: Vytvoření tabulky a nastavení globálního ohraničení

```java
Table table = builder.startTable();
builder.insertCell();

// Set the borders for the entire table.
table.setBorders(LineStyle.SINGLE, 2.0, Color.BLACK);
        
// Set the cell shading for this cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.RED);
builder.writeln("Cell #1");

builder.insertCell();
        
// Specify a different cell shading for the second cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.GREEN);
builder.writeln("Cell #2");

builder.endRow();
```

### Krok 3: Změna ohraničení jedné buňky

```java
// Clear the cell formatting from previous operations.
builder.getCellFormat().clearFormatting();

builder.insertCell();

// Create larger borders for the first cell of this row.
builder.getCellFormat().getBorders().getLeft().setLineWidth(4.0);
builder.getCellFormat().getBorders().getRight().setLineWidth(4.0);
builder.getCellFormat().getBorders().getTop().setLineWidth(4.0);
builder.getCellFormat().getBorders().getBottom().setLineWidth(4.0);
builder.writeln("Cell #3");

builder.insertCell();
builder.getCellFormat().clearFormatting();
builder.writeln("Cell #4");
        
doc.save("FormatTableAndCellWithDifferentBorders.docx");
```

#### Co kód dělá
- **Globální ohraničení** – `table.setBorders` nastaví celé tabulce černou čáru o tloušťce 2 pt.  
- **Stínování buňky** – Ukazuje, jak obarvit jednotlivé buňky (červená a zelená).  
- **Vlastní ohraničení buňky** – Třetí buňka dostane ohraničení 4 pt na všech stranách, čímž vynikne.

## Použití stylů tabulky (včetně stylu první sloupce)

Styly tabulky vám umožní aplikovat jednotný vzhled jedním voláním. Ukážeme také, jak povolit *styl první sloupce* a automaticky přizpůsobit tabulku jejímu obsahu.

### Krok 4: Vytvoření nového dokumentu pro stylování

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Table table = builder.startTable();
        
// We must insert at least one row first before setting any table formatting.
builder.insertCell();
```

### Krok 5: Aplikace předdefinovaného stylu a povolení formátování první sloupce

```java
// Set the table style based on a unique style identifier.
table.setStyleIdentifier(StyleIdentifier.MEDIUM_SHADING_1_ACCENT_1);
        
// Apply which features should be formatted by the style.
table.setStyleOptions(TableStyleOptions.FIRST_COLUMN | TableStyleOptions.ROW_BANDS | TableStyleOptions.FIRST_ROW);

// Auto‑fit the table so columns shrink or expand to fit the content.
table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS);
```

### Krok 6: Naplnění tabulky daty

```java
builder.writeln("Item");
builder.getCellFormat().setRightPadding(40.0);
builder.insertCell();
builder.writeln("Quantity (kg)");
builder.endRow();

builder.insertCell();
builder.writeln("Apples");
builder.insertCell();
builder.writeln("20");
builder.endRow();

builder.insertCell();
builder.writeln("Bananas");
builder.insertCell();
builder.writeln("40");
builder.endRow();

builder.insertCell();
builder.writeln("Carrots");
builder.insertCell();
builder.writeln("50");
builder.endRow();

doc.save("BuildTableWithStyle.docx");
```

#### Proč je to důležité
- **Identifikátor stylu** – `MEDIUM_SHADING_1_ACCENT_1` dodá tabulce čistý, stínovaný vzhled.  
- **Styl první sloupce** – Zvýraznění první sloupce zlepšuje čitelnost, zejména v reportech.  
- **Proužky řádků** – Střídavé barvy řádků usnadňují orientaci ve velkých tabulkách.  
- **Auto‑fit** – Zajišťuje, že šířka tabulky se přizpůsobí obsahu, čímž se zabrání oříznutému textu.

## Časté problémy a řešení

| Problém | Typická příčina | Rychlé řešení |
|---------|----------------|---------------|
| Ohraničení se nezobrazuje | Použití `clearFormatting()` po nastavení ohraničení | Nastavte ohraničení **po** vyčištění formátování, nebo je znovu aplikujte. |
| Stínování ignorováno u sloučených buněk | Stínování aplikováno před sloučením | Aplikujte stínování **po** sloučení buněk. |
| Šířka tabulky přesahuje okraje stránky | Nebyl použit auto‑fit | Zavolejte `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` nebo nastavte pevnou šířku. |
| Styl se neaplikoval | Nesprávná hodnota `StyleIdentifier` | Ověřte, že identifikátor existuje ve verzi Aspose.Words, kterou používáte. |

## Často kladené otázky

**Q: Mohu použít vlastní styly tabulek, které nejsou v základní nabídce?**  
A: Ano, můžete vytvářet a aplikovat vlastní styly programově. Viz [dokumentace Aspose.Words](https://reference.aspose.com/words/java/) pro podrobnosti.

**Q: Jak mohu aplikovat podmíněné formátování na buňky?**  
A: Použijte standardní Java logiku k inspekci hodnot buněk a poté zavolejte příslušné metody formátování (např. změna barvy pozadí, pokud hodnota překročí práh).

**Q: Je možné formátovat sloučené buňky stejným způsobem jako běžné buňky?**  
A: Rozhodně. Po sloučení buněk použijte stejné API `CellFormat` pro nastavení stínování nebo ohraničení.

**Q: Co když potřebuji, aby se tabulka dynamicky měnila podle vstupu uživatele?**  
A: Upravit šířky sloupců nebo znovu zavolat `autoFit` po vložení nových dat, aby se přepočítalo rozvržení.

**Q: Kde najdu další příklady stylování tabulek?**  
A: Oficiální [dokumentace Aspose.Words API](https://reference.aspose.com/words/java/) obsahuje rozsáhlou sadu ukázek.

## Závěr

Nyní máte kompletní sadu nástrojů pro **změnu ohraničení buněk**, aplikaci *stylu první sloupce* a **automatické přizpůsobení obsahu tabulky** pomocí Aspose.Words pro Java. Ovládnutím těchto technik můžete vytvářet dokumenty, které jsou jak datově bohaté, tak vizuálně atraktivní – ideální pro reporty, faktury a jakýkoli jiný obchodně kritický výstup.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Poslední aktualizace:** 2025-11-28  
**Testováno s:** Aspose.Words pro Java 24.12 (nejnovější v době psaní)  
**Autor:** Aspose