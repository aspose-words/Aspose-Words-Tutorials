---
date: 2026-01-24
description: Học cách hợp nhất dữ liệu XML với Aspose.Words cho Java, tự động tạo
  tài liệu Java và sử dụng cú pháp Mustache cho tài liệu động.
linktitle: Using XML Data
second_title: Aspose.Words Java Document Processing API
title: Cách hợp nhất XML trong Aspose.Words cho Java
url: /vi/java/document-manipulation/using-xml-data/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cách hợp nhất XML trong Aspose.Words cho Java

Trong hướng dẫn chi tiết này, bạn sẽ khám phá **cách hợp nhất XML** bằng Aspose.Words cho Java. Chúng tôi sẽ hướng dẫn qua các kịch bản mail‑merge cơ bản và lồng nhau, chỉ cho bạn cách **sử dụng cú pháp Mustache**, và giải thích cách **tự động tạo tài liệu kiểu Java**. Khi kết thúc, bạn sẽ có thể tạo các tài liệu Word cá nhân hoá trực tiếp từ nguồn XML chỉ với vài dòng mã.

## Trả lời nhanh
- **Lớp chính cho mail merge là gì?** `Document` và thuộc tính `MailMerge` của nó.  
- **Tôi có thể hợp nhất các bảng XML lồng nhau không?** Có – sử dụng `executeWithRegions` cho dữ liệu phân cấp.  
- **Cú pháp Mustache có được hỗ trợ không?** Kích hoạt bằng `setUseNonMergeFields(true)`.  
- **Tôi có cần giấy phép cho môi trường sản xuất không?** Cần một giấy phép thương mại Aspose.Words.  
- **Phiên bản Java nào tương thích?** Java 8+ và các phiên bản sau đều được hỗ trợ đầy đủ.

## Mail Merge XML trong Aspose.Words là gì?
Mail merge XML cho phép bạn ràng buộc các bộ dữ liệu dựa trên XML vào các placeholder trong mẫu Word. Engine sẽ thay thế mỗi placeholder bằng giá trị của nút XML tương ứng, tạo ra tài liệu hoàn chỉnh mà không cần chỉnh sửa thủ công.

## Tại sao nên sử dụng Aspose.Words cho việc tạo tài liệu dựa trên XML?
- **Tự động tạo tài liệu Java** mà không phụ thuộc vào Microsoft Office.  
- **Hỗ trợ cấu trúc phân cấp phức tạp** – bảng lồng nhau, phần lặp lại, và nội dung có điều kiện.  
- **Cú pháp Mustache** cung cấp các placeholder linh hoạt, không phải là trường merge truyền thống, cho việc tạo mẫu nâng cao.  
- **Đa nền tảng** – hoạt động trên Windows, Linux và macOS.

## Yêu cầu trước

Trước khi bắt đầu, hãy đảm bảo bạn đã có:

- [Aspose.Words for Java](https://products.aspose.com/words/java/) đã được cài đặt (phiên bản mới nhất).  
- Các tệp XML mẫu cho khách hàng, đơn hàng và nhà cung cấp (bài hướng dẫn sử dụng `Mail merge data - Customers.xml`, `Orders.xml`, và `Vendors.xml`).  
- Các tài liệu mẫu Word chứa các trường merge (ví dụ: `Registration complete.docx`, `Invoice.docx`, `Vendor.docx`).  

## Cách hợp nhất XML – Mail Merge cơ bản

Mail merge cơ bản lấy một bảng XML duy nhất vào mẫu Word. Thực hiện các bước sau:

1. Tải tệp XML vào một `DataSet`.  
2. Mở tài liệu Word đích.  
3. Thực hiện merge bằng tên bảng.  
4. Lưu tài liệu đã hợp nhất.

```java
DataSet customersDs = new DataSet();
customersDs.readXml("Your Directory Path" + "Mail merge data - Customers.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Registration complete.docx");
doc.getMailMerge().execute(customersDs.getTables().get("Customer"));
doc.save("Your Directory Path" + "BasicMailMerge.docx");
```

**Mẹo:** Giữ cấu trúc XML phẳng cho các merge đơn giản – mỗi bảng nên ánh xạ trực tiếp tới một tập các trường merge.

## Cách hợp nhất XML – Mail Merge lồng nhau

Khi XML của bạn chứa quan hệ cha‑con (ví dụ: đơn hàng có các mục hàng), bạn cần một merge lồng nhau. Phương thức `executeWithRegions` sẽ xử lý mỗi vùng một cách đệ quy.

1. Tải XML phân cấp vào một `DataSet`.  
2. Tắt việc cắt bỏ khoảng trắng nếu bạn cần định dạng chính xác.  
3. Gọi `executeWithRegions` để xử lý tất cả các bảng lồng nhau.  
4. Lưu kết quả.

```java
DataSet pizzaDs = new DataSet();
pizzaDs.readXml("Your Directory Path" + "Mail merge data - Orders.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Invoice.docx");
doc.getMailMerge().setTrimWhitespaces(false);
doc.getMailMerge().executeWithRegions(pizzaDs);
doc.save("Your Directory Path" + "NestedMailMerge.docx");
```

**Những lỗi thường gặp:** Quên thiết lập `setTrimWhitespaces(false)` có thể gây ra các khoảng trắng không mong muốn trong tài liệu cuối cùng, đặc biệt đối với các trường tiền tệ hoặc số.

## Cách sử dụng cú pháp Mustache với DataSet

Cú pháp Mustache cho phép bạn chèn các placeholder không phải là trường merge (ví dụ: `{{CustomerName}}`) vào mẫu. Kích hoạt nó và chạy merge dựa trên vùng.

1. Tải XML nhà cung cấp.  
2. Bật hỗ trợ Mustache bằng `setUseNonMergeFields(true)`.  
3. Thực hiện merge với các vùng.  
4. Lưu kết quả.

```java
DataSet ds = new DataSet();
ds.readXml("Your Directory Path" + "Mail merge data - Vendors.xml");
Document doc = new Document("Your Directory Path" + "Mail merge destinations - Vendor.docx");
doc.getMailMerge().setUseNonMergeFields(true);
doc.getMailMerge().executeWithRegions(ds);
doc.save("Your Directory Path" + "MustacheSyntaxUsingDataSet.docx");
```

**Tại sao nên dùng Mustache?** Nó cung cấp một cách tiếp cận sạch sẽ, không phụ thuộc ngôn ngữ để tham chiếu dữ liệu, giúp mẫu của bạn dễ đọc và bảo trì hơn, đặc biệt khi **tạo tài liệu dựa trên XML** trong các quy trình làm việc.

## Các vấn đề thường gặp và giải pháp

| Vấn đề | Giải pháp |
|-------|----------|
| Các nút XML không khớp với trường merge | Kiểm tra lại tên phần tử XML phải giống hệt tên trường merge (phân biệt chữ hoa‑thường). |
| Khoảng trắng xuất hiện quanh giá trị đã merge | Sử dụng `doc.getMailMerge().setTrimWhitespaces(false)` để giữ nguyên khoảng trắng gốc. |
| Bảng lồng nhau bị bỏ qua | Đảm bảo vùng bảng cha được định nghĩa trong mẫu (ví dụ: `{{#Orders}} … {{/Orders}}`). |
| Placeholder Mustache không được thay thế | Gọi `setUseNonMergeFields(true)` trước khi thực hiện merge. |

## Câu hỏi thường gặp

### Làm sao chuẩn bị dữ liệu XML cho mail merge?

Đảm bảo XML của bạn có cấu trúc dạng bảng, trong đó mỗi phần tử `<TableName>` chứa các hàng (`<Row>`) và cột tương ứng với các trường merge trong mẫu Word.

### Tôi có thể tùy chỉnh hành vi cắt bỏ khoảng trắng pháp Mustache là gì và khiName}}`) cho phép các placeholder linh hoạt không bị giới hạn bởi các trường merge truyền thống. Kích hoạt bằngsetUseNonMergeFields(true)` khi bạn muốn mẫu sạch hơn hoặc muốn tách logic dữ liệu ra khỏi mã trường Word.

### Làm sao tự động tạo tài liệu cho các dự án Java bằng cách này?

Tích hợp các đoạn mã trên vào lớp dịch vụ của bạn, đọc XML từ cơ sở dữ liệu hoặc API, và gọi routine merge mỗi khi cần tạo tài liệu mới (ví dụ: tạo hoá, hợp đồng).

### Có cần giấy phép thương mại để sử dụng trong môi trường sản xuất không?

Có, Aspose.Words yêu cầu giấy phép hợp lệ cho các triển khai sản xuất. Một giấy phép tạm thời miễn phí có sẵn cho mục đích đánh giá.

---

**Cập nhật lần cuối:** 2026-01-24  
**Được kiểm thử với:** Aspose.Words for Java (phiên bản mới nhất)  
**Tác giả:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}