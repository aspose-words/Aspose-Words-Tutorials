---
category: general
date: 2026-10-26
description: Tìm hiểu cách tạo tài liệu Word bằng C# và thêm nút ActiveX một cách
  lập trình. Hướng dẫn chi tiết này bao gồm việc chèn nút lệnh, ẩn nó trong thời gian
  thiết kế và lưu tệp.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to add activex button
- create command button word
- programmatically add command button
language: vi
lastmod: 2026-10-26
og_description: Tạo tài liệu Word bằng C# và thêm một nút ActiveX một cách lập trình.
  Tham khảo hướng dẫn đầy đủ này để nhúng một nút lệnh chỉ xuất hiện khi chạy.
og_image_alt: Screenshot of a Word document created with C# that contains an ActiveX
  command button
og_title: Tạo tài liệu Word bằng C# với nút lệnh ActiveX – hướng dẫn đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document C# and add an ActiveX button programmatically.
    This step‑by‑step guide covers inserting a command button, hiding it at design
    time, and saving the file.
  headline: How to create Word document C# with an ActiveX command button
  type: TechArticle
tags:
- C#
- Aspose.Words
- ActiveX
- Word automation
title: Cách tạo tài liệu Word bằng C# với nút lệnh ActiveX
url: /vi/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo tài liệu Word C# với nút lệnh ActiveX

Nếu bạn cần **tạo tài liệu Word C#** có chứa một nút tương tác, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Sau hai câu đầu tiên, bạn sẽ nắm được cách tiếp cận tổng thể, và các bước tiếp theo sẽ hướng dẫn chi tiết từng dòng mã bạn phải viết.

Bạn sẽ học cách thêm nút ActiveX, ẩn nó trong quá trình thiết kế, và chỉ hiển thị khi người dùng mở tệp. Bài học cũng đề cập đến các vấn đề thường gặp như cảnh báo bảo mật và tương thích phiên bản, giúp bạn phát hành các tài liệu đáng tin cậy.

## Yêu cầu trước

Trước khi bắt đầu, hãy đảm bảo bạn có:

* .NET 6.0 hoặc phiên bản mới hơn đã được cài đặt  
* Bản sao có giấy phép của **Aspose.Words for .NET** (bản dùng thử miễn phí đủ cho việc thử nghiệm)  
* Kiến thức cơ bản về C# và Visual Studio (bất kỳ IDE nào hỗ trợ .NET đều được)  

Không cần thêm bất kỳ gói NuGet nào ngoài `Aspose.Words`.

## Bước 1: Tạo tài liệu Word C# và khởi tạo DocumentBuilder

Bước đầu tiên là tạo một đối tượng `Document` và một `DocumentBuilder`. `Document` đại diện cho toàn bộ tệp .docx, trong khi `DocumentBuilder` cung cấp các phương thức fluent để thêm nội dung.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document document = new Document();

        // Attach a builder to the document so we can insert nodes.
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Tại sao điều này quan trọng:** Nếu không có `DocumentBuilder` bạn sẽ phải thao tác trực tiếp với DOM OpenXML, điều này dễ gây lỗi và khó đọc. Builder ẩn đi những chi tiết đó và đảm bảo tạo ra một tệp Word hợp lệ.

## Bước 2: Cách thêm nút ActiveX – chèn điều khiển CommandButton

Bây giờ chúng ta chèn một **điều khiển CommandButton ActiveX** vào vị trí cụ thể. Hình chữ nhật xác định vị trí (X, Y) và kích thước (rộng, cao) của nút tính bằng điểm.

```csharp
        // Define the button's position and size.
        RectangleF buttonRect = new RectangleF(100, 100, 120, 30);

        // Insert the ActiveX CommandButton control.
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,   // Type of ActiveX control
            buttonRect,                          // Geometry
            "ClickMe");                          // Caption shown at design time
```

**Tại sao điều này quan trọng:** `InsertForms2OleControl` là phương thức duy nhất của Aspose.Words tạo ra một đối tượng OLE ActiveX thực sự. Giá trị enum `Forms2OleControlType.CommandButton` báo cho Word nhúng một nút có thể nhấn thay vì một container OLE chung.

## Bước 3: Thêm nút lệnh bằng mã – ẩn nó cho đến thời gian chạy

Word mặc định hiển thị mọi hình dạng được chèn. Để giữ nút ẩn trong khi bạn thiết kế mẫu, hãy đặt thuộc tính `Hidden` trên hình dạng mà builder vừa tạo.

```csharp
        // Retrieve the shape that represents the newly added control.
        Shape oleShape = (Shape)builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)[0];

        // Hide the shape; it will become visible when the document is opened.
        oleShape.Hidden = true;
```

**Tại sao điều này quan trọng:** Đặt `Hidden = true` ngăn nút làm lộn xộn giao diện thiết kế. Khi tài liệu được mở trong Word, môi trường thời gian chạy sẽ tự động hiển thị điều khiển, duy trì trải nghiệm người dùng như mong muốn.

## Bước 4: Lưu tệp – tạo tài liệu Word có nút lệnh

Cuối cùng, ghi tài liệu ra đĩa. Chọn một đường dẫn mà ứng dụng của bạn có quyền ghi, và sử dụng phần mở rộng `.docx` để đảm bảo tính tương thích hiện đại.

```csharp
        // Save the document containing the ActiveX button.
        document.Save(@"C:\Temp\ActiveXButton.docx");
    }
}
```

