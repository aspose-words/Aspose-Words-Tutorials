---
category: general
date: 2026-09-21
description: 使用 Aspose.Words 建立空白 Word 文件，設定圖形大小、設定圖形位置、設定圖形顏色，並在一次操作中儲存 docx 檔案。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set shape size
- save docx file
- set shape position
- set shape color
language: zh-hant
lastmod: 2026-09-21
og_description: 使用 Aspose.Words 只需數分鐘即可建立空白 Word 文件、設定圖形大小、設定圖形位置、設定圖形顏色，並儲存為 docx
  檔案。
og_image_alt: Screenshot of a blank Word document containing two colored rectangles
  grouped together
og_title: 建立空白 Word 檔案並加入彩色形狀 – Aspose.Words 指南
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create a blank Word document using Aspose.Words, set shape size, set
    shape position, set shape color, and save the docx file in a single walkthrough.
  headline: Create a blank Word document and add colored shapes with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: 建立空白 Word 文件，並使用 Aspose.Words 添加彩色形狀
url: /zh-hant/net/programming-with-shapes/create-a-blank-word-document-and-add-colored-shapes-with-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立空白 Word 文件並使用 Aspose.Words 加入彩色圖形

如果您需要以程式方式 **建立空白 Word 文件**，本教學將示範如何使用 Aspose.Words。您將學會 **設定圖形大小**、**設定圖形位置**、**設定圖形顏色**，最後 **儲存 docx 檔案**，全程不必離開 IDE。

在 C# 中操作 Word 檔案通常需要處理低階的 OpenXML 呼叫，但 Aspose.Words 已將複雜度抽象化。完成本教學後，您將擁有一個功能完整的 `.docx`，內含由兩個彩色矩形組成的群組圖形，適用於報告、證書或自訂範本。

## 前置條件

- .NET 6.0 或更新版本（此程式碼亦相容 .NET Framework 4.7+）
- Aspose.Words for .NET 23.9 或更新版本（透過 NuGet 安裝：`Install-Package Aspose.Words`）
- 具備 C# 與 Visual Studio（或任意 C# 編輯器）的基本知識

不需要事先存在的 Word 檔案；本教學一開始即 **建立空白 Word 文件**。

## 使用 Aspose.Words 建立空白 Word 文件

第一步是實例化 `Document` 物件。此物件代表記憶體中的空白 Word 檔案。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty document.
Document document = new Document();

// DocumentBuilder gives you a cursor to add content.
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` 初始為空，正好符合您 **建立空白 Word 文件** 的需求。稍後會使用 `builder` 在目前游標位置插入圖形群組。

## 設定圖形大小並建立 GroupShape

`GroupShape` 如同容器，可容納多個個別圖形。首先，定義容器的整體尺寸。

```csharp
// Create a GroupShape that will hold multiple shapes.
// Width = 300 points, Height = 200 points.
GroupShape groupShape = new GroupShape(document, 300, 200);

// Position the group on the page: 100 points from the left, 100 points from the top.
groupShape.Left = 100;
groupShape.Top  = 100;
```

此處 **設定圖形大小** 為群組本身的 300 × 200。每個子圖形也使用相同的屬性名稱（`Width`、`Height`），讓您能細緻控制每個元素。

## 新增第一個矩形並設定圖形顏色

現在將矩形加入群組，並為其設定背景顏色。

```csharp
// First rectangle – light blue background.
Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 0,          // Position relative to the group’s left edge.
    Top = 0,           // Position relative to the group’s top edge.
    FillColor = Color.LightBlue
};

// Append the rectangle to the group.
groupShape.AppendChild(rectangle1);
```

`FillColor` 屬性 **設定圖形顏色**。使用 `System.Drawing.Color` 可選擇任何預設或自訂的 ARGB 值。

## 新增第二個矩形，設定其大小、位置與顏色

第二個矩形示範如何 **設定圖形位置**（相對於群組）以及如何變更顏色。

```csharp
// Second rectangle – light coral background.
Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 150,               // 150 points to the right of the group’s left edge.
    Top = 0,                  // Same vertical alignment as the first rectangle.
    FillColor = Color.LightCoral
};

