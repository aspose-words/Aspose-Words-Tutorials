---
category: general
date: 2026-04-10
description: Cách sử dụng LoadOptions trong Aspose.Words để ghi lại cảnh báo thay
  thế phông chữ khi tải tài liệu. Tìm hiểu giải pháp C# từng bước với ví dụ mã đầy
  đủ.
draft: false
keywords:
- how to use loadoptions
- warningcallback
- font substitution warning
- aspose.words loadoptions example
- c# document loading
language: vi
og_description: Cách sử dụng LoadOptions trong Aspose.Words để ghi nhận cảnh báo thay
  thế phông chữ khi tải tài liệu. Hướng dẫn này sẽ đưa bạn qua một triển khai đầy
  đủ bằng C#.
og_title: Cách sử dụng LoadOptions trong Aspose.Words – Hướng dẫn C# đầy đủ
tags:
- Aspose.Words
- C#
- Document Processing
- Font Management
title: Cách sử dụng LoadOptions trong Aspose.Words – Hướng dẫn C# đầy đủ
url: /vi/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách Sử Dụng LoadOptions trong Aspose.Words – Hướng Dẫn Đầy Đủ C#

Cách sử dụng LoadOptions trong Aspose.Words là một rào cản phổ biến khi bạn cần kiểm soát chặt chẽ quá trình tải tài liệu. Trong hướng dẫn này, chúng tôi sẽ chỉ cho bạn **cách sử dụng LoadOptions** để bắt các cảnh báo thay thế phông chữ và phản hồi chúng trong C#.  

Nếu bạn từng mở một tệp DOCX tham chiếu đến một phông chữ bị thiếu và tự hỏi tại sao kết quả hiển thị kỳ lạ, bạn đã đến đúng nơi. Chúng tôi sẽ đi qua toàn bộ quy trình, từ việc tạo một thể hiện `LoadOptions` đến việc in chi tiết cảnh báo lên console. Khi kết thúc, bạn sẽ có một đoạn mã sẵn sàng chạy mà bạn có thể chèn vào bất kỳ dự án .NET nào.

## Những Điều Bạn Sẽ Học

- Tại sao `LoadOptions` lại quan trọng đối với việc nhập tài liệu đáng tin cậy.  
- Cách gắn một **WarningCallback** để specifically watches for **font substitution warnings**.  
- Mã chính xác cần thiết để tải một tệp Word với các tùy chọn này được bật.  
- Mẹo xử lý các trường hợp đặc biệt, như tài liệu chứa nhiều phông chữ bị thiếu.  

Không cần tài liệu bên ngoài—mọi thứ bạn cần đều có ở đây.

## Yêu Cầu

| Yêu Cầu | Lý Do |
|-------------|--------|
| .NET 6.0 hoặc mới hơn | Cung cấp môi trường chạy cho cú pháp C# 10 được sử dụng trong các ví dụ. |
| Aspose.Words for .NET (phiên bản mới nhất) | Thư viện cung cấp `LoadOptions` và cơ sở hạ tầng cảnh báo. |
| Một tệp DOCX có thể tham chiếu đến các phông chữ bạn chưa cài đặt | Để thấy callback cảnh báo hoạt động. |
| Visual Studio 2022 (hoặc bất kỳ IDE nào bạn thích) | Giúp việc gỡ lỗi và kiểm thử trở nên đơn giản. |

Nếu bạn đã có những thứ này, tuyệt vời—hãy bắt đầu.

## Bước 1 – Tạo Đối Tượng LoadOptions và Kết Nối WarningCallback

Điều đầu tiên bạn làm khi **cách sử dụng LoadOptions** là khởi tạo nó. Phần quan trọng là gán một delegate cho `WarningCallback`. Delegate này sẽ được kích hoạt mỗi khi Aspose.Words gặp một tình huống muốn thông báo cho bạn—đặc biệt là phông chữ bị thiếu.

```csharp
using System;
using Aspose.Words;

// Step 1: Build LoadOptions with a warning listener.
LoadOptions loadOptions = new LoadOptions
{
    // The lambda receives the sender (unused) and a WarningInfo object.
    WarningCallback = (sender, args) =>
    {
        // We'll filter for font‑substitution warnings later.
        if (args.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution: {args.Description}");
        }
    }
};
```

