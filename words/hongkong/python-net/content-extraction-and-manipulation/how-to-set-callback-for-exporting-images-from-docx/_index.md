---
category: general
date: 2026-06-24
description: 如何設定回呼函式，在將 DOCX 另存為 Markdown 時匯出圖片。了解如何提取圖片、從 Word 中提取 SVG，並以自訂方式將 DOCX
  儲存為 Markdown。
draft: false
keywords:
- how to set callback
- export images from docx
- how to extract images
- save docx as markdown
- extract svg from word
language: zh-hant
og_description: 如何在將 DOCX 轉換為 Markdown 時設定回呼以匯出圖片。本指南將示範如何高效提取圖片與 SVG。
og_title: 如何設定回調函式以從 DOCX 匯出圖片
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  headline: How to Set Callback for Exporting Images from DOCX
  type: TechArticle
- description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  name: How to Set Callback for Exporting Images from DOCX
  steps:
  - name: '**Deterministic names** – useful for version control or CDN publishing.'
    text: '**Deterministic names** – useful for version control or CDN publishing.'
  - name: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
    text: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
  - name: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
    text: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Conversion
title: 如何設定從 DOCX 匯出圖像的回呼函式
url: /zh-hant/python/content-extraction-and-manipulation/how-to-set-callback-for-exporting-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何為從 DOCX 匯出圖像設定回呼

有沒有想過 **如何設定回呼**，以便在將 DOCX 轉換為 Markdown 時 **匯出圖像**？你並不是唯一有此疑問的人。許多開發者在預設轉換會把所有圖像丟到一個通用資料夾，甚至更糟的是會完全遺失 SVG 圖形時，卡住了。  

在本教學中，我們將一步步示範完整、可直接執行的解決方案，回答「如何設定回呼」的問題，展示 **如何抽取圖像**，甚至涵蓋 **從 Word 抽取 SVG**。完成後，你將能夠 **將 DOCX 儲存為 Markdown**，並為每個圖像資源使用自訂命名規則——不需要手動處理。

## 你將學到

- 為什麼回呼是控制轉換過程中圖像檔名的最佳方式。  
- 如何掛接 Aspose.Words 的 `MarkdownSaveOptions.resource_saving_callback`。  
- 逐步程式碼，抽取 **PNG**、**JPG**、**SVG** 以及其他內嵌資源。  
- 處理檔名衝突、大檔案以及跨平台路徑怪癖的技巧。  

> **專業小技巧：** 若你已在較大的工作流程中使用 Aspose.Words，只要把這段回呼程式碼加入，即可不必更動其他程式碼。

---

