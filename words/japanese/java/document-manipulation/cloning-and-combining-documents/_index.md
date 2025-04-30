---
"description": "Aspose.Words for Javaでドキュメントを複製および結合する方法を学びましょう。ソースコード例付きのステップバイステップガイドです。"
"linktitle": "ドキュメントの複製と結合"
"second_title": "Aspose.Words Java ドキュメント処理 API"
"title": "Aspose.Words for Java でのドキュメントの複製と結合"
"url": "/ja/java/document-manipulation/cloning-and-combining-documents/"
"weight": 27
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java でのドキュメントの複製と結合


## Aspose.Words for Java でのドキュメントの複製と結合の概要

このチュートリアルでは、Aspose.Words for Java を使用してドキュメントを複製および結合する方法を説明します。ドキュメントの複製、置換ポイントへのドキュメントの挿入、ブックマーク、差し込み印刷など、さまざまなシナリオを取り上げます。

## ステップ1：ドキュメントの複製

Aspose.Words for Javaでドキュメントを複製するには、 `deepClone()` 方法。簡単な例を以下に示します。

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "CloneAndCombineDocuments.CloningDocument.docx");
```

このコードは、元のドキュメントのディープクローンを作成し、新しいファイルとして保存します。

## ステップ2: 置換ポイントにドキュメントを挿入する

別の文書内の特定の置換ポイントに文書を挿入することができます。手順は以下のとおりです。

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
FindReplaceOptions options = new FindReplaceOptions();
options.setDirection(FindReplaceDirection.BACKWARD);
options.setReplacingCallback(new InsertDocumentAtReplaceHandler());
mainDoc.getRange().replace(Pattern.compile("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

この例では、 `FindReplaceOptions` 置換のためのコールバックハンドラを指定するオブジェクト。 `InsertDocumentAtReplaceHandler` クラスは挿入ロジックを処理します。

## ステップ3: ブックマークにドキュメントを挿入する

別のドキュメント内の特定のブックマークにドキュメントを挿入するには、次のコードを使用できます。

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
Document subDoc = new Document("Your Directory Path" + "Document insertion 2.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("insertionPlace");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtBookmark.docx");
```

ここでは、名前でブックマークを検索し、 `insertDocument` コンテンツを挿入する方法 `subDoc` ブックマークの場所にあるドキュメント。

## ステップ4: 差し込み印刷中に文書を挿入する

Aspose.Words for Javaでは、差し込み印刷中にドキュメントを挿入できます。手順は以下のとおりです。

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "Document_1" }, new Object[] { "Your Directory Path" + "Document insertion 2.docx" });
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

この例では、フィールドマージコールバックを次のように設定します。 `InsertDocumentAtMailMergeHandler` 「Document_1」フィールドで指定されたドキュメントの挿入を処理するクラス。

## 結論

Aspose.Words for Javaでは、様々な手法を用いてドキュメントの複製と結合が可能です。ドキュメントの複製、置換ポイントやブックマークへのコンテンツの挿入、差し込み印刷など、Aspose.Wordsはドキュメントをシームレスに操作するための強力な機能を提供します。

## よくある質問

### Aspose.Words for Java でドキュメントを複製するにはどうすればよいですか?

Aspose.Words for Javaでは、 `deepClone()` 方法。以下に例を示します。

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "ClonedDocument.docx");
```

### ブックマークにドキュメントを挿入するにはどうすればいいですか?

Aspose.Words for Javaでブックマークにドキュメントを挿入するには、ブックマーク名で検索し、 `insertDocument` コンテンツを挿入するメソッド。以下に例を示します。

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
Document subDoc = new Document("Your Directory Path" + "SubDocument.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("MyBookmark");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CombinedDocument.docx");
```

### Aspose.Words for Java で差し込み印刷中にドキュメントを挿入するにはどうすればよいですか?

Aspose.Words for Javaでは、フィールドマージコールバックを設定し、挿入するドキュメントを指定することで、差し込み印刷時にドキュメントを挿入できます。以下に例を示します。

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "DocumentField" }, new Object[] { "Your Directory Path" + "DocumentToInsert.docx" });
mainDoc.save("Your Directory Path" + "MergedDocument.docx");
```

この例では、 `InsertDocumentAtMailMergeHandler` クラスは、差し込み印刷中の「DocumentField」の挿入ロジックを処理します。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}