---
"description": "Naučte se, jak formátovat tabulky a buňky s různými ohraničeními pomocí Aspose.Words pro .NET. Vylepšete své dokumenty Word pomocí přizpůsobených stylů tabulek a stínování buněk."
"linktitle": "Formátování tabulky a buňky s různými ohraničeními"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Formátování tabulky a buňky s různými ohraničeními"
"url": "/cs/net/programming-with-table-styles-and-formatting/format-table-and-cell-with-different-borders/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formátování tabulky a buňky s různými ohraničeními

## Zavedení

Už jste někdy zkoušeli, jak vylepšit vzhled vašich dokumentů Word úpravou okrajů tabulek a buněk? Pokud ne, čeká vás lahůdka! Tento tutoriál vás provede procesem formátování tabulek a buněk s různými okraji pomocí Aspose.Words pro .NET. Představte si, že máte možnost změnit vzhled svých tabulek jen pomocí několika řádků kódu. Zaujalo vás to? Pojďme se do toho pustit a prozkoumat, jak toho snadno dosáhnout.

## Předpoklady

Než začneme, ujistěte se, že máte splněny následující předpoklady:
- Základní znalost programování v C#.
- Visual Studio nainstalované na vašem počítači.
- Knihovna Aspose.Words pro .NET. Pokud ji ještě nemáte nainstalovanou, můžete si ji stáhnout. [zde](https://releases.aspose.com/words/net/).
- Platná licence Aspose. Bezplatnou zkušební verzi nebo dočasnou licenci můžete získat od [zde](https://purchase.aspose.com/temporary-license/).

## Importovat jmenné prostory

Pro práci s Aspose.Words pro .NET je nutné do projektu importovat potřebné jmenné prostory. Na začátek souboru s kódem přidejte následující direktivy using:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;
```

## Krok 1: Inicializace dokumentu a DocumentBuilderu

Nejprve je třeba vytvořit nový dokument a inicializovat DocumentBuilder, který pomáhá s vytvářením obsahu dokumentu. 

```csharp
// Cesta k adresáři s dokumenty 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 2: Začněte vytvářet tabulku

Dále použijte DocumentBuilder k zahájení vytváření tabulky a vložení první buňky.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

## Krok 3: Nastavení ohraničení tabulky

Nastavte ohraničení pro celou tabulku. Tento krok zajistí, že všechny buňky v tabulce budou mít konzistentní styl ohraničení, pokud není uvedeno jinak.

```csharp
// Nastavte ohraničení pro celou tabulku.
table.SetBorders(LineStyle.Single, 2.0, Color.Black);
```

## Krok 4: Použití stínování buněk

Pro vizuální odlišení buněk použijte na ně stínování. V tomto příkladu nastavíme barvu pozadí první buňky na červenou.


```csharp
// Nastavte stínování buňky pro tuto buňku.
builder.CellFormat.Shading.BackgroundPatternColor = Color.Red;
builder.Writeln("Cell #1");
```

## Krok 5: Vložte další buňku s jiným stínováním

Vložte druhou buňku a použijte jinou barvu stínování. Tabulka se tak stane barevnější a snáze čitelnou.

```csharp
builder.InsertCell();
// Zadejte jiné stínování buněk pro druhou buňku.
builder.CellFormat.Shading.BackgroundPatternColor = Color.Green;
builder.Writeln("Cell #2");
builder.EndRow();
```

## Krok 6: Vymazání formátování buněk

Vymažte formátování buněk z předchozích operací, abyste zajistili, že další buňky nebudou dědit stejné styly.


```csharp
// Vymaže formátování buněk z předchozích operací.
builder.CellFormat.ClearFormatting();
```

## Krok 7: Úprava ohraničení pro konkrétní buňky

Upravte ohraničení konkrétních buněk tak, aby vynikly. Zde nastavíme větší ohraničení pro první buňku nového řádku.

```csharp
builder.InsertCell();
// Vytvořte větší ohraničení pro první buňku v tomto řádku. Bude to jiné.
// ve srovnání s okraji stanovenými pro stůl.
builder.CellFormat.Borders.Left.LineWidth = 4.0;
builder.CellFormat.Borders.Right.LineWidth = 4.0;
builder.CellFormat.Borders.Top.LineWidth = 4.0;
builder.CellFormat.Borders.Bottom.LineWidth = 4.0;
builder.Writeln("Cell #3");
```

## Krok 8: Vložení poslední buňky

Vložte poslední buňku a ujistěte se, že je její formátování vymazáno, aby se použily výchozí styly tabulky.

```csharp
builder.InsertCell();
builder.CellFormat.ClearFormatting();
builder.Writeln("Cell #4");
```

## Krok 9: Uložte dokument

Nakonec uložte dokument do zadaného adresáře.

```csharp
doc.Save(dataDir + "WorkingWithTableStylesAndFormatting.FormatTableAndCellWithDifferentBorders.docx");
```

## Závěr

A tady to máte! Právě jste se naučili, jak formátovat tabulky a buňky s různými ohraničeními pomocí Aspose.Words pro .NET. Úpravou ohraničení tabulek a stínování buněk můžete výrazně vylepšit vizuální atraktivitu vašich dokumentů. Tak se do toho pusťte, experimentujte s různými styly a nechte své dokumenty vyniknout!

## Často kladené otázky

### Mohu pro každou buňku použít různé styly ohraničení?
Ano, pro každou buňku můžete nastavit různé styly ohraničení pomocí `CellFormat.Borders` vlastnictví.

### Jak mohu odstranit všechny okraje z tabulky?
Všechny ohraničení můžete odstranit nastavením stylu ohraničení na `LineStyle.None`.

### Je možné nastavit pro každou buňku jinou barvu ohraničení?
Rozhodně! Barvu ohraničení pro každou buňku si můžete přizpůsobit pomocí `CellFormat.Borders.Color` vlastnictví.

### Mohu použít obrázky jako pozadí buněk?
I když Aspose.Words přímo nepodporuje obrázky jako pozadí buněk, můžete do buňky vložit obrázek a upravit jeho velikost tak, aby pokrýval oblast buňky.

### Jak sloučím buňky v tabulce?
Buňky můžete sloučit pomocí `CellFormat.HorizontalMerge` a `CellFormat.VerticalMerge` vlastnosti.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}