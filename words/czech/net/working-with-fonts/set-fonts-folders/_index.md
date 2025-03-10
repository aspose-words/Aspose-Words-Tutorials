---
title: Nastavte složky písem
linktitle: Nastavte složky písem
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak nastavit vlastní složky písem v Aspose.Words pro .NET pomocí tohoto komplexního průvodce krok za krokem. Ideální pro vývojáře, kteří chtějí vylepšit písma dokumentů.
weight: 10
url: /cs/net/working-with-fonts/set-fonts-folders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nastavte složky písem

## Zavedení

Ahoj! Jste připraveni ponořit se do světa vlastních písem v Aspose.Words pro .NET? Začněme. Tento tutoriál vás provede procesem nastavení vlastních složek písem a zajistí, že vaše dokumenty budou vypadat přesně tak, jak chcete. Ať už jste zkušený vývojář nebo teprve začínáte, tento průvodce vás provede každým krokem. Tak, pojďme, aby ty fonty vypadaly báječně!

## Předpoklady

Než se do toho pustíme, ujistěte se, že máte vše, co potřebujete:

-  Aspose.Words pro .NET: Můžete[stáhnout](https://releases.aspose.com/words/net/) pokud jste to ještě neudělali.
- Visual Studio: Bude fungovat jakákoli verze, ale nejnovější je vždy nejlepší.
- Dokument: Pro tento tutoriál použijeme dokument aplikace Word. Můžete si vytvořit vlastní nebo použít existující.
- Vlastní písma: Připravte si vlastní písma. Použijeme je k ukázce, jak nastavit složky písem.

## Importovat jmenné prostory

Nejprve importujme potřebné jmenné prostory. To je nezbytné pro přístup ke třídám a metodám, které potřebujeme z Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Po importu těchto jmenných prostorů jsme připraveni začít nastavovat naše vlastní složky písem.

## Krok 1: Definujte svůj adresář dokumentů

 Začněme definováním cesty k adresáři s dokumenty. Zde je uložen váš dokument aplikace Word. Budeme používat proměnnou tzv`dataDir` pro uložení této cesty.

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Nahradit`"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou k vašemu adresáři. To je zásadní, protože Aspose.Words bude muset vědět, kde najde váš dokument.

## Krok 2: Nastavte zdroje písem

 Dále musíme nastavit zdroje písem. Zde říkáme Aspose.Words, kde najdou naše vlastní písma. Budeme používat`FontSettings.DefaultInstance.SetFontsSources` způsob, jak toho dosáhnout.

```csharp
FontSettings.DefaultInstance.SetFontsSources(new FontSourceBase[]
{
	new SystemFontSource(), new FolderFontSource("C:\\MyFonts\\", true)
});
```

Zde je to, co děláme:

- SystemFontSource: Toto říká Aspose.Words, aby použilo výchozí fonty systému.
-  FolderFontSource: Zde určujeme složku obsahující naše vlastní písma. Nahradit`"C:\\MyFonts\\"` s cestou k vašemu adresáři vlastních písem. The`true` Parametr označuje, že by měly být zahrnuty také podadresáře.

## Krok 3: Vložte svůj dokument

Nyní, když jsme nastavili zdroje písem, je čas načíst dokument, se kterým chceme pracovat. Použijeme`Document` třída z Aspose.Slova k tomu.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

 Zajistěte to`"Rendering.docx"` je název vašeho dokumentu aplikace Word. Pokud má váš dokument jiný název, nezapomeňte jej odpovídajícím způsobem aktualizovat.

## Krok 4: Uložte dokument jako PDF

 Nakonec uložme náš dokument jako PDF, abychom viděli vlastní písma v akci. Použijeme`Save` metoda`Document` třída.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFolders.pdf");
```

Tím se váš dokument uloží jako PDF do určeného adresáře s použitím vlastních písem, která jsme nastavili dříve.

## Závěr

A tady to máte! Úspěšně jste nastavili vlastní složky písem v Aspose.Words pro .NET a uložili dokument jako PDF s těmito vlastními písmy. Docela cool, že? Přizpůsobení písem může výrazně změnit vzhled vašich dokumentů a nyní přesně víte, jak na to. Šťastné kódování!

## FAQ

### Jak nainstaluji Aspose.Words for .NET?

 Můžete[stáhnout](https://releases.aspose.com/words/net/) nejnovější verzi Aspose.Words pro .NET z webu.

### Mohu použít více vlastních složek písem?

 Ano, můžete přidat více`FolderFontSource` instance k`SetFontsSources`metoda pro použití písem z různých adresářů.

### Je nutné zahrnout systémová písma?

Zahrnutí systémových písem je volitelné, ale doporučuje se, aby byla zajištěna dostupnost všech standardních písem.

### Jaké typy souborů podporuje Aspose.Words?

Aspose.Words podporuje širokou škálu formátů souborů, včetně DOCX, DOC, PDF, TXT, HTML a mnoha dalších.

### Jak mohu získat dočasnou licenci pro Aspose.Words?

 Můžete získat a[dočasná licence](https://purchase.aspose.com/temporary-license/) z webu Aspose, abyste mohli vyzkoušet všechny funkce Aspose.Words.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
