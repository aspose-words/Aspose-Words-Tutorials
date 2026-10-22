---
category: general
date: 2026-09-21
description: 使用 Aspose.Words for Python 將 docx 另存為 txt。將 Word 轉換為純文字，並在三個簡單步驟中將公式匯出為
  LaTeX。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx as txt
- convert word to plain text
- how to convert docx to txt
- save document as plain text
- export equations to latex
language: zh-hant
lastmod: 2026-09-21
og_description: 使用 Aspose.Words for Python 將 docx 另存為 txt。只需幾行程式碼，即可將 Word 轉換為純文字，並將方程式匯出為
  LaTeX。
og_image_alt: Screenshot showing save docx as txt code snippet in Python
og_title: 使用 Aspose.Words for Python 將 docx 另存為 txt – 快速指南
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Save docx as txt using Aspose.Words for Python. Convert Word to plain
    text and export equations to LaTeX in three simple steps.
  headline: How to save docx as txt with Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- document conversion
- plain text
- LaTeX
title: 如何使用 Aspose.Words for Python 將 docx 另存為 txt
url: /zh-hant/python/document-conversion/how-to-save-docx-as-txt-with-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words for Python 將 docx 儲存為 txt

如果您需要 **將 docx 儲存為 txt**，本指南將示範如何使用 Aspose.Words for Python 完成。按照以下步驟即可輕鬆將 Word 轉換為純文字，同時保留公式。

您將學會如何 **將 word 轉換為純文字**、設定 Office Math 物件的匯出模式，並驗證產生的檔案是否包含公式的 LaTeX 標記。此教學假設您具備基本的 Python 知識，且使用 Python 近期版本（3.8 以上）。

## 安裝 Aspose.Words for Python

在撰寫任何程式碼之前，先從 PyPI 安裝 Aspose.Words 套件。

```bash
pip install aspose-words
```

此函式庫提供本教學中使用的 `aw` 命名空間。安裝只需執行一次；之後的所有轉換皆可使用同一套件。

## 準備來源文件

將您要轉換的 DOCX 檔案放置於已知目錄中。使用絕對路徑可避免腳本在不同工作目錄執行時產生混淆。

```python
import aspose.words as aw
import os

# Define input and output paths
input_path = os.path.abspath("YOUR_DIRECTORY/input.docx")
output_path = os.path.abspath("YOUR_DIRECTORY/output.txt")
```

`aw.Document` 類別會讀取 DOCX 檔案，並建立可在記憶體中操作的表示，您可以進一步處理或儲存為其他格式。

## 設定 TXT 儲存選項

若要 **將 docx 儲存為 txt**，必須建立 `TxtSaveOptions` 物件。此物件允許您控制 Office Math 物件的呈現方式。

```python
# Step 1: Load the source document
doc = aw.Document(input_path)

# Step 2: Create TXT save options and specify how Office Math objects should be exported
txt_opts = aw.saving.TxtSaveOptions()
txt_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
```

將 `office_math_export_mode` 設為 `LATEX` 可確保所有公式以 LaTeX 程式碼寫入，而非純 Unicode 符號。這滿足 **export equations to latex** 的需求。

## 將文件儲存為純文字

現在您可以使用先前設定的選項，將文件寫入純文字檔案。

```python
# Step 3: Save the document as a plain‑text file using the configured options
doc.save(output_path, txt_opts)
print(f"Document saved as plain text at: {output_path}")
```

呼叫 `doc.save` 即可在單行程式碼中完成轉換，達成 **save document as plain text** 的目標。

## 驗證輸出結果

使用任意文字編輯器開啟產生的 `output.txt` 檔案。您應該會看到一般段落，且每個公式後皆有 LaTeX 片段，例如：

```
This is a sample paragraph.

\[
\int_{a}^{b} f(x)\,dx = F(b) - F(a)
\]

Another paragraph without equations.
```

若檔案中包含 LaTeX 標記，則 **export equations to latex** 步驟已正確執行。

## 邊緣情況與實用技巧

* **缺少字型** – Aspose.Words 會以預設字型取代缺失的字型。純文字輸出不受影響，但渲染公式的視覺忠實度可能會改變。請確保來源文件使用標準字型，或在可能的情況下嵌入字型。
* **大型文件** – 若檔案超過 100 MB，建議使用 `aw.loading.LoadOptions` 以串流方式讀取，降低記憶體使用量。
* **非 ASCII 字元** – `TxtSaveOptions` 類別預設使用 UTF‑8 編碼，可保留 Unicode 字元。若需其他編碼，可設定 `txt_opts.encoding = aw.saving.Encoding.ASCII`（大多數語言不建議使用）。
* **路徑處理** – 請始終使用 `os.path.abspath` 或 `pathlib.Path`，避免相對路徑帶來的意外，尤其在腳本作為排程任務執行時。

## 完整腳本，快速複製貼上

以下為完整且可執行的範例，涵蓋上述所有步驟。

```python
import aspose.words as aw
import os

def save_docx_as_txt(input_docx: str, output_txt: str) -> None:
    """
    Converts a DOCX file to plain text and exports any Office Math objects as LaTeX.
    """
    # Load the source document
    doc = aw.Document(input_docx)

    # Configure TXT save options
    txt_opts = aw.saving.TxtSaveOptions()
    txt_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX

    # Save as plain‑text file
    doc.save(output_txt, txt_opts)

if __name__ == "__main__":
    # Adjust these paths for your environment
    input_path = os.path.abspath("YOUR_DIRECTORY/input.docx")
    output_path = os.path.abspath("YOUR_DIRECTORY/output.txt")

    # Ensure the output directory exists
    os.makedirs(os.path.dirname(output_path), exist_ok=True)

    save_docx_as_txt(input_path, output_path)
    print(f"Document saved as plain text at: {output_path}")
```

執行此腳本會產生一個 `.txt` 檔案，內含原始文件的文字以及所有公式的 LaTeX 表示，達成 **how to convert docx to txt** 目標。

![Screenshot of save docx as txt code snippet in Python](placeholder-image.png){: .img-fluid alt="顯示在 Python 中將 docx 儲存為 txt 程式碼片段的螢幕截圖"}

## 結論

現在您已了解如何使用 Aspose.Words for Python **將 docx 儲存為 txt**、如何 **將 word 轉換為純文字**，以及在需要時 **將公式匯出為 latex**。完整範例示範了在保留數學內容的前提下，將 Word 文件轉換為純文字檔的建議做法。

接下來，您可以透過調整儲存選項類別，探索其他匯出格式，如 HTML 或 PDF。亦可嘗試為純文字輸出設定自訂分隔符，或將此轉換整合至更大的文件處理流程中。

祝開發順利！

## 接下來您應該學習什麼？

以下教學涵蓋與本指南密切相關的主題，並在此基礎上延伸技術。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在自己的專案中探索替代實作方式。

- [Aspose.Words – 將 docx 儲存為 txt 並將 Word 公式匯出為 LaTeX – 完整指南](/words/english/net/basic-conversions/save-docx-as-txt-complete-guide-to-export-word-equations-as/)
- [將 docx 儲存為 txt – 使用 Aspose.Words 匯出公式為 LaTeX](/words/english/net/programming-with-officemath/save-docx-as-txt-export-equations-to-latex-with-aspose-words/)
- [將 docx 轉換為 txt – 匯出 Word 公式為 LaTeX](/words/english/java/document-conversion-and-export/convert-docx-to-txt-export-word-equations-as-latex/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}