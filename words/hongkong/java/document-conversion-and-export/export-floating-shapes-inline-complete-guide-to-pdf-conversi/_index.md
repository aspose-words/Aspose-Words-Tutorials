---
category: general
date: 2026-07-03
description: 在將 Word 轉換為 PDF 時，將浮動圖形匯出為行內。了解如何在 Java 中設定 PDF 選項以及將 Word 儲存為 PDF 的選項。
draft: false
keywords:
- export floating shapes inline
- convert word to pdf inline
- how to set pdf options
- save word as pdf options
language: zh-hant
og_description: 在將 Word 文件轉換為 PDF 時，將浮動圖形匯出為內嵌。此教學示範如何設定 PDF 選項以及將 Word 儲存為 PDF 的選項。
og_title: 匯出內嵌浮動形狀 – Java PDF 轉換指南
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  headline: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  type: TechArticle
- description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  name: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  steps:
  - name: 1. “What if my document contains complex SmartArt?”
    text: SmartArt is treated as a drawing object. The inline flag works for most
      vector shapes, but very intricate SmartArt may still be rendered as an image.
      In those cases, consider flattening the SmartArt in Word before conversion,
      or use `pdfOptions.setExportSmartArtAsImage(true)` to force image export.
  - name: 2. “Can I combine inline and block exports in the same document?”
    text: Unfortunately the API applies the setting globally. If you need mixed behavior,
      split the document into sections, export each section separately with different
      options, then merge the PDFs using `PdfMerger`.
  - name: 3. “Does this affect font embedding?”
    text: No. Font embedding is controlled by `pdfOptions.setEmbedFullFonts(true)`
      (default). You can safely enable or disable it without touching the inline shape
      flag.
  - name: 4. “How do I verify that shapes are really `<span>`?”
    text: Open the resulting PDF in a tool like **PDF.js** or **Adobe Acrobat** →
      **Edit PDF** → **Object Inspector**. You’ll see the shape wrapped in a `<span>`
      element in the underlying XML. If you see `<div>`, the option wasn’t applied.
  type: HowTo
tags:
- Java
- PDF
- Aspose.Words
title: 匯出浮動形狀內嵌 – PDF 轉換完整指南
url: /zh-hant/java/document-conversion-and-export/export-floating-shapes-inline-complete-guide-to-pdf-conversi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 匯出浮動圖形為內聯 – PDF 轉換完整指南

在將 Word 文件轉換為 PDF 時，是否曾需要 **export floating shapes inline**？你並不孤單——許多開發者都會遇到圖表或圖示神祕地移到獨立圖層的問題。好消息是，只要設定一個 PDF 選項，就能讓這些圖形緊貼在 `<span>` 標籤內，完整保留在 Word 中看到的版面配置。

在本教學中，我們將逐步說明如何在 Java 中 **how to set PDF options**，展示 **save Word as PDF options** 的完整程式碼，並解釋為何你可能想要 **convert Word to PDF inline**，而非預設的區塊層級匯出。完成後，你將擁有一段可直接放入任何 Maven 或 Gradle 專案的即用程式碼片段。

## 你將學習

- inline `<span>` 與 block `<div>` 匯出浮動圖形的差異。  
- `PdfSaveOptions` 的設定方式，以強制內聯渲染。  
- 逐步程式碼示範：載入 `.docx`、套用選項，並輸出 PDF。  
- 常見陷阱（缺少字型、不支援的圖形）以及避免方法。  
- 測試輸出結果的技巧，及將此方法擴展至其他文件元素。

**Prerequisites** – 需要 Java 8 或更新版本、Aspose.Words for Java 函式庫（或任何具備相同 `PdfSaveOptions` 類別的 API），以及一個包含浮動圖形的範例 Word 檔（本教學使用 `FloatingShapes.docx`）。不需要其他外部工具。

---

## 第一步：載入來源 Word 文件

首先要做的事是開啟要轉換的 `.docx`。這很簡單，但請確保路徑是絕對路徑或能正確從 classpath 解析。

```java
import com.aspose.words.Document;

// Step 1: Load the source Word document
Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");
```

*為什麼這很重要:*  
如果文件未正確載入，隨後的 PDF 轉換會拋出 `FileNotFoundException`。使用 `Document` 可確保內部物件模型完整填充，包括頁面上所有的浮動圖形。

## 第二步：建立 PDF 儲存選項並將浮動圖形設定為內聯

這就是魔法發生的地方。預設情況下，Aspose.Words 會將浮動圖形匯出為區塊層級的 `<div>` 元素，這會破壞基於 HTML 的 PDF 流程。設定 `setExportFloatingShapesAsInlineTag(true)` 可指示引擎將每個圖形包裹在內聯的 `<span>` 中。

```java
import com.aspose.words.PdfSaveOptions;

// Step 2: Create PDF save options and set floating shapes to be exported as inline <span> elements
PdfSaveOptions pdfOptions = new PdfSaveOptions();
pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → <span>, false → <div>
```

*為什麼這很重要:*  
- **版面忠實度** – 內聯標籤可讓圖形與周圍文字對齊，避免產生不必要的空白。  
- **可搜尋性** – 內聯元素較容易被 PDF 閱讀器正確索引。  
- **樣式控制** – 若日後將 PDF 轉回 HTML，可使用 CSS 針對 `<span>` 進行樣式設定。

> **小技巧:** 如果你需要對特定文件使用舊的區塊行為，只需傳入 `false` 或直接省略此呼叫。

## 第三步：使用設定好的選項將文件儲存為 PDF

