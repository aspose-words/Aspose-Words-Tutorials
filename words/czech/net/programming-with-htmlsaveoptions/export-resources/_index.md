---
"description": "Naučte se, jak exportovat zdroje, jako jsou CSS a fonty, a zároveň ukládat dokumenty Wordu jako HTML pomocí Aspose.Words pro .NET. Postupujte podle našeho podrobného návodu."
"linktitle": "Exportní zdroje"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Exportní zdroje"
"url": "/cs/net/programming-with-htmlsaveoptions/export-resources/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Exportní zdroje

## Zavedení

Ahoj, techničtí nadšenci! Pokud jste někdy potřebovali převést dokumenty Wordu do HTML, jste na správném místě. Dnes se ponoříme do úžasného světa Aspose.Words pro .NET. Tato výkonná knihovna usnadňuje programovou práci s dokumenty Wordu. V tomto tutoriálu si projdeme kroky exportu zdrojů, jako jsou fonty a CSS, při ukládání dokumentu Wordu do HTML pomocí Aspose.Words pro .NET. Připoutejte se na zábavnou a informativní jízdu!

## Předpoklady

Než se pustíme do kódu, ujistěme se, že máte vše, co potřebujete k zahájení. Zde je stručný kontrolní seznam:

1. Visual Studio: Ujistěte se, že máte na svém počítači nainstalované Visual Studio. Můžete si ho stáhnout z [Webové stránky Visual Studia](https://visualstudio.microsoft.com/).
2. Aspose.Words pro .NET: Budete potřebovat knihovnu Aspose.Words pro .NET. Pokud ji ještě nemáte, stáhněte si bezplatnou zkušební verzi z [Aspose Releases](https://releases.aspose.com/words/net/) nebo si ho zakoupit od [Obchod Aspose](https://purchase.aspose.com/buy).
3. Základní znalost jazyka C#: Základní znalost jazyka C# vám pomůže sledovat příklady kódu.

Rozumíte tomu všemu? Skvělé! Pojďme k importu potřebných jmenných prostorů.

## Importovat jmenné prostory

Chcete-li používat Aspose.Words pro .NET, musíte do projektu zahrnout příslušné jmenné prostory. Postupujte takto:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Tyto jmenné prostory jsou klíčové pro přístup ke třídám a metodám Aspose.Words, které budeme používat v našem tutoriálu.

Pojďme si rozebrat proces exportu zdrojů při ukládání dokumentu Word ve formátu HTML. Provedeme to krok za krokem, aby to bylo snadné sledovat.

## Krok 1: Nastavení adresáře dokumentů

Nejprve je třeba zadat cestu k adresáři s vašimi dokumenty. Zde se nachází váš dokument Wordu a kam bude uložen soubor HTML.

```csharp
// Cesta k adresáři s dokumenty.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Nahradit `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou k vašemu adresáři.

## Krok 2: Načtěte dokument Wordu

Dále načtěme dokument Wordu, který chcete převést do formátu HTML. V tomto tutoriálu použijeme dokument s názvem `Rendering.docx`.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Tento řádek kódu načte dokument ze zadaného adresáře.

## Krok 3: Konfigurace možností ukládání HTML

Pro export zdrojů, jako jsou CSS a fonty, je třeba nakonfigurovat `HtmlSaveOptions`Tento krok je klíčový pro zajištění dobré struktury HTML výstupu a jeho obsahu potřebných zdrojů.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External,
    ExportFontResources = true,
    ResourceFolder = dataDir + "Resources",
    ResourceFolderAlias = "http://example.com/resources"
};
```

Pojďme si rozebrat, co každá možnost dělá:
- `CssStyleSheetType = CssStyleSheetType.External`Tato možnost určuje, že styly CSS by měly být uloženy v externím stylovém listu.
- `ExportFontResources = true`: Toto umožňuje export zdrojů písem.
- `ResourceFolder = dataDir + "Resources"`Určuje lokální složku, kam budou uloženy zdroje (jako jsou fonty a soubory CSS).
- `ResourceFolderAlias = "http://example.com/resources"`: Nastaví alias pro složku zdrojů, který bude použit v souboru HTML.

## Krok 4: Uložte dokument jako HTML

Po nastavení možností ukládání je posledním krokem uložení dokumentu jako souboru HTML. Postupujte takto:

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
```

Tento řádek kódu uloží dokument ve formátu HTML spolu s exportovanými zdroji.

## Závěr

A tady to máte! Úspěšně jste exportovali zdroje a zároveň uložili dokument Word ve formátu HTML pomocí Aspose.Words pro .NET. S touto výkonnou knihovnou se programově stává manipulace s dokumenty Word hračkou. Ať už pracujete na webové aplikaci, nebo jen potřebujete převést dokumenty pro offline použití, Aspose.Words vám s tím pomůže.

## Často kladené otázky

### Mohu exportovat obrázky spolu s fonty a CSS?
Ano, můžete! Aspose.Words pro .NET také podporuje export obrázků. Jen se ujistěte, že jste nakonfigurovali `HtmlSaveOptions` podle toho.

### Existuje způsob, jak vložit CSS místo použití externího stylového listu?
Rozhodně. Můžete nastavit `CssStyleSheetType` na `CssStyleSheetType.Embedded` pokud dáváte přednost vloženým stylům.

### Jak mohu přizpůsobit název výstupního HTML souboru?
Můžete zadat libovolný název souboru v `doc.Save` metoda. Například, `doc.Save(dataDir + "CustomFileName.html", saveOptions);`.

### Podporuje Aspose.Words i jiné formáty než HTML?
Ano, podporuje různé formáty včetně PDF, DOCX, TXT a dalších. Podívejte se na [dokumentace](https://reference.aspose.com/words/net/) pro úplný seznam.

### Kde mohu získat více podpory a zdrojů?
Pro další pomoc navštivte [Fórum podpory Aspose.Words](https://forum.aspose.com/c/words/8)Podrobnou dokumentaci a příklady naleznete také na [Webové stránky Aspose](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}