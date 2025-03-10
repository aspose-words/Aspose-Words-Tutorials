---
title: Vložit plovoucí obrázek do dokumentu aplikace Word
linktitle: Vložit plovoucí obrázek do dokumentu aplikace Word
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak vložit plovoucí obrázek do dokumentu aplikace Word pomocí Aspose.Words for .NET, pomocí tohoto podrobného průvodce krok za krokem. Ideální pro vylepšení vašich dokumentů.
weight: 10
url: /cs/net/add-content-using-documentbuilder/insert-floating-image/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vložit plovoucí obrázek do dokumentu aplikace Word

## Zavedení

Představte si, že vytvoříte ohromující zprávu nebo návrh, kde jsou obrázky dokonale umístěny tak, aby doplňovaly váš text. S Aspose.Words pro .NET toho můžete dosáhnout bez námahy. Tato knihovna poskytuje výkonné funkce pro manipulaci s dokumenty, což z ní činí řešení pro vývojáře. V tomto tutoriálu se zaměříme na vložení plovoucího obrázku pomocí třídy DocumentBuilder. Ať už jste zkušený vývojář nebo teprve začínáte, tento průvodce vás provede každým krokem.

## Předpoklady

Než se do toho pustíme, ujistěte se, že máte vše, co potřebujete, abyste mohli začít:

1.  Aspose.Words for .NET: Knihovnu si můžete stáhnout z[Aspose stránku vydání](https://releases.aspose.com/words/net/).
2. Visual Studio: Jakákoli verze, která podporuje vývoj .NET.
3. Základní znalost C#: Bude užitečné porozumět základům programování v C#.
4. Soubor obrázku: Soubor obrázku, který chcete vložit, například logo nebo obrázek.

## Importovat jmenné prostory

Chcete-li ve svém projektu použít Aspose.Words, musíte importovat potřebné jmenné prostory. To se provede přidáním následujících řádků do horní části souboru C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

S těmito předpoklady a jmennými prostory jsme připraveni zahájit náš výukový program.

Pojďme si proces vložení plovoucího obrázku do dokumentu aplikace Word rozdělit na zvládnutelné kroky. Každý krok bude podrobně vysvětlen, abyste zajistili, že jej budete moci sledovat bez škytavky.

## Krok 1: Nastavte svůj projekt

Nejprve vytvořte nový projekt C# v sadě Visual Studio. Pro jednoduchost si můžete vybrat konzolovou aplikaci.

1. Otevřete Visual Studio a vytvořte nový projekt.
2. Vyberte „Console App (.NET Core)“ a klikněte na „Další“.
3. Pojmenujte svůj projekt a vyberte umístění pro jeho uložení. Klikněte na „Vytvořit“.
4. Nainstalujte Aspose.Words for .NET přes NuGet Package Manager. Klikněte pravým tlačítkem na svůj projekt v Průzkumníku řešení, vyberte "Spravovat balíčky NuGet" a vyhledejte "Aspose.Words." Nainstalujte nejnovější verzi.

## Krok 2: Inicializujte Document a DocumentBuilder

Nyní, když je váš projekt nastaven, pojďme inicializovat objekty Document a DocumentBuilder.

1.  Vytvořte novou instanci souboru`Document` třída:

```csharp
Document doc = new Document();
```

2. Inicializujte objekt DocumentBuilder:

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

 The`Document` objekt představuje dokument aplikace Word a`DocumentBuilder` pomáhá při přidávání obsahu.

## Krok 3: Definujte cestu obrázku

Dále zadejte cestu k souboru obrázku. Ujistěte se, že je váš obrázek přístupný z adresáře vašeho projektu.

Definujte adresář obrázku a název souboru obrázku:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
string imagePath = dataDir + "Transparent background logo.png";
```

 Nahradit`"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou, kde je váš obrázek uložen.

## Krok 4: Vložte plovoucí obrázek

Když je vše nastaveno, vložíme plovoucí obrázek do dokumentu.

 Použijte`InsertImage` metoda`DocumentBuilder` třída pro vložení obrázku:

```csharp
builder.InsertImage(imagePath,
   RelativeHorizontalPosition.Margin,
   100,
   RelativeVerticalPosition.Margin,
   100,
   200,
   100,
   WrapType.Square);
```

Každý parametr znamená:
- `imagePath`: Cesta k souboru obrázku.
- `RelativeHorizontalPosition.Margin`: Vodorovná poloha vzhledem k okraji.
- `100`: Horizontální odsazení od okraje (v bodech).
- `RelativeVerticalPosition.Margin`: Svislá poloha vzhledem k okraji.
- `100`: Svislé odsazení od okraje (v bodech).
- `200`: Šířka obrázku (v bodech).
- `100`: Výška obrázku (v bodech).
- `WrapType.Square`: Styl obtékání textu kolem obrázku.

## Krok 5: Uložte dokument

Nakonec dokument uložte na požadované místo.

1. Zadejte cestu k výstupnímu souboru:

```csharp
string outputPath = dataDir + "AddContentUsingDocumentBuilder.InsertFloatingImage.docx";
```

2. Uložte dokument:

```csharp
doc.Save(outputPath);
```

Váš dokument aplikace Word s plovoucím obrázkem je nyní připraven!

## Závěr

Vložení plovoucího obrázku do dokumentu aplikace Word pomocí Aspose.Words for .NET je jednoduchý proces, pokud je rozdělen do zvládnutelných kroků. Podle této příručky můžete do svých dokumentů přidat profesionálně vypadající obrázky a zvýšit tak jejich vizuální přitažlivost. Aspose.Words poskytuje robustní API, díky kterému je manipulace s dokumenty hračkou, ať už pracujete na sestavách, návrzích nebo jakémkoli jiném typu dokumentu.

## FAQ

### Mohu vložit více obrázků pomocí Aspose.Words for .NET?

 Ano, můžete vložit více obrázků opakováním`InsertImage` metoda pro každý obrázek s požadovanými parametry.

### Jak změním polohu obrázku?

 Můžete upravit`RelativeHorizontalPosition`, `RelativeVerticalPosition`a parametry odsazení pro umístění obrazu podle potřeby.

### Jaké další typy obtékání jsou k dispozici pro obrázky?

 Aspose.Words podporuje různé typy zalamování jako např`Inline`, `TopBottom`, `Tight`, `Through`a další. Můžete si vybrat ten, který nejlépe odpovídá rozvržení vašeho dokumentu.

### Mohu použít různé formáty obrázků?

Ano, Aspose.Words podporuje širokou škálu obrazových formátů včetně JPEG, PNG, BMP a GIF.

### Jak získám bezplatnou zkušební verzi Aspose.Words pro .NET?

 Můžete získat bezplatnou zkušební verzi od[Aspose zkušební stránku zdarma](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
