---
category: general
date: 2026-09-30
description: 啟用恢復模式以使用 Aspose.Words 開啟損毀的 Word 文件。了解如何安全可靠地復原損毀的 docx 檔案。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- enable recovery mode
- open corrupted word document
- recover corrupted docx
- how to open corrupted docx
- load document with recovery
language: zh-hant
lastmod: 2026-09-30
og_description: 啟用復原模式以使用 Aspose.Words 開啟損壞的 Word 文件。本指南逐步說明如何修復損壞的 docx 檔案，並保持工作流程穩定。
og_image_alt: Code snippet showing Aspose.Words recovery mode enabled for a corrupted
  DOCX
og_title: 啟用復原模式以開啟損毀的 Word 檔案
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Enable recovery mode to open a corrupted Word document using Aspose.Words.
    Learn how to recover corrupted docx files safely and reliably.
  headline: Enable recovery mode to open a corrupted Word document
  type: TechArticle
tags:
- Aspose.Words
- Python
- Document recovery
title: 啟用復原模式以開啟損毀的 Word 文件
url: /zh-hant/python/document-options-and-settings/enable-recovery-mode-to-open-a-corrupted-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 啟用復原模式以開啟受損的 Word 文件

如果您需要在開啟受損的 Word 文件時 **啟用復原模式**，本教學將示範如何使用 Aspose.Words for Python 來完成。無論檔案是在傳輸過程中受損，或是被不相容的程式編輯，啟用復原模式都能讓函式庫嘗試修復文件，而不是直接拋出例外。

在本指南中，您將學會如何 **開啟受損的 word document** 檔案、**復原受損的 docx** 內容，並了解控制 **load document with recovery** 流程的選項。以下步驟適用於 Aspose.Words 23.10（撰寫時的最新版本），且僅需一般的 Python 環境。

## 前置條件

開始之前，請確保您已具備：

* 已安裝 Python 3.9 或更新版本。
* 已安裝 Aspose.Words for Python via .NET（`aspose-words`），可透過 `pip install aspose-words` 安裝。
* 一個已知受損的 DOCX 檔案（測試時可將有效的 `.docx` 重新命名為 `.zip`，再手動破壞其中的 XML）。

> **專業提示：** 請保留原始檔案的備份。復原模式只會在記憶體中修改文件，除非您明確呼叫儲存，否則不會寫回來源檔案。

## 步驟 1：匯入函式庫並建立載入選項

首先必須匯入 `aspose.words`，並實例化 `LoadOptions` 物件。此物件保存所有影響檔案讀取方式的設定。

```python
import aspose.words as aw

# Create load options – this is where we will enable recovery mode
load_options = aw.loading.LoadOptions()
```

*為什麼這很重要：* `LoadOptions` 是微調解析器的入口。若不使用它，Aspose.Words 會採用預設的嚴格模式，遇到任何結構錯誤就會中止。

## 步驟 2：啟用復原模式

將 `recovery_mode` 屬性設為 `RecoveryMode.RECOVER`。這會告訴載入器嘗試自動修復缺少的 XML 節點、斷裂的關聯或被截斷的串流等問題。

```python
# Enable recovery mode – the core of “enable recovery mode” for this tutorial
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER
```

啟用復原模式 **不保證** 完全恢復文件，但能大幅提升仍能擷取文字、圖片或表格的機會。

## 步驟 3：使用已設定的選項載入可能受損的 DOCX

接著使用接受檔案路徑與 `LoadOptions` 實例的 `Document` 建構子。

```python
# Path to the corrupted file – replace with your actual location
corrupted_path = "YOUR_DIRECTORY/corrupted.docx"

try:
    # Load the document using the recovery‑enabled options
    document = aw.Document(corrupted_path, load_options)
    print("Document loaded successfully with recovery mode.")
except aw.core.exceptions.InvalidOperationException as ex:
    # If recovery fails, the library throws an exception
    print(f"Failed to load document even with recovery mode: {ex}")
```

*為什麼這很重要：* `try/except` 區塊示範了 **如何安全地開啟受損的 docx**。若未啟用復原模式，同樣的呼叫會立即拋出例外，導致程式中斷。

## 步驟 4：驗證復原後的內容（可選但建議執行）

載入完成後，應檢查文件是否包含有意義的內容。快速的方法是擷取純文字並印出前幾個字元。

```python
# Extract plain text to verify recovery
text = document.get_text()
if text.strip():
    print("Recovered text preview (first 200 chars):")
    print(text[:200])
else:
    print("Document appears empty after recovery – further inspection may be needed.")
```

