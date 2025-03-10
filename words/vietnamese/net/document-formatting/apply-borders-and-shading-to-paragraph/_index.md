---
title: Áp dụng đường viền và đổ bóng cho đoạn văn trong tài liệu Word
linktitle: Áp dụng đường viền và đổ bóng cho đoạn văn trong tài liệu Word
second_title: API xử lý tài liệu Aspose.Words
description: Áp dụng đường viền và đổ bóng cho các đoạn văn trong tài liệu Word bằng Aspose.Words cho .NET. Làm theo hướng dẫn từng bước của chúng tôi để cải thiện định dạng tài liệu của bạn.
weight: 10
url: /vi/net/document-formatting/apply-borders-and-shading-to-paragraph/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Áp dụng đường viền và đổ bóng cho đoạn văn trong tài liệu Word

## Giới thiệu

Xin chào, bạn đã bao giờ tự hỏi làm thế nào để làm cho tài liệu Word của mình nổi bật với một số đường viền và đổ bóng lạ mắt chưa? Vâng, bạn đã đến đúng nơi rồi! Hôm nay, chúng ta sẽ khám phá thế giới của Aspose.Words dành cho .NET để làm cho các đoạn văn của chúng ta trở nên hấp dẫn hơn. Hãy tưởng tượng tài liệu của bạn trông bóng bẩy như tác phẩm của một nhà thiết kế chuyên nghiệp chỉ với một vài dòng mã. Sẵn sàng bắt đầu chưa? Bắt đầu thôi!

## Điều kiện tiên quyết

Trước khi xắn tay áo và bắt tay vào viết mã, hãy đảm bảo rằng chúng ta có mọi thứ cần thiết. Sau đây là danh sách kiểm tra nhanh của bạn:

