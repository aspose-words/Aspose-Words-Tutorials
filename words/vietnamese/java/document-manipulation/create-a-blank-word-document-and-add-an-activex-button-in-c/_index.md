---
category: general
date: 2026-10-23
description: Tạo tài liệu Word trống bằng C# và học cách chèn các điều khiển ActiveX,
  bao gồm một nút, bằng Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- create activex control
- word document activex button
language: vi
lastmod: 2026-10-23
og_description: Tạo tài liệu Word trống bằng C# và học cách chèn các điều khiển ActiveX,
  bao gồm một nút, bằng Aspose.Words.
og_image_alt: Result of creating a blank Word document with an ActiveX Submit button
og_title: Tạo tài liệu Word trống và thêm nút ActiveX trong C#
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button in C#
  type: TechArticle
- description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  name: Create a blank Word document and add an ActiveX button in C#
  steps:
  - name: Instantiate a `Document`.
    text: Instantiate a `Document`.
  - name: Use `DocumentBuilder` to work with the file.
    text: Use `DocumentBuilder` to work with the file.
  - name: Call `InsertForms2OleControl` to **how to insert activex** controls.
    text: Call `InsertForms2OleControl` to **how to insert activex** controls.
  - name: Configure the control’s properties (**create activex control**).
    text: Configure the control’s properties (**create activex control**).
  - name: Save the file, yielding a **word document activex button** ready for VBA
      integration.
    text: Save the file, yielding a **word document activex button** ready for VBA
      integration.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Tạo tài liệu Word trống và thêm nút ActiveX trong C#
url: /vi/java/document-manipulation/create-a-blank-word-document-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo một tài liệu Word trống và thêm nút ActiveX trong C#

Nếu bạn cần **tạo tài liệu Word trống** một cách lập trình, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Bạn sẽ thấy một ví dụ hoàn chỉnh, có thể chạy được, tạo một tài liệu mới, chèn một ActiveX CommandButton và lưu tệp — tất cả bằng Aspose.Words cho .NET.

