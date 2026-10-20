---
category: general
date: 2026-09-05
description: Tìm hiểu cách tạo nhóm hình dạng trong docx, chèn nút lệnh ActiveX và
  tải Markdown vào tài liệu Word với một ví dụ C# đầy đủ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create group shape docx
- insert activex command button
- load markdown into word document
language: vi
lastmod: 2026-09-05
og_description: Tạo nhóm hình dạng docx, chèn nút lệnh ActiveX và tải Markdown vào
  tài liệu Word bằng C#. Thực hiện theo hướng dẫn từng bước này.
og_image_alt: Screenshot of a Word document showing a grouped shape and an ActiveX
  button
og_title: Tạo nhóm hình dạng trong docx và nhúng điều khiển ActiveX – Hướng dẫn C#
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create group shape docx, insert ActiveX command button,
    and load Markdown into a Word document with a complete C# example.
  headline: How to create group shape docx and add interactive controls in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document automation
title: Cách tạo nhóm hình dạng docx và thêm các điều khiển tương tác trong C#
url: /vi/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo group shape docx và thêm các điều khiển tương tác trong C#

Nếu bạn cần **create group shape docx** file một cách lập trình, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Bạn cũng sẽ thấy cách **insert ActiveX command button** và **load Markdown into a Word document** mà không mất định dạng gạch chân. Khi kết thúc tutorial, bạn sẽ có một file `.docx` hoạt động đầy đủ, kết hợp đồ họa vector, các yếu tố UI tương tác và nội dung dựa trên markdown.

Tutorial này giả định bạn đã có môi trường phát triển C# cơ bản và đã cài đặt thư viện Aspose.Words cho .NET. Không cần công cụ bên ngoài — mọi thứ chạy trong một ứng dụng console hoặc desktop .NET tiêu chuẩn.

## Yêu cầu trước

- .NET 6.0 SDK hoặc phiên bản mới hơn (mã cũng hoạt động với .NET Framework 4.7+)
- Aspose.Words cho .NET (gói NuGet `Aspose.Words`)
- Chứng chỉ X.509 hợp lệ (`.pfx`) nếu bạn muốn thử bước ký
- Tệp hình ảnh (ví dụ, `logo.png`) và tệp markdown (`sample.md`) đặt trong một thư mục đã biết

> **Mẹo:** Giữ tất cả các tệp đầu vào trong một thư mục *resources* duy nhất để đơn giản hoá các đường dẫn tương đối.

## Bước 1: Thiết lập dự án và nhập các namespace

Tạo một dự án console mới và thêm các chỉ thị `using` cần thiết. Khối này cũng minh họa cách tham chiếu các lớp Aspose.Words mà bạn sẽ sử dụng sau.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving;
using Aspose.Words.Saving.XpsSaveOptions; // only needed for signing example
using Aspose.Words.Saving.Signature;

// Ensure the license is applied if you have one
// Aspose.Words.License license = new Aspose.Words.License();
// license.SetLicense("Aspose.Words.lic");
```

Các câu lệnh `using` cho phép bạn truy cập trực tiếp tới `Document`, `DocumentBuilder`, `GroupShape`, `Forms2OleControl`, và các kiểu khác được sử dụng trong suốt tutorial.

## Bước 2: **Create group shape docx** – thêm một shape nhóm với các phần tử con

Một *group shape* cho phép bạn xử lý nhiều đối tượng vẽ như một đơn vị duy nhất. Điều này hữu ích khi di chuyển hoặc thay đổi kích thước các đồ họa liên quan cùng nhau.

```csharp
// Initialize a new empty document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a group shape container
GroupShape group = builder.InsertGroupShape();

// Add a rectangle (100 × 50 points) as the first child
Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
group.AppendChild(rect);

// Add an ellipse (80 × 40 points) as the second child
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
group.AppendChild(ellipse);

// Optional: set a fill color for visual distinction
rect.FillColor = System.Drawing.Color.LightBlue;
ellipse.FillColor = System.Drawing.Color.LightCoral;

// Save the intermediate document so you can inspect the group
document.Save("Output/GroupShape.docx");
```

**Tại sao lại dùng group shape?**  
Việc nhóm giữ cho hình chữ nhật và hình ellipse căn chỉnh khi người dùng kéo chúng trong Word. Nó cũng đơn giản hoá các thao tác sau này như áp dụng viền chung hoặc di chuyển toàn bộ đồ họa bằng mã.

## Bước 3: Chèn một content control dạng plain‑text (placeholder cho người dùng nhập liệu)

Content control cung cấp cho người dùng cuối một khu vực có cấu trúc để nhập văn bản. Văn bản placeholder sẽ biến mất khi người dùng bắt đầu gõ.

```csharp
// Insert a plain‑text StructuredDocumentTag (SDT) after the group shape
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Set a friendly placeholder that appears in the UI
sdt.PlaceholderName = "Enter text here";

