---
category: general
date: 2026-06-27
description: 使用 Python 將 docx 轉換為 markdown。學習從 Word 中提取圖片，並使用自訂回呼函式儲存 markdown 輸出。
draft: false
keywords:
- convert docx to markdown
- extract images from word
- convert word to markdown
- python docx to markdown
- save markdown output
language: zh-hant
og_description: 在 Python 中將 docx 轉換為 markdown，從 Word 中提取圖片，並使用自訂資源回呼函式儲存 markdown
  輸出。
og_title: 將 docx 轉換為 markdown – Python 指南（含圖片提取）
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Convert docx to markdown using Python. Learn to extract images from
    Word and save markdown output with a custom callback.
  headline: Convert docx to markdown – Complete Python Guide with Image Extraction
  type: TechArticle
- description: Convert docx to markdown using Python. Learn to extract images from
    Word and save markdown output with a custom callback.
  name: Convert docx to markdown – Complete Python Guide with Image Extraction
  steps:
  - name: Expected Output
    text: '```markdown # Sample Document'
  - name: Quick sanity check
    text: '```bash # On Unix/macOS cat YOUR_DIRECTORY/output.md ls YOUR_DIRECTORY/images/
      ```'
  - name: Dealing with duplicate image names
    text: 'Word sometimes reuses the same internal name for different pictures. To
      avoid overwriting, you can tweak `image_saver`:'
  - name: Converting large documents
    text: 'For multi‑megabyte documents, consider streaming the output to avoid memory
      spikes:'
  type: HowTo
tags:
- Python
- Aspose.Words
- Document Conversion
title: 將 docx 轉換為 markdown – 完整 Python 指南與圖像提取
url: /zh-hant/python/document-conversion/convert-docx-to-markdown-complete-python-guide-with-image-ex/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 將 docx 轉換為 markdown – 完整 Python 指南與圖片提取

有沒有想過如何 **convert docx to markdown** 而不遺失 Word 檔案中嵌入的圖片？你並不是唯一的遇到這個問題的人。許多開發者在轉換時圖片會消失，導致 markdown 出現斷裂的連結，甚至根本沒有圖片。  

好消息是？只需幾行 Python 程式碼搭配 Aspose.Words，即可輕鬆將 `.docx` 轉換為乾淨的 markdown **並** 把每張圖片抽取到您指定的資料夾中。本教學將逐步說明整個流程，從安裝函式庫到設定回呼函式，將每張圖片儲存到您想要的位置。  

完成本指南後，您將能夠 **convert word to markdown**，提取所有圖形，並 **save markdown output**，可直接用於靜態網站生成器、文件化流程或任何其他 markdown 為先的工作流程。

## 您需要的條件

- Python 3.8 或更新版本（程式碼在 3.9+ 亦可運作）  
- `pip` 可用於安裝第三方套件  
- 有效的 Aspose.Words for Python 授權（免費試用版可用於評估）  
- 一個包含文字與至少一張圖片的範例 `input.docx`  

就這樣——不需要大型的 Office 安裝，不需要 COM 互操作，純粹使用 Python。

## 步驟 1：安裝 Aspose.Words for Python

首先，先取得函式庫。打開終端機並執行：

```bash
pip install aspose-words
```

如果遇到權限錯誤，請在指令前加上 `--user` 或使用虛擬環境。安裝完成後，您即可使用 `aspose.words` 套件（在範例中以 `aw` 匯入）。

> **專業提示：** 請保持 `requirements.txt` 整潔；加入 `aspose-words==<latest-version>`，讓協作者能精確重現環境。

## 步驟 2：設定自訂圖片儲存回呼函式

Aspose.Words 允許您透過 *resource‑saving callback* 鉤入儲存流程。可將其視為中介，接收每張圖片的位元組串流，並告訴函式庫在產生的 markdown 檔案中如何引用它。

以下是回呼函式的核心：

```python
# Step 1: Define a callback to store extracted images in a custom folder
def image_saver(image_bytes, image_name):
    """
    Saves an image to YOUR_DIRECTORY/images/ and returns the relative path
    that will be placed in the markdown file.
    """
    # Ensure the target folder exists
    import os
    target_dir = os.path.join("YOUR_DIRECTORY", "images")
    os.makedirs(target_dir, exist_ok=True)

    # Build the full path on disk
    file_path = os.path.join(target_dir, image_name)

    # Write the raw image bytes to disk
    with open(file_path, "wb") as f:
        f.write(image_bytes)

    # Return the path that markdown will use (relative to the .md file)
    return os.path.join("images", image_name)
