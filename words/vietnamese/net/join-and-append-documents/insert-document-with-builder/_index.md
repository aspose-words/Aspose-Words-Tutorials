---
"description": "Tìm hiểu cách hợp nhất hai tài liệu Word bằng Aspose.Words cho .NET. Hướng dẫn từng bước để chèn tài liệu bằng DocumentBuilder và giữ nguyên định dạng."
"linktitle": "Chèn Tài Liệu Với Builder"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Chèn Tài Liệu Với Builder"
"url": "/vi/net/join-and-append-documents/insert-document-with-builder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Chèn Tài Liệu Với Builder

## Giới thiệu

Vậy là bạn có hai tài liệu Word và bạn muốn hợp nhất chúng thành một. Bạn có thể đang nghĩ, "Có cách nào dễ dàng để thực hiện việc này theo chương trình không?" Chắc chắn rồi! Hôm nay, tôi sẽ hướng dẫn bạn quy trình chèn một tài liệu vào tài liệu khác bằng thư viện Aspose.Words for .NET. Phương pháp này cực kỳ tiện dụng, đặc biệt là khi bạn đang xử lý các tài liệu lớn hoặc cần tự động hóa quy trình. Hãy cùng bắt đầu ngay nhé!

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn đã có mọi thứ cần thiết:

1. Aspose.Words cho .NET: Nếu bạn chưa tải xuống, bạn có thể tải xuống từ [đây](https://releases.aspose.com/words/net/).
2. Môi trường phát triển: Đảm bảo bạn đã cài đặt Visual Studio hoặc bất kỳ IDE phù hợp nào khác.
3. Kiến thức cơ bản về C#: Một chút quen thuộc với C# sẽ có ích rất nhiều.

## Nhập không gian tên

Trước tiên, bạn cần nhập các không gian tên cần thiết để truy cập các chức năng của thư viện Aspose.Words. Sau đây là cách bạn có thể thực hiện:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Bây giờ chúng ta đã có đủ điều kiện tiên quyết, hãy cùng phân tích quy trình theo từng bước.

## Bước 1: Thiết lập thư mục tài liệu của bạn

Trước khi bắt đầu mã hóa, bạn cần thiết lập đường dẫn đến thư mục tài liệu của mình. Đây là nơi lưu trữ tài liệu nguồn và đích của bạn.

```csharp
// Đường dẫn đến thư mục tài liệu của bạn 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Thay thế `"YOUR DOCUMENT DIRECTORY"` với đường dẫn thực tế nơi tài liệu của bạn được lưu trữ. Điều này sẽ giúp chương trình tìm thấy các tập tin của bạn một cách dễ dàng.

## Bước 2: Tải tài liệu nguồn và đích

Tiếp theo, chúng ta cần tải các tài liệu mà chúng ta muốn làm việc. Trong ví dụ này, chúng ta có một tài liệu nguồn và một tài liệu đích.

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

Ở đây, chúng tôi đang sử dụng `Document` lớp từ thư viện Aspose.Words để tải tài liệu của chúng tôi. Đảm bảo tên tệp khớp với tên trong thư mục của bạn.

## Bước 3: Tạo đối tượng DocumentBuilder

Các `DocumentBuilder` class là một công cụ mạnh mẽ trong thư viện Aspose.Words. Nó cho phép chúng ta điều hướng và thao tác tài liệu.

```csharp
DocumentBuilder builder = new DocumentBuilder(dstDoc);
```

Trong bước này, chúng tôi đã tạo ra một `DocumentBuilder` đối tượng cho tài liệu đích của chúng ta. Điều này sẽ giúp chúng ta chèn nội dung vào tài liệu.

## Bước 4: Di chuyển đến cuối tài liệu

Chúng ta cần di chuyển con trỏ xây dựng đến cuối tài liệu đích trước khi chèn tài liệu nguồn.

```csharp
builder.MoveToDocumentEnd();
```

Điều này đảm bảo rằng tài liệu nguồn được chèn vào cuối tài liệu đích.

## Bước 5: Chèn Ngắt Trang

Để giữ mọi thứ gọn gàng, hãy thêm ngắt trang trước khi chèn tài liệu nguồn. Thao tác này sẽ bắt đầu nội dung của tài liệu nguồn trên một trang mới.

```csharp
builder.InsertBreak(BreakType.PageBreak);
```

Ngắt trang đảm bảo nội dung của tài liệu nguồn bắt đầu ở một trang mới, làm cho tài liệu được hợp nhất trông chuyên nghiệp hơn.

## Bước 6: Chèn Tài liệu Nguồn

Bây giờ đến phần thú vị nhất—là chèn tài liệu nguồn vào tài liệu đích.

```csharp
builder.InsertDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

Sử dụng `InsertDocument` phương pháp, chúng ta có thể chèn toàn bộ tài liệu nguồn vào tài liệu đích. `ImportFormatMode.KeepSourceFormatting` đảm bảo định dạng của tài liệu nguồn được giữ nguyên.

## Bước 7: Lưu tài liệu đã hợp nhất

Cuối cùng, hãy lưu tài liệu đã hợp nhất. Thao tác này sẽ hợp nhất tài liệu nguồn và tài liệu đích thành một tệp.

```csharp
builder.Document.Save(dataDir + "JoinAndAppendDocuments.InsertDocumentWithBuilder.docx");
```

Bằng cách lưu tài liệu, chúng ta hoàn tất quá trình hợp nhất hai tài liệu. Tài liệu mới của bạn hiện đã sẵn sàng và được lưu trong thư mục đã chỉ định.

## Phần kết luận

Và thế là xong! Bạn đã chèn thành công một tài liệu vào tài liệu khác bằng Aspose.Words for .NET. Phương pháp này không chỉ hiệu quả mà còn bảo toàn định dạng của cả hai tài liệu, đảm bảo hợp nhất liền mạch. Cho dù bạn đang làm việc trên một dự án một lần hay cần tự động hóa quá trình xử lý tài liệu, Aspose.Words for .NET đều có thể giúp bạn.

## Câu hỏi thường gặp

### Aspose.Words dành cho .NET là gì?  
Aspose.Words for .NET là một thư viện mạnh mẽ cho phép các nhà phát triển tạo, chỉnh sửa, chuyển đổi và thao tác các tài liệu Word theo cách lập trình.

### Tôi có thể giữ nguyên định dạng của tài liệu nguồn không?  
Có, bằng cách sử dụng `ImportFormatMode.KeepSourceFormatting`định dạng của tài liệu nguồn sẽ được giữ nguyên khi nó được chèn vào tài liệu đích.

### Tôi có cần giấy phép để sử dụng Aspose.Words cho .NET không?  
Có, Aspose.Words cho .NET yêu cầu giấy phép để có đầy đủ chức năng. Bạn có thể nhận được [giấy phép tạm thời](https://purchase.aspose.com/temporary-license/) để đánh giá.

### Tôi có thể tự động hóa quá trình này không?  
Hoàn toàn có thể! Phương pháp được mô tả có thể được tích hợp vào các ứng dụng lớn hơn để tự động hóa các tác vụ xử lý tài liệu.

### Tôi có thể tìm thêm tài nguyên và hỗ trợ ở đâu?  
Để biết thêm thông tin, bạn có thể kiểm tra [tài liệu](https://reference.aspose.com/words/net/), hoặc ghé thăm [diễn đàn hỗ trợ](https://forum.aspose.com/c/words/8) để được hỗ trợ.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}