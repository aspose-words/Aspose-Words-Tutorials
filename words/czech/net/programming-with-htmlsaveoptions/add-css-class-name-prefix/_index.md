---
"description": "Naučte se, jak přidat předponu názvu třídy CSS při ukládání dokumentů Word ve formátu HTML pomocí Aspose.Words pro .NET. Součástí je podrobný návod, úryvky kódu a často kladené otázky."
"linktitle": "Přidat předponu názvu třídy CSS"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Přidat předponu názvu třídy CSS"
"url": "/cs/net/programming-with-htmlsaveoptions/add-css-class-name-prefix/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Přidat předponu názvu třídy CSS

## Zavedení

Vítejte! Pokud se ponořujete do světa Aspose.Words pro .NET, čeká vás lahůdka. Dnes se podíváme na to, jak přidat prefix názvu třídy CSS při ukládání dokumentu Word ve formátu HTML pomocí Aspose.Words pro .NET. Tato funkce je velmi užitečná, pokud se chcete vyhnout konfliktům názvů tříd ve vašich souborech HTML.

## Předpoklady

Než začneme, ujistěte se, že máte následující:

- Aspose.Words pro .NET: Pokud jste si ho ještě nenainstalovali, [stáhněte si to zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Visual Studio nebo jakékoli jiné C# IDE.
- Dokument Word: Použijeme dokument s názvem `Rendering.docx`Umístěte jej do adresáře projektu.

## Importovat jmenné prostory

Nejprve se ujistěte, že máte do projektu v C# importovány potřebné jmenné prostory. Přidejte je na začátek souboru s kódem:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

A teď se pojďme ponořit do podrobného návodu!

## Krok 1: Nastavení projektu

Než začneme přidávat prefix názvu CSS třídy, nastavme si náš projekt.

### Krok 1.1: Vytvoření nového projektu

Spusťte Visual Studio a vytvořte nový projekt konzolové aplikace. Pojmenujte ho nějak chytlavě, například `AsposeCssPrefixExample`.

### Krok 1.2: Přidání Aspose.Words pro .NET

Pokud jste to ještě neudělali, přidejte Aspose.Words pro .NET do svého projektu pomocí NuGetu. Jednoduše otevřete konzoli Správce balíčků NuGet a spusťte:

```bash
Install-Package Aspose.Words
```

Skvělé! Teď můžeme začít programovat.

## Krok 2: Vložte dokument

První věc, kterou musíme udělat, je načíst dokument Wordu, který chceme převést do HTML.

### Krok 2.1: Definování cesty k dokumentu

Nastavte cestu k adresáři s dokumenty. Pro účely tohoto tutoriálu předpokládejme, že váš dokument je ve složce s názvem `Documents` v adresáři vašeho projektu.

```csharp
string dataDir = @"C:\YourProject\Documents\";
```

### Krok 2.2: Načtení dokumentu

Nyní si načtěme dokument pomocí Aspose.Words:

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Krok 3: Konfigurace možností ukládání HTML

Dále musíme nakonfigurovat možnosti ukládání HTML tak, aby zahrnovaly prefix názvu třídy CSS.

### Krok 3.1: Vytvoření možností uložení HTML

Vytvořte instanci `HtmlSaveOptions` objekt a nastavte typ stylu CSS na `External`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External
};
```

### Krok 3.2: Nastavení předpony názvu třídy CSS

Nyní nastavme `CssClassNamePrefix` vlastnost na požadovaný prefix. V tomto příkladu použijeme `"pfx_"`.

```csharp
saveOptions.CssClassNamePrefix = "pfx_";
```

## Krok 4: Uložte dokument jako HTML

Nakonec uložme dokument jako HTML soubor s našimi nakonfigurovanými možnostmi.


Zadejte cestu k výstupnímu HTML souboru a uložte dokument.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
```

## Krok 5: Ověření výstupu

Po spuštění projektu přejděte do `Documents` složku. Měli byste najít soubor HTML s názvem `WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html`Otevřete tento soubor v textovém editoru nebo prohlížeči a ověřte, zda třídy CSS mají prefix `pfx_`.

## Závěr

A tady to máte! Dodržováním těchto kroků jste úspěšně přidali prefix názvu třídy CSS do svého HTML výstupu pomocí Aspose.Words pro .NET. Tato jednoduchá, ale výkonná funkce vám pomůže udržovat čisté a bezkonfliktní styly ve vašich HTML dokumentech.

## Často kladené otázky

### Mohu pro každou operaci ukládání použít jiný prefix?
Ano, předponu si můžete přizpůsobit při každém uložení dokumentu změnou `CssClassNamePrefix` vlastnictví.

### Podporuje tato metoda inline CSS?
Ten/Ta/To `CssClassNamePrefix` Property funguje s externím CSS. Pro inline CSS budete potřebovat jiný přístup.

### Jak mohu zahrnout další možnosti ukládání HTML?
Můžete nakonfigurovat různé vlastnosti `HtmlSaveOptions` pro přizpůsobení HTML výstupu. Zaškrtněte [dokumentace](https://reference.aspose.com/words/net/) pro více informací.

### Je možné uložit HTML do streamu?
Rozhodně! Dokument můžete uložit do streamu předáním objektu streamu do `Save` metoda.

### Jak získám podporu, pokud narazím na problémy?
Podporu můžete získat od [Fórum Aspose](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}