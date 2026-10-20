---
category: general
date: 2026-05-01
description: Cách di chuyển bóng trên một hình dạng trong Aspose.Words bằng C#. Học
  cách thêm bóng cho hình dạng, thay đổi độ mờ, đặt độ trong suốt và xoay bóng trong
  vài phút.
draft: false
keywords:
- how to move shadow
- add shadow to shape
- how to change blur
- how to set transparency
- how to rotate shadow
language: vi
og_description: Cách di chuyển bóng đổ trên một hình dạng trong Aspose.Words bằng
  C#. Hướng dẫn này cho bạn biết cách thêm bóng đổ vào hình dạng, thay đổi độ mờ,
  đặt độ trong suốt và xoay bóng đổ.
og_title: Cách di chuyển bóng trong Aspose.Words – Hướng dẫn đầy đủ C#
tags:
- Aspose.Words
- C#
- Document Automation
title: Cách di chuyển bóng trong Aspose.Words – Hướng dẫn đầy đủ C#
url: /vi/net/programming-with-shapes/how-to-move-shadow-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách Di chuyển Bóng trong Aspose.Words – Hướng dẫn C# đầy đủ

Bạn đã bao giờ tự hỏi **cách di chuyển bóng** trên một hình dạng trong tài liệu Word mà không cần mở Word thủ công chưa? Trong công việc hàng ngày, tôi thường phải chỉnh sửa bóng của hình dạng một cách lập trình—cho dù đó là để tạo báo cáo chuyên nghiệp hay mẫu động. Tin tốt là gì? Với Aspose.Words bạn có thể thực hiện trong vài dòng code, và bạn cũng sẽ học **add shadow to shape**, **how to change blur**, **how to set transparency**, và **how to rotate shadow** trong cùng một lần.

Trong tutorial này, chúng ta sẽ đi qua một kịch bản thực tế: tải một tệp DOCX hiện có đã có một hình dạng, điều chỉnh vị trí, độ mềm mại, độ mờ và hướng của bóng, và cuối cùng lưu kết quả. Khi kết thúc, bạn sẽ có một đoạn mã có thể tái sử dụng để chèn vào bất kỳ dự án .NET nào, và bạn sẽ hiểu tại sao mỗi thuộc tính lại quan trọng.

## Yêu cầu trước – Những gì bạn cần trước khi bắt đầu

- **Aspose.Words for .NET** (phiên bản 23.12 trở lên). Bạn có thể tải nó từ NuGet bằng `Install-Package Aspose.Words`.
- Môi trường phát triển .NET 6+ (Visual Studio, VS Code, Rider—bất kỳ công cụ nào bạn thích).
- Tệp Word đầu vào (`input.docx`) đã chứa ít nhất một hình dạng (hình chữ nhật, vòng tròn, hoặc ảnh đều được).
- Kiến thức cơ bản về cú pháp C#—không cần phức tạp.

Nếu bạn thiếu bất kỳ mục nào ở trên, hãy tạm dừng và cài đặt thư viện; phần còn lại của hướng dẫn giả định rằng gói đã được tham chiếu.

## Bước 1: Tải tài liệu và lấy hình dạng mục tiêu – **How to Move Shadow** bắt đầu ở đây

Điều đầu tiên chúng ta làm là tải tài liệu nguồn và tìm vị trí hình dạng cần chỉnh sửa. Aspose.Words xem mỗi đối tượng (đoạn văn, bảng, hình dạng) như một nút trong cây, vì vậy chúng ta có thể truy vấn trực tiếp.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // 📂 Load the source DOCX that already contains a shape with a shadow.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // 🎯 Retrieve the first shape in the document.
        // The GetChild method walks the node tree; the third argument (true) means “search deep”.
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        // If no shape is found, bail out early.
        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // -------------------------------------------------
        // The next sections show **how to move shadow**,
        // **add shadow to shape**, **how to change blur**,
        // **how to set transparency**, and **how to rotate shadow**.
        // -------------------------------------------------
