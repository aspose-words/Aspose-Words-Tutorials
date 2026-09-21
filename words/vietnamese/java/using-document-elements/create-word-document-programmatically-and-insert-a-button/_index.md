---
category: general
date: 2026-09-21
description: Tạo tài liệu Word bằng lập trình và học cách lưu tài liệu Word bằng nút,
  chèn nút lệnh Word, và đặt chú thích cho nút lệnh bằng DocumentBuilder.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- save word document button
- insert command button word
- set command button caption
- how to use documentbuilder
language: vi
lastmod: 2026-09-21
og_description: Tạo tài liệu Word bằng lập trình với Aspose.Words. Tìm hiểu cách lưu
  tài liệu Word bằng nút, chèn nút lệnh vào Word, đặt chú thích cho nút lệnh và sử
  dụng DocumentBuilder cho các biểu mẫu tương tác.
og_image_alt: Screenshot of a Word file that contains an inserted CommandButton created
  programmatically
og_title: Tạo tài liệu Word bằng lập trình và thêm nút
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically and learn how to save word document
    button, insert command button word, and set command button caption using DocumentBuilder.
  headline: Create word document programmatically and insert a button
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Tạo tài liệu Word bằng lập trình và chèn một nút
url: /vi/java/using-document-elements/create-word-document-programmatically-and-insert-a-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu Word bằng chương trình và chèn nút

Nếu bạn cần **tạo tài liệu Word bằng chương trình**, Aspose.Words cung cấp một API linh hoạt cho phép bạn thêm các điều khiển tương tác như CommandButton. Hướng dẫn này cũng giải thích **cách sử dụng DocumentBuilder**, cách **lưu nút tài liệu Word**, và cách **đặt chú thích cho nút lệnh** để nút hiển thị chính xác như bạn mong muốn trong tệp .docx.

Bạn sẽ học cách:

* Khởi tạo một tài liệu trống bằng `Document`.
* Sử dụng `DocumentBuilder` để chỉnh sửa tài liệu.
* Chèn một **CommandButton** (`insert command button word`).
* Đặt tên và chú thích hiển thị cho nút (`set command button caption`).
* Lưu kết quả ra đĩa (`save word document button`).

Các bước được viết cho các nhà phát triển .NET sử dụng C# và Aspose.Words for .NET mới nhất (v24.10). Không cần bất kỳ gói NuGet bổ sung nào ngoài Aspose.Words.

---

## Những gì bạn cần trước khi bắt đầu

