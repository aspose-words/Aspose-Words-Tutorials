---
title: Könyvjelzők elrejtése a Word-dokumentumban
linktitle: Könyvjelzők elrejtése a Word-dokumentumban
second_title: Aspose.Words Document Processing API
description: Részletes útmutatónkból megtudhatja, hogyan lehet dinamikusan megjeleníteni vagy elrejteni könyvjelzőket egy Word-dokumentumban az Aspose.Words for .NET használatával. Tökéletes fejlesztőknek.
weight: 10
url: /hu/net/programming-with-bookmarks/show-hide-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Könyvjelzők elrejtése a Word-dokumentumban

## Bevezetés

Volt már olyan, hogy el kell rejtenie vagy dinamikusan meg kell jelenítenie Word-dokumentuma egyes részeit? Nos, szerencséd van! Az Aspose.Words for .NET segítségével egyszerűen kezelheti a könyvjelzőkkel ellátott tartalom láthatóságát a dokumentumokban. Ez az oktatóanyag végigvezeti a könyvjelzők Word-dokumentumban való megjelenítésének és elrejtésének folyamatán az Aspose.Words for .NET használatával. A kódot lépésről lépésre bontjuk le, így akár tapasztalt fejlesztő, akár kezdő, ezt az útmutatót könnyen követni fogja.

## Előfeltételek

Mielőtt belemerülnénk a kódba, győződjön meg arról, hogy mindennel rendelkezik, amire szüksége van:

1.  Aspose.Words for .NET: Győződjön meg arról, hogy telepítve van az Aspose.Words for .NET könyvtár. Ha nem, akkor letöltheti[itt](https://releases.aspose.com/words/net/).
2. Fejlesztői környezet: Egy IDE, mint a Visual Studio.
3. C# alapismeretek: A C# programozás ismerete előnyt jelent.
4. Word-dokumentum: minta Word-dokumentum könyvjelzőkkel.

## Névterek importálása

Mielőtt elkezdené a kódot, importálnia kell a szükséges névtereket. Adja hozzá a következőket a C# fájl elejéhez:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

## 1. lépés: Töltse be a dokumentumot

Először is be kell töltenie a könyvjelzőket tartalmazó Word-dokumentumot. A következőképpen teheti meg:

```csharp
// A dokumentumok könyvtárának elérési útja.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

### Magyarázat

- dataDir: Ez az a könyvtár elérési útja, ahol a Word-dokumentum található.
-  Dokumentumdokumentum: Ez inicializálja a`Document` osztályt a megadott fájllal.

## 2. lépés: A könyvjelzővel ellátott tartalom megjelenítése vagy elrejtése

Ezután meghatározunk egy módszert a könyvjelzővel ellátott tartalom megjelenítésére vagy elrejtésére. Íme a teljes módszer:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool showHide)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.MoveToDocumentEnd();

    // {IF "{MERGEFIELD könyvjelző}" = "igaz" "" ""}
    Field field = builder.InsertField("IF \"", null);
    builder.MoveTo(field.Start.NextSibling);
    builder.InsertField("MERGEFIELD " + bookmarkName + "", null);
    builder.Write("\" = \"true\" ");
    builder.Write("\"");
    builder.Write("\"");
    builder.Write(" \"\"");

    Node currentNode = field.Start;
    bool flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.Run)
            if (currentNode.ToString(SaveFormat.Text).Trim() == "\"")
                flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkStart.ParentNode.InsertBefore(currentNode, bm.BookmarkStart);
        currentNode = nextNode;
    }

    Node endNode = bm.BookmarkEnd;
    flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.FieldEnd)
            flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkEnd.ParentNode.InsertAfter(currentNode, endNode);
        endNode = currentNode;
        currentNode = nextNode;
    }

    doc.MailMerge.Execute(new[] { bookmarkName }, new object[] { showHide });
}
```

### Magyarázat

- Könyvjelző bm: Lekéri a könyvjelzőt a dokumentumból.
- DocumentBuilder builder: Segít a dokumentumban való navigálásban és módosításában.
- Mezőmező: IF mezőt szúr be a könyvjelző állapotának ellenőrzéséhez.
- Node currentNode: A csomópontokon áthaladva megkeresi a mező kezdetét és végét.

## 3. lépés: Hajtsa végre a Megjelenítés/elrejtés funkciót

 Most fel kell hívnia a`ShowHideBookmarkedContent` módszer, átadja a dokumentumot, a könyvjelző nevét és a láthatósági jelzőt:

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", false);
```

### Magyarázat

- doc: Az Ön dokumentumobjektuma.
- "MyBookmark1": A megjeleníteni/elrejteni kívánt könyvjelző neve.
- false: A láthatósági zászló (igaz a megjelenítéshez, hamis az elrejtéshez).

## 4. lépés: Mentse el a dokumentumot

Végül mentse el a módosított dokumentumot:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Magyarázat

- dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx": Annak az új dokumentumnak az elérési útja és neve, amelybe a változások mentésre kerülnek.

## Következtetés

És megvan! Sikeresen megtanulta, hogyan jeleníthet meg és rejthet el könyvjelzőket egy Word-dokumentumban az Aspose.Words for .NET segítségével. Ez a technika hihetetlenül hasznos lehet feltételes tartalmú dokumentumok dinamikus generálásához.

## GYIK

### Mi az Aspose.Words for .NET?
Az Aspose.Words for .NET egy hatékony dokumentumfeldolgozó könyvtár, amely lehetővé teszi a fejlesztők számára Word-dokumentumok programozott létrehozását, módosítását és konvertálását.

### Hogyan szerezhetem be az Aspose.Words for .NET fájlt?
 Az Aspose.Words for .NET letölthető innen[itt](https://releases.aspose.com/words/net/). Ingyenes próbaverzió is elérhető.

### Használhatom ezt a módszert más típusú könyvjelzőkhöz?
Igen, ez a módszer adaptálható a Word-dokumentumban lévő könyvjelzők láthatóságának kezelésére.

### Mi a teendő, ha a dokumentumom nem tartalmazza a megadott könyvjelzőt?
Ha a könyvjelző nem létezik, a metódus hibát jelez. Győződjön meg arról, hogy a könyvjelző létezik, mielőtt megpróbálná megjeleníteni/elrejteni.

### Hogyan kaphatok támogatást, ha problémákba ütközöm?
 Támogatást kaphat az Aspose közösségtől[itt](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
