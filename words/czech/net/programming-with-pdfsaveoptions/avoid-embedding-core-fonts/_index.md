---
title: Zmenšete velikost souboru PDF nevkládáním základních písem
linktitle: Zmenšete velikost souboru PDF nevkládáním základních písem
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak zmenšit velikost souboru PDF nevkládáním základních písem pomocí Aspose.Words for .NET. Chcete-li optimalizovat soubory PDF, postupujte podle našeho podrobného průvodce.
weight: 10
url: /cs/net/programming-with-pdfsaveoptions/avoid-embedding-core-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zmenšete velikost souboru PDF nevkládáním základních písem

## Zavedení

Stává se vám někdy, že se škrábete na hlavě a říkáte si, proč jsou vaše soubory PDF tak velké? No, nejsi sám. Jedním společným viníkem je vkládání základních písem, jako jsou Arial a Times New Roman. Naštěstí má Aspose.Words pro .NET šikovný způsob, jak tento problém vyřešit. V tomto tutoriálu vám ukážu, jak zmenšit velikost souboru PDF tím, že se vyhnete vkládání těchto základních písem. Pojďme se rovnou ponořit!

## Předpoklady

Než se vydáme na tuto vzrušující cestu, ujistěte se, že máte vše, co potřebujete. Zde je rychlý kontrolní seznam:

-  Aspose.Words for .NET: Ujistěte se, že máte nainstalovanou aplikaci Aspose.Words for .NET. Pokud ji ještě nemáte, můžete si ji stáhnout[zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Budete potřebovat vývojové prostředí, jako je Visual Studio.
- Dokument aplikace Word: Pro tento výukový program budeme používat dokument aplikace Word (např. „Rendering.docx“).
- Základní znalost C#: Základní znalost C# vám pomůže pokračovat.

Dobře, teď, když jsme vše připraveni, pojďme do toho natvrdo!

## Importovat jmenné prostory

Nejprve importujme potřebné jmenné prostory. Tento krok zajišťuje, že máme přístup ke všem funkcím Aspose.Words, které potřebujeme.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Inicializujte svůj adresář dokumentů

Než začneme s naším dokumentem manipulovat, musíme určit adresář, kde jsou naše dokumenty uloženy. To je nezbytné pro přístup k souborům.

```csharp
// Cesta k adresáři dokumentů.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Nahradit`"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou, kde se nachází váš dokument aplikace Word.

## Krok 2: Načtěte dokument aplikace Word

Dále musíme načíst dokument Word, který chceme převést do PDF. V tomto příkladu používáme dokument s názvem "Rendering.docx".

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Tento řádek kódu načte dokument do paměti, připraven k dalšímu zpracování.

## Krok 3: Nakonfigurujte možnosti uložení PDF

Teď přichází ta kouzelná část! Nakonfigurujeme možnosti uložení PDF, abychom se vyhnuli vkládání základních písem. Toto je klíčový krok, který pomáhá zmenšit velikost souboru PDF.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    UseCoreFonts = true
};
```

 Nastavení`UseCoreFonts` na`true` zajišťuje, že základní písma jako Arial a Times New Roman nejsou vložena do PDF, což výrazně snižuje velikost souboru.

## Krok 4: Uložte dokument jako PDF

Nakonec uložíme dokument aplikace Word jako PDF pomocí nakonfigurovaných možností uložení. Tento krok vygeneruje soubor PDF bez vkládání základních písem.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.AvoidEmbeddingCoreFonts.pdf", saveOptions);
```

A tady to máte! Váš soubor PDF je nyní uložen v určeném adresáři bez těchto objemných základních písem.

## Závěr

Zmenšení velikosti souboru PDF může být s Aspose.Words pro .NET hračkou. Tím, že se vyhnete vkládání základních písem, můžete výrazně zmenšit velikost souboru, což usnadňuje sdílení a ukládání dokumentů. Doufám, že vám tento tutoriál pomohl a dal vám jasné pochopení procesu. Pamatujte, že malé úpravy mohou znamenat velký rozdíl!

## FAQ

### Proč bych se měl vyhnout vkládání základních písem do souborů PDF?
Vyhýbání se vkládání základních písem snižuje velikost souboru, což usnadňuje sdílení a ukládání.

### Mohu stále správně zobrazit PDF bez vložených základních písem?
Ano, základní písma jako Arial a Times New Roman jsou obecně dostupná na většině systémů.

### Co když potřebuji vložit vlastní písma?
 Můžete si přizpůsobit`PdfSaveOptions`podle potřeby vložit konkrétní písma.

### Je Aspose.Words for .NET zdarma k použití?
 Aspose.Words for .NET vyžaduje licenci. Můžete získat bezplatnou zkušební verzi[zde](https://releases.aspose.com/).

### Kde najdu další dokumentaci k Aspose.Words pro .NET?
 Můžete najít podrobnou dokumentaci[zde](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
