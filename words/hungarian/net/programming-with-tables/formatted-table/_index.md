---
"description": "Tanuld meg, hogyan hozhatsz létre és formázhatsz táblázatokat Word-dokumentumokban az Aspose.Words for .NET segítségével ebből a részletes, lépésről lépésre haladó útmutatóból."
"linktitle": "Formázott táblázat"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Formázott táblázat"
"url": "/hu/net/programming-with-tables/formatted-table/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formázott táblázat

## Bevezetés

A Word-dokumentumokban lévő táblázatok programozott létrehozása és formázása ijesztő feladatnak tűnhet, de az Aspose.Words for .NET segítségével ez egyszerűvé és kezelhetővé válik. Ebben az oktatóanyagban végigvezetjük Önt azon, hogyan hozhat létre formázott táblázatot egy Word-dokumentumban az Aspose.Words for .NET használatával. Mindent lefedünk a környezet beállításától kezdve a dokumentum gyönyörűen formázott táblázattal történő mentéséig.

## Előfeltételek

Mielőtt belemerülnénk a kódba, győződjünk meg róla, hogy minden szükséges dolog megvan:

1. Aspose.Words .NET könyvtárhoz: Töltse le innen [itt](https://releases.aspose.com/words/net/).
2. Fejlesztői környezet: Egy IDE, mint például a Visual Studio.
3. .NET-keretrendszer: Győződjön meg arról, hogy a .NET-keretrendszer telepítve van a gépén.

## Névterek importálása

A tényleges kód megírása előtt importálni kell a szükséges névtereket:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

## 1. lépés: Dokumentumkönyvtár beállítása

Először is meg kell adnia azt az elérési utat, ahová a dokumentumot menteni fogja.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Csere `"YOUR DOCUMENT DIRECTORY"` a dokumentum tényleges mentési útvonalával.

## 2. lépés: A dokumentum és a DocumentBuilder inicializálása

Most inicializáljon egy új dokumentumot és egy DocumentBuilder objektumot.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

A `DocumentBuilder` egy segítő osztály, amely leegyszerűsíti a dokumentumok építésének folyamatát.

## 3. lépés: Indítsa el a táblázatot

Ezután kezdje el létrehozni a táblázatot a `StartTable` módszer.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

A táblázat elindításához cella beszúrása szükséges.

## 4. lépés: Táblázatszintű formázás alkalmazása

Lehetőség van olyan formázást alkalmazni, amely az egész táblázatra hatással van. Például beállíthatja a bal oldali behúzást:

```csharp
table.LeftIndent = 20.0;
```

## 5. lépés: A fejlécsor formázása

Állítsa be a fejlécsor magasságát, igazítását és egyéb tulajdonságait.

```csharp
builder.RowFormat.Height = 40.0;
builder.RowFormat.HeightRule = HeightRule.AtLeast;
builder.CellFormat.Shading.BackgroundPatternColor = Color.FromArgb(198, 217, 241);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Font.Size = 16;
builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.CellFormat.Width = 100.0;
builder.Write("Header Row,\n Cell 1");
```

Ebben a lépésben a fejlécsor kiemelését a háttérszín, a betűméret és az igazítás beállításával végezzük.

## 6. lépés: További fejléccellák beszúrása

További cellák beszúrása a fejlécsorba:

```csharp
builder.InsertCell();
builder.Write("Header Row,\n Cell 2");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Header Row,\n Cell 3");
builder.EndRow();
```

## 7. lépés: A törzs sorainak formázása

A fejléc beállítása után formázd meg a táblázat törzsét:

```csharp
builder.CellFormat.Shading.BackgroundPatternColor = Color.White;
builder.CellFormat.Width = 100.0;
builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;
builder.RowFormat.Height = 30.0;
builder.RowFormat.HeightRule = HeightRule.Auto;
```

## 8. lépés: Törzs sorok beszúrása

Szúrja be a törzs sorait tartalommal:

```csharp
builder.InsertCell();
builder.Font.Size = 12;
builder.Font.Bold = false;
builder.Write("Row 1, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 1, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 1, Cell 3 Content");
builder.EndRow();
```

Ismételje meg a további sorok esetében:

```csharp
builder.InsertCell();
builder.CellFormat.Width = 100.0;
builder.Write("Row 2, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 2, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 2, Cell 3 Content.");
builder.EndRow();
builder.EndTable();
```

## 9. lépés: A dokumentum mentése

Végül mentse el a dokumentumot a megadott könyvtárba:

```csharp
doc.Save(dataDir + "WorkingWithTables.FormattedTable.docx");
```

Ez létrehoz és ment egy Word-dokumentumot a formázott táblázattal.

## Következtetés

És íme! A következő lépéseket követve jól formázott táblázatot hozhat létre egy Word-dokumentumban az Aspose.Words for .NET segítségével. Ez a hatékony függvénykönyvtár megkönnyíti a Word-dokumentumok programozott kezelését, így időt és energiát takarít meg.

## GYIK

### Mi az Aspose.Words .NET-hez?
Az Aspose.Words for .NET egy hatékony függvénytár Word-dokumentumok programozott létrehozásához, szerkesztéséhez és konvertálásához.

### Használhatok különböző színeket a különböző sorokhoz?
Igen, alkalmazhat különböző formázásokat, beleértve a színeket is, a különböző sorokra vagy cellákra.

### Ingyenes az Aspose.Words .NET-hez?
Az Aspose.Words for .NET egy fizetős könyvtár, de letöltheti [ingyenes próba](https://releases.aspose.com/).

### Hogyan kaphatok támogatást az Aspose.Words for .NET-hez?
Támogatást kaphatsz a [Aspose közösségi fórumok](https://forum.aspose.com/c/words/8).

### Létrehozhatok más típusú dokumentumokat az Aspose.Words for .NET segítségével?
Igen, az Aspose.Words for .NET számos dokumentumformátumot támogat, beleértve a PDF, HTML és TXT fájlokat.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}