---
category: general
date: 2026-10-07
description: 學習如何在使用 Aspose.Words for Python 時，將文件另存為 PDF，同時加入矩形形狀與自訂陰影。附有逐步程式碼示例。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save document as pdf
- add rectangle shape
- export word to pdf
- set rectangle dimensions
- draw rectangle word
language: zh-hant
lastmod: 2026-10-07
og_description: 使用 Aspose.Words for Python，將文件儲存為 PDF 並加入自訂矩形形狀。遵循完整範例以繪製、設定樣式，並將
  Word 匯出為 PDF。
og_image_alt: Screenshot of the generated PDF showing the rectangle shape after save
  document as pdf
og_title: 將文件儲存為 PDF 並加上矩形形狀 – 完整 Python 指南
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  headline: How to save document as PDF with a custom rectangle shape in Python
  type: TechArticle
- description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  name: How to save document as PDF with a custom rectangle shape in Python
  steps:
  - name: Initialize a new blank document
    text: '```python import aspose.words as aw'
  - name: Add rectangle shape to the document
    text: '```python # Create a rectangle shape and attach it to the document. rectangle
      = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)'
  - name: Set rectangle dimensions
    text: '```python # Define width and height in points (1 point = 1/72 inch). rectangle.width
      = 200 # 200 points ≈ 2.78 inches rectangle.height = 100 # 100 points ≈ 1.39
      inches ```'
  - name: (Optional) Apply a visible custom shadow
    text: '```python shadow = rectangle.shadow_format shadow.visible = True # Show
      the shadow shadow.blur = 5.0 # Softness of the shadow edge shadow.distance =
      3.0 # How far the shadow is offset shadow.angle = 45 # Direction in degrees
      shadow.color = aw.drawing.Color.black ```'
  - name: Save document as PDF
    text: '```python output_path = "output/shadow_rectangle.pdf" document.save(output_path)
      print(f"PDF saved to {output_path}") ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Word automation
title: 如何在 Python 中將文件儲存為 PDF 並使用自訂矩形形狀
url: /zh-hant/python/document-conversion/how-to-save-document-as-pdf-with-a-custom-rectangle-shape-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Python 中以自訂矩形形狀將文件儲存為 PDF

如果您需要在加入自訂圖形的同時 **save document as PDF**，本指南將一步步說明。我们將示範如何建立空白 Word 檔案、**drawing a rectangle shape**、設定尺寸、套用可見陰影，最後使用 Aspose.Words for Python 套件 **export Word to PDF**。

完成後您將得到一個包含精確定位矩形的 PDF，適用於報告、發票或任何文件自動化情境。無需外部工具——只需 Python 與 Aspose.Words 套件。

## 您需要的條件

| 必要條件 | 為何重要 |
|----------|----------|
| Python 3.8+ | Aspose.Words for Python API 針對現代直譯器。 |
| `aspose-words` 套件 (`pip install aspose-words`) | 提供程式碼範例中使用的 `aw` 命名空間。 |
| 具備 Python 及物件導向程式設計的基本知識 | 本教學會操作 `Document` 與 `Shape` 等物件。 |
| 具備寫入 PDF 將儲存之資料夾的權限 | `save document as pdf` 步驟會將檔案寫入磁碟。 |

> **專業提示：** 使用虛擬環境 (`python -m venv venv`) 以保持相依套件獨立。

## 如何以矩形形狀將文件儲存為 PDF

以下是一個完整且可執行的範例。每一步都會說明 **為何** 執行此操作，而不僅是 **做什麼**。

### 步驟 1：初始化新的空白文件

```python
import aspose.words as aw

# Create an empty Word document – this is the canvas for our shape.
document = aw.Document()
```

建立全新的 `Document` 物件可取得乾淨的頁面集合。若您之後想 **export Word to PDF**，也可以載入現有的 *.docx*，但從空白開始能讓範例更聚焦。

### 步驟 2：將矩形形狀加入文件

```python
# Create a rectangle shape and attach it to the document.
rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

# The shape must be placed inside a paragraph before it appears.
paragraph = document.first_section.body.first_paragraph
paragraph.append_child(rectangle)
```

`add rectangle shape` 步驟使用 `ShapeType.RECTANGLE`。將形狀附加到段落後，Aspose.Words 便能知道在最終 PDF 中的渲染位置。

### 步驟 3：設定矩形尺寸

```python
# Define width and height in points (1 point = 1/72 inch).
rectangle.width = 200   # 200 points ≈ 2.78 inches
rectangle.height = 100  # 100 points ≈ 1.39 inches
```

設定明確的 **rectangle dimensions** 可確保形狀在各平台上保持一致。若偏好英制單位，也可使用 `convert_to_inches` 輔助函式。

