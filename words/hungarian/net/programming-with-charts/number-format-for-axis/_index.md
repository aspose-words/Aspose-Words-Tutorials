---
"description": "Tanuld meg, hogyan formázhatod a diagram tengelyszámait az Aspose.Words for .NET segítségével ezzel a lépésről lépésre haladó útmutatóval. Növeld dokumentumod olvashatóságát és professzionalizmusát erőfeszítés nélkül."
"linktitle": "Számformátum a diagram tengelyeihez"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Számformátum a diagram tengelyeihez"
"url": "/hu/net/programming-with-charts/number-format-for-axis/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Számformátum a diagram tengelyeihez

## Bevezetés

Sziasztok! Dolgoztatok már diagramokkal a dokumentumaitokban, és szerettetek volna formázni a tengelyeken lévő számokat, hogy professzionálisabbnak tűnjenek? Nos, szerencsétek van! Ebben az oktatóanyagban mélyrehatóan megvizsgáljuk, hogyan érhetitek el ezt az Aspose.Words for .NET használatával. Ez a hatékony könyvtár lehetővé teszi a Word-dokumentumok egyszerű kezelését. Ma pedig arra összpontosítunk, hogy egyéni számformátumokkal alakítsuk át ezeket a diagramtengelyeket.

## Előfeltételek

Mielőtt belekezdenénk, ellenőrizzük, hogy minden megvan-e, amire szükséged van. Íme egy gyors ellenőrzőlista:

- Aspose.Words .NET-hez: Győződjön meg róla, hogy telepítve van. Ha nem, akkor megteheti [töltsd le itt](https://releases.aspose.com/words/net/).
- .NET-keretrendszer: Győződjön meg arról, hogy telepítve van egy kompatibilis .NET-keretrendszer.
- Fejlesztői környezet: Egy IDE, mint például a Visual Studio, tökéletesen működni fog.
- C# alapismeretek: Ez segít majd követni a kódolási példákat.

## Névterek importálása

Először is importálnod kell a szükséges névtereket a projektedbe. Ez olyan, mintha leraknád az alapokat egy ház építése előtt. Add hozzá a következőket direktívák használatával a kódfájl elejéhez:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Reporting;
```

Most pedig bontsuk le a folyamatot egyszerű, könnyen követhető lépésekre.

## 1. lépés: A dokumentum beállítása

Címsor: Dokumentum inicializálása

Először létre kell hoznod egy új dokumentumot és egy dokumentumszerkesztőt. Gondolj erre a lépésre úgy, mintha előkészítenéd a vásznat és az ecsetet, mielőtt elkezdenéd a remekműved megalkotását.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Itt, `dataDir` a dokumentumkönyvtár elérési útja, ahová a végső fájlt menteni fogja. `Document` és `DocumentBuilder` az Aspose.Words osztályai, amelyek segítenek Word dokumentumok létrehozásában és kezelésében.

## 2. lépés: Diagram beszúrása

Címsor: Táblázat hozzáadása a dokumentumhoz

Következő lépésként adjunk hozzá egy diagramot a dokumentumhoz. Itt kezdődik a varázslat. Beszúrunk egy oszlopdiagramot, amely üres vászonként fog szolgálni.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

A `InsertChart` metódus egy megadott típusú (jelen esetben Oszlop) és méretű diagramot szúr be a dokumentumba.

## 3. lépés: A diagramsorozat testreszabása

Címsor: Töltsd fel a diagramodat adatokkal

Most hozzá kell adnunk néhány adatot a diagramunkhoz. Ez a lépés hasonló ahhoz, mintha értelmes információkkal töltenénk fel a diagramot.

```csharp
chart.Series.Clear();
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1900000, 850000, 2100000, 600000, 1500000 });
```

Itt egy új, öt adatponttal rendelkező, „Aspose Series 1” nevű sorozatot adunk hozzá. `Series.Clear` A metódus biztosítja, hogy minden meglévő adat eltávolításra kerüljön az új sorozat hozzáadása előtt.

## 4. lépés: A tengelyszámok formázása

Cím: Szépítsd a tengelyszámaidat

Végül formázzuk meg az Y tengelyen lévő számokat, hogy olvashatóbbak legyenek. Ez olyan, mintha az utolsó simításokat végeznénk a grafikán.

```csharp
chart.AxisY.NumberFormat.FormatCode = "#,##0";
```

A `FormatCode` tulajdonság lehetővé teszi a tengelyen lévő számok egyéni formátumának beállítását. Ebben a példában a `#,##0` biztosítja, hogy a nagy számok ezresek helyett vesszővel jelenjenek meg.

## 5. lépés: A dokumentum mentése

Cím: Mentsd el a remekműved

Most, hogy minden elő van készítve, itt az ideje menteni a dokumentumot. Ez a lépés a munkád nagy felfedése.

```csharp
doc.Save(dataDir + "WorkingWithCharts.NumberFormatForAxis.docx");
```

Itt a `Save` metódus a megadott elérési útra menti a dokumentumot a fájlnévvel. `WorkingWithCharts.NumberFormatForAxis.docx`.

## Következtetés

És íme! Sikeresen formáztad a diagramod Y tengelyén lévő számokat az Aspose.Words for .NET segítségével. Ez nemcsak professzionálisabb megjelenésűvé teszi a diagramjaidat, hanem javítja az olvashatóságot is. Az Aspose.Words számos olyan funkciót kínál, amelyek segítségével lenyűgöző Word-dokumentumokat hozhatsz létre programozottan. Szóval, miért ne fedeznél fel többet, és néznéd meg, hogy mit tehetsz még?

## GYIK

### Mi az Aspose.Words .NET-hez?
Az Aspose.Words for .NET egy hatékony függvénytár, amely lehetővé teszi a fejlesztők számára, hogy programozottan hozzanak létre, szerkeszszenek és konvertáljanak Word dokumentumokat.

### Formázhatom a diagram más aspektusait is a tengelyszámokon kívül?
Abszolút! Az Aspose.Words for .NET lehetővé teszi a címek és címkék formázását, sőt, a diagram megjelenésének testreszabását is.

### Van ingyenes próbaverzió az Aspose.Words for .NET-hez?
Igen, kaphatsz egy [ingyenes próba itt](https://releases.aspose.com/).

### Használhatom az Aspose.Words for .NET-et más .NET nyelvekkel is a C#-on kívül?
Igen, az Aspose.Words for .NET kompatibilis bármely .NET nyelvvel, beleértve a VB.NET-et és az F#-ot is.

### Hol találok részletesebb dokumentációt?
Részletes dokumentáció elérhető a [Aspose.Words .NET dokumentációs oldal](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}