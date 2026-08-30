---
category: general
date: 2026-07-26
description: Chèn hình chữ nhật trong Java bằng Aspose.Words. Tìm hiểu cách đặt kích
  thước hình, vị trí hình và cách nhóm các hình trong tệp DOCX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- set shape size
- position shape
- how to group shapes
- how to add rectangle
language: vi
lastmod: 2026-07-26
og_description: Chèn hình chữ nhật trong Java để tạo đồ họa DOCX phong phú. Hãy làm
  theo hướng dẫn từng bước này để thiết lập kích thước hình, định vị hình và nhóm
  các hình một cách dễ dàng.
og_image_alt: Screenshot showing a rectangle shape inserted and grouped in a Java‑generated
  Word document
og_title: Chèn Hình Chữ Nhật trong Java – Thành thạo Nhóm và Định vị
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert rectangle shape in Java using Aspose.Words. Learn how to set
    shape size, position shape, and how to group shapes in a DOCX file.
  headline: Insert Rectangle Shape in Java – Group and Position Shapes
  type: TechArticle
tags:
- Aspose.Words
- Java
- Shapes
- DOCX
title: Chèn Hình Chữ Nhật trong Java – Nhóm và Định Vị Các Hình
url: /vi/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Chèn Hình Chữ Nhật trong Java – Nhóm và Định Vị Hình

Bạn đã bao giờ cần **insert rectangle shape** vào một tài liệu Word khi viết mã Java chưa? Bạn không phải là người duy nhất—các nhà phát triển tạo báo cáo, hoá đơn, hoặc mẫu tùy chỉnh luôn gặp vấn đề này. Tin tốt là với một vài dòng mã Aspose.Words for Java, bạn có thể **insert rectangle shape**, **set shape size**, **position shape**, và thậm chí **how to group shapes** để chúng di chuyển như một đơn vị duy nhất.

Trong hướng dẫn này, chúng ta sẽ đi qua toàn bộ quy trình từ tạo tài liệu trống đến lưu một tệp `.docx` chứa hai hình chữ nhật được nhóm gọn gàng lại với nhau. Khi kết thúc, bạn sẽ biết **how to add rectangle** đối tượng, kiểm soát kích thước của chúng, đặt chúng chính xác ở vị trí mong muốn, và gộp chúng thành một nhóm có thể tái sử dụng. Không cần thư viện bên ngoài nào ngoài Aspose.Words, và mã hoạt động với Java 8‑plus.

## Yêu cầu trước

- Java 8 hoặc mới hơn đã được cài đặt (tôi đang dùng JDK 17, nhưng bất kỳ phiên bản nào hỗ trợ Maven đều được)
- Aspose.Words for Java 23.9 hoặc mới hơn – thêm phụ thuộc vào `pom.xml` của bạn hoặc tải JAR về
- Hiểu biết cơ bản về cú pháp Java (nếu bạn có thể viết một phương thức `main`, bạn đã sẵn sàng)
- Một IDE hoặc trình soạn thảo văn bản mà bạn thích (IntelliJ IDEA, Eclipse, VS Code…)

> **Mẹo chuyên gia:** Nếu bạn đang sử dụng Maven, phụ thuộc trông như sau:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Bây giờ chúng ta đã chuẩn bị nền tảng, hãy đi sâu vào mã.

## Chèn Hình Chữ Nhật và Đặt Kích Thước

Điều đầu tiên bạn sẽ làm là tạo một `Document` mới và một `DocumentBuilder`. Builder là “bút” của bạn để vẽ các hình lên trang. Dưới đây chúng tôi **insert rectangle shape** và ngay lập tức **set shape size** thành 100 × 80 điểm.

```java
import com.aspose.words.*;

public class GroupedRectanglesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder to add content
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape(400, 200);
        // The group itself is 400×200 points – adjust as needed

        // ---------- First rectangle ----------
        // Insert rectangle shape
        Shape rectangle1 = new Shape(document, ShapeType.RECTANGLE);
        // Set shape size
        rectangle1.setWidth(100);
        rectangle1.setHeight(80);
        // Position shape inside the group
        rectangle1.setLeft(20);   // 20 points from the left edge of the group
        rectangle1.setTop(30);    // 30 points from the top edge of the group
        // Add the rectangle to the group
        group.appendChild(rectangle1);
```

Lưu ý cách các lời gọi `setWidth`/`setHeight` **set shape size** bằng điểm (1 pt ≈ 1/72 inch). Bạn cũng có thể dùng `setSize` nếu muốn một phương thức duy nhất, nhưng các lời gọi rõ ràng giúp ý định trở nên trong suốt.

## Định Vị Hình Trên Trang

Sau khi có hình chữ nhật đầu tiên, chúng ta cần **position shape** hình thứ hai để nó không chồng lên hình đầu. Việc định vị hoạt động tương tự: bạn đặt các thuộc tính `Left` và `Top` tương đối với gốc của nhóm.

```java
        // ---------- Second rectangle ----------
        Shape rectangle2 = new Shape(document, ShapeType.RECTANGLE);
        rectangle2.setWidth(120);
        rectangle2.setHeight(60);
        // Position this rectangle a bit farther to the right and lower down
        rectangle2.setLeft(150);
        rectangle2.setTop(50);
        group.appendChild(rectangle2);
```

