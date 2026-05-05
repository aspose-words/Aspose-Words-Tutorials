---
category: general
date: 2026-05-04
description: 如何設定從 Word 匯出為 Markdown 的解析度。了解 Markdown 圖片解析度、如何匯出方程式，以及在 Java 中將 Word
  儲存為 Markdown。
draft: false
keywords:
- how to set resolution
- markdown image resolution
- how to use markdown
- how to export equations
- save word as markdown
language: zh-hant
og_description: 如何設定從 Word 匯出 Markdown 的解析度。本指南說明 Markdown 圖片解析度、匯出方程式，以及將 Word 儲存為
  Markdown。
og_title: 將 Word 另存為 Markdown 時如何設定解析度
tags:
- Aspose.Words
- Java
- Markdown
- Document Export
title: 將 Word 另存為 Markdown 時如何設定解析度
url: /zh-hant/java/document-conversion-and-export/how-to-set-resolution-when-saving-word-as-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在將 Word 儲存為 Markdown 時設定解析度

有沒有想過 **如何設定解析度** 於從 Word 文件產生的 Markdown 檔案中出現的圖片？你並非唯一有此疑問的人。許多開發者在預設的點陣化數學圖片在高 DPI 螢幕上看起來模糊時，常會卡關。  

在本教學中，我們將逐步說明如何控制 *markdown image resolution*，同時示範 **如何將方程式匯出** 為 LaTeX，最後說明如何使用 Aspose.Words for Java **將 Word 儲存為 markdown**。完成後，你將擁有一個清晰、可投入生產環境的 Markdown 檔案，方程式渲染乾淨，圖片品質符合需求。

## 前置條件

- Java 17（或任何較新的 JDK）  
- Aspose.Words for Java 23.6 或更新版本 – 可從 Maven Central 取得  
- 一個包含 OfficeMath 物件（方程式）且可能有點陣圖的 Word 文件（`.docx`）  
- 具備 Maven/Gradle 與 IDE（IntelliJ IDEA、Eclipse、VS Code 等）的基本使用經驗

不需要額外的函式庫；其餘皆由 Aspose.Words 處理。

---

## 如何設定 Markdown 匯出的解析度

> **小技巧：** 你選擇的解析度會直接影響產生圖片的檔案大小。**300 dpi** 的數值對大多數基於網頁的 Markdown 檢視器而言是個不錯的平衡。

```java
// Step 1: Load the source Word document containing equations
Document doc = new Document("YOUR_DIRECTORY/Math.docx");

// Step 2: Create Markdown save options to control the export behavior
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();

// Step 3: Export OfficeMath objects as LaTeX expressions
saveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

// Step 4 (optional): Set image resolution for any rasterized Math images
saveOptions.setImageResolution(300);   // <-- this is where we set the resolution

// Step 5: Save the document as a Markdown file using the configured options
doc.save("YOUR_DIRECTORY/MathExport.md", saveOptions);
```

`setImageResolution(int dpi)` 呼叫是 **如何設定解析度** 的核心。它告訴 Aspose.Words 以指定的每英吋點數 (dpi) 來點陣化任何備援圖片（例如，當方程式無法以純 LaTeX 表示時）。若省略此行，函式庫會退回使用預設的 220 dpi，於 Retina 螢幕上可能顯得模糊。

### 為什麼要使用 LaTeX 來表示方程式？

當你以 LaTeX（`OfficeMathExportMode.LATEX`）匯出方程式時，產生的 Markdown 會包含以 `$…$` 或 `$$…$$` 包裹的原始 LaTeX 程式碼。大多數現代的 Markdown 渲染器（GitHub、GitLab、搭配 MathJax 的 MkDocs）會將其渲染為清晰、可縮放的向量圖形——不會有解析度的問題。解析度設定僅在 **markdown image resolution** 針對任何點陣備援圖片（例如嵌入的圖表或 Markdown 原生不支援的圖片）時才會生效。

---

## 如何有效使用 Markdown 圖片解析度

如果需要在 Word 檔案中嵌入一般圖片（例如螢幕截圖），它們會被 Aspose.Words 轉換為 PNG。相同的 `setImageResolution` 方法會套用，確保這些 PNG 繼承你指定的 DPI。以下是一個快速檢查清單：

1. **選擇符合目標平台的 DPI** – 72 dpi 用於舊版網頁、150 dpi 用於一般顯示器、300 dpi 用於列印品質的 PDF。  
2. **測試輸出** – 在你喜愛的檢視器中開啟產生的 `.md` 檔案，放大以驗證清晰度。  
3. **考量檔案大小** – 較高的 DPI 會產生較大的 PNG；若擔心頻寬，可嘗試 200 dpi 並比較。

