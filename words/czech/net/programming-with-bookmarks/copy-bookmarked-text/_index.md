---
"description": "Snadno kopírujte text označený záložkami mezi dokumenty Wordu pomocí Aspose.Words pro .NET. Naučte se, jak na to, s tímto podrobným návodem."
"linktitle": "Kopírování textu označeného záložkou v dokumentu Word"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Kopírování textu označeného záložkou v dokumentu Word"
"url": "/cs/net/programming-with-bookmarks/copy-bookmarked-text/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Kopírování textu označeného záložkou v dokumentu Word

## Zavedení

Už jste někdy zjistili, že potřebujete kopírovat určité části z jednoho dokumentu Wordu do druhého? Máte štěstí! V tomto tutoriálu si ukážeme, jak kopírovat text označený záložkou z jednoho dokumentu Wordu do druhého pomocí Aspose.Words pro .NET. Ať už vytváříte dynamickou sestavu nebo automatizujete generování dokumentů, tento průvodce vám celý proces zjednoduší.

## Předpoklady

Než se do toho pustíme, ujistěte se, že máte následující:

- Knihovna Aspose.Words pro .NET: Můžete si ji stáhnout z [zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Visual Studio nebo jakékoli jiné vývojové prostředí pro .NET.
- Základní znalost C#: Znalost programování v C# a frameworku .NET.

## Importovat jmenné prostory

Pro začátek se ujistěte, že máte v projektu importovány potřebné jmenné prostory:

```csharp
using Aspose.Words;
using Aspose.Words.Import;
using Aspose.Words.Bookmark;
```

## Krok 1: Načtení zdrojového dokumentu

Nejdříve je potřeba načíst zdrojový dokument, který obsahuje text označený záložkou, který chcete kopírovat.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Bookmarks.docx");
```

Zde, `dataDir` je cesta k adresáři s vašimi dokumenty a `Bookmarks.docx` je zdrojový dokument.

## Krok 2: Identifikace záložky

Dále určete záložku, kterou chcete zkopírovat ze zdrojového dokumentu.

```csharp
Bookmark srcBookmark = srcDoc.Range.Bookmarks["MyBookmark1"];
```

Nahradit `"MyBookmark1"` se skutečným názvem vaší záložky.

## Krok 3: Vytvořte cílový dokument

Nyní vytvořte nový dokument, kam bude zkopírován text označený záložkou.

```csharp
Document dstDoc = new Document();
CompositeNode dstNode = dstDoc.LastSection.Body;
```

## Krok 4: Importujte obsah označený záložkami

Chcete-li zajistit zachování stylů a formátování, použijte `NodeImporter` importovat obsah označený záložkou ze zdrojového dokumentu do cílového dokumentu.

```csharp
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);
AppendBookmarkedText(importer, srcBookmark, dstNode);
```

## Krok 5: Definování metody AppendBookmarkedText

A tady se začne dít ta pravá magie. Definujte metodu pro kopírování textu označeného záložkou:

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

## Krok 6: Uložení cílového dokumentu

Nakonec uložte cílový dokument, abyste ověřili zkopírovaný obsah.

```csharp
dstDoc.Save(dataDir + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

## Závěr

to je vše! Úspěšně jste zkopírovali text označený záložkou z jednoho dokumentu Wordu do druhého pomocí Aspose.Words pro .NET. Tato metoda je účinná pro automatizaci úloh manipulace s dokumenty, čímž zefektivňuje a zjednodušuje váš pracovní postup.

## Často kladené otázky

### Mohu kopírovat více záložek najednou?
Ano, můžete procházet více záložek a každou z nich zkopírovat stejnou metodou.

### Co se stane, když se záložka nenajde?
Ten/Ta/To `Range.Bookmarks` majetek se vrátí `null`, proto se ujistěte, že tento případ řešíte, abyste se vyhnuli výjimkám.

### Mohu zachovat formátování původní záložky?
Rozhodně! Používání `ImportFormatMode.KeepSourceFormatting` zajišťuje zachování původního formátování.

### Existuje omezení velikosti textu v záložkách?
Neexistuje žádný konkrétní limit, ale výkon se může u extrémně velkých dokumentů lišit.

### Mohu kopírovat text mezi různými formáty dokumentů Wordu?
Ano, Aspose.Words podporuje různé formáty Wordu a metoda funguje napříč těmito formáty.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}