---
title: Xóa Nguồn Đầu Trang Chân Trang
linktitle: Xóa Nguồn Đầu Trang Chân Trang
second_title: API xử lý tài liệu Aspose.Words
description: Tìm hiểu cách xóa tiêu đề và chân trang trong tài liệu Word bằng Aspose.Words cho .NET. Đơn giản hóa việc quản lý tài liệu của bạn với hướng dẫn từng bước của chúng tôi.
weight: 10
url: /vi/net/join-and-append-documents/remove-source-headers-footers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Xóa Nguồn Đầu Trang Chân Trang

## Giới thiệu

Trong hướng dẫn toàn diện này, chúng ta sẽ đi sâu vào cách xóa tiêu đề và chân trang khỏi tài liệu Word một cách hiệu quả bằng Aspose.Words cho .NET. Tiêu đề và chân trang thường được sử dụng để đánh số trang, tiêu đề tài liệu hoặc nội dung lặp lại khác trong tài liệu Word. Cho dù bạn đang hợp nhất tài liệu hay dọn dẹp định dạng, việc thành thạo quy trình này có thể hợp lý hóa các tác vụ quản lý tài liệu của bạn. Hãy cùng khám phá quy trình từng bước để thực hiện việc này bằng Aspose.Words cho .NET.

## Điều kiện tiên quyết

Trước khi bắt đầu hướng dẫn, hãy đảm bảo bạn đã thiết lập các điều kiện tiên quyết sau:

1. Môi trường phát triển: Đã cài đặt Visual Studio hoặc bất kỳ môi trường phát triển .NET nào khác.
2.  Aspose.Words cho .NET: Đảm bảo bạn đã tải xuống và cài đặt Aspose.Words cho .NET. Nếu chưa, bạn có thể tải xuống từ[đây](https://releases.aspose.com/words/net/).
3. Kiến thức cơ bản: Có kiến thức cơ bản về lập trình C# và .NET framework.

## Nhập không gian tên

Trước khi bắt đầu viết mã, hãy đảm bảo nhập các không gian tên cần thiết vào tệp C# của bạn:

```csharp
using Aspose.Words;
```

## Bước 1: Tải Tài liệu Nguồn

 Đầu tiên, bạn cần tải tài liệu nguồn mà bạn muốn xóa tiêu đề và chân trang. Thay thế`"YOUR DOCUMENT DIRECTORY"` với đường dẫn thực tế đến thư mục tài liệu nơi chứa tài liệu nguồn.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Document source.docx");
```

## Bước 2: Tạo hoặc Tải Tài liệu Đích

 Nếu bạn chưa tạo tài liệu đích nơi bạn muốn đặt nội dung đã sửa đổi, bạn có thể tạo một tài liệu mới`Document` đối tượng hoặc tải đối tượng hiện có.

```csharp
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## Bước 3: Xóa Tiêu đề và Chân trang khỏi Các phần

Lặp lại qua từng phần trong tài liệu nguồn (`srcDoc`) và xóa phần đầu trang và chân trang.

```csharp
foreach (Section section in srcDoc.Sections)
{
    section.ClearHeadersFooters();
}
```

## Bước 4: Quản lý cài đặt LinkToPrevious

Để ngăn chặn phần đầu trang và phần chân trang tiếp tục trong tài liệu đích (`dstDoc` ), đảm bảo rằng`LinkToPrevious` thiết lập cho tiêu đề và chân trang được thiết lập thành`false`.

```csharp
srcDoc.FirstSection.HeadersFooters.LinkToPrevious(false);
```

## Bước 5: Thêm tài liệu đã sửa đổi vào tài liệu đích

Cuối cùng, thêm nội dung đã sửa đổi từ tài liệu nguồn (`srcDoc`) đến tài liệu đích (`dstDoc`) trong khi vẫn giữ nguyên định dạng nguồn.

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

## Bước 6: Lưu tài liệu kết quả

Lưu tài liệu cuối cùng đã xóa phần đầu trang và chân trang vào thư mục bạn chỉ định.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.RemoveSourceHeadersFooters.docx");
```

## Phần kết luận

Xóa tiêu đề và chân trang khỏi tài liệu Word bằng Aspose.Words cho .NET là một quy trình đơn giản có thể cải thiện đáng kể các tác vụ quản lý tài liệu. Bằng cách làm theo các bước nêu trên, bạn có thể dọn dẹp tài liệu hiệu quả để có giao diện chuyên nghiệp, bóng bẩy.

## Câu hỏi thường gặp

### Tôi có thể xóa phần đầu trang và phần chân trang khỏi các phần cụ thể không?
Có, bạn có thể lặp lại qua các phần và xóa phần đầu trang và chân trang một cách có chọn lọc khi cần.

### Aspose.Words cho .NET có hỗ trợ xóa tiêu đề và chân trang trên nhiều tài liệu không?
Hoàn toàn có thể thao tác phần đầu trang và chân trang trên nhiều tài liệu bằng Aspose.Words cho .NET.

###  Điều gì xảy ra nếu tôi quên cài đặt`LinkToPrevious` to `false`?
Tiêu đề và chân trang từ tài liệu nguồn có thể tiếp tục trong tài liệu đích.

### Tôi có thể xóa phần đầu trang và phần chân trang theo chương trình mà không ảnh hưởng đến các định dạng khác không?
Có, Aspose.Words cho .NET cho phép bạn xóa phần đầu trang và chân trang trong khi vẫn giữ nguyên định dạng còn lại của tài liệu.

### Tôi có thể tìm thêm tài nguyên và hỗ trợ cho Aspose.Words dành cho .NET ở đâu?
 Ghé thăm[Aspose.Words cho tài liệu .NET](https://reference.aspose.com/words/net/) để biết ví dụ và tài liệu tham khảo API chi tiết.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
