---
title: 在 Aspose.Words for Java 中將文件分割為 HTML 頁面
linktitle: 將文檔拆分為 HTML 頁面
second_title: Aspose.Words Java 文件處理 API
description: 了解如何使用 Aspose.Words for Java 將文件分割為 HTML 頁面。請按照我們的逐步指南進行無縫文件轉換。
weight: 25
url: /zh-hant/java/document-manipulation/splitting-documents-into-html-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中將文件分割為 HTML 頁面


## 在 Aspose.Words for Java 中將文件分割為 HTML 頁面簡介

在本逐步指南中，我們將探討如何使用 Aspose.Words for Java 將文件分割為 HTML 頁面。 Aspose.Words 是一個強大的 Java API，用於處理 Microsoft Word 文檔，它提供了廣泛的文檔操作功能，包括將文檔轉換為各種格式（包括 HTML）的能力。

## 先決條件

在我們開始之前，請確保您具備以下先決條件：

- 您的系統上安裝了 Java 開發工具包 (JDK)。
-  Aspose.Words for Java 函式庫。您可以從以下位置下載：[這裡](https://releases.aspose.com/words/java/).

## 步驟1：導入必要的套件

```java
import com.aspose.words.*;
import java.io.*;
import java.util.ArrayList;
```

## 步驟 2：建立 Word 到 HTML 轉換的方法

```java
class WordToHtmlConverter
{
    //Word 到 HTML 轉換的實作細節。
    //…
}
```

## 步驟 3：選擇標題段落作為主題開始

```java
private ArrayList<Paragraph> selectTopicStarts()
{
    NodeCollection paras = mDoc.getChildNodes(NodeType.PARAGRAPH, true);
    ArrayList<Paragraph> topicStartParas = new ArrayList<Paragraph>();
    for (Paragraph para : (Iterable<Paragraph>) paras)
    {
        int style = para.getParagraphFormat().getStyleIdentifier();
        if (style == StyleIdentifier.HEADING_1)
            topicStartParas.add(para);
    }
    return topicStartParas;
}
```

## 步驟 4：在標題段落前插入分節符

```java
private void insertSectionBreaks(ArrayList<Paragraph> topicStartParas)
{
    DocumentBuilder builder = new DocumentBuilder(mDoc);
    for (Paragraph para : topicStartParas)
    {
        Section section = para.getParentSection();
        if (para != section.getBody().getFirstParagraph())
        {
            builder.moveTo(para.getFirstChild());
            builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
            section.getBody().getLastParagraph().remove();
        }
    }
}
```

## 第 5 步：將文件拆分為主題

```java
private ArrayList<Topic> saveHtmlTopics() throws Exception
{
    ArrayList<Topic> topics = new ArrayList<Topic>();
    for (int sectionIdx = 0; sectionIdx < mDoc.getSections().getCount(); sectionIdx++)
    {
        Section section = mDoc.getSections().get(sectionIdx);
        String paraText = section.getBody().getFirstParagraph().getText();
        String fileName = makeTopicFileName(paraText);
        if ("".equals(fileName))
            fileName = "UNTITLED SECTION " + sectionIdx;
        fileName = mDstDir + fileName + ".html";
        String title = makeTopicTitle(paraText);
        if ("".equals(title))
            title = "UNTITLED SECTION " + sectionIdx;
        Topic topic = new Topic(title, fileName);
        topics.add(topic);
        saveHtmlTopic(section, topic);
    }
    return topics;
}
```

## 第 6 步：將每個主題儲存為 HTML 文件

```java
private void saveHtmlTopic(Section section, Topic topic) throws Exception
{
    Document dummyDoc = new Document();
    dummyDoc.removeAllChildren();
    dummyDoc.appendChild(dummyDoc.importNode(section, true, ImportFormatMode.KEEP_SOURCE_FORMATTING));
    dummyDoc.getBuiltInDocumentProperties().setTitle(topic.getTitle());
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    {
        saveOptions.setPrettyFormat(true);
        saveOptions.setAllowNegativeIndent(true);
        saveOptions.setExportHeadersFootersMode(ExportHeadersFootersMode.NONE);
    }
    dummyDoc.save(topic.getFileName(), saveOptions);
}
```

## 第 7 步：產生主題目錄

```java
private void saveTableOfContents(ArrayList<Topic> topics) throws Exception
{
    Document tocDoc = new Document(mTocTemplate);
    tocDoc.getMailMerge().setFieldMergingCallback(new HandleTocMergeField());
    tocDoc.getMailMerge().executeWithRegions(new TocMailMergeDataSource(topics));
    tocDoc.save(mDstDir + "contents.html");
}
```

現在我們已經概述了這些步驟，您可以在 Java 專案中實作每個步驟，以使用 Aspose.Words for Java 將文件分割為 HTML 頁面。此過程將允許您建立文件的結構化 HTML 表示形式，使它們更易於存取和用戶友好。

## 結論

在本綜合指南中，我們介紹了使用 Aspose.Words for Java 將文件分割為 HTML 頁面的過程。透過執行概述的步驟，您可以有效地將 Word 文件轉換為 HTML 格式，使您的內容在網路上更易於存取。

## 常見問題解答

### 如何安裝 Aspose.Words for Java？

要安裝 Aspose.Words for Java，您可以從以下位置下載該程式庫：[這裡](https://releases.aspose.com/words/java/)並按照文件中提供的安裝說明進行操作。

### 我可以自訂 HTML 輸出嗎？

是的，您可以透過調整儲存選項來自訂 HTML 輸出`HtmlSaveOptions`班級。這允許您控制生成的 HTML 文件的格式和外觀。

### Aspose.Words for Java 支援哪些版本的 Microsoft Word？

Aspose.Words for Java 支援多種 Microsoft Word 文件格式，包括 DOC、DOCX、RTF 等。它與 Microsoft Word 的各個版本相容。

### 如何處理轉換後的 HTML 中的圖片？

Aspose.Words for Java 可以透過將轉換後的 HTML 中的圖片儲存為與 HTML 檔案相同的資料夾中的單獨檔案來處理這些映像。這可確保圖像在 HTML 輸出中正確顯示。

### 是否有 Aspose.Words for Java 的試用版？

是的，您可以在購買授權之前從 Aspose 網站請求 Aspose.Words for Java 的免費試用版來評估其特性和功能。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
