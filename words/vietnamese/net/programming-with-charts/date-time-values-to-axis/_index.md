---
"description": "Tìm hiểu cách thêm giá trị ngày và giờ vào trục biểu đồ bằng Aspose.Words cho .NET trong hướng dẫn từng bước toàn diện này."
"linktitle": "Thêm giá trị ngày giờ vào trục của biểu đồ"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Thêm giá trị ngày giờ vào trục của biểu đồ"
"url": "/vi/net/programming-with-charts/date-time-values-to-axis/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Thêm giá trị ngày giờ vào trục của biểu đồ

## Giới thiệu

Tạo biểu đồ trong tài liệu có thể là một cách mạnh mẽ để trực quan hóa dữ liệu. Khi xử lý dữ liệu chuỗi thời gian, việc thêm giá trị ngày và giờ vào trục của biểu đồ là rất quan trọng để làm rõ. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn quy trình thêm giá trị ngày và giờ vào trục của biểu đồ bằng Aspose.Words cho .NET. Hướng dẫn từng bước này sẽ giúp bạn thiết lập môi trường, viết mã và hiểu từng phần của quy trình. Hãy cùng tìm hiểu!

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn đã đáp ứng đủ các điều kiện tiên quyết sau:

1. Visual Studio hoặc bất kỳ IDE .NET nào: Bạn cần một môi trường phát triển để viết và chạy mã .NET của mình.
2. Aspose.Words cho .NET: Bạn nên cài đặt thư viện Aspose.Words cho .NET. Bạn có thể tải xuống từ [đây](https://releases.aspose.com/words/net/).
3. Kiến thức cơ bản về C#: Hướng dẫn này giả định rằng bạn có hiểu biết cơ bản về lập trình C#.
4. Giấy phép Aspose hợp lệ: Bạn có thể xin giấy phép tạm thời từ [đây](https://purchase.aspose.com/temporary-license/).

## Nhập không gian tên

Để bắt đầu, hãy đảm bảo bạn đã nhập các không gian tên cần thiết vào dự án của mình. Bước này rất quan trọng để truy cập các lớp và phương thức Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Bước 1: Thiết lập thư mục tài liệu của bạn

Đầu tiên, bạn cần xác định thư mục nơi tài liệu của bạn sẽ được lưu. Điều này rất quan trọng để sắp xếp các tệp của bạn và đảm bảo mã của bạn chạy đúng.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Bước 2: Tạo một Tài liệu mới và DocumentBuilder

Tiếp theo, tạo một phiên bản mới của `Document` lớp và một `DocumentBuilder` đối tượng. Các đối tượng này sẽ giúp bạn xây dựng và thao tác tài liệu của mình.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Bước 3: Chèn biểu đồ vào tài liệu

Bây giờ, chèn biểu đồ vào tài liệu của bạn bằng cách sử dụng `DocumentBuilder` đối tượng. Trong ví dụ này, chúng tôi sử dụng biểu đồ cột, nhưng bạn cũng có thể chọn các loại khác.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

## Bước 4: Xóa chuỗi hiện có

Xóa bất kỳ chuỗi nào hiện có trong biểu đồ để đảm bảo bạn bắt đầu với một trang trống. Bước này rất cần thiết cho dữ liệu tùy chỉnh.

```csharp
chart.Series.Clear();
```

## Bước 5: Thêm giá trị ngày và giờ vào chuỗi

Thêm giá trị ngày và giờ vào chuỗi biểu đồ. Bước này bao gồm việc tạo mảng cho ngày và các giá trị tương ứng.

```csharp
chart.Series.Add("Aspose Series 1",
    new[]
    {
        new DateTime(2017, 11, 06), new DateTime(2017, 11, 09), new DateTime(2017, 11, 15),
        new DateTime(2017, 11, 21), new DateTime(2017, 11, 25), new DateTime(2017, 11, 29)
    },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2, 5.3 });
```

## Bước 6: Cấu hình Trục X

Đặt tỷ lệ và vạch chia cho trục X. Điều này đảm bảo ngày tháng của bạn được hiển thị chính xác và theo các khoảng thời gian thích hợp.

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.Scaling.Minimum = new AxisBound(new DateTime(2017, 11, 05).ToOADate());
xAxis.Scaling.Maximum = new AxisBound(new DateTime(2017, 12, 03).ToOADate());
xAxis.MajorUnit = 7;
xAxis.MinorUnit = 1;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
```

## Bước 7: Lưu tài liệu

Cuối cùng, lưu tài liệu của bạn vào thư mục đã chỉ định. Bước này kết thúc quá trình và tài liệu của bạn bây giờ sẽ chứa một biểu đồ với các giá trị ngày và giờ trên trục X.

```csharp
doc.Save(dataDir + "WorkingWithCharts.DateTimeValuesToAxis.docx");
```

## Phần kết luận

Thêm giá trị ngày và giờ vào trục biểu đồ trong tài liệu là một quy trình đơn giản với Aspose.Words for .NET. Bằng cách làm theo các bước được nêu trong hướng dẫn này, bạn có thể tạo biểu đồ rõ ràng và nhiều thông tin, trực quan hóa dữ liệu chuỗi thời gian một cách hiệu quả. Cho dù bạn đang chuẩn bị báo cáo, bài thuyết trình hay bất kỳ tài liệu nào yêu cầu biểu diễn dữ liệu chi tiết, Aspose.Words đều cung cấp các công cụ bạn cần để thành công.

## Câu hỏi thường gặp

### Tôi có thể sử dụng các loại biểu đồ khác với Aspose.Words cho .NET không?

Có, Aspose.Words hỗ trợ nhiều loại biểu đồ khác nhau, bao gồm biểu đồ đường, biểu đồ thanh, biểu đồ tròn, v.v.

### Làm thế nào để tùy chỉnh giao diện biểu đồ của tôi?

Bạn có thể tùy chỉnh giao diện bằng cách truy cập vào các thuộc tính của biểu đồ và thiết lập kiểu dáng, màu sắc, v.v.

### Có thể thêm nhiều chuỗi vào biểu đồ không?

Chắc chắn rồi! Bạn có thể thêm nhiều chuỗi vào biểu đồ của mình bằng cách gọi `Series.Add` phương pháp nhiều lần với dữ liệu khác nhau.

### Tôi phải làm sao nếu cần cập nhật dữ liệu biểu đồ một cách linh hoạt?

Bạn có thể cập nhật dữ liệu biểu đồ một cách linh hoạt bằng cách thao tác các thuộc tính chuỗi và trục theo chương trình dựa trên yêu cầu của bạn.

### Tôi có thể tìm tài liệu chi tiết hơn về Aspose.Words cho .NET ở đâu?

Bạn có thể tìm thấy tài liệu chi tiết hơn [đây](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}