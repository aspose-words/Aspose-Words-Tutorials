---
date: 2025-12-10
description: Tìm hiểu cách tạo nhãn mã vạch tùy chỉnh bằng Aspose.Words cho Java.
  Hướng dẫn từng bước này cho bạn biết cách chèn mã vạch vào tài liệu Word.
linktitle: Generating Custom Barcode Labels
second_title: Aspose.Words Java Document Processing API
title: Tạo Nhãn Mã Vạch Tùy Chỉnh trong Aspose.Words cho Java
url: /vi/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tạo Nhãn Mã Vạch Tùy Chỉnh trong Aspose.Words cho Java

## Giới thiệu về việc tạo mã vạch tùy chỉnh trong Aspose.Words cho Java

Mã vạch là yếu tố quan trọng trong các ứng dụng hiện đại—cho dù bạn đang quản lý tồn kho, in vé, hay tạo thẻ ID. Trong hướng dẫn này, bạn sẽ **tạo nhãn mã vạch tùy chỉnh** và nhúng chúng trực tiếp vào tài liệu Word bằng giao diện `IBarcodeGenerator`. Chúng tôi sẽ hướng dẫn từng bước, từ việc thiết lập môi trường đến chèn hình ảnh mã vạch, để bạn có thể bắt đầu sử dụng mã vạch trong các dự án Java ngay lập tức.

## Câu trả lời nhanh
- **Hướng dẫn này dạy gì?** Cách tạo nhãn mã vạch tùy chỉnh và nhúng chúng vào tệp Word bằng Aspose.Words cho Java.  
- **Loại mã vạch nào được sử dụng trong ví dụ?** Mã QR (bạn có thể thay thế bằng bất kỳ loại nào được hỗ trợ).  
- **Tôi có cần giấy phép không?** Cần một giấy phép tạm thời để truy cập không giới hạn trong quá trình phát triển.  
- **Yêu cầu phiên bản Java nào?** JDK 8 trở lên.  
- **Tôi có thể thay đổi kích thước hoặc màu sắc của mã vạch không?** Có — chỉnh sửa các thiết lập `BarcodeParameters` và `BarcodeGenerator`.

## Yêu cầu trước

Trước khi bắt đầu viết mã, hãy đảm bảo bạn có những thứ sau:

