---
title: Oldja ki a sor könyvjelzőit a Word dokumentumban
linktitle: Oldja ki a sor könyvjelzőit a Word dokumentumban
second_title: Aspose.Words Document Processing API
description: Az Aspose.Words for .NET segítségével könnyedén feloldhatja a kusza soros könyvjelzőket Word-dokumentumaiban. Ez az útmutató végigvezeti Önt a tisztább és biztonságosabb könyvjelzőkezelés folyamatán.
weight: 10
url: /hu/net/programming-with-bookmarks/untangle-row-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Oldja ki a sor könyvjelzőit a Word dokumentumban

## Bevezetés

Találkozott már olyan helyzettel, amikor egy Word-dokumentum egy sorának könyvjelzővel történő törlése összezavarja a szomszédos sorok többi könyvjelzőjét? Ez hihetetlenül frusztráló lehet, különösen, ha összetett táblázatokkal foglalkozunk. Szerencsére az Aspose.Words for .NET hatékony megoldást kínál: feloldja a soros könyvjelzőket. 

Ez az útmutató végigvezeti Önt a sor könyvjelzők feloldásán a Word-dokumentumokban az Aspose.Words for .NET használatával. A kódot könnyen érthető lépésekre bontjuk, és elmagyarázzuk az egyes funkciók célját, így Ön magabiztosan kezelheti a könyvjelzőkkel kapcsolatos kellemetlen problémákat.

## Előfeltételek

Mielőtt merülne, szüksége lesz néhány dologra:

1.  Aspose.Words for .NET: Ez a kereskedelmi könyvtár olyan funkciókat biztosít, amelyek segítségével programozottan dolgozhat Word dokumentumokkal. 2. Ingyenes próbaverziót tölthet le a webhelyről[letöltési link](https://releases.aspose.com/words/net/) vagy vásároljon licencet innen[vétel](https://purchase.aspose.com/buy).
3. AC# fejlesztői környezet: A Visual Studio vagy bármely más C# IDE tökéletesen működik.
4. Word-dokumentum soros könyvjelzőkkel: A „Táblázat oszlopos könyvjelzői.docx” elnevezésű mintadokumentumot használjuk demonstrációs célokra.

## Névterek importálása

Az első lépés a szükséges névterek importálása a C# projektbe. Ezek a névterek hozzáférést biztosítanak az Aspose.Words for .NET általunk használt osztályokhoz és funkciókhoz:

```csharp
using Aspose.Words;
using System;
```

## 1. lépés: Töltse be a Word-dokumentumot

 Kezdjük az összegabalyodott sor könyvjelzőit tartalmazó Word dokumentum betöltésével. A`Document` osztály kezeli az Aspose.Words dokumentumkezelést. Így töltheti be a dokumentumot:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // Cserélje ki a dokumentum helyével
Document doc = new Document(dataDir + "Table column bookmarks.docx");
```

 Ne felejtse el cserélni`"YOUR DOCUMENT DIRECTORY"` a "Táblázat oszlopos könyvjelzői.docx" fájl tényleges elérési útjával.

## 2. lépés: Oldja ki a sor könyvjelzőit

 Itt történik a varázslat! A`Untangle` funkció gondoskodik a sor könyvjelzőinek kioldásáról. Bontsuk le a funkcióit:

```csharp
private void Untangle(Document doc)
{
   foreach (Bookmark bookmark in doc.Range.Bookmarks)
   {
	   // Szerezze meg a könyvjelző és a könyvjelzővég szülősorát
	   Row row1 = (Row)bookmark.BookmarkStart.GetAncestor(typeof(Row));
	   Row row2 = (Row)bookmark.BookmarkEnd.GetAncestor(typeof(Row));

	   // Ellenőrizze, hogy a sorok érvényesek és szomszédosak-e
	   if (row1 != null && row2 != null && row1.NextSibling == row2)
		   //Mozgassa a könyvjelző végét a felső sor utolsó cellájának utolsó bekezdésébe
		   row1.LastCell.LastParagraph.AppendChild(bookmark.BookmarkEnd);
   }
}
```

Íme lépésről lépésre a kód működésének magyarázata:

 A dokumentumban található összes könyvjelzőn keresztül iterálunk az a`foreach` hurok.
Minden könyvjelzőnél lekérjük mindkét könyvjelző kezdősorának szülősorát (`bookmark.BookmarkStart`) és a könyvjelző vége (`bookmark.BookmarkEnd` ) segítségével`GetAncestor` módszer.
Ezután ellenőrizzük, hogy mindkét sor megtalálható-e (`row1 != null`és`row2 != null`) és ha szomszédos sorok (`row1.NextSibling == row2`). Ez biztosítja, hogy csak a szomszédos sorokon átívelő könyvjelzőket módosítsuk.
Ha a feltételek teljesülnek, a könyvjelző végcsomópontját áthelyezzük a felső sor utolsó cellájának utolsó bekezdésének végére (`row1.LastCell.LastParagraph.AppendChild(bookmark.BookmarkEnd)`) hatékonyan kibogozni őket.

## 3. lépés: Sor törlése könyvjelzővel

 Most, hogy a könyvjelzőket kibontották, biztonságosan törölhetjük a sorokat a könyvjelzők nevével. A`DeleteRowByBookmark` függvény kezeli ezt a feladatot:

```csharp
private void DeleteRowByBookmark(Document doc, string bookmarkName)
{
   Bookmark bookmark = doc.Range.Bookmarks[bookmarkName];

   Row row = (Row)bookmark?.BookmarkStart.GetAncestor(typeof(Row));
   row?.Remove();
}
```

Íme ennek a függvénynek a bontása:

Felvesszük a könyvjelző nevét (`bookmarkName`) bemenetként.
 A megfelelő könyvjelző objektumot a segítségével lekérjük`doc.Range.Bookmarks[bookmarkName]`.
Ezután a könyvjelző szülősorát kezdjük el használni`GetAncestor` (hasonlóan a`Untangle` funkció).
Végül ellenőrizzük, hogy létezik-e a könyvjelző és a sor (`bookmark != null` és

## 4. lépés: Ellenőrizze a kibontást

 Míg a`Untangle` funkciónak biztosítania kell a többi könyvjelző biztonságát, ezt mindig jó gyakorlat ellenőrizni. Így ellenőrizhetjük, hogy a kibontási folyamat nem törölte-e véletlenül egy másik könyvjelző végét:

```csharp
if (doc.Range.Bookmarks["ROW1"].BookmarkEnd == null)
   throw new Exception("Wrong, the end of the bookmark was deleted.");
```

Ez a kódrészlet ellenőrzi, hogy a "ROW1" nevű könyvjelző vége továbbra is létezik-e a "ROW2" könyvjelzővel ellátott sor törlése után. Ha ez nulla, a rendszer kivételt dob, jelezve, hogy probléma van a kibontási folyamattal. 

## 5. lépés: Mentse el a dokumentumot

 Végül a könyvjelzők kibontása és a sorok esetleges törlése után mentse el a módosított dokumentumot a`Save` módszer:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

Ezzel a dokumentumot a kibontott könyvjelzőkkel és a törölt sorokkal együtt új „WorkingWithBookmarks.UntangleRowBookmarks.docx” fájlnéven menti. 

## Következtetés

 Ezen lépések követésével és a`Untangle`Az Aspose.Words for .NET segítségével hatékonyan kibonthatja a soros könyvjelzőket a Word-dokumentumokban. Ez biztosítja, hogy a sorok könyvjelzők általi törlése ne okozzon nem kívánt következményeket a szomszédos sorokban lévő többi könyvjelzővel kapcsolatban. Ne felejtse el lecserélni a helyőrzőket, mint például`"YOUR DOCUMENT DIRECTORY"` a tényleges elérési utakkal és fájlnevekkel.

## GYIK

### Az Aspose.Words for .NET ingyenes?

 Az Aspose.Words for .NET egy ingyenes próbaverzióval rendelkező kereskedelmi könyvtár. Letöltheti innen[letöltési link](https://releases.aspose.com/words/net/).

### Kibonthatom kézzel a sorkönyvjelzőket a Wordben?

Bár technikailag lehetséges, a könyvjelzők kézi kibontása a Wordben fárasztó és hibás lehet. Az Aspose.Words for .NET automatizálja ezt a folyamatot, így időt és erőfeszítést takarít meg.

###  Mi történik, ha a`Untangle` function encounters an error?

A kód tartalmaz egy kivételkezelőt, amely kivételt dob, ha a kibontási folyamat véletlenül törli egy másik könyvjelző végét. Ezt a hibakezelést személyre szabhatja saját igényeinek megfelelően.

### Használhatom ezt a kódot a nem szomszédos sorok könyvjelzőinek kibontására?

Jelenleg a kód a szomszédos sorokon átívelő könyvjelzők feloldására összpontosít. A kód módosítása a nem szomszédos sorok kezeléséhez további logikát igényel ezen forgatókönyvek azonosításához és kezeléséhez.

### Vannak korlátai ennek a megközelítésnek?

Ez a megközelítés feltételezi, hogy a könyvjelzők jól meghatározottak a táblázatcellákon belül. Ha a könyvjelzőket a cellákon kívülre vagy váratlan helyekre helyezi, előfordulhat, hogy a kibontási folyamat nem fog megfelelően működni.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
