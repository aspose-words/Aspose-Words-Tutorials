---
title: Formázza a táblázatot és a cellát különböző szegéllyel
linktitle: Formázza a táblázatot és a cellát különböző szegéllyel
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan formázhat különböző szegélyű táblázatokat és cellákat az Aspose.Words for .NET használatával. Javítsa Word-dokumentumait testreszabott táblázatstílusokkal és cellaárnyékolással.
weight: 10
url: /hu/net/programming-with-table-styles-and-formatting/format-table-and-cell-with-different-borders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formázza a táblázatot és a cellát különböző szegéllyel

## Bevezetés

Próbálta már Word-dokumentumait professzionálisabbá tenni a táblázatok és cellák határainak testreszabásával? Ha nem, akkor egy csemege! Ez az oktatóanyag végigvezeti a különböző szegélyű táblázatok és cellák formázásán az Aspose.Words for .NET használatával. Képzelje el, hogy néhány sornyi kóddal megváltoztathatja a táblák megjelenését. Érdekelt? Merüljünk el, és fedezzük fel, hogyan érheti el ezt könnyedén.

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy a következő előfeltételek teljesülnek:
- A C# programozás alapvető ismerete.
- A Visual Studio telepítve van a számítógépére.
-  Aspose.Words a .NET könyvtárhoz. Ha még nem telepítette, letöltheti[itt](https://releases.aspose.com/words/net/).
-  Érvényes Aspose engedély. Ingyenes próbaverziót vagy ideiglenes licencet kaphat a webhelyen[itt](https://purchase.aspose.com/temporary-license/).

## Névterek importálása

Az Aspose.Words for .NET használatához importálnia kell a szükséges névtereket a projektbe. Adja hozzá a következőket a kódfájl tetején található direktívák használatával:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;
```

## 1. lépés: Inicializálja a Dokumentumot és a DocumentBuilder-t

Először is létre kell hoznia egy új dokumentumot, és inicializálnia kell a DocumentBuildert, amely segít a dokumentumtartalom felépítésében. 

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 2. lépés: Kezdje el a táblázat létrehozását

Ezután a DocumentBuilder segítségével kezdje el a táblázat létrehozását, és szúrja be az első cellát.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

## 3. lépés: Állítsa be a táblázat szegélyeit

Állítsa be a szegélyeket az egész táblázathoz. Ez a lépés biztosítja, hogy a táblázat minden cellájának konzisztens szegélystílusa legyen, hacsak nincs másképp megadva.

```csharp
// Állítsa be a szegélyeket az egész táblázathoz.
table.SetBorders(LineStyle.Single, 2.0, Color.Black);
```

## 4. lépés: Alkalmazza a cellaárnyékolást

Alkalmazzon árnyékolást a cellákra, hogy vizuálisan megkülönböztethetővé váljanak. Ebben a példában az első cella háttérszínét pirosra állítjuk.


```csharp
// Állítsa be a cella árnyékolását ehhez a cellához.
builder.CellFormat.Shading.BackgroundPatternColor = Color.Red;
builder.Writeln("Cell #1");
```

## 5. lépés: Szúrjon be egy másik cellát eltérő árnyékolással

Helyezze be a második cellát, és alkalmazzon egy másik árnyékoló színt. Ez színesebbé és könnyebben olvashatóvá teszi a táblázatot.

```csharp
builder.InsertCell();
// Adjon meg más cellaárnyékolást a második cellához.
builder.CellFormat.Shading.BackgroundPatternColor = Color.Green;
builder.Writeln("Cell #2");
builder.EndRow();
```

## 6. lépés: Törölje a cellaformázást

Törölje a cellaformázást az előző műveletekből, hogy a következő cellák ne örököljék ugyanazokat a stílusokat.


```csharp
// Törölje a cellaformázást a korábbi műveletekből.
builder.CellFormat.ClearFormatting();
```

## 7. lépés: A szegélyek testreszabása adott cellákhoz

Testreszabhatja az egyes cellák szegélyeit, hogy kiemelkedjenek. Itt nagyobb szegélyeket állítunk be az új sor első cellájához.

```csharp
builder.InsertCell();
// Hozzon létre nagyobb kereteket a sor első cellájához. Ez más lesz
// a táblázathoz beállított szegélyekhez képest.
builder.CellFormat.Borders.Left.LineWidth = 4.0;
builder.CellFormat.Borders.Right.LineWidth = 4.0;
builder.CellFormat.Borders.Top.LineWidth = 4.0;
builder.CellFormat.Borders.Bottom.LineWidth = 4.0;
builder.Writeln("Cell #3");
```

## 8. lépés: Az utolsó cella beszúrása

Szúrja be az utolsó cellát, és győződjön meg arról, hogy a formázása törlődik, így a táblázat alapértelmezett stílusait használja.

```csharp
builder.InsertCell();
builder.CellFormat.ClearFormatting();
builder.Writeln("Cell #4");
```

## 9. lépés: Mentse el a dokumentumot

Végül mentse a dokumentumot a megadott könyvtárba.

```csharp
doc.Save(dataDir + "WorkingWithTableStylesAndFormatting.FormatTableAndCellWithDifferentBorders.docx");
```

## Következtetés

És megvan! Most tanulta meg, hogyan formázhat különböző szegélyű táblázatokat és cellákat az Aspose.Words for .NET használatával. A táblázatszegélyek és a cellaárnyékolás testreszabásával jelentősen javíthatja dokumentumai vizuális vonzerejét. Tehát folytassa, kísérletezzen különböző stílusokkal, és tegye kiemelkedővé dokumentumait!

## GYIK

### Használhatok különböző szegélystílusokat minden cellához?
 Igen, az egyes cellákhoz különböző szegélystílusokat állíthat be a`CellFormat.Borders` ingatlan.

### Hogyan távolíthatom el az összes szegélyt egy táblázatból?
 Az összes szegélyt eltávolíthatja a szegélystílus beállításával`LineStyle.None`.

### Lehetséges minden cellához különböző keretszínt beállítani?
 Teljesen! Testreszabhatja az egyes cellák keretének színét a`CellFormat.Borders.Color` ingatlan.

### Használhatok képeket cellaháttérként?
Míg az Aspose.Words közvetlenül nem támogatja a képeket cellaháttérként, beszúrhat egy képet a cellába, és beállíthatja a méretét, hogy lefedje a cella területét.

### Hogyan egyesíthetem a cellákat egy táblázatban?
 A cellákat a segítségével egyesítheti`CellFormat.HorizontalMerge` és`CellFormat.VerticalMerge` tulajdonságait.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
