---
category: general
date: 2026-09-21
description: Học cách tạo nút lệnh ActiveX trong tài liệu Word bằng Aspose.Words và
  C#. Hướng dẫn từng bước bao gồm việc chèn, định vị và lưu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- aspose.words activex
- c# documentbuilder
- insertforms2olecontrol
- activeX control in word
- programmatically add button
language: vi
lastmod: 2026-09-21
og_description: Tạo nút lệnh ActiveX trong tài liệu Word bằng C# và Aspose.Words.
  Thực hiện theo hướng dẫn đầy đủ này để chèn, định vị và lưu nút một cách lập trình.
og_image_alt: Screenshot showing an ActiveX command button inserted in a Word document
  using C#
og_title: Tạo nút lệnh ActiveX trong Word bằng C# – hướng dẫn đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create ActiveX command button in a Word document with
    Aspose.Words and C#. Step‑by‑step guide covers insertion, positioning, and saving.
  headline: How to create ActiveX command button in Word using C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
- DocumentBuilder
title: Cách tạo nút lệnh ActiveX trong Word bằng C#
url: /vi/net/working-with-oleobjects-and-activex/how-to-create-activex-command-button-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo nút lệnh ActiveX trong Word bằng C#

## Những gì bạn sẽ cần

* .NET 6.0 SDK hoặc phiên bản sau (code cũng hoạt động với .NET Framework 4.7+)
* Aspose.Words for .NET (gói NuGet `Aspose.Words`)
* Một IDE như Visual Studio 2022 hoặc VS Code
* Kiến thức cơ bản về C# và các khái niệm tài liệu Word

Không cần cài đặt Office bổ sung vì Aspose.Words hoạt động độc lập với Microsoft Word.

## Bước 1: Thiết lập dự án C#

Tạo một dự án console mới và thêm gói Aspose.Words.

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

Thư viện `Aspose.Words` cung cấp lớp **DocumentBuilder** mà chúng ta sẽ dùng để thao tác với tài liệu.

## Bước 2: Khởi tạo tài liệu và builder

Khối mã đầu tiên tạo một tài liệu trống và một thể hiện `DocumentBuilder`. Đối tượng này là điểm vào cho tất cả các thao tác xử lý Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// Create a new blank document.
Document doc = new Document();

// Create a builder to edit the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Tại sao điều này quan trọng:** `DocumentBuilder` duy trì vị trí con trỏ hiện tại, vì vậy bất kỳ chèn nào tiếp theo sẽ xuất hiện đúng nơi bạn đặt con trỏ.

## Bước 3: Chèn nút lệnh ActiveX

Phương thức **InsertForms2OleControl** tạo một điều khiển ActiveX theo loại yêu cầu. Ở đây chúng ta yêu cầu một `CommandButton` và chỉ định kích thước của nó bằng điểm (200 × 30 pt).

```csharp
// Insert an ActiveX CommandButton control (200 × 30 pt).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    OleControlType.CommandButton, 200, 30);
```

**Giải thích:**  
* `OleControlType.CommandButton` cho Aspose.Words biết tạo một nút thay vì loại điều khiển khác.  
* Phương thức trả về một đối tượng `Forms2OleControl`, cung cấp các trường vị trí và thuộc tính.

## Bước 4: Định vị nút và đặt các thuộc tính

Sau khi chèn, bạn có thể di chuyển nút tới bất kỳ vị trí nào trên trang và đặt cho nó một tên lập trình và chú thích hiển thị.

