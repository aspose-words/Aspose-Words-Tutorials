---
title: Aspose.Words for Java でのドキュメントの複製と結合
linktitle: ドキュメントの複製と結合
second_title: Aspose.Words Java ドキュメント処理 API
description: Aspose.Words for Java でドキュメントを複製および結合する方法を学びます。ソース コードの例を含むステップ バイ ステップ ガイド。
weight: 27
url: /ja/java/document-manipulation/cloning-and-combining-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java でのドキュメントの複製と結合


## Aspose.Words for Java でのドキュメントの複製と結合の概要

このチュートリアルでは、Aspose.Words for Java を使用してドキュメントを複製および結合する方法について説明します。ドキュメントの複製、置換ポイント、ブックマーク、差し込み印刷操作でのドキュメントの挿入など、さまざまなシナリオについて説明します。

## ステップ1: ドキュメントの複製

Aspose.Words for Javaでドキュメントを複製するには、`deepClone()`方法。簡単な例を次に示します。

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "CloneAndCombineDocuments.CloningDocument.docx");
```

このコードは、元のドキュメントのディープクローンを作成し、新しいファイルとして保存します。

## ステップ2: 置換ポイントにドキュメントを挿入する

別のドキュメントの特定の置換ポイントにドキュメントを挿入できます。手順は次のとおりです。

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
FindReplaceOptions options = new FindReplaceOptions();
options.setDirection(FindReplaceDirection.BACKWARD);
options.setReplacingCallback(new InsertDocumentAtReplaceHandler());
mainDoc.getRange().replace(Pattern.compile("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

この例では、`FindReplaceOptions`置換用のコールバックハンドラを指定するオブジェクト。`InsertDocumentAtReplaceHandler`クラスは挿入ロジックを処理します。

## ステップ3: ブックマークにドキュメントを挿入する

別のドキュメント内の特定のブックマークにドキュメントを挿入するには、次のコードを使用できます。

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
Document subDoc = new Document("Your Directory Path" + "Document insertion 2.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("insertionPlace");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtBookmark.docx");
```

ここでは、名前でブックマークを検索し、`insertDocument`コンテンツを挿入する方法`subDoc`ブックマークの場所にあるドキュメント。

## ステップ4: 差し込み印刷中に文書を挿入する

Aspose.Words for Java では、差し込み印刷操作中にドキュメントを挿入できます。手順は次のとおりです。

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "Document_1" }, new Object[] { "Your Directory Path" + "Document insertion 2.docx" });
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

この例では、フィールドマージコールバックを次のように設定します。`InsertDocumentAtMailMergeHandler` 「Document_1」フィールドで指定されたドキュメントの挿入を処理するクラス。

## 結論

Aspose.Words for Java では、さまざまな手法を使用してドキュメントの複製と結合を行うことができます。ドキュメントの複製、置換ポイントやブックマークへのコンテンツの挿入、または差し込み印刷が必要な場合でも、Aspose.Words はドキュメントをシームレスに操作するための強力な機能を提供します。

## よくある質問

### Aspose.Words for Java でドキュメントを複製するにはどうすればよいですか?

 Aspose.Words for Javaでは、`deepClone()`方法。次に例を示します。

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "ClonedDocument.docx");
```

### ブックマークにドキュメントを挿入するにはどうすればいいですか?

 Aspose.Words for Javaのブックマークにドキュメントを挿入するには、ブックマークの名前を検索し、`insertDocument`コンテンツを挿入する方法。次に例を示します。

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
Document subDoc = new Document("Your Directory Path" + "SubDocument.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("MyBookmark");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CombinedDocument.docx");
```

### Aspose.Words for Java で差し込み印刷中にドキュメントを挿入するにはどうすればよいですか?

Aspose.Words for Java では、フィールド結合コールバックを設定し、挿入するドキュメントを指定することにより、差し込み印刷中にドキュメントを挿入できます。次に例を示します。

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "DocumentField" }, new Object[] { "Your Directory Path" + "DocumentToInsert.docx" });
mainDoc.save("Your Directory Path" + "MergedDocument.docx");
```

この例では、`InsertDocumentAtMailMergeHandler`クラスは、差し込み印刷中に「DocumentField」の挿入ロジックを処理します。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
