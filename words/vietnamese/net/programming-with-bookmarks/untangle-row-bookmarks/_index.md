---
title: Gỡ rối các dấu trang hàng trong tài liệu Word
linktitle: Gỡ rối các dấu trang hàng trong tài liệu Word
second_title: API xử lý tài liệu Aspose.Words
description: Gỡ rối các dấu trang hàng rối rắm trong tài liệu Word của bạn một cách dễ dàng bằng cách sử dụng Aspose.Words for .NET. Hướng dẫn này sẽ hướng dẫn bạn quy trình quản lý dấu trang sạch hơn và an toàn hơn.
weight: 10
url: /vi/net/programming-with-bookmarks/untangle-row-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Gỡ rối các dấu trang hàng trong tài liệu Word

## Giới thiệu

Bạn đã bao giờ gặp phải tình huống xóa một hàng trong tài liệu Word bằng một dấu trang sẽ làm rối các dấu trang khác ở các hàng liền kề chưa? Điều này có thể cực kỳ khó chịu, đặc biệt là khi xử lý các bảng phức tạp. Rất may, Aspose.Words for .NET cung cấp một giải pháp mạnh mẽ: gỡ rối các dấu trang hàng. 

Hướng dẫn này sẽ hướng dẫn bạn quy trình gỡ rối các dấu trang hàng trong tài liệu Word bằng Aspose.Words cho .NET. Chúng tôi sẽ chia mã thành các bước dễ hiểu và giải thích mục đích của từng chức năng, giúp bạn tự tin giải quyết các vấn đề về dấu trang rắc rối đó.

## Điều kiện tiên quyết

Trước khi đi sâu vào, bạn sẽ cần một vài điều:

1.  Aspose.Words for .NET: Thư viện thương mại này cung cấp các chức năng để làm việc với tài liệu Word theo chương trình. 2. Bạn có thể tải xuống bản dùng thử miễn phí từ[liên kết tải xuống](https://releases.aspose.com/words/net/) hoặc mua giấy phép từ[mua](https://purchase.aspose.com/buy).
3. Môi trường phát triển AC#: Visual Studio hoặc bất kỳ IDE C# nào khác sẽ hoạt động hoàn hảo.
4. Tài liệu Word có dấu trang hàng: Chúng tôi sẽ sử dụng tài liệu mẫu có tên "Dấu trang cột bảng.docx" cho mục đích minh họa.

## Nhập không gian tên

Bước đầu tiên liên quan đến việc nhập các không gian tên cần thiết vào dự án C# của bạn. Các không gian tên này cung cấp quyền truy cập vào các lớp và chức năng mà chúng tôi sẽ sử dụng từ Aspose.Words cho .NET:

```csharp
using Aspose.Words;
using System;
```

## Bước 1: Tải tài liệu Word

 Chúng tôi bắt đầu bằng cách tải tài liệu Word có chứa dấu trang hàng rối. các`Document` lớp xử lý thao tác tài liệu trong Aspose.Words. Đây là cách tải tài liệu:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // Thay thế bằng vị trí tài liệu của bạn
Document doc = new Document(dataDir + "Table column bookmarks.docx");
```

 Nhớ thay thế`"YOUR DOCUMENT DIRECTORY"` bằng đường dẫn thực tế tới tệp "Bookmarks.docx cột bảng" của bạn.

## Bước 2: Gỡ rối các dấu trang ở hàng

 Đây là nơi phép thuật xảy ra! các`Untangle` chức năng này đảm nhiệm việc gỡ rối các dấu trang hàng. Hãy chia nhỏ chức năng của nó:

```csharp
private void Untangle(Document doc)
{
   foreach (Bookmark bookmark in doc.Range.Bookmarks)
   {
	   // Lấy hàng cha của cả dấu trang và phần cuối dấu trang
	   Row row1 = (Row)bookmark.BookmarkStart.GetAncestor(typeof(Row));
	   Row row2 = (Row)bookmark.BookmarkEnd.GetAncestor(typeof(Row));

	   // Kiểm tra xem các hàng có hợp lệ và liền kề không
	   if (row1 != null && row2 != null && row1.NextSibling == row2)
		   //Di chuyển phần cuối dấu trang đến đoạn cuối cùng của ô cuối cùng ở hàng trên cùng
		   row1.LastCell.LastParagraph.AppendChild(bookmark.BookmarkEnd);
   }
}
```

Dưới đây là giải thích từng bước về chức năng của mã:

 Chúng tôi lặp qua tất cả dấu trang trong tài liệu bằng cách sử dụng`foreach` vòng lặp.
Đối với mỗi dấu trang, chúng tôi truy xuất hàng gốc của cả dấu trang bắt đầu (`bookmark.BookmarkStart`) và phần cuối dấu trang (`bookmark.BookmarkEnd` ) bằng cách sử dụng`GetAncestor` phương pháp.
Sau đó chúng tôi kiểm tra xem cả hai hàng có được tìm thấy không (`row1 != null`Và`row2 != null`) và nếu chúng là các hàng liền kề (`row1.NextSibling == row2`). Điều này đảm bảo chúng tôi chỉ sửa đổi dấu trang trải dài trên các hàng liền kề.
Nếu đáp ứng các điều kiện, chúng ta di chuyển nút cuối dấu trang đến cuối đoạn cuối trong ô cuối cùng của hàng trên cùng (`row1.LastCell.LastParagraph.AppendChild(bookmark.BookmarkEnd)`) gỡ rối chúng một cách hiệu quả.

## Bước 3: Xóa hàng theo dấu trang

 Bây giờ các dấu trang đã được gỡ rối, chúng ta có thể xóa các hàng bằng tên dấu trang của chúng một cách an toàn. các`DeleteRowByBookmark` Hàm xử lý tác vụ này:

```csharp
private void DeleteRowByBookmark(Document doc, string bookmarkName)
{
   Bookmark bookmark = doc.Range.Bookmarks[bookmarkName];

   Row row = (Row)bookmark?.BookmarkStart.GetAncestor(typeof(Row));
   row?.Remove();
}
```

Đây là bảng phân tích chức năng này:

Chúng tôi lấy tên dấu trang (`bookmarkName`) làm đầu vào.
 Chúng tôi truy xuất đối tượng đánh dấu tương ứng bằng cách sử dụng`doc.Range.Bookmarks[bookmarkName]`.
Sau đó chúng tôi lấy hàng gốc của dấu trang bắt đầu sử dụng`GetAncestor` (tương tự như`Untangle` chức năng).
Cuối cùng, chúng tôi kiểm tra xem dấu trang và hàng có tồn tại không (`bookmark != null` Và

## Bước 4: Xác minh gỡ rối

 Trong khi`Untangle` phải đảm bảo sự an toàn của các dấu trang khác, việc xác minh luôn là một cách tốt. Dưới đây là cách chúng tôi có thể kiểm tra xem quá trình gỡ rối có vô tình xóa phần cuối của dấu trang khác hay không:

```csharp
if (doc.Range.Bookmarks["ROW1"].BookmarkEnd == null)
   throw new Exception("Wrong, the end of the bookmark was deleted.");
```

Đoạn mã này kiểm tra xem phần cuối của dấu trang có tên "ROW1" có còn tồn tại sau khi xóa hàng có dấu trang "ROW2" hay không. Nếu nó là null, một ngoại lệ sẽ được đưa ra, cho biết có vấn đề với quá trình gỡ rối. 

## Bước 5: Lưu tài liệu

 Cuối cùng, sau khi gỡ rối các dấu trang và có khả năng xóa các hàng, hãy lưu tài liệu đã sửa đổi bằng cách sử dụng`Save` phương pháp:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

Thao tác này sẽ lưu tài liệu với các dấu trang đã được gỡ rối và mọi hàng đã xóa dưới tên tệp mới "WorkingWithBookmarks.UntangleRowBookmarks.docx". 

## Phần kết luận

 Bằng cách làm theo các bước sau và sử dụng`Untangle`chức năng, bạn có thể gỡ rối các dấu trang hàng trong tài liệu Word một cách hiệu quả bằng Aspose.Words for .NET. Điều này đảm bảo rằng việc xóa các hàng bằng dấu trang không gây ra hậu quả ngoài ý muốn với các dấu trang khác ở các hàng liền kề. Hãy nhớ thay thế phần giữ chỗ như`"YOUR DOCUMENT DIRECTORY"` với đường dẫn và tên tệp thực tế của bạn.

## Câu hỏi thường gặp

### Aspose.Words cho .NET có miễn phí không?

 Aspose.Words for .NET là một thư viện thương mại có bản dùng thử miễn phí. Bạn có thể tải nó xuống từ[liên kết tải xuống](https://releases.aspose.com/words/net/).

### Tôi có thể gỡ rối các dấu trang hàng trong Word theo cách thủ công không?

Mặc dù về mặt kỹ thuật có thể thực hiện được nhưng việc gỡ rối các dấu trang trong Word theo cách thủ công có thể tẻ nhạt và dễ xảy ra lỗi. Aspose.Words for .NET tự động hóa quá trình này, giúp bạn tiết kiệm thời gian và công sức.

###  Điều gì xảy ra nếu`Untangle` function encounters an error?

Mã bao gồm một trình xử lý ngoại lệ sẽ đưa ra một ngoại lệ nếu quá trình gỡ rối vô tình xóa phần cuối của một dấu trang khác. Bạn có thể tùy chỉnh việc xử lý lỗi này để phù hợp với nhu cầu cụ thể của mình.

### Tôi có thể sử dụng mã này để gỡ rối dấu trang trên các hàng không liền kề không?

Hiện tại, mã này tập trung vào việc gỡ rối các dấu trang trải dài trên các hàng liền kề. Việc sửa đổi mã để xử lý các hàng không liền kề sẽ yêu cầu logic bổ sung để xác định và xử lý các tình huống đó.

### Có bất kỳ hạn chế nào khi sử dụng phương pháp này không?

Cách tiếp cận này giả định rằng dấu trang được xác định rõ ràng trong các ô của bảng. Nếu dấu trang được đặt bên ngoài ô hoặc ở vị trí không mong muốn thì quá trình gỡ rối có thể không hoạt động như dự định.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
