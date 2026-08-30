---
category: general
date: 2026-06-21
description: 匯出 Word 為 Markdown 並使用 Python 儲存 Word 中的圖片。學習如何將 docx 轉換為 markdown、使用
  Python 寫入二進位檔案，以及從 docx 中提取圖片。
draft: false
keywords:
- export word to markdown
- convert docx to markdown
- save images from word
- write binary file python
- how to extract images from docx
language: zh-hant
og_description: 將 Word 匯出為 Markdown 並自動儲存 Word 圖片。本分步指南說明如何將 docx 轉換為 markdown、使用
  Python 寫入二進位檔案，以及從 docx 中提取圖片。
og_title: 將 Word 匯出為 Markdown – 完整 Python 教學
schemas:
- author: Aspose
  dateModified: '2026-06-21'
  description: Export Word to Markdown and save images from Word using Python. Learn
    how to convert docx to markdown, write binary file python, and extract images
    from docx.
  headline: Export Word to Markdown – Full Guide with Image Extraction in Python
  type: TechArticle
- description: Export Word to Markdown and save images from Word using Python. Learn
    how to convert docx to markdown, write binary file python, and extract images
    from docx.
  name: Export Word to Markdown – Full Guide with Image Extraction in Python
  steps:
  - name: Expected Output Example
    text: 'If `input.docx` contained a single picture named `image1.png`, the resulting
      `output.md` might look like:'
  - name: What if the document has duplicate image names?
    text: 'Aspose.Words will suggest the same name for identical images. Our callback
      uses the suggested name directly, which could cause overwrites. To avoid that,
      modify the callback to append a unique identifier:'
  - name: Can I change the image format during extraction?
    text: Absolutely. After writing the binary data, you could open it with Pillow
      (`PIL.Image`) and save it as a different format (e.g., JPEG). This is useful
      when you need to **convert docx to markdown** for a web‑optimized site.
  - name: Does this work on macOS/Linux as well as Windows?
    text: Yes. The code uses `os.path` and avoids hard‑coded path separators, so it’s
      cross‑platform. Just remember to grant the script write permissions to the target
      directory.
  - name: What if I need to export tables or footnotes too?
    text: '`MarkdownSaveOptions` supports a range of features—tables become markdown
      tables, footnotes become inline references. No extra code is required; just
      experiment with the generated markdown to see how it renders.'
  type: HowTo
tags:
- python
- docx
- markdown
- image-extraction
title: 將 Word 匯出為 Markdown – Python 圖片提取完整指南
url: /zh-hant/python/document-conversion/export-word-to-markdown-full-guide-with-image-extraction-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 將 Word 匯出為 Markdown – 完整指南與圖片提取（Python）

有沒有想過如何 **export Word to markdown** 而不遺失文件中嵌入的圖片？你並不是唯一有此疑問的人——開發者們不斷尋求一種無痛的方式，將 `.docx` 轉換為乾淨的 markdown，同時保留每張圖片。

在本教學中，我們將逐步說明一個完整的解決方案，不僅能 **convert docx to markdown**，還能 **save images from word** 檔案，全部使用純 Python。完成後，你將擁有一個即時可執行的腳本，能以 binary file python 方式寫入檔案，並提取所有需要的圖片。

## 本指南涵蓋內容

- 安裝正確的函式庫 (Aspose.Words for Python)  
- 定義一個將二進位資料寫入磁碟的回呼函式  
- 將 Word 文件轉換為 markdown，並處理圖片  
- 驗證輸出並排除常見問題  

不需要外部服務，也不需手動複製貼上——只要一個獨立的腳本即可直接放入任何專案中使用。

## 前置條件

在開始之前，請確保你已具備以下條件：

| Requirement | Why it matters |
|-------------|----------------|
| Python 3.8+ | 現代語法與型別提示 |
| `pip` 存取權限 | 用於安裝 Aspose.Words 套件 |
| 對資料夾的寫入權限 | 回呼函式會以 **write binary file python** 方式寫入檔案 |
| 含有圖片的 `.docx` 檔案 | 以觀察 **save images from word** 功能的實際運作 |

如果上述任一項目聽起來陌生，別擔心——接下來的步驟會教你如何設定。

