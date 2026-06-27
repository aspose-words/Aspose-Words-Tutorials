---
category: general
date: 2026-06-27
description: 學習如何在 Python 中使用 Aspose.Words 插入矩形形狀、更改陰影顏色、添加外部陰影，並將陰影效果套用於形狀——一次教學完整說明。
draft: false
keywords:
- how to insert rectangle shape
- how to change shadow color
- how to add outer shadow
- apply shadow effect to shape
language: zh-hant
og_description: 掌握如何在 Python 中插入矩形形狀、更改其陰影顏色、添加外部陰影，並使用 Aspose.Words 為形狀套用陰影效果。
og_title: 如何在 Python 中插入矩形形狀 – Aspose.Words 教程
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  headline: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  name: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: Pro tip
    text: If you need the rectangle positioned at a specific location, use `builder.move_to`
      before inserting, or adjust `rectangle.left` and `rectangle.top` after creation.
  - name: Edge case
    text: If you forget to set `shadow.opacity`, the default is fully opaque, which
      can make the shadow look like a solid shape. Always pair a color change with
      an appropriate opacity level.
  - name: Common pitfalls
    text: '- **Missing directory:** `doc.save` will raise an error if the folder doesn’t
      exist. Create it first or use `os.makedirs`. - **Version mismatch:** The shadow
      API requires Aspose.Words 22.9+; older versions silently ignore shadow settings.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
title: 如何在 Python 中插入矩形形狀 – 完整的 Aspose.Words 指南
url: /zh-hant/python/images-shapes/how-to-insert-rectangle-shape-in-python-complete-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Python 中插入矩形形狀 – 完整 Aspose.Words 指南

有沒有想過 **如何在 Python 中插入矩形形狀** 到 Word 文件裡？你並不是唯一遇到這個問題的人——許多開發者在自動化報告或建立範本時都會卡關。好消息是 Aspose.Words 讓這件事變得非常簡單，在本教學中，我們會一步步說明整個流程，從繪製矩形到為它加上時尚的外部陰影。

我們還會說明 **如何變更陰影顏色**、**如何加入外部陰影**，以及最後一步 **將陰影效果套用到形狀**。完成後，你將擁有一個完整樣式的矩形，能以程式方式插入任何 .docx 檔案。

## 前置條件

- 已在機器上安裝 Python 3.8+  
- 透過 `pip install aspose-words` 安裝 Aspose.Words for Python  
- 具備基本的 Python 腳本撰寫能力（不需要深入的 Word API 知識）  

如果你已具備上述條件，太好了——讓我們直接開始。若尚未安裝，請先取得套件；以下說明假設匯入程式碼能順利執行。

## 如何使用 Aspose.Words for Python 插入矩形形狀

第一步正如主要關鍵字所示：**如何插入矩形形狀**。我們會建立新文件、啟動 `DocumentBuilder`，然後在頁面上放置一個矩形。

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a fresh document and a builder to add content
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Insert a rectangle shape of 200x100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# Optional: give the rectangle a light fill so the shadow is visible
rectangle.fill_color = aw.drawing.Color.light_blue
```

> **為什麼這很重要：** `insert_shape` 呼叫是 *如何插入矩形形狀* 的核心。它會回傳一個 `Shape` 物件，之後你可以對其大小、位置、填色、邊框等進行操作。請注意我們同時設定了 `fill_color`；若未設定，陰影可能會與白色頁面融合，難以辨識。

### 小技巧
若需要將矩形放在特定位置，可在插入前使用 `builder.move_to`，或在建立後調整 `rectangle.left` 與 `rectangle.top`。

## 變更形狀的陰影顏色

現在矩形已經在文件中，接著說明 **如何變更陰影顏色**。Aspose.Words 提供 `ShadowEffect` 物件，你可以將 `color` 屬性設定為任意 RGB 值。

```python
# Create a shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # we’ll also cover outer shadow later
shadow.blur_radius = 8.0                  # smooth edges
shadow.distance = 6.0                     # how far the shadow sits from the shape
shadow.direction = 45                     # angle in degrees
shadow.opacity = 0.6                      # semi‑transparent

# Change the shadow color to a deep gray instead of black
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)

