---
date: 2025-12-20
description: Tìm hiểu cách sắp xếp tệp theo loại và phát hiện định dạng tài liệu trong
  Java với Aspose.Words. Hỗ trợ DOC, DOCX, RTF và hơn nữa.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Sắp xếp tệp theo loại bằng Aspose.Words cho Java
url: /vi/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tổ chức các tệp theo loại bằng Aspose.Words cho Java

Khi bạn cần **tổ chức các tệp theo loại** trong một ứng dụng Java, bước đầu tiên là xác định một cách đáng tin cậy định dạng của mỗi tài liệu. Aspose.Words cho Java làm cho việc này trở nên đơn giản, cho phép bạn phát hiện các định dạng DOC, DOCX, RTF, HTML, ODT và nhiều định dạng khác – ngay cả các tệp được mã hóa hoặc không xác định. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn cách thiết lập thư mục, phát hiện định dạng tệp và tự động sắp xếp các tệp của bạn.

## Câu trả lời nhanh
- **“Tổ chức các tệp theo loại” có nghĩa là gì?** Nó có nghĩa là tự động di chuyển tài liệu vào các thư mục dựa trên định dạng đã phát hiện (ví dụ: DOCX, PDF, RTF).  
- **Thư viện nào giúp phát hiện định dạng tệp trong Java?** Aspose.Words cho Java cung cấp `FileFormatUtil.detectFileFormat()`.  
- **API có thể xác định các loại tệp không xác định không?** Có – nó trả về `LoadFormat.UNKNOWN` cho các tệp không được hỗ trợ hoặc không nhận dạng được.  
- **Có hỗ trợ phát hiện tài liệu được mã hóa không?** Hoàn toàn có; cờ `FileFormatInfo.isEncrypted()` cho biết tệp có được bảo vệ bằng mật khẩu hay không.  
- **Tôi có cần giấy phép cho việc sử dụng trong môi trường sản xuất không?** Cần có giấy phép Aspose.Words hợp lệ cho các triển khai thương mại.

## Giới thiệu: Tổ chức các tệp theo loại với Aspose.Words cho Java

Khi làm việc với xử lý tài liệu trong Java, việc xác định định dạng của các tệp bạn đang xử lý là rất quan trọng. Aspose.Words cho Java cung cấp các tính năng mạnh mẽ để **detect file format java**, và chúng tôi sẽ hướng dẫn bạn quy trình tổ chức các tệp một cách hiệu quả.

## Yêu cầu trước

- [Aspose.Words for Java](https://releases.aspose.com/words/java/)
- Java Development Kit (JDK) được cài đặt trên hệ thống của bạn
- Kiến thức cơ bản về lập trình Java

## Bước 1: Cài đặt thư mục

Đầu tiên, chúng ta cần thiết lập các thư mục cần thiết để tổ chức các tệp một cách hiệu quả. Chúng ta sẽ tạo các thư mục cho các loại tài liệu khác nhau.

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

// Create the directories if they do not already exist.
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

Chúng tôi đã tạo các thư mục cho các loại tài liệu được hỗ trợ, không xác định, được mã hóa và tài liệu pre‑97.

## Bước 2: Phát hiện định dạng tài liệu

Bây giờ, hãy phát hiện định dạng của các tài liệu trong các thư mục của chúng ta. Chúng ta sẽ sử dụng Aspose.Words cho Java để thực hiện điều này.

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // Display the document type
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // Add cases for other document formats as needed
    }

    // Handle encrypted documents
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // Handle other document types
        switch (info.getLoadFormat()) {
            case LoadFormat.DOC_PRE_WORD_60:
                FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                break;
            case LoadFormat.UNKNOWN:
                FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                break;
            default:
                FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                break;
        }
    }
}
```

Trong đoạn mã này, chúng tôi duyệt qua các tệp, **detect file format java**, và sắp xếp chúng vào các thư mục phù hợp.

## Mã nguồn hoàn chỉnh để xác định định dạng tài liệu trong Aspose.Words cho Java

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        // Create the directories if they do not already exist.
        if (supportedDir.exists() == false)
            supportedDir.mkdir();
        if (unknownDir.exists() == false)
            unknownDir.mkdir();
        if (encryptedDir.exists() == false)
            encryptedDir.mkdir();
        if (pre97Dir.exists() == false)
            pre97Dir.mkdir();
        Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
                .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
                .map(File::getPath)
                .collect(Collectors.toSet());
        for (String fileName : listFiles) {
            String nameOnly = Paths.get(fileName).getFileName().toString();
            System.out.println(nameOnly);
            FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);
            // Display the document type
            switch (info.getLoadFormat()) {
                case LoadFormat.DOC:
                    System.out.println("\tMicrosoft Word 97-2003 document.");
                    break;
                case LoadFormat.DOT:
                    System.out.println("\tMicrosoft Word 97-2003 template.");
                    break;
                case LoadFormat.DOCX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Document.");
                    break;
                case LoadFormat.DOCM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
                    break;
                case LoadFormat.DOTX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Template.");
                    break;
                case LoadFormat.DOTM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
                    break;
                case LoadFormat.FLAT_OPC:
                    System.out.println("\tFlat OPC document.");
                    break;
                case LoadFormat.RTF:
                    System.out.println("\tRTF format.");
                    break;
                case LoadFormat.WORD_ML:
                    System.out.println("\tMicrosoft Word 2003 WordprocessingML format.");
                    break;
                case LoadFormat.HTML:
                    System.out.println("\tHTML format.");
                    break;
                case LoadFormat.MHTML:
                    System.out.println("\tMHTML (Web archive) format.");
                    break;
                case LoadFormat.ODT:
                    System.out.println("\tOpenDocument Text.");
                    break;
                case LoadFormat.OTT:
                    System.out.println("\tOpenDocument Text Template.");
                    break;
                case LoadFormat.DOC_PRE_WORD_60:
                    System.out.println("\tMS Word 6 or Word 95 format.");
                    break;
                case LoadFormat.UNKNOWN:
                    System.out.println("\tUnknown format.");
                    break;
            }
            if (info.isEncrypted()) {
                System.out.println("\tAn encrypted document.");
                FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
            } else {
                switch (info.getLoadFormat()) {
                    case LoadFormat.DOC_PRE_WORD_60:
                        FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                        break;
                    case LoadFormat.UNKNOWN:
                        FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                        break;
                    default:
                        FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                        break;
                }
            }
        }

```

