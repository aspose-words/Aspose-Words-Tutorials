---
category: general
date: 2026-08-20
description: Học cách tạo điều khiển ActiveX, thiết lập kích thước nút và thêm nút
  vào Word với một ví dụ C# đầy đủ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- set button size
- add button to word
- how to insert button
- create clickable button
language: vi
lastmod: 2026-08-20
og_description: Tạo điều khiển ActiveX trong tệp Word bằng C#. Hướng dẫn này chỉ cách
  thiết lập kích thước nút, thêm nút vào Word và tạo nút có thể nhấp chuột.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX control
  button
og_title: Tạo một điều khiển ActiveX trong Word – hướng dẫn C# chi tiết từng bước
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  headline: How to create ActiveX control in a Word document using C#
  type: TechArticle
- description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  name: How to create ActiveX control in a Word document using C#
  steps:
  - name: Why this works
    text: '* `InsertForms2OleControl` tells Word to embed an OLE object of type **CommandButton**,
      which is the classic ActiveX button class. * The width and height arguments
      directly **set button size**; Word translates the values from points (1 pt ≈
      1/72 in). * Naming the control (`Name = "btnSubmit"`) makes'
  - name: Pro tip
    text: 'If you want a square button, set both dimensions to the same value:'
  - name: 1. What if the button does not appear after saving?
    text: '* Verify that the Aspose.Words version supports `InsertForms2OleControl`.
      Versions prior to 22.5 lack this feature. * Ensure the target file format is
      `.docx` or `.doc`. Older formats like `.rtf` cannot store ActiveX objects.'
  - name: 2. Can I insert the button at a specific bookmark?
    text: 'Yes. Move the builder to the bookmark before calling `InsertForms2OleControl`:'
  - name: 3. How to **set button size** dynamically based on text length?
    text: Calculate the required width using the `Graphics.MeasureString` method (from
      `System.Drawing`) and convert pixels to points (`points = pixels * 72 / DPI`).
      Then pass the computed width to `InsertForms2OleControl`.
  - name: 4. Is there a way to add multiple buttons in a loop?
    text: 'Absolutely. Wrap the insertion logic in a `for` loop and adjust the `Left`
      and `Top` properties for each iteration:'
  type: HowTo
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
title: Cách tạo điều khiển ActiveX trong tài liệu Word bằng C#
url: /vi/java/integration-interoperability/how-to-create-activex-control-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo điều khiển ActiveX trong tài liệu Word bằng C#

Nếu bạn cần **tạo điều khiển ActiveX** bên trong một tệp Microsoft Word, hướng dẫn này sẽ chỉ cho bạn cách thực hiện chính xác. Bạn sẽ thấy cách **thêm nút vào Word**, đặt kích thước của nút, và làm cho điều khiển có thể nhấn – tất cả chỉ với một chương trình C# ngắn gọn, tự chứa.

Trong tutorial này, bạn sẽ:

* Hiểu tại sao một điều khiển ActiveX hữu ích cho các tài liệu Word tương tác.  
* Học đoạn mã chính xác để **đặt kích thước nút** và gán chú thích.  
* Xem cách **tạo nút có thể nhấn** mà sau này có thể gắn với macro hoặc logic bên ngoài.  

Các bước này hoạt động với Aspose.Words .NET 23.12 trở lên và chỉ yêu cầu môi trường phát triển .NET.

> **Yêu cầu trước** – Bạn có giấy phép Aspose.Words hợp lệ (hoặc đang sử dụng phiên bản dùng thử) và Visual Studio 2022 hoặc bất kỳ IDE C# nào.

---

## Cách tạo điều khiển ActiveX trong tài liệu Word

