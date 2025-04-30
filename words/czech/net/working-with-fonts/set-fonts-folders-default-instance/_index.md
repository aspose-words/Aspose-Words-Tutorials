---
"description": "Naučte se v tomto podrobném návodu, jak nastavit složky písem pro výchozí instanci v Aspose.Words pro .NET. Přizpůsobte si své dokumenty Word bez námahy."
"linktitle": "Nastavení výchozí instance složek písem"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Nastavení výchozí instance složek písem"
"url": "/cs/net/working-with-fonts/set-fonts-folders-default-instance/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Nastavení výchozí instance složek písem

## Zavedení

Ahoj, kolegové programátoři! Pokud pracujete s dokumenty Wordu v .NET, pravděpodobně víte, jak důležité je mít správně nastavená písma. Dnes se ponoříme do toho, jak nastavit složky s písmy pro výchozí instanci pomocí Aspose.Words pro .NET. Představte si, že máte všechna svá vlastní písma na dosah ruky a vaše dokumenty budou vypadat přesně tak, jak si je představujete. Zní to skvěle, že? Pojďme na to!

## Předpoklady

Než se ponoříme do detailů, ujistěme se, že máte vše, co potřebujete:
- Aspose.Words pro .NET: Ujistěte se, že máte knihovnu nainstalovanou. Pokud ne, můžete [stáhněte si to zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Visual Studio nebo jakékoli jiné IDE kompatibilní s .NET.
- Základní znalost C#: Měli byste se orientovat v programování v C#.
- Složka fontů: Adresář obsahující vaše vlastní fonty.

## Importovat jmenné prostory

Nejdříve si importujme potřebné jmenné prostory. To nám pomůže s přístupem ke třídám a metodám potřebným pro nastavení složky s fonty.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Rozdělme si proces na jednoduché a stravitelné kroky.

## Krok 1: Definování datového adresáře

Každá velká cesta začíná jediným krokem a ten náš začíná definováním adresáře, kde je váš dokument uložen. Právě zde bude Aspose.Words hledat váš dokument Wordu.

```csharp
// Cesta k adresáři s dokumenty
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Zde nahraďte `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou k adresáři s vašimi dokumenty. Zde se nachází váš zdrojový dokument a kam se uloží výstup.

## Krok 2: Nastavení složky s fonty

Nyní řekněme Aspose.Words, kde má najít vaše vlastní fonty. To se provede nastavením složky fonty pomocí `FontSettings.DefaultInstance.SetFontsFolder` metoda.

```csharp
FontSettings.DefaultInstance.SetFontsFolder("C:\\MyFonts\\", true);
```

V tomto řádku, `"C:\\MyFonts\\"` je cesta ke složce s vlastními fonty. Druhý parametr, `true`, označuje, že písma v této složce by měla být prohledávána rekurzivně.

## Krok 3: Vložte dokument

Po nastavení složky s fonty je dalším krokem načtení dokumentu Word do Aspose.Words. To se provádí pomocí `Document` třída.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Zde, `dataDir + "Rendering.docx"` odkazuje na úplnou cestu k dokumentu aplikace Word. Ujistěte se, že se dokument nachází v zadaném adresáři.

## Krok 4: Uložte dokument

Posledním krokem je uložení dokumentu po nastavení složky s fonty. Tím zajistíte, že vaše vlastní fonty budou ve výstupu správně použity.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersDefaultInstance.pdf");
```

Tento řádek uloží váš dokument jako PDF s použitými vlastními fonty. Výstupní soubor bude umístěn ve stejném adresáři jako váš zdrojový dokument.

## Závěr

je to! Nastavení složek písem pro výchozí instanci v Aspose.Words pro .NET je hračka, když si to rozdělíte do jednoduchých kroků. Dodržováním tohoto návodu si můžete být jisti, že vaše dokumenty Wordu budou vypadat přesně tak, jak chcete, se všemi vašimi vlastními písmy. Tak do toho, vyzkoušejte to a nechte své dokumenty zářit!

## Často kladené otázky

### Mohu nastavit více složek s fonty?
Ano, můžete nastavit více složek s fonty pomocí `SetFontsFolders` metoda, která přijímá pole cest ke složkám.

### Jaké formáty souborů Aspose.Words podporuje pro ukládání dokumentů?
Aspose.Words podporuje různé formáty včetně DOCX, PDF, HTML, EPUB a dalších.

### Je možné v Aspose.Words používat online fonty?
Ne, Aspose.Words v současné době podporuje pouze lokální soubory písem.

### Jak mohu zajistit, aby moje vlastní písma byla vložena do uloženého PDF?
Nastavením `FontSettings` Pokud jsou fonty správně a jsou k dispozici, Aspose.Words je vloží do výstupu PDF.

### Co se stane, když se písmo v zadané složce nenajde?
Aspose.Words použije záložní písmo, pokud zadané písmo nebude nalezeno.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}