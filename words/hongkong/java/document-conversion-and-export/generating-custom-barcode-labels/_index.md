---
date: 2025-12-10
description: 學習如何使用 Aspose.Words for Java 產生自訂條碼標籤。本分步指南將示範如何在 Word 文件中嵌入條碼。
linktitle: Generating Custom Barcode Labels
second_title: Aspose.Words Java Document Processing API
title: 在 Aspose.Words for Java 中生成自訂條碼標籤
url: /zh-hant/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中產生自訂條碼標籤

## 在 Aspose.Words for Java 中產生自訂條碼的簡介

條碼在現代應用程式中扮演重要角色——無論是管理庫存、列印票券，或是製作身分證。於本教學中，您將 **產生自訂條碼** 標籤，並直接將其嵌入 Word 文件，使用 `IBarcodeGenerator` 介面。我們會一步步說明，從環境設定到插入條碼影像，讓您立即在 Java 專案中使用條碼。

## 快速答覆
- **本教學教什麼？** 如何產生自訂條碼標籤，並以 Aspose.Words for Java 嵌入 Word 檔案。  
- **範例使用哪種條碼類型？** QR Code（您可自行替換為任何支援的類型）。  
- **需要授權嗎？** 開發期間需使用臨時授權，以取得完整功能。  
- **需要哪個 Java 版本？** JDK 8 或以上。  
- **可以調整條碼尺寸或顏色嗎？** 可以——只要修改 `BarcodeParameters` 與 `BarcodeGenerator` 的設定即可。

## 前置需求

在開始編寫程式碼前，請確保您已具備以下項目：

- Java Development Kit (JDK)：版本 8 或以上。  
- Aspose.Words for Java 程式庫： [下載此處](https://releases.aspose.com/words/java/)。  
- Aspose.BarCode for Java 程式庫： [下載此處](https://releases.aspose.com/)。  
- 整合開發環境 (IDE)：IntelliJ IDEA、Eclipse，或您慣用的任何 IDE。  
- 臨時授權：取得 [臨時授權](https://purchase.aspose.com/temporary-license/) 以獲得完整存取權限。

## 匯入套件

我們將使用 Aspose.Words 與 Aspose.BarCode 程式庫。請在專案中匯入以下套件：

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

上述匯入讓我們能存取條碼產生 API 以及 Word 文件相關類別。

## 步驟 1：建立條碼操作的工具類別

為了讓主要程式碼保持簡潔，我們會將常用的輔助方法——例如 **將 twips 轉換為像素** 以及 **十六進位顏色轉換**——封裝在一個工具類別中。

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
- `convertColor` – 將十六進位字串（例如 `"FF0000"` 代表紅色）轉換為 `java.awt.Color` 物件，讓您 **插入條碼** 時可自訂前景與背景顏色。

## 步驟 2：實作自訂條碼產生器

接下來，我們實作 `IBarcodeGenerator` 介面。此類別負責產生 **Java 風格的 QR Code** 影像，供 Aspose.Words 直接嵌入。

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

- `getBarcodeImage` 會建立 `BarcodeGenerator` 實例，套用 `BarcodeParameters` 所提供的顏色，最後回傳 `BufferedImage`。  
- 若發生例外，方法會回傳佔位圖，確保 Word 文件的產生不會因錯誤而中斷。

## 步驟 3：產生條碼並 **在 Word 中嵌入條碼**

完成產生器後，我們即可產生條碼影像，並 **插入至 Word 文件**。

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

1. **文件初始化** – 建立全新的 `Document`（或載入既有範本）。  
2. **條碼參數** – 定義條碼類型（`QR`）、要編碼的值，以及前景/背景顏色。  
3. **影像插入** – `builder.insertImage` 於指定大小（200 × 200 像素）插入產生的條碼，這就是 **在 Word 檔案中插入條碼** 的核心。  
4. **儲存** – 最終文件 `CustomBarcodeLabels.docx` 已包含嵌入的條碼，可直接列印或分發。

## 為何使用 Aspose.Words 產生自訂條碼標籤？

- **完整控制** 條碼外觀（類型、尺寸、顏色）。  
- **無縫整合** —— 不需中間影像檔案，條碼於記憶體中產生後直接插入。  
- **跨平台** —— 只要支援 Java 的作業系統皆可執行，適合伺服器端文件產生。  
- **可擴充** —— 可遍歷資料來源，一次產生數百張個人化標籤。

## 常見問題與除錯

| 症狀 | 可能原因 | 解決方式 |
|------|----------|----------|
| 條碼顯示空白 | `BarcodeParameters` 的前景色與背景色相同（例如黑色在黑色上） | 檢查 `foregroundColor` 與 `backgroundColor` 的值。 |
| 影像變形 | 傳入 `insertImage` 的像素尺寸不正確 | 調整寬度/高度參數，或使用 `twipsToPixels` 進行精確換算。 |
| 不支援的條碼類型錯誤 | 使用了 `CustomBarcodeGeneratorUtils.getBarcodeEncodeType` 未辨識的類型 | 確認條碼類型字串符合支援的 `EncodeTypes`（例如 `"QR"`、`"CODE128"`）。 |

## 常見問答

**Q: 可以在沒有授權的情況下使用 Aspose.Words for Java 嗎？**  
A: 可以，但會有功能限制。取得 [臨時授權](https://purchase.aspose.com/temporary-license/) 可獲得完整功能。

**Q: 我可以產生哪些類型的條碼？**  
A: Aspose.BarCode 支援 QR、Code 128、EAN‑13 等多種格式。請參考 [文件說明](https://reference.aspose.com/words/java/) 取得完整清單。

**Q: 要如何調整條碼尺寸？**  
A: 調整 `builder.insertImage` 的寬度與高度參數，或使用 `twipsToPixels` 將 Word 單位轉為像素。

**Q: 能否為條碼文字使用自訂字型？**  
A: 可以，透過 `BarcodeGenerator` 的 `CodeTextParameters` 屬性自訂文字字型。

**Q: 若遇到問題，該向哪裡尋求協助？**  
A: 前往 [支援論壇](https://forum.aspose.com/c/words/8/) 向 Aspose 社群與工程師求助。

## 結論

依照上述步驟，您已掌握如何 **產生自訂條碼** 影像，並 **在 Word 中嵌入條碼**，使用 Aspose.Words for Java。此技巧彈性十足，適用於庫存標籤、活動票券，或任何需要將條碼納入自動產生文件的情境。可自行嘗試不同條碼類型與樣式，以符合您的業務需求。

---

**最後更新：** 2025-12-10  
**測試環境：** Aspose.Words for Java 24.12、Aspose.BarCode for Java 24.12  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}