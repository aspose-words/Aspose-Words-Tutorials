---
title: Nhận thay thế không có hậu tố
linktitle: Nhận thay thế không có hậu tố
second_title: API xử lý tài liệu Aspose.Words
description: Tìm hiểu cách quản lý thay thế phông chữ mà không cần hậu tố trong Aspose.Words cho .NET. Làm theo hướng dẫn từng bước của chúng tôi để đảm bảo tài liệu của bạn luôn hoàn hảo.
weight: 10
url: /vi/net/working-with-fonts/get-substitution-without-suffixes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nhận thay thế không có hậu tố

## Giới thiệu

Chào mừng bạn đến với hướng dẫn toàn diện này về quản lý thay thế phông chữ bằng Aspose.Words cho .NET. Nếu bạn đã từng vật lộn với phông chữ không hiển thị đúng trong tài liệu của mình, bạn đã đến đúng nơi rồi. Hướng dẫn này sẽ hướng dẫn bạn từng bước để xử lý thay thế phông chữ mà không cần hậu tố một cách hiệu quả.

## Điều kiện tiên quyết

Trước khi bắt đầu hướng dẫn, hãy đảm bảo bạn có những điều sau:

- Kiến thức cơ bản về C#: Hiểu về lập trình C# sẽ giúp bạn dễ dàng làm theo và thực hiện các bước hơn.
-  Aspose.Words cho Thư viện .NET: Tải xuống và cài đặt thư viện từ[liên kết tải xuống](https://releases.aspose.com/words/net/).
- Môi trường phát triển: Thiết lập môi trường phát triển như Visual Studio để viết và chạy mã của bạn.
-  Tài liệu mẫu: Một tài liệu mẫu (ví dụ,`Rendering.docx`) để sử dụng trong hướng dẫn này.

## Nhập không gian tên

Đầu tiên, chúng ta cần import các không gian tên cần thiết để truy cập các lớp và phương thức do Aspose.Words cung cấp.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System.Collections.Generic;
```

## Bước 1: Xác định thư mục tài liệu

Để bắt đầu, hãy chỉ định thư mục chứa tài liệu của bạn. Điều này giúp xác định vị trí tài liệu bạn muốn làm việc.

```csharp
// Đường dẫn đến thư mục tài liệu của bạn
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Bước 2: Thiết lập Trình xử lý cảnh báo thay thế

Tiếp theo, chúng ta cần thiết lập trình xử lý cảnh báo sẽ thông báo cho chúng ta bất cứ khi nào có sự thay thế phông chữ xảy ra trong quá trình xử lý tài liệu. Điều này rất quan trọng để phát hiện và xử lý mọi sự cố về phông chữ.

```csharp
DocumentSubstitutionWarnings substitutionWarningHandler = new DocumentSubstitutionWarnings();
Document doc = new Document(dataDir + "Rendering.docx");
doc.WarningCallback = substitutionWarningHandler;
```

## Bước 3: Thêm nguồn phông chữ tùy chỉnh

Trong bước này, chúng tôi sẽ thêm các nguồn phông chữ tùy chỉnh để đảm bảo Aspose.Words có thể định vị và sử dụng đúng phông chữ. Điều này đặc biệt hữu ích nếu bạn có các phông chữ cụ thể được lưu trữ trong các thư mục tùy chỉnh.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(FontSettings.DefaultInstance.GetFontsSources());

FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);

FontSourceBase[] updatedFontSources = fontSources.ToArray();
FontSettings.DefaultInstance.SetFontsSources(updatedFontSources);
```

Trong đoạn mã này:
-  Chúng tôi lấy lại các nguồn phông chữ hiện tại và thêm một phông chữ mới`FolderFontSource` trỏ đến thư mục phông chữ tùy chỉnh của chúng tôi (`C:\\MyFonts\\`).
- Sau đó, chúng tôi cập nhật các nguồn phông chữ bằng danh sách mới này.

## Bước 4: Lưu tài liệu

Cuối cùng, lưu tài liệu sau khi áp dụng cài đặt thay thế phông chữ. Đối với hướng dẫn này, chúng tôi sẽ lưu dưới dạng PDF.

```csharp
doc.Save(dataDir + "WorkingWithFonts.GetSubstitutionWithoutSuffixes.pdf");
```

## Bước 5: Tạo lớp xử lý cảnh báo

 Để xử lý cảnh báo hiệu quả, hãy tạo một lớp tùy chỉnh thực hiện`IWarningCallback` giao diện. Lớp này sẽ ghi lại và ghi lại bất kỳ cảnh báo thay thế phông chữ nào.

```csharp
public class DocumentSubstitutionWarnings : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            FontWarnings.Warning(info);
    }

    public WarningInfoCollection FontWarnings = new WarningInfoCollection();
}
```

Trong lớp này:
-  Các`Warning`phương pháp này ghi lại các cảnh báo liên quan đến việc thay thế phông chữ.
-  Các`FontWarnings` bộ sưu tập lưu trữ những cảnh báo này để kiểm tra hoặc ghi nhật ký sau này.

## Phần kết luận

Bây giờ bạn đã thành thạo quy trình xử lý thay thế phông chữ mà không cần hậu tố bằng Aspose.Words cho .NET. Kiến thức này sẽ đảm bảo rằng tài liệu của bạn duy trì được giao diện mong muốn, bất kể phông chữ nào có sẵn trên hệ thống. Tiếp tục thử nghiệm với các cài đặt và nguồn khác nhau để khai thác đầy đủ sức mạnh của Aspose.Words.

## Câu hỏi thường gặp

### Làm thế nào để tôi có thể sử dụng phông chữ từ nhiều thư mục tùy chỉnh?

 Bạn có thể thêm nhiều`FolderFontSource` trường hợp đến`fontSources` liệt kê và cập nhật các nguồn phông chữ cho phù hợp.

### Tôi có thể tải xuống bản dùng thử miễn phí Aspose.Words cho .NET ở đâu?

 Bạn có thể tải xuống bản dùng thử miễn phí từ[Trang dùng thử miễn phí Aspose](https://releases.aspose.com/).

###  Tôi có thể xử lý nhiều loại cảnh báo bằng cách sử dụng`IWarningCallback`?

 Vâng,`IWarningCallback` Giao diện cho phép bạn xử lý nhiều loại cảnh báo khác nhau, không chỉ thay thế phông chữ.

### Tôi có thể nhận hỗ trợ cho Aspose.Words ở đâu?

 Để được hỗ trợ, hãy truy cập[Diễn đàn hỗ trợ Aspose.Words](https://forum.aspose.com/c/words/8).

### Tôi có thể mua giấy phép tạm thời được không?

 Có, bạn có thể xin giấy phép tạm thời từ[trang giấy phép tạm thời](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
