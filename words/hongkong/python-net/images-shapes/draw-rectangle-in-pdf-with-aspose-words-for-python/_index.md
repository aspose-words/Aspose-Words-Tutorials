---
category: general
date: 2026-08-07
description: 使用 Aspose.Words for Python 在 PDF 中繪製矩形，並學習如何為形狀添加陰影、設定形狀陰影，以及將文件另存為 PDF。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle in pdf
- add shadow to shape
- save document as pdf
- configure shape shadow
language: zh-hant
lastmod: 2026-08-07
og_description: 使用 Aspose.Words for Python 在 PDF 中繪製矩形。本教學示範如何為形狀加入陰影、設定形狀陰影，並將文件另存為
  PDF，以實現專業文件產出。
og_image_alt: PDF page showing a rectangle shape with a visible shadow created by
  Aspose.Words for Python
og_title: 使用 Aspose.Words for Python 在 PDF 中繪製矩形 – 指南
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Draw rectangle in PDF using Aspose.Words for Python and learn how to
    add shadow to shape, configure shape shadow, and save document as PDF.
  headline: Draw rectangle in PDF with Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF
- Shape
- Shadow
title: 使用 Aspose.Words for Python 在 PDF 中繪製矩形
url: /zh-hant/python/images-shapes/draw-rectangle-in-pdf-with-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 PDF 中繪製矩形（使用 Aspose.Words for Python）

如果您在使用 Python 時需要 **在 PDF 中繪製矩形**，本指南提供完整、可直接執行的解決方案。您將會看到如何 **為形狀新增陰影**、設定該陰影，最後 **將文件另存為 PDF** 以供分發或存檔。

在報告、發票或視覺註解中，建立帶陰影的矩形是常見需求。完成本教學後，您將擁有一個產生包含具真實陰影矩形的 PDF 的單一腳本，並了解如何調整尺寸、顏色與偏移，以符合任何設計需求。

## 前置條件

* 已安裝 Python 3.8+。
* Aspose.Words for Python via .NET 套件 (`aspose-words`) – 安裝方式如下：

```bash
pip install aspose-words
```

* 對欲儲存 PDF 的資料夾具有寫入權限。

不需要其他額外函式庫；Aspose.Words 內部已處理形狀建立、陰影設定與 PDF 匯出。

## 步驟 1：建立新的空白文件（在 PDF 中繪製矩形 – 初始化）

第一步是實例化 `Document` 物件。此物件代表整個 PDF 檔案，並提供 sections、paragraphs 與 shapes 的容器。

```python
import aspose.words as aw

# Create an empty Word document – it will become a PDF later
doc = aw.Document()
```

**為何重要：** Aspose.Words 將 PDF 產生視為從 Word 文件模型的轉換，因此即使最終輸出為 PDF，我們仍從 `Document` 開始。

## 步驟 2：在文件正文插入矩形形狀

矩形是特定的 `ShapeType`。我們將它加入第一個 section 的 body，儲存為 PDF 時會自動產生新頁面。

```python
# Append a rectangle shape to the first section's body
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Set the rectangle's dimensions (points = 1/72 inch)
rectangle.width = 200   # 200 pt ≈ 2.78 in
rectangle.height = 100  # 100 pt ≈ 1.39 in

# Optional: give the shape some visible text
rectangle.text = "Shadow demo"
```

**說明：** `width` 與 `height` 屬性控制形狀在 PDF 中的視覺尺寸。加入文字可在測試時更容易驗證矩形。

## 步驟 3：為形狀新增陰影 – 啟用與自訂

現在我們開啟陰影效果並微調其外觀。這正是 **add shadow to shape** 關鍵字發揮作用的地方。

```python
# Access the shape's shadow effect object
shadow = rectangle.shadow_effect

# Make the shadow visible
shadow.visible = True

# Configure blur radius (pt) – higher values produce a softer edge
shadow.blur = 8

# Set the distance (offset) from the shape in points
shadow.distance = 5

# Define the direction of the shadow in degrees (0 = right, 90 = down)
shadow.angle = 45

# Choose a shadow color – black works for most documents
shadow.color = aw.drawing.Color.black
```

**為何要設定形狀陰影？** 調整 `blur`、`distance` 與 `angle` 可模擬真實光照，提升產生的 PDF 可讀性與視覺層次。