如果輸出顯示合理的預覽，您即可繼續處理文件（例如轉成 PDF、擷取表格等）。若文字為空，表示檔案可能已無法修復，需重新取得新檔。

## 步驟 5：儲存修復後的文件（如需乾淨的副本）

當您對復原的內容滿意時，可以將其另存為全新的、乾淨的 DOCX。此步驟為可選，但在後續工作流程中常很有用。

```python
repaired_path = "YOUR_DIRECTORY/repaired.docx"
document.save(repaired_path)
print(f"Repaired document saved to {repaired_path}")
```

儲存會產生一個不再包含觸發復原模式之損壞的全新檔案。

## 邊緣情況與額外提示

| 情境                                   | 推薦做法 |
|----------------------------------------|----------|
| **檔案不是 DOCX**（例如 `.doc`）      | 在載入前使用 `aw.loading.LoadOptions.file_format = aw.LoadFormat.DOC`。 |
| **僅部分復原**                         | 載入後檢查 `document.get_text()` 與 `document.get_page_count()`。若頁數為 0，表示文件可能無法復原。 |
| **大型文件**                           | 設定 `load_options.memory_optimization = aw.loading.MemoryOptimizationMode.OPTIMIZE` 以降低復原時的記憶體使用。 |
| **需要記錄修復內容**                   | 設定 `load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER`，然後讀取 `document.get_last_save_options().recovery_log`（若有提供）以取得詳細資訊。 |

> **注意：** 復原模式可能會靜默移除不支援的元素（例如缺少的字型）。若視覺相似度非常重要，請將修復後的檔案與已知良好的版本進行比對。

## 完整範例程式

將上述所有步驟整合在一起，以下是一個可直接執行的自包含腳本：

```python
import aspose.words as aw

def open_corrupted_docx(path: str, output_path: str = None):
    """Load a corrupted DOCX with recovery mode and optionally save a repaired copy."""
    # 1. Configure load options
    load_options = aw.loading.LoadOptions()
    load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER

    # 2. Attempt to load the document
    try:
        doc = aw.Document(path, load_options)
        print("✅ Document loaded with recovery mode.")
    except aw.core.exceptions.InvalidOperationException as err:
        print(f"❌ Unable to recover document: {err}")
        return None

    # 3. Verify recovered content
    txt = doc.get_text()
    if txt.strip():
        print("📄 Text preview (first 200 chars):")
        print(txt[:200])
    else:
        print("⚠️ Document appears empty after recovery.")

    # 4. Save a clean copy if requested
    if output_path:
        doc.save(output_path)
        print(f"💾 Repaired file saved to {output_path}")

    return doc

if __name__ == "__main__":
    corrupted_file = "YOUR_DIRECTORY/corrupted.docx"
    repaired_file = "YOUR_DIRECTORY/repaired.docx"
    open_corrupted_docx(corrupted_file, repaired_file)
```

執行此腳本會印出成功訊息、簡短的文字摘錄，並在同一資料夾產生 `repaired.docx`。

## 結論

您現在已掌握如何 **啟用復原模式** 以 **開啟受損的 word document** 檔案、**復原受損的 docx** 內容，並安全地 **load document with recovery**，全部透過 Aspose.Words for Python。建立 `LoadOptions`、開啟 `RecoveryMode.RECOVER`、以及例外處理的主要步驟，構成一個可靠的模式，可在任何自動化流程中重複使用。

接下來，您可以探索以下相關主題，例如 **將復原的文件轉成 PDF**、**使用 `DocumentVisitor` 擷取表格**，或 **批次處理資料夾內的受損檔案**。所有這些都建立在本教學示範的復原模式基礎上。

祝程式開發順利，願您的文件永遠健康！

## 接下來該學什麼？

以下教學與本指南的技術緊密相關，提供完整的程式碼範例與逐步說明，協助您深入掌握更多 API 功能，並在專案中探索替代實作方式。

- [如何復原 docx – 設定復原模式並開啟受損的 Word 檔案](/words/english/net/programming-with-loadoptions/how-to-recover-docx-set-recovery-mode-open-corrupted-word-fi/)
- [使用 Aspose.Words 復原受損的 docx – 設定復原模式與載入選項](/words/english/net/programming-with-loadoptions/recover-damaged-docx-with-aspose-words-set-recovery-mode-and/)
- [使用 Aspose.Words LoadOptions 復原受損 DOCX – 完整 C# 指南](/words/english/net/programming-with-loadoptions/recover-corrupted-docx-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}