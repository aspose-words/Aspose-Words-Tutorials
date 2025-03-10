---
title: Aspose.Words for Java でのテキストの検索と置換
linktitle: テキストの検索と置換
second_title: Aspose.Words Java ドキュメント処理 API
description: Aspose.Words for Java を使用して Word 文書内のテキストを検索および置換する方法を学びます。コード例を使用したステップバイステップのガイド。Java 文書の操作スキルを強化します。
weight: 15
url: /ja/java/document-manipulation/finding-and-replacing-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java でのテキストの検索と置換


## Aspose.Words for Java でのテキストの検索と置換の概要

Aspose.Words for Java は、Word 文書をプログラムで操作できる強力な Java API です。Word 文書を扱う際の一般的なタスクの 1 つは、テキストの検索と置換です。テンプレートのプレースホルダーを更新する必要がある場合でも、より複雑なテキスト操作を実行する必要がある場合でも、Aspose.Words for Java を使用すると、効率的に目標を達成できます。

## 前提条件

テキストの検索と置換の詳細に入る前に、次の前提条件が満たされていることを確認してください。

- Java開発環境
- Aspose.Words for Java ライブラリ
- 作業に使えるサンプルのWord文書

Aspose.Words for Javaライブラリは以下からダウンロードできます。[ここ](https://releases.aspose.com/words/java/).

## 単純なテキストの検索と置換

```java
//ドキュメントを読み込む
Document doc = new Document("your-document.docx");

//ドキュメントビルダーを作成する
DocumentBuilder builder = new DocumentBuilder(doc);

//テキストの検索と置換
builder.getRange().replace("old-text", "new-text", new FindReplaceOptions());

//変更したドキュメントを保存する
doc.save("modified-document.docx");
```

この例では、Word文書を読み込み、`DocumentBuilder` 、そして`replace`ドキュメント内の「古いテキスト」を検索して「新しいテキスト」に置き換える方法。

## 正規表現の使用

正規表現は、テキストの検索と置換のための強力なパターン マッチング機能を提供します。Aspose.Words for Java は、より高度な検索および置換操作のための正規表現をサポートしています。

```java
//ドキュメントを読み込む
Document doc = new Document("your-document.docx");

//ドキュメントビルダーを作成する
DocumentBuilder builder = new DocumentBuilder(doc);

//正規表現を使用してテキストを検索および置換する
Pattern regex = Pattern.compile("your-pattern");
builder.getRange().replace(regex, "replacement-text", new FindReplaceOptions());

//変更したドキュメントを保存する
doc.save("modified-document.docx");
```

この例では、正規表現パターンを使用して、ドキュメント内のテキストを検索して置換します。

## フィールド内のテキストを無視する

検索および置換操作を実行するときにフィールド内のテキストを無視するように Aspose.Words を構成できます。

```java
//ドキュメントを読み込む
Document doc = new Document("your-document.docx");

// FindReplaceOptionsインスタンスを作成し、IgnoreFieldsをtrueに設定する
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreFields(true);

//テキストを置換するときにオプションを使用する
doc.getRange().replace("text-to-replace", "new-text", options);

//変更したドキュメントを保存する
doc.save("modified-document.docx");
```

これは、マージ フィールドなどのフィールド内のテキストを置換対象から除外する場合に便利です。

## 削除リビジョン内のテキストを無視する

検索および置換操作中に削除リビジョン内のテキストを無視するように Aspose.Words を構成できます。

```java
//ドキュメントを読み込む
Document doc = new Document("your-document.docx");

// FindReplaceOptionsインスタンスを作成し、IgnoreDeletedをtrueに設定する
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreDeleted(true);

//テキストを置換するときにオプションを使用する
doc.getRange().replace("text-to-replace", "new-text", options);

//変更したドキュメントを保存する
doc.save("modified-document.docx");
```

これにより、変更履歴で削除対象としてマークされたテキストを置き換えから除外できます。

## 挿入リビジョン内のテキストを無視する

検索および置換操作中に挿入リビジョン内のテキストを無視するように Aspose.Words を構成できます。

```java
//ドキュメントを読み込む
Document doc = new Document("your-document.docx");

// FindReplaceOptionsインスタンスを作成し、IgnoreInsertedをtrueに設定する
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreInserted(true);

//テキストを置換するときにオプションを使用する
doc.getRange().replace("text-to-replace", "new-text", options);

//変更したドキュメントを保存する
doc.save("modified-document.docx");
```

これにより、変更履歴で挿入としてマークされたテキストを置換対象から除外できます。

## テキストをHTMLに置き換える

Aspose.Words for Java を使用して、テキストを HTML コンテンツに置き換えることができます。

```java
//ドキュメントを読み込む
Document doc = new Document("your-document.docx");

//カスタム置換コールバックを使用して FindReplaceOptions インスタンスを作成する
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceWithHtmlEvaluator(options));

//テキストを置換するときにオプションを使用する
doc.getRange().replace("text-to-replace", "new-html-content", options);

//変更したドキュメントを保存する
doc.save("modified-document.docx");
```

この例では、カスタム`ReplaceWithHtmlEvaluator`テキストを HTML コンテンツに置き換えます。

## ヘッダーとフッターのテキストの置き換え

Word 文書のヘッダーとフッター内のテキストを検索して置換できます。

```java
//ドキュメントを読み込む
Document doc = new Document("your-document.docx");

//ヘッダーとフッターのコレクションを取得する
HeaderFooterCollection headersFooters = doc.getFirstSection().getHeadersFooters();

//テキストを置き換えるヘッダーまたはフッターの種類を選択します (例: HeaderFooterType.FOOTER_PRIMARY)
HeaderFooter footer = headersFooters.getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);

// FindReplaceOptionsインスタンスを作成し、フッターの範囲に適用します。
FindReplaceOptions options = new FindReplaceOptions();
footer.getRange().replace("text-to-replace", "new-text", options);

//変更したドキュメントを保存する
doc.save("modified-document.docx");
```

これにより、ヘッダーとフッター内のテキストの置換を具体的に実行できるようになります。

## ヘッダーとフッターの順序の変更を表示する

Aspose.Words を使用すると、ドキュメント内のヘッダーとフッターの順序の変更を表示できます。

```java
//ドキュメントを読み込む
Document doc = new Document("your-document.docx");

//最初のセクションを取得する
Section firstPageSection = doc.getFirstSection();

//FindReplaceOptionsインスタンスを作成し、それをドキュメントの範囲に適用します。
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceLog());

//ヘッダーとフッターの順序に影響するテキストを置き換える
doc.getRange().replace(Pattern.compile("(header|footer)"), "", options);

//変更したドキュメントを保存する
doc.save("modified-document.docx");
```

これにより、ドキュメント内のヘッダーとフッターの順序に関連する変更を視覚化できます。

## テキストをフィールドで置き換える

Aspose.Words for Java を使用して、テキストをフィールドに置き換えることができます。

```java
//ドキュメントを読み込む
Document doc = new Document("your-document.docx");

// FindReplaceOptionsインスタンスを作成し、フィールドのカスタム置換コールバックを設定します。
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceTextWithFieldHandler(FieldType.FIELD_MERGE_FIELD));

//テキストを置換するときにオプションを使用する
doc.getRange().replace(Pattern.compile("PlaceHolder(\\d+)"), "", options);

//変更したドキュメントを保存する
doc.save("modified-document.docx");
```

この例では、テキストをフィールドに置き換え、フィールドタイプを指定します（例：`FieldType.FIELD_MERGE_FIELD`）。

## 評価者との交代

カスタム評価ツールを使用すると、置換テキストを動的に決定できます。

```java
//ドキュメントを読み込む
Document doc = new Document("your-document.docx");

// FindReplaceOptionsインスタンスを作成し、カスタム置換コールバックを設定する
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new MyReplaceEvaluator());

//テキストを置換するときにオプションを使用する
doc.getRange().replace(Pattern.compile("[s|m]ad"), "", options);

//変更したドキュメントを保存する
doc.save("modified-document.docx");
```

この例では、カスタム評価器（`MyReplaceEvaluator`）を使用してテキストを置き換えます。

## 正規表現による置換

Aspose.Words for Java を使用すると、正規表現を使用してテキストを置き換えることができます。

```java
//ドキュメントを読み込む
Document doc = new Document("your-document.docx");

//正規表現を使用してテキストを検索および置換する
doc.getRange().replace(Pattern.compile("[s|m]ad"), "bad", new FindReplaceOptions());

//変更したドキュメントを保存する
doc.save("modified-document.docx");
```

この例では、正規表現パターンを使用して、ドキュメント内のテキストを検索して置換します。

## 置換パターン内の認識と置換

Aspose.Words for Java を使用すると、置換パターン内での置換を認識して実行できます。

```java
//ドキュメントを読み込む
Document doc = new Document("your-document.docx");

// UseSubstitutionsをtrueに設定してFindReplaceOptionsインスタンスを作成します。
FindReplaceOptions options = new FindReplaceOptions();
options.setUseSubstitutions(true);

//テキストをパターンに置き換えるときにオプションを使用する
doc.getRange().replace(Pattern.compile("([A-z]+) give money to ([A-z]+)"), "$2 take money from $1", options);

//変更したドキュメントを保存する
doc.save("modified-document.docx");
```

これにより、置換パターン内で置換を実行し、より高度な置換を実行できるようになります。

## 文字列で置き換える

Aspose.Words for Java を使用して、テキストを単純な文字列に置き換えることができます。

```java
//ドキュメントを読み込む
Document doc = new Document("your-document.docx");

//テキストを文字列に置き換える
doc.getRange().replace("text-to-replace", "new-string", new FindReplaceOptions());

//変更したドキュメントを保存する
doc.save("modified-document.docx");
```

この例では、ドキュメント内の「text-to-replace」を「new-string」に置き換えます。

## レガシーオーダーの使用

検索および置換操作を実行するときに、従来の順序を使用できます。

```java
//ドキュメントを読み込む
Document doc = new Document("your-document.docx");

// FindReplaceOptionsインスタンスを作成し、UseLegacyOrderをtrueに設定する
FindReplaceOptions options = new FindReplaceOptions();
options.setUseLegacyOrder(true);

//テキストを置換するときにオプションを使用する
doc.getRange().replace(Pattern.compile("\\[(.*?)\\]"), "", options);

//変更したドキュメントを保存する
doc.save("modified-document.docx");
```

これにより、検索および置換操作に従来の順序を使用できるようになります。

## 表内のテキストの置換

Word 文書内の表内のテキストを検索して置換できます。

```java
//ドキュメントを読み込む
Document doc = new Document("your-document.docx");

//特定のテーブル（例：最初のテーブル）を取得する
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);

//表内のテキストを置換するには FindReplaceOptions を使用します
table.getRange().replace("old-text", "new-text", new FindReplaceOptions());

//変更したドキュメントを保存する
doc.save("modified-document.docx");
```

これにより、テーブル内でのみテキストの置換を実行できます。

## 結論

Aspose.Words for Java は、Word 文書内のテキストを検索および置換するための包括的な機能を提供します。単純なテキスト置換を実行する必要がある場合でも、正規表現、フィールド操作、カスタム評価子を使用したより高度な操作を実行する必要がある場合でも、Aspose.Words for Java が対応します。この強力な Java ライブラリの可能性を最大限に活用するには、Aspose が提供する広範なドキュメントと例を必ず参照してください。

## よくある質問

### Aspose.Words for Java をダウンロードするにはどうすればいいですか?

 Aspose.Words for Javaは、次のWebサイトからダウンロードできます。[このリンク](https://releases.aspose.com/words/java/).

### テキストの置換に正規表現を使用できますか?

はい、Aspose.Words for Java では、テキスト置換に正規表現を使用できます。これにより、より高度で柔軟な検索および置換操作を実行できます。

### 置換中にフィールド内のテキストを無視するにはどうすればよいですか?

置換時にフィールド内のテキストを無視するには、`IgnoreFields`の財産`FindReplaceOptions`に`true`これにより、マージ フィールドなどのフィールド内のテキストが置換から除外されます。

### ヘッダーとフッター内のテキストを置き換えることはできますか?

はい、Word文書のヘッダーとフッター内のテキストを置き換えることができます。適切なヘッダーまたはフッターにアクセスし、`replace`望ましい方法`FindReplaceOptions`.

### UseLegacyOrder オプションの目的は何ですか?

の`UseLegacyOrder`オプション`FindReplaceOptions`検索および置換操作を実行するときに従来の順序を使用できます。これは、従来の順序の動作が望ましい特定のシナリオで役立ちます。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
