---
title: Alak felülvizsgálata
linktitle: Alak felülvizsgálata
second_title: Aspose.Words Document Processing API
description: Ebből az átfogó útmutatóból megtudhatja, hogyan kezelheti a Word-dokumentumok alakváltozatait az Aspose.Words for .NET használatával. Sajátítsa el a változások követését, alakzatok beszúrását és egyebeket.
weight: 10
url: /hu/net/working-with-revisions/shape-revision/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Alak felülvizsgálata

## Bevezetés

Word-dokumentumok programozott szerkesztése ijesztő feladat lehet, különösen, ha alakzatok kezeléséről van szó. Akár jelentéseket készít, akár sablonokat tervez, akár egyszerűen automatizálja a dokumentumok létrehozását, az alakváltozatok nyomon követésének és kezelésének képessége döntő fontosságú. Az Aspose.Words for .NET hatékony API-t kínál, hogy ez a folyamat zökkenőmentes és hatékony legyen. Ebben az oktatóanyagban belemerülünk a Word-dokumentumok alakzatainak átdolgozásának sajátosságaiba, így biztosítva, hogy rendelkezzen a dokumentumok egyszerű kezeléséhez szükséges eszközökkel és ismeretekkel.

## Előfeltételek

Mielőtt belemerülnénk a kódba, győződjön meg arról, hogy mindennel rendelkezik, amire szüksége van:

-  Aspose.Words for .NET: Győződjön meg arról, hogy telepítve van az Aspose.Words könyvtár. Megteheti[töltse le itt](https://releases.aspose.com/words/net/).
- Fejlesztési környezet: Be kell állítania egy fejlesztői környezetet, például a Visual Studio-t.
- A C# alapismerete: A C# programozási nyelv ismerete és az objektum-orientált programozás alapfogalmai.
- Word-dokumentum: Word-dokumentum, amellyel dolgozni kell, vagy létrehozhat egyet az oktatóprogram során.

## Névterek importálása

Először is importáljuk a szükséges névtereket. Ezek hozzáférést biztosítanak számunkra a Word dokumentumok és alakzatok kezeléséhez szükséges osztályokhoz és módszerekhez.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## 1. lépés: A dokumentumkönyvtár beállítása

Mielőtt elkezdenénk az alakzatokkal dolgozni, meg kell határoznunk a dokumentumkönyvtárunk elérési útját. Ide mentjük a módosított dokumentumainkat.

```csharp
// A dokumentumok könyvtárának elérési útja.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 2. lépés: Új dokumentum létrehozása

Hozzon létre egy új Word-dokumentumot, amelyben alakzatokat szúrunk be és módosítunk.

```csharp
Document doc = new Document();
```

## 3. lépés: Inline alakzat beszúrása

Kezdjük azzal, hogy beszúrunk egy soros alakzatot a dokumentumunkba anélkül, hogy a revíziókat követnénk. A szövegközi alakzat az, amely a szöveggel együtt folyik.

```csharp
Shape shape = new Shape(doc, ShapeType.Cube);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## 4. lépés: A változatok követésének megkezdése

A dokumentumunk változásainak nyomon követéséhez engedélyeznünk kell a revíziókövetést. Ez elengedhetetlen az alakzatokon végrehajtott módosítások azonosításához.

```csharp
doc.StartTrackRevisions("John Doe");
```

## 5. lépés: Egy másik alakzat beszúrása felülvizsgálatokkal

Most, hogy a verziókövetés engedélyezve van, szúrjunk be egy másik alakzatot. Ezúttal minden változást nyomon követünk.

```csharp
shape = new Shape(doc, ShapeType.Sun);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## 6. lépés: Alakzatok visszakeresése és módosítása

A dokumentumban lévő összes alakzatot lekérhetjük és szükség szerint módosíthatjuk. Itt megkapjuk az alakzatokat, és eltávolítjuk az elsőt.

```csharp
List<Shape> shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
shapes[0].Remove();
```

## 7. lépés: A dokumentum mentése

módosítások elvégzése után el kell mentenünk a dokumentumot. Ez biztosítja az összes revízió és módosítás tárolását.

```csharp
doc.Save(dataDir + "Revision shape.docx");
```

## 8. lépés: Az alakmozgatási változatok kezelése

Ha egy alakzatot mozgat, az Aspose.Words ezt átdolgozásként követi nyomon. Ez azt jelenti, hogy az alakzatnak két példánya lesz: egy az eredeti helyén, egy pedig az új helyén.

```csharp
doc = new Document(dataDir + "Revision shape.docx");
shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
```

## Következtetés

És megvan! Sikeresen megtanulta, hogyan kell kezelni a Word dokumentumok alakváltozatait az Aspose.Words for .NET segítségével. Akár dokumentumsablonokat kezel, akár jelentéseket automatizál, akár egyszerűen nyomon követi a változásokat, ezek a készségek felbecsülhetetlen értékűek. A lépésenkénti útmutató követésével nemcsak az alapokat sajátította el, hanem betekintést nyert a fejlettebb dokumentumkezelési technikákba is.

## GYIK

### Mi az Aspose.Words for .NET?
Az Aspose.Words for .NET egy hatékony könyvtár, amely lehetővé teszi a fejlesztők számára Word-dokumentumok programozott C# használatával történő létrehozását, módosítását és konvertálását.

### Nyomon követhetem a Word-dokumentum más elemeinek módosításait?
Igen, az Aspose.Words for .NET támogatja a különféle elemek változásainak nyomon követését, beleértve a szöveget, táblázatokat és egyebeket.

### Hogyan szerezhetem be az Aspose.Words for .NET ingyenes próbaverzióját?
 Ingyenes próbaverziót kaphat az Aspose.Words for .NET-hez[itt](https://releases.aspose.com/).

### Lehetséges-e programozottan elfogadni vagy elutasítani a módosításokat?
Igen, az Aspose.Words for .NET módszereket biztosít a revíziók programozott elfogadására vagy elutasítására.

### Használhatom az Aspose.Words for .NET-et a C#-on kívül más .NET-nyelvekkel is?
Teljesen! Az Aspose.Words for .NET bármely .NET nyelvvel használható, beleértve a VB.NET-et és az F#-ot is.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
