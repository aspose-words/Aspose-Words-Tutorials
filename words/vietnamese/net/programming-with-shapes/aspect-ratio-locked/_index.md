---
title: Tỷ lệ khung hình đã khóa
linktitle: Tỷ lệ khung hình đã khóa
second_title: API xử lý tài liệu Aspose.Words
description: Tìm hiểu cách khóa tỷ lệ khung hình của hình dạng trong tài liệu Word bằng Aspose.Words cho .NET. Thực hiện theo hướng dẫn từng bước này để giữ cho hình ảnh và hình dạng của bạn cân đối.
weight: 10
url: /vi/net/programming-with-shapes/aspect-ratio-locked/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tỷ lệ khung hình đã khóa

## Giới thiệu

Bạn đã bao giờ tự hỏi làm thế nào để duy trì tỷ lệ hoàn hảo của hình ảnh và hình dạng trong tài liệu Word của mình chưa? Đôi khi, bạn cần đảm bảo rằng hình ảnh và hình dạng của mình không bị méo khi thay đổi kích thước. Đây là lúc khóa tỷ lệ khung hình trở nên hữu ích. Trong hướng dẫn này, chúng ta sẽ khám phá cách đặt tỷ lệ khung hình cho hình dạng trong tài liệu Word bằng Aspose.Words cho .NET. Chúng tôi sẽ chia nhỏ thành các bước dễ thực hiện, đảm bảo rằng bạn có thể áp dụng các kỹ năng này vào dự án của mình một cách tự tin.

## Điều kiện tiên quyết

Trước khi đi sâu vào mã, chúng ta hãy xem qua những gì bạn cần để bắt đầu:

- Thư viện Aspose.Words cho .NET: Bạn cần cài đặt Aspose.Words cho .NET. Nếu bạn chưa cài đặt, bạn có thể[tải xuống ở đây](https://releases.aspose.com/words/net/).
- Môi trường phát triển: Đảm bảo bạn đã thiết lập môi trường phát triển .NET. Visual Studio là lựa chọn phổ biến.
- Kiến thức cơ bản về C#: Có một chút hiểu biết về lập trình C# sẽ rất hữu ích.

## Nhập không gian tên

Trước tiên, hãy nhập các không gian tên cần thiết. Các không gian tên này sẽ cho phép chúng ta truy cập vào các lớp và phương thức cần thiết để làm việc với các tài liệu và hình dạng Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Bước 1: Thiết lập thư mục tài liệu của bạn

 Trước khi bắt đầu thao tác hình dạng, chúng ta cần thiết lập một thư mục nơi các tài liệu của chúng ta sẽ được lưu trữ. Để đơn giản, chúng ta sẽ sử dụng một trình giữ chỗ`YOUR DOCUMENT DIRECTORY`. Thay thế đường dẫn này bằng đường dẫn thực tế tới thư mục tài liệu của bạn.

```csharp
// Đường dẫn đến thư mục tài liệu của bạn
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Bước 2: Tạo một tài liệu mới

Tiếp theo, chúng ta sẽ tạo một tài liệu Word mới bằng Aspose.Words. Tài liệu này sẽ đóng vai trò là canvas để thêm hình dạng và hình ảnh.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Ở đây, chúng ta tạo một thể hiện của`Document` lớp và sử dụng một`DocumentBuilder` để giúp chúng tôi xây dựng nội dung tài liệu.

## Bước 3: Chèn hình ảnh

 Bây giờ, hãy chèn một hình ảnh vào tài liệu của chúng ta. Chúng ta sẽ sử dụng`InsertImage` phương pháp của`DocumentBuilder`lớp. Đảm bảo bạn có hình ảnh trong thư mục đã chỉ định.

```csharp
Shape shape = builder.InsertImage(dataDir + "Transparent background logo.png");
```

 Thay thế`dataDir + "Transparent background logo.png"` bằng đường dẫn đến tệp hình ảnh của bạn.

## Bước 4: Khóa tỷ lệ khung hình

Sau khi chèn hình ảnh, chúng ta có thể khóa tỷ lệ khung hình của hình ảnh. Khóa tỷ lệ khung hình đảm bảo tỷ lệ của hình ảnh không đổi khi thay đổi kích thước.

```csharp
shape.AspectRatioLocked = true;
```

 Cài đặt`AspectRatioLocked` ĐẾN`true` đảm bảo hình ảnh duy trì tỷ lệ khung hình ban đầu.

## Bước 5: Lưu tài liệu

Cuối cùng, chúng ta sẽ lưu tài liệu vào thư mục đã chỉ định. Bước này ghi lại tất cả các thay đổi chúng ta đã thực hiện vào tệp tài liệu.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Phần kết luận

Xin chúc mừng! Bạn đã học thành công cách thiết lập tỷ lệ khung hình cho các hình dạng trong tài liệu Word bằng Aspose.Words cho .NET. Bằng cách làm theo các bước này, bạn có thể đảm bảo rằng hình ảnh và hình dạng của mình giữ nguyên tỷ lệ, giúp tài liệu của bạn trông chuyên nghiệp và bóng bẩy. Hãy thoải mái thử nghiệm với các hình ảnh và hình dạng khác nhau để xem tính năng khóa tỷ lệ khung hình hoạt động như thế nào trong các tình huống khác nhau.

## Câu hỏi thường gặp

### Tôi có thể mở khóa tỷ lệ khung hình sau khi đã khóa không?
Có, bạn có thể mở khóa tỷ lệ khung hình bằng cách thiết lập`shape.AspectRatioLocked = false`.

### Điều gì xảy ra nếu tôi thay đổi kích thước hình ảnh có tỷ lệ khung hình cố định?
Hình ảnh sẽ thay đổi kích thước theo tỷ lệ, vẫn giữ nguyên tỷ lệ chiều rộng/chiều cao ban đầu.

### Tôi có thể áp dụng điều này cho các hình dạng khác ngoài hình ảnh không?
Chắc chắn rồi! Tính năng khóa tỷ lệ khung hình có thể áp dụng cho bất kỳ hình dạng nào, bao gồm hình chữ nhật, hình tròn, v.v.

### Aspose.Words cho .NET có tương thích với .NET Core không?
Có, Aspose.Words cho .NET hỗ trợ cả .NET Framework và .NET Core.

### Tôi có thể tìm thêm tài liệu về Aspose.Words cho .NET ở đâu?
 Bạn có thể tìm thấy tài liệu toàn diện[đây](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
