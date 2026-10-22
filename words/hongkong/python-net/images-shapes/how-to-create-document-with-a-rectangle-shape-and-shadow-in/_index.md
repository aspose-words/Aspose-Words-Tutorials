---
category: general
date: 2026-10-04
description: 如何使用 Aspose.Words 在 Python 中建立文件並為形狀添加陰影。學習設定陰影顏色、插入矩形形狀以及自訂外部陰影。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create document
- add shadow to shape
- set shadow color
- insert rectangle shape
- how to add shadow
language: zh-hant
lastmod: 2026-10-04
og_description: 如何在 Python 中建立文件並為形狀添加陰影。本指南將示範如何設定陰影顏色、插入矩形形狀，以及使用 Aspose.Words 套用外部陰影。
og_image_alt: Python code inserting a rectangle shape with a visible shadow into a
  Word document
og_title: 如何在 Python 中建立帶有矩形形狀與陰影的文件
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  headline: How to create document with a rectangle shape and shadow in Python
  type: TechArticle
- description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  name: How to create document with a rectangle shape and shadow in Python
  steps:
  - name: Why does the shadow sometimes appear invisible?
    text: The shadow is only rendered if `shadow.visible` is set to `True` **and**
      the shape’s `wrap_type` allows it to be displayed. An inline shape works reliably;
      floating shapes may require additional layout adjustments.
  - name: How can I change the shadow color to match a brand palette?
    text: 'Replace `aw.drawing.Color.black` with a custom RGB value:'
  - name: What if I need the shape to appear behind text?
    text: Set the wrap type to `WrapType.BEHIND` and adjust the `z_order_position`
      if necessary. Keep in mind that some viewers may render behind‑text shapes differently.
  - name: Can I apply the same shadow settings to multiple shapes?
    text: Yes. Create a helper function that configures the shadow and call it for
      each shape you insert. This promotes code reuse and ensures consistent styling.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: 如何使用 Python 建立帶有矩形形狀與陰影的文件
url: /zh-hant/python/images-shapes/how-to-create-document-with-a-rectangle-shape-and-shadow-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Python 中建立帶有矩形形狀與陰影的文件

如果您需要 **how to create document** 包含一個已樣式化的矩形，本指南提供完整解決方案。您將看到如何 **add shadow to shape**、設定陰影的顏色，並控制其偏移與模糊——全部使用 Aspose.Words for Python。完成本教學後，您即可產生一個外觀精緻、可直接發佈的 `.docx` 檔案。

以下步驟涵蓋從安裝函式庫到自訂陰影外觀的全部內容。無需參考外部文件；程式碼已可直接複製、執行，並套用到您的專案中。您還將學習如何 **insert rectangle shape**、選擇 **outer shadow style**，以及處理常見問題，例如陰影不可見或環繞設定不正確。

## 前置條件

* 已安裝 Python 3.8 或更新版本。
* 擁有有效的 Aspose.Words for Python 授權（或免費評估金鑰）。
* 具備基本的 Python 腳本撰寫經驗。
* 能存取一個可寫入的檔案系統位置，以儲存產生的文件。

您可以使用 pip 安裝 SDK：

```bash
pip install aspose-words
```

## 步驟 1：匯入函式庫並建立新的空白文件

在任何 Word 自動化情境中，建立新文件是第一步。`aw.Document()` 建構子會產生一個空白檔案，您可以在其中加入文字、影像或圖形。

```python
import aspose.words as aw

# Create a new blank document
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

`DocumentBuilder` 物件簡化了內容的插入。它會追蹤目前的游標位置，讓您能依序加入元素，而不必手動管理節。

## 步驟 2：插入指定尺寸的矩形圖形

矩形圖形可作為視覺元素的容器。您可以以點 (pt) 為單位定義其寬度與高度 (1 pt ≈ 1/72 in)。

```python
# Insert a rectangle shape that is 150 pt wide and 80 pt tall
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

此時圖形尚未套用任何樣式，僅顯示為普通輪廓。接下來的步驟會為它加入深度與顏色。

## 步驟 3：將圖形設定為與周圍文字內嵌

當圖形設定為 **inline** 時，它的行為類似段落中的字元。這可確保矩形在文件版面中保持預期的位置。

```python
# Make the shape inline so it follows the text flow
rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE
```

如果您希望圖形漂浮於文字之上，可使用 `WrapType.SQUARE` 或 `WrapType.TOP_BOTTOM`，但對於大多數報告而言，內嵌圖形能讓版面更易預測。

## 步驟 4：讓陰影可見並選擇其顏色

不可見的陰影不會帶來任何視覺效果。`visible` 旗標會啟用此效果，而 `color` 屬性則決定其色調。使用黑色可呈現經典且細緻的深度感。

```python
# Enable the shadow and set its color to black
rectangle_shape.shadow.visible = True
rectangle_shape.shadow.color = aw.drawing.Color.black
```

您可以將 `aw.drawing.Color.black` 替換為其他顏色，例如 `aw.drawing.Color.gray`，或自訂的 RGB 值 (`aw.drawing.Color.from_argb(255, 128, 128, 128)`)。

## 步驟 5：定義陰影的偏移與模糊以產生深度

偏移量決定陰影相對於圖形的位移距離，模糊半徑則會使邊緣變得柔和。較小的數值會產生銳利的陰影；較大的數值則呈現較柔和的外觀。

