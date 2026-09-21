---
category: general
date: 2026-01-11
description: 學習在將 DOCX 檔案轉換為 Markdown 時嵌入圖片，對小圖使用 Base64，較大的資源則另行儲存。
draft: false
keywords:
- how to embed images
- convert docx to markdown
- how to convert docx
- embed images as base64
- export word document markdown
language: zh-hant
og_description: 學習如何在將 DOCX 檔案轉換為 Markdown 時嵌入圖片，對於小圖片使用 Base64，較大的資源則另行儲存。
og_title: 將 DOCX 轉換為 Markdown 時如何嵌入圖片
tags:
- Aspose.Words
- Java
- Markdown
- Image Embedding
title: 將 DOCX 轉換為 Markdown 時如何嵌入圖片
url: /zh-hant/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在將 DOCX 轉換為 Markdown 時嵌入圖片

是否曾好奇 **如何嵌入圖片** 到來源於 Word 文件的 Markdown 檔案中？你並不孤單。大多數開發者在轉換過程中會遇到圖片遺失或以破壞最終版面配置的方式儲存的問題。  

在本指南中，我們將示範一個完整、可直接執行的範例，說明 **如何嵌入圖片** 為 Base64 data URI（適用於小圖），同時將較大的資源寫入旁邊的資料夾。過程中我們也會涵蓋 **convert docx to markdown**、探討使用 Aspose.Words **how to convert docx** 的方式，並說明將圖片以 Base64 嵌入與匯出為獨立檔案之間的差異。  

> **小技巧：** 若只需要快速的概念驗證，以下程式碼在加入單一 Maven 依賴後即可直接使用。

---

## 您需要的環境

- **Java 17**（或任何近期的 JDK）– API 以 Java 為主，但概念可套用至其他語言。  
- **Aspose.Words for Java** – 商業套件，支援 DOCX → Markdown 轉換。  
- 一個包含小圖示與較大照片的 **sample DOCX**。  
- 用來存放 Markdown 及其資源的資料夾。  

不需要額外框架或外部腳本。只要純 Java 加上 Aspose.Words 即可。

---

## 第一步 – 將 Aspose.Words 加入專案 (convert docx to markdown)

如果使用 Maven，請將以下片段放入 `pom.xml` 中。可自行將版本號換成當前最新版本。

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for newer versions -->
</dependency>
```

> **為什麼這很重要：** Aspose.Words 負責解析 DOCX 結構、擷取圖片以及產生 Markdown 語法的繁重工作。自行開發解析器會讓你陷入不必要的泥沼。

---

## 第二步 – 載入來源 DOCX 文件

首先，將 API 指向欲轉換的 Word 檔案。`Document` 建構子會完成所有工作——不需要手動解析 XML。

```java
import com.aspose.words.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Step 2: Load the source DOCX document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

請注意註解說明了 *為何* 這行程式碼關鍵：若沒有 `Document` 實例，就無法執行轉換。

---

## 第三步 – 使用 Resource‑Saving Callback 建立 MarkdownSaveOptions

這是正確 **如何嵌入圖片** 的核心。回呼讓你在每個資源（圖片、樣式等）寫入時取得介入點。

```java
        // Step 3: Create Markdown save options and define a resource‑saving callback
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
        saveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            public void resourceSaving(ResourceSavingArgs args) {
                // Step 4: Decide how to handle each image
                if (args.getResourceType() == ResourceType.IMAGE && args.getData().length < 10_000) {
                    // Small image – embed as Base64
                    String base64 = java.util.Base64.getEncoder()
                            .encodeToString(args.getData());
                    args.setUri("data:image/png;base64," + base64);
                    args.setKeepResourceStreamOpen(false);
                } else {
                    // Larger image – write to a folder
                    Path outPath = Paths.get("markdown_resources", args.getFileName());
                    try {
                        Files.createDirectories(outPath.getParent());
                        Files.write(outPath, args.getData());
                        // Normalize path for Markdown (use forward slashes)
                        args.setUri(outPath.toString().replace('\\', '/'));
                    } catch (Exception e) {
                        throw new RuntimeException(e);
                    }
                }
            }
        });
```

