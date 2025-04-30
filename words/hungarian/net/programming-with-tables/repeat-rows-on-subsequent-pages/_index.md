---
"description": "Tanuld meg, hogyan hozhatsz létre ismétlődő táblázatfejlécsorokkal rendelkező Word-dokumentumokat az Aspose.Words for .NET segítségével. Kövesd ezt az útmutatót a professzionális és kifinomult dokumentumok érdekében."
"linktitle": "Sorok ismétlése a következő oldalakon"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Sorok ismétlése a következő oldalakon"
"url": "/hu/net/programming-with-tables/repeat-rows-on-subsequent-pages/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sorok ismétlése a következő oldalakon

## Bevezetés

Egy Word-dokumentum programozott létrehozása ijesztő feladat lehet, különösen akkor, ha több oldalon is meg kell őrizni a formázást. Próbáltál már táblázatot készíteni a Wordben, és rájöttél, hogy a fejlécsorok nem ismétlődnek a következő oldalakon? Ne félj! Az Aspose.Words for .NET segítségével könnyedén biztosíthatod, hogy a táblázat fejlécei minden oldalon ismétlődjenek, professzionális és letisztult megjelenést kölcsönözve a dokumentumoknak. Ebben az oktatóanyagban egyszerű kódpéldákkal és részletes magyarázatokkal végigvezetünk a lépéseken, hogy ezt elérhesd. Vágjunk bele!

## Előfeltételek

Mielőtt belekezdenénk, győződjünk meg róla, hogy a következőkkel rendelkezünk:

1. Aspose.Words .NET-hez: Letöltheti [itt](https://releases.aspose.com/words/net/).
2. .NET-keretrendszer telepítve a gépedre.
3. Visual Studio vagy bármely más IDE, amely támogatja a .NET fejlesztést.
4. C# programozás alapjainak ismerete.

A folytatás előtt győződjön meg arról, hogy telepítette az Aspose.Words for .NET programot, és beállította a fejlesztői környezetet.

## Névterek importálása

Kezdésként importálnod kell a szükséges névtereket a projektedbe. Add hozzá a következőket direktívák használatával a C# fájlod elejéhez:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Ezek a névterek tartalmazzák a Word-dokumentumok és -táblázatok kezeléséhez szükséges osztályokat és metódusokat.

## 1. lépés: A dokumentum inicializálása

Először is hozzunk létre egy új Word dokumentumot, és egy `DocumentBuilder` hogy elkészítsük az asztalunkat.

```csharp
// A dokumentumkönyvtár elérési útja 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Ez a kód inicializál egy új dokumentumot és egy `DocumentBuilder` objektum, amely segít a dokumentum szerkezetének felépítésében.

## 2. lépés: Indítsa el a táblázatot és definiálja a fejlécsorokat

Ezután elkezdjük a táblázatot, és meghatározzuk a fejlécsorokat, amelyeket a következő oldalakon meg szeretnénk ismételni.

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

Itt új táblázatot kezdünk, beállítjuk a `HeadingFormat` ingatlan `true` annak jelzésére, hogy a sorok fejlécek, és meghatározzák a cellák igazítását és szélességét.

## 3. lépés: Adatsorok hozzáadása a táblázathoz

Most több adatsort fogunk hozzáadni a táblázatunkhoz. Ezek a sorok nem fognak ismétlődni a következő oldalakon.

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

Ez a ciklus 50 sornyi adatot szúr be a táblázatba, soronként két oszloppal. `HeadingFormat` erre van beállítva `false` ezekhez a sorokhoz, mivel ezek nem fejlécsorok.

## 4. lépés: A dokumentum mentése

Végül a dokumentumot a megadott könyvtárba mentjük.

```csharp
doc.Save(dataDir + "WorkingWithTables.RepeatRowsOnSubsequentPages.docx");
```

Ez a megadott néven menti a dokumentumot a dokumentumkönyvtárba.

## Következtetés

És íme! Mindössze néhány sornyi kóddal létrehozhatsz egy Word-dokumentumot, amelynek táblázatai ismétlődő fejlécsorokkal rendelkeznek a következő oldalakon az Aspose.Words for .NET segítségével. Ez nemcsak a dokumentumok olvashatóságát javítja, hanem egységes és professzionális megjelenést is biztosít. Most pedig próbáld ki a projektjeidben!

## GYIK

### Testreszabhatom a fejléc sorokat?
Igen, további formázást alkalmazhat a fejlécsorokra a tulajdonságainak módosításával. `ParagraphFormat`, `RowFormat`, és `CellFormat`.

### Lehetséges további oszlopokat hozzáadni a táblázathoz?
Természetesen! Annyi oszlopot adhatsz hozzá, amennyire szükséged van, további cellák beszúrásával az oszlopba. `InsertCell` módszer.

### Hogyan tudom ismétlődő sorokat beállítani a következő oldalakon?
Bármely sor ismétlődéséhez állítsa be a `RowFormat.HeadingFormat` ingatlan `true` az adott sorhoz.

### Használhatom ezt a módszert egy dokumentumban lévő meglévő táblázatokhoz?
Igen, módosíthatja a meglévő táblázatokat azáltal, hogy hozzáfér hozzájuk a `Document` objektumot, és hasonló formázást alkalmaz.

### Milyen egyéb táblázatformázási lehetőségek érhetők el az Aspose.Words for .NET programban?
Az Aspose.Words for .NET számos táblázatformázási lehetőséget kínál, beleértve a cellaegyesítést, a szegélybeállításokat és a táblázat igazítását. Nézze meg a [dokumentáció](https://reference.aspose.com/words/net/) további részletekért.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}