Bước đầu tiên là khởi tạo một `Document` trống và một `DocumentBuilder`. Builder cung cấp API cấp cao để chèn các đối tượng như điều khiển ActiveX.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document and obtain a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // The rest of the steps are explained in the following sections.
            InsertActiveXButton(builder);

            // Save the result so you can open it in Word.
            doc.Save("ActiveXButton.docx");
            Console.WriteLine("Document saved as ActiveXButton.docx");
        }
```

Phương thức `InsertActiveXButton` (được định nghĩa phía dưới) chứa logic **cách chèn nút** và cấu hình nó.

```csharp
        /// <summary>
        /// Inserts a CommandButton ActiveX control, sets its size, name, and caption.
        /// </summary>
        static void InsertActiveXButton(DocumentBuilder builder)
        {
            // Step 2: Insert a CommandButton ActiveX control with the desired size (width: 100, height: 30).
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                "CommandButton", 100, 30);

            // Step 3: Assign a name to the control for later reference.
            commandButton.Name = "btnSubmit";

            // Step 4: Set the caption that will be displayed on the button.
            commandButton.Caption = "Submit";

            // Optional: Position the button on the page (e.g., 100 points from the top left).
            commandButton.Left = 100;
            commandButton.Top = 150;
        }
    }
}
```

Chạy chương trình sẽ tạo **ActiveXButton.docx**. Mở tệp trong Word sẽ hiển thị một nút có nhãn **Submit**. Điều khiển hoạt động đầy đủ — khi nhấn sẽ kích hoạt sự kiện chuẩn `CommandButton_Click`, bạn có thể liên kết sau này với một macro VBA.

### Tại sao cách này hoạt động

* `InsertForms2OleControl` yêu cầu Word nhúng một đối tượng OLE loại **CommandButton**, đây là lớp nút ActiveX cổ điển.  
* Các đối số chiều rộng và chiều cao trực tiếp **đặt kích thước nút**; Word chuyển đổi giá trị từ điểm (1 pt ≈ 1/72 in).  
* Đặt tên cho điều khiển (`Name = "btnSubmit"`) giúp dễ dàng tìm kiếm từ VBA (`ActiveDocument.InlineShapes("btnSubmit")`).  

---

## Đặt kích thước và chú thích cho nút

Nếu bạn muốn giao diện khác, hãy điều chỉnh các đối số số trong lời gọi `InsertForms2OleControl`. Chữ ký của phương thức là:

```csharp
Forms2OleControl InsertForms2OleControl(string progId, double width, double height);
```

* **progId** – Định danh chương trình của lớp ActiveX (`"CommandButton"` cho nút tiêu chuẩn).  
* **width / height** – Kích thước tính bằng điểm. Đối với nút rộng 2 cm, dùng `width = 56.7` (2 cm ≈ 56.7 pt).  

Bạn cũng có thể sửa đổi chú thích sau khi chèn:

```csharp
commandButton.Caption = "Send Request";
```

Thay đổi chú thích không ảnh hưởng đến kích thước, nhưng sẽ thay đổi phản hồi hình ảnh cho người dùng.

### Mẹo chuyên nghiệp

Nếu bạn muốn nút hình vuông, hãy đặt cả hai kích thước bằng nhau:

```csharp
Forms2OleControl squareBtn = builder.InsertForms2OleControl("CommandButton", 50, 50);
squareBtn.Caption = "OK";
```

---

## Thêm nút vào Word và làm cho nó có thể nhấn

Mã ở trên đã **thêm nút vào Word**. Để nút thực hiện một hành động, bạn phải viết một macro VBA xử lý sự kiện `Click`. Dưới đây là macro tối thiểu bạn có thể dán vào trình chỉnh sửa VBA của Word (`Alt+F11` → Insert → Module):

```vba
Sub btnSubmit_Click()
    MsgBox "You clicked the Submit button!", vbInformation
