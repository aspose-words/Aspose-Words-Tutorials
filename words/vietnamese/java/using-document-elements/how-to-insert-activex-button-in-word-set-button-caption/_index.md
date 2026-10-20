---
category: general
date: 2026-07-26
description: Cách chèn nút ActiveX vào tài liệu Word bằng Aspose.Words – học cách
  đặt chú thích, vị trí và kích thước của nút chỉ trong vài dòng.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert activex
- set button caption
language: vi
lastmod: 2026-07-26
og_description: Cách chèn nút ActiveX vào tài liệu Word bằng Aspose.Words. Thực hiện
  theo hướng dẫn từng bước này để đặt chú thích, vị trí và kích thước cho nút.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX CommandButton
  with a custom caption
og_title: Cách chèn nút ActiveX trong Word – Hướng dẫn nhanh
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: How to insert ActiveX button in a Word document using Aspose.Words
    – learn to set button caption, position, and size in just a few lines.
  headline: How to Insert ActiveX Button in Word – Set Button Caption
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- Document generation
title: Cách chèn nút ActiveX trong Word – Đặt nhãn nút
url: /vi/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách chèn nút ActiveX vào Word – Đặt chú thích nút

Bạn đã bao giờ tự hỏi **how to insert ActiveX** điều khiển vào một tệp Word mà không cần mở giao diện người dùng chưa? Bạn không phải là người duy nhất. Trong nhiều ứng dụng doanh nghiệp, bạn cần một nút có thể nhấp được để chạy macro, và việc thực hiện nó bằng chương trình sẽ tiết kiệm hàng giờ. Hướng dẫn này sẽ cho bạn thấy chính xác **how to insert ActiveX** CommandButton bằng Aspose.Words cho Java, và—đúng—cách **set button caption** để người dùng biết cần nhấn gì.

Chúng tôi sẽ hướng dẫn toàn bộ quy trình: từ việc thiết lập thư viện, tạo tài liệu mới, chèn nút, điều chỉnh kích thước và vị trí, đặt chú thích thân thiện, và cuối cùng lưu tệp. Khi hoàn thành, bạn sẽ có một file `.docx` có thể chạy được, mở trong Word với nút ActiveX hoạt động đầy đủ, sẵn sàng kích hoạt macro của bạn.

---

## Những gì bạn sẽ học

- Cài đặt và tham chiếu Aspose.Words trong dự án Java.  
- Tạo một `Document` và `DocumentBuilder` mới.  
- **Insert ActiveX** CommandButton control chỉ bằng một dòng mã.  
- **Set button caption**, điều chỉnh vị trí và xác định kích thước của nó.  
- Lưu tài liệu và mở trong Word để xem kết quả.

Không cần kinh nghiệm trước về ActiveX; chỉ cần kiến thức cơ bản về Java và một bản sao Aspose.Words.

---

## Yêu cầu trước

- Java 8 hoặc mới hơn đã được cài đặt trên máy của bạn.  
- Maven hoặc Gradle để quản lý phụ thuộc (chúng tôi sẽ hiển thị đoạn mã Maven).  
- Bản sao có giấy phép hoặc bản dùng thử của **Aspose.Words for Java** (bản dùng thử miễn phí hoạt động tốt cho bản demo này).  
- Microsoft Word (bất kỳ phiên bản mới nào) để kiểm tra tệp đã tạo.

---

## Bước 1: Thiết lập Aspose.Words trong dự án của bạn

Đầu tiên, thêm phụ thuộc Aspose.Words. Nếu bạn dùng Maven, chèn đoạn này vào `pom.xml` của bạn:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for the latest version -->
</dependency>
```

Người dùng Gradle có thể thêm:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

Sau khi chạy nhanh `mvn clean install` (hoặc `gradle build`) thư viện sẽ có trong classpath và bạn đã sẵn sàng viết mã.

---

## Bước 2: Tạo tài liệu mới và Builder

`Document` đại diện cho toàn bộ tệp Word, trong khi `DocumentBuilder` cho phép bạn chỉnh sửa nó. Hãy nghĩ về Builder như một cây bút vẽ trên một canvas trắng mới.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();                 // creates an empty .docx
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Tại sao lại bắt đầu với tài liệu trống? Điều này đảm bảo bạn có toàn quyền kiểm soát mọi thành phần bạn thêm vào, và không có định dạng ẩn nào gây bất ngờ sau này.

---

## Bước 3: Chèn điều khiển ActiveX CommandButton

Bây giờ là phần trọng tâm. Aspose.Words cung cấp phương thức `insertForms2OleControl` có thể đặt bất kỳ điều khiển ActiveX nào bạn chỉ định. Ở đây chúng ta yêu cầu một **CommandButton**.

```java
        // Step 3: Insert a CommandButton ActiveX control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

Phương thức này trả về một đối tượng `Forms2OleControl`, cho phép bạn truy cập lập trình vào các thuộc tính của nút. Đây là nơi **how to insert activex** trở thành một dòng lệnh—không cần can thiệp vào các API COM cấp thấp.

---

