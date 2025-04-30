---
"description": "了解如何使用 Aspose.Words for Java 從 DataTable 產生表。輕鬆建立具有格式化表格的專業 Word 文件。"
"linktitle": "從資料表產生表"
"second_title": "Aspose.Words Java文件處理API"
"title": "從資料表產生表"
"url": "/zh-hant/java/table-processing/generate-table-from-datatable/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 從資料表產生表

## 介紹

從資料來源動態建立表格是許多應用程式中的常見任務。無論您產生的是報告、發票還是資料摘要，能夠以程式設計方式填入表格中的資料可以為您節省大量時間和精力。在本教程中，我們將探討如何使用 Aspose.Words for Java 從 DataTable 產生表。我們將把流程分解為易於管理的步驟，確保您清楚地了解每個部分。

## 先決條件

在深入研究程式碼之前，請確保您已準備好開始所需的一切：

1. Java 開發工具包 (JDK)：確保您的機器上安裝了 JDK。您可以從 [Oracle 網站](https://www。oracle.com/java/technologies/javase-jdk11-downloads.html).
   
2. Java 的 Aspose.Words：您將需要 Aspose.Words 函式庫。您可以從 [Aspose 的發佈頁面](https://releases。aspose.com/words/java/).

3. IDE：像 IntelliJ IDEA 或 Eclipse 這樣的整合開發環境 (IDE) 將使編碼變得更容易。

4. Java 基礎：熟悉 Java 程式設計概念將幫助您更好地理解程式碼片段。

5. 範例資料：在本教學中，我們將使用名為「List of people.xml」的 XML 檔案來模擬資料來源。您可以使用範例資料建立此文件進行測試。

## 步驟 1：建立新文檔

首先，我們需要建立一個新文件來放置我們的表格。這是我們工作的畫布。

```java
Document doc = new Document();
```

在這裡，我們實例化一個新的 `Document` 目的。這將作為我們建立表格的工作文件。

## 步驟2：初始化DocumentBuilder

接下來，我們將使用 `DocumentBuilder` 類，它使我們能夠更輕鬆地操作文件。

```java
DocumentBuilder builder = new DocumentBuilder(doc);
```

這 `DocumentBuilder` 物件提供將表格、文字和其他元素插入文件的方法。

## 步驟 3：設定頁面方向

由於我們預計表格會很寬，因此我們將頁面方向設為橫向。

```java
doc.getFirstSection().getPageSetup().setOrientation(Orientation.LANDSCAPE);
```

這一步至關重要，因為它可以確保我們的表格很好地適合頁面而不會被切斷。

## 步驟 4：從 XML 載入數據

現在，我們需要將資料從 XML 檔案載入到 `DataTable`。這就是我們的數據來源。

```java
DataSet ds = new DataSet();
ds.readXml(getMyDir() + "List of people.xml");
DataTable dataTable = ds.getTables().get(0);
```

在這裡，我們讀取 XML 檔案並從資料集中檢索第一個表。這 `DataTable` 將保存我們想要在文件中顯示的資料。

## 步驟 5：從 DataTable 匯入表

現在到了令人興奮的部分：將我們的資料作為表格匯入文件。

```java
Table table = importTableFromDataTable(builder, dataTable, true);
```

我們稱該方法為 `importTableFromDataTable`，透過 `DocumentBuilder`， 我們的 `DataTable`，以及一個布林值來指示是否包含列標題。

## 步驟 6：設定表格樣式

一旦我們有了表格，我們就可以應用一些樣式讓它看起來更美觀。

```java
table.setStyleIdentifier(StyleIdentifier.MEDIUM_LIST_2_ACCENT_1);
table.setStyleOptions(TableStyleOptions.FIRST_ROW | TableStyleOptions.ROW_BANDS | TableStyleOptions.LAST_COLUMN);
```

此程式碼將預定義樣式應用於表格，增強了其視覺吸引力和可讀性。

## 步驟 7：刪除不需要的儲存格

如果您有任何不想顯示的列，例如圖像列，您可以輕鬆地將其刪除。

```java
table.getFirstRow().getLastCell().removeAllChildren();
```

此步驟可確保我們的表格僅顯示相關資訊。

## 步驟8：儲存文檔

最後，我們將生成的表格儲存到文件中。

```java
doc.save(getArtifactsDir() + "WorkingWithTables.BuildTableFromDataTable.docx");
```

此行將文件保存在指定的目錄中，以便您查看結果。

## importTableFromDataTable 方法

讓我們仔細看看 `importTableFromDataTable` 方法。該方法負責創建表結構並用資料填充它。

### 步驟 1：啟動表格

首先，我們需要在文件中開始一個新表格。

```java
Table table = builder.startTable();
```

這將在我們的文件中初始化一個新表。

### 第 2 步：新增列標題

如果我們想包含列標題，我們檢查 `importColumnHeadings` 旗幟。

```java
if (importColumnHeadings) {
    // 儲存原始格式
    boolean boldValue = builder.getFont().getBold();
    int paragraphAlignmentValue = builder.getParagraphFormat().getAlignment();

    // 設定標題格式
    builder.getFont().setBold(true);
    builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

    // 插入列名稱
    for (DataColumn column : dataTable.getColumns()) {
        builder.insertCell();
        builder.writeln(column.getColumnName());
    }

    builder.endRow();

    // 恢復原始格式
    builder.getFont().setBold(boldValue);
    builder.getParagraphFormat().setAlignment(paragraphAlignmentValue);
}
```

此程式碼區塊格式化標題行並插入來自 `DataTable`。

### 步驟 3：用資料填入表

現在，我們循環遍歷 `DataTable` 將資料插入表中。

```java
for (DataRow dataRow : (Iterable<DataRow>) dataTable.getRows()) {
    for (Object item : dataRow.getItemArray()) {
        builder.insertCell();
        switch (item.getClass().getName()) {
            case "DateTime":
                Date dateTime = (Date) item;
                SimpleDateFormat simpleDateFormat = new SimpleDateFormat("MMMM d, yyyy");
                builder.write(simpleDateFormat.format(dateTime));
                break;
            default:
                builder.write(item.toString());
                break;
        }
    }
    builder.endRow();
}
```

在本節中，我們將處理不同的資料類型，適當地格式化日期，同時將其他資料插入為文字。

### 步驟 4：結束表格

最後，一旦所有資料都插入完畢，我們就完成了表格。

```java
builder.endTable();
```

這條線標誌著我們表格的結束，允許 `DocumentBuilder` 知道我們已經完成了這一部分。

## 結論

就是這樣！您已成功學習如何使用 Aspose.Words for Java 從 DataTable 產生表。透過遵循這些步驟，您可以輕鬆地根據各種資料來源在文件中建立動態表格。無論您產生報告還是發票，此方法都會簡化您的工作流程並增強您的文件建立流程。

## 常見問題解答

### 什麼是 Aspose.Words for Java？
Aspose.Words for Java 是一個功能強大的程式庫，用於以程式設計方式建立、操作和轉換 Word 文件。

### 我可以免費使用 Aspose.Words 嗎？
是的，Aspose 提供免費試用版。您可以從下載 [這裡](https://releases。aspose.com/).

### 如何在 Aspose.Words 中設定表格樣式？
您可以使用庫提供的預先定義樣式標識符和選項來套用樣式。

### 我可以將哪些類型的資料插入表中？
您可以插入各種資料類型，包括文字、數字和日期，並可以相應地設定格式。

### 我可以在哪裡獲得 Aspose.Words 的支援？
您可以在 [Aspose 論壇](https://forum。aspose.com/c/words/8/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}