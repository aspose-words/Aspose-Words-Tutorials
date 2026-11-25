---
category: general
date: 2026-11-25
description: 在 Word 文件中使用 Python 為形狀添加陰影。了解如何在 Word 中插入矩形形狀，並使用 Aspose.Words 套用透明陰影。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- insert rectangle shape word
- how to create word document python
- Aspose.Words Python
- shape formatting Python
language: zh-hant
lastmod: 2026-11-25
og_description: 使用 Python 為 Word 文件中的形狀加入陰影。本教學示範如何在 Word 中插入矩形形狀，並使用 Aspose.Words
  設定 30% 透明的陰影。
og_image_alt: Add shadow to shape example in a Word document created by Python
og_title: 在 Word 文件中使用 Python 為形狀添加陰影 – 步驟指南
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Add shadow to shape in a Word document with Python. Learn how to insert
    rectangle shape in Word and apply a transparent shadow using Aspose.Words.
  headline: How to add shadow to shape in a Word document using Python
  type: TechArticle
tags:
- Python
- Aspose.Words
- Word automation
title: 如何使用 Python 為 Word 文件中的形狀添加陰影
url: /zh-hant/python/images-shapes/how-to-add-shadow-to-shape-in-a-word-document-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 文件中使用 Python 為形狀添加陰影

如果您需要在 Word 文件中**為形狀添加陰影**，本指南將為您展示一個完整且可執行的解決方案。您將看到如何建立 Word 檔案、插入矩形形狀，並套用 30% 透明的陰影——全部使用 Aspose.Words for Python 函式庫。

以程式方式操作 Word 文件可免除手動格式設定，並讓您能大規模產生報告、合約或行銷傳單。完成本教學後，您將能以即用的程式碼範例回答「**how to create Word document python**」的問題。

## 前置條件

* 已安裝 Python 3.8 或更新版本。
* 擁有有效的 Aspose.Words for Python 授權（免費試用可用於評估）。
* `aspose-words` 套件已透過 `pip install aspose-words` 安裝。
* 一個可寫入輸出檔案的資料夾（程式碼中請將 `YOUR_DIRECTORY` 替換為實際路徑）。

不需要其他相依性。

## 步驟 1：建立新 Word 文件

第一步是實例化一個 `Document` 物件。此物件在記憶體中代表整個 .docx 檔案。

```python
import aspose.words as aw

# Create an empty Word document
doc = aw.Document()
# DocumentBuilder provides a convenient API for adding content
builder = aw.DocumentBuilder(doc)
```

`DocumentBuilder` 的運作方式類似虛擬游標。當您呼叫其方法時，函式庫會在目前游標位置插入相應的元素。

## 步驟 2：插入矩形形狀

接下來，使用 builder 的 `insert_shape` 方法**插入矩形形狀**。此方法需要指定形狀類型以及以點為單位的尺寸（1 點 = 1/72 英吋）。

```python
# Insert a rectangle shape that is 100 points wide and 50 points tall
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)
```

您可以調整尺寸以符合設計需求。矩形會成為文件繪圖層的一部分，之後您即可修改其填色、輪廓或陰影。

## 步驟 3：存取形狀的陰影格式

每個繪圖物件都會公開 `shadow_format` 屬性，用以控制陰影外觀。取得該屬性後，您即可調整透明度、偏移、模糊程度與顏色。

```python
# Get the ShadowFormat object for the rectangle
shadow = shape.shadow_format
```

此時形狀仍使用預設陰影（即無陰影）。`ShadowFormat` 物件包含建立真實效果所需的所有參數。

## 步驟 4：將陰影設定為 30% 透明

透明度以 `0`（完全不透明）到 `1`（完全透明）之間的數值表示。將其設為 `0.3` 即可得到 30% 透明的陰影，通常足以增添層次感而不會蓋過文字。

```python
# Apply a 30 % transparent shadow
shadow.transparency = 0.3
# Optional: adjust other shadow properties for a nicer look
shadow.visible = True               # Ensure the shadow is turned on
shadow.distance = 4                 # Distance of the shadow from the shape (points)
shadow.blur = 4                     # Amount of blur applied to the shadow
shadow.color = aw.Color.black       # Shadow color
```

這些額外屬性並非必須，但可說明如何微調效果。`visible` 旗標是關鍵；若遺漏，陰影將不會顯示，即使其他設定已正確設定。

