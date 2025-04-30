---
"description": "Tanuld meg, hogyan formázhatsz táblázatokat és cellákat különböző szegélyekkel az Aspose.Words for .NET segítségével. Dobd fel Word-dokumentumaidat testreszabott táblázatstílusokkal és cellaárnyékolással."
"linktitle": "Táblázat és cella formázása eltérő szegélyekkel"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Táblázat és cella formázása eltérő szegélyekkel"
"url": "/hu/net/programming-with-table-styles-and-formatting/format-table-and-cell-with-different-borders/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Táblázat és cella formázása eltérő szegélyekkel

## Bevezetés

Próbáltad már valaha professzionálisabb megjelenést elérni a Word-dokumentumaiddal a táblázatok és cellák szegélyeinek testreszabásával? Ha nem, akkor igazi meglepetésben lesz részed! Ez az oktatóanyag végigvezet a táblázatok és cellák különböző szegélyekkel történő formázásán az Aspose.Words for .NET használatával. Képzeld el, hogy mindössze néhány sornyi kóddal megváltoztathatod a táblázataid megjelenését. Felkeltette az érdeklődésedet? Vágjunk bele, és fedezzük fel, hogyan érheted ezt el könnyedén.

## Előfeltételek

Mielőtt elkezdenénk, győződjünk meg róla, hogy a következő előfeltételek teljesülnek:
- A C# programozás alapjainak ismerete.
- Visual Studio telepítve a számítógépére.
- Aspose.Words .NET könyvtárhoz. Ha még nem telepítetted, letöltheted. [itt](https://releases.aspose.com/words/net/).
- Érvényes Aspose licenc. Ingyenes próbaverziót vagy ideiglenes licencet szerezhet be a következő címen: [itt](https://purchase.aspose.com/temporary-license/).

## Névterek importálása

Az Aspose.Words for .NET használatához importálnia kell a szükséges névtereket a projektjébe. Adja hozzá a következő direktívákat a kódfájl elejéhez:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;
```

## 1. lépés: A Document és a DocumentBuilder inicializálása

Először létre kell hozni egy új dokumentumot, és inicializálni kell a DocumentBuildert, amely segít a dokumentum tartalmának felépítésében. 

```csharp
// A dokumentumkönyvtár elérési útja 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 2. lépés: Táblázat létrehozásának megkezdése

Ezután a DocumentBuilder segítségével kezdj el táblázatot létrehozni, és illeszd be az első cellát.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

## 3. lépés: Táblázatszegélyek beállítása

Állítsa be a teljes táblázat szegélyeit. Ez a lépés biztosítja, hogy a táblázat összes cellájának szegélystílusa egységes legyen, hacsak másképp nincs megadva.

```csharp
// Állítsa be a teljes táblázat szegélyeit.
table.SetBorders(LineStyle.Single, 2.0, Color.Black);
```

## 4. lépés: Cellaárnyékolás alkalmazása

Árnyékolást alkalmazzon a cellákra, hogy vizuálisan megkülönböztethetőek legyenek. Ebben a példában az első cella háttérszínét pirosra állítjuk.


```csharp
// Állítsa be a cella árnyékolását.
builder.CellFormat.Shading.BackgroundPatternColor = Color.Red;
builder.Writeln("Cell #1");
```

## 5. lépés: Helyezzen be egy másik cellát eltérő árnyékolással

Szúrd be a második cellát, és alkalmazz rá egy másik árnyékolószínt. Ezáltal a táblázat színesebb és könnyebben olvasható lesz.

```csharp
builder.InsertCell();
// Adjon meg egy eltérő cellaárnyékolást a második cellához.
builder.CellFormat.Shading.BackgroundPatternColor = Color.Green;
builder.Writeln("Cell #2");
builder.EndRow();
```

## 6. lépés: Cellaformázás törlése

Töröld a korábbi műveletekből származó cellaformázást, hogy a következő cellák ne örököljék ugyanazokat a stílusokat.


```csharp
// Törölje a cellaformázást az előző műveletekből.
builder.CellFormat.ClearFormatting();
```

## 7. lépés: Testreszabhatja a szegélyeket adott cellákhoz

Testreszabhatja az egyes cellák szegélyeit, hogy kiemelkedjenek. Itt nagyobb szegélyeket fogunk beállítani az új sor első cellájához.

```csharp
builder.InsertCell();
// Hozz létre nagyobb szegélyeket a sor első cellájához. Ez más lesz.
// az asztalhoz beállított szegélyekhez képest.
builder.CellFormat.Borders.Left.LineWidth = 4.0;
builder.CellFormat.Borders.Right.LineWidth = 4.0;
builder.CellFormat.Borders.Top.LineWidth = 4.0;
builder.CellFormat.Borders.Bottom.LineWidth = 4.0;
builder.Writeln("Cell #3");
```

## 8. lépés: Utolsó cella beszúrása

Szúrja be az utolsó cellát, és győződjön meg arról, hogy a formázása törölve van, így a táblázat alapértelmezett stílusait használja.

```csharp
builder.InsertCell();
builder.CellFormat.ClearFormatting();
builder.Writeln("Cell #4");
```

## 9. lépés: A dokumentum mentése

Végül mentse el a dokumentumot a megadott könyvtárba.

```csharp
doc.Save(dataDir + "WorkingWithTableStylesAndFormatting.FormatTableAndCellWithDifferentBorders.docx");
```

## Következtetés

És tessék! Most megtanultad, hogyan formázhatsz táblázatokat és cellákat különböző szegélyekkel az Aspose.Words for .NET segítségével. A táblázatszegélyek és a cellaárnyékolás testreszabásával jelentősen javíthatod dokumentumaid vizuális megjelenését. Tehát csak kísérletezz különböző stílusokkal, és tedd dokumentumaidat különlegessé!

## GYIK

### Használhatok különböző szegélystílusokat minden cellához?
Igen, minden cellához különböző szegélystílusokat állíthat be a használatával. `CellFormat.Borders` ingatlan.

### Hogyan tudom eltávolítani az összes szegélyt egy táblázatból?
Az összes szegélyt eltávolíthatja a szegélystílus beállításával. `LineStyle.None`.

### Lehetséges minden cellához különböző szegélyszínt beállítani?
Természetesen! Minden cella szegélyének színét testreszabhatod a `CellFormat.Borders.Color` ingatlan.

### Használhatok képeket cella háttereként?
Bár az Aspose.Words nem támogatja közvetlenül a képeket cella háttereként, beszúrhat egy képet egy cellába, és beállíthatja a méretét, hogy lefedje a cella területét.

### Hogyan tudok cellákat egyesíteni egy táblázatban?
A cellákat a következővel egyesítheti: `CellFormat.HorizontalMerge` és `CellFormat.VerticalMerge` tulajdonságok.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}