# Apply the shadow to our rectangle
rectangle.shadow = shadow
```

> **為什麼會想這麼做：** 深黑的陰影在淺色文件上會顯得過於刺眼。調整顏色可以配合企業品牌，或僅僅是為了獲得較柔和的視覺效果。

### 邊緣情況
如果忘記設定 `shadow.opacity`，預設會是完全不透明，陰影看起來會像實體形狀。務必在變更顏色時，同時設定合適的透明度。

## 加入外部陰影效果

許多人接下來會問 **如何加入外部陰影**。`ShadowStyle.OUTER` 旗標會告訴 Aspose.Words 在形狀輪廓外部繪製陰影，而非內部。

上方程式碼已使用 `ShadowStyle.OUTER`，以下僅將此設定單獨說明，以利清晰：

```python
# Ensure the shadow style is outer
shadow.style = ShadowStyle.OUTER
```

若改用 `ShadowStyle.INNER`，陰影會出現在矩形內部，適合做浮雕效果。對於大多數文件設計情境，外部樣式能提供自然的投影感。

## 將陰影效果套用到形狀

我們已透過 `rectangle.shadow = shadow` **將陰影效果套用到形狀**。現在把所有步驟整合起來，並儲存文件，以確認效果持續存在。

```python
# Save the document – choose a folder you have write access to
output_path = "output/RectangleWithShadow.docx"
doc.save(output_path)

print(f"Document saved to {output_path}. Open it to see the rectangle with its outer shadow.")
```

當你在 Microsoft Word 中開啟 `RectangleWithShadow.docx` 時，應該會看到一個淡藍色矩形，並在 45° 角度投射出細緻的灰色外部陰影。陰影會稍微模糊且有偏移，正如我們先前設定的那樣。

### 常見陷阱
- **目錄不存在：** 若資料夾不存在，`doc.save` 會拋出錯誤。請先建立目錄或使用 `os.makedirs`。  
- **版本不相容：** 陰影 API 需要 Aspose.Words 22.9 以上版本；舊版會靜默忽略陰影設定。

## 完整可執行範例

以下是結合所有步驟的完整腳本。將它複製貼上成名為 `rectangle_shadow.py` 的檔案，然後以 `python rectangle_shadow.py` 執行。

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Create a new document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2️⃣ Insert the rectangle shape (how to insert rectangle shape)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle.fill_color = aw.drawing.Color.light_blue   # make the shape visible

# 3️⃣ Define the shadow (how to change shadow color, how to add outer shadow)
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # outer shadow
shadow.blur_radius = 8.0
shadow.distance = 6.0
shadow.direction = 45
shadow.opacity = 0.6
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)  # custom gray

# 4️⃣ Apply the shadow (apply shadow effect to shape)
rectangle.shadow = shadow

# 5️⃣ Save the file
output_path = os.path.join(output_dir, "RectangleWithShadow.docx")
doc.save(output_path)

print(f"✅ Document generated: {output_path}")
```

**預期結果：** 產生一個 Word 文件（`RectangleWithShadow.docx`），內含單一矩形與灰色外部陰影。於 Word 中開啟即可驗證視覺效果。

## 常見問題

| 問題 | 解答 |
|----------|--------|
| *我可以使用其他形狀類型嗎？* | 當然可以——將 `ShapeType.RECTANGLE` 換成 `ShapeType.OVAL`、`ShapeType.TRIANGLE` 等，陰影邏輯同樣適用。 |
| *如果需要更粗的邊框該怎麼做？* | 在套用陰影前，設定 `rectangle.line_width = 2.0`（點）即可。 |
| *可以為陰影加入動畫嗎？* | Aspose.Words 本身不支援動畫；若需動畫效果，須匯出為 HTML/CSS 後自行實作。 |
| *這在 macOS 上可用嗎？* | 可以——只要 Python 能執行，Aspose.Words 就與平台無關。 |

## 結論

我們已完整說明 **如何插入矩形形狀**、示範 **如何變更陰影顏色**、解釋 **如何加入外部陰影**，最後展示 **如何將陰影效果套用到形狀**，全程使用 Aspose.Words for Python。完整腳本已可直接放入任何自動化流程，讓你在數秒內得到具備精緻陰影的專業矩形。

準備好進一步挑戰了嗎？試著更換填色、調整不同的 `direction` 角度，或在同一頁面加入多個形狀。你也可以探索 Aspose.Words 豐富的文字格式化 API，將陰影與樣式文字結合，打造吸睛的報告。

如果本教學對你有幫助，請給個讚、分享給同事，或留下你的變化版本留言。祝編程愉快！

![Diagram showing how to insert rectangle shape with an outer shadow applied in a Word document](/images/rectangle-shadow.png)


## 接下來該學什麼？

以下教學與本指南緊密相關，能進一步深化你所學的技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助你掌握更多 API 功能，或在專案中探索其他實作方式。

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}