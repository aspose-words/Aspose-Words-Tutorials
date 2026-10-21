---
category: general
date: 2026-10-16
description: 使用 Python 建立空白 Word 文件，在 Word 中插入圖形，加入外部陰影，並儲存為 PDF。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert shape in word
- save as pdf python
- add outer shadow shape
- create pdf with shape
language: zh-hant
lastmod: 2026-10-16
og_description: 使用 Aspose.Words for Python 建立一個帶有外部陰影形狀的空白 Word 文件。本指南說明如何插入形狀、套用陰影，並將檔案儲存為
  PDF。
og_image_alt: Screenshot of a Word document containing a rectangle shape with an outer
  shadow, saved as PDF
og_title: 建立帶有形狀陰影的空白 Word 文件 – Python 指南
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document, insert shape in Word, add outer shadow,
    and save as PDF using Python.
  headline: Create blank Word document with shadowed shape in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- PDF generation
- Shape styling
title: 使用 Python 建立帶陰影形狀的空白 Word 文件
url: /zh-hant/python/word-automation/create-blank-word-document-with-shadowed-shape-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Python 中建立帶陰影形狀的空白 Word 文件

如果你需要 **建立空白 Word 文件** 並加入自訂圖形，本指南將為你一步步說明。我們會示範如何 **在 Word 中插入形狀**、套用 **外部陰影形狀**，最後 **使用 Python 另存為 PDF**。

你將學會如何設定 Aspose.Words for Python、建立矩形、設定其陰影樣式，並產生保留視覺效果的 PDF。無需事先了解 Aspose API，但你應具備基本的 Python 知識，且已安裝 Python 3.10 或更新版本。

## 前置條件

在開始之前，請確保你已具備：

* 已安裝 Python 3.10 或更新版本。
* 有效的 Aspose.Words for Python 授權（免費試用版可用於評估）。
* `pip` 可用於安裝 `aspose-words` 套件。
* 對將儲存 PDF 的目錄具有寫入權限。

你可以使用單一指令安裝此函式庫：

```bash
pip install aspose-words
```

## 建立空白 Word 文件 – 環境設定

第一步是建立一個空的 Word 檔案，作為形狀的畫布。

```python
import aspose.words as aw

# Initialize a new, empty document
doc = aw.Document()
# DocumentBuilder provides convenient methods for adding content
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` 代表一個完全空白的 Word 檔案。使用 `DocumentBuilder` 後，你即可存取如 `insert_shape` 等方法，我們將在下一步使用它。

## 在 Word 中插入形狀並設定尺寸

現在我們加入一個矩形，稍後會套用外部陰影。尺寸以點 (point) 為單位表示 (1 pt ≈ 1/72 英吋)。

```python
# Insert a rectangle shape with a width of 200 pt and a height of 100 pt
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)
```

`insert_shape` 會回傳一個 `Shape` 物件，你可以進一步自訂。此時文件在 Microsoft Word 中開啟時已顯示可見的矩形。

## 新增外部陰影形狀 – 客製化效果

Aspose.Words 提供 `ShadowEffect` 類別，用於定義陰影屬性，例如樣式、模糊、距離與顏色。

```python
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a new shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # Choose an outer shadow
shadow.blur = 5.0                         # Softness of the shadow edges
shadow.distance = 3.0                     # Offset distance from the shape
shadow.color = aw.Color.black             # Shadow color

# Apply the shadow to the rectangle
rectangle.shadow = shadow
```

將 `style` 設為 `OUTER` 可確保陰影出現在矩形邊框之外，呈現細緻的 3‑D 效果。你可以嘗試調整 `blur` 與 `distance` 以得到較緊密或較散布的陰影。

## 使用 Python 另存為 PDF – 完成文件

在設定完形狀樣式後，文件即可直接另存為 PDF。Aspose.Words 於內部處理轉換，保留陰影效果。

```python
output_path = "output/shape_with_shadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

當你在任何 PDF 檢視器中開啟 `shape_with_shadow.pdf` 時，會看到與 Word 中相同的帶外部陰影的矩形。

## 完整範例程式

以下為結合所有步驟的完整腳本。將其複製到名為 `create_word_with_shadow.py` 的檔案中並執行。

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1. Create a blank Word document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2. Insert a rectangle shape
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)

# 3. Define and apply an outer shadow
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER
shadow.blur = 5.0
shadow.distance = 3.0
shadow.color = aw.Color.black
rectangle.shadow = shadow

# 4. Save the document as PDF
pdf_path = os.path.join(output_dir, "shape_with_shadow.pdf")
doc.save(pdf_path)

print(f"PDF generated at: {pdf_path}")
```

**預期輸出**

執行腳本會印出確認訊息，例如：

```
PDF generated at: output/shape_with_shadow.pdf
```

開啟產生的 PDF 後會看到單頁，內含一個 200 pt × 100 pt 的矩形，帶有柔和的黑色外部陰影。

## 常見變化與邊緣案例

* **變更陰影顏色** – 將 `aw.Color.black` 替換為其他 `aw.Color` 值，例如 `aw.Color.red` 或 `aw.Color.from_argb(255, 0, 120, 215)`。
* **使用不同形狀** – 將 `aw.drawing.ShapeType.RECTANGLE` 改為 `OVAL`、`DIAMOND` 或其他支援的列舉值。
* **另存為 DOCX 而非 PDF** – 呼叫 `doc.save("output/shape.docx")` 以保留 Word 格式。
* **多個形狀** – 再次呼叫 `builder.insert_shape` 以建立其他形狀；每個形狀皆可擁有自己的 `ShadowEffect`。

**專業提示：** 若需將形狀放置於特定位置，可在插入後設定 `rectangle.left` 與 `rectangle.top`。這樣即可像素級精確控制位置。

## 結論

現在你已了解如何 **建立空白 Word 文件**、**在 Word 中插入形狀**、**新增外部陰影形狀**，以及 **使用 Python 另存為 PDF**。完整的程式碼範例展示了端對端的工作流程，說明則闡明了每個 API 呼叫的必要性。

接下來你可以探索更進階的樣式選項、在形狀內加入文字，或結合多個形狀以建立複雜圖表。嘗試不同的陰影參數以符合品牌的視覺語言，並將此方法整合至更大型的文件產生流程中。

祝開發順利！

## 接下來該學什麼？

以下教學涵蓋與本指南密切相關的主題，建立在所示技術之上。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助你精通其他 API 功能，並在自己的專案中探索替代實作方式。

- [建立矩形形狀、加入陰影並另存為 PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [從 Word 建立 PDF – 完整 Python 指南與 Aspose.Words](/words/english/python-net/document-conversion/create-pdf-from-word-complete-python-guide-with-aspose-words/)
- [在 Word 中使用 Aspose.Words 為形狀加入陰影 – 步驟說明](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}