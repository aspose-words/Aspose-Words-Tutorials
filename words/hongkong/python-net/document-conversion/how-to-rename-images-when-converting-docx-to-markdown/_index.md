---
category: general
date: 2026-06-30
description: 如何在將 DOCX 轉換為 Markdown 時重新命名圖片。學習更改圖片名稱，並以自訂圖片檔名將 Word 儲存為 Markdown。
draft: false
keywords:
- how to rename images
- convert docx to markdown
- change image names
- save word as markdown
- custom image filenames
language: zh-hant
og_description: 在將 DOCX 轉換為 Markdown 時如何重新命名圖片。本指南將示範如何更改圖片名稱、將 Word 儲存為 Markdown，以及使用自訂圖片檔名。
og_title: 將 DOCX 轉換為 Markdown 時如何重新命名圖片
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: How to rename images while converting DOCX to markdown. Learn to change
    image names and save Word as markdown with custom image filenames.
  headline: How to Rename Images When Converting DOCX to Markdown
  type: TechArticle
- description: How to rename images while converting DOCX to markdown. Learn to change
    image names and save Word as markdown with custom image filenames.
  name: How to Rename Images When Converting DOCX to Markdown
  steps:
  - name: Why Use a GUID?
    text: '* **Uniqueness** – A GUID (`uuid4`) guarantees that two images will never
      clash, even across multiple runs. * **Traceability** – If you need to debug
      later, the GUID can be logged alongside the original Word paragraph number.
      * **Portability** – No reliance on the original Word naming scheme, which '
  - name: Expected Output (excerpt)
    text: '```markdown # Sample Document'
  - name: What if the document contains non‑image resources?
    text: Our callback already checks the file extension and returns `True` for anything
      that isn’t an image. This means CSS files, fonts, or embedded OLE objects keep
      their original names, which is usually what you want when you **save word as
      markdown**.
  - name: Can I use a custom naming scheme instead of GUIDs?
    text: 'Absolutely. Replace the `uuid.uuid4()` call with any function that returns
      a string. For example, you could prepend the original paragraph index:'
  - name: How does this affect performance on large documents?
    text: The callback runs once per resource, so the overhead is minimal—mostly the
      time to generate a GUID. Even a 200‑page report with dozens of images finishes
      in under a second on a modern laptop.
  - name: What if I need the image filenames to be deterministic (e.g., for CI builds)?
    text: 'Swap `uuid.uuid4()` for a hash of the original image bytes:'
  type: HowTo
tags:
- Aspose.Words
- Python
- Markdown
- Image Processing
title: 將 DOCX 轉換為 Markdown 時如何重新命名圖片
url: /zh-hant/python/document-conversion/how-to-rename-images-when-converting-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在將 DOCX 轉換為 Markdown 時重新命名圖像

有沒有想過在將 DOCX 檔案轉換為 Markdown 時，**自動重新命名圖像**？你並非唯一有此疑問的人。在許多文件流程中，預設的圖像名稱（例如 `image1.png`）會變成難以追蹤的惡夢，尤其當相同的 markdown 在團隊間進行版本控制時。  

好消息是，Aspose.Words for Python 讓即時 **變更圖像名稱** 變得輕而易舉，您可以保持 Markdown 的整潔，同時保留一個命名自訂的資產資料夾。  

在本教學中您將學會：

* 在 Python 中載入 Word 文件（`.docx`）。  
* 使用回呼在 Markdown 儲存過程中為每個圖像賦予 GUID 為基礎的檔名。  
* 將文件儲存為 Markdown，讓產生的檔案引用新命名的圖像。  

如果您對基本的 Python 已有了解且已安裝 Aspose.Words，五分鐘內即可上手。無需外部腳本、無需手動重新命名——只要一個自包含的程式即可完成繁重工作。

---

## 前置條件 — 開始前您需要的項目

| 需求 | 原因說明 |
|------|----------|
| **Python 3.7+** | 範例使用 3.6 版引入的 f‑strings 與型別提示，但 3.7+ 提供 `os.path.splitext` 的便利功能。 |
| **Aspose.Words for Python via .NET** (`pip install aspose-words`) | 此函式庫提供我們依賴的 `aw.Document` 類別與 `MarkdownSaveOptions`。 |
| **Write permission** to the output folder | 回呼函式會建立新圖像檔案，腳本必須具備寫入權限。 |
| **A DOCX file** you want to convert | 任何從簡單報告到複雜手冊的檔案皆可使用。 |

> **專業提示：** 若您使用虛擬環境，請在安裝 Aspose.Words 前先啟用它。這可將相依性隔離，避免版本衝突。

## 步驟 1：載入 Word 文件  

當您想要 **將 docx 轉換為 markdown** 時，第一件事就是開啟來源檔案。Aspose.Words 抽象化了所有低階的 OPC 處理，只需一行程式碼即可完成。

