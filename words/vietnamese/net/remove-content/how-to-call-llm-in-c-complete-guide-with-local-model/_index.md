---
category: general
date: 2026-01-13
description: Học cách gọi LLM từ C# bằng endpoint LLM cục bộ, chỉnh sửa file Word,
  xóa toàn bộ nội dung và lưu file docx—tất cả trong một hướng dẫn.
draft: false
keywords:
- how to call llm
- use local llm
- remove all content
- how to edit word
- how to save docx
language: vi
og_description: Cách gọi LLM từ C# bằng mô hình cục bộ, chỉnh sửa tài liệu Word, xóa
  toàn bộ nội dung và lưu file docx một cách hiệu quả.
og_title: Cách gọi LLM trong C# – Hướng dẫn từng bước
tags:
- Aspose.Words
- C#
- LLM Integration
title: Cách gọi LLM trong C# – Hướng dẫn đầy đủ với mô hình cục bộ
url: /vi/net/remove-content/how-to-call-llm-in-c-complete-guide-with-local-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách Gọi LLM trong C# – Hướng Dẫn Đầy Đủ với Mô Hình Cục Bộ

Bạn đã bao giờ tự hỏi **how to call LLM** từ một ứng dụng .NET mà không gửi dữ liệu lên đám mây chưa? Bạn không phải là người duy nhất. Nhiều nhà phát triển muốn giữ các prompt và tài liệu trên máy chủ nội bộ, đặc biệt khi xử lý văn bản nhạy cảm. Trong hướng dẫn này, chúng ta sẽ đi qua một kịch bản thực tế: sử dụng một endpoint LLM tự lưu trữ để viết lại tài liệu Word, xóa toàn bộ nội dung, chỉnh sửa tệp, và cuối cùng **how to save docx** trở lại đĩa.  

Chúng tôi cũng sẽ đề cập đến **use local LLM**, cho bạn thấy đoạn mã chính xác để **remove all content** từ một `Document` của Aspose.Words, và giải thích các chi tiết khi chỉnh sửa tệp Word bằng chương trình. Khi kết thúc, bạn sẽ có một giải pháp copy‑and‑paste hoạt động với Aspose.Words 7+ và bất kỳ mô hình cục bộ tương thích OpenAI nào.

## Các Yêu Cầu Trước – Những Gì Bạn Cần Trước Khi Bắt Đầu

- **.NET 6+** (hoặc .NET Framework 4.7.2 nếu bạn thích phiên bản cổ điển)
- **Aspose.Words for .NET** gói NuGet (`Aspose.Words` và `Aspose.Words.AI`)
- Một **local LLM** cung cấp endpoint `/v1` tương thích OpenAI (ví dụ: máy chủ GPT‑Neo tại `http://localhost:8000/v1`)
- Một mẫu `input.docx` được đặt trong thư mục bạn kiểm soát
- Visual Studio, Rider, hoặc bất kỳ trình soạn thảo nào bạn thích – tôi sẽ dùng VS Code trong các ảnh chụp màn hình

> **Pro tip:** Nếu bạn chưa có mô hình cục bộ, hãy xem hình ảnh Docker miễn phí cho GPT‑Neo 2.7B – nó khởi động trong vòng chưa đầy một phút và tuân thủ cùng hợp đồng API mà chúng tôi sử dụng ở đây.

## Bước 1 – Cấu Hình Endpoint Local LLM (How to Call LLM)

Điều đầu tiên bạn cần làm khi muốn **how to call llm** từ C# là tạo một đối tượng client trỏ tới dịch vụ tự lưu trữ của bạn. Aspose.Words.AI cung cấp một trợ giúp `LocalLargeLanguageModel` để trừu tượng hoá các cuộc gọi HTTP.

```csharp
using Aspose.Words;
using Aspose.Words.AI;

// Configure the self‑hosted LLM endpoint
var llm = new LocalLargeLanguageModel
{
    Endpoint = "http://localhost:8000/v1",   // your local server
    ModelName = "my-gpt-neo"                // name as registered in the server
};
```

> **Why this matters:** Bằng cách tự cấu hình endpoint, bạn giữ toàn quyền kiểm soát payload yêu cầu, xác thực và độ trễ. Đây là cốt lõi của **how to call llm** mà không phụ thuộc vào dịch vụ bên ngoài.

