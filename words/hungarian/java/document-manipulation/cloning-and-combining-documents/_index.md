---
"description": "Tanuld meg, hogyan klónozhatsz és kombinálhatsz dokumentumokat az Aspose.Words for Java programban. Lépésről lépésre útmutató forráskód példákkal."
"linktitle": "Dokumentumok klónozása és egyesítése"
"second_title": "Aspose.Words Java dokumentumfeldolgozó API"
"title": "Dokumentumok klónozása és kombinálása Aspose.Words programban Java-ban"
"url": "/hu/java/document-manipulation/cloning-and-combining-documents/"
"weight": 27
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentumok klónozása és kombinálása Aspose.Words programban Java-ban


## Bevezetés a dokumentumok klónozásába és kombinálásába az Aspose.Words Java-ban

Ebben az oktatóanyagban azt vizsgáljuk meg, hogyan klónozhatunk és kombinálhatunk dokumentumokat az Aspose.Words for Java használatával. Különböző forgatókönyveket fogunk áttekinteni, beleértve a dokumentumok klónozását, dokumentumok beszúrását a cserepontoknál, könyvjelzőket és körlevél műveletek közben.

## 1. lépés: Dokumentum klónozása

Dokumentum klónozásához az Aspose.Words for Java programban használhatja a következőt: `deepClone()` metódus. Íme egy egyszerű példa:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "CloneAndCombineDocuments.CloningDocument.docx");
```

Ez a kód létrehozza az eredeti dokumentum egy mély klónját, és új fájlként menti el.

## 2. lépés: Dokumentumok beszúrása a cserepontokhoz

Dokumentumokat beszúrhat egy másik dokumentum meghatározott cserepontjaihoz. Így teheti meg:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
FindReplaceOptions options = new FindReplaceOptions();
options.setDirection(FindReplaceDirection.BACKWARD);
options.setReplacingCallback(new InsertDocumentAtReplaceHandler());
mainDoc.getRange().replace(Pattern.compile("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

Ebben a példában egy `FindReplaceOptions` objektumot a csere visszahívási kezelőjének megadásához. `InsertDocumentAtReplaceHandler` Az osztály kezeli a beszúrási logikát.

## 3. lépés: Dokumentumok beszúrása könyvjelzőkhöz

Egy dokumentum egy másik dokumentumban lévő adott könyvjelzőhöz való beszúrásához a következő kódot használhatja:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
Document subDoc = new Document("Your Directory Path" + "Document insertion 2.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("insertionPlace");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtBookmark.docx");
```

Itt név szerint keressük meg a könyvjelzőt, és a `insertDocument` tartalom beillesztésének módja `subDoc` dokumentumot a könyvjelző helyén.

## 4. lépés: Dokumentumok beszúrása körlevelezés közben

Az Aspose.Words for Java programban körlevelezési művelet során dokumentumokat szúrhat be. Így teheti meg:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "Document_1" }, new Object[] { "Your Directory Path" + "Document insertion 2.docx" });
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

Ebben a példában egy mezőegyesítési visszahívást állítunk be a következő használatával: `InsertDocumentAtMailMergeHandler` osztály a "Document_1" mező által megadott dokumentum beszúrásának kezelésére.

## Következtetés

Az Aspose.Words for Java programban a dokumentumok klónozása és kombinálása különféle technikákkal végezhető el. Akár dokumentum klónozására, tartalom beszúrására cserepontoknál, könyvjelzők elhelyezésére vagy körlevelezés közben van szükség, az Aspose.Words hatékony funkciókat kínál a dokumentumok zökkenőmentes kezeléséhez.

## GYIK

### Hogyan klónozhatok egy dokumentumot az Aspose.Words for Java programban?

Klónozhatsz egy dokumentumot az Aspose.Words for Java programban a következő használatával: `deepClone()` módszer. Íme egy példa:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "ClonedDocument.docx");
```

### Hogyan tudok egy dokumentumot beszúrni egy könyvjelzőbe?

Dokumentum beszúrásához egy könyvjelzőhöz az Aspose.Words for Java programban, megkeresheti a könyvjelzőt név szerint, majd használhatja a `insertDocument` metódus a tartalom beszúrásához. Íme egy példa:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
Document subDoc = new Document("Your Directory Path" + "SubDocument.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("MyBookmark");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CombinedDocument.docx");
```

### Hogyan szúrhatok be dokumentumokat körlevelezés közben az Aspose.Words for Java programban?

Az Aspose.Words for Java programban körlevelezés közben dokumentumokat szúrhat be egy mezőegyesítési visszahívás beállításával és a beszúrandó dokumentum megadásával. Íme egy példa:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "DocumentField" }, new Object[] { "Your Directory Path" + "DocumentToInsert.docx" });
mainDoc.save("Your Directory Path" + "MergedDocument.docx");
```

Ebben a példában a `InsertDocumentAtMailMergeHandler` Az osztály kezeli a „DocumentField” beszúrási logikáját körlevelezés közben.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}