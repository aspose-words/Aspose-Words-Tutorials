---
title: Nastavte relativní horizontální nebo vertikální polohu
linktitle: Nastavte relativní horizontální nebo vertikální polohu
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak nastavit relativní vodorovné a svislé polohy tabulek v dokumentech aplikace Word pomocí Aspose.Words for .NET, pomocí tohoto podrobného průvodce.
weight: 10
url: /cs/net/programming-with-tables/set-relative-horizontal-or-vertical-position/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nastavte relativní horizontální nebo vertikální polohu

## Zavedení

Zasekli jste se někdy v tom, jak umístit tabulky v dokumentech aplikace Word tak, jak chcete? No, nejsi sám. Ať už vytváříte profesionální zprávu nebo stylovou brožuru, zarovnání tabulek může znamenat velký rozdíl. To je místo, kde se Aspose.Words for .NET hodí. Tento tutoriál vás krok za krokem provede nastavením relativní vodorovné nebo svislé polohy tabulek v dokumentech aplikace Word. Pojďme se ponořit!

## Předpoklady

Než začneme, ujistěte se, že máte následující:

1.  Aspose.Words for .NET: Pokud jste to ještě neudělali, můžete si ji stáhnout[zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Visual Studio nebo jakékoli jiné IDE kompatibilní s .NET.
3. Základní znalost C#: Tento tutoriál předpokládá, že jste obeznámeni se základy programování v C#.

## Importovat jmenné prostory

Nejprve musíte importovat potřebné jmenné prostory. To je nezbytné pro přístup k funkcím Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Krok 1: Vložte svůj dokument

Chcete-li začít, musíte do programu načíst dokument aplikace Word. Můžete to udělat takto:

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table wrapped by text.docx");
```

Tento fragment kódu nastaví cestu k adresáři dokumentů a načte konkrétní dokument, na kterém chcete pracovat. Ujistěte se, že cesta dokumentu je správná, abyste předešli problémům s načítáním.

## Krok 2: Přístup k tabulce

Dále potřebujeme přistupovat k tabulce v dokumentu. Obvykle byste chtěli pracovat s první tabulkou v části těla.

```csharp
Table table = doc.FirstSection.Body.Tables[0];
```

Tento řádek kódu načte první tabulku z těla dokumentu. Pokud má váš dokument více tabulek, můžete podle toho upravit index.

## Krok 3: Nastavte vodorovnou polohu

Nyní nastavíme vodorovnou polohu stolu vzhledem ke konkrétnímu prvku. V tomto příkladu jej umístíme vzhledem ke sloupci.

```csharp
table.HorizontalAnchor = RelativeHorizontalPosition.Column;
```

 Nastavením`HorizontalAnchor` na`RelativeHorizontalPosition.Column`, říkáte tabulce, aby se zarovnala vodorovně vzhledem ke sloupci, ve kterém se nachází.

## Krok 4: Nastavte vertikální pozici

Podobně jako u horizontálního polohování můžete nastavit i vertikální polohu. Zde jej umístíme vzhledem ke stránce.

```csharp
table.VerticalAnchor = RelativeVerticalPosition.Page;
```

 Nastavení`VerticalAnchor` na`RelativeVerticalPosition.Page` zajišťuje svislé zarovnání tabulky podle stránky.

## Krok 5: Uložte dokument

Nakonec uložte změny do nového dokumentu. Toto je zásadní krok, abyste se ujistili, že vaše změny zůstanou zachovány.

```csharp
doc.Save(dataDir + "WorkingWithTables.SetFloatingTablePosition.docx");
```

Tento příkaz uloží upravený dokument pod novým názvem, čímž zajistí, že nepřepíšete svůj původní soubor.

## Závěr

A tady to máte! Úspěšně jste nastavili relativní horizontální a vertikální pozice pro tabulku v dokumentu aplikace Word pomocí Aspose.Words for .NET. S touto nově objevenou dovedností můžete vylepšit rozvržení a čitelnost vašich dokumentů, aby vypadaly profesionálněji a uhlazeněji. Pokračujte v experimentování s různými pozicemi a zjistěte, co nejlépe vyhovuje vašim potřebám.

## FAQ

### Mohu umístit tabulky vzhledem k jiným prvkům?  
Ano, Aspose.Words vám umožňuje umístit tabulky vzhledem k různým prvkům, jako jsou okraje, stránky, sloupce a další.

### Potřebuji licenci k používání Aspose.Words pro .NET?  
 Ano, můžete si zakoupit licenci[zde](https://purchase.aspose.com/buy) nebo získat dočasnou licenci[zde](https://purchase.aspose.com/temporary-license/).

### Je k dispozici bezplatná zkušební verze pro Aspose.Words pro .NET?  
 Absolutně! Můžete si stáhnout bezplatnou zkušební verzi[zde](https://releases.aspose.com/).

### Mohu používat Aspose.Words s jinými programovacími jazyky?  
Aspose.Words je navržen primárně pro .NET, ale jsou dostupné verze pro Java, Python a další platformy.

### Kde najdu podrobnější dokumentaci?  
Podrobnější informace naleznete v dokumentaci Aspose.Words[zde](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
