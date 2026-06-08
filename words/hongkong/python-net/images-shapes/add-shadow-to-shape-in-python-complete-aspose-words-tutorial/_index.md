---
category: general
date: 2026-06-08
description: 使用 Aspose.Words for Python 為形狀添加陰影，並在幾個步驟內設定形狀填充顏色。了解完整工作流程及可執行程式碼。
draft: false
keywords:
- add shadow to shape
- set shape fill color
- Aspose.Words Python shadow
- shape formatting Python
- PDF generation Aspose
language: zh-hant
og_description: 使用 Aspose.Words for Python 為形狀添加陰影，並即時設定形狀填充顏色。跟隨此一步一步的教學以產生 PDF 輸出。
og_title: 在 Python 中為形狀添加陰影 – 完整 Aspose.Words 指南
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Add shadow to shape using Aspose.Words for Python and set shape fill
    color in just a few steps. Learn the full workflow with runnable code.
  headline: Add Shadow to Shape in Python – Complete Aspose.Words Tutorial
  type: TechArticle
- description: Add shadow to shape using Aspose.Words for Python and set shape fill
    color in just a few steps. Learn the full workflow with runnable code.
  name: Add Shadow to Shape in Python – Complete Aspose.Words Tutorial
  steps:
  - name: Create the Document and Builder
    text: '```python import aspose.words as aw from aspose.words.drawing import ShadowEffect,
      ShadowType, Color'
  - name: Insert a Rectangle Shape and Set Its Fill Color
    text: '```python # Insert a rectangle shape of width 200 points and height 100
      points. rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE,
      200, 100)'
  - name: Define the Shadow Effect
    text: '```python # Create a new shadow effect object. shape_shadow = ShadowEffect()
      shape_shadow.type = ShadowType.OUTER # outer shadow around the shape shape_shadow.blur_radius
      = 10.0 # softer edges shape_shadow.distance = 5.0 # how far the shadow sits
      from the shape shape_shadow.direction = 45 # angle in'
  - name: Apply the Shadow to the Shape
    text: '```python # Attach the shadow effect to the rectangle. rectangle_shape.shadow_effect
      = shape_shadow ```'
  - name: Save the Document as PDF
    text: '```python # Choose a folder you have write access to. output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
      doc.save(output_path) print(f"Document saved to {output_path}") ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
title: 在 Python 中為形狀添加陰影 – 完整 Aspose.Words 教程
url: /zh-hant/python/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Python 中為形狀添加陰影 – 完整的 Aspose.Words 教程

有沒有想過在使用 Aspose.Words for Python 產生文件時，如何 **為形狀添加陰影**？你並不是唯一有此疑問的人。無論你是在建立報告範本、行銷傳單，或是技術圖表，一個細緻的陰影都能讓矩形更突出，顯得更專業。  

在本指南中，我們還會示範 **如何設定形狀填色**，讓你得到一個完整樣式的矩形，隨時可匯出為 PDF。解決方案簡單直接，程式碼可直接執行，且每一行的原理都以淺顯英文說明。

## 本教程涵蓋內容

- 初始化 Aspose.Words 文件與 Builder。  
- 插入矩形形狀並 **設定其填色**。  
- 定義並套用 **陰影效果** 至該形狀。  
- 將結果儲存為 PDF。  
- 完整可執行範例以及常見陷阱的提示。

閱讀完本文後，你只需幾行 Python 程式碼，即可在任何 Word 或 PDF 檔案中插入樣式化的矩形。無需外部工具，也不必猜測。

> **先決條件** – 需要 Python 3.7 以上以及 `aspose-words` 套件（`pip install aspose-words`）。任意你喜好的 IDE 或文字編輯器皆可；Visual Studio Code 表現優秀。

---

## 為形狀添加陰影 – 步驟說明

以下我們將流程拆解為多個邏輯區塊。每一步都提供所需的完整程式碼、簡短的 *原因* 說明，以及避免日後卡關的快速提示。

### 步驟 1：建立文件與 Builder

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowType, Color

# Create a new, empty document.
doc = aw.Document()

# DocumentBuilder gives us a convenient way to add content.
builder = aw.DocumentBuilder(doc)
```

**為什麼重要**：`Document` 是所有內容的容器——頁面、樣式、圖片與形狀。`DocumentBuilder` 是高階 API，讓我們在不必關注底層節點樹的情況下放置物件。

### 步驟 2：插入矩形形狀並設定其填色

```python
# Insert a rectangle shape of width 200 points and height 100 points.
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# Set the interior color of the shape.
rectangle_shape.fill_color = Color.BLUE   # <-- set shape fill color
```

**為什麼重要**：形狀就像陰影的畫布。透過 **設定形狀填色**，確保矩形不只是透明的方框，而是可被陰影突顯的可見元素。你可以將 `Color.BLUE` 替換為任何 RGB 值，甚至是漸層，以獲得更多變化。

> **專業提示**：如果你打算在多個形狀中重複使用相同顏色，請將其存入變數（`my_fill = Color.from_argb(0, 120, 200, 255)`），並重複使用該參考。

### 步驟 3：定義陰影效果

```python
# Create a new shadow effect object.
shape_shadow = ShadowEffect()
shape_shadow.type = ShadowType.OUTER          # outer shadow around the shape
shape_shadow.blur_radius = 10.0               # softer edges
shape_shadow.distance = 5.0                   # how far the shadow sits from the shape
shape_shadow.direction = 45                   # angle in degrees (45° = diagonal)
shape_shadow.color = Color.from_argb(128, 0, 0, 0)  # semi‑transparent black
```

**為什麼重要**：陰影不只是視覺噱頭；它傳達深度與層次感。`blur_radius` 控制柔和度，`distance` 決定偏移距離，`direction` 則模擬光源方向。依據你的設計語言調整這些數值。

### 步驟 4：將陰影套用至形狀

```python
# Attach the shadow effect to the rectangle.
rectangle_shape.shadow_effect = shape_shadow
```

**為什麼重要**：在執行此行之前，形狀仍保持平面。指派 `shadow_effect` 後，Aspose.Words 會在儲存文件時以定義好的陰影渲染矩形。

### 步驟 5：將文件儲存為 PDF

```python
# Choose a folder you have write access to.
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

