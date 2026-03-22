---
category: general
date: 2026-03-22
description: Lưu tài liệu Word và phát hiện phông chữ thiếu bằng Aspose.Words. Tìm
  hiểu cách theo dõi phông chữ thiếu và ghi lại lỗi phông chữ trong C#.
draft: false
keywords:
- save word document
- detect missing fonts
- track missing fonts
- capture font errors
language: vi
og_description: Lưu tài liệu Word và phát hiện phông chữ thiếu trong C#. Hướng dẫn
  này chỉ cách theo dõi các phông chữ thiếu và ghi lại lỗi phông chữ bằng callback
  cảnh báo.
og_title: Lưu tài liệu Word – Phát hiện phông chữ thiếu với Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Lưu tài liệu Word – Phát hiện phông chữ thiếu với Aspose.Words
url: /vi/net/working-with-fonts/save-word-document-detect-missing-fonts-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lưu tài liệu Word – Phát hiện phông chữ thiếu với Aspose.Words

Bạn đã bao giờ cần **lưu tài liệu Word** nhưng không chắc một số phông chữ bên trong có tồn tại sau quá trình lưu‑xử lý không? Điều này xảy ra thường xuyên hơn bạn nghĩ, đặc biệt khi tài liệu di chuyển giữa các máy có thư viện phông chữ khác nhau. Tin tốt là gì? Aspose.Words cung cấp cho bạn một cách tích hợp để **phát hiện phông chữ thiếu** khi bạn **lưu tài liệu Word**, giúp bạn ghi log, cảnh báo, hoặc thậm chí thay thế chúng trước khi tệp xuất hiện trên màn hình người dùng.

Trong tutorial này, chúng ta sẽ đi qua một ví dụ hoàn chỉnh, sẵn sàng chạy, không chỉ lưu tài liệu Word mà còn **theo dõi phông chữ thiếu** và **bắt lỗi phông chữ** bằng một trình xử lý cảnh báo tùy chỉnh. Khi kết thúc, bạn sẽ hiểu tại sao callback cảnh báo quan trọng, cách gắn nó vào, và kết quả console trông như thế nào khi có sự thay thế. Không có phần thừa—chỉ có mã bạn có thể sao chép vào dự án .NET ngay lập tức.

> **Yêu cầu trước**  
> • .NET 6 (hoặc bất kỳ .NET Framework hiện đại nào) đã được cài đặt  
> • Visual Studio 2022 hoặc IDE yêu thích của bạn  
> • Bản sao có giấy phép của **Aspose.Words for .NET** (bản dùng thử miễn phí cũng đủ để thử nghiệm)  

Nếu bạn đã có những thứ trên, hãy bắt đầu nào.

---

## Lưu tài liệu Word và phát hiện phông chữ thiếu

Ý tưởng cốt lõi rất đơn giản: trước khi gọi `Document.Save`, gán một đối tượng thực thi `IWarningCallback` cho `Document.WarningCallback`. Aspose.Words sẽ gọi đối tượng này cho mọi cảnh báo mà nó gặp, bao gồm cả các cảnh báo **thay thế phông chữ** xảy ra khi tài liệu nguồn tham chiếu một phông chữ mà hệ thống của bạn không tìm thấy.

```csharp
using Aspose.Words;
using Aspose.Words.Warning;

// Step 1: Create a warning handler that prints font substitution messages
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only react to font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// Step 2: Load a document that may contain missing fonts
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Step 3: Register the warning handler with the document
document.WarningCallback = new FontWarningHandler();

// Step 4: Save the document; any font substitution warnings will be output to the console
document.Save("YOUR_DIRECTORY/output.docx");
```

**Bạn sẽ thấy:**  
Nếu `input.docx` tham chiếu một phông chữ chưa được cài đặt, console sẽ in ra một dòng như sau:

```
Font substitution: Font "Comic Sans MS" was substituted with "Arial".
```

