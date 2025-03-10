---
title: Làm việc với mô hình AI mở
linktitle: Làm việc với mô hình AI mở
second_title: API xử lý tài liệu Aspose.Words
description: Mở khóa tóm tắt tài liệu hiệu quả bằng Aspose.Words cho .NET với các mô hình mạnh mẽ của OpenAI. Khám phá hướng dẫn toàn diện này ngay.
weight: 10
url: /vi/net/ai-powered-document-processing/working-with-open-ai-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Làm việc với mô hình AI mở

## Giới thiệu

Trong thế giới kỹ thuật số ngày nay, nội dung là vua. Cho dù bạn là sinh viên, chuyên gia kinh doanh hay nhà văn nhiệt huyết, khả năng thao tác, tóm tắt và tạo tài liệu hiệu quả là vô giá. Đây là lúc thư viện Aspose.Words for .NET phát huy tác dụng, cho phép bạn quản lý tài liệu như một chuyên gia. Trong hướng dẫn toàn diện này, chúng ta sẽ tìm hiểu cách tận dụng Aspose.Words kết hợp với các mô hình OpenAI để tóm tắt tài liệu hiệu quả. Sẵn sàng khai phá tiềm năng quản lý tài liệu của bạn? Hãy bắt đầu thôi!

## Điều kiện tiên quyết

Trước khi bắt tay vào viết mã, bạn cần lưu ý một số điều cần thiết sau:

### Khung .NET
Đảm bảo bạn đang chạy trên phiên bản .NET framework tương thích với Aspose.Words. Nhìn chung, .NET 5.0 trở lên sẽ hoạt động hoàn hảo.

