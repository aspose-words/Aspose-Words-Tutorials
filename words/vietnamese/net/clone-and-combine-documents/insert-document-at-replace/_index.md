---
title: Chèn Tài Liệu Vào Thay Thế
linktitle: Chèn Tài Liệu Vào Thay Thế
second_title: API xử lý tài liệu Aspose.Words
description: Tìm hiểu cách chèn liền mạch một tài liệu Word vào tài liệu khác bằng Aspose.Words cho .NET với hướng dẫn chi tiết từng bước của chúng tôi. Hoàn hảo cho các nhà phát triển muốn hợp lý hóa quá trình xử lý tài liệu.
weight: 10
url: /vi/net/clone-and-combine-documents/insert-document-at-replace/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Chèn Tài Liệu Vào Thay Thế

## Giới thiệu

Xin chào, các bậc thầy về tài liệu! Bạn đã bao giờ thấy mình đang loay hoay trong mã lệnh, cố gắng tìm cách chèn một tài liệu Word vào một tài liệu Word khác một cách liền mạch chưa? Đừng lo, vì hôm nay chúng ta sẽ khám phá thế giới của Aspose.Words dành cho .NET để biến nhiệm vụ đó trở nên dễ dàng. Chúng ta sẽ hướng dẫn chi tiết từng bước về cách sử dụng thư viện mạnh mẽ này để chèn tài liệu tại các điểm cụ thể trong quá trình tìm và thay thế. Bạn đã sẵn sàng trở thành một phù thủy Aspose.Words chưa? Hãy bắt đầu thôi!

## Điều kiện tiên quyết

Trước khi tìm hiểu về mã, bạn cần chuẩn bị một số thứ sau:

