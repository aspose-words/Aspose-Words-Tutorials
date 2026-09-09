---
category: general
date: 2026-02-10
description: Thêm hiệu ứng bóng cho một hình dạng trong Word bằng C#. Tìm hiểu cách
  thay đổi màu bóng, đặt độ trong suốt và áp dụng bóng cho hình dạng chỉ trong vài
  bước.
draft: false
keywords:
- add shadow effect
- change shadow color
- how to set transparency
- add shape shadow
- apply shadow color
language: vi
og_description: Thêm hiệu ứng đổ bóng cho một hình dạng trong Word bằng C#. Tìm hiểu
  cách thay đổi màu bóng, đặt độ trong suốt và áp dụng bóng cho hình dạng chỉ trong
  vài bước.
og_title: Thêm Hiệu Ứng Bóng Đổ cho Các Hình Dạng Word – Hướng Dẫn C# Đầy Đủ
tags:
- Aspose.Words
- C#
- Document Automation
title: Thêm Hiệu Ứng Bóng Đổ cho Các Hình Dạng Word – Hướng Dẫn C# Toàn Diện
url: /vi/net/programming-with-shapes/add-shadow-effect-to-word-shapes-complete-c-guide/
---

, plus a handful of tips you’ll wish you’d known earlier."

Translate.

Continue.

List of coverage.

Translate table.

Blockquote.

All.

Let's craft.

Be careful to keep markdown formatting.

Proceed.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Thêm Hiệu Ứng Bóng Đổ cho Các Hình Dạng Word – Hướng Dẫn C# Đầy Đủ

Bạn đã bao giờ cần **thêm hiệu ứng bóng đổ** cho một hình dạng trong Word nhưng không biết bắt đầu từ đâu? Bạn không phải là người duy nhất—các nhà phát triển thường hỏi: “Làm sao để một hình dạng trông có chiều sâu hơn một chút?” Tin tốt là chỉ với vài dòng C# bạn có thể thay đổi màu bóng, đặt độ trong suốt và tinh chỉnh ngoại hình của bất kỳ hình dạng nào. Trong tutorial này, chúng ta sẽ đi qua một ví dụ đầy đủ, có thể chạy ngay, thực hiện đúng những gì trên, cùng với một loạt các mẹo bạn sẽ muốn biết từ sớm.

Chúng ta sẽ đề cập tới:

* Tải một tệp DOCX đã chứa sẵn một hình dạng.  
* Tìm kiếm hình dạng (ngay cả khi nó nằm trong một nhóm).  
* Áp dụng bóng đổ—khoảng cách, độ mờ, màu và độ trong suốt.  
* Kiểm chứng kết quả bằng cách lưu tài liệu.  

Không cần tài liệu bên ngoài; mọi thứ bạn cần đều có ở đây. Yêu cầu duy nhất là có tham chiếu tới **Aspose.Words for .NET** (hoặc bất kỳ thư viện tương thích nào cung cấp `Shape.ShadowFormat`). Nếu bạn dùng NuGet, chỉ cần chạy `Install-Package Aspose.Words`. Sẵn sàng chưa? Hãy bắt đầu.

---

## Prerequisites

| Requirement | Why it matters |
|-------------|----------------|
| .NET 6.0 hoặc mới hơn | API hiện đại, hiệu năng tốt hơn |
| Aspose.Words for .NET (hoặc tương đương) | Cung cấp các lớp `Document`, `Shape` và `ShadowFormat` |
| Một tệp DOCX (`input.docx`) chứa ít nhất một hình dạng | Tutorial sẽ thao tác trên một hình dạng hiện có; bạn có thể tạo một hình dạng trong Word thủ công nếu cần |

> **Pro tip:** Nếu chưa có sẵn hình dạng, mở Word, chèn một hình chữ nhật đơn giản, lưu tệp dưới tên `input.docx` và đặt nó vào thư mục `Resources` của dự án.

---

## Step 1 – Load the Word Document and Locate the Shape {#add-shadow-effect-step1}

First thing’s first: we need a `Document` object that points at our source file. Then we’ll fetch the first shape using a recursive search so it works even when the shape lives inside a group.

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Step 1: Load the Word document that contains a shape
        Document doc = new Document("Resources/input.docx");

        // Step 2: Retrieve the first shape in the document (searches recursively)
        Shape targetShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (targetShape == null)
        {
            Console.WriteLine("No shape found in the document.");
            return;
        }

        // Continue with shadow settings...
