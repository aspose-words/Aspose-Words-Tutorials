---
"description": "Tanuld meg, hogyan alkalmazhatsz körvonalas szegélyt egy táblázatra Wordben az Aspose.Words for .NET segítségével. Kövesd lépésről lépésre szóló útmutatónkat a tökéletes táblázatformázáshoz."
"linktitle": "Körvonal szegélyének alkalmazása"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Körvonal szegélyének alkalmazása"
"url": "/hu/net/programming-with-table-styles-and-formatting/apply-outline-border/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Körvonal szegélyének alkalmazása

## Bevezetés

mai oktatóanyagban az Aspose.Words for .NET segítségével merülünk el a dokumentummanipuláció világában. Konkrétan azt fogjuk megtanulni, hogyan alkalmazhatunk körvonalas szegélyt egy táblázatra egy Word-dokumentumban. Ez egy fantasztikus készség, amit érdemes beépíteni az eszköztáradba, ha gyakran dolgozol automatizált dokumentumgenerálással és -formázással. Kezdjük el tehát ezt az utat, hogy a táblázataid ne csak funkcionálisak, hanem vizuálisan is vonzóak is legyenek.

## Előfeltételek

Mielőtt belevágnánk a kódba, van néhány dolog, amire szükséged lesz:

1. Aspose.Words for .NET: Telepítenie kell az Aspose.Words for .NET programot. Letöltheti [itt](https://releases.aspose.com/words/net/).
2. Fejlesztői környezet: Egy megfelelő fejlesztői környezet, például a Visual Studio.
3. C# alapismeretek: A C# alapvető ismerete segít a tutoriál követésében.

## Névterek importálása

Először is győződj meg róla, hogy importáltad a szükséges névtereket. Ez elengedhetetlen az Aspose.Words funkcióinak eléréséhez.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

Bontsuk le a folyamatot egyszerű, könnyen követhető lépésekre.

## 1. lépés: A dokumentum betöltése

Először is be kell töltenünk azt a Word dokumentumot, amelyik a formázni kívánt táblázatot tartalmazza.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Tables.docx");
```

Ebben a lépésben a következőt használjuk: `Document` osztály az Aspose.Words-ből egy meglévő dokumentum betöltéséhez. Csere `"YOUR DOCUMENT DIRECTORY"` dokumentum tényleges tárolási útvonalával.

## 2. lépés: Hozzáférés a táblázathoz

Ezután hozzá kell férnünk ahhoz a konkrét táblázathoz, amelyet formázni szeretnénk. 

```csharp
Table table = (Table)doc.GetChild(NodeType.Table, 0, true);
```

Itt, `GetChild` metódus a dokumentum első táblázatát kéri le. A paraméterek `NodeType.Table, 0, true` győződjünk meg arról, hogy a megfelelő csomóponttípust kapjuk.

## 3. lépés: A táblázat igazítása

Most igazítsuk középre a táblázatot az oldalon.

```csharp
table.Alignment = TableAlignment.Center;
```

Ez a lépés biztosítja, hogy az asztal szépen középre legyen igazítva, professzionális megjelenést kölcsönözve neki.

## 4. lépés: Törölje a meglévő határokat

Mielőtt új szegélyeket alkalmaznánk, el kell távolítanunk a meglévőket.

```csharp
table.ClearBorders();
```

A szegélyek kitisztítása biztosítja, hogy az új szegélyek tisztán kerüljenek felhelyezésre, a régi stílusok zavarása nélkül.

## 5. lépés: Vázlatszegélyek beállítása

Most alkalmazzuk a zöld körvonalas szegélyeket a táblázatra.

```csharp
table.SetBorder(BorderType.Left, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Right, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Top, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Bottom, LineStyle.Single, 1.5, Color.Green, true);
```

Minden szegélytípust (bal, jobb, felső, alsó) külön állítunk be. `LineStyle.Single` egy folytonos vonalért, `1.5` a vonalvastagsághoz, és `Color.Green` a szegély színéhez.

## 6. lépés: Cellaárnyékolás alkalmazása

A táblázat vizuálisan vonzóbbá tétele érdekében töltsük ki a cellákat világoszöld színnel.

```csharp
table.SetShading(TextureIndex.TextureSolid, Color.LightGreen, Color.Empty);
```

Itt, `SetShading` a cellákra egyszínű világoszöld színt alkalmaznak, ami kiemeli a táblázatot.

## 7. lépés: A dokumentum mentése

Végül mentse el a módosított dokumentumot.

```csharp
doc.Save(dataDir + "WorkingWithTableStylesAndFormatting.ApplyOutlineBorder.docx");
```

Ez a lépés a formázással menti a dokumentumot. Megnyithatja, hogy megtekinthesse a szépen formázott táblázatot.

## Következtetés

És íme! A következő lépéseket követve sikeresen alkalmaztál egy körvonalas szegélyt egy Word-dokumentumban lévő táblázatra az Aspose.Words for .NET segítségével. Ez az oktatóanyag a dokumentum betöltését, a táblázat elérését, igazítását, a meglévő szegélyek törlését, új szegélyek alkalmazását, cellaárnyékolás hozzáadását és végül a dokumentum mentését ismertette. 

Ezekkel a készségekkel javíthatod a táblázataid vizuális megjelenítését, így dokumentumaid professzionálisabbak és vonzóbbak lesznek. Jó programozást!

## GYIK

### Alkalmazhatok különböző stílusokat a táblázat minden szegélyére?  
Igen, az egyes szegélyekre különböző stílusokat és színeket alkalmazhat a paraméterek módosításával a `SetBorder` módszer.

### Hogyan tudom megváltoztatni a szegély szélességét?  
A szélességet a harmadik paraméter módosításával módosíthatja a `SetBorder` módszer. Például, `1.5` 1,5 pont szélességet állít be.

### Lehetséges árnyékolást alkalmazni az egyes cellákra?  
Igen, az egyes cellákra árnyékolást alkalmazhat úgy, hogy minden egyes cellához hozzáfér, és a `SetShading` módszer.

### Használhatok más színeket szegélyekhez és árnyékoláshoz?  
Természetesen! Bármelyik elérhető színt használhatod. `System.Drawing.Color` osztály.

### Hogyan tudom vízszintesen középre igazítani a táblázatot?  
A `table.Alignment = TableAlignment.Center;` A kódban a sor vízszintesen középre igazítja a táblázatot az oldalon.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}