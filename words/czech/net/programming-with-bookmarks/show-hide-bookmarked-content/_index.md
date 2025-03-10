---
title: Zobrazit skrýt obsah označený záložkou v dokumentu aplikace Word
linktitle: Zobrazit skrýt obsah označený záložkou v dokumentu aplikace Word
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak zobrazit a skrýt obsah se záložkami v dokumentech aplikace Word pomocí Aspose.Words for .NET pomocí tohoto podrobného průvodce krok za krokem.
weight: 10
url: /cs/net/programming-with-bookmarks/show-hide-bookmarked-content/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zobrazit skrýt obsah označený záložkou v dokumentu aplikace Word

## Zavedení

Jste připraveni ponořit se do světa manipulace s dokumenty s Aspose.Words pro .NET? Ať už jste vývojář, který chce automatizovat úlohy s dokumenty, nebo jen někdo, kdo se zajímá o práci se soubory Wordu programově, jste na správném místě. Dnes prozkoumáme, jak zobrazit a skrýt obsah označený záložkou v dokumentu aplikace Word pomocí Aspose.Words for .NET. Tento podrobný průvodce z vás udělá profesionála v ovládání viditelnosti obsahu na základě záložek. Začněme!

## Předpoklady

Než se vrhneme na to, co je v pořádku, je několik věcí, které budete potřebovat:

1. Visual Studio: Jakákoli verze kompatibilní s .NET.
2.  Aspose.Words pro .NET: Stáhněte si ji[zde](https://releases.aspose.com/words/net/).
3. Základní porozumění C#: Pokud umíte napsat jednoduchý program „Hello World“, můžete začít.
4. Dokument aplikace Word se záložkami: Pro tento výukový program použijeme vzorový dokument se záložkami.

## Importovat jmenné prostory

Nejprve importujme potřebné jmenné prostory. To zajišťuje, že máme všechny nástroje, které pro náš úkol potřebujeme.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

těmito jmennými prostory na místě jsme všichni připraveni vyrazit na cestu.

## Krok 1: Nastavení vašeho projektu

Dobře, začněme tím, že náš projekt nastavíme ve Visual Studiu.

### Vytvořit nový projekt

Otevřete Visual Studio a vytvořte nový projekt Console App (.NET Core). Pojmenujte to nějak chytlavě, například „BookmarkVisibilityManager“.

### Přidejte Aspose.Words pro .NET

Do projektu budete muset přidat Aspose.Words for .NET. Můžete to udělat pomocí Správce balíčků NuGet.

1. Přejděte na Nástroje > Správce balíčků NuGet > Spravovat balíčky NuGet pro řešení.
2. Vyhledejte "Aspose.Words".
3. Nainstalujte balíček.

Velký! Nyní, když je náš projekt nastaven, přejděme k načítání našeho dokumentu.

## Krok 2: Vložení dokumentu

Musíme načíst dokument aplikace Word, který obsahuje záložky. Pro tento tutoriál použijeme vzorový dokument s názvem „Bookmarks.docx“.

```csharp
// Cesta k adresáři dokumentů.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

 Tento fragment kódu nastaví cestu k adresáři vašeho dokumentu a načte dokument do`doc` objekt.

## Krok 3: Zobrazit/skrýt obsah označený záložkou

Nyní přichází ta zábavná část – zobrazení nebo skrytí obsahu na základě záložek. Vytvoříme metodu tzv`ShowHideBookmarkedContent` zvládnout tohle.

Zde je metoda, která přepne viditelnost obsahu v záložkách:

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

### Rozdělení metody

-  Načítání záložek:`Bookmark bm = doc.Range.Bookmarks[bookmarkName];` načte záložku.
- Procházení uzlem: Procházíme uzly v záložce.
-  Přepínač viditelnosti: Pokud je uzel a`Run` (souvislý běh textu), nastavíme jeho`Hidden` vlastnictví.

## Krok 4: Použití metody

S naší metodou ji použijte k zobrazení nebo skrytí obsahu založeného na záložce.

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true);
```

Tento řádek kódu skryje obsah v záložce s názvem „MyBookmark1“.

## Krok 5: Uložení dokumentu

Nakonec náš upravený dokument uložíme.

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

Tím se dokument uloží se změnami, které jsme provedli.

## Závěr

tady to máte! Právě jste se naučili, jak zobrazit a skrýt obsah se záložkami v dokumentu aplikace Word pomocí Aspose.Words for .NET. Díky tomuto výkonnému nástroji je manipulace s dokumenty hračkou, ať už automatizujete sestavy, vytváříte šablony nebo si jen hrajete se soubory aplikace Word. Šťastné kódování!

## FAQ

### Mohu přepnout více záložek najednou?
 Ano, můžete zavolat na`ShowHideBookmarkedContent` pro každou záložku, kterou chcete přepnout.

### Ovlivňuje skrytí obsahu strukturu dokumentu?
Ne, skrytí obsahu ovlivní pouze jeho viditelnost. Obsah zůstává v dokumentu.

### Mohu tuto metodu použít pro jiné typy obsahu?
Tato metoda konkrétně přepíná spouštění textu. U ostatních typů obsahu budete muset upravit logiku procházení uzlu.

### Je Aspose.Words for .NET zdarma?
 Aspose.Words nabízí bezplatnou zkušební verzi[zde](https://releases.aspose.com/) , ale pro produkční použití je vyžadována plná licence. Můžete si jej zakoupit[zde](https://purchase.aspose.com/buy).

### Jak mohu získat podporu, pokud narazím na problémy?
 Můžete získat podporu od komunity Aspose[zde](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
