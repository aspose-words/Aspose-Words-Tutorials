---
title: A tartalomvezérlők módosítása
linktitle: A tartalomvezérlők módosítása
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan módosíthatja a strukturált dokumentumcímkéket a Wordben az Aspose.Words for .NET használatával. Frissítse a szöveget, a legördülő listákat és a képeket lépésről lépésre.
weight: 10
url: /hu/net/programming-with-sdt/modify-content-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# A tartalomvezérlők módosítása

## Bevezetés

Ha valaha is dolgozott Word-dokumentumokkal, és módosítania kellett a strukturált tartalomvezérlőket – például az egyszerű szöveget, a legördülő listákat vagy a képeket – az Aspose.Words for .NET használatával, akkor jó helyen jár! A strukturált dokumentumcímkék (SDT) olyan hatékony eszközök, amelyek egyszerűbbé és rugalmasabbá teszik a dokumentumautomatizálást. Ebben az oktatóanyagban belemerülünk abba, hogyan módosíthatja ezeket az SDT-ket az igényeinek megfelelően. Függetlenül attól, hogy szöveget frissít, legördülő menüt módosít, vagy képeket cserél ki, ez az útmutató lépésről lépésre végigvezeti a folyamaton.

## Előfeltételek

Mielőtt belevágnánk a tartalomvezérlők módosításának aprólékos dolgaiba, győződjön meg arról, hogy rendelkezik a következőkkel:

1.  Aspose.Words for .NET telepítve: Győződjön meg arról, hogy telepítve van az Aspose.Words könyvtár. Ha nem, akkor megteheti[töltse le itt](https://releases.aspose.com/words/net/).

2. Alapvető C# ismerete: Ez az oktatóanyag feltételezi, hogy ismeri az alapvető C# programozási fogalmakat.

3. .NET fejlesztői környezet: A .NET-alkalmazások futtatásához be kell állítania egy IDE-t, mint a Visual Studio.

4. Mintadokumentum: Word-mintadokumentumot fogunk használni különféle típusú SDT-kkel. Használhatja a példában szereplőt, vagy létrehozhatja sajátját.

5.  Hozzáférés az Aspose dokumentációjához: Részletesebb információkért tekintse meg a[Aspose.Words dokumentáció](https://reference.aspose.com/words/net/).

## Névterek importálása

Az Aspose.Words használatához importálnia kell a megfelelő névtereket a C# projektbe. Íme, hogyan kell csinálni:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Ezek a névterek hozzáférést biztosítanak a Word-dokumentumokban lévő strukturált dokumentumcímkék kezeléséhez szükséges osztályokhoz és metódusokhoz.

## 1. lépés: Állítsa be a dokumentum elérési útját

 Mielőtt bármilyen változtatást végrehajtana, meg kell adnia a dokumentum elérési útját. Cserélje ki`"YOUR DOCUMENT DIRECTORY"` a tényleges elérési úttal, ahol a dokumentumot tárolják.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Structured document tags.docx");
```

## 2. lépés: Hurok a strukturált dokumentumcímkéken keresztül

 Az SDT-k módosításához először át kell tekintenie a dokumentumban található összes SDT-t. Ez a`GetChildNodes` módszer az összes típusú csomópont lekéréséhez`StructuredDocumentTag`.

```csharp
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    // Módosítsa az SDT-ket típusuk alapján
}
```

## 3. lépés: Módosítsa az egyszerű szöveges SDT-ket

Ha az SDT egyszerű szöveges típusú, akkor lecserélheti a tartalmát. Először törölje a meglévő tartalmat, majd adjon hozzá új szöveget.

```csharp
if (sdt.SdtType == SdtType.PlainText)
{
    sdt.RemoveAllChildren();
    Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
    Run run = new Run(doc, "new text goes here");
    para.AppendChild(run);
}
```

 Magyarázat: Tessék,`RemoveAllChildren()`törli az SDT meglévő tartalmát. Ezután létrehozunk egy újat`Paragraph` és`Run` objektumot az új szöveg beszúrásához.

## 4. lépés: A legördülő lista SDT-k módosítása

 A legördülő listás SDT-k esetén módosíthatja a kiválasztott elemet a`ListItems` gyűjtemény. Itt kiválasztjuk a lista harmadik elemét.

```csharp
if (sdt.SdtType == SdtType.DropDownList)
{
    SdtListItem secondItem = sdt.ListItems[2];
    sdt.ListItems.SelectedValue = secondItem;
}
```

Magyarázat: Ez a kódrészlet a 2. indexben lévő elemet (harmadik elem) választja ki a legördülő listából. Állítsa be az indexet igényei szerint.

## 5. lépés: Módosítsa a kép SDT-ket

Egy kép SDT-n belüli frissítéséhez lecserélheti a meglévő képet egy újra.

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

 Magyarázat: Ez a kód ellenőrzi, hogy az alakzat tartalmaz-e képet, majd lecseréli egy új, a címen található képre`ImagesDir`.

## 6. lépés: Mentse el a módosított dokumentumot

Az összes szükséges módosítás elvégzése után mentse el a módosított dokumentumot új néven, hogy az eredeti dokumentum sértetlen maradjon.

```csharp
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");
```

Magyarázat: Ez új fájlnévvel menti a dokumentumot, így könnyen meg tudja különböztetni az eredetitől.

## Következtetés

Word-dokumentumok tartalomvezérlőinek módosítása az Aspose.Words for .NET használatával egyszerű, ha megértette a szükséges lépéseket. Legyen szó szövegfrissítésről, legördülő kijelölések módosításáról vagy képek cseréjéről, az Aspose.Words robusztus API-t biztosít ezekhez a feladatokhoz. Az oktatóanyag követésével hatékonyan kezelheti és testreszabhatja dokumentumai strukturált tartalomvezérlőit, így dokumentumait dinamikusabbá és az Ön igényeihez szabottabbá teheti.

## GYIK

1. Mi az a strukturált dokumentumcímke (SDT)?

Az SDT-k a Word-dokumentumok olyan elemei, amelyek segítenek kezelni és formázni a dokumentumtartalmat, például szövegdobozokat, legördülő listákat vagy képeket.

2. Hogyan adhatok hozzá új legördülő elemet az SDT-hez?

 Új elem hozzáadásához használja a`ListItems` tulajdonságot, és csatoljon egy újat`SdtListItem` a gyűjteményhez.

3. Az Aspose.Words segítségével eltávolíthatom az SDT-ket egy dokumentumból?

Igen, eltávolíthatja az SDT-ket, ha hozzáfér a dokumentum csomópontjaihoz, és törli a kívánt SDT-t.

4. Hogyan kezelhetem a más elemekbe ágyazott SDT-ket?

 Használja a`GetChildNodes` metódus megfelelő paraméterekkel a beágyazott SDT-k eléréséhez.

5. Mi a teendő, ha a módosítandó SDT nem látható a dokumentumban?

Győződjön meg arról, hogy az SDT nincs rejtve vagy védett. Ellenőrizze a dokumentumbeállításokat, és győződjön meg arról, hogy a kód megfelelően célozza az SDT típust.


### Példa forráskódra a tartalomvezérlők módosításához az Aspose.Words segítségével .NET-hez 

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

Ennyi! Sikeresen módosította a Word-dokumentum különböző típusú tartalomvezérlőit az Aspose.Words for .NET segítségével.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
