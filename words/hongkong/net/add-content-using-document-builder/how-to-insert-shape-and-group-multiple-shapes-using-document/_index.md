---
category: general
date: 2026-11-15
description: 學習如何在 Word 文件中插入形狀，並使用 Aspose.Words DocumentBuilder 將多個形狀分組。包括插入矩形形狀和插入多個形狀的範例。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert shape
- group multiple shapes
- insert multiple shapes
- insert rectangle shape
language: zh-hant
lastmod: 2026-11-15
og_description: 如何使用 Aspose.Words 在 Word 檔案中插入形狀。本指南涵蓋多形狀分組、插入矩形形狀以及高效新增多個形狀。
og_image_alt: Screenshot showing how to insert shape and group multiple shapes in
  a Word document using DocumentBuilder
og_title: 如何使用 DocumentBuilder 插入形狀並將多個形狀分組
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  headline: How to insert shape and group multiple shapes using DocumentBuilder in
    C#
  type: TechArticle
- description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  name: How to insert shape and group multiple shapes using DocumentBuilder in C#
  steps:
  - name: Why use a group?
    text: '* **Single‑point transformation** – rotate or resize the whole group with
      one call. * **Logical organization** – the Word document tree reflects the grouping,
      making later edits easier. * **Consistent layout** – moving the group keeps
      the relative positions of its children intact.'
  - name: Adding more shapes – extending **insert multiple shapes** inside the group
    text: 'You can keep calling `InsertShape` while the cursor remains inside the
      `GroupShape`. For example, to add a triangle:'
  - name: Expected output
    text: '* **First two shapes** – a rectangle and an ellipse placed independently
      on the page. * **Grouped block** – a rectangle, an ellipse, and a triangle that
      move together when you click any of them in Word.'
  type: HowTo
tags:
- Aspose.Words
- C#
- DocumentBuilder
- Shape handling
title: 如何使用 C# 中的 DocumentBuilder 插入形狀並將多個形狀分組
url: /zh-hant/net/add-content-using-document-builder/how-to-insert-shape-and-group-multiple-shapes-using-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 DocumentBuilder 在 C# 中插入圖形並將多個圖形分組

如果您需要了解 **how to insert shape** 到 Word 文件中使用 Aspose.Words，本指南會向您展示具體步驟。您還會學習如何 **group multiple shapes**，使它們作為單一物件運作，以及如何 **insert rectangle shape** 與其他圖形一起使用。

文件自動化通常需要加入多個圖形——圖表、標誌、說明框——同時保持其組織有序。完成本教學後，您將能夠 **insert multiple shapes**，將它們放入分組，並儲存乾淨且可重複使用的版面配置。

## 前置條件

* .NET 6.0 或更新版本已安裝  
* Visual Studio 2022（或任何 C# IDE）  
* Aspose.Words for .NET 授權或免費評估金鑰  
* 具備 C# 與 Aspose.Words `DocumentBuilder` 類別的基本知識  

您 **不** 需要任何其他第三方函式庫；所有必要的功能皆內建於 Aspose.Words。

## 步驟 1：透過 NuGet 安裝 Aspose.Words

在 Visual Studio 中開啟您的專案，並在套件管理員主控台執行以下指令：

```powershell
Install-Package Aspose.Words
```

此套件包含本教學中會使用到的 `DocumentBuilder`、`Shape` 與 `GroupShape` 類別。

## 步驟 2：建立 DocumentBuilder 實例 ─ **how to insert shape** 的基礎

第一行可執行的程式碼是建立 `DocumentBuilder`。此物件讓您直接存取文件樹，從而能精確地將圖形放置在想要的位置。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Initialise a new blank document
        Document doc = new Document();
        // Create a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // The rest of the tutorial inserts and groups shapes here …
    }
}
```

*為什麼重要*：`DocumentBuilder` 會維持一個游標（「插入點」）。之後的每個 `Insert...` 呼叫都會使用該游標，這也是我們稍後將它移入 `GroupShape` 以將所有圖形聚集在一起的原因。

## 步驟 3：**Insert rectangle shape** ─ 您將加入的第一個圖形

矩形是常見的佔位符，可用於表格、圖片或說明框。使用 `InsertShape` 搭配 `ShapeType.Rectangle`，並以點 (pt) 為單位指定寬度與高度（1 pt ≈ 1/72 英吋）。

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

矩形會出現在目前游標位置。若有需要，您之後可以自訂其填充、線條樣式或文字。

## 步驟 4：插入另一個圖形 ─ 用橢圓增加視覺變化

加入多於一個圖形可示範 **insert multiple shapes**。橢圓會緊接在矩形之後，依文件流程排列。

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

此時文件中已包含兩個獨立的圖形。若您移動游標或加入文字，圖形仍會保留在插入時的位置。

## 步驟 5：**Group multiple shapes** 使其作為單一單元

當您需要一次性移動、旋轉或格式化多個圖形時，分組是必須的。以下程式碼會建立一個 `GroupShape`，將 builder 的游標移入其中，然後再次插入相同的圖形──這次它們會成為群組的子圖形。

```csharp
// 1️⃣ Create a GroupShape and add it to the document tree
GroupShape group = new GroupShape(builder.Document);
builder.InsertNode(group);

