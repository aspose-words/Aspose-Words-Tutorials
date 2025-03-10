---
title: Sửa đổi hình dạng
linktitle: Sửa đổi hình dạng
second_title: API xử lý tài liệu Aspose.Words
description: Tìm hiểu cách xử lý các bản sửa đổi hình dạng trong tài liệu Word bằng Aspose.Words cho .NET với hướng dẫn toàn diện này. Làm chủ việc theo dõi các thay đổi, chèn hình dạng và nhiều hơn nữa.
weight: 10
url: /vi/net/working-with-revisions/shape-revision/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Sửa đổi hình dạng

## Giới thiệu

Chỉnh sửa tài liệu Word theo chương trình có thể là một nhiệm vụ khó khăn, đặc biệt là khi xử lý hình dạng. Cho dù bạn đang tạo báo cáo, thiết kế mẫu hay chỉ đơn giản là tự động hóa việc tạo tài liệu, khả năng theo dõi và quản lý các bản sửa đổi hình dạng là rất quan trọng. Aspose.Words for .NET cung cấp một API mạnh mẽ để làm cho quá trình này liền mạch và hiệu quả. Trong hướng dẫn này, chúng ta sẽ đi sâu vào các chi tiết cụ thể về việc sửa đổi hình dạng trong tài liệu Word, đảm bảo bạn có các công cụ và kiến thức để quản lý tài liệu của mình một cách dễ dàng.

## Điều kiện tiên quyết

Trước khi tìm hiểu mã, hãy đảm bảo bạn có mọi thứ cần thiết:

-  Aspose.Words cho .NET: Đảm bảo bạn đã cài đặt thư viện Aspose.Words. Bạn có thể[tải xuống ở đây](https://releases.aspose.com/words/net/).
- Môi trường phát triển: Bạn nên thiết lập một môi trường phát triển, chẳng hạn như Visual Studio.
- Hiểu biết cơ bản về C#: Làm quen với ngôn ngữ lập trình C# và các khái niệm cơ bản về lập trình hướng đối tượng.
- Tài liệu Word: Tài liệu Word để làm việc hoặc bạn có thể tạo một tài liệu trong quá trình hướng dẫn.

## Nhập không gian tên

Trước tiên, hãy nhập các không gian tên cần thiết. Chúng sẽ cung cấp cho chúng ta quyền truy cập vào các lớp và phương thức cần thiết để xử lý các tài liệu và hình dạng Word.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Bước 1: Thiết lập thư mục tài liệu của bạn

Trước khi bắt đầu làm việc với hình dạng, chúng ta cần xác định đường dẫn đến thư mục tài liệu của mình. Đây là nơi chúng ta sẽ lưu các tài liệu đã sửa đổi.

```csharp
// Đường dẫn đến thư mục tài liệu.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Bước 2: Tạo một tài liệu mới

Hãy tạo một tài liệu Word mới để chèn và chỉnh sửa hình dạng.

```csharp
Document doc = new Document();
```

## Bước 3: Chèn một hình dạng nội tuyến

Chúng ta sẽ bắt đầu bằng cách chèn một hình dạng nội tuyến vào tài liệu của mình mà không theo dõi các bản sửa đổi. Hình dạng nội tuyến là hình dạng chảy theo văn bản.

```csharp
Shape shape = new Shape(doc, ShapeType.Cube);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Bước 4: Bắt đầu theo dõi bản sửa đổi

Để theo dõi những thay đổi trong tài liệu của chúng tôi, chúng tôi cần bật tính năng theo dõi sửa đổi. Điều này rất cần thiết để xác định những thay đổi được thực hiện đối với hình dạng.

```csharp
doc.StartTrackRevisions("John Doe");
```

## Bước 5: Chèn một hình dạng khác với các bản sửa đổi

Bây giờ khi tính năng theo dõi sửa đổi đã được bật, hãy chèn một hình dạng khác. Lần này, mọi thay đổi sẽ được theo dõi.

```csharp
shape = new Shape(doc, ShapeType.Sun);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## Bước 6: Lấy lại và sửa đổi hình dạng

Chúng ta có thể lấy tất cả các hình dạng trong tài liệu và chỉnh sửa chúng khi cần. Ở đây, chúng ta sẽ lấy các hình dạng và xóa hình dạng đầu tiên.

```csharp
List<Shape> shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
shapes[0].Remove();
```

## Bước 7: Lưu tài liệu

Sau khi thực hiện thay đổi, chúng ta cần lưu tài liệu. Điều này đảm bảo tất cả các bản sửa đổi và thay đổi đều được lưu trữ.

```csharp
doc.Save(dataDir + "Revision shape.docx");
```

## Bước 8: Xử lý các bản sửa đổi di chuyển hình dạng

Khi một hình dạng được di chuyển, Aspose.Words theo dõi điều này như một bản sửa đổi. Điều này có nghĩa là sẽ có hai trường hợp của hình dạng: một ở vị trí ban đầu và một ở vị trí mới.

```csharp
doc = new Document(dataDir + "Revision shape.docx");
shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
```

## Phần kết luận

Và bạn đã có nó! Bạn đã học thành công cách xử lý các bản sửa đổi hình dạng trong tài liệu Word bằng Aspose.Words cho .NET. Cho dù bạn đang quản lý các mẫu tài liệu, tự động hóa báo cáo hay chỉ đơn giản là theo dõi các thay đổi, những kỹ năng này đều vô cùng hữu ích. Bằng cách làm theo hướng dẫn từng bước này, bạn không chỉ nắm vững những điều cơ bản mà còn hiểu sâu hơn về các kỹ thuật xử lý tài liệu nâng cao hơn.

## Câu hỏi thường gặp

### Aspose.Words dành cho .NET là gì?
Aspose.Words for .NET là một thư viện mạnh mẽ cho phép các nhà phát triển tạo, sửa đổi và chuyển đổi các tài liệu Word theo chương trình bằng C#.

### Tôi có thể theo dõi những thay đổi được thực hiện trên các thành phần khác trong tài liệu Word không?
Có, Aspose.Words for .NET hỗ trợ theo dõi những thay đổi ở nhiều thành phần khác nhau, bao gồm văn bản, bảng, v.v.

### Làm thế nào tôi có thể dùng thử miễn phí Aspose.Words cho .NET?
 Bạn có thể dùng thử miễn phí Aspose.Words cho .NET[đây](https://releases.aspose.com/).

### Có thể chấp nhận hoặc từ chối sửa đổi theo chương trình không?
Có, Aspose.Words cho .NET cung cấp các phương pháp để chấp nhận hoặc từ chối các bản sửa đổi theo cách lập trình.

### Tôi có thể sử dụng Aspose.Words cho .NET với các ngôn ngữ .NET khác ngoài C# không?
Hoàn toàn có thể! Aspose.Words cho .NET có thể được sử dụng với bất kỳ ngôn ngữ .NET nào, bao gồm VB.NET và F#.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
