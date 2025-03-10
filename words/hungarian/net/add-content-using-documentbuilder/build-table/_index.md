---
title: Táblázat összeállítása Word dokumentumban
linktitle: Táblázat összeállítása Word dokumentumban
second_title: Aspose.Words Document Processing API
description: Ebből a részletes, lépésenkénti oktatóanyagból megtudhatja, hogyan hozhat létre táblázatot Word-dokumentumban az Aspose.Words for .NET használatával. Kezdőknek és profiknak egyaránt tökéletes.
weight: 10
url: /hu/net/add-content-using-documentbuilder/build-table/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Táblázat összeállítása Word dokumentumban

## Bevezetés

Szia! Táblázatokat szeretne programozottan létrehozni Word-dokumentumaiban? Nos, jó helyre jött! Ma az Aspose.Words for .NET varázslatos világába merülünk. Ezzel a nagy teljesítményű könyvtárral profi módon kezelheti a Word dokumentumokat. Képzelje el, hogy Ön egy varázsló, és az Aspose.Words az Ön pálcája, amely lehetővé teszi, hogy egy csuklómozdulattal (vagy inkább egy kódsorral) hozzon létre, szerkeszthessen és formázzon dokumentumokat. Ebben az oktatóanyagban a táblázat Word-dokumentumban való felépítésére összpontosítunk. Szóval, fogd meg a kódoló kalapot, és kezdjük is!

## Előfeltételek

Mielőtt nekivágnánk az asztalépítési kalandunknak, győződjünk meg arról, hogy az összes kacsánkat egy sorban megvan. Íme, amire szüksége van:

