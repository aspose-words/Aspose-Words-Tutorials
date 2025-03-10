---
title: Nastavit složky písem více složek
linktitle: Nastavit složky písem více složek
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak nastavit více složek písem v dokumentech aplikace Word pomocí Aspose.Words for .NET. Tento podrobný průvodce zajistí, že vaše dokumenty budou používat přesně ta písma, která potřebujete.
weight: 10
url: /cs/net/working-with-fonts/set-fonts-folders-multiple-folders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nastavit složky písem více složek

## Zavedení

Přemýšleli jste někdy, jak spravovat více zdrojů písem v dokumentech aplikace Word? Možná máte sbírku písem roztroušených v různých složkách a potřebujete způsob, jak zajistit, aby je vaše dokumenty používaly bez problémů. Tak to máš štěstí! Dnes se ponoříme do toho, jak nastavit složky písem pomocí Aspose.Words pro .NET. Tato příručka vás provede procesem krok za krokem a zajistí, aby vaše dokumenty vypadaly přesně tak, jak chcete.

## Předpoklady

Než začneme, ujistěte se, že máte vše, co potřebujete. Zde je to, co budete muset dodržet:

-  Aspose.Words for .NET: Pokud jste to ještě neudělali, stáhněte si a nainstalujte Aspose.Words for .NET. Můžete to získat[zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Visual Studio nebo jakékoli jiné vývojové prostředí kompatibilní s .NET.
- Základní znalost C#: Malá znalost C# vám pomůže postupovat podle příkladů.
- Soubory písem: Ujistěte se, že máte soubory písem uloženy v adresářích, ke kterým máte snadný přístup.

## Importovat jmenné prostory

Nejprve importujme potřebné jmenné prostory do vašeho projektu C#. To zajišťuje, že budete mít přístup ke všem funkcím Aspose.Words, které budete potřebovat.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

S touto sadou se pojďme ponořit do podrobného průvodce nastavením složek písem v Aspose.Words pro .NET.

## Krok 1: Vložte svůj dokument

Dobře, začněme načtením dokumentu aplikace Word, se kterým chcete pracovat. Ujistěte se, že máte připravenou cestu k dokumentu. V tomto příkladu použijeme dokument s názvem „Rendering.docx“.

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

Zde načteme dokument ze zadaného adresáře. Dost jednoduché, že?

## Krok 2: Vytvořte objekt FontSettings

 Dále musíme vytvořit a`FontSettings` objekt. Tento objekt nám umožní spravovat zdroje písem pro náš dokument.

```csharp
FontSettings fontSettings = new FontSettings();
```

 Tento`FontSettings`objekt nám pomůže definovat, které složky písem použít.

## Krok 3: Nastavte složky písem

Nyní přichází klíčová část – nastavení složek písem. Zde zadáváte adresáře, kde jsou umístěny vaše fonty. V tomto příkladu máme písma v "C:\MyFonts\" a "D:\Misc\Fonts\".

```csharp
fontSettings.SetFontsFolders(new[] { @"C:\MyFonts\", @"D:\Misc\Fonts\" }, true);
```

Druhý parametr (`true` ) znamená, že tyto složky přepíší všechny výchozí zdroje písem. Pokud chcete zachovat i systémové zdroje písem, můžete použít kombinaci`GetFontSources` a`SetFontSources`.

## Krok 4: Použijte nastavení písma na dokument

S nastavenými složkami písem musíme tato nastavení použít na náš dokument. Tím zajistíte, že dokument během vykreslování používá zadaná písma.

```csharp
doc.FontSettings = fontSettings;
```

## Krok 5: Uložte dokument

Nakonec dokument uložíme. Uložíme jej jako PDF, abychom viděli písma v akci.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersMultipleFolders.pdf");
```

A tady to máte! Úspěšně jste pro svůj dokument nastavili několik složek písem.

## Závěr

Správa písem ve vašich dokumentech se může zdát jako skličující úkol, ale s Aspose.Words pro .NET je to hračka! Pomocí těchto jednoduchých kroků zajistíte, že vaše dokumenty budou vypadat profesionálně a budou používat přesně ta písma, která potřebujete. Ať už pracujete na projektu, který vyžaduje specifický branding, nebo jen chcete mít větší kontrolu nad vzhledem vašeho dokumentu, nastavení složek písem je dovednost, kterou stojí za to zvládnout.

## FAQ

### Mohu použít síťové cesty pro složky písem?
Ano, pro složky písem můžete použít síťové cesty. Jen se ujistěte, že cesty jsou přístupné z vaší aplikace.

### Co se stane, když v zadaných složkách chybí písmo?
Pokud písmo chybí, Aspose.Words přejde zpět na zadané výchozí písmo nebo použije náhradní písmo.

### Mohu přidat složky písem bez přepsání systémových písem?
 Absolutně! Použití`FontSettings.GetFontSources` k načtení existujících zdrojů a jejich zkombinování s vašimi vlastními složkami pomocí`FontSettings.SetFontSources`.

### Existuje nějaký limit na počet složek písem, které mohu přidat?
Neexistuje žádný přísný limit na počet složek písem. Pamatujte však na výkon, protože více složek může prodloužit dobu načítání písem.

### Jak mohu zkontrolovat, která písma jsou použita v mém dokumentu?
 Můžete použít`FontSettings.GetFontsSources` metoda pro načtení a kontrolu zdrojů písem aktuálně nastavených pro váš dokument.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