// Optionally, lock the content control to prevent deletion
sdt.LockContents = false;
sdt.LockContentControl = false;
```

Thuộc tính `PlaceholderName` là những gì Word hiển thị dưới dạng gợi ý màu xám nhạt. Người dùng có thể thay thế bằng văn bản của mình, và XML nền vẫn giữ cấu trúc hợp lệ.

## Bước 4: **Insert ActiveX command button** – thêm UI tương tác vào tài liệu

Các điều khiển ActiveX vẫn được hỗ trợ trong các file Word hiện đại và có thể kích hoạt macro hoặc tự động hoá bên ngoài. Dưới đây chúng ta sẽ thêm một *command button* và đặt tiêu đề cho nó.

```csharp
// Insert an ActiveX Forms2OleControl at the current cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl();

// Define the control type as a command button
commandBtn.ControlType = Forms2OleControl.ControlType.CommandButton;

// Set the visible caption
commandBtn.Caption = "Click Me";

// Position the button relative to the page (optional)
commandBtn.Left = 150;   // points from the left margin
commandBtn.Top = 300;    // points from the top margin
```

**Khi nào nên dùng nút ActiveX?**  
Nếu bạn phân phối tài liệu trong môi trường doanh nghiệp dựa vào macro VBA, nút ActiveX có thể khởi chạy một macro hoặc một ứng dụng bên ngoài. Đối với tương tác thuần HTML, hãy cân nhắc sử dụng *content controls* với *Office.js* thay thế.

## Bước 5: Chèn một hình ảnh ẩn (ví dụ, logo) để branding hoặc truy cập sau bằng script

Các shape ẩn không hiển thị trong tài liệu đã in nhưng vẫn tồn tại trong XML, cho phép bạn truy xuất chúng bằng mã sau này.

```csharp
// Insert an image from disk
Shape logo = builder.InsertImage("Resources/logo.png");

// Hide the image from the view/layout
logo.Hidden = true;

// You can still reference the image via its ShapeId if needed
string logoId = logo.Name;
```

## Bước 6: **Load markdown into a Word document** trong khi giữ định dạng gạch chân

Aspose.Words có thể nhập Markdown trực tiếp. Bật `ImportUnderlineFormatting` đảm bảo rằng các gạch chân trong markdown (`<u>` hoặc `__text__`) sẽ trở thành kiểu gạch chân của Word thay vì văn bản thường.

```csharp
// Configure markdown load options
MarkdownLoadOptions mdOptions = new MarkdownLoadOptions
{
    ImportUnderlineFormatting = true
};

// Load the markdown file into a new Document instance
Document markdownDoc = new Document("Resources/sample.md", mdOptions);

// Append the markdown content to the main document after the previous elements
builder.MoveToDocumentEnd();
builder.InsertDocument(markdownDoc, ImportFormatMode.KeepSourceFormatting);
```

**Trường hợp đặc biệt:** Nếu tệp markdown chứa bảng, chúng sẽ tự động chuyển thành bảng Word. Nếu bạn cần kiểu bảng tùy chỉnh, hãy áp dụng `DocumentBuilder` sau khi chèn.

## Bước 7: Ký tài liệu bằng XAdES‑EPES (bước bảo mật tùy chọn)

Chữ ký số đảm bảo tính toàn vẹn của tài liệu. Đoạn mã dưới đây ký file **create group shape docx** bằng hồ sơ XAdES‑EPES.

```csharp
// Initialize the signature object for the current document
Signature signature = new Signature(document);

// Choose the XAdES‑EPES level
signature.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;

// Sign using a .pfx certificate (replace path and password)
signature.Sign("Resources/cert.pfx", "password");