## Bước 4: Vị trí, kích thước và Đặt chú thích nút

Một nút trôi giữa trang không thực sự hữu ích. Bạn sẽ muốn đặt nó ở vị trí người dùng mong đợi, cho nó kích thước hợp lý, và—quan trọng nhất—**set button caption** để họ biết nhấn vào gì sẽ xảy ra.

```java
        // Step 4a: Position the button (coordinates are in points)
        commandBtn.setLeft(100);   // distance from the left margin
        commandBtn.setTop(150);    // distance from the top margin

        // Step 4b: Define width and height
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Step 4c: Set the button caption (the text that appears on the button)
        commandBtn.setCaption("Click Me");
```

**Tại sao lại dùng các số này?** Word sử dụng đơn vị điểm (1 pt ≈ 1/72 inch). `100 pt` ≈ 1.4 in từ trái, `150 pt` ≈ 2.1 in từ trên—gần trung tâm của một trang A4 tiêu chuẩn. Điều chỉnh chúng cho phù hợp với bố cục của bạn.

Đặt chú thích là điều quan trọng; nếu không, nút sẽ chỉ hiển thị một hình chữ nhật trống. Phương thức `setCaption` chấp nhận bất kỳ chuỗi nào, vì vậy bạn có thể địa phương hoá sau này nếu cần.

---

## Bước 5: Lưu tài liệu

Cuối cùng, ghi tài liệu ra đĩa. Bạn có thể chọn bất kỳ thư mục nào; chỉ cần đảm bảo đường dẫn tồn tại.

```java
        // Step 5: Save the document to a .docx file
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Khi bạn mở `ActiveXButton.docx` trong Word, bạn sẽ thấy một nút được đặt đẹp mắt với nhãn **“Click Me.”** Nếu bạn nhấp đúp vào nó, Word sẽ yêu cầu bạn bật macro (vì các điều khiển ActiveX được xem là macro‑enabled). Từ đó bạn có thể gán một routine VBA vào sự kiện `Click` của nút.

---

## Các trường hợp đặc biệt & Mẹo bạn có thể bỏ qua

- **Macro‑Enabled Format**: Word vô hiệu hoá các điều khiển ActiveX trong các tệp `.docx` thông thường trừ khi người dùng bật macro. Nếu bạn cần nút hoạt động ngay, hãy cân nhắc lưu dưới dạng `.docm` (macro‑enabled) bằng cách sử dụng `doc.save(outputPath, SaveFormat.DOCM);`.  
- **Compatibility**: Các phiên bản Word cũ hơn (trước 2007) sử dụng định dạng nhị phân `.doc`. Aspose.Words có thể lưu sang định dạng đó, nhưng các thuộc tính của điều khiển có thể hiển thị hơi khác nhau.  
- **Security Settings**: Một số môi trường doanh nghiệp khóa ActiveX. Nếu nút của bạn không xuất hiện, kiểm tra Trust Center của Word → ActiveX Settings.  
- **Multiple Buttons**: Muốn có nhiều hơn một nút? Chỉ cần lặp lại lời gọi `insertForms2OleControl` và điều chỉnh các giá trị `Left`/`Top` cho mỗi nút. Giữ lại các đối tượng trả về để bạn có thể đặt chú thích riêng cho từng nút.  
- **Styling the Caption**: Chú thích kế thừa phông chữ mặc định. Để thay đổi, bạn cần chỉnh sửa XML nền hoặc áp dụng một style Word sau khi chèn—điều này nằm ngoài phạm vi của hướng dẫn nhanh này, nhưng có thể thực hiện được bằng API `ParagraphFormat` của Aspose.Words.

---

## Ví dụ hoàn chỉnh hoạt động

Dưới đây là lớp Java đầy đủ, sẵn sàng chạy. Sao chép‑dán vào IDE của bạn, điều chỉnh đường dẫn xuất, và nhấn **Run**.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Position the button (points from the left/top margins)
        commandBtn.setLeft(100);
        commandBtn.setTop(150);

        // Set size (width × height in points)
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Set the button caption – this is the visible text
        commandBtn.setCaption("Click Me");

        // Save the document; you may also use SaveFormat.DOCM for macro‑enabled files
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

**Kết quả mong đợi**: Sau khi chạy, console sẽ in ra vị trí lưu. Mở tệp đã tạo trong Word sẽ hiển thị một nút đặt gần trung tâm trang, nhãn “Click Me”. Nhấp vào nó sẽ kích hoạt sự kiện click chuẩn của ActiveX (bạn sẽ cần gắn một macro VBA để phản hồi).

---

## Kết luận

Bạn giờ đã biết **how to insert ActiveX** CommandButton vào tài liệu Word một cách lập trình bằng Aspose.Words, và đã thấy chính xác cách **set button caption**, vị trí và kích thước của điều khiển. Cách tiếp cận này loại bỏ công việc UI thủ công, tích hợp sạch sẽ vào các trình tạo báo cáo tự động, và cho bạn toàn quyền kiểm soát trên

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Insert an Image into Word Document Header | Aspose.Words for .NET](/words/english/net/header-footer-formatting/insert-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}