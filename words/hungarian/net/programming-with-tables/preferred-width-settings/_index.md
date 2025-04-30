---
"description": "Tanuld meg, hogyan hozhatsz létre abszolút, relatív és automatikus szélességbeállításokkal rendelkező táblázatokat az Aspose.Words for .NET programban ezzel a lépésről lépésre szóló útmutatóval."
"linktitle": "Előnyben részesített szélességbeállítások"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Előnyben részesített szélességbeállítások"
"url": "/hu/net/programming-with-tables/preferred-width-settings/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Előnyben részesített szélességbeállítások

## Bevezetés

A táblázatok hatékony eszközt jelentenek a Word-dokumentumokban található információk rendszerezésére és megjelenítésére. Amikor az Aspose.Words for .NET programban táblázatokkal dolgozik, számos lehetőség közül választhat a táblázatcellák szélességének beállítására, hogy azok tökéletesen illeszkedjenek a dokumentum elrendezéséhez. Ez az útmutató végigvezeti Önt a kívánt szélességbeállításokkal rendelkező táblázatok létrehozásának folyamatán az Aspose.Words for .NET használatával, az abszolút, relatív és automatikus méretezési lehetőségekre összpontosítva. 

## Előfeltételek

Mielőtt belevágnál az oktatóanyagba, győződj meg róla, hogy a következőkkel rendelkezel:

1. Aspose.Words for .NET: Győződjön meg róla, hogy az Aspose.Words for .NET telepítve van a fejlesztői környezetében. Letöltheti [itt](https://releases.aspose.com/words/net/).

2. .NET fejlesztői környezet: Rendelkezzen egy beállított .NET fejlesztői környezettel, például a Visual Studio-val.

3. C# alapismeretek: A C# programozással való ismeret segít jobban megérteni a kódrészleteket és példákat.

4. Aspose.Words dokumentáció: Lásd a [Aspose.Words dokumentáció](https://reference.aspose.com/words/net/) részletes API-információkért és további olvasmányokért lásd:

## Névterek importálása

Mielőtt elkezdenéd a kódolást, importálnod kell a szükséges névtereket a C# projektedbe:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Ezek a névterek hozzáférést biztosítanak az Aspose.Words és a Table objektum alapvető funkcióihoz, lehetővé téve a dokumentumtáblák kezelését.

Bontsuk le világos és kezelhető lépésekre a különböző szélességbeállításokkal rendelkező táblázatok létrehozásának folyamatát.

## 1. lépés: A dokumentum és a DocumentBuilder inicializálása

Cím: Új dokumentum létrehozása és a DocumentBuilder

Magyarázat: Kezdésként hozzon létre egy új Word dokumentumot, és `DocumentBuilder` például. A `DocumentBuilder` Az osztály egyszerű módot kínál tartalom hozzáadására a dokumentumhoz.

```csharp
// Adja meg a dokumentum mentési útvonalát.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Hozz létre egy új dokumentumot.
Document doc = new Document();

// Hozz létre egy DocumentBuildert ehhez a dokumentumhoz.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Itt adhatja meg azt a könyvtárat, ahová a dokumentumot menteni szeretné, és inicializálja a `Document` és `DocumentBuilder` tárgyak.

## 2. lépés: Az első táblázatcella beszúrása abszolút szélességgel

Szúrja be a táblázat első celláját 40 pontos fix szélességgel. Ez biztosítja, hogy a cella szélessége mindig 40 pont maradjon, függetlenül a táblázat méretétől.

```csharp
// Helyezzen be egy abszolút méretű cellát.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPoints(40);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightYellow;
builder.Writeln("Cell at 40 points width");
```

Ebben a lépésben elkezdi létrehozni a táblázatot, és beszúr egy abszolút szélességű cellát. `PreferredWidth.FromPoints(40)` A metódus a cella szélességét 40 pontra állítja be, és `Shading.BackgroundPatternColor` világossárga háttérszínt alkalmaz.

## 3. lépés: Relatív méretű cella beszúrása

Szúrjon be egy újabb cellát, amelynek szélessége a táblázat teljes szélességének 20%-a. Ez a relatív méretezés biztosítja, hogy a cella arányosan igazodjon a táblázat szélességéhez.

```csharp
// Relatív (százalékos) méretű cella beszúrása.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(20);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
builder.Writeln("Cell at 20% width");
```

cella szélessége a táblázat teljes szélességének 20%-a lesz, így alkalmazkodni fog a különböző képernyőméretekhez vagy dokumentumelrendezésekhez.

### 4. lépés: Automatikusan méretezett cella beszúrása

Végül szúrjon be egy cellát, amely automatikusan méretezi magát a táblázatban fennmaradó rendelkezésre álló hely alapján.

```csharp
// Automatikusan méretezett cella beszúrása.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.Auto;
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightGreen;
builder.Writeln("Cell automatically sized. A size of this cell is calculated from the table preferred width.");
builder.Writeln("In this case the cell will fill up the rest of the available space.");
```

The `PreferredWidth.Auto` A beállítás lehetővé teszi, hogy ez a cella a többi cella figyelembevétele után megmaradó hely alapján bővüljön vagy zsugorodjon. Ez biztosítja, hogy a táblázat elrendezése kiegyensúlyozott és professzionális legyen.

## 5. lépés: A dokumentum véglegesítése és mentése

Miután beszúrta az összes cellát, töltse ki a táblázatot, és mentse el a dokumentumot a megadott elérési útra.

```csharp
// Mentse el a dokumentumot.
doc.Save(dataDir + "WorkingWithTables.PreferredWidthSettings.docx");
```

Ez a lépés véglegesíti a táblázatot, és a dokumentumot „WorkingWithTables.PreferredWidthSettings.docx” fájlnévvel menti a megadott könyvtárba.

## Következtetés

Az Aspose.Words for .NET programban a kívánt szélességbeállításokkal rendelkező táblázatok létrehozása egyszerű, ha már ismeri a különböző méretezési lehetőségeket. Akár fix, relatív, akár automatikus cellassagosságra van szüksége, az Aspose.Words rugalmasságot biztosít a különféle táblázatelrendezési forgatókönyvek hatékony kezeléséhez. Az útmutatóban ismertetett lépéseket követve biztosíthatja, hogy táblázatai jól strukturáltak és vizuálisan vonzóak legyenek a Word-dokumentumokban.

## GYIK

### Mi a különbség az abszolút és a relatív cellaméret között?
Az abszolút cella szélességek rögzítettek és nem változnak, míg a relatív szélességek a táblázat teljes szélességétől függően módosulnak.

### Használhatok negatív százalékokat relatív szélességekhez?
Nem, a negatív százalékok nem érvényesek a cella szélességére. Csak pozitív százalékok engedélyezettek.

### Hogyan működik az automatikus méretezés funkció?
Az automatikus méretezés úgy állítja be a cella szélességét, hogy kitöltse a táblázatban fennmaradó helyet, miután a többi cella méretezése megtörtént.

### Alkalmazhatok különböző stílusokat eltérő szélességű cellákra?
Igen, különféle stílusokat és formázásokat alkalmazhat a cellákra, a szélességi beállításoktól függetlenül.

### Mi történik, ha a táblázat teljes szélessége kisebb, mint az összes cella szélességének összege?
A táblázat automatikusan a rendelkezésre álló helyhez igazítja a cellák szélességét, ami egyes cellák méretének csökkenését okozhatja.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}