-  Visual Studio: Đảm bảo bạn đã cài đặt Visual Studio trên máy của mình. Nếu bạn chưa có, bạn có thể tải xuống từ[đây](https://visualstudio.microsoft.com/).
-  Aspose.Words cho .NET: Bạn sẽ cần thư viện Aspose.Words. Bạn có thể lấy nó từ[Trang web Aspose](https://releases.aspose.com/words/net/).
- Kiến thức cơ bản về C#: Hiểu biết cơ bản về C# và .NET sẽ giúp bạn theo dõi hướng dẫn này.

Được rồi, sau khi đã giải quyết xong những vấn đề đó, chúng ta hãy cùng bắt tay vào viết mã nhé!

## Nhập không gian tên

Trước tiên, chúng ta cần import các namespace cần thiết để làm việc với Aspose.Words. Điều này giống như việc tập hợp tất cả các công cụ của bạn trước khi bắt đầu một dự án. Thêm các chỉ thị using này vào đầu tệp C# của bạn:

```csharp
using System;
using System.Text.RegularExpressions;
using Aspose.Words;
using Aspose.Words.Replacing;
using Aspose.Words.Tables;
```

Bây giờ chúng ta đã có đủ điều kiện tiên quyết, hãy chia nhỏ quy trình thành các bước nhỏ. Mỗi bước đều quan trọng và sẽ đưa chúng ta đến gần hơn với mục tiêu của mình.

## Bước 1: Thiết lập thư mục tài liệu

Đầu tiên, chúng ta cần chỉ định thư mục lưu trữ tài liệu của mình. Điều này giống như việc chuẩn bị sân khấu trước buổi biểu diễn lớn.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Thay thế`"YOUR DOCUMENT DIRECTORY"` với đường dẫn đến thư mục của bạn. Đây là nơi tài liệu của bạn sẽ tồn tại và phát triển.

## Bước 2: Tải Tài liệu Chính

Tiếp theo, chúng ta tải tài liệu chính mà chúng ta muốn chèn một tài liệu khác vào. Hãy coi đây là sân khấu chính của chúng ta, nơi mọi hành động sẽ diễn ra.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

Đoạn mã này tải tài liệu chính từ thư mục được chỉ định.

## Bước 3: Thiết lập tùy chọn Tìm và Thay thế

Để tìm vị trí cụ thể mà chúng ta muốn chèn tài liệu, chúng ta sử dụng chức năng tìm và thay thế. Điều này giống như sử dụng bản đồ để tìm vị trí chính xác cho phần bổ sung mới của chúng ta.

```csharp
FindReplaceOptions options = new FindReplaceOptions
{
    Direction = FindReplaceDirection.Backward,
    ReplacingCallback = new InsertDocumentAtReplaceHandler()
};
```

Ở đây, chúng ta thiết lập hướng ngược lại và chỉ định trình xử lý gọi lại tùy chỉnh mà chúng ta sẽ xác định tiếp theo.

## Bước 4: Thực hiện thao tác thay thế

Bây giờ, chúng ta yêu cầu tài liệu chính tìm kiếm một văn bản giữ chỗ cụ thể và thay thế nó bằng không, trong khi sử dụng lệnh gọi lại tùy chỉnh để chèn một tài liệu khác.

```csharp
mainDoc.Range.Replace(new Regex("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

Mã này thực hiện thao tác tìm kiếm và thay thế, sau đó lưu tài liệu đã cập nhật.

## Bước 5: Tạo Trình xử lý Gọi lại Thay thế Tùy chỉnh

Trình xử lý gọi lại tùy chỉnh của chúng tôi là nơi phép thuật xảy ra. Trình xử lý này sẽ xác định cách chèn tài liệu được thực hiện trong quá trình tìm và thay thế.

```csharp
private class InsertDocumentAtReplaceHandler : IReplacingCallback
{
    ReplaceAction IReplacingCallback.Replacing(ReplacingArgs args)
    {
        Document subDoc = new Document(dataDir + "Document insertion 2.docx");

        // Chèn một tài liệu sau đoạn văn có chứa văn bản phù hợp.
        Paragraph para = (Paragraph)args.MatchNode.ParentNode;
        InsertDocument(para, subDoc);

        // Xóa đoạn văn có văn bản trùng khớp.
        para.Remove();
        return ReplaceAction.Skip;
    }
}
```

Ở đây, chúng ta tải tài liệu cần chèn và sau đó gọi phương thức trợ giúp để thực hiện việc chèn.

## Bước 6: Xác định phương pháp chèn tài liệu

Mảnh ghép cuối cùng của câu đố chính là phương pháp chèn tài liệu vào vị trí đã chỉ định.

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    // Kiểm tra xem đích chèn là Đoạn văn hay Bảng
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;

        // Tạo NodeImporter để nhập các nút từ tài liệu nguồn
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        // Lặp qua tất cả các nút cấp khối trong các phần của tài liệu nguồn
        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        {
            foreach (Node srcNode in srcSection.Body)
            {
                // Bỏ qua đoạn văn trống cuối cùng của một phần
                if (srcNode.NodeType == NodeType.Paragraph)
                {
                    Paragraph para = (Paragraph)srcNode;
                    if (para.IsEndOfSection && !para.HasChildNodes)
                        continue;
                }

                // Nhập và chèn nút vào đích
                Node newNode = importer.ImportNode(srcNode, true);
                destinationParent.InsertAfter(newNode, insertionDestination);
                insertionDestination = newNode;
            }
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}

```

Phương pháp này xử lý việc nhập các nút từ tài liệu cần chèn và đặt chúng vào đúng vị trí trong tài liệu chính.

## Phần kết luận

Và bạn đã có nó! Hướng dẫn toàn diện về cách chèn một tài liệu vào tài liệu khác bằng Aspose.Words cho .NET. Bằng cách làm theo các bước này, bạn có thể dễ dàng tự động hóa các tác vụ lắp ráp và thao tác tài liệu. Cho dù bạn đang xây dựng hệ thống quản lý tài liệu hay chỉ cần hợp lý hóa quy trình xử lý tài liệu của mình, Aspose.Words chính là trợ thủ đáng tin cậy của bạn.

## Câu hỏi thường gặp

### Aspose.Words dành cho .NET là gì?
Aspose.Words for .NET là một thư viện mạnh mẽ để thao tác các tài liệu Word theo chương trình. Nó cho phép bạn tạo, sửa đổi, chuyển đổi và xử lý các tài liệu Word một cách dễ dàng.

### Tôi có thể chèn nhiều tài liệu cùng một lúc không?
Có, bạn có thể sửa đổi trình xử lý gọi lại để xử lý nhiều lần chèn bằng cách lặp qua một tập hợp tài liệu.

### Có bản dùng thử miễn phí không?
 Chắc chắn rồi! Bạn có thể tải xuống bản dùng thử miễn phí từ[đây](https://releases.aspose.com/).

### Làm thế nào để tôi nhận được hỗ trợ cho Aspose.Words?
 Bạn có thể nhận được hỗ trợ bằng cách truy cập[Diễn đàn Aspose.Words](https://forum.aspose.com/c/words/8).

### Tôi có thể giữ nguyên định dạng của tài liệu đã chèn không?
 Vâng,`NodeImporter` Lớp này cho phép bạn chỉ định cách xử lý định dạng khi nhập các nút từ tài liệu này sang tài liệu khác.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