---

## 如何將方程式匯出為 LaTeX

`saveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);` 這行指示 Aspose.Words 將每個 OfficeMath 物件轉換為 LaTeX。這是建議的做法，原因如下：

- **可伸縮性** – LaTeX 可在任何尺寸下渲染而不失真。  
- **可編輯性** – 之後可直接在 Markdown 檔案中調整 LaTeX。  
- **相容性** – 大多數靜態網站產生器與文件工具已支援 LaTeX 渲染。  

若你仍需要舊有的基於圖片的備援，只需切換為 `OfficeMathExportMode.IMAGE`。此時，你設定的解析度就更加重要。

---

## 將 Word 儲存為 Markdown – 完整端對端範例

以下是一段完整且可執行的 Maven 專案程式碼片段，示範從相依性宣告到執行的整個流程。

```xml
<!-- pom.xml -->
<project xmlns="http://maven.apache.org/POM/4.0.0" ...>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>markdown-export</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.6</version>
        </dependency>
    </dependencies>
</project>
```

```java
// src/main/java/com/example/MarkdownMathExport.java
package com.example;

import com.aspose.words.*;

public class MarkdownMathExport {
    public static void main(String[] args) throws Exception {
        // Load the source Word document containing equations and images
        Document doc = new Document("src/main/resources/Math.docx");

        // Configure Markdown export options
        MarkdownSaveOptions options = new MarkdownSaveOptions();
        options.setOfficeMathExportMode(OfficeMathExportMode.LATEX); // export equations as LaTeX
        options.setImageResolution(300); // set resolution for rasterized images

        // Save as Markdown
        doc.save("output/MathExport.md", options);

        System.out.println("✅ Markdown export complete! Check output/MathExport.md");
    }
}
```

**預期結果：** `MathExport.md` 會包含每個方程式的 LaTeX 區塊，且所有嵌入的圖片會以 DPI 為 300 的 PNG 連結出現。於支援 MathJax 的 Markdown 檢視器（例如安裝 Markdown Preview Enhanced 擴充功能的 VS Code）開啟此檔案，即可看到方程式與圖片皆相當銳利。

---

## 常見問題與邊緣情況

### 如果只想為單一圖片設定不同的 DPI 該怎麼辦？

Aspose.Words 會透過 `setImageResolution` 全域套用 DPI。若要針對單張圖片設定不同 DPI，需在產生的 Markdown 後處理：將 PNG 檔替換為較高解析度的版本，並手動調整圖片連結。雖非理想方案，但對少數特殊情況仍可行。

### 這在 Linux/macOS 上能運作嗎？

絕對可以。此函式庫純粹使用 Java，因此只要 JDK 可執行的環境皆可運作。只需確保檔案路徑使用正斜線或 `Paths.get(...)` 以達到跨平台相容性。

### 那 SVG 輸出呢？

若偏好使用向量圖作為圖表，可設定 `saveOptions.setExportImagesAsSvg(true);`。SVG 不受 DPI 影響，因而 **markdown image resolution** 的問題不復存在。然而，並非所有 Markdown 渲染器都能順利處理 SVG，請先於目標平台測試。

### 我可以將產生的 Markdown 嵌入靜態網站產生器嗎？

可以。輸出為純 `.md` 檔，使用標準 Markdown 語法加上 LaTeX 分隔符。大多數產生器（Jekyll、Hugo、MkDocs）皆可直接使用。只需在站點設定中啟用 MathJax 或 KaTeX 即可。

---

## 結論

我們已說明在 **將 Word 儲存為 markdown** 時 **如何設定解析度**，探討 **markdown image resolution** 的細節，示範 **如何將方程式匯出** 為 LaTeX，並展示完整的 Java 實作。透過調整 `setImageResolution` 並選擇適當的 `OfficeMathExportMode`，即可精確掌控視覺品質與檔案大小。

準備好進一步了嗎？可嘗試將此方法與 Aspose.PDF 結合，直接將相同的 Word 原始檔轉為 PDF，或實驗 `setExportImagesAsSvg(true)` 以取得向量圖形。此處學到的技巧是任何自動化文件流程的基礎組件。

如果你覺得本指南有幫助，請在 GitHub 上給予星標，與同事分享，或在下方留言分享你的技巧。祝開發愉快！  

![設定解析度範例](resolution.png "將 Word 儲存為 Markdown 時的解析度設定")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}