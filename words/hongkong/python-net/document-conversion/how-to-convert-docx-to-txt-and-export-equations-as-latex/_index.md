---
category: general
date: 2026-11-15
description: 將 docx 轉換為 txt，同時保留方程式為 LaTeX。一步一步學習如何從 Word 提取文字，並使用 Aspose.Words for
  Python 將 Word 儲存為 txt。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- convert docx to txt
- extract text from word
- how to export equations
- export word equations latex
- save word as txt
language: zh-hant
lastmod: 2026-11-15
og_description: 即時將 docx 轉換為 txt。本教學示範如何從 Word 中提取文字、將方程式匯出為 LaTeX，並使用 Aspose.Words
  將 Word 儲存為 txt。
og_image_alt: Screenshot illustrating convert docx to txt workflow with LaTeX equation
  export
og_title: 將 docx 轉成 txt 並匯出 LaTeX 方程式 – Python 指南
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: convert docx to txt while preserving equations as LaTeX. Learn step‑by‑step
    how to extract text from Word and save Word as txt using Aspose.Words for Python.
  headline: How to convert docx to txt and export equations as LaTeX
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
title: 將 docx 轉換成 txt，並將方程式匯出為 LaTeX
url: /zh-hant/python/document-conversion/how-to-convert-docx-to-txt-and-export-equations-as-latex/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何將 docx 轉換為 txt 並將方程式匯出為 LaTeX

如果您需要 **將 docx 轉換為 txt** 並保留每個方程式的 LaTeX 格式，本指南將帶您完整步驟。您將學會如何 **從 Word 中提取文字**、設定儲存選項，最後 **將 Word 儲存為 txt**，並保有乾淨的 LaTeX 標記。

此解決方案適用於 Aspose.Words for Python via .NET，只需少量程式碼，且可在支援 Python 3.8+ 的任何平台上執行。無需額外的轉換工具。

## 前置條件

* 已安裝 Python 3.8 或更新版本。
* 有效的 Aspose.Words for Python via .NET 授權（或免費評估金鑰）。
* 已安裝 `aspose-words` 套件（`pip install aspose-words`）。
* 包含一般文字與 Office Math 方程式的 Word 文件（`.docx`）。

## 第一步：設定專案並匯入函式庫

建立一個新的 Python 檔案，例如 `convert_docx_to_txt.py`，並加入所需的匯入語句。

```python
import aspose.words as aw

# Optional: set your license if you have one
# aw.License().set_license("Aspose.Words.lic")
```

**此步驟的重要性：** 匯入 `aspose.words` 可讓您使用 `Document` 類別與 `TxtSaveOptions` 物件，這對於控制 DOCX 內容寫入純文字檔案至關重要。

## 第二步：載入 Word 文件

```python
# Load the source .docx file
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)
```

**此步驟的重要性：** `Document` 物件在記憶體中代表整個 Word 檔案。一次載入後即可重複使用該物件進行多次匯出操作，提升大型文件的效能。

## 第三步：設定 TXT 儲存選項以將方程式匯出為 LaTeX

```python
# Create TXT save options
txt_opts = aw.saving.TxtSaveOptions()

# Export Office Math equations using LaTeX syntax
txt_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX

# Optional: force UTF‑8 encoding to preserve special characters
txt_opts.encoding = "utf-8"
```

**此步驟的重要性：** 將 `office_math_export_mode` 設為 `LATEX` 後，所有方程式會轉換為 LaTeX 表示，而不會被移除或以純文字呈現。`encoding` 屬性確保 ASCII 範圍外的字元（例如希臘字母）能正確儲存。

## 第四步：將文件儲存為純文字檔案

```python
# Define the output path
output_path = "YOUR_DIRECTORY/output.txt"

# Save using the configured options
doc.save(output_path, txt_opts)
print(f"Document successfully converted and saved to {output_path}")
```

**此步驟的重要性：** `save` 方法會依照您設定的選項將文件寫入 `.txt` 檔案。最終得到的純文字檔案，普通段落與 Word 中相同，且每個方程式皆以 LaTeX 區塊顯示。

## 預期輸出

假設 `input.docx` 包含以下段落：

```
The quadratic formula is given by:
```

接著是方程式 *x = \frac{-b \pm \sqrt{b^2-4ac}}{2a}*。

執行腳本後，`output.txt` 會包含：

