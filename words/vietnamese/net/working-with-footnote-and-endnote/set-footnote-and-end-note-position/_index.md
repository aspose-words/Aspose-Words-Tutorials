---
"description": "Tìm hiểu cách đặt vị trí chú thích cuối trang và chú thích cuối văn bản trong tài liệu Word bằng Aspose.Words cho .NET với hướng dẫn từng bước chi tiết này."
"linktitle": "Đặt vị trí chú thích cuối trang và chú thích cuối"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Đặt vị trí chú thích cuối trang và chú thích cuối trang"
"url": "/vi/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Đặt vị trí chú thích cuối trang và chú thích cuối trang

## Giới thiệu

Nếu bạn đang làm việc với các tài liệu Word và cần quản lý chú thích cuối trang và chú thích cuối văn bản hiệu quả, Aspose.Words for .NET là thư viện dành cho bạn. Hướng dẫn này sẽ hướng dẫn bạn cách thiết lập vị trí chú thích cuối trang và chú thích cuối văn bản trong tài liệu Word bằng Aspose.Words for .NET. Chúng tôi sẽ chia nhỏ từng bước để bạn dễ dàng thực hiện và triển khai.

## Điều kiện tiên quyết

Trước khi bắt đầu hướng dẫn, hãy đảm bảo bạn có những điều sau:

- Aspose.Words cho Thư viện .NET: Bạn có thể tải xuống từ [đây](https://releases.aspose.com/words/net/).
- Visual Studio: Bất kỳ phiên bản nào gần đây đều hoạt động tốt.
- Kiến thức cơ bản về C#: Hiểu những kiến thức cơ bản sẽ giúp bạn dễ dàng theo dõi.

## Nhập không gian tên

Đầu tiên, hãy nhập các không gian tên cần thiết vào dự án C# của bạn:

```csharp
using System;
using Aspose.Words;
```

## Bước 1: Tải tài liệu Word

Để bắt đầu, bạn cần tải tài liệu Word của mình vào đối tượng Tài liệu Aspose.Words. Điều này sẽ cho phép bạn thao tác nội dung của tài liệu.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

Trong mã này, thay thế `"YOUR DOCUMENT DIRECTORY"` với đường dẫn thực tế nơi tài liệu của bạn được lưu trữ.

## Bước 2: Đặt Vị trí Chú thích

Tiếp theo, bạn sẽ thiết lập vị trí của chú thích. Aspose.Words cho .NET cho phép bạn đặt chú thích ở cuối trang hoặc bên dưới văn bản.

```csharp
doc.FootnoteOptions.Position = FootnotePosition.BeneathText;
```

Ở đây, chúng tôi đã thiết lập chú thích xuất hiện bên dưới văn bản. Nếu bạn thích chúng ở cuối trang, hãy sử dụng `FootnotePosition.BottomOfPage`.

## Bước 3: Đặt vị trí Endnote

Tương tự như vậy, bạn có thể thiết lập vị trí của chú thích cuối trang. Chú thích cuối trang có thể được đặt ở cuối phần hoặc cuối tài liệu.

```csharp
doc.EndnoteOptions.Position = EndnotePosition.EndOfSection;
```

Trong ví dụ này, chú thích cuối trang được đặt ở cuối mỗi phần. Để đặt chúng ở cuối tài liệu, hãy sử dụng `EndnotePosition.EndOfDocument`.

## Bước 4: Lưu tài liệu

Cuối cùng, lưu tài liệu để áp dụng các thay đổi. Đảm bảo bạn chỉ định đúng đường dẫn tệp và tên cho tài liệu đầu ra.

```csharp
doc.Save(dataDir + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
```

Dòng này lưu tài liệu đã sửa đổi vào thư mục bạn chỉ định.

## Phần kết luận

Việc thiết lập vị trí chú thích cuối trang và chú thích cuối văn bản trong tài liệu Word bằng Aspose.Words cho .NET rất đơn giản khi bạn đã biết các bước. Bằng cách làm theo hướng dẫn này, bạn có thể tùy chỉnh tài liệu của mình theo nhu cầu, đảm bảo rằng chú thích cuối trang và chú thích cuối văn bản được định vị chính xác ở vị trí bạn muốn.

## Câu hỏi thường gặp

### Tôi có thể thiết lập các vị trí khác nhau cho từng chú thích cuối trang hoặc chú thích cuối văn bản không?

Không, Aspose.Words dành cho .NET sẽ thiết lập vị trí cho tất cả chú thích cuối trang và chú thích cuối văn bản trong một tài liệu một cách thống nhất.

### Aspose.Words for .NET có tương thích với tất cả các phiên bản tài liệu Word không?

Có, Aspose.Words for .NET hỗ trợ nhiều định dạng tài liệu Word, bao gồm DOC, DOCX, RTF, v.v.

### Tôi có thể sử dụng Aspose.Words cho .NET với các ngôn ngữ lập trình khác không?

Aspose.Words for .NET được thiết kế cho các ứng dụng .NET, nhưng bạn có thể sử dụng nó với bất kỳ ngôn ngữ nào hỗ trợ .NET như C#, VB.NET, v.v.

### Có bản dùng thử miễn phí Aspose.Words dành cho .NET không?

Có, bạn có thể dùng thử miễn phí [đây](https://releases.aspose.com/).

### Tôi có thể tìm tài liệu chi tiết hơn về Aspose.Words cho .NET ở đâu?

Tài liệu chi tiết có sẵn [đây](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}