## 步驟 1：透過 pip 安裝 Aspose.Words for Python

Aspose.Words 是一個功能強大的函式庫，能完整解析 Word 文件格式，包括嵌入的媒體。使用以下單行指令即可安裝：

```bash
pip install aspose-words
```

> **專業提示：** 使用虛擬環境 (`python -m venv venv`) 以保持相依套件整潔，同時避免與其他專案的版本衝突。

## 步驟 2：建立資源儲存回呼函式（Write Binary File Python）

此解決方案的核心是一個回呼函式，會接收每個二進位資源（例如圖片），並決定儲存位置。這裡就是我們以 **write binary file python** 方式寫入檔案的地方。

```python
def my_resource_saver(resource: bytes, suggested_name: str) -> str:
    """
    Save a binary resource (e.g., an image) to a custom folder and
    return the relative path for markdown linking.

    :param resource: Raw binary data of the resource.
    :param suggested_name: A filename suggested by Aspose.Words.
    :return: Relative path to be used in the markdown file.
    """
    # Build a relative path inside a custom folder.
    folder = "custom_images"
    os.makedirs(folder, exist_ok=True)          # Ensure the folder exists.
    file_path = os.path.join(folder, suggested_name)

    # Write the binary data to disk – classic write binary file python.
    with open(file_path, "wb") as f:
        f.write(resource)

    # Return the path so the Markdown writer can reference it.
    return file_path
```

**為什麼需要回呼函式？**  
Aspose.Words 不知道你希望圖片儲存於何處。將 `my_resource_saver` 提供給它後，你即可完全掌控檔名、資料夾結構，甚至在需要時進行後處理（例如圖片壓縮）。

## 步驟 3：載入來源 Word 文件

現在我們將函式庫指向欲轉換的 `.docx` 檔案。

```python
import aspose.words as aw
import os

# Adjust the path to your actual file location.
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)
```

若找不到檔案，請再次確認路徑並確保腳本具有讀取權限。常見錯誤是 Windows 上混用正斜線與反斜線；`os.path.join` 會為你處理這些差異。

## 步驟 4：設定 Markdown 儲存選項並掛載回呼函式

此步驟將所有設定串接起來。我們告訴 Aspose.Words 使用 markdown 作為輸出格式，並在遇到圖片時呼叫我們的 `my_resource_saver`。

```python
# Create Markdown save options.
md_save = aw.saving.MarkdownSaveOptions()

# Attach the resource‑saving callback.
md_save.resource_saving_callback = my_resource_saver
```

你可以在此微調 markdown 輸出（例如，若偏好嵌入式圖片，可將 `md_save.export_images_as_base64 = False` 設為 False）。對於 **how to extract images from docx** 的需求，將圖片保存為獨立檔案通常較為整潔。

## 步驟 5：匯出文件 – 最終的 Export Word to Markdown 呼叫

剩下的就是執行繁重工作的單行程式碼。

```python
output_md = "YOUR_DIRECTORY/output.md"
doc.save(output_md, md_save)
print(f"✅ Markdown saved to {output_md}")
print(f"🖼️ Images stored in ./custom_images/")
```

執行腳本後，你會看到一個 `output.md` 檔案，旁邊會產生 `custom_images` 資料夾，內含原始 Word 檔案的所有圖片。markdown 會以相對路徑引用這些圖片，方便用於靜態網站產生器或 GitHub 渲染。

### 預期輸出範例

若 `input.docx` 內僅包含一張名為 `image1.png` 的圖片，產生的 `output.md` 可能如下：

```markdown
# Sample Document

Here is an illustration:

![image1.png](custom_images/image1.png)

More text follows...
```

以及資料夾結構：

```
/YOUR_DIRECTORY/
│─ input.docx
│─ output.md
└─ custom_images/
   └─ image1.png
```

## 常見問題與邊緣案例

### 如果文件中有重複的圖片名稱該怎麼辦？

Aspose.Words 會為相同的圖片建議相同的名稱。我們的回呼直接使用建議的名稱，可能導致覆寫。為避免此情況，請修改回呼以在名稱後加入唯一識別碼：

