---
title: Hiển thị Ẩn Nội dung được Đánh dấu trong Tài liệu Word
linktitle: Hiển thị Ẩn Nội dung được Đánh dấu trong Tài liệu Word
second_title: API xử lý tài liệu Aspose.Words
description: Tìm hiểu cách hiển thị và ẩn nội dung được đánh dấu trong tài liệu Word bằng Aspose.Words cho .NET với hướng dẫn chi tiết từng bước này.
weight: 10
url: /vi/net/programming-with-bookmarks/show-hide-bookmarked-content/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hiển thị Ẩn Nội dung được Đánh dấu trong Tài liệu Word

## Giới thiệu

Sẵn sàng khám phá thế giới thao tác tài liệu với Aspose.Words for .NET? Cho dù bạn là nhà phát triển muốn tự động hóa các tác vụ tài liệu hay chỉ là người tò mò về cách xử lý các tệp Word theo chương trình, bạn đã đến đúng nơi. Hôm nay, chúng ta sẽ khám phá cách hiển thị và ẩn nội dung được đánh dấu trong tài liệu Word bằng Aspose.Words for .NET. Hướng dẫn từng bước này sẽ giúp bạn trở thành chuyên gia trong việc kiểm soát khả năng hiển thị nội dung dựa trên dấu trang. Hãy bắt đầu nào!

## Điều kiện tiên quyết

Trước khi đi sâu vào vấn đề chính, bạn cần có một số thứ sau:

1. Visual Studio: Bất kỳ phiên bản nào tương thích với .NET.
2.  Aspose.Words cho .NET: Tải xuống[đây](https://releases.aspose.com/words/net/).
3. Hiểu biết cơ bản về C#: Nếu bạn có thể viết chương trình "Hello World" đơn giản thì bạn đã sẵn sàng rồi.
4. Tài liệu Word có dấu trang: Chúng tôi sẽ sử dụng một tài liệu mẫu có dấu trang cho hướng dẫn này.

## Nhập không gian tên

Trước tiên, hãy nhập các không gian tên cần thiết. Điều này đảm bảo chúng ta có tất cả các công cụ cần thiết cho nhiệm vụ của mình.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

Với những không gian tên này, chúng ta đã sẵn sàng bắt đầu hành trình.

## Bước 1: Thiết lập dự án của bạn

Được rồi, chúng ta hãy bắt đầu bằng cách thiết lập dự án trong Visual Studio.

### Tạo một dự án mới

Mở Visual Studio và tạo một dự án Console App (.NET Core) mới. Đặt tên cho nó là một cái tên hấp dẫn, như "BookmarkVisibilityManager".

### Thêm Aspose.Words cho .NET

Bạn sẽ cần thêm Aspose.Words cho .NET vào dự án của mình. Bạn có thể thực hiện việc này thông qua NuGet Package Manager.

1. Vào Công cụ > Trình quản lý gói NuGet > Quản lý gói NuGet cho Solution.
2. Tìm kiếm "Aspose.Words".
3. Cài đặt gói.

Tuyệt! Bây giờ dự án của chúng ta đã được thiết lập, hãy chuyển sang tải tài liệu.

## Bước 2: Tải tài liệu

Chúng ta cần tải tài liệu Word có chứa các dấu trang. Đối với hướng dẫn này, chúng ta sẽ sử dụng một tài liệu mẫu có tên là "Bookmarks.docx".

```csharp
// Đường dẫn đến thư mục tài liệu.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

 Đoạn mã này thiết lập đường dẫn đến thư mục tài liệu của bạn và tải tài liệu vào`doc` sự vật.

## Bước 3: Hiển thị/Ẩn Nội dung được Đánh dấu

Bây giờ đến phần thú vị – hiển thị hoặc ẩn nội dung dựa trên dấu trang. Chúng ta sẽ tạo một phương thức có tên là`ShowHideBookmarkedContent` để xử lý việc này.

Sau đây là phương pháp chuyển đổi chế độ hiển thị của nội dung được đánh dấu:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool isHidden)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    Node currentNode = bm.BookmarkStart;
    while (currentNode != null && currentNode.NodeType != NodeType.BookmarkEnd)
    {
        if (currentNode.NodeType == NodeType.Run)
        {
            Run run = currentNode as Run;
            run.Font.Hidden = isHidden;
        }
        currentNode = currentNode.NextSibling;
    }
}
```

### Phân tích phương pháp

-  Lấy lại dấu trang:`Bookmark bm = doc.Range.Bookmarks[bookmarkName];` lấy dấu trang.
- Duyệt nút: Chúng ta duyệt các nút trong dấu trang.
-  Chuyển đổi khả năng hiển thị: Nếu nút là một`Run` (một đoạn văn bản liên tiếp), chúng tôi thiết lập nó`Hidden` tài sản.

## Bước 4: Áp dụng phương pháp

Sau khi đã có phương pháp, hãy áp dụng nó để hiển thị hoặc ẩn nội dung dựa trên dấu trang.

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true);
```

Dòng mã này sẽ ẩn nội dung bên trong dấu trang có tên "MyBookmark1".

## Bước 5: Lưu tài liệu

Cuối cùng, hãy lưu tài liệu đã chỉnh sửa.

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

Thao tác này sẽ lưu tài liệu với những thay đổi chúng ta đã thực hiện.

## Phần kết luận

Và bạn đã có nó! Bạn vừa học cách hiển thị và ẩn nội dung được đánh dấu trong tài liệu Word bằng Aspose.Words cho .NET. Công cụ mạnh mẽ này giúp thao tác tài liệu trở nên dễ dàng, cho dù bạn đang tự động hóa báo cáo, tạo mẫu hay chỉ chỉnh sửa tệp Word. Chúc bạn viết mã vui vẻ!

## Câu hỏi thường gặp

### Tôi có thể chuyển đổi nhiều dấu trang cùng lúc không?
 Vâng, bạn có thể gọi`ShowHideBookmarkedContent` phương pháp cho mỗi dấu trang bạn muốn chuyển đổi.

### Việc ẩn nội dung có ảnh hưởng đến cấu trúc tài liệu không?
Không, việc ẩn nội dung chỉ ảnh hưởng đến khả năng hiển thị của nội dung đó. Nội dung vẫn nằm trong tài liệu.

### Tôi có thể sử dụng phương pháp này cho các loại nội dung khác không?
Phương pháp này đặc biệt chuyển đổi các lần chạy văn bản. Đối với các loại nội dung khác, bạn sẽ cần phải sửa đổi logic duyệt nút.

### Aspose.Words cho .NET có miễn phí không?
 Aspose.Words cung cấp bản dùng thử miễn phí[đây](https://releases.aspose.com/) , nhưng cần có giấy phép đầy đủ để sử dụng sản xuất. Bạn có thể mua nó[đây](https://purchase.aspose.com/buy).

### Tôi có thể nhận được hỗ trợ như thế nào nếu gặp vấn đề?
 Bạn có thể nhận được sự hỗ trợ từ cộng đồng Aspose[đây](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
