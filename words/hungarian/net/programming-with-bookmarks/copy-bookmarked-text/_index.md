---
title: Könyvjelzővel ellátott szöveg másolása Word dokumentumba
linktitle: Könyvjelzővel ellátott szöveg másolása Word dokumentumba
second_title: Aspose.Words Document Processing API
description: Könnyedén másolhat könyvjelzővel ellátott szöveget a Word-dokumentumok között az Aspose.Words for .NET segítségével. Ebből a lépésről lépésre szóló útmutatóból megtudhatja, hogyan.
weight: 10
url: /hu/net/programming-with-bookmarks/copy-bookmarked-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Könyvjelzővel ellátott szöveg másolása Word dokumentumba

## Bevezetés

Volt már olyan, hogy bizonyos szakaszokat kell másolnia egyik Word-dokumentumból a másikba? Nos, szerencséd van! Ebben az oktatóanyagban végigvezetjük, hogyan másolhat könyvjelzővel ellátott szöveget egyik Word-dokumentumból a másikba az Aspose.Words for .NET használatával. Akár dinamikus jelentést készít, akár automatizálja a dokumentumgenerálást, ez az útmutató leegyszerűsíti a folyamatot.

## Előfeltételek

Mielőtt belemerülnénk, győződjön meg arról, hogy rendelkezik az alábbiakkal:

-  Aspose.Words for .NET Library: Letöltheti innen[itt](https://releases.aspose.com/words/net/).
- Fejlesztői környezet: Visual Studio vagy bármely más .NET fejlesztői környezet.
- C# alapismeretek: C# programozás és .NET keretrendszer ismerete.

## Névterek importálása

A kezdéshez győződjön meg arról, hogy a szükséges névtereket importálta a projektbe:

```csharp
using Aspose.Words;
using Aspose.Words.Import;
using Aspose.Words.Bookmark;
```

## 1. lépés: Töltse be a forrásdokumentumot

Először is be kell töltenie azt a forrásdokumentumot, amely a másolni kívánt könyvjelzővel ellátott szöveget tartalmazza.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Bookmarks.docx");
```

 Itt,`dataDir` a dokumentumkönyvtár elérési útja, és`Bookmarks.docx` a forrásdokumentum.

## 2. lépés: A könyvjelző azonosítása

Ezután azonosítsa a könyvjelzőt, amelyet másolni szeretne a forrásdokumentumból.

```csharp
Bookmark srcBookmark = srcDoc.Range.Bookmarks["MyBookmark1"];
```

 Cserélje ki`"MyBookmark1"` a könyvjelző tényleges nevével.

## 3. lépés: Készítse el a céldokumentumot

Most hozzon létre egy új dokumentumot, amelybe a könyvjelzővel ellátott szöveg másolásra kerül.

```csharp
Document dstDoc = new Document();
CompositeNode dstNode = dstDoc.LastSection.Body;
```

## 4. lépés: Importáljon könyvjelzővel ellátott tartalmat

 A stílusok és formázások megőrzése érdekében használja a`NodeImporter` a könyvjelzővel ellátott tartalom importálása a forrásdokumentumból a céldokumentumba.

```csharp
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);
AppendBookmarkedText(importer, srcBookmark, dstNode);
```

## 5. lépés: Határozza meg az AppendBookmarkedText módszert

Itt történik a varázslat. Határozzon meg egy módszert a könyvjelzővel ellátott szöveg másolására:

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

## 6. lépés: Mentse el a céldokumentumot

Végül mentse el a céldokumentumot a másolt tartalom ellenőrzéséhez.

```csharp
dstDoc.Save(dataDir + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

## Következtetés

És ennyi! Sikeresen átmásolta a könyvjelzővel ellátott szöveget egyik Word-dokumentumból a másikba az Aspose.Words for .NET segítségével. Ez a módszer hatékonyan automatizálja a dokumentumkezelési feladatokat, hatékonyabbá és egyszerűbbé teszi a munkafolyamatot.

## GYIK

### Másolhatok több könyvjelzőt egyszerre?
Igen, ismételhet több könyvjelzőt is, és ugyanazt a módszert használhatja mindegyik másolásához.

### Mi történik, ha a könyvjelző nem található?
 A`Range.Bookmarks` ingatlan visszakerül`null`, ezért mindenképpen kezelje ezt az esetet a kivételek elkerülése érdekében.

### Megőrizhetem az eredeti könyvjelző formázását?
 Teljesen! Használata`ImportFormatMode.KeepSourceFormatting` biztosítja az eredeti formázás megőrzését.

### Van-e korlátozás a könyvjelzővel ellátott szöveg méretére?
Nincs konkrét korlát, de a teljesítmény rendkívül nagy dokumentumok esetén változhat.

### Másolhatok szöveget a különböző Word dokumentumformátumok között?
Igen, az Aspose.Words különféle Word-formátumokat támogat, és a módszer ezeken a formátumokon is működik.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
