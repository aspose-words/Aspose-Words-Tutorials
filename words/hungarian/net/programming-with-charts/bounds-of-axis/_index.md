---
title: Tengely határai Egy Chartban
linktitle: Tengely határai Egy Chartban
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan állíthatja be egy tengely határait egy diagramon az Aspose.Words for .NET segítségével, amely a tengelyen megjelenített értéktartományt szabályozza.
weight: 10
url: /hu/net/programming-with-charts/bounds-of-axis/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tengely határai Egy Chartban

## Bevezetés

Professzionális dokumentumokat szeretne létrehozni diagramokkal .NET-ben? Jó helyen jársz! Ez az útmutató végigvezeti az Aspose.Words for .NET használatával a tengely határainak diagramon történő beállításához. Minden egyes lépést lebontunk, hogy könnyen nyomon követhessük, még akkor is, ha még új vagy a könyvtárban. Szóval, merüljünk bele, és kezdjük el!

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik a következőkkel:

-  Aspose.Words for .NET: Megteheti[letöltés](https://releases.aspose.com/words/net/) a legújabb verziót, vagy használja a[ingyenes próbaverzió](https://releases.aspose.com/).
- .NET-keretrendszer: Győződjön meg arról, hogy a .NET telepítve van a rendszeren.
- IDE: Olyan fejlesztői környezet, mint a Visual Studio.

Ha mindennel készen van, folytathatjuk a következő lépésekkel.

## Névterek importálása

A kezdéshez importálnia kell a szükséges névtereket. Ezek lehetővé teszik az Aspose.Words könyvtár és annak diagramozási funkcióinak elérését.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## 1. lépés: Állítsa be a dokumentumkönyvtárat

Először is be kell állítania azt a könyvtárat, ahová a dokumentumot menteni fogja. Ez egy egyszerű lépés, de elengedhetetlen a fájlok rendszerezéséhez.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 2. lépés: Hozzon létre egy új dokumentumot

Ezután hozzon létre egy új dokumentumobjektumot. Ez a dokumentum a diagram tárolójaként fog szolgálni.

```csharp
Document doc = new Document();
```

## 3. lépés: Inicializálja a Dokumentumkészítőt

A DocumentBuilder osztály gyors és egyszerű módot biztosít a dokumentumok létrehozására. Inicializálja a dokumentummal.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 4. lépés: Helyezzen be egy diagramot

Most itt az ideje, hogy beszúrjon egy diagramot a dokumentumba. Ebben a példában oszlopdiagramot fogunk használni.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

## 5. lépés: Törölje a meglévő sorozatokat

Annak érdekében, hogy tiszta lappal induljon, törölje a diagramból a meglévő sorozatokat.

```csharp
chart.Series.Clear();
```

## 6. lépés: Adjon hozzá adatokat a diagramhoz

Itt adatokat adunk a diagramhoz. Ez magában foglalja a sorozat nevének és az adatpontok megadását.

```csharp
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2 });
```

## 7. lépés: Állítsa be a tengelyhatárokat

Az Y tengely határainak beállítása biztosítja a diagram megfelelő méretezését.

```csharp
chart.AxisY.Scaling.Minimum = new AxisBound(0);
chart.AxisY.Scaling.Maximum = new AxisBound(6);
```

## 8. lépés: Mentse el a dokumentumot

Végül mentse a dokumentumot a megadott könyvtárba.

```csharp
doc.Save(dataDir + "WorkingWithCharts.BoundsOfAxis.docx");
```

És ennyi! Sikeresen létrehozott egy dokumentumot diagrammal az Aspose.Words for .NET használatával. 

## Következtetés

Az Aspose.Words for .NET használatával egyszerűen hozhat létre és kezelhet diagramokat a dokumentumokban. Ez a lépésről lépésre bemutatott útmutató bemutatja, hogyan állíthatja be a tengely határait egy diagramon, így pontosabbá és professzionálisabbá teheti az adatok bemutatását. Akár jelentéseket, prezentációkat vagy bármilyen más dokumentumot készít, az Aspose.Words biztosítja a szükséges eszközöket.

## GYIK

### Mi az Aspose.Words for .NET?
Az Aspose.Words for .NET egy olyan könyvtár, amely lehetővé teszi Word-dokumentumok programozott létrehozását, módosítását és konvertálását a .NET-keretrendszer használatával.

### Hogyan állíthatom be az Aspose.Words for .NET-et?
 Letöltheti innen[itt](https://releases.aspose.com/words/net/)és kövesse a mellékelt telepítési utasításokat.

### Használhatom ingyenesen az Aspose.Words-t?
 Igen, használhatod a[ingyenes próbaverzió](https://releases.aspose.com/) vagy kap a[ideiglenes engedély](https://purchase.aspose.com/temporary-license/).

### Hol találom az Aspose.Words for .NET dokumentációját?
 A részletes dokumentáció elérhető[itt](https://reference.aspose.com/words/net/).

### Hogyan kaphatok támogatást az Aspose.Words számára?
 Meglátogathatja a[támogatási fórum](https://forum.aspose.com/c/words/8) segítségért.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
