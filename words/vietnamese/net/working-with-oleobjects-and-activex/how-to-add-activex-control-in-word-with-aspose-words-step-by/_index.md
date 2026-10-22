---
category: general
date: 2026-08-07
description: Học cách thêm điều khiển ActiveX vào tài liệu Word bằng C#. Bao gồm việc
  liên kết macro với nút và thêm các ví dụ về nút có thể nhấp trong Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex control
- associate macro with button
- add clickable button word
- add command button word
language: vi
lastmod: 2026-08-07
og_description: Cách thêm điều khiển ActiveX vào tài liệu Word bằng Aspose.Words.
  Thực hiện theo hướng dẫn này để chèn một nút, gắn macro vào nút và thêm từ nút có
  thể nhấp được.
og_image_alt: Screenshot showing a Word document with an ActiveX command button inserted
  via Aspose.Words
og_title: cách thêm điều khiển ActiveX vào Word – hướng dẫn C# đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  headline: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  name: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  steps:
  - name: Why each line matters
    text: '| Line | Purpose | |------|---------| | `Document doc = new Document();`
      | Instantiates a fresh Word package in memory. | | `DocumentBuilder builder
      = new DocumentBuilder(doc);` | Provides a fluent API for inserting content,
      including ActiveX controls. | | `InsertForms2OleControl` | The only Aspose.'
  - name: Common pitfalls when associating a macro
    text: '* **Macro security settings** – If the document is opened on a machine
      with strict security policies, the macro may be blocked. Provide instructions
      to lower the security level or sign the macro. * **Naming conflicts** – The
      macro name must be unique within the document’s VBA project; otherwise Word'
  - name: 'Edge case: Long captions'
    text: Word truncates captions that exceed the button’s width. To avoid clipping,
      either increase the width argument in `InsertForms2OleControl` or shorten the
      text. Testing with different languages (e.g., German or Japanese) is advisable
      because character width varies.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Cách thêm điều khiển ActiveX vào Word với Aspose.Words – hướng dẫn từng bước
url: /vi/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách thêm ActiveX control trong Word với Aspose.Words

Nếu bạn cần **cách thêm điều khiển activex** vào một tệp Microsoft Word một cách lập trình, hướng dẫn này sẽ cho bạn thấy các bước chính xác bằng cách sử dụng Aspose.Words cho .NET. Bạn sẽ thấy cách chèn một nút lệnh, đặt chú thích cho nó, và **liên kết macro với nút** để điều khiển phản hồi khi người dùng nhấp vào. Khi kết thúc, bạn sẽ có một tệp `.docm` có macro cho phép chứa một nút hoạt động đầy đủ.

Thêm một nút ActiveX là yêu cầu phổ biến khi xây dựng các mẫu tương tác như đơn vay, mẫu onboarding nhân viên, hoặc báo cáo tự động. Hướng dẫn này đi qua từng dòng mã, giải thích **tại sao** mỗi bước lại quan trọng, và đề cập đến các lỗi thường gặp mà bạn có thể gặp phải.

## Yêu cầu trước

