---
category: general
date: 2026-08-17
description: 如何使用 Aspose.Words for Python 儲存 PNG。學習為圖形加入陰影、將文件另存為 PDF，並在同一指南中將 Word
  匯出為 PNG。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save png
- add shadow to shape
- save document as pdf
- export word to png
- convert word to pdf
language: zh-hant
lastmod: 2026-08-17
og_description: 如何使用 Aspose.Words 儲存 PNG。本教程展示了為形狀添加陰影、將文件另存為 PDF，以及將 Word 匯出為 PNG。
og_image_alt: Screenshot of a Word document with a rectangle shape that has a shadow,
  saved as PNG and PDF
og_title: 如何使用 Aspose.Words 儲存 PNG 並為形狀添加陰影
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  headline: How to save PNG and add shadow to shape with Aspose.Words
  type: TechArticle
- description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  name: How to save PNG and add shadow to shape with Aspose.Words
  steps:
  - name: Pro tip
    text: If you need a sharper shadow, reduce `blur`. For a more pronounced offset,
      increase `distance`. The `Shadow` class also exposes `angle` and `transparency`
      for fine‑tuned control.
  - name: 'Optional: higher‑resolution PNG'
    text: '```python png_options = aw.image.PngSaveOptions() png_options.resolution
      = 300 # DPI doc.save("output/high_res_output.png", png_options) ```'
  - name: Expected output
    text: 'Running the script creates three files:'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Image export
title: 如何使用 Aspose.Words 儲存 PNG 並為形狀添加陰影
url: /zh-hant/python/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words 儲存 PNG 並為形狀添加陰影

如果您需要 **how to save PNG** 從 Word 檔案中導出，本指南提供完整且可執行的解決方案。您還將看到如何 **add shadow to shape**、**save document as PDF**，以及 **export Word to PNG**，且全程不離開 Aspose.Words 環境。

本教學涵蓋將空白 Word 文件轉換為 PDF 與 PNG 圖像的全部步驟，同時對矩形形狀套用簡單的陰影效果。無需任何外部工具，且程式碼可在 Aspose.Words for Python via .NET 7 或更高版本上執行。

## 您將完成的工作

在閱讀完本篇文章後，您將能夠：

* 以程式方式建立新的 Word 文件。  
* 插入矩形形狀並設定陰影效果。  
* 將同一文件儲存為 PDF 檔案。  
* 將文件匯出為 PNG 圖像。  

這些步驟回應了常見的查詢 **how to save PNG**，同時在單一工作流程中處理 **add shadow to shape** 與 **save document as PDF**。

## 前置條件

* Python 3.9 或更新版本。  
* 已安裝 Aspose.Words for Python via .NET（`pip install aspose-words`）。  
* 具備對您指定之輸出目錄的寫入權限。  

如果尚未安裝 Aspose.Words，請執行：

```bash
pip install aspose-words
```

## 使用 Aspose.Words 儲存 PNG

第一個主要步驟是建立文件與 `DocumentBuilder`。Builder 為您提供流暢的 API，以插入形狀、表格或文字等內容。

```python
import aspose.words as aw

# Create a new blank document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` 代表記憶體中的整個 Word 檔案。`aw.DocumentBuilder` 指向目前的插入位置，最初位於第一（也是唯一）節的開頭。

## 在匯出前為形狀添加陰影

形狀可以是任何繪圖物件——矩形、橢圓或自訂多邊形。此處我們建立一個 100 × 100 點的矩形，並套用柔和的陰影。

```python
# Insert a rectangle shape (100x100 points)
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

# Configure a simple shadow
shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Softness of the shadow edges
shape.shadow.distance = 3.0      # Distance from the shape
shape.shadow.color = aw.Color.black
```

為何要在儲存前設定陰影？Aspose.Words 會在 PDF 與 PNG 匯出階段渲染陰影，因而在兩種輸出格式中皆保留視覺效果。

### 小技巧
若需要更銳利的陰影，可減少 `blur`。若想要更明顯的偏移，則增加 `distance`。`Shadow` 類別亦提供 `angle` 與 `transparency` 以進行精細調整。

## 將文件儲存為 PDF

一旦內容準備好，將 Word 文件儲存為 PDF 只需一行程式碼。`SaveFormat.PDF` 常數告訴 Aspose.Words 執行轉換。

```python
# Save the document as PDF (shadow is rendered in the output)
pdf_path = "output/output.pdf"
doc.save(pdf_path, aw.SaveFormat.PDF)
```

產生的 PDF 包含您定義的矩形及其精確陰影。Aspose.Words 會處理向量圖形，因此 PDF 檔案大小保持適中。

## 將 Word 匯出為 PNG

匯出為 PNG 會為每頁產生點陣圖。預設 Aspose.Words 使用 96 DPI；您可提供 `PngSaveOptions` 物件以提升此數值，取得更高解析度的輸出。

