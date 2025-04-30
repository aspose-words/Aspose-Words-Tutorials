---
"description": "Tìm hiểu cách thêm văn bản được đánh dấu vào tài liệu Word bằng Aspose.Words cho .NET với hướng dẫn từng bước này. Hoàn hảo cho các nhà phát triển."
"linktitle": "Thêm văn bản được đánh dấu vào tài liệu Word"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Thêm văn bản được đánh dấu vào tài liệu Word"
"url": "/vi/net/programming-with-bookmarks/append-bookmarked-text/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Thêm văn bản được đánh dấu vào tài liệu Word

## Giới thiệu

Xin chào! Bạn đã bao giờ thử thêm văn bản từ một phần được đánh dấu vào tài liệu Word và thấy khó khăn chưa? Bạn thật may mắn! Hướng dẫn này sẽ hướng dẫn bạn thực hiện quy trình bằng Aspose.Words cho .NET. Chúng tôi sẽ chia nhỏ thành các bước đơn giản để bạn có thể dễ dàng thực hiện. Hãy cùng bắt đầu và thêm văn bản được đánh dấu đó như một chuyên gia!

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo rằng bạn có mọi thứ cần thiết:

- Aspose.Words cho .NET: Hãy đảm bảo bạn đã cài đặt nó. Nếu chưa, bạn có thể [tải xuống ở đây](https://releases.aspose.com/words/net/).
- Môi trường phát triển: Bất kỳ môi trường phát triển .NET nào như Visual Studio.
- Kiến thức cơ bản về C#: Hiểu các khái niệm lập trình C# cơ bản sẽ giúp ích.
- Tài liệu Word có dấu trang: Tài liệu Word có dấu trang được thiết lập, chúng ta sẽ sử dụng dấu trang này để thêm văn bản.

## Nhập không gian tên

Trước tiên, hãy nhập các không gian tên cần thiết. Điều này sẽ đảm bảo chúng ta có tất cả các công cụ cần thiết trong tầm tay.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Importing;
```

Chúng ta hãy chia nhỏ ví dụ thành các bước chi tiết.

## Bước 1: Tải Tài liệu và Khởi tạo Biến

Được rồi, chúng ta hãy bắt đầu bằng cách tải tài liệu Word và khởi tạo các biến mà chúng ta cần.

```csharp
// Tải tài liệu nguồn và đích.
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");

// Khởi tạo trình nhập tài liệu.
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);

// Tìm dấu trang trong tài liệu nguồn.
Bookmark srcBookmark = srcDoc.Range.Bookmarks["YourBookmarkName"];
```

## Bước 2: Xác định đoạn văn bắt đầu và kết thúc

Bây giờ, hãy xác định vị trí các đoạn văn mà dấu trang bắt đầu và kết thúc. Điều này rất quan trọng vì chúng ta cần xử lý văn bản trong các giới hạn này.

```csharp
// Đây là đoạn văn chứa phần mở đầu của dấu trang.
Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;

// Đây là đoạn văn chứa nội dung kết thúc của dấu trang.
Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

if (startPara == null || endPara == null)
    throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");
```

## Bước 3: Xác thực đoạn văn cha

Chúng ta cần đảm bảo đoạn mở đầu và kết thúc có cùng phần cha. Đây là một kịch bản đơn giản để giữ mọi thứ đơn giản.

```csharp
// Giới hạn bản thân vào một kịch bản khá đơn giản.
if (startPara.ParentNode != endPara.ParentNode)
    throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");
```

## Bước 4: Xác định nút cần dừng

Tiếp theo, chúng ta cần xác định nút mà chúng ta sẽ dừng sao chép văn bản. Đây sẽ là nút ngay sau đoạn văn kết thúc.

```csharp
// Chúng tôi muốn sao chép tất cả các đoạn văn từ đoạn văn đầu cho đến (và bao gồm) đoạn văn cuối,
// do đó nút mà chúng ta dừng lại là nút sau đoạn kết thúc.
Node endNode = endPara.NextSibling;
```

## Bước 5: Thêm văn bản được đánh dấu vào tài liệu đích

Cuối cùng, hãy lặp qua các nút từ đoạn văn bắt đầu đến nút sau đoạn văn kết thúc và thêm chúng vào tài liệu đích.

```csharp
for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
{
    // Điều này tạo ra một bản sao của nút hiện tại và nhập nó (làm cho nó hợp lệ) trong ngữ cảnh
    // của tài liệu đích. Nhập có nghĩa là điều chỉnh kiểu và danh sách định danh một cách chính xác.
    Node newNode = importer.ImportNode(curNode, true);

    // Thêm nút đã nhập vào tài liệu đích.
    dstDoc.FirstSection.Body.AppendChild(newNode);
}

// Lưu tài liệu đích cùng với văn bản được thêm vào.
dstDoc.Save("appended_document.docx");
```

## Phần kết luận

Và thế là xong! Bạn đã thêm thành công văn bản từ một phần được đánh dấu trong tài liệu Word bằng Aspose.Words cho .NET. Công cụ mạnh mẽ này giúp việc thao tác tài liệu trở nên dễ dàng và giờ bạn có thêm một mẹo nữa. Chúc bạn viết mã vui vẻ!

## Câu hỏi thường gặp

### Tôi có thể thêm văn bản từ nhiều dấu trang cùng một lúc không?
Có, bạn có thể lặp lại quy trình này cho từng dấu trang và thêm văn bản cho phù hợp.

### Nếu đoạn mở đầu và đoạn kết có phần cha khác nhau thì sao?
Ví dụ hiện tại giả định chúng có cùng cha mẹ. Đối với các cha mẹ khác nhau, cần phải xử lý phức tạp hơn.

### Tôi có thể giữ nguyên định dạng gốc của văn bản được thêm vào không?
Chắc chắn rồi! `ImportFormatMode.KeepSourceFormatting` đảm bảo định dạng ban đầu được giữ nguyên.

### Có thể thêm văn bản vào vị trí cụ thể trong tài liệu đích không?
Có, bạn có thể thêm văn bản vào bất kỳ vị trí nào bằng cách điều hướng đến nút mong muốn trong tài liệu đích.

### Tôi phải làm sao nếu cần thêm văn bản từ dấu trang vào phần mới?
Bạn có thể tạo một phần mới trong tài liệu đích và thêm văn bản vào đó.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}