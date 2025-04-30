---
"description": "Tanuld meg, hogyan állíthatod be a cellák elrendezését az Aspose.Words for .NET használatával ebből az átfogó útmutatóból. Tökéletes azoknak a fejlesztőknek, akik testre szeretnék szabni a Word dokumentumokat."
"linktitle": "Elrendezés a cellában"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Elrendezés a cellában"
"url": "/hu/net/programming-with-shapes/layout-in-cell/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Elrendezés a cellában

## Bevezetés

Ha valaha is szerettél volna programozottan finomhangolni a táblázatcellák elrendezését a Word-dokumentumokban, jó helyen jársz. Ma belemerülünk abba, hogyan állíthatod be az elrendezést a cellákban az Aspose.Words for .NET használatával. Egy gyakorlati példán keresztül lépésről lépésre lebontjuk a folyamatot, hogy könnyedén követhesd.

## Előfeltételek

Mielőtt belevágnánk a kódba, győződjünk meg róla, hogy minden szükséges dolog megvan:

1. Aspose.Words .NET-hez: Győződjön meg róla, hogy telepítve van az Aspose.Words .NET-hez tartozó könyvtár. Ha nem, akkor megteheti [töltsd le itt](https://releases.aspose.com/words/net/).
2. Fejlesztői környezet: Szükséged lesz egy .NET-tel beállított fejlesztői környezetre. A Visual Studio nagyszerű választás, ha ajánlásokat keresel.
3. C# alapismeretek: Bár minden lépést elmagyarázok, a C# alapvető ismerete segít abban, hogy könnyebben kövesd a lépéseket.
4. Dokumentumkönyvtár: Készítsen elő egy könyvtár elérési útját, ahová a dokumentumokat menteni fogja. Ezt a következőképpen fogjuk megnevezni: `YOUR DOCUMENT DIRECTORY`.

## Névterek importálása

Első lépésként győződjön meg arról, hogy importálja a szükséges névtereket a projektjébe:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Bontsuk le a folyamatot kezelhető lépésekre.

## 1. lépés: Új dokumentum létrehozása

Először is létrehozunk egy új Word dokumentumot, és inicializáljuk a `DocumentBuilder` objektum, amely segít nekünk a tartalmunk felépítésében.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 2. lépés: Táblázat létrehozása és sorformátum beállítása

Elkezdjük a táblázat létrehozását, és megadjuk a sorok magasságát és magassági szabályát.

```csharp
builder.StartTable();
builder.RowFormat.Height = 100;
builder.RowFormat.HeightRule = HeightRule.Exactly;
```

## 3. lépés: Cellák beszúrása és tartalommal való feltöltése

Ezután egy ciklust futtatunk, amely cellákat szúr be a táblázatba. Minden 7. cella után lezárjuk a sort, hogy egy új cellát hozzunk létre.

```csharp
for (int i = 0; i < 31; i++)
{
    if (i != 0 && i % 7 == 0) builder.EndRow();
    builder.InsertCell();
    builder.Write("Cell contents");
}
builder.EndTable();
```

## 4. lépés: Vízjel alakzat hozzáadása

Most adjunk hozzá egy vízjelet a dokumentumunkhoz. Létrehozunk egy `Shape` objektumot, és beállítjuk a tulajdonságait.

```csharp
Shape watermark = new Shape(doc, ShapeType.TextPlainText)
{
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    RelativeVerticalPosition = RelativeVerticalPosition.Page,
    IsLayoutInCell = true, // Jelenítse meg az alakzatot a táblázatcellán kívül, ha az egy cellába kerül.
    Width = 300,
    Height = 70,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    Rotation = -40
};
```

## 5. lépés: A vízjel megjelenésének testreszabása

A vízjel megjelenését a szín- és szövegtulajdonságok beállításával fogjuk tovább testreszabni.

```csharp
watermark.FillColor = Color.Gray;
watermark.StrokeColor = Color.Gray;
watermark.TextPath.Text = "watermarkText";
watermark.TextPath.FontFamily = "Arial";
watermark.Name = $"WaterMark_{Guid.NewGuid()}";
watermark.WrapType = WrapType.None;
```

## 6. lépés: Vízjel beszúrása a dokumentumba

Megkeressük a dokumentumban az utolsó futtatást, és oda illesztjük be a vízjelet.

```csharp
Run run = doc.GetChildNodes(NodeType.Run, true)[doc.GetChildNodes(NodeType.Run, true).Count - 1] as Run;
builder.MoveTo(run);
builder.InsertNode(watermark);
```

## 7. lépés: Dokumentum optimalizálása Word 2010-hez

A kompatibilitás biztosítása érdekében optimalizáljuk a dokumentumot a Word 2010-hez.

```csharp
doc.CompatibilityOptions.OptimizeFor(MsWordVersion.Word2010);
```

## 8. lépés: A dokumentum mentése

Végül mentsük el a dokumentumunkat a megadott könyvtárba.

```csharp
doc.Save(dataDir + "WorkingWithShapes.LayoutInCell.docx");
```

## Következtetés

És íme! Sikeresen létrehoztál egy Word-dokumentumot testreszabott táblázatelrendezéssel, és hozzáadtál egy vízjelet az Aspose.Words for .NET segítségével. Ez az oktatóanyag egy világos, lépésről lépésre haladó útmutatót kívánt nyújtani, amely segít megérteni a folyamat minden egyes részét. Ezekkel a készségekkel mostantól programozottan is létrehozhatsz kifinomultabb és testreszabottabb Word-dokumentumokat.

## GYIK

### Használhatok más betűtípust a vízjel szövegéhez?
Igen, a betűtípust módosíthatja a beállítással `watermark.TextPath.FontFamily` tulajdonságot a kívánt betűtípushoz.

### Hogyan tudom beállítani a vízjel pozícióját?
Módosíthatja a `RelativeHorizontalPosition`, `RelativeVerticalPosition`, `HorizontalAlignment`, és `VerticalAlignment` tulajdonságok a vízjel pozíciójának beállításához.

### Lehetséges képet használni szöveg helyett vízjelként?
Természetesen! Létrehozhatsz egy `Shape` a típussal `ShapeType.Image` és állítsa be a képét a `ImageData.SetImage` módszer.

### Létrehozhatok táblázatokat változó sormagasságokkal?
Igen, minden sorhoz különböző magasságokat állíthat be a `RowFormat.Height` tulajdonságot, mielőtt cellákat szúrna be az adott sorba.

### Hogyan távolíthatok el egy vízjelet a dokumentumból?
A vízjelet úgy távolíthatja el, hogy megkeresi azt a dokumentum alakzatgyűjteményében, és meghívja a `Remove` módszer.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}