**Tại sao điều này quan trọng:** Nếu không có callback, Aspose.Words sẽ âm thầm thay thế các phông chữ thiếu bằng mặc định, và bạn có thể không bao giờ nhận ra sự thay đổi về hình ảnh. Bằng cách đăng ký một `WarningCallback`, bạn sẽ có một log thời gian thực của mọi lần thay thế, điều này rất cần thiết cho các pipeline tài liệu đảm bảo chất lượng.

## Bước 2 – Chỉ Phản Hồi Các Cảnh Báo Thay Thế Phông Chữ

Bạn có thể tự hỏi liệu callback có tràn ngập bạn bằng các cảnh báo không liên quan (như tính năng đã lỗi thời) không. Câu trả lời là *có*—nhưng chúng ta có thể lọc chúng. Trong đoạn mã trên, chúng ta đã kiểm tra `args.WarningType == WarningType.FontSubstitution`. Dòng này là **bộ bảo vệ cảnh báo thay thế phông chữ**, một từ khóa phụ giúp giữ cho đầu ra tập trung.

Nếu bạn cần xử lý các loại cảnh báo khác, chỉ cần mở rộng khối `if`:

```csharp
if (args.WarningType == WarningType.FontSubstitution)
{
    // Existing handling…
}
else if (args.WarningType == WarningType.UnknownFileFormat)
{
    Console.WriteLine($"❓ Unknown format: {args.Description}");
}
```

Mẫu này cho thấy cơ chế **warningcallback** linh hoạt như thế nào, cho phép bạn tùy chỉnh phản hồi chính xác cho các kịch bản mà bạn quan tâm.

## Bước 3 – Tải Tài Liệu Của Bạn Bằng LoadOptions Đã Cấu Hình

Bây giờ listener đã sẵn sàng, phần cuối cùng là truyền thể hiện `LoadOptions` vào constructor của `Document`. Đây là khoảnh khắc mà **ví dụ Aspose.Words LoadOptions** thực sự tỏa sáng.

```csharp
// Step 3: Load the DOCX while the warning callback is active.
try
{
    Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
    Console.WriteLine("✅ Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"🚨 Failed to load document: {ex.Message}");
}
```

**Bạn sẽ thấy gì:** Nếu DOCX tham chiếu đến một phông chữ không được cài đặt trên máy, console sẽ xuất ra một dòng như:

```
⚠️ Font substitution: Font 'Calibri Light' has been substituted with 'Arial'.
✅ Document loaded successfully.
```

Dòng output này xác nhận bạn đã **cách sử dụng LoadOptions** thành công để giám sát các vấn đề phông chữ.

## Ví Dụ Hoàn Chỉnh (Sẵn Sàng Sao Chép‑Dán)