```

**Why we do this:**  
* `Document` là điểm vào cho bất kỳ tệp Word nào.  
* `GetChild(NodeType.Shape, 0, true)` duyệt toàn bộ cây node, đảm bảo không bỏ sót các hình dạng lồng nhau.  
* Kiểm tra null ngăn ngừa `NullReferenceException` nếu tệp không có hình dạng—một trường hợp góc mà nhiều người mới bắt đầu thường bỏ qua.

---

## Step 2 – Set the Shadow Distance and Blur {#add-shadow-effect-step2}

A shadow isn’t just a colour; its offset and softness matter just as much. Let’s push the shadow a few points away and give it a subtle blur.

```csharp
        // Step 3: Set how far the shadow is offset from the shape
        targetShape.ShadowFormat.Distance = 4.0;   // 4 points offset

        // Step 4: Define the softness of the shadow edges
        targetShape.ShadowFormat.BlurRadius = 2.0; // 2 points blur
```

**Explanation:**  
* **Distance** kiểm soát độ dịch chuyển X/Y. Giá trị `4.0` di chuyển bóng xuống và sang phải, mô phỏng nguồn sáng từ góc trên‑trái.  
* **BlurRadius** quyết định độ mờ của cạnh. Số thấp giữ bóng sắc nét; số cao làm bóng trông như ánh sáng mềm.

Nếu bạn cần hướng ánh sáng khác, cũng có thể điều chỉnh `ShadowFormat.Angle` (mặc định là 45°).  

---

## Step 3 – Change Shadow Color and Set Transparency {#add-shadow-effect-step3}

Now for the fun part—changing the colour and making the shadow partially see‑through. This is where the secondary keywords **change shadow color** and **how to set transparency** come into play.

```csharp
        // Step 5: Choose a colour for the shadow
        targetShape.ShadowFormat.Color = Color.DarkGray; // Change shadow color here

        // Step 6: Make the shadow partially transparent (30 % transparent)
        targetShape.ShadowFormat.Transparency = 0.3; // Value between 0 (opaque) and 1 (fully transparent)
```

**Why it matters:**  
* `Color.DarkGray` là màu mặc định an toàn, hoạt động tốt trên cả nền sáng và tối. Bạn có thể thay thế bằng `Color.FromArgb(255, 0, 0, 0)` cho màu đen thuần hoặc bất kỳ giá trị ARGB tùy chỉnh nào.  
* Đặt `Transparency` thành `0.3` tạo hiệu ứng trong suốt 30 %—đủ để gợi lên độ sâu mà không che khuất hình dạng phía dưới.  

**Edge case:** Một số phiên bản Word cũ bỏ qua độ trong suốt trên một số loại hình dạng (ví dụ, WordArt). Nếu bạn thấy bóng vẫn hoàn toàn không trong suốt, hãy thử chuyển hình dạng sang dạng ảnh trước.

---

## Step 4 – Save and Verify the Result {#add-shadow-effect-step4}

After tweaking the shadow, we write the document back to disk. Opening the file in Word should reveal a subtle, coloured, semi‑transparent shadow around the shape.

```csharp
        // Step 7: Save the modified document
        doc.Save("Resources/output_with_shadow.docx");
        Console.WriteLine("Shadow effect applied successfully. Check output_with_shadow.docx.");
    }
}
```

**Verification checklist:**

1. Mở `output_with_shadow.docx` trong Microsoft Word.  
2. Nhấp vào hình dạng → Format → Shape Effects → Shadow.  
3. Bạn sẽ thấy một bóng màu xám đậm, dịch chuyển khoảng ~4 pt, có độ mờ và trong suốt 30 %.

Nếu có gì không đúng, hãy kiểm tra lại các thuộc tính của `ShadowFormat`—đặc biệt là `Distance` và `Transparency`.  

---

## Common Variations and What‑If Scenarios {#add-shadow-effect-variations}

### Adding a Shadow to Multiple Shapes

If you need to **add shape shadow** to every shape in a document, replace the single‑shape fetch with a loop:

```csharp
        NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
        foreach (Shape shp in shapes)
        {
            shp.ShadowFormat.Distance = 5.0;
            shp.ShadowFormat.BlurRadius = 3.0;
            shp.ShadowFormat.Color = Color.Black;
            shp.ShadowFormat.Transparency = 0.4;
        }
