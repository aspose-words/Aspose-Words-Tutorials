---
title: Elrendezés cellában
linktitle: Elrendezés cellában
second_title: Aspose.Words Document Processing API
description: Ebből az átfogó útmutatóból megtudhatja, hogyan állíthatja be az elrendezést a cellában az Aspose.Words for .NET használatával. Tökéletes azoknak a fejlesztőknek, akik a Word dokumentumokat szeretnék testre szabni.
weight: 10
url: /hu/net/programming-with-shapes/layout-in-cell/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Elrendezés cellában

## Bevezetés

Ha valaha is szerette volna programozottan finomhangolni a Word-dokumentumok táblázatcelláinak elrendezését, akkor jó helyen jár. Ma elmerülünk a cellák elrendezésének beállításában az Aspose.Words for .NET használatával. Végigjárunk egy gyakorlati példát, lépésről lépésre lebontva, hogy könnyedén követhesse.

## Előfeltételek

Mielőtt belevágnánk a kódba, győződjünk meg arról, hogy mindennel rendelkezik, amire szüksége van:

1.  Aspose.Words for .NET: Győződjön meg arról, hogy telepítve van az Aspose.Words for .NET könyvtár. Ha nem, akkor megteheti[töltse le itt](https://releases.aspose.com/words/net/).
2. Fejlesztői környezet: Szüksége lesz egy .NET-tel beállított fejlesztői környezetre. A Visual Studio nagyszerű választás, ha ajánlásokat keres.
3. Alapvető C# ismerete: Bár minden lépést elmagyarázok, a C# alapvető ismerete segít a könnyebb követésben.
4.  Dokumentumkönyvtár: Készítsen egy könyvtár elérési utat, ahová a dokumentumokat mentheti. Ezt úgy fogjuk hivatkozni`YOUR DOCUMENT DIRECTORY`.

## Névterek importálása

kezdéshez győződjön meg róla, hogy importálja a szükséges névtereket a projektben:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Bontsuk fel a folyamatot kezelhető lépésekre.

## 1. lépés: Hozzon létre egy új dokumentumot

 Először létrehozunk egy új Word-dokumentumot, és inicializáljuk a`DocumentBuilder` tárgyat, hogy segítsen nekünk a tartalom megalkotásában.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 2. lépés: Indítson el egy táblázatot, és állítsa be a sorformátumot

Elkezdjük összeállítani a táblázatot, és megadjuk a sorok magassági és magassági szabályait.

```csharp
builder.StartTable();
builder.RowFormat.Height = 100;
builder.RowFormat.HeightRule = HeightRule.Exactly;
```

## 3. lépés: Cellák beszúrása és tartalom feltöltése

Következő ciklusban cellákat szúrunk be a táblázatba. Minden 7 cellánál lezárjuk a sort, hogy újat hozzunk létre.

```csharp
for (int i = 0; i < 31; i++)
{
    if (i != 0 && i % 7 == 0) builder.EndRow();
    builder.InsertCell();
    builder.Write("Cell contents");
}
builder.EndTable();
```

## 4. lépés: Adjon hozzá egy vízjel alakzatot

 Most adjunk vízjelet a dokumentumunkhoz. Létrehozunk a`Shape` objektumot, és állítsa be a tulajdonságait.

```csharp
Shape watermark = new Shape(doc, ShapeType.TextPlainText)
{
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    RelativeVerticalPosition = RelativeVerticalPosition.Page,
    IsLayoutInCell = true, // Az alakzat megjelenítése a táblázatcellán kívül, ha cellába kerül.
    Width = 300,
    Height = 70,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    Rotation = -40
};
```

## 5. lépés: A vízjel megjelenésének testreszabása

Tovább szabjuk a vízjel megjelenését a szín és a szöveg tulajdonságainak beállításával.

```csharp
watermark.FillColor = Color.Gray;
watermark.StrokeColor = Color.Gray;
watermark.TextPath.Text = "watermarkText";
watermark.TextPath.FontFamily = "Arial";
watermark.Name = $"WaterMark_{Guid.NewGuid()}";
watermark.WrapType = WrapType.None;
```

## 6. lépés: Helyezze be a vízjelet a dokumentumba

Megtaláljuk az utolsó futtatást a dokumentumban, és beillesztjük a vízjelet arra a helyre.

```csharp
Run run = doc.GetChildNodes(NodeType.Run, true)[doc.GetChildNodes(NodeType.Run, true).Count - 1] as Run;
builder.MoveTo(run);
builder.InsertNode(watermark);
```

## 7. lépés: Optimalizálja a dokumentumot a Word 2010 számára

kompatibilitás biztosítása érdekében a dokumentumot Word 2010-re optimalizáljuk.

```csharp
doc.CompatibilityOptions.OptimizeFor(MsWordVersion.Word2010);
```

## 8. lépés: Mentse el a dokumentumot

Végül elmentjük a dokumentumunkat a megadott könyvtárba.

```csharp
doc.Save(dataDir + "WorkingWithShapes.LayoutInCell.docx");
```

## Következtetés

És megvan! Sikeresen létrehozott egy Word-dokumentumot testreszabott táblázatelrendezéssel, és vízjelet adott hozzá az Aspose.Words for .NET segítségével. Ennek az oktatóanyagnak az volt a célja, hogy világos, lépésenkénti útmutatót nyújtson a folyamat egyes részeinek megértéséhez. Ezekkel a készségekkel most már kifinomultabb és személyre szabott Word-dokumentumokat hozhat létre programozottan.

## GYIK

### Használhatok más betűtípust a vízjel szövegéhez?
 Igen, módosíthatja a betűtípust a`watermark.TextPath.FontFamily` tulajdonságot a kívánt betűtípusra.

### Hogyan állíthatom be a vízjel helyzetét?
 Módosíthatja a`RelativeHorizontalPosition`, `RelativeVerticalPosition`, `HorizontalAlignment` , és`VerticalAlignment` tulajdonságait a vízjel helyzetének beállításához.

### Lehetséges-e szöveg helyett képet használni a vízjelhez?
 Teljesen! Létrehozhat a`Shape` a típussal`ShapeType.Image` és állítsa be a képét a segítségével`ImageData.SetImage` módszer.

### Létrehozhatok változó sormagasságú táblázatokat?
Igen, az egyes sorokhoz különböző magasságokat állíthat be a`RowFormat.Height` tulajdonságot, mielőtt cellákat illeszt be a sorba.

### Hogyan távolíthatok el vízjelet a dokumentumból?
 A vízjel eltávolításához keresse meg a dokumentum alakzatgyűjteményében, és hívja meg a`Remove` módszer.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
