---
category: general
date: 2026-08-17
description: Chèn ví dụ OleControlType.CommandButton trong Word bằng Aspose.Words.
  Tìm hiểu cách thêm các điều khiển biểu mẫu vào tài liệu Word một cách lập trình.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert olecontroltype.commandbutton example
- how to add form controls to word document
- Aspose.Words ActiveX button
- C# Word automation
- programmatic form controls
language: vi
lastmod: 2026-08-17
og_description: Chèn ví dụ OleControlType.CommandButton vào Word bằng Aspose.Words.
  Hãy làm theo hướng dẫn này để thêm các điều khiển biểu mẫu vào tài liệu Word.
og_image_alt: Screenshot showing an ActiveX CommandButton inserted into a Word document
  using Aspose.Words
og_title: Chèn ví dụ OleControlType.CommandButton trong Word
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: Insert OleControlType.CommandButton example in Word using Aspose.Words.
    Learn how to add form controls to a Word document programmatically.
  headline: Insert OleControlType.CommandButton example in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Chèn ví dụ OleControlType.CommandButton vào Word
url: /vi/net/working-with-oleobjects-and-activex/insert-olecontroltype-commandbutton-example-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Chèn ví dụ OleControlType.CommandButton trong Word

Nếu bạn cần **ví dụ chèn OleControlType.CommandButton** vào một tệp Word, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Bạn sẽ học **cách thêm các điều khiển biểu mẫu vào tài liệu Word** bằng Aspose.Words, với một chương trình C# đầy đủ, có thể chạy được.

Các điều khiển biểu mẫu như nút ActiveX cho phép bạn tạo các mẫu Word tương tác—hữu ích cho hợp đồng, bảng câu hỏi hoặc công cụ nội bộ. Các bước dưới đây bao gồm mọi thứ từ thiết lập dự án đến việc xác minh nút hiển thị đúng trong tệp `.docx` đã lưu.

## Yêu cầu trước

- .NET 6.0 SDK hoặc phiên bản mới hơn đã được cài đặt  
- Visual Studio 2022 (hoặc bất kỳ IDE C# nào)  
- Giấy phép Aspose.Words cho .NET hoặc giấy phép tạm thời miễn phí  
- Kiến thức cơ bản về C# và các khái niệm tệp Word  

> **Mẹo chuyên nghiệp:** Nếu bạn đang sử dụng bản dùng thử miễn phí, đặt tệp giấy phép trong cùng thư mục với tệp thực thi và tải nó ở đầu hàm `Main`.

## Bước 1: Tạo dự án console mới và thêm Aspose.Words

Mở terminal và chạy:

```bash
dotnet new console -n OleCommandButtonDemo
cd OleCommandButtonDemo
dotnet add package Aspose.Words
```

Điều này tạo một dự án sạch sẽ và tải về gói Aspose.Words mới nhất, cung cấp các API `Document`, `DocumentBuilder` và `InsertForms2OleControl` cần thiết cho **ví dụ chèn OleControlType.CommandButton**.

## Bước 2: Viết chương trình đầy đủ

Tạo hoặc thay thế `Program.cs` bằng đoạn mã sau. Nó chứa tất cả các chỉ thị `using` cần thiết, việc tải giấy phép, và quy trình bốn bước được hiển thị trong đoạn mã gốc.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;          // For OleControlType

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Optional: load a trial or commercial license.
        // -------------------------------------------------
        // var license = new Aspose.Words.License();
        // license.SetLicense("Aspose.Words.lic");

        // -------------------------------------------------
        // Step 1: Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // Step 2: Initialize a DocumentBuilder to work with the document
        // -------------------------------------------------
        DocumentBuilder builder = new DocumentBuilder(doc);

        // -------------------------------------------------
        // Step 3: Insert an ActiveX CommandButton control
        // -------------------------------------------------
        // OleControlType.CommandButton creates a CommandButton.
        // "ClickMe" is the control's name.
        // The Rectangle defines the button's position (x, y) and size (width, height).
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "ClickMe",
            new Rectangle(100, 100, 80, 30));

        // -------------------------------------------------
        // Step 4: Save the document containing the ActiveX button
        // -------------------------------------------------
        string outputPath = "ActiveXButton.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Tại sao mỗi dòng lại quan trọng

* **License loading** – đảm bảo bạn không bị giới hạn bởi các hạn chế đánh giá.  
* **`Document doc = new Document();`** – tạo container cho toàn bộ nội dung Word; đây là nền tảng của **ví dụ chèn OleControlType.CommandButton**.  
* **`DocumentBuilder builder = new DocumentBuilder(doc);`** – cung cấp một API linh hoạt để thêm văn bản, hình ảnh và các điều khiển.  
* **`InsertForms2OleControl`** – phương thức cốt lõi thực hiện **cách thêm các điều khiển biểu mẫu vào tài liệu Word**. Giá trị enum `OleControlType.CommandButton` chỉ cho Aspose.Words tạo một nút ActiveX.  
* **`new Rectangle(100, 100, 80, 30)`** – đặt vị trí nút cách lề trái và trên 100 pts, với chiều rộng 80 pts và chiều cao 30 pts. Điều chỉnh các số này để phù hợp với bố cục của bạn.  
* **`doc.Save`** – ghi tệp .docx ra đĩa; tệp hiện chứa nút được nhúng.