Dòng này cho bạn biết chính xác phông chữ nào bị thiếu và Aspose.Words đã dùng phông nào thay thế—hoàn hảo để **bắt lỗi phông chữ** trước khi bạn phát hành tệp.

---

## Theo dõi phông chữ thiếu bằng Callback Cảnh báo (Bước‑từng‑bước)

### 1️⃣ Cài đặt Aspose.Words

Mở console NuGet của dự án và chạy:

```bash
dotnet add package Aspose.Words
```

Lệnh này sẽ tải phiên bản ổn định mới nhất (hiện tại là 24.10). Giữ thư viện luôn cập nhật giúp bạn nhận được các khả năng **phát hiện phông chữ thiếu** mới nhất và các bản sửa lỗi.

### 2️⃣ Định nghĩa Trình xử lý Cảnh báo

Tại sao chúng ta cần một lớp riêng? Việc thực thi `IWarningCallback` cho phép bạn tập trung toàn bộ logic cảnh báo ở một nơi. Bạn cũng có thể ghi log vào file, gửi telemetry, hoặc ném ngoại lệ nếu phông chữ thiếu là lỗi nghiêm trọng trong quy trình của bạn.

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only the warnings we care about
        if (info.Type == WarningType.FontSubstitution)
        {
            // Here we simply write to the console,
            // but you could replace this with any logging framework.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

> **Mẹo chuyên nghiệp:** Nếu bạn cần **theo dõi phông chữ thiếu** trên nhiều tài liệu, hãy lưu các thông điệp trong một `List<string>` bên trong handler và cung cấp chúng sau này để báo cáo.

### 3️⃣ Tải Tài liệu Nguồn của Bạn

Constructor `Document` có thể nhận đường dẫn file, stream, hoặc thậm chí là mảng byte thô. Trong hầu hết các trường hợp, bạn sẽ trỏ nó tới một `.docx` mà bạn nhận được từ người dùng hoặc hệ thống khác.

```csharp
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Nếu tệp lớn, cân nhắc sử dụng `LoadOptions` để bật lazy loading, giúp giảm áp lực bộ nhớ.

### 4️⃣ Gắn Callback

Gán thể hiện của bạn cho `doc.WarningCallback`. Từ thời điểm này, mọi cảnh báo (bao gồm cả thay thế phông chữ) sẽ đi qua handler của bạn.

```csharp
doc.WarningCallback = new FontWarningHandler();
```

### 5️⃣ Lưu Tài liệu

Bây giờ bạn có thể an toàn gọi `Save`. Trình xử lý cảnh báo chạy **đồng bộ** trong quá trình lưu, vì vậy bạn sẽ thấy đầu ra ngay lập tức.

```csharp
doc.Save("YOUR_DIRECTORY/output.docx");
```

Nếu bạn muốn lưu sang định dạng khác (PDF, HTML, v.v.), cơ chế cảnh báo vẫn hoạt động—Aspose.Words sẽ vẫn báo cáo phông chữ thiếu trước khi chuyển đổi.

---

## Bắt Lỗi Phông Chữ – Các Trường Hợp Cạnh Thường Gặp

Mặc dù luồng cơ bản bao phủ hầu hết các kịch bản, các dự án thực tế thường gặp một vài rắc rối. Dưới đây là một số biến thể bạn có thể gặp và cách xử lý chúng.

### Phông chữ thiếu trong Header/Footer

Header và Footer là các node riêng biệt, nhưng hệ thống cảnh báo xử lý chúng giống như văn bản trong body. Không cần code thêm; callback sẽ được kích hoạt cho các phông chữ này nữa. Chỉ cần chắc chắn bạn tải toàn bộ tài liệu (đây là hành vi mặc định).

### Nhiều lần Thay Thế trong Một Tài liệu

Nếu tài liệu sử dụng nhiều phông chữ không xác định, handler sẽ được gọi một lần cho mỗi lần thay thế. Để tránh tràn console, bạn có thể loại bỏ trùng lặp các thông điệp:

```csharp
class FontWarningHandler : IWarningCallback
{
    private readonly HashSet<string> _seen = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution && _seen.Add(info.Description))
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

### Chuyển Cảnh Báo thành Ngoại Lệ

Đôi khi một phông chữ thiếu là vấn đề không thể chấp nhận. Ném một ngoại lệ bên trong handler để hủy quá trình lưu:

```csharp
if (info.Type == WarningType.FontSubstitution)
{
    throw new InvalidOperationException($"Missing font detected: {info.Description}");
}
```

Nhớ bọc `doc.Save` trong khối `try/catch` để xử lý ngoại lệ một cách mềm mại.

---

## Xác Minh Kết Quả – Điều Gì Được Mong Đợi

Sau khi lưu xong, mở `output.docx` trong Microsoft Word (hoặc bất kỳ trình xem tương thích nào). Bạn sẽ thấy bố cục hình ảnh giống như bản gốc, nhưng các phông chữ đã được thay thế sẽ hiển thị dưới dạng fallback mà bạn đã thấy trong console. Để kiểm tra kỹ hơn, bạn có thể:

1. Mở **File → Options → Advanced → Show document content → Use draft quality** – tùy chọn này buộc Word hiển thị bất kỳ sự thay thế phông chữ ẩn nào.  
2. Sử dụng hộp thoại **Replace Fonts** của Word (`Ctrl+Shift+F`) để xem các phông chữ thực tế đã được nhúng.

Nếu mọi thứ khớp nhau, bạn đã **lưu tài liệu Word** thành công đồng thời **phát hiện phông chữ thiếu** và **bắt lỗi phông chữ**. 🎉

---

## Ví dụ Hoàn chỉnh (Sẵn sàng Sao chép)

Dưới đây là toàn bộ chương trình bạn có thể đưa vào một dự án Console App mới. Chỉ cần thay `YOUR_DIRECTORY` bằng đường dẫn thư mục thực tế trên máy của bạn.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warning;

namespace FontWarningDemo
{
    // Step 1: Create a warning handler that prints font substitution messages
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            // Only handle font‑substitution warnings
            if (info.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substitution: {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Load a document that may contain missing fonts
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // Step 3: Register the warning handler with the document
            document.WarningCallback = new FontWarningHandler();

            // Step 4: Save the document; any font substitution warnings will be output to the console
            document.Save("YOUR_DIRECTORY/output.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Kết quả console mong đợi** (ví dụ):

```
Font substitution: Font "Times New Roman" was substituted with "Arial".
Document saved successfully.
```

Đó là toàn bộ câu chuyện—không có bước ẩn, không có tài liệu bên ngoài phải tìm kiếm.

---

## Kết luận

Chúng tôi vừa cho bạn thấy cách **lưu tài liệu Word** đồng thời **phát hiện phông chữ thiếu**, **theo dõi phông chữ thiếu**, và **bắt lỗi phông chữ** bằng callback cảnh báo của Aspose.Words. Bằng cách kết nối một triển khai nhỏ `IWarningCallback`, bạn sẽ có khả năng quan sát đầy đủ các lần thay thế phông chữ tại thời điểm lưu, cho phép bạn ghi log, thay thế, hoặc hủy quá trình nếu cần.

Sẵn sàng cho thử thách tiếp theo? Hãy mở rộng handler để ghi cảnh báo vào một file JSON có cấu trúc, hoặc kết hợp với Aspose.PDF để chuyển đổi cùng tài liệu trong khi bảo toàn thông tin phông chữ. Bạn cũng có thể khám phá việc nhúng trực tiếp các phông chữ thiếu vào tệp đầu ra—Aspose.Words hỗ trợ nhúng phông chữ qua `LoadOptions.FontSettings`.

Hãy thử nghiệm, điều chỉnh mã cho phù hợp với quy trình của bạn, và cho chúng tôi biết kết quả như thế nào. Chúc bạn lập trình vui vẻ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}