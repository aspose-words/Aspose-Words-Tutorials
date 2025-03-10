---
title: Mỏ neo dọc
linktitle: Mỏ neo dọc
second_title: API xử lý tài liệu Aspose.Words
description: Tìm hiểu cách thiết lập vị trí neo dọc cho hộp văn bản trong tài liệu Word bằng Aspose.Words cho .NET. Có kèm hướng dẫn từng bước dễ dàng.
weight: 10
url: /vi/net/programming-with-shapes/vertical-anchor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mỏ neo dọc

## Giới thiệu

Bạn đã bao giờ thấy mình cần kiểm soát chính xác vị trí văn bản xuất hiện bên trong hộp văn bản trong tài liệu Word chưa? Có thể bạn muốn neo văn bản của mình vào đầu, giữa hoặc cuối hộp văn bản? Nếu vậy, bạn đã đến đúng nơi rồi! Trong hướng dẫn này, chúng ta sẽ khám phá cách sử dụng Aspose.Words cho .NET để đặt neo dọc của hộp văn bản trong tài liệu Word. Hãy nghĩ về neo dọc như cây đũa thần định vị văn bản của bạn chính xác ở vị trí bạn muốn trong vùng chứa của nó. Sẵn sàng để bắt đầu chưa? Hãy bắt đầu thôi!

## Điều kiện tiên quyết

Trước khi đi sâu vào các chi tiết cơ bản của neo thẳng đứng, bạn cần chuẩn bị một số thứ sau:

1.  Aspose.Words cho .NET: Đảm bảo bạn đã cài đặt thư viện Aspose.Words cho .NET. Nếu bạn chưa có, bạn có thể[tải xuống ở đây](https://releases.aspose.com/words/net/).
2. Visual Studio: Hướng dẫn này giả định rằng bạn đang sử dụng Visual Studio hoặc một IDE .NET khác để viết mã.
3. Kiến thức cơ bản về C#: Sự quen thuộc với C# và .NET sẽ giúp bạn theo dõi dễ dàng.

## Nhập không gian tên

Để bắt đầu, bạn cần nhập các không gian tên cần thiết vào mã C# của mình. Đây là nơi bạn cho ứng dụng biết nơi tìm các lớp và phương thức bạn sẽ sử dụng. Sau đây là cách thực hiện:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Các không gian tên này cung cấp các lớp bạn cần để làm việc với tài liệu và hình dạng.

## Bước 1: Khởi tạo Tài liệu

Trước tiên, bạn cần tạo một tài liệu Word mới. Hãy nghĩ về điều này như việc thiết lập canvas trước khi bạn bắt đầu vẽ.

```csharp
// Đường dẫn đến thư mục tài liệu của bạn
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Đây,`Document` là bức tranh trắng của bạn, và`DocumentBuilder` là cọ vẽ của bạn, cho phép bạn thêm hình dạng và văn bản.

## Bước 2: Chèn Hình Hộp Văn Bản

Bây giờ, hãy thêm một hộp văn bản vào tài liệu của chúng ta. Đây là nơi văn bản của bạn sẽ nằm. 

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextBox, 200, 200);
```

 Trong ví dụ này,`ShapeType.TextBox` chỉ định hình dạng bạn muốn và`200, 200` là chiều rộng và chiều cao của hộp văn bản tính bằng điểm.

## Bước 3: Đặt neo dọc

Đây là nơi phép thuật xảy ra! Bạn có thể thiết lập căn chỉnh theo chiều dọc của văn bản trong hộp văn bản. Điều này xác định xem văn bản được neo vào đầu, giữa hay cuối hộp văn bản.

```csharp
textBox.TextBox.VerticalAnchor = TextBoxAnchor.Bottom;
```

 Trong trường hợp này,`TextBoxAnchor.Bottom`đảm bảo rằng văn bản sẽ được neo vào dưới cùng của hộp văn bản. Nếu bạn muốn nó được căn giữa hoặc căn chỉnh lên trên cùng, bạn sẽ sử dụng`TextBoxAnchor.Center` hoặc`TextBoxAnchor.Top`, tương ứng.

## Bước 4: Thêm văn bản vào hộp văn bản

Bây giờ là lúc thêm một số nội dung vào hộp văn bản của bạn. Hãy nghĩ về việc này như việc điền vào khung vẽ của bạn những nét hoàn thiện cuối cùng.

```csharp
builder.MoveTo(textBox.FirstParagraph);
builder.Write("Textbox contents");
```

 Đây,`MoveTo` đảm bảo rằng văn bản được chèn vào hộp văn bản và`Write` thêm văn bản thực tế.

## Bước 5: Lưu tài liệu

Bước cuối cùng là lưu tài liệu của bạn. Điều này giống như việc bạn đặt bức tranh đã hoàn thành vào khung.

```csharp
doc.Save(dataDir + "WorkingWithShapes.VerticalAnchor.docx");
```

## Phần kết luận

Và bạn đã có nó! Bạn vừa học cách kiểm soát căn chỉnh theo chiều dọc của văn bản trong hộp văn bản trong tài liệu Word bằng Aspose.Words cho .NET. Cho dù bạn đang neo văn bản vào đầu, giữa hay cuối, tính năng này cung cấp cho bạn quyền kiểm soát chính xác đối với bố cục của tài liệu. Vì vậy, lần tới khi bạn cần điều chỉnh vị trí văn bản của tài liệu, bạn sẽ biết chính xác phải làm gì!

## Câu hỏi thường gặp

### Neo dọc trong tài liệu Word là gì?
Neo theo chiều dọc kiểm soát vị trí văn bản được định vị trong hộp văn bản, chẳng hạn như căn chỉnh trên cùng, giữa hoặc dưới cùng.

### Tôi có thể sử dụng hình dạng khác ngoài hộp văn bản không?
Có, bạn có thể sử dụng neo theo chiều dọc với các hình dạng khác, mặc dù hộp văn bản là trường hợp sử dụng phổ biến nhất.

### Làm thế nào để thay đổi điểm neo sau khi tạo hộp văn bản?
 Bạn có thể thay đổi điểm neo bằng cách thiết lập`VerticalAnchor` thuộc tính trên đối tượng hình dạng hộp văn bản.

### Có thể neo văn bản vào giữa hộp văn bản không?
 Chắc chắn rồi! Chỉ cần sử dụng`TextBoxAnchor.Center` để căn giữa văn bản theo chiều dọc trong hộp văn bản.

### Tôi có thể tìm thêm thông tin về Aspose.Words cho .NET ở đâu?
 Kiểm tra các[Tài liệu Aspose.Words](https://reference.aspose.com/words/net/) để biết thêm chi tiết và hướng dẫn.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
