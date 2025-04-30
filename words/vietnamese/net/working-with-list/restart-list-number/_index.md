---
"description": "Tìm hiểu cách khởi động lại danh sách số trong tài liệu Word bằng Aspose.Words cho .NET. Hướng dẫn chi tiết dài 2000 từ này bao gồm mọi thứ bạn cần biết, từ thiết lập đến tùy chỉnh nâng cao."
"linktitle": "Số danh sách khởi động lại"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Số danh sách khởi động lại"
"url": "/vi/net/working-with-list/restart-list-number/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Số danh sách khởi động lại

## Giới thiệu

Bạn có muốn thành thạo nghệ thuật thao tác danh sách trong tài liệu Word của mình bằng Aspose.Words cho .NET không? Vâng, bạn đã đến đúng nơi rồi! Trong hướng dẫn này, chúng ta sẽ đi sâu vào việc khởi động lại số danh sách, một tính năng tiện lợi sẽ đưa kỹ năng tự động hóa tài liệu của bạn lên một tầm cao mới. Hãy thắt dây an toàn và bắt đầu thôi!

## Điều kiện tiên quyết

Trước khi tìm hiểu về mã, hãy đảm bảo rằng bạn có mọi thứ cần thiết:

1. Aspose.Words cho .NET: Bạn cần cài đặt Aspose.Words cho .NET. Nếu bạn chưa cài đặt, bạn có thể [tải xuống ở đây](https://releases.aspose.com/words/net/).
2. Môi trường phát triển: Đảm bảo bạn có môi trường phát triển phù hợp như Visual Studio.
3. Kiến thức cơ bản về C#: Hiểu biết cơ bản về C# sẽ giúp bạn theo dõi hướng dẫn.

## Nhập không gian tên

Trước tiên, hãy nhập các không gian tên cần thiết. Đây là những không gian tên quan trọng để truy cập các tính năng của Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
using System.Drawing;
```

Bây giờ, chúng ta hãy chia nhỏ quy trình thành các bước dễ thực hiện. Chúng ta sẽ đề cập đến mọi thứ từ việc tạo danh sách đến việc đánh số lại.

## Bước 1: Thiết lập Tài liệu và Trình tạo của Bạn

Trước khi bạn có thể bắt đầu thao tác danh sách, bạn cần một tài liệu và DocumentBuilder. DocumentBuilder là công cụ bạn cần để thêm nội dung vào tài liệu của mình.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Bước 2: Tạo và tùy chỉnh danh sách đầu tiên của bạn

Tiếp theo, chúng ta sẽ tạo một danh sách dựa trên mẫu và tùy chỉnh giao diện của nó. Trong ví dụ này, chúng ta sử dụng định dạng số Ả Rập có dấu ngoặc đơn.

```csharp
List list1 = doc.Lists.Add(ListTemplate.NumberArabicParenthesis);
list1.ListLevels[0].Font.Color = Color.Red;
list1.ListLevels[0].Alignment = ListLevelAlignment.Right;
```

Ở đây, chúng tôi đặt màu phông chữ thành màu đỏ và căn chỉnh văn bản sang bên phải.

## Bước 3: Thêm mục vào danh sách đầu tiên của bạn

Với danh sách đã sẵn sàng, đã đến lúc thêm một số mục. DocumentBuilder `ListFormat.List` Thuộc tính này giúp áp dụng định dạng danh sách vào văn bản.

```csharp
builder.Writeln("List 1 starts below:");
builder.ListFormat.List = list1;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Bước 4: Khởi động lại danh sách đánh số

Để sử dụng lại danh sách và khởi động lại việc đánh số, bạn cần tạo một bản sao của danh sách gốc. Điều này cho phép bạn sửa đổi danh sách mới một cách độc lập.

```csharp
List list2 = doc.Lists.AddCopy(list1);
list2.ListLevels[0].StartAt = 10;
```

Trong ví dụ này, danh sách mới bắt đầu từ số 10.

## Bước 5: Thêm mục vào danh sách mới

Giống như trước, hãy thêm các mục vào danh sách mới của bạn. Điều này chứng minh danh sách khởi động lại ở số đã chỉ định.

```csharp
builder.Writeln("List 2 starts below:");
builder.ListFormat.List = list2;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Bước 6: Lưu tài liệu của bạn

Cuối cùng, lưu tài liệu vào thư mục bạn chỉ định.

```csharp
builder.Document.Save(dataDir + "WorkingWithList.RestartListNumber.docx");
```

## Phần kết luận

Việc khởi động lại danh sách số trong tài liệu Word bằng Aspose.Words cho .NET rất đơn giản và cực kỳ hữu ích. Cho dù bạn đang tạo báo cáo, tạo tài liệu có cấu trúc hay chỉ cần kiểm soát danh sách của mình tốt hơn, kỹ thuật này sẽ giúp bạn.

## Câu hỏi thường gặp

### Tôi có thể sử dụng các mẫu danh sách khác ngoài NumberArabicParenthesis không?

Chắc chắn rồi! Aspose.Words cung cấp nhiều mẫu danh sách như dấu đầu dòng, chữ cái, số La Mã, v.v. Bạn có thể chọn mẫu phù hợp nhất với nhu cầu của mình.

### Làm thế nào để thay đổi cấp độ danh sách?

Bạn có thể thay đổi cấp độ danh sách bằng cách sửa đổi `ListLevels` tài sản. Ví dụ, `list1.ListLevels[1]` sẽ đề cập đến cấp độ thứ hai của danh sách.

### Tôi có thể bắt đầu lại việc đánh số ở bất kỳ số nào không?

Có, bạn có thể đặt số bắt đầu thành bất kỳ giá trị số nguyên nào bằng cách sử dụng `StartAt` thuộc tính của cấp độ danh sách.

### Có thể định dạng khác nhau cho các cấp danh sách khác nhau không?

Thật vậy! Mỗi cấp danh sách có thể có các thiết lập định dạng riêng, chẳng hạn như phông chữ, căn chỉnh và kiểu đánh số.

### Tôi phải làm sao nếu muốn tiếp tục đánh số từ danh sách trước đó thay vì bắt đầu lại?

Nếu bạn muốn tiếp tục đánh số, bạn không cần phải tạo bản sao của danh sách. Chỉ cần tiếp tục thêm các mục vào danh sách gốc.





{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}