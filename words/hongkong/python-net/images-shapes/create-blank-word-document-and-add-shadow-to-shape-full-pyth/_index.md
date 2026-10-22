---
category: general
date: 2026-07-20
description: 在 Python 中建立空白 Word 文件，並學習如何使用 Aspose.Words 為形狀添加陰影，包括如何添加陰影以及套用陰影顏色。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add shadow to shape
- how to add shadow
- apply shadow color
language: zh-hant
lastmod: 2026-07-20
og_description: 在 Python 中建立空白 Word 文件，了解如何為形狀添加陰影，以及應用陰影顏色的技巧，打造精緻文件。
og_image_alt: Screenshot showing a blank Word document with a shape that has a shadow
  applied
og_title: 建立空白 Word 文件 – 用 Python 為形狀加上陰影
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Create blank word document in Python and learn how to add shadow to
    shape with Aspose.Words, including how to add shadow and apply shadow color.
  headline: Create Blank Word Document and Add Shadow to Shape – Full Python Guide
  type: TechArticle
- description: Create blank word document in Python and learn how to add shadow to
    shape with Aspose.Words, including how to add shadow and apply shadow color.
  name: Create Blank Word Document and Add Shadow to Shape – Full Python Guide
  steps:
  - name: Why start with a blank document?
    text: Because it guarantees that no hidden styles or remnants from templates interfere
      with the **shadow** effect we’ll add later. A clean document also speeds up
      processing, especially when you generate thousands of files in a batch job.
  - name: Why these values?
    text: '- A **blur of 5.0** gives a gentle feathered look without making the shape
      look detached. - Offsets of **2.0** create a subtle depth effect—enough to be
      noticeable but not overpowering. - Using **black** is a safe default; however,
      you can replace it with `aw.drawing.Color.from_argb(255, 30, 144, 25'
  - name: Expected Output
    text: '- A single‑page Word file. - A 200 × 100 pt rectangle positioned 100 pt
      from the top‑left corner. - A shadow that is **blurred**, **offset** by 2 pt
      on both axes, and colored **black** (or your custom color).'
  type: HowTo
- questions:
  - answer: It’s the most neutral shape, making the shadow effect obvious.
    question: Why a rectangle?
  - answer: The code safely grabs the first paragraph or creates one, so it works
      on both fresh and populated docs.
    question: What if the document already has content?
  type: FAQPage
tags:
- Aspose.Words
- Python
- Document Automation
- Shape Styling
title: 建立空白 Word 文件並為形狀添加陰影 – 完整 Python 指南
url: /zh-hant/python/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-pyth/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立空白 Word 文件並為圖形加入陰影 – 完整 Python 教學

是否曾需要 **從頭建立空白 word 文件**，然後讓圖形呈現細緻的陰影？你並不孤單。無論是打造模板引擎或僅是快速製作報告，掌握如何為圖形加入陰影，都能讓你的 Word 檔案更具專業感。

在本教學中，我們將使用 Aspose.Words for Python via .NET 完整示範整個流程。首先建立空白 Word 文件，插入簡單圖形，接著 **為圖形加入陰影**，微調模糊度與位移，最後 **套用陰影顏色** 以符合品牌色彩。完成後，你將得到一段可直接在任何專案中執行的腳本。

## 你將學到

- 如何使用 Aspose.Words 程式化 **建立空白 word 文件**。
- **為圖形加入陰影** 的完整步驟與外觀控制方式。
- 為何 **加入陰影** 的細節（模糊、位移）對視覺層次感很重要。
- **套用陰影顏色** 的技巧，確保文件風格一致。
- 常見陷阱（例如圖形不存在、格式不支援）以及避免方法。

> **先備條件** – 需要 Python 3.8+ 以及已安裝 `aspose-words` 套件（`pip install aspose-words`）。不需要事先了解 Aspose，但具備 Python 物件的基本概念會更順手。

![Create blank word document with a shadowed shape](image.png){alt="建立帶有陰影的圖形的空白 word 文件"}

## 使用 Aspose.Words (Python) 建立空白 Word 文件

我們的第一件事是取得一個 **空白 Word 文件**，之後再填入內容。Aspose.Words 只需要一行程式碼即可完成：

```python
import aspose.words as aw

