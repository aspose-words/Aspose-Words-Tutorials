---
title: Nastavte složku obrázků
linktitle: Nastavte složku obrázků
second_title: Aspose.Words API pro zpracování dokumentů
description: Převeďte dokumenty aplikace Word do formátu Markdown se správným zarovnáním tabulek pomocí Aspose.Words for .NET. Pro dokonalé výsledky postupujte podle našeho podrobného průvodce.
weight: 10
url: /cs/net/programming-with-markdownsaveoptions/set-images-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nastavte složku obrázků

## Zavedení

Chtěli jste někdy exportovat dokument aplikace Word do formátu Markdown a zároveň zajistit, aby byly tabulky a obsah dokonale zarovnány? Aspose.Words for .NET je vaším řešením pro tento úkol. V tomto článku vás provedeme procesem nastavení Aspose.Words, přípravou dokumentu a jeho exportem do Markdown se správným zarovnáním obsahu tabulky. Každý krok rozebereme, aby se dal snadno sledovat a pochopit. Pojďme se tedy ponořit a přeměnit vaše dokumenty Wordu na krásně zarovnané soubory Markdown!

## Předpoklady

Než začneme, ujistěte se, že máte následující:

-  Aspose.Words for .NET: Můžete si ji stáhnout[zde](https://releases.aspose.com/words/net/).
-  Platná licence: Získejte bezplatnou zkušební verzi[zde](https://releases.aspose.com/) nebo dočasnou licenci[zde](https://purchase.aspose.com/temporary-license/).
- Visual Studio: Nebo jakékoli jiné IDE, které podporuje vývoj .NET.
- Základní znalost C#: Pochopení programovacího jazyka C#.

## Importovat jmenné prostory

Chcete-li začít, budete muset importovat potřebné jmenné prostory do svého projektu C#. Tyto jmenné prostory vám umožní přístup k funkcím Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;
```

## Krok 1: Nastavte svůj projekt

Nejprve nastavte svůj .NET projekt ve vašem IDE. Vytvořte novou konzolovou aplikaci a přidejte odkaz na Aspose.Words for .NET.

### 1.1 Vytvořte nový projekt

Otevřete Visual Studio a vytvořte nový projekt aplikace konzoly. Pojmenujte to "MarkdownExporter" nebo něco podobného.

### 1.2 Přidat odkaz Aspose.Words

 Chcete-li přidat Aspose.Words do svého projektu, můžete si stáhnout DLL z[Aspose webové stránky](https://releases.aspose.com/words/net/) a přidejte jej ručně nebo použijte NuGet Package Manager:

```bash
Install-Package Aspose.Words
```

## Krok 2: Napište kód pro export jako Markdown

Nyní napíšeme kód pro čtení dokumentu aplikace Word a uložíme jej jako soubor Markdown se správným zarovnáním tabulky.

### 2.1 Definujte cestu k vašemu dokumentu

Nastavte cestu k dokumentu aplikace Word a složku, kam chcete obrázky uložit.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
```

### 2.2 Vložte dokument

Načtěte dokument aplikace Word pomocí Aspose.Words.

```csharp
Document doc = new Document(dataDir + "Image bullet points.docx");
```

### 2.3 Konfigurace možností uložení Markdown

 Nakonfigurujte`MarkdownSaveOptions` určit, kam mají být obrázky uloženy.

```csharp
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    ImagesFolder = dataDir + "Images"
};
```

### 2.4 Uložte dokument jako Markdown

 Použijte a`MemoryStream` pro uložení dokumentu ve formátu Markdown.

```csharp
using (MemoryStream stream = new MemoryStream())
{
    doc.Save(stream, saveOptions);
}
```

## Závěr

Export dokumentu Word do Markdown se zarovnáním obsahu tabulky pomocí Aspose.Words for .NET je jednoduchý, když budete postupovat podle těchto kroků. Pomocí několika řádků kódu můžete automatizovat proces převodu a zajistit, aby byl váš obsah dobře naformátován. Nyní můžete snadno sdílet své dokumenty ve formátu Markdown s vědomím, že budou vypadat skvěle a zachovají si svou strukturu.

## FAQ

### Mohu používat Aspose.Words pro .NET s jinými programovacími jazyky?

Ano, Aspose.Words for .NET lze použít s jakýmkoli jazykem kompatibilním s .NET, jako je VB.NET, F# a další.

### Jak získám dočasnou licenci pro Aspose.Words?

Můžete získat dočasnou licenci[zde](https://purchase.aspose.com/temporary-license/).

### Jaké typy dokumentů mohu převést na Markdown?

Můžete převádět různé dokumenty aplikace Word včetně .doc, .docx, .rtf a dalších.

### Existují nějaká omezení ve zkušební verzi Aspose.Words?

Zkušební verze má určitá omezení, jako jsou vodoznaky ve výstupních souborech. Můžete získat bezplatnou zkušební verzi[zde](https://releases.aspose.com/).

### Kde najdu další příklady a dokumentaci pro Aspose.Words?

 Podrobnou dokumentaci a příklady naleznete na[Aspose webové stránky](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
