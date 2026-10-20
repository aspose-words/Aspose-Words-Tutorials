---
category: general
date: 2026-10-20
description: 學習如何建立空白 Word 文件、在 Word 中將形狀分組、設定形狀填色，並使用內嵌環繞類型，完整示範 C# 範例。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- how to group shapes
- set shape fill color
- wrap type inline
language: zh-hant
lastmod: 2026-10-20
og_description: 使用 Aspose.Words 與 C# 建立空白 Word 文件、在 Word 中將形狀群組，並將形狀填色設定為內嵌環繞類型。請參考完整教學。
og_image_alt: Screenshot of a blank Word document containing a grouped rectangle and
  text box created with Aspose.Words
og_title: 建立空白 Word 文件並在 Word 中將形狀分組 – 步驟教學
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  headline: How to create a blank Word document and group shapes in Word using Aspose.Words
  type: TechArticle
- description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  name: How to create a blank Word document and group shapes in Word using Aspose.Words
  steps:
  - name: Expected result
    text: '* A .docx file containing a single paragraph. * Inside the paragraph, an
      inline group that looks like a single composite object. * The rectangle is filled
      with light blue, and the text box displays “Grouped text”.'
  - name: What if I need the group to float rather than be inline?
    text: Replace `WrapType.Inline` with `WrapType.TopBottom` (or any other `WrapType`
      enum value). Floating groups can be positioned independently of paragraph flow,
      but they lose the automatic inline alignment.
  - name: Can I add more shapes, such as circles or images?
    text: Yes. Create additional `Shape` objects with `ShapeType.Ellipse` or `ShapeType.Image`,
      configure their properties, and call `group.AppendChild(newShape)`. The group
      will automatically expand to accommodate the new bounds if you update `group.Bounds`
      accordingly.
  - name: How do I change the group’s overall size after adding children?
    text: Adjust `group.Bounds` after all children are appended, or compute the union
      of child bounds programmatically. This ensures the group’s hit‑test area matches
      the visual content.
  - name: What if the output folder does not exist?
    text: 'Aspose.Words throws a `DirectoryNotFoundException`. Create the directory
      first:'
  - name: Does this work with .NET Framework instead of .NET Core?
    text: All APIs used (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) are
      available in the .NET Framework version of Aspose.Words, so the same code works
      unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 如何使用 Aspose.Words 建立空白 Word 文件並將圖形分組
url: /zh-hant/net/programming-with-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中建立空白文件並將圖形分組

如果您需要 **建立空白 Word 文件**，且其中包含多個作為單一單位運作的圖形，本指南將一步步說明。您將會看到如何 **在 Word 中分組圖形**、設定圖形的填色，以及套用 **內嵌換行類型**——全部透過簡潔且可執行的 C# 程式示範。

本教學會逐行說明程式碼，解釋每一步的意義，並指出常見的陷阱。完成後，您將得到一個 .docx 檔案，內含一個矩形與文字方塊已分組在一起，隨時可進一步自動化。

## 您將學會

* 如何使用 Aspose.Words 初始化空的 Word 檔案。  
* 正確建立 **GroupShape** 並加入子圖形的方法。  
* **設定圖形填色** 以及控制位置的技巧。  
* 使用 **內嵌換行類型** 讓群組行為如同單一內嵌物件。  
* 如何儲存並驗證結果。

不需要事先具備 Aspose.Words 的經驗，但您應該熟悉基本的 C# 語法，且已安裝 Visual Studio（或其他 IDE）。

## 前置條件

| 需求 | 原因 |
|-------------|--------|
| .NET 6.0 或更新版本 | 為 C# 專案提供執行環境。 |
| Aspose.Words for .NET（最新版本） | 提供本範例使用的 `Document`、`DocumentBuilder` 與圖形類別。 |
| 可寫入的資料夾路徑 | `doc.Save` 需要有效的目錄來寫入輸出檔案。 |
| 基本的 C# 知識 | 讓您能夠跟隨程式碼並依需求自行修改。 |

透過 NuGet 安裝 Aspose.Words：

```bash
dotnet add package Aspose.Words
```

---

## 第一步：建立空白 Word 文件

第一個動作是 **建立空白 Word 文件**。Aspose.Words 的 `Document` 類別代表記憶體中的 Word 檔案，而 `DocumentBuilder` 提供便利的 API 讓您編輯它。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new empty document.
Document doc = new Document();

// Attach a builder to the document for easy content insertion.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*為何重要*：從乾淨的文件開始，可確保您加入的群組圖形是唯一內容，驗證過程也更直接。

## 第二步：定義具有內嵌換行類型的群組圖形

**GroupShape** 充當其他圖形的容器。將其 `WrapType` 設為 `Inline` 可確保群組在段落流中表現為單一內嵌物件。

```csharp
// Create a group shape that will hold the rectangle and text box.
GroupShape group = new GroupShape(doc, WrapType.Inline);

// Define the bounding rectangle of the group (x, y, width, height).
group.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
```

*為何重要*：使用 **內嵌換行類型** 可防止群組漂移離開周圍文字，這在您希望群組作為整體移動時相當重要。

## 第三步：加入矩形並設定圖形填色

矩形是常見的視覺元素。`Shape` 建構子接受 `ShapeType`；接著指定尺寸與填色。

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 150,
    Height = 100,
    FillColor = System.Drawing.Color.LightBlue
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