## 步驟 5：儲存文件以檢視結果

最後，將文件寫入磁碟。使用 Microsoft Word 或任何相容檢視器開啟產生的 `.docx` 檔案，即可看到套用了透明陰影的矩形。

```python
# Save the document to the desired location
output_path = r"YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

當您開啟 `output.docx` 時，會看到一個普通的矩形，右下方有淡淡的灰色陰影。30% 的透明度使形狀看起來像是從頁面上抬起來的。

![Add shadow to shape example](placeholder-image.png){: .align-center alt="使用 Python 建立的 Word 文件中為形狀添加陰影的範例"}

## 完整、可執行的腳本

將所有步驟組合起來，即可得到一個可自行執行的腳本，您可以直接複製、貼上並立即執行。

```python
import aspose.words as aw

def create_word_with_shadow(output_path: str):
    """
    Creates a Word document that contains a rectangle shape
    with a 30 % transparent shadow.
    """
    # Step 1: Initialize document and builder
    doc = aw.Document()
    builder = aw.DocumentBuilder(doc)

    # Step 2: Insert rectangle shape
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)

    # Step 3: Access shadow format
    shadow = shape.shadow_format

    # Step 4: Configure shadow properties
    shadow.visible = True
    shadow.transparency = 0.3
    shadow.distance = 4
    shadow.blur = 4
    shadow.color = aw.Color.black

    # Step 5: Save the document
    doc.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    # Replace with a valid folder on your machine
    create_word_with_shadow(r"YOUR_DIRECTORY/output.docx")
```

**預期輸出：** 開啟產生的 `output.docx` 後，會看到單頁文件上有一個投射出淡淡、半透明陰影的矩形。無需額外格式設定。

## 常見變化與邊緣情況

| 情況 | 如何調整程式碼 |
|-----------|-----------------------|
| **不同的形狀類型**（例如橢圓） | 將 `aw.drawing.ShapeType.RECTANGLE` 改為 `aw.drawing.ShapeType.ELLIPSE`。 |
| **自訂陰影顏色** | 設定 `shadow.color = aw.Color.from_argb(255, 128, 0, 0)` 以取得紅色系陰影。 |
| **多個形狀** | 重複呼叫 `builder.insert_shape`；每次呼叫都會回傳一個獨立的 `Shape` 物件，您可以分別設定樣式。 |
| **另存為 PDF** | 將 `doc.save(output_path)` 改為 `doc.save(output_path.replace('.docx', '.pdf'))`，並使用 `.pdf` 副檔名。 |
| **未使用授權執行** | 免費試用版會在首頁加上浮水印。取得授權即可在正式環境中移除。 |

## 小技巧與最佳實踐

* **重複使用 builder**：在整個文件中保留單一 `DocumentBuilder` 實例，以避免不必要的物件建立。
* **釋放資源**：在長時間執行的服務中，儲存後呼叫 `doc.dispose()` 以釋放原生記憶體。
* **驗證輸出**：若需確保符合 Open XML 標準，請在儲存前使用 `doc.validate(aw.ValidationType.FULL_VALIDATION)`。
* **版本相容性**：此程式碼相容於 Aspose.Words for Python ≥ 22.9。請使用 `pip install --upgrade aspose-words` 確保套件為最新版本。

## 結論

您現在已了解如何在 Word 文件中使用 Python **為形狀添加陰影**。透過這五個步驟——建立文件、**插入矩形形狀**、設定陰影，最後儲存，您即可自動化產出精緻的報告、發票或行銷素材。

接下來，您可以探索其他格式設定選項，例如漸層填色、文字環繞，或將文件轉換為 PDF。這些主題皆基於本教學中介紹的 `DocumentBuilder` 與形狀格式化概念。

祝程式開發順利，並欣賞簡單陰影為您的自動化 Word 文件帶來的視覺層次感！

## 接下來該學什麼？

以下教學涵蓋與本指南密切相關的主題，並以此為基礎。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索其他實作方式。

- [如何在 Word 文件中使用 Python 建立矩形形狀](/words/english/python-net/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/)
- [在 Python 中為形狀添加陰影 – 完整 Aspose.Words 教學](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [建立空白 Word 文件並為形狀添加陰影 – 完整 Python 指南](/words/english/python-net/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-pyth/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}