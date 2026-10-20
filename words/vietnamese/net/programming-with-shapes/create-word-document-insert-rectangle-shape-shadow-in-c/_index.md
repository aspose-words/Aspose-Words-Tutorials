---
category: general
date: 2026-05-26
description: Tạo tài liệu Word trong C# bằng Aspose.Words, chèn hình chữ nhật, đặt
  màu nền và thêm hiệu ứng đổ bóng – hướng dẫn từng bước.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- how to set fill
language: vi
og_description: Tạo tài liệu Word trong C# bằng Aspose.Words. Tìm hiểu cách chèn hình
  chữ nhật, đặt màu nền và thêm hiệu ứng bóng.
og_title: Tạo tài liệu Word – Chèn hình chữ nhật và bóng trong C#
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create Word document in C# with Aspose.Words, insert rectangle shape,
    set fill color, and add shadow effect – step‑by‑step guide.
  headline: Create Word Document – Insert Rectangle Shape & Shadow in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Tạo tài liệu Word – Chèn hình chữ nhật và bóng trong C#
url: /vi/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu Word – Chèn hình chữ nhật và bóng trong C#

Bạn đã bao giờ tự hỏi làm thế nào để **tạo tài liệu Word** một cách lập trình mà không cần mở Microsoft Word trước không? Bạn không phải là người duy nhất. Trong nhiều kịch bản tự động hoá—như hoá đơn, hợp đồng, hoặc tạo báo cáo hàng loạt—bạn cần một cách đáng tin cậy để tạo một tệp .docx, chèn một hình dạng vào bên trong, tô màu cho nó, và thậm chí có thể thêm bóng để có vẻ ngoài chuyên nghiệp.

Trong hướng dẫn này chúng ta sẽ đi qua từng bước: sử dụng Aspose.Words for .NET để **tạo tài liệu Word**, **chèn hình chữ nhật**, áp dụng màu nền, và **thêm bóng**. Khi kết thúc, bạn sẽ có một tệp sẵn sàng lưu và có thể đưa vào bất kỳ quy trình downstream nào.  

Chúng ta cũng sẽ đề cập đến **cách chèn hình dạng** một cách linh hoạt, và tại sao **cách đặt màu nền** lại quan trọng đối với tính nhất quán về hình ảnh. Không có phần thừa thãi, chỉ có mã bạn có thể sao chép‑dán và chạy.

## Yêu cầu trước

- .NET 6+ (hoặc .NET Framework 4.7+) đã được cài đặt.
- Giấy phép Aspose.Words for .NET hợp lệ (hoặc khóa đánh giá tạm thời).
- Visual Studio, Rider, hoặc bất kỳ IDE C# nào bạn thích.
- Kiến thức cơ bản về cú pháp C#—không cần gì phức tạp.

Bạn đã có tất cả? Tuyệt vời, hãy bắt đầu.

## Bước 1 – Tạo tài liệu Word

Điều đầu tiên bạn cần là một đối tượng tài liệu trống. Đây là canvas nơi mọi thứ khác sẽ tồn tại.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder.
Document doc = new Document();                 // The document itself.
DocumentBuilder builder = new DocumentBuilder(doc); // Helper to add content.
```

`Document` đại diện cho tệp .docx trong bộ nhớ, trong khi `DocumentBuilder` cung cấp một API tiện lợi để chèn văn bản, bảng và hình dạng. **Tạo tài liệu Word** theo cách này là tức thì—không giao diện người dùng, không COM interop, chỉ thuần .NET.

## Bước 2 – Chèn hình chữ nhật

Bây giờ chúng ta đã có tài liệu, hãy **chèn hình chữ nhật**. Phương thức `InsertShape` nhận một enum `ShapeType`, chiều rộng và chiều cao (đơn vị điểm). Chúng ta sẽ sử dụng một hình chữ nhật kích thước 150 × 80 điểm, tương đương khoảng 2 × 1 inch.

```csharp
// Step 2: Insert a rectangle shape of the desired size.
Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

Ở phía sau, Aspose tạo một đối tượng `Shape`, thêm nó vào đoạn hiện tại, và trả về một tham chiếu để bạn có thể định dạng. Đây là cốt lõi của **cách chèn hình dạng**—chỉ một dòng mã, nhưng vô cùng mạnh mẽ.

## Bước 3 – Cách đặt màu nền

Một hình dạng không có màu nền sẽ vô hình trên trang trắng. Hãy cho nó một nền xanh‑nhạt dễ chịu.

```csharp
// Step 3: Apply a fill color to make the shape visible.
shape.FillColor = System.Drawing.Color.LightBlue; // Any System.Drawing.Color works.
```

Bạn cũng có thể sử dụng gradient, texture, hoặc thậm chí là ảnh làm nền, nhưng màu đồng nhất giữ ví dụ đơn giản. Điều này minh họa **cách đặt màu nền** cho bất kỳ hình dạng nào bạn tạo, đảm bảo người đọc nhận được dấu hiệu hình ảnh mong muốn.

## Bước 4 – Cách thêm bóng

Bóng tạo độ sâu và làm cho hình dạng nổi bật hơn. Aspose.Words cung cấp một đối tượng `ShadowFormat` nơi bạn có thể bật/tắt hiển thị, chọn màu, và tinh chỉnh độ mờ, khoảng cách và góc.