// 2️⃣ Position the cursor inside the group so new inserts go into it
builder.MoveTo(group);

// 3️⃣ Insert a rectangle shape inside the group
builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Insert an ellipse shape inside the same group
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

### 為什麼使用群組？

* **單點轉換** – 只需一次呼叫即可旋轉或調整整個群組的大小。  
* **邏輯組織** – Word 文件樹會反映此分組，讓之後的編輯更簡單。  
* **一致的版面** – 移動群組時，子圖形之間的相對位置會保持不變。  

### 新增更多圖形 ─ 在群組內擴充 **insert multiple shapes**

只要游標仍在 `GroupShape` 內，您即可持續呼叫 `InsertShape`。例如，加入一個三角形：

```csharp
builder.InsertShape(ShapeType.Triangle, 60, 60);
```

每次呼叫都會遵循群組的上下文，因此三角形會自動成為同一分組集合的一部份。

## 步驟 6：儲存文件並驗證結果

在所有圖形放置完畢後，將文件保存為 `.docx` 檔案。使用 Microsoft Word（或任何相容的檢視器）開啟該檔案，應會看到兩個獨立的圖形，接著是一個包含相同矩形、橢圓與三角形的分組。

```csharp
// Save the document
doc.Save("GroupedShapesDemo.docx");
```

### 預期輸出

* **前兩個圖形** – 矩形與橢圓分別獨立放置於頁面上。  
* **分組區塊** – 矩形、橢圓與三角形組成的群組，於 Word 中點擊任一圖形時會一起移動。  

您可以透過選取群組內的任意圖形來測試分組；Word 會突顯整個集合，證明 **group multiple shapes** 操作已成功。

## 常見陷阱與專業提示

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| 圖形出現在預期頁面之外 | 在插入前未將 builder 的游標移入 `GroupShape`。 | 在任何屬於該群組的 `InsertShape` 呼叫之前，務必先執行 `builder.MoveTo(group)` **before**。 |
| 儲存後群組消失 | 群組在插入時未加入文件的節點集合。 | 在建立 `GroupShape` 後立即使用 `builder.InsertNode(group)`。 |
| 由於文件 DPI 而導致尺寸不符 | Aspose.Words 使用點 (points)；若以像素思考會產生尺寸不匹配。 | 將像素轉換為點 (`points = pixels * 72 / 96`) 或直接使用點作為單位。 |
| 圖形意外重疊 | 未設定明確位置，Word 會依序放置。 | 插入後設定 `Shape.Left` 與 `Shape.Top` 以控制精確位置。 |

**專業提示**：分組後，您可以取得群組的 `Shapes` 集合（`group.Shapes`），以進行遍歷、重新命名或批次格式設定。

## 步驟 7：擴充範例 ─ 接下來該做什麼？

既然您已了解 **how to insert shape**、**insert rectangle shape** 與 **group multiple shapes**，接下來可以探索以下內容：

* **為群組圖形添加動畫** – 設定群組的旋轉或翻轉屬性。  
* **套用樣式** – 使用 `Shape.FillColor`、`Shape.LineFormat` 或 `Shape.TextBox` 來加入標籤。  
* **匯出為 PDF** – 呼叫 `doc.Save("output.pdf")` 時，相同的分組版面會正確呈現。  

所有這些擴充皆重複使用相同的 `DocumentBuilder` 工作流程，讓程式碼保持簡潔且易於維護。

## 結論

本教學示範了如何使用 Aspose.Words 在 Word 文件中 **how to insert shape**、如何 **insert rectangle shape**，以及如何 **group multiple shapes** 使其作為單一物件運作。透過遵循一步步的程式碼，您可以可靠地 **insert multiple shapes**、將它們組織成群組，並以程式方式產生專業等級的文件。

歡迎嘗試不同的圖形類型、顏色與群組變換。準備好後，將此模式整合至更大型的報表或範本解決方案，以自動化複雜的文件版面配置。祝開發愉快！

## 接下來您可以學習什麼？

以下教學涵蓋與本指南技術密切相關的主題，並以完整可執行的程式碼範例與逐步說明，協助您精通其他 API 功能，並在自己的專案中探索替代實作方式。

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [How to create and insert ellipse and rectangle shapes inside a group shape in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [How to group shapes in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}