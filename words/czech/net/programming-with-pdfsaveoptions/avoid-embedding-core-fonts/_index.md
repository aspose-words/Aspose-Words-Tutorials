---
"description": "Naučte se, jak zmenšit velikost PDF souboru tím, že nevložíte základní písma pomocí Aspose.Words pro .NET. Postupujte podle našeho podrobného návodu k optimalizaci vašich PDF souborů."
"linktitle": "Zmenšení velikosti PDF souboru bez vkládání základních písem"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Zmenšení velikosti PDF souboru bez vkládání základních písem"
"url": "/cs/net/programming-with-pdfsaveoptions/avoid-embedding-core-fonts/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Zmenšení velikosti PDF souboru bez vkládání základních písem

## Zavedení

Stává se vám někdy, že si lámete hlavu a přemýšlíte, proč jsou vaše PDF soubory tak velké? Nejste v tom sami. Jedním z častých viníků je vkládání základních fontů, jako jsou Arial a Times New Roman. Naštěstí má Aspose.Words pro .NET šikovný způsob, jak tento problém vyřešit. V tomto tutoriálu vám ukážu, jak zmenšit velikost PDF souboru tím, že se vyhnete vkládání těchto základních fontů. Pojďme se do toho pustit!

## Předpoklady

Než se vydáme na tuto vzrušující cestu, ujistěme se, že máte vše, co potřebujete. Zde je stručný kontrolní seznam:

- Aspose.Words pro .NET: Ujistěte se, že máte nainstalovaný Aspose.Words pro .NET. Pokud ho ještě nemáte, můžete si ho stáhnout. [zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Budete potřebovat vývojové prostředí, jako je Visual Studio.
- Dokument Word: V tomto tutoriálu použijeme dokument Word (např. „Rendering.docx“).
- Základní znalost C#: Základní znalost C# vám pomůže se v daném textu orientovat.

Dobře, teď když už máme vše připravené, pojďme k jádru věci!

## Importovat jmenné prostory

Nejdříve si importujme potřebné jmenné prostory. Tento krok nám zajistí přístup ke všem funkcím Aspose.Words, které potřebujeme.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Inicializace adresáře dokumentů

Než začneme s manipulací s dokumentem, musíme určit adresář, kde jsou naše dokumenty uloženy. To je nezbytné pro přístup k souborům.

```csharp
// Cesta k adresáři s dokumenty.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Nahradit `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou, kde se nachází váš dokument Word.

## Krok 2: Načtěte dokument Wordu

Dále musíme načíst dokument Wordu, který chceme převést do formátu PDF. V tomto příkladu používáme dokument s názvem „Rendering.docx“.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Tento řádek kódu načte dokument do paměti a připraví ho k dalšímu zpracování.

## Krok 3: Konfigurace možností ukládání PDF

teď přichází ta magická část! Nakonfigurujeme možnosti ukládání PDF tak, abychom se vyhnuli vkládání základních písem. To je klíčový krok, který pomáhá zmenšit velikost PDF souboru.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    UseCoreFonts = true
};
```

Prostředí `UseCoreFonts` na `true` zajišťuje, že základní fonty jako Arial a Times New Roman nejsou vloženy do PDF, což výrazně snižuje velikost souboru.

## Krok 4: Uložte dokument jako PDF

Nakonec uložíme dokument Wordu jako PDF s použitím nakonfigurovaných možností ukládání. Tento krok vygeneruje soubor PDF bez vložení základních písem.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.AvoidEmbeddingCoreFonts.pdf", saveOptions);
```

A tady to máte! Váš PDF soubor je nyní uložen v určeném adresáři bez těch objemných základních písem.

## Závěr

Zmenšení velikosti PDF souboru může být s Aspose.Words pro .NET hračka. Vyhnete se vkládání základních písem a můžete výrazně zmenšit velikost souboru, což usnadní sdílení a ukládání dokumentů. Doufám, že tento návod byl užitečný a poskytl vám jasnou představu o celém procesu. Nezapomeňte, že i malé úpravy mohou mít velký význam!

## Často kladené otázky

### Proč bych se měl vyhýbat vkládání základních písem do PDF souborů?
Vyhýbání se vkládání základních písem snižuje velikost souboru, což usnadňuje jeho sdílení a ukládání.

### Mohu si PDF soubor zobrazit správně i bez vložených základních písem?
Ano, základní fonty jako Arial a Times New Roman jsou obecně dostupné na většině systémů.

### Co když potřebuji vložit vlastní písma?
Můžete si přizpůsobit `PdfSaveOptions` vkládat konkrétní písma dle potřeby.

### Je Aspose.Words pro .NET zdarma k použití?
Aspose.Words pro .NET vyžaduje licenci. Můžete získat bezplatnou zkušební verzi. [zde](https://releases.aspose.com/).

### Kde najdu další dokumentaci k Aspose.Words pro .NET?
Podrobnou dokumentaci naleznete [zde](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}