```csharp
// Step 4: Configure the shadow effect – enable it, set color, blur, distance and angle.
shape.ShadowFormat.Visible = true;                     // Turn the shadow on.
shape.ShadowFormat.Color = System.Drawing.Color.Gray; // Shadow color.
shape.ShadowFormat.BlurRadius = 4.0;                  // Softness in pixels.
shape.ShadowFormat.Distance = 3.0;                    // How far the shadow is offset.
shape.ShadowFormat.Angle = 45;                        // Direction of the offset (degrees).
```

Tại sao lại dùng các giá trị này? Góc 45° tạo nguồn sáng tự nhiên từ trên‑phải, độ mờ vừa phải giữ bóng nhẹ nhàng, và khoảng cách ngắn ngăn hình dạng trông bị tách rời. Bạn có thể thử nghiệm—thay góc thành 135° sẽ làm bóng rơi về phía dưới‑trái, ví dụ.

## Bước 5 – Lưu tài liệu

Mọi công việc đã hoàn thành; bây giờ chúng ta ghi tệp ra đĩa. Chọn bất kỳ đường dẫn nào bạn muốn; chỉ cần chắc chắn thư mục tồn tại.

```csharp
// Step 5: Save the document with the shaped shadow.
doc.Save("YOUR_DIRECTORY/ShadowShape.docx");
```

Khi bạn mở `ShadowShape.docx` trong Microsoft Word, bạn sẽ thấy một hình chữ nhật xanh‑nhạt với bóng xám mềm—chính xác như chúng ta đã lập trình.

## Ví dụ hoàn chỉnh

Kết hợp tất cả lại, đây là chương trình đầy đủ, sẵn sàng sao chép‑dán:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a rectangle shape (150 × 80 points).
        Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

        // 3️⃣ Set a solid fill color so the shape is visible.
        shape.FillColor = System.Drawing.Color.LightBlue;

        // 4️⃣ Add a subtle shadow for depth.
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.Color = System.Drawing.Color.Gray;
        shape.ShadowFormat.BlurRadius = 4.0;   // pixels
        shape.ShadowFormat.Distance = 3.0;     // pixels
        shape.ShadowFormat.Angle = 45;        // degrees

        // 5️⃣ Persist the document.
        doc.Save("ShadowShape.docx");
    }
}
```

### Kết quả mong đợi

- Một tệp có tên **ShadowShape.docx** xuất hiện trong thư mục đích.
- Mở nó trong Word sẽ hiển thị một hình chữ nhật xanh‑nhạt nằm ở giữa trang đầu.
- Hình chữ nhật tạo ra một bóng xám với góc 45°, tạo hiệu ứng 3‑D nhẹ nhàng.

## Câu hỏi thường gặp & Trường hợp đặc biệt

**Nếu tôi cần một hình dạng khác thì sao?**  
Thay `ShapeType.Rectangle` bằng bất kỳ giá trị enum nào khác (`Ellipse`, `Star`, `Arrow`, v.v.). Phần còn lại của mã vẫn giữ nguyên.

**Tôi có thể thêm văn bản bên trong hình dạng không?**  
Có—sau khi tạo hình dạng, gọi `shape.AppendChild(new Paragraph(doc))` rồi chèn một `Run` chứa văn bản của bạn. Nhớ thiết lập các thuộc tính `shape.TextBox` nếu muốn văn bản được bao quanh.

**Còn DPI hoặc đơn vị đo lường thì sao?**  
Aspose làm việc bằng điểm (1 pt = 1/72 inch). Nếu bạn thích centimet, nhân với 28.35 (vì 1 cm ≈ 28.35 pt).

**Tôi có cần giấy phép để chạy không?**  
Phiên bản đánh giá sẽ thêm watermark trên trang đầu. Giấy phép chính thức sẽ loại bỏ watermark và mở khóa toàn bộ API.

## Mẹo & Lưu ý

- **Pro tip:** Gọi `builder.MoveToDocumentEnd()` trước khi chèn hình dạng nếu bạn muốn nó ở cuối cùng của tài liệu.
- **Watch out for:** Lưu vào thư mục chỉ đọc sẽ gây ra `UnauthorizedAccessException`. Đảm bảo ứng dụng của bạn có quyền ghi.
- **Performance note:** Đối với việc tạo hàng loạt (hàng trăm tài liệu), tái sử dụng một đối tượng `Document` làm mẫu và sao chép nó bằng `doc.Clone(true)` để tránh việc khởi tạo lặp lại.

## Kết luận

Bạn giờ đã biết cách **tạo tài liệu Word**, **chèn hình chữ nhật**, **đặt màu nền**, và **thêm bóng** bằng Aspose.Words for .NET. Đoạn mã trên là một giải pháp tự chứa mà bạn có thể đưa vào bất kỳ dự án C# nào, dù là ứng dụng console, API web, hay dịch vụ nền.

Từ đây bạn có thể khám phá:

- Thêm nhiều hình dạng với các màu khác nhau.
- Sử dụng gradient hoặc ảnh làm nền (`shape.FillColor = ...` → `shape.FillPattern`).
- Kết hợp hình dạng với bảng để tạo bố cục báo cáo phức tạp.

Hãy thử, điều chỉnh các tham số, và xem các tệp Word tự động của bạn trông chuyên nghiệp hơn chỉ với vài dòng mã. Chúc lập trình vui!

## Hướng dẫn liên quan

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}