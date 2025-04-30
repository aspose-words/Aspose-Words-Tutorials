---
"description": "Naučte se, jak exportovat pole formuláře pro zadávání textu jako prostý text pomocí Aspose.Words pro .NET s tímto komplexním podrobným návodem."
"linktitle": "Exportovat pole formuláře pro vstup textu jako text"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Exportovat pole formuláře pro vstup textu jako text"
"url": "/cs/net/programming-with-htmlsaveoptions/export-text-input-form-field-as-text/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Exportovat pole formuláře pro vstup textu jako text

## Zavedení

Takže se ponořujete do světa Aspose.Words pro .NET? Skvělá volba! Pokud se chcete naučit, jak exportovat pole formuláře pro zadávání textu jako text, jste na správném místě. Ať už s tím teprve začínáte, nebo si jen osvěžujete své dovednosti, tento průvodce vás provede vším, co potřebujete vědět. Pojďme na to, co říkáte?

## Předpoklady

Než se ponoříme do detailů, ujistěme se, že máte vše potřebné k hladkému průběhu:

- Aspose.Words pro .NET: Stáhněte a nainstalujte nejnovější verzi z [zde](https://releases.aspose.com/words/net/).
- IDE: Visual Studio nebo jakékoli vývojové prostředí C#.
- Základní znalost C#: Pochopení základní syntaxe C# a konceptů objektově orientovaného programování.
- Dokument: Ukázkový dokument Wordu (`Rendering.docx`) s poli formuláře pro zadávání textu.

## Importovat jmenné prostory

Nejdříve je potřeba importovat potřebné jmenné prostory. Ty jsou jako stavební kameny, díky nimž vše funguje bez problémů.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;
```

Dobře, teď, když máme naše jmenné prostory připravené, pojďme se pustit do akce!

## Krok 1: Nastavení projektu

Než se pustíme do kódu, ujistěme se, že je náš projekt správně nastavený.

## Vytvoření projektu

1. Otevřete Visual Studio: Začněte otevřením Visual Studia nebo preferovaného vývojového prostředí C#.
2. Vytvoření nového projektu: Přejděte na `File > New > Project`Vyberte `Console App (.NET Core)` nebo jakýkoli jiný relevantní typ projektu.
3. Pojmenujte svůj projekt: Dejte svému projektu smysluplný název, například `AsposeWordsExportExample`.

## Přidání Aspose.Words

1. Správa balíčků NuGet: V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte `Manage NuGet Packages`.
2. Hledání Aspose.Words: Ve Správci balíčků NuGet vyhledejte `Aspose.Words`.
3. Instalace Aspose.Words: Klikněte na `Install` přidat knihovnu Aspose.Words do vašeho projektu.

## Krok 2: Načtěte dokument Wordu

Nyní, když je náš projekt nastavený, načtěme dokument Wordu, který obsahuje pole formuláře pro zadávání textu.

1. Zadejte adresář dokumentů: Definujte cestu k adresáři, kde je dokument uložen.
2. Vložení dokumentu: Použijte `Document` třída pro načtení dokumentu Word.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

## Krok 3: Příprava adresáře pro export

Než začneme exportovat, ujistěte se, že je připraven adresář pro export. Zde se uloží náš HTML soubor a obrázky.

1. Definujte adresář pro export: Zadejte cestu, kam budou uloženy exportované soubory.
2. Zkontrolujte a vyčistěte adresář: Ujistěte se, že adresář existuje a je prázdný.

```csharp
string imagesDir = Path.Combine(dataDir, "Images");

if (Directory.Exists(imagesDir))
    Directory.Delete(imagesDir, true);

Directory.CreateDirectory(imagesDir);
```

## Krok 4: Konfigurace možností ukládání

A tady se začne dít ta pravá magie. Musíme nastavit možnosti ukládání tak, aby se pole textového formuláře exportovalo jako prostý text.

1. Vytvořit možnosti uložení: Inicializovat nové `HtmlSaveOptions` objekt.
2. Nastavení možností exportu textu: Konfigurace `ExportTextInputFormFieldAsText` majetek `true`.
3. Nastavit složku obrázků: Definujte složku, kam budou obrázky ukládány.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Html)
{
    ExportTextInputFormFieldAsText = true,
    ImagesFolder = imagesDir
};
```

## Krok 5: Uložte dokument jako HTML

Nakonec uložme dokument Wordu jako soubor HTML pomocí našich nakonfigurovaných možností ukládání.

1. Definujte výstupní cestu: Zadejte cestu, kam bude uložen soubor HTML.
2. Uložení dokumentu: Použijte `Save` metoda `Document` třída pro export dokumentu.

```csharp
doc.Save(dataDir + "ExportedDocument.html", saveOptions);
```

## Závěr

tady to máte! Úspěšně jste exportovali pole formuláře pro zadávání textu jako prostý text pomocí Aspose.Words pro .NET. Tato příručka by vám měla poskytnout jasný a podrobný postup, jak tohoto úkolu dosáhnout. Pamatujte, že cvičení dělá mistra, proto experimentujte s různými možnostmi a nastaveními, abyste zjistili, co dalšího můžete s Aspose.Words dělat.

## Často kladené otázky

### Mohu stejnou metodou exportovat i jiné typy polí formuláře?

Ano, můžete exportovat i jiné typy polí formuláře konfigurací různých vlastností `HtmlSaveOptions` třída.

### Co když můj dokument obsahuje obrázky?

Obrázky budou uloženy do zadané složky obrázků. Ujistěte se, že jste nastavili `ImagesFolder` nemovitost v `HtmlSaveOptions`.

### Potřebuji licenci pro Aspose.Words?

Ano, můžete získat bezplatnou zkušební verzi [zde](https://releases.aspose.com/) nebo si zakoupit licenci [zde](https://purchase.aspose.com/buy).

### Mohu si exportovaný HTML kód upravit?

Rozhodně! Aspose.Words nabízí různé možnosti pro přizpůsobení HTML výstupu. Viz [dokumentace](https://reference.aspose.com/words/net/) pro více informací.

### Je Aspose.Words kompatibilní s .NET Core?

Ano, Aspose.Words je kompatibilní s .NET Core, .NET Framework a dalšími platformami .NET.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}