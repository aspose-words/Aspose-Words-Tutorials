---
"description": "Naučte se, jak nastavit směr textu v dokumentu ve Wordu pomocí Aspose.Words pro .NET v tomto podrobném návodu. Ideální pro práci s jazyky psanými zprava doleva."
"linktitle": "Směr textu dokumentu"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Směr textu dokumentu"
"url": "/cs/net/programming-with-txtloadoptions/document-text-direction/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Směr textu dokumentu

## Zavedení

Při práci s dokumenty aplikace Word, zejména s těmi, které obsahují více jazyků nebo vyžadují speciální formátování, může být nastavení směru textu klíčové. Například při práci s jazyky psanými zprava doleva, jako je hebrejština nebo arabština, může být nutné směr textu odpovídajícím způsobem upravit. V této příručce si ukážeme, jak nastavit směr textu v dokumentu pomocí nástroje Aspose.Words pro .NET. 

## Předpoklady

Než se pustíme do kódu, ujistěte se, že máte následující:

- Knihovna Aspose.Words pro .NET: Ujistěte se, že máte nainstalovanou knihovnu Aspose.Words pro .NET. Můžete si ji stáhnout z [Webové stránky Aspose](https://releases.aspose.com/words/net/).
- Visual Studio: Vývojové prostředí pro psaní a spouštění kódu v jazyce C#.
- Základní znalost C#: Znalost programování v C# bude přínosem, protože budeme psát nějaký kód.

## Importovat jmenné prostory

Pro začátek budete muset importovat potřebné jmenné prostory pro práci s Aspose.Words ve vašem projektu. Zde je návod, jak to udělat:

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
```

Tyto jmenné prostory poskytují přístup ke třídám a metodám potřebným k manipulaci s dokumenty aplikace Word.

## Krok 1: Definujte cestu k adresáři dokumentů

Nejprve nastavte cestu k umístění vašeho dokumentu. To je klíčové pro správné načítání a ukládání souborů.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Nahradit `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou, kde je váš dokument uložen.

## Krok 2: Vytvořte TxtLoadOptions s nastavením směru dokumentu

Dále budete muset vytvořit instanci `TxtLoadOptions` a nastavit jeho `DocumentDirection` vlastnost. Toto říká Aspose.Words, jak má v dokumentu zpracovat směr textu.

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DocumentDirection = DocumentDirection.Auto };
```

V tomto příkladu používáme `DocumentDirection.Auto` nechat Aspose.Words automaticky určit směr na základě obsahu.

## Krok 3: Vložení dokumentu

Nyní načtěte dokument pomocí `Document` třída a dříve definovaná `loadOptions`.

```csharp
Document doc = new Document(dataDir + "Hebrew text.txt", loadOptions);
```

Zde, `"Hebrew text.txt"` je název vašeho textového souboru. Ujistěte se, že tento soubor existuje ve vámi zadaném adresáři.

## Krok 4: Zpřístupnění a kontrola obousměrného formátování odstavce

Chcete-li ověřit, zda je směr textu správně nastaven, přejděte k prvnímu odstavci dokumentu a zkontrolujte jeho obousměrné formátování.

```csharp
Paragraph paragraph = doc.FirstSection.Body.FirstParagraph;
Console.WriteLine(paragraph.ParagraphFormat.Bidi);
```

Tento krok je užitečný pro ladění a ověření, zda byl směr textu v dokumentu použit podle očekávání.

## Krok 5: Uložte dokument s novým nastavením

Nakonec dokument uložte, aby se změny projevily a zachovaly.

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
```

Zde, `"WorkingWithTxtLoadOptions.DocumentTextDirection.docx"` je název výstupního souboru. Ujistěte se, že zvolíte název, který odráží provedené změny.

## Závěr

Nastavení směru textu v dokumentech Wordu je s Aspose.Words pro .NET jednoduchý proces. Dodržováním těchto kroků můžete snadno nakonfigurovat, jak dokument zpracovává text zprava doleva nebo zleva doprava. Ať už pracujete s vícejazyčnými dokumenty nebo potřebujete formátovat směr textu pro konkrétní jazyky, Aspose.Words poskytuje robustní řešení, které splní vaše potřeby.

## Často kladené otázky

### Co je `DocumentDirection` k čemu je nemovitost používána?

Ten/Ta/To `DocumentDirection` nemovitost v `TxtLoadOptions` určuje směr textu v dokumentu. Lze jej nastavit na `DocumentDirection.Auto`, `DocumentDirection.LeftToRight`nebo `DocumentDirection.RightToLeft`.

### Mohu nastavit směr textu pro konkrétní odstavce místo pro celý dokument?

Ano, směr textu pro konkrétní odstavce můžete nastavit pomocí `ParagraphFormat.Bidi` majetek, ale `TxtLoadOptions.DocumentDirection` vlastnost nastavuje výchozí směr pro celý dokument.

### Jaké formáty souborů jsou podporovány pro načítání pomocí `TxtLoadOptions`?

`TxtLoadOptions` používá se primárně pro načítání textových souborů (.txt). Pro jiné formáty souborů použijte jiné třídy, jako například `DocLoadOptions` nebo `DocxLoadOptions`.

### Jak mohu zpracovat dokumenty se smíšenými textovými pokyny?

U dokumentů se smíšenými textovými pokyny může být nutné formátování upravovat pro každý odstavec. Použijte `ParagraphFormat.Bidi` vlastnost pro úpravu směru každého odstavce dle potřeby.

### Kde najdu více informací o Aspose.Words pro .NET?

Pro více informací se podívejte na [Dokumentace k Aspose.Words pro .NET](https://reference.aspose.com/words/net/)Můžete si také prohlédnout další zdroje, jako například [Odkaz ke stažení](https://releases.aspose.com/words/net/), [Nakoupit](https://purchase.aspose.com/buy), [Bezplatná zkušební verze](https://releases.aspose.com/), [Dočasná licence](https://purchase.aspose.com/temporary-license/)a [Podpora](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}