---
category: general
date: 2026-09-18
description: Tạo tài liệu trống và chèn các hình dạng vào Word bằng Aspose.Words –
  tìm hiểu cách thêm hình tam giác và nhiều hơn nữa.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- add shapes to word
- how to insert triangle
- add triangle shape
- create word document
language: vi
lastmod: 2026-09-18
og_description: Tạo tài liệu trống trong Word bằng Aspose.Words và học cách chèn hình
  tam giác, nhóm các hình dạng và các đồ họa khác. Theo dõi hướng dẫn đầy đủ này.
og_image_alt: Screenshot of a Word document showing a grouped shape with a triangle
  inside
og_title: Tạo tài liệu trống và thêm hình dạng vào Word – hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document and insert shapes to Word with Aspose.Words –
    learn how to add a triangle shape and more.
  headline: How to create blank document and add shapes to Word
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Cách tạo tài liệu trống và thêm hình dạng vào Word
url: /vi/java/images-shapes/how-to-create-blank-document-and-add-shapes-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo tài liệu trống và thêm hình dạng vào Word

Nếu bạn cần **tạo tài liệu trống** và sau đó làm phong phú nó bằng đồ họa, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Chúng tôi sẽ hướng dẫn tạo một tệp Word từ đầu và **thêm hình dạng vào Word**, bao gồm **cách chèn hình tam giác**, sử dụng Aspose.Words for Java.

Bạn sẽ hoàn thành tutorial với một tệp *.docx* sẵn sàng sử dụng chứa một hình dạng nhóm giữ một tam giác. Các bước bao gồm mọi thứ từ thiết lập dự án đến lưu **tạo tài liệu word** cuối cùng. Không cần công cụ bên ngoài nào ngoài Aspose.Words.

## Các yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* Java 17 hoặc phiên bản mới hơn đã được cài đặt  
* Maven hoặc Gradle để quản lý phụ thuộc  
* Giấy phép Aspose.Words for Java (bản đánh giá miễn phí hoạt động cho demo này)  

Nếu bạn thích hệ thống build khác, hãy điều chỉnh cú pháp phụ thuộc cho phù hợp. Mã hoạt động trên bất kỳ nền tảng nào hỗ trợ Java.

## Tạo tài liệu trống với Aspose.Words

Hoạt động đầu tiên là **tạo tài liệu trống** trong bộ nhớ. Aspose.Words cung cấp lớp `Document` đại diện cho một tệp Word không có nội dung nào.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank document
```

Bộ tạo `new Document()` xây dựng một cấu trúc *.docx* rỗng, bạn có thể sau này điền vào các đoạn văn, bảng hoặc đồ họa. Vì tài liệu trống, bạn có toàn quyền kiểm soát mọi yếu tố bạn thêm vào.

## Thêm hình dạng vào Word – chèn một hình dạng nhóm

Một hình dạng nhóm cho phép bạn xử lý nhiều đồ họa như một đơn vị duy nhất. Điều này hữu ích khi bạn muốn di chuyển hoặc thay đổi kích thước nhiều hình dạng cùng lúc.

```java
        // Step 2: Initialize a DocumentBuilder to construct content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a group shape of size 300 × 300 points
        GroupShape group = builder.insertGroupShape(300.0, 300.0);
