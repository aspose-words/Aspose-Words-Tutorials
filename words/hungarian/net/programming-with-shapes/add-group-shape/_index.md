---
"description": "Tanulja meg, hogyan adhat hozzá csoportos alakzatokat Word-dokumentumokhoz az Aspose.Words for .NET használatával ebből az átfogó, lépésről lépésre haladó oktatóanyagból."
"linktitle": "Csoport alakzat hozzáadása"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Csoport alakzat hozzáadása"
"url": "/hu/net/programming-with-shapes/add-group-shape/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Csoport alakzat hozzáadása

## Bevezetés

Gazdag vizuális elemekkel rendelkező, összetett dokumentumok létrehozása néha ijesztő feladat lehet, különösen csoportos alakzatok esetén. De ne félj! Az Aspose.Words for .NET leegyszerűsíti ezt a folyamatot, gyerekjátékká téve. Ebben az oktatóanyagban végigvezetünk a Word-dokumentumokhoz való csoportos alakzatok hozzáadásának lépésein. Készen állsz a belevágni? Kezdjük is!

## Előfeltételek

Mielőtt elkezdenénk, győződjünk meg arról, hogy a következőkkel rendelkezünk:

1. Aspose.Words .NET-hez: Letöltheti innen: [Aspose kiadási oldal](https://releases.aspose.com/words/net/).
2. Fejlesztői környezet: Visual Studio vagy bármilyen más .NET-tel kompatibilis IDE.
3. C# alapismeretek: A C# programozásban való jártasság előnyt jelent.

## Névterek importálása

Kezdésként importálnunk kell a szükséges névtereket a projektünkbe. Ezek a névterek hozzáférést biztosítanak azokhoz az osztályokhoz és metódusokhoz, amelyek a Word dokumentumok Aspose.Words segítségével történő kezeléséhez szükségesek.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## 1. lépés: A dokumentum inicializálása

Először is, inicializáljunk egy új Word-dokumentumot. Gondoljunk erre úgy, mintha egy üres vászon hoznánk létre, ahová majd hozzáadjuk a csoportos alakzatokat.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
doc.EnsureMinimum();
```

Itt, `EnsureMinimum()` hozzáadja a dokumentumhoz szükséges minimális csomópont-készletet.

## 2. lépés: A GroupShape objektum létrehozása

Ezután létre kell hoznunk egy `GroupShape` objektum. Ez az objektum tárolóként szolgál majd más alakzatok számára, lehetővé téve számunkra, hogy csoportosítsuk őket.

```csharp
GroupShape groupShape = new GroupShape(doc);
```

## 3. lépés: Alakzatok hozzáadása a GroupShape-hez

Most adjunk hozzá egyedi alakzatokat a miénkhez `GroupShape` konténer. Először egy hangsúlyos szegélyformát használunk, majd hozzáadunk egy műveletgomb alakzatot.

### Ékezeti szegély alakjának hozzáadása

```csharp
Shape accentBorderShape = new Shape(doc, ShapeType.AccentBorderCallout1)
{
    Width = 100,
    Height = 100
};
groupShape.AppendChild(accentBorderShape);
```

Ez a kódrészlet egy 100 egység szélességű és magasságú hangsúlyos szegélyformát hoz létre, és hozzáadja a `GroupShape`.

### Műveletgomb alakzat hozzáadása

```csharp
Shape actionButtonShape = new Shape(doc, ShapeType.ActionButtonBeginning)
{
    Left = 100,
    Width = 100,
    Height = 200
};
groupShape.AppendChild(actionButtonShape);
```

Itt létrehozunk egy akciógomb alakzatot, elhelyezzük, és hozzáadjuk a `GroupShape`.

## 4. lépés: A GroupShape méreteinek meghatározása

Ahhoz, hogy alakzataink jól illeszkedjenek a csoportba, meg kell adnunk a méreteit. `GroupShape`.

```csharp
groupShape.Width = 200;
groupShape.Height = 200;
groupShape.CoordSize = new Size(200, 200);
```

Ez határozza meg a szélességét és magasságát `GroupShape` 200 egységként, és ennek megfelelően állítja be a koordinátaméretet.

## 5. lépés: A GroupShape beillesztése a dokumentumba

Most pedig illesszük be a miénket `GroupShape` a dokumentumba a következő használatával: `DocumentBuilder`.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.InsertNode(groupShape);
```

`DocumentBuilder` egyszerű módot kínál csomópontok, beleértve az alakzatokat is, hozzáadására a dokumentumhoz.

## 6. lépés: A dokumentum mentése

Végül mentse el a dokumentumot a megadott könyvtárba.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddGroupShape.docx");
```

És íme! Kész is a csoportos alakzatokat tartalmazó dokumentum.

## Következtetés

A csoportos alakzatok hozzáadása a Word-dokumentumokhoz nem kell, hogy bonyolult folyamat legyen. Az Aspose.Words for .NET segítségével könnyedén hozhatsz létre és manipulálhatsz alakzatokat, így dokumentumaid vizuálisan vonzóbbak és funkcionálisabbak lesznek. Kövesd az ebben az oktatóanyagban ismertetett lépéseket, és pillanatok alatt profi leszel!

## GYIK

### Hozzáadhatok kettőnél több alakzatot egy GroupShape-hoz?
Igen, annyi alakzatot adhatsz hozzá, amennyire szükséged van. `GroupShape`Csak használd a `AppendChild` módszer minden alakzathoz.

### Lehetséges formázni az alakzatokat egy GroupShape-en belül?
Természetesen! Minden alakzat egyedileg formázható a rendelkezésre álló tulajdonságok használatával. `Shape` osztály.

### Hogyan tudom elhelyezni a GroupShape-et a dokumentumban?
Elhelyezheti a `GroupShape` beállításával `Left` és `Top` tulajdonságok.

### Hozzáadhatok szöveget az alakzatokhoz a GroupShape-en belül?
Igen, szöveget adhatsz hozzá alakzatokhoz a `AppendChild` módszer egy hozzáadására `Paragraph` tartalmazó `Run` szöveggel ellátott csomópontok.

### Lehetséges az alakzatokat dinamikusan csoportosítani a felhasználói bevitel alapján?
Igen, dinamikusan létrehozhat és csoportosíthat alakzatokat a felhasználói bevitel alapján a tulajdonságok és metódusok megfelelő módosításával.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}