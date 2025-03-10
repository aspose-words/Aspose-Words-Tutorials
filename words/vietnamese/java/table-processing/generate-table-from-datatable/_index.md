---
title: Tạo bảng từ Datatable
linktitle: Tạo bảng từ Datatable
second_title: API xử lý tài liệu Java Aspose.Words
description: Tìm hiểu cách tạo bảng từ DataTable bằng Aspose.Words for Java. Tạo tài liệu Word chuyên nghiệp với các bảng được định dạng dễ dàng.
weight: 11
url: /vi/java/table-processing/generate-table-from-datatable/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo bảng từ Datatable

## Giới thiệu

Tạo bảng động từ các nguồn dữ liệu là một tác vụ phổ biến trong nhiều ứng dụng. Cho dù bạn đang tạo báo cáo, hóa đơn hay tóm tắt dữ liệu, khả năng điền dữ liệu vào bảng theo chương trình có thể giúp bạn tiết kiệm rất nhiều thời gian và công sức. Trong hướng dẫn này, chúng ta sẽ khám phá cách tạo bảng từ DataTable bằng Aspose.Words for Java. Chúng ta sẽ chia nhỏ quy trình thành các bước dễ quản lý, đảm bảo bạn hiểu rõ từng phần.

## Điều kiện tiên quyết

Trước khi tìm hiểu về mã, hãy đảm bảo rằng bạn có mọi thứ cần thiết để bắt đầu:

1.  Java Development Kit (JDK): Đảm bảo bạn đã cài đặt JDK trên máy của mình. Bạn có thể tải xuống từ[Trang web của Oracle](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html).
   
