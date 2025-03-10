---
title: 使用 Ole 套件在 Word 中插入 Ole 對象
linktitle: 使用 Ole 套件在 Word 中插入 Ole 對象
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 在 Word 文件中插入 OLE 物件。按照我們詳細的逐步指南無縫嵌入文件。
weight: 10
url: /zh-hant/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Ole 套件在 Word 中插入 Ole 對象

## 介紹

如果您曾經想將文件嵌入到 Word 文件中，那麼您來對地方了。無論是 ZIP 檔案、Excel 工作表或任何其他文件類型，將其直接嵌入到 Word 文件中都非常有用。可以將其想像為在您的文件中設置一個秘密隔間，您可以在其中存放各種寶藏。今天，我們將介紹如何使用 Aspose.Words for .NET 來完成此操作。準備好成為 Word 奇才了嗎？讓我們深入了解吧！

## 先決條件

在我們開始之前，請確保您具備以下條件：

1. Aspose.Words for .NET：如果您還沒有下載，請從[這裡](https://releases.aspose.com/words/net/).
2. 開發環境：Visual Studio 或任何其他 .NET 開發環境。
3. 對 C# 的基本了解：您不需要成為專家，但了解 C# 的方法會有所幫助。
4. 文件目錄：您可以在其中儲存和檢索文件的資料夾。

## 導入命名空間

首先，讓我們按順序排列命名空間。您需要在專案中包含以下命名空間：

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
```

讓我們將其分解為幾個小步驟，這樣就很容易遵循。

## 第 1 步：設定您的文檔

想像一下，您是一位擁有空白畫布的藝術家。首先，我們需要空白畫布，即 Word 文件。設定方法如下：

```csharp
//文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

此程式碼初始化一個新的 Word 文件並設定一個 DocumentBuilder，我們將使用它向文件中插入內容。

## 第 2 步：讀取 Ole 對象

接下來，讓我們讀取要嵌入的檔案。把這想像成撿起你想藏在秘密隔間裡的寶藏：

```csharp
byte[] bs = File.ReadAllBytes(dataDir + "Zip file.zip");
```

此行從 ZIP 檔案中讀取所有位元組並將它們儲存在位元組數組中。

## 第 3 步：插入 Ole 對象

現在到了神奇的部分。我們要將文件嵌入到 Word 文件中：

```csharp
using (Stream stream = new MemoryStream(bs))
{
    Shape shape = builder.InsertOleObject(stream, "Package", true, null);
    OlePackage olePackage = shape.OleFormat.OlePackage;
    olePackage.FileName = "filename.zip";
    olePackage.DisplayName = "displayname.zip";
}
```

在這裡，我們從位元組數組創建一個記憶體流並使用`InsertOleObject`方法將其嵌入到文件中。我們也設定嵌入物件的檔案名稱和顯示名稱。

## 第 4 步：儲存您的文檔

最後，讓我們保存我們的傑作：

```csharp
doc.Save(dataDir + "WorkingWithOleObjectsAndActiveX.InsertOleObjectWithOlePackage.docx");
```

這會將文件與嵌入文件一起保存在指定目錄中。

## 結論

現在你就擁有了！您已使用 Aspose.Words for .NET 成功將 OLE 物件嵌入到 Word 文件中。這就像在文件中添加一顆隱藏的寶石，可以隨時揭開面紗。該技術對於從技術文件到動態報告的各種應用都非常有用。 

## 常見問題解答

### 我可以使用此方法嵌入其他文件類型嗎？
是的，您可以嵌入各種文件類型，例如 Excel 工作表、PDF 和圖像。

### 我需要 Aspose.Words 授權嗎？
是的，您需要有效的許可證。你可以獲得一個[臨時執照](https://purchase.aspose.com/temporary-license/)進行評估。

### 如何自訂 OLE 物件的顯示名稱？
您可以設定`DisplayName`的財產`OlePackage`來定制它。

### Aspose.Words 與 .NET Core 相容嗎？
是的，Aspose.Words 支援 .NET Framework 和 .NET Core。

### 我可以編輯 Word 文件中嵌入的 OLE 物件嗎？
不可以，您不能直接在 Word 中編輯 OLE 物件。您需要在其本機應用程式中開啟它。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
