---
category: general
date: 2026-01-02
description: Tạo thư mục assets và chuyển đổi Word sang Markdown bằng Aspose.Words.
  Tìm hiểu cách trích xuất hình ảnh từ docx và lưu docx dưới dạng markdown bằng C#.
draft: false
keywords:
- create assets folder
- convert word to markdown
- extract images from docx
- save docx as markdown
- docx to markdown c#
language: vi
og_description: Tạo thư mục assets và chuyển đổi Word sang Markdown bằng Aspose.Words.
  Hướng dẫn này cho thấy cách trích xuất hình ảnh từ file docx và lưu file docx dưới
  dạng markdown trong C#.
og_title: Tạo thư mục assets khi chuyển đổi Word sang Markdown – Hướng dẫn C#
tags:
- Aspose.Words
- C#
- Markdown conversion
title: Tạo thư mục assets khi chuyển đổi Word sang Markdown trong C#
url: /vi/net/programming-with-markdownsaveoptions/create-assets-folder-while-converting-word-to-markdown-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo thư mục assets khi chuyển đổi Word sang Markdown trong C#

Bạn đã bao giờ cần **tạo thư mục assets** khi bạn đang chuyển đổi tài liệu Word sang Markdown chưa? Bạn không phải là người duy nhất. Nhiều nhà phát triển gặp khó khăn khi hình ảnh và các tài nguyên nhúng khác bị mất trong quá trình chuyển đổi, để lại các liên kết bị hỏng trong tệp `.md` kết quả.  

Tin tốt là gì? Với Aspose.Words bạn có thể **chuyển đổi Word sang Markdown** và tự động đưa mọi hình ảnh vào một thư mục `assets` gọn gàng—không cần sao chép thủ công. Trong hướng dẫn này chúng ta sẽ đi qua toàn bộ quy trình, từ việc tải tệp `.docx` đến việc trích xuất hình ảnh, lưu markdown, và dĩ nhiên, tạo ra thư mục assets mà bạn đang tìm kiếm.

Khi hoàn thành, bạn sẽ có thể **lưu docx dưới dạng markdown**, mọi hình ảnh sẽ được lưu trữ gọn gàng, và hiểu cách tinh chỉnh quy trình cho các trường hợp đặc biệt như PDF lớn hoặc quy tắc đặt tên hình ảnh tùy chỉnh. Sẵn sàng chưa? Hãy bắt đầu.

---

## Những gì bạn cần

- **Aspose.Words cho .NET** (v23.12 hoặc mới hơn). Thư viện này miễn phí dùng thử; giấy phép sẽ loại bỏ dấu watermark đánh giá.
- **.NET 6+** (hoặc .NET Framework 4.7.2+ nếu bạn thích môi trường chạy cổ điển).
- Một IDE C# cơ bản (Visual Studio, Rider, hoặc VS Code với extension C#).
- Một tệp mẫu `input.docx` chứa ít nhất một hình ảnh, để chúng ta có thể thấy bước **trích xuất hình ảnh từ docx** hoạt động.

Không cần bất kỳ gói NuGet bổ sung nào ngoài Aspose.Words.

---

## Bước 1: Thiết lập dự án và cài đặt Aspose.Words

Đầu tiên, tạo một ứng dụng console:

```bash
dotnet new console -n DocxToMarkdownDemo
cd DocxToMarkdownDemo
dotnet add package Aspose.Words
```

> **Mẹo:** Nếu bạn đang dùng Visual Studio, chỉ cần tạo một dự án “Console App (.NET Core)” mới và thêm gói NuGet qua giao diện Package Manager UI.

Sau khi gói được cài đặt, mở `Program.cs`. Chúng ta sẽ bắt đầu bằng cách thêm các chỉ thị `using` cần thiết:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;
```

Các namespace này cung cấp cho chúng ta lớp `Document`, `MarkdownSaveOptions`, và các trợ giúp hệ thống tệp mà chúng ta sẽ cần cho bước **tạo thư mục assets**.

---

## Bước 2: Tải tài liệu Word nguồn

Việc tải một tệp `.docx` đơn giản chỉ cần truyền đường dẫn tệp vào hàm khởi tạo `Document`. Đảm bảo tệp nằm ở vị trí mà ứng dụng của bạn có thể đọc — tốt nhất là cùng thư mục với file thực thi cho bản demo này.

```csharp
// Step 2: Load the source Word document
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

if (!File.Exists(inputPath))
{
    Console.WriteLine($"❌ Could not find {inputPath}. Drop a Word file there and try again.");
    return;
}

