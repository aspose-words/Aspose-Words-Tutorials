---
category: general
date: 2026-10-04
description: 在 Aspose.Words 中啟用恢復模式，以安全方式復原受損的 Word 文件。請遵循逐步指南，內含完整的 Python 程式碼與說明。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- enable recovery mode
- recover corrupted word document
- Aspose.Words load options
- document recovery Python
- handling damaged .docx files
language: zh-hant
lastmod: 2026-10-04
og_description: 啟用復原模式以使用 Aspose.Words 復原受損的 Word 文件。本教學展示了完整的 Python 程式碼、其運作原理，以及如何處理邊緣情況。
og_image_alt: Screenshot of Python code loading a corrupted Word document with recovery
  mode enabled
og_title: 啟用恢復模式以復原損毀的 Word 文件 – 完整指南
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Enable recovery mode in Aspose.Words to recover a corrupted Word document
    safely. Follow the step‑by‑step guide with full Python code and explanations.
  headline: Enable recovery mode to recover a corrupted Word document
  type: TechArticle
- description: Enable recovery mode in Aspose.Words to recover a corrupted Word document
    safely. Follow the step‑by‑step guide with full Python code and explanations.
  name: Enable recovery mode to recover a corrupted Word document
  steps:
  - name: Create `LoadOptions` and set `recovery_mode` to `RECOVER`.
    text: Create `LoadOptions` and set `recovery_mode` to `RECOVER`.
  - name: Load the `.docx` using those options.
    text: Load the `.docx` using those options.
  - name: Verify the mode and optionally save a repaired copy.
    text: Verify the mode and optionally save a repaired copy.
  type: HowTo
tags:
- Aspose.Words
- Python
- Document processing
- Error handling
title: 啟用復原模式以復原受損的 Word 文件
url: /zh-hant/python/document-options-and-settings/enable-recovery-mode-to-recover-a-corrupted-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 啟用復原模式以修復損毀的 Word 文件

如果您需要在載入 Word 檔案時**啟用復原模式**，本指南將向您展示如何使用 Aspose.Words for Python 完成此操作。開啟復原模式後，您可以**修復損毀的 Word 文件**，避免拋出例外。

在以下章節中，您將學習：

* 哪些類別與屬性控制復原行為。  
* 如何在不讓應用程式崩潰的情況下載入可能受損的 `.docx` 檔案。  
* 疑難排解常見載入問題與自訂復原策略的技巧。

> **先決條件** – 您已安裝 Aspose.Words for Python（`pip install aspose-words`），並具備 Python 檔案 I/O 的基本概念。

## 復原模式的功能與為何應該啟用它

Aspose.Words 在將 Word 檔案的內部結構解析為 `Document` 物件之前，會先解析其結構。當檔案損毀——缺少部份、XML 損壞或關聯無效——解析器可能會：

| 模式 | 行為 |
|------|------------|
| `STRICT` | 在首次偵測到損毀時拋出例外。 |
| `IGNORE_ERRORS` | 跳過無法讀取的部份，但可能會悄悄遺失內容。 |
| `RECOVER` (**啟用復原模式**選項) | 嘗試重建文件，盡可能保留內容，並透過 `load_options.recovery_mode` 暴露所選模式。 |

`RECOVER` 是在您必須**修復損毀的 Word 文件**以進行後續處理（例如抽取文字或轉換為 PDF）時的建議選擇。

## 步驟 1：建立 LoadOptions 並啟用復原模式

第一步是實例化 `LoadOptions`，並將 `recovery_mode` 屬性設定為 `RecoveryMode.RECOVER`。這會告訴函式庫在解析過程中進入復原路徑。

```python
import aspose.words as aw

# Step 1: Create load options and enable recovery mode
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER  # alternatives: .IGNORE_ERRORS, .STRICT
```

**為何重要：**  
如果跳過此步驟且文件受損，建構子 `aw.Document(...)` 會拋出 `InvalidOperationException`。啟用復原模式可防止崩潰，並提供一個部分修復的 `Document` 物件供您繼續使用。

## 步驟 2：使用指定的選項載入可能損毀的文件

將 `load_options` 實例傳遞給 `Document` 建構子。載入器現在會自動套用復原演算法。

```python
# Step 2: Load the potentially corrupted document using the specified options
doc_path = "YOUR_DIRECTORY/Corrupted.docx"
doc = aw.Document(doc_path, load_options)
```

**提示：**將 `YOUR_DIRECTORY` 替換為執行環境可存取的絕對或相對路徑。如果檔案不存在，Aspose.Words 會在進入復原邏輯之前拋出 `FileNotFoundError`。

## 步驟 3：驗證已套用復原模式

您可以透過檢查 `load_options.recovery_mode` 來確認目前使用的模式。此資訊對於日誌記錄或後續流程的條件處理非常有用。