```

`DocumentBuilder` là API chính để thêm nội dung. Lệnh `insertGroupShape` tạo một container có kích thước 300 × 300 điểm (khoảng 4 × 4 inch). Sau lệnh này, con trỏ được đặt *bên trong* nhóm, sẵn sàng cho các hình dạng bổ sung.

### Tại sao nên dùng hình dạng nhóm?

Nhóm giúp các đồ họa liên quan được căn chỉnh và dễ dàng áp dụng định dạng đồng nhất. Nếu sau này bạn quyết định di chuyển tam giác, toàn bộ nhóm sẽ di chuyển cùng nhau, giữ nguyên bố cục.

## Cách chèn hình tam giác vào trong nhóm

Bây giờ chúng ta sẽ giải quyết **cách chèn hình tam giác**. Tam giác là một trong các giá trị `ShapeType` có sẵn.

```java
        // Step 4: Move the cursor into the group's first paragraph
        builder.moveTo(group.getFirstParagraph());

        // Step 5: Insert a triangle shape of size 60 × 60 points inside the group
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);
```

Lệnh `moveTo` đảm bảo điểm chèn của builder là đoạn văn đầu tiên của nhóm. `insertShape` sau đó thêm một tam giác có kích thước 60 × 60 điểm. Vì con trỏ đang ở bên trong nhóm, tam giác trở thành một phần con của hình dạng nhóm.

**Mẹo thêm hình tam giác**:

* Kích thước được đo bằng điểm; 72 điểm bằng một inch. Điều chỉnh kích thước cho phù hợp với bố cục của bạn.  
* Nếu bạn cần hướng khác, sử dụng `builder.getCurrentParagraph().getParagraphFormat().setAlignment()` để căn chỉnh hình dạng trong nhóm.  
* Tam giác sẽ kế thừa màu nền và kiểu đường viền của nhóm trừ khi bạn ghi đè bằng `shape.getFillColor()` hoặc `shape.getStrokeColor()`.

## Lưu tài liệu – tạo tài liệu word

Sau khi xây dựng đồ họa, bạn lưu tệp. Bước này hoàn thiện thao tác **tạo tài liệu word**.

```java
        // Step 6: Save the document with the extended group shape
        doc.save("ExtendedGroup.docx");               // create word document
    }
}
```

`doc.save` ghi biểu diễn trong bộ nhớ ra đĩa dưới dạng tài liệu Word tiêu chuẩn. Bạn có thể mở `ExtendedGroup.docx` trong Microsoft Word, LibreOffice hoặc bất kỳ trình xem nào hỗ trợ định dạng OOXML. Tệp sẽ hiển thị một hình dạng nhóm chứa một tam giác, chính xác như mã đã tạo.

## Ví dụ đầy đủ có thể chạy

Kết hợp tất cả các phần lại, đây là chương trình hoàn chỉnh mà bạn có thể sao chép, biên dịch và chạy:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Prepare a builder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a group shape (300 × 300 points)
        GroupShape group = builder.insertGroupShape(300.0, 300.0);

        // 4. Position the cursor inside the group
        builder.moveTo(group.getFirstParagraph());

        // 5. Insert a triangle shape (60 × 60 points)
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);

        // 6. Save the file – this creates the final Word document
        doc.save("ExtendedGroup.docx");
    }
}
```

### Kết quả mong đợi

Khi mở `ExtendedGroup.docx`, bạn sẽ thấy một hình dạng nhóm duy nhất nằm ở trung tâm trang. Bên trong nhóm, một tam giác nhỏ xuất hiện ở vị trí mặc định. Tam giác có thể được chọn và di chuyển như một phần của nhóm, xác nhận rằng **thêm hình dạng vào word** đã hoạt động như dự kiến.

## Các câu hỏi thường gặp và trường hợp đặc biệt

| Câu hỏi | Trả lời |
|----------|--------|
| *Tôi có thể thêm hơn một hình dạng vào trong nhóm không?* | Có. Sau khi chèn tam giác, giữ con trỏ bên trong nhóm và gọi lại `builder.insertShape` với một `ShapeType` khác. |
| *Nếu tôi muốn tam giác có màu đỏ thì sao?* | Lấy đối tượng `Shape` trả về bởi `insertShape` và gọi `shape.getFillColor().setColor(Color.RED)`. |
| *Điều này có hoạt động với các tệp .doc cũ không?* | Aspose.Words lưu ở định dạng bạn chỉ định. Sử dụng `doc.save("file.doc", SaveFormat.DOC)` để tạo tệp Word phiên bản cũ. |
| *Làm sao thay đổi viền của nhóm?* | Dùng `group.getStrokeColor().setColor(Color.BLUE)` và `group.setLineWeight(2.0)` để tùy chỉnh đường viền. |
| *Có cách nào xoay tam giác không?* | Gọi `shape.getRotation()` để đặt góc độ theo độ. |

## Mẹo chuyên nghiệp

* **Tái sử dụng builder** – tạo một `DocumentBuilder` mới cho mỗi hình dạng sẽ gây tốn tài nguyên. Giữ một builder duy nhất cho toàn bộ tài liệu.  
* **Chuyển đổi đơn vị** – nếu bạn làm việc với milimet, chuyển chúng sang điểm (`points = mm * 2.83465`).  
* **Hiệu năng** – đối với tài liệu lớn, gọi `doc.updatePageLayout()` chỉ một lần sau khi tất cả các hình dạng đã được thêm.

## Kết luận

Bây giờ bạn đã biết cách **tạo tài liệu trống**, **thêm hình dạng vào Word**, và cụ thể **cách chèn hình tam giác** bằng Aspose.Words for Java. Ví dụ đầy đủ minh họa quy trình từ tệp rỗng đến một **tạo tài liệu word** đã lưu chứa một tam giác nhóm.

Từ đây, bạn có thể khám phá các giá trị `ShapeType` khác, áp dụng kiểu dáng tùy chỉnh, hoặc kết hợp nhiều nhóm để xây dựng các sơ đồ phức tạp. Thử nghiệm với các kích thước, màu sắc và vị trí khác nhau để thành thạo tự động hoá Word bằng Java.

--- 

*Bạn đã sẵn sàng tự động hoá báo cáo tiếp theo chưa? Sao chép ví dụ, điều chỉnh kích thước và tích hợp mã vào ứng dụng của mình ngay hôm nay.*


## Bạn nên học gì tiếp theo?


Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm mã mẫu đầy đủ và các giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}