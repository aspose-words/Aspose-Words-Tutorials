---
title: Dokumentum beszúrása a körlevélbe
linktitle: Dokumentum beszúrása a körlevélbe
second_title: Aspose.Words Document Processing API
description: Ebben az átfogó, lépésenkénti oktatóanyagban megtudhatja, hogyan lehet dokumentumokat beszúrni a körlevél mezőkbe az Aspose.Words for .NET használatával.
weight: 10
url: /hu/net/clone-and-combine-documents/insert-document-at-mail-merge/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentum beszúrása a körlevélbe

## Bevezetés

Üdvözöljük a dokumentumautomatizálás világában az Aspose.Words for .NET segítségével! Gondolkozott már azon, hogyan lehet dokumentumokat dinamikusan beszúrni egy fő dokumentum meghatározott mezőibe egy körlevél-művelet során? Nos, jó helyen jársz. Ez az oktatóanyag lépésről lépésre végigvezeti a dokumentumok körlevél-mezőkbe történő beszúrásának folyamatán az Aspose.Words for .NET használatával. Olyan ez, mint egy puzzle összerakása, ahol minden darab tökéletesen a helyére kerül. Szóval, merüljünk bele!

## Előfeltételek

Mielőtt elkezdenénk, győződjön meg arról, hogy rendelkezik a következőkkel:

1.  Aspose.Words for .NET: Megteheti[töltse le a legújabb verziót innen](https://releases.aspose.com/words/net/) . Ha licencet kell vásárolnia, megteheti[itt](https://purchase.aspose.com/buy) . Alternatív megoldásként kaphat a[ideiglenes engedély](https://purchase.aspose.com/temporary-license/) vagy próbálja ki a[ingyenes próbaverzió](https://releases.aspose.com/).
2. Fejlesztői környezet: Visual Studio vagy bármely más C# IDE.
3. A C# alapismeretei: A C# programozás ismerete gyerekjáték lesz ez az oktatóanyag.

## Névterek importálása

Először is importálnia kell a szükséges névtereket. Ezek olyanok, mint a projekt építőkövei.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.MailMerging;
using System.Linq;
```

Bontsuk fel a folyamatot kezelhető lépésekre. Minden lépés az előzőre épül, és a teljes megoldáshoz vezet.

## 1. lépés: A címtár beállítása

A dokumentumok beszúrásának megkezdése előtt meg kell határoznia a dokumentumkönyvtár elérési útját. Itt tárolják a dokumentumokat.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 2. lépés: A fő dokumentum betöltése

Ezután töltse be a fő dokumentumot. Ez a dokumentum tartalmazza azokat az egyesítési mezőket, amelyekbe más dokumentumok kerülnek beszúrásra.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

## 3. lépés: A visszahívási összevonás mező beállítása

Az egyesítési folyamat kezeléséhez be kell állítania egy visszahívási funkciót. Ez a funkció felelős a dokumentumok beszúrásáért a megadott egyesítési mezőkbe.

```csharp
mainDoc.MailMerge.FieldMergingCallback = new InsertDocumentAtMailMergeHandler();
```

## 4. lépés: A körlevél végrehajtása

Most itt az ideje végrehajtani a körlevél-összevonást. Itt történik a varázslat. Meg kell adni az egyesítési mezőt és a dokumentumot, amelyet ebbe a mezőbe kell beilleszteni.

```csharp
mainDoc.MailMerge.Execute(new[] { "Document_1" }, new object[] { dataDir + "Document insertion 2.docx" });
```

## 5. lépés: A dokumentum mentése

körlevél-összevonás befejezése után elmenti a módosított dokumentumot. Ebben az új dokumentumban ott lesz a beszúrt tartalom, ahol szeretné.

```csharp
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

## 6. lépés: A visszahíváskezelő létrehozása

A visszahíváskezelő egy olyan osztály, amely speciális feldolgozást végez az egyesítési mező számára. Betölti a mező értékében megadott dokumentumot és beszúrja az aktuális egyesítési mezőbe.

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

## 7. lépés: A dokumentum beszúrása

Ez a módszer beszúrja a megadott dokumentumot az aktuális bekezdésbe vagy táblázatcellába.

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

És megvan! Sikeresen beszúrt dokumentumokat meghatározott mezőkbe az Aspose.Words for .NET használatával végzett körlevél-művelet során. Ezzel a hatékony funkcióval rengeteg időt és erőfeszítést takaríthat meg, különösen, ha nagy mennyiségű dokumentumot kezel. Tekintsd úgy, mintha van egy személyi asszisztens, aki elvégzi helyetted az összes nehézemelést. Szóval, menj és próbáld ki. Boldog kódolást!

## GYIK

### Beszúrhatok több dokumentumot különböző egyesítési mezőkbe?
Igen, megteheti. Egyszerűen adja meg a megfelelő egyesítési mezőket és a megfelelő dokumentumútvonalakat a`MailMerge.Execute` módszer.

### Lehetséges a beillesztett dokumentumot a fő dokumentumtól eltérően formázni?
 Teljesen! Használhatja a`ImportFormatMode` paraméter a`NodeImporter` a formázás szabályozásához.

### Mi a teendő, ha az egyesítési mező neve dinamikus?
A dinamikus egyesítési mezőneveket úgy kezelheti, hogy paraméterként adja át őket a visszahíváskezelőnek.

### Használhatom ezt a módszert különböző fájlformátumokkal?
Igen, az Aspose.Words különféle fájlformátumokat támogat, beleértve a DOCX-et, PDF-et és még sok mást.

### Hogyan kezelhetem a hibákat a dokumentumbeillesztési folyamat során?
Az esetlegesen előforduló kivételek kezeléséhez alkalmazza a hibakezelést a visszahíváskezelőben.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