```

**為什麼這很重要：**  
- **Control** – 您可以自行決定資料夾結構、命名規則，甚至在需要時轉換圖片格式。  
- **Portability** – 回傳的相對路徑使 markdown 能在不同機器間保持可攜，只要 `images` 資料夾一起搬移即可。  
- **Performance** – 回呼函式對每張圖片僅執行一次，避免重複寫入。

## 步驟 3：設定 Markdown 儲存選項

現在我們將回呼函式綁定到 `MarkdownSaveOptions` 物件。這會告訴 Aspose.Words 每當遇到圖片資源時，都使用我們的 `image_saver`。

```python
# Step 2: Create Markdown save options and attach the callback
md_options = aw.saving.MarkdownSaveOptions()
md_options.resource_saving_callback = image_saver
```

您也可以在此調整一些可選設定，例如 `export_images_as_base64`（設為 `False`，因為我們希望圖片為獨立檔案）或 `add_table_of_contents`（若需要目錄）。本指南中我們將使用預設值。

## 步驟 4：載入來源 Word 文件

載入 `.docx` 非常簡單。只要將 Aspose.Words 指向檔案路徑即可：

```python
# Step 3: Load the source Word document
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

如果文件很大，您可以考慮使用 `aw.LoadOptions` 以串流方式載入，但對於大多數情況，直接使用簡單的建構子即可。

## 步驟 5：儲存為 Markdown – 讓回呼函式負責繁重工作

最後，我們請 Aspose.Words 輸出 markdown 檔案。函式庫會對每張嵌入的圖片呼叫 `image_saver`，儲存檔案，並嵌入正確的 markdown 圖片連結。

```python
# Step 4: Save the document as Markdown, letting the callback handle image resources
doc.save("YOUR_DIRECTORY/output.md", md_options)
```

流程完成後，您會看到兩件事：

1. `output.md` 包含 markdown 文字，裡面有類似 `![](images/image1.png)` 的行  
2. 一個 `images` 子資料夾，內含每張抽取出的圖片。

### 預期輸出

```markdown
# Sample Document

This is a paragraph from the Word file.

![](images/image1.png)

Another paragraph follows the picture.
```

在任何 markdown 預覽工具（如 VS Code、GitHub、MkDocs）中開啟 `output.md`，您應該會看到圖片如同原始 Word 檔案中呈現的一樣。

## 步驟 6：驗證結果並處理邊緣案例

### 快速檢查

```bash
# On Unix/macOS
cat YOUR_DIRECTORY/output.md
ls YOUR_DIRECTORY/images/
```

確保圖片檔名與 markdown 中的路徑相符。若發現缺少圖片，請再次確認回呼函式回傳的是 **相對** 路徑（而非絕對路徑），且 `images` 資料夾的引用正確。

### 處理重複的圖片名稱

Word 有時會為不同的圖片使用相同的內部名稱。為避免覆寫，您可以調整 `image_saver`：

```python
import uuid

def image_saver(image_bytes, image_name):
    unique_name = f"{uuid.uuid4().hex}_{image_name}"
    # rest of the code uses unique_name instead of image_name
    ...
    return os.path.join("images", unique_name)
```

### 轉換大型文件

對於多兆位元組的文件，建議使用串流輸出以避免記憶體激增：

```python
with open("YOUR_DIRECTORY/output.md", "w", encoding="utf-8") as out_file:
    doc.save(out_file, md_options)
```

Aspose.Words 會在內部處理串流，因此您不必將整個 markdown 載入記憶體。

## 步驟 7：自動化工作流程（可選）

如果需要批次處理一個資料夾中的 Word 檔案，可將邏輯包在迴圈中：

```python
import glob

for doc_path in glob.glob("YOUR_DIRECTORY/*.docx"):
    doc = aw.Document(doc_path)
    base_name = os.path.splitext(os.path.basename(doc_path))[0]
    md_path = f"YOUR_DIRECTORY/{base_name}.md"
    doc.save(md_path, md_options)
    print(f"Converted {doc_path} → {md_path}")
```

現在您只要把數百個 `.docx` 檔案放入該目錄，腳本就會逐一處理，每個檔案都會有自己的 `images` 子資料夾。

## 結論

我們已說明如何在保留所有圖片的前提下 **convert docx to markdown**，只需使用簡潔的 Python 腳本與 Aspose.Words 強大的回呼機制。您現在已了解如何：

- **Extract images from Word** 透過自訂的 `resource_saving_callback` 抽取圖片  
- **Convert word to markdown** 以最少的設定完成轉換  
- **Save markdown output** 並將其與整齊排列的圖片資料夾一起儲存  

接下來您可以嘗試額外的 markdown 擴充功能（如表格、腳註），或將此腳本整合到自動建置文件的 CI 流程中。無限可能——只要記得保持圖片儲存邏輯的彈性，您的 markdown 就能保持整潔。  

對於邊緣案例或授權有任何疑問？請在下方留言，祝編程愉快！

## 接下來您可以學習什麼？

以下教學涵蓋與本指南密切相關的主題，建立在本篇示範的技術之上。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通其他 API 功能，並在自己的專案中探索替代實作方式。

- [如何從 Word 儲存 Markdown – 完整 Python 指南](/words/english/python-net/document-conversion/how-to-save-markdown-from-word-complete-python-guide/)
- [將 Docx 檔案轉換為 Markdown](/words/english/net/basic-conversions/docx-to-markdown/)
- [將 Word 轉換為 Markdown – 以 Base64 嵌入圖片](/words/english/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}