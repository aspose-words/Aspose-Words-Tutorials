---
category: general
date: 2026-08-04
description: Změna oddělovače poznámky pod čarou v C# pomocí Aspose.Words – naučte
  se, jak upravit oddělovač poznámky pod čarou a změnit oddělovač koncové poznámky
  v dokumentech Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote separator
- edit footnote separator
- how to change footnote separator
- change endnote separator
language: cs
lastmod: 2026-08-04
og_description: Změňte oddělovač poznámky pod čarou v C# pomocí Aspose.Words. Tento
  průvodce vám ukáže, jak upravit oddělovač poznámky pod čarou, přizpůsobit oddělovač
  koncové poznámky a uložit aktualizovaný dokument.
og_image_alt: Screenshot showing the changed footnote separator in a Word document
og_title: Změna oddělovače poznámky pod čarou v C# – kompletní průvodce Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Change footnote separator in C# using Aspose.Words – learn how to edit
    footnote separator and change endnote separator in Word documents.
  headline: Change footnote separator in C# using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
- Document processing
title: Změna oddělovače poznámky pod čarou v C# pomocí Aspose.Words
url: /cs/net/working-with-footnote-and-endnote/change-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Změna oddělovače poznámky pod čarou v C# pomocí Aspose.Words

Pokud potřebujete **change footnote separator** v dokumentu Word, tento tutoriál vás provede přesné kroky s Aspose.Words pro .NET. Ať už chcete nahradit výchozí čáru symbolem, nebo použít jiný styl pro oddělovače koncových poznámek, níže uvedený kód pokrývá celý postup.

Také se naučíte, jak **edit footnote separator** a související operaci **change endnote separator**, takže stejný dokument může mít konzistentní styl jak pro poznámky pod čarou, tak pro koncové poznámky. Žádné externí nástroje nejsou potřeba – stačí jen několik řádků C#.

## Co dosáhnete

* Načíst existující soubor *.docx*, který obsahuje poznámky pod čarou a koncové poznámky.  
* Získat přístup k uzlům oddělovačů pro poznámky pod čarou, pokračování poznámek pod čarou a koncové poznámky.  
* Nahradit znak oddělovače (například změnit výchozí čáru na hvězdičku).  
* Uložit upravený dokument bez ztráty jakéhokoli dalšího obsahu.  

Tutoriál předpokládá, že máte základní znalosti C# a nainstalovali jste balíček NuGet **Aspose.Words** (verze 24.9 nebo novější).

---

## Požadavky

| Požadavek | Důvod |
|-------------|--------|
| .NET 6.0+ or .NET Framework 4.7.2+ | Požadované runtime pro Aspose.Words |
| Aspose.Words for .NET library | Poskytuje API `Document` a `FootnoteOptions` |
| An input Word file (`input.docx`) with at least one footnote or endnote | Ukazuje změnu oddělovače |

Do svého projektu můžete přidat Aspose.Words pomocí následujícího příkazu CLI:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

## Krok 1: Načtení dokumentu obsahujícího poznámky pod čarou

Prvním krokem je načíst zdrojový soubor do objektu `Document`. Tento objekt představuje celý soubor Word v paměti a poskytuje vám přístup ke všem jeho uzlům.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Load the .docx file that contains footnotes and endnotes.
Document document = new Document(@"C:\Docs\input.docx");
```

**Proč je to důležité:**  
Načtení dokumentu je vstupním bodem pro jakoukoli manipulaci. Pokud soubor nelze najít, Aspose.Words vyhodí výjimku `FileNotFoundException`, takže před pokračováním se ujistěte, že cesta je správná.

## Krok 2: Přístup k uzlům oddělovačů poznámek pod čarou a koncových poznámek

`Document.FootnoteOptions` poskytuje tři uzly oddělovačů:

* `Separator` – čára, která se objeví po sbírce poznámek pod čarou na první stránce.  
* `ContinuationSeparator` – čára používaná, když se poznámky pod čarou pokračují na další stránku.  
* `EndnoteSeparator` – čára, která odděluje hlavní text od seznamu koncových poznámek.  

Tyto uzly získáte jako obecné objekty `Node` a poté je přetypujete na `Run`, abyste mohli upravit text.

```csharp
// Retrieve the three separator nodes.
Node footnoteSeparator = document.FootnoteOptions.Separator;
Node footnoteContinuation = document.FootnoteOptions.ContinuationSeparator;
Node endnoteSeparator = document.FootnoteOptions.EndnoteSeparator;
```

**Proč je to důležité:**  
Tyto uzly jsou jedinými místy, kde se nachází vizuální znak oddělovače. Změna jakéhokoli jiného uzlu (např. běžného odstavce) neovlivní formátování poznámek pod čarou.

## Krok 3: Změna znaku oddělovače poznámky pod čarou

Nejčastější požadavek je nahradit výchozí čáru symbolem, například hvězdičkou (`*`). Protože je oddělovač uložen jako `Run`, můžete bezpečně upravit jeho vlastnost `Text`.

```csharp
// Change the primary footnote separator to an asterisk.
if (footnoteSeparator is Run footnoteRun)
{
    footnoteRun.Text = "*";
}

