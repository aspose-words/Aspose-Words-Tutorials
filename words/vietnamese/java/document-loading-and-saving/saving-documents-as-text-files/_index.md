---
date: 2025-12-24
description: Tìm hiểu cách tạo tệp văn bản thuần từ tài liệu Word bằng Aspose.Words
  cho Java. Hướng dẫn này chỉ ra cách chuyển đổi Word sang txt, sử dụng thụt lề bằng
  tab và lưu Word dưới dạng txt.
linktitle: Saving Documents as Text Files
second_title: Aspose.Words Java Document Processing API
title: Cách tạo tệp văn bản thuần với Aspose.Words cho Java
url: /vi/java/document-loading-and-saving/saving-documents-as-text-files/
weight: 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo tệp văn bản thuần với Aspose.Words cho Java

## Giới thiệu về việc lưu tài liệu dưới dạng tệp văn bản trong Aspose.Words cho Java

Trong hướng dẫn này, bạn sẽ học **cách tạo tệp văn bản thuần** từ một tài liệu Word bằng thư viện Aspose.Words cho Java. Dù bạn cần **chuyển đổi word sang txt**, tự động tạo báo cáo, hay chỉ đơn giản là trích xuất văn bản thô để xử lý tiếp, hướng dẫn này sẽ dẫn bạn qua toàn bộ quy trình—từ việc tạo tài liệu đến tinh chỉnh các tùy chọn lưu như **sử dụng thụt lề bằng tab** hoặc thêm dấu bidi. Hãy bắt đầu nào!

## Trả lời nhanh
- **Lớp chính để tạo tài liệu là gì?** `Document` từ Aspose.Words.  
- **Tùy chọn nào thêm dấu bidi cho các ngôn ngữ từ phải sang trái?** `TxtSaveOptions.setAddBidiMarks(true)`.  
- **Làm sao để thụt lề các mục danh sách bằng tab?** Đặt `ListIndentation.Character` thành `'\t'`.  
- **Có cần giấy phép cho việc phát triển không?** Bản dùng thử miễn phí đủ cho việc thử nghiệm; cần giấy phép cho môi trường sản xuất.  
- **Có thể lưu tệp với tên và đường dẫn tùy chỉnh không?** Có — chỉ cần truyền đường dẫn đầy đủ vào `doc.save()`.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn bạn đã chuẩn bị các yêu cầu sau:

