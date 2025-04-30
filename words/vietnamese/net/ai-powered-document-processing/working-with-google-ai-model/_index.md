---
"description": "Nâng cao khả năng xử lý tài liệu của bạn với Aspose.Words dành cho .NET và Google AI để tạo bản tóm tắt ngắn gọn một cách dễ dàng."
"linktitle": "Làm việc với mô hình AI của Google"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Làm việc với mô hình AI của Google"
"url": "/vi/net/ai-powered-document-processing/working-with-google-ai-model/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Làm việc với mô hình AI của Google

## Giới thiệu

Trong bài viết này, chúng ta sẽ khám phá cách tóm tắt tài liệu bằng Aspose.Words và các mô hình AI của Google từng bước. Cho dù bạn muốn cô đọng một báo cáo dài hay trích xuất thông tin chi tiết từ nhiều nguồn, chúng tôi đều có thể giúp bạn.

## Điều kiện tiên quyết

Trước khi đi sâu vào phần thực hành, hãy đảm bảo rằng bạn đã sẵn sàng để thành công. Sau đây là những gì bạn cần:

1. Kiến thức cơ bản về C# và .NET: Sự quen thuộc với các khái niệm lập trình sẽ giúp bạn nắm bắt các ví dụ tốt hơn.
   
2. Aspose.Words cho Thư viện .NET: Thư viện mạnh mẽ này cho phép bạn tạo và thao tác các tài liệu Word một cách liền mạch. Bạn có thể [tải xuống ở đây](https://releases.aspose.com/words/net/).

3. Khóa API cho Mô hình AI của Google: Để sử dụng các mô hình AI, bạn cần có khóa API để xác thực. Lưu trữ khóa này một cách an toàn trong các biến môi trường của bạn.

4. Môi trường phát triển: Đảm bảo rằng bạn đã thiết lập môi trường .NET đang hoạt động (Visual Studio hoặc bất kỳ IDE nào khác).

5. Tài liệu mẫu: Bạn sẽ cần các tài liệu Word mẫu (ví dụ: "Big document.docx", "Document.docx") để kiểm tra bản tóm tắt.

Bây giờ chúng ta đã nắm được những kiến thức cơ bản, hãy cùng tìm hiểu sâu hơn về mã nhé!

## Nhập gói

Để làm việc với Aspose.Words và tích hợp các mô hình Google AI, bạn cần nhập các không gian tên cần thiết. Sau đây là cách bạn có thể thực hiện:

```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

Bây giờ bạn đã nhập các gói cần thiết, chúng ta hãy cùng tìm hiểu quy trình tóm tắt tài liệu theo từng bước.

## Bước 1: Thiết lập thư mục tài liệu của bạn

Trước khi có thể xử lý tài liệu, chúng ta cần chỉ định nơi lưu trữ các tệp của mình. Bước này rất quan trọng để đảm bảo Aspose.Words có thể truy cập vào các tài liệu.

```csharp
// Thư mục tài liệu của bạn
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// Thư mục ArtifactsDir của bạn
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

Thay thế `"YOUR_DOCUMENT_DIRECTORY"` Và `"YOUR_ARTIFACTS_DIRECTORY"` với các đường dẫn thực tế trên hệ thống của bạn nơi tài liệu của bạn được lưu trữ. Điều này sẽ đóng vai trò là đường cơ sở để đọc và lưu tài liệu.

## Bước 2: Tải tài liệu

Tiếp theo, chúng ta cần tải các tài liệu mà chúng ta muốn tóm tắt. Trong trường hợp này, bạn sẽ tải hai tài liệu mà chúng ta đã chỉ định trước đó.

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

Các `Document` lớp từ Aspose.Words cho phép bạn tải các tệp Word vào bộ nhớ. Đảm bảo rằng tên tệp khớp với các tài liệu thực tế trong thư mục của bạn, nếu không bạn sẽ gặp lỗi không tìm thấy tệp!

## Bước 3: Lấy khóa API

Để sử dụng mô hình AI, bạn sẽ cần lấy Khóa API của mình. Khóa này đóng vai trò là thẻ truy cập vào các dịch vụ AI của Google.

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```

Dòng mã này sẽ lấy khóa API mà bạn đã lưu trong các biến môi trường của mình. Tốt nhất là bạn nên giữ thông tin nhạy cảm như khóa API ra khỏi mã của mình vì lý do bảo mật.

## Bước 4: Tạo một phiên bản mô hình AI

Bây giờ, đã đến lúc tạo một phiên bản của mô hình AI. Tại đây, bạn có thể chọn mô hình nào để sử dụng—trong ví dụ này, chúng tôi chọn mô hình GPT-4 Mini.

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

Dòng này thiết lập mô hình AI mà bạn sẽ sử dụng để tóm tắt tài liệu. Hãy chắc chắn tham khảo [tài liệu](https://reference.aspose.com/words/net/) để biết thông tin chi tiết về các mẫu khác nhau và khả năng của chúng.

## Bước 5: Tóm tắt một tài liệu duy nhất

Chúng ta hãy tập trung vào việc tóm tắt tài liệu đầu tiên. Chúng ta có thể chọn tóm tắt ngắn gọn ở đây.

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

Trong bước này, chúng tôi sử dụng `Summarize` phương pháp từ phiên bản mô hình AI để có được bản tóm tắt của tài liệu đầu tiên. Chiều dài tóm tắt được đặt thành ngắn, nhưng bạn có thể tùy chỉnh tùy theo nhu cầu của mình. Cuối cùng, tài liệu tóm tắt được lưu vào thư mục hiện vật của bạn.

## Bước 6: Tóm tắt nhiều tài liệu

Bạn muốn tóm tắt nhiều tài liệu cùng lúc? Aspose.Words cũng giúp bạn làm điều này dễ dàng!

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

Ở đây, chúng tôi đang gọi `Summarize` phương pháp một lần nữa, nhưng lần này với một mảng các tài liệu. Điều này sẽ cung cấp cho bạn một bản tóm tắt dài tóm tắt bản chất của cả hai tệp. Giống như trước đây, kết quả được lưu trong thư mục hiện vật đã chỉ định.

## Phần kết luận

Và bạn đã có nó! Bạn đã thiết lập thành công một môi trường để tóm tắt tài liệu bằng Aspose.Words cho .NET và các mô hình AI của Google. Từ việc tải tài liệu đến tạo bản tóm tắt ngắn gọn, các bước này cung cấp một phương pháp tiếp cận hợp lý để quản lý khối lượng lớn văn bản một cách hiệu quả.

## Câu hỏi thường gặp

### Aspose.Words là gì?
Aspose.Words là một thư viện mạnh mẽ để tạo, chỉnh sửa và chuyển đổi tài liệu Word bằng .NET.

### Làm thế nào để tôi có được khóa API cho Google AI?
Bạn thường có thể lấy khóa API bằng cách đăng ký Google Cloud và kích hoạt các dịch vụ API cần thiết.

### Tôi có thể tóm tắt nhiều tài liệu cùng một lúc không?
Có! Như đã trình bày, bạn có thể truyền một mảng tài liệu vào phương thức tóm tắt.

### Tôi có thể tạo những loại tóm tắt nào?
Bạn có thể chọn tóm tắt ngắn, trung bình và dài tùy theo nhu cầu của mình.

### Tôi có thể tìm thêm tài nguyên Aspose.Words ở đâu?
Kiểm tra các [tài liệu](https://reference.aspose.com/words/net/) để biết thêm ví dụ và hướng dẫn.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}