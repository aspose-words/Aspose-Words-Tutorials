---
title: 更改欄位更新文化來源
linktitle: 更改欄位更新文化來源
second_title: Aspose.Words 文件處理 API
description: 透過本指南了解如何變更 Aspose.Words for .NET 中的欄位更新區域性來源。輕鬆控制基於不同文化的日期格式。
weight: 10
url: /zh-hant/net/working-with-fields/change-field-update-culture-source/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 更改欄位更新文化來源

## 介紹

在本教程中，我們將深入了解 Aspose.Words for .NET 的世界，並探索如何變更欄位更新文化來源。如果您正在處理包含日期欄位的 Word 文檔，並且需要根據不同的文化控制這些日期的格式，那麼本指南適合您。讓我們逐步完成這個過程，確保您掌握每個概念並能夠在您的專案中有效地應用它。

## 先決條件

在我們開始編寫程式碼之前，請確保您具備以下條件：

-  Aspose.Words for .NET：您可以從以下位置下載它[這裡](https://releases.aspose.com/words/net/).
- 開發環境：任何.NET 相容的IDE（例如Visual Studio）。
- C# 基礎知識：本教學假設您對 C# 程式設計有基本的了解。

## 導入命名空間

首先，讓我們為我們的專案導入必要的命名空間。這將確保我們能夠存取 Aspose.Words 提供的所有必需的類別和方法。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

現在，讓我們將範例分解為多個步驟，以協助您了解如何變更 Aspose.Words for .NET 中的欄位更新區域性來源。

## 步驟1：初始化文檔

第一步是建立一個新的實例`Document`類別和一個`DocumentBuilder`。這為建置和操作 Word 文件奠定了基礎。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 步驟 2：插入具有特定區域設定的字段

接下來，我們需要將欄位插入文件中。對於本範例，我們將插入兩個日期欄位。我們將字體的區域設定設為德語 (LocaleId = 1031)，以示範文化如何影響日期格式。

```csharp
builder.Font.LocaleId = 1031; //德文
builder.InsertField("MERGEFIELD Date1 \\@ \"dddd, d MMMM yyyy\"");
builder.Write(" - ");
builder.InsertField("MERGEFIELD Date2 \\@ \"dddd, d MMMM yyyy\"");
```

## 步驟3：設定欄位更新文化來源

為了控制更新欄位時使用的區域性，我們設定`FieldUpdateCultureSource`的財產`FieldOptions`班級。此屬性決定區域性是從欄位程式碼還是從文件中取得。

```csharp
doc.FieldOptions.FieldUpdateCultureSource = FieldUpdateCultureSource.FieldCode;
```

## 第 4 步：執行郵件合併

我們現在需要執行郵件合併以使用實際資料填充欄位。在此範例中，我們將設定第二個日期欄位（`Date2`）至2011年1月1日。

```csharp
doc.MailMerge.Execute(new string[] { "Date2" }, new object[] { new DateTime(2011, 1, 1) });
```

## 第 5 步：儲存文檔

最後，我們將文檔儲存到指定的目錄中。此步驟完成更改欄位更新文化來源的過程。

```csharp
doc.Save(dataDir + "WorkingWithFields.ChangeFieldUpdateCultureSource.docx");
```

## 結論

現在你就擁有了！您已成功變更 Aspose.Words for .NET 中的欄位更新區域性來源。透過執行下列步驟，您可以確保 Word 文件根據指定的區域性設定顯示日期和其他欄位值。這在為國際受眾產生文件時特別有用。

## 常見問題解答

### 設定的目的是什麼`LocaleId`?
這`LocaleId`指定文字的區域性設置，這會影響日期和其他區域設定敏感資料的格式設定。

### 我可以使用德語以外的其他語言環境嗎？
是的，您可以設定`LocaleId`任何有效的區域設定標識符。例如，1033 代表英語（美國）。

### 如果我不設定會發生什麼`FieldUpdateCultureSource` property?
如果未設定此屬性，則更新欄位時將使用文件的預設區域性設定。

### 是否可以根據文檔的區域性而不是字段代碼來更新字段？
是的，你可以設定`FieldUpdateCultureSource`到`FieldUpdateCultureSource.Document`使用文件的區域性設定。

### 如何以不同的模式設定日期格式？
您可以變更日期格式模式`InsertField`方法透過修改`\\@`開關值。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