```python
# Export the same document as PNG
png_path = "output/output.png"
doc.save(png_path, aw.SaveFormat.PNG)
```

當您 **export Word to PNG** 時，每頁會另存為單獨的 PNG 檔。由於範例文件僅有一頁，僅會產生一個 PNG 檔案。

### 可選：更高解析度 PNG

```python
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI
doc.save("output/high_res_output.png", png_options)
```

較高的 DPI 在 PNG 用於印刷或需要清晰縮圖時相當有用。

## 完整腳本 – 複製、貼上並執行

以下為完整且獨立的腳本，實作上述所有步驟。將其儲存為 `generate_assets.py`，並於命令列執行。

```python
import os
import aspose.words as aw

# ------------------------------------------------------------------
# 1. Prepare output folder
# ------------------------------------------------------------------
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# ------------------------------------------------------------------
# 2. Create a new blank document and a builder
# ------------------------------------------------------------------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ------------------------------------------------------------------
# 3. Insert a rectangle shape and add a shadow
# ------------------------------------------------------------------
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Soft edges
shape.shadow.distance = 3.0      # Offset from shape
shape.shadow.color = aw.Color.black

# ------------------------------------------------------------------
# 4. Save as PDF (demonstrates "save document as pdf")
# ------------------------------------------------------------------
pdf_path = os.path.join(output_dir, "output.pdf")
doc.save(pdf_path, aw.SaveFormat.PDF)

# ------------------------------------------------------------------
# 5. Export as PNG (demonstrates "how to save png")
# ------------------------------------------------------------------
png_path = os.path.join(output_dir, "output.png")
doc.save(png_path, aw.SaveFormat.PNG)

# ------------------------------------------------------------------
# 6. Optional high‑resolution PNG (demonstrates "export word to png")
# ------------------------------------------------------------------
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI for sharper output
high_res_png_path = os.path.join(output_dir, "high_res_output.png")
doc.save(high_res_png_path, png_options)

print(f"Files written to {os.path.abspath(output_dir)}")
```

### 預期輸出

執行腳本會產生三個檔案：

* `output/output.pdf` – 包含投射黑色陰影矩形的 PDF。  
* `output/output.png` – 同一頁面的 96 DPI PNG 影像。  
* `output/high_res_output.png` – 300 DPI PNG，提供更高品質。  

使用您喜愛的檢視器開啟任一檔案，即可驗證陰影是否如預期般正確呈現。

## 常見問題與邊緣案例

**如果輸出目錄不存在會怎樣？**  
腳本會呼叫 `os.makedirs(output_dir, exist_ok=True)`，自動建立資料夾。這可避免在儲存過程中拋出 `FileNotFoundError`。

**我可以新增多個具有不同陰影的形狀嗎？**  
可以。建立額外的 `Shape` 物件，分別獨立設定 `shadow` 屬性，並於儲存前以 `builder.insert_node(shape)` 插入。

**將陰影轉換為其他點陣格式（例如 JPEG）時會保留嗎？**  
Aspose.Words 會為 `SaveFormat` 支援的所有點陣格式渲染陰影。您可將 `aw.SaveFormat.PNG` 替換為 `aw.SaveFormat.JPEG`，陰影仍會顯示。

**這與「convert word to pdf」有何不同？**  
`convert word to pdf` 基本上與第 4 步執行的操作相同。使用 `SaveFormat.PDF` 的 `doc.save` 呼叫在內部完成轉換，保留版面配置、字型與圖形（如陰影）。

**形狀大小有上限嗎？**  
形狀以點為單位測量（1 pt ≈ 1/72 英吋）。極大尺寸可能會增加最終檔案大小，但 Aspose.Words 沒有硬性上限。建立 `aw.Shape` 時可調整 `width` 與 `height` 參數以符合版面需求。

## 結論

您現在已了解如何 **how to save PNG** 從 Word 文件中導出，同時學會 **add shadow to shape**、**save document as PDF** 與 **export Word to PNG**，皆透過 Aspose.Words for Python 完成。完整腳本示範了清晰且可重複使用的模式，您可將其套用於更大型的文件、多頁或更複雜的圖形效果。

接下來的步驟可能包括：

* 嘗試其他 `ShapeType` 值（如 ellipse、cloud 等）。  
* 使用 `

## 接下來您應該學習什麼？

以下教學涵蓋與本指南技術密切相關的主題。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索替代實作方式。

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [How to Convert DOCX to PNG in Java – Aspose.Words](/words/english/java/document-converting/converting-documents-images/)
- [Save Word Documents as PostScript in Python Using Aspose.Words: A Comprehensive Guide](/words/english/python-net/document-operations/save-docs-as-postscript-using-aspose-words-python/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}