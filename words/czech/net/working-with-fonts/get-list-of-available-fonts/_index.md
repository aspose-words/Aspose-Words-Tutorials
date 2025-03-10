---
title: Získejte seznam dostupných písem
linktitle: Získejte seznam dostupných písem
second_title: Aspose.Words API pro zpracování dokumentů
description: Zjistěte, jak získat seznam dostupných písem pomocí Aspose.Words pro .NET v tomto podrobném návodu krok za krokem. Zvyšte své dovednosti v oblasti správy písem.
weight: 10
url: /cs/net/working-with-fonts/get-list-of-available-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Získejte seznam dostupných písem

## Zavedení

Přistihli jste se někdy, že máte problémy se správou písem v dokumentech aplikace Word? Pokud jste vývojář .NET, Aspose.Words for .NET je tu, aby vás zachránil! Tato výkonná knihovna vám nejen pomáhá vytvářet a manipulovat s dokumenty Wordu programově, ale nabízí také rozsáhlé možnosti správy písem. V této příručce vás provedeme podrobným návodem, jak získat seznam dostupných písem pomocí Aspose.Words pro .NET. Rozdělíme to do stravitelných kroků, abyste se ujistili, že je budete snadno sledovat. Pojďme se tedy ponořit a udělat ze správy písem hračku!

## Předpoklady

Než začneme, budete potřebovat několik věcí:

-  Aspose.Words for .NET: Ujistěte se, že máte nainstalovanou knihovnu Aspose.Words for .NET. Můžete si jej stáhnout z[zde](https://releases.aspose.com/words/net/).
- Visual Studio: Tento příklad používá Visual Studio jako vývojové prostředí.
- .NET Framework: Ujistěte se, že máte na svém počítači nainstalované rozhraní .NET Framework.
- Adresář dokumentů: Cesta k adresáři, kde jsou uloženy vaše dokumenty.

## Importovat jmenné prostory

Nejprve do projektu importujte potřebné jmenné prostory:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

## Krok 1: Inicializujte nastavení písma

Prvním krokem je inicializace nastavení písma. To vám umožní spravovat zdroje písem pro vaše dokumenty.

```csharp
FontSettings fontSettings = new FontSettings();
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

- FontSettings: Tato třída se používá ke specifikaci nastavení pro nahrazování písem a zdroje písem.
- Zdroje písem: Vytváříme seznam existujících zdrojů písem z aktuálního nastavení písem.

## Krok 2: Definujte adresář dokumentů

Dále zadejte cestu k adresáři dokumentů. Zde bude Aspose.Words hledat fonty.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

-  dataDir: Tato řetězcová proměnná obsahuje cestu k adresáři, kde jsou umístěny vaše fonty. Nahradit`"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou.

## Krok 3: Přidejte vlastní složku písem

Nyní přidejte nový zdroj složky a instruujte Aspose.Words, aby v této složce hledala písma.

```csharp
FolderFontSource folderFontSource = new FolderFontSource(dataDir, true);
```

- FolderFontSource: Tato třída představuje zdroj písem složky. Druhý parametr (`true`) označuje, zda se mají písma hledat rekurzivně v podsložkách.

## Krok 4: Aktualizujte zdroje písem

Přidejte složku vlastních písem do seznamu existujících zdrojů písem a aktualizujte nastavení písem.

```csharp
fontSources.Add(folderFontSource);
FontSourceBase[] updatedFontSources = fontSources.ToArray();
```

- fontSources.Add(folderFontSource): Přidá vlastní složku písem ke stávajícím zdrojům písem.
- updatedFontSources: Převede seznam zdrojů písem na pole.

## Krok 5: Načtení a zobrazení písem

Nakonec načtěte dostupná písma a zobrazte jejich podrobnosti.

```csharp
foreach (PhysicalFontInfo fontInfo in updatedFontSources[0].GetAvailableFonts())
{
    Console.WriteLine("FontFamilyName : " + fontInfo.FontFamilyName);
    Console.WriteLine("FullFontName  : " + fontInfo.FullFontName);
    Console.WriteLine("Version  : " + fontInfo.Version);
    Console.WriteLine("FilePath : " + fontInfo.FilePath);
}
```

- GetAvailableFonts(): Načte seznam dostupných písem z prvního zdroje písem v aktualizovaném seznamu.
-  fontInfo: Instance`PhysicalFontInfo` obsahující podrobnosti o každém fontu.

## Závěr

Gratuluji! Úspěšně jste získali seznam dostupných písem pomocí Aspose.Words for .NET. Tento tutoriál vás provede každým krokem, od inicializace nastavení písma až po zobrazení podrobností o písmu. S těmito znalostmi nyní můžete snadno spravovat písma v dokumentech aplikace Word. Pamatujte, že Aspose.Words for .NET je výkonný nástroj, který může výrazně zlepšit vaše možnosti zpracování dokumentů. Takže pokračujte a prozkoumejte další funkce, aby byl váš vývojový proces ještě efektivnější.

## FAQ

### Mohu používat Aspose.Words pro .NET s jinými frameworky .NET?
Ano, Aspose.Words for .NET je kompatibilní s různými frameworky .NET včetně .NET Core a .NET 5+.

### Jak nainstaluji Aspose.Words for .NET?
Můžete jej nainstalovat přes NuGet Package Manager ve Visual Studiu vyhledáním „Aspose.Words“.

### Je možné přidat více vlastních složek písem?
 Ano, můžete přidat více vlastních složek písem vytvořením více`FolderFontSource` instance a jejich přidání do seznamu zdrojů písem.

### Mohu načíst podrobnosti o písmu z konkrétního zdroje písem?
 Ano, podrobnosti o písmu můžete načíst z libovolného zdroje písem zadáním indexu zdroje písem v souboru`updatedFontSources` pole.

### Podporuje Aspose.Words for .NET náhradu písem?
Ano, podporuje nahrazování písem, aby bylo zajištěno, že se text vykreslí správně, i když původní písmo není k dispozici.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
