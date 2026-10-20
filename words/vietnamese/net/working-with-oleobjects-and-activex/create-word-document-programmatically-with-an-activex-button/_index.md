---
category: general
date: 2026-10-20
description: Tạo tài liệu Word bằng lập trình và thêm nút lệnh bằng Aspose.Words.
  Học cách chèn điều khiển ActiveX và đặt chú thích cho nút.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add command button
- add activex control
- insert activex button
- set button caption
language: vi
lastmod: 2026-10-20
og_description: Tạo tài liệu Word bằng lập trình và nhúng một nút lệnh ActiveX. Hướng
  dẫn này giải thích cách chèn điều khiển và đặt nhãn cho nó bằng Aspose.Words.
og_image_alt: Word file showing an ActiveX command button inserted by Aspose.Words
og_title: Tạo tài liệu Word bằng lập trình – thêm nút ActiveX
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  headline: Create Word document programmatically with an ActiveX button
  type: TechArticle
- description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  name: Create Word document programmatically with an ActiveX button
  steps:
  - name: 'Open a terminal or Visual Studio and create a new console project:'
    text: 'Open a terminal or Visual Studio and create a new console project:'
  - name: 'Add the Aspose.Words package:'
    text: 'Add the Aspose.Words package:'
  - name: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
    text: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
  - name: Open `ActiveXCommandButton.docx` in Microsoft Word.
    text: Open `ActiveXCommandButton.docx` in Microsoft Word.
  - name: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
    text: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
  - name: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
    text: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
  - name: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
    text: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Tạo tài liệu Word bằng lập trình với nút ActiveX
url: /vi/net/working-with-oleobjects-and-activex/create-word-document-programmatically-with-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu Word bằng chương trình với nút ActiveX

Tạo tài liệu Word bằng chương trình với Aspose.Words, sau đó thêm một nút lệnh mà người dùng có thể nhấp. Hướng dẫn này sẽ chỉ cho bạn cách chèn một điều khiển ActiveX, cấu hình các thuộc tính của nó, và lưu kết quả dưới dạng tệp **.docx**.

Bạn sẽ thấy một ví dụ đầy đủ, có thể chạy được mà bạn có thể sao chép vào một ứng dụng console. Khi kết thúc hướng dẫn, bạn có thể tạo một tệp Word chứa một nút lệnh hoạt động đầy đủ, và bạn sẽ hiểu cách **add command button**, **add activex control**, **insert activex button**, và **set button caption** mà không rời khỏi mã C# của mình.

## Yêu cầu trước

* .NET 6.0 SDK hoặc phiên bản mới hơn đã được cài đặt  
* Visual Studio 2022 (hoặc bất kỳ IDE nào tương thích với C#)  
* Tệp giấy phép Aspose.Words cho .NET (bản dùng thử miễn phí hoạt động cho ví dụ này)  
* Kiến thức cơ bản về C# và hệ thống dự án .NET  

Không cần thêm bất kỳ gói NuGet nào ngoài **Aspose.Words** vì hỗ trợ ActiveX đã được tích hợp sẵn trong thư viện.

## Bước 1: Thiết lập dự án và thêm Aspose.Words

1. Mở terminal hoặc Visual Studio và tạo một dự án console mới:

   ```bash
   dotnet new console -n WordActiveXDemo
   cd WordActiveXDemo
   ```

2. Thêm gói Aspose.Words:

   ```bash
   dotnet add package Aspose.Words
   ```

3. (Tùy chọn) Nếu bạn có tệp giấy phép, đặt nó vào thư mục gốc của dự án và thêm dòng sau vào đầu file `Program.cs` để tránh các dấu nước đánh giá:

   ```csharp
   Aspose.Words.License license = new Aspose.Words.License();
   license.SetLicense("Aspose.Words.lic");
   ```

## Bước 2: Tạo tài liệu Word bằng chương trình – khởi tạo tài liệu

Hoạt động đầu tiên là **create Word document programmatically**. Bạn thực hiện điều này bằng cách khởi tạo một đối tượng `Document` và một `DocumentBuilder` cho phép bạn chỉnh sửa nội dung tài liệu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;   // Provides ActiveX control types
using System.Drawing;        // For Point and Size structs

// Initialize a new blank document
Document document = new Document();

// DocumentBuilder gives a cursor‑based API for inserting elements
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` đại diện cho toàn bộ tệp, trong khi `DocumentBuilder` duy trì một con trỏ mà bạn có thể di chuyển đến bất kỳ vị trí nào trong tài liệu. Sự tách biệt này giữ cho API sạch sẽ và cho phép bạn **add activex control** sau này mà không cần quản lý thủ công các cấu trúc cấp thấp.

## Bước 3: Thêm nút lệnh – chèn điều khiển ActiveX

Bây giờ bạn sẽ **add command button** bằng cách chèn một điều khiển ActiveX loại `OleControlType.CommandButton`. Phương thức `InsertForms2OleControl` yêu cầu loại điều khiển, vị trí (`Point`), và kích thước (`Size`).

```csharp
// Define where the button will appear (X = 100 pt, Y = 150 pt)
Point buttonPosition = new Point(100, 150);

// Define the button dimensions (width = 120 pt, height = 30 pt)
Size buttonSize = new Size(120, 30);

// Insert the ActiveX command button at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton, // control type
    buttonPosition,              // position
    buttonSize);                 // size
