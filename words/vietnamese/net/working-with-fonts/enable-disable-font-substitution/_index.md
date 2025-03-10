---
title: Bật Tắt Thay Thế Phông Chữ
linktitle: Bật Tắt Thay Thế Phông Chữ
second_title: API xử lý tài liệu Aspose.Words
description: Tìm hiểu cách bật hoặc tắt tính năng thay thế phông chữ trong tài liệu Word bằng Aspose.Words cho .NET. Đảm bảo tài liệu của bạn trông nhất quán trên mọi nền tảng.
weight: 10
url: /vi/net/working-with-fonts/enable-disable-font-substitution/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bật Tắt Thay Thế Phông Chữ

## Giới thiệu

Bạn đã bao giờ rơi vào tình huống phông chữ bạn chọn kỹ lưỡng trong tài liệu Word bị thay thế khi xem trên máy tính khác chưa? Thật khó chịu phải không? Điều này xảy ra do thay thế phông chữ, một quá trình mà hệ thống thay thế phông chữ bị thiếu bằng phông chữ có sẵn. Nhưng đừng lo! Với Aspose.Words for .NET, bạn có thể dễ dàng quản lý và kiểm soát việc thay thế phông chữ. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn các bước để bật hoặc tắt thay thế phông chữ trong tài liệu Word của bạn, đảm bảo tài liệu của bạn luôn trông đúng như bạn muốn.

## Điều kiện tiên quyết

Trước khi thực hiện các bước, hãy đảm bảo rằng bạn có mọi thứ cần thiết:

-  Aspose.Words cho .NET: Tải xuống phiên bản mới nhất[đây](https://releases.aspose.com/words/net/).
- Visual Studio: Bất kỳ phiên bản nào hỗ trợ .NET.
- Kiến thức cơ bản về C#: Điều này sẽ giúp bạn theo dõi các ví dụ mã hóa.

## Nhập không gian tên

Để bắt đầu, hãy đảm bảo bạn đã nhập các không gian tên cần thiết vào dự án của mình. Thêm những không gian tên này vào đầu tệp C# của bạn:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Bây giờ, chúng ta hãy chia nhỏ quy trình thành các bước đơn giản và dễ quản lý.

## Bước 1: Thiết lập dự án của bạn

Đầu tiên, hãy thiết lập một dự án mới trong Visual Studio và thêm tham chiếu đến thư viện Aspose.Words cho .NET. Nếu bạn chưa tải xuống, hãy tải xuống từ[Trang web Aspose](https://releases.aspose.com/words/net/).

## Bước 2: Tải tài liệu của bạn

Tiếp theo, tải tài liệu bạn muốn làm việc. Đây là cách thực hiện:

```csharp
// Đường dẫn đến thư mục tài liệu của bạn
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

 Thay thế`"YOUR DOCUMENT DIRECTORY"` với đường dẫn thực tế đến thư mục tài liệu của bạn. Mã này tải tài liệu vào bộ nhớ để bạn có thể thao tác.

## Bước 3: Cấu hình cài đặt phông chữ

 Bây giờ, chúng ta hãy tạo một`FontSettings` đối tượng để quản lý cài đặt thay thế phông chữ:

```csharp
FontSettings fontSettings = new FontSettings();
```

## Bước 4: Thiết lập thay thế phông chữ mặc định

Đặt phông chữ thay thế mặc định thành phông chữ bạn chọn. Phông chữ này sẽ được sử dụng nếu phông chữ gốc không khả dụng:

```csharp
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

Trong ví dụ này, chúng tôi sử dụng Arial làm phông chữ mặc định.

## Bước 5: Vô hiệu hóa thay thế thông tin phông chữ

Để vô hiệu hóa tính năng thay thế thông tin phông chữ, ngăn hệ thống thay thế phông chữ bị thiếu bằng phông chữ có sẵn, hãy sử dụng mã sau:

```csharp
fontSettings.SubstitutionSettings.FontInfoSubstitution.Enabled = false;
```

## Bước 6: Áp dụng Cài đặt Phông chữ cho Tài liệu

Bây giờ, hãy áp dụng các thiết lập này vào tài liệu của bạn:

```csharp
doc.FontSettings = fontSettings;
```

## Bước 7: Lưu tài liệu của bạn

Cuối cùng, lưu tài liệu đã chỉnh sửa của bạn. Bạn có thể lưu ở bất kỳ định dạng nào bạn thích. Đối với hướng dẫn này, chúng tôi sẽ lưu dưới dạng PDF:

```csharp
doc.Save(dataDir + "WorkingWithFonts.EnableDisableFontSubstitution.pdf");
```

## Phần kết luận

Và bạn đã có nó! Bằng cách làm theo các bước này, bạn có thể dễ dàng kiểm soát việc thay thế phông chữ trong tài liệu Word của mình bằng Aspose.Words cho .NET. Điều này đảm bảo tài liệu của bạn duy trì được giao diện mong muốn, bất kể chúng được xem ở đâu.

## Câu hỏi thường gặp

### Tôi có thể sử dụng phông chữ khác ngoài Arial để thay thế không?

 Chắc chắn rồi! Bạn có thể chỉ định bất kỳ phông chữ nào có sẵn trên hệ thống của bạn bằng cách thay đổi tên phông chữ trong`DefaultFontName` tài sản.

### Điều gì xảy ra nếu phông chữ mặc định được chỉ định không khả dụng?

Nếu phông chữ mặc định không khả dụng, Aspose.Words sẽ sử dụng cơ chế dự phòng của hệ thống để tìm phông chữ thay thế phù hợp.

### Tôi có thể bật lại tính năng thay thế phông chữ sau khi đã tắt nó không?

 Có, bạn có thể chuyển đổi`Enabled` tài sản của`FontInfoSubstitution` trở lại`true` nếu bạn muốn bật lại chức năng thay thế phông chữ.

### Có cách nào để kiểm tra phông chữ nào đang được thay thế không?

Có, Aspose.Words cung cấp các phương pháp để ghi lại và theo dõi việc thay thế phông chữ, cho phép bạn xem phông chữ nào đang được thay thế.

### Tôi có thể sử dụng phương pháp này cho các định dạng tài liệu khác ngoài DOCX không?

Chắc chắn rồi! Aspose.Words hỗ trợ nhiều định dạng khác nhau và bạn có thể áp dụng các cài đặt phông chữ này cho bất kỳ định dạng nào được hỗ trợ.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
