---
category: general
date: 2026-08-04
description: Tạo tài liệu Word trống và chèn nút lệnh bằng Aspose.Words. Học cách
  đặt kích thước nút và thêm nút có thể nhấp trong C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert command button
- add clickable button
- set button size
- create command button
language: vi
lastmod: 2026-08-04
og_description: Tạo tài liệu Word trống bằng Aspose.Words và chèn một nút lệnh. Hướng
  dẫn này chỉ cách thiết lập kích thước nút, thêm nút có thể nhấp, và lưu tệp.
og_image_alt: Screenshot of a Word document containing a clickable command button
  created with C#
og_title: Tạo tài liệu Word trống và thêm nút lệnh – hướng dẫn C# đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  headline: Create blank word document with a command button – step‑by‑step guide
  type: TechArticle
- description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  name: Create blank word document with a command button – step‑by‑step guide
  steps:
  - name: The ProgID of the OLE control – `"CommandButton"` for a standard button.
    text: The ProgID of the OLE control – `"CommandButton"` for a standard button.
  - name: A `Rectangle` that defines the **set button size** and position.
    text: A `Rectangle` that defines the **set button size** and position.
  - name: The caption that appears on the button.
    text: The caption that appears on the button.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Tạo tài liệu Word trống bằng nút lệnh – hướng dẫn từng bước
url: /vi/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu Word trống với nút lệnh – hướng dẫn từng bước

Nếu bạn cần **tạo tài liệu Word trống** có chứa một nút tương tác, hướng dẫn này sẽ chỉ cho bạn cách thực hiện bằng Aspose.Words for .NET. Bạn sẽ học cách **chèn nút lệnh**, điều chỉnh giao diện của nó và làm cho nó có thể nhấp – tất cả chỉ trong vài dòng C#.

Hướng dẫn bao gồm mọi thứ từ thiết lập dự án đến lưu file cuối cùng, vì vậy bạn có thể sao chép‑dán giải pháp hoàn chỉnh vào ứng dụng của mình. Trong quá trình thực hiện, chúng tôi cũng sẽ giải thích cách **thêm nút có thể nhấp**, **đặt kích thước nút**, và **tạo nút lệnh** bằng mã.

## Prerequisites

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* .NET 6.0 SDK hoặc phiên bản mới hơn.
* Visual Studio 2022 (hoặc bất kỳ IDE nào hỗ trợ .NET).
* Gói NuGet Aspose.Words for .NET (`Aspose.Words` phiên bản 23.12 hoặc mới hơn).
* Kiến thức cơ bản về C# và lập trình hướng đối tượng.

Không cần bất kỳ assembly interop Office nào bổ sung vì Aspose.Words hoạt động hoàn toàn độc lập với Microsoft Word.

## Step 1: Set up the .NET project

Tạo một ứng dụng console sẽ chứa mã tự động hoá Word.

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

Lệnh này tạo một thư mục mới `WordButtonDemo` với file `Program.cs` đã sẵn sàng chạy và thêm thư viện Aspose.Words.

## Step 2: Create blank word document

Hoạt động đầu tiên là **tạo tài liệu Word trống**. Aspose.Words cung cấp lớp `Document` đại diện cho một file Word rỗng ngay từ đầu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a new, empty Word document.
Document doc = new Document();
```

Việc tạo một tài liệu trống cung cấp cho bạn một canvas sạch sẽ để có thể thêm đoạn văn, bảng, hoặc trong trường hợp này, một nút lệnh OLE.

## Step 3: Initialize DocumentBuilder

`DocumentBuilder` là công cụ trợ giúp cho phép bạn chèn nội dung vào tài liệu. Bạn cần gắn nó vào tài liệu vừa tạo.

```csharp
// Attach a DocumentBuilder to the empty document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder duy trì vị trí con trỏ hiện tại, vì vậy bất kỳ chèn nào tiếp theo sẽ diễn ra chính xác ở vị trí bạn muốn.

## Step 4: Insert command button

Bây giờ chúng ta **chèn nút lệnh** (một OLE `Forms2OleControl`) vào tài liệu. Phương thức `InsertForms2OleControl` yêu cầu ba đối số:

1. ProgID của điều khiển OLE – `"CommandButton"` cho một nút tiêu chuẩn.
2. Một `Rectangle` xác định **đặt kích thước nút** và vị trí.
3. Caption (chú thích) sẽ hiển thị trên nút.

```csharp
// Define the button's position (x, y) and size (width, height).
Rectangle buttonRect = new Rectangle(0, 0, 120, 30); // 120 px wide, 30 px high

// Insert the command button with the desired caption.
Forms2OleControl cmdButton = builder.InsertForms2OleControl(
    "CommandButton",   // ProgID for a CommandButton control
    buttonRect,        // Position and size
    "Click Me");       // Caption displayed on the button
```

Khi tài liệu được mở trong Word, nút sẽ hoạt động như bất kỳ điều khiển biểu mẫu gốc nào — bạn có thể nhấp vào nó, và Word sẽ kích hoạt macro liên quan (nếu có). Điều này đáp ứng yêu cầu **thêm nút có thể nhấp**.

