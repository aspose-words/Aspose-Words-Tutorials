---
date: 2026-02-09
description: 使用 Aspose Barcode Java 在 Aspose.Words for Java 中生成自訂條碼標籤。了解如何在 Word 文件中嵌入條碼以及生成
  QR Code 的 Java 範例。
linktitle: Generating Custom Barcode Labels
second_title: Aspose.Words Java Document Processing API
title: 使用 Aspose Barcode Java 生成自訂條碼標籤
url: /zh-hant/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose Barcode Java 產生自訂條碼標籤

## 介紹 Aspose.Words for Java 中產生自訂條碼標籤

條碼在現代應用程式中扮演關鍵角色，而 **Aspose Barcode Java** 讓您可以直接在 Word 文件中輕鬆建立條碼。無論是 **在 Word 中嵌入條碼**、為 URL 產生 QR Code，或是轉換測量單位，本教學都會一步步帶您完成。準備好了嗎？讓我們開始吧！

## 快速答覆
- **哪個函式庫可以在 Java 中產生條碼？** Aspose Barcode Java 搭配 Aspose.Words for Java。  
- **示範使用哪種條碼類型？** QR Code（generate qr code java）。  
- **如何將 twips 轉換成像素？** 使用提供的 `twipsToPixels` 工具方法。  
- **可以將條碼加入現有的 Word 檔案嗎？** 可以，只要使用 `DocumentBuilder.insertImage` 方法。  
- **需要授權嗎？** 臨時授權可移除評估限制。

## 什麼是 Aspose Barcode Java？
Aspose Barcode Java 是一套功能強大的 API，讓開發者能以程式方式產生各式 1D 與 2D 條碼（含 QR Code）。結合 Aspose.Words for Java 後，您可以 **在 Word 中嵌入條碼**，且全程停留在 Java 環境中。

## 為什麼要將 Aspose Barcode Java 與 Aspose.Words 結合使用？
- **完整控制** 條碼外觀（顏色、尺寸、格式）。  
- **無縫整合** – 條碼影像可直接插入 Word 文件。  
- **跨平台** – 可在任何支援 Java 的平台上執行。  
- **可擴充** – 您可以建立公用的工具類別，於多個專案中重複使用條碼邏輯。

## 前置條件

在開始撰寫程式碼之前，請先確保您具備以下環境：

- Java Development Kit (JDK)：版本 8 以上。  
- Aspose.Words for Java 套件：[在此下載](https://releases.aspose.com/words/java/)。  
- Aspose.BarCode for Java 套件：[在此下載](https://releases.aspose.com/)。  
- 整合開發環境 (IDE)：IntelliJ IDEA、Eclipse 或您慣用的任何 IDE。  
- 臨時授權：取得 [臨時授權](https://purchase.aspose.com/temporary-license/) 以解除功能限制。

## 匯入套件

我們將使用 Aspose.Words 與 Aspose.BarCode 套件。請在專案中匯入以下套件：

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

這些匯入讓我們能使用條碼產生功能並將其整合至 Word 文件。

接下來，我們把任務拆解成可管理的步驟。

## 步驟 1：建立條碼操作的工具類別

為了簡化條碼相關的操作，我們會建立一個工具類別，內含顏色轉換與 **convert twips to pixels** 等常用方法。

### 程式碼：

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

- `twipsToPixels` 將 Word 使用的測量單位（twips）轉換為螢幕像素——在需要精確尺寸時非常實用。  
- `convertColor` 將十六進位顏色字串（例如 “FF0000”）轉換為 Java `Color` 物件，讓您自訂條碼前景與背景顏色。

## 步驟 2：實作自訂條碼產生器

我們將實作 `IBarcodeGenerator` 介面，讓 Aspose.Words 在遇到條碼欄位時能呼叫產生條碼影像。

### 程式碼：

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

- `getBarcodeImage` 依您指定的 **generate qr code java** 類型（此例為 QR）建立 `BarcodeGenerator`。  
- 透過工具方法套用前景與背景顏色，最後回傳渲染好的影像。  
- 若條碼產生失敗，會回傳備用影像，確保程式不中斷。

## 步驟 3：產生條碼並加入 Word 文件

現在把所有元件組合起來：建立文件、產生條碼，並 **how to add barcode** 至 Word 檔案。

### 程式碼：

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

1. **文件初始化** – 建立全新的 `Document`（或載入既有的 .docx）。  
2. **條碼參數** – 定義類型（`QR`）、值與顏色，示範 **generate qr code java** 的使用方式。  
3. **影像插入** – `builder.insertImage` 將條碼插入指定位置，實際展示 **how to add barcode** 至 Word 檔案的流程。  
4. **儲存** – 最終文件 (`CustomBarcodeLabels.docx`) 已內嵌條碼，可直接列印或分發。

## 常見問題與解決方案

| 問題 | 原因 | 解決方式 |
|------|------|----------|
| 條碼顯示空白 | 顏色字串無效或條碼類型不支援 | 檢查十六進位顏色格式，並使用支援的類型（例如 QR、Code128）。 |
| 影像尺寸不正確 | 像素轉換計算錯誤 | 使用 `twipsToPixels` 依 Word 版面計算精確尺寸。 |
| 授權例外 | 未提供有效的 Aspose 授權 | 在執行程式前套用臨時或正式授權。 |

## 常見問答

**Q：可以在沒有授權的情況下使用 Aspose.Words for Java 嗎？**  
A：可以，但會受到評估限制。建議取得 [臨時授權](https://purchase.aspose.com/temporary-license/) 以獲得完整功能。

**Q：我可以產生哪些類型的條碼？**  
A：Aspose.BarCode 支援 QR、Code 128、EAN‑13 等多種條碼。完整清單請參閱官方 [文件](https://reference.aspose.com/words/java/)。  

**Q：如何調整條碼大小？**  
A：可在 `builder.insertImage` 的寬高參數調整，或修改 `BarcodeGenerator` 物件的 `XDimension` 與 `BarHeight` 屬性。  

**Q：可以為條碼的可讀文字使用自訂字型嗎？**  
A：當然可以。使用 `CodeTextParameters` 屬性設定字型族、大小與樣式。  

**Q：在哪裡可以取得 Aspose.Words 的支援？**  
A：請前往 [支援論壇](https://forum.aspose.com/c/words/8/) 與社群或官方取得協助。  

---

**最後更新：** 2026-02-09  
**測試環境：** Aspose.Words for Java 24.12、Aspose.BarCode for Java 24.12  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}