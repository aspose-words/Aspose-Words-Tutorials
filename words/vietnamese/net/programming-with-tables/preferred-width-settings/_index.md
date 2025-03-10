---
title: Cài đặt chiều rộng ưa thích
linktitle: Cài đặt chiều rộng ưa thích
second_title: API xử lý tài liệu Aspose.Words
description: Tìm hiểu cách tạo bảng với cài đặt chiều rộng tuyệt đối, tương đối và tự động trong Aspose.Words cho .NET với hướng dẫn từng bước này.
weight: 10
url: /vi/net/programming-with-tables/preferred-width-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cài đặt chiều rộng ưa thích

## Giới thiệu

Bảng là một cách mạnh mẽ để sắp xếp và trình bày thông tin trong tài liệu Word của bạn. Khi làm việc với bảng trong Aspose.Words cho .NET, bạn có một số tùy chọn để thiết lập chiều rộng của các ô bảng để đảm bảo chúng phù hợp hoàn hảo với bố cục tài liệu của bạn. Hướng dẫn này sẽ hướng dẫn bạn quy trình tạo bảng với các thiết lập chiều rộng ưa thích bằng Aspose.Words cho .NET, tập trung vào các tùy chọn kích thước tuyệt đối, tương đối và tự động. 

## Điều kiện tiên quyết

Trước khi bắt đầu hướng dẫn, hãy đảm bảo bạn có những điều sau:

1.  Aspose.Words cho .NET: Đảm bảo bạn đã cài đặt Aspose.Words cho .NET trong môi trường phát triển của mình. Bạn có thể tải xuống[đây](https://releases.aspose.com/words/net/).

2. Môi trường phát triển .NET: Thiết lập môi trường phát triển .NET, chẳng hạn như Visual Studio.

3. Kiến thức cơ bản về C#: Sự quen thuộc với lập trình C# sẽ giúp bạn hiểu các đoạn mã và ví dụ tốt hơn.

4.  Tài liệu Aspose.Words: Tham khảo[Tài liệu Aspose.Words](https://reference.aspose.com/words/net/) để biết thông tin chi tiết về API và đọc thêm.

## Nhập không gian tên

Trước khi bắt đầu viết mã, bạn cần nhập các không gian tên cần thiết vào dự án C# của mình:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Các không gian tên này cung cấp quyền truy cập vào các chức năng cốt lõi của Aspose.Words và đối tượng Table, cho phép bạn thao tác các bảng tài liệu.

Chúng ta hãy chia nhỏ quy trình tạo bảng với nhiều thiết lập chiều rộng ưu tiên thành các bước rõ ràng, dễ quản lý.

## Bước 1: Khởi tạo Document và DocumentBuilder

Tiêu đề: Tạo một tài liệu mới và DocumentBuilder

 Giải thích: Bắt đầu bằng cách tạo một tài liệu Word mới và một`DocumentBuilder` Ví dụ. Các`DocumentBuilder` Lớp này cung cấp một cách đơn giản để thêm nội dung vào tài liệu của bạn.

```csharp
// Xác định đường dẫn để lưu tài liệu.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Tạo một tài liệu mới.
Document doc = new Document();

// Tạo DocumentBuilder cho Tài liệu này.
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Tại đây, bạn chỉ định thư mục nơi tài liệu sẽ được lưu và khởi tạo`Document` Và`DocumentBuilder` đồ vật.

## Bước 2: Chèn ô đầu tiên của bảng có chiều rộng tuyệt đối

Chèn ô đầu tiên vào bảng có chiều rộng cố định là 40 điểm. Điều này sẽ đảm bảo rằng ô này luôn duy trì chiều rộng là 40 điểm bất kể kích thước bảng.

```csharp
// Chèn một ô có kích thước tuyệt đối.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPoints(40);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightYellow;
builder.Writeln("Cell at 40 points width");
```

Trong bước này, bạn bắt đầu tạo bảng và chèn một ô có chiều rộng tuyệt đối.`PreferredWidth.FromPoints(40)` phương pháp này đặt chiều rộng của ô là 40 điểm và`Shading.BackgroundPatternColor` áp dụng màu nền vàng nhạt.

## Bước 3: Chèn một ô có kích thước tương đối

Chèn một ô khác có chiều rộng bằng 20% tổng chiều rộng của bảng. Kích thước tương đối này đảm bảo ô điều chỉnh theo tỷ lệ với chiều rộng của bảng.

```csharp
// Chèn ô có kích thước tương đối (phần trăm).
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(20);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
builder.Writeln("Cell at 20% width");
```

Chiều rộng của ô này sẽ bằng 20% tổng chiều rộng của bảng, giúp nó phù hợp với nhiều kích thước màn hình hoặc bố cục tài liệu khác nhau.

### Bước 4: Chèn một ô có kích thước tự động

Cuối cùng, chèn một ô có khả năng tự động thay đổi kích thước dựa trên không gian còn lại trong bảng.

```csharp
// Chèn một ô có kích thước tự động.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.Auto;
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightGreen;
builder.Writeln("Cell automatically sized. The size of this cell is calculated from the table preferred width.");
builder.Writeln("In this case the cell will fill up the rest of the available space.");
```

 Các`PreferredWidth.Auto` thiết lập cho phép ô này mở rộng hoặc co lại dựa trên không gian còn lại sau khi các ô khác được tính đến. Điều này đảm bảo bố cục bảng trông cân bằng và chuyên nghiệp.

## Bước 5: Hoàn thiện và Lưu Tài liệu

Sau khi chèn tất cả các ô, hãy hoàn thiện bảng và lưu tài liệu vào đường dẫn đã chỉ định.

```csharp
// Lưu tài liệu.
doc.Save(dataDir + "WorkingWithTables.PreferredWidthSettings.docx");
```

Bước này hoàn thiện bảng và lưu tài liệu với tên tệp "WorkingWithTables.PreferredWidthSettings.docx" trong thư mục được chỉ định của bạn.

## Phần kết luận

Tạo bảng với các thiết lập chiều rộng ưa thích trong Aspose.Words cho .NET rất đơn giản khi bạn hiểu các tùy chọn kích thước khác nhau có sẵn. Cho dù bạn cần chiều rộng ô cố định, tương đối hay tự động, Aspose.Words cung cấp tính linh hoạt để xử lý hiệu quả nhiều tình huống bố trí bảng khác nhau. Bằng cách làm theo các bước được nêu trong hướng dẫn này, bạn có thể đảm bảo bảng của mình được cấu trúc tốt và hấp dẫn về mặt hình ảnh trong tài liệu Word của bạn.

## Câu hỏi thường gặp

### Sự khác biệt giữa chiều rộng ô tuyệt đối và tương đối là gì?
Chiều rộng tuyệt đối của ô là cố định và không thay đổi, trong khi chiều rộng tương đối được điều chỉnh dựa trên tổng chiều rộng của bảng.

### Tôi có thể sử dụng phần trăm âm cho chiều rộng tương đối không?
Không, phần trăm âm không hợp lệ với chiều rộng ô. Chỉ phần trăm dương mới được phép.

### Tính năng tự động điều chỉnh kích thước hoạt động như thế nào?
Tính năng tự động thay đổi kích thước sẽ điều chỉnh chiều rộng của ô để lấp đầy bất kỳ khoảng trống nào còn lại trong bảng sau khi các ô khác đã được thay đổi kích thước.

### Tôi có thể áp dụng nhiều kiểu khác nhau cho các ô có cài đặt chiều rộng khác nhau không?
Có, bạn có thể áp dụng nhiều kiểu và định dạng khác nhau cho các ô bất kể cài đặt độ rộng của chúng.

### Điều gì xảy ra nếu tổng chiều rộng của bảng nhỏ hơn tổng chiều rộng của tất cả các ô?
Bảng sẽ tự động điều chỉnh độ rộng của các ô cho vừa với không gian có sẵn, điều này có thể khiến một số ô bị co lại.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