Dưới đây là chương trình đầy đủ mà bạn có thể biên dịch và chạy ngay lập tức. Nó kết hợp cả ba bước, thêm một vài tiện ích (như banner thân thiện), và minh họa cách xử lý lỗi.

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        Console.WriteLine("=== Aspose.Words LoadOptions Demo ===");

        // 1️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = (sender, args) =>
            {
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substitution: {args.Description}");
                }
            }
        };

        // 2️⃣ Attempt to load the document.
        try
        {
            // Replace the path with your own file that may contain missing fonts.
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
            Console.WriteLine("✅ Document loaded without fatal errors.");

            // Optional: Do something with the document, e.g., save as PDF.
            // doc.Save("output.pdf");
        }
        catch (Exception e)
        {
            Console.WriteLine($"🚨 Error: {e.Message}");
        }

        Console.WriteLine("=== End of Demo ===");
    }
}
```

### Kết Quả Mong Đợi

Chạy chương trình trên một máy không có phông chữ được tham chiếu trong `input.docx` sẽ cho ra kết quả tương tự:

```
=== Aspose.Words LoadOptions Demo ===
⚠️ Font substitution: Font 'Times New Roman' has been substituted with 'Arial'.
✅ Document loaded without fatal errors.
=== End of Demo ===
```

Nếu mọi phông chữ đều có, bạn sẽ chỉ thấy các thông báo thành công—không có dòng cảnh báo nào xuất hiện.

## Những Sai Lầm Thường Gặp & Mẹo Chuyên Nghiệp

- **Sai lầm:** Quên thiết lập `WarningCallback`. Mã vẫn sẽ tải, nhưng bạn sẽ bỏ lỡ chi tiết thay thế.  
  **Mẹo:** Luôn gán callback ngay sau khi tạo `LoadOptions`; việc này nhẹ và sẽ đền đáp sau này.

- **Sai lầm:** Sử dụng đường dẫn tương đối trỏ sai thư mục.  
  **Mẹo:** Dùng `Path.Combine(Environment.CurrentDirectory, "input.docx")` để tìm file một cách chắc chắn hơn.

- **Sai lầm:** Giả định rằng cảnh báo sẽ ngăn việc tải.  
  **Mẹo:** Cảnh báo thay thế phông chữ là *thông tin*; chúng không làm dừng quá trình tải. Nếu bạn cần kiểm tra nghiêm ngặt hơn, ném ngoại lệ trong callback khi xảy ra thay thế.

- **Sai lầm:** Chạy trên server không cài bất kỳ phông chữ nào (ví dụ, Docker image tối thiểu).  
  **Mẹo:** Cài trước các phông chữ cần thiết hoặc đóng gói chúng cùng ứng dụng, sau đó xác minh bằng callback rằng không có sự thay thế nào xảy ra trong môi trường production.

## Khi Nào Nên Dùng LoadOptions Thay Vì Kiểm Tra Sau Khi Tải

Bạn có thể hỏi, “Tại sao không chỉ kiểm tra tài liệu sau khi đã tải?” Câu trả lời nằm ở hiệu suất và độ chính xác. Bằng cách xử lý cảnh báo **trong quá trình tải**, bạn bắt gặp vấn đề sớm—trước khi bất kỳ tính toán bố cục hay chuyển đổi PDF nào diễn ra. Điều này đặc biệt có giá trị trong các pipeline xử lý hàng loạt, nơi mỗi bước bổ sung đều tốn thời gian.

## Mở Rộng Ví Dụ: Lưu Báo Cáo Các Phông Chữ Đã Thay Thế

Nếu bạn cần một bản ghi vĩnh viễn (có thể cho mục đích tuân thủ), hãy chỉnh sửa callback để thu thập các thông điệp vào một danh sách và ghi chúng vào file sau khi tải:

```csharp
var substitutions = new List<string>();

loadOptions.WarningCallback = (s, a) =>
{
    if (a.WarningType == WarningType.FontSubstitution)
    {
        substitutions.Add(a.Description);
        Console.WriteLine($"⚠️ {a.Description}");
    }
};

// After loading:
File.WriteAllLines("font-substitutions.txt", substitutions);
```

Bây giờ bạn có cả phản hồi trên console và một log bền vững.

## Các Chủ Đề Liên Quan Bạn Có Thể Khám Phá Tiếp Theo

- **Cách nhúng phông chữ tùy chỉnh trong Aspose.Words** – loại bỏ hoàn toàn việc thay thế.  
- **Sử dụng LoadOptions để giới hạn kích thước tài liệu** – giúp bảo vệ trước các tệp độc hại quá lớn.  
- **Chuyển đổi Word sang PDF với kiểu chữ được bảo toàn** – kết hợp tốt với cách tiếp cận warning‑callback.  

Mỗi mục trên đều dựa trên nền tảng bạn vừa xây dựng với `LoadOptions`.

## Kết Luận

Chúng ta đã bao quát **cách sử dụng LoadOptions** trong Aspose.Words từ đầu đến cuối: tạo các tùy chọn, gắn một `WarningCallback` tập trung vào **cảnh báo thay thế phông chữ**, và tải tài liệu một cách tự tin. Ví dụ đầy đủ chạy ngay “out‑of‑the‑box”, và các mẹo bổ sung giúp bạn tránh những bẫy thường gặp.  

Hãy thoải mái thử nghiệm—đổi callback sang các loại cảnh báo khác, ghi log vào cơ sở dữ liệu, hoặc tích hợp logic này vào dịch vụ web kiểm tra các tệp Word được tải lên. Mô hình này linh hoạt, đáng tin cậy, và quan trọng nhất, cung cấp cho bạn khả năng nhìn thấy quá trình thay thế phông chữ ẩn có thể làm hỏng việc hiển thị tài liệu.

Chúc lập trình vui vẻ, và mong tài liệu của bạn luôn hiển thị đúng như mong muốn!

![Sơ đồ mô tả luồng sử dụng LoadOptions với callback cảnh báo trong Aspose.Words](https://example.com/images/loadoptions-flow.png "Sơ đồ cách sử dụng LoadOptions")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}