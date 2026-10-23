---
date: 2026-10-23
description: Tìm hiểu cách tạo nhãn QR code Java với Aspose.Words. Hướng dẫn từng
  bước này chỉ cho bạn cách nhúng barcodes vào Word documents và tùy chỉnh size, colors
  và format.
keywords:
- create qr code java
- how to create barcode label
- add barcode to word document
- embed barcode in word
lastmod: 2026-10-23
linktitle: Tạo nhãn Barcode tùy chỉnh
og_description: Tìm hiểu cách tạo nhãn QR code Java với Aspose.Words. Hướng dẫn này
  giải thích việc nhúng barcode, kiểm soát size và tùy chỉnh color trong Word documents.
og_image_alt: 'Developer guide: generate custom QR code labels in Java with Aspose.Words'
og_title: Cách tạo nhãn QR code Java bằng Aspose.Words
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
title: Cách tạo nhãn QR code Java bằng Aspose.Words
url: /vi/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo nhãn QR code Java bằng Aspose.Words

Mã vạch là yếu tố quan trọng trong các ứng dụng hiện đại—bất kể bạn đang quản lý tồn kho, in vé, hay tạo thẻ ID. Trong hướng dẫn này, bạn sẽ **tạo nhãn QR code Java** và nhúng chúng trực tiếp vào tài liệu Word bằng giao diện `IBarcodeGenerator`. Chúng tôi sẽ hướng dẫn từng bước, từ việc thiết lập môi trường đến chèn hình ảnh mã vạch, để bạn có thể ngay lập tức sử dụng mã vạch trong các dự án Java của mình.

## Câu trả lời nhanh
- **Hướng dẫn này dạy gì?** Cách tạo nhãn QR code Java và nhúng chúng vào tệp Word với Aspose.Words for Java.  
- **Loại mã vạch nào được sử dụng trong ví dụ?** QR code (bạn có thể thay thế bằng bất kỳ loại nào trong hơn 20 loại được hỗ trợ).  
- **Tôi có cần giấy phép không?** Cần một giấy phép tạm thời để truy cập không giới hạn trong quá trình phát triển.  
- **Phiên bản Java nào được yêu cầu?** JDK 8 trở lên.  
- **Tôi có thể thay đổi kích thước hoặc màu sắc của mã vạch không?** Có—sửa các thiết lập `BarcodeParameters` và `BarcodeGenerator`.

## create QR code Java là gì?
`create QR code Java` đề cập đến việc tạo hình ảnh QR‑code một cách lập trình trong môi trường Java và chèn nó vào tài liệu hoặc thành phần UI. Aspose.Words for Java kết hợp với Aspose.BarCode cho phép bạn tạo hình ảnh hoàn toàn trong bộ nhớ, tránh việc tạo file tạm.

## Tại sao tạo nhãn mã vạch tùy chỉnh với Aspose.Words?
Aspose.Words hỗ trợ **35+ định dạng đầu vào và đầu ra** và có thể xử lý **tài liệu 500 trang trong dưới 3 giây** trên phần cứng máy chủ tiêu chuẩn. Khi sử dụng tạo mã vạch trong bộ nhớ, bạn có toàn quyền kiểm soát loại, kích thước và màu sắc đồng thời giữ quy trình hoàn toàn dựa trên Java và không phụ thuộc vào nền tảng.

## Yêu cầu trước

