---
"description": "Tìm hiểu cách hủy liên kết header và footer trong tài liệu Word bằng Aspose.Words cho .NET. Làm theo hướng dẫn chi tiết từng bước của chúng tôi để thành thạo thao tác tài liệu."
"linktitle": "Hủy liên kết Header Footer"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Hủy liên kết Header Footer"
"url": "/vi/net/join-and-append-documents/unlink-headers-footers/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hủy liên kết Header Footer

## Giới thiệu

Trong thế giới xử lý tài liệu, việc giữ cho phần đầu trang và phần chân trang nhất quán đôi khi có thể là một thách thức. Cho dù bạn đang hợp nhất tài liệu hay chỉ muốn có các phần đầu trang và phần chân trang khác nhau cho các phần khác nhau, thì việc biết cách hủy liên kết chúng là điều cần thiết. Hôm nay, chúng ta sẽ tìm hiểu cách bạn có thể thực hiện điều này bằng cách sử dụng Aspose.Words cho .NET. Chúng tôi sẽ chia nhỏ từng bước để bạn có thể dễ dàng theo dõi. Sẵn sàng để thành thạo thao tác tài liệu? Hãy bắt đầu thôi!

## Điều kiện tiên quyết

Trước khi đi sâu vào chi tiết, bạn cần chuẩn bị một số thứ sau:

- Aspose.Words cho Thư viện .NET: Bạn có thể tải xuống từ [Trang phát hành Aspose](https://releases.aspose.com/words/net/).
- .NET Framework: Đảm bảo bạn đã cài đặt .NET Framework tương thích.
- IDE: Visual Studio hoặc bất kỳ Môi trường phát triển tích hợp nào khác tương thích với .NET.
- Hiểu biết cơ bản về C#: Bạn cần có hiểu biết cơ bản về ngôn ngữ lập trình C#.

## Nhập không gian tên

Để bắt đầu, hãy đảm bảo nhập các không gian tên cần thiết vào dự án của bạn. Điều này sẽ cho phép bạn truy cập thư viện Aspose.Words và các tính năng của nó.

```csharp
using Aspose.Words;
```

Chúng ta hãy chia nhỏ quy trình thành các bước dễ quản lý để giúp bạn hủy liên kết đầu trang và chân trang trong tài liệu Word.

## Bước 1: Thiết lập dự án của bạn

Trước tiên, bạn cần thiết lập môi trường dự án của mình. Mở IDE và tạo một dự án .NET mới. Thêm tham chiếu đến thư viện Aspose.Words mà bạn đã tải xuống trước đó.

```csharp
// Đường dẫn đến thư mục tài liệu của bạn 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Bước 2: Tải Tài liệu Nguồn

Tiếp theo, bạn cần tải tài liệu nguồn mà bạn muốn sửa đổi. Tài liệu này sẽ có phần đầu trang và chân trang không được liên kết.

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
```

## Bước 3: Tải Tài liệu đích

Bây giờ, hãy tải tài liệu đích vào nơi bạn sẽ thêm tài liệu nguồn sau khi hủy liên kết phần đầu trang và phần chân trang.

```csharp
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## Bước 4: Hủy liên kết Header và Footer

Bước này rất quan trọng. Để hủy liên kết phần đầu trang và phần chân trang của tài liệu nguồn khỏi phần đầu trang và phần chân trang của tài liệu đích, bạn sẽ sử dụng `LinkToPrevious` Phương pháp này đảm bảo rằng phần đầu trang và phần chân trang không được chuyển sang tài liệu được thêm vào.

```csharp
// Hủy liên kết phần đầu trang và phần chân trang trong tài liệu nguồn để dừng việc này
// từ việc tiếp tục phần đầu trang và phần chân trang của tài liệu đích.
srcDoc.FirstSection.HeadersFooters.LinkToPrevious(false);
```

## Bước 5: Thêm Tài liệu Nguồn

Sau khi hủy liên kết phần đầu trang và phần chân trang, bạn có thể thêm tài liệu nguồn vào tài liệu đích. Sử dụng `AppendDocument` phương pháp và thiết lập chế độ định dạng nhập khẩu thành `KeepSourceFormatting` để duy trì định dạng gốc của tài liệu nguồn.

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

## Bước 6: Lưu tài liệu cuối cùng

Cuối cùng, lưu tài liệu mới tạo. Tài liệu này sẽ có nội dung của tài liệu nguồn được thêm vào tài liệu đích, với phần đầu trang và chân trang không được liên kết.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.UnlinkHeadersFooters.docx");
```

## Phần kết luận

Và bạn đã có nó! Bằng cách làm theo các bước này, bạn đã hủy liên kết thành công các tiêu đề và chân trang trong tài liệu nguồn của mình và thêm nó vào tài liệu đích bằng Aspose.Words cho .NET. Kỹ thuật này có thể đặc biệt hữu ích khi bạn làm việc với các tài liệu phức tạp yêu cầu các tiêu đề và chân trang khác nhau cho các phần khác nhau. Chúc bạn viết mã vui vẻ!

## Câu hỏi thường gặp

### Aspose.Words dành cho .NET là gì?  
Aspose.Words for .NET là một thư viện mạnh mẽ để làm việc với các tài liệu Word trong các ứng dụng .NET. Nó cho phép các nhà phát triển tạo, sửa đổi, chuyển đổi và in tài liệu theo chương trình.

### Tôi có thể hủy liên kết phần đầu trang và phần chân trang chỉ cho các phần cụ thể không?  
Có, bạn có thể hủy liên kết phần đầu trang và phần chân trang cho các phần cụ thể bằng cách truy cập `HeadersFooters` thuộc tính của phần mong muốn và sử dụng `LinkToPrevious` phương pháp.

### Có thể giữ nguyên định dạng gốc của tài liệu nguồn không?  
Có, khi thêm tài liệu nguồn, hãy sử dụng `ImportFormatMode.KeepSourceFormatting` tùy chọn giữ nguyên định dạng gốc.

### Tôi có thể sử dụng Aspose.Words cho .NET với các ngôn ngữ .NET khác ngoài C# không?  
Hoàn toàn có thể! Aspose.Words cho .NET có thể được sử dụng với bất kỳ ngôn ngữ .NET nào, bao gồm VB.NET và F#.

### Tôi có thể tìm thêm tài liệu và hỗ trợ cho Aspose.Words dành cho .NET ở đâu?  
Bạn có thể tìm thấy tài liệu toàn diện về [Trang tài liệu Aspose.Words cho .NET](https://reference.aspose.com/words/net/)và hỗ trợ có sẵn trên [Diễn đàn Aspose](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}