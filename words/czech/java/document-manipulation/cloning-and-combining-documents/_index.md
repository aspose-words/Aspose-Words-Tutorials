---
"description": "Naučte se, jak klonovat a kombinovat dokumenty v Aspose.Words pro Javu. Podrobný návod s příklady zdrojového kódu."
"linktitle": "Klonování a kombinování dokumentů"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Klonování a kombinování dokumentů v Aspose.Words pro Javu"
"url": "/cs/java/document-manipulation/cloning-and-combining-documents/"
"weight": 27
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Klonování a kombinování dokumentů v Aspose.Words pro Javu


## Úvod do klonování a kombinování dokumentů v Aspose.Words pro Javu

tomto tutoriálu se podíváme na to, jak klonovat a kombinovat dokumenty pomocí Aspose.Words pro Javu. Probereme různé scénáře, včetně klonování dokumentu, vkládání dokumentů do bodů nahrazení, záložek a během operací hromadné korespondence.

## Krok 1: Klonování dokumentu

Chcete-li klonovat dokument v Aspose.Words pro Javu, můžete použít `deepClone()` metoda. Zde je jednoduchý příklad:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "CloneAndCombineDocuments.CloningDocument.docx");
```

Tento kód vytvoří hloubkovou kopii původního dokumentu a uloží ji jako nový soubor.

## Krok 2: Vkládání dokumentů do bodů nahrazení

Dokumenty můžete vkládat na konkrétní místa nahrazení v jiném dokumentu. Postupujte takto:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
FindReplaceOptions options = new FindReplaceOptions();
options.setDirection(FindReplaceDirection.BACKWARD);
options.setReplacingCallback(new InsertDocumentAtReplaceHandler());
mainDoc.getRange().replace(Pattern.compile("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

V tomto příkladu používáme `FindReplaceOptions` objekt pro určení obslužné rutiny zpětného volání pro nahrazení. `InsertDocumentAtReplaceHandler` třída zpracovává logiku vkládání.

## Krok 3: Vkládání dokumentů do záložek

Chcete-li vložit dokument na konkrétní záložku v jiném dokumentu, můžete použít následující kód:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
Document subDoc = new Document("Your Directory Path" + "Document insertion 2.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("insertionPlace");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtBookmark.docx");
```

Zde najdeme záložku podle názvu a použijeme `insertDocument` metoda pro vložení obsahu `subDoc` dokument v umístění záložky.

## Krok 4: Vkládání dokumentů během hromadné korespondence

Během hromadné korespondence v Aspose.Words pro Javu můžete vkládat dokumenty. Postupujte takto:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "Document_1" }, new Object[] { "Your Directory Path" + "Document insertion 2.docx" });
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

V tomto příkladu nastavujeme zpětné volání pro slučování polí pomocí `InsertDocumentAtMailMergeHandler` třída pro zpracování vložení dokumentu určeného polem „Document_1“.

## Závěr

Klonování a kombinování dokumentů v Aspose.Words pro Javu lze provádět pomocí různých technik. Ať už potřebujete klonovat dokument, vkládat obsah do bodů nahrazení, záložek nebo během hromadné korespondence, Aspose.Words poskytuje výkonné funkce pro bezproblémovou manipulaci s dokumenty.

## Často kladené otázky

### Jak naklonuji dokument v Aspose.Words pro Javu?

Dokument v Aspose.Words pro Javu můžete naklonovat pomocí `deepClone()` metoda. Zde je příklad:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "ClonedDocument.docx");
```

### Jak mohu vložit dokument na místo záložky?

Chcete-li vložit dokument na místo záložky v Aspose.Words pro Javu, můžete záložku vyhledat podle názvu a poté použít `insertDocument` metoda pro vložení obsahu. Zde je příklad:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
Document subDoc = new Document("Your Directory Path" + "SubDocument.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("MyBookmark");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CombinedDocument.docx");
```

### Jak vložím dokumenty během hromadné korespondence v Aspose.Words pro Javu?

V Aspose.Words pro Javu můžete během hromadné korespondence vkládat dokumenty nastavením zpětného volání pro slučování polí a zadáním dokumentu, který má být vložen. Zde je příklad:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "DocumentField" }, new Object[] { "Your Directory Path" + "DocumentToInsert.docx" });
mainDoc.save("Your Directory Path" + "MergedDocument.docx");
```

V tomto příkladu `InsertDocumentAtMailMergeHandler` Třída zpracovává logiku vkládání pro „DocumentField“ během hromadné korespondence.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}