- Java Development Kit (JDK): Phiên bản 8 trở lên.  
- Thư viện Aspose.Words for Java: [Tải xuống tại đây](https://releases.aspose.com/words/java/).  
- Thư viện Aspose.BarCode for Java: [Tải xuống tại đây](https://releases.aspose.com/).  
- Môi trường Phát triển Tích hợp (IDE): IntelliJ IDEA, Eclipse, hoặc bất kỳ IDE nào bạn thích.  
- Giấy phép tạm thời: Nhận một [giấy phép tạm thời](https://purchase.aspose.com/temporary-license/) để truy cập không giới hạn.

## Nhập các gói

Chúng ta sẽ sử dụng các thư viện Aspose.Words và Aspose.BarCode. Nhập các gói sau vào dự án của bạn:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Các import này cho phép chúng ta truy cập API tạo mã vạch và các lớp tài liệu Word cần thiết.

## Bước 1: tạo lớp tiện ích cho các thao tác mã vạch

Lớp tiện ích chứa các hàm trợ giúp có thể tái sử dụng như **chuyển đổi twips sang pixel** và **chuyển đổi màu hex**.  
Lớp `CustomBarcodeGeneratorUtils` cung cấp các phương thức tĩnh cho việc chuyển đổi đơn vị và xử lý màu sắc.

### Mã

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
- `convertColor` – Chuyển một chuỗi hexa (ví dụ, `"FF0000"` cho màu đỏ) thành đối tượng `java.awt.Color`, cho phép bạn **thêm mã vạch vào tài liệu Word** với màu nền và màu chữ tùy chỉnh.

## Bước 2: triển khai trình tạo mã vạch tùy chỉnh

Bây giờ chúng ta sẽ triển khai giao diện `IBarcodeGenerator`. Lớp này chịu trách nhiệm **tạo hình ảnh QR code Java** mà Aspose.Words có thể nhúng.  
Giao diện `IBarcodeGenerator` định nghĩa một phương thức duy nhất trả về một `BufferedImage` đại diện cho mã vạch.

### Mã

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
- Phương thức cũng xử lý lỗi một cách nhẹ nhàng bằng cách trả về hình ảnh placeholder, đảm bảo quá trình tạo tài liệu Word không bị crash.

## Cách nhúng mã vạch vào Word bằng Aspose.Words?

Tải tệp Word của bạn bằng `new Document("template.docx")` (hoặc tạo một `Document` mới) và gọi `builder.insertImage` với hình ảnh mã vạch trả về từ trình tạo. Mẫu hai‑bước này nhúng mã vạch trực tiếp mà không cần ghi file tạm vào đĩa. Bằng cách chỉ định kích thước ảnh bằng pixel hoặc chuyển đổi twips của Word sang pixel, bạn có thể kiểm soát kích thước và vị trí chính xác của mã vạch trong tài liệu, đảm bảo bố cục chuyên nghiệp và in ra đúng trên bất kỳ máy in nào.

## Bước 3: tạo mã vạch và nhúng mã vạch vào Word

Với trình tạo đã sẵn sàng, chúng ta có thể tạo hình ảnh mã vạch và **chèn nó vào tài liệu Word**.

### Mã

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

1. **Khởi tạo Document** – Tạo một `Document` mới (hoặc bạn có thể tải một mẫu hiện có).  
2. **Tham số mã vạch** – Xác định loại mã vạch (`QR`), giá trị cần mã hoá, và màu nền/màu chữ.  
3. **Chèn ảnh** – `builder.insertImage` đặt mã vạch đã tạo ở kích thước mong muốn (200 × 200 pixel). Đây là phần cốt lõi của **cách nhúng mã vạch vào Word**.  
4. **Lưu** – Tài liệu cuối cùng, `CustomBarcodeLabels.docx`, chứa mã vạch đã nhúng, sẵn sàng để in hoặc phân phối.

## Các vấn đề thường gặp & khắc phục

| Triệu chứng | Nguyên nhân có thể | Cách khắc phục |
|------------|--------------------|----------------|
| Mã vạch hiển thị trống | Màu `BarcodeParameters` giống nhau (ví dụ, đen trên nền đen) | Kiểm tra lại giá trị `foregroundColor` và `backgroundColor`. |
| Hình ảnh bị biến dạng | Kích thước pixel truyền vào `insertImage` không đúng | Điều chỉnh các tham số chiều rộng/chiều cao hoặc sử dụng chuyển đổi `twipsToPixels` để có kích thước chính xác. |
| Lỗi loại mã vạch không được hỗ trợ | Sử dụng loại không được `CustomBarcodeGeneratorUtils.getBarcodeEncodeType` nhận diện | Đảm bảo chuỗi loại mã vạch khớp với một trong các `EncodeTypes` được hỗ trợ (ví dụ, `"QR"`, `"CODE128"`). |

## Câu hỏi thường gặp

**Q: Tôi có thể sử dụng Aspose.Words cho Java mà không có giấy phép không?**  
A: Có, nhưng sẽ có các hạn chế trong phiên bản đánh giá. Nhận một [giấy phép tạm thời](https://purchase.aspose.com/temporary-license/) để có đầy đủ chức năng.

**Q: Tôi có thể tạo những loại mã vạch nào?**  
A: Aspose.BarCode hỗ trợ QR, Code 128, EAN‑13, DataMatrix, PDF417 và nhiều định dạng khác—hơn 20 biểu tượng tổng cộng. Xem [tài liệu](https://reference.aspose.com/words/java/) để biết danh sách đầy đủ.

**Q: Làm sao tôi có thể thay đổi kích thước mã vạch?**  
A: Điều chỉnh các tham số chiều rộng và chiều cao trong `builder.insertImage`, hoặc tính toán chính xác twips của Word bằng `twipsToPixels` để kiểm soát pixel‑perfect.

**Q: Có thể sử dụng phông chữ tùy chỉnh cho văn bản mã vạch không?**  
A: Có, bạn có thể tùy chỉnh phông chữ văn bản qua thuộc tính `CodeTextParameters` của `BarcodeGenerator`.

**Q: Tôi có thể tìm trợ giúp ở đâu nếu gặp vấn đề?**  
A: Truy cập [diễn đàn hỗ trợ](https://forum.aspose.com/c/words/8/) để nhận sự trợ giúp từ cộng đồng và các kỹ sư Aspose.

## Kết luận

Bằng cách làm theo các bước trên, bạn đã biết cách **tạo hình ảnh QR code Java** và **nhúng mã vạch vào tài liệu Word** bằng Aspose.Words for Java. Kỹ thuật này đủ linh hoạt cho thẻ kho, vé sự kiện, hoặc bất kỳ trường hợp nào cần mã vạch là một phần của tài liệu được tạo. Hãy thử nghiệm các loại mã vạch, màu sắc và tùy chọn kích thước khác nhau để phù hợp với nhu cầu kinh doanh cụ thể của bạn.

---

**Last Updated:** 2026-10-23  
**Tested With:** Aspose.Words for Java 24.12, Aspose.BarCode for Java 24.12  
**Author:** Aspose

## Các hướng dẫn liên quan

- [Tạo PDF từ Word với tạo mã vạch – Aspose.Words cho Java](/words/java/document-conversion-and-export/using-barcode-generation/)
- [Lưu Word dưới dạng Pdf với Aspose Words – Hướng dẫn từng bước cho Java](/words/java/document-conversion-and-export/save-word-as-pdf-with-aspose-words-step-by-step-java-guide/)
- [Tạo tài liệu Word trống trong Java với Aspose Words](/words/java/document-manipulation/create-blank-word-document-in-java-with-aspose-words/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}