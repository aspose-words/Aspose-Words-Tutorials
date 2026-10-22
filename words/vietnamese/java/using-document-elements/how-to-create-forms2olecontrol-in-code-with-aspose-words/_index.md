---
category: general
date: 2026-09-11
description: Tìm hiểu cách tạo forms2olecontrol trong mã bằng Aspose.Words DocumentBuilder.
  Hướng dẫn từng bước này bao gồm việc chèn nút lệnh ActiveX, cách sử dụng setOleClassName
  và việc điều chỉnh kích thước.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create forms2olecontrol in code
- ActiveX command button
- Aspose.Words DocumentBuilder
- setOleClassName method
- Forms2OleControl size
language: vi
lastmod: 2026-09-11
og_description: Tạo forms2olecontrol trong mã bằng Aspose.Words. Hãy làm theo hướng
  dẫn này để chèn một nút lệnh ActiveX, đặt tên lớp cho nó và điều chỉnh kích thước.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX command
  button inserted via code
og_title: Tạo forms2olecontrol bằng mã – hướng dẫn đầy đủ Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  headline: How to create forms2olecontrol in code with Aspose.Words
  type: TechArticle
- description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  name: How to create forms2olecontrol in code with Aspose.Words
  steps:
  - name: Initialise the DocumentBuilder
    text: The `DocumentBuilder` class is the entry point for most document‑generation
      tasks in Aspose.Words. It gives you methods to add text, images, tables, and,
      importantly for this tutorial, OLE controls.
  - name: Insert the Forms2OleControl
    text: The `insertForms2OleControl` method returns a `Forms2OleControl` object.
      This object represents the OLE control placeholder that Word will render as
      an ActiveX button.
  - name: Specify the ActiveX class with setOleClassName
    text: Word needs to know which type of ActiveX control to render. The class name
      for a standard command button is `"Forms.CommandButton.1"`.
  - name: Adjust the Forms2OleControl size
    text: A button that is too small or too large looks unprofessional. You can control
      its dimensions with `setWidth` and `setHeight`.
  - name: Save the document and test
    text: After configuring the control, save the document to a location of your choice.
  - name: When to use Forms2OleControl vs. Content Controls
    text: If you only need simple data entry (e.g., a plain text field), Word’s built‑in
      content controls are lighter weight. Use `Forms2OleControl` when you require
      full ActiveX functionality such as event handling or custom VBA interaction.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Cách tạo forms2olecontrol trong mã bằng Aspose.Words
url: /vi/java/using-document-elements/how-to-create-forms2olecontrol-in-code-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo forms2olecontrol trong mã với Aspose.Words

Nếu bạn cần **tạo forms2olecontrol trong mã**, hướng dẫn này sẽ chỉ cho bạn cách thực hiện chính xác bằng cách sử dụng API Aspose.Words .NET. Cho dù bạn đang tự động hoá một mẫu cần nút lệnh ActiveX hoặc chỉ muốn làm phong phú tài liệu Word một cách lập trình, các bước dưới đây bao gồm mọi thứ từ việc chèn điều khiển đến cấu hình giao diện của nó.

Trong tutorial này, bạn sẽ học cách sử dụng **Aspose.Words DocumentBuilder** để chèn một **ActiveX command button**, đặt lớp của nó bằng **phương thức setOleClassName**, và điều chỉnh **kích thước Forms2OleControl**. Không cần công cụ bên ngoài — chỉ cần môi trường phát triển .NET và thư viện Aspose.Words.

## Prerequisites

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* .NET 6.0 hoặc phiên bản mới hơn đã được cài đặt (mã cũng hoạt động với .NET Framework 4.7+)
* Phiên bản mới nhất của gói NuGet Aspose.Words for .NET
* Kiến thức cơ bản về C# và khái niệm điều khiển ActiveX trong tài liệu Word

Nếu thiếu bất kỳ mục nào, hãy cài đặt gói NuGet bằng:

```bash
dotnet add package Aspose.Words
```

## What this tutorial covers

* Tạo một thể hiện `DocumentBuilder`
* Chèn một `Forms2OleControl` (đối tượng nền tảng cho nút lệnh ActiveX)
* Gán tên lớp đúng bằng `setOleClassName`
* Đặt chiều rộng và chiều cao hiển thị bằng các thuộc tính **kích thước Forms2OleControl**
* Lưu tài liệu và kiểm tra kết quả

Khi hoàn thành hướng dẫn, bạn sẽ có một tệp Word hoạt động đầy đủ chứa một nút có thể nhấn được, mà bạn có thể tùy chỉnh thêm hoặc liên kết với macro VBA.

---

## How to create forms2olecontrol in code – step‑by‑step

