---
"description": "Tìm hiểu cách thiết lập tùy chọn mặc định cho nhãn dữ liệu trong biểu đồ bằng Aspose.Words cho .NET. Làm theo hướng dẫn từng bước của chúng tôi để tạo và tùy chỉnh biểu đồ dễ dàng."
"linktitle": "Thiết lập tùy chọn mặc định cho nhãn dữ liệu trong biểu đồ"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Thiết lập tùy chọn mặc định cho nhãn dữ liệu trong biểu đồ"
"url": "/vi/net/programming-with-charts/default-options-for-data-labels/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Thiết lập tùy chọn mặc định cho nhãn dữ liệu trong biểu đồ

## Giới thiệu

Xin chào! Bạn có hào hứng khám phá thế giới tự động hóa tài liệu không? Hôm nay, chúng ta sẽ khám phá cách sử dụng Aspose.Words cho .NET để tạo các tài liệu tuyệt đẹp theo chương trình. Aspose.Words là một thư viện mạnh mẽ cho phép bạn dễ dàng thao tác các tài liệu Word và trong hướng dẫn này, chúng ta sẽ tập trung vào việc thiết lập các tùy chọn mặc định cho nhãn dữ liệu trong biểu đồ. Cho dù bạn là nhà phát triển dày dạn kinh nghiệm hay người mới bắt đầu, hướng dẫn này sẽ hướng dẫn bạn từng bước để bạn có thể bắt đầu và chạy ngay lập tức.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn có mọi thứ cần thiết để làm theo hướng dẫn này. Sau đây là danh sách kiểm tra nhanh:

- Visual Studio hoặc bất kỳ IDE nào khác tương thích với .NET: Đây là nơi bạn sẽ viết và chạy mã của mình.
- Aspose.Words cho .NET: Bạn có thể [tải xuống phiên bản mới nhất](https://releases.aspose.com/words/net/) và cài đặt nó vào dự án của bạn.
- Kiến thức cơ bản về lập trình C#: Mặc dù hướng dẫn này dành cho người mới bắt đầu, nhưng việc quen thuộc một chút với C# sẽ rất hữu ích.
- Đã cài đặt .NET Framework: Đảm bảo rằng bạn đã cài đặt .NET Framework trên máy của mình.
- Giấy phép tạm thời cho Aspose.Words: Nhận một giấy phép [đây](https://purchase.aspose.com/temporary-license/) để mở khóa đầy đủ chức năng.

Sau khi đã đáp ứng được những điều kiện tiên quyết này, chúng ta đã sẵn sàng bắt đầu!

## Nhập không gian tên

Trước tiên, hãy thiết lập dự án của chúng ta và nhập các không gian tên cần thiết. Các không gian tên này rất quan trọng để truy cập chức năng Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.ReportingServices;
```

## Bước 1: Tạo một tài liệu mới


Cuộc hành trình bắt đầu bằng việc tạo một tài liệu mới và khởi tạo một `DocumentBuilder`. Các `DocumentBuilder` Lớp này cung cấp một tập hợp các phương thức để thao tác nội dung tài liệu một cách dễ dàng.

```csharp
// Đường dẫn đến thư mục tài liệu của bạn
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Tạo một tài liệu mới
Document doc = new Document();

// Khởi tạo DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Giải thích

Trong bước này, chúng tôi đã thiết lập tài liệu và trình xây dựng mà chúng tôi sẽ sử dụng để chèn và định dạng nội dung của mình. `dataDir` biến giữ đường dẫn nơi chúng ta sẽ lưu tài liệu cuối cùng.

## Bước 2: Chèn biểu đồ

Tiếp theo, chúng ta sẽ thêm biểu đồ hình tròn vào tài liệu của mình. `InsertChart` phương pháp của `DocumentBuilder` lớp học làm cho điều này trở nên cực kỳ dễ dàng.

```csharp
// Chèn biểu đồ hình tròn
Shape shape = builder.InsertChart(ChartType.Pie, 432, 252);

// Truy cập vào đối tượng biểu đồ
Chart chart = shape.Chart;
```

### Giải thích

Ở đây, chúng tôi đang chèn một biểu đồ hình tròn vào tài liệu của mình. `InsertChart` phương pháp này yêu cầu loại biểu đồ, chiều rộng và chiều cao làm tham số. Sau khi chèn biểu đồ, chúng ta truy cập đối tượng biểu đồ để thao tác thêm.

## Bước 3: Tùy chỉnh Chuỗi Biểu đồ

Bây giờ, chúng ta sẽ xóa bất kỳ chuỗi nào hiện có trong biểu đồ và thêm chuỗi tùy chỉnh của chúng ta. Chuỗi này sẽ biểu diễn các điểm dữ liệu của chúng ta.

```csharp
// Xóa chuỗi biểu đồ hiện có
chart.Series.Clear();

// Thêm chuỗi mới vào biểu đồ
ChartSeries series = chart.Series.Add("Aspose Series 1",
    new string[] { "Category 1", "Category 2", "Category 3" },
    new double[] { 2.7, 3.2, 0.8 });
```

### Giải thích

Trong bước này, chúng ta đảm bảo biểu đồ của mình trống bằng cách xóa bất kỳ chuỗi nào đã tồn tại trước đó. Sau đó, chúng ta thêm một chuỗi mới với các danh mục và giá trị tùy chỉnh, sẽ được hiển thị trong biểu đồ hình tròn của chúng ta.

## Bước 4: Đặt tùy chọn mặc định cho nhãn dữ liệu

Nhãn dữ liệu rất quan trọng để làm cho biểu đồ của bạn có nhiều thông tin. Chúng tôi sẽ thiết lập các tùy chọn để hiển thị phần trăm, giá trị và tùy chỉnh dấu phân cách.

```csharp
// Truy cập bộ sưu tập nhãn dữ liệu
ChartDataLabelCollection labels = series.DataLabels;

// Đặt tùy chọn nhãn dữ liệu
labels.ShowPercentage = true;
labels.ShowValue = true;
labels.ShowLeaderLines = false;
labels.Separator = " - ";
```

### Giải thích

Ở đây, chúng ta đang truy cập `DataLabels` thuộc tính của chuỗi của chúng tôi để tùy chỉnh giao diện và thông tin hiển thị trên mỗi nhãn dữ liệu. Chúng tôi đã chọn hiển thị cả phần trăm và giá trị, ẩn các dòng dẫn và đặt dấu phân cách tùy chỉnh.

## Bước 5: Lưu tài liệu

Cuối cùng, chúng ta sẽ lưu tài liệu vào thư mục đã chỉ định. Bước này đảm bảo rằng tất cả các thay đổi của chúng ta đều được ghi vào một tệp.

```csharp
// Lưu tài liệu
doc.Save(dataDir + "WorkingWithCharts.DefaultOptionsForDataLabels.docx");
```

### Giải thích

Trong bước cuối cùng này, chúng tôi lưu tài liệu của mình bằng cách sử dụng `Save` phương pháp. Tài liệu sẽ được lưu trong thư mục được chỉ định bởi `dataDir`, có tên là "WorkingWithCharts.DefaultOptionsForDataLabels.docx".

## Phần kết luận

Và bạn đã có nó! Bạn đã tạo thành công một tài liệu Word với biểu đồ hình tròn tùy chỉnh bằng Aspose.Words cho .NET. Thư viện mạnh mẽ này giúp bạn dễ dàng tự động hóa việc tạo và thao tác tài liệu, giúp bạn tiết kiệm thời gian và công sức. Cho dù bạn đang tạo báo cáo, hóa đơn hay bất kỳ loại tài liệu nào khác, Aspose.Words đều có thể giúp bạn.

Hãy thoải mái khám phá [Tài liệu Aspose.Words](https://reference.aspose.com/words/net/) để biết thêm nhiều tính năng và ví dụ. Chúc bạn viết mã vui vẻ!

## Câu hỏi thường gặp

### Tôi có thể sử dụng Aspose.Words miễn phí không?
Bạn có thể sử dụng Aspose.Words miễn phí với [giấy phép tạm thời](https://purchase.aspose.com/temporary-license/) hoặc khám phá các tính năng của nó bằng cách sử dụng [dùng thử miễn phí](https://releases.aspose.com/).

### Làm thế nào để tôi nhận được hỗ trợ cho Aspose.Words?
Bạn có thể nhận được hỗ trợ thông qua [Diễn đàn hỗ trợ Aspose.Words](https://forum.aspose.com/c/words/8).

### Tôi có thể thêm các loại biểu đồ khác không?
Có, Aspose.Words hỗ trợ nhiều loại biểu đồ như biểu đồ thanh, biểu đồ đường và biểu đồ cột. Kiểm tra [tài liệu](https://reference.aspose.com/words/net/) để biết thêm chi tiết.

### Aspose.Words có tương thích với .NET Core không?
Có, Aspose.Words tương thích với .NET Core. Bạn có thể tìm thêm thông tin trong [tài liệu](https://reference.aspose.com/words/net/).

### Làm thế nào tôi có thể mua giấy phép cho Aspose.Words?
Bạn có thể mua giấy phép từ [Cửa hàng Aspose](https://purchase.aspose.com/buy).




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}