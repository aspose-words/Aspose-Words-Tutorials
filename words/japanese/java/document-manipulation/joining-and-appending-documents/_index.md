---
title: Aspose.Words for Java でのドキュメントの結合と追加
linktitle: ドキュメントの結合と追加
second_title: Aspose.Words Java ドキュメント処理 API
description: Aspose.Words for Java を使用して、ドキュメントを簡単に結合および追加する方法を学びます。書式設定を保持し、ヘッダーやフッターなどを管理します。
weight: 30
url: /ja/java/document-manipulation/joining-and-appending-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java でのドキュメントの結合と追加


## Aspose.Words for Java でのドキュメントの結合と追加の概要

このチュートリアルでは、Aspose.Words for Java ライブラリを使用してドキュメントを結合および追加する方法について説明します。書式と構造を維持しながら、複数のドキュメントをシームレスに結合する方法を学習します。

## 前提条件

始める前に、Java プロジェクトに Aspose.Words for Java API が設定されていることを確認してください。

## ドキュメント結合オプション

### 単純な追加

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### インポート形式オプションを追加

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

### 空白のドキュメントに追加

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document();
dstDoc.removeAllChildren();
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### ページ番号変換で追加

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
convertNumPageFieldsToPageRef(dstDoc); //NUMPAGESフィールドを変換する
dstDoc.updatePageLayout(); //正しい番号付けのためにページレイアウトを更新します
```

## 異なるページ設定の処理

異なるページ設定のドキュメントを追加する場合:

```java
srcDoc.getFirstSection().getPageSetup().setSectionStart(SectionStart.CONTINUOUS);
srcDoc.getFirstSection().getPageSetup().setRestartPageNumbering(true);
//ページ設定が宛先ドキュメントと一致していることを確認する
```

## 異なるスタイルのドキュメントを結合する

```java
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES);
```

## スマートスタイルの動作

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setSmartStyleBehavior(true);
builder.insertDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

## DocumentBuilder によるドキュメントの挿入

```java
DocumentBuilder builder = new DocumentBuilder(dstDoc);
builder.insertDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## ソース番号の保持

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## テキストボックスの処理

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setIgnoreTextBoxes(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## ヘッダーとフッターの管理

### ヘッダーとフッターのリンク

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### ヘッダーとフッターのリンクを解除する

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## 結論

Aspose.Words for Java は、書式設定の維持、さまざまなページ設定の処理、ヘッダーとフッターの管理など、ドキュメントを結合および追加するための柔軟で強力なツールを提供します。これらの手法を試して、特定のドキュメント処理のニーズを満たしてください。

## よくある質問

### 異なるスタイルのドキュメントをシームレスに結合するにはどうすればよいでしょうか?

異なるスタイルの文書を結合するには、`ImportFormatMode.USE_DESTINATION_STYLES`追加するとき。

### ドキュメントを追加するときにページ番号を保持できますか?

はい、ページ番号を維持するには、`convertNumPageFieldsToPageRef`メソッドとページ レイアウトの更新について説明します。

### スマートスタイルビヘイビアとは何ですか?

スマートスタイルビヘイビアは、ドキュメントを追加するときに一貫したスタイルを維持するのに役立ちます。`ImportFormatOptions`より良い結果を得るために。

### ドキュメントを追加するときにテキスト ボックスをどのように処理すればよいですか?

セット`importFormatOptions.setIgnoreTextBoxes(false)`追加時にテキスト ボックスを含めます。

### ドキュメント間でヘッダーとフッターをリンク/リンク解除したい場合はどうすればよいでしょうか?

ヘッダーとフッターをリンクすることができます`linkToPrevious(true)`またはリンクを解除する`linkToPrevious(false)`必要に応じて。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