### Step 1: Initialise the DocumentBuilder

Lớp `DocumentBuilder` là điểm khởi đầu cho hầu hết các tác vụ tạo tài liệu trong Aspose.Words. Nó cung cấp cho bạn các phương thức để thêm văn bản, hình ảnh, bảng và, quan trọng đối với tutorial này, các điều khiển OLE.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Initialise the builder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:**  
`DocumentBuilder` duy trì vị trí con trỏ hiện tại trong tài liệu. Bằng cách tạo nó sớm, bạn đảm bảo rằng bất kỳ chèn nào tiếp theo — chẳng hạn như **ActiveX command button** — sẽ xuất hiện đúng nơi bạn muốn.

### Step 2: Insert the Forms2OleControl

Phương thức `insertForms2OleControl` trả về một đối tượng `Forms2OleControl`. Đối tượng này đại diện cho chỗ giữ OLE mà Word sẽ hiển thị dưới dạng nút ActiveX.

```csharp
// Insert the Forms2OleControl at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

**Why this matters:**  
Nếu không gọi phương thức này, bạn sẽ không thể thao tác với các thuộc tính của điều khiển. `Forms2OleControl` trả về cho bạn quyền truy cập đầy đủ vào **phương thức setOleClassName**, các thuộc tính kích thước và các cài đặt OLE‑specific khác.

### Step 3: Specify the ActiveX class with setOleClassName

Word cần biết loại điều khiển ActiveX nào sẽ được hiển thị. Tên lớp cho một nút lệnh chuẩn là `"Forms.CommandButton.1"`.

```csharp
// Tell Word that this OLE control is a CommandButton
commandButton.SetOleClassName("Forms.CommandButton.1");
```

**Why this matters:**  
Phương thức `setOleClassName` là cầu nối giữa chỗ giữ OLE chung và **ActiveX command button** cụ thể. Sử dụng tên lớp sai sẽ dẫn đến đối tượng trống hoặc lỗi thời gian chạy khi mở tài liệu.

### Step 4: Adjust the Forms2OleControl size

Một nút quá nhỏ hoặc quá lớn sẽ trông không chuyên nghiệp. Bạn có thể kiểm soát kích thước của nó bằng `setWidth` và `setHeight`.

```csharp
// Set the visual dimensions (points) of the button
commandButton.SetWidth(80);   // width in points
commandButton.SetHeight(30);  // height in points
```

**Why this matters:**  
Các thuộc tính này tạo nên **kích thước Forms2OleControl**. Chúng ảnh hưởng đến cách nút hiển thị trong giao diện Word và đảm bảo rằng bất kỳ macro nào được gắn vào cũng có đủ vùng nhấn.

### Step 5: Save the document and test

Sau khi cấu hình điều khiển, lưu tài liệu vào vị trí bạn muốn.

```csharp
// Save the document as a .docx file
doc.Save("ActiveXButton.docx");
```

Mở `ActiveXButton.docx` trong Microsoft Word. Bạn sẽ thấy một nút có nhãn “CommandButton1” (chú thích mặc định). Nhấn vào nó sẽ không làm gì trừ khi bạn thêm macro VBA, nhưng điều khiển đã hoạt động đầy đủ.

**Expected output:**  

![Tài liệu Word với nút ActiveX command button được chèn](/images/activeX-button.png "Screenshot of a Word document showing a newly created ActiveX command button inserted via code")

*Văn bản alt của hình ảnh chứa từ khóa chính để hỗ trợ truy cập và SEO.*

---

## Understanding the ActiveX Forms2OleControl class

Lớp `Forms2OleControl` bao bọc hạ tầng OLE cấp thấp mà Word sử dụng cho các phần tử ActiveX. Nó kế thừa từ `Shape`, nghĩa là bạn cũng có thể áp dụng các định dạng hình dạng thông thường (ví dụ: viền, xoay) nếu cần.

* **ActiveX command button** – Trường hợp sử dụng phổ biến nhất; bạn có thể liên kết nó với macro qua công cụ phát triển của Word.  
* **phương thức setOleClassName** – Xác định lớp COM mà Word sẽ tải; các giá trị hợp lệ khác bao gồm `"Forms.TextBox.1"` và `"Forms.ComboBox.1"`.  
* **kích thước Forms2OleControl** – Kiểm soát qua `SetWidth`/`SetHeight`. Các phương thức này nhận đơn vị điểm (1 pt = 1/72 in).

### When to use Forms2OleControl vs. Content Controls

Nếu bạn chỉ cần nhập dữ liệu đơn giản (ví dụ: trường văn bản thuần), các điều khiển nội dung tích hợp sẵn của Word nhẹ hơn. Hãy sử dụng `Forms2OleControl` khi bạn cần chức năng ActiveX đầy đủ như xử lý sự kiện hoặc tương tác VBA tùy chỉnh.

---

## Setting additional properties (optional)

Mặc dù các bước cơ bản đã đủ để **tạo forms2olecontrol trong mã**, bạn thường muốn tinh chỉnh thêm giao diện hoặc hành vi của nút.

```csharp
// Change the button caption (requires a VBA macro to read it)
commandButton.SetOleData("Caption", "Submit");

