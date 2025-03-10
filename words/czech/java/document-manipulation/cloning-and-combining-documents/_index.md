---
title: Klonování a kombinování dokumentů v Aspose.Words pro Javu
linktitle: Klonování a kombinování dokumentů
second_title: Aspose.Words Java Document Processing API
description: Naučte se klonovat a kombinovat dokumenty v Aspose.Words for Java. Průvodce krok za krokem s příklady zdrojového kódu.
weight: 27
url: /cs/java/document-manipulation/cloning-and-combining-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Klonování a kombinování dokumentů v Aspose.Words pro Javu


## Úvod do klonování a kombinování dokumentů v Aspose.Words pro Javu

V tomto tutoriálu prozkoumáme, jak klonovat a kombinovat dokumenty pomocí Aspose.Words for Java. Probereme různé scénáře, včetně klonování dokumentu, vkládání dokumentů do bodů nahrazení, záložek a během operací hromadné korespondence.

## Krok 1: Klonování dokumentu

 Chcete-li klonovat dokument v Aspose.Words pro Java, můžete použít`deepClone()` metoda. Zde je jednoduchý příklad:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "CloneAndCombineDocuments.CloningDocument.docx");
```

Tento kód vytvoří hluboký klon původního dokumentu a uloží jej jako nový soubor.

## Krok 2: Vkládání dokumentů v bodech nahrazení

Dokumenty můžete vložit do určitých bodů nahrazení v jiném dokumentu. Můžete to udělat takto:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
FindReplaceOptions options = new FindReplaceOptions();
options.setDirection(FindReplaceDirection.BACKWARD);
options.setReplacingCallback(new InsertDocumentAtReplaceHandler());
mainDoc.getRange().replace(Pattern.compile("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

 V tomto příkladu používáme a`FindReplaceOptions` objekt k určení obsluhy zpětného volání pro nahrazení. The`InsertDocumentAtReplaceHandler` třída zpracovává logiku vkládání.

## Krok 3: Vkládání dokumentů do záložek

Chcete-li vložit dokument na konkrétní záložku v jiném dokumentu, můžete použít následující kód:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
Document subDoc = new Document("Your Directory Path" + "Document insertion 2.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("insertionPlace");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtBookmark.docx");
```

 Zde najdeme záložku podle názvu a použijeme`insertDocument` způsob vložení obsahu`subDoc` dokument v umístění záložky.

## Krok 4: Vkládání dokumentů během hromadné korespondence

Dokumenty můžete vkládat během operace hromadné korespondence v Aspose.Words for Java. Zde je postup:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "Document_1" }, new Object[] { "Your Directory Path" + "Document insertion 2.docx" });
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

 V tomto příkladu jsme nastavili zpětné volání slučování polí pomocí`InsertDocumentAtMailMergeHandler` třídy pro zpracování vložení dokumentu určeného polem "Dokument_1".

## Závěr

Klonování a kombinování dokumentů v Aspose.Words pro Java lze provést pomocí různých technik. Ať už potřebujete klonovat dokument, vkládat obsah do bodů nahrazení, záložek nebo během hromadné korespondence, Aspose.Words poskytuje výkonné funkce pro bezproblémovou manipulaci s dokumenty.

## FAQ

### Jak naklonuji dokument v Aspose.Words for Java?

 Můžete klonovat dokument v Aspose.Words pro Java pomocí`deepClone()` metoda. Zde je příklad:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "ClonedDocument.docx");
```

### Jak mohu vložit dokument do záložky?

 Chcete-li vložit dokument na záložku v Aspose.Words pro Java, můžete záložku najít podle názvu a poté použít`insertDocument` způsob vložení obsahu. Zde je příklad:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
Document subDoc = new Document("Your Directory Path" + "SubDocument.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("MyBookmark");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CombinedDocument.docx");
```

### Jak vložím dokumenty během hromadné korespondence v Aspose.Words for Java?

Dokumenty můžete vkládat během hromadné korespondence v Aspose.Words for Java nastavením zpětného volání sloučení polí a určením dokumentu, který má být vložen. Zde je příklad:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "DocumentField" }, new Object[] { "Your Directory Path" + "DocumentToInsert.docx" });
mainDoc.save("Your Directory Path" + "MergedDocument.docx");
```

 V tomto příkladu je`InsertDocumentAtMailMergeHandler`class zpracovává logiku vkládání pro "DocumentField" během hromadné korespondence.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
