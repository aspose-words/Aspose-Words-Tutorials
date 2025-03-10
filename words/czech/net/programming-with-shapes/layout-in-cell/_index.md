---
title: Rozložení v buňce
linktitle: Rozložení v buňce
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak nastavit rozvržení v buňce pomocí Aspose.Words pro .NET pomocí tohoto komplexního průvodce. Ideální pro vývojáře, kteří chtějí upravit dokumenty aplikace Word.
weight: 10
url: /cs/net/programming-with-shapes/layout-in-cell/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rozložení v buňce

## Zavedení

Pokud jste někdy chtěli doladit rozložení buněk tabulky v dokumentech Wordu programově, jste na správném místě. Dnes se ponoříme do toho, jak nastavit rozložení v buňce pomocí Aspose.Words pro .NET. Projdeme si praktický příklad a rozebereme ho krok za krokem, abyste jej mohli snadno sledovat.

## Předpoklady

Než se pustíme do kódu, ujistěte se, že máte vše, co potřebujete:

1.  Aspose.Words for .NET: Ujistěte se, že máte nainstalovanou knihovnu Aspose.Words for .NET. Pokud ne, můžete[stáhněte si to zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Budete potřebovat vývojové prostředí nastavené s .NET. Visual Studio je skvělá volba, pokud hledáte doporučení.
3. Základní znalost C#: I když vysvětlím každý krok, základní znalost C# vám pomůže snáze pokračovat.
4.  Adresář dokumentů: Připravte si cestu k adresáři, kam budete dokumenty ukládat. Budeme to označovat jako`YOUR DOCUMENT DIRECTORY`.

## Importovat jmenné prostory

Chcete-li začít, ujistěte se, že do projektu importujete potřebné jmenné prostory:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Pojďme si tento proces rozdělit na zvládnutelné kroky.

## Krok 1: Vytvořte nový dokument

 Nejprve vytvoříme nový dokument Word a inicializujeme a`DocumentBuilder` objekt, který nám pomůže vytvořit náš obsah.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 2: Spusťte tabulku a nastavte formát řádků

Začneme konstruovat tabulku a určíme výšku a pravidlo výšky pro řádky.

```csharp
builder.StartTable();
builder.RowFormat.Height = 100;
builder.RowFormat.HeightRule = HeightRule.Exactly;
```

## Krok 3: Vložte buňky a naplňte je obsahem

Dále smyčkou vložíme buňky do tabulky. Pro každých 7 buněk ukončíme řádek a vytvoříme nový.

```csharp
for (int i = 0; i < 31; i++)
{
    if (i != 0 && i % 7 == 0) builder.EndRow();
    builder.InsertCell();
    builder.Write("Cell contents");
}
builder.EndTable();
```

## Krok 4: Přidejte tvar vodoznaku

 Nyní do našeho dokumentu přidáme vodoznak. Vytvoříme a`Shape` objekt a nastavit jeho vlastnosti.

```csharp
Shape watermark = new Shape(doc, ShapeType.TextPlainText)
{
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    RelativeVerticalPosition = RelativeVerticalPosition.Page,
    IsLayoutInCell = true, // Zobrazte tvar mimo buňku tabulky, pokud bude umístěn do buňky.
    Width = 300,
    Height = 70,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    Rotation = -40
};
```

## Krok 5: Přizpůsobte vzhled vodoznaku

Vzhled vodoznaku dále přizpůsobíme nastavením jeho barev a vlastností textu.

```csharp
watermark.FillColor = Color.Gray;
watermark.StrokeColor = Color.Gray;
watermark.TextPath.Text = "watermarkText";
watermark.TextPath.FontFamily = "Arial";
watermark.Name = $"WaterMark_{Guid.NewGuid()}";
watermark.WrapType = WrapType.None;
```

## Krok 6: Vložte vodoznak do dokumentu

V dokumentu najdeme poslední běh a na toto místo vložíme vodoznak.

```csharp
Run run = doc.GetChildNodes(NodeType.Run, true)[doc.GetChildNodes(NodeType.Run, true).Count - 1] as Run;
builder.MoveTo(run);
builder.InsertNode(watermark);
```

## Krok 7: Optimalizujte dokument pro Word 2010

Aby byla zajištěna kompatibilita, optimalizujeme dokument pro Word 2010.

```csharp
doc.CompatibilityOptions.OptimizeFor(MsWordVersion.Word2010);
```

## Krok 8: Uložte dokument

Nakonec náš dokument uložíme do zadaného adresáře.

```csharp
doc.Save(dataDir + "WorkingWithShapes.LayoutInCell.docx");
```

## Závěr

A tady to máte! Úspěšně jste vytvořili dokument aplikace Word s přizpůsobeným rozložením tabulky a přidali jste vodoznak pomocí Aspose.Words for .NET. Cílem tohoto kurzu bylo poskytnout jasného průvodce krok za krokem, který vám pomůže porozumět každé části procesu. S těmito dovednostmi nyní můžete programově vytvářet sofistikovanější a přizpůsobené dokumenty Wordu.

## FAQ

### Mohu pro text vodoznaku použít jiné písmo?
 Ano, můžete změnit písmo nastavením`watermark.TextPath.FontFamily` vlastnost na požadované písmo.

### Jak upravím polohu vodoznaku?
 Můžete upravit`RelativeHorizontalPosition`, `RelativeVerticalPosition`, `HorizontalAlignment` a`VerticalAlignment` vlastnosti pro úpravu polohy vodoznaku.

### Je možné pro vodoznak použít místo textu obrázek?
 Absolutně! Můžete vytvořit a`Shape` s typem`ShapeType.Image` a nastavte jeho obrázek pomocí`ImageData.SetImage` metoda.

### Mohu vytvářet tabulky s různou výškou řádků?
Ano, můžete nastavit různé výšky pro každý řádek změnou`RowFormat.Height` vlastnost před vložením buněk do tohoto řádku.

### Jak odstraním vodoznak z dokumentu?
 Vodoznak můžete odstranit tak, že jej vyhledáte v kolekci tvarů dokumentu a zavoláte jej`Remove` metoda.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
