---
"description": "Tìm hiểu cách định dạng nhãn dữ liệu trong biểu đồ bằng Aspose.Words cho .NET với hướng dẫn từng bước này. Cải thiện tài liệu Word của bạn một cách dễ dàng."
"linktitle": "Định dạng số nhãn dữ liệu trong biểu đồ"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Định dạng số nhãn dữ liệu trong biểu đồ"
"url": "/vi/net/programming-with-charts/format-number-of-data-label/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Định dạng số nhãn dữ liệu trong biểu đồ

## Giới thiệu

Việc tạo các tài liệu hấp dẫn và nhiều thông tin thường liên quan đến việc đưa vào các biểu đồ có nhãn dữ liệu được định dạng tốt. Nếu bạn là nhà phát triển .NET muốn nâng cao tài liệu Word của mình bằng các biểu đồ tinh vi, Aspose.Words for .NET là một thư viện tuyệt vời giúp bạn đạt được điều đó. Hướng dẫn này sẽ hướng dẫn bạn từng bước trong quy trình định dạng nhãn số trong biểu đồ bằng Aspose.Words for .NET.

## Điều kiện tiên quyết

Trước khi bắt đầu viết mã, bạn cần phải có một số điều kiện tiên quyết sau:

- Aspose.Words cho .NET: Đảm bảo bạn đã cài đặt thư viện Aspose.Words cho .NET. Nếu bạn chưa cài đặt, bạn có thể [tải xuống ở đây](https://releases.aspose.com/words/net/).
- Môi trường phát triển: Bạn nên thiết lập môi trường phát triển .NET. Visual Studio được khuyến khích sử dụng.
- Kiến thức cơ bản về C#: Sự quen thuộc với lập trình C# là điều cần thiết vì hướng dẫn này liên quan đến việc viết và hiểu mã C#.
- Giấy phép tạm thời: Để sử dụng Aspose.Words mà không có bất kỳ hạn chế nào, bạn có thể nhận được [giấy phép tạm thời](https://purchase.aspose.com/temporary-license/).

Bây giờ, chúng ta hãy cùng tìm hiểu từng bước trong quy trình định dạng nhãn số trong biểu đồ.

## Nhập không gian tên

Trước tiên, chúng ta cần nhập các không gian tên cần thiết để làm việc với Aspose.Words cho .NET. Thêm các dòng sau vào đầu tệp C# của bạn:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## Bước 1: Thiết lập thư mục tài liệu của bạn

Trước khi bạn có thể bắt đầu thao tác với tài liệu Word, bạn cần chỉ định thư mục nơi tài liệu của bạn sẽ được lưu. Điều này rất cần thiết cho thao tác lưu sau này.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Thay thế `"YOUR DOCUMENT DIRECTORY"` với đường dẫn thực tế đến thư mục tài liệu của bạn.

## Bước 2: Khởi tạo Document và DocumentBuilder

Bước tiếp theo là khởi tạo một cái mới `Document` và một `DocumentBuilder`. Các `DocumentBuilder` là lớp trợ giúp cho phép chúng ta xây dựng nội dung tài liệu.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Bước 3: Chèn biểu đồ vào tài liệu

Bây giờ, hãy chèn biểu đồ vào tài liệu bằng cách sử dụng `DocumentBuilder`. Trong hướng dẫn này, chúng ta sẽ sử dụng biểu đồ đường làm ví dụ.

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
chart.Title.Text = "Data Labels With Different Number Format";
```

Tại đây, chúng ta chèn biểu đồ đường có chiều rộng và chiều cao cụ thể và đặt tiêu đề cho biểu đồ.

## Bước 4: Xóa Series mặc định và thêm Series mới

Theo mặc định, biểu đồ sẽ có một số chuỗi được tạo sẵn. Chúng ta cần xóa những chuỗi này và thêm chuỗi của riêng mình với các điểm dữ liệu cụ thể.

```csharp
// Xóa chuỗi mặc định được tạo.
chart.Series.Clear();

// Thêm chuỗi mới với các điểm dữ liệu tùy chỉnh.
ChartSeries series1 = chart.Series.Add("Aspose Series 1", 
	new string[] { "Category 1", "Category 2", "Category 3" }, 
	new double[] { 2.5, 1.5, 3.5 });
```

## Bước 5: Kích hoạt nhãn dữ liệu

Để hiển thị nhãn dữ liệu trên biểu đồ, chúng ta cần bật chúng cho chuỗi dữ liệu của mình.

```csharp
series1.HasDataLabels = true;
series1.DataLabels.ShowValue = true;
```

## Bước 6: Định dạng nhãn dữ liệu

Cốt lõi của hướng dẫn này là định dạng nhãn dữ liệu. Chúng ta có thể áp dụng các định dạng số khác nhau cho từng nhãn dữ liệu riêng lẻ.

```csharp
series1.DataLabels[0].NumberFormat.FormatCode = "\"$\"#,##0.00"; // Định dạng tiền tệ
series1.DataLabels[1].NumberFormat.FormatCode = "dd/mm/yyyy"; // Định dạng ngày tháng
series1.DataLabels[2].NumberFormat.FormatCode = "0.00%"; // Định dạng phần trăm
```

Ngoài ra, bạn có thể liên kết định dạng của nhãn dữ liệu với ô nguồn. Khi được liên kết, `NumberFormat` sẽ được thiết lập lại thành chung và kế thừa từ ô nguồn.

```csharp
series1.DataLabels[2].NumberFormat.IsLinkedToSource = true;
```

## Bước 7: Lưu tài liệu

Cuối cùng, lưu tài liệu vào thư mục đã chỉ định.

```csharp
doc.Save(dataDir + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

Thao tác này sẽ lưu tài liệu của bạn theo tên đã chỉ định và đảm bảo biểu đồ có nhãn dữ liệu được định dạng sẽ được bảo toàn.

## Phần kết luận

Định dạng nhãn dữ liệu trong biểu đồ bằng Aspose.Words for .NET có thể cải thiện đáng kể khả năng đọc và tính chuyên nghiệp của tài liệu Word của bạn. Bằng cách làm theo hướng dẫn từng bước này, giờ đây bạn có thể tạo biểu đồ, thêm chuỗi dữ liệu và định dạng nhãn dữ liệu để đáp ứng nhu cầu của mình. Aspose.Words for .NET là một công cụ mạnh mẽ cho phép tùy chỉnh và tự động hóa rộng rãi các tài liệu Word, khiến nó trở thành một tài sản vô giá đối với các nhà phát triển .NET.

## Câu hỏi thường gặp

### Aspose.Words dành cho .NET là gì?
Aspose.Words for .NET là một thư viện mạnh mẽ để tạo, thao tác và chuyển đổi các tài liệu Word theo chương trình sử dụng C#.

### Tôi có thể định dạng các loại biểu đồ khác bằng Aspose.Words cho .NET không?
Có, Aspose.Words for .NET hỗ trợ nhiều loại biểu đồ, bao gồm biểu đồ thanh, biểu đồ cột, biểu đồ tròn, v.v.

### Làm thế nào để tôi có được giấy phép tạm thời cho Aspose.Words dành cho .NET?
Bạn có thể xin giấy phép tạm thời [đây](https://purchase.aspose.com/temporary-license/).

### Có thể liên kết nhãn dữ liệu với ô nguồn trong Excel không?
Có, bạn có thể liên kết nhãn dữ liệu với các ô nguồn, cho phép định dạng số được kế thừa từ ô nguồn.

### Tôi có thể tìm tài liệu chi tiết hơn về Aspose.Words cho .NET ở đâu?
Bạn có thể tìm thấy tài liệu toàn diện [đây](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}