2.  Aspose.Words cho Java: Bạn sẽ cần thư viện Aspose.Words. Bạn có thể tải xuống phiên bản mới nhất từ[Trang phát hành của Aspose](https://releases.aspose.com/words/java/).

3. IDE: Môi trường phát triển tích hợp (IDE) như IntelliJ IDEA hoặc Eclipse sẽ giúp việc viết mã dễ dàng hơn.

4. Kiến thức cơ bản về Java: Sự quen thuộc với các khái niệm lập trình Java sẽ giúp bạn hiểu các đoạn mã tốt hơn.

5. Dữ liệu mẫu: Đối với hướng dẫn này, chúng tôi sẽ sử dụng tệp XML có tên "Danh sách people.xml" để mô phỏng nguồn dữ liệu. Bạn có thể tạo tệp này với dữ liệu mẫu để thử nghiệm.

## Bước 1: Tạo một tài liệu mới

Đầu tiên, chúng ta cần tạo một tài liệu mới nơi bảng của chúng ta sẽ nằm. Đây là canvas cho công việc của chúng ta.

```java
Document doc = new Document();
```

 Ở đây, chúng ta khởi tạo một cái mới`Document` đối tượng. Đây sẽ là tài liệu làm việc để chúng ta xây dựng bảng.

## Bước 2: Khởi tạo DocumentBuilder

 Tiếp theo, chúng ta sẽ sử dụng`DocumentBuilder` lớp cho phép chúng ta thao tác tài liệu dễ dàng hơn.

```java
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Các`DocumentBuilder` đối tượng cung cấp các phương thức để chèn bảng, văn bản và các thành phần khác vào tài liệu.

## Bước 3: Thiết lập hướng trang

Vì chúng ta muốn bảng có chiều rộng nên chúng ta sẽ đặt hướng trang theo chiều ngang.

```java
doc.getFirstSection().getPageSetup().setOrientation(Orientation.LANDSCAPE);
```

Bước này rất quan trọng vì nó đảm bảo bảng của chúng ta vừa khít trên trang mà không bị cắt mất.

## Bước 4: Tải dữ liệu từ XML

 Bây giờ, chúng ta cần tải dữ liệu của mình từ tệp XML vào một`DataTable`. Đây là nguồn dữ liệu của chúng tôi.

```java
DataSet ds = new DataSet();
ds.readXml(getMyDir() + "List of people.xml");
DataTable dataTable = ds.getTables().get(0);
```

 Ở đây, chúng tôi đọc tệp XML và lấy bảng đầu tiên từ tập dữ liệu. Điều này`DataTable` sẽ lưu trữ dữ liệu chúng ta muốn hiển thị trong tài liệu.

## Bước 5: Nhập Bảng từ DataTable

Bây giờ đến phần thú vị: nhập dữ liệu vào tài liệu dưới dạng bảng.

```java
Table table = importTableFromDataTable(builder, dataTable, true);
```

 Chúng tôi gọi phương pháp này`importTableFromDataTable` , vượt qua`DocumentBuilder` , của chúng tôi`DataTable`và một giá trị boolean để chỉ ra liệu có nên bao gồm tiêu đề cột hay không.

## Bước 6: Tạo kiểu cho bảng

Khi đã có bảng, chúng ta có thể áp dụng một số kiểu dáng để làm cho nó trông đẹp mắt.

```java
table.setStyleIdentifier(StyleIdentifier.MEDIUM_LIST_2_ACCENT_1);
table.setStyleOptions(TableStyleOptions.FIRST_ROW | TableStyleOptions.ROW_BANDS | TableStyleOptions.LAST_COLUMN);
```

Mã này áp dụng kiểu được xác định trước cho bảng, tăng cường tính hấp dẫn về mặt thị giác và khả năng đọc của bảng.

## Bước 7: Loại bỏ các tế bào không mong muốn

Nếu bạn có bất kỳ cột nào không muốn hiển thị, chẳng hạn như cột hình ảnh, bạn có thể dễ dàng xóa cột đó.

```java
table.getFirstRow().getLastCell().removeAllChildren();
```

Bước này đảm bảo rằng bảng của chúng ta chỉ hiển thị thông tin có liên quan.

## Bước 8: Lưu tài liệu

Cuối cùng, chúng ta lưu tài liệu với bảng đã tạo.

```java
doc.save(getArtifactsDir() + "WorkingWithTables.BuildTableFromDataTable.docx");
```

Dòng này lưu tài liệu vào thư mục đã chỉ định, cho phép bạn xem lại kết quả.

## Phương pháp importTableFromDataTable

 Chúng ta hãy xem xét kỹ hơn`importTableFromDataTable` phương pháp. Phương pháp này chịu trách nhiệm tạo cấu trúc bảng và điền dữ liệu vào đó.

### Bước 1: Bắt đầu bảng

Đầu tiên, chúng ta cần tạo một bảng mới trong tài liệu.

```java
Table table = builder.startTable();
```

Thao tác này sẽ khởi tạo một bảng mới trong tài liệu của chúng ta.

### Bước 2: Thêm Tiêu đề Cột

 Nếu chúng ta muốn bao gồm các tiêu đề cột, chúng ta kiểm tra`importColumnHeadings` lá cờ.

```java
if (importColumnHeadings) {
    // Lưu trữ định dạng gốc
    boolean boldValue = builder.getFont().getBold();
    int paragraphAlignmentValue = builder.getParagraphFormat().getAlignment();

    // Đặt định dạng tiêu đề
    builder.getFont().setBold(true);
    builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

    // Chèn tên cột
    for (DataColumn column : dataTable.getColumns()) {
        builder.insertCell();
        builder.writeln(column.getColumnName());
    }

    builder.endRow();

    // Khôi phục định dạng ban đầu
    builder.getFont().setBold(boldValue);
    builder.getParagraphFormat().setAlignment(paragraphAlignmentValue);
}
```

 Khối mã này định dạng hàng tiêu đề và chèn tên của các cột từ`DataTable`.

### Bước 3: Điền dữ liệu vào bảng

 Bây giờ, chúng ta lặp qua từng hàng của`DataTable` để chèn dữ liệu vào bảng.

```java
for (DataRow dataRow : (Iterable<DataRow>) dataTable.getRows()) {
    for (Object item : dataRow.getItemArray()) {
        builder.insertCell();
        switch (item.getClass().getName()) {
            case "DateTime":
                Date dateTime = (Date) item;
                SimpleDateFormat simpleDateFormat = new SimpleDateFormat("MMMM d, yyyy");
                builder.write(simpleDateFormat.format(dateTime));
                break;
            default:
                builder.write(item.toString());
                break;
        }
    }
    builder.endRow();
}
```

Trong phần này, chúng ta sẽ xử lý các kiểu dữ liệu khác nhau, định dạng ngày tháng một cách phù hợp trong khi chèn dữ liệu khác dưới dạng văn bản.

### Bước 4: Kết thúc bảng

Cuối cùng, chúng ta hoàn thiện bảng sau khi đã chèn đầy đủ dữ liệu.

```java
builder.endTable();
```

 Dòng này đánh dấu phần cuối của bảng của chúng tôi, cho phép`DocumentBuilder` để biết rằng chúng ta đã hoàn thành phần này.

## Phần kết luận

Và bạn đã có nó! Bạn đã học thành công cách tạo bảng từ DataTable bằng Aspose.Words for Java. Bằng cách làm theo các bước này, bạn có thể dễ dàng tạo các bảng động trong tài liệu của mình dựa trên nhiều nguồn dữ liệu khác nhau. Cho dù bạn đang tạo báo cáo hay hóa đơn, phương pháp này sẽ hợp lý hóa quy trình làm việc của bạn và cải thiện quy trình tạo tài liệu của bạn.

## Câu hỏi thường gặp

### Aspose.Words dành cho Java là gì?
Aspose.Words for Java là một thư viện mạnh mẽ để tạo, xử lý và chuyển đổi các tài liệu Word theo cách lập trình.

### Tôi có thể sử dụng Aspose.Words miễn phí không?
 Có, Aspose cung cấp phiên bản dùng thử miễn phí. Bạn có thể tải xuống từ[đây](https://releases.aspose.com/).

### Làm thế nào để định dạng bảng trong Aspose.Words?
Bạn có thể áp dụng các kiểu bằng cách sử dụng các tùy chọn và mã định danh kiểu được xác định trước do thư viện cung cấp.

### Tôi có thể chèn những loại dữ liệu nào vào bảng?
Bạn có thể chèn nhiều kiểu dữ liệu khác nhau, bao gồm văn bản, số và ngày tháng, có thể định dạng theo ý muốn.

### Tôi có thể nhận hỗ trợ cho Aspose.Words ở đâu?
 Bạn có thể tìm thấy sự hỗ trợ và đặt câu hỏi trên[Diễn đàn Aspose](https://forum.aspose.com/c/words/8/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
