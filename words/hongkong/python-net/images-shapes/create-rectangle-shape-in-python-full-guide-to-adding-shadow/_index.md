---
category: general
date: 2026-05-04
description: 學習如何建立矩形形狀、如何加入帶陰影的形狀、更改陰影顏色、設定陰影距離，並使用 Aspose.Words for Python 將文件另存為
  PDF。
draft: false
keywords:
- create rectangle shape
- how to add shape
- change shadow color
- save document as pdf
- set shadow distance
language: zh-hant
og_description: 使用 Aspose.Words for Python 建立矩形形狀，了解如何新增形狀、變更陰影顏色、設定陰影距離，並將文件儲存為 PDF。
og_title: 建立矩形形狀 – 加入陰影、更改顏色並另存為 PDF
tags:
- Aspose.Words
- Python
- PDF generation
title: 在 Python 中建立矩形形狀 – 添加陰影與儲存為 PDF 完整指南
url: /zh-hant/python/images-shapes/create-rectangle-shape-in-python-full-guide-to-adding-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立矩形形狀 – Python 開發者完整教學

是否曾需要在 Word 文件中 **建立矩形形狀**，卻又想為它加上精緻的陰影？也許你正在開發報表產生器，而視覺效果相當重要——尤其最終輸出是 PDF 時。好消息是，使用 Aspose.Words for Python 不僅可以 **how to add shape**，還能調整陰影的每一個屬性，從顏色到距離，最後 **save document as pdf**，一次完成。

本指南將一步一步帶你完成整個流程。你會看到可以直接複製貼上的完整程式碼，了解每一行 **為何** 必要，並學到處理特殊情況（例如透明陰影或非標準 DPI）的技巧。完成後，你將能 **create rectangle shape**、自訂陰影，並順利匯出清晰的 PDF，毫不費力。

## 前置條件

- 已在機器上安裝 Python 3.8+。  
- 透過 `pip install aspose-words` 安裝 Aspose.Words for Python。  
- 具備基本的物件導向 Python 知識（不需要太進階）。  

如果已經有虛擬環境，只要執行安裝指令即可開始。

## 步驟 1：初始化 Document 與 Builder

在 **how to add shape** 之前，需要先有一個空白文件。`Document` 類別代表整個檔案，而 `DocumentBuilder` 則是你的畫筆。

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder to edit it
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

*為何重要：* `Document` 包含所有章節、頁面與資源。`DocumentBuilder` 提供流暢的 API，讓你能在需要的地方插入內容——就像在文字處理器中的游標一樣。

## 步驟 2：插入矩形形狀

現在我們真正 **how to add shape**。`insert_shape` 方法需要形狀類型與尺寸（以點為單位）。此處我們選擇 200 × 100 pt 的矩形，並填入淡藍色。

```python
# Step 2: Insert a rectangle shape and give it a light‑blue fill
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,  # shape type
    200,                            # width in points
    100)                            # height in points
rectangle_shape.fill_color = aw.Color.light_blue
```

*小技巧：* 若需要形狀與現有文字對齊，可在插入前使用 `builder.move_to`，或在建立後調整 `left`/`top` 屬性。

## 步驟 3：開啟陰影

沒有陰影的形狀會顯得平面。要 **set shadow distance** 並讓效果可見，先取得陰影格式並將其啟用。

```python
# Step 3: Access the shape's shadow format and make the shadow visible
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
```

*此步驟的原因：* 陰影格式是獨立的物件；必須先將 `visible` 設為 `True`，否則其他陰影屬性皆會被忽略。

## 步驟 4：設定陰影 – 顏色、模糊、距離、方向

這裡就是魔法發生的地方。我們會 **change shadow color**、調整模糊半徑、設定陰影與矩形的距離，並將其旋轉 45°。

```python
# Step 4: Configure the appearance of the shadow
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER   # outer shadow
rectangle_shadow.blur_radius = 10.0                    # blur amount (pixels)
rectangle_shadow.distance = 5.0                        # distance from the shape
rectangle_shadow.direction = 45.0                     # angle in degrees
rectangle_shadow.color = aw.Color.gray                 # shadow colour
```

*各屬性說明：*

