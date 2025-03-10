---
title: Sửa đổi Kiểm soát Nội dung
linktitle: Sửa đổi Kiểm soát Nội dung
second_title: API xử lý tài liệu Aspose.Words
description: Tìm hiểu cách sửa đổi thẻ tài liệu có cấu trúc trong Word bằng Aspose.Words cho .NET. Cập nhật văn bản, danh sách thả xuống và hình ảnh từng bước.
weight: 10
url: /vi/net/programming-with-sdt/modify-content-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Sửa đổi Kiểm soát Nội dung

## Giới thiệu

Nếu bạn đã từng làm việc với các tài liệu Word và cần sửa đổi các điều khiển nội dung có cấu trúc—như văn bản thuần túy, danh sách thả xuống hoặc hình ảnh—bằng Aspose.Words cho .NET, bạn đã đến đúng nơi rồi! Thẻ tài liệu có cấu trúc (SDT) là các công cụ mạnh mẽ giúp tự động hóa tài liệu dễ dàng và linh hoạt hơn. Trong hướng dẫn này, chúng tôi sẽ đi sâu vào cách bạn có thể sửa đổi các SDT này để phù hợp với nhu cầu của mình. Cho dù bạn đang cập nhật văn bản, thay đổi các lựa chọn thả xuống hay hoán đổi hình ảnh, hướng dẫn này sẽ hướng dẫn bạn từng bước trong quy trình.

## Điều kiện tiên quyết

Trước khi đi sâu vào việc sửa đổi các điều khiển nội dung, hãy đảm bảo bạn có những điều sau:

1.  Đã cài đặt Aspose.Words cho .NET: Đảm bảo bạn đã cài đặt thư viện Aspose.Words. Nếu chưa, bạn có thể[tải xuống ở đây](https://releases.aspose.com/words/net/).

2. Kiến thức cơ bản về C#: Hướng dẫn này giả định rằng bạn đã quen thuộc với các khái niệm lập trình C# cơ bản.

3. Môi trường phát triển .NET: Bạn nên thiết lập một IDE như Visual Studio để chạy các ứng dụng .NET.

4. Tài liệu mẫu: Chúng tôi sẽ sử dụng một tài liệu Word mẫu với nhiều loại SDT khác nhau. Bạn có thể sử dụng tài liệu trong ví dụ hoặc tự tạo tài liệu của riêng mình.

5.  Truy cập vào Tài liệu Aspose: Để biết thông tin chi tiết hơn, hãy xem[Tài liệu Aspose.Words](https://reference.aspose.com/words/net/).

## Nhập không gian tên

Để bắt đầu làm việc với Aspose.Words, bạn cần nhập các không gian tên có liên quan vào dự án C# của mình. Sau đây là cách thực hiện:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Các không gian tên này sẽ cung cấp cho bạn quyền truy cập vào các lớp và phương thức cần thiết để thao tác các thẻ tài liệu có cấu trúc trong tài liệu Word của bạn.

## Bước 1: Thiết lập đường dẫn tài liệu của bạn

 Trước khi thực hiện bất kỳ thay đổi nào, bạn cần chỉ định đường dẫn đến tài liệu của mình. Thay thế`"YOUR DOCUMENT DIRECTORY"` với đường dẫn thực tế nơi tài liệu của bạn được lưu trữ.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Structured document tags.docx");
```

## Bước 2: Lặp qua các thẻ tài liệu có cấu trúc

 Để sửa đổi SDT, trước tiên bạn cần lặp qua tất cả SDT trong tài liệu. Điều này được thực hiện bằng cách sử dụng`GetChildNodes` phương pháp để lấy tất cả các nút có kiểu`StructuredDocumentTag`.

```csharp
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    // Sửa đổi SDT dựa trên loại của chúng
}
```

## Bước 3: Sửa đổi SDT văn bản thuần túy

Nếu SDT là loại văn bản thuần túy, bạn có thể thay thế nội dung của nó. Trước tiên, xóa nội dung hiện có, sau đó thêm văn bản mới.

```csharp
if (sdt.SdtType == SdtType.PlainText)
{
    sdt.RemoveAllChildren();
    Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
    Run run = new Run(doc, "new text goes here");
    para.AppendChild(run);
}
```

 Giải thích: Ở đây,`RemoveAllChildren()`xóa nội dung hiện có của SDT. Sau đó chúng tôi tạo một nội dung mới`Paragraph` Và`Run` đối tượng để chèn văn bản mới.

## Bước 4: Sửa đổi SDT của danh sách thả xuống

 Đối với danh sách thả xuống SDT, bạn có thể thay đổi mục đã chọn bằng cách truy cập`ListItems` bộ sưu tập. Ở đây, chúng ta chọn mục thứ ba trong danh sách.

```csharp
if (sdt.SdtType == SdtType.DropDownList)
{
    SdtListItem secondItem = sdt.ListItems[2];
    sdt.ListItems.SelectedValue = secondItem;
}
```

Giải thích: Đoạn mã này chọn mục ở chỉ mục 2 (mục thứ ba) từ danh sách thả xuống. Điều chỉnh chỉ mục dựa trên nhu cầu của bạn.

## Bước 5: Sửa đổi SDT của hình ảnh

Để cập nhật hình ảnh trong SDT hình ảnh, bạn có thể thay thế hình ảnh hiện tại bằng hình ảnh mới.

```csharp
if (sdt.SdtType == SdtType.Picture)
{
    Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
    if (shape.HasImage)
    {
        shape.ImageData.SetImage(ImagesDir + "Watermark.png");
    }
}
```

 Giải thích: Mã này kiểm tra xem hình dạng có chứa hình ảnh hay không và sau đó thay thế nó bằng một hình ảnh mới nằm tại`ImagesDir`.

## Bước 6: Lưu tài liệu đã sửa đổi của bạn

Sau khi thực hiện tất cả các thay đổi cần thiết, hãy lưu tài liệu đã sửa đổi với tên mới để giữ nguyên tài liệu gốc.

```csharp
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");
```

Giải thích: Thao tác này sẽ lưu tài liệu với tên tệp mới để bạn có thể dễ dàng phân biệt với tệp gốc.

## Phần kết luận

Việc sửa đổi các điều khiển nội dung trong tài liệu Word bằng Aspose.Words cho .NET rất đơn giản khi bạn hiểu các bước liên quan. Cho dù bạn đang cập nhật văn bản, thay đổi lựa chọn thả xuống hay hoán đổi hình ảnh, Aspose.Words đều cung cấp API mạnh mẽ cho các tác vụ này. Bằng cách làm theo hướng dẫn này, bạn có thể quản lý và tùy chỉnh hiệu quả các điều khiển nội dung có cấu trúc của tài liệu, giúp tài liệu của bạn năng động hơn và phù hợp hơn với nhu cầu của bạn.

## Câu hỏi thường gặp

1. Thẻ tài liệu có cấu trúc (SDT) là gì?

SDT là các thành phần trong tài liệu Word giúp quản lý và định dạng nội dung tài liệu, như hộp văn bản, danh sách thả xuống hoặc hình ảnh.

2. Làm thế nào để thêm mục thả xuống mới vào SDT?

 Để thêm một mục mới, hãy sử dụng`ListItems` thuộc tính và thêm một cái mới`SdtListItem` vào bộ sưu tập.

3. Tôi có thể sử dụng Aspose.Words để xóa SDT khỏi tài liệu không?

Có, bạn có thể xóa SDT bằng cách truy cập vào các nút của tài liệu và xóa SDT mong muốn.

4. Tôi phải xử lý các SDT được lồng vào các phần tử khác như thế nào?

 Sử dụng`GetChildNodes` phương pháp có tham số thích hợp để truy cập SDT lồng nhau.

5. Tôi phải làm gì nếu SDT tôi cần sửa đổi không hiển thị trong tài liệu?

Đảm bảo SDT không bị ẩn hoặc được bảo vệ. Kiểm tra cài đặt tài liệu và đảm bảo mã của bạn đang nhắm mục tiêu đúng loại SDT.


### Mã nguồn ví dụ để Sửa đổi Kiểm soát Nội dung bằng Aspose.Words cho .NET 

```csharp
// Đường dẫn đến thư mục tài liệu của bạn
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Structured document tags.docx");
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
	switch (sdt.SdtType)
	{
		case SdtType.PlainText:
		{
			sdt.RemoveAllChildren();
			Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
			Run run = new Run(doc, "new text goes here");
			para.AppendChild(run);
			break;
		}
		case SdtType.DropDownList:
		{
			SdtListItem secondItem = sdt.ListItems[2];
			sdt.ListItems.SelectedValue = secondItem;
			break;
		}
		case SdtType.Picture:
		{
			Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
			if (shape.HasImage)
			{
				shape.ImageData.SetImage(ImagesDir + "Watermark.png");
			}
			break;
		}
	}
}
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");

```

Vậy là xong! Bạn đã sửa đổi thành công các loại điều khiển nội dung khác nhau trong tài liệu Word của mình bằng Aspose.Words cho .NET.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
