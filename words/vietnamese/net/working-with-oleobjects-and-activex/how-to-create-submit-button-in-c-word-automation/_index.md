---
category: general
date: 2026-08-23
description: Tạo nút submit trong tự động hoá Word bằng C#. Học cách thêm nút ActiveX,
  đặt tên nút, chú thích và văn bản một cách lập trình.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create submit button
- set button text
- set button name
- add activex button
- set button caption
language: vi
lastmod: 2026-08-23
og_description: Tạo nút gửi trong tự động hoá Word bằng C#. Hướng dẫn này cho thấy
  cách thêm nút ActiveX, đặt tên, tiêu đề và văn bản của nó bằng Aspose.Words.
og_image_alt: Screenshot of a Word document showing a created submit button
og_title: Tạo nút gửi trong tự động hoá Word bằng C#
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  headline: How to create submit button in C# Word automation
  type: TechArticle
- description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  name: How to create submit button in C# Word automation
  steps:
  - name: Expected output
    text: 'Running the program creates `SubmitButton.docx`. When you open the file
      in Microsoft Word:'
  - name: Handling naming collisions
    text: 'If you run the routine multiple times on the same document, Word may auto‑rename
      duplicate controls. To guarantee uniqueness, you can prepend a GUID:'
  - name: Localizing the button caption
    text: 'For multilingual documents, store captions in a resource file and assign
      them at runtime:'
  - name: Responding to the button click
    text: 'The button itself does not contain click logic in C#. You typically attach
      a VBA macro:'
  type: HowTo
tags:
- C#
- Word automation
- ActiveX
- Aspose.Words
title: Cách tạo nút gửi trong tự động hoá Word bằng C#
url: /vi/net/working-with-oleobjects-and-activex/how-to-create-submit-button-in-c-word-automation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo nút submit trong tự động hoá Word bằng C#

Nếu bạn cần **tạo nút submit** trong một tài liệu Word bằng C#, hướng dẫn này sẽ đưa bạn qua toàn bộ quá trình. Bạn sẽ thấy cách thêm một nút ActiveX, gán một tên lập trình, và đặt chú thích cho nút sao cho nó trông giống như một điều khiển *Submit* thông thường.

Tự động hoá các điều khiển biểu mẫu trong Word có thể thay thế công việc bố trí thủ công và đảm bảo tính nhất quán trên hàng trăm tài liệu. Trong các bước dưới đây, bạn cũng sẽ học cách **đặt văn bản nút**, **đặt tên nút**, và **đặt chú thích nút** — tất cả đều thiết yếu khi nút tham gia vào quy trình làm việc dựa trên macro.

## Yêu cầu trước

* .NET 6.0 (hoặc mới hơn) đã được cài đặt.  
* Tham chiếu đến **Aspose.Words for .NET** (thư viện cung cấp `DocumentBuilder.InsertForms2OleControl`).  
* Kiến thức cơ bản về C# và các điều khiển biểu mẫu ActiveX của Word.  

Bạn có thể cài đặt Aspose.Words qua NuGet:

```bash
dotnet add package Aspose.Words
```

> **Mẹo chuyên nghiệp:** Sử dụng phiên bản ổn định mới nhất của Aspose.Words để được hưởng các bản sửa lỗi và tính năng mới liên quan đến các điều khiển ActiveX.

## Tổng quan về giải pháp

Hướng dẫn được tổ chức thành ba bước rõ ràng:

1. **Thêm nút ActiveX** – sử dụng phương thức `InsertForms2OleControl` để đặt một nút lệnh vào tài liệu.  
2. **Đặt tên nút** – gán một định danh lập trình duy nhất bằng thuộc tính `Name`.  
3. **Đặt chú thích nút** – xác định văn bản hiển thị trên nút qua thuộc tính `Caption` (cũng kiểm soát **đặt văn bản nút** mà bạn thấy trong giao diện người dùng).  

