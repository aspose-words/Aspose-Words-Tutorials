---
category: general
date: 2026-08-14
description: Cách thêm nút ActiveX vào tài liệu Word bằng Aspose.Words – học cách
  tạo tài liệu Word trống và chèn nút ActiveX một cách lập trình.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert activex button
- create empty word document
- create word document aspose
language: vi
lastmod: 2026-08-14
og_description: Cách thêm nút ActiveX vào tài liệu Word bằng Aspose.Words. Hướng dẫn
  này chỉ cho bạn cách tạo một tài liệu Word trống, chèn nút ActiveX và lưu kết quả.
og_image_alt: Screenshot of an ActiveX button inserted into a Word document using
  Aspose.Words
og_title: Cách thêm nút ActiveX trong Word – Hướng dẫn Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  headline: How to add ActiveX button in a Word document with Aspose.Words
  type: TechArticle
- description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  name: How to add ActiveX button in a Word document with Aspose.Words
  steps:
  - name: Does the button work in all Word versions?
    text: ActiveX controls are supported in the desktop version of Word on Windows.
      They are not rendered in Word Online, Word for macOS, or mobile clients. If
      you need cross‑platform interactivity, consider using content controls or HTML‑based
      solutions instead.
  - name: What if I need a different size or position?
    text: '`InsertForms2OleControl` places the control at the current builder cursor.
      To move it, adjust the cursor with `builder.MoveTo` before insertion, or modify
      the control’s `Left` and `Top` properties after creation:'
  - name: Can I add other ActiveX types?
    text: Yes. The `Forms2OleControlType` enumeration includes `CheckBox`, `OptionButton`,
      `ListBox`, and more. Replace `CommandButton` with the desired enum value and
      adjust properties accordingly.
  - name: Is a macro required for the button to do something?
    text: The button itself does nothing until you attach VBA code. In Word, press
      **Alt+F11** to open the VBA editor, locate `btnSubmit_Click`, and write the
      desired logic. The generated document will retain the VBA project if you enable
      the **SaveFormat.Doc** (legacy `.doc`) format, but `.docx` files cannot
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Word automation
- C#
title: Cách thêm nút ActiveX vào tài liệu Word bằng Aspose.Words
url: /vi/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách thêm nút ActiveX vào tài liệu Word bằng Aspose.Words

Nếu bạn cần **cách thêm ActiveX** vào các điều khiển trong một tệp Word được tạo, hướng dẫn này sẽ cho bạn các bước chính xác. Bạn sẽ học cách **chèn nút ActiveX** một cách lập trình, bắt đầu từ **tạo tài liệu Word trống** và kết thúc bằng một tệp đã lưu có thể mở trong Microsoft Word.

Thêm một nút chạy mã VBA hoặc kích hoạt macro là yêu cầu phổ biến cho các trình tạo báo cáo tự động, mẫu biểu mẫu hoặc hợp đồng tương tác. Sử dụng Aspose.Words cho .NET cho phép bạn xây dựng tài liệu mà không cần khởi chạy Office, giữ cho quá trình nhanh chóng và thân thiện với máy chủ.

## Yêu cầu trước

* .NET 6.0 (hoặc mới hơn) SDK đã được cài đặt.  
* Visual Studio 2022 hoặc bất kỳ IDE nào hỗ trợ C#.  
* Gói NuGet Aspose.Words cho .NET (`Aspose.Words` phiên bản 24.9 hoặc mới hơn).  
  Cài đặt bằng cách:
  ```bash
  dotnet add package Aspose.Words
  ```
* Môi trường Windows nếu bạn dự định kiểm thử nút ActiveX, vì các điều khiển ActiveX yêu cầu phiên bản Windows của Microsoft Word.

## Bước 1: Tạo tài liệu Word trống

Nhiệm vụ đầu tiên là **tạo tài liệu Word trống** trong bộ nhớ. Aspose.Words cung cấp lớp `Document` cho mục đích này.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, blank Word document.
Document doc = new Document();
```

`Document` đại diện cho toàn bộ tệp .docx. Tại thời điểm này tài liệu chưa có trang nào, nhưng bạn có thể bắt đầu thêm nội dung ngay lập tức.

## Bước 2: Khởi tạo DocumentBuilder

`DocumentBuilder` là một công cụ hỗ trợ cho phép bạn chèn văn bản, hình ảnh và các đối tượng khác vào tài liệu. Nó hoạt động trên đối tượng `Document` mà bạn vừa tạo.

```csharp
// Initialise the builder with the blank document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder duy trì vị trí con trỏ; bất kỳ nội dung nào bạn chèn sau dòng này sẽ xuất hiện ở đầu trang đầu tiên.

## Bước 3: Chèn điều khiển ActiveX CommandButton

Aspose.Words cung cấp phương thức `InsertForms2OleControl` để thêm các điều khiển biểu mẫu cổ điển, bao gồm ActiveX. Phương thức này yêu cầu loại điều khiển và kích thước của nó tính bằng điểm.