Làm việc với các tệp Word thường đòi hỏi nhiều hơn chỉ văn bản thuần. Thêm một **nút ActiveX** cho phép bạn nhúng chức năng tương tác có thể được sử dụng trong các mẫu hỗ trợ macro hoặc các giải pháp chỉ dành cho Windows. Khi kết thúc tutorial này, bạn sẽ có thể chèn bất kỳ điều khiển ActiveX nào, nhưng chúng tôi tập trung vào kịch bản phổ biến nhất: một **nút activex trong tài liệu Word** để gửi biểu mẫu.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* .NET 6.0 hoặc mới hơn (mã cũng hoạt động với .NET Framework 4.7+)
* Visual Studio 2022 (hoặc bất kỳ IDE C# nào)
* **Aspose.Words for .NET** NuGet package  
  ```bash
  dotnet add package Aspose.Words
  ```
* Kiến thức cơ bản về cú pháp C#

> **Mẹo chuyên nghiệp:** Aspose.Words là một thư viện thương mại, nhưng nó cung cấp giấy phép tạm thời miễn phí để thử nghiệm. Cài đặt giấy phép sớm để tránh dấu nước bản đánh giá.

## Bước 1: Tạo một tài liệu Word trống với Aspose.Words

Bước đầu tiên là khởi tạo một đối tượng `Document`. Đối tượng này đại diện cho một tệp `.docx` rỗng trong bộ nhớ.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
```

`Document` bắt đầu không có phần, trang hay nội dung nào. Đây là nền tảng sạch sẽ bạn cần cho các kịch bản **tạo tài liệu Word trống** như tạo báo cáo từ đầu.

## Bước 2: Lấy DocumentBuilder để chỉnh sửa tài liệu

`DocumentBuilder` cung cấp một API tiện lợi để thêm văn bản, hình ảnh và các điều khiển. Chúng ta sẽ dùng nó để định vị điều khiển ActiveX.

```csharp
// Obtain a DocumentBuilder tied to the blank document
DocumentBuilder builder = new DocumentBuilder(document);
```

Builder tự động thêm một phần mặc định và một trang đầu tiên, vì vậy bạn có thể bắt đầu chèn các đối tượng ngay lập tức.

## Bước 3: Cách chèn các điều khiển ActiveX vào tài liệu

Aspose.Words cung cấp `InsertForms2OleControl` để nhúng các đối tượng OLE/ActiveX. Phương thức này yêu cầu loại điều khiển, chiều rộng và chiều cao (đơn vị điểm). Dưới đây chúng ta chèn một **CommandButton** — nút biểu mẫu cổ điển mà bạn thấy trong các mẫu Word cũ.

```csharp
// Insert an ActiveX CommandButton control (100 × 30 points)
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

> **Tại sao cách này hoạt động:** `Forms2OleControlType.COMMANDBUTTON` báo cho Word tạo một nút có thể phản hồi sự kiện nhấp khi tài liệu được mở trong môi trường Windows hỗ trợ ActiveX.

## Bước 4: Tạo một điều khiển ActiveX – thiết lập các thuộc tính

Bây giờ chúng ta đặt cho nút một tên lập trình và một chú thích hiển thị. Đây là phần **tạo điều khiển activex** mà các nhà phát triển thường bỏ qua.

```csharp
// Set the button's name (used in VBA) and the text shown to users
commandButton.Name = "btnSubmit";
commandButton.Caption = "Submit";
```

* `Name` là định danh mà bạn sẽ tham chiếu từ macro VBA (`ActiveDocument.InlineShapes("btnSubmit")`).
* `Caption` là nhãn hiển thị trên nút.

## Bước 5: Lưu tài liệu Word với nút ActiveX

Cuối cùng, ghi tài liệu ra đĩa. Phần mở rộng tệp phải là `.docx` (hoặc `.docm` nếu bạn dự định thêm macro sau này). Ví dụ lưu vào một thư mục tạm — hãy thay thế bằng đường dẫn của bạn.

```csharp
// Save the document containing the ActiveX button
string outputPath = @"C:\Temp\ActiveXButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Khi bạn mở tệp kết quả trong Microsoft Word (chỉ trên Windows), bạn sẽ thấy một **nút activex trong tài liệu Word** có thể được kết nối với mã VBA.

## Ví dụ hoàn chỉnh hoạt động

Dưới đây là chương trình đầy đủ mà bạn có thể sao chép‑dán vào một dự án console mới.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a blank Word document
            Document document = new Document();

            // 2. Get a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3. Insert an ActiveX CommandButton (100 × 30 points)
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

            // 4. Configure the button
            commandButton.Name = "btnSubmit";
            commandButton.Caption = "Submit";

            // 5. Save the file
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Kết quả mong đợi khi bạn chạy chương trình**

```
Document saved to C:\Temp\ActiveXButton.docx
```

Mở file `ActiveXButton.docx` đã tạo trong Word, và bạn sẽ thấy một nút có nhãn **Submit** được đặt ở đầu trang đầu tiên.

## Các trường hợp đặc biệt và lỗi thường gặp

| Tình huống | Điều cần lưu ý | Khuyến nghị |
|-----------|-------------------|----------------|
| Chạy trên macOS hoặc Linux | ActiveX là công nghệ chỉ dành cho Windows, vì vậy nút sẽ hiển thị dưới dạng chỗ giữ chỗ. | Chỉ sử dụng tutorial này cho các mẫu nhắm tới Windows. |
| Tài liệu được mở trong Word Online | Các điều khiển ActiveX không được hỗ trợ trong chế độ xem trình duyệt. | Cung cấp giao diện dự phòng hoặc hướng người dùng mở tệp trong client desktop. |
| Cần một tệp hỗ trợ macro | Các tệp `.docx` không thể lưu mã VBA. | Lưu dưới dạng `.docm` (`document.Save("MyFile.docm", SaveFormat.Docm)`) và thêm macro riêng. |
| Kích thước điều khiển không khớp | Giá trị chiều rộng/chiều cao tính bằng điểm (1 pt ≈ 1/72 in). | Điều chỉnh các giá trị số để đạt kích thước hiển thị mong muốn. |

## Câu hỏi thường gặp

**Làm thế nào để chèn các điều khiển ActiveX khác ngoài nút?**  
Sử dụng cùng phương thức `InsertForms2OleControl` nhưng truyền một giá trị enum `Forms2OleControlType` khác, chẳng hạn `COMBOBOX` hoặc `LISTBOX`.

**Tôi có thể thay đổi phông chữ hoặc màu sắc của nút không?**  
Giao diện nút ActiveX được điều khiển bởi ứng dụng chủ (Word) và giao diện Windows nền. Bạn có thể sửa các thuộc tính như `ForeColor` và `BackColor` qua VBA sau khi tài liệu được mở.

**Có cách nào để thêm trình xử lý sự kiện click trực tiếp từ C# không?**  
Không. Sự kiện click phải được xử lý bằng VBA hoặc một add‑in Word vì nút chạy trong tiến trình của Word, không phải ứng dụng .NET của bạn.

## Kết luận

Bây giờ bạn đã biết cách **tạo tài liệu Word trống** một cách lập trình và nhúng một **nút ActiveX** bằng Aspose.Words cho .NET. Các bước đã thực hiện:

1. Khởi tạo một `Document`.
2. Sử dụng `DocumentBuilder` để làm việc với tệp.
3. Gọi `InsertForms2OleControl` để **cách chèn activex** các điều khiển.
4. Cấu hình các thuộc tính của điều khiển (**tạo điều khiển activex**).
5. Lưu tệp, tạo ra một **nút activex trong tài liệu Word** sẵn sàng cho việc tích hợp VBA.

Từ đây bạn có thể khám phá việc thêm các loại điều khiển khác, kết nối macro VBA, hoặc chuyển đổi tài liệu sang PDF trong khi giữ lại nút (dưới dạng hình ảnh tĩnh). Hãy thử nghiệm với các kích thước, chú thích và tên khác nhau.

## Bạn nên học gì tiếp theo?

Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách thêm nút ActiveX vào tài liệu Word với Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Tạo tài liệu Word với nút ActiveX – Hướng dẫn C#](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}