---
title: Thiết lập hệ thống thư mục phông chữ và thư mục tùy chỉnh
linktitle: Thiết lập hệ thống thư mục phông chữ và thư mục tùy chỉnh
second_title: API xử lý tài liệu Aspose.Words
description: Tìm hiểu cách thiết lập thư mục phông chữ hệ thống và tùy chỉnh trong tài liệu Word bằng Aspose.Words cho .NET, đảm bảo tài liệu của bạn hiển thị chính xác trên nhiều môi trường khác nhau.
weight: 10
url: /vi/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Thiết lập hệ thống thư mục phông chữ và thư mục tùy chỉnh

## Giới thiệu

Hãy tưởng tượng bạn đang tạo một tài liệu với kiểu phông chữ độc đáo, chỉ để phát hiện ra rằng phông chữ không hiển thị đúng trên một máy khác. Thật bực bội, phải không? Đây là lúc cấu hình thư mục phông chữ phát huy tác dụng. Với Aspose.Words cho .NET, bạn có thể xác định thư mục phông chữ hệ thống và tùy chỉnh để đảm bảo tài liệu của bạn luôn trông như mong muốn. Hãy cùng tìm hiểu cách bạn có thể đạt được điều này.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn có những điều sau:

-  Aspose.Words cho Thư viện .NET: Nếu bạn chưa tải xuống, hãy tải xuống[đây](https://releases.aspose.com/words/net/).
- Môi trường phát triển: Một IDE như Visual Studio.
- Kiến thức cơ bản về C#: Sự quen thuộc với C# sẽ giúp bạn theo dõi các ví dụ về mã.

## Nhập không gian tên

Đầu tiên, hãy nhập các không gian tên cần thiết vào dự án của bạn:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Bây giờ, chúng ta hãy chia nhỏ quy trình thành các bước đơn giản.

## Bước 1: Tải tài liệu

 Để bắt đầu, hãy tải tài liệu Word của bạn vào Aspose.Words`Document` đối tượng. Đây sẽ là tài liệu mà bạn muốn thiết lập các thư mục phông chữ.

```csharp
// Đường dẫn đến thư mục tài liệu của bạn
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

## Bước 2: Khởi tạo cài đặt phông chữ

 Tạo một phiên bản mới của`FontSettings`. Đối tượng này sẽ cho phép bạn quản lý nguồn phông chữ.

```csharp
FontSettings fontSettings = new FontSettings();
```

## Bước 3: Truy xuất nguồn phông chữ hệ thống

Truy xuất các nguồn phông chữ hệ thống mặc định. Trên máy Windows, điều này thường bao gồm "Windows\Fonts\"thư mục.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

## Bước 4: Thêm một thư mục phông chữ tùy chỉnh

Thêm một thư mục tùy chỉnh chứa các phông chữ bổ sung của bạn. Điều này hữu ích nếu bạn có các phông chữ cụ thể không được cài đặt trong thư mục phông chữ hệ thống.

```csharp
FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);
```

## Bước 5: Cập nhật nguồn phông chữ

 Chuyển đổi danh sách các nguồn phông chữ trở lại thành một mảng và đặt nó thành`FontSettings` sự vật.

```csharp
FontSourceBase[] updatedFontSources = fontSources.ToArray();
fontSettings.SetFontsSources(updatedFontSources);
```

## Bước 6: Áp dụng Cài đặt Phông chữ cho Tài liệu

 Cuối cùng, áp dụng cấu hình`FontSettings` vào tài liệu của bạn và lưu ở định dạng mong muốn, chẳng hạn như PDF.

```csharp
doc.FontSettings = fontSettings;
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersSystemAndCustomFolder.pdf");
```

## Phần kết luận

Và bạn đã có nó! Bằng cách làm theo các bước này, bạn có thể đảm bảo rằng các tài liệu Word của mình sử dụng đúng phông chữ, cho dù đó là phông chữ hệ thống hay phông chữ tùy chỉnh được lưu trữ trong một thư mục cụ thể. Thiết lập này giúp duy trì tính toàn vẹn của giao diện tài liệu của bạn trên các môi trường khác nhau.

## Câu hỏi thường gặp

### Điều gì xảy ra nếu một phông chữ bị thiếu trong cả thư mục hệ thống và thư mục tùy chỉnh?

Aspose.Words sẽ sử dụng phông chữ mặc định để thay thế phông chữ bị thiếu, đảm bảo tài liệu vẫn có thể đọc được.

### Tôi có thể thêm nhiều thư mục phông chữ tùy chỉnh không?

 Có, bạn có thể thêm nhiều thư mục phông chữ tùy chỉnh bằng cách lặp lại quy trình tạo`FolderFontSource` đối tượng và thêm chúng vào danh sách nguồn phông chữ.

### Có thể sử dụng đường dẫn mạng cho thư mục phông chữ tùy chỉnh không?

 Có, bạn có thể chỉ định đường dẫn mạng trong`FolderFontSource` người xây dựng.

### Aspose.Words hỗ trợ những định dạng tệp nào để lưu tài liệu?

Aspose.Words hỗ trợ nhiều định dạng khác nhau, bao gồm DOCX, PDF, HTML, v.v.

### Tôi phải xử lý thông báo thay thế phông chữ như thế nào?

 Bạn có thể xử lý thông báo thay thế phông chữ bằng cách sử dụng`FontSettings` lớp học`FontSubstitutionWarning`sự kiện.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