-  Aspose.Words cho .NET: Bạn cần cài đặt thư viện này. Bạn có thể tải xuống từ[Trang web Aspose](https://releases.aspose.com/words/net/).
- Môi trường phát triển: Visual Studio hoặc bất kỳ IDE nào khác hỗ trợ .NET.
- Kiến thức cơ bản về C#: Chỉ đủ để hiểu và chỉnh sửa các đoạn mã.
- Giấy phép hợp lệ: Hoặc là[giấy phép tạm thời](https://purchase.aspose.com/temporary-license/) hoặc một cái đã mua từ[Đặt ra](https://purchase.aspose.com/buy).

## Nhập không gian tên

Trước khi bắt đầu code, chúng ta cần đảm bảo rằng chúng ta đã nhập các namespace cần thiết vào dự án của mình. Điều này giúp chúng ta có thể sử dụng tất cả các tính năng tuyệt vời của Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using Aspose.Words.Drawing;
using System.Drawing;
```

Bây giờ, chúng ta hãy chia nhỏ quy trình thành các bước nhỏ. Mỗi bước sẽ có tiêu đề và giải thích chi tiết. Sẵn sàng chưa? Bắt đầu thôi!

## Bước 1: Thiết lập thư mục tài liệu của bạn

Trước tiên, chúng ta cần một nơi để lưu tài liệu được định dạng đẹp mắt của mình. Hãy thiết lập đường dẫn đến thư mục tài liệu của bạn.

```csharp
// Đường dẫn đến thư mục tài liệu.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Thư mục này là nơi tài liệu cuối cùng của bạn sẽ được lưu. Thay thế`"YOUR DOCUMENT DIRECTORY"` với đường dẫn thực tế trên máy của bạn.

## Bước 2: Tạo một Tài liệu mới và DocumentBuilder

 Tiếp theo, chúng ta cần tạo một tài liệu mới và một`DocumentBuilder` đối tượng. Các`DocumentBuilder` là cây đũa thần cho phép chúng ta thao tác tài liệu.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Các`Document` đối tượng đại diện cho toàn bộ tài liệu Word của chúng tôi và`DocumentBuilder` giúp chúng tôi thêm và định dạng nội dung.

## Bước 3: Xác định đường viền đoạn văn

Bây giờ, hãy thêm một số đường viền thời trang vào đoạn văn của chúng ta. Chúng ta sẽ xác định khoảng cách từ văn bản và thiết lập các kiểu đường viền khác nhau.

```csharp
BorderCollection borders = builder.ParagraphFormat.Borders;
borders.DistanceFromText = 20;
borders[BorderType.Left].LineStyle = LineStyle.Double;
borders[BorderType.Right].LineStyle = LineStyle.Double;
borders[BorderType.Top].LineStyle = LineStyle.Double;
borders[BorderType.Bottom].LineStyle = LineStyle.Double;
```

Ở đây, chúng ta đặt khoảng cách 20 điểm giữa văn bản và đường viền. Đường viền ở tất cả các mặt (trái, phải, trên, dưới) được đặt thành đường đôi. Thật lạ mắt phải không?

## Bước 4: Áp dụng tô bóng cho đoạn văn

Đường viền rất tuyệt, nhưng hãy nâng cấp bằng cách thêm một chút đổ bóng. Chúng ta sẽ sử dụng mẫu chữ thập chéo với sự pha trộn màu sắc để làm cho đoạn văn của chúng ta nổi bật.

```csharp
Shading shading = builder.ParagraphFormat.Shading;
shading.Texture = TextureIndex.TextureDiagonalCross;
shading.BackgroundPatternColor = System.Drawing.Color.LightCoral;
shading.ForegroundPatternColor = System.Drawing.Color.LightSalmon;
```

Trong bước này, chúng tôi áp dụng họa tiết chéo chéo với màu san hô nhạt làm màu nền và màu hồng nhạt làm màu nền trước. Giống như việc bạn mặc quần áo thiết kế cho đoạn văn của mình vậy!

## Bước 5: Thêm văn bản vào đoạn văn

Một đoạn văn không có văn bản thì sao? Hãy thêm một câu mẫu để xem cách định dạng của chúng tôi như thế nào.

```csharp
builder.Write("I'm a formatted paragraph with double border and nice shading.");
```

Dòng này chèn văn bản của chúng ta vào tài liệu. Đơn giản, nhưng giờ đây nó được bao bọc trong một khung thời trang và nền bóng mờ.

## Bước 6: Lưu tài liệu

Cuối cùng, đã đến lúc lưu công việc của chúng ta. Hãy lưu tài liệu vào thư mục đã chỉ định với tên mô tả.

```csharp
doc.Save(dataDir + "DocumentFormatting.ApplyBordersAndShadingToParagraph.doc");
```

 Điều này lưu tài liệu của chúng tôi với tên`DocumentFormatting.ApplyBordersAndShadingToParagraph.doc` trong thư mục chúng tôi đã chỉ định trước đó.

## Phần kết luận

Và bạn đã có nó! Chỉ với một vài dòng mã, chúng tôi đã chuyển đổi một đoạn văn đơn giản thành một nội dung hấp dẫn về mặt thị giác. Aspose.Words cho .NET giúp bạn dễ dàng thêm định dạng trông chuyên nghiệp vào tài liệu của mình. Cho dù bạn đang chuẩn bị báo cáo, thư hay bất kỳ tài liệu nào, những thủ thuật này sẽ giúp bạn tạo ấn tượng tuyệt vời. Vì vậy, hãy tiếp tục, thử nghiệm và xem tài liệu của bạn trở nên sống động!

## Câu hỏi thường gặp

### Tôi có thể sử dụng các kiểu đường kẻ khác nhau cho mỗi đường viền không?  
 Chắc chắn rồi! Aspose.Words cho .NET cho phép bạn tùy chỉnh từng đường viền riêng lẻ. Chỉ cần đặt`LineStyle` cho từng loại đường viền như được hiển thị trong hướng dẫn.

### Có những kết cấu đổ bóng nào khác?  
 Có một số kết cấu bạn có thể sử dụng, chẳng hạn như kết cấu rắn, sọc ngang, sọc dọc, v.v. Kiểm tra[Tài liệu Aspose](https://reference.aspose.com/words/net/) để biết danh sách đầy đủ.

### Làm thế nào để tôi có thể thay đổi màu đường viền?  
 Bạn có thể thiết lập màu đường viền bằng cách sử dụng`Color` thuộc tính cho mỗi đường viền. Ví dụ,`borders[BorderType.Left].Color = Color.Red;`.

### Có thể áp dụng đường viền và đổ bóng cho một phần cụ thể của văn bản không?  
 Có, bạn có thể áp dụng đường viền và đổ bóng cho các đoạn văn bản cụ thể bằng cách sử dụng`Run` đối tượng trong`DocumentBuilder`.

### Tôi có thể tự động hóa quy trình này cho nhiều đoạn văn không?  
Chắc chắn rồi! Bạn có thể lặp lại các đoạn văn của mình và áp dụng cùng các đường viền và thiết lập đổ bóng theo chương trình.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