| Điều kiện tiên quyết | Lý do |
|----------------------|-------|
| Visual Studio 2022 (hoặc bất kỳ IDE C# nào) | Để biên dịch và chạy mã mẫu. |
| .NET 6.0 SDK hoặc mới hơn | Cung cấp môi trường chạy cho ví dụ. |
| Aspose.Words for .NET (v24.10 hoặc mới hơn) | Thư viện cho phép bạn **tạo tài liệu Word bằng chương trình** và thao tác các điều khiển biểu mẫu. |
| Kiến thức cơ bản về C# và các khái niệm OOP | Cần thiết để hiểu luồng mã. |

Bạn có thể cài đặt Aspose.Words qua NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Tạo tài liệu Word bằng chương trình

Bước đầu tiên là khởi tạo một `Document` trống. Đối tượng này đại diện cho toàn bộ tệp Word trong bộ nhớ.

```csharp
// Step 1: Create a new blank document
Document doc = new Document();
```

Tạo tài liệu bằng chương trình cung cấp cho bạn một canvas sạch để bạn có thể thêm đoạn văn, bảng hoặc các điều khiển tương tác.  

---

## Cách sử dụng DocumentBuilder

`DocumentBuilder` là lớp chính để chỉnh sửa một `Document`. Nó cung cấp các phương thức để chèn văn bản, hình ảnh và các trường biểu mẫu. Trong hướng dẫn này chúng ta dùng nó để đặt một CommandButton.

```csharp
// Step 2: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder duy trì một con trỏ nội bộ chỉ tới vị trí chèn hiện tại. Mặc định nó bắt đầu ở đầu phần đầu tiên, phù hợp cho ví dụ của chúng ta.

---

## Chèn CommandButton vào Word

Aspose.Words coi một CommandButton như một điều khiển ActiveX. Phương thức `InsertForms2OleControl` tạo một điều khiển OLE chung mà chúng ta sau đó cấu hình thành nút.

```csharp
// Step 3: Insert an ActiveX Forms2OleControl (a CommandButton)
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

Tại thời điểm này, điều khiển đã tồn tại trong tài liệu nhưng chưa có biểu diễn hình ảnh cho đến khi chúng ta xác định loại của nó.

---

## Đặt chú thích cho nút lệnh

Bây giờ chúng ta nói với điều khiển OLE rằng nó nên hoạt động như một CommandButton và đặt cho nó một nhãn thân thiện.

```csharp
// Step 4: Define the control as a CommandButton
commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

// Step 5: Set a unique name for the button (used for identification)
commandButton.SetName("btnSubmit");

// Step 6: Set the visible caption that appears on the button
commandButton.SetCaption("Submit");
```

Việc đặt **chú thích cho nút lệnh** là cần thiết vì Word hiển thị văn bản này trên bề mặt nút. Nếu bạn bỏ qua `SetCaption`, nút sẽ hiển thị một nhãn chung.

---

## Lưu tài liệu Word với nút

Cuối cùng, lưu tài liệu ra đĩa. Phương thức `Save` ghi toàn bộ gói Word, bao gồm nút mới chèn, vào tệp .docx.

```csharp
// Step 7: Save the document containing the CommandButton
doc.Save("YOUR_DIRECTORY/CommandButton.docx");
```

Tệp `CommandButton.docx` hiện chứa một nút hoạt động đầy đủ có nhãn **Submit**. Khi người dùng mở tệp trong Microsoft Word và nhấn nút, hành động mặc định (bạn có thể liên kết sau này qua VBA) sẽ được kích hoạt.

---

## Ví dụ hoàn chỉnh

Dưới đây là chương trình đầy đủ mà bạn có thể sao chép, dán và chạy. Nó minh họa toàn bộ quy trình từ tạo tài liệu đến lưu nút.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder (how to use DocumentBuilder)
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a CommandButton (insert command button word)
        Forms2OleControl commandButton = builder.InsertForms2OleControl();

        // 4. Define the control type as CommandButton
        commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

        // 5. Give the button a unique name (optional but useful)
        commandButton.SetName("btnSubmit");

        // 6. Set the visible caption (set command button caption)
        commandButton.SetCaption("Submit");

        // 7. Save the document (save word document button)
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Kết quả mong đợi**

* Một tệp có tên `CommandButton.docx` nằm ở đường dẫn bạn chỉ định.
* Mở tệp trong Microsoft Word sẽ hiển thị một nút **Submit** duy nhất trên trang đầu.
* Nút có thể được chọn, thay đổi kích thước, hoặc liên kết tới macro từ tab **Developer** của Word.

---

## Câu hỏi thường gặp và xử lý các trường hợp đặc biệt

| Câu hỏi | Trả lời |
|----------|--------|
| *Nếu tôi cần hơn một nút?* | Lặp lại các bước 3–6 với các tên và chú thích khác nhau. Mỗi nút phải có giá trị `SetName` duy nhất. |
| *Có thể đặt kích thước cho nút không?* | Có. Sau khi chèn điều khiển, bạn có thể sửa đổi các thuộc tính `Width` và `Height` thông qua đối tượng `OleFormat`. |
| *Nút sẽ hoạt động trên mọi phiên bản Word không?* | Các điều khiển ActiveX được hỗ trợ trong phiên bản desktop của Word (Windows). Chúng không được hiển thị trong Word Online hoặc trên macOS. |
| *Làm thế nào để thêm trình xử lý sự kiện click?* | Bạn cần viết mã VBA tham chiếu tới tên nút (`btnSubmit`). Macro VBA có thể được nhúng bằng cách sử dụng `doc.VbaProject`. |
| *Nếu tôi cần chèn nút vào trong một ô bảng thì sao?* | Di chuyển con trỏ của builder tới ô mong muốn (`builder.MoveTo(cell.FirstParagraph)`) trước khi gọi `InsertForms2OleControl`. |

---

## Mẹo chuyên nghiệp

* **Mẹo:** Luôn đặt tên có ý nghĩa bằng `SetName`. Điều này đơn giản hoá tự động hoá VBA và dễ dàng gỡ lỗi hơn.
* **Cảnh báo:** Quên gọi `SetControlType`. Nếu không gọi, đối tượng OLE sẽ xuất hiện như một placeholder chung thay vì nút có thể nhấn.
* **Mẹo hiệu năng:** Nếu bạn tạo nhiều tài liệu trong vòng lặp, hãy tái sử dụng một thể hiện `DocumentBuilder` duy nhất và gọi `builder.MoveToDocumentEnd()` trước mỗi lần chèn để tránh việc đặt lại con trỏ không cần thiết.

---

## Bước tiếp theo

Bây giờ bạn đã biết cách **tạo tài liệu Word bằng chương trình**, **chèn CommandButton vào Word**, **đặt chú thích cho nút lệnh**, và **lưu tài liệu Word với nút**, bạn có thể khám phá các kịch bản nâng cao hơn:

* Thêm các điều khiển **TextFormField** để người dùng nhập dữ liệu.
* Kết hợp các nút với trường **MacroButton** để thực thi VBA trực tiếp.
* Sử dụng **DocumentBuilder.InsertImage** để đặt biểu tượng lên nút của bạn.
* Tích hợp với ASP.NET để tạo biểu mẫu Word trên

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây bao quát các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo Tài liệu Word Mới](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Tạo Tài liệu Word với Aspose.Words cho .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Chèn Hình ảnh Inline trong Tài liệu Word bằng Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}