---
"description": "Ebben az átfogó, lépésről lépésre haladó oktatóanyagban megtudhatja, hogyan szúrhat be dokumentumokat a körlevelező mezőkbe az Aspose.Words for .NET használatával."
"linktitle": "Dokumentum beszúrása körlevélhez"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Dokumentum beszúrása körlevélhez"
"url": "/hu/net/clone-and-combine-documents/insert-document-at-mail-merge/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentum beszúrása körlevélhez

## Bevezetés

Üdvözlünk a dokumentumautomatizálás világában az Aspose.Words for .NET segítségével! Elgondolkodott már azon, hogyan szúrhat be dinamikusan dokumentumokat egy fő dokumentum adott mezőibe egy körlevelezési művelet során? Nos, jó helyen jár. Ez az oktatóanyag lépésről lépésre végigvezeti Önt a dokumentumok körlevelezési mezőkbe való beszúrásának folyamatán az Aspose.Words for .NET használatával. Olyan ez, mint egy kirakós darab összerakása, ahol minden darab tökéletesen a helyére kerül. Akkor vágjunk bele!

## Előfeltételek

Mielőtt belekezdenénk, győződjünk meg róla, hogy a következőkkel rendelkezünk:

1. Aspose.Words .NET-hez: Meg tudod csinálni [töltsd le a legújabb verziót itt](https://releases.aspose.com/words/net/)Ha licencet kell vásárolnia, megteheti [itt](https://purchase.aspose.com/buy)Alternatív megoldásként szerezhet egy [ideiglenes engedély](https://purchase.aspose.com/temporary-license/) vagy próbáld ki egy [ingyenes próba](https://releases.aspose.com/).
2. Fejlesztői környezet: Visual Studio vagy bármilyen más C# IDE.
3. C# alapismeretek: A C# programozásban való jártasság gyerekjátékká teszi ezt az oktatóanyagot.

## Névterek importálása

Először is importálnod kell a szükséges névtereket. Ezek a projekted építőelemei.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.MailMerging;
using System.Linq;
```

Bontsuk le a folyamatot kezelhető lépésekre. Minden lépés az előzőre épül, elvezetve egy teljes megoldáshoz.

## 1. lépés: A címtár beállítása

Mielőtt elkezdhetné a dokumentumok beszúrását, meg kell adnia a dokumentumok könyvtárának elérési útját. Itt tárolódnak a dokumentumok.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 2. lépés: A fő dokumentum betöltése

Ezután betölti a fő dokumentumot. Ez a dokumentum tartalmazza az egyesítési mezőket, ahová a többi dokumentum be lesz szúrva.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

## 3. lépés: A mezőegyesítés visszahívásának beállítása

Az egyesítési folyamat kezeléséhez be kell állítania egy visszahívó függvényt. Ez a függvény felelős a dokumentumok beszúrásáért a megadott egyesítési mezőkbe.

```csharp
mainDoc.MailMerge.FieldMergingCallback = new InsertDocumentAtMailMergeHandler();
```

## 4. lépés: A körlevél végrehajtása

Most itt az ideje a körlevélkészítésnek. Itt történik a varázslat. Meg kell adnod az egyesítési mezőt és a mezőbe beszúrandó dokumentumot.

```csharp
mainDoc.MailMerge.Execute(new[] { "Document_1" }, new object[] { dataDir + "Document insertion 2.docx" });
```

## 5. lépés: A dokumentum mentése

Miután a körlevél elkészült, mentse el a módosított dokumentumot. Az új dokumentumban a beszúrt tartalom pontosan ott lesz, ahol szeretné.

```csharp
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

## 6. lépés: A visszahívás-kezelő létrehozása

A visszahívás-kezelő egy olyan osztály, amely speciális feldolgozást végez az egyesítési mező számára. Betölti a mező értékében megadott dokumentumot, és beszúrja azt az aktuális egyesítési mezőbe.

```csharp
private class InsertDocumentAtMailMergeHandler : IFieldMergingCallback
{
    void IFieldMergingCallback.FieldMerging(FieldMergingArgs args)
    {
        if (args.DocumentFieldName == "Document_1")
        {
            DocumentBuilder builder = new DocumentBuilder(args.Document);
            builder.MoveToMergeField(args.DocumentFieldName);

            Document subDoc = new Document((string)args.FieldValue);
            InsertDocument(builder.CurrentParagraph, subDoc);

            if (!builder.CurrentParagraph.HasChildNodes)
                builder.CurrentParagraph.Remove();

            args.Text = null;
        }
    }
}
```

## 7. lépés: A dokumentum beillesztése

Ez a metódus beszúrja a megadott dokumentumot az aktuális bekezdésbe vagy táblázatcellába.

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        foreach (Node srcNode in srcSection.Body)
        {
            if (srcNode.NodeType == NodeType.Paragraph)
            {
                Paragraph para = (Paragraph)srcNode;
                if (para.IsEndOfSection && !para.HasChildNodes)
                    continue;
            }

            Node newNode = importer.ImportNode(srcNode, true);
            destinationParent.InsertAfter(newNode, insertionDestination);
            insertionDestination = newNode;
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}
```

## Következtetés

És íme! Sikeresen beszúrtál dokumentumokat adott mezőkbe egy körlevelezési művelet során az Aspose.Words for .NET használatával. Ez a hatékony funkció rengeteg időt és energiát takaríthat meg, különösen nagy mennyiségű dokumentum kezelésekor. Gondolj rá úgy, mint egy személyi asszisztensre, aki elvégzi helyetted az összes nehéz munkát. Szóval, próbáld ki. Jó programozást!

## GYIK

### Beszúrhatok több dokumentumot különböző mezőkbe?
Igen, megteheti. Egyszerűen adja meg a megfelelő egyesítési mezőket és a hozzájuk tartozó dokumentumútvonalakat a `MailMerge.Execute` módszer.

### Lehetséges a beszúrt dokumentumot a fő dokumentumtól eltérően formázni?
Természetesen! Használhatod a `ImportFormatMode` paraméter a `NodeImporter` a formázás szabályozására.

### Mi van, ha az egyesítési mező neve dinamikus?
A dinamikus egyesítési mezők neveit úgy kezelheted, hogy paraméterként adod át őket a visszahívási kezelőnek.

### Használhatom ezt a módszert különböző fájlformátumokkal?
Igen, az Aspose.Words számos fájlformátumot támogat, beleértve a DOCX-et, PDF-et és egyebeket.

### Hogyan kezeljem a dokumentumok beszúrása során felmerülő hibákat?
Implementálj hibakezelést a visszahívási kezelődben az esetlegesen előforduló kivételek kezeléséhez.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}