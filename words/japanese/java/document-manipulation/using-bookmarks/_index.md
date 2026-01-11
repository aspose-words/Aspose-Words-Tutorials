---
date: 2026-01-11
description: Aspose.Words for Java を使用して、ブックマークの表示/非表示やブックマークの作成方法を学び、効率的な文書ナビゲーションと操作を実現しましょう。
linktitle: Using Bookmarks
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words for Javaでブックマークの表示と非表示
url: /ja/java/document-manipulation/using-bookmarks/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java を使用したブックマークの表示/非表示

## Aspose.Words for Java におけるブックマーク使用の概要

ブックマークは Aspose.Words for Java の強力な機能で、**create bookmark java** を作成し、特定のコンテンツへナビゲートし、さらに **show hide bookmarks** を使用して異なる文書バージョンを生成する際にブックマークの表示・非表示を切り替えることができます。このステップバイステップ ガイドでは、ブックマークの作成、取得、更新、コピー、表示切替の方法を順に解説し、文書操作を完全にコントロールできるようにします。

## Quick Answers
- **ブックマークの主な目的は何ですか？** 文書の特定部分にマークを付け、後で取得できるようにすることです。  
- **最終出力でブックマークマーカーを非表示にできますか？** はい—show/hide API を使用して表示状態を切り替えます。  
- **テーブルセル内にブックマークを作成するには？** カーソルをセル内に置いた状態で `DocumentBuilder` を使い、ブックマークの開始と終了を呼び出します。  
- **ブックマークされたテキストを別の文書にコピーできますか？** もちろんです—`NodeImporter` を使用すれば書式を保持できます。  
- **必要な Aspose.Words のバージョンは？** 最新の 2026 ビルドを含む、最近のリリースであれば問題ありません。

## “show hide bookmarks” とは？

**show hide bookmarks** 機能は、保存された文書内でブックマークの区切り記号をプログラムから表示または非表示にできるものです。エンドユーザー向けにクリーンな出力を生成しつつ、内部処理用にブックマークデータを保持したい場合に便利です。

## Java の文書自動化でブックマークを使用する理由

- **効率的なナビゲーション** – ファイル全体を走査せずにセクションへ直接ジャンプできます。  
- **動的コンテンツ生成** – ブックマークに紐付くテキストの挿入、置換、削除が可能です。  
- **条件付き表示** – ユーザーの設定や出力形式に応じてブックマークマーカーを表示/非表示にできます。  
- **再利用性** – スタイルを保持したまま、ブックマークされたフラグメントを文書間でコピーできます。

## 前提条件
- Java Development Kit (JDK) 8 以上。  
- プロジェクトに Aspose.Words for Java ライブラリを追加済み（Maven/Gradle または JAR）。  
- `Document` と `DocumentBuilder` クラスの基本的な知識。

## 手順ガイド

### Step 1: Create a Bookmark (create bookmark java)

ブックマークを追加するには、開始位置を設定し、コンテンツを書き込み、終了位置を設定します。以下の例は **My Bookmark** というシンプルなブックマークを作成します。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start the bookmark
builder.startBookmark("My Bookmark");
builder.writeln("Text inside a bookmark.");

// End the bookmark
builder.endBookmark("My Bookmark");
```

### Step 2: Access Bookmarks (access bookmarks java)

ブックマークはインデックス（0 ベース）または名前で取得できます。下記コードは両方の方法を示しています。

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");

// By index:
Bookmark bookmark1 = doc.getRange().getBookmarks().get(0);

// By name:
Bookmark bookmark2 = doc.getRange().getBookmarks().get("MyBookmark3");
```

### Step 3: Update Bookmark Data (update bookmark text)

ブックマークの名前変更やテキスト内容の置換が可能です。文書が変更された際に便利です。

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("MyBookmark1");
String name = bookmark.getName();
String text = bookmark.getText();
bookmark.setName("RenamedBookmark");
bookmark.setText("This is new bookmarked text.");
```

### Step 4: Work with Bookmarked Text (copy bookmarked text)

`NodeImporter` を使用すれば、元の書式を保持したままブックマークされたフラグメントを別文書へコピーできます。

```java
Document srcDoc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark srcBookmark = srcDoc.getRange().getBookmarks().get("MyBookmark1");
Document dstDoc = new Document();
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
appendBookmarkedText(importer, srcBookmark, dstDoc.getLastSection().getBody());
dstDoc.save("Your Directory Path" + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

### Step 5: Show and Hide Bookmarks (show hide bookmarks)

以下のスニペットは、保存ファイル内でブックマークのマーカーを非表示にする方法を示しています。`false` を渡すと非表示、`true` を渡すと表示されます。

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
showHideBookmarkedContent(doc, "MyBookmark1", false);
doc.save("Your Directory Path" + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Step 6: Untangle Row Bookmarks (bookmark table cell)

ブックマークがテーブル行を跨ぐと絡まりやすくなります。以下のユーティリティメソッドはそれらを解消し、特定の行をブックマークで削除できるようにします。

```java
Document doc = new Document("Your Directory Path" + "Table column bookmarks.docx");
untangle(doc);
deleteRowByBookmark(doc, "ROW2");
doc.save("Your Directory Path" + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

## よくある問題と解決策

| Issue | Solution |
|-------|----------|
| **Bookmark not found** | ブックマーク名が完全に一致しているか（大文字小文字を含む）確認し、作成後に文書が保存されていることを確認してください。 |
| **Copied text loses formatting** | Step 4 の例のように `NodeImporter` に `ImportFormatMode.KEEP_SOURCE_FORMATTING` を指定してください。 |
| **Show/hide does not affect output** | 文書を保存する **前に** `showHideBookmarkedContent` を呼び出しているか確認してください。 |
| **Bookmark inside a table cell is ignored** | `DocumentBuilder` のカーソルが対象セル内にある状態で start/end 呼び出しを行ってください。 |

## Frequently Asked Questions

**Q: テーブルセル内にブックマークを作成するには？**  
A: `DocumentBuilder` で目的のセルにカーソルを移動し、セル内容の前後で `startBookmark` と `endBookmark` を呼び出します。

**Q: ブックマークを別の文書にコピーできますか？**  
A: はい—Step 4 で示したように `NodeImporter` クラスを使用すれば、元の書式を保持したままインポートできます。

**Q: ブックマークで行を削除するには？**  
A: まずブックマークを含む行を特定し、Step 6 の例のようにその行ノードに対して `remove` を呼び出します。

**Q: ブックマークの一般的なユースケースは？**  
A: 目次の生成、レポート用の特定セクション抽出、ユーザー選択に基づく文書組み立ての自動化などがあります。

**Q: Aspose.Words for Java の詳細情報はどこで入手できますか？**  
A: 詳細なドキュメントとダウンロードは [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/) をご覧ください。

---

**Last Updated:** 2026-01-11  
**Tested With:** Aspose.Words for Java 24.11 (2026)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}