* .NET 6 (hoặc .NET Core 3.1 / .NET Framework 4.8) đã được cài đặt.  
* Giấy phép Aspose.Words for .NET hợp lệ hoặc khóa đánh giá tạm thời.  
* Visual Studio 2022 (hoặc bất kỳ IDE nào hỗ trợ C#).  
* Kiến thức cơ bản về macro Word (VBA) nếu bạn dự định viết macro mà nút sẽ kích hoạt.

> **Mẹo chuyên nghiệp:** Khi chạy mẫu, lưu kết quả vào thư mục mà bạn có quyền ghi, nếu không `doc.Save` sẽ ném ra ngoại lệ.

## Cách thêm ActiveX control trong tài liệu Word bằng Aspose.Words

Cốt lõi của giải pháp là một chương trình C# ngắn tạo một tài liệu mới, chèn một điều khiển ActiveX **CommandButton**, và lưu tệp dưới dạng tài liệu có macro (`.docm`). Mã hoàn chỉnh và sẵn sàng sao chép‑dán.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert an ActiveX CommandButton control (Forms2OleControl)
        // Parameters: control type, left, top, width, height (in points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            0,   // left position (points)
            0,   // top position (points)
            150, // width (points)
            30   // height (points)
        );

        // Step 3: Set the button's visible caption – this is the add clickable button word
        commandButton.Caption = "Click Me";

        // Step 4 (optional): Associate a macro with the button's click action
        // This demonstrates how to associate macro with button
        commandButton.OnAction = "MyMacro";

        // Step 5: Save the document as a macro‑enabled file to preserve the button reference
        // The file extension .docm tells Word to keep ActiveX controls and macros
        doc.Save("CommandButton.docm");
    }
}
```

### Tại sao mỗi dòng lại quan trọng

| Dòng | Mục đích |
|------|----------|
| `Document doc = new Document();` | Khởi tạo một gói Word mới trong bộ nhớ. |
| `DocumentBuilder builder = new DocumentBuilder(doc);` | Cung cấp API dạng fluent để chèn nội dung, bao gồm các điều khiển ActiveX. |
| `InsertForms2OleControl` | Phương thức duy nhất của Aspose.Words tạo điều khiển ActiveX; bạn chỉ định loại điều khiển (`CommandButton`) và hình học của nó. |
| `commandButton.Caption = "Click Me";` | Đặt **thêm từ nút có thể nhấp** mà người dùng cuối nhìn thấy. Nếu không có chú thích, nút sẽ trống. |
| `commandButton.OnAction = "MyMacro";` | **liên kết macro với nút** – cho Word biết macro VBA nào sẽ chạy khi điều khiển được nhấp. |
| `doc.Save("CommandButton.docm");` | Lưu tài liệu dưới dạng tệp macro‑enabled; một tệp `.docx` thông thường sẽ loại bỏ điều khiển và macro. |

> **Ghi chú:** Các tọa độ (trái, trên) được đo bằng điểm (1 pt ≈ 1/72 in). Điều chỉnh chúng để đặt nút ở vị trí mong muốn trên trang.

## Cách liên kết macro với nút

Thuộc tính `OnAction` liên kết nút với macro VBA có tên `MyMacro`. Bạn vẫn cần tạo macro đó trong tệp Word, hoặc bằng cách thủ công hoặc bằng cách tiêm mã VBA một cách lập trình (Aspose.Words không ghi mã VBA). Dưới đây là một macro tối thiểu bạn có thể thêm bằng trình soạn thảo **Developer → Visual Basic** của Word:

```vba
Sub MyMacro()
    MsgBox "Button clicked!", vbInformation, "ActiveX Demo"
End Sub
```

Khi người dùng mở `CommandButton.docm` và nhấp vào nút, Word sẽ thực thi `MyMacro` và hiển thị một hộp thông báo. Nếu bảo mật macro được đặt thành **Disable all macros without notification**, nút sẽ hiển thị bị vô hiệu hoá. Hướng dẫn người dùng bật macro cho tài liệu hoặc ký macro bằng chứng chỉ tin cậy.

### Các lỗi thường gặp khi liên kết macro

* **Macro security settings** – Nếu tài liệu được mở trên máy có chính sách bảo mật nghiêm ngặt, macro có thể bị chặn. Cung cấp hướng dẫn hạ mức bảo mật hoặc ký macro.  
* **Naming conflicts** – Tên macro phải là duy nhất trong dự án VBA của tài liệu; nếu không Word sẽ báo lỗi “duplicate procedure name”.  
* **64‑bit vs 32‑bit Word** – Các điều khiển ActiveX hoạt động tương tự, nhưng trình soạn thảo VBA có thể hiển thị các cảnh báo khác nhau tùy phiên bản Office.

## Cách thêm từ nút có thể nhấp vào mẫu Word

Thuộc tính `Caption` là nội dung người dùng nhìn thấy trên nút. Bạn có thể tùy chỉnh thêm:

```csharp
commandButton.Caption = "Submit Form";
commandButton.Font.Size = 10;      // Adjust font size
commandButton.Font.Name = "Arial"; // Choose a readable font
```

Nếu bạn cần caption thay đổi động dựa trên đầu vào của người dùng, sau này bạn có thể truy cập điều khiển qua mô hình đối tượng của Word:

```vba
Sub UpdateButtonCaption()
    Dim btn As InlineShape
    Set btn = ActiveDocument.InlineShapes(1).OLEFormat.Object
    btn.Caption = "Updated Text"
