---
category: general
date: 2026-07-20
description: Tạo tài liệu Word trống trong Java bằng Aspose.Words. Tìm hiểu cách tạo
  nhóm, chèn hình chữ nhật và nhúng hình ảnh vào hình dạng.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create group
- add image word document
- insert rectangle shape
- embed image in shape
language: vi
lastmod: 2026-07-20
og_description: Tạo tài liệu Word trống trong Java bằng Aspose.Words. Hướng dẫn này
  chỉ cách tạo nhóm, chèn hình chữ nhật và nhúng hình ảnh vào hình dạng cho các tệp
  Word động.
og_image_alt: Screenshot of a blank Word document containing a grouped shape with
  a rectangle and an embedded image
og_title: Tạo tài liệu Word trống với hình dạng nhóm – Hướng dẫn Java
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  headline: Create blank word document with grouped shape – Java guide
  type: TechArticle
- description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  name: Create blank word document with grouped shape – Java guide
  steps:
  - name: '`output.docx` appears in the project folder.'
    text: '`output.docx` appears in the project folder.'
  - name: Opening the file shows a single page with a grouped shape.
    text: Opening the file shows a single page with a grouped shape.
  - name: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
    text: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
  - name: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
    text: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Tạo tài liệu Word trống với hình nhóm – Hướng dẫn Java
url: /vi/java/images-shapes/create-blank-word-document-with-grouped-shape-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu Word trống với hình dạng nhóm – Hướng dẫn Java

Bạn đã bao giờ tự hỏi làm thế nào để **tạo tài liệu Word trống** mà đã chứa sẵn một hình dạng được nhóm gọn gàng chưa? Có thể bạn đang xây dựng mẫu báo cáo, hoặc cần một chỗ giữ chỗ cho logo và chú thích. Dù sao, vấn đề này rất phổ biến: bạn bắt đầu với một tệp rỗng, sau đó phải thêm một nhóm, chèn một hình chữ nhật vào bên trong, và cuối cùng nhúng một hình ảnh — tất cả đều được thực hiện bằng mã.

Trong hướng dẫn này, chúng tôi sẽ đi qua một ví dụ Java hoàn chỉnh, sẵn sàng chạy, thực hiện chính xác những việc trên. Bạn sẽ học **cách tạo nhóm**, **chèn hình chữ nhật**, và **thêm hình ảnh vào tài liệu Word** trong cùng một nhóm. Khi kết thúc, bạn sẽ có một tệp Word trông như một mẫu đã được hoàn thiện, sẵn sàng cho việc tùy chỉnh thêm.

> **Bạn sẽ nhận được:** một lớp Java hoạt động đầy đủ, giải thích từng bước, mẹo xử lý đường dẫn tệp, và bản xem trước kết quả mong đợi. Không cần tài liệu bên ngoài — mọi thứ bạn cần đều có ở đây.

---

## Tạo tài liệu Word trống – Tổng quan từng bước

Điều đầu tiên chúng ta cần là một tệp Word thực sự trống. Aspose.Words làm cho việc này trở nên đơn giản: chỉ cần khởi tạo lớp `Document` bằng hàm khởi tạo mặc định. Điều này cung cấp cho bạn một canvas sạch, tương đương với việc mở Word và nhấn **New → Blank document**.

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Tại sao bắt đầu với tài liệu trống?**  
> Một tài liệu trống đảm bảo không có kiểu dáng hay phần ẩn nào can thiệp vào các hình dạng bạn sẽ thêm sau này. Nó cũng giữ kích thước tệp tối thiểu, rất hữu ích khi bạn tạo hàng chục tệp trong một công việc batch.

---

## Cách tạo nhóm và thêm các hình dạng

Một **group shape** về cơ bản là một container có thể chứa nhiều hình dạng con — giống như một thư mục cho các đối tượng vẽ. Bằng cách nhóm, bạn có thể di chuyển, thay đổi kích thước, hoặc xoay toàn bộ bộ với một lệnh duy nhất.

```java
        // 2️⃣ Insert a group shape 200x200 points
        GroupShape group = builder.insertGroupShape(200.0, 200.0);
```

Phương thức `insertGroupShape` trả về một đối tượng `GroupShape` mà chúng ta sẽ dùng làm cha cho hình chữ nhật và hình ảnh. Kích thước được biểu thị bằng điểm (1 point = 1/72 inch), vì vậy 200 point cho bạn một hộp khoảng 2.78 × 2.78 inch.

> **Mẹo chuyên nghiệp:** Nếu bạn muốn nhóm trong suốt, đặt `group.setFillColor(Color.getWhite());` sau khi tạo.

Bây giờ nhóm đã tồn tại, chúng ta cần chỉ cho builder nơi đặt các hình dạng tiếp theo. Con trỏ của builder phải được đặt bên trong đoạn văn đầu tiên của nhóm.

```java
        // Move the cursor to the first paragraph of the group
        builder.moveTo(group.getFirstParagraph());
```

---

## Chèn hình chữ nhật vào trong nhóm

Hình chữ nhật thường được dùng làm chỗ giữ chỗ cho văn bản hoặc như một dấu hiệu trực quan. Thêm nó như **đứa con đầu tiên** của nhóm đảm bảo nó nằm phía sau bất kỳ hình ảnh nào sau này.

```java
        // 3️⃣ Insert a rectangle (100x50 points) as the first child
        builder.insertShape(ShapeType.RECTANGLE, 100.0, 50.0);
```

