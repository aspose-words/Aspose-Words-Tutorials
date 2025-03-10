---
title: Hiển thị Ẩn dấu trang trong tài liệu Word
linktitle: Hiển thị Ẩn dấu trang trong tài liệu Word
second_title: API xử lý tài liệu Aspose.Words
description: Tìm hiểu cách tự động hiển thị hoặc ẩn dấu trang trong tài liệu Word bằng Aspose.Words cho .NET với hướng dẫn từng bước của chúng tôi. Hoàn hảo cho các nhà phát triển.
weight: 10
url: /vi/net/programming-with-bookmarks/show-hide-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hiển thị Ẩn dấu trang trong tài liệu Word

## Giới thiệu

Bạn có bao giờ thấy mình cần ẩn hoặc hiển thị một số phần nhất định trong tài liệu Word của mình một cách linh hoạt không? Vâng, bạn thật may mắn! Với Aspose.Words for .NET, bạn có thể dễ dàng quản lý khả năng hiển thị nội dung được đánh dấu trong tài liệu của mình. Hướng dẫn này sẽ hướng dẫn bạn quy trình hiển thị và ẩn dấu trang trong tài liệu Word bằng Aspose.Words cho .NET. Chúng tôi sẽ chia nhỏ mã theo từng bước, vì vậy, cho dù bạn là nhà phát triển dày dạn kinh nghiệm hay người mới, bạn sẽ thấy hướng dẫn này dễ làm theo.

## Điều kiện tiên quyết

Trước khi đi sâu vào mã, hãy đảm bảo bạn có mọi thứ mình cần:

1.  Aspose.Words for .NET: Đảm bảo bạn đã cài đặt thư viện Aspose.Words for .NET. Nếu không, bạn có thể tải xuống[đây](https://releases.aspose.com/words/net/).
2. Môi trường phát triển: Một IDE như Visual Studio.
3. Kiến thức cơ bản về C#: Làm quen với lập trình C# sẽ có lợi.
4. Tài liệu Word: Tài liệu Word mẫu có dấu trang.

## Nhập không gian tên

Trước khi bắt đầu với mã, bạn cần nhập các không gian tên cần thiết. Thêm phần sau vào đầu tệp C# của bạn:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

## Bước 1: Tải tài liệu của bạn

Trước tiên, bạn cần tải tài liệu Word có chứa dấu trang. Đây là cách bạn có thể làm điều đó:

```csharp
// Đường dẫn đến thư mục tài liệu.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

### Giải trình

- dataDir: Đây là đường dẫn thư mục chứa tài liệu Word của bạn.
-  Tài liệu doc: Thao tác này khởi tạo một phiên bản mới của`Document` class bằng tệp được chỉ định của bạn.

## Bước 2: Hiển thị hoặc ẩn nội dung được đánh dấu

Tiếp theo, chúng tôi sẽ xác định phương pháp hiển thị hoặc ẩn nội dung được đánh dấu. Đây là phương pháp hoàn chỉnh:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool showHide)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.MoveToDocumentEnd();

    // {IF "{Dấu trang MERGEFIELD}" = "true" "" ""}
    Field field = builder.InsertField("IF \"", null);
    builder.MoveTo(field.Start.NextSibling);
    builder.InsertField("MERGEFIELD " + bookmarkName + "", null);
    builder.Write("\" = \"true\" ");
    builder.Write("\"");
    builder.Write("\"");
    builder.Write(" \"\"");

    Node currentNode = field.Start;
    bool flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.Run)
            if (currentNode.ToString(SaveFormat.Text).Trim() == "\"")
                flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkStart.ParentNode.InsertBefore(currentNode, bm.BookmarkStart);
        currentNode = nextNode;
    }

    Node endNode = bm.BookmarkEnd;
    flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.FieldEnd)
            flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkEnd.ParentNode.InsertAfter(currentNode, endNode);
        endNode = currentNode;
        currentNode = nextNode;
    }

    doc.MailMerge.Execute(new[] { bookmarkName }, new object[] { showHide });
}
```

### Giải trình

- Bookmark bm: Lấy dấu trang từ tài liệu.
- Trình tạo DocumentBuilder: Giúp điều hướng và sửa đổi tài liệu.
- Trường trường: Chèn trường IF để kiểm tra tình trạng của dấu trang.
- Node currentNode: Duyệt qua các nút để tìm điểm bắt đầu và kết thúc của trường.

## Bước 3: Thực hiện chức năng Hiển thị/Ẩn

 Bây giờ, bạn cần gọi`ShowHideBookmarkedContent` phương thức, chuyển tài liệu, tên dấu trang và cờ hiển thị:

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", false);
```

### Giải trình

- doc: Đối tượng tài liệu của bạn.
- "MyBookmark1": Tên của bookmark bạn muốn hiển thị/ẩn.
- false: Cờ hiển thị (true để hiển thị, sai để ẩn).

## Bước 4: Lưu tài liệu của bạn

Cuối cùng, lưu tài liệu đã sửa đổi:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Giải trình

- dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx": Đường dẫn và tên của tài liệu mới nơi các thay đổi sẽ được lưu.

## Phần kết luận

Và bạn có nó rồi đấy! Bạn đã học thành công cách hiển thị và ẩn dấu trang trong tài liệu Word bằng Aspose.Words cho .NET. Kỹ thuật này có thể cực kỳ hữu ích để tạo động các tài liệu có nội dung có điều kiện.

## Câu hỏi thường gặp

### Aspose.Words cho .NET là gì?
Aspose.Words for .NET là một thư viện xử lý tài liệu mạnh mẽ cho phép các nhà phát triển tạo, sửa đổi và chuyển đổi tài liệu Word theo chương trình.

### Làm cách nào để có được Aspose.Words cho .NET?
 Bạn có thể tải xuống Aspose.Words cho .NET từ[đây](https://releases.aspose.com/words/net/). Bản dùng thử miễn phí cũng có sẵn.

### Tôi có thể sử dụng phương pháp này cho các loại dấu trang khác không?
Có, phương pháp này có thể được điều chỉnh để quản lý khả năng hiển thị của mọi dấu trang trong tài liệu Word của bạn.

### Điều gì sẽ xảy ra nếu tài liệu của tôi không chứa dấu trang được chỉ định?
Nếu dấu trang không tồn tại, phương thức sẽ báo lỗi. Đảm bảo dấu trang tồn tại trước khi thử hiển thị/ẩn nó.

### Làm cách nào tôi có thể nhận được hỗ trợ nếu gặp sự cố?
 Bạn có thể nhận được hỗ trợ từ cộng đồng Aspose[đây](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
