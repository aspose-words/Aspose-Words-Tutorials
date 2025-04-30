---
"description": "Naučte se implementovat zpětné volání dělení slov v Aspose.Words pro .NET pro vylepšení formátování dokumentů s tímto komplexním podrobným návodem."
"linktitle": "Zpětné volání dělení slov"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Zpětné volání dělení slov"
"url": "/cs/net/working-with-hyphenation/hyphenation-callback/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Zpětné volání dělení slov


## Zavedení

Ahoj! Už jste se někdy ocitli v složitosti formátování textu, zejména při práci s jazyky, které vyžadují dělení slov? Nejste sami. Dělení slov, ačkoli je klíčové pro správné rozvržení textu, může být trochu otravné. Ale víte co? Aspose.Words pro .NET vám pomůže. Tato výkonná knihovna vám umožňuje bezproblémově spravovat formátování textu, včetně práce s dělením slov pomocí mechanismu zpětného volání. Zaujalo vás to? Pojďme se ponořit do detailů, jak implementovat zpětné volání dělení slov pomocí Aspose.Words pro .NET.

## Předpoklady

Než se pustíme do kódování, ujistěme se, že máte vše potřebné:

1. Aspose.Words pro .NET: Ujistěte se, že máte knihovnu. Můžete [stáhněte si to zde](https://releases.aspose.com/words/net/).
2. IDE: Vývojové prostředí, jako je Visual Studio.
3. Základní znalost C#: Znalost C# a .NET frameworku.
4. Slovníky pro dělení slov: Slovníky pro dělení slov pro jazyky, které plánujete používat.
5. Licence Aspose: Platná licence Aspose. Můžete získat [dočasná licence](https://purchase.aspose.com/temporary-license/) pokud ho nemáte.

## Importovat jmenné prostory

Nejdříve si importujme potřebné jmenné prostory. Tím zajistíme, že náš kód bude mít přístup ke všem třídám a metodám z Aspose.Words, které potřebujeme.

```csharp
using Aspose.Words;
using System;
using System.IO;
```

## Krok 1: Registrace zpětného volání dělení slov

Pro začátek musíme zaregistrovat naši zpětnou funkci pro dělení slov. Zde sdělíme Aspose.Words, aby použila naši vlastní logiku pro dělení slov.

```csharp
try
{
    // Registrace zpětného volání pro dělení slov.
    Hyphenation.Callback = new CustomHyphenationCallback();
}
catch (Exception e)
{
    Console.WriteLine($"Error registering hyphenation callback: {e.Message}");
}
```

Zde vytváříme instanci našeho vlastního zpětného volání a přiřazujeme ji k `Hyphenation.Callback`.

## Krok 2: Definování cesty k dokumentu

Dále musíme definovat adresář, kde jsou uloženy naše dokumenty. To je klíčové, protože budeme načítat a ukládat dokumenty z této cesty.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Nahradit `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou k vašim dokumentům.

## Krok 3: Vložení dokumentu

Nyní načtěme dokument, který vyžaduje rozdělení slov.

```csharp
Document document = new Document(dataDir + "German text.docx");
```

Zde načítáme německý textový dokument. Můžete nahradit `"German text.docx"` názvem souboru vašeho dokumentu.

## Krok 4: Uložte dokument

Po načtení dokumentu jej uložíme do nového souboru a v tomto procesu použijeme zpětné volání pro dělení slov.

```csharp
document.Save(dataDir + "TreatmentByCesureWithRecall.pdf");
```

Tento řádek uloží dokument jako PDF s použitým dělením slov.

## Krok 5: Ošetření výjimky chybějícího slovníku dělení slov

Někdy se můžete setkat s problémem, kdy chybí slovník pro pomlčky. Pojďme se s tím vypořádat.

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

V tomto bloku zachytíme specifickou výjimku týkající se chybějících slovníků a vypíšeme zprávu.

## Krok 6: Implementace vlastní třídy zpětného volání pro dělení slov

Nyní implementujme `CustomHyphenationCallback` třída, která zpracovává požadavky na slovníky pro dělení slov.

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
        // Zaregistrovat slovník pro požadovaný jazyk.
        Hyphenation.RegisterDictionary(language, dictionaryFullFileName);
    }
}
```

V této třídě, `RequestDictionary` Metoda se volá vždy, když je potřeba slovník pro pomlčky. Zkontroluje jazyk a zaregistruje příslušný slovník.

## Závěr

tady to máte! Právě jste se naučili, jak implementovat zpětné volání pro dělení slov v Aspose.Words pro .NET. Dodržováním těchto kroků zajistíte, že vaše dokumenty budou krásně formátovány bez ohledu na jazyk. Ať už pracujete s angličtinou, němčinou nebo jakýmkoli jiným jazykem, tato metoda vám umožní snadno zvládnout dělení slov.

## Často kladené otázky

### Co je Aspose.Words pro .NET?
Aspose.Words pro .NET je výkonná knihovna pro manipulaci s dokumenty, která umožňuje vývojářům programově vytvářet, upravovat a převádět dokumenty.

### Proč je dělení slov důležité při formátování dokumentu?
Dělení slov zlepšuje rozvržení textu tím, že rozděluje slova na správná místa, čímž zajišťuje čitelnější a vizuálně atraktivnější dokument.

### Mohu používat Aspose.Words zdarma?
Aspose.Words nabízí bezplatnou zkušební verzi. Můžete si ji stáhnout [zde](https://releases.aspose.com/).

### Jak získám slovník pro pomlčky?
Slovníky pro pomlčky si můžete stáhnout z různých online zdrojů nebo si v případě potřeby vytvořit vlastní.

### Co se stane, když chybí slovník pro dělení slov?
Pokud slovník chybí, `RequestDictionary` Metoda vyvolá výjimku, kterou můžete zpracovat, abyste informovali uživatele nebo poskytli záložní řešení.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}