---
title: 在 Aspose.Words for Java 中使用修訂版
linktitle: 使用修訂版
second_title: Aspose.Words Java 文件處理 API
description: 學習有效率地使用Aspose.Words for Java 的修訂版。開發人員的分步指南。優化您的文件管理。
weight: 22
url: /zh-hant/java/using-document-elements/using-revisions/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中使用修訂版


如果您是一位希望處理文件並需要實施修訂控制的 Java 開發人員，Aspose.Words for Java 提供了一組強大的工具來幫助您有效地管理修訂。在本教程中，我們將指導您逐步使用 Aspose.Words for Java 中的修訂版。 

## 1.Aspose.Words for Java簡介

Aspose.Words for Java 是一個強大的 Java API，可讓您建立、修改和操作 Word 文檔，而無需 Microsoft Word。當您需要在文件中進行修訂時，它特別有用。

## 2. 設定您的開發環境

在我們深入使用 Aspose.Words for Java 之前，您需要設定您的開發環境。確保您安裝了必要的 Java 開發工具和 Aspose.Words for Java 程式庫。

## 3. 建立新文檔

讓我們先使用 Aspose.Words for Java 建立一個新的 Word 文件。您可以這樣做：

```java
string outPath = "Your Output Directory";
Document doc = new Document();
Body body = doc.getFirstSection().getBody();
Paragraph para = body.getFirstParagraph();
```

## 4.向文件添加內容

現在您有了一個空白文檔，您可以向其中添加內容。在此範例中，我們將新增三個段落：

```java
para.appendChild(new Run(doc, "Paragraph 1. "));
body.appendParagraph("Paragraph 2. ");
body.appendParagraph("Paragraph 3. ");
```

## 5. 開始修訂跟踪

若要追蹤文件中的修訂，您可以使用以下程式碼：

```java
doc.startTrackRevisions("John Doe", new Date());
```

## 6. 修改

讓我們修改一下，再補充一段：

```java
para = body.appendParagraph("Paragraph 4. ");
```

## 7. 接受和拒絕修改

您可以使用 Aspose.Words for Java 接受或拒絕文件中的修訂。產生文件後，可以在 Microsoft Word 中輕鬆管理修訂。

## 8. 停止修訂跟踪

若要停止追蹤修訂，請使用以下代碼：

```java
doc.stopTrackRevisions();
```

## 9. 儲存文檔

最後，儲存您的文件：

```java
doc.save(outPath + "WorkingWithRevisions.AcceptRevisions.docx");
```

## 10. 結論

在本教程中，我們介紹了在 Aspose.Words for Java 中使用修訂版的基礎知識。您已了解如何建立文件、新增內容、啟動和停止修訂追蹤以及儲存文件。

現在，您擁有了使用 Aspose.Words for Java 有效管理 Java 應用程式中的修訂所需的工具。

## 完整的原始碼
```java
string outPath = "Your Output Directory";
Document doc = new Document();
Body body = doc.getFirstSection().getBody();
Paragraph para = body.getFirstParagraph();
//將文字新增到第一個段落，然後再新增兩個段落。
para.appendChild(new Run(doc, "Paragraph 1. "));
body.appendParagraph("Paragraph 2. ");
body.appendParagraph("Paragraph 3. ");
//我們有三個段落，其中沒有一個被註冊為任何類型的修訂
//如果我們在追蹤修訂時新增/刪除文件中的任何內容，
//它們將在文件中顯示並可以接受/拒絕。
doc.startTrackRevisions("John Doe", new Date());
//本段是修訂版，並將設定對應的「IsInsertRevision」標誌。
para = body.appendParagraph("Paragraph 4. ");
Assert.assertTrue(para.isInsertRevision());
//取得文件的段落集合並刪除段落。
ParagraphCollection paragraphs = body.getParagraphs();
Assert.assertEquals(4, paragraphs.getCount());
para = paragraphs.get(2);
para.remove();
//由於我們正在追蹤修訂，該段落仍然存在於文件中，將設定“IsDeleteRevision”
//並將在 Microsoft Word 中顯示為修訂版本，直到我們接受或拒絕所有修訂版本。
Assert.assertEquals(4, paragraphs.getCount());
Assert.assertTrue(para.isDeleteRevision());
//一旦我們接受更改，刪除修訂段落就會被刪除。
doc.acceptAllRevisions();
Assert.assertEquals(3, paragraphs.getCount());
Assert.assertEquals(para.getRuns().getCount(), 0); //是 Is.Empty
//停止追蹤修訂會使該文字顯示為普通文字。
//文件變更時不計算修訂版本。
doc.stopTrackRevisions();
//儲存文檔。
doc.save(outPath + "WorkingWithRevisions.AcceptRevisions.docx");
  
```

## 常見問題解答

### 1. 我可以將 Aspose.Words for Java 與其他程式語言一起使用嗎？

不，Aspose.Words for Java 是專為 Java 開發而設計的。

### 2. Aspose.Words for Java 是否與所有版本的 Microsoft Word 相容？

是的，Aspose.Words for Java 旨在與各種版本的 Microsoft Word 相容。

### 3. 我可以追蹤現有 Word 文件的修訂嗎？

是的，您可以使用 Aspose.Words for Java 來追蹤現有 Word 文件中的修訂。

### 4. 使用 Aspose.Words for Java 有任何授權要求嗎？

是的，您需要獲得許可證才能在專案中使用 Aspose.Words for Java。你可以[在這裡獲取許可證](https://purchase.aspose.com/buy).

### 5. 在哪裡可以找到 Aspose.Words for Java 的支援？

如有任何疑問或問題，您可以訪問[Aspose.Words for Java 支援論壇](https://forum.aspose.com/).

立即開始使用 Aspose.Words for Java 並簡化您的文件管理流程。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