## 步驟 4：將文件另存為 PDF – 最終輸出

在定義好矩形及其陰影後，最後一步是將 Word 文件匯出為 PDF。這滿足 **save document as pdf** 的需求。

```python
# Define the output path – replace YOUR_DIRECTORY with an actual folder
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)
print(f"PDF saved to {output_path}")
```

當您開啟 `shadow_rectangle.pdf` 時，會看到單一頁面，內含一個灰色邊框的矩形，標題為「Shadow demo」，並帶有清晰的對角線陰影。

### 預期輸出

* 名為 `shadow_rectangle.pdf` 的 PDF 檔案。
* 單一頁面，包含 200 pt × 100 pt 的矩形。
* 可見的陰影，偏移 5 pt，角度 45°，模糊度 8 pt。

## 步驟 5：探索變體與邊緣情況（可選）

以下列出在實務專案中可能需要的常見調整：

| 變體 | 程式碼片段 | 使用時機 |
|-----------|--------------|-------------|
| **不同的形狀類型**（例如橢圓） | `aw.drawing.ShapeType.OVAL` instead of `RECTANGLE` | 用於圓形圖形或徽章 |
| **自訂陰影顏色** | `shadow.color = aw.drawing.Color.from_argb(255, 100, 100, 100)` | 需要灰色或品牌特定陰影時 |
| **多個形狀** | Repeat the shape‑creation block and adjust `left`/`top` properties | 用於建立複雜圖表 |
| **形狀內無文字** | Omit `rectangle.text = "..."` | 形狀僅作為裝飾時 |
| **更高 DPI 輸出** | `doc.save(output_path, aw.SaveFormat.PDF, aw.PdfSaveOptions())` with `PdfSaveOptions` set for image quality | 用於列印品質的 PDF |

**專業提示：** 在調整其他屬性之前，務必先設定 `shadow.visible = True`；否則變更會被靜默忽略。

## 完整腳本 – 複製、貼上並執行

```python
import aspose.words as aw

# 1️⃣ Create a new blank document
doc = aw.Document()

# 2️⃣ Add a rectangle shape
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
rectangle.width = 200          # width in points
rectangle.height = 100         # height in points
rectangle.text = "Shadow demo"

# 3️⃣ Configure a visible shadow effect
shadow = rectangle.shadow_effect
shadow.visible = True
shadow.blur = 8                # blur radius (pt)
shadow.distance = 5            # offset distance (pt)
shadow.angle = 45              # direction (degrees)
shadow.color = aw.drawing.Color.black

# 4️⃣ Save the document as a PDF
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)

print(f"PDF successfully created at: {output_path}")
```

在終端機或 IDE 中執行腳本。將 `YOUR_DIRECTORY` 替換為實際的資料夾路徑，例如 `"/tmp"` 或 `"C:\\Users\\Me\\Documents"`。

## 結論

現在您已了解如何使用 Aspose.Words for Python **在 PDF 中繪製矩形**、**為形狀新增陰影**、**設定形狀陰影**，以及 **將文件另存為 PDF**。完整範例示範了從文件建立到最終匯出的每一步，而可選的變體則說明如何將程式碼套用於更複雜的情境。

接下來，您可以探索：

* 新增其他形狀類型（`ShapeType.LINE`、`ShapeType.ELLIPSE`）。
* 套用漸層填色或邊框以提升視覺效果。
* 使用 `PdfSaveOptions` 來嵌入字型或控制影像壓縮。

歡迎自行實驗各參數，以符合您的品牌或設計規範。祝您 PDF 程式撰寫愉快！

## 接下來該學什麼？

以下教學涵蓋與本指南技術緊密相關的主題，並以完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索其他實作方式。

- [使用 Aspose.Words for Python 優化 PDF 書籤](/words/english/python-net/performance-optimization/optimize-pdf-bookmarks-aspose-words-python/)
- [使用 Aspose.Words for Python 優化 PDF 載入（跳過圖片）](/words/hindi/python-net/performance-optimization/optimize-pdf-loading-python-aspose-words-skip-images/)
- [Aspose Words Python PDF 操作](/words/hongkong/python-net/document-operations/aspose-words-python-pdf-manipulation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}