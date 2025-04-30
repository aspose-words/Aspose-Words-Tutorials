---
"description": "Naučte se, jak získat typy revizí slov v dokumentu Word pomocí Aspose.Words pro .NET. Tato podrobná příručka vám pomůže efektivně zvládat revize dokumentů."
"linktitle": "Získejte revizní typy slov"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Získejte revizní typy slov"
"url": "/cs/net/working-with-revisions/get-revision-types/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Získejte revizní typy slov

## Zavedení

Už jste se někdy ocitli po kolena v moři revizí dokumentů a přemýšleli, kdo co a kdy přesunul? Nejste sami. Zpracování revizí dokumentů může být zdlouhavý úkol, zejména při práci s rozsáhlými dokumenty. Ale nebojte se! S Aspose.Words pro .NET můžete tyto revize snadno identifikovat a spravovat. V této příručce vás krok za krokem provedeme procesem, jak získat typy revizí slov v dokumentu Word pomocí Aspose.Words pro .NET. Takže se připoutejte a pojďme se do toho pustit!

## Předpoklady

Než se pustíme do kódování, je tu pár věcí, které budete potřebovat:

1. Knihovna Aspose.Words pro .NET: Pokud jste tak ještě neučinili, stáhněte si ji z [zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Visual Studio nebo jakékoli jiné IDE kompatibilní s .NET.
3. Základní znalost C#: Znalost programovacího jazyka C# bude výhodou.
4. Dokument Word s revizemi: Ujistěte se, že máte `.docx` soubor se sledovanými změnami pro otestování kódu.

## Importovat jmenné prostory

Pro začátek budete muset do svého projektu v C# importovat potřebné jmenné prostory. To vám umožní přístup k funkcím poskytovaným Aspose.Words pro .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Revision;
using System;
```

Pro lepší pochopení a implementaci si příklad rozdělme do několika kroků.

## Krok 1: Nastavení adresáře dokumentů

Nejprve je třeba definovat cestu k adresáři s dokumenty. Zde bude umístěn váš dokument Wordu s revizemi.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Nahradit `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou ke složce s dokumenty.

## Krok 2: Načtěte dokument aplikace Word

Dále je třeba načíst dokument aplikace Word do projektu. Tento dokument by měl obsahovat revize, které chcete analyzovat.

```csharp
Document doc = new Document(dataDir + "Revisions.docx");
```

Ujistěte se, že soubor `Revisions.docx` existuje v zadaném adresáři.

## Krok 3: Přístup ke kolekci odstavců

Nyní, když je váš dokument načten, potřebujete přistupovat k odstavcům v první části těla dokumentu. To vám pomůže procházet každý odstavec a kontrolovat revize.

```csharp
ParagraphCollection paragraphs = doc.FirstSection.Body.Paragraphs;
```

## Krok 4: Procházení odstavců a kontrola revizí

A tady se začne dít ta pravá magie. Projdete každý odstavec a zkontrolujete, zda byl přesunut (smazán nebo vložen).

```csharp
for (int i = 0; i < paragraphs.Count; i++)
{
    if (paragraphs[i].IsMoveFromRevision)
        Console.WriteLine("Paragraph {0} has been moved (deleted).", i);
    if (paragraphs[i].IsMoveToRevision)
        Console.WriteLine("Paragraph {0} has been moved (inserted).", i);
}
```

Tato smyčka prochází každým odstavcem a používá `IsMoveFromRevision` a `IsMoveToRevision` vlastnosti, které určují, zda byl odstavec přesunut (smazán) nebo přesunut (vložen).

## Závěr

A máte to! Pomocí knihovny Aspose.Words pro .NET můžete snadno identifikovat typy revizí ve vašem dokumentu Wordu pomocí několika řádků kódu. Tato výkonná knihovna usnadňuje práci s revizemi dokumentů a umožňuje vám soustředit se na důležitější úkoly. 

## Často kladené otázky

### Mohu použít Aspose.Words pro .NET ke sledování změn provedených konkrétními uživateli?

Ano, Aspose.Words pro .NET poskytuje funkce pro přístup k podrobnostem o revizích, včetně autora změn.

### Je k dispozici bezplatná zkušební verze pro Aspose.Words pro .NET?

Rozhodně! Můžete získat bezplatnou zkušební verzi [zde](https://releases.aspose.com/).

### Jak mohu požádat o dočasnou licenci pro Aspose.Words pro .NET?

Dočasnou licenci si můžete vyžádat a zažádat si od [zde](https://purchase.aspose.com/temporary-license/).

### Kde najdu podrobnější dokumentaci k Aspose.Words pro .NET?

Podrobná dokumentace je k dispozici na [Webové stránky Aspose](https://reference.aspose.com/words/net/).

### Mohu použít Aspose.Words pro .NET v nekomerčním projektu?

Ano, Aspose.Words pro .NET lze použít v komerčních i nekomerčních projektech, ale nezapomeňte si zkontrolovat licenční podmínky.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}