// Save the signed document
document.Save("Output/SignedGroupShape.docx");
```

> **Lưu ý bảo mật:** Giữ mật khẩu chứng chỉ ra khỏi source control. Sử dụng biến môi trường hoặc kho bảo mật trong môi trường production.

## Ví dụ đầy đủ có thể chạy

Kết hợp tất cả các bước lại với nhau tạo thành một chương trình tự chứa duy nhất. Lưu tệp dưới tên `Program.cs` và chạy từ dòng lệnh.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving.Signature;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the document and group shape
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        GroupShape group = builder.InsertGroupShape();
        group.AppendChild(builder.InsertShape(ShapeType.Rectangle, 100, 50));
        group.AppendChild(builder.InsertShape(ShapeType.Ellipse, 80, 40));

        // 2️⃣ Add a plain‑text content control
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText, "MyTag");
        sdt.PlaceholderName = "Enter text here";

        // 3️⃣ Insert an ActiveX command button
        Forms2OleControl btn = builder.InsertForms2OleControl();
        btn.ControlType = Forms2OleControl.ControlType.CommandButton;
        btn.Caption = "Click Me";

        // 4️⃣ Insert a hidden logo image
        Shape logo = builder.InsertImage("Resources/logo.png");
        logo.Hidden = true;

        // 5️⃣ Load markdown while keeping underline formatting
        MarkdownLoadOptions mdOpts = new MarkdownLoadOptions
        {
            ImportUnderlineFormatting = true
        };
        Document mdDoc = new Document("Resources/sample.md", mdOpts);
        builder.MoveToDocumentEnd();
        builder.InsertDocument(mdDoc, ImportFormatMode.KeepSourceFormatting);

        // 6️⃣ Sign the document (optional)
        Signature sig = new Signature(doc);
        sig.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;
        sig.Sign("Resources/cert.pfx", "password");

        // Save the final file
        doc.Save("Output/CompleteGroupShape.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

Running the program generates `CompleteGroupShape.docx` containing:

- Một hình chữ nhật + ellipse được nhóm (lõi **create group shape docx**)
- Một content control dạng plain‑text với văn bản placeholder
- Một **insert ActiveX command button** có nhãn “Click Me”
- Một hình logo ẩn
- Nội dung Markdown với gạch chân được giữ nguyên
- Một chữ ký số XAdES‑EPES (nếu cung cấp chứng chỉ)

## Các câu hỏi thường gặp và khắc phục sự cố

| Question | Answer |
|---|---|
| **Nút ActiveX có hoạt động trên Word macOS không?** | Word trên macOS không hỗ trợ các điều khiển ActiveX. Nút sẽ hiển thị dưới dạng hình ảnh tĩnh. Hãy sử dụng content controls với Office.js để có tính tương tác đa nền tảng. |
| **Nếu tệp markdown chứa CSS tùy chỉnh thì sao?** | Aspose.Words bỏ qua CSS; chỉ xử lý cú pháp markdown chuẩn. Chuyển các phần tử được định dạng bằng CSS sang style Word một cách thủ công sau khi nhập. |
| **Tôi có thể thêm nhiều shape vào cùng một group sau này không?** | Có. Lấy `GroupShape` bằng tên hoặc chỉ mục, sau đó gọi `AppendChild(newShape)`. Nhớ lưu lại tài liệu sau khi thực hiện thay đổi. |
| **Làm sao để thay đổi thuật toán ký?** | Đặt `signature.SignatureAlgorithm` trước khi gọi `Sign`. Mặc định là SHA‑256, đáp ứng hầu hết các yêu cầu tuân thủ. |
| **Hình ảnh ẩn có hiển thị trong giao diện Word không?** | Không, nhưng có thể hiển thị bằng cách bật tùy chọn *Show hidden text* trong cài đặt Word. Điều này hữu ích để lưu trữ metadata mà không làm rối bố cục. |

## Các bước tiếp theo

Bây giờ bạn đã có thể **create group shape docx**, **insert ActiveX command button**, và **load markdown into a Word document**, bạn có thể khám phá:

- **Nhúng macro VBA** phản hồi khi nút ActiveX được nhấn.
- **Áp dụng style tùy chỉnh** cho các đoạn văn được tạo từ markdown.
- **Tạo PDF** từ cùng một tài liệu bằng cách sử dụng `doc.Save("output.pdf", SaveFormat.Pdf)`.
- **Tự động hoá xử lý hàng loạt** nhiều tệp markdown thành một báo cáo tổng hợp.

Các mở rộng này cho phép bạn xây dựng quy trình tài liệu hoàn toàn tự động, kết hợp đồ họa phong phú, các điều khiển tương tác và việc soạn thảo dựa trên markdown — tất cả đều từ C#.

---

*Chúc lập trình vui! Nếu bạn thấy tutorial này

## Bạn Nên Học Gì Tiếp Theo?

Các tutorial sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo Group Shape trong Tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Tạo hình chữ nhật trong Word bằng C# – Hướng dẫn từng bước](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Tạo markdown từ Word – Hướng dẫn C# đầy đủ](/words/english/java/document-conversion-and-export/create-markdown-from-word-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}