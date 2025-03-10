---
title: Lưu tài liệu dưới dạng tệp văn bản trong Aspose.Words cho Java
linktitle: Lưu tài liệu dưới dạng tệp văn bản
second_title: API xử lý tài liệu Java Aspose.Words
description: Tìm hiểu cách lưu tài liệu dưới dạng tệp văn bản trong Aspose.Words cho Java. Làm theo hướng dẫn từng bước của chúng tôi với các ví dụ về mã Java.
weight: 24
url: /vi/java/document-loading-and-saving/saving-documents-as-text-files/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lưu tài liệu dưới dạng tệp văn bản trong Aspose.Words cho Java


## Giới thiệu về Lưu tài liệu dưới dạng tệp văn bản trong Aspose.Words cho Java

Trong hướng dẫn này, chúng ta sẽ khám phá cách lưu tài liệu dưới dạng tệp văn bản bằng thư viện Aspose.Words for Java. Aspose.Words là một API Java mạnh mẽ để làm việc với các tài liệu Word và cung cấp nhiều tùy chọn để lưu tài liệu ở nhiều định dạng khác nhau, bao gồm cả văn bản thuần túy. Chúng tôi sẽ trình bày các bước để thực hiện điều này và cung cấp mã Java mẫu trong suốt quá trình.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn đã đáp ứng đủ các điều kiện tiên quyết sau:

- Bộ công cụ phát triển Java (JDK) được cài đặt trên hệ thống của bạn.
-  Aspose.Words cho thư viện Java được tích hợp vào dự án của bạn. Bạn có thể tải xuống từ[đây](https://releases.aspose.com/words/java/).
- Kiến thức cơ bản về lập trình Java.

## Bước 1: Tạo một tài liệu

Để lưu tài liệu dưới dạng tệp văn bản, trước tiên chúng ta cần tạo tài liệu bằng Aspose.Words. Sau đây là đoạn mã Java đơn giản để tạo tài liệu có một số nội dung:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

Trong đoạn mã này, chúng ta tạo một tài liệu mới và thêm một số văn bản vào đó, bao gồm văn bản bằng nhiều ngôn ngữ khác nhau.

## Bước 2: Xác định tùy chọn lưu văn bản

Tiếp theo, chúng ta cần xác định các tùy chọn lưu văn bản để chỉ định cách tài liệu sẽ được lưu dưới dạng tệp văn bản. Chúng ta có thể định cấu hình nhiều thiết lập khác nhau như thêm dấu bidi, thụt lề danh sách, v.v. Hãy xem hai ví dụ:

### Ví dụ 1: Thêm dấu Bidi

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

 Trong ví dụ này, chúng tôi tạo ra một`TxtSaveOptions` đối tượng và thiết lập`AddBidiMarks`tài sản để`true` để đưa dấu bidi vào đầu ra văn bản.

### Ví dụ 2: Sử dụng ký tự Tab để thụt lề danh sách

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Tại đây, chúng tôi cấu hình các tùy chọn lưu để sử dụng ký tự tab cho việc thụt lề danh sách với số lượng là 1.

## Bước 3: Lưu tài liệu dưới dạng văn bản

Bây giờ chúng ta đã định nghĩa các tùy chọn lưu văn bản, chúng ta có thể lưu tài liệu dưới dạng tệp văn bản. Mã sau đây minh họa cách thực hiện việc này:

```java
doc.save("output.txt", saveOptions);
```

 Thay thế`"output.txt"` với đường dẫn tệp mong muốn mà bạn muốn lưu tệp văn bản.

## Mã nguồn đầy đủ để lưu tài liệu dưới dạng tệp văn bản trong Aspose.Words cho Java

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
        // Tạo một danh sách có ba mức thụt lề.
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
        // Tạo một danh sách có ba mức thụt lề.
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

## Phần kết luận

Trong hướng dẫn này, chúng ta đã học cách lưu tài liệu dưới dạng tệp văn bản trong Aspose.Words for Java. Chúng tôi đã trình bày các bước để tạo tài liệu, xác định tùy chọn lưu văn bản và lưu tài liệu ở định dạng văn bản. Aspose.Words cung cấp tính linh hoạt cao khi lưu tài liệu, cho phép bạn tùy chỉnh đầu ra theo yêu cầu cụ thể của mình.

## Câu hỏi thường gặp

### Làm thế nào để thêm dấu bidi vào đầu ra văn bản?

 Để thêm dấu bidi vào đầu ra văn bản, hãy đặt`AddBidiMarks` tài sản của`TxtSaveOptions` ĐẾN`true`. Ví dụ:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Tôi có thể tùy chỉnh ký tự thụt lề danh sách không?

 Có, bạn có thể tùy chỉnh ký tự thụt lề danh sách bằng cách cấu hình`ListIndentation` tài sản của`TxtSaveOptions`. Ví dụ, để sử dụng ký tự tab để thụt lề danh sách, bạn có thể thực hiện như sau:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Aspose.Words for Java có phù hợp để xử lý văn bản đa ngôn ngữ không?

Có, Aspose.Words for Java phù hợp để xử lý văn bản đa ngôn ngữ. Nó hỗ trợ nhiều ngôn ngữ và mã hóa ký tự, khiến nó trở thành lựa chọn linh hoạt để làm việc với các tài liệu bằng nhiều ngôn ngữ khác nhau.

### Làm thế nào tôi có thể truy cập thêm tài liệu và tài nguyên cho Aspose.Words for Java?

 Bạn có thể tìm thấy tài liệu và nguồn tài nguyên toàn diện cho Aspose.Words for Java trên trang web tài liệu Aspose:[Tài liệu Aspose.Words cho Java](https://reference.aspose.com/words/java/).

### Tôi có thể tải Aspose.Words cho Java ở đâu?

 Bạn có thể tải xuống thư viện Aspose.Words cho Java từ trang web Aspose:[Tải xuống Aspose.Words cho Java](https://releases.aspose.com/words/java/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
