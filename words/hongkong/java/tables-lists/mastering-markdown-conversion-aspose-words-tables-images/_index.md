---
"date": "2025-03-28"
"description": "了解如何使用 Aspose.Words for Java 將 Word 文件轉換為結構良好的 Markdown，並專注於表格和圖片。"
"title": "使用 Aspose.Words 掌握 Markdown 轉換錶格和圖片指南"
"url": "/zh-hant/java/tables-lists/mastering-markdown-conversion-aspose-words-tables-images/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# 使用 Aspose.Words 掌握 Markdown 轉換：表格和圖片指南
## 介紹
難以將複雜的 Word 文件轉換為乾淨、結構良好的 Markdown 文件？無論是對齊表格內容還是在轉換過程中重新命名影像，正確的工具都可以發揮重要作用。本指南將協助您使用 **Aspose.Words for Java** 實現無縫 Markdown 轉換。您將了解：
- 在 Markdown 中對齊表格內容
- Markdown 轉換期間高效率地重命名影像
- 指定映像資料夾和別名
- 將底線格式和表格匯出為 HTML
從 Word 過渡到 Markdown 並不一定很麻煩 - 讓我們來探索 Aspose.Words Java 如何簡化這個過程。
## 先決條件
在深入實施之前，請確保您已配備必要的工具：
- **Aspose.Words for Java**：這個強大的庫有助於文件處理和轉換。
- **Java 開發工具包 (JDK)**：建議使用 8 或更高版本。
- **整合開發環境**：任何整合開發環境，如 IntelliJ IDEA 或 Eclipse。
您還應該對 Java 程式設計有基本的了解，包括透過 Maven 或 Gradle 處理依賴項。
## 設定 Aspose.Words
要開始使用 Aspose.Words for Java，請將其包含在您的專案中。方法如下：
### Maven 依賴
將以下相依性新增至您的 `pom.xml` 文件：
```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```
### Gradle 依賴
或者，將其包含在您的 `build.gradle` 文件：
```gradle
implementation 'com.aspose:aspose-words:25.3'
```
### 許可證獲取
若要解鎖 Aspose.Words 的全部功能，請考慮取得授權。您可以開始免費試用或申請臨時許可證來無限制地測試功能。
## 實施指南
讓我們分解每個功能並引導您完成實施過程：
### 在 Markdown 中對齊表格內容
對齊表格內容可確保您的資料以 Markdown 格式整齊地呈現。以下是使用 Aspose.Words 實現此目的的方法：
#### 概述
此功能可讓您在將文件轉換為 Markdown 時指定表格內容的對齊設定。
```java
import com.aspose.words.*;

DocumentBuilder builder = new DocumentBuilder();
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT); // 設定所需的對齊方式

builder.getDocument().save("AlignedTableContents.md", saveOptions);
```
**解釋**： 
- `DocumentBuilder` 用於建立和操作文件。
- `setAlignment()` 設定每個單元格的段落對齊方式。
- `setTableContentAlignment()` 指定表格內容在 Markdown 中的對齊方式。
### Markdown 轉換期間重新命名影像
在轉換過程中自訂影像檔案名稱有助於有效地組織資源：
#### 概述
此功能可讓您動態地重新命名映像，使轉換後的檔案管理更加容易。
```java
import com.aspose.words.*;
import java.text.MessageFormat;
import org.apache.commons.io.FilenameUtils;

class ImageRenameFeature implements IImageSavingCallback {
    private int mCount = 0;
    private String mOutFileName;

    public ImageRenameFeature(String outFileName) {
        this.mOutFileName = outFileName;
    }

    @Override
    public void imageSaving(ImageSavingArgs args) throws Exception {
        String imageFileName = MessageFormat.format("{0} shape {1}, of type {2}.{3}",
                mOutFileName, ++mCount, args.getCurrentShape().getShapeType(), FilenameUtils.getExtension(args.getImageFileName()));
        args.setImageFileName(imageFileName);
        args.setKeepImageStreamOpen(false);
    }
}

Document doc = new Document("YOUR_DOCUMENT_PATH");
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImageSavingCallback(new ImageRenameFeature("CustomImages"));
doc.save("RenamedImages.md", saveOptions);
```
**解釋**： 
- 實施 `IImageSavingCallback` 自訂圖像檔案名稱。
- 使用 `MessageFormat` 和 `FilenameUtils` 用於結構化命名。
### 在 Markdown 中指定映像資料夾和別名
透過在轉換期間指定專用資料夾和別名來組織映像：
#### 概述
此功能可確保所有影像都保存在具有適當 URI 別名的指定目錄中。
```java
import com.aspose.words.*;
import java.nio.file.Paths;

DocumentBuilder builder = new DocumentBuilder();
builder.writeln("Some image below:");
builder.insertImage("YOUR_IMAGE_PATH" + "Logo.jpg");

String imagesFolder = Paths.get("YOUR_DOCUMENT_DIRECTORY", "ImagesDir").toString();
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder(imagesFolder);
saveOptions.setImagesFolderAlias("http://example.com/images”);

builder.getDocument().save("ImageFolderSpecified.md", saveOptions);
```
**解釋**： 
- `setImagesFolder()` 指定影像的儲存位置。
- `setImagesFolderAlias()` 分配一個 URI 來引用圖像資料夾。
### 在 Markdown 匯出底線格式
透過匯出下劃線格式來保留視覺強調：
#### 概述
此功能將 Word 文件下劃線轉換為 Markdown 友善的語法。
```java
import com.aspose.words.*;

Document doc = new Document();
doc.getRange().getFont().setUnderline(Underline.SINGLE);
doc.getFirstSection().getBody().appendParagraph("Lorem ipsum. Dolor sit amet.");

MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setExportUnderlineFormatting(true);

doc.save("UnderlineFormatted.md", saveOptions);
```
**解釋**： 
- `setUnderline()` 應用下劃線格式。
- `setExportUnderlineFormatting()` 確保下劃線被翻譯成 Markdown 語法。
### 在 Markdown 中將表格匯出為 HTML
透過將複雜的表格結構匯出為原始 HTML 來維護它們：
#### 概述
此功能允許將表格直接匯出為 HTML，並保留其原始結構。
```java
import com.aspose.words.*;

Document doc = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(doc);
documentBuilder.writeln("Sample table:");
documentBuilder.insertCell();
documentBuilder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
documentBuilder.write("Cell1");
documentBuilder.insertCell();
documentBuilder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
documentBuilder.write("Cell2");

MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setExportAsHtml(MarkdownExportAsHtml.TABLES);

doc.save("TableAsHtml.md", saveOptions);
```
**解釋**： 
- 使用 `setExportAsHtml()` 將 Markdown 文件中的表格匯出為 HTML。
## 實際應用
這些特性可以應用於各種場景：
1. **文件轉換**：將技術手冊轉換為使用者友善的 Markdown。
2. **網頁內容創作**：使用結構化資料和圖像為部落格或網站產生內容。
3. **合作項目**：使用 Git 等版本控制系統在團隊之間共用文件。
## 性能考慮
為確保最佳性能：
- **管理記憶體使用情況**：在轉換過程中使用適當的緩衝區大小並有效地管理資源。
- **優化檔案 I/O**：透過批次保存影像或匯出表格來最大限度地減少磁碟操作。
- **利用多執行緒**：如果適用，對大型文件使用並發處理。
## 結論
透過掌握 Aspose.Words for Java 的這些功能，您可以精確、輕鬆地將 Word 文件轉換為 Markdown。無論是對齊表格、重新命名圖像還是匯出格式，本指南都會為您提供高效文件轉換所需的技能。

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}