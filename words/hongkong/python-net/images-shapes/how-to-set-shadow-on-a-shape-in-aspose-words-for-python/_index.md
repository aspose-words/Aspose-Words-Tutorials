---
category: general
date: 2026-09-27
description: 學習如何使用 Aspose.Words for Python 為形狀設定陰影。本指南涵蓋為形狀添加陰影、套用陰影效果以及設定陰影顏色。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to set shadow
- add shadow to shape
- apply shadow effect
- set shadow color
- how to add shadow
language: zh-hant
lastmod: 2026-09-27
og_description: 如何使用 Aspose.Words for Python 為形狀設定陰影。請依照步驟指南為形狀添加陰影、套用陰影效果，並設定陰影顏色。
og_image_alt: Screenshot showing how to set shadow on a shape in a Word document
og_title: 如何在 Aspose.Words for Python 中為形狀設定陰影
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to set shadow on a shape with Aspose.Words for Python. This
    guide covers add shadow to shape, apply shadow effect, and set shadow color.
  headline: How to set shadow on a shape in Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Shapes
- Shadow effect
title: 如何在 Aspose.Words for Python 中為形狀設定陰影
url: /zh-hant/python/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Aspose.Words for Python 中為圖形設定陰影

如果您需要 **設定陰影** 給繪圖物件，本指南將完整說明整個流程。您將看到如何為圖形加入陰影、設定陰影的模糊度、偏移量與顏色，並在不離開程式碼的情況下儲存更新後的文件。

本教學假設您已具備基本的 Aspose.Words for Python 環境。閱讀完本文後，您將能為 DOCX 檔中的任何圖形套用專業的陰影效果。

## 前置條件

開始之前，請確保您已具備：

* 已安裝 Python 3.8 以上版本。
* 已安裝 Aspose.Words for Python via .NET（`pip install aspose-words`）。
* 一個包含至少一個圖形（例如矩形或圖片）的 Word 文件（`input.docx`）。  
  若文件為空，程式碼會自行建立一個示範圖形。

上述項目可確保後續步驟不會因匯入錯誤而中斷。

## 步驟 1：載入或建立 Word 文件

第一步是取得 `Document` 物件。您可以載入既有檔案，或是建立全新文件。

```python
import aspose.words as aw

# Load an existing document, or create a new blank document if the file does not exist.
try:
    doc = aw.Document("YOUR_DIRECTORY/input.docx")
except Exception:
    doc = aw.Document()          # Creates an empty document
    # Optional: add a paragraph so the document is not completely empty.
    builder = aw.DocumentBuilder(doc)
    builder.writeln("Document created for shadow demo.")
```

*此步驟的重要性*：`Document` 物件是所有 Word 處理操作的入口。沒有它就無法存取圖形或套用視覺效果。

## 步驟 2：取得目標圖形

若要操作圖形的外觀，需要先取得圖形節點的參考。以下範例會抓取文件層級中第一個找到的圖形。

```python
# Retrieve the first shape in the document tree.
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# If the document has no shapes, create one for demonstration purposes.
if shape is None:
    builder = aw.DocumentBuilder(doc)
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 100)
    shape.wrap_type = aw.drawing.WrapType.INLINE
```

*此步驟的重要性*：`add shadow to shape` 必須有具體的圖形物件。程式碼會安全處理文件中沒有圖形的情況，確保每位讀者都能順利執行教學。

## 步驟 3：設定陰影外觀

現在可以透過調整圖形的 `shadow` 屬性來 **套用陰影效果**。以下設定會產生細緻的深色陰影。

```python
# Set the shadow blur radius (softness). Larger values produce a more diffused shadow.
shape.shadow.blur = 5.0

# Horizontal displacement of the shadow in points.
shape.shadow.offset_x = 2.0

# Vertical displacement of the shadow in points.
shape.shadow.offset_y = 2.0

# Set the shadow color. This demonstrates **set shadow color** to black.
shape.shadow.color = aw.Color.black

# Enable the shadow (some older versions require explicit visibility).
shape.shadow.visible = True
```

*各屬性說明*：

| 屬性 | 效果 |
|------|------|
| `blur` | 控制陰影的模糊程度。 |
| `offset_x` / `offset_y` | 決定陰影相對於圖形的方向與距離。 |
| `color` | 定義陰影的色調；可使用任意 `aw.Color`。 |
| `visible` | 確保陰影在輸出檔案中被渲染。 |