**為什麼重要**：儲存為 PDF 可鎖定視覺樣式，使陰影如同設計時般呈現。若日後需進一步編輯，也可儲存為 `.docx`——Aspose.Words 能無縫處理兩種格式。

---

## 設定形狀填色 – 客製外觀

若需要不同色調，可將 `Color.BLUE` 的指定替換為以下任一範例：

```python
# Solid RGB color
rectangle_shape.fill_color = Color.from_argb(255, 255, 165, 0)   # orange

# Semi‑transparent fill
rectangle_shape.fill_color = Color.from_argb(128, 0, 128, 0)    # 50% transparent green
```

> **為什麼可能需要**：半透明填色搭配陰影，可產生在現代 UI 模型中常見的「玻璃」效果。

## 完整可執行範例

以下是一整段腳本。將其複製貼上至名為 `shadow_shape.py` 的檔案並執行——前提是已安裝 `aspose-words`。

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowType, Color

# 1️⃣ Create document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2️⃣ Insert rectangle and set fill color
rect = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
rect.fill_color = Color.BLUE          # set shape fill color

# 3️⃣ Configure shadow
shadow = ShadowEffect()
shadow.type = ShadowType.OUTER
shadow.blur_radius = 10.0
shadow.distance = 5.0
shadow.direction = 45
shadow.color = Color.from_argb(128, 0, 0, 0)

# 4️⃣ Apply shadow
rect.shadow_effect = shadow

# 5️⃣ Save as PDF
output = "ShadowShape.pdf"
doc.save(output)
print(f"✅ PDF generated: {output}")
```

**預期輸出**：開啟 `ShadowShape.pdf`，你會看到一個藍色矩形，右下角有柔和的對角線黑色陰影。陰影略帶模糊，使形狀呈現提升的感覺。

---

## 常見陷阱與專業提示

| Issue | Why it Happens | Fix |
|------|----------------|-----|
| **陰影未顯示** | 形狀的填色完全透明，或 PDF 檢視器關閉了陰影顯示。 | 確保 `fill_color` 不透明（`alpha = 255`），或調整陰影 `color` 的透明度。 |
| **檔案路徑錯誤** | `YOUR_DIRECTORY` 不存在，或你沒有寫入權限。 | 在 `doc.save` 前使用 `os.makedirs("YOUR_DIRECTORY", exist_ok=True)`。 |
| **匯入錯誤** | 嘗試從錯誤的子模組匯入 `ShadowEffect`。 | 精確如示範匯入：`from aspose.words.drawing import ShadowEffect, ShadowType, Color`。 |
| **顏色異常** | 使用 `Color.from_argb` 時順序錯誤（alpha、red、green、blue）。 | 記住順序：**alpha**、**red**、**green**、**blue**。 |

---

## 往後步驟 – 擴充你的形狀工具箱

既然你已了解如何 **為形狀添加陰影** 以及 **設定形狀填色**，接下來可以探索：

- **漸層填色** (`LinearGradientBrush`) 以獲得更豐富的背景。  
- **多重陰影**（內部 + 外部）透過串接 `ShadowEffect` 物件實現。  
- **其他形狀類型** (`Ellipse`, `Polygon`) 用於建立圖示或流程圖元件。  
- **將 PDF 嵌入**於使用 Flask 或 Django 的網頁回應或電子郵件附件中。

上述主題皆基於本指南的核心概念，讓你能輕鬆上手。

---

## 結論

我們已完整說明在 Aspose.Words for Python 中 **為形狀添加陰影** 並 **設定形狀填色** 的全過程。從文件建立到 PDF 匯出，程式碼自成一體，可直接投入生產使用。  

隨意調整模糊半徑、距離或顏色，以符合品牌指引。若遇到特殊情況或有功能需求，歡迎在下方留言——祝開發愉快！

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，並以此為基礎。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助你掌握更多 API 功能，並在自己的專案中探索其他實作方式。

- [在 Python 中設定 Aspose.Words 授權](/words/english/python-net/getting-started/aspose-words-license-python-setup/)
- [在 Word 中建立矩形形狀 – Aspose.Words 步驟說明](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words 形狀陰影教學 – 在 C# 中為 Word 形狀添加陰影](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}