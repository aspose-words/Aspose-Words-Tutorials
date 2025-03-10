---
title: Formátovaná tabulka
linktitle: Formátovaná tabulka
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se vytvářet a formátovat tabulky v dokumentech aplikace Word pomocí Aspose.Words for .NET pomocí tohoto podrobného průvodce krok za krokem.
weight: 10
url: /cs/net/programming-with-tables/formatted-table/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formátovaná tabulka

## Zavedení

Vytváření a formátování tabulek v dokumentech aplikace Word programově se může zdát jako skličující úkol, ale s Aspose.Words pro .NET se to stává přímočarým a ovladatelným. V tomto tutoriálu vás provedeme vytvořením formátované tabulky v dokumentu aplikace Word pomocí Aspose.Words for .NET. Pokryjeme vše od nastavení prostředí až po uložení dokumentu pomocí krásně formátované tabulky.

## Předpoklady

Než se ponoříte do kódu, ujistěte se, že máte vše, co potřebujete:

1. Aspose.Words for .NET Library: Stáhněte si ji z[zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: IDE jako Visual Studio.
3. .NET Framework: Ujistěte se, že máte na svém počítači nainstalované rozhraní .NET Framework.

## Importovat jmenné prostory

Před napsáním skutečného kódu musíte importovat potřebné jmenné prostory:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

## Krok 1: Nastavte adresář dokumentů

Nejprve musíte definovat cestu, kam bude váš dokument uložen.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Nahradit`"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou, kam chcete dokument uložit.

## Krok 2: Inicializujte Document a DocumentBuilder

Nyní inicializujte nový dokument a objekt DocumentBuilder.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 The`DocumentBuilder` je pomocná třída, která zjednodušuje proces vytváření dokumentů.

## Krok 3: Spusťte tabulku

 Dále začněte vytvářet tabulku pomocí`StartTable` metoda.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

Pro spuštění tabulky je nutné vložit buňku.

## Krok 4: Použijte formátování na šířku tabulky

Můžete použít formátování, které ovlivní celou tabulku. Například nastavení levého odsazení:

```csharp
table.LeftIndent = 20.0;
```

## Krok 5: Naformátujte řádek záhlaví

Nastavte výšku, zarovnání a další vlastnosti pro řádek záhlaví.

```csharp
builder.RowFormat.Height = 40.0;
builder.RowFormat.HeightRule = HeightRule.AtLeast;
builder.CellFormat.Shading.BackgroundPatternColor = Color.FromArgb(198, 217, 241);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Font.Size = 16;
builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.CellFormat.Width = 100.0;
builder.Write("Header Row,\n Cell 1");
```

V tomto kroku dáme vyniknout řádku záhlaví nastavením barvy pozadí, velikosti písma a zarovnání.

## Krok 6: Vložte další buňky záhlaví

Vložte další buňky pro řádek záhlaví:

```csharp
builder.InsertCell();
builder.Write("Header Row,\n Cell 2");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Header Row,\n Cell 3");
builder.EndRow();
```

## Krok 7: Naformátujte řádky těla

Po nastavení záhlaví naformátujte tělo tabulky:

```csharp
builder.CellFormat.Shading.BackgroundPatternColor = Color.White;
builder.CellFormat.Width = 100.0;
builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;
builder.RowFormat.Height = 30.0;
builder.RowFormat.HeightRule = HeightRule.Auto;
```

## Krok 8: Vložte řádky těla

Vložte řádky těla s obsahem:

```csharp
builder.InsertCell();
builder.Font.Size = 12;
builder.Font.Bold = false;
builder.Write("Row 1, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 1, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 1, Cell 3 Content");
builder.EndRow();
```

Opakujte pro další řádky:

```csharp
builder.InsertCell();
builder.CellFormat.Width = 100.0;
builder.Write("Row 2, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 2, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 2, Cell 3 Content.");
builder.EndRow();
builder.EndTable();
```

## Krok 9: Uložte dokument

Nakonec uložte dokument do určeného adresáře:

```csharp
doc.Save(dataDir + "WorkingWithTables.FormattedTable.docx");
```

Tím vytvoříte a uložíte dokument aplikace Word s formátovanou tabulkou.

## Závěr

A tady to máte! Pomocí následujících kroků můžete vytvořit dobře formátovanou tabulku v dokumentu aplikace Word pomocí Aspose.Words for .NET. Tato výkonná knihovna usnadňuje programovou manipulaci s dokumenty Wordu a šetří vám čas a námahu.

## FAQ

### Co je Aspose.Words for .NET?
Aspose.Words for .NET je výkonná knihovna pro vytváření, úpravy a převod dokumentů aplikace Word programově.

### Mohu použít různé barvy pro různé řádky?
Ano, na různé řádky nebo buňky můžete použít různé formátování, včetně barev.

### Je Aspose.Words for .NET zdarma?
 Aspose.Words for .NET je placená knihovna, ale můžete získat a[zkušební verze zdarma](https://releases.aspose.com/).

### Jak získám podporu pro Aspose.Words for .NET?
 Můžete získat podporu od[Aspose komunitní fóra](https://forum.aspose.com/c/words/8).

### Mohu pomocí Aspose.Words for .NET vytvářet jiné typy dokumentů?
Ano, Aspose.Words for .NET podporuje různé formáty dokumentů, včetně PDF, HTML a TXT.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
