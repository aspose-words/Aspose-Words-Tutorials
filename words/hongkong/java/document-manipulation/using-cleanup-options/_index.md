---
title: 在 Aspose.Words for Java 中使用清理選項
linktitle: 使用清理選項
second_title: Aspose.Words Java 文件處理 API
description: 使用 Aspose.Words for Java 清理選項增強文件清晰度。了解如何刪除空白段落、未使用的區域等。
weight: 10
url: /zh-hant/java/document-manipulation/using-cleanup-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中使用清理選項


## 在 Aspose.Words for Java 中使用清理選項的簡介

在本教學中，我們將探討如何在郵件合併過程中使用 Aspose.Words for Java 中的清理選項來操作和清理文件。清理選項可讓您控製文件清理的各個方面，例如刪除空白段落、未使用的區域等。

## 先決條件

在開始之前，請確保您已將 Aspose.Words for Java 程式庫整合到您的專案中。您可以從以下位置下載：[這裡](https://releases.aspose.com/words/java/).

## 第 1 步：刪除空白段落

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

//插入合併字段
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

//設定清理選項
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

//啟用標點符號的清理段落
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

//執行郵件合併
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

//儲存文件
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

在此範例中，我們建立一個新文檔，插入合併字段，並設定清理選項以刪除空白段落。此外，我們也可以刪除有標點符號的段落。執行郵件合併後，將儲存文件並套用指定的清理。

## 步驟2：刪除未合併的區域

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

//設定清理選項以刪除未使用的區域
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

//執行與區域的郵件合併
doc.getMailMerge().executeWithRegions(data);

//儲存文件
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

在此範例中，我們開啟一個包含合併區域的現有文檔，設定清理選項以刪除未使用的區域，然後使用空白資料執行郵件合併。此過程會自動從文件中刪除未使用的區域。

## 第 3 步：刪除空白字段

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

//設定清理選項以刪除空白字段
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

//執行郵件合併
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

//儲存文件
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

在此範例中，我們開啟一個包含合併字段的文檔，設定清理選項以刪除空白字段，然後執行與資料的郵件合併。合併後，任何空白欄位都將從文件中刪除。

## 第 4 步：刪除未使用的字段

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

//設定清理選項以刪除未使用的字段
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

//執行郵件合併
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

//儲存文件
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

在此範例中，我們開啟一個包含合併字段的文檔，設定清理選項以刪除未使用的字段，然後執行與資料的郵件合併。合併後，任何未使用的欄位將從文件中刪除。

## 第 5 步：刪除包含字段

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

//設定清理選項以刪除包含字段
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

//執行郵件合併
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

//儲存文件
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

在此範例中，我們開啟一個包含合併字段的文檔，設定清理選項以刪除包含字段，然後執行與資料的郵件合併。合併後，欄位本身將從文件中刪除。

## 步驟 6：刪除空白表格行

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

//設定清理選項以刪除空白表行
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

//執行郵件合併
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

//儲存文件
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

在此範例中，我們開啟一個包含表格和合併欄位的文檔，設定清理選項以刪除空白表行，並執行與資料的郵件合併。合併後，任何空白表行都將從文件中刪除。

## 結論

在本教學中，您學習如何在郵件合併過程中使用 Aspose.Words for Java 中的清理選項來操作和清理文件。這些選項提供對文件清理的細粒度控制，使您可以輕鬆建立精美的自訂文件。

## 常見問題解答

### Aspose.Words for Java 中的清理選項有哪些？

Aspose.Words for Java 中的清理選項可讓您在郵件合併過程中控製文件清理的各個方面。它們使您能夠刪除不必要的元素，例如空白段落、未使用的區域等，確保您的最終文件結構良好且優美。

### 如何從文件中刪除空段落？

若要使用 Aspose.Words for Java 從文件中刪除空段落，您可以設定`MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS`選項為真。這將自動消除沒有內容的段落，從而產生更乾淨的文件。

### 目的是什麼`REMOVE_UNUSED_REGIONS` cleanup option?

這`MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS`選項用於在郵件合併過程中刪除文件中沒有相應資料的區域。它透過刪除未使用的佔位符來幫助保持文件整潔。

### 我可以使用 Aspose.Words for Java 從文件中刪除空表行嗎？

是的，您可以透過設定從文件中刪除空白表格行`MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS`清理選項設定為 true。這將自動刪除任何不包含資料的表格行，確保文件中的表格結構良好。

### 當我設定時會發生什麼`REMOVE_CONTAINING_FIELDS` option?

設定`MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS`選項將在郵件合併過程中從文件中刪除整個合併字段，包括其包含的段落。當您想要消除合併欄位及其關聯文字時，這非常有用。

### 如何從文件中刪除未使用的合併欄位？

若要從文件中刪除未使用的合併字段，您可以設定`MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS`選項為真。這將自動消除郵件合併期間未填入的合併字段，從而產生更乾淨的文件。

### 有什麼區別`REMOVE_EMPTY_FIELDS` and `REMOVE_UNUSED_FIELDS` cleanup options?

這`REMOVE_EMPTY_FIELDS`選項會刪除郵件合併過程中沒有資料或為空的合併欄位。另一方面，`REMOVE_UNUSED_FIELDS`選項刪除合併期間未填入資料的合併欄位。它們之間的選擇取決於您是否要刪除沒有內容的欄位或特定合併操作中未使用的欄位。

### 如何刪除有標點符號的段落？

若要啟用刪除帶有標點符號的段落，您可以設定`cleanupParagraphsWithPunctuationMarks`選項設為 true 並指定要考慮清理的標點符號。這使您可以透過刪除不必要的僅標點符號段落來創建更精緻的文件。

### 我可以自訂 Aspose.Words for Java 中的清理選項嗎？

是的，您可以根據您的特定需求自訂清理選項。您可以選擇要套用的清理選項，並根據您的文件清理要求對其進行配置，以確保您的最終文件符合您所需的標準。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