- Java Development Kit (JDK) đã được cài đặt trên hệ thống.  
- Thư viện Aspose.Words cho Java đã được tích hợp vào dự án. Bạn có thể tải về từ [đây](https://releases.aspose.com/words/java/).  
- Kiến thức cơ bản về lập trình Java.

## Bước 1: Tạo một Document

Để **lưu word dưới dạng txt**, trước tiên chúng ta cần một thể hiện `Document`. Dưới đây là một đoạn mã Java đơn giản tạo tài liệu và ghi một vài dòng văn bản đa ngôn ngữ:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

Trong đoạn mã này, chúng ta tạo một tài liệu mới, thêm văn bản tiếng Anh, tiếng Do Thái và tiếng Ả Rập, đồng thời bật định dạng từ phải sang trái cho đoạn văn tiếng Do Thái.

## Bước 2: Định nghĩa tùy chọn lưu văn bản

Tiếp theo, chúng ta cấu hình cách tài liệu sẽ được lưu dưới dạng tệp văn bản thuần. Aspose.Words cung cấp lớp `TxtSaveOptions`, cho phép bạn kiểm soát mọi thứ từ dấu bidi đến thụt lề danh sách.

### Ví dụ 1: Thêm dấu Bidi (cách lưu txt với hỗ trợ RTL đúng)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

Đặt `AddBidiMarks` thành `true` sẽ đảm bảo các ký tự từ phải sang trái được biểu diễn chính xác trong **tệp văn bản thuần** kết quả.

### Ví dụ 2: Sử dụng ký tự Tab cho thụt lề danh sách (sử dụng thụt lề bằng tab)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Ở đây chúng ta yêu cầu Aspose.Words chèn một ký tự tab (`'\t'`) trước mỗi mức độ danh sách, giúp đầu ra văn bản dễ đọc hơn.

## Bước 3: Lưu Document dưới dạng Text

Bây giờ các tùy chọn lưu đã sẵn sàng, bạn có thể ghi tài liệu thành **tệp văn bản thuần**:

```java
doc.save("output.txt", saveOptions);
```

Thay `"output.txt"` bằng đường dẫn đầy đủ nơi bạn muốn lưu tệp.

## Mã nguồn hoàn chỉnh để lưu tài liệu dưới dạng tệp văn bản trong Aspose.Words cho Java

```java
    public void addBidiMarks() throws Exception
    {        
		Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.writeln("Hello world!");
        builder.getParagraphFormat().setBidi(true);
        builder.writeln("שלום עולם!");
        builder.writeln("مرحبا بالعالم!");
        TxtSaveOptions saveOptions = new TxtSaveOptions(); { saveOptions.setAddBidiMarks(true); }
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
    }
    @Test
    public void useTabCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Create a list with three levels of indentation.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(1);
        saveOptions.getListIndentation().setCharacter('\t');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseTabCharacterPerLevelForListIndentation.txt", saveOptions);
    }
    @Test
    public void useSpaceCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Create a list with three levels of indentation.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(3);
        saveOptions.getListIndentation().setCharacter(' ');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
	}
```

## Các vấn đề thường gặp và giải pháp

| Vấn đề | Giải pháp |
|-------|----------|
| **Các ký tự bidi hiển thị thành văn bản rối** | Đảm bảo `setAddBidiMarks(true)` được bật và tệp đầu ra được mở bằng mã hoá UTF‑8. |
| **Thụt lề danh sách hiển thị không đúng** | Kiểm tra `ListIndentation.Count` và `Character` đã được đặt đúng giá trị (tab `'\t'` hoặc space `' '` ). |
| **Tệp không được tạo** | Kiểm tra đường dẫn thư mục tồn tại và ứng dụng có quyền ghi. |

## Câu hỏi thường gặp

### Làm thế nào để tôi thêm dấu bidi vào đầu ra văn bản?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Tôi có thể tùy chỉnh ký tự thụt lề danh sách không?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Aspose.Words cho Java có phù hợp để xử lý văn bản đa ngôn ngữ không?

Có, Aspose.Words cho Java hỗ trợ nhiều ngôn ngữ và bộ mã ký tự, rất thích hợp để trích xuất và lưu nội dung đa ngôn ngữ dưới dạng văn bản thuần.

### Làm sao tôi có thể truy cập thêm tài liệu và tài nguyên cho Aspose.Words cho Java?

Bạn có thể tìm thấy tài liệu và tài nguyên đầy đủ trên trang Tài liệu Aspose.Words cho Java: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

### Tôi có thể tải Aspose.Words cho Java ở đâu?

Bạn có thể tải thư viện từ trang chính thức: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/).

### Nếu tôi cần **chuyển đổi word sang txt** trong quy trình batch thì sao?

Hãy bọc đoạn mã trên trong một vòng lặp để tải mỗi tệp `.docx`, áp dụng cùng một `TxtSaveOptions`, và lưu mỗi tệp dưới dạng `.txt`. Đảm bảo giải phóng tài nguyên bằng cách hủy các đối tượng `Document` sau mỗi lần lặp.

### API có hỗ trợ lưu trực tiếp vào stream thay vì tệp không?

Có, bạn có thể truyền một `OutputStream` vào `doc.save(outputStream, saveOptions)` để xử lý trong bộ nhớ hoặc khi tích hợp với dịch vụ web.

---

**Cập nhật lần cuối:** 2025-12-24  
**Kiểm thử với:** Aspose.Words cho Java 24.12 (phiên bản mới nhất)  
**Tác giả:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}