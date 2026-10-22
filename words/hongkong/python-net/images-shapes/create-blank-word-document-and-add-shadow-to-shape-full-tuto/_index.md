---
category: general
date: 2026-07-20
description: 使用 Aspose.Words 建立空白 Word 文件並為圖形添加陰影。只需幾個步驟，即可學習如何調整陰影的不透明度與透明度。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add shadow to shape
- add shadow effect
- change shadow transparency
- change shadow opacity
language: zh-hant
lastmod: 2026-07-20
og_description: 使用 Aspose.Words 建立空白 Word 文件，並為形狀新增陰影效果。透過清晰的程式碼範例變更陰影的不透明度與透明度。
og_image_alt: Screenshot showing a Word document with a shape that has a semi‑transparent
  shadow
og_title: 建立空白 Word 文件並為形狀添加陰影 – 逐步指南
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Create blank Word document with Aspose.Words and add shadow to shape.
    Learn how to change shadow opacity and transparency in just a few steps.
  headline: Create Blank Word Document and Add Shadow to Shape – Full Tutorial
  type: TechArticle
- description: Create blank Word document with Aspose.Words and add shadow to shape.
    Learn how to change shadow opacity and transparency in just a few steps.
  name: Create Blank Word Document and Add Shadow to Shape – Full Tutorial
  steps:
  - name: Expected Output
    text: When you open **ShadowedShape.docx**, you should see a rectangle with a
      gray, semi‑transparent shadow that has a gentle blur. The shadow will be offset
      slightly down and to the right, giving the illusion that the shape is lifted
      off the page.
  - name: What if the document already contains multiple shapes?
    text: 'The current script grabs the *first* shape (`index 0`). To target a specific
      shape, change the index or iterate over all shapes:'
  - name: Can I change the shadow color?
    text: 'Absolutely. Shadow color is another property:'
  - name: How do I make the shadow offset differently?
    text: 'Adjust `distance_x` and `distance_y`:'
  - name: Does this work with older Word versions?
    text: Aspose.Words writes the modern OOXML format (`.docx`). Word 2007+ can open
      it without issues. For legacy `.doc` files, call `doc.save("file.doc", aw.SaveFormat.DOC)`—the
      shadow properties will still be preserved.
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
- Word Shapes
title: 建立空白 Word 文件並為形狀加入陰影 – 完整教學
url: /zh-hant/python/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-tuto/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立空白 Word 文件並為形狀添加陰影 – 完整教學

有沒有需要**建立空白 Word 文件**，然後讓形狀以細緻的陰影突顯出來？你並非唯一有此需求的人。在許多報告、傳單或內部儀表板中，一點深度就能把平面的矩形變成吸引目光的視覺提示。  

本指南將逐步說明如何使用 Aspose.Words for Python 建立全新的 Word 檔案、取得第一個形狀，然後**為形狀添加陰影**，同時調整其不透明度與模糊度。完成後，你將得到一份外觀精緻的文件——不需要手動調整。

> **你將獲得** – 完整可執行的腳本、每行程式碼意義的說明，以及處理未包含形狀的文件的技巧。

## Prerequisites

- 已安裝 Python 3.8 以上（任何較新的版本皆可）
- 透過 `pip install aspose-words` 安裝 Aspose.Words for Python
- 具備 Python 基礎以及 Word 中「形狀」概念的了解（例如文字方塊、圖片或自動圖形）

不需要其他函式庫；程式碼是自包含的。

## Step 1: Create a Blank Word Document with Aspose.Words

首先，我們需要一個乾淨的畫布。Aspose.Words 讓這變得非常簡單——只要實例化一個 `Document` 物件即可。

```python
import aspose.words as aw

# Step 1: Create a new blank document
doc = aw.Document()
print("✅ Blank Word document created.")
```

*為什麼這很重要*：`Document` 類別是所有操作的入口。從全新文件開始，可確保之後不會出現隱藏的格式問題。

## Step 2: Insert a Sample Shape (so we have something to shadow)

如果在空白檔案上執行腳本，嘗試取得形狀時會卡住——因為根本沒有形狀。讓我們加入一個簡單的矩形，讓後續步驟有目標可操作。

```python
# Step 2: Add a rectangle shape to the first page
builder = aw.DocumentBuilder(doc)
builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
print("🔲 Rectangle shape inserted.")
```

> **專業提示**：調整寬度/高度值 (200, 100) 以符合你的設計需求。較大的形狀能更清楚地顯示陰影。

## Step 3: Retrieve the First Shape in the Document

現在已有形狀，我們可以安全地取得它。`get_child` 方法會遍歷節點樹，返回第一個符合指定類型的節點。

```python
# Step 3: Retrieve the first shape (index 0) – true = deep search
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

if shape is None:
    raise ValueError("No shape found in the document.")
print(f"🕵️ Retrieved shape of type: {shape.shape_type}")
```

*為什麼要檢查 `None`*：在實務情況中，文件可能由其他地方產生，若缺少形狀會導致難以理解的 `AttributeError`。拋出明確的例外可節省除錯時間。

## Step 4: Add Shadow Effect – Change Shadow Opacity

陰影不僅是視覺裝飾；它還能傳達層次感。讓我們將不透明度設定為 75 %，使其半透明。