| Property | 功能說明 | 常見數值 |
|----------|----------|----------|
| `style` | 決定陰影是 *內部* 還是 *外部*。 | `OUTER`（最常用） |
| `blur_radius` | 控制柔和程度，數值越高邊緣越模糊。 | 0–20 px 為常見範圍 |
| `distance` | 陰影相對於形狀的偏移距離。 | 0–10 pt 為細緻，>10 為戲劇化 |
| `direction` | 光源角度，順時針從 X 軸測量。 | 0‑360° |
| `color` | 陰影顏色。 | 任意 `aw.Color`（例如 `gray`、`dark_red`） |

*邊緣情況：* 若將 `distance` 設為 `0`，陰影會直接覆蓋在形狀下方，等同隱藏填色。請保持大於 `0` 才能看到偏移效果。

## 步驟 5：將文件儲存為 PDF

最後，我們 **save document as pdf**。Aspose.Words 會自動將陰影光柵化，PDF 的呈現與 Word 端完全一致。

```python
# Step 5: Save the document as a PDF with the shadowed shape
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

*為何選 PDF？* PDF 能在不同平台保持版面不變，非常適合報表、發票或任何可列印的文件。

---

![Create rectangle shape with shadow](https://example.com/images/rectangle-shadow.png){: .align-center alt="create rectangle shape with shadow example"}

*上圖展示最終的 PDF 輸出——淡藍色矩形搭配柔和的灰色外陰影，正如我們所設定的樣子。*

## 常見問題與變化

### 若需要 **透明** 陰影該怎麼做？

在陰影顏色上設定 alpha 通道：

```python
transparent_gray = aw.Color.from_argb(128, 0, 0, 0)  # 50% opacity black
rectangle_shadow.color = transparent_gray
```

### 能否將相同的陰影套用到多個形狀？

可以。從一個形狀取得 `ShadowFormat`，再指派給其他形狀：

```python
another_shape = builder.insert_shape(aw.drawing.ShapeType.ELLIPSE, 150, 150)
another_shape.shadow_format = rectangle_shadow.clone()
```

### 若要為 **不同形狀類型** 更改陰影？

所有形狀類型共用相同的 `ShadowFormat` 屬性，只要把 `ShapeType.RECTANGLE` 換成 `ShapeType.OVAL`、`ShapeType.TRIANGLE` 等即可。

### 如何產生 **高解析度 PDF** 以供列印？

使用較高 DPI 的 `PdfSaveOptions`：

```python
options = aw.saving.PdfSaveOptions()
options.image_resolution = 300  # 300 DPI for print quality
document.save(output_path, options)
```

## 重點回顧

我們已說明如何 **create rectangle shape**、**how to add shape**、自訂 **shadow colour**、**set shadow distance**，最後 **save document as pdf**。完整、可執行的腳本如下：

```python
import aspose.words as aw

# Initialise document
document = aw.Document()
builder = aw.DocumentBuilder(document)

# Insert rectangle shape
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle_shape.fill_color = aw.Color.light_blue

# Enable and style shadow
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER
rectangle_shadow.blur_radius = 10.0
rectangle_shadow.distance = 5.0
rectangle_shadow.direction = 45.0
rectangle_shadow.color = aw.Color.gray

# Save as PDF
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

執行腳本後，開啟產生的 `ShadowedShape.pdf`，即可看到帶有細緻灰色陰影的清晰矩形——正是專業報表應有的視覺效果。

## 接下來可以做什麼？

- **探索其他形狀類型**（`ShapeType.OVAL`、`ShapeType.LINE`）以豐富文件內容。  
- **組合多重陰影**：透過疊加形狀甚至使用內部陰影與亮色打造「發光」效果。  
- **自動化批次處理**：迴圈遍歷資料列，為每列產生形狀，最後合併成單一 PDF。  
- **結合其他 Aspose 套件**（例如 Aspose.Slides），若需將相同視覺輸出至 PowerPoint。

盡情實驗吧——調整 `blur_radius`、改變 `direction`，或把 `gray` 換成品牌專屬色彩。API 足夠彈性，少量調整即可帶來巨大的視覺衝擊。

有任何問題或特殊情境想討論？歡迎在下方留言或前往 Aspose 社群論壇。祝開發順利，享受這些美觀的陰影矩形吧！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}