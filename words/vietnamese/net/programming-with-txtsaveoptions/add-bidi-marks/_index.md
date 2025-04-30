---
"description": "Tìm hiểu cách thêm dấu hai chiều (Bidi) vào tài liệu Word bằng Aspose.Words cho .NET với hướng dẫn này. Đảm bảo hướng văn bản phù hợp cho nội dung đa ngôn ngữ."
"linktitle": "Thêm Dấu Bidi vào Tài liệu Word"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Thêm Dấu Bidi vào Tài liệu Word"
"url": "/vi/net/programming-with-txtsaveoptions/add-bidi-marks/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Thêm Dấu Bidi vào Tài liệu Word

## Giới thiệu

Trong thế giới xử lý tài liệu, văn bản hai chiều (Bidi) thường có thể hơi khó quản lý. Điều này đặc biệt đúng khi xử lý các ngôn ngữ có hướng văn bản khác nhau, chẳng hạn như tiếng Ả Rập hoặc tiếng Do Thái. May mắn thay, Aspose.Words for .NET giúp bạn dễ dàng xử lý các tình huống như vậy. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn cách thêm dấu Bidi vào tài liệu Word bằng Aspose.Words for .NET.

## Điều kiện tiên quyết

Trước khi tìm hiểu mã, hãy đảm bảo bạn có những điều sau:

1. Aspose.Words cho .NET: Bạn cần phải cài đặt Aspose.Words cho .NET. Bạn có thể tải xuống từ [Trang Tải xuống Aspose](https://releases.aspose.com/words/net/).
2. .NET Framework hoặc .NET Core: Đảm bảo rằng bạn đã thiết lập môi trường .NET tương thích để chạy các ví dụ.
3. Kiến thức cơ bản về C#: Có hiểu biết về ngôn ngữ lập trình C# và các thao tác cơ bản trong .NET.

## Nhập không gian tên

Để bắt đầu, bạn cần nhập các không gian tên cần thiết. Sau đây là cách bạn có thể đưa chúng vào dự án của mình:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Chúng ta hãy chia nhỏ quy trình thêm dấu Bidi vào tài liệu Word thành các bước rõ ràng. Mỗi bước sẽ hướng dẫn bạn về mã và mục đích của mã.

## Bước 1: Thiết lập tài liệu của bạn

Bắt đầu bằng cách tạo một phiên bản mới của `Document` lớp và một `DocumentBuilder` để thêm nội dung vào tài liệu.

```csharp
// Đường dẫn đến thư mục tài liệu của bạn
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Tạo tài liệu và thêm nội dung
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Trong bước này, bạn khởi tạo một tài liệu Word mới và thiết lập một `DocumentBuilder` để tạo điều kiện chèn nội dung.

## Bước 2: Thêm nội dung vào tài liệu của bạn

Tiếp theo, thêm một số văn bản vào tài liệu của bạn. Ở đây, chúng tôi sẽ thêm văn bản bằng các ngôn ngữ khác nhau để minh họa cách xử lý văn bản Bidi.

```csharp
builder.Writeln("Hello world!");
builder.ParagraphFormat.Bidi = true;
builder.Writeln("שלום עולם!");
builder.Writeln("مرحبا بالعالم!");
```

Ở đây, trước tiên chúng ta thêm một cụm từ tiếng Anh chuẩn. Sau đó, chúng ta kích hoạt định dạng văn bản Bidi cho văn bản tiếp theo, được viết bằng tiếng Do Thái và tiếng Ả Rập. Điều này minh họa cách kết hợp văn bản hai chiều.

## Bước 3: Cấu hình tùy chọn lưu cho Bidi Marks

Để đảm bảo rằng các dấu Bidi được lưu chính xác trong tài liệu, bạn cần cấu hình `TxtSaveOptions` và kích hoạt `AddBidiMarks` lựa chọn.

```csharp
// Thêm dấu Bidi
TxtSaveOptions saveOptions = new TxtSaveOptions { AddBidiMarks = true };
doc.Save(dataDir + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
```

Trong bước này, chúng ta tạo một thể hiện của `TxtSaveOptions` và thiết lập `AddBidiMarks` tài sản để `true`. Điều này đảm bảo rằng các dấu Bidi sẽ được bao gồm khi lưu tài liệu dưới dạng tệp văn bản.

## Phần kết luận

Thêm dấu Bidi vào tài liệu Word của bạn có thể là một bước quan trọng khi xử lý nội dung đa ngôn ngữ bao gồm các ngôn ngữ có hướng văn bản khác nhau. Với Aspose.Words cho .NET, quy trình này rất đơn giản và hiệu quả. Bằng cách làm theo các bước nêu trên, bạn có thể đảm bảo rằng tài liệu của mình thể hiện đúng văn bản Bidi, nâng cao khả năng đọc và độ chính xác.

## Câu hỏi thường gặp

### Dấu Bidi là gì và tại sao chúng lại quan trọng?
Dấu Bidi là các ký tự đặc biệt được sử dụng để kiểm soát hướng của văn bản trong tài liệu. Chúng rất cần thiết để hiển thị đúng các ngôn ngữ đọc từ phải sang trái, như tiếng Ả Rập và tiếng Do Thái.

### Tôi có thể sử dụng Aspose.Words cho .NET để xử lý các loại vấn đề về hướng văn bản khác không?
Có, Aspose.Words for .NET cung cấp hỗ trợ toàn diện cho nhiều nhu cầu định dạng và hướng văn bản, bao gồm ngôn ngữ từ phải sang trái và từ trái sang phải.

### Có thể áp dụng định dạng Bidi cho các phần cụ thể của tài liệu không?
Có, bạn có thể áp dụng định dạng Bidi cho các đoạn văn hoặc phần cụ thể trong tài liệu khi cần.

### Tôi có thể lưu tài liệu bằng Bidi Marks ở định dạng nào?
Trong ví dụ được cung cấp, tài liệu được lưu dưới dạng tệp văn bản. Tuy nhiên, Aspose.Words cũng hỗ trợ lưu tài liệu ở nhiều định dạng khác nhau trong khi vẫn giữ nguyên dấu Bidi.

### Tôi có thể tìm thêm thông tin về Aspose.Words cho .NET ở đâu?
Bạn có thể khám phá thêm về Aspose.Words cho .NET thông qua [Tài liệu Aspose](https://reference.aspose.com/words/net/) và truy cập [Diễn đàn hỗ trợ](https://forum.aspose.com/c/words/8) để được trợ giúp thêm.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}