```

> **Tại sao điều này quan trọng:** Tải tài liệu một lần và tái sử dụng cùng một đối tượng `Document` là hiệu quả. Lệnh gọi `GetChild` an toàn vì nó trả về `null` nếu chỉ số vượt quá phạm vi, cho phép chúng ta xử lý các hình dạng thiếu một cách nhẹ nhàng.

## Bước 2: Điều chỉnh bán kính làm mờ – Nắm vững **How to Change Blur**

Bóng mềm trông chuyên nghiệp, trong khi cạnh cứng có thể cảm giác rẻ tiền. Thuộc tính `BlurRadius` kiểm soát độ mềm trong điểm (1 pt ≈ 1/72 inch). Hãy tăng nó lên 8 pt.

```csharp
        // Increase the blur radius to soften the shadow edges.
        shape.ShadowFormat.BlurRadius = 8.0; // 8 points ≈ 0.11 inches
```

> **Mẹo chuyên nghiệp:** Độ mờ mặc định là 0.5 pt. Bất kỳ giá trị nào trên 5 pt thường dễ nhận thấy, nhưng hãy cẩn thận khi tăng quá lớn—nó có thể làm cho hình dạng trông tách rời khỏi trang.

## Bước 3: Đặt độ trong suốt – Câu trả lời cho **How to Set Transparency**

Độ trong suốt quyết định mức độ trong suốt của bóng. Giá trị `0` nghĩa là hoàn toàn đục; `1` nghĩa là hoàn toàn trong suốt. Để tạo hiệu ứng nhẹ nhàng, chúng ta sẽ dùng `0.3` (30 % trong suốt).

```csharp
        // Make the shadow semi‑transparent so the shape remains visible through it.
        shape.ShadowFormat.Transparency = 0.3; // 30% transparent
```

> **Tại sao bạn có thể quan tâm:** Nếu hình dạng màu tối, bóng hoàn toàn đục có thể làm lấn át văn bản phía dưới. Điều chỉnh độ trong suốt giúp tài liệu vẫn đọc được đồng thời tạo độ sâu.

## Bước 4: Di chuyển bóng – Cốt lõi của **How to Move Shadow**

Thuộc tính `Distance` xác định khoảng cách bóng lệch so với hình dạng, đo bằng điểm. Khoảng cách lớn hơn đẩy bóng ra xa hơn, tạo hiệu ứng kịch tính hơn.

```csharp
        // Move the shadow farther from the shape for a more pronounced effect.
        shape.ShadowFormat.Distance = 4.0; // 4 points ≈ 0.055 inches
```

> **Nếu bạn cần độ lệch rất nhỏ?** Đặt `Distance` thành `0` sẽ khiến bóng nằm ngay sau hình dạng, hữu ích cho hiệu ứng khắc nổi.

## Bước 5: Xoay nguồn sáng – Giải quyết **How to Rotate Shadow**

Bóng không chỉ thẳng xuống; chúng tuân theo góc của nguồn sáng. Thuộc tính `Angle` (độ) xoay bóng quanh hình dạng. Hãy nghiêng nó 45°.

```csharp
        // Rotate the light source to change the shadow direction.
        shape.ShadowFormat.Angle = 45; // 45 degrees clockwise from the vertical axis
