---
title: Preferált szélesség beállítások
linktitle: Preferált szélesség beállítások
second_title: Aspose.Words Document Processing API
description: Ebből a lépésről lépésre szóló útmutatóból megtudhatja, hogyan hozhat létre táblázatokat abszolút, relatív és automatikus szélességbeállításokkal az Aspose.Words for .NET alkalmazásban.
weight: 10
url: /hu/net/programming-with-tables/preferred-width-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Preferált szélesség beállítások

## Bevezetés

táblázatok hatékony módszert jelentenek az információk rendszerezésére és megjelenítésére a Word-dokumentumokban. Ha táblázatokkal dolgozik az Aspose.Words for .NET programban, számos lehetőség közül választhat a táblázatcellák szélességének beállítására, hogy azok tökéletesen illeszkedjenek a dokumentum elrendezéséhez. Ez az útmutató végigvezeti az Aspose.Words for .NET segítségével előnyben részesített szélességbeállításokkal rendelkező táblázatok létrehozásának folyamatán, az abszolút, relatív és automatikus méretezési beállításokra összpontosítva. 

## Előfeltételek

Mielőtt belevágna az oktatóanyagba, győződjön meg arról, hogy rendelkezik az alábbiakkal:

1.  Aspose.Words for .NET: Győződjön meg arról, hogy az Aspose.Words for .NET telepítve van a fejlesztői környezetében. Letöltheti[itt](https://releases.aspose.com/words/net/).

2. .NET fejlesztői környezet: legyen beállítva egy .NET fejlesztői környezet, például a Visual Studio.

3. A C# alapismeretei: A C# programozás ismerete segít jobban megérteni a kódrészleteket és a példákat.

4.  Aspose.Words Dokumentáció: Lásd a[Aspose.Words Dokumentáció](https://reference.aspose.com/words/net/) részletes API-információkért és további olvasnivalókért.

## Névterek importálása

A kódolás megkezdése előtt importálnia kell a szükséges névtereket a C# projektbe:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Ezek a névterek hozzáférést biztosítanak az Aspose.Words és a Table objektum alapvető funkcióihoz, lehetővé téve a dokumentumtáblázatok kezelését.

Bontsuk le a különböző preferált szélességű táblázatok létrehozásának folyamatát világos, kezelhető lépésekre.

## 1. lépés: Inicializálja a Dokumentumot és a DocumentBuildert

Címsor: Új dokumentum és dokumentumkészítő létrehozása

 Magyarázat: Kezdje egy új Word-dokumentum létrehozásával, és a`DocumentBuilder` példa. A`DocumentBuilder` osztály egyszerű módot kínál a dokumentum tartalmának hozzáadására.

```csharp
// Határozza meg a dokumentum mentési útvonalát.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Hozzon létre egy új dokumentumot.
Document doc = new Document();

// Hozzon létre egy DocumentBuilder programot ehhez a dokumentumhoz.
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Itt adja meg azt a könyvtárat, ahová a dokumentumot menti, és inicializálja a`Document` és`DocumentBuilder` tárgyakat.

## 2. lépés: Helyezze be az első abszolút szélességű táblázatcellát

Szúrja be az első cellát a táblázatba fix 40 pontos szélességgel. Ez biztosítja, hogy a cella szélessége mindig 40 pont legyen, függetlenül a táblázat méretétől.

```csharp
// Szúrjon be egy abszolút méretű cellát.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPoints(40);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightYellow;
builder.Writeln("Cell at 40 points width");
```

Ebben a lépésben elkezdi létrehozni a táblázatot, és beszúrni egy abszolút szélességű cellát. A`PreferredWidth.FromPoints(40)` metódus a cella szélességét 40 pontra állítja, és`Shading.BackgroundPatternColor` világos sárga háttérszínt alkalmaz.

## 3. lépés: Helyezzen be egy relatív méretű cellát

Szúrjon be egy másik cellát, amelynek szélessége a táblázat teljes szélességének 20%-a. Ez a relatív méretezés biztosítja, hogy a cella arányosan igazodjon a táblázat szélességéhez.

```csharp
// Szúrjon be egy relatív (százalékos) méretű cellát.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(20);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
builder.Writeln("Cell at 20% width");
```

Ennek a cellának a szélessége a táblázat teljes szélességének 20%-a lesz, így a különböző képernyőméretekhez vagy dokumentumelrendezésekhez igazítható.

### 4. lépés: Helyezzen be egy automatikus méretű cellát

Végül szúrjon be egy cellát, amely automatikusan méretezi magát a táblázatban rendelkezésre álló szabad hely alapján.

```csharp
// Szúrjon be egy automatikus méretű cellát.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.Auto;
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightGreen;
builder.Writeln("Cell automatically sized. The size of this cell is calculated from the table preferred width.");
builder.Writeln("In this case the cell will fill up the rest of the available space.");
```

 A`PreferredWidth.Auto` A beállítás lehetővé teszi, hogy ez a cella kibővüljön vagy összehúzódjon a többi cella elszámolása után hagyott hely alapján. Ez biztosítja, hogy az asztal elrendezése kiegyensúlyozott és professzionális legyen.

## 5. lépés: Véglegesítse és mentse a dokumentumot

Miután beszúrta az összes cellát, töltse ki a táblázatot, és mentse a dokumentumot a megadott elérési útra.

```csharp
// Mentse el a dokumentumot.
doc.Save(dataDir + "WorkingWithTables.PreferredWidthSettings.docx");
```

Ez a lépés véglegesíti a táblázatot, és elmenti a dokumentumot „WorkingWithTables.PreferredWidthSettings.docx” fájlnévvel a kijelölt könyvtárba.

## Következtetés

Az Aspose.Words for .NET-ben előnyben részesített szélességi beállításokkal rendelkező táblázatok létrehozása egyszerű, ha megismeri a rendelkezésre álló különböző méretezési lehetőségeket. Függetlenül attól, hogy rögzített, relatív vagy automatikus cellaszélességre van szüksége, az Aspose.Words rugalmasságot biztosít a különféle táblázatelrendezési forgatókönyvek hatékony kezelésére. Az ebben az útmutatóban vázolt lépések követésével biztosíthatja, hogy a táblázatok jól strukturáltak és tetszetősek legyenek a Word-dokumentumokban.

## GYIK

### Mi a különbség az abszolút és a relatív cellaszélesség között?
Az abszolút cellaszélességek rögzítettek és nem változnak, míg a relatív szélességek a táblázat teljes szélessége alapján módosulnak.

### Használhatok negatív százalékot a relatív szélességekhez?
Nem, a negatív százalékok nem érvényesek a cellaszélességekre. Csak pozitív százalékok megengedettek.

### Hogyan működik az automatikus méretezés funkció?
Az automatikus méretezés úgy állítja be a cella szélességét, hogy a többi cella méretezése után a táblázatban fennmaradó helyet kitöltse.

### Alkalmazhatok különböző stílusokat a különböző szélességi beállításokkal rendelkező cellákra?
Igen, különféle stílusokat és formázásokat alkalmazhat a cellákra, függetlenül azok szélességi beállításaitól.

### Mi történik, ha a táblázat teljes szélessége kisebb, mint az összes cellaszélesség összege?
A táblázat automatikusan beállítja a cellák szélességét, hogy beleférjen a rendelkezésre álló helyre, ami egyes cellák zsugorodását okozhatja.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
