---
category: general
date: 2026-09-30
description: 學習如何使用 Aspose.Words for Python 建立矩形形狀、為形狀套用陰影，並儲存帶有形狀的 Word 文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- how to add shape
- apply shadow to shape
- set shadow blur
- save word with shape
language: zh-hant
lastmod: 2026-09-30
og_description: 快速在 Word 文件中建立矩形形狀。本教學示範如何新增形狀、為形狀套用陰影、設定陰影模糊，以及儲存含有形狀的 Word 文件。
og_image_alt: Screenshot of a Word document showing a rectangle shape with a soft
  shadow
og_title: 使用 Python 在 Word 中建立矩形形狀 – 逐步指南
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Learn how to create rectangle shape, apply shadow to shape, and save
    Word with shape using Aspose.Words for Python.
  headline: How to create rectangle shape in a Word document using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- Shapes
title: 如何使用 Python 在 Word 文件中建立矩形形狀
url: /zh-hant/python/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Python 在 Word 文件中建立矩形形狀

如果您需要在 Word 檔案中**建立矩形形狀**，本教學將提供完整且可執行的解決方案。您將會看到如何加入形狀、套用陰影效果、調整模糊程度，最後**儲存含形狀的 Word**，讓結果可以在 Microsoft Word 或任何相容的檢視器中開啟。

此範例使用 **Aspose.Words for Python via .NET**，這是一套讓您在未安裝 Microsoft Office 的環境下操作 Word 文件的函式庫。您不需要事先了解 API，只要具備基本的 Python 知識即可。

## 您將達成的目標

- 在新文件的第一個節點插入一個矩形。  
- 透過設定模糊、偏移與顏色，為矩形配置柔和的陰影。  
- 將文件寫入磁碟並驗證視覺效果。

## 前置條件

- Python 3.8 或更新版本。  
- 已安裝 `aspose-words` 套件（`pip install aspose-words`）。  
- 具備寫入輸出目錄的權限。

## 建立矩形形狀並設定外觀

第一步是建立一個空白文件，並在其中加入矩形形狀。此形狀將作為陰影效果的畫布。

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Step 1: Create a new blank document
doc = aw.Document()

# Step 2: Add a rectangle shape to the first section
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Optional: Define the shape’s size and position (in points)
shape.width = aw.ConvertUtil.inch_to_point(2)   # 2 inches wide
shape.height = aw.ConvertUtil.inch_to_point(1)  # 1 inch tall
shape.left = aw.ConvertUtil.inch_to_point(1)    # 1 inch from the left margin
shape.top = aw.ConvertUtil.inch_to_point(1)     # 1 inch from the top margin
```

**為什麼這很重要：**  
建立矩形可讓您取得具體的物件（`shape`），之後即可為其設定樣式。明確指定尺寸可確保形狀在各平台上呈現一致。

## 如何將形狀加入 Word 文件

雖然上述程式碼已將矩形加入文件，您日後可能還會加入其他形狀（例如圓形、箭頭）。相同的模式適用：在文件的 body 上呼叫 `append_child`，並傳入想要的 `ShapeType`。

```python
# Example: Adding a second shape – an ellipse
ellipse = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.ELLIPSE)
)
ellipse.width = aw.ConvertUtil.inch_to_point(1.5)
ellipse.height = aw.ConvertUtil.inch_to_point(1)
ellipse.left = aw.ConvertUtil.inch_to_point(3.5)
ellipse.top = aw.ConvertUtil.inch_to_point(1)
```

**小技巧：** 使用 `ShapeType` 列舉可瀏覽所有支援的形狀。這樣可讓程式碼更易讀，且避免使用魔術數字。

## 為形狀套用陰影並設定陰影模糊

陰影能為圖形增添深度與視覺趣味。`ShadowEffect` 類別讓您控制模糊、偏移與顏色。以下範例為矩形套用柔和的黑色陰影。

```python
# Step 3: Configure a shadow effect for the rectangle
shadow = ShadowEffect()
shadow.blur = 5.0          # Sets the softness of the shadow edge
shadow.offset_x = 2.0      # Horizontal displacement from the shape
shadow.offset_y = 2.0      # Vertical displacement from the shape
shadow.color = aw.Color.black