## Bước 3: Xây dựng và chạy chương trình

Từ thư mục dự án, thực thi:

```bash
dotnet run
```

Bạn sẽ thấy thông báo trên console:

```
Document saved to ActiveXButton.docx
```

Mở `ActiveXButton.docx` trong Microsoft Word. Bạn sẽ thấy một nút có nhãn **ClickMe** được đặt gần giữa trang. Nhấp vào nút sẽ kích hoạt hành vi mặc định của ActiveX (thường là không làm gì trừ khi bạn gắn macro).

![ví dụ chèn olecontroltype.commandbutton](/images/activex-button.png "ActiveX CommandButton được chèn vào tài liệu Word")

**Văn bản thay thế hình ảnh:** ví dụ chèn olecontroltype.commandbutton – một nút ActiveX CommandButton hiển thị trong tài liệu Word.

## Bước 4: Tùy chỉnh nút (tùy chọn)

Ví dụ **chèn OleControlType.CommandButton** cơ bản tạo một nút mặc định. Bạn có thể sửa đổi chú thích, phông chữ, hoặc thậm chí gắn macro bằng cách chỉnh sửa đối tượng OLE bên dưới. Dưới đây là cách ngắn gọn để thay đổi chú thích của nút sau khi chèn:

```csharp
// Retrieve the first shape (our button) from the document
Shape buttonShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

// Access the OLE format and set the caption
buttonShape.OleFormat.GetControl().SetProperty("Caption", "Submit");
```

> **Lưu ý:** Việc thao tác trực tiếp các thuộc tính OLE yêu cầu hiểu biết về giao diện COM bên dưới. Trong hầu hết các trường hợp, chú thích mặc định là đủ.

## Bước 5: Những vấn đề thường gặp và cách tránh chúng

| Vấn đề | Nguyên nhân | Cách khắc phục |
|-------|-------------|----------------|
| Nút không hiển thị trong Word | Tài liệu được lưu dưới dạng `.docx` nhưng được mở bằng trình xem loại bỏ các điều khiển OLE (ví dụ: Google Docs). | Mở tệp trong Microsoft Word hoặc Word Online với quyền chỉnh sửa. |
| Lỗi runtime `ArgumentOutOfRangeException` | Các tọa độ `Rectangle` nằm ngoài lề trang. | Sử dụng các giá trị nằm trong kích thước trang (ví dụ: 0‑500 cho A4). |
| Ngoại lệ giấy phép | Giấy phép dùng thử hết hạn sau 30 ngày. | Tải tệp giấy phép hợp lệ hoặc yêu cầu dùng thử kéo dài từ Aspose. |

## Bước 6: Cách ví dụ này phù hợp với các dự án tự động hoá lớn hơn

Khi bạn cần **cách thêm các điều khiển biểu mẫu vào tài liệu Word** ở quy mô lớn—ví dụ tạo hàng trăm mẫu hợp đồng—hãy đóng gói logic chèn vào một phương thức có thể tái sử dụng:

```csharp
static void AddCommandButton(DocumentBuilder builder, string name, Rectangle bounds)
{
    builder.InsertForms2OleControl(OleControlType.CommandButton, name, bounds);
}
```

Bạn có thể gọi `AddCommandButton` trong các vòng lặp xử lý các dòng dữ liệu, đảm bảo mỗi tài liệu được tạo ra chứa một nút có tên duy nhất (ví dụ: `Approve_001`, `Approve_002`).

## Kết luận

Bây giờ bạn đã có một **ví dụ chèn OleControlType.CommandButton** hoàn chỉnh, minh họa **cách thêm các điều khiển biểu mẫu vào tài liệu Word** bằng Aspose.Words cho .NET. Hướng dẫn đã bao gồm thiết lập dự án, mã nguồn đầy đủ, các mẹo tùy chỉnh và các bước khắc phục sự cố thường gặp.

Bạn có thể khám phá thêm:

- Thêm các loại điều khiển khác như **CheckBox** hoặc **ComboBox** (`OleControlType.CheckBox`, `OleControlType.ComboBox`).  
- Liên kết nút với macro VBA để tăng tính tương tác.  
- Tạo PDF từ cùng tài liệu trong khi giữ nguyên các trường biểu mẫu.

Thử nghiệm với các kích thước, vị trí và tên điều khiển khác nhau để phù hợp với trường hợp sử dụng cụ thể của bạn. Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với các giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Chèn trường Combo Box vào tài liệu Word](/words/english/net/add-content-using-documentbuilder/insert-combo-box-form-field/)
- [Chèn trường Check Box vào tài liệu Word](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)
- [Chèn trường nhập văn bản vào tài liệu Word](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}