---
category: general
date: 2026-07-29
description: Thêm nút lệnh vào tài liệu Word bằng Aspose.Words. Tìm hiểu cách thiết
  lập các thuộc tính của điều khiển ActiveX và đặt chú thích cho nút lệnh trong vài
  bước đơn giản.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button to word document
- set activex control properties
- set command button caption
- Aspose.Words ActiveX example
- C# insert ActiveX control
language: vi
lastmod: 2026-07-29
og_description: Thêm nút lệnh vào tài liệu Word bằng Aspose.Words. Hướng dẫn này cho
  thấy cách thiết lập các thuộc tính của điều khiển ActiveX và đặt chú thích cho nút
  lệnh một cách nhanh chóng.
og_image_alt: Screenshot of a Word document with a Submit command button inserted
  via C#
og_title: Thêm nút lệnh vào tài liệu Word – Hướng dẫn từng bước Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  headline: Add Command Button to Word Document with Aspose.Words – Complete Guide
  type: TechArticle
- description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  name: Add Command Button to Word Document with Aspose.Words – Complete Guide
  steps:
  - name: Setting the Caption
    text: 'The caption is the text that appears on the button itself. To **set command
      button caption**, simply assign a string to the `Caption` property:'
  - name: Naming the Control
    text: 'Giving the control a meaningful name makes it easier to reference later
      (for example, when automating Word macros). We’ll set the `Name` property:'
  - name: Positioning on the Page
    text: 'Word uses points (1/72 of an inch) for layout. Adjust the `Left` and `Top`
      properties to place the button where you need it:'
  - name: Expected Result
    text: 1. The Word document opens with a single page. 2. A rectangular button labeled
      **Submit** appears at the coordinates you specified. 3. If you right‑click the
      button and choose **Properties**, you’ll see the name `btnSubmit` and other
      properties you set.
  - name: Inserting Other ActiveX Types
    text: 'The `InsertForms2OleControl` method isn’t limited to command buttons. You
      can embed check boxes, option buttons, or even custom ActiveX objects:'
  - name: Handling Word Versions
    text: Older Word versions (pre‑2007) use the binary `.doc` format, which stores
      ActiveX controls differently. Aspose.Words automatically converts the control
      when you save as `.doc`, but some properties (like precise positioning) may
      shift. If you target legacy formats, test the output in the specific Wor
  - name: Security Settings
    text: 'Word may disable ActiveX controls on machines with strict macro security.
      To avoid a “Security Warning” dialog, consider:'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Thêm Nút Lệnh vào Tài liệu Word bằng Aspose.Words – Hướng Dẫn Toàn Diện
url: /vi/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Thêm Nút Lệnh vào Tài liệu Word – Hướng dẫn Lập trình Toàn diện

Bạn đã bao giờ **add command button to word document** nhưng không chắc nên dùng API nào? Bạn không đơn độc; nhiều nhà phát triển gặp khó khăn khi lần đầu tiên cố gắng nhúng các điều khiển tương tác vào file DOCX. Tin tốt là Aspose.Words làm cho việc này trở nên vô cùng dễ dàng. Trong hướng dẫn này, chúng ta sẽ đi qua cách tạo một điều khiển ActiveX CommandButton, **set activex control properties**, và **set command button caption** — tất cả bằng mã C# sạch sẽ mà bạn có thể sao chép‑dán ngay lập tức.

Sau khi hoàn thành tutorial này, bạn sẽ có một file Word hoạt động đầy đủ chứa một nút “Submit” có thể nhấn được, sẵn sàng mở trong Microsoft Word. Không cần script VBA bên ngoài, không cần thao tác UI thủ công — chỉ toàn quyền kiểm soát bằng lập trình.

## Những Điều Bạn Sẽ Học

* Cách tạo một tài liệu Word trống và một `DocumentBuilder`.
* Lệnh gọi phương thức chính xác để **add command button to word document** bằng Aspose.Words.
* Cách **set activex control properties** như kích thước, vị trí và tên.
* Kỹ thuật đúng để **set command button caption** sao cho nút hiển thị đúng nội dung bạn muốn.
* Mẹo xử lý các trường hợp đặc biệt như các loại nút khác nhau, DPI scaling, và khả năng tương thích với các phiên bản Word.

