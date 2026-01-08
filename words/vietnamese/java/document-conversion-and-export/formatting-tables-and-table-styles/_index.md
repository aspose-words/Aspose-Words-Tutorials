---
date: 2025-11-28
description: Tìm hiểu cách thay đổi viền ô và định dạng bảng bằng Aspose.Words cho
  Java. Hướng dẫn từng bước này bao gồm việc thiết lập viền, áp dụng kiểu cột đầu
  tiên, tự động điều chỉnh nội dung bảng và áp dụng các kiểu bảng.
linktitle: How to Change Cell Borders in Tables – Aspose.Words for Java
second_title: Aspose.Words Java Document Processing API
title: Cách thay đổi viền ô trong bảng – Aspose.Words cho Java
url: /vi/java/document-conversion-and-export/formatting-tables-and-table-styles/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cách Thay Đổi Viền Ô Trong Bảng – Aspose.Words cho Java

## Giới thiệu

Khi nói đến việc định dạng tài liệu, bảng đóng một vai trò quan trọng, và **biết cách thay đổi viền ô** là cần thiết để tạo ra bố cục rõ ràng, chuyên nghiệp. Nếu bạn đang phát triển với Java và Aspose.Words, bạn đã có một bộ công cụ mạnh mẽ trong tay. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn quy trình đầy đủ để định dạng bảng, thay đổi viền ô, áp dụng *kiểu cột đầu tiên*, và sử dụng *tự động điều chỉnh nội dung bảng* để tài liệu của bạn trông hoàn hảo.

## Câu trả lời nhanh
- **Lớp chính để tạo bảng là gì?** `DocumentBuilder` tạo bảng và ô một cách lập trình.  
- **Làm thế nào để thay đổi độ dày viền của một ô duy nhất?** Sử dụng `builder.getCellFormat().getBorders().getLeft().setLineWidth(value)`.  
- **Tôi có thể áp dụng kiểu bảng đã định nghĩa trước không?** Có – gọi `table.setStyleIdentifier(StyleIdentifier.YOUR_STYLE)`.  
- **Phương thức nào tự động điều chỉnh bảng theo nội dung?** `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)`.  
- **Tôi có cần giấy phép cho môi trường sản xuất không?** Cần một giấy phép Aspose.Words hợp lệ cho việc sử dụng không phải thử nghiệm.

## “Cách thay đổi viền ô” trong Aspose.Words là gì?

Thay đổi viền ô có nghĩa là tùy chỉnh các đường viền trực quan tách các ô—màu sắc, độ rộng và kiểu đường. Aspose.Words cung cấp một API phong phú cho phép bạn điều chỉnh các thuộc tính này ở mức bảng, hàng hoặc ô riêng lẻ, mang lại khả năng kiểm soát chi tiết về giao diện của tài liệu.

## Tại sao nên sử dụng Aspose.Words cho Java để tạo kiểu bảng?

- **Giao diện nhất quán trên các nền tảng** – cùng một đoạn mã tạo kiểu hoạt động trên Windows, Linux và macOS.  
- **Không phụ thuộc vào Microsoft Word** – tạo hoặc chỉnh sửa tài liệu phía máy chủ.  
- **Thư viện kiểu phong phú** – các kiểu bảng tích hợp (ví dụ, *kiểu cột đầu tiên*) và khả năng tự động điều chỉnh đầy đủ.  

## Yêu cầu trước

