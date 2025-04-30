---
"description": "Tìm hiểu cách triển khai lệnh gọi lại ngắt dòng trong Aspose.Words cho .NET để cải thiện định dạng tài liệu với hướng dẫn từng bước toàn diện này."
"linktitle": "Gọi lại dấu gạch nối"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Gọi lại dấu gạch nối"
"url": "/vi/net/working-with-hyphenation/hyphenation-callback/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Gọi lại dấu gạch nối


## Giới thiệu

Xin chào! Bạn đã bao giờ thấy mình bị vướng vào sự phức tạp của việc định dạng văn bản, đặc biệt là khi xử lý các ngôn ngữ yêu cầu ngắt dòng chưa? Bạn không đơn độc. Ngắt dòng, mặc dù rất quan trọng đối với bố cục văn bản phù hợp, nhưng có thể hơi đau đầu. Nhưng đoán xem sao? Aspose.Words for .NET sẽ hỗ trợ bạn. Thư viện mạnh mẽ này cho phép bạn quản lý định dạng văn bản một cách liền mạch, bao gồm xử lý ngắt dòng thông qua cơ chế gọi lại. Bạn có tò mò không? Hãy cùng tìm hiểu sâu hơn về cách bạn có thể triển khai lệnh gọi lại ngắt dòng bằng Aspose.Words for .NET.

## Điều kiện tiên quyết

Trước khi bắt tay vào viết mã, hãy đảm bảo rằng bạn đã có mọi thứ cần thiết:

1. Aspose.Words cho .NET: Đảm bảo bạn có thư viện. Bạn có thể [tải xuống ở đây](https://releases.aspose.com/words/net/).
2. IDE: Một môi trường phát triển như Visual Studio.
3. Kiến thức cơ bản về C#: Hiểu biết về C# và .NET framework.
4. Từ điển phân cách chữ viết: Từ điển phân cách chữ viết cho các ngôn ngữ bạn dự định sử dụng.
5. Giấy phép Aspose: Giấy phép Aspose hợp lệ. Bạn có thể nhận được [giấy phép tạm thời](https://purchase.aspose.com/temporary-license/) nếu bạn không có.

## Nhập không gian tên

Trước tiên, hãy nhập các không gian tên cần thiết. Điều này đảm bảo mã của chúng ta có thể truy cập vào tất cả các lớp và phương thức cần thiết từ Aspose.Words.

```csharp
using Aspose.Words;
using System;
using System.IO;
```

## Bước 1: Đăng ký lệnh gọi lại ngắt dòng

Để bắt đầu, chúng ta cần đăng ký lệnh gọi lại ngắt dòng. Đây là nơi chúng ta yêu cầu Aspose.Words sử dụng logic ngắt dòng tùy chỉnh của chúng ta.

```csharp
try
{
    // Đăng ký gọi lại dấu gạch nối.
    Hyphenation.Callback = new CustomHyphenationCallback();
}
catch (Exception e)
{
    Console.WriteLine($"Error registering hyphenation callback: {e.Message}");
}
```

Ở đây, chúng tôi đang tạo một phiên bản của hàm gọi lại tùy chỉnh của chúng tôi và gán nó cho `Hyphenation.Callback`.

## Bước 2: Xác định Đường dẫn Tài liệu

Tiếp theo, chúng ta cần xác định thư mục lưu trữ tài liệu của mình. Điều này rất quan trọng vì chúng ta sẽ tải và lưu tài liệu từ đường dẫn này.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Thay thế `"YOUR DOCUMENT DIRECTORY"` với đường dẫn thực tế tới tài liệu của bạn.

## Bước 3: Tải tài liệu

Bây giờ, hãy tải tài liệu cần ngắt dòng.

```csharp
Document document = new Document(dataDir + "German text.docx");
```

Ở đây, chúng tôi đang tải một tài liệu văn bản tiếng Đức. Bạn có thể thay thế `"German text.docx"` bằng tên tệp tài liệu của bạn.

## Bước 4: Lưu tài liệu

Sau khi tải tài liệu, chúng tôi lưu nó vào một tệp mới, áp dụng lệnh gọi lại ngắt dòng trong quá trình này.

```csharp
document.Save(dataDir + "TreatmentByCesureWithRecall.pdf");
```

Dòng này lưu tài liệu dưới dạng PDF có áp dụng dấu gạch nối.

## Bước 5: Xử lý ngoại lệ từ điển ngắt dòng bị thiếu

Đôi khi, bạn có thể gặp phải sự cố thiếu từ điển ngắt dòng. Hãy cùng giải quyết vấn đề đó.

```csharp
catch (Exception e) when (e.Message.StartsWith("Missing hyphenation dictionary"))
{
    Console.WriteLine(e.Message);
}
finally
{
    Hyphenation.Callback = null;
}
```

Trong khối này, chúng tôi phát hiện ngoại lệ cụ thể liên quan đến việc thiếu từ điển và in ra thông báo.

## Bước 6: Triển khai lớp gọi lại ngắt dòng tùy chỉnh

Bây giờ, chúng ta hãy thực hiện `CustomHyphenationCallback` lớp xử lý yêu cầu về từ điển ngắt dòng.

```csharp
public class CustomHyphenationCallback : IHyphenationCallback
{
    public void RequestDictionary(string language)
    {
        string dictionaryFolder = MyDir;
        string dictionaryFullFileName;
        switch (language)
        {
            case "en-US":
                dictionaryFullFileName = Path.Combine(dictionaryFolder, "hyph_en_US.dic");
                break;
            case "de-CH":
                dictionaryFullFileName = Path.Combine(dictionaryFolder, "hyph_de_CH.dic");
                break;
            default:
                throw new Exception($"Missing hyphenation dictionary for {language}.");
        }
        // Đăng ký từ điển cho ngôn ngữ yêu cầu.
        Hyphenation.RegisterDictionary(language, dictionaryFullFileName);
    }
}
```

Trong lớp này, `RequestDictionary` phương pháp này được gọi bất cứ khi nào cần một từ điển ngắt dòng. Nó kiểm tra ngôn ngữ và đăng ký từ điển thích hợp.

## Phần kết luận

Và bạn đã có nó! Bạn vừa học cách triển khai lệnh gọi lại ngắt dòng trong Aspose.Words cho .NET. Bằng cách làm theo các bước này, bạn có thể đảm bảo tài liệu của mình được định dạng đẹp mắt, bất kể ngôn ngữ nào. Cho dù bạn đang xử lý tiếng Anh, tiếng Đức hay bất kỳ ngôn ngữ nào khác, phương pháp này cho phép bạn xử lý ngắt dòng một cách dễ dàng.

## Câu hỏi thường gặp

### Aspose.Words dành cho .NET là gì?
Aspose.Words for .NET là một thư viện xử lý tài liệu mạnh mẽ cho phép các nhà phát triển tạo, sửa đổi và chuyển đổi tài liệu theo cách lập trình.

### Tại sao việc ngắt dòng lại quan trọng khi định dạng tài liệu?
Ngắt dòng giúp cải thiện bố cục văn bản bằng cách ngắt các từ ở những vị trí thích hợp, đảm bảo tài liệu dễ đọc hơn và hấp dẫn hơn về mặt thị giác.

### Tôi có thể sử dụng Aspose.Words miễn phí không?
Aspose.Words cung cấp bản dùng thử miễn phí. Bạn có thể nhận được nó [đây](https://releases.aspose.com/).

### Làm thế nào để tôi có được từ điển gạch nối?
Bạn có thể tải xuống từ điển ngắt dòng từ nhiều nguồn trực tuyến khác nhau hoặc tự tạo từ điển của riêng mình nếu cần.

### Sẽ thế nào nếu thiếu từ điển ngắt dòng?
Nếu thiếu một cuốn từ điển, `RequestDictionary` phương pháp này đưa ra một ngoại lệ, bạn có thể xử lý để thông báo cho người dùng hoặc cung cấp giải pháp dự phòng.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}