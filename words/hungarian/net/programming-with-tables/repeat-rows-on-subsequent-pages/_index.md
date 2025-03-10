---
title: Sorok ismétlése a következő oldalakon
linktitle: Sorok ismétlése a következő oldalakon
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan hozhat létre ismétlődő táblázatfejlécsorokat tartalmazó Word-dokumentumokat az Aspose.Words for .NET használatával. Kövesse ezt az útmutatót a professzionális és kidolgozott dokumentumok biztosításához.
weight: 10
url: /hu/net/programming-with-tables/repeat-rows-on-subsequent-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Sorok ismétlése a következő oldalakon

## Bevezetés

Word-dokumentumok programozott létrehozása ijesztő feladat lehet, különösen akkor, ha a formázást több oldalon is meg kell őriznie. Próbáltál már táblázatot készíteni a Wordben, de rájöttél, hogy a fejlécsorok nem ismétlődnek a következő oldalakon? Ne félj! Az Aspose.Words for .NET segítségével könnyedén biztosíthatja, hogy a táblázat fejlécei minden oldalon ismétlődjenek, így professzionális és csiszolt megjelenést kölcsönöz dokumentumainak. Ebben az oktatóanyagban egyszerű kódpéldák és részletes magyarázatok segítségével végigvezetjük az ehhez szükséges lépéseken. Merüljünk el!

## Előfeltételek

Mielőtt elkezdenénk, győződjön meg arról, hogy rendelkezik a következőkkel:

1.  Aspose.Words for .NET: Letöltheti[itt](https://releases.aspose.com/words/net/).
2. .NET Framework telepítve van a gépére.
3. Visual Studio vagy bármely más IDE, amely támogatja a .NET fejlesztést.
4. A C# programozás alapjai.

A folytatás előtt győződjön meg arról, hogy telepítette az Aspose.Words for .NET programot, és beállította a fejlesztői környezetet.

## Névterek importálása

A kezdéshez importálnia kell a szükséges névtereket a projektbe. Adja hozzá a következőket a C# fájl tetején található direktívák használatával:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Ezek a névterek tartalmazzák a Word-dokumentumok és -táblázatok kezeléséhez szükséges osztályokat és metódusokat.

## 1. lépés: Inicializálja a dokumentumot

 Először hozzunk létre egy új Word dokumentumot, és a`DocumentBuilder` asztalunk elkészítéséhez.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Ez a kód inicializál egy új dokumentumot, és a`DocumentBuilder` objektum, amely segít a dokumentumstruktúra felépítésében.

## 2. lépés: Indítsa el a táblázatot, és határozza meg a fejlécsorokat

Ezután elindítjuk a táblázatot, és meghatározzuk azokat a fejlécsorokat, amelyeket meg szeretnénk ismételni a következő oldalakon.

```csharp
builder.StartTable();
builder.RowFormat.HeadingFormat = true;
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.CellFormat.Width = 100;

builder.InsertCell();
builder.Writeln("Heading row 1");
builder.EndRow();

builder.InsertCell();
builder.Writeln("Heading row 2");
builder.EndRow();
```

 Itt indítunk egy új táblázatot, állítjuk be a`HeadingFormat`tulajdonát`true` jelzi, hogy a sorok fejlécek, és meghatározza a cellák igazítását és szélességét.

## 3. lépés: Adjon hozzá adatsorokat a táblázathoz

Most több adatsort adunk hozzá a táblázatunkhoz. Ezek a sorok nem ismétlődnek a következő oldalakon.

```csharp
builder.CellFormat.Width = 50;
builder.ParagraphFormat.ClearFormatting();
for (int i = 0; i < 50; i++)
{
    builder.InsertCell();
    builder.RowFormat.HeadingFormat = false;
    builder.Write("Column 1 Text");
    
    builder.InsertCell();
    builder.Write("Column 2 Text");
    builder.EndRow();
}
```

 Ez a ciklus 50 adatsort szúr be a táblázatba, minden sorban két oszloppal. A`HeadingFormat` be van állítva`false` ezekhez a sorokhoz, mivel ezek nem fejlécesorok.

## 4. lépés: Mentse el a dokumentumot

Végül elmentjük a dokumentumot a megadott könyvtárba.

```csharp
doc.Save(dataDir + "WorkingWithTables.RepeatRowsOnSubsequentPages.docx");
```

Ezzel elmenti a dokumentumot a megadott néven a dokumentumkönyvtárába.

## Következtetés

És megvan! Néhány sornyi kóddal az Aspose.Words for .NET segítségével létrehozhat egy Word-dokumentumot olyan táblázatokkal, amelyek következő oldalain ismétlődő fejlécsorok vannak. Ez nemcsak javítja a dokumentumok olvashatóságát, hanem egységes és professzionális megjelenést is biztosít. Most pedig próbálja ki ezt a projektjeiben!

## GYIK

### Tovább szabhatom a fejlécsorokat?
 Igen, a fejlécek tulajdonságainak módosításával további formázást is alkalmazhat`ParagraphFormat`, `RowFormat` , és`CellFormat`.

### Lehet-e további oszlopokat hozzáadni a táblázathoz?
 Teljesen! Annyi oszlopot adhat hozzá, amennyi szükséges, ha több cellát szúr be a`InsertCell` módszer.

### Hogyan állíthatom be, hogy más sorok ismétlődjenek a következő oldalakon?
 Ha bármelyik sort meg szeretné ismételni, állítsa be a`RowFormat.HeadingFormat`tulajdonát`true` az adott sorhoz.

### Használhatom ezt a módszert egy dokumentum meglévő tábláihoz?
 Igen, módosíthatja a meglévő táblákat, ha eléri őket a`Document` objektum és hasonló formázás alkalmazása.

### Milyen egyéb táblázatformázási lehetőségek érhetők el az Aspose.Words for .NET-ben?
 Az Aspose.Words for .NET a táblázatformázási lehetőségek széles skáláját kínálja, beleértve a cellaegyesítést, a szegélybeállításokat és a táblázat igazítását. Nézze meg a[dokumentáció](https://reference.aspose.com/words/net/) további részletekért.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
