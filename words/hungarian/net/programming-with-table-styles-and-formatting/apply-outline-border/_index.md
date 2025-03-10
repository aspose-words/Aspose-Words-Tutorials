---
title: Alkalmazza a körvonalszegélyt
linktitle: Alkalmazza a körvonalszegélyt
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan alkalmazhat vázlatszegélyt egy Word-táblázatra az Aspose.Words for .NET használatával. Kövesse lépésről lépésre útmutatónkat a tökéletes táblázatformázás érdekében.
weight: 10
url: /hu/net/programming-with-table-styles-and-formatting/apply-outline-border/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Alkalmazza a körvonalszegélyt

## Bevezetés

mai oktatóanyagban az Aspose.Words for .NET segítségével történő dokumentumkezelés világába merülünk. Pontosabban, meg fogjuk tanulni, hogyan lehet vázlatszegélyt alkalmazni egy Word-dokumentum táblázatára. Ez egy fantasztikus készség az eszköztárban, ha gyakran dolgozik automatizált dokumentumgenerálással és -formázással. Kezdjük hát ezen az úton, hogy asztalait ne csak funkcionálissá, hanem vizuálisan is vonzóvá tegyük.

## Előfeltételek

Mielőtt belevágnánk a kódba, néhány dologra lesz szüksége:

1.  Aspose.Words for .NET: Az Aspose.Words for .NET-re telepítve kell lennie. Letöltheti[itt](https://releases.aspose.com/words/net/).
2. Fejlesztési környezet: Megfelelő fejlesztői környezet, mint a Visual Studio.
3. Alapvető C# ismerete: A C# alapvető ismerete segít az oktatóanyag követésében.

## Névterek importálása

Először is győződjön meg arról, hogy a szükséges névtereket importálta. Ez kulcsfontosságú az Aspose.Words funkcióinak eléréséhez.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

Bontsuk le a folyamatot egyszerű, kezelhető lépésekre.

## 1. lépés: Töltse be a dokumentumot

Először is be kell töltenünk a Word dokumentumot, amely a formázni kívánt táblázatot tartalmazza.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Tables.docx");
```

 Ebben a lépésben a`Document` osztályt az Aspose.Words-ből egy meglévő dokumentum betöltéséhez. Cserélje ki`"YOUR DOCUMENT DIRECTORY"` a tényleges elérési úttal, ahol a dokumentumot tárolják.

## 2. lépés: Nyissa meg a táblázatot

Ezután el kell érnünk a formázni kívánt táblázatot. 

```csharp
Table table = (Table)doc.GetChild(NodeType.Table, 0, true);
```

 Itt,`GetChild` metódus lekéri a dokumentum első táblázatát. A paraméterek`NodeType.Table, 0, true` győződjön meg arról, hogy a megfelelő csomóponttípust kapjuk.

## 3. lépés: Igazítsa a táblázatot

Most igazítsuk középre a táblázatot az oldalon.

```csharp
table.Alignment = TableAlignment.Center;
```

Ez a lépés biztosítja, hogy az asztal szépen középre kerüljön, így professzionális megjelenést kölcsönöz neki.

## 4. lépés: Törölje a meglévő határokat

Mielőtt új határokat alkalmaznánk, törölnünk kell a meglévő határokat.

```csharp
table.ClearBorders();
```

A szegélyek törlése biztosítja, hogy új szegélyeink tisztán, a régi stílusok beavatkozása nélkül kerüljenek alkalmazásra.

## 5. lépés: Állítsa be a körvonalhatárokat

Most alkalmazzuk a zöld körvonalszegélyeket a táblázatra.

```csharp
table.SetBorder(BorderType.Left, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Right, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Top, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Bottom, LineStyle.Single, 1.5, Color.Green, true);
```

 Minden szegélytípus (bal, jobb, felső, alsó) egyedileg beállítható. használjuk`LineStyle.Single` folytonos vonalhoz,`1.5` a vonalszélességhez, és`Color.Green` a szegély színéhez.

## 6. lépés: Alkalmazza a cellaárnyékolást

A táblázat látványosabbá tétele érdekében töltsük ki a cellákat világoszöld színnel.

```csharp
table.SetShading(TextureIndex.TextureSolid, Color.LightGreen, Color.Empty);
```

 Itt,`SetShading` arra szolgál, hogy egyszínű világoszöld színt vigyen fel a cellákra, így az asztal kiemelkedik.

## 7. lépés: Mentse el a dokumentumot

Végül mentse el a módosított dokumentumot.

```csharp
doc.Save(dataDir + "WorkingWithTableStylesAndFormatting.ApplyOutlineBorder.docx");
```

Ez a lépés elmenti a dokumentumot az alkalmazott formázással. Megnyitva láthatja a gyönyörűen formázott táblázatot.

## Következtetés

És megvan! Az alábbi lépések végrehajtásával sikeresen alkalmazott körvonalszegélyt egy Word-dokumentum táblázatához az Aspose.Words for .NET segítségével. Ez az oktatóanyag a dokumentum betöltését, a táblázat elérését, igazítását, a meglévő szegélyek törlését, új szegélyek alkalmazását, cellaárnyékolás hozzáadását és végül a dokumentum mentését tárgyalta. 

Ezekkel a készségekkel javíthatja a táblázatok vizuális megjelenését, így dokumentumait professzionálisabbá és vonzóbbá teheti. Boldog kódolást!

## GYIK

### Alkalmazhatok különböző stílusokat a táblázat minden szegélyére?  
 Igen, az egyes szegélyekre különböző stílusokat és színeket alkalmazhat a paraméterek beállításával`SetBorder` módszer.

### Hogyan tudom megváltoztatni a szegély szélességét?  
 A szélességet a harmadik paraméter módosításával módosíthatja a`SetBorder` módszer. Például,`1.5` 1,5 pontos szélességet állít be.

### Lehetséges-e árnyékolást alkalmazni az egyes cellákra?  
 Igen, az egyes cellákra árnyékolást alkalmazhat az egyes cellák elérésével és a`SetShading` módszer.

### Használhatok más színeket a szegélyekhez és az árnyékoláshoz?  
 Teljesen! Bármilyen elérhető színt használhat`System.Drawing.Color` osztály.

### Hogyan igazíthatom vízszintesen középre a táblázatot?  
 A`table.Alignment = TableAlignment.Center;` sor a kódban vízszintesen középre helyezi a táblázatot az oldalon.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
