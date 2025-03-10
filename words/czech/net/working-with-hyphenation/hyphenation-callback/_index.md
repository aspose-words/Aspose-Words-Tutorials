---
title: Zpětné volání dělení slov
linktitle: Zpětné volání dělení slov
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se implementovat zpětné volání dělení slov v Aspose.Words pro .NET a vylepšit formátování dokumentu pomocí tohoto komplexního podrobného průvodce.
weight: 10
url: /cs/net/working-with-hyphenation/hyphenation-callback/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zpětné volání dělení slov


## Zavedení

Ahoj! Zapletli jste se někdy do složitosti formátování textu, zejména při práci s jazyky, které vyžadují dělení slov? Nejsi sám. Dělení slov, i když je klíčové pro správné rozvržení textu, může být trochu bolehlav. Ale hádejte co? Aspose.Words for .NET vám drží záda. Tato výkonná knihovna umožňuje bezproblémovou správu formátování textu, včetně zpracování dělení slov pomocí mechanismu zpětného volání. Zaujalo? Pojďme se ponořit do toho, jak můžete implementovat zpětné volání dělení slov pomocí Aspose.Words pro .NET.

## Předpoklady

Než si ušpiníme ruce kódem, ujistěte se, že máte vše, co potřebujete:

1. Aspose.Words for .NET: Ujistěte se, že máte knihovnu. Můžete[stáhněte si to zde](https://releases.aspose.com/words/net/).
2. IDE: Vývojové prostředí jako Visual Studio.
3. Základní znalost C#: Pochopení C# a .NET frameworku.
4. Slovníky dělení slov: Slovníky dělení slov pro jazyky, které plánujete používat.
5.  Licence Aspose: Platná licence Aspose. Můžete získat a[dočasná licence](https://purchase.aspose.com/temporary-license/) pokud žádný nemáte.

## Importovat jmenné prostory

Nejprve importujme potřebné jmenné prostory. To zajišťuje, že náš kód má přístup ke všem třídám a metodám, které potřebujeme z Aspose.Words.

```csharp
using Aspose.Words;
using System;
using System.IO;
```

## Krok 1: Zaregistrujte zpětné volání dělení slov

Chcete-li začít, musíme zaregistrovat naše zpětné volání dělení slov. Zde říkáme Aspose.Words, aby použil naši vlastní logiku dělení slov.

```csharp
try
{
    // Zaregistrujte zpětné volání dělení slov.
    Hyphenation.Callback = new CustomHyphenationCallback();
}
catch (Exception e)
{
    Console.WriteLine($"Error registering hyphenation callback: {e.Message}");
}
```

 Zde vytváříme instanci našeho vlastního zpětného volání a přiřazujeme ji`Hyphenation.Callback`.

## Krok 2: Definujte cestu dokumentu

Dále musíme definovat adresář, kde jsou uloženy naše dokumenty. To je zásadní, protože budeme načítat a ukládat dokumenty z této cesty.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Nahradit`"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou k vašim dokumentům.

## Krok 3: Vložte dokument

Nyní načteme dokument, který vyžaduje dělení slov.

```csharp
Document document = new Document(dataDir + "German text.docx");
```

Zde načítáme německý textový dokument. Můžete vyměnit`"German text.docx"` s názvem souboru vašeho dokumentu.

## Krok 4: Uložte dokument

Po načtení dokumentu jej uložíme do nového souboru, přičemž v procesu použijeme zpětné volání dělení slov.

```csharp
document.Save(dataDir + "TreatmentByCesureWithRecall.pdf");
```

Tento řádek uloží dokument jako PDF s použitým dělením slov.

## Krok 5: Ošetřete chybějící výjimku slovníku dělení slov

Někdy můžete narazit na problém, kdy chybí slovník dělení slov. Pojďme to zvládnout.

```csharp
catch (Exception e) when (e.Message.StartsWith("Missing hyphenation dictionary"))
{
    Console.WriteLine(e.Message);
}
finally
{
    Hyphenation.Callback = null;
}
```

V tomto bloku zachytíme konkrétní výjimku související s chybějícími slovníky a zprávu vytiskneme.

## Krok 6: Implementujte vlastní třídu zpětného volání dělení slov

 Nyní implementujme`CustomHyphenationCallback` třída, která zpracovává požadavek na slovníky dělení slov.

```csharp
public class CustomHyphenationCallback : IHyphenationCallback
{
    public void RequestDictionary(string language)
    {
        string dictionaryFolder = MyDir;
        string dictionaryFullFileName;
        switch (language)
        {
            case "en-US":
                dictionaryFullFileName = Path.Combine(dictionaryFolder, "hyph_en_US.dic");
                break;
            case "de-CH":
                dictionaryFullFileName = Path.Combine(dictionaryFolder, "hyph_de_CH.dic");
                break;
            default:
                throw new Exception($"Missing hyphenation dictionary for {language}.");
        }
        // Zaregistrujte slovník pro požadovaný jazyk.
        Hyphenation.RegisterDictionary(language, dictionaryFullFileName);
    }
}
```

 V této třídě je`RequestDictionary` metoda se volá vždy, když je potřeba slovník dělení slov. Zkontroluje jazyk a zaregistruje příslušný slovník.

## Závěr

tady to máte! Právě jste se naučili, jak implementovat zpětné volání dělení slov v Aspose.Words pro .NET. Pomocí těchto kroků můžete zajistit, že vaše dokumenty budou krásně naformátované bez ohledu na jazyk. Ať už máte co do činění s angličtinou, němčinou nebo jakýmkoli jiným jazykem, tato metoda vám umožní zvládnout dělení slov bez námahy.

## FAQ

### Co je Aspose.Words for .NET?
Aspose.Words for .NET je výkonná knihovna pro manipulaci s dokumenty, která umožňuje vývojářům vytvářet, upravovat a převádět dokumenty programově.

### Proč je dělení slov důležité při formátování dokumentu?
Dělení slov zlepšuje rozvržení textu rozdělením slov na vhodná místa, což zajišťuje čitelnější a vizuálně přitažlivější dokument.

### Mohu používat Aspose.Words zdarma?
 Aspose.Words nabízí bezplatnou zkušební verzi. Můžete to získat[zde](https://releases.aspose.com/).

### Jak získám slovník dělení slov?
Slovníky dělení slov si můžete stáhnout z různých online zdrojů nebo si v případě potřeby vytvořit vlastní.

### Co se stane, když chybí slovník dělení slov?
 Pokud slovník chybí,`RequestDictionary`metoda vyvolá výjimku, kterou můžete zpracovat za účelem informování uživatele nebo poskytnutí nouzového řešení.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
