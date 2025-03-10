---
title: Định dạng số cho trục trong biểu đồ
linktitle: Định dạng số cho trục trong biểu đồ
second_title: API xử lý tài liệu Aspose.Words
description: Tìm hiểu cách định dạng số trục biểu đồ bằng Aspose.Words cho .NET với hướng dẫn từng bước này. Nâng cao khả năng đọc và tính chuyên nghiệp của tài liệu của bạn một cách dễ dàng.
weight: 10
url: /vi/net/programming-with-charts/number-format-for-axis/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Định dạng số cho trục trong biểu đồ

## Giới thiệu

Xin chào! Bạn đã bao giờ làm việc với biểu đồ trong tài liệu của mình và muốn định dạng các con số trên trục để chúng trông chuyên nghiệp hơn chưa? Vâng, bạn thật may mắn! Trong hướng dẫn này, chúng ta sẽ đi sâu vào cách bạn có thể đạt được điều đó bằng cách sử dụng Aspose.Words cho .NET. Thư viện mạnh mẽ này cho phép bạn xử lý các tài liệu Word theo cách dễ như ăn bánh. Và hôm nay, chúng ta sẽ tập trung vào việc làm mới các trục biểu đồ đó bằng các định dạng số tùy chỉnh.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn đã có mọi thứ cần thiết. Sau đây là danh sách kiểm tra nhanh:

-  Aspose.Words cho .NET: Hãy đảm bảo bạn đã cài đặt nó. Nếu chưa, bạn có thể[tải xuống ở đây](https://releases.aspose.com/words/net/).
- .NET Framework: Đảm bảo bạn đã cài đặt .NET Framework tương thích.
- Môi trường phát triển: Một IDE như Visual Studio sẽ hoạt động hoàn hảo.
- Kiến thức cơ bản về C#: Điều này sẽ giúp bạn theo dõi các ví dụ mã hóa.

## Nhập không gian tên

Trước tiên, bạn cần nhập các không gian tên cần thiết vào dự án của mình. Điều này giống như việc đặt nền móng trước khi xây nhà. Thêm các chỉ thị using sau vào đầu tệp mã của bạn:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Reporting;
```

Bây giờ, chúng ta hãy chia nhỏ quy trình thành các bước đơn giản, dễ thực hiện.

## Bước 1: Thiết lập tài liệu

Tiêu đề: Khởi tạo tài liệu của bạn

Đầu tiên, bạn cần tạo một tài liệu mới và một trình tạo tài liệu. Hãy nghĩ về bước này như việc chuẩn bị canvas và cọ vẽ trước khi bắt đầu kiệt tác của bạn.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Đây,`dataDir` là đường dẫn đến thư mục tài liệu nơi bạn sẽ lưu tập tin cuối cùng.`Document` Và`DocumentBuilder` là các lớp từ Aspose.Words giúp bạn tạo và thao tác với các tài liệu Word.

## Bước 2: Chèn biểu đồ

Tiêu đề: Thêm biểu đồ vào tài liệu của bạn

Tiếp theo, hãy thêm biểu đồ vào tài liệu của bạn. Đây là nơi phép thuật bắt đầu. Chúng ta sẽ chèn biểu đồ cột đóng vai trò như một khung vẽ trống.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

 Các`InsertChart` phương pháp này chèn một biểu đồ có kiểu được chỉ định (trong trường hợp này là Cột) và kích thước vào tài liệu.

## Bước 3: Tùy chỉnh Chuỗi Biểu đồ

Tiêu đề: Điền dữ liệu vào biểu đồ của bạn

Bây giờ, chúng ta cần thêm một số dữ liệu vào biểu đồ. Bước này tương tự như việc điền thông tin có ý nghĩa vào biểu đồ của bạn.

```csharp
chart.Series.Clear();
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1900000, 850000, 2100000, 600000, 1500000 });
```

 Ở đây, chúng tôi đang thêm một loạt mới có tên là "Aspose Series 1" với năm điểm dữ liệu.`Series.Clear` phương pháp này đảm bảo mọi dữ liệu có sẵn sẽ bị xóa trước khi thêm chuỗi mới của chúng tôi.

## Bước 4: Định dạng số trục

Tiêu đề: Làm đẹp số trục của bạn

Cuối cùng, hãy định dạng các con số trên trục Y để dễ đọc hơn. Điều này giống như việc hoàn thiện tác phẩm nghệ thuật của bạn.

```csharp
chart.AxisY.NumberFormat.FormatCode = "#,##0";
```

 Các`FormatCode` thuộc tính cho phép bạn thiết lập định dạng tùy chỉnh cho các số trên trục. Trong ví dụ này,`#,##0`đảm bảo rằng các số lớn được hiển thị với dấu phẩy cho hàng nghìn.

## Bước 5: Lưu tài liệu

Tiêu đề: Lưu kiệt tác của bạn

Bây giờ mọi thứ đã được thiết lập, đã đến lúc lưu tài liệu của bạn. Bước này là bước công bố tuyệt vời về tác phẩm của bạn.

```csharp
doc.Save(dataDir + "WorkingWithCharts.NumberFormatForAxis.docx");
```

 Ở đây,`Save` phương pháp lưu tài liệu vào đường dẫn đã chỉ định với tên tệp`WorkingWithCharts.NumberFormatForAxis.docx`.

## Phần kết luận

Và bạn đã có nó! Bạn đã định dạng thành công các con số trên trục Y của biểu đồ bằng Aspose.Words cho .NET. Điều này không chỉ làm cho biểu đồ của bạn trông chuyên nghiệp hơn mà còn tăng khả năng đọc. Aspose.Words cung cấp rất nhiều tính năng có thể giúp bạn tạo các tài liệu Word tuyệt đẹp theo chương trình. Vậy, tại sao không khám phá thêm và xem bạn có thể làm gì khác?

## Câu hỏi thường gặp

### Aspose.Words dành cho .NET là gì?
Aspose.Words for .NET là một thư viện mạnh mẽ cho phép các nhà phát triển tạo, thao tác và chuyển đổi các tài liệu Word theo cách lập trình.

### Tôi có thể định dạng các khía cạnh khác của biểu đồ ngoài số trục không?
Hoàn toàn đúng! Aspose.Words for .NET cho phép bạn định dạng tiêu đề, nhãn và thậm chí tùy chỉnh giao diện của biểu đồ.

### Có bản dùng thử miễn phí Aspose.Words dành cho .NET không?
 Vâng, bạn có thể nhận được một[dùng thử miễn phí tại đây](https://releases.aspose.com/).

### Tôi có thể sử dụng Aspose.Words cho .NET với các ngôn ngữ .NET khác ngoài C# không?
Có, Aspose.Words cho .NET tương thích với bất kỳ ngôn ngữ .NET nào, bao gồm VB.NET và F#.

### Tôi có thể tìm tài liệu chi tiết hơn ở đâu?
 Tài liệu chi tiết có sẵn trên[Trang tài liệu Aspose.Words cho .NET](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
