---
"date": "2025-03-28"
"description": "Tìm hiểu cách thành thạo việc hợp nhất ô theo chiều dọc và chiều ngang trong bảng bằng Aspose.Words cho Java. Hướng dẫn này bao gồm thiết lập, triển khai và ứng dụng thực tế."
"title": "Làm chủ việc hợp nhất ô trong bảng với Aspose.Words Java&#58; Kỹ thuật theo chiều dọc và chiều ngang"
"url": "/vi/java/tables-lists/aspose-words-java-cell-merging-tables/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# Làm chủ việc hợp nhất ô theo chiều dọc và chiều ngang trong bảng với Aspose.Words Java

## Giới thiệu
Việc thao tác định dạng ô bảng là điều cần thiết trong tự động hóa tài liệu để nâng cao khả năng trình bày dữ liệu. Cho dù tạo hóa đơn hay báo cáo, việc hợp nhất các ô đều cải thiện khả năng đọc và tính thẩm mỹ. Kiểm soát việc hợp nhất theo chiều dọc và chiều ngang có thể là một thách thức.

Aspose.Words for Java đơn giản hóa các tác vụ này bằng API mạnh mẽ, cho phép tạo các tài liệu trông chuyên nghiệp một cách dễ dàng. Hướng dẫn này sẽ hướng dẫn bạn cách làm chủ việc hợp nhất ô bằng Aspose.Words trong Java.

### Những gì bạn sẽ học được:
- Hợp nhất các ô theo chiều dọc và chiều ngang bằng cách sử dụng Aspose.Words Java
- Thiết lập môi trường của bạn với các phụ thuộc Maven hoặc Gradle
- Triển khai các đoạn mã thực tế
- Xử lý sự cố thường gặp

Trước tiên, hãy đảm bảo bạn có mọi thứ cần thiết để thực hiện theo.

## Điều kiện tiên quyết
Trước khi bắt đầu hợp nhất ô, hãy đảm bảo bạn có các công cụ và kiến thức cần thiết:

### Thư viện và phụ thuộc cần thiết:
1. **Aspose.Words cho Java**: Thư viện chính để thao tác các tài liệu Word theo chương trình.
2. **JUnit 5 (TestNG)**: Để chạy các trường hợp thử nghiệm như được minh họa trong đoạn mã.

### Yêu cầu thiết lập môi trường:
- Bộ công cụ phát triển Java (JDK) phiên bản 8 trở lên đang hoạt động
- Một Môi trường phát triển tích hợp (IDE) như IntelliJ IDEA, Eclipse hoặc NetBeans

### Điều kiện tiên quyết về kiến thức:
- Hiểu biết cơ bản về lập trình Java
- Quen thuộc với các công cụ xây dựng Maven hoặc Gradle để quản lý sự phụ thuộc

## Thiết lập Aspose.Words
Để bắt đầu hợp nhất các ô, hãy thiết lập Aspose.Words trong dự án của bạn.