> **Prerequisite:** Visual Studio (hoặc bất kỳ IDE C# nào) với Aspose.Words for .NET đã được cài đặt (gói NuGet `Aspose.Words`). Không yêu cầu kinh nghiệm trước về ActiveX.

---

## Bước 1: Thiết lập Dự án và Nhập Namespace

Trước khi chúng ta có thể **add command button to word document**, chúng ta cần một dự án C# tham chiếu tới Aspose.Words. Tạo một ứng dụng console .NET mới, sau đó thêm gói NuGet:

```bash
dotnet add package Aspose.Words
```

Bây giờ đưa các namespace cần thiết vào file nguồn của bạn:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;
```

Ba chỉ thị `using` này cho phép bạn truy cập các lớp `Document`, `DocumentBuilder`, và `Forms2OleControl` chịu trách nhiệm chèn ActiveX.

*Pro tip:* Nếu bạn đang dùng Visual Studio, IDE sẽ gợi ý tự động thêm chúng khi bạn gõ tên lớp.

---

## Bước 2: Tạo Tài liệu Trống và Builder

Một đối tượng `Document` mới đại diện cho một file Word rỗng. `DocumentBuilder` là “bút” tiện lợi cho phép chúng ta vẽ, chèn văn bản, và—quan trọng—đặt các điều khiển ActiveX.

```csharp
// Initialize a new, empty Word document.
Document doc = new Document();

// Attach a builder to the document for editing.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Tại thời điểm này, tài liệu chỉ là một canvas trắng—giống như một tờ giấy sạch đang chờ nút lệnh của bạn.

---

## Bước 3: Chèn Điều Khiển CommandButton ActiveX

Bây giờ chúng ta cuối cùng **add command button to word document**. Aspose.Words cung cấp phương thức `InsertForms2OleControl`, nhận loại điều khiển và kích thước. Chúng ta sẽ dùng `Forms2OleControlType.CommandButton` và đặt chiều rộng 150 điểm và chiều cao 30 điểm.

```csharp
// Insert a CommandButton ActiveX control with a specific size.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton,
    width: 150,
    height: 30);
```

Phương thức trả về một thể hiện `Forms2OleControl`, mà chúng ta sẽ dùng để **set activex control properties** trong bước tiếp theo.

---

## Bước 4: Cấu Hình Điều Khiển – Tên, Caption và Vị Trí

### Đặt Caption

Caption là văn bản hiển thị trên nút. Để **set command button caption**, chỉ cần gán một chuỗi cho thuộc tính `Caption`:

```csharp
commandButton.Caption = "Submit";
```

Bạn có thể thay `"Submit"` bằng bất kỳ từ nào—“Save”, “Export”, “Launch”, v.v.—và Word sẽ hiển thị đúng văn bản đó.

### Đặt Tên cho Điều Khiển

Việc đặt tên có ý nghĩa cho điều khiển giúp bạn dễ tham chiếu sau này (ví dụ, khi tự động hoá macro Word). Chúng ta sẽ thiết lập thuộc tính `Name`:

```csharp
commandButton.Name = "btnSubmit";
```

### Định Vị Trên Trang

Word sử dụng đơn vị điểm (1/72 inch) cho bố cục. Điều chỉnh các thuộc tính `Left` và `Top` để đặt nút ở vị trí mong muốn:

```csharp
commandButton.Left = 100; // 100 points from the left margin
commandButton.Top  = 200; // 200 points from the top of the page
```

Nếu bạn cần căn nút so với một đoạn văn, có thể di chuyển con trỏ của builder trước, sau đó chèn điều khiển; các tọa độ sẽ tính dựa trên vị trí đó.

*Edge case:* Trên màn hình DPI cao, kích thước hiển thị có thể hơi khác so với Word. Để giữ kích thước vật lý nhất quán trên các thiết bị, bạn có thể tính điểm dựa trên DPI mục tiêu (thông thường là 96 DPI cho Word).

---

## Bước 5: Lưu Tài liệu

Với nút đã được cấu hình hoàn chỉnh, việc lưu file chỉ cần một dòng lệnh:

```csharp
// Save the document; the ActiveX control is stored inside the DOCX.
doc.Save("CommandButton.docx");
```

File `CommandButton.docx` kết quả chứa một nút ActiveX hoạt động đầy đủ. Mở nó trong Microsoft Word, và bạn sẽ thấy nút “Submit” được đặt chính xác ở vị trí bạn chỉ định.

### Kết Quả Mong Đợi

1. Tài liệu Word mở ra với một trang duy nhất.  
2. Một nút hình chữ nhật có nhãn **Submit** xuất hiện tại tọa độ bạn đã chỉ định.  
3. Nếu bạn nhấp chuột phải vào nút và chọn **Properties**, sẽ thấy tên `btnSubmit` và các thuộc tính khác mà bạn đã thiết lập.

---

## Bước 6: Biến Thể Nâng Cao và Những Cạm Bẫy Thông Thường

### Chèn Các Loại ActiveX Khác

Phương thức `InsertForms2OleControl` không chỉ giới hạn ở command button. Bạn có thể nhúng checkbox, option button, hoặc thậm chí các đối tượng ActiveX tùy chỉnh:

```csharp
// Example: Insert a CheckBox instead of a CommandButton.
Forms2OleControl checkBox = builder.InsertForms2OleControl(
    Forms2OleControlType.CheckBox,
    width: 20,
    height: 20);
checkBox.Name = "chkAgree";
checkBox.Caption = "I Agree";
```

Mẫu **set activex control properties** vẫn áp dụng—chỉ cần thay đổi enum loại.

### Xử Lý Các Phiên Bản Word

Các phiên bản Word cũ hơn (trước‑2007) dùng định dạng nhị phân `.doc`, lưu trữ ActiveX khác nhau. Aspose.Words tự động chuyển đổi điều khiển khi bạn lưu dưới dạng `.doc`, nhưng một số thuộc tính (như vị trí chính xác) có thể bị dịch chuyển. Nếu bạn nhắm tới định dạng legacy, hãy kiểm tra kết quả trên phiên bản Word cụ thể.

### Cài Đặt Bảo Mật

Word có thể vô hiệu hoá ActiveX trên các máy có cài đặt bảo mật macro nghiêm ngặt. Để tránh hộp thoại “Security Warning”, cân nhắc:

* Ký tài liệu bằng chứng chỉ tin cậy.  
* Hướng dẫn người dùng bật nội dung ActiveX cho vị trí file đó.  
* Sử dụng giải pháp không macro (ví dụ, content controls thuần) nếu bảo mật là mối quan tâm.

---

## Bước 7: Ví Dụ Hoàn Chỉnh

Dưới đây là chương trình hoàn chỉnh, sẵn sàng chạy, bao gồm mọi bước chúng ta đã thảo luận. Sao chép vào `Program.cs` của bạn, điều chỉnh đường dẫn xuất nếu cần, và nhấn **Run**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            width: 150,   // Width in points
            height: 30);  // Height in points

        // Step 3: Set the control's name and caption.
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Step 4: Position the control on the page.
        commandButton.Left = 100; // 100 points from left edge
        commandButton.Top  = 200; // 200 points from top edge

        // Optional: Add a paragraph above the button for context.
        builder.MoveToDocumentEnd();
        builder.Writeln("Click the button below to submit the form:");

        // Step 5: Save the document.
        string outputPath = "CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved successfully to {outputPath}");
    }
}
```

**Chức năng của đoạn mã này:**

* Bắt đầu với một tài liệu mới.  
* Chèn một command button, **sets activex control properties**, và **sets command button caption**.  
* Thêm một đoạn văn giải thích ngắn gọn.  
* Lưu file dưới tên `CommandButton.docx`.

Chạy chương trình, mở file đã tạo, và bạn sẽ thấy nút nằm dưới đoạn văn giải thích.

---

## Kết Luận

Chúng ta vừa minh họa cách **add command button to word document** bằng Aspose.Words, cách **set activex control properties**, và cách **set command button caption** — tất cả trong một đoạn mã C# ngắn gọn, sẵn sàng cho môi trường production. Cách tiếp cận này có thể mở rộng: thay đổi loại điều khiển, điều chỉnh kích thước, hoặc lặp qua nguồn dữ liệu để chèn hàng chục nút một cách tự động.

Muốn tiến xa hơn? Hãy thử:

* Gắn nút với macro để thực hiện xuất dữ liệu.  
* Thêm hình ảnh hoặc biểu tượng tùy chỉnh vào nút bằng thuộc tính `Picture`.  
* Xây dựng một form đầy đủ với nhiều điều khiển ActiveX (textbox, combo box, …).

Thực hành là cách tốt nhất để thành thạo tự động hoá Word. Nếu gặp khó khăn, hãy kiểm tra lại phép tính DPI và cài đặt bảo mật của Word. Chúc bạn lập trình vui vẻ và tài liệu của bạn ngày càng tương tác hơn!

## Bạn Nên Học Gì Tiếp Theo?


Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm mã mẫu đầy đủ cùng giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}