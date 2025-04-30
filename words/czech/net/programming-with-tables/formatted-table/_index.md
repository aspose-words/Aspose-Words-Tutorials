---
"description": "Naučte se, jak vytvářet a formátovat tabulky v dokumentech Wordu pomocí Aspose.Words pro .NET s tímto podrobným návodem krok za krokem."
"linktitle": "Formátovaná tabulka"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Formátovaná tabulka"
"url": "/cs/net/programming-with-tables/formatted-table/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formátovaná tabulka

## Zavedení

Vytváření a formátování tabulek v dokumentech Word programově se může zdát jako náročný úkol, ale s Aspose.Words pro .NET se to stává jednoduchým a zvládnutelným. V tomto tutoriálu vás provedeme tím, jak vytvořit formátovanou tabulku v dokumentu Word pomocí Aspose.Words pro .NET. Probereme vše od nastavení prostředí až po uložení dokumentu s krásně formátovanou tabulkou.

## Předpoklady

Než se ponoříme do kódu, ujistěte se, že máte vše potřebné:

1. Knihovna Aspose.Words pro .NET: Stáhněte si ji z [zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: IDE, podobné Visual Studiu.
3. .NET Framework: Ujistěte se, že máte na svém počítači nainstalovaný .NET Framework.

## Importovat jmenné prostory

Před samotným napsáním kódu je třeba importovat potřebné jmenné prostory:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

## Krok 1: Nastavení adresáře dokumentů

Nejprve je třeba definovat cestu, kam bude dokument uložen.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Nahradit `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou, kam chcete dokument uložit.

## Krok 2: Inicializace dokumentu a nástroje DocumentBuilder

Nyní inicializujte nový dokument a objekt DocumentBuilder.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Ten/Ta/To `DocumentBuilder` je pomocná třída, která zjednodušuje proces vytváření dokumentů.

## Krok 3: Spuštění tabulky

Dále začněte vytvářet tabulku pomocí `StartTable` metoda.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

Vložení buňky je nutné pro zahájení tabulky.

## Krok 4: Použití formátování v celé tabulce

Můžete použít formátování, které ovlivní celou tabulku. Například nastavení levého odsazení:

```csharp
table.LeftIndent = 20.0;
```

## Krok 5: Formátování řádku záhlaví

Nastavte výšku, zarovnání a další vlastnosti řádku záhlaví.

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

V tomto kroku zvýrazníme řádek záhlaví nastavením barvy pozadí, velikosti písma a zarovnání.

## Krok 6: Vložení dalších buněk záhlaví

Vložte další buňky pro řádek záhlaví:

```csharp
builder.InsertCell();
builder.Write("Header Row,\n Cell 2");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Header Row,\n Cell 3");
builder.EndRow();
```

## Krok 7: Formátování řádků těla

Po nastavení záhlaví naformátujte tělo tabulky:

```csharp
builder.CellFormat.Shading.BackgroundPatternColor = Color.White;
builder.CellFormat.Width = 100.0;
builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;
builder.RowFormat.Height = 30.0;
builder.RowFormat.HeightRule = HeightRule.Auto;
```

## Krok 8: Vložení řádků těla

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

Nakonec uložte dokument do zadaného adresáře:

```csharp
doc.Save(dataDir + "WorkingWithTables.FormattedTable.docx");
```

Tím se vytvoří a uloží dokument Wordu s formátovanou tabulkou.

## Závěr

A máte to! Dodržováním těchto kroků můžete vytvořit dobře formátovanou tabulku v dokumentu Word pomocí knihovny Aspose.Words pro .NET. Tato výkonná knihovna usnadňuje programovou manipulaci s dokumenty Word a šetří vám čas a úsilí.

## Často kladené otázky

### Co je Aspose.Words pro .NET?
Aspose.Words pro .NET je výkonná knihovna pro programovou tvorbu, úpravu a převod dokumentů Wordu.

### Mohu použít různé barvy pro různé řádky?
Ano, na různé řádky nebo buňky můžete použít různé formátování, včetně barev.

### Je Aspose.Words pro .NET zdarma?
Aspose.Words pro .NET je placená knihovna, ale můžete si ji pořídit [bezplatná zkušební verze](https://releases.aspose.com/).

### Jak získám podporu pro Aspose.Words pro .NET?
Podporu můžete získat od [Fóra komunity Aspose](https://forum.aspose.com/c/words/8).

### Mohu s Aspose.Words pro .NET vytvářet i jiné typy dokumentů?
Ano, Aspose.Words pro .NET podporuje různé formáty dokumentů, včetně PDF, HTML a TXT.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}