## Cách phát hiện định dạng tệp Java

Phương thức `FileFormatUtil.detectFileFormat()` kiểm tra tiêu đề tệp và trả về một đối tượng `FileFormatInfo`. Đối tượng này cho bạn biết **load format**, liệu tệp có được mã hóa hay không, và các siêu dữ liệu hữu ích khác. Sử dụng thông tin này, bạn có thể lập trình để **identify unknown file types** và quyết định cách xử lý mỗi tệp.

## Xác định các loại tệp không xác định

Khi API trả về `LoadFormat.UNKNOWN`, tệp có thể bị hỏng hoặc sử dụng một định dạng mà Aspose.Words không hỗ trợ. Trong mã mẫu của chúng tôi, chúng tôi di chuyển những tệp đó vào thư mục **Unknown** để bạn có thể xem xét lại sau.

## Các vấn đề thường gặp và giải pháp

| Vấn đề | Lý do | Giải pháp |
|-------|--------|-----|
| Các tệp luôn được đặt vào thư mục *Supported* | `FileFormatUtil` không thể đọc tiêu đề (ví dụ: tệp rỗng) | Đảm bảo bạn truyền đúng đường dẫn tệp và tệp không có kích thước 0 byte. |
| Các tệp được mã hóa gây ra ngoại lệ | Cố gắng đọc mà không xử lý việc mã hóa | Sử dụng kiểm tra `info.isEncrypted()` trước khi thực hiện bất kỳ xử lý nào tiếp theo, như trong mã mẫu. |
| Tài liệu Word pre‑97 không được phát hiện | Các định dạng cũ cần trường hợp `DOC_PRE_WORD_60` | Giữ khối `case LoadFormat.DOC_PRE_WORD_60` để chuyển chúng vào thư mục *Pre97*. |

## Câu hỏi thường gặp

### Làm thế nào để cài đặt Aspose.Words cho Java?

Bạn có thể tải Aspose.Words cho Java từ [đây](https://releases.aspose.com/words/java/) và làm theo hướng dẫn cài đặt được cung cấp.

### Các định dạng tài liệu được hỗ trợ là gì?

Aspose.Words cho Java hỗ trợ nhiều định dạng tài liệu, bao gồm DOC, DOCX, RTF, HTML, ODT và hơn thế nữa. Tham khảo tài liệu chính thức để biết danh sách đầy đủ.

### Làm sao tôi có thể phát hiện tài liệu được mã hóa bằng Aspose.Words cho Java?

Sử dụng phương thức `FileFormatUtil.detectFileFormat()`; cờ `FileFormatInfo.isEncrypted()` trả về cho biết tài liệu có được mã hóa hay không, như đã minh họa trong hướng dẫn này.

### Có bất kỳ hạn chế nào khi làm việc với các định dạng tài liệu cũ không?

Các định dạng cũ như MS Word 6 hoặc Word 95 có thể thiếu các tính năng hiện đại và có thể gặp vấn đề tương thích. Hãy cân nhắc chuyển đổi chúng sang các định dạng mới hơn khi có thể.

### Tôi có thể tự động phát hiện định dạng tài liệu trong ứng dụng Java của mình không?

Có, hãy nhúng mã đã cung cấp vào quy trình xử lý của ứng dụng. Điều này cho phép tự động sắp xếp và xử lý dựa trên các định dạng đã phát hiện.

---

**Cập nhật lần cuối:** 2025-12-20  
**Kiểm tra với:** Aspose.Words for Java 24.12 (mới nhất)  
**Tác giả:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}