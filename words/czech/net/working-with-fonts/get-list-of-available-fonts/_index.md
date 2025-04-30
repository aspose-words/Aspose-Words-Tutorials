---
"description": "Zjistěte v tomto podrobném návodu, jak získat seznam dostupných písem pomocí Aspose.Words pro .NET. Zlepšete si své dovednosti v oblasti správy písem."
"linktitle": "Zobrazit seznam dostupných písem"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Zobrazit seznam dostupných písem"
"url": "/cs/net/working-with-fonts/get-list-of-available-fonts/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Zobrazit seznam dostupných písem

## Zavedení

Už jste někdy měli potíže se správou písem v dokumentech Word? Pokud jste vývojář v .NET, Aspose.Words pro .NET je tu, aby vám pomohla! Tato výkonná knihovna vám nejen pomáhá programově vytvářet a manipulovat s dokumenty Word, ale také nabízí rozsáhlé možnosti správy písem. V této příručce vás provedeme podrobným návodem, jak získat seznam dostupných písem pomocí Aspose.Words pro .NET. Rozdělíme si ho do srozumitelných kroků, abyste se v něm snadno zorientovali. Pojďme se tedy do toho pustit a správu písem si ulehčit!

## Předpoklady

Než začneme, budete potřebovat několik věcí:

- Aspose.Words pro .NET: Ujistěte se, že máte nainstalovanou knihovnu Aspose.Words pro .NET. Můžete si ji stáhnout z [zde](https://releases.aspose.com/words/net/).
- Visual Studio: Tento příklad používá jako vývojové prostředí Visual Studio.
- .NET Framework: Ujistěte se, že máte na svém počítači nainstalovaný .NET Framework.
- Adresář dokumentů: Cesta k adresáři, kde jsou uloženy vaše dokumenty.

## Importovat jmenné prostory

Nejprve importujte potřebné jmenné prostory do projektu:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

## Krok 1: Inicializace nastavení písma

Prvním krokem je inicializace nastavení písma. To vám umožní spravovat zdroje písem pro vaše dokumenty.

```csharp
FontSettings fontSettings = new FontSettings();
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

- FontSettings: Tato třída se používá k určení nastavení pro nahrazování písem a zdroje písem.
- Zdroje fontů: Vytvoříme seznam existujících zdrojů fontů z aktuálního nastavení fontů.

## Krok 2: Definování adresáře dokumentů

Dále zadejte cestu k adresáři s dokumenty. Zde bude Aspose.Words hledat fonty.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

- dataDir: Tato řetězcová proměnná obsahuje cestu k adresáři, kde se nacházejí vaše fonty. Nahraďte `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou.

## Krok 3: Přidání vlastní složky písem

Nyní přidejte novou složku source, která bude Aspose.Words instruovat, aby v této složce prohledala fonty.

```csharp
FolderFontSource folderFontSource = new FolderFontSource(dataDir, true);
```

- FolderFontSource: Tato třída představuje zdroj písma složky. Druhý parametr (`true`označuje, zda se mají fonty rekurzivně vyhledávat v podsložkách.

## Krok 4: Aktualizace zdrojů písem

Přidejte složku vlastních písem do seznamu existujících zdrojů písem a aktualizujte nastavení písem.

```csharp
fontSources.Add(folderFontSource);
FontSourceBase[] updatedFontSources = fontSources.ToArray();
```

- fontSources.Add(folderFontSource): Přidá vlastní složku písem k existujícím zdrojům písem.
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
- fontInfo: Instance třídy `PhysicalFontInfo` obsahující podrobnosti o každém písmu.

## Závěr

Gratulujeme! Úspěšně jste načetli seznam dostupných písem pomocí Aspose.Words pro .NET. Tento tutoriál vás provedl každým krokem, od inicializace nastavení písem až po zobrazení podrobností o písmech. S těmito znalostmi nyní můžete snadno spravovat písma ve svých dokumentech Word. Nezapomeňte, že Aspose.Words pro .NET je výkonný nástroj, který může výrazně vylepšit vaše možnosti zpracování dokumentů. Prozkoumejte tedy další funkce, které ještě více zefektivní váš proces vývoje.

## Často kladené otázky

### Mohu používat Aspose.Words pro .NET s jinými .NET frameworky?
Ano, Aspose.Words pro .NET je kompatibilní s různými frameworky .NET, včetně .NET Core a .NET 5+.

### Jak nainstaluji Aspose.Words pro .NET?
Můžete si jej nainstalovat pomocí Správce balíčků NuGet ve Visual Studiu vyhledáním „Aspose.Words“.

### Je možné přidat více vlastních složek s písmy?
Ano, můžete přidat více vlastních složek písem vytvořením několika `FolderFontSource` instance a jejich přidání do seznamu zdrojů písem.

### Mohu získat podrobnosti o písmu z konkrétního zdroje písma?
Ano, podrobnosti o písmu můžete načíst z libovolného zdroje písma zadáním indexu zdroje písma v `updatedFontSources` pole.

### Podporuje Aspose.Words pro .NET nahrazování fontů?
Ano, podporuje nahrazování písem, aby se zajistilo správné vykreslení textu, i když původní písmo není k dispozici.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}