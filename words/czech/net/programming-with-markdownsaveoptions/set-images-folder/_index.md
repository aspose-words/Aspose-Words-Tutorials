---
"description": "Převeďte dokumenty Wordu do Markdownu se správným zarovnáním tabulek pomocí Aspose.Words pro .NET. Pro perfektní výsledky se řiďte naším podrobným návodem."
"linktitle": "Nastavit složku s obrázky"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Nastavit složku s obrázky"
"url": "/cs/net/programming-with-markdownsaveoptions/set-images-folder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Nastavit složku s obrázky

## Zavedení

Chtěli jste někdy exportovat dokument Word do formátu Markdown a zároveň zajistit, aby se tabulky a obsah dokonale zarovnaly? Aspose.Words pro .NET je pro tento úkol ideálním řešením. V tomto článku vás provedeme procesem nastavení Aspose.Words, přípravy dokumentu a jeho exportu do Markdownu se správným zarovnáním obsahu tabulek. Rozebereme si jednotlivé kroky, aby byly snadno sledovatelné a pochopené. Pojďme se tedy do toho pustit a transformovat vaše dokumenty Word do krásně zarovnaných souborů Markdown!

## Předpoklady

Než začneme, ujistěte se, že máte následující:

- Aspose.Words pro .NET: Můžete si ho stáhnout [zde](https://releases.aspose.com/words/net/).
- Platná licence: Získejte bezplatnou zkušební verzi [zde](https://releases.aspose.com/) nebo dočasné povolení [zde](https://purchase.aspose.com/temporary-license/).
- Visual Studio: Nebo jakékoli jiné IDE, které podporuje vývoj v .NET.
- Základní znalost C#: Znalost programovacího jazyka C#.

## Importovat jmenné prostory

Pro začátek budete muset do svého projektu v C# importovat potřebné jmenné prostory. Tyto jmenné prostory vám umožní přístup k funkcím Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;
```

## Krok 1: Nastavení projektu

Nejdříve si v IDE nastavte projekt .NET. Vytvořte novou konzolovou aplikaci a přidejte odkaz na Aspose.Words pro .NET.

### 1.1 Vytvoření nového projektu

Otevřete Visual Studio a vytvořte nový projekt konzolové aplikace. Pojmenujte ho „MarkdownExporter“ nebo něco podobného.

### 1.2 Přidání reference Aspose.Words

Chcete-li do projektu přidat Aspose.Words, můžete si buď stáhnout DLL z [Webové stránky Aspose](https://releases.aspose.com/words/net/) a přidejte jej ručně nebo použijte Správce balíčků NuGet:

```bash
Install-Package Aspose.Words
```

## Krok 2: Napište kód pro export jako Markdown

Nyní si napišme kód pro čtení dokumentu Wordu a jeho uložení jako souboru Markdown se správným zarovnáním tabulek.

### 2.1 Definování cesty k dokumentu

Nastavte cestu k dokumentu Wordu a složku, kam chcete ukládat obrázky.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
```

### 2.2 Vložení dokumentu

Načtěte dokument Wordu pomocí Aspose.Words.

```csharp
Document doc = new Document(dataDir + "Image bullet points.docx");
```

### 2.3 Konfigurace možností ukládání v Markdownu

Nakonfigurujte `MarkdownSaveOptions` určit, kam mají být obrázky uloženy.

```csharp
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    ImagesFolder = dataDir + "Images"
};
```

### 2.4 Uložení dokumentu ve formátu Markdown

Použijte `MemoryStream` uložit dokument ve formátu Markdown.

```csharp
using (MemoryStream stream = new MemoryStream())
{
    doc.Save(stream, saveOptions);
}
```

## Závěr

Export dokumentu Word do Markdownu se zarovnáním obsahu tabulky pomocí Aspose.Words pro .NET je po provedení těchto kroků jednoduchý. Pomocí několika řádků kódu můžete proces převodu automatizovat a zajistit, aby byl váš obsah správně naformátován. Nyní můžete snadno sdílet své dokumenty ve formátu Markdown s vědomím, že budou vypadat skvěle a zachovají si svou strukturu.

## Často kladené otázky

### Mohu používat Aspose.Words pro .NET s jinými programovacími jazyky?

Ano, Aspose.Words pro .NET lze použít s jakýmkoli jazykem kompatibilním s .NET, jako je VB.NET, F# a další.

### Jak získám dočasnou licenci pro Aspose.Words?

Můžete získat dočasnou licenci [zde](https://purchase.aspose.com/temporary-license/).

### Jaké typy dokumentů mohu převést do formátu Markdown?

Můžete převádět různé dokumenty aplikace Word, včetně formátů .doc, .docx, .rtf a dalších.

### Existují nějaká omezení zkušební verze Aspose.Words?

Zkušební verze má určitá omezení, jako například vodoznaky ve výstupních souborech. Můžete si ji zdarma vyzkoušet. [zde](https://releases.aspose.com/).

### Kde najdu další příklady a dokumentaci k Aspose.Words?

Podrobnou dokumentaci a příklady naleznete na [Webové stránky Aspose](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}