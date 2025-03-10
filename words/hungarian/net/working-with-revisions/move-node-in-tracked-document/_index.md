---
title: Csomópont mozgatása nyomon követett dokumentumban
linktitle: Csomópont mozgatása nyomon követett dokumentumban
second_title: Aspose.Words Document Processing API
description: Részletes, lépésenkénti útmutatónkból megtudhatja, hogyan helyezhet át csomópontokat egy nyomon követett Word-dokumentumban az Aspose.Words for .NET használatával. Tökéletes fejlesztőknek.
weight: 10
url: /hu/net/working-with-revisions/move-node-in-tracked-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Csomópont mozgatása nyomon követett dokumentumban

## Bevezetés

Szia, Aspose. Words rajongók! Ha valaha is át kellett helyeznie egy csomópontot egy Word-dokumentumban a revíziók követése közben, akkor jó helyen jár. Ma az Aspose.Words for .NET használatával valósítható meg. Nemcsak a lépésről lépésre tanulja meg a folyamatot, hanem néhány tippet és trükköt is megtudhat, hogy a dokumentumkezelést gördülékenyebbé és hatékonysá tegye.

## Előfeltételek

Mielőtt bepiszkítanánk a kezünket egy kóddal, győződjünk meg arról, hogy mindent megvan, amire szüksége van:

-  Aspose.Words for .NET: Töltse le[itt](https://releases.aspose.com/words/net/).
- .NET-környezet: Győződjön meg arról, hogy kompatibilis .NET-fejlesztői környezetet állított be.
- Alapvető C# ismeretek: Ez az oktatóanyag feltételezi, hogy rendelkezik a C# alapvető ismereteivel.

Megvan minden? Nagy! Térjünk át az importálandó névterekre.

## Névterek importálása

Először is importálnunk kell a szükséges névtereket. Ezek elengedhetetlenek az Aspose.Words-szel való munkához és a dokumentumcsomópontok kezeléséhez.

```csharp
using Aspose.Words;
using System;
```

Rendben, bontsuk fel a folyamatot kezelhető lépésekre. Minden lépést részletesen elmagyarázunk annak érdekében, hogy megértse, mi történik minden ponton.

## 1. lépés: Inicializálja a dokumentumot

 Kezdésként inicializálnunk kell egy új dokumentumot, és az a`DocumentBuilder` néhány bekezdés hozzáadásához.

```csharp
// A dokumentumok könyvtárának elérési útja.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Néhány bekezdés hozzáadása
builder.Writeln("Paragraph 1");
builder.Writeln("Paragraph 2");
builder.Writeln("Paragraph 3");
builder.Writeln("Paragraph 4");
builder.Writeln("Paragraph 5");
builder.Writeln("Paragraph 6");

// Ellenőrizze a kezdeti bekezdések számát
Body body = doc.FirstSection.Body;
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## 2. lépés: Kezdje el a módosítások követését

Ezután el kell kezdenünk a revíziók nyomon követését. Ez döntő fontosságú, mivel lehetővé teszi számunkra, hogy láthassuk a dokumentumon végrehajtott változtatásokat.

```csharp
// Kezdje el a revíziók követését
doc.StartTrackRevisions("Author", new DateTime(2020, 12, 23, 14, 0, 0));
```

## 3. lépés: Csomópontok mozgatása

Most jön a feladatunk alapvető része: egy csomópont áthelyezése egyik helyről a másikra. A harmadik bekezdést áthelyezzük, és az első bekezdés elé helyezzük.

```csharp
// Határozza meg az áthelyezni kívánt csomópontot és annak végtartományát
Node node = body.Paragraphs[3];
Node endNode = body.Paragraphs[5].NextSibling;
Node referenceNode = body.Paragraphs[0];

// Mozgassa a csomópontokat a meghatározott tartományon belül
while (node != endNode)
{
    Node nextNode = node.NextSibling;
    body.InsertBefore(node, referenceNode);
    node = nextNode;
}
```

## 4. lépés: Állítsa le a módosítások követését

Miután áthelyeztük a csomópontokat, le kell állítani a revíziók követését.

```csharp
// Állítsa le a változatok követését
doc.StopTrackRevisions();
```

## 5. lépés: Mentse el a dokumentumot

Végül mentsük el a módosított dokumentumunkat a megadott könyvtárba.

```csharp
// Mentse el a módosított dokumentumot
doc.Save(dataDir + "WorkingWithRevisions.MoveNodeInTrackedDocument.docx");

// Adja meg az utolsó bekezdések számát
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## Következtetés

És megvan! Sikeresen áthelyezett egy csomópontot egy nyomon követett dokumentumban az Aspose.Words for .NET használatával. Ez a hatékony könyvtár megkönnyíti a Word-dokumentumok programozott kezelését. Akár létrehoz, akár szerkeszt, akár nyomon követi a változtatásokat, az Aspose.Words mindenre kiterjed. Szóval, menj és próbáld ki. Boldog kódolást!

## GYIK

### Mi az Aspose.Words for .NET?

Az Aspose.Words for .NET egy osztálykönyvtár Word-dokumentumokkal való programozott munkavégzéshez. Lehetővé teszi a fejlesztők számára Word dokumentumok létrehozását, szerkesztését, konvertálását és nyomtatását .NET alkalmazásokon belül.

### Hogyan követhetem nyomon a revíziókat egy Word-dokumentumban az Aspose.Words használatával?

 A revíziók nyomon követéséhez használja a`StartTrackRevisions` módszer a`Document` objektum. Ez lehetővé teszi a revíziókövetést, és megjeleníti a dokumentumon végrehajtott módosításokat.

### Mozgathatok több csomópontot az Aspose.Wordsben?

Igen, több csomópontot is áthelyezhet, ha átiterál rajtuk, és olyan módszereket használ, mint pl`InsertBefore` vagy`InsertAfter` hogy a kívánt helyre helyezze őket.

### Hogyan állíthatom le a revíziók követését az Aspose.Wordsben?

 Használja a`StopTrackRevisions` módszer a`Document` ellenzi a revíziók követésének leállítását.

### Hol találok további dokumentációt az Aspose.Words for .NET-ről?

 Részletes dokumentációt találhat[itt](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
