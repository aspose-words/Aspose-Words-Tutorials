---
"description": "透過本指南了解如何在 Aspose.Words for .NET 中變更欄位更新文化來源。輕鬆控制基於不同文化的日期格式。"
"linktitle": "更改欄位更新文化來源"
"second_title": "Aspose.Words文件處理API"
"title": "更改欄位更新文化來源"
"url": "/zh-hant/net/working-with-fields/change-field-update-culture-source/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 更改欄位更新文化來源

## 介紹

在本教程中，我們將深入了解 Aspose.Words for .NET 的世界，並探索如何變更欄位更新文化來源。如果您正在處理包含日期欄位的 Word 文檔，並且需要根據不同的文化來控制這些日期的格式，那麼本指南適合您。讓我們逐步介紹整個過程，確保您掌握每個概念並能夠在您的專案中有效地應用它。

## 先決條件

在我們進入程式碼之前，請確保您具有以下內容：

- Aspose.Words for .NET：您可以從 [這裡](https://releases。aspose.com/words/net/).
- 開發環境：任何與 .NET 相容的 IDE（例如 Visual Studio）。
- C# 基礎知識：本教學假設您對 C# 程式設計有基本的了解。

## 導入命名空間

首先，讓我們匯入專案所需的命名空間。這將確保我們可以存取 Aspose.Words 提供的所有必要的類別和方法。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

現在，讓我們將範例分解為多個步驟，以幫助您了解如何在 Aspose.Words for .NET 中變更欄位更新文化來源。

## 步驟 1：初始化文檔

第一步是建立一個新的實例 `Document` 類別和一個 `DocumentBuilder`。這為建立和操作我們的 Word 文件奠定了基礎。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 步驟 2：插入具有特定語言環境的字段

接下來，我們需要在文檔中插入欄位。對於此範例，我們將插入兩個日期欄位。我們將字體的區域設定設為德語（LocaleId = 1031）以示範文化如何影響日期格式。

```csharp
builder.Font.LocaleId = 1031; // 德文
builder.InsertField("MERGEFIELD Date1 \\@ \"dddd, d MMMM yyyy\"");
builder.Write(" - ");
builder.InsertField("MERGEFIELD Date2 \\@ \"dddd, d MMMM yyyy\"");
```

## 步驟3：設定欄位更新文化來源

為了控制更新字段時使用的文化，我們設置 `FieldUpdateCultureSource` 的財產 `FieldOptions` 班級。此屬性決定文化是從欄位程式碼還是文件中取得。

```csharp
doc.FieldOptions.FieldUpdateCultureSource = FieldUpdateCultureSource.FieldCode;
```

## 步驟 4：執行郵件合併

我們現在需要執行郵件合併來用實際資料填充欄位。在此範例中，我們將設定第二個日期欄位（`Date2`）至2011年1月1日。

```csharp
doc.MailMerge.Execute(new string[] { "Date2" }, new object[] { new DateTime(2011, 1, 1) });
```

## 步驟5：儲存文檔

最後我們將文檔儲存到指定的目錄。這一步驟完成了欄位更新文化來源的變更過程。

```csharp
doc.Save(dataDir + "WorkingWithFields.ChangeFieldUpdateCultureSource.docx");
```

## 結論

就是這樣！您已成功變更 Aspose.Words for .NET 中的欄位更新文化來源。透過遵循這些步驟，您可以確保您的 Word 文件根據指定的文化設定顯示日期和其他欄位值。這在為國際受眾產生文件時特別有用。

## 常見問題解答

### 設立的目的是什麼 `LocaleId`？
這 `LocaleId` 指定文字的文化設置，這會影響日期和其他區域敏感資料的格式。

### 我可以使用德語以外的其他語言環境嗎？
是的，您可以設定 `LocaleId` 任何有效的語言環境標識符。例如，1033 代表英語（美國）。

### 如果我不設定 `FieldUpdateCultureSource` 財產？
如果未設定此屬性，則更新欄位時將使用文件的預設文化設定。

### 是否可以根據文檔的文化而不是字段代碼來更新字段？
是的，你可以設定 `FieldUpdateCultureSource` 到 `FieldUpdateCultureSource.Document` 使用文檔的文化設定。

### 如何以不同的模式格式化日期？
您可以在 `InsertField` 方法透過修改 `\\@` 開關值。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}