---
title: Směr textu dokumentu
linktitle: Směr textu dokumentu
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak nastavit směr textu dokumentu ve Wordu pomocí Aspose.Words for .NET, pomocí tohoto podrobného průvodce. Perfektní pro práci s jazyky psanými zprava doleva.
weight: 10
url: /cs/net/programming-with-txtloadoptions/document-text-direction/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Směr textu dokumentu

## Zavedení

Při práci s dokumenty aplikace Word, zejména s těmi, které obsahují více jazyků nebo speciální potřeby formátování, může být rozhodující nastavení směru textu. Například při práci s jazyky se zápisem zprava doleva, jako je hebrejština nebo arabština, možná budete muset odpovídajícím způsobem upravit směr textu. V této příručce si projdeme, jak nastavit směr textu dokumentu pomocí Aspose.Words pro .NET. 

## Předpoklady

Než se ponoříme do kódu, ujistěte se, že máte následující:

-  Aspose.Words for .NET Library: Ujistěte se, že máte nainstalovanou Aspose.Words for .NET. Můžete si jej stáhnout z[Aspose webové stránky](https://releases.aspose.com/words/net/).
- Visual Studio: Vývojové prostředí pro psaní a spouštění kódu C#.
- Základní znalost C#: Znalost programování v C# bude prospěšná, protože budeme psát nějaký kód.

## Importovat jmenné prostory

Chcete-li začít, budete muset importovat potřebné jmenné prostory pro práci s Aspose.Words ve vašem projektu. Můžete to udělat takto:

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
```

Tyto jmenné prostory poskytují přístup ke třídám a metodám potřebným pro manipulaci s dokumenty aplikace Word.

## Krok 1: Definujte cestu k adresáři vašeho dokumentu

Nejprve nastavte cestu k umístění dokumentu. To je klíčové pro správné načítání a ukládání souborů.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Nahradit`"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou, kde je dokument uložen.

## Krok 2: Vytvořte možnosti TxtLoadOptions s nastavením směru dokumentu

 Dále budete muset vytvořit instanci`TxtLoadOptions` a nastavte jej`DocumentDirection` vlastnictví. To říká Aspose.Words, jak zacházet se směrem textu v dokumentu.

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DocumentDirection = DocumentDirection.Auto };
```

 V tomto příkladu používáme`DocumentDirection.Auto` nechat Aspose.Words automaticky určit směr na základě obsahu.

## Krok 3: Vložte dokument

 Nyní načtěte dokument pomocí`Document` třídy a dříve definované`loadOptions`.

```csharp
Document doc = new Document(dataDir + "Hebrew text.txt", loadOptions);
```

 Zde,`"Hebrew text.txt"` je název vašeho textového souboru. Ujistěte se, že tento soubor existuje ve vašem zadaném adresáři.

## Krok 4: Otevřete a zkontrolujte obousměrné formátování odstavce

Chcete-li si ověřit, zda je směr textu správně nastaven, přejděte k prvnímu odstavci dokumentu a zkontrolujte jeho obousměrné formátování.

```csharp
Paragraph paragraph = doc.FirstSection.Body.FirstParagraph;
Console.WriteLine(paragraph.ParagraphFormat.Bidi);
```

Tento krok je užitečný pro ladění a ověření, že směr textu dokumentu byl použit podle očekávání.

## Krok 5: Uložte dokument s novým nastavením

Nakonec dokument uložte, abyste změny použili a zachovali.

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
```

 Zde,`"WorkingWithTxtLoadOptions.DocumentTextDirection.docx"` je název výstupního souboru. Ujistěte se, že jste vybrali název, který odráží změny, které jste provedli.

## Závěr

Nastavení směru textu v dokumentech aplikace Word je s Aspose.Words pro .NET jednoduchý proces. Pomocí těchto kroků můžete snadno nakonfigurovat, jak váš dokument zpracovává text zprava doleva nebo zleva doprava. Ať už pracujete s vícejazyčnými dokumenty nebo potřebujete formátovat směr textu pro konkrétní jazyky, Aspose.Words poskytuje robustní řešení, které splní vaše potřeby.

## FAQ

###  Co je`DocumentDirection` property used for?

 The`DocumentDirection` majetek v`TxtLoadOptions` určuje směr textu dokumentu. Dá se nastavit na`DocumentDirection.Auto`, `DocumentDirection.LeftToRight` nebo`DocumentDirection.RightToLeft`.

### Mohu nastavit směr textu pro konkrétní odstavce místo celého dokumentu?

 Ano, směr textu pro konkrétní odstavce můžete nastavit pomocí`ParagraphFormat.Bidi` majetek, ale`TxtLoadOptions.DocumentDirection` vlastnost nastavuje výchozí směr pro celý dokument.

###  Jaké formáty souborů jsou podporovány pro načítání`TxtLoadOptions`?

`TxtLoadOptions` se používá především pro načítání textových souborů (.txt). Pro jiné formáty souborů použijte různé třídy jako`DocLoadOptions` nebo`DocxLoadOptions`.

### Jak mohu pracovat s dokumenty se smíšenými směry textu?

 U dokumentů se smíšenými směry textu budete možná muset zpracovat formátování podle odstavce. Použijte`ParagraphFormat.Bidi` vlastnost upravit směr každého odstavce podle potřeby.

### Kde najdu další informace o Aspose.Words pro .NET?

 Pro více podrobností se podívejte na[Aspose.Words pro .NET dokumentaci](https://reference.aspose.com/words/net/) . Můžete také prozkoumat další zdroje, např[Odkaz ke stažení](https://releases.aspose.com/words/net/), [Nakoupit](https://purchase.aspose.com/buy), [Bezplatná zkušební verze](https://releases.aspose.com/), [Dočasná licence](https://purchase.aspose.com/temporary-license/) a[Podpora](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
