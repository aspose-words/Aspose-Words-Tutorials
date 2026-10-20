---
category: general
date: 2026-06-24
description: Cách sử dụng IWarningCallback để phát hiện phông chữ thiếu trong tài
  liệu Aspose.Words. Tìm hiểu ví dụ đầy đủ, có thể chạy được và các thực tiễn tốt
  nhất.
draft: false
keywords:
- how to use iwarningcallback
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- missing font detection in .docx
language: vi
og_description: Cách sử dụng IWarningCallback để phát hiện phông chữ thiếu trong Aspose.Words.
  Tham khảo hướng dẫn từng bước để có giải pháp hoàn chỉnh, sẵn sàng cho môi trường
  sản xuất.
og_title: Cách sử dụng IWarningCallback – Phát hiện phông chữ thiếu
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to use IWarningCallback to detect missing fonts in Aspose.Words
    documents. Learn a full, runnable example and best practices.
  headline: How to Use IWarningCallback – Detect Missing Fonts with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Processing
title: Cách sử dụng IWarningCallback – Phát hiện phông chữ thiếu với Aspose.Words
url: /vi/net/working-with-fonts/how-to-use-iwarningcallback-detect-missing-fonts-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách Sử Dụng IWarningCallback – Phát Hiện Phông Chữ Thiếu trong Aspose.Words

Việc sử dụng **IWarningCallback** là rất quan trọng khi bạn làm việc với Aspose.Words và cần **phát hiện phông chữ thiếu** trong tệp DOCX. Trong hướng dẫn này, chúng tôi sẽ đi qua một ví dụ đầy đủ, có thể sao chép‑dán, cho bạn thấy cách sử dụng IWarningCallback để bắt các cảnh báo thay thế phông chữ, lý do tại sao nó quan trọng, và những việc cần làm sau khi bạn đã thu thập chúng.

Nếu bạn từng mở một tài liệu và thấy văn bản bị rối vì một phông chữ tùy chỉnh chưa được cài đặt, bạn sẽ hiểu sự bực bội. Khi kết thúc tutorial này, bạn sẽ có một cách đáng tin cậy để phát hiện các vấn đề đó bằng chương trình, ghi lại chúng, hoặc thậm chí tự động áp dụng phông chữ dự phòng.

## Những Điều Bạn Sẽ Học

- Mục đích của **IWarningCallback** và khi nào nên sử dụng nó.  
- Cách triển khai một bộ thu thập cảnh báo tùy chỉnh để cô lập các sự kiện **detect missing fonts**.  
- Kết nối bộ thu thập vào **LoadOptions** để mọi lần tải tài liệu đều được giám sát.  
- Xác minh đầu ra và xử lý các trường hợp biên (nhiều phông chữ thiếu, cảnh báo im lặng, v.v.).  

### Yêu Cầu Trước

- .NET 6.0 hoặc cao hơn (mã cũng hoạt động trên .NET Framework 4.6+).  
- Aspose.Words cho .NET được cài đặt qua NuGet (`Install-Package Aspose.Words`).  
- Một tệp DOCX tham chiếu tới một phông chữ không có trên máy (ví dụ, `DocumentWithMissingFont.docx`).  

Không cần thư viện bổ sung—tất cả đều nằm trong Aspose.Words.

---

## Cách Sử Dụng IWarningCallback để Phát Hiện Phông Chữ Thiếu trong Aspose.Words