```

Lệnh trên **insert activex button** vào tài liệu tại các tọa độ chính xác mà bạn chỉ định. Các tọa độ được đo bằng điểm (1 pt ≈ 1/72 in). Nếu bạn cần nút trên một đoạn văn cụ thể, hãy di chuyển con trỏ của builder trước:

```csharp
builder.Writeln("Click the button below:");
builder.MoveToDocumentEnd(); // places the cursor after the paragraph
```

## Bước 4: Đặt chú thích nút – tùy chỉnh văn bản nút lệnh

Một nút không có nhãn sẽ gây nhầm lẫn, vì vậy bạn sẽ **set button caption** thành một nội dung có ý nghĩa. Thuộc tính `Caption` xác định văn bản hiển thị trên nút, trong khi `Name` cung cấp cho điều khiển một định danh lập trình.

```csharp
// Give the button a unique name for later reference
commandButton.Name = "btnSubmit";

// Set the visible text on the button
commandButton.Caption = "Submit";

// Optional: assign a macro name that Word will call when the button is clicked
commandButton.OnClick = "SubmitForm()";
```

Nếu bạn sau này xuất tài liệu sang định dạng hỗ trợ macro (`.docm`), giá trị `OnClick` phải khớp với tên macro VBA. Đối với tệp `.docx` thông thường, thuộc tính này được lưu nhưng không được thực thi, điều này phù hợp với hầu hết các kịch bản tự động.

## Bước 5: Lưu tài liệu chứa nút ActiveX

Sau khi cấu hình điều khiển, bạn có thể **save the document**. Chọn một thư mục mà bạn có quyền ghi, và sử dụng phần mở rộng `.docx` để đạt độ tương thích tối đa.

```csharp
// Replace with your desired output folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ActiveXCommandButton.docx");

// Save the document to disk
document.Save(outputPath);
```

Khi bạn mở tệp đã tạo trong Microsoft Word, bạn sẽ thấy một nút có nhãn **Submit** tại các tọa độ bạn đã chỉ định. Nhấp vào nút trong ứng dụng desktop sẽ cố gắng chạy macro `SubmitForm` (nếu nó tồn tại).

## Bước 6: Xác minh kết quả và khắc phục các vấn đề thường gặp

1. Mở `ActiveXCommandButton.docx` trong Microsoft Word.  
2. Chuyển sang **Design Mode** (tab Developer → **Design Mode**) để xem viền của nút.  
3. Nếu nút không hiển thị, kiểm tra xem tab **Developer** đã được bật và phiên bản Word của bạn có hỗ trợ các điều khiển ActiveX hay không.  
4. Đối với các tệp hỗ trợ macro (`.docm`), đảm bảo tên macro trong `OnClick` khớp với một routine VBA; nếu không, Word sẽ hiển thị cảnh báo bảo mật.

### Mẹo chuyên nghiệp

Các điều khiển ActiveX chỉ hỗ trợ Windows. Nếu bạn cần tính tương tác đa nền tảng, hãy xem xét sử dụng **Content Controls** (`RichTextContentControl`) thay vì nút ActiveX.

## Mã nguồn đầy đủ

Dưới đây là chương trình đầy đủ, sẵn sàng chạy. Sao chép nó vào `Program.cs` và thực thi `dotnet run`.

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Optional: apply a license to remove evaluation watermarks
        // var license = new Aspose.Words.License();
        // license.SetLicense("Aspose.Words.lic");

        // Step 2: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a paragraph to give context
        builder.Writeln("Please click the button below to submit the form:");
        builder.MoveToDocumentEnd();

        // Step 3: Add command button – insert ActiveX control
        Point position = new Point(100, 150);
        Size size = new Size(120, 30);
        Forms2OleControl commandButton = builder.InsertForms2OleControl(


## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, dựa trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo tài liệu Word với nút ActiveX – Hướng dẫn C#](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)
- [Thêm nút lệnh vào tài liệu Word với Aspose.Words – Hướng dẫn đầy đủ](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)
- [tạo nút tài liệu word với Aspose.Words – Ví dụ mã đầy đủ](/words/english/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}