Document doc = new Document(inputPath);
Console.WriteLine("✅ Loaded input.docx successfully.");
```

Tại sao chúng ta lại kiểm tra `File.Exists`? Bởi vì tệp bị thiếu là rào cản phổ biến nhất khi bạn lần đầu cố gắng **chuyển đổi word sang markdown**. Điều kiện bảo vệ này sẽ đưa ra thông báo lỗi thân thiện thay vì một ngoại lệ khó hiểu.

---

## Bước 3: Cấu hình tùy chọn Markdown và callback lưu tài nguyên

Aspose.Words cho phép chúng ta can thiệp vào quy trình lưu thông qua `IResourceSavingCallback`. Đây là nơi chúng ta sẽ **tạo thư mục assets** và đặt tên duy nhất cho mỗi hình ảnh.

```csharp
// Step 3: Configure Markdown save options and attach a resource‑saving callback
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // Use a callback to control where each resource (image, etc.) ends up
    ResourceSavingCallback = new MyResourceCallback()
};
```

Lớp callback nằm vài dòng phía dưới. Nó thực hiện ba việc:

1. Đảm bảo thư mục `assets` tồn tại.
2. Tạo tên tệp dựa trên GUID để tránh trùng lặp.
3. Cập nhật `args.ResourceFileName` để Aspose ghi tệp vào vị trí đúng.

---

## Bước 4: Triển khai Resource‑Saving Callback (Tạo Thư mục Assets)

Dưới đây là triển khai đầy đủ. Lưu ý các chú thích chi tiết — điều này làm cho hướng dẫn **có thể trích dẫn** vì bất kỳ ai cũng có thể theo dõi lý do mà không phải đoán mò.

```csharp
// Step 4: Callback that stores each resource (e.g., images) in an assets folder
class MyResourceCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // -----------------------------------------------------------------
        // 1️⃣ Decide where the assets folder lives.
        //    You can make this configurable, but for this demo we’ll
        //    place it next to the output markdown file.
        // -----------------------------------------------------------------
        string outputDir = Path.GetDirectoryName(args.DocumentFileName);
        string assetsFolder = Path.Combine(outputDir, "assets");

        // Ensure the folder exists – this is the core of “create assets folder”
        Directory.CreateDirectory(assetsFolder);

        // -----------------------------------------------------------------
        // 2️⃣ Generate a unique file name.
        //    Using a GUID prevents name clashes when the source doc has
        //    multiple images with the same original name.
        // -----------------------------------------------------------------
        string extension = Path.GetExtension(args.ResourceFileName);
        string uniqueName = $"{Guid.NewGuid()}{extension}";

        // -----------------------------------------------------------------
        // 3️⃣ Tell Aspose where to write the file.
        //    The markdown will reference this relative path.
        // -----------------------------------------------------------------
        args.ResourceFileName = Path.Combine(assetsFolder, uniqueName);

        // No need to set args.Cancel = true; the default saving will continue.
    }
}
```

> **Tại sao lại dùng GUID?** Nếu bạn chỉ tái sử dụng `args.ResourceFileName`, hai hình ảnh có tên `image1.png` có thể ghi đè lên nhau. GUID đảm bảo tính duy nhất, điều này đặc biệt hữu ích khi bạn **trích xuất hình ảnh từ docx** mà chứa nhiều tên tệp giống nhau.

---

## Bước 5: Lưu tài liệu dưới dạng Markdown

Bây giờ chúng ta đã sẵn sàng thực hiện chuyển đổi. Tệp đầu ra sẽ nằm cạnh thư mục `assets`, và markdown sẽ chứa các liên kết tương đối như `![Image](assets/123e4567-e89b-12d3-a456-426614174000.png)`.

```csharp
// Step 5: Save the document as Markdown; the callback will handle embedded resources
string outputPath = Path.Combine(Environment.CurrentDirectory, "output", "report.md");

// Ensure the output directory exists
Directory.CreateDirectory(Path.GetDirectoryName(outputPath));

doc.Save(outputPath, mdOptions);
Console.WriteLine($"✅ Markdown saved to {outputPath}");
Console.WriteLine("📁 Assets folder created at: " + Path.Combine(Path.GetDirectoryName(outputPath), "assets"));
```

Chạy chương trình ngay bây giờ sẽ tạo ra:

- `output/report.md` – phiên bản markdown của tệp Word của bạn.
- `output/assets/` – một thư mục chứa mọi hình ảnh đã được trích xuất.

Mở `report.md` bằng bất kỳ trình xem markdown nào (xem trước trong VS Code, GitHub, v.v.) và bạn sẽ thấy các hình ảnh hiển thị đúng.

---

## Bước 6: Xác minh kết quả – Markdown trông như thế nào

Dưới đây là một đoạn trích của markdown được tạo ra sau khi chuyển đổi:

```markdown
# Sample Document

Here’s a paragraph with an image:

![Image](assets/4f3c2a1b-9e6d-4b2f-a9d3-0c9e5d6f7a12.png)

