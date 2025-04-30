---
"description": "了解如何使用 Aspose.Words for Java 產生和自訂目錄 (TOC)。輕鬆建立有條理且專業的文件。"
"linktitle": "生成目錄"
"second_title": "Aspose.Words Java文件處理API"
"title": "在 Aspose.Words for Java 中產生目錄"
"url": "/zh-hant/java/document-manipulation/generating-table-of-contents/"
"weight": 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中產生目錄


## Aspose.Words for Java 中目錄產生簡介

在本教學中，我們將引導您完成使用 Aspose.Words for Java 產生目錄 (TOC) 的過程。 TOC 是建立有組織的文件的關鍵功能。我們將介紹如何自訂目錄的外觀和佈局。

## 先決條件

在開始之前，請確保您已在 Java 專案中安裝並設定了 Aspose.Words for Java。

## 步驟 1：建立新文檔

首先，讓我們建立一個新的文件。

```java
Document doc = new Document();
```

## 第 2 步：自訂目錄樣式

若要自訂目錄的外觀，您可以修改與其相關的樣式。在此範例中，我們將使第一級目錄條目變為粗體。

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

## 步驟 3：為文件新增內容

您可以將您的內容新增至文件。此內容將用於產生目錄。

## 步驟 4：生成目錄

若要產生目錄，請在文件中的所需位置插入目錄欄位。此欄位將根據文件中的標題和樣式自動填入。

```java
// 在文件的所需位置插入目錄欄位。
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

## 步驟5：儲存文檔

最後，將文檔與目錄一起儲存。

```java
doc.save("your_output_path_here");
```

## 自訂目錄中的製表位

您也可以自訂目錄中的製表位來控制頁碼的佈局。更改製表位的方法如下：

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // 取得本段落使用的第一個製表符，用於對齊頁碼。
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // 刪除舊標籤。
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // 在修改的位置插入一個新標籤（例如，向左 50 個單位）。
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

現在，您的文件中已經有了自訂的目錄，其中的製表位已調整以便頁碼對齊。


## 結論

在本教學中，我們探討如何使用 Aspose.Words for Java（一個用於處理 Word 文件的強大函式庫）來產生目錄 (TOC)。結構良好的目錄對於組織和瀏覽長篇文件至關重要，而 Aspose.Words 提供了輕鬆建立和自訂目錄的工具。

## 常見問題解答

### 如何變更目錄條目的格式？

您可以使用以下方式修改與目錄層級相關的樣式 `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`，其中 X 是 TOC 水準。

### 如何為我的目錄添加更多層級？

若要在目錄中包含更多級別，您可以修改目錄欄位並指定所需的級別數。

### 我可以更改特定目錄條目的製表位位置嗎？

是的，如上面的程式碼範例所示，您可以透過遍歷段落並相應地修改製表位來更改特定目錄條目的製表位位置。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}