1. **Java Development Kit (JDK) 8+** – đảm bảo `java` có trong PATH.  
2. **IDE** – IntelliJ IDEA, Eclipse, hoặc bất kỳ trình soạn thảo nào bạn thích.  
3. **Aspose.Words cho Java** – tải JAR mới nhất từ [trang chính thức](https://releases.aspose.com/words/java/).  
4. **Kiến thức Java cơ bản** – bạn nên thoải mái tạo dự án Maven/Gradle và thêm JAR bên ngoài.  

## Nhập Gói

Để bắt đầu làm việc với bảng, bạn cần các lớp cốt lõi của Aspose.Words:

```java
import com.aspose.words.*;
```

Lệnh import duy nhất này cho phép bạn truy cập vào `Document`, `DocumentBuilder`, `Table`, `StyleIdentifier`, và nhiều tiện ích khác.

## Cách Thay Đổi Viền Ô

Dưới đây chúng ta sẽ tạo một bảng đơn giản, thay đổi viền tổng thể của nó, sau đó tùy chỉnh các ô riêng lẻ.

### Bước 1: Tải Tài Liệu Mới

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Bước 2: Tạo Bảng và Đặt Viền Toàn Cục

```java
Table table = builder.startTable();
builder.insertCell();

// Set the borders for the entire table.
table.setBorders(LineStyle.SINGLE, 2.0, Color.BLACK);
        
// Set the cell shading for this cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.RED);
builder.writeln("Cell #1");

builder.insertCell();
        
// Specify a different cell shading for the second cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.GREEN);
builder.writeln("Cell #2");

builder.endRow();
```

### Bước 3: Thay Đổi Viền của Một Ô Đơn Lẻ

```java
// Clear the cell formatting from previous operations.
builder.getCellFormat().clearFormatting();

builder.insertCell();

// Create larger borders for the first cell of this row.
builder.getCellFormat().getBorders().getLeft().setLineWidth(4.0);
builder.getCellFormat().getBorders().getRight().setLineWidth(4.0);
builder.getCellFormat().getBorders().getTop().setLineWidth(4.0);
builder.getCellFormat().getBorders().getBottom().setLineWidth(4.0);
builder.writeln("Cell #3");

builder.insertCell();
builder.getCellFormat().clearFormatting();
builder.writeln("Cell #4");
        
doc.save("FormatTableAndCellWithDifferentBorders.docx");
```

#### Những gì mã thực hiện
- **Viền toàn cục** – `table.setBorders` đặt cho toàn bộ bảng một đường đen dày 2 điểm.  
- **Tô màu ô** – Minh họa cách tô màu các ô riêng lẻ (đỏ & xanh lá).  
- **Viền ô tùy chỉnh** – Ô thứ ba nhận viền 4 điểm ở mọi phía, làm nó nổi bật.

## Áp Dụng Kiểu Bảng (bao gồm Kiểu Cột Đầu Tiên)

Kiểu bảng cho phép bạn áp dụng giao diện nhất quán chỉ bằng một lệnh. Chúng tôi cũng sẽ chỉ cách bật *kiểu cột đầu tiên* và tự động điều chỉnh bảng theo nội dung.

### Bước 4: Tạo Tài Liệu Mới cho Việc Định Dạng

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Table table = builder.startTable();
        
// We must insert at least one row first before setting any table formatting.
builder.insertCell();
```

### Bước 5: Áp Dụng Kiểu Định Nghĩa Trước và Bật Định Dạng Cột Đầu Tiên

```java
// Set the table style based on a unique style identifier.
table.setStyleIdentifier(StyleIdentifier.MEDIUM_SHADING_1_ACCENT_1);
        
// Apply which features should be formatted by the style.
table.setStyleOptions(TableStyleOptions.FIRST_COLUMN | TableStyleOptions.ROW_BANDS | TableStyleOptions.FIRST_ROW);

// Auto‑fit the table so columns shrink or expand to fit the content.
table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS);
```

### Bước 6: Điền Dữ Liệu Vào Bảng

```java
builder.writeln("Item");
builder.getCellFormat().setRightPadding(40.0);
builder.insertCell();
builder.writeln("Quantity (kg)");
builder.endRow();

builder.insertCell();
builder.writeln("Apples");
builder.insertCell();
builder.writeln("20");
builder.endRow();

builder.insertCell();
builder.writeln("Bananas");
builder.insertCell();
builder.writeln("40");
builder.endRow();

