---
title: Export zdrojů
linktitle: Export zdrojů
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se exportovat zdroje, jako jsou CSS a písma, a zároveň ukládat dokumenty Wordu jako HTML pomocí Aspose.Words for .NET. Postupujte podle našeho podrobného průvodce.
weight: 10
url: /cs/net/programming-with-htmlsaveoptions/export-resources/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Export zdrojů

## Zavedení

Ahoj, kolegové tech nadšenci! Pokud jste někdy zjistili, že potřebujete převést dokumenty Wordu do HTML, jste na správném místě. Dnes se ponoříme do nádherného světa Aspose.Words pro .NET. Díky této výkonné knihovně je práce s dokumenty Wordu hračkou. V tomto tutoriálu si projdeme kroky k exportu zdrojů, jako jsou fonty a CSS, při ukládání dokumentu aplikace Word jako HTML pomocí Aspose.Words for .NET. Připoutejte se na zábavnou a poučnou jízdu!

## Předpoklady

Než se ponoříme do kódu, ujistěte se, že máte vše, co potřebujete, abyste mohli začít. Zde je rychlý kontrolní seznam:

1.  Visual Studio: Ujistěte se, že máte na svém počítači nainstalované Visual Studio. Můžete si jej stáhnout z[Web Visual Studio](https://visualstudio.microsoft.com/).
2.  Aspose.Words for .NET: Budete potřebovat knihovnu Aspose.Words for .NET. Pokud jej ještě nemáte, vyzkoušejte si bezplatnou zkušební verzi[Aspose Releases](https://releases.aspose.com/words/net/) nebo si jej kupte od[Obchod Aspose](https://purchase.aspose.com/buy).
3. Základní znalost C#: Základní znalost C# vám pomůže sledovat příklady kódu.

Máš to všechno? Velký! Přejděme k importu potřebných jmenných prostorů.

## Importovat jmenné prostory

Chcete-li používat Aspose.Words pro .NET, musíte do projektu zahrnout příslušné jmenné prostory. Postup je následující:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Tyto jmenné prostory jsou klíčové pro přístup k třídám a metodám Aspose.Words, které budeme používat v našem tutoriálu.

Pojďme si rozebrat proces exportu zdrojů při ukládání dokumentu aplikace Word jako HTML. Vezmeme to krok za krokem, takže je snadné to sledovat.

## Krok 1: Nastavte adresář dokumentů

Nejprve musíte zadat cestu k adresáři dokumentů. Zde je umístěn váš dokument aplikace Word a kde bude uložen soubor HTML.

```csharp
// Cesta k adresáři dokumentů.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Nahradit`"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou k vašemu adresáři.

## Krok 2: Načtěte dokument aplikace Word

 Dále načteme dokument aplikace Word, který chcete převést do HTML. Pro tento tutoriál použijeme dokument s názvem`Rendering.docx`.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Tento řádek kódu načte dokument ze zadaného adresáře.

## Krok 3: Nakonfigurujte možnosti uložení HTML

Chcete-li exportovat zdroje, jako jsou CSS a písma, musíte nakonfigurovat`HtmlSaveOptions`. Tento krok je zásadní pro zajištění správné struktury výstupu HTML a zajištění nezbytných zdrojů.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External,
    ExportFontResources = true,
    ResourceFolder = dataDir + "Resources",
    ResourceFolderAlias = "http://example.com/resources"
};
```

Pojďme si rozebrat, co každá možnost dělá:
- `CssStyleSheetType = CssStyleSheetType.External`: Tato možnost určuje, že styly CSS by měly být uloženy v externí šabloně stylů.
- `ExportFontResources = true`: Umožňuje export zdrojů písem.
- `ResourceFolder = dataDir + "Resources"`: Určuje místní složku, kam se budou ukládat prostředky (jako jsou písma a soubory CSS).
- `ResourceFolderAlias = "http://example.com/resources"`: Nastaví alias pro složku prostředků, která bude použita v souboru HTML.

## Krok 4: Uložte dokument jako HTML

S nakonfigurovanými možnostmi uložení je posledním krokem uložení dokumentu jako souboru HTML. Postup je následující:

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
```

Tento řádek kódu uloží dokument ve formátu HTML spolu s exportovanými zdroji.

## Závěr

tady to máte! Úspěšně jste exportovali zdroje při ukládání dokumentu aplikace Word jako HTML pomocí Aspose.Words for .NET. S touto výkonnou knihovnou se programová manipulace s dokumenty Word stává hračkou. Ať už pracujete na webové aplikaci, nebo jen potřebujete převést dokumenty pro offline použití, Aspose.Words vám pomůže.

## FAQ

### Mohu exportovat obrázky spolu s fonty a CSS?
 Ano, můžete! Aspose.Words for .NET podporuje také export obrázků. Jen se ujistěte, že jste nakonfigurovali`HtmlSaveOptions` podle toho.

### Existuje způsob, jak vložit CSS namísto použití externí šablony stylů?
 Absolutně. Můžete nastavit`CssStyleSheetType` na`CssStyleSheetType.Embedded` pokud dáváte přednost vloženým stylům.

### Jak mohu upravit název výstupního souboru HTML?
 V souboru můžete zadat libovolný název souboru, který se vám líbí`doc.Save` metoda. Například,`doc.Save(dataDir + "CustomFileName.html", saveOptions);`.

### Podporuje Aspose.Words jiné formáty kromě HTML?
 Ano, podporuje různé formáty včetně PDF, DOCX, TXT a dalších. Podívejte se na[dokumentace](https://reference.aspose.com/words/net/) pro úplný seznam.

### Kde mohu získat další podporu a zdroje?
Pro další pomoc navštivte stránku[Fórum podpory Aspose.Words](https://forum.aspose.com/c/words/8) . Můžete také najít podrobnou dokumentaci a příklady na[Aspose webové stránky](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