Another paragraph follows...
```

Nếu bạn mở tệp markdown và hình ảnh hiển thị, bạn đã **lưu docx dưới dạng markdown** thành công trong khi thư mục assets chứa mọi hình ảnh bạn cần để **trích xuất hình ảnh từ docx**.

---

## Các câu hỏi thường gặp & Trường hợp đặc biệt

### 1️⃣ Tệp Word chứa đồ họa SVG hoặc EMF thì sao?

Aspose.Words chuyển đổi hầu hết các định dạng vector sang PNG theo mặc định khi lưu thành Markdown. Nếu bạn cần giữ nguyên định dạng gốc, có thể điều chỉnh `mdOptions.ImageSavingOptions` (ví dụ: đặt `ImageSavingOptions.ImageFormat = ImageSaveOptions.SaveFormat.Svg`). Đừng quên cập nhật callback để bảo toàn phần mở rộng tệp đúng.

### 2️⃣ Làm sao để kiểm soát tên thư mục assets?

Chỉ cần thay `"assets"` trong `MyResourceCallback` bằng bất kỳ chuỗi nào bạn muốn, hoặc đọc nó từ tệp cấu hình:

```csharp
string assetsFolder = Path.Combine(outputDir, ConfigurationManager.AppSettings["AssetsFolderName"]);
```

### 3️⃣ Tài liệu của tôi có hàng trăm hình ảnh độ phân giải cao. Điều này có làm tăng bộ nhớ không?

Aspose.Words truyền tài nguyên ra đĩa từng cái một, vì vậy mức tiêu thụ bộ nhớ vẫn thấp. Tuy nhiên, tổng kích thước của thư mục assets sẽ bằng kích thước của các hình ảnh nhúng. Hãy cân nhắc nén chúng sau khi chuyển đổi nếu lo ngại về dung lượng lưu trữ.

### 4️⃣ Tôi cần markdown tham chiếu hình ảnh qua URL tuyệt đối (ví dụ cho trình tạo site tĩnh). Có thể không?

Có. Trong callback bạn có thể thêm tiền tố URL cơ sở:

```csharp
string baseUrl = "https://cdn.example.com/docs/assets/";
args.ResourceFileName = baseUrl + uniqueName;
```

Chỉ cần chắc chắn các tệp đã được tải lên cùng vị trí mà URL chỉ tới.

### 5️⃣ Điều này có hoạt động với tệp `.doc` (Word nhị phân) không?

Hoàn toàn có. Hàm khởi tạo `Document` tự động phát hiện định dạng, vì vậy bạn có thể đưa một tệp `.doc` và quy trình sẽ chuyển đổi sang Markdown, trích xuất hình ảnh theo cùng cách.

---

## Mẹo chuyên nghiệp cho chuyển đổi sẵn sàng sản xuất

- **Xử lý hàng loạt:** Đặt logic chuyển đổi trong một vòng `foreach` duyệt qua thư mục các tệp `.docx`. Giữ một thể hiện `MyResourceCallback` duy nhất và tái sử dụng nó để tăng tốc.
- **Ghi log:** Sử dụng framework ghi log (Serilog, NLog) thay vì `Console.WriteLine` cho các ứng dụng thực tế. Ghi lại tên hình ảnh gốc để dễ truy vết.
- **Xử lý lỗi:** Bao quanh lệnh `doc.Save` bằng khối `try‑catch` để bắt các ngoại lệ của `Aspose.Words`. Thường chúng xuất hiện khi có tính năng không được hỗ trợ (như đối tượng OLE).
- **Kiểm thử đơn vị:** Viết một test cung cấp một tệp `.docx` đã biết có hai hình ảnh và xác nhận rằng thư mục `assets` chứa đúng hai tệp sau khi chuyển đổi. Điều này bảo vệ khỏi regression khi nâng cấp Aspose.

---

## Ví dụ hoàn chỉnh (Sẵn sàng sao chép)

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

namespace DocxToMarkdownDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source document
            string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
            if (!File.Exists(inputPath))
            {
                Console.WriteLine($"❌ {inputPath} not found.");
                return;
            }

            Document doc = new Document(inputPath);
            Console.WriteLine("✅ Loaded input.docx");

            // 2️⃣ Configure save options with our callback
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new MyResourceCallback()
            };

            // 3️⃣ Prepare output location
            string outputPath = Path.Combine(Environment.CurrentDirectory, "output", "report.md");
            Directory.CreateDirectory(Path.GetDirectoryName(outputPath));

            // 4️⃣ Save as Markdown (assets folder will be created automatically)
            doc.Save(outputPath, mdOptions);
            Console.WriteLine($"✅ Markdown saved to {outputPath}");
            Console.WriteLine("📁 Assets folder: " + Path.Combine(Path.GetDirectoryName(outputPath), "assets"));
        }
    }

    // 5️⃣ Callback that creates the assets folder and gives each image a unique name

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}