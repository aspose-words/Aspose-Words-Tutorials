---
category: general
date: 2026-07-23
description: 建立空白 Word 文件並在 C# 中加入矩形形狀。了解如何使用 Aspose.Words 在 Word 中插入形狀與群組形狀。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- group shapes word
- how to insert shapes
- how to group shapes
language: zh-hant
lastmod: 2026-07-23
og_description: 在 C# 中建立空白 Word 文件，學習如何插入圖形、添加矩形圖形，以及使用 Aspose.Words 對 Word 圖形進行分組。
og_image_alt: Screenshot showing a blank Word document with two rectangle shapes grouped
  together
og_title: 建立含有分組矩形的空白 Word 文件 – C# 教學
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  headline: Create blank word document with grouped rectangles – C# guide
  type: TechArticle
- description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  name: Create blank word document with grouped rectangles – C# guide
  steps:
  - name: What if I need more than two shapes?
    text: Just keep calling `builder.InsertShape(...)` and `group.AppendChild(...)`
      for each new shape. The group can hold any number of children.
  - name: Can I set fill colour or border on the rectangles?
    text: 'Absolutely. After creating a rectangle you can tweak its `FillColor`, `OutlineColor`,
      and `LineWidth`:'
  - name: How do I move the whole group after it’s been created?
    text: 'Use the group''s `Left` and `Top` properties, measured in points:'
  - name: What about scaling the group?
    text: Set `group.Width` and `group.Height` or use `group.ScaleX` / `group.ScaleY`.
      The child rectangles retain their proportions relative to the group.
  - name: Does this work with older .doc files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. The only limitation is that some newer shape features may be down‑sampled
      when saving to the older binary format.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 建立空白 Word 文件，內含已群組的矩形 – C# 指南
url: /zh-hant/java/images-shapes/create-blank-word-document-with-grouped-rectangles-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立空白 Word 文件並分組矩形 – C# 指南

是否曾需要 **create blank word document**（建立空白 Word 文件），但又想要裡面已經包含一組圖形，卻不確定該如何將它們好好分組？你並非唯一有此需求的人。在許多報表或範本產生的情境中，你會希望有一個乾淨的畫布，裡面放置幾個矩形作為佔位符，並且希望它們能一起移動，視為同一個單位。

在本教學中，我們將逐步說明如何使用 Aspose.Words 程式庫 **create blank word document**、**add rectangle shape**，以及 **group shapes word**。完成後，你將擁有一個可直接使用的 `.docx` 檔案，兩個矩形已屬於同一個群組，之後的定位或調整大小都會同時影響兩者。  

我們也會回答常見的「**how to insert shapes**」與「**how to group shapes**」問題，這些問題常見於論壇與 Stack Overflow。無需額外文件——所有內容皆在此處。

---

## 先決條件

- .NET 6 或更新版本（程式碼亦可在 .NET Core 上編譯）  
- Aspose.Words for .NET（NuGet 套件 `Aspose.Words`）  
- 具備基本的 C# 語法概念（只要寫過「Hello World」即可）  

如果尚未安裝 Aspose.Words，請執行以下指令：

```bash
dotnet add package Aspose.Words
```

就這樣——不需要額外的 DLL、也不需要 COM interop，只要一個乾淨的 NuGet 參考即可。

## 步驟 1：建立空白 Word 文件並初始化 Builder

我們首先建立一個空的 `Document` 物件。可以把它想像成一張全新的紙張。接著我們會附加一個 `DocumentBuilder`，這是 Aspose 提供的便利工具，用於插入內容。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();               // <-- create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **為什麼這很重要：** 若沒有 `DocumentBuilder`，你必須手動操作低階的節點樹，容易出錯。Builder 抽象化了 `.docx` 檔案的 XML 複雜性。

## 步驟 2：如何插入圖形 – 先新增群組容器

Aspose 允許你插入一個 *group shape*，之後可以容納其他圖形。這是 **group shapes word** 的基礎。

```csharp
        // Step 2: Insert a group shape that will act as a container
        Shape group = builder.InsertGroupShape();
```

> **小技巧：** 群組本身在加入子圖形之前是不可見的，因此在下一步之前，你不會在產生的文件中看到任何痕跡。

## 步驟 3：新增矩形圖形 – 真正可見的物件

現在我們將 **add rectangle shape** 兩次，每次都有自己的尺寸。`InsertShape` 方法接受 `ShapeType` 以及以點為單位的尺寸（1 pt ≈ 1/72 英吋）。

```csharp
        // Step 3: Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); // 100 pt × 50 pt
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);  // 80 pt × 40 pt
```

