---
"description": "Tìm hiểu cách chèn trường TOA mà không cần sử dụng trình tạo tài liệu trong Aspose.Words cho .NET. Làm theo hướng dẫn từng bước của chúng tôi để quản lý trích dẫn pháp lý hiệu quả."
"linktitle": "Chèn Trường TOA Không Có Trình Tạo Tài Liệu"
"second_title": "API xử lý tài liệu Aspose.Words"
"title": "Chèn Trường TOA Không Có Trình Tạo Tài Liệu"
"url": "/vi/net/working-with-fields/insert-toafield-without-document-builder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Chèn Trường TOA Không Có Trình Tạo Tài Liệu

## Giới thiệu

Việc tạo trường Bảng thẩm quyền (TOA) trong tài liệu Word có thể giống như việc ghép lại một câu đố phức tạp. Tuy nhiên, với sự trợ giúp của Aspose.Words dành cho .NET, quá trình này trở nên dễ dàng và đơn giản. Trong bài viết này, chúng tôi sẽ hướng dẫn bạn các bước chèn trường TOA mà không cần sử dụng trình tạo tài liệu, giúp bạn dễ dàng quản lý trích dẫn và tài liệu tham khảo pháp lý trong tài liệu Word của mình.

## Điều kiện tiên quyết

Trước khi đi sâu vào hướng dẫn, chúng ta hãy cùng tìm hiểu những điều cần thiết mà bạn sẽ cần:

- Aspose.Words cho .NET: Đảm bảo bạn đã cài đặt phiên bản mới nhất. Bạn có thể tải xuống từ [Trang web Aspose](https://releases.aspose.com/words/net/).
- Môi trường phát triển: Một IDE tương thích với .NET như Visual Studio.
- Kiến thức cơ bản về C#: Hiểu cú pháp và khái niệm cơ bản của C# sẽ rất hữu ích.
- Mẫu tài liệu Word: Tạo hoặc chuẩn bị một tài liệu mẫu để chèn trường TOA.

## Nhập không gian tên

Để bắt đầu, bạn sẽ cần nhập các không gian tên cần thiết từ thư viện Aspose.Words. Thiết lập này đảm bảo rằng bạn có quyền truy cập vào tất cả các lớp và phương thức cần thiết để thao tác tài liệu.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Hãy chia nhỏ quy trình thành các bước đơn giản, dễ làm theo. Chúng tôi sẽ hướng dẫn bạn qua từng giai đoạn, giải thích từng đoạn mã thực hiện chức năng gì và cách chúng đóng góp vào việc tạo trường TOA.

## Bước 1: Khởi tạo Tài liệu

Đầu tiên, bạn cần tạo một phiên bản của `Document` lớp. Đối tượng này đại diện cho tài liệu Word mà bạn đang làm việc.

```csharp
// Đường dẫn đến thư mục tài liệu.
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

Mã này khởi tạo một tài liệu Word mới. Bạn có thể nghĩ về nó như việc tạo một trang giấy trắng để thêm nội dung của mình vào.

## Bước 2: Tạo và cấu hình trường TA

Tiếp theo, chúng ta sẽ thêm trường TA (Bảng thẩm quyền). Trường này đánh dấu các mục sẽ xuất hiện trong TOA.

```csharp
Paragraph para = new Paragraph(doc);

// Chúng tôi muốn chèn các trường TA và TOA như thế này:
// { TA \c 1 \l "Giá trị 0" }
FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);
fieldTA.EntryCategory = "1";
fieldTA.LongCitation = "Value 0";

doc.FirstSection.Body.AppendChild(para);
```

Sau đây là thông tin chi tiết:
- Đoạn văn para = new Paragraph(doc);: Tạo một đoạn văn mới trong tài liệu.
- FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEEntry, false);: Thêm trường TA vào đoạn văn. các `FieldType.FieldTOAEntry` chỉ rõ đây là trường nhập TOA.
- fieldTA.EntryCategory = "1";: Đặt danh mục mục nhập. Điều này hữu ích để phân loại các loại mục nhập khác nhau.
- fieldTA.LongCitation = "Giá trị 0";: Chỉ định văn bản trích dẫn dài. Đây là văn bản sẽ xuất hiện trong TOA.
- doc.FirstSection.Body.AppendChild(para);: Thêm đoạn văn có trường TA vào phần nội dung của tài liệu.

## Bước 3: Thêm trường TOA

Bây giờ, chúng ta sẽ chèn trường TOA thực tế để biên dịch tất cả các mục TA vào một bảng.

```csharp
para = new Paragraph(doc);

FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);
fieldToa.EntryCategory = "1";
doc.FirstSection.Body.AppendChild(para);
```

Ở bước này:
- FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);: Thêm trường TOA vào đoạn văn.
- fieldToa.EntryCategory = "1";: Lọc các mục để chỉ bao gồm những mục được đánh dấu bằng danh mục "1".

## Bước 4: Cập nhật trường TOA

Sau khi chèn trường TOA, bạn cần cập nhật trường này để đảm bảo trường phản ánh các mục nhập mới nhất.

```csharp
fieldToa.Update();
```

Lệnh này làm mới trường TOA, đảm bảo rằng tất cả các mục được đánh dấu đều được hiển thị chính xác trong bảng.

## Bước 5: Lưu tài liệu

Cuối cùng, hãy lưu tài liệu của bạn với trường TOA mới được thêm vào.

```csharp
doc.Save(dataDir + "WorkingWithFields.InsertTOAFieldWithoutDocumentBuilder.docx");
```

Dòng mã này lưu tài liệu vào thư mục đã chỉ định. Hãy đảm bảo thay thế `"YOUR DOCUMENT DIRECTORY"` với đường dẫn thực tế mà bạn muốn lưu tệp của mình.

## Phần kết luận

Và thế là xong! Bạn đã thêm thành công trường TOA vào tài liệu Word mà không cần sử dụng trình tạo tài liệu. Bằng cách làm theo các bước này, bạn có thể quản lý hiệu quả các trích dẫn và tạo các bảng thẩm quyền toàn diện trong các tài liệu pháp lý của mình. Aspose.Words for .NET giúp quá trình này trở nên suôn sẻ và hiệu quả, cung cấp cho bạn các công cụ để xử lý các tác vụ tài liệu phức tạp một cách dễ dàng.

## Câu hỏi thường gặp

### Tôi có thể thêm nhiều trường TA với các danh mục khác nhau không?
Có, bạn có thể thêm nhiều trường TA với các danh mục khác nhau bằng cách thiết lập `EntryCategory` tài sản theo đó.

### Tôi có thể tùy chỉnh giao diện của TOA như thế nào?
Bạn có thể tùy chỉnh giao diện của TOA bằng cách sửa đổi các thuộc tính của trường TOA, chẳng hạn như định dạng mục nhập và nhãn danh mục.

### Có thể cập nhật trường TOA tự động được không?
Trong khi bạn có thể cập nhật thủ công trường TOA bằng cách sử dụng `Update` phương pháp, Aspose.Words hiện không hỗ trợ cập nhật tự động khi có thay đổi trong tài liệu.

### Tôi có thể thêm trường TA theo chương trình vào các phần cụ thể của tài liệu không?
Có, bạn có thể thêm trường TA vào các vị trí cụ thể bằng cách chèn chúng vào các đoạn văn hoặc phần mong muốn.

### Làm thế nào để xử lý nhiều trường TOA trong một tài liệu?
Bạn có thể quản lý nhiều trường TOA bằng cách chỉ định các trường khác nhau `EntryCategory` giá trị và đảm bảo mỗi trường TOA lọc các mục nhập dựa trên danh mục của nó.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}