# Step 1: Instantiate a new, empty document
doc = aw.Document()
```

這行程式碼為我們提供了一張乾淨的畫布——就像全新紙張。背後 Aspose 會自動建立文件結構（章節、正文等），讓你不必處理低階 XML。

### 為什麼要從空白文件開始？

因為這樣能保證沒有隱藏樣式或模板遺留，避免影響之後要加入的 **陰影** 效果。乾淨的文件也能提升處理速度，特別是在批次產生上千檔案時。

## 插入圖形再加入陰影

沒有圖形怎麼加陰影？所以先在第一頁放一個簡單的矩形，這同時示範了 **為圖形加入陰影** 的實務流程。

```python
# Step 2: Create a rectangle shape (200x100 points) and add it to the first section
shape = aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
shape.width = 200
shape.height = 100
shape.left = 100   # Horizontal position from the left margin
shape.top = 100    # Vertical position from the top margin

# Add the shape to the document’s first paragraph (creates one if missing)
first_section = doc.first_section
first_paragraph = first_section.body.first_paragraph
if first_paragraph is None:
    first_paragraph = aw.Paragraph(doc)
    first_section.body.append_child(first_paragraph)

first_paragraph.append_child(shape)
```

幾點說明：

- **為什麼選矩形？** 它是最中性的形狀，能讓陰影效果一目了然。
- **如果文件已有內容呢？** 程式碼會安全地取得第一個段落或自行建立段落，適用於全新或已填充的文件。

## 為圖形加入陰影 – 步驟實作

現在已有圖形，該回答 **如何加入陰影** 的問題了。Aspose.Words 提供 `Shadow` 物件，可調整多項屬性。

```python
# Step 3: Enable a shadow on the shape
shape.shadow = aw.drawing.Shadow()
```

這行程式碼開啟陰影功能。預設陰影為黑色，模糊度適中且位移為 0。接下來我們自訂設定。

## 如何加入陰影：設定模糊、位移與顏色

陰影的視覺衝擊主要取決於三個參數：

1. **模糊半徑** – 控制邊緣的柔和程度。
2. **X/Y 位移** – 水平與垂直方向的偏移量。
3. **顏色** – 讓你配合企業色盤。

完整設定如下：

```python
# Step 4: Set the blur radius (higher = softer)
shape.shadow.blur = 5.0          # 5 points blur

# Step 5: Define horizontal and vertical offsets
shape.shadow.offset_x = 2.0      # 2 points to the right
shape.shadow.offset_y = 2.0      # 2 points down

# Step 6: Choose the shadow color (apply shadow color)
shape.shadow.color = aw.drawing.Color.black  # You can use any RGB value
```

### 為什麼選這些數值？

- **5.0 的模糊** 能產生柔和的羽化效果，同時不會讓圖形看起來脫離。
- **2.0 的位移** 創造微妙的深度感——足夠顯眼但不會過於突兀。
- **黑色** 是安全的預設；若想使用品牌藍，可改成 `aw.drawing.Color.from_argb(255, 30, 144, 255)`，呈現涼爽的藍色陰影。

## 套用陰影顏色以精確樣式

若需要非黑色陰影，只要執行 **套用陰影顏色** 步驟即可。Aspose 允許你定義任意 ARGB 顏色：

```python
# Example: Apply a navy blue shadow
navy = aw.drawing.Color.from_argb(255, 0, 0, 128)  # Fully opaque, RGB(0,0,128)
shape.shadow.color = navy
```

> **小技巧**：在企業模板中，將品牌顏色存於 JSON 檔，執行時載入。如此即可在不修改程式碼的情況下，為不同文件切換陰影顏色。

## 儲存文件並驗證結果

所有重點已完成，只剩下將檔案寫入磁碟。Aspose 支援多種格式，我們仍以通用的 DOCX 為例。

```python
# Step 7: Save the document to disk
output_path = "ShadowedShape.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