```python
# Step 3: Confirm that the document was loaded with the chosen recovery mode
print("Document loaded with recovery mode:", load_options.recovery_mode)
```

**預期輸出**

```
Document loaded with recovery mode: RecoveryMode.RECOVER
```

如果輸出顯示 `RECOVER`，即表示您已成功**啟用復原模式**，文件現在已可進行後續處理（例如抽取文字、轉換為 PDF，或儲存修復後的副本）。

## 步驟 4（可選）：儲存修復副本以供未來使用

載入完成後，您可能想將修復後的文件持久化，避免重複執行復原步驟。

```python
# Optional: Save the repaired document
repaired_path = "YOUR_DIRECTORY/Corrupted_Repaired.docx"
doc.save(repaired_path)
print(f"Repaired document saved to {repaired_path}")
```

儲存會產生一個新的 `.docx`，Aspose.Words 視其為有效檔案，可在 Microsoft Word 中開啟且不會出現警告。

## 常見問題與邊緣案例處理

| 問題 | 答案 |
|----------|--------|
| **如果文件完全無法讀取該怎麼辦？** | 即使在 `RECOVER` 模式下，某些檔案仍無法修復。`Document` 物件會被建立，但可能只包含一個空白頁面。請檢查 `doc.get_page_count()` 以驗證內容。 |
| **載入後可以改成 `IGNORE_ERRORS` 嗎？** | 不行。復原模式必須在 `Document` 建構子執行 **之前** 設定。如需不同策略，請重新建立 `LoadOptions` 實例。 |
| **復原模式會影響效能嗎？** | 會。因為函式庫需要嘗試重建損壞的部份，會產生少量額外開銷。對大多數檔案（< 2 MB）影響可忽略不計。 |
| **此方法是否與語言無關？** | 相同概念也存在於 .NET、Java 與 Node.js API（`LoadOptions.RecoveryMode`）。程式語法會不同，但邏輯完全相同。 |

## 專業提示：記錄詳細的復原資訊

Aspose.Words 提供 `LoadOptions.recovery_callback`，可接收每個復原步驟的詳細訊息。將其掛勾後，有助於診斷特定文件失敗的原因。

```python
def recovery_logger(message):
    print("[Recovery] ", message)

load_options.recovery_callback = recovery_logger
```

現在每個內部修正（例如「Removed duplicate relationship」）都會印出到主控台。

## 完整、可執行範例

將所有片段組合在一起，以下是一個可直接複製貼上並立即執行的獨立腳本：

```python
import aspose.words as aw

def enable_recovery_and_load(doc_path: str, save_repaired: bool = False):
    # Create load options and enable recovery mode
    load_options = aw.loading.LoadOptions()
    load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER

    # Optional: attach a simple logger
    load_options.recovery_callback = lambda msg: print("[Recovery] ", msg)

    # Load the document with recovery enabled
    doc = aw.Document(doc_path, load_options)

    # Verify the mode
    print("Document loaded with recovery mode:", load_options.recovery_mode)

    # Show basic info
    print("Page count:", doc.page_count)
    print("Word count:", doc.get_text().split())

    # Optionally save a repaired copy
    if save_repaired:
        repaired_path = doc_path.replace(".docx", "_repaired.docx")
        doc.save(repaired_path)
        print(f"Repaired document saved to {repaired_path}")

    return doc

if __name__ == "__main__":
    corrupted_path = "YOUR_DIRECTORY/Corrupted.docx"
    enable_recovery_and_load(corrupted_path, save_repaired=True)
```

執行腳本會印出復原模式、頁數，以及從修復後文件中抽取的單字列表。若將 `save_repaired=True`，則會在原始檔旁產生一個全新的乾淨檔案。

## 結論

您現在已了解如何在 Aspose.Words for Python 中**啟用復原模式**，並可靠地**修復損毀的 Word 文件**。關鍵步驟如下：

1. 建立 `LoadOptions` 並將 `recovery_mode` 設為 `RECOVER`。  
2. 使用上述選項載入 `.docx`。  
3. 驗證模式，必要時儲存修復副本。

接下來，您可以探索如**從修復文件抽取文字**、**轉換為 PDF**，或**為大型文件庫自動化批次復原**等進階主題。

---


## 接下來您應該學習什麼？

以下教學涵蓋與本指南技術緊密相關的主題，並提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索替代實作方式。

- [修復損毀的 DOCX – 完整指南：啟用復原模式與取得頁數](/words/english/python-net/document-operations/recover-corrupted-docx-complete-guide-to-enable-recovery-mod/)
- [修復損毀的 DOCX – 開啟與載入 Word 文件](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)
- [使用 Aspose.Words 修復受損的 docx – 設定復原模式與載入選項](/words/english/net/programming-with-loadoptions/recover-damaged-docx-with-aspose-words-set-recovery-mode-and/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}