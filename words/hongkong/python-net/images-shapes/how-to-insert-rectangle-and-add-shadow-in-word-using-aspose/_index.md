---
category: general
date: 2026-05-30
description: 如何在 Word 中使用 Aspose 插入矩形並添加陰影 – 一個逐步的 Python 教學，教您建立帶有形狀陰影效果的 Word 文件。
draft: false
keywords:
- how to insert rectangle
- add shadow to shape
- how to add shape shadow
- apply shadow effect word
- create word document aspose
language: zh-hant
og_description: 如何使用 Aspose 在 Word 中插入矩形並添加陰影 – 學習在 Python 中建立具有形狀陰影效果的 Word 文件。
og_title: 如何在 Word 中使用 Aspose 插入矩形並加上陰影
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: How to insert rectangle and add shadow in Word using Aspose – a step‑by‑step
    Python guide to create a Word document with shape shadow effect.
  headline: How to insert rectangle and add shadow in Word using Aspose
  type: TechArticle
- description: How to insert rectangle and add shadow in Word using Aspose – a step‑by‑step
    Python guide to create a Word document with shape shadow effect.
  name: How to insert rectangle and add shadow in Word using Aspose
  steps:
  - name: What each property does
    text: '| Property | Effect | Typical Range | |----------|--------|---------------|
      | `visible` | Turns the shadow on/off | `True` / `False` | | `distance` | How
      far the shadow sits from the shape | 2 – 10 pts | | `blur` | Softness of the
      shadow edges | 4 – 12 pts | | `color` | Shadow hue; dark gray is a sa'
  - name: Adding Multiple Shapes
    text: If you need more than one rectangle, simply repeat the `insert_shape` call.
      Remember to move the builder’s cursor (`builder.move_to(shape)`) or adjust `shape.left`/`shape.top`
      to avoid overlap.
  - name: Changing the Shape Type
    text: While this guide focuses on rectangles, the same pattern works for ovals,
      stars, or custom free‑form shapes. Replace `ShapeType.RECTANGLE` with `ShapeType.OVAL`,
      `ShapeType.CLOUD`, etc., and the shadow settings remain identical.
  - name: Saving to Other Formats
    text: 'Aspose.Words can export to PDF, PNG, or even XPS with a single line:'
  - name: Handling Large Documents
    text: When generating massive reports, consider calling `doc.update_page_layout()`
      after inserting all shapes. This forces a layout pass and can improve performance
      when you later convert to PDF.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word Automation
title: 如何使用 Aspose 在 Word 中插入矩形並加入陰影
url: /zh-hant/python/images-shapes/how-to-insert-rectangle-and-add-shadow-in-word-using-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中使用 Aspose 插入矩形並添加陰影

有沒有想過 **如何在不開啟 UI 的情況下插入矩形** 到 Word 檔案？你並不孤單。許多開發者需要即時產生報表、發票或證書，而在簡單的矩形上加上一個漂亮的陰影，能讓輸出看起來更精緻。在本教學中，我們將一步步說明如何建立 Word 文件、放入矩形圖形，並使用 Aspose.Words for Python 套用真實感的陰影。

我們會從設定 Aspose 套件開始，教你調整陰影的距離、模糊度與不透明度。完成後，你將擁有一段可重複使用的程式碼，能直接放入任何自動化流程。沒有魔法，只有清晰的程式碼與實用小技巧。

## 前置條件

在開始之前，請確保你已具備：

- 已安裝 Python 3.8+（程式碼在 3.9、3.10 以及更新版本皆可執行）
- 有效的 Aspose.Words for Python 授權或免費評估金鑰
- 透過 `pip install aspose-words` 安裝 `aspose-words` 套件
- 一個可寫入的資料夾，用來儲存產生的 **create word document aspose**  

就這樣——不需要額外的 DLL、也不需要 COM interop，純粹使用 Python。

## 第一步：初始化文件（How to create word document aspose）

首先，你需要一個全新的 `Document` 物件。把它想成一張白紙。以下程式碼會建立文件以及一個 `DocumentBuilder`，讓我們可以插入圖形。

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

*為什麼這很重要：* `DocumentBuilder` 提供高階 API，讓你可以加入段落、表格，甚至 **圖形**，而不必直接操作底層節點樹。如果直接操作節點，程式碼會變得冗長且難以維護。

## 第二步：插入矩形（how to insert rectangle）

現在我們真正 **how to insert rectangle**。Aspose.Words 把矩形視為一種通用圖形類型。你需要以點 (point) 為單位指定寬度與高度（1 point ≈ 1/72 英吋），可自行調整數值以符合版面需求。