### Why use Forms2OleControl?

`Forms2OleControl` nhúng một đối tượng OLE trực tiếp vào file DOCX, giữ nguyên các thuộc tính của điều khiển mà không cần assembly Word Interop. Đây là cách đáng tin cậy nhất để **tạo nút lệnh** hoạt động trên mọi phiên bản Word.

## Step 5: Customize the button (optional)

Bạn có thể muốn **đặt kích thước nút** một cách chính xác hơn hoặc thay đổi các thuộc tính bổ sung như phông chữ hoặc màu nền. Aspose.Words cho phép truy cập đối tượng OLE nền tảng, giúp bạn tinh chỉnh thêm.

```csharp
// Example: change the button's background color (requires OLE automation).
// Note: This step is optional and demonstrates additional customization.
cmdButton.OleFormat.Icon = true; // Show an icon instead of the default appearance.
```

Nếu cần kích thước khác, chỉ cần điều chỉnh các giá trị `Rectangle` trong Bước 4. Các tọa độ được đo bằng điểm (1 pt = 1/72 inch), vì vậy `120` tương đương khoảng 1.67 inch chiều rộng.

## Step 6: Save the document

Cuối cùng, ghi tài liệu ra đĩa. File kết quả sẽ là một **tài liệu Word trống** có nút lệnh hoạt động đầy đủ.

```csharp
// Save the document as a .docx file.
doc.Save("CommandButtonDemo.docx");
```

Khi bạn mở `CommandButtonDemo.docx` trong Microsoft Word, sẽ thấy một nút có nhãn “Click Me”. Nhấp vào nút sẽ hiển thị hộp thoại macro mặc định trừ khi bạn gắn macro tùy chỉnh.

## Complete source code

Dưới đây là chương trình đầy đủ mà bạn có thể sao chép vào `Program.cs`. Nó bao gồm tất cả các bước đã mô tả và biên dịch mà không cần chỉnh sửa.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordButtonDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Create a blank word document.
            Document doc = new Document();

            // Step 3: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 4: Define button size and insert command button.
            Rectangle buttonRect = new Rectangle(0, 0, 120, 30);
            Forms2OleControl cmdButton = builder.InsertForms2OleControl(
                "CommandButton",
                buttonRect,
                "Click Me");

            // Optional: further customization (e.g., set icon).
            // cmdButton.OleFormat.Icon = true;

            // Step 6: Save the document.
            doc.Save("CommandButtonDemo.docx");

            System.Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Expected result

Chạy chương trình sẽ tạo ra `CommandButtonDemo.docx`. Mở file trong Word sẽ hiển thị:

* Một trang duy nhất chứa một nút có nhãn **Click Me**.
* Nút tuân theo **đặt kích thước nút** (120 × 30 điểm).
* Nhấp vào nút sẽ kích hoạt hành vi nút lệnh mặc định của Word, xác nhận rằng thao tác **thêm nút có thể nhấp** đã thành công.

## Common questions and edge cases

| Question | Answer |
|----------|--------|
| **Does this work with .doc files?** | Yes. Change the file extension in `doc.Save("file.doc")`. The OLE control is stored in the legacy binary format as well. |
| **What if I need multiple buttons?** | Call `InsertForms2OleControl` repeatedly, adjusting the `Rectangle` for each new button to avoid overlap. |
| **Can I attach a macro to the button?** | The button itself does not contain macro code. You must add a VBA macro to the document manually or via the `Document` object’s `Modules` collection. |
| **Is the button visible in PDF export?** | When you export the DOCX to PDF using Aspose.Words, the button is rendered as a static image, not an interactive control. |
| **What versions of Word are supported?** | The OLE command button works in Word 2007 and later, as it follows the standard Forms2.0 specification. |

## Conclusion

Bạn đã biết cách **tạo tài liệu Word trống**, **chèn nút lệnh**, **thêm nút có thể nhấp**, và **đặt kích thước nút** bằng Aspose.Words for .NET. Ví dụ hoàn chỉnh minh họa quy trình **tạo nút lệnh** từ đầu đến cuối, cung cấp nền tảng vững chắc cho các tác vụ tự động hoá Word nâng cao hơn.

## Next steps

* Khám phá các điều khiển OLE khác (ví dụ: `CheckBox`, `ListBox`) bằng cách thay đổi ProgID trong `InsertForms2OleControl`.
* Kết hợp nút với macro VBA để thực hiện các hành động tùy chỉnh khi người dùng nhấp.
* Sử dụng `DocumentBuilder` của Aspose.Words để thêm nội dung bổ sung như bảng, hình ảnh hoặc chú thích trước khi chèn nút.
* Thử nghiệm các giá trị **đặt kích thước nút** để phù hợp với yêu cầu bố cục tài liệu của bạn.

Happy coding, and enjoy building richer Word documents with interactive controls!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}