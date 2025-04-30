---
"description": "Naučte se, jak přidat text označený záložkou do dokumentu Wordu pomocí Aspose.Words pro .NET v tomto podrobném návodu. Ideální pro vývojáře."
"linktitle": "Přidat text označený záložkou v dokumentu Word"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Přidat text označený záložkou v dokumentu Word"
"url": "/cs/net/programming-with-bookmarks/append-bookmarked-text/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Přidat text označený záložkou v dokumentu Word

## Zavedení

Ahoj! Už jste někdy zkoušeli přidat text ze záložky v dokumentu Word a zjistili jste, že je to složité? Máte štěstí! Tento tutoriál vás provede celým procesem s Aspose.Words pro .NET. Rozdělíme si ho do jednoduchých kroků, abyste se v něm snadno orientovali. Pojďme se do toho pustit a přidat text ze záložek jako profesionál!

## Předpoklady

Než začneme, ujistěte se, že máte vše, co potřebujete:

- Aspose.Words pro .NET: Ujistěte se, že jej máte nainstalovaný. Pokud ne, můžete [stáhněte si to zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Jakékoli vývojové prostředí pro .NET, například Visual Studio.
- Základní znalost C#: Pochopení základních konceptů programování v C# bude užitečné.
- Dokument Wordu se záložkami: Dokument Wordu s nastavenými záložkami, ze kterých budeme přidávat text.

## Importovat jmenné prostory

Nejdříve si importujme potřebné jmenné prostory. Tím zajistíme, že budeme mít všechny potřebné nástroje po ruce.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Importing;
```

Rozeberme si příklad na podrobné kroky.

## Krok 1: Načtení dokumentu a inicializace proměnných

Dobře, začněme načtením našeho dokumentu Word a inicializací proměnných, které budeme potřebovat.

```csharp
// Načtěte zdrojové a cílové dokumenty.
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");

// Inicializujte importér dokumentů.
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);

// Vyhledejte záložku ve zdrojovém dokumentu.
Bookmark srcBookmark = srcDoc.Range.Bookmarks["YourBookmarkName"];
```

## Krok 2: Určete počáteční a koncový odstavec

Nyní si vyhledejme odstavce, kde záložka začíná a končí. To je klíčové, protože musíme s textem manipulovat v rámci těchto hranic.

```csharp
// Toto je odstavec, který obsahuje začátek záložky.
Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;

// Toto je odstavec, který obsahuje konec záložky.
Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

if (startPara == null || endPara == null)
    throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");
```

## Krok 3: Ověření rodičů odstavců

Musíme zajistit, aby počáteční a koncový odstavec měly stejného nadřazeného odstavce. Toto je jednoduchý scénář, který vše zjednoduší.

```csharp
// Omezme se na poměrně jednoduchý scénář.
if (startPara.ParentNode != endPara.ParentNode)
    throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");
```

## Krok 4: Identifikace uzlu k zastavení

Dále musíme určit uzel, kde ukončíme kopírování textu. Bude to uzel bezprostředně za koncovým odstavcem.

```csharp
// Chceme zkopírovat všechny odstavce od úvodního odstavce až po koncový odstavec (včetně).
// proto uzel, u kterého se zastavíme, je jeden za koncem odstavce.
Node endNode = endPara.NextSibling;
```

## Krok 5: Přidání textu záložkou do cílového dokumentu

Nakonec projdeme uzly od počátečního odstavce k uzlu za koncovým odstavcem a připojíme je do cílového dokumentu.

```csharp
for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
{
    // Tím se vytvoří kopie aktuálního uzlu a importuje se (učiní se platnou) v kontextu.
    // cílového dokumentu. Import znamená správné nastavení stylů a identifikátorů seznamů.
    Node newNode = importer.ImportNode(curNode, true);

    // Připojte importovaný uzel k cílovému dokumentu.
    dstDoc.FirstSection.Body.AppendChild(newNode);
}

// Uložte cílový dokument s připojeným textem.
dstDoc.Save("appended_document.docx");
```

## Závěr

tady to máte! Úspěšně jste přidali text ze záložky v dokumentu Wordu pomocí Aspose.Words pro .NET. Tento výkonný nástroj usnadňuje manipulaci s dokumenty a teď máte v rukávu další trik. Hodně štěstí s programováním!

## Často kladené otázky

### Mohu přidat text z více záložek najednou?
Ano, postup můžete opakovat pro každou záložku a podle toho doplnit text.

### Co když mají počáteční a koncový odstavec různé nadřazené odstavce?
V tomto příkladu se předpokládá, že mají stejného rodiče. Pro různé rodiče je vyžadována složitější manipulace.

### Mohu zachovat původní formátování připojeného textu?
Rozhodně! `ImportFormatMode.KeepSourceFormatting` zajišťuje zachování původního formátování.

### Je možné přidat text na určitou pozici v cílovém dokumentu?
Ano, text můžete přidat na libovolnou pozici tak, že přejdete na požadovaný uzel v cílovém dokumentu.

### Co když potřebuji přidat text ze záložky do nové sekce?
cílovém dokumentu můžete vytvořit novou sekci a text tam přidat.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}