> **為什麼選擇矩形？** 它是最簡單的幾何形狀，非常適合作為佔位符、類似按鈕的 UI 模型或簡單的圖形元素。

## 步驟 4：如何分組圖形 – 將矩形附加至群組

在建立矩形之後，我們現在透過將它們作為子項目加入先前插入的群組圖形，來 **how to group shapes**。

```csharp
        // Step 4: Append the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);
```

> **背後發生了什麼？** 群組圖形會成為文件 XML 樹中的父節點。移動群組時，兩個矩形會一起移動，保持相對位置不變。

## 步驟 5：儲存文件 – 你現在擁有一個含分組圖形的 Word 檔案

最後，我們將文件寫入磁碟。請將路徑改為你機器上實際存在的目錄。

```csharp
        // Step 5: Save the document with the grouped shapes
        doc.Save("GroupShape.docx");   // Creates a blank word document with grouped rectangles
    }
}
```

程式碼就完成了。執行後，開啟 `GroupShape.docx`，你會看到兩個矩形並排放置。若選取其中一個，整個群組會被高亮——正是 **group shapes word** 所應達成的效果。

## 完整原始碼彙整於此

為了方便起見，以下提供完整、可直接複製貼上的範例：

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape that will contain other shapes
        Shape group = builder.InsertGroupShape();

        // Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);

        // Add the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);

        // Save the document
        doc.Save("GroupShape.docx");
    }
}
```

**預期輸出：** 開啟 `GroupShape.docx` 後會看到空白頁面上有兩個已分組的矩形。選取其中一個矩形會自動選取另一個，證明分組成功。

## 常見問題與邊緣案例處理

### 如果需要超過兩個圖形怎麼辦？

只要持續呼叫 `builder.InsertShape(...)` 與 `group.AppendChild(...)` 來新增圖形即可。群組可以容納任意數量的子項目。

### 我可以設定矩形的填色或邊框嗎？

當然可以。建立矩形後，你可以調整其 `FillColor`、`OutlineColor` 與 `LineWidth`：

```csharp
rect1.FillColor = System.Drawing.Color.LightBlue;
rect1.OutlineColor = System.Drawing.Color.DarkBlue;
rect1.LineWidth = 1.5;
```

### 如何在建立後移動整個群組？

使用群組的 `Left` 與 `Top` 屬性，以點為單位進行定位：

```csharp
group.Left = 150;   // move 150 pt from the left margin
group.Top  = 200;   // move 200 pt from the top of the page
```

### 如何縮放群組？

設定 `group.Width` 與 `group.Height`，或使用 `group.ScaleX` / `group.ScaleY`。子矩形會相對於群組保持比例。

### 這能否用於較舊的 .doc 檔案？

Aspose.Words 抽象化了檔案格式，因此相同程式碼同時適用於 `.doc` 與 `.docx`。唯一的限制是，某些較新的圖形功能在儲存為較舊的二進位格式時可能會被降級。

## 生產環境程式碼的專業建議

- **釋放資源** – 若處理大型檔案，請將 `Document` 包在 `using` 區塊中，以即時釋放記憶體。  
- **錯誤處理** – 若要嵌入自訂字型，請捕捉 `Aspose.Words.Fonts.FontSettingsException`。  
- **效能** – 插入大量圖形時，可暫時停用版面配置更新：`doc.LayoutOptions = new LayoutOptions { UpdateFields = false };`，完成後再重新啟用。

## 結論

現在你已掌握使用 Aspose.Words 於 C# 中 **how to create blank word document**、**add rectangle shape** 與 **group shapes word** 的方法。此範例涵蓋了關鍵的「**how to insert shapes**」與「**how to group shapes**」步驟，說明每行程式碼的目的，並觸及自訂、邊緣案例與最佳實踐。

接下來，你可以探索 **how to insert images**、**add text inside grouped shapes**，或 **export the document to PDF**——這些皆遵循相同的 `DocumentBuilder` 與圖形操作模式。持續實驗吧，Aspose API 足夠強大，能處理幾乎所有你能想像的 Word 自動化情境。

祝程式開發順利，若遇到任何問題，歡迎留下評論！

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，並以此為基礎。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助你精通更多 API 功能，並在自己的專案中探索替代實作方式。

- [在 Word 文件中使用 Aspose.Words for .NET 插入圖形](/words/english/net/working-with-shapes/insert-shape/)
- [在 Word 文件中使用 Aspose.Words for .NET 建立群組圖形](/words/english/net/working-with-shapes/add-group-shape/)
- [使用 C# 建立 Word 矩形圖形 – 步驟說明指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}