```python
import aspose.words as aw

# Replace YOUR_DIRECTORY with the folder that holds your .docx file
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

*為何重要：* 若未載入文件，您無法檢查其資源，Markdown 匯出器也沒有可寫入的內容。`aw.Document` 物件會在記憶體中保存整個 Word 套件，讓您在儲存前安全地操作。

## 步驟 2：撰寫一個 **重新命名圖像資源** 的回呼函式  

Aspose.Words 允許您將 `resource_saving_callback` 插入 `MarkdownSaveOptions`。此回呼在每個資源（圖像、CSS 等）寫入磁碟前被呼叫。透過變更 `resource.file_name`，我們可以強制使用 **自訂圖像檔名**。

```python
def rename_image_resource(resource):
    """
    Rename image resources with a unique GUID before saving.
    This is where we implement how to rename images.
    """
    import uuid, os

    # Guard: only process image resources, ignore CSS or other files
    if not resource.file_name.lower().endswith(('.png', '.jpg', '.jpeg', '.gif', '.bmp')):
        return True  # Let Aspose handle non‑image resources unchanged

    # Extract the original extension so we keep PNG as PNG, JPG as JPG, etc.
    _, ext = os.path.splitext(resource.file_name)

    # Generate a globally unique identifier and tack the original extension on
    new_name = f"{uuid.uuid4()}{ext}"
    resource.file_name = new_name

    # Returning True tells Aspose to proceed with the default saving logic
    return True
```

### 為何使用 GUID？

* **唯一性** – GUID（`uuid4`）保證即使在多次執行中，兩個圖像也不會衝突。  
* **可追蹤性** – 若日後需除錯，可將 GUID 與原始 Word 段落編號一起記錄。  
* **可移植性** – 不依賴原始 Word 的命名規則，避免因空格或特殊字元導致 Markdown 連結失效。

## 步驟 3：將回呼附加至 Markdown 儲存選項  

現在我們告訴 Aspose，無論何時寫入圖像至輸出資料夾，都使用我們的重新命名邏輯。

```python
md_options = aw.saving.MarkdownSaveOptions()
md_options.resource_saving_callback = rename_image_resource

# Optional: control where images are placed relative to the markdown file
md_options.images_folder = "images"  # creates a sub‑folder called 'images'
```

*說明：* `MarkdownSaveOptions` 類別控制從換行到圖像資料夾位置的所有設定。透過設定 `resource_saving_callback`，您取得一個 **掛鉤**，在每個嵌入資源寫入前觸發，讓您有機會在檔案寫入磁碟前 **變更圖像名稱**。

## 步驟 4：將文件儲存為 Markdown – 最後一步  

有了回呼後，最後一步相當直接。

```python
output_path = "YOUR_DIRECTORY/CustomResources.md"
doc.save(output_path, md_options)
print(f"Markdown saved to {output_path}")
```

腳本執行完畢後，您會看到：

* `CustomResources.md` – 您的 Word 檔案的 Markdown 表示。  
* 一個 `images/` 資料夾（或您設定的任何資料夾），內含如 `d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e.png` 的檔案。  

Markdown 檔案會引用新的 GUID 為基礎的檔名，因此任何後續處理器（GitHub、MkDocs 等）都會正確取得圖像，您無需手動重新命名。

### 預期輸出（摘錄）

```markdown
# Sample Document

Here is an image that was originally called `image1.png` in the DOCX:

![d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e](images/d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e.png)

And another one:

![a1b2c3d4-e5f6-7a8b-9c0d-e1f2a3b4c5d6](images/a1b2c3d4-e5f6-7a8b-9c0d-e1f2a3b4c5d6.jpg)
```

每次執行產生的 GUID 會不同，但模式保持一致。

## 處理邊緣案例與常見問題  

### 若文件包含非圖像資源，該怎麼辦？

我們的回呼已檢查檔案副檔名，對非圖像的資源回傳 `True`。這表示 CSS 檔案、字型或嵌入的 OLE 物件會保留原始名稱，這通常是您在 **將 word 儲存為 markdown** 時想要的行為。

### 我可以使用自訂命名規則取代 GUID 嗎？

當然可以。將 `uuid.uuid4()` 呼叫替換為任何回傳字串的函式。例如，您可以在前面加上原始段落索引：

```python
new_name = f"para{resource.resource_id}{ext}"
```

只要確保產生的名稱在整份文件中是唯一的即可。

### 這對大型文件的效能有何影響？

回呼會對每個資源執行一次，因此開銷極小——主要是產生 GUID 的時間。即使是 200 頁、包含數十張圖像的報告，在現代筆記型電腦上也能在一秒內完成。

### 若需要圖像檔名具決定性（例如 CI 建置），該怎麼辦？

將 `uuid.uuid4()` 換成原始圖像位元組的雜湊值：

```python
import hashlib
hash = hashlib.sha256(resource.raw_bytes).hexdigest()[:12]
new_name = f"{hash}{ext}"
```

這樣在相同來源圖像上每次執行腳本時，都會產生相同的檔名。

## 完整可執行腳本 – 複製、貼上、執行  



## 接下來您應該學習什麼？

以下教學涵蓋與本指南緊密相關的主題，並以此為基礎。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在自己的專案中探索替代實作方式。

- [將 docx 儲存為 markdown – 完整 C# 指南與圖像提取](/words/english/net/programming-with-markdownsaveoptions/save-docx-as-markdown-full-c-guide-with-image-extraction/)
- [如何從 DOCX 儲存 Markdown – 步驟指南](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}