---
title: Helyezze be a dokumentumot a Csere pontnál
linktitle: Helyezze be a dokumentumot a Csere pontnál
second_title: Aspose.Words Document Processing API
description: Részletes, lépésenkénti útmutatónkból megtudhatja, hogyan lehet zökkenőmentesen beilleszteni egy Word-dokumentumot a másikba az Aspose.Words for .NET segítségével. Tökéletes azoknak a fejlesztőknek, akik egyszerűsíteni szeretnék a dokumentumfeldolgozást.
weight: 10
url: /hu/net/clone-and-combine-documents/insert-document-at-replace/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Helyezze be a dokumentumot a Csere pontnál

## Bevezetés

Szia, dokumentummesterek! Volt már valaha olyan, hogy térdig a kódban találta magát, amikor megpróbálta kitalálni, hogyan lehet zökkenőmentesen beilleszteni egy Word-dokumentumot a másikba? Ne féljen, mert ma az Aspose.Words for .NET világába merülünk, hogy ezt a feladatot gyerekjáték tegyük. Részletes, lépésről lépésre bemutatjuk, hogyan használhatja ezt a hatékony könyvtárat dokumentumok beszúrására bizonyos pontokon a keresési és csereművelet során. Készen áll arra, hogy Aspose.Words varázslóvá váljon? Kezdjük is!

## Előfeltételek

Mielőtt belevágnánk a kódba, néhány dolgot meg kell határoznia:

