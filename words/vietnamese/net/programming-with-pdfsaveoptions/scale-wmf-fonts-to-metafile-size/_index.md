---
"description": "Hướng dẫn từng bước để giảm kích thước tệp PDF bằng cách sử dụng phông chữ wmf để chuyển đổi kích thước tệp metafile khi chuyển đổi sang PDF bằng Aspose.Words cho .NET."
"linktitle": "Giảm kích thước PDF bằng cách sử dụng Scale Wmf Fonts To Metafile Size"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Giảm kích thước PDF bằng cách sử dụng Scale Wmf Fonts To Metafile Size"
"url": "/vi/net/programming-with-pdfsaveoptions/scale-wmf-fonts-to-metafile-size/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Giảm kích thước PDF bằng cách sử dụng Scale Wmf Fonts To Metafile Size

## Giới thiệu

Khi làm việc với các tệp PDF, đặc biệt là các tệp được tạo từ tài liệu Word có chứa đồ họa WMF (Windows Metafile), quản lý kích thước có thể trở thành một khía cạnh quan trọng trong việc xử lý tài liệu. Một cách để kiểm soát kích thước PDF là điều chỉnh cách phông chữ WMF được hiển thị trong tài liệu. Trong hướng dẫn này, chúng ta sẽ khám phá cách giảm kích thước PDF bằng cách thu nhỏ phông chữ WMF theo kích thước metafile bằng Aspose.Words cho .NET.

## Điều kiện tiên quyết

Trước khi thực hiện các bước, hãy đảm bảo bạn có đủ những điều sau:

1. Aspose.Words cho .NET: Đảm bảo bạn đã cài đặt thư viện Aspose.Words. Nếu chưa, bạn có thể [tải xuống ở đây](https://releases.aspose.com/words/net/).
2. Môi trường phát triển: Hướng dẫn này giả định rằng bạn đã thiết lập môi trường phát triển .NET (như Visual Studio) nơi bạn có thể viết và thực thi mã C#.
3. Hiểu biết cơ bản về lập trình .NET: Sự quen thuộc với các khái niệm lập trình .NET cơ bản và cú pháp C# sẽ rất hữu ích.
4. Tài liệu Word có đồ họa WMF: Bạn sẽ cần một tài liệu Word có đồ họa WMF. Bạn có thể sử dụng tài liệu của riêng bạn hoặc tạo một tài liệu để thử nghiệm.

## Nhập không gian tên

Đầu tiên, bạn cần nhập các không gian tên cần thiết vào dự án C# của mình. Điều này sẽ cho phép bạn truy cập vào các lớp và phương thức cần thiết để làm việc với Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Bước 1: Tải tài liệu Word

Để bắt đầu, hãy tải tài liệu Word có chứa đồ họa WMF. Điều này được thực hiện bằng cách sử dụng `Document` lớp từ Aspose.Words.

```csharp
// Đường dẫn đến thư mục tài liệu.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Tải tài liệu
Document doc = new Document(dataDir + "WMF with text.docx");
```

Đây, `dataDir` là một trình giữ chỗ cho đường dẫn thư mục tài liệu của bạn. Chúng tôi tạo một phiên bản của `Document` lớp bằng cách truyền đường dẫn đến tệp Word. Thao tác này tải tài liệu vào bộ nhớ, sẵn sàng để xử lý thêm.

## Bước 2: Cấu hình Tùy chọn Kết xuất Metafile

Tiếp theo, bạn cần cấu hình các tùy chọn kết xuất metafile. Cụ thể, hãy thiết lập `ScaleWmfFontsToMetafileSize` tài sản để `false`. Điều này kiểm soát xem phông chữ WMF có được điều chỉnh để phù hợp với kích thước tệp siêu dữ liệu hay không.

```csharp
// Tạo một phiên bản mới của MetafileRenderingOptions
MetafileRenderingOptions metafileRenderingOptions = new MetafileRenderingOptions
{
    ScaleWmfFontsToMetafileSize = false
};
```

Các `MetafileRenderingOptions` lớp cung cấp các tùy chọn về cách các tệp siêu dữ liệu (như WMF) được hiển thị. Bằng cách thiết lập `ScaleWmfFontsToMetafileSize` ĐẾN `false`, bạn đang hướng dẫn Aspose.Words không thay đổi kích thước phông chữ theo kích thước tệp siêu dữ liệu, điều này có thể giúp giảm kích thước PDF tổng thể.

## Bước 3: Thiết lập tùy chọn lưu PDF

Bây giờ, hãy cấu hình tùy chọn lưu PDF để sử dụng tùy chọn kết xuất metafile mà bạn vừa thiết lập. Điều này cho Aspose.Words biết cách xử lý metafile khi lưu tài liệu dưới dạng PDF.

```csharp
// Tạo một phiên bản mới của PdfSaveOptions
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    MetafileRenderingOptions = metafileRenderingOptions
};
```

Các `PdfSaveOptions` lớp cho phép bạn chỉ định nhiều thiết lập khác nhau để lưu tài liệu dưới dạng PDF. Bằng cách chỉ định cấu hình trước đó `MetafileRenderingOptions` đến `MetafileRenderingOptions` tài sản của `PdfSaveOptions`, bạn đảm bảo rằng tài liệu được lưu theo cài đặt kết xuất metafile mong muốn của bạn.

## Bước 4: Lưu tài liệu dưới dạng PDF

Cuối cùng, lưu tài liệu Word dưới dạng PDF bằng cách sử dụng các tùy chọn lưu đã cấu hình. Thao tác này sẽ áp dụng tất cả các cài đặt, bao gồm các tùy chọn kết xuất metafile, vào PDF đầu ra.


```csharp
// Lưu tài liệu dưới dạng PDF
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ScaleWmfFontsToMetafileSize.pdf", saveOptions);
```

Trong bước này, `Save` phương pháp của `Document` lớp được sử dụng để xuất tài liệu sang tệp PDF. Đường dẫn nơi tệp PDF sẽ được lưu được chỉ định, cùng với `PdfSaveOptions` bao gồm các thiết lập kết xuất metafile.

## Phần kết luận

Bằng cách thu nhỏ phông chữ WMF theo kích thước tệp meta, bạn có thể giảm đáng kể kích thước tệp PDF được tạo từ tài liệu Word. Kỹ thuật này giúp tối ưu hóa lưu trữ và phân phối tài liệu mà không làm giảm chất lượng nội dung trực quan. Thực hiện theo các bước nêu trên đảm bảo tệp PDF của bạn dễ quản lý và hiệu quả hơn về kích thước.

## Câu hỏi thường gặp

### WMF là gì và tại sao nó lại quan trọng đối với kích thước PDF?

WMF (Windows Metafile) là định dạng đồ họa được sử dụng trong Microsoft Windows. Định dạng này có thể chứa cả dữ liệu vector và bitmap. Vì dữ liệu vector có thể được chia tỷ lệ và thao tác, nên điều quan trọng là phải xử lý đúng cách để tránh các tệp PDF lớn không cần thiết.

### Việc thay đổi kích thước phông chữ WMF theo kích thước tệp metafile ảnh hưởng đến PDF như thế nào?

Việc thu nhỏ phông chữ WMF theo kích thước tệp siêu dữ liệu có thể giúp giảm kích thước PDF tổng thể bằng cách tránh hiển thị phông chữ có độ phân giải cao có thể làm tăng kích thước tệp.

### Tôi có thể sử dụng các định dạng metafile khác với Aspose.Words không?

Có, Aspose.Words hỗ trợ nhiều định dạng metafile khác nhau, bao gồm EMF (Enhanced Metafile) ngoài WMF.

### Kỹ thuật này có thể áp dụng cho mọi loại tài liệu Word không?

Có, kỹ thuật này có thể áp dụng cho bất kỳ tài liệu Word nào có chứa đồ họa WMF, giúp tối ưu hóa kích thước của tệp PDF được tạo.

### Tôi có thể tìm thêm thông tin về Aspose.Words ở đâu?

Bạn có thể khám phá thêm về Aspose.Words trong [Tài liệu Aspose.Words](https://reference.aspose.com/words/net/)Để tải xuống, dùng thử và hỗ trợ, hãy truy cập [Trang Tải xuống Aspose.Words](https://releases.aspose.com/words/net/), [Mua Aspose.Words](https://purchase.aspose.com/buy), [Dùng thử miễn phí](https://releases.aspose.com/), [Giấy phép tạm thời](https://purchase.aspose.com/temporary-license/), Và [Ủng hộ](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}