Hình chữ nhật thừa hưởng hệ tọa độ của nhóm, vì vậy kích thước 100 × 50 point sẽ được căn giữa mặc định. Bạn có thể tùy chỉnh thêm — thêm viền, đổi màu nền, hoặc áp dụng bóng đổ — bằng cách truy cập đối tượng `Shape` được trả về.

```java
        // Optional styling (commented out for brevity)
        // Shape rect = builder.getCurrentShape();
        // rect.setFillColor(Color.getLightGray());
        // rect.setStrokeColor(Color.getBlack());
```

---

## Thêm hình ảnh vào tài liệu Word – nhúng hình ảnh trong shape

Bây giờ đến phần thú vị: **nhúng hình ảnh trong shape**. Chúng ta sẽ chèn một ảnh JPEG làm đứa con thứ hai của cùng một nhóm. Vì con trỏ vẫn còn trong nhóm, hình ảnh sẽ tự động trở thành một nút con.

```java
        // 4️⃣ Insert an image (make sure the path is correct)
        builder.insertImage("sample.jpg");   // <-- replace with your image path
```

Nếu không tìm thấy tệp hình ảnh, Aspose.Words sẽ ném ra một `FileNotFoundException`. Để tránh điều này, hãy đặt `sample.jpg` trong thư mục làm việc của dự án hoặc sử dụng đường dẫn tuyệt đối.

> **Nếu bạn cần định dạng ảnh khác?**  
> Aspose.Words hỗ trợ PNG, BMP, GIF, TIFF, và thậm chí SVG. Chỉ cần thay đổi phần mở rộng tệp và thư viện sẽ tự xử lý việc chuyển đổi.

---

## Lưu tài liệu và xem kết quả

Cuối cùng, chúng ta ghi tài liệu trong bộ nhớ ra đĩa. Tệp `.docx` kết quả sẽ chứa một trang duy nhất với một shape nhóm chứa cả hình chữ nhật và hình ảnh.

```java
        // 5️⃣ Save the document to verify the output
        doc.save("output.docx");
    }
}
```

Khi bạn mở `output.docx` trong Microsoft Word, bạn sẽ thấy một nhóm 200 × 200 point ở góc trên‑trái. Bên trong nhóm, một hình chữ nhật màu xám nhạt nằm ở trên cùng, và ngay dưới đó là bức ảnh bạn chỉ định, căn chỉnh hoàn hảo.

![Grouped shape example](grouped-shape.png){:alt="Ảnh chụp màn hình của tài liệu Word trống với một shape nhóm chứa hình chữ nhật và một hình ảnh được nhúng"}

---

## Các biến thể phổ biến và xử lý trường hợp biên

| Kịch bản | Cần thay đổi | Lý do quan trọng |
|----------|--------------|-------------------|
| **Kích thước nhóm khác** | Điều chỉnh các tham số của `insertGroupShape(width, height)` | Nhóm lớn hơn có thể chứa các bố cục phức tạp hơn. |
| **Nhiều hình ảnh** | Gọi `builder.insertImage()` liên tục sau khi di chuyển vào đoạn văn của nhóm mỗi lần | Mỗi lần gọi sẽ thêm một nút con mới; bạn cũng có thể định vị chúng bằng `Shape.setLeft()` / `setTop()`. |
| **Đường dẫn ảnh động** | Sử dụng `String.format("images/%s.jpg", imageName)` | Giúp mã tái sử dụng cho việc xử lý batch. |
| **Lưu dưới dạng PDF** | Thay `doc.save("output.pdf")` | Aspose.Words có thể chuyển đổi ngay lập tức, cho phép bạn tạo PDF trực tiếp. |
| **Xoay nhóm** | `group.setRotation(45);` | Hữu ích cho các watermark trang trí hoặc tiêu đề kiểu cách. |

---

## Kết quả mong đợi và cách kiểm tra

Sau khi chạy lớp:

1. `output.docx` xuất hiện trong thư mục dự án.  
2. Mở tệp, bạn sẽ thấy một trang duy nhất với một shape nhóm.  
3. Bên trong nhóm, hình chữ nhật được đặt ở góc trên‑trái, và hình ảnh nằm ngay dưới nó.  
4. Khi chọn nhóm trong Word, cả hai đối tượng con sẽ được đánh dấu, xác nhận chúng thực sự được nhóm lại.

Nếu bất kỳ bước nào không thành công, hãy kiểm tra lại đường dẫn ảnh và đảm bảo JAR Aspose.Words đã có trong classpath của bạn.

---

## Kết luận

Bây giờ bạn đã biết **cách tạo tài liệu Word trống** và làm phong phú nó bằng một shape nhóm chứa hình chữ nhật và một bức ảnh được nhúng. Bằng cách nắm vững **cách tạo nhóm**, **chèn hình chữ nhật**, và **thêm hình ảnh vào tài liệu Word**, bạn có thể xây dựng các mẫu Word tinh vi hoàn toàn bằng mã — không cần chỉnh sửa thủ công.

Sẵn sàng cho thử thách tiếp theo? Hãy thử thêm các hộp văn bản bên trong cùng một nhóm, hoặc thử nghiệm các kiểu shape khác nhau để phù hợp với bộ nhận diện thương hiệu của công ty. Bạn thậm chí có thể tạo một thư viện báo cáo toàn diện, trong đó mỗi tài liệu đều bắt đầu với bố cục này.

Chúc bạn lập trình vui vẻ, và đừng ngại chia sẻ các biến thể của mình trong phần bình luận bên dưới!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}