開啟 `ShadowedShape.docx`（使用 Microsoft Word 或 LibreOffice），即可看到帶有乾淨、柔和陰影的矩形——正是我們剛剛設定的樣子。

### 預期輸出

- 單頁 Word 檔。
- 大小為 200 × 100 pt 的矩形，左上角距離 100 pt。
- 陰影 **模糊**、在兩個軸向各 **偏移 2 pt**，顏色為 **黑色**（或自訂顏色）。

如果圖形出現卻沒有陰影，請確認在設定其他屬性之前已呼叫 `shape.shadow = aw.drawing.Shadow()`。順序很重要，因為必須先建立 `Shadow` 物件。

## 常見陷阱與邊緣案例

| 問題 | 為何會發生 | 解決方式 |
|------|------------|----------|
| `shape` 為 `None` | 在圖形尚未建立前就嘗試取得 | 先插入圖形（參見「插入圖形」段落） |
| Word 中看不到陰影 | 陰影顏色與背景相同（例如白色在白色上） | 改用對比色或提升模糊度 |
| 位移過大 | 陰影跑到頁面外，導致被裁切 | 標準頁面建議位移保持在 10 pt 以下 |
| 儲存時拋出 `PermissionError` | 檔案正被 Word 開啟 | 關閉檔案或改存至其他路徑 |

## 完整可執行範例（直接複製貼上）

```python
import aspose.words as aw

# 1️⃣ Create a blank Word document
doc = aw.Document()

# 2️⃣ Insert a rectangle shape
shape = aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
shape.width = 200
shape.height = 100
shape.left = 100
shape.top = 100

first_section = doc.first_section
first_paragraph = first_section.body.first_paragraph
if first_paragraph is None:
    first_paragraph = aw.Paragraph(doc)
    first_section.body.append_child(first_paragraph)

first_paragraph.append_child(shape)

# 3️⃣ Enable shadow
shape.shadow = aw.drawing.Shadow()

# 4️⃣ Configure blur, offset, and color
shape.shadow.blur = 5.0
shape.shadow.offset_x = 2.0
shape.shadow.offset_y = 2.0
shape.shadow.color = aw.drawing.Color.black   # Change to any color you like

# 5️⃣ Save the result
output_path = "ShadowedShape.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

執行腳本、開啟產生的檔案，即可看到陰影矩形——證明你已成功 **建立空白 word 文件**、**為圖形加入陰影**，並 **套用陰影顏色**。

## 後續步驟與相關主題

- **文字樣式** – 學習如何在圖形旁加入格式化段落。
- **多圖形處理** – 迴圈處理多個圖形，為每個圖形設定獨特陰影。
- **匯出為 PDF** – 將 DOCX 轉為 PDF，同時保留陰影效果（`doc.save("output.pdf")`）。
- **動態顏色** – 從設定檔讀取品牌顏色，程式化套用。

上述主題皆以本教學的核心概念為基礎，歡迎自行實驗。使用 Aspose.Words 越久，你會越欣賞其在文件自動化上的彈性。

---

**總結**：現在你已掌握 **建立空白 word 文件**、**為圖形加入陰影**、了解 **加入陰影** 的細節（模糊、位移），並能自信 **套用陰影顏色** 讓文件更顯精緻。下次報表專案就試試看吧——再也不會有乏味的矩形。

## 接下來該學什麼？

以下教學與本指南緊密相關，能延伸本章所示技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助你精通更多 API 功能，並在自己的專案中探索其他實作方式。

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}