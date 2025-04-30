---
"description": "Naučte se, jak nastavit rozvržení v buňce pomocí Aspose.Words pro .NET v tomto komplexním průvodci. Ideální pro vývojáře, kteří chtějí přizpůsobit dokumenty Wordu."
"linktitle": "Rozložení v buňce"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Rozložení v buňce"
"url": "/cs/net/programming-with-shapes/layout-in-cell/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Rozložení v buňce

## Zavedení

Pokud jste si někdy chtěli programově doladit rozvržení buněk tabulky v dokumentech Word, jste na správném místě. Dnes se ponoříme do toho, jak nastavit rozvržení v buňce pomocí Aspose.Words pro .NET. Projdeme si praktický příklad a krok za krokem si ho rozebereme, abyste ho snadno sledovali.

## Předpoklady

Než se pustíme do kódu, ujistěte se, že máte vše potřebné:

1. Aspose.Words pro .NET: Ujistěte se, že máte nainstalovanou knihovnu Aspose.Words pro .NET. Pokud ji nemáte, můžete [stáhněte si to zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Budete potřebovat vývojové prostředí s .NET. Pokud hledáte doporučení, je Visual Studio skvělou volbou.
3. Základní znalost C#: I když budu vysvětlovat jednotlivé kroky, základní znalost C# vám pomůže snáze se v textu orientovat.
4. Adresář dokumentů: Připravte si cestu k adresáři, kam budete ukládat dokumenty. Budeme jej označovat jako `YOUR DOCUMENT DIRECTORY`.

## Importovat jmenné prostory

Chcete-li začít, ujistěte se, že do projektu importujete potřebné jmenné prostory:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Rozdělme si proces na zvládnutelné kroky.

## Krok 1: Vytvořte nový dokument

Nejprve vytvoříme nový dokument Wordu a inicializujeme `DocumentBuilder` objekt, který nám pomůže sestavit náš obsah.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 2: Vytvoření tabulky a nastavení formátu řádků

Začneme s tvorbou tabulky a zadáme výšku a pravidlo výšky pro řádky.

```csharp
builder.StartTable();
builder.RowFormat.Height = 100;
builder.RowFormat.HeightRule = HeightRule.Exactly;
```

## Krok 3: Vložení buněk a naplnění obsahem

Dále pomocí smyčky vložíme buňky do tabulky. Pro každých 7 buněk ukončíme řádek a vytvoříme novou buňku.

```csharp
for (int i = 0; i < 31; i++)
{
    if (i != 0 && i % 7 == 0) builder.EndRow();
    builder.InsertCell();
    builder.Write("Cell contents");
}
builder.EndTable();
```

## Krok 4: Přidání tvaru vodoznaku

Nyní přidáme do našeho dokumentu vodoznak. Vytvoříme `Shape` objekt a nastavit jeho vlastnosti.

```csharp
Shape watermark = new Shape(doc, ShapeType.TextPlainText)
{
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    RelativeVerticalPosition = RelativeVerticalPosition.Page,
    IsLayoutInCell = true, // Pokud bude tvar umístěn do buňky, zobrazí se mimo buňku tabulky.
    Width = 300,
    Height = 70,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    Rotation = -40
};
```

## Krok 5: Úprava vzhledu vodoznaku

Vzhled vodoznaku dále upravíme nastavením jeho barvy a textových vlastností.

```csharp
watermark.FillColor = Color.Gray;
watermark.StrokeColor = Color.Gray;
watermark.TextPath.Text = "watermarkText";
watermark.TextPath.FontFamily = "Arial";
watermark.Name = $"WaterMark_{Guid.NewGuid()}";
watermark.WrapType = WrapType.None;
```

## Krok 6: Vložení vodoznaku do dokumentu

Najdeme v dokumentu poslední spuštění a vložíme vodoznak na tuto pozici.

```csharp
Run run = doc.GetChildNodes(NodeType.Run, true)[doc.GetChildNodes(NodeType.Run, true).Count - 1] as Run;
builder.MoveTo(run);
builder.InsertNode(watermark);
```

## Krok 7: Optimalizace dokumentu pro Word 2010

Abychom zajistili kompatibilitu, optimalizujeme dokument pro Word 2010.

```csharp
doc.CompatibilityOptions.OptimizeFor(MsWordVersion.Word2010);
```

## Krok 8: Uložte dokument

Nakonec uložíme náš dokument do zadaného adresáře.

```csharp
doc.Save(dataDir + "WorkingWithShapes.LayoutInCell.docx");
```

## Závěr

tady to máte! Úspěšně jste vytvořili dokument Word s přizpůsobeným rozvržením tabulky a přidali vodoznak pomocí Aspose.Words pro .NET. Tento tutoriál si kladl za cíl poskytnout jasného a podrobného průvodce, který vám pomůže porozumět každé části procesu. S těmito dovednostmi nyní můžete programově vytvářet sofistikovanější a přizpůsobené dokumenty Word.

## Často kladené otázky

### Mohu pro text vodoznaku použít jiné písmo?
Ano, písmo můžete změnit nastavením `watermark.TextPath.FontFamily` vlastnost na požadované písmo.

### Jak upravím polohu vodoznaku?
Můžete upravit `RelativeHorizontalPosition`, `RelativeVerticalPosition`, `HorizontalAlignment`a `VerticalAlignment` vlastnosti pro úpravu polohy vodoznaku.

### Je možné použít pro vodoznak obrázek místo textu?
Rozhodně! Můžete si vytvořit `Shape` s typem `ShapeType.Image` a nastavte jeho obrázek pomocí `ImageData.SetImage` metoda.

### Mohu vytvářet tabulky s různou výškou řádků?
Ano, pro každý řádek můžete nastavit různé výšky změnou `RowFormat.Height` vlastnost před vložením buněk do daného řádku.

### Jak odstraním vodoznak z dokumentu?
Vodoznak můžete odstranit tak, že jej vyhledáte v kolekci tvarů dokumentu a zavoláte funkci `Remove` metoda.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}