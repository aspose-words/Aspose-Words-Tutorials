---
date: 2026-02-09
description: Tạo nhãn mã vạch tùy chỉnh bằng Aspose Barcode Java trong Aspose.Words
  for Java. Tìm hiểu cách nhúng mã vạch vào tài liệu Word và tạo các ví dụ Java về
  mã QR.
linktitle: Generating Custom Barcode Labels
second_title: Aspose.Words Java Document Processing API
title: Tạo nhãn mã vạch tùy chỉnh với Aspose Barcode Java
url: /vi/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tạo Nhãn Mã Vạch Tùy Chỉnh với Aspose Barcode Java

## Giới thiệu về Tạo Nhãn Mã Vạch Tùy Chỉnh trong Aspose.Words cho Java

Mã vạch là yếu tố thiết yếu trong các ứng dụng hiện đại, và **Aspose Barcode Java** giúp bạn tạo chúng một cách dễ dàng ngay trong tài liệu Word. Dù bạn cần **nhúng mã vạch vào Word**, tạo mã QR cho một URL, hay chuyển đổi đơn vị đo, hướng dẫn này sẽ hướng dẫn bạn qua mọi bước cần thiết. Sẵn sàng chưa? Hãy bắt đầu!

## Câu trả lời nhanh
- **Thư viện nào tạo mã vạch trong Java?** Aspose Barcode Java kết hợp với Aspose.Words cho Java.  
- **Loại mã vạch nào được minh họa?** Mã QR (generate qr code java).  
- **Làm sao chuyển đổi twips sang pixel?** Sử dụng phương thức tiện ích `twipsToPixels` được cung cấp.  
- **Có thể thêm mã vạch vào tệp Word hiện có không?** Có – chỉ cần dùng phương thức `DocumentBuilder.insertImage`.  
- **Có cần giấy phép không?** Giấy phép tạm thời sẽ loại bỏ các giới hạn đánh giá.

## Aspose Barcode Java là gì?
Aspose Barcode Java là một API mạnh mẽ cho phép các nhà phát triển tạo ra một loạt các mã vạch 1D và 2D (bao gồm cả mã QR) một cách lập trình. Khi kết hợp với Aspose.Words cho Java, bạn có thể **nhúng mã vạch vào Word** mà không cần rời khỏi môi trường Java.

## Tại sao nên dùng Aspose Barcode Java cùng Aspose.Words?
- **Kiểm soát toàn diện** về giao diện mã vạch (màu sắc, kích thước, định dạng).  
- **Tích hợp liền mạch** – hình ảnh mã vạch có thể được chèn trực tiếp vào tài liệu Word.  
- **Đa nền tảng** – hoạt động trên bất kỳ nền tảng nào hỗ trợ Java.  
- **Mở rộng** – bạn có thể tạo các lớp tiện ích để tái sử dụng logic mã vạch trong các dự án.

## Yêu cầu trước

Trước khi bắt đầu viết mã, hãy chắc chắn rằng bạn đã có:

- Java Development Kit (JDK): Phiên bản 8 trở lên.  
- Thư viện Aspose.Words cho Java: [Tải về tại đây](https://releases.aspose.com/words/java/).  
- Thư viện Aspose.BarCode cho Java: [Tải về tại đây](https://releases.aspose.com/).  
- Môi trường Phát triển Tích hợp (IDE): IntelliJ IDEA, Eclipse, hoặc bất kỳ IDE nào bạn thích.  
- Giấy phép tạm thời: Lấy một [giấy phép tạm thời](https://purchase.aspose.com/temporary-license/) để truy cập không giới hạn.

## Nhập các gói

Chúng ta sẽ sử dụng các thư viện Aspose.Words và Aspose.BarCode. Nhập các gói sau vào dự án của bạn:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Các import này cho phép chúng ta sử dụng các tính năng tạo mã vạch và tích hợp chúng vào tài liệu Word.

Hãy chia công việc này thành các bước dễ quản lý.

## Bước 1: Tạo lớp tiện ích cho các thao tác mã vạch

Để đơn giản hoá các thao tác liên quan đến mã vạch, chúng ta sẽ tạo một lớp tiện ích với các phương thức hỗ trợ các nhiệm vụ phổ biến như chuyển đổi màu và **chuyển đổi twips sang pixel**.

### Code:

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

- `twipsToPixels` chuyển đổi đơn vị đo mà Word sử dụng (twips) sang pixel màn hình – một công cụ hữu ích khi bạn cần kích thước chính xác.  
- `convertColor` chuyển một chuỗi màu hex (ví dụ “FF0000”) thành đối tượng `Color` của Java, cho phép bạn tùy chỉnh màu nền và màu mã vạch.

## Bước 2: Triển khai Trình tạo Mã vạch Tùy chỉnh

Chúng ta sẽ triển khai giao diện `IBarcodeGenerator` để Aspose.Words có thể yêu cầu hình ảnh mã vạch mỗi khi gặp trường mã vạch.

### Code:

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

- `getBarcodeImage` tạo một `BarcodeGenerator` sử dụng loại **generate qr code java** mà bạn chỉ định (QR trong ví dụ này).  
- Nó áp dụng màu nền và màu mã vạch thông qua các phương thức tiện ích, sau đó trả về hình ảnh đã render.  
- Hình ảnh dự phòng đảm bảo chương trình vẫn tiếp tục chạy ngay cả khi việc tạo mã vạch thất bại.

## Bước 3: Tạo mã vạch và chèn vào tài liệu Word

Bây giờ chúng ta sẽ kết hợp mọi thứ: tạo một tài liệu, tạo mã vạch, và **cách thêm mã vạch** vào tệp Word.

### Code:

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

1. **Khởi tạo Document** – tạo một `Document` mới (hoặc bạn có thể tải một file .docx hiện có).  
2. **Tham số Mã vạch** – xác định loại (`QR`), giá trị, và màu sắc, minh họa cách **generate qr code java** được sử dụng.  
3. **Chèn Hình ảnh** – `builder.insertImage` đặt mã vạch vào vị trí bạn muốn, thực tế cho thấy **cách thêm mã vạch** vào tệp Word.  
4. **Lưu** – tài liệu cuối cùng (`CustomBarcodeLabels.docx`) chứa mã vạch đã nhúng, sẵn sàng để in hoặc phân phối.

## Các vấn đề thường gặp và giải pháp

| Vấn đề | Nguyên nhân | Cách khắc phục |
|-------|-------------|----------------|
| Mã vạch hiển thị trống | Chuỗi màu không hợp lệ hoặc loại mã vạch không được hỗ trợ | Kiểm tra định dạng màu hex và sử dụng loại được hỗ trợ (ví dụ QR, Code128). |
| Kích thước hình ảnh sai | Chuyển đổi pixel không chính xác | Sử dụng `twipsToPixels` để tính kích thước chính xác dựa trên bố cục của Word. |
| Ngoại lệ giấy phép | Không có giấy phép Aspose hợp lệ | Áp dụng giấy phép tạm thời hoặc mua giấy phép trước khi chạy mã. |

## Câu hỏi thường gặp

**H: Tôi có thể sử dụng Aspose.Words cho Java mà không có giấy phép không?**  
Đ: Có, nhưng bạn sẽ gặp các giới hạn đánh giá. Hãy lấy một [giấy phép tạm thời](https://purchase.aspose.com/temporary-license/) để có đầy đủ chức năng.

**H: Tôi có thể tạo những loại mã vạch nào?**  
Đ: Aspose.BarCode hỗ trợ QR, Code 128, EAN‑13 và nhiều loại khác. Xem [tài liệu chính thức](https://reference.aspose.com/words/java/) để biết danh sách đầy đủ.

**H: Làm sao thay đổi kích thước mã vạch?**  
Đ: Điều chỉnh các tham số width/height trong `builder.insertImage` hoặc sửa các thuộc tính `XDimension` và `BarHeight` của đối tượng `BarcodeGenerator`.

**H: Tôi có thể sử dụng phông chữ tùy chỉnh cho phần đọc được của mã vạch không?**  
Đ: Chắc chắn rồi. Sử dụng thuộc tính `CodeTextParameters` để đặt họ phông, kích thước và kiểu.

**H: Tôi có thể nhận hỗ trợ về Aspose.Words ở đâu?**  
Đ: Truy cập [diễn đàn hỗ trợ](https://forum.aspose.com/c/words/8/) để nhận trợ giúp từ cộng đồng và hỗ trợ chính thức.

---

**Cập nhật lần cuối:** 2026-02-09  
**Đã kiểm tra với:** Aspose.Words cho Java 24.12, Aspose.BarCode cho Java 24.12  
**Tác giả:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}