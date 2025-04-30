---
"description": "Aspose.Words for Java のクリーンアップオプションでドキュメントの明瞭性を高めましょう。空の段落や未使用領域などを削除する方法を学びましょう。"
"linktitle": "クリーンアップオプションの使用"
"second_title": "Aspose.Words Java ドキュメント処理 API"
"title": "Aspose.Words for Java のクリーンアップ オプションの使用"
"url": "/ja/java/document-manipulation/using-cleanup-options/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java のクリーンアップ オプションの使用


## Aspose.Words for Java のクリーンアップ オプションの使用の概要

このチュートリアルでは、Aspose.Words for Java のクリーンアップオプションを使用して、差し込み印刷処理中にドキュメントを操作およびクリーンアップする方法を説明します。クリーンアップオプションを使用すると、空の段落や未使用領域の削除など、ドキュメントのクリーンアップのさまざまな側面を制御できます。

## 前提条件

始める前に、Aspose.Words for Javaライブラリがプロジェクトに統合されていることを確認してください。ダウンロードはこちらから。 [ここ](https://releases。aspose.com/words/java/).

## ステップ1：空の段落を削除する

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 差し込みフィールドを挿入する
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// クリーンアップオプションを設定する
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// 句読点を含む段落のクリーンアップを有効にする
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// 差し込み印刷を実行する
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// ドキュメントを保存する
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

この例では、新規文書を作成し、差し込みフィールドを挿入し、空の段落を削除するようにクリーンアップオプションを設定します。さらに、句読点を含む段落の削除も有効にします。差し込み印刷を実行すると、指定したクリーンアップが適用された状態で文書が保存されます。

## ステップ2: 結合されていない領域を削除する

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// 未使用領域を削除するクリーンアップオプションを設定する
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// 領域を指定して差し込み印刷を実行する
doc.getMailMerge().executeWithRegions(data);

// ドキュメントを保存する
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

この例では、差し込み領域を含む既存の文書を開き、不要な領域を削除するようにクリーンアップオプションを設定してから、空のデータで差し込み印刷を実行します。この処理により、文書から不要な領域が自動的に削除されます。

## ステップ3: 空のフィールドを削除する

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// 空のフィールドを削除するクリーンアップオプションを設定する
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// 差し込み印刷を実行する
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// ドキュメントを保存する
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

この例では、差し込みフィールドを含む文書を開き、空のフィールドを削除するようにクリーンアップオプションを設定し、データを含む差し込み印刷を実行します。差し込み印刷後、空のフィールドは文書から削除されます。

## ステップ4: 未使用フィールドの削除

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// 未使用のフィールドを削除するにはクリーンアップ オプションを設定します
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// 差し込み印刷を実行する
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// ドキュメントを保存する
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

この例では、差し込みフィールドを含む文書を開き、未使用のフィールドを削除するようにクリーンアップオプションを設定し、データを使用して差し込み印刷を実行します。差し込み印刷後、未使用のフィールドは文書から削除されます。

## ステップ5: 包含フィールドの削除

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// 包含フィールドを削除するクリーンアップオプションを設定する
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// 差し込み印刷を実行する
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// ドキュメントを保存する
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

この例では、差し込みフィールドを含む文書を開き、クリーンアップオプションで該当するフィールドを削除し、データを含む差し込み印刷を実行します。差し込み印刷後、フィールド自体は文書から削除されます。

## ステップ6: 空のテーブル行を削除する

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// 空のテーブル行を削除するクリーンアップオプションを設定する
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// 差し込み印刷を実行する
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// ドキュメントを保存する
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

この例では、表と差し込みフィールドを含む文書を開き、空の表行を削除するようにクリーンアップオプションを設定し、データを含む差し込み印刷を実行します。差し込み印刷後、空の表行は文書から削除されます。

## 結論

このチュートリアルでは、Aspose.Words for Java のクリーンアップオプションを使用して、差し込み印刷プロセス中にドキュメントを操作およびクリーンアップする方法を学びました。これらのオプションを使用すると、ドキュメントのクリーンアップを細かく制御できるため、洗練されたカスタマイズされたドキュメントを簡単に作成できます。

## よくある質問

### Aspose.Words for Java のクリーンアップ オプションとは何ですか?

Aspose.Words for Java のクリーンアップオプションは、差し込み印刷処理中のドキュメントのクリーンアップに関するさまざまな側面を制御できる設定です。空の段落や未使用領域などの不要な要素を削除することで、最終的なドキュメントの構造が整えられ、洗練された仕上がりを実現します。

### 文書から空の段落を削除するにはどうすればよいでしょうか?

Aspose.Words for Javaを使用してドキュメントから空の段落を削除するには、 `MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS` このオプションをtrueに設定します。これにより、コンテンツのない段落が自動的に削除され、よりクリーンなドキュメントが作成されます。

### の目的は何ですか？ `REMOVE_UNUSED_REGIONS` クリーンアップオプション?

その `MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS` このオプションは、差し込み印刷処理中に対応するデータがない文書内の領域を削除するために使用されます。これにより、未使用のプレースホルダーが削除され、文書が整理された状態を保つことができます。

### Aspose.Words for Java を使用してドキュメントから空のテーブル行を削除できますか?

はい、ドキュメントから空の表の行を削除するには、 `MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS` cleanup オプションを true に設定します。これにより、データが含まれていない表の行が自動的に削除され、ドキュメント内の表の構造が適切に整えられます。

### 設定するとどうなるか `REMOVE_CONTAINING_FIELDS` オプション？

設定 `MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS` このオプションを選択すると、差し込み印刷処理中に、差し込みフィールド全体（段落を含む）が文書から削除されます。これは、差し込みフィールドとそれに関連するテキストを削除したい場合に便利です。

### ドキュメントから未使用の差し込みフィールドを削除するにはどうすればよいですか?

文書から未使用の差し込みフィールドを削除するには、 `MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` このオプションをtrueに設定します。これにより、差し込み印刷時に入力されていない差し込みフィールドが自動的に削除され、よりクリーンな文書が作成されます。

### 違いは何ですか？ `REMOVE_EMPTY_FIELDS` そして `REMOVE_UNUSED_FIELDS` クリーンアップオプション?

その `REMOVE_EMPTY_FIELDS` オプションは、差し込み印刷処理中に、データが入力されていない、または空の差し込みフィールドを削除します。一方、 `REMOVE_UNUSED_FIELDS` このオプションは、マージ中にデータが入力されていないマージフィールドを削除します。どちらを選択するかは、コンテンツのないフィールドを削除するか、特定のマージ操作で使用されないフィールドを削除するかによって異なります。

### 句読点の付いた段落を削除するにはどうすればよいですか?

句読点を含む段落を削除するには、 `cleanupParagraphsWithPunctuationMarks` オプションをtrueに設定し、クリーンアップの対象となる句読点を指定します。これにより、不要な句読点のみの段落を削除し、より洗練されたドキュメントを作成できます。

### Aspose.Words for Java のクリーンアップ オプションをカスタマイズできますか?

はい、お客様のニーズに合わせてクリーンアップオプションをカスタマイズできます。適用するクリーンアップオプションを選択し、ドキュメントのクリーンアップ要件に合わせて設定することで、最終的なドキュメントがご希望の基準を満たすことを保証します。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}