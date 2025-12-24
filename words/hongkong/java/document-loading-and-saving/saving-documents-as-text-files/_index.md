---
date: 2025-12-24
description: 學習如何使用 Aspose.Words for Java 從 Word 文件建立純文字檔案。本指南示範如何將 Word 轉換為 txt、使用
  Tab 縮排，以及將 Word 儲存為 txt。
linktitle: Saving Documents as Text Files
second_title: Aspose.Words Java Document Processing API
title: 如何使用 Aspose.Words for Java 建立純文字檔案
url: /zh-hant/java/document-loading-and-saving/saving-documents-as-text-files/
weight: 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words for Java 建立純文字檔案

## 簡介：在 Aspose.Words for Java 中將文件儲存為文字檔案

在本教學中，您將學習 **如何建立純文字檔案**，從 Word 文件使用 Aspose.Words for Java 函式庫轉換。無論您需要 **convert word to txt**、自動化報告產生，或僅僅提取原始文字以供後續處理，本指南都會一步步帶您完成整個工作流程——從文件建立到微調儲存選項，例如 **use tab indentation** 或加入 bidi 標記。讓我們開始吧！

## 快速問答
- **建立文件的主要類別是什麼？** `Document` 來自 Aspose.Words。  
- **哪個選項會為從右至左語言加入 bidi 標記？** `TxtSaveOptions.setAddBidiMarks(true)`。  
- **如何使用 Tab 來縮排清單項目？** 將 `ListIndentation.Character` 設為 `'\t'`。  
- **開發時需要授權嗎？** 免費試用版可用於測試；正式環境需購買授權。  
- **我可以使用自訂的檔名與路徑儲存檔案嗎？** 可以——將完整路徑傳遞給 `doc.save()`。

## 先決條件

在開始之前，請確保您已具備以下條件：

- 已在系統上安裝 Java Development Kit (JDK)。  
- 已將 Aspose.Words for Java 函式庫整合至您的專案中。您可以從 [here](https://releases.aspose.com/words/java/) 下載。  
- 具備基本的 Java 程式設計知識。

## 步驟 1：建立文件

要 **save word as txt**，我們首先需要一個 `Document` 實例。以下是一段簡單的 Java 程式碼範例，建立文件並寫入幾行多語言文字：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

在此程式碼中，我們建立了一個新文件，加入英文、希伯來文與阿拉伯文文字，並為希伯來文段落啟用從右至左的格式。

## 步驟 2：定義文字儲存選項

接下來，我們設定文件將如何儲存為純文字檔。Aspose.Words 提供 `TxtSaveOptions` 類別，讓您可以從 bidi 標記到清單縮排全部掌控。

### 範例 1：加入 Bidi 標記（如何以正確的 RTL 支援儲存 txt）

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

將 `AddBidiMarks` 設為 `true` 可確保右至左字元在產生的 **純文字檔案** 中正確呈現。

### 範例 2：使用 Tab 字元作為清單縮排（使用 Tab 縮排）

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

此範例告訴 Aspose.Words 在每個清單層級前加上 Tab 字元 (`'\t'`)，使文字輸出更易閱讀。

## 步驟 3：將文件儲存為文字檔

現在儲存選項已設定完成，您可以將文件持久化為 **純文字檔案**：

```java
doc.save("output.txt", saveOptions);
```

將 `"output.txt"` 替換為您想要儲存檔案的完整路徑。

## 完整範例程式碼：在 Aspose.Words for Java 中將文件儲存為文字檔案

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
        // Create a list with three levels of indentation.
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
        // Create a list with three levels of indentation.
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

## 常見問題與解決方案

| 問題 | 解決方案 |
|-------|----------|
| **Bidi characters appear as garbled text** | 確保已啟用 `setAddBidiMarks(true)`，且以 UTF‑8 編碼開啟輸出檔案。 |
| **List indentation looks wrong** | 檢查 `ListIndentation.Count` 與 `Character` 是否設定為期望的值（Tab `'\t'` 或空格 `' '`）。 |
| **File not created** | 確認目錄路徑存在且應用程式具有寫入權限。 |

## 常見問答

### 如何在文字輸出中加入 bidi 標記？

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### 我可以自訂清單縮排字元嗎？

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Aspose.Words for Java 是否適合處理多語言文字？

是的，Aspose.Words for Java 支援廣泛的語言與字元編碼，適合將多語言內容提取並儲存為純文字。

### 如何取得更多 Aspose.Words for Java 的文件與資源？

您可於 Aspose.Words for Java 文件頁面找到完整的說明與資源：[Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/)。

### 哪裡可以下載 Aspose.Words for Java？

您可從官方網站下載函式庫：[Download Aspose.Words for Java](https://releases.aspose.com/words/java/)。

### 如果需要在批次處理中 **convert word to txt** 該怎麼做？

將上述程式碼包在迴圈中，載入每個 `.docx` 檔案，套用相同的 `TxtSaveOptions`，並儲存為 `.txt`。請確保在每次迭代後釋放 `Document` 物件以管理資源。

### API 是否支援直接儲存至串流而非檔案？

是的，您可以將 `OutputStream` 傳遞給 `doc.save(outputStream, saveOptions)`，以進行記憶體內處理或與 Web 服務整合。

---

**最後更新：** 2025-12-24  
**測試版本：** Aspose.Words for Java 24.12（最新）  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}