**Tại sao điều này quan trọng:** Lưu dưới dạng `.docx` đảm bảo rằng điều khiển ActiveX được nhúng tuân thủ tiêu chuẩn Office Open XML, được hỗ trợ bởi Word 2007 trở lên. Nếu bạn cần hỗ trợ định dạng cũ `.doc`, hãy thay đổi phần mở rộng và dùng `SaveFormat.Doc`.

## Ví dụ hoàn chỉnh

Kết hợp tất cả lại, dưới đây là chương trình đầy đủ mà bạn có thể sao chép, dán và chạy:

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Step 1: Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control.
        RectangleF commandButtonRect = new RectangleF(100, 100, 120, 30);
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            commandButtonRect,
            "ClickMe");

        // Step 3: Hide the control so it appears only at runtime.
        Shape oleShape = (Shape)builder.CurrentParagraph
                                         .GetChildNodes(NodeType.Shape, true)[0];
        oleShape.Hidden = true;

        // Step 4: Save the document containing the ActiveX control.
        document.Save(@"C:\Temp\ActiveX.docx");
    }
}
```

**Kết quả mong đợi:** Sau khi chạy chương trình, mở `C:\Temp\ActiveX.docx` trong Microsoft Word. Bạn sẽ thấy một tài liệu trống; nút không hiển thị ở chế độ thiết kế. Nhấn **Alt + F9** để chuyển đổi mã trường, sau đó nhấp vào khu vực nút—Word sẽ hiển thị điều khiển ActiveX và bạn có thể tương tác với nó (ví dụ: nhấp đúp để xem thuộc tính).

## Các trường hợp đặc biệt và mẹo thực hành tốt

| Tình huống | Điều cần chú ý | Giải pháp đề xuất |
|-----------|-------------------|-----------------|
| **Người dùng tắt ActiveX** | Word có thể hiển thị cảnh báo bảo mật hoặc chặn điều khiển. | Hướng dẫn người dùng bật “ActiveX controls” trong Trust Center, hoặc cung cấp giải pháp thay thế đã ký macro. |
| **Tài liệu mở trong Word Online** | Word Online không hỗ trợ ActiveX; nút sẽ bị bỏ qua. | Sử dụng siêu liên kết dự phòng hoặc content control nếu cần tương thích đám mây. |
| **Cài đặt DPI khác nhau** | Kích thước hình chữ nhật có thể lớn hơn hoặc nhỏ hơn trên màn hình DPI cao. | Sử dụng `GraphicsUnit.Point` (mặc định) và kiểm tra trên các cài đặt DPI phổ biến (96 dpi, 120 dpi). |
| **Nhiều nút** | Lệnh `GetChildNodes(NodeType.Shape, true)[0]` chỉ lấy hình dạng đầu tiên. | Duyệt qua `builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)` và đặt `Hidden` cho mỗi hình dạng bạn thêm. |
| **Định dạng .doc cũ** | Một số thuộc tính ActiveX bị mất khi lưu dưới dạng `.doc`. | Ưu tiên `.docx` trừ khi bạn có yêu cầu nghiêm ngặt về định dạng cũ. |

**Mẹo chuyên nghiệp:** Sau khi chèn nút, bạn có thể gán macro cho thuộc tính `OnAction` của nó qua giao diện Word. Điều này cho phép bạn định nghĩa hành vi khi nhấn mà không cần viết thêm mã C#.

## Câu hỏi thường gặp

* **Điều này có hoạt động với .NET Core không?**  
  Có. Aspose.Words for .NET hoàn toàn tương thích với .NET 5, .NET 6 và các phiên bản sau. Chỉ cần tham chiếu cùng một gói NuGet.

* **Tôi có thể thay đổi chú thích của nút sau khi tài liệu được tạo không?**  
  Chú thích được đặt trong `InsertForms2OleControl` sẽ là văn bản mặc định ở thời gian thiết kế. Người dùng có thể chỉnh sửa nó trong Word, hoặc bạn cũng có thể cập nhật chú thích bằng cách truy cập thuộc tính của đối tượng OLE qua API `Shape.OleFormat`.

* **Nếu tôi cần kích thước nút khác thì sao?**  
  Điều chỉnh các giá trị của `RectangleF`. Hai tham số đầu là tọa độ X và Y; hai tham số cuối là chiều rộng và chiều cao tính bằng điểm (1 pt = 1/72 inch).

## Kết luận

Bây giờ bạn đã biết cách **tạo tài liệu Word C#** và **thêm nút lệnh một cách lập trình** bằng Aspose.Words. Bài hướng dẫn đã bao gồm việc khởi tạo tài liệu, chèn nút ActiveX, ẩn nó cho đến thời gian chạy, và lưu tệp cuối cùng. Với những khối xây dựng này, bạn có thể nhúng các điều khiển tương tác vào bất kỳ mẫu Word nào bạn tạo.

Tiếp theo, hãy khám phá các chủ đề liên quan như **cách xử lý sự kiện nút ActiveX**, **tạo kiểu nút lệnh Word** bằng VBA, và **thêm nút lệnh một cách lập trình** vào tài liệu hiện có. Mở rộng mẫu này sang checkbox, combo box, hoặc đối tượng OLE tùy chỉnh cũng thực hiện theo các bước tương tự—chỉ cần thay đổi giá trị enum `Forms2OleControlType`.

Bắt đầu thử nghiệm: thay đổi chú thích, điều chỉnh vị trí, hoặc nối nhiều điều khiển lại với nhau. Bạn càng thực hành, bạn sẽ càng thành thạo trong việc cung cấp các tài liệu Word phong phú, tương tác từ C#. Chúc bạn lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích chi tiết từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [How to add a command button programmatically in a Word document](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [How to add ActiveX button in a Word document with Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Create Word Document with ActiveX Button – C# Guide](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}