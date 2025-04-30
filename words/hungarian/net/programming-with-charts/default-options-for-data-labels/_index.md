---
"description": "Tanuld meg, hogyan állíthatod be az adatcímkék alapértelmezett beállításait egy diagramban az Aspose.Words for .NET használatával. Kövesd lépésről lépésre szóló útmutatónkat a diagramok egyszerű létrehozásához és testreszabásához."
"linktitle": "Diagram adatcímkéinek alapértelmezett beállításainak megadása"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Diagram adatcímkéinek alapértelmezett beállításainak megadása"
"url": "/hu/net/programming-with-charts/default-options-for-data-labels/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Diagram adatcímkéinek alapértelmezett beállításainak megadása

## Bevezetés

Sziasztok! Izgatottan várjátok, hogy belevágjatok a dokumentumautomatizálás világába? Ma azt fogjuk felfedezni, hogyan használhatjátok az Aspose.Words for .NET-et lenyűgöző dokumentumok programozott létrehozásához. Az Aspose.Words egy hatékony függvénykönyvtár, amely lehetővé teszi a Word-dokumentumok egyszerű kezelését, és ebben az oktatóanyagban a diagramok adatcímkéinek alapértelmezett beállításainak megadására fogunk összpontosítani. Akár tapasztalt fejlesztő vagy, akár kezdő, ez az útmutató végigvezet a lépéseken, hogy pillanatok alatt elkezdhessétek a munkát.

## Előfeltételek

Mielőtt belekezdenénk, győződjünk meg róla, hogy minden megvan, amire szükséged van ehhez az oktatóanyaghoz. Íme egy gyors ellenőrzőlista:

- Visual Studio vagy bármely más .NET-kompatibilis IDE: Itt fogod megírni és futtatni a kódodat.
- Aspose.Words .NET-hez: Meg tudod csinálni [töltsd le a legújabb verziót](https://releases.aspose.com/words/net/) és telepítsd a projektedbe.
- C# programozási alapismeretek: Bár ez az útmutató kezdőknek szól, egy kis C# ismeretség hasznos lehet.
- Telepített .NET-keretrendszer: Győződjön meg arról, hogy a .NET-keretrendszer telepítve van a gépén.
- Ideiglenes licenc az Aspose.Words-hez: Szerezz egyet [itt](https://purchase.aspose.com/temporary-license/) a teljes funkcionalitás feloldásához.

Miután ezeket az előfeltételeket rendezted, készen állunk a kezdésre!

## Névterek importálása

Először is, állítsuk be a projektünket, és importáljuk a szükséges névtereket. Ezek a névterek elengedhetetlenek az Aspose.Words funkcionalitásának eléréséhez.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.ReportingServices;
```

## 1. lépés: Új dokumentum létrehozása


Az utazás egy új dokumentum létrehozásával és inicializálásával kezdődik. `DocumentBuilder`. A `DocumentBuilder` Az osztály metódusokat biztosít a dokumentum tartalmának egyszerű kezeléséhez.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Új dokumentum létrehozása
Document doc = new Document();

// DocumentBuilder inicializálása
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Magyarázat

Ebben a lépésben beállítottuk a dokumentumot és a tartalomszerkesztőt, amelyet a tartalom beszúrásához és formázásához fogunk használni. `dataDir` változó tartalmazza azt az elérési utat, ahová a végső dokumentumot menteni fogjuk.

## 2. lépés: Diagram beszúrása

Ezután hozzáadunk egy kördiagramot a dokumentumunkhoz. `InsertChart` a módszer `DocumentBuilder` az osztály ezt szuper könnyűvé teszi.

```csharp
// Kördiagram beszúrása
Shape shape = builder.InsertChart(ChartType.Pie, 432, 252);

// Hozzáférés a diagram objektumhoz
Chart chart = shape.Chart;
```

### Magyarázat

Itt egy kördiagramot szúrunk be a dokumentumunkba. `InsertChart` A metódus paraméterként kéri a diagram típusát, szélességét és magasságát. A diagram beillesztése után hozzáférünk a diagram objektumhoz a további manipulációhoz.

## 3. lépés: A diagramsorozat testreszabása

Most töröljük a diagramon található összes meglévő sorozatot, és hozzáadjuk az egyéni sorozatunkat. Ez a sorozat fogja az adatpontjainkat ábrázolni.

```csharp
// Meglévő diagramsorozat törlése
chart.Series.Clear();

// Új sorozat hozzáadása a diagramhoz
ChartSeries series = chart.Series.Add("Aspose Series 1",
    new string[] { "Category 1", "Category 2", "Category 3" },
    new double[] { 2.7, 3.2, 0.8 });
```

### Magyarázat

Ebben a lépésben gondoskodunk arról, hogy a diagramunk üres legyen, ezért töröljük a már meglévő sorozatokat. Ezután hozzáadunk egy új sorozatot egyéni kategóriákkal és értékekkel, amelyek megjelennek a kördiagramon.

## 4. lépés: Az adatcímkék alapértelmezett beállításainak megadása

Az adatcímkék elengedhetetlenek ahhoz, hogy a diagram informatív legyen. Beállítjuk a százalékos és érték megjelenítését, valamint testreszabjuk az elválasztójelet.

```csharp
// Hozzáférés az adatcímkék gyűjteményéhez
ChartDataLabelCollection labels = series.DataLabels;

// Adatcímke-beállítások megadása
labels.ShowPercentage = true;
labels.ShowValue = true;
labels.ShowLeaderLines = false;
labels.Separator = " - ";
```

### Magyarázat

Itt férünk hozzá a `DataLabels` tulajdonságát használjuk az egyes adatcímkék megjelenésének és az azokon megjelenített információk testreszabásához. Úgy döntöttünk, hogy megjelenítjük a százalékos értéket és az értéket is, elrejtjük a vezető vonalakat, és egyéni elválasztót állítunk be.

## 5. lépés: A dokumentum mentése

Végül mentsük el a dokumentumot a megadott könyvtárba. Ez a lépés biztosítja, hogy minden módosításunk fájlba kerüljön.

```csharp
// Mentse el a dokumentumot
doc.Save(dataDir + "WorkingWithCharts.DefaultOptionsForDataLabels.docx");
```

### Magyarázat

Ebben az utolsó lépésben a következővel mentjük el a dokumentumot: `Save` metódus. A dokumentum a megadott könyvtárba lesz mentve. `dataDir`, a következő néven: „WorkingWithCharts.DefaultOptionsForDataLabels.docx”.

## Következtetés

És íme! Sikeresen létrehoztál egy Word dokumentumot testreszabott kördiagrammal az Aspose.Words for .NET segítségével. Ez a hatékony könyvtár megkönnyíti a dokumentumok létrehozásának és kezelésének automatizálását, így időt és energiát takarít meg. Akár jelentéseket, számlákat vagy bármilyen más típusú dokumentumot generálsz, az Aspose.Words segít neked.

Nyugodtan fedezd fel a [Aspose.Words dokumentáció](https://reference.aspose.com/words/net/) további funkciókért és példákért. Jó kódolást!

## GYIK

### Ingyenesen használhatom az Aspose.Words-öt?
Az Aspose.Words-öt ingyenesen használhatod egy [ideiglenes engedély](https://purchase.aspose.com/temporary-license/) vagy fedezze fel a funkcióit a [ingyenes próba](https://releases.aspose.com/).

### Hogyan kaphatok támogatást az Aspose.Words-höz?
Támogatást kaphatsz a következőn keresztül: [Aspose.Words támogatói fórum](https://forum.aspose.com/c/words/8).

### Hozzáadhatok más típusú diagramokat is?
Igen, az Aspose.Words különféle diagramtípusokat támogat, például sáv-, vonal- és oszlopdiagramokat. Ellenőrizze a [dokumentáció](https://reference.aspose.com/words/net/) további részletekért.

### Kompatibilis az Aspose.Words a .NET Core-ral?
Igen, az Aspose.Words kompatibilis a .NET Core-ral. További információkat a következő helyen talál. [dokumentáció](https://reference.aspose.com/words/net/).

### Hogyan vásárolhatok licencet az Aspose.Words-höz?
Licenc vásárlása a következő címen lehetséges: [Aspose áruház](https://purchase.aspose.com/buy).




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}