```python
# Step 2: Insert a rectangle shape of the desired size
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

> **專業提示：** 若需要將矩形放置在頁面的特定位置，插入後請設定 `shape.left` 與 `shape.top`。這樣即可精確控制位置。

## 第三步：取得圖形的陰影格式（add shadow to shape）

圖形的視覺效果由 `ShadowFormat` 控制。取得它之後，我們就能存取所有定義陰影外觀的屬性。

```python
# Step 3: Access the shape's shadow format
shadow = shape.shadow_format
```

此時陰影仍是隱形的——就像一層等待指令的隱藏圖層。

## 第四步：設定陰影（how to add shape shadow, apply shadow effect word）

魔法就從這裡開始。我們會開啟陰影並微調外觀。以下數值會產生柔和的對角陰影，適用於大多數文件，你也可以自行實驗。

```python
# Step 4: Make the shadow visible and configure its appearance
shadow.visible = True                # Show the shadow
shadow.distance = 5.0                # Distance from the shape (points)
shadow.blur = 8.0                    # Blur radius (points)
shadow.color = aw.Color.dark_grey   # Shadow color
shadow.opacity = 0.6                 # Opacity (0‑1)
shadow.angle = 45.0                  # Direction in degrees
```

### 各屬性說明

| Property | Effect | Typical Range |
|----------|--------|---------------|
| `visible` | 開啟/關閉陰影 | `True` / `False` |
| `distance` | 陰影與圖形的距離 | 2 – 10 pts |
| `blur` | 陰影邊緣的柔和程度 | 4 – 12 pts |
| `color` | 陰影顏色；深灰色是安全預設 | 任意 `aw.Color` |
| `opacity` | 透明度；0 = 隱形，1 = 實心 | 0.3 – 0.8（建議的柔和外觀） |
| `angle` | 光源方向 | 0 – 360° |

**為什麼要調整這些？** 透過適當的陰影設定，平面的矩形看起來彷彿浮在頁面上，增添深度而不需使用圖片。若 `opacity` 設得太高，陰影會顯得生硬；太低則會消失不見。

## 第五步：儲存文件（create word document aspose）

最後，將檔案寫入磁碟。你可以使用 Aspose.Words 支援的任何副檔名（`.docx`、`.pdf`、`.html`）。本教學以 `.docx` 為例。

```python
# Step 5: Save the document with the shaped shadow
output_path = "output/ShapeWithShadow.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

在 Microsoft Word 中開啟產生的檔案，你會看到一個帶有細緻陰影的矩形——正如專業範本的預期效果。

![how to insert rectangle shape with shadow using Aspose.Words](/images/rectangle-shadow.png){alt="使用 Aspose.Words 插入帶陰影的矩形圖形"}

*上圖顯示已套用陰影的矩形。留意柔和的模糊與 45° 角度，營造自然感。*

## 常見變化與邊緣案例

### 新增多個圖形

若需要多個矩形，只要重複呼叫 `insert_shape` 即可。記得移動 builder 的游標 (`builder.move_to(shape)`) 或調整 `shape.left`/`shape.top`，避免重疊。

```python
# Example: Insert a second rectangle 200 points to the right
second_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
second_shape.left = shape.left + 200
second_shape.top = shape.top
```

### 更換圖形類型

本指南以矩形為例，其他圖形（橢圓、星形、自由形狀等）同樣適用。只要把 `ShapeType.RECTANGLE` 換成 `ShapeType.OVAL`、`ShapeType.CLOUD` 等，陰影設定不需變更。

### 儲存為其他格式

Aspose.Words 只需一行程式碼即可匯出為 PDF、PNG 或 XPS：

```python
doc.save("output/ShapeWithShadow.pdf")
```

陰影的呈現會在所有格式中保留，因此 PDF 看起來會與 Word 完全相同。

### 處理大型文件

產生大量報表時，建議在插入完所有圖形後呼叫 `doc.update_page_layout()`。這會強制重新排版，提升之後轉 PDF 的效能。

## 完整範例（結合所有步驟）

以下是完整腳本，可直接複製貼上為 `rectangle_shadow.py`，然後以 `python rectangle_shadow.py` 執行，產生的檔案會放在 `output` 資料夾。

```python
import aspose.words as aw
import os

# Ensure the output directory exists
os.makedirs("output", exist_ok=True)

# Initialize the document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Insert a rectangle
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

# Configure the shadow
shadow = shape.shadow_format
shadow.visible = True
shadow.distance = 5.0
shadow.blur = 8.0
shadow.color = aw.Color.dark_grey
shadow.opacity = 0.6
shadow.angle = 45.0

# Save the document
output_path = "output/ShapeWithShadow.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

執行此腳本會產生與前述說明完全相同的文件。隨意調整數值；程式碼刻意保持簡潔，讓你可以放心嘗試。

## 常見問答

**Q: 這在 Linux 上可用嗎？**


## 接下來該學什麼？

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}