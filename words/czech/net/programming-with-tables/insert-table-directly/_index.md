---
"description": "Naučte se, jak vkládat tabulky přímo do dokumentů Wordu pomocí Aspose.Words pro .NET. Postupujte podle našeho podrobného návodu krok za krokem a zefektivníte si tvorbu dokumentů."
"linktitle": "Vložit tabulku přímo"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Vložit tabulku přímo"
"url": "/cs/net/programming-with-tables/insert-table-directly/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vložit tabulku přímo

## Zavedení
Programové vytváření tabulek může být docela náročné, zejména při práci se složitými strukturami dokumentů. Ale nebojte se, jsme tu, abychom vám to rozebrali! V této příručce si ukážeme kroky vkládání tabulky přímo do dokumentu Wordu pomocí Aspose.Words pro .NET. Ať už jste zkušený vývojář, nebo teprve začínáte, tento tutoriál vám pomůže tento proces snadno zvládnout.

## Předpoklady

Než se pustíme do kódu, ujistěte se, že máte vše, co potřebujete k zahájení. Zde je stručný kontrolní seznam:

1. Knihovna Aspose.Words pro .NET: Ujistěte se, že jste si stáhli a nainstalovali knihovnu Aspose.Words pro .NET. Můžete ji získat z [stránka ke stažení](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Vývojové prostředí, jako je Visual Studio.
3. Základní znalost C#: Pochopení základů programování v C#.
4. Adresář dokumentů: Cesta k adresáři, kam budete ukládat dokumenty.

těmito předpoklady jste připraveni začít programovat!

## Importovat jmenné prostory

Nejprve si importujme potřebné jmenné prostory. Tyto jmenné prostory nám poskytnou třídy a metody potřebné pro práci s dokumenty Wordu.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

Nyní, když máme nastavené jmenné prostory, pojďme se přesunout k té vzrušující části – vytváření a vkládání tabulek přímo do dokumentu Wordu.

## Krok 1: Nastavení dokumentu

Začněme vytvořením nového dokumentu Wordu. Sem vložíme naši tabulku.

```csharp
// Cesta k adresáři s dokumenty 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

Tento kód inicializuje nový dokument aplikace Word. Budete muset nahradit `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou k adresáři dokumentů.

## Krok 2: Vytvoření objektu tabulky

Dále vytvoříme objekt tabulky. Zde definujeme strukturu naší tabulky.

```csharp
// Začneme vytvořením objektu table. Všimněte si, že musíme předat objekt document.
// konstruktoru každého uzlu. Je to proto, že každý uzel, který vytvoříme, musí patřit
// nějakému dokumentu.
Table table = new Table(doc);
doc.FirstSection.Body.AppendChild(table);
```

Zde vytvoříme novou tabulku a připojíme ji k tělu první části našeho dokumentu.

## Krok 3: Přidání řádků a buněk

Tabulka se skládá z řádků a buněk. Pojďme tyto prvky přidat krok za krokem.

### Přidání řádku

```csharp
// Zde bychom mohli zavolat metodu EnsureMinimum, která nám vytvoří řádky a buňky. Tato metoda se používá
// aby se zajistilo, že zadaný uzel je platný. V tomto případě by platná tabulka měla mít alespoň jeden řádek a jednu buňku.
// Místo toho si vytvoření řádku a tabulky vyřídíme sami.
// To by byl nejlepší způsob, jak to udělat, pokud bychom vytvářeli tabulku uvnitř algoritmu.
Row row = new Row(doc);
row.RowFormat.AllowBreakAcrossPages = true;
table.AppendChild(row);
```

Tento kód vytvoří nový řádek a přidá ho do naší tabulky.

### Přidávání buněk do řádku

Nyní přidejme do našeho řádku několik buněk. 

```csharp
Cell cell = new Cell(doc);
cell.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
cell.CellFormat.Width = 80;
cell.AppendChild(new Paragraph(doc));
cell.FirstParagraph.AppendChild(new Run(doc, "Row 1, Cell 1 Text"));
row.AppendChild(cell);
```

V tomto úryvku kódu vytvoříme buňku, nastavíme její barvu pozadí na světle modrou a definujeme její šířku. Poté do buňky přidáme odstavec a řádek pro uložení našeho textu.

## Krok 4: Klonování buněk

Abychom urychlili proces přidávání buněk, můžeme klonovat existující buňky.

```csharp
// Postup bychom pak zopakovali pro ostatní buňky a řádky v tabulce.
// Můžeme to také urychlit klonováním existujících buněk a řádků.
row.AppendChild(cell.Clone(false));
row.LastCell.AppendChild(new Paragraph(doc));
row.LastCell.FirstParagraph.AppendChild(new Run(doc, "Row 1, Cell 2 Text"));
```

Tento kód naklonuje existující buňku a přidá ji do řádku. Poté do nové buňky přidáme odstavec a řádek.

## Krok 5: Použití nastavení automatického přizpůsobení

Nakonec aplikujme na naši tabulku nastavení automatického přizpůsobení, abychom zajistili, že sloupce budou mít pevnou šířku.

```csharp
// Nyní můžeme použít libovolná nastavení automatického přizpůsobení.
table.AutoFit(AutoFitBehavior.FixedColumnWidths);
```

## Krok 6: Uložení dokumentu

S kompletně připraveným stolem je čas uložit dokument.

```csharp
doc.Save(dataDir + "WorkingWithTables.InsertTableDirectly.docx");
```

Tento kód uloží dokument s vloženou tabulkou.

## Závěr

Gratulujeme! Úspěšně jste vložili tabulku přímo do dokumentu Wordu pomocí Aspose.Words pro .NET. Tento proces lze použít k programovému vytváření složitých tabulek, což vám výrazně usnadní automatizaci dokumentů. Ať už generujete sestavy, faktury nebo jakýkoli jiný typ dokumentu, pochopení toho, jak s tabulkami manipulovat, je klíčová dovednost.

## Často kladené otázky

### Jak si mohu stáhnout Aspose.Words pro .NET?
Aspose.Words pro .NET si můžete stáhnout z [stránka ke stažení](https://releases.aspose.com/words/net/).

### Mohu si před zakoupením vyzkoušet Aspose.Words pro .NET?
Ano, můžete požádat o [bezplatná zkušební verze](https://releases.aspose.com/) zhodnotit knihovnu před nákupem.

### Jak si mohu zakoupit Aspose.Words pro .NET?
Aspose.Words pro .NET si můžete koupit od [stránka nákupu](https://purchase.aspose.com/buy).

### Kde najdu dokumentaci k Aspose.Words pro .NET?
Dokumentace je k dispozici [zde](https://reference.aspose.com/words/net/).

### Co když potřebuji pomoc s používáním Aspose.Words pro .NET?
Pro podporu můžete navštívit [Fórum Aspose.Words](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}