您可以將 `aw.Color.black` 換成 `aw.Color.from_argb(255, 0, 0, 0)` 以使用自訂 RGBA 值，或使用其他預設顏色。

## 步驟 4：儲存已修改的文件

設定完陰影後，將變更寫入新檔案。

```python
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved with shadow effect at: {output_path}")
```

當您在 Microsoft Word 中開啟 `output.docx` 時，選取的圖形會顯示向右 2 pt、向下 2 pt 的柔和黑色陰影。

## 完整範例

將所有步驟整合成一個可直接貼到 IDE 中執行的獨立腳本。

```python
import aspose.words as aw

def add_shadow_to_first_shape(input_path: str, output_path: str):
    # Load or create the document.
    try:
        doc = aw.Document(input_path)
    except Exception:
        doc = aw.Document()
        builder = aw.DocumentBuilder(doc)
        builder.writeln("Document created for shadow demo.")

    # Retrieve the first shape; create one if none exist.
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
    if shape is None:
        builder = aw.DocumentBuilder(doc)
        shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 100)
        shape.wrap_type = aw.drawing.WrapType.INLINE

    # Apply shadow settings.
    shape.shadow.blur = 5.0
    shape.shadow.offset_x = 2.0
    shape.shadow.offset_y = 2.0
    shape.shadow.color = aw.Color.black
    shape.shadow.visible = True

    # Save the result.
    doc.save(output_path)
    print(f"Shadow applied and saved to {output_path}")

# Example usage
if __name__ == "__main__":
    add_shadow_to_first_shape(
        input_path="YOUR_DIRECTORY/input.docx",
        output_path="YOUR_DIRECTORY/output.docx"
    )
```

執行腳本後會產生 `output.docx`，其中第一個圖形已套用設定好的陰影。

## 常見問題與避免方式

| 問題 | 原因 | 解決方案 |
|------|------|----------|
| `shape` 為 `None`，即使已載入文件 | 文件中沒有繪圖物件。 | 使用步驟 2 中示範的備援圖形建立區塊。 |
| 陰影在 Word 中未顯示 | `shape.shadow.visible` 仍為 `False`，或文件以舊格式（如 `.doc`）儲存。 | 確認 `visible = True`，並以 `.docx` 格式儲存。 |
| 顏色與預期不同 | 文件主題會覆寫明確設定的顏色。 | 在停用主題覆寫後設定 `shape.shadow.color`，或使用 `aw.Color.from_argb`。 |

處理好這些邊緣情況，可讓解決方案在正式環境中更為穩健。

## 擴充效果（後續步驟）

既然您已掌握 **如何加入陰影**，可以進一步探索以下增強功能：

* 透過調整 `shape.shadow` 子屬性，**套用漸層或多重陰影**。
* 根據使用者輸入或主題顏色 **動態設定陰影顏色**。
* 將 **add shadow to shape** 與旋轉、線條樣式或 3‑D 效果等其他格式化操作結合。
* 透過遍歷 `doc.get_child_nodes(aw.NodeType.SHAPE, True)`，自動為文件中的每個圖形加入陰影。

這些延伸讓您能建構出產出精緻、視覺一致的文件生成管線。

## 結論

現在您已擁有一套完整、可執行的 **設定圖形陰影** 解決方案，使用 Aspose.Words for Python。本文說明了載入文件、取得或建立圖形、設定模糊度、偏移與 **設定陰影顏色**，最後儲存檔案的全流程。將此模式套用到任何自動化專案中的圖形，並嘗試其他視覺調整，以符合您的設計需求。

--- 

*隨意將程式碼調整為其他圖形類型、顏色或偏移值。如遇問題，先參考「常見問題」表格是個不錯的起點。*


## 接下來您可以學習什麼？

以下教學與本指南緊密相關，進一步延伸所學技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，並在自己的專案中探索替代實作方式。

- [在 C# 中為圖形加入陰影 – 完整陰影效果應用指南](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-c-complete-guide-to-apply-shadow-effe/)
- [在 Word 中為圖形加入陰影 – 完整 Aspose.Words 教學](/words/english/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/)
- [建立矩形圖形、加入陰影並儲存為 PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}