### 為什麼需要回呼？

- **Control:** 你可以決定圖片是以內嵌 Base64 字串形式還是另存為檔案。  
- **Performance:** 小圖示直接嵌入 Markdown，減少額外的 HTTP 請求。  
- **Portability:** 較大的圖片保留為外部檔案，讓 Markdown 檔案大小保持合理。

---

## 第四步 – 將文件儲存為 Markdown

最後，使用剛才設定好的選項，指示 Aspose.Words 輸出 Markdown 檔案。

```java
        // Step 5: Save the document as Markdown using the configured options
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

執行程式後會產生兩樣東西：

1. `output.md` – 原始 DOCX 的 Markdown 表示。  
2. `markdown_resources` 資料夾，內含所有未內嵌的較大圖片。

---

## 完整範例（一步到位）

以下是完整的來源檔案，可直接複製貼上至 IDE。將 `YOUR_DIRECTORY` 替換為實際路徑。

```java
import com.aspose.words.*;
import java.nio.file.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the source DOCX document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Create Markdown save options and define a resource‑saving callback
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
        saveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            public void resourceSaving(ResourceSavingArgs args) {
                // Small images (<10 KB) become Base64 data URIs
                if (args.getResourceType() == ResourceType.IMAGE && args.getData().length < 10_000) {
                    String base64 = java.util.Base64.getEncoder()
                            .encodeToString(args.getData());
                    args.setUri("data:image/png;base64," + base64);
                    args.setKeepResourceStreamOpen(false);
                } else {
                    // Larger images are written to a dedicated folder
                    Path outPath = Paths.get("markdown_resources", args.getFileName());
                    try {
                        Files.createDirectories(outPath.getParent());
                        Files.write(outPath, args.getData());
                        args.setUri(outPath.toString().replace('\\', '/'));
                    } catch (Exception e) {
                        throw new RuntimeException(e);
                    }
                }
            }
        });

        // Step 3: Save the document as Markdown
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

**預期輸出：** 在任意 Markdown 檢視器開啟 `output.md`。小圖示會內嵌顯示，例如：

```markdown
![Embedded Icon](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
```

較大的圖片則會以以下方式引用：

```markdown
![Photo](markdown_resources/photo1.jpg)
```

這正是你在 **嵌入圖片** 時，同時保持檔案大小可控的最佳做法。

---

## 常見問題與特殊情況

### 若圖片是 JPEG 而非 PNG 該怎麼辦？

上述回呼始終以 `image/png` 為 URI 前綴。若遇 JPEG，可檢查 `args.getData()` 的前幾個位元組，或使用 `args.getFileName()` 推斷正確的 MIME 類型：

```java
String mime = args.getFileName().toLowerCase().endsWith(".jpg") ||
              args.getFileName().toLowerCase().endsWith(".jpeg")
              ? "image/jpeg" : "image/png";
args.setUri("data:" + mime + ";base64," + base64);
```

### 可以調整大小門檻嗎？

當然可以。`10_000` 位元組的限制僅為示範。若頻寬充足，可提升至 50 KB 或更高；若需極輕量的 Markdown，則可降低門檻。

### 這樣能處理表格或其他 Word 物件嗎？

可以。Aspose.Words 會自動將表格、清單、甚至註腳轉換為 Markdown。資源回呼只攔截圖片，其他元素不需額外程式碼。

### 非 ASCII 檔名會有問題嗎？

API 在寫入 `markdown_resources` 資料夾時會安全地編碼 Unicode 檔名。只要你的檔案系統支援 UTF‑8（大多數現代作業系統皆支援），就不會有問題。

---

## 平順轉換的實用小技巧

- **保持輸出資料夾整潔。** 每次轉換只呼叫一次 `Files.createDirectories`，或在每次執行前刪除該資料夾以獲得全新環境。  
- **驗證 Markdown。** 使用 `markdownlint` 等工具可捕捉因 Base64 字串格式錯誤而產生的雜訊字元。  
- **鎖定 Aspose.Words 版本。** 指定特定版本可確保程式碼在未來的重大更新中仍能正常運作。  
- **使用 .gitignore** 來排除 `markdown_resources/`  

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}