---
category: general
date: 2026-06-24
description: 使用 Aspose.Words 在 Python 中建立矩形形狀，學習如何為形狀添加陰影、設定陰影角度，並在數分鐘內將文件另存為 PDF。
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shape shadow
- set shadow angle
language: zh-hant
og_description: 在 Python 中建立矩形形狀，為形狀添加陰影，設定陰影角度，並使用 Aspose.Words 將文件儲存為 PDF。請跟隨此一步一步的指南。
og_title: 在 Python 中建立矩形形狀 – 完整 Aspose.Words 教程
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  headline: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  name: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: What if I need a different shape?
    text: Aspose.Words supports many `ShapeType` values (ellipse, star, callout, etc.).
      Simply replace `aw.drawing.ShapeType.RECTANGLE` with the desired enum, like
      `aw.drawing.ShapeType.ELLIPSE`.
  - name: Can I add multiple shadows?
    text: The API exposes only one `ShadowFormat` per shape, but you can simulate
      multiple shadows by duplicating the shape, offsetting each copy, and adjusting
      transparency.
  - name: How do I change the shadow color to match my brand?
    text: Just set `shadow.color` to any `aw.drawing.Color`. For a brand blue, use
      `aw.drawing.Color.from_argb(255, 0, 120, 215)`.
  - name: What about saving as DOCX instead of PDF?
    text: Replace `document.save(pdf_path)` with `document.save("output/shadowed_rectangle.docx")`.
      The shadow rendering is preserved across both formats.
  - name: Does the shadow work on older PDF viewers?
    text: Aspose.Words renders the shadow as a vector effect, which is widely supported.
      However, very old viewers might flatten the effect; testing on your target audience’s
      devices is always a good habit.
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: 在 Python 中建立矩形形狀 – 完整 Aspose.Words 指南
url: /zh-hant/python/images-shapes/create-rectangle-shape-in-python-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Python 中建立矩形形狀 – 完整 Aspose.Words 指南

有沒有想過要如何在 Word 文件中使用 Python **create rectangle shape**？也許你需要一個醒目的說明框、圖表的視覺提示，或只是想在報告中加入一個漂亮的矩形。無論是哪種情況，你都來對地方了。本教學將一步步說明整個流程——從插入矩形、加入細緻陰影、調整陰影角度，最後 **save document as PDF**，讓你可以隨時分享。

我們將使用 **Aspose.Words for Python via .NET**，這是一套強大的函式庫，讓你在不開啟 Word 的情況下操作 Word 檔案。完成本指南後，你將能自信地回答「如何 add shape shadow」的問題，並擁有一段可直接放入任何專案的完整腳本。

---

## 需要的環境

在開始之前，請確保你已具備以下條件：

- 已在電腦上安裝 **Python 3.8+**。  
- 已安裝 **Aspose.Words for Python via .NET**（`aspose-words` 套件）。使用以下指令安裝：

  ```bash
  pip install aspose-words
  ```

- 有一個可寫入的資料夾，用來存放產生的 PDF。  
- （可選）IDE 或文字編輯器——VS Code 表現不錯。

就這樣。無需額外 DLL、也不需要安裝 Office，只要一個 pip 套件即可。

---

## 第一步：設定 Document 與 Builder

首先，你需要建立 **create rectangle shape** 所需的物件：`Document` 與 `DocumentBuilder`。把 Builder 想成你的筆，它會替你繪製所有內容。

```python
import aspose.words as aw

# Initialize a new blank document
document = aw.Document()

# DocumentBuilder gives us a convenient way to add content
builder = aw.DocumentBuilder(document)
```

> **為什麼這很重要：** `Document` 物件代表整個 .docx 檔案，而 `DocumentBuilder` 提供 `insert_shape` 等方法，讓繪製圖形變得輕而易舉。

---

## 第二步：插入矩形形狀

有了 Builder 後，我們終於可以 **create rectangle shape**。`insert_shape` 方法需要三個參數：形狀類型、寬度與高度。我們使用 200 pt 寬、100 pt 高，比例剛好。

```python
# Insert a rectangle with a width of 200 points and a height of 100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

此時，你已成功在文件中 **create rectangle shape**。如果稍後開啟產生的 DOCX（我們之後會示範），就會看到一個普通的矩形出現在游標所在位置。

---

## 第三步：取得陰影格式物件

要 **add shadow to shape**，首先必須取得該形狀的陰影格式。Aspose.Words 中的每個形狀都有 `shadow_format` 屬性，提供所有與陰影相關的設定。

```python
# Grab the shadow formatting object for later tweaks
shadow = rectangle.shadow_format
```

取得 `shadow` 參考後，我們就能在幾行程式碼內切換可見性、模糊度、距離、角度、顏色與透明度。

---

## 第四步：啟用陰影並設定外觀

接下來就是魔法時刻。我們將 **add shadow to shape**、稍微模糊、稍作偏移、設定方向（即 **set shadow angle**），並給予半透明的黑色調。

```python
# Turn the shadow on
shadow.visible = True

# Soften the edges – a blur radius of 8 points looks natural
shadow.blur_radius = 8.0