*為何重要*：`FillColor` 屬性示範了 **設定圖形填色** 的實作，讓矩形呈現淡藍色背景，於最終文件中更為顯眼。

## 第四步：加入文字方塊 ── 有效分組圖形的方式

文字方塊提供可編輯的文字內容。透過調整 `Top` 屬性，使其相對於群組座標系統定位。

```csharp
// Create a text box shape.
Shape textBox = new Shape(doc, ShapeType.TextBox)
{
    Width = 120,
    Height = 60,
    TextBoxText = "Grouped text",
    Top = 110 // Position below the rectangle inside the group.
};

// Append the text box to the group.
group.AppendChild(textBox);
```

*為何重要*：此步說明 **如何分組圖形**──將每個子圖形加入同一個 `GroupShape` 實例。`Top` 偏移確保文字方塊出現在矩形下方，展示精確的版面控制。

## 第五步：將完成的群組圖形插入文件

現在群組已包含兩個子圖形，將其插入目前 builder 的位置。

```csharp
// Insert the group shape at the builder’s cursor location.
builder.InsertNode(group);
```

*為何重要*：以單一節點插入群組，可保證 Word 將矩形與文字方塊視為一個邏輯物件，編輯時會保留相對位置。

## 第六步：儲存文件並驗證輸出

最後，將文件寫入磁碟。將 `YOUR_DIRECTORY` 替換為您機器上的實際路徑。

```csharp
// Save the document to the specified folder.
doc.Save("YOUR_DIRECTORY/GroupShape.docx");
```

開啟 `GroupShape.docx` 後，您應該會看到一個淡藍色矩形，下方緊接著標示「Grouped text」的文字方塊。選取任一圖形都會同時選取整個群組，證實 **在 Word 中分組圖形** 已如預期運作。

### 預期結果

* 一個包含單一段落的 .docx 檔案。  
* 段落內有一個看似單一複合物件的內嵌群組。  
* 矩形填滿淡藍色，文字方塊顯示「Grouped text」。

![產生的 Word 文件截圖](grouped_shapes.png){.center width=600 alt="使用 Aspose.Words 建立的空白 Word 文件，內含分組矩形與文字方塊的截圖"}

## 常見問題與邊緣案例處理

### 如果我需要群組浮動而非內嵌，該怎麼做？

將 `WrapType.Inline` 改為 `WrapType.TopBottom`（或其他 `WrapType` 列舉值）。浮動群組可獨立於段落流定位，但會失去自動內嵌對齊的特性。

### 我可以加入更多圖形，例如圓形或圖片嗎？

可以。使用 `ShapeType.Ellipse` 或 `ShapeType.Image` 建立額外的 `Shape` 物件，設定其屬性後呼叫 `group.AppendChild(newShape)`。若同時更新 `group.Bounds`，群組會自動擴展以容納新範圍。

### 如何在加入子圖形後變更群組的整體大小？

在全部子圖形加入後調整 `group.Bounds`，或以程式計算子圖形範圍的聯集。這樣可確保群組的點擊區域與實際視覺內容相符。

### 若輸出資料夾不存在會怎樣？

Aspose.Words 會拋出 `DirectoryNotFoundException`。請先建立目錄：

```csharp
string outputPath = "YOUR_DIRECTORY";
Directory.CreateDirectory(outputPath);
doc.Save(Path.Combine(outputPath, "GroupShape.docx"));
```

### 這能在 .NET Framework 而非 .NET Core 上執行嗎？

使用的所有 API（`Document`、`DocumentBuilder`、`GroupShape`、`Shape`）在 Aspose.Words 的 .NET Framework 版亦可使用，程式碼不需變更即可執行。

## 專業小技巧

* **效能建議** – 在插入大量群組時，重複使用同一個 `DocumentBuilder` 實例；為每個群組建立新 builder 會增加開銷。  
* **視覺一致性** – 將 `rectangle.StrokeColor` 設為與 `FillColor` 相同，或將 `rectangle.LineWidth = 0` 以隱藏邊框，達到更平滑的外觀。  
* **除錯技巧** – 在儲存前呼叫 `doc.UpdatePageLayout()`，若您修改了大量圖形，這會強制 Word 重新計算版面，避免意外的裁切問題。

## 結論

您現在已掌握如何 **建立空白 Word 文件**、**在 Word 中分組圖形**、**設定圖形填色**，以及使用 **內嵌換行類型**，全部透過 Aspose.Words for .NET 完成。完整範例示範了在 Word 中構建可作為單一物件操作的複合圖形的標準做法。

接下來您可以探索：

* 加入圖片或圖表等其他圖形。  
* 嘗試不同的 `WrapType` 值以建立浮動群組。  
* 在多個文件間自動批次產生分組圖示。

歡迎將您的程式碼套用於自己的自動化情境，並在留言中分享成果！

## 接下來該學什麼？

以下教學與本指南緊密相關，能進一步深化您對 API 的運用與替代實作方式的了解。

- [使用 Aspose.Words for .NET 在 Word 文件中建立群組圖形](/words/english/net/working-with-shapes/add-group-shape/)
- [使用 Aspose.Words 建立空白 Word 文件 – 步驟說明指南](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [如何從 Word 以內嵌圖形儲存 PDF – 完整指南](/words/english/java/document-conversion-and-export/how-to-save-pdf-from-word-with-inline-shapes-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}