Khi kết thúc hướng dẫn, bạn sẽ có một quy trình **tạo nút submit** hoàn chỉnh mà có thể tái sử dụng trong bất kỳ dự án tự động hoá Word nào.

## Bước 1: Thêm nút ActiveX vào tài liệu

Nhiệm vụ đầu tiên là **thêm nút activex** vào tệp Word. Aspose.Words cung cấp enum `Forms2OleControlType.CommandButton` cho mục đích này.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load or create a new document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a CommandButton ActiveX control at the cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton);
```

**Tại sao bước này quan trọng:**  
Các điều khiển ActiveX là yếu tố duy nhất trong biểu mẫu Word có thể thực thi macro VBA hoặc tương tác với mã bên ngoài. Thêm điều khiển tạo ra một vị trí giữ chỗ mà các bước sau có thể cấu hình.

> **Trường hợp đặc biệt:** Nếu tài liệu đã chứa một điều khiển có cùng tên, Word sẽ tự động đổi tên cho điều khiển mới (ví dụ, `CommandButton1`). Việc đặt tên một cách rõ ràng trong bước tiếp theo sẽ tránh các xung đột này.

## Bước 2: Đặt tên nút

Một **đặt tên nút** đáng tin cậy là rất quan trọng khi bạn cần tham chiếu đến điều khiển từ VBA hoặc từ các phần khác của mã C#. Thuộc tính `Name` cung cấp cho nút một định danh lập trình.

```csharp
// Assign a unique programmatic name
commandBtn.Name = "btnSubmit";
```

**Tại sao bạn nên đặt tên:**  
Khi tài liệu được mở, VBA có thể lấy nút thông qua `ActiveDocument.InlineShapes("btnSubmit")`. Một tên có ý nghĩa như `btnSubmit` cũng làm rõ mục đích khi bạn kiểm tra XML của tài liệu.

> **Mẹo:** Giữ tên ngắn, chỉ gồm các ký tự chữ và số, và bắt đầu bằng một chữ cái để tương thích với quy tắc đặt tên của VBA.

## Bước 3: Đặt chú thích nút (văn bản hiển thị)

Văn bản mà người dùng thấy trên nút được điều khiển bởi thuộc tính **đặt chú thích nút**. Trong giao diện Word, điều này hiển thị dưới dạng nhãn của nút, cũng là **đặt văn bản nút** mà bạn muốn hiển thị.

```csharp
// Define the text shown on the button
commandBtn.Caption = "Submit";
```

**Tại sao chú thích quan trọng:**  
Chú thích là nhãn hướng tới người dùng. Thay đổi nó sau này không ảnh hưởng đến tên của nút, vì vậy bạn có thể địa phương hoá giao diện mà không làm hỏng bất kỳ mã nào phụ thuộc vào `btnSubmit`.

> **Câu hỏi thường gặp:** *Tôi có thể đặt cả Caption và Value không?*  
> Đối với `CommandButton`, `Caption` kiểm soát nhãn, trong khi `Value` không được sử dụng. Nếu bạn cần một giá trị ẩn, hãy lưu nó trong thuộc tính tài liệu tùy chỉnh thay vì.

## Ví dụ hoàn chỉnh hoạt động

Kết hợp ba bước lại với nhau sẽ cho bạn một quy trình hoàn chỉnh mà bạn có thể chèn vào bất kỳ ứng dụng console hoặc Windows nào:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert the ActiveX command button
        Forms2OleControl commandBtn = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton);

        // 3. Set a meaningful name for later reference
        commandBtn.Name = "btnSubmit";

        // 4. Set the visible caption (this is the button text)
        commandBtn.Caption = "Submit";

        // Optional: position the button (in points)
        commandBtn.Left = 100;   // distance from left margin
        commandBtn.Top = 200;    // distance from top margin
        commandBtn.Width = 80;
        commandBtn.Height = 30;

        // Save the document
        doc.Save("SubmitButton.docx");
        Console.WriteLine("Document with submit button created successfully.");
    }
}
```

