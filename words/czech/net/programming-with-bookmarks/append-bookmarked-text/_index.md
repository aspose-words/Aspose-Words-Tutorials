---
title: Přidat text se záložkou v dokumentu aplikace Word
linktitle: Přidat text se záložkou v dokumentu aplikace Word
second_title: Aspose.Words API pro zpracování dokumentů
description: V tomto podrobném průvodci se dozvíte, jak přidat text se záložkou do dokumentu aplikace Word pomocí Aspose.Words for .NET. Ideální pro vývojáře.
weight: 10
url: /cs/net/programming-with-bookmarks/append-bookmarked-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Přidat text se záložkou v dokumentu aplikace Word

## Zavedení

Ahoj! Zkoušeli jste někdy přidat text z části označené záložkou v dokumentu aplikace Word a přišlo vám to složité? Máte štěstí! Tento tutoriál vás provede procesem pomocí Aspose.Words pro .NET. Rozdělíme to do jednoduchých kroků, abyste je mohli snadno sledovat. Ponořme se do toho a připojme tento text se záložkou jako profesionál!

## Předpoklady

Než začneme, ujistěte se, že máte vše, co potřebujete:

-  Aspose.Words for .NET: Ujistěte se, že jej máte nainstalovaný. Pokud ne, můžete[stáhněte si to zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Jakékoli vývojové prostředí .NET, jako je Visual Studio.
- Základní znalost C#: Pomůže vám pochopení základních pojmů programování v C#.
- Dokument aplikace Word se záložkami: Dokument aplikace Word s nastavenými záložkami, které použijeme k připojení textu.

## Importovat jmenné prostory

Nejprve importujme potřebné jmenné prostory. Díky tomu budeme mít všechny nástroje, které potřebujeme, na dosah ruky.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Importing;
```

Rozdělme si příklad na podrobné kroky.

## Krok 1: Načtěte dokument a inicializujte proměnné

Dobře, začněme načtením našeho dokumentu Word a inicializací proměnných, které budeme potřebovat.

```csharp
// Načtěte zdrojové a cílové dokumenty.
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");

// Inicializujte importér dokumentů.
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);

// Najděte záložku ve zdrojovém dokumentu.
Bookmark srcBookmark = srcDoc.Range.Bookmarks["YourBookmarkName"];
```

## Krok 2: Identifikujte počáteční a koncový odstavec

Nyní najdeme odstavce, kde začíná a končí záložka. To je zásadní, protože musíme s textem zacházet v těchto mezích.

```csharp
// Toto je odstavec, který obsahuje začátek záložky.
Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;

// Toto je odstavec, který obsahuje konec záložky.
Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

if (startPara == null || endPara == null)
    throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");
```

## Krok 3: Ověřte rodiče odstavce

Musíme zajistit, aby počáteční a koncové odstavce měly stejného rodiče. Toto je jednoduchý scénář, aby věci zůstaly přímočaré.

```csharp
// Omezte se na přiměřeně jednoduchý scénář.
if (startPara.ParentNode != endPara.ParentNode)
    throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");
```

## Krok 4: Identifikujte uzel, který chcete zastavit

Dále musíme určit uzel, kde přestaneme kopírovat text. Toto bude uzel bezprostředně za koncovým odstavcem.

```csharp
// Chceme zkopírovat všechny odstavce od počátečního odstavce až po (včetně) koncového odstavce,
// proto uzel, u kterého zastavíme, je jeden za koncovým odstavcem.
Node endNode = endPara.NextSibling;
```

## Krok 5: Přidejte text označený záložkou k cílovému dokumentu

Nakonec projdeme uzly od počátečního odstavce k uzlu za koncovým odstavcem a připojíme je k cílovému dokumentu.

```csharp
for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
{
    // Tím se vytvoří kopie aktuálního uzlu a importuje se (učiní se platným) v kontextu
    // cílového dokumentu. Import znamená správnou úpravu stylů a identifikátorů seznamu.
    Node newNode = importer.ImportNode(curNode, true);

    // Připojte importovaný uzel k cílovému dokumentu.
    dstDoc.FirstSection.Body.AppendChild(newNode);
}

// Uložte cílový dokument s připojeným textem.
dstDoc.Save("appended_document.docx");
```

## Závěr

A tady to máte! Úspěšně jste přidali text ze sekce se záložkou v dokumentu aplikace Word pomocí Aspose.Words for .NET. Díky tomuto mocnému nástroji je manipulace s dokumenty hračkou a nyní máte v rukávu ještě jeden trik. Šťastné kódování!

## FAQ

### Mohu přidat text z více záložek najednou?
Ano, postup můžete opakovat pro každou záložku a podle toho přidat text.

### Co když mají počáteční a koncové odstavce různé rodiče?
Aktuální příklad předpokládá, že mají stejného rodiče. U různých rodičů je nutná složitější manipulace.

### Mohu zachovat původní formátování připojeného textu?
 Absolutně! The`ImportFormatMode.KeepSourceFormatting` zajišťuje zachování původního formátování.

### Je možné připojit text na konkrétní pozici v cílovém dokumentu?
Ano, text můžete připojit na libovolné místo tak, že přejdete na požadovaný uzel v cílovém dokumentu.

### Co když potřebuji přidat text ze záložky do nové sekce?
V cílovém dokumentu můžete vytvořit novou sekci a přidat tam text.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
