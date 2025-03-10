---
title: Dokumentumok klónozása és kombinálása az Aspose.Words for Java programban
linktitle: Dokumentumok klónozása és kombinálása
second_title: Aspose.Words Java Document Processing API
description: Ismerje meg, hogyan klónozhat és kombinálhat dokumentumokat az Aspose.Words for Java programban. Lépésről lépésre, forráskód-példákkal.
weight: 27
url: /hu/java/document-manipulation/cloning-and-combining-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentumok klónozása és kombinálása az Aspose.Words for Java programban


## Bevezetés az Aspose.Words for Java dokumentumok klónozásába és kombinálásába

Ebben az oktatóanyagban megvizsgáljuk, hogyan klónozhatunk és kombinálhatunk dokumentumokat az Aspose.Words for Java használatával. Különféle forgatókönyvekkel foglalkozunk, beleértve a dokumentum klónozását, dokumentumok beszúrását a cserepontokhoz, a könyvjelzőket és a körlevél-műveletek során.

## 1. lépés: Dokumentum klónozása

 Egy dokumentum klónozásához az Aspose.Words for Java programban használhatja a`deepClone()` módszer. Íme egy egyszerű példa:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "CloneAndCombineDocuments.CloningDocument.docx");
```

Ez a kód létrehozza az eredeti dokumentum mély klónját, és új fájlként menti el.

## 2. lépés: Dokumentumok beszúrása a cserepontokon

Beszúrhat dokumentumokat egy másik dokumentum adott cserepontjaira. A következőképpen teheti meg:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
FindReplaceOptions options = new FindReplaceOptions();
options.setDirection(FindReplaceDirection.BACKWARD);
options.setReplacingCallback(new InsertDocumentAtReplaceHandler());
mainDoc.getRange().replace(Pattern.compile("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

 Ebben a példában az a`FindReplaceOptions` objektum egy visszahíváskezelő megadásához a csere számára. A`InsertDocumentAtReplaceHandler` osztály kezeli a beillesztési logikát.

## 3. lépés: Dokumentumok beszúrása a könyvjelzők közé

Ha egy dokumentumot egy adott könyvjelzőhöz szeretne beszúrni egy másik dokumentumba, használja a következő kódot:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
Document subDoc = new Document("Your Directory Path" + "Document insertion 2.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("insertionPlace");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtBookmark.docx");
```

 Itt megtaláljuk a könyvjelzőt név szerint, és használjuk a`insertDocument` a tartalom beillesztésének módja`subDoc` dokumentumot a könyvjelző helyén.

## 4. lépés: Dokumentumok beszúrása a körlevél-egyesítés során

Az Aspose.Words for Java programban a körlevél-művelet során dokumentumokat szúrhat be. Íme, hogyan:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "Document_1" }, new Object[] { "Your Directory Path" + "Document insertion 2.docx" });
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

 Ebben a példában a visszahívást egyesítő mezőt állítunk be a`InsertDocumentAtMailMergeHandler` osztály a "Dokumentum_1" mezőben megadott dokumentum beszúrásának kezelésére.

## Következtetés

dokumentumok klónozása és kombinálása az Aspose.Words for Java programban többféle technikával is megvalósítható. Függetlenül attól, hogy klónoznia kell egy dokumentumot, tartalmat kell beszúrnia a cserepontokba, a könyvjelzőkbe vagy a körlevél-egyesítés során, az Aspose.Words hatékony funkciókat kínál a dokumentumok zökkenőmentes kezeléséhez.

## GYIK

### Hogyan klónozhatok egy dokumentumot az Aspose.Words for Java programban?

 Az Aspose.Words for Java programban a dokumentumot klónozhatja a`deepClone()` módszer. Íme egy példa:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "ClonedDocument.docx");
```

### Hogyan illeszthetek be egy dokumentumot egy könyvjelzőhöz?

 Ha dokumentumot szeretne beszúrni egy könyvjelzőhöz az Aspose.Words for Java programban, keresse meg a könyvjelzőt név szerint, majd használja a`insertDocument` a tartalom beillesztésének módja. Íme egy példa:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
Document subDoc = new Document("Your Directory Path" + "SubDocument.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("MyBookmark");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CombinedDocument.docx");
```

### Hogyan illeszthetek be dokumentumokat az Aspose.Words for Java programban?

Az Aspose.Words for Java programban a körlevél-összevonás során dokumentumokat illeszthet be úgy, hogy beállít egy mezőegyesítési visszahívást, és megadja a beillesztendő dokumentumot. Íme egy példa:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "DocumentField" }, new Object[] { "Your Directory Path" + "DocumentToInsert.docx" });
mainDoc.save("Your Directory Path" + "MergedDocument.docx");
```

 Ebben a példában a`InsertDocumentAtMailMergeHandler`osztály kezeli a "DocumentField" beillesztési logikáját a körlevél-összevonás során.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
