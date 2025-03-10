---
title: Csoportalak hozzáadása
linktitle: Csoportalak hozzáadása
second_title: Aspose.Words Document Processing API
description: Ezzel az átfogó, lépésenkénti oktatóanyaggal megtudhatja, hogyan adhat hozzá csoportalakzatokat Word-dokumentumokhoz az Aspose.Words for .NET segítségével.
weight: 10
url: /hu/net/programming-with-shapes/add-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Csoportalak hozzáadása

## Bevezetés

gazdag vizuális elemekkel rendelkező összetett dokumentumok létrehozása néha ijesztő feladat lehet, különösen csoportos alakzatok kezelésekor. De ne félj! Az Aspose.Words for .NET leegyszerűsíti ezt a folyamatot, és olyan egyszerűvé teszi, mint a torta. Ebben az oktatóanyagban végigvezetjük azokat a lépéseket, amelyekkel csoportalakzatokat adhat hozzá Word-dokumentumaihoz. Készen állsz a merülésre? Kezdjük is!

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik az alábbiakkal:

1.  Aspose.Words for .NET: Letöltheti a[Az Aspose kiadási oldala](https://releases.aspose.com/words/net/).
2. Fejlesztői környezet: Visual Studio vagy bármely más, .NET-tel kompatibilis IDE.
3. Alapvető C# ismerete: A C# programozás ismerete előnyt jelent.

## Névterek importálása

A kezdéshez importálnunk kell a szükséges névtereket a projektünkbe. Ezek a névterek hozzáférést biztosítanak az Aspose.Words Word-dokumentumok kezeléséhez szükséges osztályokhoz és metódusokhoz.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## 1. lépés: Inicializálja a dokumentumot

Először is inicializáljunk egy új Word-dokumentumot. Gondoljon erre úgy, mint egy üres vászon létrehozására, amelyhez hozzáadjuk a csoport alakzatait.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
doc.EnsureMinimum();
```

 Itt,`EnsureMinimum()` hozzáad egy minimális csomópontkészletet, amely a dokumentumhoz szükséges.

## 2. lépés: Hozza létre a GroupShape objektumot

 Ezután létre kell hoznunk a`GroupShape`objektum. Ez az objektum tárolóként fog szolgálni más formák számára, lehetővé téve, hogy csoportosítsuk őket.

```csharp
GroupShape groupShape = new GroupShape(doc);
```

## 3. lépés: Adjon hozzá alakzatokat a GroupShape-hoz

 Most pedig adjunk hozzá egyedi alakzatokat`GroupShape` tartály. Kezdjük egy ékezetes szegély alakzattal, majd adjunk hozzá egy műveletgomb alakzatot.

### Kiemelt szegélyforma hozzáadása

```csharp
Shape accentBorderShape = new Shape(doc, ShapeType.AccentBorderCallout1)
{
    Width = 100,
    Height = 100
};
groupShape.AppendChild(accentBorderShape);
```

 Ez a kódrészlet 100 egység szélességű és magasságú hangsúlyos szegély alakzatot hoz létre, és hozzáadja a`GroupShape`.

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

 Itt létrehozunk egy műveletgomb alakzatot, elhelyezzük, és hozzáadjuk a sajátunkhoz`GroupShape`.

## 4. lépés: Határozza meg a GroupShape dimenzióit

 Annak érdekében, hogy alakjaink jól illeszkedjenek a csoportba, meg kell határoznunk a méreteit`GroupShape`.

```csharp
groupShape.Width = 200;
groupShape.Height = 200;
groupShape.CoordSize = new Size(200, 200);
```

 Ez határozza meg a szélességét és magasságát`GroupShape` 200 egységként, és ennek megfelelően állítja be a koordináta méretét.

## 5. lépés: Illessze be a GroupShape elemet a dokumentumba

 Most pedig illesszük be a mi`GroupShape` segítségével a dokumentumba`DocumentBuilder`.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.InsertNode(groupShape);
```

`DocumentBuilder` egyszerű módot kínál csomópontok, köztük alakzatok hozzáadására a dokumentumhoz.

## 6. lépés: Mentse el a dokumentumot

Végül mentse a dokumentumot a megadott könyvtárba.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddGroupShape.docx");
```

És megvan! A csoport alakzatokat tartalmazó dokumentum készen áll.

## Következtetés

Csoportalakzatok hozzáadása a Word-dokumentumokhoz nem kell, hogy bonyolult folyamat legyen. Az Aspose.Words for .NET segítségével könnyedén hozhat létre és kezelhet alakzatokat, így dokumentumai látványosabbá és funkcionálisabbá válnak. Kövesse az oktatóanyagban leírt lépéseket, és pillanatok alatt profi lesz!

## GYIK

### Hozzáadhatok kettőnél több alakzatot egy GroupShape-hoz?
 Igen, annyi alakzatot adhat hozzá a`GroupShape` . Csak használja a`AppendChild` módszer minden alakzathoz.

### Lehetséges-e stílusozni az alakzatokat egy GroupShape-en belül?
 Teljesen! Minden alakzat egyedileg formázható a következőben elérhető tulajdonságok segítségével`Shape` osztály.

### Hogyan helyezhetem el a GroupShape-ot a dokumentumban?
 Elhelyezheti a`GroupShape` beállításával`Left` és`Top` tulajdonságait.

### Hozzáadhatok szöveget az alakzatokhoz a GroupShape-en belül?
 Igen, szöveget adhat az alakzatokhoz a`AppendChild` módszer hozzáadásához a`Paragraph` tartalmazó`Run` csomópontok szöveggel.

### Lehetséges az alakzatok dinamikus csoportosítása a felhasználói bevitel alapján?
Igen, dinamikusan hozhat létre és csoportosíthat alakzatokat a felhasználói bevitel alapján a tulajdonságok és módszerek megfelelő beállításával.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