groupShape.AppendChild(rectangle2);
```

因為群組寬度為 300 點，兩個 120 點的矩形可在中間保留 30 點的間距。如需不同版面配置，可調整 `Left` 與 `Top`。

## 將 GroupShape 插入文件

完成群組設定後，將其放置於目前游標位置。

```csharp
// Insert the completed group shape at the builder’s current location.
builder.InsertNode(groupShape);
```

`InsertNode` 直接將圖形寫入文件的 body，保留先前 **設定圖形位置** 的精確資訊。

## 儲存 docx 檔案

最後一步是將文件寫入磁碟。此步驟示範 **儲存 docx 檔案** 的操作。

```csharp
// Define the output path (ensure the directory exists).
string outputPath = @"C:\Temp\GroupShape.docx";

// Save the document in DOCX format.
document.Save(outputPath);
```

執行程式後，於 Microsoft Word 開啟 `GroupShape.docx`。您應該會看到一個空白頁面，內含兩個並排的彩色矩形組成的群組圖形。

### 預期結果

- 單頁 `.docx` 檔案。
- 該頁的群組圖形距左、上邊界各 100 pts。
- 群組內左側為淡藍色矩形，右側為淡珊瑚色矩形，尺寸皆為 120 × 80 pts。

## 完整可執行範例

以下為可直接貼入 Console 應用程式的完整程式碼，無需其他檔案。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Define a GroupShape and set its size and position.
        GroupShape groupShape = new GroupShape(document, 300, 200)
        {
            Left = 100,
            Top = 100
        };

        // 3️⃣ First rectangle – set size, position, and color.
        Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 0,
            Top = 0,
            FillColor = Color.LightBlue
        };
        groupShape.AppendChild(rectangle1);

        // 4️⃣ Second rectangle – set size, position, and color.
        Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 150,
            Top = 0,
            FillColor = Color.LightCoral
        };
        groupShape.AppendChild(rectangle2);

        // 5️⃣ Insert the grouped shape into the document.
        builder.InsertNode(groupShape);

        // 6️⃣ Save the docx file.
        string outputPath = @"C:\Temp\GroupShape.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

執行此程式即會產生前述文件，完成四項目標：**建立空白 Word 文件**、**設定圖形大小**、**設定圖形位置**、**設定圖形顏色**，以及 **儲存 docx 檔案**。

## 常見變化與例外情況

| 情境 | 需要變更的地方 | 為何重要 |
|------|----------------|----------|
| **不同的圖形類型** | 將 `ShapeType.Rectangle` 改為 `ShapeType.Ellipse`、`ShapeType.Triangle` 等 | 讓您在不使用外部圖片的情況下建立更複雜的圖形 |
| **動態尺寸** | 從使用者輸入或設定檔計算 `Width` 與 `Height` | 使解決方案可在多個文件範本間重複使用 |
| **另存為 PDF** | 呼叫 `document.Save("output.pdf", SaveFormat.Pdf);` | 若收件者需要不可編輯的格式，PDF 是安全的選擇 |
| **在圖形內加入文字** | 建立 `TextBox` 圖形並設定 `TextBox.Text` | 方便製作帶標籤的徽章或說明框 |
| **同頁多個群組** | 以不同的 `Left`/`Top` 值重複步驟 2‑5 | 可建構儀表板或多區段版面配置 |

### 小技巧

當需要精確對齊圖形時，可在插入群組前設定 `ShapeBase.WrapType = WrapType.Inline`。此屬性會讓群組行為如同段落，避免文字意外環繞圖形。

## 結論

現在您已掌握如何使用 Aspose.Words **建立空白 Word 文件**、**設定圖形大小**、**設定圖形位置**、**設定圖形顏色**，以及 **儲存 docx 檔案**。完整範例展示了一個乾淨、可重用的模式，適用於任何 Word 自動化專案。

接下來您可以探索：

- 為同一個 `GroupShape` 加入更多圖形或圖片（**設定圖形大小**、**設定圖形顏色** 的變化）。
- 使用 `ShapeBase.Rotation` 旋轉矩形，以達到裝飾效果。
- 將同一文件匯出為 PDF 或 HTML，擴大分發渠道（**儲存 docx 檔案** 的替代方案）。

歡迎自行嘗試不同的顏色、尺寸與版面邏輯，以符合您的報表或範本需求。祝開發順利！

## 接下來該學什麼？

以下教學與本指南緊密相關，能進一步深化您所學的技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，並在自己的專案中探索替代實作方式。

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}