End Sub
```

Vì điều khiển được đặt tên `btnSubmit`, Word tự động ánh xạ sự kiện `Click` tới `btnSubmit_Click`. Đây là cách tiêu chuẩn để **tạo nút có thể nhấn** mà không cần thư viện bên ngoài.

> **Lưu ý:** Cài đặt bảo mật macro trong Word có thể chặn các điều khiển ActiveX. Đảm bảo chọn “Enable all macros” hoặc “Enable VBA macros” cho tài liệu, hoặc ký số macro để sử dụng trong môi trường sản xuất.

---

## Câu hỏi thường gặp: cách chèn nút và khắc phục sự cố

### 1. Nếu nút không xuất hiện sau khi lưu thì sao?

* Kiểm tra phiên bản Aspose.Words có hỗ trợ `InsertForms2OleControl` không. Các phiên bản trước 22.5 không có tính năng này.  
* Đảm bảo định dạng tệp đích là `.docx` hoặc `.doc`. Các định dạng cũ như `.rtf` không thể lưu đối tượng ActiveX.

### 2. Tôi có thể chèn nút vào một bookmark cụ thể không?

Có. Di chuyển builder tới bookmark trước khi gọi `InsertForms2OleControl`:

```csharp
builder.MoveToBookmark("InsertHere");
builder.InsertForms2OleControl("CommandButton", 100, 30);
```

### 3. Làm thế nào **đặt kích thước nút** một cách động dựa trên độ dài văn bản?

Tính chiều rộng cần thiết bằng phương thức `Graphics.MeasureString` (từ `System.Drawing`) và chuyển đổi pixel sang điểm (`points = pixels * 72 / DPI`). Sau đó truyền giá trị chiều rộng đã tính vào `InsertForms2OleControl`.

### 4. Có cách thêm nhiều nút trong một vòng lặp không?

Chắc chắn rồi. Đặt logic chèn vào một vòng `for` và điều chỉnh các thuộc tính `Left` và `Top` cho mỗi lần lặp:

```csharp
for (int i = 0; i < 3; i++)
{
    Forms2OleControl btn = builder.InsertForms2OleControl("CommandButton", 80, 25);
    btn.Name = $"btnOption{i + 1}";
    btn.Caption = $"Option {i + 1}";
    btn.Left = 50;
    btn.Top = 100 + i * 40; // stagger vertically
}
```

---

## Kết quả mong đợi

Khi bạn chạy chương trình và mở **ActiveXButton.docx**:

* Một nút **Submit** duy nhất xuất hiện gần góc trên‑trái của trang đầu.  
* Kích thước nút khớp với các kích thước bạn cung cấp (`100 pt × 30 pt`).  
* Nếu bạn đã thêm macro VBA, việc nhấn nút sẽ hiển thị hộp thoại: “You clicked the Submit button!”.

Bạn đã thành công trong việc **tạo điều khiển ActiveX**, **đặt kích thước nút**, và **thêm nút vào Word** đồng thời học được cách **chèn nút** và **tạo nút có thể nhấn** cho các tác vụ tự động trong tương lai.

---

## Kết luận

Trong tutorial này, bạn đã học cách **tạo điều khiển ActiveX** trong tài liệu Word bằng C#. Bằng cách làm theo các bước, bạn có thể **đặt kích thước nút**, đặt tên có ý nghĩa cho điều khiển, và **thêm nút vào Word** để biến nó thành một **nút có thể nhấn** được gắn với macro VBA.  

Từ đây, bạn có thể khám phá:

* Liên kết nút với một .NET COM add‑in thay vì VBA.  
* Sử dụng các lớp ActiveX khác như `CheckBox` hoặc `ComboBox`.  
* Tự động tạo các mẫu biểu mẫu đầy đủ với nhiều điều khiển.

Hãy thoải mái thử nghiệm với các kích thước khác nhau


## Bạn nên học gì tiếp theo?


Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm mã mẫu hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create Word Document with Floating Image in .NET](/words/english/net/add-content-using-document-builder/insert-floating-image/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create Accessible PDF from Word – Complete Guide](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-from-word-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}