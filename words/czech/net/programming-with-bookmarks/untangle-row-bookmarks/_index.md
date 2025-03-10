---
title: Rozmotat záložky řádků v dokumentu aplikace Word
linktitle: Rozmotat záložky řádků v dokumentu aplikace Word
second_title: Aspose.Words API pro zpracování dokumentů
description: Pomocí Aspose.Words for .NET snadno rozmotejte zamotané záložky řádků v dokumentech aplikace Word. Tato příručka vás provede procesem čistší a bezpečnější správy záložek.
weight: 10
url: /cs/net/programming-with-bookmarks/untangle-row-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rozmotat záložky řádků v dokumentu aplikace Word

## Zavedení

Už jste se někdy setkali se situací, kdy smazání řádku v dokumentu aplikace Word záložkou zpackalo ostatní záložky v sousedních řádcích? To může být neuvěřitelně frustrující, zejména při práci se složitými tabulkami. Naštěstí Aspose.Words for .NET nabízí výkonné řešení: rozmotání záložek řádků. 

Tato příručka vás provede procesem rozpletení záložek řádků v dokumentech aplikace Word pomocí Aspose.Words for .NET. Rozdělíme kód do snadno srozumitelných kroků a vysvětlíme účel každé funkce, což vám umožní s jistotou řešit tyto nepříjemné problémy se záložkami.

## Předpoklady

Než se ponoříte, budete potřebovat několik věcí:

1.  Aspose.Words for .NET: Tato komerční knihovna poskytuje funkce pro programovou práci s dokumenty Wordu. 2. Můžete si stáhnout bezplatnou zkušební verzi z[odkaz ke stažení](https://releases.aspose.com/words/net/) nebo zakoupit licenci od[nakoupit](https://purchase.aspose.com/buy).
3. Vývojové prostředí AC#: Visual Studio nebo jakékoli jiné C# IDE bude fungovat perfektně.
4. Dokument aplikace Word se záložkami řádků: Pro demonstrační účely použijeme vzorový dokument s názvem „Sloupec tabulky bookmarks.docx“.

## Importovat jmenné prostory

První krok zahrnuje import potřebných jmenných prostorů do vašeho projektu C#. Tyto jmenné prostory poskytují přístup ke třídám a funkcím, které budeme používat z Aspose.Words pro .NET:

```csharp
using Aspose.Words;
using System;
```

## Krok 1: Načtěte dokument aplikace Word

 Začneme načtením dokumentu aplikace Word obsahující záložky spletených řádků. The`Document` třída zpracovává manipulaci s dokumenty v Aspose.Words. Postup načtení dokumentu:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // Nahraďte umístěním vašeho dokumentu
Document doc = new Document(dataDir + "Table column bookmarks.docx");
```

 Nezapomeňte vyměnit`"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou k vašemu souboru "Sloupec tabulky bookmarks.docx".

## Krok 2: Rozbalte záložky řádků

 Tady se děje kouzlo! The`Untangle` funkce se stará o rozmotání záložek řádků. Pojďme si rozebrat jeho funkčnost:

```csharp
private void Untangle(Document doc)
{
   foreach (Bookmark bookmark in doc.Range.Bookmarks)
   {
	   // Získejte nadřazený řádek záložky i konce záložky
	   Row row1 = (Row)bookmark.BookmarkStart.GetAncestor(typeof(Row));
	   Row row2 = (Row)bookmark.BookmarkEnd.GetAncestor(typeof(Row));

	   // Zkontrolujte, zda jsou řádky platné a sousedící
	   if (row1 != null && row2 != null && row1.NextSibling == row2)
		   //Přesunout konec záložky na poslední odstavec poslední buňky horního řádku
		   row1.LastCell.LastParagraph.AppendChild(bookmark.BookmarkEnd);
   }
}
```

Zde je podrobné vysvětlení toho, co kód dělá:

 Iterujeme všechny záložky v dokumentu pomocí a`foreach` smyčka.
Pro každou záložku získáme nadřazený řádek začátku záložky (`bookmark.BookmarkStart`) a konec záložky (`bookmark.BookmarkEnd` ) pomocí`GetAncestor` metoda.
Poté zkontrolujeme, zda byly nalezeny oba řádky (`row1 != null`a`row2 != null`) a pokud se jedná o sousední řádky (`row1.NextSibling == row2`). To zajišťuje, že upravíme pouze záložky, které se rozprostírají přes sousední řádky.
Pokud jsou podmínky splněny, přesuneme koncový uzel záložky na konec posledního odstavce v poslední buňce horního řádku (`row1.LastCell.LastParagraph.AppendChild(bookmark.BookmarkEnd)`) efektivně je rozmotat.

## Krok 3: Odstraňte řádek podle záložky

 Nyní, když jsou záložky rozmotané, můžeme bezpečně mazat řádky pomocí jejich názvů záložek. The`DeleteRowByBookmark` funkce řeší tento úkol:

```csharp
private void DeleteRowByBookmark(Document doc, string bookmarkName)
{
   Bookmark bookmark = doc.Range.Bookmarks[bookmarkName];

   Row row = (Row)bookmark?.BookmarkStart.GetAncestor(typeof(Row));
   row?.Remove();
}
```

Zde je rozpis této funkce:

Vezmeme název záložky (`bookmarkName`) jako vstup.
 Načteme odpovídající objekt záložky pomocí`doc.Range.Bookmarks[bookmarkName]`.
Poté se začne používat nadřazený řádek záložky`GetAncestor` (podobně jako`Untangle` funkce).
Nakonec zkontrolujeme, zda záložka a řádek existují (`bookmark != null` a

## Krok 4: Ověřte rozpletení

 Zatímco`Untangle` funkce by měla zajistit bezpečnost ostatních záložek, je vždy dobré to ověřit. Zde je návod, jak můžeme zkontrolovat, zda proces rozmotávání omylem nesmazal konec jiné záložky:

```csharp
if (doc.Range.Bookmarks["ROW1"].BookmarkEnd == null)
   throw new Exception("Wrong, the end of the bookmark was deleted.");
```

Tento fragment kódu zkontroluje, zda konec záložky s názvem "ROW1" stále existuje po odstranění řádku se záložkou "ROW2". Pokud je null, je vyvolána výjimka označující problém s procesem rozmotávání. 

## Krok 5: Uložte dokument

 Nakonec po rozbalení záložek a případném odstranění řádků uložte upravený dokument pomocí souboru`Save` metoda:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

Tím se dokument uloží s rozmotanými záložkami a všemi odstraněnými řádky pod novým názvem "WorkingWithBookmarks.UntangleRowBookmarks.docx". 

## Závěr

 Podle těchto kroků a pomocí`Untangle`Pomocí funkce Aspose.Words for .NET můžete efektivně rozmotat záložky řádků v dokumentech aplikace Word. Tím je zajištěno, že odstranění řádků pomocí záložek nezpůsobí nezamýšlené následky s jinými záložkami v sousedních řádcích. Nezapomeňte nahradit zástupné symboly jako`"YOUR DOCUMENT DIRECTORY"` s vašimi skutečnými cestami a názvy souborů.

## FAQ

### Je Aspose.Words for .NET zdarma?

 Aspose.Words for .NET je komerční knihovna s bezplatnou zkušební verzí. Můžete si jej stáhnout z[odkaz ke stažení](https://releases.aspose.com/words/net/).

### Mohu ručně rozmotat záložky řádků ve Wordu?

I když je to technicky možné, ruční rozmotávání záložek ve Wordu může být zdlouhavé a náchylné k chybám. Aspose.Words for .NET tento proces automatizuje, což vám ušetří čas a námahu.

###  Co se stane, když`Untangle` function encounters an error?

Kód obsahuje obslužnou rutinu výjimky, která vyvolá výjimku, pokud proces rozmotávání náhodně odstraní konec jiné záložky. Toto zpracování chyb můžete přizpůsobit svým konkrétním potřebám.

### Mohu tento kód použít k rozmotání záložek napříč nesousedícími řádky?

současné době se kód zaměřuje na rozmotávání záložek, které se rozprostírají přes sousední řádky. Úprava kódu pro zpracování nesousedících řádků by vyžadovala další logiku k identifikaci a zpracování těchto scénářů.

### Existují nějaká omezení pro použití tohoto přístupu?

Tento přístup předpokládá, že záložky jsou dobře definované v buňkách tabulky. Pokud jsou záložky umístěny mimo buňky nebo na neočekávaná místa, proces rozmotávání nemusí fungovat podle očekávání.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