```

### Using a Custom Colour with Alpha

Sometimes you want the shadow colour itself to be semi‑transparent. Combine `Color.FromArgb` with `Transparency` for layered effect:

```csharp
        // Semi‑transparent blue shadow
        targetShape.ShadowFormat.Color = Color.FromArgb(180, 0, 0, 255); // 180/255 ≈ 70% opacity
        targetShape.ShadowFormat.Transparency = 0.2; // Additional 20% transparency
```

### Handling Shapes Inside a Group

Grouped shapes are stored as a `GroupShape` node. The recursive search we used (`true` flag) already dives into groups, but if you need to treat the group as a single entity, cast to `GroupShape` and iterate its `ChildNodes`.

```csharp
        GroupShape group = targetShape.ParentNode as GroupShape;
        if (group != null)
        {
            foreach (Shape inner in group.GetChildNodes(NodeType.Shape, true))
            {
                // Apply same shadow settings to each inner shape
                inner.ShadowFormat = targetShape.ShadowFormat.Clone();
            }
        }
```

---

## Pro Tips & Pitfalls {#add-shadow-effect-tips}

* **Pro tip:** Khi thử nghiệm, hãy đặt `ShadowFormat.Visible = true` một cách rõ ràng. Một số API ẩn bóng cho đến khi thuộc tính nào đó thay đổi.  
* **Watch out for:** Cài đặt “No Outline” của Word có thể khiến bóng trông tách rời. Đảm bảo kiểu đường viền của hình dạng được hiển thị nếu bạn muốn bóng bổ trợ cho nó.  
* **Performance note:** Cập nhật hàng ngàn hình dạng trong một tài liệu lớn có thể chậm. Hãy thực hiện thay đổi theo batch và gọi `doc.UpdatePageLayout()` một lần ở cuối.  
* **Compatibility:** Aspose.Words 23.10+ hỗ trợ đầy đủ các thuộc tính bóng cho DOCX, nhưng các phiên bản cũ hơn có thể bỏ qua `BlurRadius`. Luôn kiểm tra với phiên bản thư viện bạn đang phát hành.

---

## Full Working Example {#add-shadow-effect-complete}

Below is the complete, copy‑and‑paste‑ready program. It includes all `using` directives, error handling, and comments.

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the document that already contains a shape.
        Document doc = new Document("Resources/input.docx");

        // Retrieve the first shape (recursively searches groups).
        Shape targetShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (targetShape == null)
        {
            Console.WriteLine("No shape found in the document.");
            return;
        }

        // Apply shadow distance and blur.
        targetShape.ShadowFormat.Distance = 4.0;      // Offset from shape
        targetShape.ShadowFormat.BlurRadius = 2.0;   // Soft edges

        // Change shadow color and set transparency.
        targetShape.ShadowFormat.Color = Color.DarkGray; // Change shadow color
        targetShape.ShadowFormat.Transparency = 0.3;     // How to set transparency (30%)

        // Save the modified document.
        doc.Save("Resources/output_with_shadow.docx");
        Console.WriteLine("Shadow effect applied successfully. Check output_with_shadow.docx.");
    }
}
```

Running this program will produce `output_with_shadow.docx` with the **add shadow effect** you asked for. Open the file, and you’ll see a nicely blurred, dark‑gray shadow that’s 30 % transparent—exactly the look you’d expect from a professional presentation.

---

## Conclusion

We’ve just demonstrated how to **add shadow effect** to a Word shape using C#. By loading the document, locating the shape, tweaking `ShadowFormat` properties, and saving the file, you gain full control over **change shadow color**, **how to set transparency**, and **add shape shadow** in a matter of minutes.  

Next up, you might want to **apply shadow color** conditionally—perhaps darker shadows for larger shapes or different colours based on user input. Or explore other visual enhancements like glow, reflection, or 3‑D bevels. The same `ShadowFormat` pattern works across those features, so you’re well‑equipped to extend this tutorial further.

Got questions or run into a quirky edge case? Drop a comment below, and let’s troubleshoot together. Happy coding, and may your documents always have that extra pop of depth!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}