現在將已載入的 `Document` 與 `PdfSaveOptions` 結合，並寫出檔案。這一行程式碼完成了大部分工作。

```java
// Step 3: Save the document as a PDF using the configured options
doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);
```

*為什麼這很重要:*  
`save` 方法會遵循在 `pdfOptions` 上設定的所有旗標。若忘記傳入這些選項，將會回復為預設的區塊匯出，失去 **export floating shapes inline** 的目的。

## 完整範例程式

將上述步驟整合起來，以下是一個可直接編譯執行的精簡程式。請將 `YOUR_DIRECTORY` 替換為你機器上的實際路徑。

```java
import com.aspose.words.*;

public class ExportFloatingShapesInlineDemo {
    public static void main(String[] args) {
        try {
            // Load the source Word document
            Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");

            // Configure PDF options to export floating shapes as inline <span>
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true);

            // Save as PDF with the above options
            doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);

            System.out.println("PDF created successfully with inline floating shapes.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Expected output** – 執行程式後，開啟 `FloatingShapes.pdf`。你應該會看到圖形與文字緊密相貼，沒有額外的空白，且若檢視 PDF 內部結構，其 HTML 表示將在每個圖形周圍包含 `<span>` 標籤。

![匯出浮動圖形為內聯範例](https://example.com/export-inline.png "顯示浮動圖形在 PDF 中內聯渲染的螢幕截圖")

*圖片替代文字:* **export floating shapes inline** PDF 內含內聯圖形的螢幕截圖。

## 常見問題與邊緣情況

### 1. 「如果我的文件包含複雜的 SmartArt 會怎樣？」

SmartArt 會被視為繪圖物件。內聯旗標對大多數向量圖形有效，但非常複雜的 SmartArt 仍可能被渲染為影像。此時可考慮在 Word 中先將 SmartArt 展平，或使用 `pdfOptions.setExportSmartArtAsImage(true)` 強制以影像匯出。

### 2. 「我可以在同一文件中同時使用內聯與區塊匯出嗎？」

遺憾的是，API 會全域套用此設定。若需要混合行為，請將文件切分為多個章節，分別以不同選項匯出，然後使用 `PdfMerger` 合併 PDF。

### 3. 「這會影響字型嵌入嗎？」

不會。字型嵌入由 `pdfOptions.setEmbedFullFonts(true)`（預設）控制。你可以安全地開啟或關閉它，而不會影響內聯圖形的設定。

### 4. 「我要如何驗證圖形真的被包在 `<span>` 中？」

在 **PDF.js** 或 **Adobe Acrobat** → **編輯 PDF** → **物件檢查器** 等工具中開啟產生的 PDF。你會在底層 XML 中看到圖形被 `<span>` 元素包裹。若看到 `<div>`，表示選項未生效。

## 擴充此方法 – 相關選項

既然已經在此，也許你想探索其他 PDF 轉換的設定：

| 選項 | 功能說明 | 典型使用情境 |
|--------|--------------|------------------|
| `setCompressImages(true)` | Reduces image size | Faster downloads |
| `setUseHighQualityRendering(true)` | Improves vector rendering | Print‑ready PDFs |
| `setExportDocumentStructure(true)` | Adds structural tags for accessibility | WCAG compliance |
| `setSaveFormat(SaveFormat.PDF)` | Explicitly sets format (rarely needed) | Multi‑format pipelines |

這些設定與 **convert word to pdf inline** 情境相得益彰，當你同時需要版面忠實度與效能時。

## 測試你的轉換

1. **視覺檢查** – 在兩個檢視器（Chrome 與 Adobe Reader）中開啟 PDF，確認圖形對齊。  
2. **自動化比對** – 使用如 `pdfbox` 的函式庫抽取 XML，並斷言 `<span>` 標籤的存在。  
3. **效能基準測試** – 測量有無 `setCompressImages` 時所需的時間，以觀察取捨。

A quick JUnit example:

```java
@Test
public void testInlineExport() throws Exception {
    Document doc = new Document("src/test/resources/FloatingShapes.docx");
    PdfSaveOptions opts = new PdfSaveOptions();
    opts.setExportFloatingShapesAsInlineTag(true);
    ByteArrayOutputStream out = new ByteArrayOutputStream();
    doc.save(out, opts);
    String pdfXml = new String(out.toByteArray(), StandardCharsets.UTF_8);
    assertTrue(pdfXml.contains("<span"));
}
```

## 結論

現在你已擁有一套完整、端對端的解決方案，可在 **export floating shapes inline** 時 **convert Word to PDF inline**。透過設定 `PdfSaveOptions`，你可以控制每個圖形使用的 HTML 標籤，讓 PDF 整潔且易於搜尋。請記得測試輸出結果，調整如影像壓縮等相關選項，並處理如複雜 SmartArt 等邊緣情況。

準備好下一步了嗎？試著將相同技巧應用於 **export floating tables inline**，或使用 Aspose 的 `HtmlSaveOptions` 進行 CSS 樣式的 PDF 實驗。相同的模式——載入、設定、儲存——適用於幾乎所有文件轉 PDF 的情境。

對 **how to set pdf options** 有更多疑問，或需要協助處理其他函式庫的 **save word as pdf options**？歡迎留言，祝開發愉快！

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，並在此基礎上延伸。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助你精通更多 API 功能，並在專案中探索其他實作方式。

- [使用 Aspose.Words for Java 將 Word 轉換為 PDF](/words/english/java/document-converting/)
- [使用 Aspose.Words for Java 將文件儲存為 PDF](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [匯出 Word 文件結構至 PDF 文件](/words/english/net/programming-with-pdfsaveoptions/export-document-structure/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}