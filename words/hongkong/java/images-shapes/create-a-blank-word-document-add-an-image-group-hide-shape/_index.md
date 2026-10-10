---
category: general
date: 2026-10-10
description: 建立一個空白的 Word 文件，將圖片插入 Word，新增圖片群組，並在儲存的檔案中隱藏形狀。請遵循此一步一步的指南。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert image into word
- add image group
- hide shape word document
language: zh-hant
lastmod: 2026-10-10
og_description: 建立一個空白的 Word 文件，將圖片插入 Word，新增圖片群組，並隱藏形狀。本指南展示完整的 C# 程式碼。
og_image_alt: Screenshot of a blank Word document with a hidden image group
og_title: 建立一個空白的 Word 文件，加入圖片群組，隱藏形狀
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Create a blank Word document, insert image into Word, add an image
    group, and hide shape in the saved file. Follow this step‑by‑step guide.
  headline: Create a blank Word document, add an image group, hide shape
  type: TechArticle
tags:
- Word automation
- Aspose.Words
- C#
- Document processing
title: 建立空白 Word 文件，加入圖片群組，隱藏形狀
url: /zh-hant/java/images-shapes/create-a-blank-word-document-add-an-image-group-hide-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立空白 Word 文件、加入圖片群組、隱藏圖形

如果您需要 **建立空白 Word 文件** 並在之後隱藏視覺元素，本教學將完整示範操作步驟。您將學會在 Word 中插入圖片、加入圖片群組，以及在單一可重用的 C# 程式中隱藏圖形。

我們將使用 Aspose.Words for .NET 函式庫，讓您在未安裝 Microsoft Word 的環境下操作 .docx 檔案。完成本指南後，您將擁有一個可執行的程式，能產生包含隱藏圖片群組的 Word 檔案，供後續處理或條件顯示使用。

## Prerequisites

- .NET 6.0 或更新版本（程式碼亦相容於 .NET Framework 4.6 以上）
- Aspose.Words for .NET NuGet 套件（`Install-Package Aspose.Words`）
- 磁碟上的資料夾，用於讀取圖片檔案及寫入輸出文件
- 具備 C# 與 Visual Studio（或您偏好的任何 IDE）的基本知識

## Create a blank Word document with Aspose.Words

第一步是 **建立空白 Word 文件**。Aspose.Words 提供 `Document` 類別，代表記憶體中的 Word 檔案。直接以無參數建構即可取得一個空白文件，準備加入內容。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();                 // blank .docx container
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*為何這很重要：* 從空白文件開始，可確保沒有隱藏的格式或遺留的段落會干擾您之後要加入的圖形。

## Insert image into Word using DocumentBuilder

接著，我們 **在 Word 中插入圖片**，首先建立一個用來容納圖片的群組圖形。群組圖形允許您將多個繪圖物件視為單一單位，方便之後一起隱藏或移動。

```csharp
        // Step 2: Insert a group shape with the desired size (width: 300, height: 200)
        GroupShape group = builder.InsertGroupShape(300, 200);
```

`InsertGroupShape` 方法會建立一個空的容器。尺寸單位為點 (1 point = 1/72 英吋)。請依您欲嵌入的圖片解析度調整大小。

## Add image group to the document

現在，我們 **加入圖片群組**，將 builder 的游標移至新建立的群組內部，然後插入圖片。之後的所有插入都會成為該群組的一部份。

```csharp
        // Step 3: Position the builder inside the group so subsequent inserts go into it
        builder.MoveTo(group);

        // Step 4: Add an image to the group shape
        // Replace the path with the actual location of your PNG/JPEG file
        builder.InsertImage(@"YOUR_DIRECTORY\photo1.png");
```

*提示：* 請使用絕對路徑或正確跳脫的相對路徑；否則 `InsertImage` 會拋出 `FileNotFoundException`。

## Hide shape in a Word document

最後，我們透過將群組的 `Hidden` 屬性設為 `true` 來 **在 Word 文件中隱藏圖形**。隱藏的圖形在 Word 開啟時不會顯示，但仍保留於檔案中，之後可程式化地將其顯示。

```csharp
        // Step 5: Hide the entire group (the image will not be visible in the saved document)
        group.Hidden = true;

        // Step 6: Save the document with the hidden group
        doc.Save(@"YOUR_DIRECTORY\GroupHidden.docx");
    }
}
```

當您在 Microsoft Word 中開啟 *GroupHidden.docx* 時，會看到一個完全空白的頁面，因為圖片群組已被隱藏。檔案仍保有圖片資料，若需要可使用 `group.Hidden = false` 解除隱藏。

## Full, runnable example

以下是完整程式碼，您可以直接複製貼上至新的 Console 專案中：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a group shape (300 pt × 200 pt)
            GroupShape group = builder.InsertGroupShape(300, 200);

            // 3️⃣ Move inside the group so inserts become part of it
            builder.MoveTo(group);

            // 4️⃣ Insert the image (replace with your own file)
            builder.InsertImage(@"YOUR_DIRECTORY\photo1.png");

            // 5️⃣ Hide the group so the image is not shown
            group.Hidden = true;

            // 6️⃣ Save the result
            doc.Save(@"YOUR_DIRECTORY\GroupHidden.docx");

            Console.WriteLine("Document created successfully.");
        }
    }
}
```

**預期輸出**

- 會在 `YOUR_DIRECTORY` 中產生名為 `GroupHidden.docx` 的檔案。
- 在 Word 中開啟該檔案會顯示空白頁面。
- 透過將 `group.Hidden = false` 並重新儲存，即可顯示隱藏的圖片。

## Common variations and edge cases

| 情況 | 如何調整程式碼 |
|-----------|----------------------|
| **多張圖片** | 在 `builder.MoveTo(group)` 之後加入額外的 `InsertImage` 呼叫。所有圖片皆位於同一群組內，並共用隱藏屬性。 |
| **不同圖片格式** | Aspose.Words 支援 PNG、JPEG、BMP、GIF、TIFF。只需更改檔案副檔名，程式碼不需變更。 |
| **條件顯示** | 儲存自訂文件變數 (`doc.Variables.Add("ShowImages", "true")`)，並在執行時依其值切換 `group.Hidden`。 |
| **大型文件** | 在插入群組前先於特定頁面建立群組 (`builder.InsertBreak(BreakType.PageBreak)`) 以避免版面移動。 |
| **相容舊版 Word** | 若需舊版 `.doc` 格式，請使用 `doc.Save("output.doc", SaveFormat.Doc)`；隱藏圖形的行為相同。 |

**專業提示：** 請務必在插入所有子元素之後再設定 `group.Hidden = true`。若在加入內容前就變更此旗標，可能在舊版 Word 中導致某些元素意外顯示。

## Conclusion

現在您已了解如何使用 Aspose.Words for .NET **建立空白 Word 文件**、**在 Word 中插入圖片**、**加入圖片群組**，以及 **在 Word 文件中隱藏圖形**。完整範例示範了從初始化文件到儲存包含隱藏圖片群組的檔案的每一步驟。

接下來，您可以探索：

- 將文字方塊或圖表加入同一群組
- 使用 `DocumentBuilder.StartBookmark` / `EndBookmark` 標記隱藏區段
- 依使用者輸入或文件變數程式化切換可見性

歡迎自行嘗試不同的圖形、尺寸與可見性規則，以符合您的自動化情境。祝開發順利！

## 接下來您可以學習什麼？

以下教學涵蓋與本指南緊密相關的主題，並以此為基礎延伸技術。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索其他實作方式。

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Floating Image in .NET](/words/english/net/add-content-using-documentbuilder/insert-floating-image/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}