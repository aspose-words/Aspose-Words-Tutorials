---
date: 2026-10-23
description: 了解如何使用 Aspose.Words 建立 QR code Java 標籤。本分步指南將示範如何在 Word 文件中嵌入 barcode，並自訂尺寸、顏色和格式。
keywords:
- create qr code java
- how to create barcode label
- add barcode to word document
- embed barcode in word
lastmod: 2026-10-23
linktitle: 產生自訂 Barcode 標籤
og_description: 了解如何使用 Aspose.Words 建立 QR code Java 標籤。本指南說明在 Word 文件中嵌入 barcode、尺寸控制與顏色自訂。
og_image_alt: 'Developer guide: generate custom QR code labels in Java with Aspose.Words'
og_title: 如何使用 Aspose.Words 建立 QR code Java 標籤
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to create QR code Java labels with Aspose.Words. This step‑by‑step
    guide shows you how to embed barcodes in Word documents and customize size, colors,
    and format.
  headline: How to create QR code Java labels using Aspose.Words
  type: TechArticle
- description: Learn how to create QR code Java labels with Aspose.Words. This step‑by‑step
    guide shows you how to embed barcodes in Word documents and customize size, colors,
    and format.
  name: How to create QR code Java labels using Aspose.Words
  steps:
  - name: '**Document initialization** – Creates a fresh `Document` (or you could
      load an existing template).'
    text: '**Document initialization** – Creates a fresh `Document` (or you could
      load an existing template).'
  - name: '**Barcode parameters** – Defines the barcode type (`QR`), the value to
      encode, and the foreground/background colors.'
    text: '**Barcode parameters** – Defines the barcode type (`QR`), the value to
      encode, and the foreground/background colors.'
  - name: '**Image insertion** – `builder.insertImage` places the generated barcode
      at the desired size (200 × 200 pixels). This is the core of **how to embed barcode
      in Word**.'
    text: '**Image insertion** – `builder.insertImage` places the generated barcode
      at the desired size (200 × 200 pixels). This is the core of **how to embed barcode
      in Word**.'
  - name: '**Saving** – The final document, `CustomBarcodeLabels.docx`, contains the
      embedded barcode ready for printing or distribution.'
    text: '**Saving** – The final document, `CustomBarcodeLabels.docx`, contains the
      embedded barcode ready for printing or distribution.'
  type: HowTo