```csharp
// Position the button (coordinates are in points).
cmdBtn.Left = 100;          // X‑coordinate
cmdBtn.Top = 150;           // Y‑coordinate

// Set the button's programmatic name and displayed text.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

**Mẹo chuyên nghiệp:** Hệ thống tọa độ bắt đầu từ góc trên‑trái của trang. Điều chỉnh `Left` và `Top` để căn chỉnh nút với các trường biểu mẫu khác.

## Bước 5: Lưu tài liệu

Cuối cùng, ghi tài liệu ra đĩa. Tệp sẽ chứa nút ActiveX, sẵn sàng mở trong Microsoft Word nơi nút sẽ trở nên tương tác.

```csharp
// Save the document that now contains the ActiveX button.
doc.Save("ActiveXCommandButton.docx");
```

Khi bạn mở `ActiveXCommandButton.docx` trong Word, bạn sẽ thấy một nút có nhãn **Submit** ở vị trí đã chỉ định. Nhấp vào nó trong Word sẽ kích hoạt hành vi mặc định của nút (bạn có thể tùy chỉnh sau này bằng VBA hoặc add‑in Word).

## Ví dụ hoàn chỉnh, có thể chạy được

Kết hợp tất cả các phần lại với nhau tạo ra một chương trình tự chứa mà bạn có thể sao chép, dán và chạy.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX CommandButton (200 × 30 pt).
        Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
            OleControlType.CommandButton, 200, 30);

        // 3. Position and configure the button.
        cmdBtn.Left = 100;          // X‑coordinate (points)
        cmdBtn.Top = 150;           // Y‑coordinate (points)
        cmdBtn.Name = "btnSubmit";
        cmdBtn.Caption = "Submit";

        // 4. Save the document.
        doc.Save("ActiveXCommandButton.docx");

        Console.WriteLine("Document created successfully.");
    }
}
```

**Kết quả mong đợi:** Console in ra *“Document created successfully.”* và thư mục hiện chứa `ActiveXCommandButton.docx`. Mở tệp trong Microsoft Word sẽ hiển thị một nút **Submit** có thể nhấp được, được đặt cách lề trái 100 pt và cách trên trang 150 pt.

## Những lỗi thường gặp và cách tránh chúng

| Vấn đề | Tại sao xảy ra | Cách khắc phục |
|-------|----------------|----------------|
| Nút xuất hiện ngoài trang | Giá trị `Left`/`Top` vượt quá kích thước trang | Sử dụng `doc.FirstSection.PageSetup.PageWidth` và `PageHeight` để tính toán tọa độ an toàn |
| Nút không hiển thị trong Word | Tài liệu được lưu ở định dạng loại bỏ điều khiển ActiveX (ví dụ, `.txt`) | Luôn lưu dưới dạng `.docx` hoặc `.doc` |
| Lỗi runtime `ArgumentOutOfRangeException` | Chiều rộng hoặc chiều cao được đặt bằng zero hoặc âm | Đảm bảo các đối số kích thước truyền vào `InsertForms2OleControl` là số dương |

## Mở rộng giải pháp

Bạn có thể tùy chỉnh thêm nút bằng cách đặt các thuộc tính bổ sung như `Enabled`, `Visible`, hoặc gắn macro qua VBA. Lớp **Forms2OleControl** cũng cho phép chèn các điều khiển ActiveX khác như hộp kiểm (`OleControlType.CheckBox`) hoặc hộp combo (`OleControlType.ComboBox`).

Nếu bạn cần tạo nhiều nút trong một vòng lặp, hãy đóng gói logic chèn vào một phương thức trợ giúp:

```csharp
static Forms2OleControl AddCommandButton(DocumentBuilder builder,
    string name, string caption, double left, double top)
{
    var btn = builder.InsertForms2OleControl(OleControlType.CommandButton, 200, 30);
    btn.Name = name;
    btn.Caption = caption;
    btn.Left = left;
    btn.Top = top;
    return btn;
}
```

## Kết luận

Bây giờ bạn đã biết cách **tạo nút lệnh ActiveX** trong tài liệu Word bằng C# và Aspose.Words. Hướng dẫn đã đề cập đến việc thiết lập dự án, chèn nút bằng `InsertForms2OleControl`, định vị nó, và lưu tệp cuối cùng. Với nền tảng này, bạn có thể tự động hoá các biểu mẫu phức tạp, nhúng các điều khiển tương tác, và tích hợp tài liệu Word vào các giải pháp .NET lớn hơn.

Tiếp theo, khám phá các chủ đề liên quan như trường biểu mẫu **Aspose.Words ActiveX**, **C# DocumentBuilder** với phong cách nâng cao, hoặc cách thêm **điều khiển ActiveX trong Word** bằng lập trình cho hộp kiểm và danh sách thả xuống. Thử nghiệm các tọa độ và kích thước khác nhau để phù hợp với yêu cầu bố cục của bạn. Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo tài liệu Word với Aspose.Words cho .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Tạo hình chữ nhật trong Word với Aspose.Words – Hướng dẫn từng bước](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Tạo tài liệu Word có bảng bằng Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}