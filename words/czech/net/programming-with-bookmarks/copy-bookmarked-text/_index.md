---
title: Kopírovat text se záložkou v dokumentu aplikace Word
linktitle: Kopírovat text se záložkou v dokumentu aplikace Word
second_title: Aspose.Words API pro zpracování dokumentů
description: Bez námahy zkopírujte text označený záložkou mezi dokumenty aplikace Word pomocí Aspose.Words pro .NET. Naučte se, jak na to, pomocí tohoto podrobného průvodce.
weight: 10
url: /cs/net/programming-with-bookmarks/copy-bookmarked-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kopírovat text se záložkou v dokumentu aplikace Word

## Zavedení

Přistihli jste se někdy, že potřebujete zkopírovat konkrétní části z jednoho dokumentu aplikace Word do druhého? Tak to máš štěstí! V tomto tutoriálu vás provedeme tím, jak zkopírovat text se záložkou z jednoho dokumentu aplikace Word do druhého pomocí Aspose.Words for .NET. Ať už vytváříte dynamickou sestavu nebo automatizujete generování dokumentů, tato příručka vám celý proces zjednoduší.

## Předpoklady

Než se ponoříme, ujistěte se, že máte následující:

-  Aspose.Words for .NET Library: Můžete si ji stáhnout z[zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Visual Studio nebo jakékoli jiné vývojové prostředí .NET.
- Základní znalost C#: Znalost programování v C# a .NET frameworku.

## Importovat jmenné prostory

Chcete-li začít, ujistěte se, že máte do projektu importované potřebné jmenné prostory:

```csharp
using Aspose.Words;
using Aspose.Words.Import;
using Aspose.Words.Bookmark;
```

## Krok 1: Načtěte zdrojový dokument

Nejprve musíte načíst zdrojový dokument, který obsahuje text označený záložkou, který chcete zkopírovat.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Bookmarks.docx");
```

 Zde,`dataDir` je cesta k vašemu adresáři dokumentů a`Bookmarks.docx` je zdrojový dokument.

## Krok 2: Identifikujte záložku

Dále identifikujte záložku, kterou chcete zkopírovat ze zdrojového dokumentu.

```csharp
Bookmark srcBookmark = srcDoc.Range.Bookmarks["MyBookmark1"];
```

 Nahradit`"MyBookmark1"` se skutečným názvem vaší záložky.

## Krok 3: Vytvořte cílový dokument

Nyní vytvořte nový dokument, do kterého bude zkopírován text označený záložkou.

```csharp
Document dstDoc = new Document();
CompositeNode dstNode = dstDoc.LastSection.Body;
```

## Krok 4: Importujte obsah se záložkami

 Chcete-li zajistit zachování stylů a formátování, použijte`NodeImporter` pro import obsahu označeného záložkou ze zdrojového dokumentu do cílového dokumentu.

```csharp
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);
AppendBookmarkedText(importer, srcBookmark, dstNode);
```

## Krok 5: Definujte metodu AppendBookmarkedText

Tady se děje kouzlo. Definujte metodu pro zpracování kopírování textu označeného záložkou:

```csharp
private void AppendBookmarkedText(NodeImporter importer, Bookmark srcBookmark, CompositeNode dstNode)
{
    Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;
    Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

    if (startPara == null || endPara == null)
        throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");

    if (startPara.ParentNode != endPara.ParentNode)
        throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");

    Node endNode = endPara.NextSibling;

    for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
    {
        Node newNode = importer.ImportNode(curNode, true);
        dstNode.AppendChild(newNode);
    }
}
```

## Krok 6: Uložte cílový dokument

Nakonec uložte cílový dokument, abyste ověřili zkopírovaný obsah.

```csharp
dstDoc.Save(dataDir + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

## Závěr

A je to! Úspěšně jste zkopírovali text označený záložkou z jednoho dokumentu aplikace Word do druhého pomocí Aspose.Words for .NET. Tato metoda je výkonná pro automatizaci úloh manipulace s dokumenty, díky čemuž je váš pracovní postup efektivnější a efektivnější.

## FAQ

### Mohu kopírovat více záložek najednou?
Ano, můžete iterovat přes více záložek a použít stejnou metodu ke zkopírování každé z nich.

### Co se stane, když záložka nebude nalezena?
 The`Range.Bookmarks` majetek se vrátí`null`, takže se ujistěte, že tento případ řešíte, abyste se vyhnuli výjimkám.

### Mohu zachovat formátování původní záložky?
 Absolutně! Použití`ImportFormatMode.KeepSourceFormatting` zajišťuje zachování původního formátování.

### Existuje omezení velikosti textu označeného záložkou?
Neexistuje žádný konkrétní limit, ale výkon se může u extrémně velkých dokumentů lišit.

### Mohu kopírovat text mezi různými formáty dokumentů aplikace Word?
Ano, Aspose.Words podporuje různé formáty Wordu a metoda funguje napříč těmito formáty.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
