---
"description": "Naučte se, jak nastavit více složek s písmy v dokumentech Word pomocí Aspose.Words pro .NET. Tento podrobný návod zajistí, že vaše dokumenty budou používat přesně ta písma, která potřebujete."
"linktitle": "Nastavení písem Složky Více složek"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Nastavení písem Složky Více složek"
"url": "/cs/net/working-with-fonts/set-fonts-folders-multiple-folders/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Nastavení písem Složky Více složek

## Zavedení

Přemýšleli jste někdy, jak spravovat více zdrojů písem v dokumentech Wordu? Možná máte sbírku písem roztroušených po různých složkách a potřebujete způsob, jak zajistit, aby je vaše dokumenty bez problémů používaly. Máte štěstí! Dnes se ponoříme do toho, jak nastavit složky s písmy pomocí Aspose.Words pro .NET. Tato příručka vás krok za krokem provede celým procesem a zajistí, aby vaše dokumenty vypadaly přesně tak, jak chcete.

## Předpoklady

Než začneme, ujistěte se, že máte vše, co potřebujete. Zde je to, co budete muset dodržovat:

- Aspose.Words pro .NET: Pokud jste tak ještě neučinili, stáhněte si a nainstalujte si Aspose.Words pro .NET. Můžete si ho stáhnout [zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Visual Studio nebo jakékoli jiné vývojové prostředí kompatibilní s .NET.
- Základní znalost C#: Trocha znalosti C# vám pomůže pochopit příklady.
- Soubory písem: Ujistěte se, že máte soubory písem uloženy v adresářích, ke kterým máte snadný přístup.

## Importovat jmenné prostory

Nejdříve si do vašeho projektu v C# importujme potřebné jmenné prostory. Tím zajistíme, že budete mít přístup ke všem funkcím Aspose.Words, které budete potřebovat.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

S touto sadou se pojďme ponořit do podrobného návodu k nastavení složek písem v Aspose.Words pro .NET.

## Krok 1: Vložte dokument

Dobře, začněme načtením dokumentu Wordu, se kterým chcete pracovat. Ujistěte se, že máte připravenou cestu k dokumentu. V tomto příkladu použijeme dokument s názvem „Rendering.docx“.

```csharp
// Cesta k adresáři s dokumenty
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

Zde načteme dokument ze zadaného adresáře. Docela jednoduché, že?

## Krok 2: Vytvoření objektu FontSettings

Dále musíme vytvořit `FontSettings` objekt. Tento objekt nám umožní spravovat zdroje písem pro náš dokument.

```csharp
FontSettings fontSettings = new FontSettings();
```

Tento `FontSettings` Objekt nám pomůže definovat, které složky s fonty máme použít.

## Krok 3: Nastavení složek písem

Nyní přichází klíčová část – nastavení složek s fonty. Zde určíte adresáře, kde se vaše fonty nacházejí. V tomto příkladu máme fonty ve složkách „C:\MyFonts“ a „D:\Misc\Fonts“.

```csharp
fontSettings.SetFontsFolders(new[] { @"C:\MyFonts\", @"D:\Misc\Fonts\" }, true);
```

Druhý parametr (`true`) označuje, že tyto složky přepíší všechny výchozí zdroje písem. Pokud chcete zachovat i systémové zdroje písem, můžete použít kombinaci `GetFontSources` a `SetFontSources`.

## Krok 4: Použití nastavení písma v dokumentu

Po nastavení složek s fonty musíme tato nastavení použít v našem dokumentu. Tím zajistíme, že dokument během vykreslování použije zadaná písma.

```csharp
doc.FontSettings = fontSettings;
```

## Krok 5: Uložte dokument

Nakonec si dokument uložíme. Uložíme ho jako PDF, abychom viděli písma v akci.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersMultipleFolders.pdf");
```

A tady to máte! Úspěšně jste nastavili více složek s písmy pro váš dokument.

## Závěr

Správa písem v dokumentech se může zdát jako náročný úkol, ale s Aspose.Words pro .NET je to hračka! Dodržováním těchto jednoduchých kroků zajistíte, že vaše dokumenty budou vypadat profesionálně a budou používat přesně ta písma, která potřebujete. Ať už pracujete na projektu, který vyžaduje specifický branding, nebo chcete mít jen větší kontrolu nad vzhledem dokumentu, nastavení složek s písmy je dovednost, kterou stojí za to zvládnout.

## Často kladené otázky

### Mohu pro složky s písmy použít síťové cesty?
Ano, pro složky s písmy můžete použít síťové cesty. Stačí se ujistit, že jsou cesty přístupné z vaší aplikace.

### Co se stane, když v zadaných složkách chybí písmo?
Pokud chybí písmo, Aspose.Words se vrátí k výchozímu zadanému písmu nebo použije náhradní písmo.

### Mohu přidat složky s fonty bez přepsání systémových fontů?
Rozhodně! Použijte `FontSettings.GetFontSources` načíst existující zdroje a zkombinovat je s vlastními složkami pomocí `FontSettings.SetFontSources`.

### Existuje omezení počtu složek s písmy, které mohu přidat?
Neexistuje žádný striktní limit pro počet složek s fonty. Mějte však na paměti výkon, protože více složek může prodloužit dobu načítání fontů.

### Jak mohu zkontrolovat, která písma jsou v mém dokumentu použita?
Můžete použít `FontSettings.GetFontsSources` metoda pro načtení a kontrolu zdrojů písem aktuálně nastavených pro váš dokument.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}