- questions:
  - answer: Yes, but it will have evaluation limitations. Obtain a [temporary license](https://purchase.aspose.com/temporary-license/)
      for full functionality.
    question: Can I use Aspose.Words for Java without a license?
  - answer: Aspose.BarCode supports QR, Code 128, EAN‑13, DataMatrix, PDF417, and
      many other formats—over 20 symbologies in total. See the [documentation](https://reference.aspose.com/words/java/)
      for the complete list.
    question: What types of barcodes can I generate?
  - answer: Adjust the width and height arguments in `builder.insertImage`, or calculate
      exact Word twips using `twipsToPixels` for pixel‑perfect control.
    question: How can I change the barcode size?
  - answer: Yes, you can customize the text font through the `CodeTextParameters`
      property of the `BarcodeGenerator`.
    question: Is it possible to use custom fonts for the barcode text?
  - answer: Visit the [support forum](https://forum.aspose.com/c/words/8/) for assistance
      from the Aspose community and engineers.
    question: Where can I get help if I run into problems?
  type: FAQPage
second_title: Aspose.Words Java Document Processing API
tags:
- barcode generation
- Aspose.Words
- Java document processing
- QR code
title: 如何使用 Aspose.Words 建立 QR code Java 標籤
url: /zh-hant/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words 建立 QR code Java 標籤

條碼在現代應用程式中至關重要——無論是管理庫存、列印票券，或是製作身分證。於本教學中，您將**建立 QR code Java** 標籤，並使用 `IBarcodeGenerator` 介面直接嵌入 Word 文件。我們會一步步說明，從環境設定到插入條碼影像，讓您立即在 Java 專案中使用條碼。

## 快速解答
- **此教學教什麼？** 如何使用 Aspose.Words for Java 建立 QR code Java 標籤並嵌入 Word 檔案。  
- **範例使用哪種條碼類型？** QR code（您可以替換為 20 多種支援的類型之一）。  
- **需要授權嗎？** 開發期間需要臨時授權以取得無限制存取。  
- **需要哪個 Java 版本？** JDK 8 或以上。  
- **可以變更條碼尺寸或顏色嗎？** 可以——修改 `BarcodeParameters` 與 `BarcodeGenerator` 設定。

## 什麼是 create QR code Java？
`create QR code Java` 指在 Java 環境中以程式方式產生 QR‑code 影像，並將其插入文件或 UI 元件。Aspose.Words for Java 搭配 Aspose.BarCode 可在記憶體中完整產生影像，避免產生暫存檔。

## 為何使用 Aspose.Words 產生自訂條碼標籤？
Aspose.Words 支援 **35+ 種輸入與輸出格式**，且能在標準伺服器硬體上於 **3 秒內處理 500 頁文件**。使用其記憶體內條碼產生功能，您可完整掌控類型、尺寸與顏色，同時保持工作流程完全以 Java 為中心且平台無關。

## 前置條件

- Java 開發工具包 (JDK)：版本 8 或以上。  
- Aspose.Words for Java Library: [Download here](https://releases.aspose.com/words/java/)。  
- Aspose.BarCode for Java Library: [Download here](https://releases.aspose.com/)。  
- 整合開發環境 (IDE)：IntelliJ IDEA、Eclipse，或任何您偏好的 IDE。  
- 臨時授權：取得 [temporary license](https://purchase.aspose.com/temporary-license/) 以取得無限制存取。

## 匯入套件

我們將使用 Aspose.Words 與 Aspose.BarCode 套件。請在專案中匯入以下套件：

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

這些匯入讓我們取得條碼產生 API 以及所需的 Word 文件類別。

## 步驟 1：建立條碼操作的工具類別

此工具類別包含可重複使用的輔助方法，例如 **convert twips to pixels** 與 **hex‑color conversion**。  
`CustomBarcodeGeneratorUtils` 類別提供靜態方法，用於單位換算與顏色處理。

### 程式碼

```java
class CustomBarcodeGeneratorUtils {
    public static double twipsToPixels(String heightInTwips, double defVal) {
        try {
            int lVal = Integer.parseInt(heightInTwips);
            return (lVal / 1440.0) * 96.0; // Assuming default DPI is 96
        } catch (Exception e) {
            return defVal;
        }
    }

    public static Color convertColor(String inputColor, Color defVal) {
        if (inputColor == null || inputColor.isEmpty()) return defVal;
        try {
            int color = Integer.parseInt(inputColor, 16);
            return new Color((color & 0xFF), ((color >> 8) & 0xFF), ((color >> 16) & 0xFF));
        } catch (Exception e) {
            return defVal;
        }
    }
}
```

**說明**  
- `twipsToPixels` – Word 以 **twips** 為單位測量尺寸；此方法將其轉換為螢幕像素，方便精確設定條碼影像大小。  
- `convertColor` – 將十六進位字串（例如 `"FF0000"` 代表紅色）轉換為 `java.awt.Color` 物件，讓您能以自訂前景與背景顏色 **將條碼加入 Word 文件**。

## 步驟 2：實作自訂條碼產生器

現在我們將實作 `IBarcodeGenerator` 介面。此類別負責 **generate QR code Java** 風格的影像，供 Aspose.Words 嵌入。  
`IBarcodeGenerator` 介面定義一個回傳 `BufferedImage`（條碼影像）的單一方法。

### 程式碼

```java
class CustomBarcodeGenerator implements IBarcodeGenerator {
    public BufferedImage getBarcodeImage(BarcodeParameters parameters) {
        try {
            BarcodeGenerator gen = new BarcodeGenerator(
                CustomBarcodeGeneratorUtils.getBarcodeEncodeType(parameters.getBarcodeType()),
                parameters.getBarcodeValue()
            );

            gen.getParameters().getBarcode().setBarColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getForegroundColor(), Color.BLACK)
            );
            gen.getParameters().setBackColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getBackgroundColor(), Color.WHITE)
            );

            return gen.generateBarCodeImage();
        } catch (Exception e) {
            return new BufferedImage(100, 100, BufferedImage.TYPE_INT_ARGB);
        }
    }

    public BufferedImage getOldBarcodeImage(BarcodeParameters parameters) {
        throw new UnsupportedOperationException();
    }
}
```

**說明**  
- `getBarcodeImage` 建立 `BarcodeGenerator` 實例，套用由 `BarcodeParameters` 提供的顏色，最後回傳 `BufferedImage`。  
- 此方法亦會妥善處理錯誤，回傳佔位圖，確保 Word 文件建立時不會當機。

## 如何使用 Aspose.Words 在 Word 中嵌入條碼？

使用 `new Document("template.docx")` 載入 Word 檔（或建立新的 `Document`），然後以產生器回傳的條碼影像呼叫 `builder.insertImage`。此兩步驟模式直接嵌入條碼，無需寫入中介檔案至磁碟。透過以像素指定影像尺寸或將 Word twips 轉換為像素，您可精確控制條碼在文件中的大小與位置，確保版面專業且在任何印表機上均能正確列印。

## 步驟 3：產生條碼並在 Word 中嵌入條碼

生成器就緒後，我們即可產生條碼影像，並 **將其插入 Word 文件**。

### 程式碼

```java
import com.aspose.words.*;

public class GenerateCustomBarcodeLabels {
    public static void main(String[] args) throws Exception {
        // Load or create a Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Set up custom barcode generator
        CustomBarcodeGenerator barcodeGenerator = new CustomBarcodeGenerator();
        BarcodeParameters barcodeParameters = new BarcodeParameters();
        barcodeParameters.setBarcodeType("QR");
        barcodeParameters.setBarcodeValue("https://example.com");
        barcodeParameters.setForegroundColor("000000");
        barcodeParameters.setBackgroundColor("FFFFFF");

        // Generate barcode image
        BufferedImage barcodeImage = barcodeGenerator.getBarcodeImage(barcodeParameters);

        // Insert barcode image into Word document
        builder.insertImage(barcodeImage, 200, 200);

        // Save the document
        doc.save("CustomBarcodeLabels.docx");

        System.out.println("Barcode labels generated successfully!");
    }
}
```

**說明**  

1. **文件初始化** – 建立全新的 `Document`（或載入現有範本）。  
2. **條碼參數** – 定義條碼類型（`QR`）、要編碼的值，以及前景/背景顏色。  
3. **影像插入** – `builder.insertImage` 將產生的條碼放置於指定尺寸（200 × 200 像素）。這即是 **how to embed barcode in Word** 的核心。  
4. **儲存** – 最終文件 `CustomBarcodeLabels.docx` 包含已嵌入的條碼，可直接列印或分發。

## 常見問題與故障排除

| 症狀 | 可能原因 | 解決方式 |
|---------|--------------|-----|
| 條碼顯示空白 | `BarcodeParameters` 顏色相同（例如黑底黑字） | 確認 `foregroundColor` 與 `backgroundColor` 的值。 |
| 影像變形 | 傳遞給 `insertImage` 的像素尺寸不正確 | 調整寬度/高度參數，或使用 `twipsToPixels` 轉換以取得精確尺寸。 |
| 不支援的條碼類型錯誤 | 使用了 `CustomBarcodeGeneratorUtils.getBarcodeEncodeType` 未識別的類型 | 確保條碼類型字串符合支援的 `EncodeTypes`（例如 `"QR"`、`"CODE128"`）。 |

## 常見問答

**Q: 我可以在沒有授權的情況下使用 Aspose.Words for Java 嗎？**  
A: 可以，但會有評估限制。取得 [temporary license](https://purchase.aspose.com/temporary-license/) 以獲得完整功能。

**Q: 我可以產生哪些類型的條碼？**  
A: Aspose.BarCode 支援 QR、Code 128、EAN‑13、DataMatrix、PDF417 等多種格式——總計超過 20 種符號。請參閱 [documentation](https://reference.aspose.com/words/java/) 取得完整清單。

**Q: 我該如何變更條碼尺寸？**  
A: 調整 `builder.insertImage` 的寬度與高度參數，或使用 `twipsToPixels` 計算精確的 Word twips，以達到像素級控制。

**Q: 能否為條碼文字使用自訂字型？**  
A: 可以，您可透過 `BarcodeGenerator` 的 `CodeTextParameters` 屬性自訂文字字型。

**Q: 若遇到問題，我該向何處尋求協助？**  
A: 前往 [support forum](https://forum.aspose.com/c/words/8/) 取得 Aspose 社群與工程師的協助。

## 結論

依照上述步驟，您現在已掌握如何使用 Aspose.Words for Java **建立 QR code Java** 影像，並 **將條碼嵌入 Word** 文件。此技術彈性高，可應用於庫存標籤、活動票券或任何需要在產生文件中加入條碼的情境。請嘗試不同的條碼類型、顏色與尺寸設定，以符合您的業務需求。

---

**最後更新：** 2026-10-23  
**測試環境：** Aspose.Words for Java 24.12, Aspose.BarCode for Java 24.12  
**作者：** Aspose

## 相關教學

- [從 Word 建立 PDF 並產生條碼 – Aspose.Words for Java](/words/java/document-conversion-and-export/using-barcode-generation/)
- [使用 Aspose Words 步驟式 Java 指南將 Word 儲存為 PDF](/words/java/document-conversion-and-export/save-word-as-pdf-with-aspose-words-step-by-step-java-guide/)
- [在 Java 中使用 Aspose Words 建立空白 Word 文件](/words/java/document-manipulation/create-blank-word-document-in-java-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}