## Bước 2 – Tải Tài Liệu Word Nguồn (How to Edit Word)

Tiếp theo, chúng ta tải tệp `.docx` gốc vào một `Document` của Aspose. Đây là bước “how to edit word” truyền thống: một khi tệp đã ở trong bộ nhớ, bạn có thể truy vấn, sửa đổi, hoặc thay thế hoàn toàn nội dung của nó.

```csharp
// Load the source document from disk
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

Nếu tệp không tồn tại, bạn sẽ nhận được `FileNotFoundException`, vì vậy hãy chắc chắn đường dẫn đúng. Bạn cũng có thể tải từ một `Stream` nếu đang xử lý các tệp tải lên.

## Bước 3 – Tạo Văn Bản Được Sửa Đổi Bằng Local LLM (How to Call LLM)

Bây giờ phần kỳ diệu: chúng ta yêu cầu LLM viết lại toàn bộ văn bản với tông trang trọng. Prompt được tạo bằng cách nối một hướng dẫn ngắn với văn bản thô được trích xuất qua `document.GetText()`.

```csharp
// Ask the model to rewrite the whole document in a formal tone
string prompt = "Rewrite the following in formal tone:\n" + document.GetText();

string revisedText = llm.GenerateText(prompt);
```

> **Edge case:** Nếu tài liệu nguồn quá lớn (hơn 10 k token) bạn có thể vượt quá giới hạn ngữ cảnh của mô hình. Trong trường hợp đó, hãy chia văn bản thành các đoạn và gọi `GenerateText` cho mỗi phần.

## Bước 4 – Xóa Tất Cả Nội Dung Hiện Tại (Remove All Content)

Trước khi chèn văn bản mới, chúng ta cần xóa sạch tài liệu. Aspose cung cấp `RemoveAllChildren()` để xoá toàn bộ sections, paragraphs, tables—tất cả. Đây là cách chuẩn để **remove all content** khỏi một tệp Word.

```csharp
// Clear the document completely
document.RemoveAllChildren();
```

> **What if you only wanted to delete the body but keep headers?** Sử dụng `document.Sections.Clear()` và sau đó xây dựng lại các sections bạn cần.

## Bước 5 – Chèn Văn Bản Được Sửa Đổi (How to Edit Word)

Với một tài liệu sạch, chúng ta có thể ghi lại văn bản do LLM tạo. `DocumentBuilder` là lớp bao bọc thân thiện cho phép bạn thêm đoạn văn, bảng, hình ảnh, v.v. Ở đây chúng ta chỉ ghi toàn bộ chuỗi thành một đoạn duy nhất.

```csharp
// Re‑populate the document with the revised text
DocumentBuilder builder = new DocumentBuilder(document);
builder.Writeln(revisedText);
```

Nếu bạn cần định dạng phong phú hơn (đậm, tiêu đề) bạn có thể phân tích đầu ra của LLM để tìm các ký hiệu markdown và áp dụng các thiết lập `builder.Font` tương ứng.

## Bước 6 – Lưu Tài Liệu Đã Cập Nhật (How to Save Docx)

Cuối cùng, chúng ta lưu các thay đổi vào một tệp mới. Điều này minh họa **how to save docx** sau khi chỉnh sửa bằng chương trình.

```csharp
// Save the edited document
document.Save("YOUR_DIRECTORY/output.docx");
```

Phương thức `Save` tự động phát hiện định dạng từ phần mở rộng tệp, vì vậy bạn cũng có thể xuất ra PDF, HTML, hoặc ODT chỉ bằng một dòng thay đổi.

### Kết Quả Mong Đợi

Khi bạn mở `output.docx`, bạn sẽ thấy toàn bộ nội dung gốc đã được viết lại theo phong cách tinh tế, trang trọng. Không còn bảng, tiêu đề hay chân trang thừa từ nguồn—chỉ có văn bản mới mà bạn yêu cầu LLM tạo ra.

![Ảnh chụp màn hình output.docx mở trong Word, hiển thị văn bản được viết lại trang trọng – how to call llm](/images/output-docx.png "ví dụ how to call llm")

*Image alt text:* **ví dụ how to call llm hiển thị tài liệu Word đã được viết lại**

## Các Câu Hỏi Thông Thường & Khắc Phục Sự Cố

### 1. “Nếu LLM của tôi trả về lỗi thì sao?”

Phương thức `GenerateText` ném ra `HttpRequestException` cho các phản hồi không phải 2xx. Bao bọc cuộc gọi trong `try/catch` và kiểm tra `ex.Message`. Thường vấn đề là thiếu header API key hoặc vượt quá giới hạn token của mô hình.

```csharp
try
{
    string revisedText = llm.GenerateText(prompt);
}
catch (HttpRequestException ex)
{
    Console.WriteLine($"LLM call failed: {ex.Message}");
    // fallback logic, e.g., return the original text
}
```

### 2. “Tôi có thể chỉnh sửa các phần cụ thể của tài liệu thay vì xóa toàn bộ không?”

Chắc chắn. Sử dụng `document.GetChildNodes(NodeType.Paragraph, true)` để liệt kê các đoạn, sau đó thay thế thuộc tính `Paragraph.Text` chỉ ở những nơi bạn cần thay đổi. Cách này cho phép bạn **how to edit word** ở mức độ chi tiết trong khi giữ nguyên các style.

### 3. “Có cách nào để giữ nguyên định dạng gốc không?”

Nếu bạn muốn giữ nguyên các style, hãy cân nhắc trả về đầu ra của LLM dưới dạng plain text và sau đó áp dụng `builder.Font.StyleIdentifier` cho mỗi đoạn dựa trên mẫu của bạn. Ngoài ra, sử dụng `DocumentBuilder.InsertHtml()` nếu LLM có thể xuất HTML.

### 4. “Làm sao để xử lý tài liệu lớn?”

Chia tài liệu thành các sections (`document.Sections`) và xử lý từng phần riêng biệt. Điều này không chỉ tránh giới hạn token mà còn giảm áp lực bộ nhớ.

## Mẹo Tối Ưu Hiệu Suất

- **Reuse `LocalLargeLanguageModel` instance** trong nhiều lần gọi; `HttpClient` nền sẽ giữ kết nối sống.
- **Cache the revised text** nếu bạn dự đoán sẽ chạy lại cùng một prompt nhiều lần—các cuộc gọi LLM có thể tốn kém ngay cả trên phần cứng cục bộ.
- **Parallelize** việc xử lý các section bằng `Parallel.ForEach` khi bạn có CPU đa nhân và một client LLM thread‑safe.

## Các Bước Tiếp Theo – Mở Rộng Quy Trình

Bây giờ bạn đã biết **how to call llm**, **use local llm**, **remove all content**, **how to edit word**, và **how to save docx**, bạn có thể muốn khám phá:

- **Batch processing**: Lặp qua một thư mục chứa các tệp `.docx` và áp dụng cùng một logic viết lại.
- **Custom prompts**: Tùy chỉnh hướng dẫn để tạo bản tóm tắt, danh sách gạch đầu dòng, hoặc bản dịch.
- **Integration with ASP.NET Core**: Phơi bày một endpoint HTTP nhận tải lên tệp, chạy LLM, và trả về tài liệu đã chỉnh sửa.
- **Advanced styling**: Phân tích markdown từ LLM và ánh xạ nó tới các style Word bằng `DocumentBuilder`.

Mỗi phần mở rộng này dựa trên mẫu cốt lõi mà chúng ta đã đề cập, vì vậy bạn sẽ có thể điều chỉnh mã với ít nỗ lực.

## Kết Luận

Trong hướng dẫn này, chúng tôi đã đề cập **how to call llm** từ C# bằng một endpoint tự lưu trữ, trình bày **use local llm**, chỉ ra cách đúng để **remove all content** khỏi một tệp Word, giải thích **how to edit word** bằng chương trình, và kết thúc bằng một ví dụ rõ ràng về **how to save docx**. Mẫu hoàn chỉnh, có thể chạy ngay đã sẵn sàng để đưa vào bất kỳ dự án .NET nào, và các giải thích cung cấp “tại sao” cho mỗi bước—giúp bạn tùy chỉnh, mở rộng hoặc gỡ lỗi một cách tự tin.

Hãy thử nghiệm, chơi với các prompt khác nhau, và để LLM cục bộ thực hiện phần công việc nặng cho các quy trình tự động hoá tài liệu của bạn. Nếu gặp bất kỳ trục trặc nào, phần khắc phục sự cố sẽ chỉ dẫn bạn đúng hướng. Chúc lập trình vui vẻ, và tận hưởng sức mạnh của LLM on‑prem!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}