![How to set callback diagram](https://example.com/images/how-to-set-callback.png "how to set callback")

## 前置條件

- Python 3.8+（範例使用 f‑string，3.6+ 即可）。  
- 已安裝 `aspose-words` 套件（`pip install aspose-words`）。  
- 一個同時包含點陣圖與向量圖（SVG）的 DOCX 檔案。  
- 具備 Python 函式與檔案 I/O 的基本概念。

如果上述條件都符合，讓我們開始吧。

---

## 如何為從 DOCX 匯出圖像設定回呼

解決方案的核心在於 **資源儲存回呼**。Aspose.Words 在你呼叫 `document.save` 時，會為每個要寫入的圖像或 SVG 呼叫此委派。只要回傳 `(new_name, data)` 元組，即可自行決定檔名與位元組內容。

```python
import aspose.words as aw
import os
import hashlib

# Step 1: Load the source document
document = aw.Document("YOUR_DIRECTORY/input.docx")
```

### 為什麼需要回呼？

若不使用回呼，Aspose.Words 會產生 `image1.png`、`image2.svg` 等檔名，並將它們放在 Markdown 檔案旁的資料夾中。這對快速示範還算可以，但在正式環境中，你通常需要：

1. **確定的檔名** – 方便版本控制或 CDN 發佈。  
2. **避免衝突** – 兩個原始名稱相同的圖像不會互相覆寫。  
3. **自訂資料夾結構** – 例如想把所有資產放在 `/assets/docs/` 下。

回呼讓你對上述三項需求皆能全權掌控。

---

## 使用資源回呼匯出 DOCX 圖像

以下是回呼的實作範例。它會對二進位資料做雜湊產生唯一的後綴，保留原始副檔名，並回傳新檔名與原始位元組。

```python
def resource_callback(resource):
    """
    Called for every image/SVG that MarkdownSaveOptions wants to write.
    Returns a tuple (new_name, data) to control the saved file name.
    """
    # Preserve the original extension (.png, .svg, …)
    extension = os.path.splitext(resource.name)[1]

    # Compute a short hash of the image bytes – guarantees uniqueness
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]

    # Build a deterministic, collision‑free filename
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data
```

#### 邊緣案例處理

- **大型檔案：** SHA‑256 對任何大小皆適用；雜湊在記憶體中計算，處理極大 PDF 時請留意記憶體限制。  
- **缺少副檔名：** 某些舊版 Word 可能未明確記錄副檔名，此時 `extension` 會是空字串；你可以預設為 `.bin`，或檢查前幾個位元組來猜測格式。  
- **非圖像資源：** 回呼會對每個外部資源（例如 OLE 物件）觸發。若只關心圖像/SVG，可在處理前依 `resource.type` 進行篩選。

---

## 如何從 Word 抽取圖像與 SVG

現在把回呼掛入 Markdown 儲存流程。`MarkdownSaveOptions` 物件正好提供 `resource_saving_callback` 屬性供此用途。

```python
# Step 2: Configure Markdown save options to use the callback
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.resource_saving_callback = resource_callback

# Optional: set the folder where images will be placed relative to the .md file
markdown_options.resource_folder = "assets/images"
```

設定 `resource_folder` 為可選項，但相當實用。若不指定，圖像會與 Markdown 檔案同層，容易讓專案根目錄變得雜亂。

### 儲存文件

```python
# Step 3: Save the document as Markdown, letting the callback store the resources
output_md_path = "YOUR_DIRECTORY/output.md"
document.save(output_md_path, markdown_options)
print(f"Markdown saved to {output_md_path}")
```

執行腳本後，你會看到類似以下的檔案：

```
assets/images/img_a1b2c3d4e5.png
assets/images/img_f6g7h8i9j0.svg
```

產生的 `output.md` 會包含指向這些檔名的圖像連結：

```markdown
![Image](assets/images/img_a1b2c3d4e5.png)
```

這就是 **抽取圖像** 的實作——每張點陣圖或向量圖都會變成獨立且唯一命名的資產。

---

## 使用自訂圖像處理將 DOCX 轉為 Markdown

把所有步驟整合起來，以下是完整腳本，可直接貼到 `convert_docx_to_md.py` 檔案中：

```python
import aspose.words as aw
import os
import hashlib

def resource_callback(resource):
    """Control the naming of each exported image/SVG."""
    extension = os.path.splitext(resource.name)[1] or ".bin"
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data

def convert_docx_to_markdown(input_path, output_md_path, image_folder="assets/images"):
    # Load the DOCX
    document = aw.Document(input_path)

    # Set up Markdown options with our callback
    md_options = aw.saving.MarkdownSaveOptions()
    md_options.resource_saving_callback = resource_callback
    md_options.resource_folder = image_folder

    # Ensure the output directory exists
    os.makedirs(os.path.dirname(output_md_path), exist_ok=True)
    os.makedirs(os.path.join(os.path.dirname(output_md_path), image_folder), exist_ok=True)

    # Perform the conversion
    document.save(output_md_path, md_options)
    print(f"✅ Conversion complete! Markdown at: {output_md_path}")

if __name__ == "__main__":
    # Adjust these paths to your environment
    INPUT_DOCX = "YOUR_DIRECTORY/input.docx"
    OUTPUT_MD = "YOUR_DIRECTORY/output.md"
    convert_docx_to_markdown(INPUT_DOCX, OUTPUT_MD)
```

**為什麼這樣可行：**  
- `resource_callback` 確保每張圖像都有唯一且可重現的名稱。  
- `resource_folder` 讓 Markdown 更整潔，資產分離存放。  
- `os.makedirs` 呼叫可避免在全新機器上執行時出現「找不到資料夾」的錯誤。

---

## 從 Word 抽取 SVG – 向量圖怎麼處理？

SVG 在回呼中與 PNG 的處理方式相同，因為它們同屬 `resource`。唯一的差異是某些舊版 Word 會把 SVG 以 *OfficeArt* 物件形式嵌入，Aspose.Words 會自動將其轉為點陣 PNG，除非你明確開啟 **preserve SVG** 旗標：

```python
md_options.export_svg = True  # Keep original SVG markup
```

在儲存前加入上述程式碼，回呼就會收到副檔名為 `.svg` 的資源，保留清晰的向量資料——非常適合響應式網頁文件。

---

## 常見問題與注意事項

| 問題 | 解答 |
|----------|--------|
| **如果兩張圖像完全相同會怎樣？** | SHA‑256 雜湊會相同，導致檔名衝突。若需要保留兩份，可在雜湊計算時加入原始 `resource.name`（例如 `hash(resource.name + resource.data)`）。 |
| **可以依檔案類型改變儲存資料夾嗎？** | 可以。在 `resource_callback` 內檢查 `extension`，回傳類似 `f"png/{new_name}"` 或 `f"svg/{new_name}"` 的路徑即可。 |
| **此程式在 Linux/macOS 上可用嗎？** | 完全沒問題。程式使用 `os.path` 抽象化路徑分隔符。若使用付費版，請確保 Aspose.Words 授權檔 (`aspose.words.lic`) 可被存取。 |
| **處理超大型文件時記憶體會不會爆掉？** | 回呼會收到每個資源的完整位元組陣列，意味著圖像會暫時佔用記憶體。若文件達到數十 GB，建議在回呼內直接將資料串流寫入磁碟，而非返回位元組。 |

---

## 結論

現在你已掌握 **如何設定回呼**，在 **將 DOCX 儲存為 Markdown** 時自行控制圖像抽取。此方法讓你 **從 DOCX 匯出圖像**、**從 Word 抽取 SVG**，同時保持 Markdown 檔案的整潔與可預測性。  

在單一、完整的腳本中，我們示範了載入文件、定義資源儲存回呼、設定 `MarkdownSaveOptions`，以及處理檔名衝突與向量圖等邊緣情況。最終產出的是一組唯一命名的資產，搭配正確連結的 Markdown 檔案，適用於靜態網站生成器、文件管線或任何需要乾淨、可重用資源的工作流程。

**接下來的步驟？**  
- 嘗試與 MkDocs 等靜態網站生成器結合，實現 Word 文件的自動發布。  
- 若偏好內嵌圖像，可將 `markdown_options.export_images_as_base64 = True`，改為使用 Base64 內嵌。  
- 深入探索 Aspose.Words 其他回呼（例如 `document_saving_callback`），進一步自訂 Markdown 輸出本身。

對 **如何從其他 Office 格式抽取圖像** 有更多疑問，或需要針對特定命名慣例調整回呼？歡迎在下方留言，祝開發順利！

## 接下來該學什麼？

以下教學與本篇內容緊密相關，能進一步擴展你的技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助你掌握更多 API 功能，或探索其他實作方式。

- [How to Rename Images When Converting DOCX to Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)
- [How to Save Markdown from DOCX – Step‑by‑Step Guide](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}