Nếu bạn thắc mắc tại sao chúng tôi dùng `setLeft` thay vì `setX`, đó là vì Aspose.Words áp dụng hệ tọa độ Windows GDI cổ điển—`Left` là độ lệch ngang, `Top` là độ lệch dọc. Thay đổi các giá trị này cho phép bạn tinh chỉnh bố cục mà không cần can thiệp vào bảng hay đoạn văn.

## Cách Nhóm Các Hình

Bạn có thể hỏi, “Tại sao phải tạo nhóm cả?” Nhóm hợp lý khi bạn muốn các hình di chuyển cùng nhau, quay thành một khối, hoặc chia sẻ cùng một kiểu. Trong đoạn mã trên, chúng tôi đã tạo một `GroupShape` bằng `builder.insertGroupShape`. Đối tượng này thực chất là một container—nghĩ như một thư mục chứa các tệp hình khác.

> **Tại sao điều này quan trọng:** Nếu sau này bạn quyết định thêm chú thích hoặc quay toàn bộ sơ đồ, bạn chỉ cần chỉnh sửa nhóm, không phải từng hình chữ nhật riêng lẻ.

## Cách Thêm Hình Chữ Nhật Vào Nhóm

Hành động **how to add rectangle** vào nhóm đơn giản chỉ là gọi `group.appendChild(rectangle)`. Bên trong, Aspose.Words cập nhật bộ sưu tập nội bộ của nhóm và tự động tính lại hộp bao để nhóm vẫn phù hợp với chiều rộng và chiều cao đã khai báo.

```java
        // At this point the group already contains both rectangles.
        // You can also set the group’s border or fill if you like.
        group.getShapeStyle().setLineColor(Color.BLACK);
        group.getShapeStyle().setFillColor(Color.LIGHTGRAY);
```

Bạn có thể thử nghiệm với các `ShapeType` khác—`ShapeType.ELLIPSE`, `ShapeType.TRIANGLE`, v.v.—và mẫu `appendChild` vẫn hoạt động.

## Lưu Tài Liệu

Cuối cùng, chúng ta ghi tài liệu ra đĩa. Đường dẫn có thể là tuyệt đối hoặc tương đối; chỉ cần chắc chắn thư mục tồn tại.

```java
        // Step 5: Save the document containing the grouped shapes
        String outPath = "output/GroupShape.docx";
        document.save(outPath);
        System.out.println("Document saved to: " + outPath);
    }
}
```

Khi bạn mở `GroupShape.docx` trong Microsoft Word, bạn sẽ thấy hai hình chữ nhật cạnh nhau, cả hai đều được khóa bên trong một hộp màu xám nhạt. Chọn hộp màu xám sẽ làm nổi bật cả hai hình chữ nhật cùng lúc—chứng minh rằng **how to group shapes** thực sự hoạt động.

![Các hình chữ nhật được nhóm trong tài liệu Word](placeholder-image.png){: .center-image alt="Ví dụ chèn hình chữ nhật hiển thị hai hình chữ nhật được nhóm trong tệp DOCX được tạo bằng Java"}

*Văn bản thay thế hình ảnh (SEO):* **insert rectangle shape example showing two rectangles grouped in a Java‑generated DOCX file**.

## Kết Quả Mong Đợi

- Một tệp `GroupShape.docx` nằm trong thư mục `output`.
- Trong tài liệu: một nhóm 400 × 200 pt chứa hai hình chữ nhật (100 × 80 pt và 120 × 60 pt) được đặt tại (20, 30) và (150, 50) tương ứng.
- Nhóm có viền đen mỏng và nền màu xám nhạt, làm cho việc nhóm trở nên rõ ràng về mặt hình ảnh.

Mở tệp và thử kéo hộp màu xám—cả hai hình chữ nhật nên di chuyển cùng nhau. Nếu không, hãy kiểm tra lại rằng bạn đã gọi `group.appendChild` cho mỗi hình.

## Những Sai Lầm Thường Gặp & Các Trường Hợp Đặc Biệt

| Vấn đề | Nguyên nhân | Cách khắc phục |
|-------|------------|----------------|
| **Rectangles appear outside the page** | Giá trị `Left`/`Top` vượt quá kích thước của nhóm | Tăng kích thước nhóm (`insertGroupShape(width, height)`) hoặc giảm độ lệch |
| **Group disappears after saving** | `Width`/`Height` của nhóm được đặt bằng 0 | Cung cấp kích thước khác 0 khi gọi `insertGroupShape` |
| **Shape colors look wrong** | Màu nền mặc định trong suốt; Word có thể hiển thị nó thành trắng | Đặt rõ ràng `setFillColor` hoặc sử dụng `ShapeStyle` |
| **Exception `ArgumentOutOfRangeException`** | Sử dụng tọa độ âm | Giữ `Left` và `Top` không âm |

Giải quyết những vấn đề này sớm sẽ giúp bạn tránh những cơn đau đầu “tại sao hình của tôi biến mất?” mà nhiều người mới gặp phải.

## Tóm Tắt & Các Bước Tiếp Theo

Chúng ta đã bao quát toàn bộ vòng đời của **insert rectangle shape** trong Java: tạo tài liệu, **set shape size**, **position shape**, **how to group shapes**, và **how to add rectangle** vào nhóm đó. Ví dụ hoàn chỉnh, có thể chạy được nằm trong khối mã ở trên, và bạn có thể dán trực tiếp vào dự án Maven để xem kết quả.

Tiếp theo là gì? Hãy thử nghiệm với:

- Thêm văn bản vào mỗi hình chữ nhật qua

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng dựa trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}