# Step 4: Apply the shadow effect to the shape
shape.shadow = shadow
```

**為什麼要設定模糊？**  
`blur` 決定陰影的散射程度。低值（例如 1.0）會產生銳利的邊緣，而較高的值（例如 5.0）則會產生柔和的漸層，通常較具美感。

**邊緣情況：** 若將 `blur` 設為 0，陰影會變成實心輪廓。某些檢視器可能會產生鋸齒狀的鋸齒，建議使用大於 0 的值以取得較平滑的輸出。

## 儲存含形狀的 Word

將文件持久化即完成所有變更。`save` 方法會寫出 `.docx` 檔案，任何現代的 Word 處理程式皆可開啟。

```python
# Step 5: Save the document to see the result
output_path = "output.docx"   # Adjust the path as needed
doc.save(output_path)
print(f"Document saved to {output_path}")
```

當您開啟 `output.docx` 時，會看到矩形位於左上角一英吋處，並帶有向右下方偏移兩點的柔和黑色陰影。陰影的模糊效果讓形狀看起來彷彿浮在頁面上。

**進階小技巧：** 若需要在迴圈中產生大量文件，可重複使用同一個 `Document` 實例，並在每次迭代前清空其 body，以降低記憶體使用。

## 常見變化與除錯

| 情境 | 需要變更的項目 | 原因 |
|-----------|----------------|--------|
| 不同的陰影顏色 | `shadow.color = aw.Color.red` | 使用品牌色或突顯重要形狀。 |
| 陰影偏移較大 | 增加 `shadow.offset_x`/`offset_y` | 在 UI 模型中強調深度。 |
| 完全不使用陰影 | 移除 `shape.shadow = shadow` 那一行 | 適用於極簡報告。 |
| 輸出為 PDF 而非 DOCX | `doc.save("output.pdf")` | PDF 適合唯讀分發。 |

如果形狀未出現，請確認您已將它加入正確的節點（`get_first_section()`），且文件在修改後已正確儲存。

## 完整、可執行的範例

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Create a new blank document
doc = aw.Document()

# Add a rectangle shape
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
shape.width = aw.ConvertUtil.inch_to_point(2)
shape.height = aw.ConvertUtil.inch_to_point(1)
shape.left = aw.ConvertUtil.inch_to_point(1)
shape.top = aw.ConvertUtil.inch_to_point(1)

# Configure and apply a shadow
shadow = ShadowEffect()
shadow.blur = 5.0
shadow.offset_x = 2.0
shadow.offset_y = 2.0
shadow.color = aw.Color.black
shape.shadow = shadow

# Save the document
output_path = "output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

執行腳本後會產生 `output.docx`，其中包含帶有柔和陰影的矩形。於 Microsoft Word 開啟檔案，即可驗證視覺效果是否符合說明。

## 結論

您現在已掌握如何**建立矩形形狀**、**將形狀加入 Word 文件**、**為形狀套用陰影**、**設定陰影模糊**，以及最後**儲存含形狀的 Word**，全部皆透過 Aspose.Words for Python 完成。相同的模式亦可延伸至其他形狀類型、顏色與效果，讓您在不依賴 Office 自動化的情況下，完整控制文件圖形。

**下一步建議**

- 嘗試使用 `Shape.fill` 加入漸層或圖片背景。  
- 使用 `Paragraph` 物件在矩形內放置文字。  
- 結合多個形狀建構複雜圖表，然後匯出為 PDF 供分發。  

歡迎依需求自行調整程式碼，並在留言區分享您的成果！

## 接下來該學什麼？

以下教學與本指南緊密相關，能進一步深化您所學的技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，並探索在專案中的其他實作方式。

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}