// Disable the button initially
commandButton.SetOleData("Enabled", false);

// Add a tooltip
commandButton.SetOleData("ToolTipText", "Click to submit the form");
```

**Why this matters:**  
`SetOleData` cho phép bạn ghi các giá trị thuộc tính tùy ý trực tiếp vào luồng OLE. Đây là cách linh hoạt nhất để tùy chỉnh một **ActiveX command button** mà không cần đến VBA.

---

## Common pitfalls and troubleshooting

| Symptom | Likely cause | Fix |
|--------|--------------|-----|
| Nút hiển thị dưới dạng hộp màu xám | Tên lớp không đúng được truyền vào `setOleClassName` | Kiểm tra chuỗi phải chính xác là `"Forms.CommandButton.1"` (phân biệt chữ hoa/thường) |
| Kích thước không thay đổi | Width/Height được đặt trước khi chèn điều khiển | Luôn gọi `SetWidth`/`SetHeight` **sau** `InsertForms2OleControl` |
| Tài liệu báo lỗi “OLE object not found” khi mở | Thiếu giấy phép Aspose.Words (phiên bản dùng thử có thể giới hạn OLE) | Áp dụng giấy phép hợp lệ hoặc dùng bản dùng thử miễn phí với hỗ trợ OLE đầy đủ |
| Nhãn nút vẫn là “CommandButton1” | `SetOleData` không được sử dụng hoặc macro không đọc thuộc tính | Sử dụng macro VBA để đọc thuộc tính `"Caption"` hoặc đặt nhãn qua giao diện Word |

---

## Full, runnable example

Dưới đây là một ứng dụng console hoàn chỉnh mà bạn có thể sao chép, dán và chạy. Nó minh họa mọi nội dung đã được đề cập trong tutorial này.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace Forms2OleControlDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1. Create a new document and a DocumentBuilder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2. Insert the Forms2OleControl (ActiveX placeholder)
            Forms2OleControl commandButton = builder.InsertForms2OleControl();

            // 3. Set the ActiveX class to CommandButton
            commandButton.SetOleClassName("Forms.CommandButton.1");

            // 4. Define the visual size of the button
            commandButton.SetWidth(80);   // 80 points = ~1.11 inches
            commandButton.SetHeight(30);  // 30 points = ~0.42 inches

            // Optional: set a custom caption via OLE data (requires VBA to read)
            commandButton.SetOleData("Caption", "Submit");

            // 5. Save the document
            string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Explanation of each section**

* **Using directives** – Kéo vào không gian tên Aspose.Words cần thiết cho `Document`, `DocumentBuilder` và `Forms2OleControl`.  
* **Document creation** – Tạo một tệp Word trống.  
* **InsertForms2OleControl** – Đặt điều khiển OLE tại vị trí con trỏ hiện tại của builder.  
* **SetOleClassName** – Thông báo cho Word rằng điều khiển là một **ActiveX command button**.  
* **SetWidth / SetHeight** – Điều chỉnh **kích thước Forms2OleControl** để có giao diện chuyên nghiệp.  
* **SetOleData (optional)** – Minh họa cách ghi các thuộc tính bổ sung như nhãn.  
* **Save** – Ghi tệp `.docx` cuối cùng ra đĩa.

Chạy chương trình (`dotnet run`) và mở `ActiveXButton.docx`. Bạn sẽ thấy một nút mà sau này có thể liên kết với macro.

---

## Conclusion

Bạn đã biết cách **tạo forms2olecontrol trong mã** bằng Aspose.Words, từ việc khởi tạo `DocumentBuilder` đến cấu hình **ActiveX command button** với `setOleClassName` và kiểm soát **kích thước Forms2OleControl**. Cách tiếp cận này cho phép bạn tự động hoá các tài liệu Word phức tạp, nhúng các yếu tố giao diện tương tác và giữ toàn bộ logic bên trong.

## What Should You Learn Next?

Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm mã mẫu hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách tạo trường biểu mẫu và thêm nội dung bằng DocumentBuilder trong Aspose.Words cho Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Tạo Group Shape trong tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Tạo hình chữ nhật trong Word với Aspose.Words – Hướng dẫn chi tiết](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}