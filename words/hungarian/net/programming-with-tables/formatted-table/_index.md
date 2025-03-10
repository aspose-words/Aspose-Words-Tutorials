---
title: Formázott táblázat
linktitle: Formázott táblázat
second_title: Aspose.Words Document Processing API
description: Ebből a részletes, lépésenkénti útmutatóból megtudhatja, hogyan hozhat létre és formázhat táblázatokat Word dokumentumokban az Aspose.Words for .NET használatával.
weight: 10
url: /hu/net/programming-with-tables/formatted-table/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formázott táblázat

## Bevezetés

A Word-dokumentumok táblázatainak programozott létrehozása és formázása ijesztő feladatnak tűnhet, de az Aspose.Words for .NET segítségével egyszerűvé és kezelhetővé válik. Ebben az oktatóanyagban végigvezetjük, hogyan hozhat létre formázott táblázatot Word-dokumentumban az Aspose.Words for .NET használatával. A környezet beállításától a dokumentum gyönyörűen formázott táblázattal történő mentéséig mindenre kiterjedünk.

## Előfeltételek

Mielőtt belemerülnénk a kódba, győződjünk meg arról, hogy mindennel rendelkezünk, amire szükségünk van:

1. Aspose.Words for .NET Library: Töltse le innen[itt](https://releases.aspose.com/words/net/).
2. Fejlesztői környezet: Egy IDE, mint a Visual Studio.
3. .NET-keretrendszer: Győződjön meg arról, hogy a .NET-keretrendszer telepítve van a számítógépen.

## Névterek importálása

A tényleges kód megírása előtt importálnia kell a szükséges névtereket:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

## 1. lépés: Állítsa be a dokumentumkönyvtárat

Először is meg kell határoznia a dokumentum mentési útvonalát.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Cserélje ki`"YOUR DOCUMENT DIRECTORY"` a tényleges elérési úttal, ahová a dokumentumot menteni szeretné.

## 2. lépés: Inicializálja a Dokumentumot és a DocumentBuildert

Most inicializáljon egy új dokumentumot és egy DocumentBuilder objektumot.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 A`DocumentBuilder` egy segítő osztály, amely leegyszerűsíti az építési dokumentumok elkészítésének folyamatát.

## 3. lépés: Indítsa el a táblázatot

 Ezután kezdje el a táblázat létrehozását a`StartTable` módszer.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

A táblázat elindításához cella beszúrása szükséges.

## 4. lépés: Alkalmazza a táblázatos formázást

Alkalmazhat olyan formázást, amely a teljes táblázatot érinti. Például a bal oldali behúzás beállítása:

```csharp
table.LeftIndent = 20.0;
```

## 5. lépés: Formázza meg a fejlécesort

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

Ebben a lépésben a fejlécsort kiemeljük a háttérszín, a betűméret és az igazítás beállításával.

## 6. lépés: Szúrjon be további fejléccellákat

További cellák beszúrása a fejlécsorba:

```csharp
builder.InsertCell();
builder.Write("Header Row,\n Cell 2");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Header Row,\n Cell 3");
builder.EndRow();
```

## 7. lépés: Formázza meg a törzssorokat

A fejléc beállítása után formázza meg a táblázat törzsét:

```csharp
builder.CellFormat.Shading.BackgroundPatternColor = Color.White;
builder.CellFormat.Width = 100.0;
builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;
builder.RowFormat.Height = 30.0;
builder.RowFormat.HeightRule = HeightRule.Auto;
```

## 8. lépés: Szúrjon be törzssorokat

Szúrja be a törzssorokat a tartalommal:

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

Ismételje meg a további soroknál:

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

## 9. lépés: Mentse el a dokumentumot

Végül mentse a dokumentumot a megadott könyvtárba:

```csharp
doc.Save(dataDir + "WorkingWithTables.FormattedTable.docx");
```

Ezzel létrehoz és ment egy Word-dokumentumot a formázott táblázattal.

## Következtetés

És megvan! Az alábbi lépések követésével jól formázott táblázatot hozhat létre Word-dokumentumban az Aspose.Words for .NET használatával. Ez a nagy teljesítményű könyvtár megkönnyíti a Word-dokumentumok programozott kezelését, így időt és erőfeszítést takarít meg.

## GYIK

### Mi az Aspose.Words for .NET?
Az Aspose.Words for .NET egy hatékony könyvtár Word-dokumentumok programozott létrehozásához, szerkesztéséhez és konvertálásához.

### Használhatok különböző színeket a különböző sorokhoz?
Igen, különböző sorokra vagy cellákra eltérő formázást alkalmazhat, beleértve a színeket is.

### Az Aspose.Words for .NET ingyenes?
 Az Aspose.Words for .NET egy fizetős könyvtár, de beszerezheti a[ingyenes próbaverzió](https://releases.aspose.com/).

### Hogyan kaphatok támogatást az Aspose.Words for .NET-hez?
 Támogatást kaphat a[Aspose közösségi fórumok](https://forum.aspose.com/c/words/8).

### Létrehozhatok más típusú dokumentumokat az Aspose.Words for .NET segítségével?
Igen, az Aspose.Words for .NET különféle dokumentumformátumokat támogat, beleértve a PDF, HTML és TXT fájlokat.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
