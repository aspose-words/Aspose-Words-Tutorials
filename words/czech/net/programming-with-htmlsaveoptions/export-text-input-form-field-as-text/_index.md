---
title: Export textového vstupního pole formuláře jako text
linktitle: Export textového vstupního pole formuláře jako text
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se exportovat pole formuláře pro zadávání textu jako prostý text pomocí Aspose.Words for .NET pomocí tohoto komplexního průvodce krok za krokem.
weight: 10
url: /cs/net/programming-with-htmlsaveoptions/export-text-input-form-field-as-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Export textového vstupního pole formuláře jako text

## Zavedení

Takže se ponoříte do světa Aspose.Words pro .NET? Skvělá volba! Pokud se chcete naučit, jak exportovat pole formuláře pro zadávání textu jako text, jste na správném místě. Ať už teprve začínáte nebo si oprašujete své dovednosti, tento průvodce vás provede vším, co potřebujete vědět. Začněme, ano?

## Předpoklady

Než se pustíme do toho nejzákladnějšího, ujistěte se, že máte vše, co potřebujete, abyste mohli hladce postupovat:

-  Aspose.Words for .NET: Stáhněte si a nainstalujte nejnovější verzi z[zde](https://releases.aspose.com/words/net/).
- IDE: Visual Studio nebo jakékoli vývojové prostředí C#.
- Základní znalosti C#: Pochopení základní syntaxe C# a konceptů objektově orientovaného programování.
- Dokument: Ukázkový dokument aplikace Word (`Rendering.docx`) s poli formuláře pro zadávání textu.

## Importovat jmenné prostory

Nejprve musíte importovat potřebné jmenné prostory. Jsou to jako stavební kameny, díky nimž vše funguje bez problémů.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;
```

Dobře, teď, když máme naše jmenné prostory připravené, pojďme se vrhnout do akce!

## Krok 1: Nastavte projekt

Než se pustíme do kódu, ujistěte se, že je náš projekt správně nastaven.

## Vytvoření projektu

1. Otevřete Visual Studio: Začněte otevřením Visual Studia nebo vašeho preferovaného vývojového prostředí C#.
2.  Vytvořit nový projekt: Přejděte na`File > New > Project` . Vybrat`Console App (.NET Core)` nebo jakýkoli jiný relevantní typ projektu.
3.  Pojmenujte svůj projekt: Dejte svému projektu smysluplný název, něco jako`AsposeWordsExportExample`.

## Přidání Aspose.Words

1.  Správa balíčků NuGet: Klikněte pravým tlačítkem na svůj projekt v Průzkumníku řešení a vyberte`Manage NuGet Packages`.
2.  Hledat Aspose.Words: Ve Správci balíčků NuGet vyhledejte`Aspose.Words`.
3.  Instalace Aspose.Words: Klikněte na`Install` pro přidání knihovny Aspose.Words do vašeho projektu.

## Krok 2: Načtěte dokument aplikace Word

Nyní, když je náš projekt nastaven, načteme dokument aplikace Word, který obsahuje pole formuláře pro zadávání textu.

1. Zadejte adresář dokumentů: Definujte cestu k adresáři, kde je uložen váš dokument.
2.  Vložte dokument: Použijte`Document` třídy k načtení dokumentu aplikace Word.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

## Krok 3: Připravte exportní adresář

Před exportem se ujistěte, že je náš exportní adresář připraven. Zde se uloží náš soubor HTML a obrázky.

1. Definujte exportní adresář: Zadejte cestu, kam budou uloženy exportované soubory.
2. Zkontrolujte a vyčistěte adresář: Ujistěte se, že adresář existuje a je prázdný.

```csharp
string imagesDir = Path.Combine(dataDir, "Images");

if (Directory.Exists(imagesDir))
    Directory.Delete(imagesDir, true);

Directory.CreateDirectory(imagesDir);
```

## Krok 4: Nakonfigurujte možnosti uložení

Tady se děje kouzlo. Potřebujeme nastavit naše možnosti ukládání, abychom exportovali pole formuláře pro zadávání textu jako prostý text.

1.  Vytvořit možnosti uložení: Inicializace nového`HtmlSaveOptions` objekt.
2.  Nastavit možnost exportu textu: Nakonfigurujte`ExportTextInputFormFieldAsText`majetek do`true`.
3. Set Images Folder: Definujte složku, kam se budou snímky ukládat.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Html)
{
    ExportTextInputFormFieldAsText = true,
    ImagesFolder = imagesDir
};
```

## Krok 5: Uložte dokument jako HTML

Nakonec uložme dokument aplikace Word jako soubor HTML pomocí našich nakonfigurovaných možností uložení.

1. Definujte výstupní cestu: Zadejte cestu, kam bude soubor HTML uložen.
2.  Uložit dokument: Použijte`Save` metoda`Document`třídy pro export dokumentu.

```csharp
doc.Save(dataDir + "ExportedDocument.html", saveOptions);
```

## Závěr

A tady to máte! Úspěšně jste exportovali pole formuláře pro zadávání textu jako prostý text pomocí Aspose.Words for .NET. Tato příručka by vám měla poskytnout jasný postup krok za krokem k dosažení tohoto úkolu. Pamatujte, že praxe dělá mistra, takže pokračujte v experimentování s různými možnostmi a nastaveními, abyste zjistili, co dalšího můžete s Aspose.Words dělat.

## FAQ

### Mohu pomocí stejné metody exportovat jiné typy polí formuláře?

 Ano, můžete exportovat jiné typy polí formuláře nakonfigurováním různých vlastností souboru`HtmlSaveOptions` třída.

### Co když můj dokument obsahuje obrázky?

 Snímky se uloží do určené složky obrázků. Ujistěte se, že jste nastavili`ImagesFolder` nemovitost v`HtmlSaveOptions`.

### Potřebuji licenci pro Aspose.Words?

 Ano, můžete získat bezplatnou zkušební verzi[zde](https://releases.aspose.com/) nebo zakoupit licenci[zde](https://purchase.aspose.com/buy).

### Mohu upravit exportovaný HTML?

 Absolutně! Aspose.Words poskytuje různé možnosti přizpůsobení výstupu HTML. Viz[dokumentace](https://reference.aspose.com/words/net/) pro více podrobností.

### Je Aspose.Words kompatibilní s .NET Core?

Ano, Aspose.Words je kompatibilní s .NET Core, .NET Framework a dalšími platformami .NET.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