-  Visual Studio: Győződjön meg arról, hogy a Visual Studio telepítve van a gépen. Ha még nincs meg, letöltheti innen[itt](https://visualstudio.microsoft.com/).
-  Aspose.Words for .NET: Szüksége lesz az Aspose.Words könyvtárra. Beszerezheti a[Aspose honlapja](https://releases.aspose.com/words/net/).
- Alapvető C#-ismeretek: A C# és a .NET alapvető ismeretei segítenek követni ezt az oktatóanyagot.

Rendben, ha nincs az útból, piszkáljuk be a kezünket egy kóddal!

## Névterek importálása

Először is importálnunk kell a szükséges névtereket az Aspose.Words használatához. Ez olyan, mintha az összes eszközt összegyűjtené egy projekt elindítása előtt. Adja hozzá ezeket a C# fájl tetején található direktívák használatával:

```csharp
using System;
using System.Text.RegularExpressions;
using Aspose.Words;
using Aspose.Words.Replacing;
using Aspose.Words.Tables;
```

Most, hogy megvannak az előfeltételeink, bontsuk le a folyamatot falatnyi lépésekre. Minden lépés döntő jelentőségű, és közelebb visz a célunkhoz.

## 1. lépés: A Dokumentumkönyvtár beállítása

Először is meg kell adnunk a könyvtárat, ahol a dokumentumainkat tároljuk. Ez olyan, mint a színpad beállítása a nagy előadás előtt.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Cserélje ki`"YOUR DOCUMENT DIRECTORY"` a könyvtár elérési útjával. Itt élnek és lélegzik a dokumentumai.

## 2. lépés: Töltse be a fő dokumentumot

Ezután betöltjük azt a fő dokumentumot, amelybe egy másik dokumentumot szeretnénk beilleszteni. Tekintsd ezt a fő színpadunknak, ahol minden tevékenység megtörténik.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

Ez a kód betölti a fő dokumentumot a megadott könyvtárból.

## 3. lépés: Állítsa be a Keresés és csere opciókat

Ahhoz, hogy megtaláljuk azt a helyet, ahová a dokumentumunkat be szeretnénk illeszteni, a keresés és csere funkciót használjuk. Ez olyan, mintha egy térképet használnánk az új kiegészítésünk pontos helyének megtalálásához.

```csharp
FindReplaceOptions options = new FindReplaceOptions
{
    Direction = FindReplaceDirection.Backward,
    ReplacingCallback = new InsertDocumentAtReplaceHandler()
};
```

Itt beállítjuk a visszafelé irányt, és megadunk egy egyéni visszahíváskezelőt, amelyet a továbbiakban határozunk meg.

## 4. lépés: Hajtsa végre a Csere műveletet

Most azt mondjuk a fő dokumentumunknak, hogy keressen egy adott helyőrző szöveget, és cserélje le semmire, miközben az egyéni visszahívásunkat használja egy másik dokumentum beszúrásához.

```csharp
mainDoc.Range.Replace(new Regex("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

Ez a kód végrehajtja a keresés és csere műveletet, majd elmenti a frissített dokumentumot.

## 5. lépés: Hozzon létre egy egyéni csere-visszahíváskezelőt

Egyedi visszahíváskezelőnk az, ahol a varázslat megtörténik. Ez a kezelő határozza meg, hogyan történjen a dokumentumbeillesztés a keresés és csere művelet során.

```csharp
private class InsertDocumentAtReplaceHandler : IReplacingCallback
{
    ReplaceAction IReplacingCallback.Replacing(ReplacingArgs args)
    {
        Document subDoc = new Document(dataDir + "Document insertion 2.docx");

        // Szúrjon be egy dokumentumot a megfelelő szöveget tartalmazó bekezdés után.
        Paragraph para = (Paragraph)args.MatchNode.ParentNode;
        InsertDocument(para, subDoc);

        // Távolítsa el a megfelelő szöveget tartalmazó bekezdést.
        para.Remove();
        return ReplaceAction.Skip;
    }
}
```

Itt betöltjük a beszúrandó dokumentumot, majd hívunk egy helper metódust a beszúráshoz.

## 6. lépés: Határozza meg a dokumentum beszúrási módját

A rejtvényünk utolsó darabja az a módszer, amely ténylegesen beszúrja a dokumentumot a megadott helyre.

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    // Ellenőrizze, hogy a beillesztési cél egy bekezdés vagy egy táblázat
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;

        // Hozzon létre egy NodeImportert a csomópontok importálásához a forrásdokumentumból
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        // A forrásdokumentum szakaszaiban görgessen végig az összes blokkszintű csomóponton
        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        {
            foreach (Node srcNode in srcSection.Body)
            {
                // Egy szakasz utolsó üres bekezdésének kihagyása
                if (srcNode.NodeType == NodeType.Paragraph)
                {
                    Paragraph para = (Paragraph)srcNode;
                    if (para.IsEndOfSection && !para.HasChildNodes)
                        continue;
                }

                // Importálja és illessze be a csomópontot a célhelyre
                Node newNode = importer.ImportNode(srcNode, true);
                destinationParent.InsertAfter(newNode, insertionDestination);
                insertionDestination = newNode;
            }
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}

```

Ez a módszer gondoskodik a csomópontok importálásáról a beillesztendő dokumentumból, és a fő dokumentum megfelelő helyre történő elhelyezéséről.

## Következtetés

És megvan! Átfogó útmutató egyik dokumentumnak a másikba való beszúrásához az Aspose.Words for .NET használatával. Ezen lépések követésével könnyedén automatizálhatja a dokumentum-összeállítási és -kezelési feladatokat. Akár dokumentumkezelő rendszert épít, akár csak egyszerűsítenie kell dokumentumfeldolgozási munkafolyamatát, az Aspose.Words az Ön megbízható segítője.

## GYIK

### Mi az Aspose.Words for .NET?
Az Aspose.Words for .NET egy hatékony könyvtár a Word dokumentumok programozott kezeléséhez. Lehetővé teszi a Word dokumentumok könnyű létrehozását, módosítását, konvertálását és feldolgozását.

### Beilleszthetek több dokumentumot egyszerre?
Igen, módosíthatja a visszahíváskezelőt úgy, hogy több beszúrást is kezeljen, ha egy dokumentumgyűjteményt ismételget.

### Van ingyenes próbaverzió?
 Teljesen! Ingyenes próbaverziót letölthet a webhelyről[itt](https://releases.aspose.com/).

### Hogyan kaphatok támogatást az Aspose.Words számára?
 Támogatást kaphat, ha ellátogat a[Aspose.Words fórum](https://forum.aspose.com/c/words/8).

### Megtarthatom a beillesztett dokumentum formázását?
 Igen, a`NodeImporter` osztály lehetővé teszi annak megadását, hogy a formázás hogyan legyen kezelve csomópontok importálásakor egyik dokumentumból a másikba.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