```csharp
// Insert an ActiveX CommandButton (150x30 points).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

Đối tượng `Forms2OleControl` trả về cho phép bạn cấu hình các thuộc tính như tên và chú thích của điều khiển.

## Bước 4: Cấu hình thuộc tính của nút

Đặt một `Name` có ý nghĩa giúp bạn tham chiếu đến điều khiển từ mã VBA sau này. `Caption` là văn bản người dùng nhìn thấy trên nút.

```csharp
// Set the button’s programmatic name (used in VBA) and displayed caption.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

> **Pro tip:** Giữ tên ngắn gọn và chỉ chứa ký tự chữ và số; Word sẽ từ chối các tên có chứa dấu cách hoặc ký tự đặc biệt.

## Bước 5: Lưu tài liệu

Cuối cùng, ghi tài liệu ra đĩa. Sử dụng phần mở rộng `.docx` cho các tệp Word hiện đại; nút ActiveX hoạt động tương tự trong các tệp `.doc`, nhưng `.docx` là định dạng được ưu tiên cho các dự án mới.

```csharp
// Save the document containing the ActiveX button.
doc.Save(@"C:\Temp\ActiveXButton.docx");
```

Khi bạn mở `ActiveXButton.docx` trong Microsoft Word, bạn sẽ thấy một nút **Submit** có thể nhấp. Nếu bật macro, bạn có thể gắn mã VBA vào `btnSubmit_Click` và nó sẽ thực thi khi người dùng nhấn nút.

## Ví dụ đầy đủ, có thể chạy được

Kết hợp tất cả các phần lại với nhau sẽ cho bạn một chương trình tự chứa mà bạn có thể sao chép, dán và chạy.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create an empty Word document.
            Document doc = new Document();

            // Step 2: Initialise DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX CommandButton control.
            Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Step 4: Set button properties.
            cmdBtn.Name = "btnSubmit";
            cmdBtn.Caption = "Submit";

            // Step 5: Save the document.
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Expected output** – Sau khi chạy chương trình, console sẽ in ra vị trí lưu, và khi mở tệp đã tạo trong Word sẽ hiển thị một nút có nhãn **Submit** nằm ở đầu trang đầu tiên.

## Xử lý các câu hỏi thường gặp và các trường hợp đặc biệt

### Nút có hoạt động trên mọi phiên bản Word không?

Các điều khiển ActiveX được hỗ trợ trong phiên bản desktop của Word trên Windows. Chúng không được hiển thị trong Word Online, Word cho macOS, hoặc các khách hàng di động. Nếu bạn cần tính tương tác đa nền tảng, hãy cân nhắc sử dụng content controls hoặc các giải pháp dựa trên HTML thay thế.

### Nếu tôi cần kích thước hoặc vị trí khác thì sao?

`InsertForms2OleControl` đặt điều khiển tại vị trí con trỏ hiện tại của builder. Để di chuyển, điều chỉnh con trỏ bằng `builder.MoveTo` trước khi chèn, hoặc sửa các thuộc tính `Left` và `Top` của điều khiển sau khi tạo:

```csharp
cmdBtn.Left = 100;   // points from the left margin
cmdBtn.Top = 200;    // points from the top margin
```

### Tôi có thể thêm các loại ActiveX khác không?

Có. Định danh `Forms2OleControlType` bao gồm `CheckBox`, `OptionButton`, `ListBox`, và nhiều hơn nữa. Thay `CommandButton` bằng giá trị enum mong muốn và điều chỉnh các thuộc tính tương ứng.

### Có cần macro để nút thực hiện hành động không?

Nút tự nó không làm gì cho tới khi bạn gắn mã VBA. Trong Word, nhấn **Alt+F11** để mở trình chỉnh sửa VBA, tìm `btnSubmit_Click`, và viết logic mong muốn. Tài liệu được tạo sẽ giữ lại dự án VBA nếu bạn bật định dạng **SaveFormat.Doc** (định dạng `.doc` kế thừa), nhưng các tệp `.docx` không thể lưu macro VBA. Sử dụng định dạng `.doc` nếu bạn cần VBA nhúng.

## Kết luận

Bạn giờ đã biết **cách thêm ActiveX** vào tệp Word bằng Aspose.Words. Bằng cách thực hiện các bước **tạo tài liệu Word trống**, khởi tạo `DocumentBuilder`, **chèn nút ActiveX**, cấu hình các thuộc tính của nó và lưu tệp, bạn có thể tạo các mẫu Word tương tác trực tiếp từ mã .NET của mình.

Tiếp theo, khám phá các chủ đề liên quan như xử lý sự kiện **insert ActiveX button**, thêm **create word document aspose** cho bảng hoặc hình ảnh, và bảo mật tài liệu có macro cho triển khai doanh nghiệp. Thử nghiệm với các loại điều khiển và tùy chọn bố cục khác nhau để điều chỉnh trải nghiệm người dùng cho nhu cầu ứng dụng của bạn.

Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao quát các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo tài liệu Word với Header và Footer bằng Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Tạo Group Shape trong tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Tạo tài liệu Word với Table bằng Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}