- Visual Studio (vagy bármely más C# IDE)
- .NET-keretrendszer (4.0 vagy újabb)
- Aspose.Words a .NET könyvtárhoz

 Ha még nincs Aspose.Words, könnyen megteheti[töltse le itt](https://releases.aspose.com/words/net/) . Kezdheti a-val is[ingyenes próbaverzió](https://releases.aspose.com/) ha tesztelni akarja a vizeket. Azok számára, akik készen állnak a lépésre, megtehetik[vásároljon licencet](https://purchase.aspose.com/buy) vagy ha több időre van szüksége az értékeléshez, ragadjon meg a[ideiglenes engedély](https://purchase.aspose.com/temporary-license/).

## Névterek importálása

Először is tegyük rendbe a névtereinket. Ez a lépés olyan, mint a színpad felállítása a nagy előadás előtt. Adja hozzá a következő névtereket a C# fájlhoz:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Tables;
```

Rendben, bontsuk fel kezelhető lépésekre a táblázat létrehozásának folyamatát egy Word-dokumentumban. Tekintsd ezt úgy, mint egy bútor összeszerelését – egyszerre csak egy csavart és csavart fogunk.

## 1. lépés: Inicializálja a Dokumentumot és a DocumentBuildert

 Először is be kell állítanunk a dokumentumunkat és a dokumentumkészítőnket. A`Document` osztály képviseli a Word dokumentumot, és`DocumentBuilder` a mi praktikus eszközünk tartalom hozzáadásához.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Képzelje el ezt úgy, hogy a festés megkezdése előtt lefekteti a vásznat. A`DocumentBuilder` az ecsetünk, amely készen áll egy remekmű létrehozására.

## 2. lépés: Indítsa el a táblázatot

 Most pedig kezdjük le az asztalunkat. Hívjuk a`StartTable` módszere a`DocumentBuilder` kezdeni.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
table.AutoFit(AutoFitBehavior.FixedColumnWidths);
```

 Használatával`StartTable` , azt mondjuk Aspose-nak.Szavak, hogy egy táblázat létrehozására készülünk. A`InsertCell` metódus hozzáadja az első cellát, és`AutoFit` biztosítja oszlopaink rögzített szélességét.

## 3. lépés: Formázza meg az első sort

Fűszerezzük az első sort egy kis szöveg hozzáadásával, és függőlegesen a középponthoz igazítva.

```csharp
builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;
builder.Write("This is row 1 cell 1");

builder.InsertCell();
builder.Write("This is row 1 cell 2");

builder.EndRow();
```

Gondolj erre úgy, mint az abrosz megterítésére és az első edények elhelyezésére. Gondoskodunk róla, hogy minden rendben és rendezett legyen.

## 4. lépés: Hozza létre a második sort egyéni formázással

Legyünk kreatívak a második sorral. Beállítjuk a sor magasságát, másképp igazítjuk a szöveget, és a szöveg tájolásának megváltoztatásával némi finomságot adunk.

```csharp
builder.InsertCell();

builder.RowFormat.Height = 100;
builder.RowFormat.HeightRule = HeightRule.Exactly;
builder.CellFormat.Orientation = TextOrientation.Upward;
builder.Writeln("This is row 2 cell 1");

builder.InsertCell();
builder.CellFormat.Orientation = TextOrientation.Downward;
builder.Writeln("This is row 2 cell 2");

builder.EndRow();
```

 Itt beállítjuk a sor magasságát, és biztosítjuk, hogy rögzítve maradjon`HeightRule.Exactly`. A szövegtájolás változásai kiemelik a táblázatunkat, egy kis egyediséget adva.

## 5. lépés: Zárja be a táblázatot

Miután soraink készen vannak, itt az ideje, hogy lezárjuk a táblázat létrehozási folyamatát.

```csharp
builder.EndTable();
```

Ez a lépés olyan, mintha az utolsó simításokat adnánk a műalkotásunkhoz. Az asztal szerkezete kész és használatra kész.

## 6. lépés: Mentse el a dokumentumot

 Végül mentsük el a dokumentumunkat. Válasszon egy helyet és egy nevet a fájlnak, majd mentse el a`.docx` kiterjesztés.

```csharp
doc.Save("YourDirectoryPath/AddContentUsingDocumentBuilder.BuildTable.docx");
```

Tekintsd ezt úgy, mint a remekművünket keretbe foglalva és bemutatni. A táblázat most egy Word-dokumentum része, készen áll a megosztásra és a csodálásra.

## Következtetés

És megvan! Sikeresen összeállított egy táblázatot egy Word-dokumentumban az Aspose.Words for .NET használatával. Ez az oktatóanyag végigvezeti Önt minden lépésen, a dokumentum inicializálásától a végtermék mentéséig. Az Aspose.Words segítségével a lehetőségek végtelenek. Függetlenül attól, hogy jelentéseket, számlákat vagy bármilyen más dokumentumot hoz létre, most lehetősége nyílik a táblázatok tetszés szerinti formázására és testreszabására.

Ne feledje, gyakorlat teszi a mestert. Tehát ne habozzon kísérletezni a különböző táblázatformátumokkal és -stílusokkal. Boldog kódolást!

## GYIK

### Mi az Aspose.Words for .NET?
Az Aspose.Words for .NET egy hatékony könyvtár Word-dokumentumokkal való programozott munkavégzéshez. Lehetővé teszi dokumentumok létrehozását, szerkesztését és kezelését Microsoft Word nélkül.

### Hogyan telepíthetem az Aspose.Words for .NET fájlt?
 Megteheti[töltse le az Aspose.Words for .NET-et innen](https://releases.aspose.com/words/net/)Kövesse a mellékelt telepítési utasításokat a fejlesztői környezetben történő beállításához.

### Használhatom ingyenesen az Aspose.Words-t?
 Az Aspose.Words ajánlatok a[ingyenes próbaverzió](https://releases.aspose.com/) így tesztelheti a tulajdonságait. Hosszabb idejű használathoz licencet vásárolhat, vagy a[ideiglenes engedély](https://purchase.aspose.com/temporary-license/).

### Milyen egyéb szolgáltatásai vannak az Aspose.Words for .NET-nek?
A táblázatok létrehozása mellett az Aspose.Words lehetővé teszi szövegekkel, képekkel, stílusokkal és sok más dokumentumelemmel való munkát. A dokumentumformátumok széles skáláját támogatja, beleértve a DOCX-et, a PDF-t és a HTML-t.

### Hol kaphatok segítséget, ha problémákba ütközöm?
 Ha támogatásra van szüksége, nézze meg a[Aspose.Words fórum](https://forum.aspose.com/c/words/8) ahol kérdéseket tehet fel, és segítséget kérhet a közösségtől és az Aspose fejlesztőitől.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