# Push the shadow away from the rectangle by 5 points
shadow.distance = 5.0

# Set the direction of the light source – 45 degrees creates a diagonal drop
shadow.angle = 45

# Choose a color; black works well for most documents
shadow.color = aw.drawing.Color.black

# Make the shadow 30 % transparent for a subtle effect
shadow.transparency = 0.3
```

> **專業小技巧：** 若想要更戲劇化的效果，可提升 `blur_radius` 或降低 `transparency`。相反地，若想要銳利且完全不透明的陰影，只需將 `blur_radius = 0` 且 `transparency = 0` 即可。

---

## 第五步：將文件另存為 PDF

我們已 **create rectangle shape**、已 **add shadow to shape**，現在要 **save document as PDF**，讓結果在任何裝置上都保持一致。Aspose.Words 只需要一行程式碼即可完成。

```python
# Define where you want the PDF to land
output_path = "output/shadowed_rectangle.pdf"

# Save the whole document (including the rectangle with its shadow) as PDF
document.save(output_path)
print(f"PDF saved to {output_path}")
```

執行腳本後，`output` 資料夾會產生 `shadowed_rectangle.pdf`。用任何 PDF 閱讀器開啟，你會看到一個乾淨的矩形，帶有 45 度的柔和陰影——正是我們剛剛設定的樣子。

---

## 完整範例程式

以下是結合上述所有步驟的完整可執行腳本。將它複製貼上成 `create_rectangle_with_shadow.py`，然後執行 `python create_rectangle_with_shadow.py`。

```python
import aspose.words as aw
import os

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Initialize document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert the rectangle shape (200 pt × 100 pt)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Access shadow formatting
shadow = rectangle.shadow_format

# 4️⃣ Configure shadow – visible, blurred, offset, angled, colored, semi‑transparent
shadow.visible = True
shadow.blur_radius = 8.0          # softer edges
shadow.distance = 5.0            # how far the shadow sits from the shape
shadow.angle = 45                # direction in degrees – this is the **set shadow angle** step
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.3        # 30 % transparent

# 5️⃣ Save the document as PDF
pdf_path = os.path.join(output_dir, "shadowed_rectangle.pdf")
document.save(pdf_path)

print(f"✅ PDF created at: {pdf_path}")
```

**預期結果：** 產生一個 PDF 檔，顯示單一矩形與柔和的對角陰影。沒有多餘的頁面、沒有隱藏的雜訊——只有我們精心打造的形狀。

---

## 常見問題與特殊情況

### 如果我要其他形狀呢？

Aspose.Words 支援多種 `ShapeType`（橢圓、星形、說明框等）。只要把 `aw.drawing.ShapeType.RECTANGLE` 換成想要的列舉，例如 `aw.drawing.ShapeType.ELLIPSE`。

### 能加入多重陰影嗎？

每個形狀僅有一個 `ShadowFormat`，但你可以透過複製形狀、分別偏移並調整透明度的方式，模擬出多重陰影的效果。

### 如何把陰影顏色改成品牌色？

只要將 `shadow.color` 設為任意 `aw.drawing.Color` 即可。品牌藍色範例：`aw.drawing.Color.from_argb(255, 0, 120, 215)`。

### 想存成 DOCX 而不是 PDF？

將 `document.save(pdf_path)` 改成 `document.save("output/shadowed_rectangle.docx")`。陰影效果在兩種格式中皆會保留。

### 陰影在舊版 PDF 閱讀器上會顯示嗎？

Aspose.Words 會把陰影渲染為向量效果，支援度相當廣泛。但極舊的閱讀器可能會將其平面化；建議在目標受眾的裝置上測試。

---

## 美化 PDF 的小技巧

- **加框線：** `rectangle.line_format.width = 1.5`，再設定顏色，即可得到清晰的外框。  
- **置中矩形：** 在插入前呼叫 `builder.move_to_document_start()`，之後設定 `builder.paragraph_format.alignment = aw.ParagraphAlignment.CENTER`。  
- **加入文字說明：** 在矩形後插入 `TextFragment`，例如 `"Important Section"`，即可為圖形加上標題。

這些微調能讓普通的矩形變身為專業的說明框，適用於報告、提案或電子書等各種文件。

---

## 結論

現在你已掌握在 Python 中 **create rectangle shape**、**add shadow to shape**、**set shadow angle**，以及 **save document as PDF** 的完整流程，全部透過 Aspose.Words 完成。步驟簡潔、程式碼自足，且每一行都有其意義——從初始化文件到最後潤飾 PDF。

接下來，你可以探索 **how to add shape shadow** 在更複雜圖形中的應用、嘗試漸層填色，或在形狀內產生表格。此函式庫亦支援將形狀連結至書籤，對於製作互動式 PDF 十分便利。

有任何新想法或問題，歡迎在留言區分享或提出。祝開發順利，讓你的文件多一層深度與質感！

![Rectangle shape with shadow – example of create rectangle shape in Python](/images/rectangle-shadow.png)


## 接下來該學什麼？

以下教學與本篇內容密切相關，能進一步延伸本指南所示的技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，助你精通更多 API 功能，或在專案中探索其他實作方式。

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}