// Optionally, change the continuation separator as well.
if (footnoteContinuation is Run continuationRun)
{
    continuationRun.Text = "*";
}
```

**Proč je to důležité:**  
Přímá úprava `Run.Text` aktualizuje vizuální reprezentaci v konečném dokumentu, aniž by ovlivnila ostatní obsah poznámek pod čarou. Stejný vzor lze použít k aplikaci libovolného řetězce, včetně Unicode symbolů.

## Krok 4: Změna oddělovače koncové poznámky (volitelné)

Pokud také potřebujete **change endnote separator**, proces je stejný jako u změny poznámky pod čarou. Nahraďte text `endnoteSeparator` požadovaným znakem.

```csharp
// Change the endnote separator to a dash.
if (endnoteSeparator is Run endnoteRun)
{
    endnoteRun.Text = "-";
}
```

**Proč je to důležité:**  
Koncové poznámky jsou často stylizovány odlišně od poznámek pod čarou. Poskytnutí samostatného oddělovače vám umožní zachovat vizuální konzistenci s designovými směrnicemi vašeho dokumentu.

## Krok 5: Uložení upraveného dokumentu

Po všech úpravách uložte změny pomocí `Document.Save`. Můžete přepsat původní soubor nebo zapsat do nového umístění.

```csharp
// Save the updated document.
document.Save(@"C:\Docs\ModifiedSeparators.docx");
```

**Proč je to důležité:**  
`Save` zapíše reprezentaci v paměti na disk a zachová všechny ostatní prvky (styly, obrázky, tabulky) beze změny.

## Kompletní, spustitelný příklad

Spojením všech částí dohromady získáte samostatnou konzolovou aplikaci, která demonstruje celý postup:

```csharp
using System;
using Aspose.Words;

namespace FootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source document.
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Access separator nodes.
            Node footnoteSep = doc.FootnoteOptions.Separator;
            Node footnoteCont = doc.FootnoteOptions.ContinuationSeparator;
            Node endnoteSep = doc.FootnoteOptions.EndnoteSeparator;

            // 3️⃣ Change footnote separator to an asterisk.
            if (footnoteSep is Run footnoteRun)
                footnoteRun.Text = "*";

            // Optional: also change the continuation separator.
            if (footnoteCont is Run contRun)
                contRun.Text = "*";

            // 4️⃣ Change endnote separator to a dash.
            if (endnoteSep is Run endnoteRun)
                endnoteRun.Text = "-";

            // 5️⃣ Save the result.
            string outputPath = @"C:\Docs\ModifiedSeparators.docx";
            doc.Save(outputPath);

            Console.WriteLine("Document saved to " + outputPath);
        }
    }
}
```

**Očekávaný výsledek:**  
Otevřete *ModifiedSeparators.docx* v Microsoft Word. Čára oddělovače poznámky pod čarou na konci první stránky s poznámkami pod čarou bude nyní jediná hvězdička (`*`). Pokud dokument obsahuje koncové poznámky, čára oddělující hlavní text od seznamu koncových poznámek se zobrazí jako pomlčka (`-`). Veškerý ostatní obsah (text, obrázky, tabulky) zůstane nedotčen.

## Časté otázky a řešení okrajových případů

| Otázka | Odpověď |
|----------|--------|
| **Co když dokument nemá žádné poznámky pod čarou?** | `FootnoteOptions.Separator` stále vrací uzel `Run`, ale jeho text může být prázdný. Kód bezpečně kontroluje typ uzlu před úpravou. |
| **Mohu použít řetězec s více znaky (např. "***")?** | Ano. Vlastnost `Run.Text` přijímá libovolný řetězec, včetně Unicode znaků. |
| **Ovlivní změna oddělovače existující číslování poznámek pod čarou?** | Ne. Oddělovač je nezávislý na schématu číslování. |
| **Musím uvolnit objekt `Document`?** | `Document` implementuje `IDisposable` implicitně přes `Node`. V krátkodobé konzolové aplikaci je to volitelné, ale pro dlouho běžící služby jej můžete zabalit do bloku `using`. |
| **Jak to funguje s .NET Core vs .NET Framework?** | API je napříč runtime identické; záleží jen na verzi cílového frameworku (musí být podporována balíčkem Aspose.Words). |

**Tip:** Pokud potřebujete použít různé oddělovače pro různé sekce, můžete iterovat přes `doc.GetChildNodes(NodeType.Footnote, true)` a individuálně upravit vlastnost `Separator` každé poznámky pod čarou. Toto je pokročilejší, ale užitečné pro složité dokumenty.

## Závěr

Nyní víte, jak **change footnote separator** a **change endnote separator** v souboru Word pomocí Aspose.Words pro C#. Průvodce pokryl načtení dokumentu, přístup k příslušným uzlům oddělovačů, úpravu jejich textu a uložení výsledku – vše v jedné samostatné aplikaci.

Odtud můžete zkoumat související témata, jako je **edit footnote separator style**, přizpůsobení číslování poznámek pod čarou nebo aplikace podmíněného formátování na základě rozvržení stránky. Stejný vzor (získat uzel, přetypovat na `Run`, upravit `Text`) funguje pro mnoho dalších scénářů zpracování Wordu.

Šťastné programování a neváhejte experimentovat s různými symboly nebo dokonce vložit obrázky jako oddělovače pro opravdu jedinečné rozvržení dokumentu!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Zpracování slov s poznámkami pod čarou a koncovými poznámkami](/words/english/net/working-with-footnote-and-endnote/)
- [Získání oddělovače stylu odstavce v dokumentu Word](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Vložení oddělovače stylu dokumentu ve Wordu](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}