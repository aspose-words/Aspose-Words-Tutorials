---
title: Vložit tabulku přímo
linktitle: Vložit tabulku přímo
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se vkládat tabulky přímo do dokumentů aplikace Word pomocí Aspose.Words for .NET. Chcete-li zjednodušit vytváření dokumentů, postupujte podle našeho podrobného průvodce krok za krokem.
weight: 10
url: /cs/net/programming-with-tables/insert-table-directly/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vložit tabulku přímo

## Zavedení
Vytváření tabulek programově může být docela problém, zvláště když se zabýváte složitými strukturami dokumentů. Ale nebojte se, jsme tu, abychom to pro vás rozebrali! V této příručce si projdeme kroky vložení tabulky přímo do dokumentu aplikace Word pomocí Aspose.Words for .NET. Ať už jste zkušený vývojář nebo teprve začínáte, tento tutoriál vám pomůže tento proces snadno zvládnout.

## Předpoklady

Než se ponoříte do kódu, ujistěte se, že máte vše, co potřebujete, abyste mohli začít. Zde je rychlý kontrolní seznam:

1.  Knihovna Aspose.Words for .NET: Ujistěte se, že jste si stáhli a nainstalovali knihovnu Aspose.Words for .NET. Můžete to získat z[stránka ke stažení](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Vývojové prostředí jako Visual Studio.
3. Základní znalost C#: Pochopení základů programování v C#.
4. Adresář dokumentů: Cesta k adresáři, kam budete ukládat dokumenty.

S těmito předpoklady jste připraveni začít kódovat!

## Importovat jmenné prostory

Nejprve importujme potřebné jmenné prostory. Tyto jmenné prostory nám poskytnou třídy a metody potřebné pro práci s dokumenty aplikace Word.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

Nyní, když máme své jmenné prostory na místě, přejděme k zajímavé části – vytváření a vkládání tabulek přímo do dokumentu aplikace Word.

## Krok 1: Nastavení dokumentu

Začněme nastavením nového dokumentu aplikace Word. Zde bude vložena naše tabulka.

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

 Tento kód inicializuje nový dokument aplikace Word. Budete muset vyměnit`"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou k vašemu adresáři dokumentů.

## Krok 2: Vytvoření objektu tabulky

Dále vytvoříme objekt tabulky. Zde definujeme strukturu naší tabulky.

```csharp
// Začneme vytvořením objektu tabulky. Všimněte si, že musíme předat objekt dokumentu
// ke konstruktoru každého uzlu. Je to proto, že každý uzel, který vytvoříme, musí patřit
// k nějakému dokumentu.
Table table = new Table(doc);
doc.FirstSection.Body.AppendChild(table);
```

Zde vytvoříme novou tabulku a připojíme ji k tělu prvního oddílu našeho dokumentu.

## Krok 3: Přidání řádků a buněk

Tabulka se skládá z řádků a buněk. Přidejme tyto prvky postupně.

### Přidání řádku

```csharp
// Zde bychom mohli zavolat SecureMinimum, aby za nás vytvořili řádky a buňky. Tato metoda se používá
// abyste se ujistili, že zadaný uzel je platný. V tomto případě by platná tabulka měla mít alespoň jeden řádek a jednu buňku.
// Místo toho si vytvoříme řádek a tabulku sami.
// To by byl nejlepší způsob, jak toho dosáhnout, pokud bychom vytvářeli tabulku uvnitř algoritmu.
Row row = new Row(doc);
row.RowFormat.AllowBreakAcrossPages = true;
table.AppendChild(row);
```

Tento kód vytvoří nový řádek a připojí jej k naší tabulce.

### Přidání buněk do řádku

Nyní přidáme několik buněk do našeho řádku. 

```csharp
Cell cell = new Cell(doc);
cell.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
cell.CellFormat.Width = 80;
cell.AppendChild(new Paragraph(doc));
cell.FirstParagraph.AppendChild(new Run(doc, "Row 1, Cell 1 Text"));
row.AppendChild(cell);
```

V tomto úryvku vytvoříme buňku, nastavíme její barvu pozadí na světle modrou a definujeme její šířku. Poté do buňky přidáme odstavec a běh, abychom udrželi náš text.

## Krok 4: Klonování buněk

Pro urychlení procesu přidávání buněk můžeme klonovat existující buňky.

```csharp
// Poté bychom postup opakovali pro další buňky a řádky v tabulce.
//Věci můžeme urychlit také klonováním existujících buněk a řádků.
row.AppendChild(cell.Clone(false));
row.LastCell.AppendChild(new Paragraph(doc));
row.LastCell.FirstParagraph.AppendChild(new Run(doc, "Row 1, Cell 2 Text"));
```

Tento kód naklonuje existující buňku a přidá ji do řádku. Do nové buňky pak přidáme odstavec a běh.

## Krok 5: Použití nastavení Auto Fit

Nakonec použijeme nastavení automatického přizpůsobení na naši tabulku, abychom zajistili, že sloupce budou mít pevnou šířku.

```csharp
// Nyní můžeme použít libovolné nastavení automatického přizpůsobení.
table.AutoFit(AutoFitBehavior.FixedColumnWidths);
```

## Krok 6: Uložení dokumentu

Když je náš stůl plně připraven, je čas dokument uložit.

```csharp
doc.Save(dataDir + "WorkingWithTables.InsertTableDirectly.docx");
```

Tento kód uloží dokument s vloženou tabulkou.

## Závěr

Gratuluji! Úspěšně jste vložili tabulku přímo do dokumentu aplikace Word pomocí Aspose.Words for .NET. Tento proces lze použít k programovému vytváření složitých tabulek, což výrazně zjednoduší vaše úlohy automatizace dokumentů. Ať už generujete sestavy, faktury nebo jakýkoli jiný typ dokumentu, pochopení toho, jak manipulovat s tabulkami, je zásadní dovedností.

## FAQ

### Jak si mohu stáhnout Aspose.Words pro .NET?
 Aspose.Words for .NET si můžete stáhnout z webu[stránka ke stažení](https://releases.aspose.com/words/net/).

### Mohu Aspose.Words for .NET vyzkoušet před nákupem?
 Ano, můžete požádat o a[zkušební verze zdarma](https://releases.aspose.com/) zhodnotit knihovnu před nákupem.

### Jak koupím Aspose.Words pro .NET?
Můžete si koupit Aspose.Words pro .NET od[nákupní stránku](https://purchase.aspose.com/buy).

### Kde najdu dokumentaci k Aspose.Words pro .NET?
 Dokumentace je k dispozici[zde](https://reference.aspose.com/words/net/).

### Co když potřebuji podporu při používání Aspose.Words pro .NET?
 Pro podporu můžete navštívit[Fórum Aspose.Words](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