```

> **Thí nghiệm nhanh:** Thử `90` để có bóng phía bên phải hoặc `-30` cho bóng nghiêng sang trái. Thay đổi trực quan ngay lập tức.

## Bước 6: Lưu tài liệu – Nhìn kết quả của **Add Shadow to Shape**

Bây giờ chúng ta đã chỉnh sửa bóng, chúng ta sẽ ghi tài liệu trở lại đĩa. Bạn có thể ghi đè lên tệp gốc hoặc tạo tệp mới; ví dụ sử dụng tệp đầu ra mới.

```csharp
        // Save the modified document with the adjusted shadow.
        doc.Save(@"YOUR_DIRECTORY\output.docx");

        System.Console.WriteLine("Shadow adjustments applied and saved to output.docx");
    }
}
```

> **Kết quả mong đợi:** Mở `output.docx`. Bóng của hình dạng sẽ mềm hơn, hơi lệch, bán trong suốt và nghiêng 45°. Nếu bạn so sánh cạnh nhau với `input.docx`, sự khác biệt là rõ ràng.

### Ví dụ đầy đủ hoạt động (Sẵn sàng sao chép‑dán)

Dưới đây là toàn bộ chương trình trong một khối. Dán vào một dự án console mới, thay thế `YOUR_DIRECTORY` bằng đường dẫn thư mục thực tế, và chạy.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the source document that already contains a shape with a shadow.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // Retrieve the first shape in the document (the one we will modify).
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // 1️⃣ Change blur – soften the edges.
        shape.ShadowFormat.BlurRadius = 8.0;

        // 2️⃣ Set transparency – make it 30% see‑through.
        shape.ShadowFormat.Transparency = 0.3;

        // 3️⃣ Move the shadow – increase distance from the shape.
        shape.ShadowFormat.Distance = 4.0;

        // 4️⃣ Rotate the shadow – change light direction.
        shape.ShadowFormat.Angle = 45;

        // Save the result.
        doc.Save(@"YOUR_DIRECTORY\output.docx");
        System.Console.WriteLine("Shadow adjustments applied and saved to output.docx");
    }
}
```

## Các câu hỏi thường gặp & Trường hợp đặc biệt

### Nếu tài liệu có nhiều hình dạng thì sao?

Bạn có thể lặp qua tất cả các hình dạng:

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    // Apply the same shadow settings or customize per shape.
}
```

### Tôi có thể thêm bóng vào một hình dạng hiện chưa có bóng không?

Chắc chắn. Đối tượng `ShadowFormat` luôn tồn tại; bạn chỉ cần bật nó:

```csharp
shape.ShadowFormat.Enabled = true;
```

### Điều này có hoạt động với ảnh và SmartArt không?

Có. Bất kỳ nút nào kế thừa từ `Shape`—bao gồm ảnh, biểu đồ và SmartArt—cũng có `ShadowFormat`. Các thuộc tính giống nhau áp dụng.

### Làm sao để điều khiển màu bóng?

Sử dụng thuộc tính `Color`:

```csharp
shape.ShadowFormat.Color = System.Drawing.Color.Gray;
```

### Lo ngại về khả năng tương thích?

Aspose.Words 23.12+ hỗ trợ .NET 6, .NET Core 3.1 và .NET Framework 4.6.2+. API được trình bày ổn định trên các phiên bản này.

## Kết luận

Chúng ta vừa mới khám phá **how to move shadow** trên một hình dạng bằng Aspose.Words, và trong quá trình đó chúng tôi cũng đã trình diễn **add shadow to shape**, **how to change blur**, **how to set transparency**, và **how to rotate shadow**. Ví dụ đầy đủ, có thể chạy ngay cho phép bạn chỉnh sửa bóng của bất kỳ hình dạng nào trong vài giây, mang lại cho tài liệu của bạn vẻ ngoài chuyên nghiệp, tinh tế mà không cần mở Word.

Sẵn sàng cho bước tiếp theo? Hãy thử kết hợp các điều chỉnh bóng này với **conditional formatting**—ví dụ, chỉ áp dụng bóng sâu hơn cho tiêu đề hoặc cho biểu đồ vượt quá một kích thước nhất định. Hoặc khám phá **gradient fills** cho chính hình dạng để tạo thiết kế thực sự bắt mắt.

Nếu gặp bất kỳ vấn đề nào, hãy để lại bình luận bên dưới. Chúc lập trình vui vẻ, và mong bóng của bạn luôn rơi đúng nơi bạn muốn!

![Sơ đồ minh họa hiệu ứng di chuyển bóng trên một hình dạng – ví dụ cách di chuyển bóng](https://example.com/images/shadow-demo.png "ví dụ cách di chuyển bóng")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}