### Aspose.Words cho Thư viện .NET
 Bạn sẽ cần tải xuống và cài đặt thư viện Aspose.Words. Bạn có thể lấy nó từ[liên kết này](https://releases.aspose.com/words/net/).

### Khóa API OpenAI
Để tích hợp các mô hình ngôn ngữ của OpenAI cho mục đích tóm tắt tài liệu, bạn sẽ cần Khóa API. Bạn có thể lấy khóa bằng cách đăng ký trên nền tảng OpenAI và lấy khóa từ cài đặt tài khoản của bạn.

### IDE cho Phát triển
Thiết lập Môi trường phát triển tích hợp (IDE) như Visual Studio là lý tưởng để phát triển các ứng dụng .NET.

### Kiến thức lập trình cơ bản
Hiểu biết cơ bản về C# và lập trình hướng đối tượng sẽ giúp bạn nắm bắt các khái niệm dễ dàng hơn.

## Nhập gói

Bây giờ chúng ta đã sắp xếp mọi thứ, hãy nhập các gói của chúng ta. Mở dự án Visual Studio của bạn và thêm các thư viện cần thiết. Sau đây là cách bạn có thể thực hiện:

### Thêm gói Aspose.Words

Bạn có thể thêm gói Aspose.Words thông qua NuGet Package Manager. Đây là cách thực hiện:
- Vào Công cụ -> Trình quản lý gói NuGet -> Quản lý gói NuGet cho Giải pháp.
- Tìm kiếm "Aspose.Words" và nhấp vào Cài đặt.

### Thêm Môi trường Hệ thống

 Hãy chắc chắn bao gồm`System`không gian tên để xử lý các biến môi trường:
```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

### Thêm Aspose.Words

Sau đó, bao gồm không gian tên Aspose.Words trong tệp C# của bạn:
```csharp
using Aspose.Words;
```

### Thêm Thư viện OpenAI

Nếu bạn đang sử dụng thư viện để giao tiếp với OpenAI (như REST client), hãy đảm bảo bao gồm cả thư viện đó. Bạn có thể cần thêm nó thông qua NuGet theo cùng cách chúng tôi đã thêm Aspose.Words.

Bây giờ chúng ta đã chuẩn bị môi trường và nhập các gói cần thiết, hãy cùng phân tích từng bước trong quy trình tóm tắt tài liệu.

## Bước 1: Xác định thư mục tài liệu của bạn

Trước khi bạn có thể bắt đầu xử lý tài liệu, bạn cần thiết lập các thư mục chứa tài liệu và hiện vật của mình:

```csharp
// Thư mục tài liệu của bạn
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// Thư mục hiện vật của bạn
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```
 Điều này làm cho mã của bạn dễ quản lý hơn vì bạn có thể dễ dàng thay đổi đường dẫn nếu cần.`MyDir` là nơi lưu trữ các tài liệu đầu vào của bạn, trong khi`ArtifactsDir` là nơi bạn sẽ lưu các bản tóm tắt đã tạo.

## Bước 2: Tải tài liệu của bạn

Tiếp theo, bạn sẽ tải các tài liệu bạn muốn tóm tắt. Điều này rất đơn giản với Aspose.Words:

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```
Hãy đảm bảo rằng tên tài liệu của bạn trùng khớp với tên bạn định sử dụng, nếu không, bạn sẽ gặp lỗi!

## Bước 3: Nhận Khóa API của bạn

Bây giờ tài liệu của bạn đã được tải, đã đến lúc lấy khóa API OpenAI của bạn. Bạn sẽ lấy khóa này từ các biến môi trường để giữ an toàn:
```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```
Việc quản lý khóa API của bạn một cách an toàn là rất cần thiết để ngăn chặn những người dùng trái phép.

## Bước 4: Tạo một phiên bản mô hình OpenAI

Với khóa API đã sẵn sàng, giờ đây bạn có thể tạo một phiên bản của mô hình OpenAI. Để tóm tắt tài liệu, chúng ta sẽ sử dụng mô hình Gpt4OMini:

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```
Về cơ bản, bước này thiết lập năng lực trí tuệ cần thiết để tóm tắt tài liệu của bạn, giúp bạn có thể truy cập vào chức năng tóm tắt do AI điều khiển.

## Bước 5: Tóm tắt một tài liệu duy nhất

Trước tiên, chúng ta hãy tóm tắt tài liệu đầu tiên. Đây chính là nơi phép thuật xảy ra:

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```
 Ở đây, chúng tôi đang sử dụng`Summarize` phương pháp của mô hình.`SummaryLength.Short`tham số chỉ rõ rằng chúng ta muốn có một bản tóm tắt ngắn — hoàn hảo cho một cái nhìn tổng quan nhanh chóng!

## Bước 6: Tóm tắt nhiều tài liệu

Bạn có cảm thấy tham vọng không? Bạn có thể tóm tắt nhiều tài liệu cùng một lúc. Hãy xem nó dễ dàng như thế nào:

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```
Tính năng này đặc biệt hữu ích khi so sánh nhiều tệp. Có thể bạn đang chuẩn bị cho một cuộc họp và cần ghi chú ngắn gọn từ nhiều báo cáo dài. Đây chính là người bạn mới tuyệt vời của bạn!

## Phần kết luận

Tóm tắt tài liệu bằng Aspose.Words cho .NET và OpenAI không chỉ là một kỹ năng có lợi; mà còn rất hữu ích. Bằng cách làm theo hướng dẫn này, bạn đã biến văn bản dài, phức tạp thành bản tóm tắt ngắn gọn, giúp bạn tiết kiệm thời gian và công sức. Cho dù bạn đang đảm bảo sự rõ ràng cho khách hàng hay chuẩn bị cho bài thuyết trình quan trọng, giờ đây bạn đã có các công cụ để thực hiện hiệu quả.

Vậy, bạn còn chờ gì nữa? Hãy tự tin vào tài liệu của mình và để công nghệ thực hiện công việc nặng nhọc!

## Câu hỏi thường gặp

### Aspose.Words dành cho .NET là gì?  
Aspose.Words for .NET là một thư viện mạnh mẽ cho phép các nhà phát triển tạo, thao tác và chuyển đổi tài liệu theo cách lập trình.

### Tôi có cần khóa API cho OpenAI không?  
Có, bạn phải có khóa API OpenAI hợp lệ để truy cập vào chức năng tóm tắt bằng mô hình của họ.

### Tôi có thể tóm tắt nhiều tài liệu cùng một lúc không?  
Chắc chắn rồi! Bạn có thể tóm tắt nhiều tài liệu trong một lần gọi, lý tưởng cho các báo cáo mở rộng.

### Làm thế nào để cài đặt Aspose.Words?  
Bạn có thể cài đặt nó thông qua NuGet Package Manager trong Visual Studio bằng cách tìm kiếm "Aspose.Words".

### Có bản dùng thử miễn phí Aspose.Words không?  
 Có, bạn có thể truy cập bản dùng thử miễn phí của Aspose.Words thông qua[trang web](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