- Java Development Kit (JDK): Phiên bản 8 trở lên.  
- Thư viện Aspose.Words cho Java: [Download here](https://releases.aspose.com/words/java/).  
- Thư viện Aspose.BarCode cho Java: [Download here](https://releases.aspose.com/).  
- Môi trường phát triển tích hợp (IDE): IntelliJ IDEA, Eclipse, hoặc bất kỳ IDE nào bạn thích.  
- Giấy phép tạm thời: Nhận một [temporary license](https://purchase.aspose.com/temporary-license/) để truy cập không giới hạn.

## Nhập các gói

Chúng tôi sẽ sử dụng các thư viện Aspose.Words và Aspose.BarCode. Nhập các gói sau vào dự án của bạn:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Các import này cho phép chúng ta truy cập API tạo mã vạch và các lớp tài liệu Word cần thiết.

## Bước 1: Tạo lớp tiện ích cho các thao tác mã vạch

Để giữ cho mã chính sạch sẽ, chúng tôi sẽ đóng gói các hàm trợ giúp chung—như **chuyển đổi twips sang pixel** và **chuyển đổi màu hex**—trong một lớp tiện ích.

### Code

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

**Giải thích**

- `twipsToPixels` – Word đo kích thước bằng **twips**; phương thức này chuyển chúng sang pixel màn hình, rất hữu ích khi bạn cần định kích thước hình ảnh mã vạch một cách chính xác.  
- `convertColor` – Chuyển một chuỗi hexa (ví dụ, `"FF0000"` cho màu đỏ) thành đối tượng `java.awt.Color`, cho phép bạn **cách chèn mã vạch** với màu nền và màu chữ tùy chỉnh.

## Bước 2: Triển khai Trình tạo Mã vạch Tùy chỉnh

Bây giờ chúng ta sẽ triển khai giao diện `IBarcodeGenerator`. Lớp này sẽ chịu trách nhiệm **generate qr code java**‑style images mà Aspose.Words có thể nhúng.

### Code

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

**Giải thích**

- `getBarcodeImage` tạo một thể hiện của `BarcodeGenerator`, áp dụng các màu được cung cấp qua `BarcodeParameters`, và cuối cùng trả về một `BufferedImage`.  
- Phương thức này cũng xử lý lỗi một cách nhẹ nhàng bằng cách trả về một hình ảnh placeholder, đảm bảo việc tạo tài liệu Word không bị lỗi.

## Bước 3: Tạo mã vạch và **nhúng mã vạch vào Word**

Với trình tạo đã sẵn sàng, chúng ta có thể tạo ra một hình ảnh mã vạch và **chèn nó vào tài liệu Word**.

### Code

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

**Giải thích**

1. **Khởi tạo tài liệu** – Tạo một `Document` mới (hoặc bạn có thể tải một mẫu có sẵn).  
2. **Tham số mã vạch** – Xác định loại mã vạch (`QR`), giá trị cần mã hoá, và màu nền/màu chữ.  
3. **Chèn hình ảnh** – `builder.insertImage` đặt mã vạch đã tạo ở kích thước mong muốn (200 × 200 pixel). Đây là phần cốt lõi của **cách chèn mã vạch** vào tệp Word.  
4. **Lưu** – Tài liệu cuối cùng, `CustomBarcodeLabels.docx`, chứa mã vạch đã nhúng, sẵn sàng để in hoặc phân phối.

## Tại sao nên tạo nhãn mã vạch tùy chỉnh với Aspose.Words?

- **Kiểm soát đầy đủ** về giao diện mã vạch (loại, kích thước, màu sắc).  
- **Tích hợp liền mạch** – không cần các tệp hình ảnh trung gian; mã vạch được tạo trong bộ nhớ và chèn trực tiếp.  
- **Đa nền tảng** – hoạt động trên bất kỳ hệ điều hành nào hỗ trợ Java, lý tưởng cho việc tạo tài liệu phía máy chủ.  
- **Mở rộng** – bạn có thể lặp qua nguồn dữ liệu để tạo hàng trăm nhãn cá nhân hoá trong một lần chạy.

## Các vấn đề thường gặp & Khắc phục

| Triệu chứng | Nguyên nhân khả dĩ | Cách khắc phục |
|-------------|---------------------|----------------|
| Mã vạch hiển thị trống | `BarcodeParameters` màu sắc giống nhau (ví dụ, đen trên đen) | Kiểm tra giá trị `foregroundColor` và `backgroundColor`. |
| Hình ảnh bị biến dạng | Kích thước pixel truyền vào `insertImage` không đúng | Điều chỉnh các tham số width/height hoặc sử dụng chuyển đổi `twipsToPixels` để có kích thước chính xác. |
| Lỗi loại mã vạch không được hỗ trợ | Sử dụng loại không được `CustomBarcodeGeneratorUtils.getBarcodeEncodeType` nhận dạng | Đảm bảo chuỗi loại mã vạch khớp với một trong các `EncodeTypes` được hỗ trợ (ví dụ, `"QR"`, `"CODE128"`). |

## Câu hỏi thường gặp

**Hỏi: Tôi có thể sử dụng Aspose.Words cho Java mà không có giấy phép không?**  
**Đáp:** Có, nhưng sẽ có một số hạn chế. Nhận một [temporary license](https://purchase.aspose.com/temporary-license/) để có đầy đủ chức năng.

**Hỏi: Tôi có thể tạo những loại mã vạch nào?**  
**Đáp:** Aspose.BarCode hỗ trợ QR, Code 128, EAN‑13 và nhiều định dạng khác. Kiểm tra [documentation](https://reference.aspose.com/words/java/) để xem danh sách đầy đủ.

**Hỏi: Làm sao tôi có thể thay đổi kích thước mã vạch?**  
**Đáp:** Điều chỉnh các tham số width và height trong `builder.insertImage`, hoặc sử dụng `twipsToPixels` để chuyển đổi đơn vị đo của Word sang pixel.

**Hỏi: Có thể sử dụng phông chữ tùy chỉnh cho văn bản mã vạch không?**  
**Đáp:** Có, bạn có thể tùy chỉnh phông chữ văn bản qua thuộc tính `CodeTextParameters` của `BarcodeGenerator`.

**Hỏi: Tôi có thể nhận được trợ giúp ở đâu nếu gặp vấn đề?**  
**Đáp:** Truy cập [support forum](https://forum.aspose.com/c/words/8/) để nhận hỗ trợ từ cộng đồng và kỹ sư Aspose.

## Kết luận

Bằng cách làm theo các bước trên, bạn đã biết cách **tạo hình ảnh mã vạch tùy chỉnh** và **nhúng mã vạch vào tài liệu Word** Aspose.Words cho Java. Kỹ thuật này đủ linh hoạt cho các thẻ kho, vé sự kiện, hoặc bất kỳ trường hợp nào mà mã vạch cần là một phần của tài liệu được tạo. Hãy thử nghiệm với các loại mã vạch và tùy chọn định dạng khác nhau để phù hợp với nhu cầu kinh doanh cụ thể của bạn.

**Cập nhật lần cuối:** 2025-12-10  
**Được kiểm tra với:** Aspose.Words cho Java 24.12, Aspose.BarCode cho Java 24.12  
**Tác giả:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}