### 步驟 4：（可選）套用可見的自訂陰影

```python
shadow = rectangle.shadow_format
shadow.visible = True          # Show the shadow
shadow.blur = 5.0              # Softness of the shadow edge
shadow.distance = 3.0          # How far the shadow is offset
shadow.angle = 45              # Direction in degrees
shadow.color = aw.drawing.Color.black
```

陰影可讓矩形在 PDF 中更為突出。必須設定 `shadow.visible` 屬性；若未啟用，其他屬性將不會產生效果。

### 步驟 5：將文件儲存為 PDF

```python
output_path = "output/shadow_rectangle.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

使用 **.pdf** 副檔名呼叫 `document.save` 會自動透過 Aspose.Words 內建的 PDF 渲染器 **save document as pdf**。不需要額外的轉換步驟，這也是此方法被推薦用於 **export Word to PDF** 的原因。

> **為什麼這樣有效：** Aspose.Words 直接將文件版面（包含矩形及其陰影）寫入 PDF 串流。此過程無損且保留向量品質。

## 完整原始碼（單一腳本）

```python
import aspose.words as aw

def create_pdf_with_rectangle(output_path: str):
    """
    Creates a PDF that contains a single rectangle shape with a custom shadow.
    The function demonstrates:
    • add rectangle shape
    • set rectangle dimensions
    • export Word to PDF (save document as pdf)
    """
    # 1️⃣ Create a new blank document
    document = aw.Document()

    # 2️⃣ Insert a rectangle shape
    rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

    # 3️⃣ Set the shape's size
    rectangle.width = 200   # points
    rectangle.height = 100  # points

    # 4️⃣ Configure a visible shadow
    shadow = rectangle.shadow_format
    shadow.visible = True
    shadow.blur = 5.0
    shadow.distance = 3.0
    shadow.angle = 45
    shadow.color = aw.drawing.Color.black

    # 5️⃣ Add shape to the first paragraph
    paragraph = document.first_section.body.first_paragraph
    paragraph.append_child(rectangle)

    # 6️⃣ Save the document as PDF
    document.save(output_path)
    print(f"PDF successfully saved to: {output_path}")

if __name__ == "__main__":
    create_pdf_with_rectangle("output/shadow_rectangle.pdf")
```

執行此腳本會產生 `shadow_rectangle.pdf`，其外觀如下：

![生成的 PDF 圖示，顯示在 save document as pdf 後的矩形形狀](placeholder-image.png)

*此 PDF 只有單一頁面，中心有一個帶黑色陰影的矩形。*

## 常見問題與邊緣情況

| 問題 | 解答 |
|------|------|
| **我可以將矩形放在特定位置嗎？** | 可以。在儲存前設定 `rectangle.left` 與 `rectangle.top`（以點為單位）。 |
| **如果需要多個形狀該怎麼辦？** | 建立額外的 `Shape` 物件，分別設定後再附加到同一段落或不同段落。 |
| **陰影會影響 PDF 大小嗎？** | 影響極小；陰影以向量元資料儲存，並非點陣圖。 |
| **我可以用它來轉換現有的 *.docx* 檔案嗎？** | 當然可以。將 `aw.Document()` 改為 `aw.Document("input.docx")`，其餘步驟不變。 |
| **有沒有辦法變更矩形的填色？** | 設定 `rectangle.fill_color = aw.drawing.Color.light_blue`（或任意您想要的 `Color`）。 |

## 往後的步驟

既然您已了解如何 **save document as PDF** 並加入自訂矩形，接下來可以探索：

* **Export Word to PDF** 搭配頁首、頁尾與頁碼。  
* **Add other drawing objects**（`Ellipse`、`Polygon`）使用相同的 `Shape` 類別。  
* **Batch process** 一個資料夾內的 Word 檔案，為每個檔案套用相同的矩形覆蓋層。  

這些延伸功能遵循相同的模式：建立形狀、設定屬性，然後 **save document as pdf**。

---

**Summary:** 本教學示範了如何 **save document as PDF** 同時 **add rectangle shape**、**set rectangle dimensions**，並使用 Aspose.Words for Python 套用自訂陰影。完整腳本已可直接複製、執行，並套用於您自己的文件自動化流程。祝開發愉快！

## 接下來該學什麼？

以下教學涵蓋與本指南密切相關的主題，並以此為基礎。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在自己的專案中探索其他實作方式。

- [建立矩形形狀、加入陰影並儲存 PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [將矩形加入 PDF（使用 Aspose.Words）– 步驟指南](/words/english/python-net/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/)
- [使用 Aspose.Words 將文件儲存為 PDF – 完整 C# 指南](/words/english/net/programming-with-pdfsaveoptions/save-document-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}