Dưới đây là **chương trình đầy đủ, có thể chạy được**. Sao chép nó vào một dự án console mới, điều chỉnh đường dẫn tệp, và chạy. Bạn sẽ thấy đầu ra console cho mỗi cảnh báo phông chữ thiếu.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 1: Create a warning collector that implements IWarningCallback.
    // This collector will be invoked each time Aspose.Words raises a warning.
    class FontWarningCollector : IWarningCallback
    {
        // The Warning method receives a WarningInfo object.
        // We filter for FontSubstitution warnings because those indicate missing fonts.
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // Print the warning to the console – you could also log to a file or database.
                Console.WriteLine($"[Missing Font] {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2: Configure LoadOptions to use our custom collector.
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // Step 3: Load the document with the specified options.
            // Any font that cannot be resolved triggers the warning collector above.
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

            try
            {
                Document doc = new Document(docPath, loadOptions);
                Console.WriteLine("Document loaded successfully.");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error loading document: {ex.Message}");
            }

            // Keep the console window open when debugging.
            Console.WriteLine("Press any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Đầu Ra Dự Kiến

Nếu `DocumentWithMissingFont.docx` tham chiếu tới một phông chữ có tên *“MyFancyFont”* mà không được cài đặt, bạn sẽ thấy một cái gì đó như sau:

```
[Missing Font] Font substitution: The font 'MyFancyFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
Press any key to exit...
```

Mỗi dòng bắt đầu bằng **[Missing Font]** được tạo ra bởi triển khai **IWarningCallback** của chúng tôi, chứng minh rằng chúng ta đã thành công trong việc **detect missing fonts**.

## Bước 1: Triển Khai Giao Diện IWarningCallback

Tại sao chúng ta cần một lớp tùy chỉnh? Aspose.Words phát sinh **warnings** vì nhiều lý do—vấn đề định dạng tệp, tính năng đã lỗi thời, và quan trọng nhất đối với chúng ta, thay thế phông chữ. Bằng cách triển khai `IWarningCallback`, chúng ta có một hook nhận mọi cảnh báo khi chúng xảy ra. Lọc theo `WarningType.FontSubstitution` giúp cô lập trường hợp cụ thể khi một phông chữ bị thiếu.

**Mẹo:** Nếu bạn cần ghi lại *tất cả* cảnh báo để chẩn đoán, chỉ cần xóa kiểm tra `if` và ghi lại mọi `info.Type`.

## Bước 2: Kết Nối Callback vào LoadOptions

`LoadOptions` là cổng cho phép Aspose.Words biết cách xử lý tài liệu đầu vào. Đặt `WarningCallback` thành một thể hiện của bộ thu thập của chúng tôi đảm bảo callback hoạt động trong toàn bộ quá trình tải. Bạn có thể tái sử dụng cùng một đối tượng `LoadOptions` cho nhiều tài liệu, rất tiện trong các pipeline xử lý hàng loạt.

**Câu hỏi thường gặp:** *Nếu tôi tải một tài liệu mà không chỉ định LoadOptions thì sao?*  
Trả lời: Aspose.Words vẫn sẽ phát sinh cảnh báo nội bộ, nhưng nếu không có callback chúng sẽ bị bỏ qua một cách im lặng, và bạn sẽ mất cơ hội **detect missing fonts**.

## Bước 3: Tải Tài Liệu và Thu Thập Cảnh Báo Phông Chữ Thiếu

Constructor `Document` nhận đường dẫn tệp và `LoadOptions` thực hiện công việc nặng. Khi tệp được phân tích, bất kỳ phông chữ nào thiếu sẽ kích hoạt phương thức `FontWarningCollector.Warning` của chúng tôi. Đầu ra console chứng minh cơ chế hoạt động.

**Trường hợp biên:** Một tài liệu có thể tham chiếu tới nhiều phông chữ không tồn tại. Callback sẽ được gọi một lần cho mỗi phông chữ thiếu, vì vậy bạn sẽ thấy nhiều dòng—lý tưởng để xây dựng báo cáo toàn diện.

## Tại Sao Nên Dùng IWarningCallback Thay Vì Kiểm Tra Phông Chữ Thủ Công?

Bạn có thể quét thủ công các thuộc tính `Run.Font` của tài liệu sau khi tải, nhưng điều này đòi hỏi tài liệu phải tải thành công trước—điều này sẽ thất bại nếu phông chữ hoàn toàn không có. Hệ thống cảnh báo hoạt động **trước** khi bất kỳ sự thay thế nào diễn ra, cung cấp cho bạn hình ảnh thực tế về những gì đang thiếu.

Thêm nữa, callback chạy **như một phần của pipeline tải**, có nghĩa là bạn có thể dừng sớm, thay thế phông chữ ngay lập tức, hoặc ghi lại chẩn đoán chi tiết mà không cần quét lại cây tài liệu.

## Xử Lý Nhiều Phông Chữ Thiếu Một Cách Trơn Tru

Nếu bạn dự đoán sẽ có nhiều phông chữ thiếu, hãy cân nhắc gom chúng vào một collection:

```csharp
class AggregatingFontCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}
```

Sau khi tải, bạn có thể duyệt qua `MissingFonts` và, ví dụ, ghi chúng vào tệp CSV cho đội thiết kế.

## Thêm: Ghi Lại Cảnh Báo Vào Tệp

Đầu ra console đủ cho demo, nhưng mã sản xuất thường ghi vào kho lưu trữ bền vững. Thay thế lời gọi `Console.WriteLine` bằng một thứ gì đó như:

```csharp
File.AppendAllText("font-warnings.log", $"{DateTime.Now}: {info.Description}{Environment.NewLine}");
```

Bây giờ bạn có một bản ghi audit có thể xem lại sau, đáp ứng yêu cầu tuân thủ.

## Kết Luận

Chúng tôi đã trình bày **cách sử dụng IWarningCallback** để **detect missing fonts** trong Aspose.Words, từ việc triển khai callback đến việc kết nối nó vào `LoadOptions` và xử lý các cảnh báo phát sinh. Cách tiếp cận này cung cấp cho bạn thông tin thời gian thực về các vấn đề liên quan đến phông chữ, cho phép bạn ghi log, thay thế, hoặc cảnh báo người dùng trước khi tài liệu được hiển thị.

Các bước tiếp theo bạn có thể khám phá:

- **Fallback fonts:** gán một phông chữ mặc định một cách lập trình khi xảy ra sự thay thế.  
- **Batch processing:** lặp qua một thư mục các tài liệu, tái sử dụng cùng một `AggregatingFontCollector`.  
- **User feedback:** hiển thị các cảnh báo phông chữ thiếu trong giao diện người dùng thay vì console.

Hãy thử trong dự án của bạn—không còn văn bản rối rắm bí ẩn, chỉ còn chẩn đoán rõ ràng, có thể hành động. Chúc lập trình vui vẻ!

## Bạn Nên Học Gì Tiếp Theo?

Các tutorial sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với các giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách Tải DOCX và Phát Hiện Phông Chữ Thiếu – Hướng Dẫn C# Đầy Đủ](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [Cách Phát Hiện Phông Chữ trong Aspose.Words – Xử Lý Cảnh Báo & Cài Đặt](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Cách Sử Dụng LoadOptions trong Aspose.Words – Hướng Dẫn Đầy Đủ](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}