builder.insertCell();
builder.writeln("Carrots");
builder.insertCell();
builder.writeln("50");
builder.endRow();

doc.save("BuildTableWithStyle.docx");
```

#### Tại sao điều này quan trọng
- **Định danh kiểu** – `MEDIUM_SHADING_1_ACCENT_1` mang lại cho bảng giao diện sạch sẽ, có bóng nhạt.  
- **Kiểu cột đầu tiên** – Tô sáng cột đầu tiên cải thiện khả năng đọc, đặc biệt trong các báo cáo.  
- **Dải hàng** – Màu sắc xen kẽ các hàng giúp các bảng lớn dễ nhìn hơn.  
- **Tự động điều chỉnh** – Đảm bảo chiều rộng bảng thích ứng với nội dung, ngăn văn bản bị cắt.

## Các Vấn Đề Thường Gặp & Khắc Phục

| Vấn đề | Nguyên nhân thường gặp | Cách khắc phục nhanh |
|--------|------------------------|----------------------|
| Viền không hiển thị | Sử dụng `clearFormatting()` sau khi đã đặt viền | Đặt viền **sau** khi xóa định dạng, hoặc áp dụng lại chúng. |
| Bóng nền bị bỏ qua trên ô đã hợp nhất | Bóng nền được áp dụng trước khi hợp nhất | Áp dụng bóng nền **sau** khi hợp nhất các ô. |
| Độ rộng bảng vượt lề trang | Không áp dụng tự động điều chỉnh | Gọi `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` hoặc đặt chiều rộng cố định. |
| Kiểu không được áp dụng | Giá trị `StyleIdentifier` sai | Kiểm tra định danh tồn tại trong phiên bản Aspose.Words bạn đang dùng. |

## Câu Hỏi Thường Gặp

**Q: Tôi có thể sử dụng các kiểu bảng tùy chỉnh không có trong các tùy chọn mặc định không?**  
A: Có, bạn có thể tạo và áp dụng các kiểu tùy chỉnh bằng lập trình. Xem [tài liệu Aspose.Words](https://reference.aspose.com/words/java/) để biết chi tiết.

**Q: Làm thế nào tôi có thể áp dụng định dạng có điều kiện cho các ô?**  
A: Sử dụng logic Java tiêu chuẩn để kiểm tra giá trị ô, sau đó gọi các phương thức định dạng phù hợp (ví dụ, thay đổi màu nền nếu giá trị vượt quá ngưỡng).

**Q: Có thể định dạng các ô đã hợp nhất giống như các ô thường không?**  
A: Chắc chắn. Sau khi hợp nhất các ô, áp dụng bóng nền hoặc viền bằng cùng các API `CellFormat`.

**Q: Nếu tôi cần bảng thay đổi kích thước động dựa trên đầu vào của người dùng thì sao?**  
A: Điều chỉnh độ rộng cột hoặc gọi lại `autoFit` sau khi chèn dữ liệu mới để tính lại bố cục.

**Q: Tôi có thể tìm thêm ví dụ về định dạng bảng ở đâu?**  
A: [Tài liệu API Aspose.Words chính thức](https://reference.aspose.com/words/java/) chứa một bộ mẫu đầy đủ.

## Kết luận

Bây giờ bạn đã có một bộ công cụ hoàn chỉnh để **thay đổi viền ô**, áp dụng *kiểu cột đầu tiên*, và **tự động điều chỉnh nội dung bảng** bằng Aspose.Words cho Java. Khi nắm vững các kỹ thuật này, bạn có thể tạo ra các tài liệu vừa giàu dữ liệu vừa hấp dẫn về mặt hình ảnh—hoàn hảo cho báo cáo, hoá đơn và bất kỳ đầu ra kinh doanh quan trọng nào.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Cập nhật lần cuối:** 2025-11-28  
**Đã kiểm tra với:** Aspose.Words cho Java 24.12 (phiên bản mới nhất tại thời điểm viết)  
**Tác giả:** Aspose