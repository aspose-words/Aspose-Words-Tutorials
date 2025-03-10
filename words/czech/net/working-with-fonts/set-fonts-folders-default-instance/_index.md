---
title: Nastavit výchozí instanci složek písem
linktitle: Nastavit výchozí instanci složek písem
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak nastavit složky písem pro výchozí instanci v Aspose.Words for .NET pomocí tohoto podrobného kurzu. Přizpůsobte si dokumenty aplikace Word bez námahy.
weight: 10
url: /cs/net/working-with-fonts/set-fonts-folders-default-instance/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nastavit výchozí instanci složek písem

## Zavedení

Ahoj, kolego kodéru! Pokud pracujete s dokumenty Wordu v .NET, pravděpodobně víte, jak je důležité mít správně nastavená písma. Dnes se ponoříme do toho, jak nastavit složky písem pro výchozí instanci pomocí Aspose.Words pro .NET. Představte si, že máte všechna svá vlastní písma na dosah ruky a vaše dokumenty budou vypadat přesně tak, jak si je představujete. Zní to skvěle, že? Začněme!

## Předpoklady

Než se ponoříme do hrubších detailů, ujistěte se, že máte vše, co potřebujete:
-  Aspose.Words for .NET: Ujistěte se, že máte nainstalovanou knihovnu. Pokud ne, můžete[stáhněte si to zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Visual Studio nebo jakékoli jiné IDE kompatibilní s .NET.
- Základní znalost C#: Měli byste být spokojeni s programováním v C#.
- Složka písem: Adresář obsahující vaše vlastní písma.

## Importovat jmenné prostory

Nejprve importujme potřebné jmenné prostory. To pomáhá při přístupu ke třídám a metodám potřebným pro nastavení složky písem.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Pojďme si tento proces rozebrat do jednoduchých, stravitelných kroků.

## Krok 1: Definujte datový adresář

Každá velká cesta začíná jediným krokem a ta naše začíná definováním adresáře, kde je váš dokument uložen. Zde bude Aspose.Words hledat váš dokument aplikace Word.

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Tady, vyměňte`"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou k vašemu adresáři dokumentů. Zde se nachází váš zdrojový dokument a kam se uloží výstup.

## Krok 2: Nastavte složku Fonts

 Nyní řekněme Aspose.Words, kde najdou svá vlastní písma. To se provádí nastavením složky písem pomocí`FontSettings.DefaultInstance.SetFontsFolder` metoda.

```csharp
FontSettings.DefaultInstance.SetFontsFolder("C:\\MyFonts\\", true);
```

 V tomto řádku`"C:\\MyFonts\\"` je cesta ke složce vlastních písem. Druhý parametr,`true`, označuje, že písma v této složce by měla být skenována rekurzivně.

## Krok 3: Vložte svůj dokument

 Po nastavení složky písem je dalším krokem načtení dokumentu aplikace Word do Aspose.Words. To se provádí pomocí`Document` třída.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

 Zde,`dataDir + "Rendering.docx"` odkazuje na úplnou cestu vašeho dokumentu aplikace Word. Ujistěte se, že je dokument v zadaném adresáři.

## Krok 4: Uložte dokument

Posledním krokem je uložení dokumentu po nastavení složky písem. Tím zajistíte, že vaše vlastní písma budou ve výstupu správně použita.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersDefaultInstance.pdf");
```

Tento řádek uloží váš dokument jako PDF s použitými vlastními fonty. Výstupní soubor bude umístěn ve stejném adresáři jako váš zdrojový dokument.

## Závěr

tady to máte! Nastavení složek písem pro výchozí instanci v Aspose.Words pro .NET je hračka, když to rozdělíte do jednoduchých kroků. Podle této příručky můžete zajistit, aby vaše dokumenty Word vypadaly přesně tak, jak chcete, se všemi vašimi vlastními fonty. Takže jděte do toho, vyzkoušejte to a vaše dokumenty zazáří!

## FAQ

### Mohu nastavit více složek písem?
 Ano, můžete nastavit více složek písem pomocí`SetFontsFolders` metoda, která přijímá pole cest složek.

### Jaké formáty souborů podporuje Aspose.Words pro ukládání dokumentů?
Aspose.Words podporuje různé formáty včetně DOCX, PDF, HTML, EPUB a dalších.

### Je možné v Aspose.Words používat online fonty?
Ne, Aspose.Words aktuálně podporuje pouze místní soubory písem.

### Jak mohu zajistit, aby moje vlastní písma byla vložena do uloženého PDF?
 Nastavením`FontSettings` správně a zajistí, že jsou dostupná písma, Aspose.Words je vloží do výstupu PDF.

### Co se stane, když písmo nebude v zadané složce nalezeno?
Aspose.Words použije záložní písmo, pokud nebude zadané písmo nalezeno.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
