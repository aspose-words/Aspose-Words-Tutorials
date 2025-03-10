---
title: 在 Aspose.Words for Java 中將文件儲存為文字文件
linktitle: 將文件儲存為文字文件
second_title: Aspose.Words Java 文件處理 API
description: 了解如何在 Aspose.Words for Java 中將文件儲存為文字檔案。請按照我們的 Java 程式碼範例逐步指南進行操作。
weight: 24
url: /zh-hant/java/document-loading-and-saving/saving-documents-as-text-files/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中將文件儲存為文字文件


## 在 Aspose.Words for Java 中將文件儲存為文字檔案簡介

在本教學中，我們將探討如何使用 Aspose.Words for Java 函式庫將文件儲存為文字檔。 Aspose.Words 是一個功能強大的 Java API，用於處理 Word 文檔，它提供了多種選項來保存不同格式的文檔，包括純文字。我們將介紹實現此目標的步驟並提供範例 Java 程式碼。

## 先決條件

在我們開始之前，請確保您具備以下先決條件：

- 您的系統上安裝了 Java 開發工具包 (JDK)。
-  Aspose.Words for Java 函式庫整合到您的專案中。您可以從以下位置下載：[這裡](https://releases.aspose.com/words/java/).
- Java 程式設計的基礎知識。

## 第 1 步：建立文檔

要將文件儲存為文字文件，我們首先需要使用 Aspose.Words 建立一個文件。以下是一個簡單的 Java 程式碼片段，用於建立包含某些內容的文件：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

在此程式碼中，我們建立一個新文件並在其中添加一些文本，包括不同語言的文本。

## 第 2 步：定義文字儲存選項

接下來，我們需要定義文字儲存選項，指定如何將文件儲存為文字檔案。我們可以配置各種設置，例如新增雙向標記、清單縮排等等。讓我們來看兩個例子：

### 範例 1：新增 Bidi 標記

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

在這個例子中，我們創建一個`TxtSaveOptions`對象並設定`AddBidiMarks`財產給`true`在文字輸出中包含 bidi 標記。

### 範例 2：使用製表符進行清單縮排

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

在這裡，我們配置保存選項以使用製表符進行列表縮進，計數為 1。

## 步驟 3：將文件另存為文字

現在我們已經定義了文字儲存選項，我們可以將文件儲存為文字檔案。以下程式碼示範如何執行此操作：

```java
doc.save("output.txt", saveOptions);
```

代替`"output.txt"`以及要儲存文字檔案的所需檔案路徑。

## 在 Aspose.Words for Java 中將文件儲存為文字檔案的完整原始碼

```java
    public void addBidiMarks() throws Exception
    {        
		Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.writeln("Hello world!");
        builder.getParagraphFormat().setBidi(true);
        builder.writeln("שלום עולם!");
        builder.writeln("مرحبا بالعالم!");
        TxtSaveOptions saveOptions = new TxtSaveOptions(); { saveOptions.setAddBidiMarks(true); }
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
    }
    @Test
    public void useTabCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        //建立一個具有三級縮排的清單。
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(1);
        saveOptions.getListIndentation().setCharacter('\t');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseTabCharacterPerLevelForListIndentation.txt", saveOptions);
    }
    @Test
    public void useSpaceCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        //建立一個具有三級縮排的清單。
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(3);
        saveOptions.getListIndentation().setCharacter(' ');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
	}
```

## 結論

在本教學中，我們學習如何在 Aspose.Words for Java 中將文件儲存為文字檔。我們介紹了建立文件、定義文字儲存選項以及以文字格式儲存文件的步驟。 Aspose.Words 在保存文件方面提供了廣泛的靈活性，可讓您根據您的特定要求自訂輸出。

## 常見問題解答

### 如何將 Bidi 標記新增至文字輸出？

若要將 Bidi 標記新增至文字輸出，請設定`AddBidiMarks`的財產`TxtSaveOptions`到`true`。例如：

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### 我可以自訂清單縮排字元嗎？

是的，您可以透過配置來自訂清單來縮排字符`ListIndentation`的財產`TxtSaveOptions`。例如，要使用製表符進行清單縮進，您可以執行下列操作：

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Aspose.Words for Java 適合處理多語言文字嗎？

是的，Aspose.Words for Java 適合處理多語言文字。它支援各種語言和字元編碼，使其成為處理不同語言文件的多功能選擇。

### 如何存取 Aspose.Words for Java 的更多文件和資源？

您可以在 Aspose 文件網站上找到 Aspose.Words for Java 的全面文件和資源：[Aspose.Words for Java 文檔](https://reference.aspose.com/words/java/).

### 哪裡可以下載 Aspose.Words for Java？

您可以從 Aspose 網站下載 Aspose.Words for Java 程式庫：[下載 Java 版 Aspose.Words](https://releases.aspose.com/words/java/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
