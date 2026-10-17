---
category: general
date: 2026-04-21
description: Tạo tài liệu Word với hình chữ nhật được định dạng và có bóng. Tìm hiểu
  cách thêm bóng, chèn hình chữ nhật, đặt màu bóng và nhiều hơn nữa trong C#.
draft: false
keywords:
- create word document
- how to add shadow
- insert rectangle shape
- create rectangle in word
- set shadow color
language: vi
og_description: Tạo tài liệu Word và thêm hình chữ nhật có bóng trong C#. Tham khảo
  hướng dẫn này để dễ dàng thiết lập màu bóng, độ mờ và độ dịch chuyển.
og_title: Tạo tài liệu Word với hình chữ nhật có bóng – Từng bước
tags:
- Aspose.Words
- C#
- Document Automation
title: Tạo tài liệu Word với hình chữ nhật có bóng – Hướng dẫn đầy đủ
url: /vi/net/programming-with-shapes/create-word-document-with-shadowed-rectangle-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo Tài liệu Word với Hình chữ nhật có Bóng – Hướng dẫn đầy đủ

Bạn đã bao giờ cần **tạo tài liệu word** trông chuyên nghiệp hơn một trang văn bản đơn giản chưa? Có thể bạn đang xây dựng mẫu báo cáo hoặc tờ rơi và một hình chữ nhật đơn giản với bóng nhẹ sẽ giải quyết vấn đề. Trong hướng dẫn này, chúng ta sẽ đi qua từng bước—cách chèn hình dạng hình chữ nhật, bật bóng, và tùy chỉnh màu, độ mờ và độ dịch chuyển—tất cả bằng C# và Aspose.Words.

Chúng tôi cũng sẽ đề cập đến **cách thêm bóng** sao cho hoạt động trên Word 2016, 2019 hoặc bản Office 365 mới nhất. Khi kết thúc, bạn sẽ có một tệp *.docx* sẵn sàng lưu, hiển thị một hình chữ nhật có bóng đẹp mắt, và bạn sẽ hiểu “tại sao” mỗi thuộc tính được thiết lập.

## Yêu cầu trước

- .NET 6 (hoặc bất kỳ phiên bản .NET Framework gần đây nào)  
- Gói NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- Kiến thức cơ bản về cú pháp C#  
- Một IDE như Visual Studio (nhưng bất kỳ trình soạn thảo nào cũng được)

Không cần thư viện bổ sung nào; mọi thứ khác đều nằm trong Aspose.Words.

## Bước 1 – Khởi tạo Document và Builder (Create Word Document)

Để **tạo tài liệu word** một cách lập trình, bạn bắt đầu với lớp `Document`. `DocumentBuilder` là cây cọ vẽ của bạn; nó cho phép bạn thêm văn bản, hình dạng và các yếu tố khác.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowRectangleDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Tại sao điều này quan trọng:* Đối tượng `Document` đại diện cho toàn bộ tệp .docx. Nếu không có nó, bạn sẽ không có nơi nào để gắn hình chữ nhật hoặc bóng của nó.

## Bước 2 – Chèn hình chữ nhật (Insert Rectangle Shape)

Bây giờ chúng ta thực sự **chèn hình chữ nhật**. Phương thức `InsertShape` nhận một enum `ShapeType`, cùng với chiều rộng và chiều cao tính bằng điểm.

```csharp
        // Step 2: Insert a rectangle shape of the desired size (200x100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

*Mẹo chuyên nghiệp:* 1 điểm ≈ 1/72 inch, vì vậy 200 điểm tương đương khoảng 2.78 inch chiều rộng. Điều chỉnh các số này để phù hợp với bố cục của bạn.

## Bước 3 – Bật bóng (How to Add Shadow)

Bóng được tắt mặc định. Đặt cờ `Visible` để bật nó.

```csharp
        // Step 3: Turn on the shadow for the shape
        rectangle.ShadowFormat.Visible = true;
```

*Điều gì đang xảy ra?* Khi `Visible` là true, Word sẽ hiển thị một bóng thả dựa trên các thuộc tính khác mà bạn sẽ thiết lập tiếp theo.

## Bước 4 – Tùy chỉnh giao diện bóng (Set Shadow Color, Blur, Offsets)

Đây là nơi bạn **đặt màu bóng**, bán kính mờ, và độ dịch chuyển X/Y. Hãy thoải mái thử nghiệm—các giá trị khác nhau sẽ cho bạn một ánh sáng nhẹ, một bóng sâu, hoặc thậm chí hiệu ứng “nổi”.

```csharp
        // Step 4: Define the shadow appearance – colour, blur radius and offsets
        rectangle.ShadowFormat.Color = Color.Gray;   // shadow colour
        rectangle.ShadowFormat.Blur = 5.0;           // blur radius (points)
        rectangle.ShadowFormat.OffsetX = 4.0;        // horizontal offset (points)
        rectangle.ShadowFormat.OffsetY = 4.0;        // vertical offset (points)