```python
# Horizontal and vertical offset of 5 pt each
rectangle_shape.shadow.offset_x = 5
rectangle_shape.shadow.offset_y = 5

# Blur radius of 3 pt for a gentle feather
rectangle_shape.shadow.blur = 3
```

請自行調整這些數值以符合您的設計規範。若需較重的投影，可同時提升偏移與模糊值。

## 步驟 6：選擇外部陰影樣式

Aspose.Words 提供多種陰影樣式，例如 `INNER`、`OUTER` 與 `PERSPECTIVE`。**outer** 樣式會將陰影放置於圖形邊框之外，適合打造乾淨、專業的外觀。

```python
# Apply an outer shadow style
rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

若需更具戲劇性的效果，可嘗試 `ShadowStyle.PERSPECTIVE`——它會加入三維傾斜感。

## 步驟 7：儲存帶有陰影的文件

儲存會完成檔案的寫入，將所有格式寫入磁碟。請選擇您具有寫入權限的目錄，並為檔案命名一個具描述性的名稱。

```python
# Save the document to the desired location
output_path = "output/ShapeWithShadow.docx"
document.save(output_path)
print(f"Document saved to {output_path}")
```

執行此腳本會產生一個 Word 檔案，內含帶有可見且有顏色陰影的矩形。請使用 Microsoft Word 或 LibreOffice 開啟檔案，以驗證結果。

## 完整可執行範例

以下為完整腳本，涵蓋上述所有步驟。請將程式碼複製到名為 `create_shadowed_shape.py` 的檔案中，並以 `python create_shadowed_shape.py` 執行。

```python
import aspose.words as aw
import os

def main():
    # Ensure the output directory exists
    output_dir = "output"
    os.makedirs(output_dir, exist_ok=True)

    # Step 1: Create a new blank document
    document = aw.Document()
    builder = aw.DocumentBuilder(document)

    # Step 2: Insert a rectangle shape of the desired size
    rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

    # Step 3: Set the shape to be inline with the text flow
    rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE

    # Step 4: Make the shadow visible and choose its color
    rectangle_shape.shadow.visible = True
    rectangle_shape.shadow.color = aw.drawing.Color.black

    # Step 5: Define the shadow's offset and blur to give it depth
    rectangle_shape.shadow.offset_x = 5   # horizontal offset in points
    rectangle_shape.shadow.offset_y = 5   # vertical offset in points
    rectangle_shape.shadow.blur = 3       # blur radius in points

    # Step 6: Choose an outer shadow style
    rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER

    # Step 7: Save the document with the shaped shadow
    output_path = os.path.join(output_dir, "ShapeWithShadow.docx")
    document.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    main()
```

**預期輸出**

當您開啟 `ShapeWithShadow.docx` 時，會看到頁面中央有一個單一矩形。矩形旁邊有一個細緻的黑色陰影，向右下方偏移，略為模糊以產生深度感。此陰影使用 outer 樣式，因而不會與矩形內部相交。

## 常見問題與邊緣情況

### 為什麼陰影有時會顯示為不可見？

只有在 `shadow.visible` 設為 `True` **且** 圖形的 `wrap_type` 允許顯示時，陰影才會被繪製。內嵌圖形通常可靠；漂浮圖形可能需要額外的版面調整。

### 如何將陰影顏色更換為符合品牌調色盤？

將 `aw.drawing.Color.black` 替換為自訂的 RGB 值：

```python
rectangle_shape.shadow.color = aw.drawing.Color.from_argb(255, 0, 120, 215)  # corporate blue
```

### 如果需要圖形顯示在文字後方該怎麼做？

將環繞類型設為 `WrapType.BEHIND`，並視需要調整 `z_order_position`。請留意某些檢視器可能會以不同方式呈現文字後方的圖形。

### 能否將相同的陰影設定套用到多個圖形？

可以。建立一個協助函式來設定陰影，然後在插入每個圖形時呼叫它。這有助於程式碼重用，並確保樣式一致。

```python
def apply_shadow(shape, color=aw.drawing.Color.black, offset=5, blur=3):
    shape.shadow.visible = True
    shape.shadow.color = color
    shape.shadow.offset_x = offset
    shape.shadow.offset_y = offset
    shape.shadow.blur = blur
    shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

## 結論

現在您已了解如何使用 Aspose.Words for Python 建立 **how to create document** 包含自訂陰影的矩形圖形檔案。本教學涵蓋了插入矩形、將圖形設定為內嵌、啟用陰影、設定顏色、偏移、模糊與樣式，最後儲存檔案的完整流程。

接下來您可以探索相關主題，例如對其他圖形類型使用 **add shadow to shape**、根據資料動態 **set shadow color**，或 **how to add shadow** 到影像與文字方塊。嘗試不同的尺寸、顏色與陰影樣式，以符合您的品牌指引或設計系統。

準備好自動化更多 Word 文件了嗎？接著可以嘗試加入表格、標題或動態內容——每一步皆建立在本教學所示的相同原則上。祝開發順利！

## 接下來該學什麼？

以下教學涵蓋與本指南密切相關的主題，並以此為基礎延伸技巧。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索其他實作方式。

- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [How to Manage Document Variables with Aspose.Words in Python&#58; A Complete Guide](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}