### Thêm sự phụ thuộc:
**Chuyên gia:**
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Cấp độ:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Mua giấy phép:
Aspose.Words for Java hoạt động theo giấy phép thương mại, nhưng bạn có thể bắt đầu bằng bản dùng thử miễn phí để khám phá các khả năng của nó:
1. **Dùng thử miễn phí**: Tải xuống thư viện Aspose.Words từ [trang web chính thức](https://releases.aspose.com/words/java/) và bắt đầu sử dụng mà không có bất kỳ hạn chế nào trong 30 ngày.
2. **Giấy phép tạm thời**: Xin giấy phép tạm thời bằng cách truy cập [Trang cấp phép của Aspose](https://purchase.aspose.com/temporary-license/) nếu bạn muốn thử nghiệm sau thời gian dùng thử.
3. **Mua**:Để sử dụng lâu dài, hãy cân nhắc mua từ [trang mua hàng](https://purchase.aspose.com/buy).

### Khởi tạo cơ bản:
Để khởi động dự án của bạn, hãy khởi tạo `Document` Và `DocumentBuilder` các lớp như sau:
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
Thao tác này sẽ thiết lập một tài liệu trống để xây dựng bảng.

## Hướng dẫn thực hiện
Chúng ta hãy chia nhỏ quá trình hợp nhất các ô trong bảng thành các bước dễ quản lý, tập trung vào cả hợp nhất theo chiều dọc và chiều ngang.

### Hợp nhất ô theo chiều dọc

#### Tổng quan:
Gộp ô theo chiều dọc kết hợp nhiều hàng vào trong một cột, lý tưởng để tạo tiêu đề hoặc nhóm thông tin liên quan.

#### Thực hiện từng bước:
**1. Tạo Tài liệu và Trình xây dựng:**
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

**2. Chèn ô bằng cách trộn theo chiều dọc:**

- **Ô đầu tiên (Bắt đầu hợp nhất):** Đặt làm điểm bắt đầu của quá trình hợp nhất theo chiều dọc.
  ```java
  builder.insertCell();
  builder.getCellFormat().setVerticalMerge(CellMerge.FIRST); // Đánh dấu ô này là điểm bắt đầu để hợp nhất.
  builder.write("Text in merged cells.");
  ```

- **Ô thứ hai (Không hợp nhất):**
  ```java
  builder.insertCell();
  builder.getCellFormat().setVerticalMerge(CellMerge.NONE); // Không áp dụng hợp nhất ở đây.
  builder.write("Text in unmerged cell.");
  builder.endRow(); // Kết thúc hàng hiện tại.
  ```

- **Ô thứ ba (Tiếp tục hợp nhất):** Hợp nhất với ô đầu tiên theo chiều dọc.
  ```java
  builder.insertCell();
  builder.getCellFormat().setVerticalMerge(CellMerge.PREVIOUS); // Tiếp tục hợp nhất theo chiều dọc từ ô trước đó.
  builder.endRow(); // Hoàn thành hàng thứ hai.
  ```

**3. Lưu tài liệu:**
```java
doc.save("VerticalMergeOutput.docx");
```

### Hợp nhất ô theo chiều ngang

#### Tổng quan:
Gộp theo chiều ngang kết hợp các ô trên một hàng duy nhất, lý tưởng để tạo tiêu đề toàn diện hoặc thông tin bao quát.

#### Thực hiện từng bước:
**1. Tạo Tài liệu và Trình xây dựng:**
Sử dụng lại mã khởi tạo giống như trước.

**2. Chèn ô bằng cách trộn theo chiều ngang:**

- **Ô đầu tiên (Bắt đầu hợp nhất):**
  ```java
  builder.insertCell();
  builder.getCellFormat().setHorizontalMerge(CellMerge.FIRST); // Bắt đầu hợp nhất theo chiều ngang.
  builder.write("Text in merged cells.");
  ```

- **Ô thứ hai (Tiếp tục hợp nhất):**
  ```java
  builder.insertCell();
  builder.getCellFormat().setHorizontalMerge(CellMerge.PREVIOUS); // Tiếp tục theo chiều ngang từ ô đầu tiên.
  builder.endRow(); // Kết thúc hàng hiện tại, hoàn tất việc hợp nhất theo chiều ngang.
  ```

**3. Lưu tài liệu:**
```java
doc.save("HorizontalMergeOutput.docx");
```

### Đệm ô

#### Tổng quan:
Thêm phần đệm vào ô giúp tăng khả năng đọc bằng cách tạo khoảng trắng giữa văn bản và đường viền.

#### Thực hiện từng bước:
**1. Đặt khoảng đệm trên ô:**
```java
builder.getCellFormat().setPaddings(5.0, 10.0, 40.0, 50.0); // Đệm trên, phải, dưới, trái theo điểm.
```

**2. Chèn một ô có đệm:**
```java
builder.startTable();
builder.insertCell();
builder.write("Lorem ipsum dolor sit amet...");
builder.endRow();
builder.endTable();
doc.save("PaddingOutput.docx");
```

## Ứng dụng thực tế
Hiểu cách hợp nhất các ô và thêm phần đệm có thể cải thiện tài liệu theo nhiều cách khác nhau:
1. **Tạo hóa đơn**: Sử dụng kết hợp theo chiều dọc cho các mô tả mục trải dài trên nhiều hàng, giúp cải thiện độ rõ ràng.
2. **Tạo báo cáo**: Việc hợp nhất theo chiều ngang rất phù hợp để thống nhất các tiêu đề phần trên các bảng.
3. **Mẫu sơ yếu lý lịch**: Thêm phần đệm để đảm bảo văn bản trong các phần sơ yếu lý lịch dễ nhìn.

## Cân nhắc về hiệu suất
Khi làm việc với các tài liệu lớn hoặc nhiều thao tác trên bảng:
- **Tối ưu hóa việc tải tài liệu:** Sử dụng `Document` xây dựng hiệu quả bằng cách chỉ tải các phần cần thiết của tài liệu nếu có thể.
- **Xử lý hàng loạt:** Kết hợp nhiều thay đổi định dạng ô thành một thao tác duy nhất để giảm thiểu chi phí xử lý.

## Phần kết luận
Việc hợp nhất các ô trong bảng bằng Aspose.Words for Java giúp tăng cường các dự án tự động hóa tài liệu. Bằng cách thành thạo việc hợp nhất theo chiều dọc và chiều ngang, cùng với việc thêm phần đệm, bạn được trang bị để tạo ra các tài liệu hoàn thiện.

### Các bước tiếp theo:
- Thử nghiệm thêm với các chức năng của Aspose.Words.
- Khám phá các tính năng bổ sung như kiểu bảng hoặc chèn hình ảnh để làm phong phú thêm tài liệu của bạn.

## Phần Câu hỏi thường gặp
**Câu hỏi 1: Tôi có thể gộp nhiều hơn hai ô theo chiều dọc không?**
A1: Có, tiếp tục cài đặt `CellMerge.PREVIOUS` cho mỗi ô bạn muốn đưa vào phần hợp nhất theo chiều dọc.

**Câu hỏi 2: Tôi phải xử lý các ô đã hợp nhất như thế nào khi chuyển đổi tài liệu sang PDF?**
A2: Aspose.Words xử lý định dạng nhất quán trên các định dạng. Đảm bảo các lệnh ghép của bạn được thiết lập chính xác trước khi chuyển đổi.

**Câu hỏi 3: Có giới hạn nào khi kết hợp các ô có hình ảnh hoặc nội dung phức tạp không?**
A3: Văn bản cơ bản hoạt động liền mạch, nhưng hãy đảm bảo rằng bất kỳ thành phần phức tạp nào cũng giữ nguyên định dạng trong quá trình hợp nhất.

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}