---
title: Přidat předponu názvu třídy CSS
linktitle: Přidat předponu názvu třídy CSS
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak přidat předponu názvu třídy CSS při ukládání dokumentů aplikace Word jako HTML pomocí Aspose.Words for .NET. Součástí je podrobný průvodce, úryvky kódu a časté dotazy.
weight: 10
url: /cs/net/programming-with-htmlsaveoptions/add-css-class-name-prefix/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Přidat předponu názvu třídy CSS

## Zavedení

Vítejte! Pokud se ponoříte do světa Aspose.Words pro .NET, budete se těšit. Dnes se podíváme na to, jak přidat předponu názvu třídy CSS při ukládání dokumentu aplikace Word jako HTML pomocí Aspose.Words for .NET. Tato funkce je velmi užitečná, když se chcete vyhnout konfliktům názvů tříd v souborech HTML.

## Předpoklady

Než začneme, ujistěte se, že máte následující:

-  Aspose.Words for .NET: Pokud jste jej ještě nenainstalovali,[stáhněte si to zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Visual Studio nebo jakékoli jiné C# IDE.
-  Dokument aplikace Word: Budeme používat dokument s názvem`Rendering.docx`. Umístěte jej do adresáře projektu.

## Importovat jmenné prostory

Nejprve se ujistěte, že máte do svého projektu C# importovány potřebné jmenné prostory. Přidejte tyto v horní části souboru kódu:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

Nyní se pojďme ponořit do podrobného průvodce!

## Krok 1: Nastavte svůj projekt

Než začneme přidávat předponu názvu třídy CSS, nastavíme náš projekt.

### Krok 1.1: Vytvořte nový projekt

 Spusťte své Visual Studio a vytvořte nový projekt Console App. Pojmenujte to nějak chytlavě jako`AsposeCssPrefixExample`.

### Krok 1.2: Přidejte Aspose.Words pro .NET

Pokud jste tak ještě neučinili, přidejte Aspose.Words for .NET do svého projektu prostřednictvím NuGet. Jednoduše otevřete konzolu NuGet Package Manager Console a spusťte:

```bash
Install-Package Aspose.Words
```

Velký! Nyní jsme připraveni začít kódovat.

## Krok 2: Vložte svůj dokument

První věc, kterou musíme udělat, je načíst dokument aplikace Word, který chceme převést do HTML.

### Krok 2.1: Definujte cestu dokumentu

 Nastavte cestu k adresáři dokumentů. Pro účely tohoto tutoriálu předpokládejme, že váš dokument je ve složce s názvem`Documents` v adresáři vašeho projektu.

```csharp
string dataDir = @"C:\YourProject\Documents\";
```

### Krok 2.2: Vložte dokument

Nyní načtěte dokument pomocí Aspose.Words:

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Krok 3: Nakonfigurujte možnosti uložení HTML

Dále musíme nakonfigurovat možnosti uložení HTML tak, aby obsahovaly předponu názvu třídy CSS.

### Krok 3.1: Vytvořte možnosti uložení HTML

 Vytvořte instanci`HtmlSaveOptions` objekt a nastavte typ šablony stylů CSS na`External`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External
};
```

### Krok 3.2: Nastavte předponu názvu třídy CSS

 Nyní nastavíme`CssClassNamePrefix` vlastnost na požadovanou předponu. Pro tento příklad použijeme`"pfx_"`.

```csharp
saveOptions.CssClassNamePrefix = "pfx_";
```

## Krok 4: Uložte dokument jako HTML

Nakonec uložme dokument jako soubor HTML s našimi nakonfigurovanými možnostmi.


Zadejte cestu k výstupnímu souboru HTML a uložte dokument.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
```

## Krok 5: Ověřte výstup

 Po spuštění projektu přejděte do svého`Documents` složku. Měli byste najít soubor HTML s názvem`WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html` . Otevřete tento soubor v textovém editoru nebo prohlížeči a ověřte, že třídy CSS mají předponu`pfx_`.

## Závěr

A tady to máte! Pomocí těchto kroků jste úspěšně přidali předponu názvu třídy CSS do výstupu HTML pomocí Aspose.Words for .NET. Tato jednoduchá, ale výkonná funkce vám může pomoci udržovat čisté a nekonfliktní styly v dokumentech HTML.

## FAQ

### Mohu pro každou operaci uložení použít jinou předponu?
 Ano, předponu můžete přizpůsobit pokaždé, když uložíte dokument změnou`CssClassNamePrefix` vlastnictví.

### Podporuje tato metoda inline CSS?
 The`CssClassNamePrefix`vlastnost pracuje s externím CSS. Pro inline CSS budete potřebovat jiný přístup.

### Jak mohu zahrnout další možnosti uložení HTML?
 Můžete nakonfigurovat různé vlastnosti`HtmlSaveOptions` pro přizpůsobení výstupu HTML. Zkontrolujte[dokumentace](https://reference.aspose.com/words/net/) pro více podrobností.

### Je možné uložit HTML do streamu?
 Absolutně! Dokument můžete uložit do streamu předáním objektu stream do`Save` metoda.

### Jak získám podporu, pokud narazím na problémy?
 Můžete získat podporu od[Aspose fórum](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