### Kết quả mong đợi

Chạy chương trình sẽ tạo ra `SubmitButton.docx`. Khi bạn mở tệp trong Microsoft Word:

* Một nút **Submit** xuất hiện tại vị trí đã chỉ định.  
* Tên của nút là `btnSubmit` (kiểm tra qua *Developer → Design Mode → Properties*).  
* Nhấp vào nút trong chế độ thiết kế sẽ hiển thị chú thích *Submit*.  

Bây giờ bạn đã có một khối xây dựng có thể tái sử dụng cho bất kỳ giải pháp Word dựa trên biểu mẫu nào.

## Các lưu ý bổ sung

### Xử lý xung đột tên

Nếu bạn chạy quy trình nhiều lần trên cùng một tài liệu, Word có thể tự động đổi tên các điều khiển trùng lặp. Để đảm bảo tính duy nhất, bạn có thể thêm một GUID vào đầu:

```csharp
commandBtn.Name = $"btnSubmit_{Guid.NewGuid():N}";
```

### Địa phương hoá chú thích nút

Đối với tài liệu đa ngôn ngữ, lưu các chú thích trong tệp tài nguyên và gán chúng tại thời gian chạy:

```csharp
commandBtn.Caption = Resources.SubmitButtonLabel;
```

### Xử lý sự kiện nhấp nút

Nút tự nó không chứa logic nhấp trong C#. Thông thường bạn sẽ gắn một macro VBA:

```vba
Sub btnSubmit_Click()
    MsgBox "Form submitted!"
End Sub
```

Vì bạn đã **đặt tên nút** thành `btnSubmit`, tên macro sẽ tự động theo quy ước `<Name>_Click`.

## Câu hỏi thường gặp (FAQ) Khắc phục sự cố

| Question | Answer |
|----------|--------|
| **Tại sao nút lại hiển thị trống?** | Đảm bảo bạn đã đặt thuộc tính `Caption`; nếu không, nút sẽ không hiển thị văn bản. |
| **Tôi có thể sử dụng một điều khiển ActiveX khác không?** | Có. Thay thế `Forms2OleControlType.CommandButton` bằng `CheckBox`, `OptionButton`, v.v., nhưng các thuộc tính sẽ khác nhau. |
| **Điều này có tương thích với .NET Core không?** | Aspose.Words for .NET hỗ trợ .NET 6+, vì vậy cùng một đoạn mã hoạt động trên .NET Core và .NET Framework. |
| **Nếu tài liệu đã có một nút thì sao?** | Sử dụng một `Name` duy nhất (ví dụ, thêm GUID) để tránh xung đột. |

## Kết luận

Bây giờ bạn đã biết cách **tạo nút submit** một cách lập trình trong tài liệu Word bằng C#. Bằng cách thực hiện ba bước—**thêm nút activex**, **đặt tên nút**, và **đặt chú thích nút**—bạn có thể một cách đáng tin cậy **đặt văn bản nút**, **đặt tên nút**, và **đặt chú thích nút** cho bất kỳ giải pháp biểu mẫu tự động nào.  

Từ đây bạn có thể khám phá:

* Thêm macro VBA phản hồi khi nhấp vào **nút submit**.  
* Định dạng nút với phông chữ hoặc màu sắc tùy chỉnh thông qua XML nền.  
* Tạo nhiều nút trong một vòng lặp cho các biểu mẫu động.  

Hãy tự do thử nghiệm với các chú thích, tên và vị trí khác nhau để phù hợp với quy trình làm việc của bạn. Chúc bạn tự động hoá vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng dựa trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên đều có các ví dụ mã hoàn chỉnh kèm giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo hình nhóm trong tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Tạo biểu đồ đường trong Word bằng Aspose.Words cho .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Tạo tài liệu Word với Header và Footer bằng Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}