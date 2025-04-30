---
"description": "Könnyedén másolhat könyvjelzővel ellátott szöveget Word-dokumentumok között az Aspose.Words for .NET segítségével. Tanulja meg, hogyan kell ezt megtenni ebből a lépésről lépésre szóló útmutatóból."
"linktitle": "Könyvjelzővel ellátott szöveg másolása Word dokumentumban"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Könyvjelzővel ellátott szöveg másolása Word dokumentumban"
"url": "/hu/net/programming-with-bookmarks/copy-bookmarked-text/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Könyvjelzővel ellátott szöveg másolása Word dokumentumban

## Bevezetés

Előfordult már, hogy bizonyos részeket kellett átmásolni egyik Word-dokumentumból a másikba? Nos, szerencséd van! Ebben az oktatóanyagban bemutatjuk, hogyan másolhatsz könyvjelzővel ellátott szöveget egyik Word-dokumentumból a másikba az Aspose.Words for .NET segítségével. Akár dinamikus jelentést készítesz, akár automatizálod a dokumentumok generálását, ez az útmutató leegyszerűsíti a folyamatot.

## Előfeltételek

Mielőtt belevágnánk, győződjünk meg róla, hogy a következőkkel rendelkezünk:

- Aspose.Words .NET könyvtárhoz: Letöltheti innen: [itt](https://releases.aspose.com/words/net/).
- Fejlesztői környezet: Visual Studio vagy bármilyen más .NET fejlesztői környezet.
- C# alapismeretek: Jártasság a C# programozásban és a .NET keretrendszerben.

## Névterek importálása

Kezdésként győződjön meg arról, hogy a szükséges névterek importálva vannak a projektbe:

```csharp
using Aspose.Words;
using Aspose.Words.Import;
using Aspose.Words.Bookmark;
```

## 1. lépés: A forrásdokumentum betöltése

Először is be kell töltenie a forrásdokumentumot, amely a másolni kívánt könyvjelzővel ellátott szöveget tartalmazza.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Bookmarks.docx");
```

Itt, `dataDir` dokumentumkönyvtár elérési útja, és `Bookmarks.docx` az a forrásdokumentum.

## 2. lépés: A könyvjelző azonosítása

Ezután azonosítsa a forrásdokumentumból másolni kívánt könyvjelzőt.

```csharp
Bookmark srcBookmark = srcDoc.Range.Bookmarks["MyBookmark1"];
```

Csere `"MyBookmark1"` a könyvjelző tényleges nevével.

## 3. lépés: Céldokumentum létrehozása

Most hozzon létre egy új dokumentumot, ahová a könyvjelzővel ellátott szöveget másolni fogja.

```csharp
Document dstDoc = new Document();
CompositeNode dstNode = dstDoc.LastSection.Body;
```

## 4. lépés: Könyvjelzővel ellátott tartalom importálása

A stílusok és formázás megőrzésének biztosításához használja a `NodeImporter` a könyvjelzővel ellátott tartalom importálásához a forrásdokumentumból a céldokumentumba.

```csharp
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);
AppendBookmarkedText(importer, srcBookmark, dstNode);
```

## 5. lépés: Az AppendBookmarkedText metódus definiálása

Itt történik a varázslat. Definiálj egy metódust a könyvjelzővel ellátott szöveg másolásának kezeléséhez:

```csharp
private void AppendBookmarkedText(NodeImporter importer, Bookmark srcBookmark, CompositeNode dstNode)
{
    Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;
    Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

    if (startPara == null || endPara == null)
        throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");

    if (startPara.ParentNode != endPara.ParentNode)
        throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");

    Node endNode = endPara.NextSibling;

    for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
    {
        Node newNode = importer.ImportNode(curNode, true);
        dstNode.AppendChild(newNode);
    }
}
```

## 6. lépés: A céldokumentum mentése

Végül mentse el a céldokumentumot a másolt tartalom ellenőrzéséhez.

```csharp
dstDoc.Save(dataDir + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

## Következtetés

És ennyi! Sikeresen átmásoltad a könyvjelzővel ellátott szöveget egyik Word-dokumentumból a másikba az Aspose.Words for .NET segítségével. Ez a módszer hatékony a dokumentumkezelési feladatok automatizálásában, így a munkafolyamat hatékonyabbá és egyszerűbbé válik.

## GYIK

### Több könyvjelzőt is másolhatok egyszerre?
Igen, több könyvjelzőn is végighaladhat, és ugyanazzal a módszerrel másolhatja mindegyiket.

### Mi történik, ha a könyvjelző nem található?
A `Range.Bookmarks` visszakerül az ingatlan `null`, ezért ügyeljen arra, hogy ezt az esetet kezelje a kivételek elkerülése érdekében.

### Megőrizhetem az eredeti könyvjelző formázását?
Abszolút! Használat `ImportFormatMode.KeepSourceFormatting` biztosítja az eredeti formázás megőrzését.

### Van korlátozás a könyvjelzővel ellátott szöveg méretére?
Nincs konkrét korlát, de a teljesítmény rendkívül nagy dokumentumok esetén változhat.

### Másolhatok szöveget különböző Word dokumentumformátumok között?
Igen, az Aspose.Words számos Word formátumot támogat, és a metódus ezekben a formátumokban működik.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}