---
title: Nhận danh sách các phông chữ có sẵn
linktitle: Nhận danh sách các phông chữ có sẵn
second_title: API xử lý tài liệu Aspose.Words
description: Khám phá cách lấy danh sách phông chữ khả dụng bằng Aspose.Words cho .NET trong hướng dẫn từng bước chi tiết này. Nâng cao kỹ năng quản lý phông chữ của bạn.
weight: 10
url: /vi/net/working-with-fonts/get-list-of-available-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nhận danh sách các phông chữ có sẵn

## Giới thiệu

Bạn đã bao giờ thấy mình đang vật lộn để quản lý phông chữ trong tài liệu Word của mình chưa? Nếu bạn là nhà phát triển .NET, Aspose.Words for .NET sẽ giải cứu bạn! Thư viện mạnh mẽ này không chỉ giúp bạn tạo và thao tác tài liệu Word theo chương trình mà còn cung cấp khả năng quản lý phông chữ mở rộng. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn từng bước về cách lấy danh sách phông chữ khả dụng bằng Aspose.Words for .NET. Chúng tôi sẽ chia nhỏ thành các bước dễ hiểu để đảm bảo bạn có thể dễ dàng thực hiện theo. Vậy, hãy cùng bắt đầu và biến việc quản lý phông chữ trở nên dễ dàng!

## Điều kiện tiên quyết

Trước khi bắt đầu, bạn cần chuẩn bị một số thứ sau:

-  Aspose.Words cho .NET: Đảm bảo bạn đã cài đặt thư viện Aspose.Words cho .NET. Bạn có thể tải xuống từ[đây](https://releases.aspose.com/words/net/).
- Visual Studio: Ví dụ này sử dụng Visual Studio làm môi trường phát triển.
- .NET Framework: Đảm bảo bạn đã cài đặt .NET Framework trên máy của mình.
- Thư mục tài liệu: Đường dẫn thư mục nơi lưu trữ tài liệu của bạn.

## Nhập không gian tên

Đầu tiên, hãy nhập các không gian tên cần thiết vào dự án của bạn:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

## Bước 1: Khởi tạo cài đặt phông chữ

Bước đầu tiên là khởi tạo cài đặt phông chữ. Điều này sẽ cho phép bạn quản lý nguồn phông chữ cho tài liệu của mình.

```csharp
FontSettings fontSettings = new FontSettings();
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

- FontSettings: Lớp này được sử dụng để chỉ định cài đặt cho việc thay thế phông chữ và nguồn phông chữ.
- fontSources: Chúng tôi tạo danh sách các nguồn phông chữ hiện có từ cài đặt phông chữ hiện tại.

## Bước 2: Xác định thư mục tài liệu

Tiếp theo, chỉ định đường dẫn đến thư mục tài liệu của bạn. Đây là nơi Aspose.Words sẽ tìm kiếm phông chữ.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

-  dataDir: Biến chuỗi này giữ đường dẫn đến thư mục chứa phông chữ của bạn. Thay thế`"YOUR DOCUMENT DIRECTORY"` với đường dẫn thực tế.

## Bước 3: Thêm thư mục phông chữ tùy chỉnh

Bây giờ, hãy thêm một thư mục nguồn mới để hướng dẫn Aspose.Words tìm kiếm phông chữ trong thư mục này.

```csharp
FolderFontSource folderFontSource = new FolderFontSource(dataDir, true);
```

- FolderFontSource: Lớp này biểu diễn một nguồn phông chữ thư mục. Tham số thứ hai (`true`) cho biết liệu có nên tìm kiếm phông chữ theo cách đệ quy trong các thư mục con hay không.

## Bước 4: Cập nhật nguồn phông chữ

Thêm thư mục phông chữ tùy chỉnh vào danh sách các nguồn phông chữ hiện có và cập nhật cài đặt phông chữ.

```csharp
fontSources.Add(folderFontSource);
FontSourceBase[] updatedFontSources = fontSources.ToArray();
```

- fontSources.Add(folderFontSource): Thêm thư mục phông chữ tùy chỉnh vào các nguồn phông chữ hiện có.
- updatedFontSources: Chuyển đổi danh sách các nguồn phông chữ thành một mảng.

## Bước 5: Lấy và Hiển thị Phông chữ

Cuối cùng, lấy các phông chữ có sẵn và hiển thị thông tin chi tiết của chúng.

```csharp
foreach (PhysicalFontInfo fontInfo in updatedFontSources[0].GetAvailableFonts())
{
    Console.WriteLine("FontFamilyName : " + fontInfo.FontFamilyName);
    Console.WriteLine("FullFontName  : " + fontInfo.FullFontName);
    Console.WriteLine("Version  : " + fontInfo.Version);
    Console.WriteLine("FilePath : " + fontInfo.FilePath);
}
```

- GetAvailableFonts(): Truy xuất danh sách các phông chữ có sẵn từ nguồn phông chữ đầu tiên trong danh sách đã cập nhật.
-  fontInfo: Một trường hợp của`PhysicalFontInfo` chứa thông tin chi tiết về từng phông chữ.

## Phần kết luận

Xin chúc mừng! Bạn đã lấy thành công danh sách các phông chữ khả dụng bằng Aspose.Words cho .NET. Hướng dẫn này đã hướng dẫn bạn từng bước, từ khởi tạo cài đặt phông chữ đến hiển thị chi tiết phông chữ. Với kiến thức này, giờ đây bạn có thể dễ dàng quản lý phông chữ trong tài liệu Word của mình. Hãy nhớ rằng, Aspose.Words cho .NET là một công cụ mạnh mẽ có thể cải thiện đáng kể khả năng xử lý tài liệu của bạn. Vì vậy, hãy tiếp tục và khám phá thêm nhiều tính năng hơn để làm cho quy trình phát triển của bạn hiệu quả hơn nữa.

## Câu hỏi thường gặp

### Tôi có thể sử dụng Aspose.Words cho .NET với các nền tảng .NET khác không?
Có, Aspose.Words cho .NET tương thích với nhiều nền tảng .NET khác nhau bao gồm .NET Core và .NET 5+.

### Làm thế nào để cài đặt Aspose.Words cho .NET?
Bạn có thể cài đặt nó thông qua NuGet Package Manager trong Visual Studio bằng cách tìm kiếm "Aspose.Words".

### Có thể thêm nhiều thư mục phông chữ tùy chỉnh không?
 Có, bạn có thể thêm nhiều thư mục phông chữ tùy chỉnh bằng cách tạo nhiều`FolderFontSource` và thêm chúng vào danh sách nguồn phông chữ.

### Tôi có thể lấy thông tin chi tiết về phông chữ từ một nguồn phông chữ cụ thể không?
 Có, bạn có thể lấy thông tin chi tiết về phông chữ từ bất kỳ nguồn phông chữ nào bằng cách chỉ định chỉ mục của nguồn phông chữ trong`updatedFontSources` mảng.

### Aspose.Words cho .NET có hỗ trợ thay thế phông chữ không?
Có, nó hỗ trợ thay thế phông chữ để đảm bảo văn bản được hiển thị chính xác ngay cả khi phông chữ gốc không khả dụng.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