```python
import uuid

def my_resource_saver(resource, suggested_name):
    unique_name = f"{uuid.uuid4().hex}_{suggested_name}"
    # rest of the code unchanged...
```

### 我可以在提取過程中變更圖片格式嗎？

當然可以。寫入二進位資料後，你可以使用 Pillow（`PIL.Image`）將其開啟並另存為其他格式（例如 JPEG）。當你需要為網站優化而 **convert docx to markdown** 時，這非常有用。

### 這在 macOS/Linux 以及 Windows 上都能正常運作嗎？

可以。程式碼使用 `os.path` 並避免硬編碼路徑分隔符號，因而具備跨平台特性。只需確保腳本對目標目錄具有寫入權限即可。

### 如果我還需要匯出表格或註腳呢？

`MarkdownSaveOptions` 支援多種功能——表格會轉換為 markdown 表格，註腳會變為內嵌參考。無需額外程式碼，只要試著檢視產生的 markdown，即可了解其呈現效果。

## 完整腳本 – 可直接複製貼上

以下為完整、可執行的範例，整合了前述所有步驟。將其儲存為 `export_word_to_md.py`，然後執行 `python export_word_to_md.py`。

```python
import os
import uuid
import aspose.words as aw

def my_resource_saver(resource: bytes, suggested_name: str) -> str:
    """
    Save binary resources (images) to a custom folder and return
    the relative path for markdown references.
    """
    folder = "custom_images"
    os.makedirs(folder, exist_ok=True)

    # Ensure unique filenames to avoid collisions.
    unique_name = f"{uuid.uuid4().hex}_{suggested_name}"
    file_path = os.path.join(folder, unique_name)

    with open(file_path, "wb") as f:
        f.write(resource)

    return file_path

def main():
    # ------------------------------------------------------------------
    # 1️⃣ Load the Word document you want to convert.
    # ------------------------------------------------------------------
    doc_path = "YOUR_DIRECTORY/input.docx"
    if not os.path.isfile(doc_path):
        raise FileNotFoundError(f"❌ {doc_path} does not exist.")
    doc = aw.Document(doc_path)

    # ------------------------------------------------------------------
    # 2️⃣ Set up markdown options and plug in the image callback.
    # ------------------------------------------------------------------
    md_save = aw.saving.MarkdownSaveOptions()
    md_save.resource_saving_callback = my_resource_saver

    # ------------------------------------------------------------------
    # 3️⃣ Perform the export – this is the core **export word to markdown** step.
    # ------------------------------------------------------------------
    output_md = "YOUR_DIRECTORY/output.md"
    doc.save(output_md, md_save)

    print(f"✅ Markdown exported to: {output_md}")
    print(f"🖼️ Extracted images are in the folder: ./custom_images/")

if __name__ == "__main__":
    main()
```

執行後，用任何 markdown 檢視器開啟 `output.md`，即可看到原始 Word 內容——文字、標題、**save images from word**，以及其他所有元素——完整還原。

## 結論

我們剛剛示範了一種穩健的方式，能 **export word to markdown** 同時保留所有嵌入的圖片。透過結合 Aspose.Words 與自訂的 **resource‑saving callback**，你可以 **convert docx to markdown**、**write binary file python**，並在單一可重用的腳本中解決經典的 **how to extract images from docx** 問題。

接下來可以做什麼？試著加入使用 Pillow 壓縮圖片的步驟，或將此腳本整合至 CI 流程，自動將文件轉換為靜態網站的文件。可能性無窮，而你現在已擁有堅實的基礎可供延伸。

有任何回饋或遇到問題嗎？在下方留言吧——祝編程愉快！

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，建立在本篇示範的技術之上。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助你精通更多 API 功能，並在自己的專案中探索其他實作方式。

- [如何從 Word 儲存 Markdown – 完整 Python 指南](/words/english/python-net/document-conversion/how-to-save-markdown-from-word-complete-python-guide/)
- [修復損毀的 DOCX 並將 Word 轉換為 Markdown](/words/english/python-net/document-conversion/recover-corrupted-docx-convert-word-to-markdown/)
- [儲存 Word 圖片 – 使用 Aspose 將 Word 轉換為 Markdown](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}