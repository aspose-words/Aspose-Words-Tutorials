---
"description": "Naučte se, jak překládat názvy písem v dokumentech Word při převodu do HTML pomocí Aspose.Words pro .NET. Podrobný návod s podrobným vysvětlením."
"linktitle": "Rozlišení názvů písem"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Rozlišení názvů písem"
"url": "/cs/net/programming-with-htmlsaveoptions/resolve-font-names/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Rozlišení názvů písem

## Zavedení

Ahoj, kolegové programátoři! Pokud jste se někdy při ukládání dokumentů Wordu ve formátu HTML potýkali s problémy s písmy, nejste sami. Fonty mohou být záludné, ale nebojte se, kryji vám záda. Dnes se ponoříme do toho, jak pomocí Aspose.Words pro .NET přeložit názvy písem v dokumentech Word. Tato příručka vás krok za krokem provede celým procesem a zajistí, aby vaše písma vypadala ve formátu HTML správně.

## Předpoklady

Než začneme, ujistěte se, že máte vše, co potřebujete:

1. Aspose.Words pro .NET: Pokud jste tak ještě neučinili, můžete si ho stáhnout [zde](https://releases.aspose.com/words/net/).
2. Platná licence: Licenci si můžete zakoupit [zde](https://purchase.aspose.com/buy) nebo si pořídit dočasný řidičský průkaz [zde](https://purchase.aspose.com/temporary-license/).
3. Základní znalost C# a .NET: Tento tutoriál předpokládá, že máte zkušenosti se základními programovacími koncepty v C#.
4. Visual Studio: Jakákoli verze, která podporuje .NET framework.

Teď, když máme splněny všechny předpoklady, pojďme se pustit do akce!

## Importovat jmenné prostory

Než začneme s kódováním, ujistěte se, že jste do projektu importovali potřebné jmenné prostory. To je klíčové pro přístup k funkcím Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Nastavení adresáře dokumentů

Nejdříve si nastavme cestu k adresáři s vašimi dokumenty. Zde se nachází váš dokument Wordu a kam budete ukládat svůj výstup.

```csharp
// Cesta k adresáři s dokumenty.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Vysvětlení:
Zde, `dataDir` obsahuje cestu k adresáři s dokumenty. Nahraďte `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou ve vašem systému.

## Krok 2: Načtení dokumentu Word

Dále musíme načíst dokument Wordu, který chceme zpracovat. Tento dokument by měl obsahovat písma, která chcete rozpoznat.

```csharp
Document doc = new Document(dataDir + "Missing font.docx");
```

Vysvětlení:
Vytvoříme `Document` objekt a načtěte dokument Word s názvem „Chybějící font.docx“ z našeho `dataDir`.

## Krok 3: Konfigurace možností ukládání HTML

Nyní nastavme možnosti pro uložení dokumentu ve formátu HTML. Zde zajistíme, aby názvy písem byly správně rozpoznány.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Html)
{
    PrettyFormat = true,
    ResolveFontNames = true
};
```

Vysvětlení:
Vytvoříme instanci `HtmlSaveOptions` s `SaveFormat.Html`Ten/Ta/To `PrettyFormat` možnost usnadňuje čitelnost HTML výstupu a `ResolveFontNames` zajišťuje, že názvy písem jsou rozlišeny.

## Krok 4: Uložení dokumentu jako HTML

Nakonec uložíme dokument jako HTML soubor s použitím nakonfigurovaných možností ukládání.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ResolveFontNames.html", saveOptions);
```

Vysvětlení:
Říkáme tomu `Save` metoda na `Document` objekt s určením výstupní cesty a nakonfigurovaných možností ukládání. Tím se vygeneruje soubor HTML s rozlišenými názvy písem.

## Závěr

A tady to máte! Dodržováním těchto kroků jste úspěšně rozpoznali názvy písem při převodu dokumentu Word do HTML pomocí Aspose.Words pro .NET. Tím se nejen zajistí správné zobrazení písem, ale také se váš HTML výstup bude zdát uhlazený a profesionální. Přeji vám hodně štěstí při programování!

## Často kladené otázky

### Co je Aspose.Words pro .NET?
Aspose.Words pro .NET je výkonná knihovna, která umožňuje vývojářům programově vytvářet, upravovat a převádět dokumenty Wordu.

### Jak nainstaluji Aspose.Words pro .NET?
Aspose.Words pro .NET si můžete stáhnout z [zde](https://releases.aspose.com/words/net/)Řiďte se pokyny k instalaci uvedenými v dokumentaci.

### Mohu používat Aspose.Words pro .NET bez licence?
Ano, ale bude to mít určitá omezení. Pro plnou funkčnost si můžete zakoupit licenci. [zde](https://purchase.aspose.com/buy) nebo si pořídit dočasný řidičský průkaz [zde](https://purchase.aspose.com/temporary-license/).

### Proč se mi písma v HTML nezobrazují správně?
tomu může dojít, pokud písma nejsou během převodu správně rozlišena. Použití `ResolveFontNames = true` v `HtmlSaveOptions` může pomoci tento problém vyřešit.

### Kde mohu získat podporu pro Aspose.Words pro .NET?
Podporu můžete získat od [Fórum podpory Aspose.Words](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}