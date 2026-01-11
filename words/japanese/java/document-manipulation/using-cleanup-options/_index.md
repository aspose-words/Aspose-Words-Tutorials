---
date: 2026-01-11
description: Aspose.Words for Java のクリーンアップオプションを使用して、空の段落や空のテーブル行、未使用のフィールドの削除など、Word
  文書のクリーンアップ方法を学びましょう。
linktitle: Using Cleanup Options
second_title: Aspose.Words Java Document Processing API
title: Aspose.Words のクリーンアップオプション（Java）を使用して Word 文書をクリーンアップ
url: /ja/java/document-manipulation/using-cleanup-options/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words のクリーンアップオプションを使用した Word 文書のクリーンアップ (Java)

このチュートリアルでは、Aspose.Words for Java を使用して **Word 文書** をクリーンアップする方法を紹介します。請求書、契約書、または大量のメールマージレポートを生成する場合でも、不要な空段落、未使用フィールド、空白のテーブル行が最終出力をプロフェッショナルでないものにしてしまうことがあります。各クリーンアップオプションをステップバイステップで解説し、必要な正確なコードを示し、*なぜ* その設定が重要なのかを説明しますので、毎回洗練された文書を作成できます。

## Quick Answers
- **「Word 文書をクリーンアップする」とは何ですか？** メールマージ操作後に残る空段落、未使用のマージ領域、空のテーブル行、その他の冗長要素を削除することです。  
- **空段落を削除するクリーンアップオプションはどれですか？** `MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS`。  
- **空のテーブル行を削除するには？** `MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS` を使用します。  
- **使用されなかったフィールドを除去できますか？** はい – `MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` または `REMOVE_EMPTY_FIELDS`。  
- **これらのサンプルを実行するのにライセンスは必要ですか？** 評価用の無料トライアルで動作しますが、本番環境では商用ライセンスが必要です。

## What Is “Clean Up Word Document” in the Context of Mail Merge?
メールマージを実行すると、Aspose.Words はマージフィールドや領域にデータを挿入します。いくつかのフィールドが `null` や空文字列になると、文書内に不要な段落や空テーブル、プレースホルダー領域が残ることがあります。**クリーンアップオプション**はこれらのアーティファクトを自動的に除去し、印刷準備が整ったクリーンな文書にします。

## Why Use Cleanup Options?
- **プロフェッショナルな外観:** 空白行や孤立したテーブルがありません。  
- **ファイルサイズの削減:** 未使用要素を削除することで文書の容量が減ります。  
- **下流処理の簡素化:** クリーンな文書は PDF、HTML などへの変換が容易です。  
- **時間の節約:** ワンラインの設定で手作業の後処理スクリプトを置き換えられます。

## Prerequisites
- Java 開発環境 (JDK 8 以上)。  
- Aspose.Words for Java ライブラリ – [こちら](https://releases.aspose.com/words/java/) からダウンロード。  
- メールマージの基本概念に関する基礎知識。

## Step‑by‑Step Guide

### Step 1: How to Remove Empty Paragraphs (Java)
まず、可視テキストがまったく含まれない段落を削除する方法を示します。これはマージフィールドが `null` に解決された場合に特に有用です。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert merge fields
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Set cleanup options
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Enable cleanup of paragraphs that contain only punctuation marks
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Execute mail merge (both fields are null, so they become empty)
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

**ここで何が起こるのか？**  
- `REMOVE_EMPTY_PARAGRAPHS` は、マージ後に空になった段落をすべて除去するよう Aspose.Words に指示します。  
- `cleanupParagraphsWithPunctuationMarks` を有効にすると、句読点だけで構成された段落（例: “?”）も削除されます。

### Step 2: How to Remove Unmerged Regions
マージ領域に対応するデータが存在しない場合、その領域全体を破棄できます。

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Set cleanup options to remove unused regions
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Execute mail merge with regions (the DataSet is empty)
doc.getMailMerge().executeWithRegions(data);

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

**なぜ重要か:**  
未使用領域は空白セクションや不要な見出しを残すことが多いです。`REMOVE_UNUSED_REGIONS` フラグはそれらを自動的にクリーンアップします。

### Step 3: How to Remove Empty Fields
フィールドが空文字列を受け取ったとき、空のプレースホルダーを残すのではなくフィールド自体を削除したい場合があります。

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove empty fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Execute mail merge with a mix of populated and empty values
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

### Step 4: How to Remove Unused Fields
マージ中に一度も参照されなかったフィールドは、完全に除去できます。

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove unused fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

### Step 5: How to Remove Containing Fields
場合によっては、マージフィールドが含まれる段落自体も削除したいことがあります。

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove containing fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

### Step 6: How to Remove Empty Table Rows
テーブルは、空フィールドだけが入った行が残りがちです。このオプションでそのような行を除去します。

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove empty table rows
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

## Common Issues & Troubleshooting
- **段落が削除されない:** `setCleanupParagraphsWithPunctuationMarks(true)` をクリーンアップオプション設定 *後* に呼び出していることを確認してください。  
- **空のテーブル行が残る:** テーブルセルが本当に空文字列か（空白文字ではないか）を確認してください。  
- **未使用フィールドが残る:** 正しい列挙子 (`REMOVE_UNUSED_FIELDS`) を使用しているか、他の場所でフィールドが誤って埋め込まれていないか再確認してください。

## Frequently Asked Questions

**Q: `REMOVE_EMPTY_FIELDS` と `REMOVE_UNUSED_FIELDS` の違いは何ですか？**  
A: `REMOVE_EMPTY_FIELDS` はマージ時に空文字列または `null` が渡されたフィールドを削除し、`REMOVE_UNUSED_FIELDS` はマージ操作自体で参照されなかったフィールドを削除します。

**Q: 複数のクリーンアップオプションを組み合わせられますか？**  
A: はい。`setCleanupOptions` メソッドは列挙値のビット単位 OR を受け取り、段落、テーブル、領域を一度の呼び出しでクリーンアップできます。

**Q: `cleanupParagraphsWithPunctuationMarks` を有効にすると通常のテキストに影響しますか？**  
A: 句読点だけで構成された段落（例: “?” や “---”）のみが削除され、通常の文章はそのまま残ります。

**Q: 対象となる句読点をカスタマイズできますか？**  
A: 現行 API は事前定義された句読点セットを使用します。カスタム動作が必要な場合は、マージ後にドキュメントを追加処理する必要があります。

**Q: これらのクリーンアップオプションは PDF 変換でも機能しますか？**  
A: 完全に対応しています。Word 文書がクリーンアップされた後、PDF、HTML などの任意のサポート形式に変換しても不要な要素は引き継がれません。

## Conclusion
これで、Aspose.Words for Java を使用したメールマージ時に **Word 文書** をクリーンアップするための完全なツールボックスが手に入りました。適切な `MailMergeCleanupOptions` を選択すれば、空段落、空テーブル行、未使用フィールドなどを自動的に除去でき、常に洗練された本番品質の文書を生成できます。

---

**最終更新日:** 2026-01-11  
**テスト環境:** Aspose.Words for Java 24.11  
**作者:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}