```

*Tại sao lại dùng các số này?* Độ mờ 5 điểm tạo ra một cạnh mềm mại, trong khi độ dịch chuyển 4 điểm di chuyển bóng xuống‑phải, mô phỏng nguồn sáng từ góc trên‑trái. Thay đổi `Color` thành `Color.Black` để tăng độ tương phản, hoặc dùng `Color.FromArgb(128, 0, 0, 0)` cho màu đen bán trong suốt.

### Trường hợp đặc biệt & Biến thể

- **Không mờ:** Đặt `Blur = 0` để có bóng sắc nét, cạnh cứng.  
- **Dịch chuyển âm:** Sử dụng `OffsetX = -4` để đẩy bóng sang trái.  
- **Hình dạng khác:** Các thuộc tính bóng giống nhau cũng hoạt động cho vòng tròn, tam giác, hoặc các hình vẽ tự do—chỉ cần thay đổi `ShapeType` ở Bước 2.  
- **Tương thích:** Aspose.Words ghi dữ liệu bóng dưới định dạng Office Open XML, hoạt động trên Word 2010‑2021 và Office 365.

## Bước 5 – Lưu tài liệu (Create Word Document)

Cuối cùng, lưu tệp xuống đĩa. Bạn có thể chọn bất kỳ định dạng nào được hỗ trợ (`.docx`, `.pdf`, `.odt`, …) nhưng trong hướng dẫn này chúng tôi sẽ giữ định dạng Word cổ điển.

```csharp
        // Step 5: Save the document with the shaped shadow
        document.Save("ShadowRectangle.docx");
    }
}
```

Khi bạn mở **ShadowRectangle.docx** trong Microsoft Word, bạn sẽ thấy một hình chữ nhật màu xám với bóng nhẹ, mờ và dịch chuyển xuống‑phải—chính xác như chúng ta đã lập trình.

### Kết quả mong đợi

- Một tệp *.docx* một trang.  
- Một hình chữ nhật 200 pt × 100 pt được căn giữa vị trí con trỏ khi gọi `InsertShape`.  
- Một bóng màu xám xuất hiện 4 điểm sang phải và 4 điểm xuống, với độ mờ 5 điểm.

Nếu hình dạng lệch trung tâm, bạn có thể di chuyển con trỏ bằng `builder.MoveTo` trước khi chèn, hoặc điều chỉnh các thuộc tính `Left` và `Top` của hình sau khi chèn.

## Câu hỏi thường gặp & Khắc phục sự cố

**Q: Bóng không hiển thị trong Word.**  
A: Đảm bảo `ShadowFormat.Visible` là `true`. Ngoài ra, kiểm tra bạn đang sử dụng phiên bản Aspose.Words mới (tính năng bóng được thêm vào từ phiên bản 20.3).  

**Q: Tôi có thể áp dụng gradient cho bóng không?**  
A: Không thể trực tiếp qua `ShadowFormat`. Giao diện Word hỗ trợ bóng gradient, nhưng schema Open XML (mà Aspose.Words tuân theo) chỉ cho phép bóng màu đồng nhất. Bạn sẽ cần chỉnh sửa XML gốc thủ công—đây là kịch bản nâng cao hơn.  

**Q: Nếu tôi cần một hình chữ nhật trong suốt chỉ có bóng thì sao?**  
A: Đặt `rectangle.FillColor = Color.Transparent;` sau khi chèn. Bóng vẫn sẽ được hiển thị vì nó độc lập với màu nền.

## Mẹo chuyên nghiệp cho mã sản xuất

- **Tái sử dụng builder:** Nếu bạn thêm nhiều hình, hãy giữ lại cùng một thể hiện `DocumentBuilder`—tạo mới cho mỗi hình sẽ gây tốn tài nguyên không cần thiết.  
- **Lưu hàng loạt:** Lưu một lần sau khi hoàn tất mọi thay đổi; I/O thường xuyên làm chậm quá trình tạo tài liệu lớn.  
- **Xử lý lỗi:** Bao bọc toàn bộ khối trong `try / catch` và ghi log các ngoại lệ `Aspose.Words`; chúng thường chứa số dòng hữu ích nếu mẫu tài liệu bị hỏng.

## Các bước tiếp theo (Chủ đề liên quan)

- **Cách thêm bóng** vào hình ảnh hoặc hộp văn bản (sử dụng `ShadowFormat` tương tự).  
- **Chèn hình chữ nhật** vào ô bảng để tùy chỉnh kiểu ô.  
- **Tạo hình chữ nhật trong Word** bằng XML gốc của Word (cho những ai thích Open XML thô).  
- **Đặt màu bóng** một cách động dựa trên đầu vào của người dùng hoặc màu chủ đề.

Thử nghiệm với các màu sắc, bán kính mờ và độ dịch chuyển khác nhau—có thể là ánh sáng xanh nhẹ cho báo cáo doanh nghiệp, hoặc bóng đen sâu cho tờ rơi ấn tượng. Các khả năng là vô hạn, và các thay đổi mã là tối thiểu.

### Tóm tắt nhanh

- Chúng tôi **đã tạo một tài liệu word** từ đầu.  
- Chúng tôi **đã chèn một hình chữ nhật** và bật bóng cho nó.  
- Chúng tôi **đã đặt màu bóng**, độ mờ và độ dịch chuyển để đạt được giao diện chuyên nghiệp.  
- Chúng tôi đã lưu tệp, sẵn sàng phân phối.

Bây giờ bạn đã có nền tảng vững chắc để thêm yếu tố trực quan vào bất kỳ dự án tự động Word nào. Có thêm ý tưởng? Hãy để lại bình luận, và chúng ta sẽ tiếp tục trao đổi. Chúc lập trình vui vẻ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}