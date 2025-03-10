---
title: Aspose.Words for Java のクリーンアップ オプションの使用
linktitle: クリーンアップオプションの使用
second_title: Aspose.Words Java ドキュメント処理 API
description: Aspose.Words for Java のクリーンアップ オプションを使用してドキュメントの明瞭性を高めます。空の段落、未使用の領域などを削除する方法を学びます。
weight: 10
url: /ja/java/document-manipulation/using-cleanup-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java のクリーンアップ オプションの使用


## Aspose.Words for Java のクリーンアップ オプションの使用の概要

このチュートリアルでは、Aspose.Words for Java のクリーンアップ オプションを使用して、差し込み印刷プロセス中にドキュメントを操作およびクリーンアップする方法について説明します。クリーンアップ オプションを使用すると、空の段落や未使用の領域などの削除など、ドキュメントのクリーンアップのさまざまな側面を制御できます。

## 前提条件

始める前に、Aspose.Words for Javaライブラリがプロジェクトに統合されていることを確認してください。ダウンロードはこちらからできます。[ここ](https://releases.aspose.com/words/java/).

## ステップ1: 空の段落を削除する

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

//差し込みフィールドを挿入する
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

//クリーンアップオプションを設定する
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

//句読点を含む段落のクリーンアップを有効にする
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

//差し込み印刷を実行する
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

//文書を保存する
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

この例では、新しいドキュメントを作成し、差し込みフィールドを挿入し、空の段落を削除するようにクリーンアップ オプションを設定します。さらに、句読点のある段落の削除を有効にします。差し込み印刷を実行すると、指定したクリーンアップが適用された状態でドキュメントが保存されます。

## ステップ2: 結合されていない領域を削除する

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

//未使用領域を削除するクリーンアップオプションを設定する
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

//領域を指定して差し込み印刷を実行する
doc.getMailMerge().executeWithRegions(data);

//文書を保存する
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

この例では、マージ領域を含む既存のドキュメントを開き、未使用の領域を削除するようにクリーンアップ オプションを設定してから、空のデータで差し込み印刷を実行します。このプロセスにより、ドキュメントから未使用の領域が自動的に削除されます。

## ステップ3: 空のフィールドを削除する

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

//空のフィールドを削除するクリーンアップオプションを設定する
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

//差し込み印刷を実行する
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

//文書を保存する
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

この例では、差し込みフィールドを含むドキュメントを開き、空のフィールドを削除するようにクリーンアップ オプションを設定し、データを使用して差し込み印刷を実行します。差し込み印刷後、空のフィールドはドキュメントから削除されます。

## ステップ4: 未使用のフィールドを削除する

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

//未使用のフィールドを削除するクリーンアップオプションを設定する
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

//差し込み印刷を実行する
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

//文書を保存する
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

この例では、差し込みフィールドを含むドキュメントを開き、未使用のフィールドを削除するようにクリーンアップ オプションを設定し、データを使用して差し込み印刷を実行します。差し込み印刷後、未使用のフィールドはドキュメントから削除されます。

## ステップ5: 包含フィールドの削除

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

//クリーンアップオプションを設定して、包含フィールドを削除します
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

//差し込み印刷を実行する
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

//文書を保存する
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

この例では、差し込みフィールドを含むドキュメントを開き、含まれるフィールドを削除するようにクリーンアップ オプションを設定し、データを使用して差し込み印刷を実行します。差し込み印刷後、フィールド自体はドキュメントから削除されます。

## ステップ6: 空のテーブル行を削除する

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

//空のテーブル行を削除するクリーンアップオプションを設定する
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

//差し込み印刷を実行する
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

//文書を保存する
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

この例では、テーブルと結合フィールドを含むドキュメントを開き、空のテーブル行を削除するようにクリーンアップ オプションを設定し、データを使用して差し込み印刷を実行します。差し込み印刷後、空のテーブル行はドキュメントから削除されます。

## 結論

このチュートリアルでは、Aspose.Words for Java のクリーンアップ オプションを使用して、差し込み印刷プロセス中にドキュメントを操作およびクリーンアップする方法を学習しました。これらのオプションを使用すると、ドキュメントのクリーンアップを細かく制御できるため、洗練されたカスタマイズされたドキュメントを簡単に作成できます。

## よくある質問

### Aspose.Words for Java のクリーンアップ オプションとは何ですか?

Aspose.Words for Java のクリーンアップ オプションは、差し込み印刷処理中にドキュメントのクリーンアップのさまざまな側面を制御できる設定です。これにより、空の段落、未使用の領域などの不要な要素を削除して、最終的なドキュメントが適切に構造化され、洗練されることが保証されます。

### 文書から空の段落を削除するにはどうすればよいですか?

 Aspose.Words for Javaを使用してドキュメントから空の段落を削除するには、`MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS`オプションを true に設定します。これにより、コンテンツのない段落が自動的に削除され、よりクリーンなドキュメントが作成されます。

### の目的は何ですか？`REMOVE_UNUSED_REGIONS` cleanup option?

の`MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS`オプションは、差し込み印刷処理中に対応するデータがない文書内の領域を削除するために使用されます。未使用のプレースホルダーを削除することで、文書を整理された状態に保つことができます。

### Aspose.Words for Java を使用してドキュメントから空のテーブル行を削除できますか?

はい、ドキュメントから空の表の行を削除するには、`MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS`cleanup オプションを true に設定します。これにより、データが含まれていないテーブル行が自動的に削除され、ドキュメント内のテーブルが適切に構造化されます。

### 設定するとどうなるか`REMOVE_CONTAINING_FIELDS` option?

設定`MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS`オプションを選択すると、差し込み印刷処理中に、差し込みフィールド全体（それに含まれる段落を含む）が文書から削除されます。これは、差し込みフィールドとそれに関連するテキストを削除する場合に便利です。

### ドキュメントから未使用の差し込みフィールドを削除するにはどうすればよいですか?

文書から未使用の差し込みフィールドを削除するには、`MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS`オプションを true に設定します。これにより、差し込み印刷中に入力されていない差し込みフィールドが自動的に削除され、よりクリーンなドキュメントが作成されます。

### 違いは何ですか？`REMOVE_EMPTY_FIELDS` and `REMOVE_UNUSED_FIELDS` cleanup options?

の`REMOVE_EMPTY_FIELDS`オプションは、差し込み印刷処理中にデータがないか空の差し込みフィールドを削除します。一方、`REMOVE_UNUSED_FIELDS`オプションは、マージ中にデータが入力されていないマージ フィールドを削除します。どちらを選択するかは、コンテンツのないフィールドを削除するか、特定のマージ操作で使用されていないフィールドを削除するかによって異なります。

### 句読点の付いた段落を削除するにはどうすればよいですか?

句読点を含む段落を削除するには、`cleanupParagraphsWithPunctuationMarks`オプションを true に設定し、クリーンアップの対象となる句読点を指定します。これにより、不要な句読点のみの段落を削除して、より洗練されたドキュメントを作成できます。

### Aspose.Words for Java のクリーンアップ オプションをカスタマイズできますか?

はい、特定のニーズに応じてクリーンアップ オプションをカスタマイズできます。適用するクリーンアップ オプションを選択し、ドキュメントのクリーンアップ要件に応じて構成することで、最終的なドキュメントが希望する基準を満たすようにすることができます。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
