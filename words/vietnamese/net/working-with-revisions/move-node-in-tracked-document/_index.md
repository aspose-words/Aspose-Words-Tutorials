---
"description": "Tìm hiểu cách di chuyển các nút trong tài liệu Word được theo dõi bằng Aspose.Words cho .NET với hướng dẫn chi tiết từng bước của chúng tôi. Hoàn hảo cho các nhà phát triển."
"linktitle": "Di chuyển nút trong tài liệu được theo dõi"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Di chuyển nút trong tài liệu được theo dõi"
"url": "/vi/net/working-with-revisions/move-node-in-tracked-document/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Di chuyển nút trong tài liệu được theo dõi

## Giới thiệu

Xin chào, những người đam mê Aspose.Words! Nếu bạn đã từng cần di chuyển một nút trong tài liệu Word trong khi theo dõi các bản sửa đổi, bạn đã đến đúng nơi rồi. Hôm nay, chúng ta sẽ tìm hiểu cách thực hiện việc này bằng Aspose.Words cho .NET. Bạn không chỉ học được quy trình từng bước mà còn học được một số mẹo và thủ thuật để thao tác tài liệu của mình một cách trơn tru và hiệu quả.

## Điều kiện tiên quyết

Trước khi bắt tay vào viết mã, hãy đảm bảo rằng bạn đã có mọi thứ mình cần:

- Aspose.Words cho .NET: Tải xuống [đây](https://releases.aspose.com/words/net/).
- Môi trường .NET: Đảm bảo bạn đã thiết lập môi trường phát triển .NET tương thích.
- Kiến thức cơ bản về C#: Hướng dẫn này giả định rằng bạn đã có hiểu biết cơ bản về C#.

Bạn đã hiểu hết chưa? Tuyệt! Hãy chuyển sang các không gian tên mà chúng ta cần nhập.

## Nhập không gian tên

Trước tiên, chúng ta cần nhập các không gian tên cần thiết. Đây là những điều cần thiết để làm việc với Aspose.Words và xử lý các nút tài liệu.

```csharp
using Aspose.Words;
using System;
```

Được rồi, chúng ta hãy chia nhỏ quy trình thành các bước dễ quản lý. Mỗi bước sẽ được giải thích chi tiết để đảm bảo bạn hiểu những gì đang diễn ra tại mọi thời điểm.

## Bước 1: Khởi tạo Tài liệu

Để bắt đầu, chúng ta cần khởi tạo một tài liệu mới và sử dụng `DocumentBuilder` để thêm một số đoạn văn.

```csharp
// Đường dẫn đến thư mục tài liệu.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Thêm một số đoạn văn
builder.Writeln("Paragraph 1");
builder.Writeln("Paragraph 2");
builder.Writeln("Paragraph 3");
builder.Writeln("Paragraph 4");
builder.Writeln("Paragraph 5");
builder.Writeln("Paragraph 6");

// Kiểm tra số lượng đoạn văn ban đầu
Body body = doc.FirstSection.Body;
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## Bước 2: Bắt đầu theo dõi bản sửa đổi

Tiếp theo, chúng ta cần bắt đầu theo dõi các bản sửa đổi. Điều này rất quan trọng vì nó cho phép chúng ta thấy những thay đổi được thực hiện đối với tài liệu.

```csharp
// Bắt đầu theo dõi các bản sửa đổi
doc.StartTrackRevisions("Author", new DateTime(2020, 12, 23, 14, 0, 0));
```

## Bước 3: Di chuyển các nút

Bây giờ đến phần cốt lõi của nhiệm vụ của chúng ta: di chuyển một nút từ vị trí này sang vị trí khác. Chúng ta sẽ di chuyển đoạn văn thứ ba và đặt nó trước đoạn văn đầu tiên.

```csharp
// Xác định nút cần di chuyển và phạm vi kết thúc của nó
Node node = body.Paragraphs[3];
Node endNode = body.Paragraphs[5].NextSibling;
Node referenceNode = body.Paragraphs[0];

// Di chuyển các nút trong phạm vi được xác định
while (node != endNode)
{
    Node nextNode = node.NextSibling;
    body.InsertBefore(node, referenceNode);
    node = nextNode;
}
```

## Bước 4: Dừng theo dõi bản sửa đổi

Sau khi di chuyển các nút, chúng ta cần dừng theo dõi các bản sửa đổi.

```csharp
// Dừng theo dõi sửa đổi
doc.StopTrackRevisions();
```

## Bước 5: Lưu tài liệu

Cuối cùng, hãy lưu tài liệu đã chỉnh sửa vào thư mục đã chỉ định.

```csharp
// Lưu tài liệu đã sửa đổi
doc.Save(dataDir + "WorkingWithRevisions.MoveNodeInTrackedDocument.docx");

// Xuất ra số lượng đoạn văn cuối cùng
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## Phần kết luận

Và thế là xong! Bạn đã di chuyển thành công một nút trong một tài liệu được theo dõi bằng Aspose.Words cho .NET. Thư viện mạnh mẽ này giúp bạn dễ dàng thao tác các tài liệu Word theo chương trình. Cho dù bạn đang tạo, chỉnh sửa hay theo dõi các thay đổi, Aspose.Words đều có thể giúp bạn. Vì vậy, hãy tiếp tục và thử. Chúc bạn lập trình vui vẻ!

## Câu hỏi thường gặp

### Aspose.Words dành cho .NET là gì?

Aspose.Words for .NET là một thư viện lớp để làm việc với các tài liệu Word theo chương trình. Nó cho phép các nhà phát triển tạo, chỉnh sửa, chuyển đổi và in các tài liệu Word trong các ứng dụng .NET.

### Làm thế nào để theo dõi các bản sửa đổi trong tài liệu Word bằng Aspose.Words?

Để theo dõi các bản sửa đổi, hãy sử dụng `StartTrackRevisions` phương pháp trên `Document` đối tượng. Điều này sẽ cho phép theo dõi bản sửa đổi, hiển thị mọi thay đổi được thực hiện đối với tài liệu.

### Tôi có thể di chuyển nhiều nút trong Aspose.Words không?

Có, bạn có thể di chuyển nhiều nút bằng cách lặp lại chúng và sử dụng các phương pháp như `InsertBefhoặce` or `InsertAfter` để đặt chúng ở vị trí mong muốn.

### Làm thế nào để tôi ngừng theo dõi bản sửa đổi trong Aspose.Words?

Sử dụng `StopTrackRevisions` phương pháp trên `Document` phản đối việc ngừng theo dõi bản sửa đổi.

### Tôi có thể tìm thêm tài liệu về Aspose.Words cho .NET ở đâu?

Bạn có thể tìm thấy tài liệu chi tiết [đây](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}