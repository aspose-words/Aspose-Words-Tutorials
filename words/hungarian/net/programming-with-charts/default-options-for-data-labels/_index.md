---
title: Állítsa be az adatcímkék alapértelmezett beállításait egy diagramon
linktitle: Állítsa be az adatcímkék alapértelmezett beállításait egy diagramon
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan állíthat be alapértelmezett beállításokat a diagramok adatcímkéihez az Aspose.Words for .NET használatával. Kövesse lépésenkénti útmutatónkat a diagramok egyszerű létrehozásához és testreszabásához.
weight: 10
url: /hu/net/programming-with-charts/default-options-for-data-labels/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Állítsa be az adatcímkék alapértelmezett beállításait egy diagramon

## Bevezetés

Szia! Izgatottan várod, hogy belemerülj a dokumentumautomatizálás világába? Ma azt vizsgáljuk meg, hogyan használhatjuk az Aspose.Words for .NET-et lenyűgöző dokumentumok programozott létrehozására. Az Aspose.Words egy hatékony könyvtár, amely lehetővé teszi a Word-dokumentumok egyszerű kezelését, és ebben az oktatóanyagban a diagramon szereplő adatcímkék alapértelmezett beállításainak beállítására összpontosítunk. Akár tapasztalt fejlesztő, akár kezdő, ez az útmutató végigvezeti Önt minden lépésen, hogy pillanatok alatt elinduljon.

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy minden szükséges eszközzel rendelkezik az oktatóanyag követéséhez. Íme egy gyors ellenőrző lista:

- Visual Studio vagy bármely más .NET-kompatibilis IDE: Itt írhatja és futtathatja a kódot.
-  Aspose.Words for .NET: Megteheti[töltse le a legújabb verziót](https://releases.aspose.com/words/net/) és telepítse a projektjébe.
- Alapvető ismeretek a C# programozásról: Bár ez az útmutató kezdők számára készült, hasznos lesz egy kis C# ismerete.
- .NET-keretrendszer telepítve: Győződjön meg arról, hogy a .NET-keretrendszer be van állítva a számítógépen.
-  Ideiglenes licenc az Aspose.Words számára: Szerezzen egyet[itt](https://purchase.aspose.com/temporary-license/) a teljes funkcionalitás feloldásához.

Ha ezeket az előfeltételeket rendezte, készen állunk a görgetésre!

## Névterek importálása

Először is állítsuk be projektünket, és importáljuk a szükséges névtereket. Ezek a névterek kulcsfontosságúak az Aspose.Words funkció eléréséhez.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.ReportingServices;
```

## 1. lépés: Hozzon létre egy új dokumentumot


 Az út egy új dokumentum létrehozásával és inicializálásával kezdődik`DocumentBuilder` . A`DocumentBuilder` osztály módszerkészletet biztosít a dokumentumtartalom egyszerű kezeléséhez.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Hozzon létre egy új dokumentumot
Document doc = new Document();

// Inicializálja a DocumentBuilder programot
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Magyarázat

 Ebben a lépésben beállítottuk a dokumentumot és az építőt, amelyet a tartalom beszúrásához és formázásához használunk. A`dataDir` változó tartalmazza azt az elérési utat, ahová a végleges dokumentumunkat menteni fogjuk.

## 2. lépés: Helyezzen be egy diagramot

 Ezután egy kördiagramot adunk a dokumentumunkhoz. A`InsertChart` módszere a`DocumentBuilder` osztály ezt rendkívül egyszerűvé teszi.

```csharp
// Helyezzen be egy kördiagramot
Shape shape = builder.InsertChart(ChartType.Pie, 432, 252);

// Hozzáférés a diagram objektumhoz
Chart chart = shape.Chart;
```

### Magyarázat

Itt egy kördiagramot illesztünk be a dokumentumunkba. A`InsertChart` metódus a diagram típusát, szélességét és magasságát igényli paraméterként. A diagram beillesztése után hozzáférünk a diagram objektumhoz, hogy tovább manipulálhassuk.

## 3. lépés: A diagramsorozat testreszabása

Most töröljük a diagramon szereplő összes meglévő sorozatot, és hozzáadjuk egyéni sorozatainkat. Ez a sorozat az adatpontjainkat fogja képviselni.

```csharp
// Meglévő diagramsorozatok törlése
chart.Series.Clear();

// Új sorozat hozzáadása a diagramhoz
ChartSeries series = chart.Series.Add("Aspose Series 1",
    new string[] { "Category 1", "Category 2", "Category 3" },
    new double[] { 2.7, 3.2, 0.8 });
```

### Magyarázat

Ebben a lépésben a már létező sorozatok törlésével biztosítjuk, hogy a diagram üres legyen. Ezután hozzáadunk egy új sorozatot egyéni kategóriákkal és értékekkel, amelyek megjelennek a kördiagramunkban.

## 4. lépés: Állítsa be az adatcímkék alapértelmezett beállításait

Az adatcímkék elengedhetetlenek ahhoz, hogy a diagram informatív legyen. Beállítjuk a százalékos értékek és az értékek megjelenítésére vonatkozó beállításokat, valamint testreszabjuk az elválasztót.

```csharp
// Hozzáférés az adatcímkék gyűjteményéhez
ChartDataLabelCollection labels = series.DataLabels;

// Adja meg az adatcímkék beállításait
labels.ShowPercentage = true;
labels.ShowValue = true;
labels.ShowLeaderLines = false;
labels.Separator = " - ";
```

### Magyarázat

 Itt elérjük a`DataLabels`sorozatunk tulajdonsága, hogy személyre szabhassa az egyes adatcímkéken megjelenő megjelenést és információkat. Úgy döntöttünk, hogy mind a százalékot, mind az értéket megjelenítjük, elrejtjük a vezetővonalakat, és beállítunk egy egyéni elválasztót.

## 5. lépés: Mentse el a dokumentumot

Végül elmentjük a dokumentumunkat a megadott könyvtárba. Ez a lépés biztosítja, hogy minden módosításunk egy fájlba kerüljön.

```csharp
// Mentse el a dokumentumot
doc.Save(dataDir + "WorkingWithCharts.DefaultOptionsForDataLabels.docx");
```

### Magyarázat

 Ebben az utolsó lépésben a dokumentumot a`Save` módszer. A dokumentum a által megadott könyvtárba kerül mentésre`dataDir`, "WorkingWithCharts.DefaultOptionsForDataLabels.docx" néven.

## Következtetés

És megvan! Sikeresen létrehozott egy Word-dokumentumot testreszabott kördiagrammal az Aspose.Words for .NET használatával. Ez a nagy teljesítményű könyvtár megkönnyíti a dokumentumok létrehozásának és kezelésének automatizálását, így időt és erőfeszítést takarít meg. Akár jelentéseket, számlákat vagy bármilyen más típusú dokumentumot készít, az Aspose.Words mindenre kiterjed.

 Nyugodtan fedezze fel a[Aspose.Words dokumentáció](https://reference.aspose.com/words/net/) további funkciókért és példákért. Boldog kódolást!

## GYIK

### Használhatom ingyenesen az Aspose.Words-t?
Az Aspose.Words ingyenesen használható a[ideiglenes engedély](https://purchase.aspose.com/temporary-license/) vagy fedezze fel funkcióit a segítségével[ingyenes próbaverzió](https://releases.aspose.com/).

### Hogyan kaphatok támogatást az Aspose.Words számára?
 A támogatást a[Aspose.Words támogatási fórum](https://forum.aspose.com/c/words/8).

### Hozzáadhatok más típusú diagramokat?
 Igen, az Aspose.Words különféle diagramtípusokat támogat, például sáv-, vonal- és oszlopdiagramokat. Ellenőrizze a[dokumentáció](https://reference.aspose.com/words/net/) további részletekért.

### Az Aspose.Words kompatibilis a .NET Core-al?
 Igen, az Aspose.Words kompatibilis a .NET Core-al. További információt a[dokumentáció](https://reference.aspose.com/words/net/).

### Hogyan vásárolhatok licencet az Aspose.Words számára?
 Engedélyt vásárolhat a[Aspose üzlet](https://purchase.aspose.com/buy).


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
