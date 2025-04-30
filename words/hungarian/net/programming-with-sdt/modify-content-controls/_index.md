---
"description": "Tanuld meg, hogyan módosíthatod a strukturált dokumentumcímkéket a Wordben az Aspose.Words for .NET segítségével. Frissítsd a szöveget, a legördülő menüket és a képeket lépésről lépésre."
"linktitle": "Tartalomvezérlők módosítása"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Tartalomvezérlők módosítása"
"url": "/hu/net/programming-with-sdt/modify-content-controls/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tartalomvezérlők módosítása

## Bevezetés

Ha valaha is dolgoztál Word dokumentumokkal, és strukturált tartalomvezérlőket – például sima szöveget, legördülő listákat vagy képeket – kellett módosítanod az Aspose.Words for .NET segítségével, akkor jó helyen jársz! A strukturált dokumentumcímkék (SDT-k) hatékony eszközök, amelyek megkönnyítik és rugalmasabbá teszik a dokumentumautomatizálást. Ebben az oktatóanyagban bemutatjuk, hogyan módosíthatod ezeket az SDT-ket az igényeidnek megfelelően. Akár szöveget frissítesz, akár legördülő listákat módosítasz, akár képeket cserélsz ki, ez az útmutató lépésről lépésre végigvezet a folyamaton.

## Előfeltételek

Mielőtt belevágnánk a tartalomvezérlők módosításának részleteibe, győződjünk meg arról, hogy a következőkkel rendelkezünk:

1. Aspose.Words .NET-hez telepítve: Győződjön meg róla, hogy telepítve van az Aspose.Words könyvtár. Ha nem, akkor megteheti [töltsd le itt](https://releases.aspose.com/words/net/).

2. C# alapismeretek: Ez az oktatóanyag feltételezi, hogy ismered a C# programozás alapvető fogalmait.

3. .NET fejlesztői környezet: Rendelkeznie kell egy .NET alkalmazások futtatásához beállított IDE-vel, például a Visual Studio-val.

4. Mintadokumentum: Egy minta Word-dokumentumot fogunk használni, amely különféle típusú SDT-ket tartalmaz. Használhatja a példában szereplő dokumentumot, vagy létrehozhat sajátot.

5. Hozzáférés az Aspose dokumentációjához: Részletesebb információkért tekintse meg a [Aspose.Words dokumentáció](https://reference.aspose.com/words/net/).

## Névterek importálása

Az Aspose.Words használatának megkezdéséhez importálnia kell a releváns névtereket a C# projektjébe. Így teheti meg:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Ezek a névterek hozzáférést biztosítanak azokhoz az osztályokhoz és metódusokhoz, amelyek a strukturált dokumentumcímkék Word-dokumentumokban történő kezeléséhez szükségesek.

## 1. lépés: Dokumentumútvonal beállítása

Mielőtt bármilyen módosítást végezne, meg kell adnia a dokumentum elérési útját. Csere `"YOUR DOCUMENT DIRECTORY"` dokumentum tényleges tárolási útvonalával.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Structured document tags.docx");
```

## 2. lépés: Strukturált dokumentumcímkék ismétlése

Az SDT-k módosításához először végig kell menni a dokumentum összes SDT-jén. Ezt a következővel teheti meg: `GetChildNodes` metódus az összes típusú csomópont lekérésére `StructuredDocumentTag`.

```csharp
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    // SDT-k módosítása típusuk alapján
}
```

## 3. lépés: Sima szöveges SDT-k módosítása

Ha az SDT sima szöveges típusú, akkor lecserélheti a tartalmát. Először törölje a meglévő tartalmat, majd adjon hozzá új szöveget.

```csharp
if (sdt.SdtType == SdtType.PlainText)
{
    sdt.RemoveAllChildren();
    Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
    Run run = new Run(doc, "new text goes here");
    para.AppendChild(run);
}
```

Magyarázat: Itt, `RemoveAllChildren()` törli az SDT meglévő tartalmát. Ezután létrehozunk egy újat `Paragraph` és `Run` objektum az új szöveg beszúrásához.

## 4. lépés: Legördülő lista SDT-k módosítása

Legördülő listás SDT-k esetén a kiválasztott elemet a következőképpen módosíthatja: `ListItems` gyűjtemény. Itt a lista harmadik elemét választjuk ki.

```csharp
if (sdt.SdtType == SdtType.DropDownList)
{
    SdtListItem secondItem = sdt.ListItems[2];
    sdt.ListItems.SelectedValue = secondItem;
}
```

Magyarázat: Ez a kódrészlet a 2. indexű (harmadik) elemet választja ki a legördülő listából. Módosítsa az indexet az igényei szerint.

## 5. lépés: Kép SDT-k módosítása

Egy kép SDT-n belüli kép frissítéséhez a meglévő képet egy újra cserélheti.

```csharp
if (sdt.SdtType == SdtType.Picture)
{
    Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
    if (shape.HasImage)
    {
        shape.ImageData.SetImage(ImagesDir + "Watermark.png");
    }
}
```

Magyarázat: Ez a kód ellenőrzi, hogy az alakzat tartalmaz-e képet, majd egy új képpel helyettesíti azt, amely a következő címen található: `ImagesDir`.

## 6. lépés: Mentse el a módosított dokumentumot

Miután elvégezte az összes szükséges módosítást, mentse el a módosított dokumentumot új néven, hogy az eredeti dokumentum érintetlen maradjon.

```csharp
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");
```

Magyarázat: Ez új fájlnévvel menti a dokumentumot, így könnyen megkülönböztethető az eredetitől.

## Következtetés

A Word-dokumentumok tartalomvezérlőinek módosítása az Aspose.Words for .NET segítségével egyszerűen elvégezhető, ha megértjük a szükséges lépéseket. Akár szöveget frissítünk, akár legördülő menükben módosítjuk a kijelölt elemeket, akár képeket cserélünk, az Aspose.Words robusztus API-t biztosít ezekhez a feladatokhoz. Az oktatóanyag követésével hatékonyan kezelhetjük és testreszabhatjuk dokumentumaink strukturált tartalomvezérlőit, így dokumentumaink dinamikusabbak és az igényeinknek megfelelőbbek lesznek.

## GYIK

1. Mi az a strukturált dokumentumcímke (SDT)?

Az SDT-k olyan elemek a Word-dokumentumokban, amelyek segítenek a dokumentum tartalmának kezelésében és formázásában, például szövegdobozok, legördülő listák vagy képek.

2. Hogyan adhatok hozzá egy új legördülő menüelemet egy SDT-hez?

Új elem hozzáadásához használja a `ListItems` tulajdonságot, és fűzz hozzá egy újat `SdtListItem` a gyűjteményhez.

3. Használhatom az Aspose.Words programot SDT-k eltávolítására egy dokumentumból?

Igen, az SDT-ket a dokumentum csomópontjainak elérésével és a kívánt SDT törlésével távolíthatja el.

4. Hogyan kezelhetem a más elemekbe ágyazott SDT-ket?

Használd a `GetChildNodes` metódus megfelelő paraméterekkel a beágyazott SDT-k eléréséhez.

5. Mit tegyek, ha a módosítandó SDT nem látható a dokumentumban?

Győződjön meg arról, hogy az SDT nincs rejtve vagy védve. Ellenőrizze a dokumentum beállításait, és győződjön meg arról, hogy a kódja helyesen célozza meg az SDT típusát.


### Példa forráskód a tartalomvezérlők módosításához az Aspose.Words for .NET használatával 

```csharp
// A dokumentumkönyvtár elérési útja 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Structured document tags.docx");
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
	switch (sdt.SdtType)
	{
		case SdtType.PlainText:
		{
			sdt.RemoveAllChildren();
			Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
			Run run = new Run(doc, "new text goes here");
			para.AppendChild(run);
			break;
		}
		case SdtType.DropDownList:
		{
			SdtListItem secondItem = sdt.ListItems[2];
			sdt.ListItems.SelectedValue = secondItem;
			break;
		}
		case SdtType.Picture:
		{
			Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
			if (shape.HasImage)
			{
				shape.ImageData.SetImage(ImagesDir + "Watermark.png");
			}
			break;
		}
	}
}
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");

```

Ennyi! Sikeresen módosítottad a különböző típusú tartalomvezérlőket a Word-dokumentumodban az Aspose.Words for .NET használatával.

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}