```
The quadratic formula is given by:
$x = \frac{-b \pm \sqrt{b^2-4ac}}{2a}$
```

所有其他文字區段會完整保留，與原始 DOCX 中的呈現相同。

## 第五步：處理例外情況與最佳實踐技巧

| 情況 | 建議處理方式 |
|-----------|----------------------|
| **沒有方程式的文件** | 腳本仍可正常執行；`office_math_export_mode` 會被忽略，您會得到純文字。 |
| **大型文件（ > 100 MB ）** | 將文件載入 `MemoryStream` 以避免過度記憶體使用，或在需要串流輸出時分批處理頁面。 |
| **自訂換行符號** | 設定 `txt_opts.add_bidi_marks = False` 以及 `txt_opts.save_format = aw.SaveFormat.TEXT` 以控制換行行為。 |
| **非 UTF‑8 目標系統** | 將 `txt_opts.encoding` 改為所需的代碼頁（例如 `"windows-1252"`）。 |
| **保留分頁符號** | 啟用 `txt_opts.save_format = aw.SaveFormat.TEXT` 並將 `txt_opts.export_page_breaks = True`。 |

**專業提示：** 若您打算將產生的 `.txt` 檔案交給 LaTeX 編譯器，請在編譯前將整個檔案包裹在最小的 LaTeX 文件標頭（`\documentclass{article} … \begin{document}`）中。

## 完整腳本，快速複製貼上

```python
import aspose.words as aw

def convert_docx_to_txt(
    input_path: str,
    output_path: str,
    encoding: str = "utf-8",
    export_equations_as_latex: bool = True,
) -> None:
    """
    Convert a DOCX file to a TXT file while optionally exporting equations as LaTeX.
    
    Parameters
    ----------
    input_path : str
        Path to the source .docx file.
    output_path : str
        Destination path for the generated .txt file.
    encoding : str, optional
        Text encoding for the output file. Default is UTF‑8.
    export_equations_as_latex : bool, optional
        When True, Office Math equations are written as LaTeX. When False, they are omitted.
    """
    # Load the document
    doc = aw.Document(input_path)

    # Configure save options
    txt_opts = aw.saving.TxtSaveOptions()
    txt_opts.encoding = encoding

    if export_equations_as_latex:
        txt_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
    else:
        txt_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.NONE

    # Save the TXT file
    doc.save(output_path, txt_opts)
    print(f"convert docx to txt completed: {output_path}")

# Example usage
if __name__ == "__main__":
    convert_docx_to_txt(
        input_path="YOUR_DIRECTORY/input.docx",
        output_path="YOUR_DIRECTORY/output.txt"
    )
```

執行腳本會印出確認訊息，並產生一個 **從 Word 提取文字** 的文字檔，同時保留所有方程式的 LaTeX 形式。

## 結論

現在您已了解如何使用 Aspose.Words for Python **將 docx 轉換為 txt**、**從 Word 提取文字**，以及 **匯出 Word 方程式為 LaTeX**。完整的解決方案說明了每項設定的意義、涵蓋常見例外情況，並提供可於未來專案重複使用的函式。

**下一步**

* 探索其他 `TxtSaveOptions` 旗標，例如 `preserve_table_layout`，若您需要保留表格結構。
* 將此轉換與批次處理器結合，以處理資料夾中的多個 DOCX 檔案。
* 若您需要 PDF 輸出而非 TXT，請將 `TxtSaveOptions` 換成 `PdfSaveOptions`，並保持相同的 LaTeX 匯出模式。

歡迎將腳本套用於您的工作流程，嘗試不同的編碼，並整合至更大的文件處理管線。祝開發愉快！

## 接下來您可以學習什麼？

以下教學涵蓋與本指南緊密相關的主題，並以步驟說明的完整程式碼範例，協助您精通更多 API 功能，並在自己的專案中探索其他實作方式。

- [convert docx to txt and export equations from Word as LaTeX – Complete Guide](/words/english/python-net/document-conversion/convert-docx-to-txt-and-export-equations-from-word-as-latex/)
- [save docx as txt – Export Word Math to LaTeX with Python](/words/english/python-net/document-conversion/save-docx-as-txt-export-word-math-to-latex-with-python/)
- [save docx as txt – Complete Guide to Export Word Equations](/words/english/python-net/document-conversion/save-docx-as-txt-complete-guide-to-export-word-equations/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}