```python
# Step 4: Set shadow opacity (0.0 = fully transparent, 1.0 = fully opaque)
shape.shadow.opacity = 0.75
print(f"🌫️ Shadow opacity set to {shape.shadow.opacity}")
```

**了解不透明度**：此值為 0 到 1 之間的浮點數。較低的數值會讓陰影淡入背景，較高的數值則使其更突出。對於大多數類 UI 文件，0.5–0.8 看起來較自然。

## Step 5: Define Shadow Blur – Change Shadow Transparency

模糊半徑決定陰影邊緣的柔和程度。較大的半徑會產生更柔和的漸變，模擬自然光的散射。

```python
# Step 5: Define blur radius (in points) for a softer edge
shape.shadow.blur_radius = 8.0
print(f"🔍 Blur radius set to {shape.shadow.blur_radius} points")
```

*為什麼模糊很重要*：硬邊陰影會顯得廉價，而細緻的模糊則能在不壓倒內容的情況下增添深度。

## Step 6: Save the Document and Verify the Result

最後，我們將文件寫入磁碟。使用 Word 開啟產生的 `.docx`，即可看到帶有新陰影的矩形。

```python
output_path = "ShadowedShape.docx"
doc.save(output_path)
print(f"💾 Document saved as '{output_path}'. Open it in Word to see the effect.")
```

### Expected Output

當你開啟 **ShadowedShape.docx** 時，應該會看到一個帶有灰色、半透明且柔和模糊陰影的矩形。陰影會稍微向下與向右偏移，營造出形狀被從頁面抬起的錯覺。

## Edge Cases & Common Questions

### What if the document already contains multiple shapes?

目前的腳本會抓取*第一個*形狀（`index 0`）。若要定位特定形狀，可更改索引或遍歷所有形狀：

```python
for i in range(doc.get_child_nodes(aw.NodeType.SHAPE, True).count):
    shp = doc.get_child(aw.NodeType.SHAPE, i, True)
    # Apply shadow settings to each shape
    shp.shadow.opacity = 0.6
    shp.shadow.blur_radius = 5.0
```

### Can I change the shadow color?

當然可以。陰影顏色是另一個屬性：

```python
shape.shadow.color = aw.drawing.Color.black
```

### How do I make the shadow offset differently?

調整 `distance_x` 與 `distance_y`：

```python
shape.shadow.distance_x = 5   # shift right
shape.shadow.distance_y = 5   # shift down
```

### Does this work with older Word versions?

Aspose.Words 會寫入現代的 OOXML 格式（`.docx`）。Word 2007 以上皆可順利開啟。若是舊版 `.doc` 檔案，可呼叫 `doc.save("file.doc", aw.SaveFormat.DOC)`——陰影屬性仍會被保留。

## Full Script Recap

將所有步驟整合起來，以下是完整、可直接執行的範例：

```python
import aspose.words as aw

# Create a new blank document
doc = aw.Document()
print("✅ Blank Word document created.")

# Insert a rectangle shape (so we have something to shadow)
builder = aw.DocumentBuilder(doc)
builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
print("🔲 Rectangle shape inserted.")

# Retrieve the first shape in the document
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
if shape is None:
    raise ValueError("No shape found in the document.")
print(f"🕵️ Retrieved shape of type: {shape.shape_type}")

# Add shadow effect – change opacity
shape.shadow.opacity = 0.75
print(f"🌫️ Shadow opacity set to {shape.shadow.opacity}")

# Change shadow transparency – define blur radius
shape.shadow.blur_radius = 8.0
print(f"🔍 Blur radius set to {shape.shadow.blur_radius} points")

# Optional: tweak color and offset
shape.shadow.color = aw.drawing.Color.gray
shape.shadow.distance_x = 4
shape.shadow.distance_y = 4

# Save the document
output_path = "ShadowedShape.docx"
doc.save(output_path)
print(f"💾 Document saved as '{output_path}'. Open it in Word to see the effect.")
```

執行此腳本，開啟產生的檔案，你會看到形狀沐浴在雅緻的陰影中——正是精緻報告所需的效果。

## Conclusion

現在你已了解如何使用 Aspose.Words **建立空白 Word 文件**、插入形狀，並 **為形狀添加陰影**，同時掌握*變更陰影不透明度*與*變更陰影透明度*。步驟簡單明瞭，但視覺效果相當顯著。  

接下來，你可以探索對圖片 **添加陰影效果**、嘗試不同的 `blur_radius` 值，或將多個形狀合併為單一的複合圖形。若想更深入了解，請參閱 Aspose 的文件：[Shape Formatting](https://docs.aspose.com/words/python-net/shape/) 以及更廣泛的 [Document Automation](https://docs.aspose.com/words/python-net/) 指南。

有嘗試過的變化嗎？在下方留言——分享實務調整能讓社群更強大。祝編程愉快！

## What Should You Learn Next?

以下教學涵蓋與本指南緊密相關的主題，並在此基礎上進一步延伸。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助你精通更多 API 功能，並在專案中探索其他實作方式。

- [建立帶陰影矩形形狀的空白 Word 文件 – 步驟教學](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words 形狀陰影教學 – 在 C# 中為 Word 形狀添加陰影](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [使用 Aspose.Words 在 Word 中建立矩形形狀 – 步驟教學](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}