---
"description": "Naučte se, jak zobrazit a skrýt obsah záložek v dokumentech Word pomocí Aspose.Words pro .NET s tímto podrobným návodem krok za krokem."
"linktitle": "Zobrazit/skrýt obsah uložený v záložkách v dokumentu Word"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Zobrazit/skrýt obsah uložený v záložkách v dokumentu Word"
"url": "/cs/net/programming-with-bookmarks/show-hide-bookmarked-content/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Zobrazit/skrýt obsah uložený v záložkách v dokumentu Word

## Zavedení

Jste připraveni ponořit se do světa manipulace s dokumenty s Aspose.Words pro .NET? Ať už jste vývojář, který chce automatizovat úlohy s dokumenty, nebo se jen zajímáte o programovou práci se soubory Wordu, jste na správném místě. Dnes se podíváme na to, jak zobrazit a skrýt obsah označený záložkami v dokumentu Wordu pomocí Aspose.Words pro .NET. Tento podrobný návod z vás udělá profesionála v ovládání viditelnosti obsahu na základě záložek. Pojďme na to!

## Předpoklady

Než se pustíme do detailů, je tu pár věcí, které budete potřebovat:

1. Visual Studio: Jakákoli verze kompatibilní s .NET.
2. Aspose.Words pro .NET: Stáhněte si jej [zde](https://releases.aspose.com/words/net/).
3. Základní znalost C#: Pokud umíte napsat jednoduchý program typu „Hello World“, můžete začít.
4. Dokument Word se záložkami: V tomto tutoriálu použijeme vzorový dokument se záložkami.

## Importovat jmenné prostory

Nejdříve si importujme potřebné jmenné prostory. Tím zajistíme, že budeme mít všechny nástroje, které pro náš úkol potřebujeme.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

S těmito jmennými prostory na místě jsme připraveni vydat se na naši cestu.

## Krok 1: Nastavení projektu

Dobře, začněme nastavením našeho projektu ve Visual Studiu.

### Vytvořit nový projekt

Otevřete Visual Studio a vytvořte nový projekt konzolové aplikace (.NET Core). Pojmenujte ho nějak chytlavě, například „BookmarkVisibilityManager“.

### Přidat Aspose.Words pro .NET

Do projektu budete muset přidat Aspose.Words pro .NET. Můžete to udělat pomocí Správce balíčků NuGet.

1. Přejděte do nabídky Nástroje > Správce balíčků NuGet > Spravovat balíčky NuGet pro řešení.
2. Hledat „Aspose.Words“.
3. Nainstalujte balíček.

Skvělé! Nyní, když je náš projekt nastavený, pojďme k načtení našeho dokumentu.

## Krok 2: Načtení dokumentu

Potřebujeme načíst dokument Wordu, který obsahuje záložky. V tomto tutoriálu použijeme vzorový dokument s názvem „Bookmarks.docx“.

```csharp
// Cesta k adresáři s dokumenty.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

Tento úryvek kódu nastaví cestu k adresáři s dokumenty a načte dokument do `doc` objekt.

## Krok 3: Zobrazit/skrýt obsah uložený v záložkách

A teď přichází ta zábavná část – zobrazení nebo skrytí obsahu na základě záložek. Vytvoříme metodu s názvem `ShowHideBookmarkedContent` aby to zvládl/a.

Zde je metoda, která přepne viditelnost obsahu uloženého v záložkách:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool isHidden)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    Node currentNode = bm.BookmarkStart;
    while (currentNode != null && currentNode.NodeType != NodeType.BookmarkEnd)
    {
        if (currentNode.NodeType == NodeType.Run)
        {
            Run run = currentNode as Run;
            run.Font.Hidden = isHidden;
        }
        currentNode = currentNode.NextSibling;
    }
}
```

### Rozklad metody

- Vyhledávání záložek: `Bookmark bm = doc.Range.Bookmarks[bookmarkName];` načte záložku.
- Průchod uzlem: Procházíme uzly v záložce.
- Přepínač viditelnosti: Pokud je uzel `Run` (souvislý sled textu), nastavíme jeho `Hidden` vlastnictví.

## Krok 4: Použití metody

naší metodou na místě ji aplikujme k zobrazení nebo skrytí obsahu na základě záložky.

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true);
```

Tento řádek kódu skryje obsah v záložce s názvem „MyBookmark1“.

## Krok 5: Uložení dokumentu

Nakonec si uložme upravený dokument.

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

Tím se dokument uloží s provedenými změnami.

## Závěr

A tady to máte! Právě jste se naučili, jak zobrazit a skrýt obsah záložek v dokumentu Word pomocí Aspose.Words pro .NET. Tento výkonný nástroj usnadňuje manipulaci s dokumenty, ať už automatizujete sestavy, vytváříte šablony nebo si jen hrajete se soubory Wordu. Přejeme vám příjemné programování!

## Často kladené otázky

### Mohu přepínat více záložek najednou?
Ano, můžete zavolat na `ShowHideBookmarkedContent` pro každou záložku, kterou chcete přepnout.

### Ovlivňuje skrytí obsahu strukturu dokumentu?
Ne, skrytí obsahu ovlivní pouze jeho viditelnost. Obsah v dokumentu zůstává.

### Mohu tuto metodu použít i pro jiné typy obsahu?
Tato metoda konkrétně přepíná průchod textu. Pro ostatní typy obsahu budete muset upravit logiku procházení uzlů.

### Je Aspose.Words pro .NET zdarma?
Aspose.Words nabízí bezplatnou zkušební verzi [zde](https://releases.aspose.com/), ale pro produkční použití je vyžadována plná licence. Můžete si ji zakoupit [zde](https://purchase.aspose.com/buy).

### Jak mohu získat podporu, pokud narazím na problémy?
Podporu můžete získat od komunity Aspose [zde](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}