---
title: Táblázat beszúrása közvetlenül
linktitle: Táblázat beszúrása közvetlenül
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan illeszthet be táblázatokat közvetlenül a Word dokumentumokba az Aspose.Words for .NET használatával. Kövesse részletes, lépésenkénti útmutatónkat a dokumentumkészítés egyszerűsítéséhez.
weight: 10
url: /hu/net/programming-with-tables/insert-table-directly/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Táblázat beszúrása közvetlenül

## Bevezetés
táblázatok programozott létrehozása komoly kihívást jelenthet, különösen összetett dokumentumszerkezetek kezelésekor. De ne aggódj, azért vagyunk itt, hogy lebontsuk neked! Ebben az útmutatóban az Aspose.Words for .NET segítségével táblázatot közvetlenül Word-dokumentumba illeszthetünk be. Akár tapasztalt fejlesztő, akár csak most kezdi, ez az oktatóanyag segít a folyamat egyszerű elsajátításában.

## Előfeltételek

Mielőtt belemerülne a kódba, győződjön meg arról, hogy mindennel rendelkezik, amire szüksége van az induláshoz. Íme egy gyors ellenőrző lista:

1.  Aspose.Words for .NET Library: Győződjön meg arról, hogy letöltötte és telepítette az Aspose.Words for .NET könyvtárat. Beszerezheti a[letöltési oldal](https://releases.aspose.com/words/net/).
2. Fejlesztői környezet: Olyan fejlesztői környezet, mint a Visual Studio.
3. C# alapismeretek: A C# programozás alapjainak megértése.
4. Dokumentumkönyvtár: Egy könyvtár elérési útja, ahová a dokumentumokat mentheti.

Ha ezekkel az előfeltételekkel rendelkezik, akkor készen áll a kódolás megkezdésére!

## Névterek importálása

Először is importáljuk a szükséges névtereket. Ezek a névterek biztosítják számunkra a Word-dokumentumok kezeléséhez szükséges osztályokat és módszereket.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

Most, hogy a névtereink a helyükön vannak, térjünk át az izgalmas részre – táblázatok létrehozására és közvetlenül egy Word dokumentumba történő beszúrására.

## 1. lépés: A dokumentum beállítása

Kezdjük egy új Word dokumentum beállításával. Ide kerül a táblázatunk.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

 Ez a kód inicializál egy új Word-dokumentumot. Cserélned kell`"YOUR DOCUMENT DIRECTORY"` a dokumentumkönyvtár tényleges elérési útjával.

## 2. lépés: A táblázatobjektum létrehozása

Ezután létrehozzuk a táblázat objektumot. Itt határozzuk meg a táblázatunk szerkezetét.

```csharp
// Kezdjük a táblázat objektum létrehozásával. Ne feledje, hogy át kell adnunk a dokumentum objektumot
// az egyes csomópontok konstruktorához. Ez azért van, mert minden általunk létrehozott csomópontnak hozzá kell tartoznia
// valamilyen dokumentumhoz.
Table table = new Table(doc);
doc.FirstSection.Body.AppendChild(table);
```

Itt létrehozunk egy új táblázatot, és hozzáfűzzük a dokumentumunk első részének törzséhez.

## 3. lépés: Sorok és cellák hozzáadása

táblázat sorokból és cellákból áll. Adjuk hozzá ezeket az elemeket lépésről lépésre.

### Sor hozzáadása

```csharp
// Itt hívhatnánk az EnsureMinimum-ot, hogy létrehozza számunkra a sorokat és cellákat. Ezt a módszert alkalmazzák
// hogy a megadott csomópont érvényes legyen. Ebben az esetben egy érvényes táblázatnak legalább egy sorral és egy cellával kell rendelkeznie.
// Ehelyett mi magunk készítjük el a sort és a táblázatot.
// Ez lenne a legjobb módja ennek, ha egy algoritmuson belül hoznánk létre egy táblázatot.
Row row = new Row(doc);
row.RowFormat.AllowBreakAcrossPages = true;
table.AppendChild(row);
```

Ez a kód egy új sort hoz létre, és hozzáfűzi a táblázatunkhoz.

### Cellák hozzáadása a sorhoz

Most adjunk hozzá néhány cellát a sorunkhoz. 

```csharp
Cell cell = new Cell(doc);
cell.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
cell.CellFormat.Width = 80;
cell.AppendChild(new Paragraph(doc));
cell.FirstParagraph.AppendChild(new Run(doc, "Row 1, Cell 1 Text"));
row.AppendChild(cell);
```

Ebben a részletben létrehozunk egy cellát, a háttérszínét világoskékre állítjuk, és meghatározzuk a szélességét. Ezután hozzáadunk egy bekezdést és egy futást a cellához, hogy megtartsuk a szövegünket.

## 4. lépés: Sejtek klónozása

A sejtek hozzáadásának felgyorsítása érdekében klónozhatjuk a meglévő sejteket.

```csharp
// Ezután megismételjük a folyamatot a táblázat többi cellájára és sorára.
//Meglévő sejtek és sorok klónozásával is felgyorsíthatjuk a dolgokat.
row.AppendChild(cell.Clone(false));
row.LastCell.AppendChild(new Paragraph(doc));
row.LastCell.FirstParagraph.AppendChild(new Run(doc, "Row 1, Cell 2 Text"));
```

Ez a kód klónozza a meglévő cellát, és hozzáadja a sorhoz. Ezután hozzáadunk egy bekezdést és egy futást az új cellához.

## 5. lépés: Az Auto Fit beállítások alkalmazása

Végül alkalmazzuk az automatikus illesztési beállításokat a táblázatunkban, hogy biztosítsuk az oszlopok rögzített szélességét.

```csharp
// Mostantól bármilyen automatikus illesztési beállítást alkalmazhatunk.
table.AutoFit(AutoFitBehavior.FixedColumnWidths);
```

## 6. lépés: A dokumentum mentése

Miután a táblázatunk teljesen készen van, ideje elmenteni a dokumentumot.

```csharp
doc.Save(dataDir + "WorkingWithTables.InsertTableDirectly.docx");
```

Ez a kód menti a dokumentumot a beszúrt táblázattal.

## Következtetés

Gratulálok! Sikeresen beszúrt egy táblázatot közvetlenül egy Word-dokumentumba az Aspose.Words for .NET segítségével. Ezzel a folyamattal összetett táblák programozottan hozhatók létre, így sokkal könnyebbé válik a dokumentumautomatizálási feladatai. Akár jelentéseket, számlákat vagy bármilyen más dokumentumtípust készít, a táblák kezelésének megértése alapvető készség.

## GYIK

### Hogyan tölthetem le az Aspose.Words for .NET fájlt?
 Az Aspose.Words for .NET letölthető innen[letöltési oldal](https://releases.aspose.com/words/net/).

### Kipróbálhatom az Aspose.Words for .NET-et a vásárlás előtt?
 Igen, kérheti a[ingyenes próbaverzió](https://releases.aspose.com/) hogy vásárlás előtt értékelje a könyvtárat.

### Hogyan vásárolhatom meg az Aspose.Words for .NET fájlt?
Az Aspose.Words for .NET megvásárolható a[vásárlási oldal](https://purchase.aspose.com/buy).

### Hol találom az Aspose.Words for .NET dokumentációját?
 A dokumentáció elérhető[itt](https://reference.aspose.com/words/net/).

### Mi a teendő, ha támogatásra van szükségem az Aspose.Words for .NET használata közben?
 Támogatásért látogassa meg a[Aspose.Words fórum](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