End Sub
```

### Trường hợp đặc biệt: Caption dài

Word sẽ cắt ngắn caption vượt quá chiều rộng của nút. Để tránh cắt, hoặc tăng giá trị chiều rộng trong `InsertForms2OleControl` hoặc rút ngắn văn bản. Nên thử nghiệm với các ngôn ngữ khác nhau (ví dụ: tiếng Đức hoặc tiếng Nhật) vì độ rộng ký tự khác nhau.

## Cách thêm từ nút lệnh cho tự động hoá biểu mẫu

Ngoài caption hiển thị, khái niệm **thêm từ nút lệnh** đề cập đến tên lập trình của điều khiển. Aspose.Words không cung cấp thuộc tính `Name` trực tiếp cho các điều khiển ActiveX, nhưng bạn có thể đặt trường `AltText`, mà Word coi là định danh của điều khiển:

```csharp
commandButton.AltText = "SubmitButton";
```

Sau này trong VBA bạn có thể tham chiếu nút bằng giá trị `AltText` của nó:

```vba
Sub FindButton()
    Dim shp As Shape
    For Each shp In ActiveDocument.Shapes
        If shp.AlternativeText = "SubmitButton" Then
            MsgBox "Found the Submit button!"
        End If
    Next shp
End Sub
```

Kỹ thuật này hữu ích khi bạn có nhiều nút và cần phân biệt chúng một cách lập trình.

## Ví dụ hoàn chỉnh hoạt động

Dưới đây là chương trình đầy đủ mà bạn có thể biên dịch và chạy như một ứng dụng console. Nó bao gồm kiểu dáng tùy chọn, liên kết macro, và một khối chú thích mô tả từng bước.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class AddActiveXButton
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert an ActiveX CommandButton.
        //    left=50pt, top=100pt places the button away from the margin.
        Forms2OleControl btn = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            50,   // left
            100,  // top
            200,  // width
            40    // height
        );

        // 3️⃣ Add clickable button word (caption) and style it.
        btn.Caption = "Submit Form";
        btn.Font.Size = 11;
        btn.Font.Name = "Calibri";

        // 4️⃣ Associate macro with button – this is how to associate macro with button.
        btn.OnAction = "SubmitMacro";

        // 5️⃣ Give the control a friendly identifier (add command button word).
        btn.AltText = "SubmitButton";

        // 6️⃣ Save as macro‑enabled document.
        doc.Save("SubmitForm.docm");
    }
}
```

**Kết quả mong đợi:** Mở `SubmitForm.docm` trong Microsoft Word sẽ hiển thị một nút viền xanh có nhãn *Submit Form*. Nhấp vào nút sẽ kích hoạt macro VBA `SubmitMacro` (giả sử bạn đã thêm macro vào tài liệu). Nút có thể được di chuyển, thay đổi kích thước, hoặc định dạng thêm bằng cùng một đối tượng `Forms2OleControl`.

## Kiểm tra giải pháp

1. Xây dựng và chạy ứng dụng console C#.  
2. Mở tệp `SubmitForm.docm` được tạo trong Word.  
3. Nếu được yêu cầu, bật macro.  
4. Nhấp vào nút *Submit Form* – bạn sẽ thấy hộp thông báo được định nghĩa trong `SubmitMacro`.

Nếu nút xuất hiện nhưng không thực hiện gì, hãy kiểm tra lại tên macro có khớp chính xác (`SubmitMacro`) và bảo mật macro không đang chặn thực thi.

## Câu hỏi thường gặp

| Câu hỏi | Trả lời |
|----------|--------|
| *Tôi có thể thêm hơn một nút ActiveX không?* | Có. Gọi `InsertForms2OleControl` nhiều lần với các tọa độ khác nhau. Sử dụng các giá trị `OnAction` và `AltText` riêng biệt để phân biệt chúng. |
| *Điều khiển ActiveX có hiển thị trong Word Online không?* | Không. |

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, mở rộng các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Thêm nội dung bằng Document Builder trong Aspose.Words cho .NET](/words/english/net/add-content-using-document-builder/)
- [Hướng dẫn Shadow cho Shape trong Aspose.Words – Thêm bóng cho Shape trong Word bằng C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Thêm một Section mới vào tài liệu Word | Aspose.Words cho .NET](/words/english/net/document-sections/add-section/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}