---
date: 2026-02-22
description: Tìm hiểu cách phát hiện định dạng tài liệu Java với Aspose.Words và tự
  động di chuyển tệp theo định dạng. Nhận dạng DOC, DOCX và nhiều định dạng khác.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Phát hiện định dạng tài liệu Java bằng Aspose.Words cho Java
url: /vi/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# phát hiện định dạng tài liệu java bằng Aspose.Words cho Java

Khi bạn cần **detect document format java** trong một lô tệp, khả năng tự động sắp xếp chúng vào các thư mục phù hợp có thể tiết kiệm hàng giờ công việc thủ công. Trong hướng dẫn này, chúng tôi sẽ chỉ cho bạn cách Aspose.Words cho Java giúp dễ dàng xác định Word, RTF, HTML, ODT và nhiều định dạng khác, và sau đó **move files by format** vào các thư mục được tổ chức.

## Câu trả lời nhanh
- **What does “detect document format java” mean?** Đó là quá trình xác định một cách lập trình định dạng xử lý văn bản của tệp (DOC, DOCX, RTF, v.v.) bằng mã Java.  
- **Which library provides this capability?** Aspose.Words cho Java cung cấp API `FileFormatUtil.detectFileFormat`.  
- **Can the utility also handle encrypted files?** Có – cờ `FileFormatInfo.isEncrypted()` cho biết tài liệu có được bảo vệ bằng mật khẩu hay không.  
- **Do I need a license for production use?** Cần có giấy phép thương mại của Aspose.Words cho các triển khai không phải đánh giá.  
- **Is it possible to move files automatically after detection?** Chắc chắn – kết hợp kết quả phát hiện với `FileUtils.copyFile` để sắp xếp tệp vào các thư mục tùy chỉnh.

## Detect document format java là gì?
`detect document format java` đề cập đến việc sử dụng mã Java để kiểm tra tiêu đề nhị phân của tệp và xác định định dạng xử lý văn bản mà nó thuộc về (ví dụ: DOC, DOCX, ODT). Aspose.Words đọc tệp mà không cần tải toàn bộ tài liệu, giúp thao tác nhanh và tiết kiệm bộ nhớ.

## Tại sao phải di chuyển tệp theo định dạng?
Việc tổ chức tài liệu theo định dạng gốc của chúng giúp đơn giản hoá quá trình xử lý tiếp theo:

- **Batch conversions** trở nên dễ dàng khi tất cả các tệp DOCX nằm trong một thư mục.  
- **Legacy support**: bạn có thể tách các tệp Word trước năm 97 để xử lý đặc biệt.  
- **Security**: các tài liệu được mã hoá có thể được cách ly tự động.  

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/) (tải phiên bản mới nhất)  
- Java Development Kit (JDK) 8 hoặc cao hơn đã được cài đặt  
- Kiến thức cơ bản về Java I/O và streams  

## Bước 1: Thiết lập thư mục cho mỗi định dạng

Đầu tiên chúng ta tạo một cấu trúc thư mục sạch sẽ nơi các tệp đã phát hiện sẽ được di chuyển. Điều này giữ cho quy trình làm việc gọn gàng và dễ dàng thêm các danh mục định dạng mới sau này.

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

> **Pro tip:** Sử dụng đường dẫn tuyệt đối hoặc cấu hình thư mục gốc thông qua file properties để tránh việc mã hoá cứng các đường dẫn trong mã sản xuất.

## Bước 2: Phát hiện định dạng tài liệu và di chuyển tệp

Phần cốt lõi của **detect document format java** nằm trong vòng lặp dưới đây. Nó quét từng tệp, xác định loại của chúng và sao chép vào thư mục phù hợp.

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

Khối `switch` có thể được mở rộng để bao phủ mọi định dạng bạn quan tâm. Mỗi case in ra một thông báo thân thiện và sau đó di chuyển tệp vào thư mục tương ứng.

## Mã nguồn hoàn chỉnh cho việc phát hiện định dạng tài liệu java

Dưới đây là ví dụ đầy đủ, sẵn sàng chạy, kết hợp thiết lập thư mục và logic phát hiện. Sao chép nó vào một lớp Java, điều chỉnh đường dẫn cơ sở, và chạy nó trên một thư mục chứa các tài liệu hỗn hợp.

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

## Các vấn đề thường gặp và khắc phục

| Issue | Lý do xảy ra | Cách khắc phục |
|-------|----------------|------------|
| **`FileFormatUtil.detectFileFormat` returns `UNKNOWN`** | Tệp bị hỏng hoặc sử dụng định dạng không phải Word. | Xác minh phần mở rộng tệp, hoặc thêm fallback để di chuyển nó vào thư mục *Unknown* (đã có trong mẫu). |
| **Encrypted files throw an exception** | API cố gắng đọc nội dung trước khi kiểm tra mã hoá. | Luôn gọi `info.isEncrypted()` trước bất kỳ thao tác nào khác trên tài liệu. |
| **Directory creation fails on Linux** | Quyền không đủ hoặc thiếu thư mục cha. | Đảm bảo quá trình Java có quyền ghi và đường dẫn cơ sở tồn tại. |

## Câu hỏi thường gặp

**Q: Làm thế nào để cài đặt Aspose.Words cho Java?**  
A: Bạn có thể tải Aspose.Words cho Java từ [đây](https://releases.aspose.com/words/java/) và làm theo hướng dẫn cài đặt được cung cấp.

**Q: Các định dạng tài liệu nào được hỗ trợ để phát hiện?**  
A: Aspose.Words có thể phát hiện DOC, DOCX, DOT, DOTX, DOCM, DOTM, RTF, HTML, MHTML, ODT, OTT, FLAT_OPC, WORD_ML, và các định dạng cũ hơn trước năm 97, cùng với các định dạng khác.

**Q: Mã này có thể xử lý tài liệu được bảo vệ bằng mật khẩu không?**  
A: Có. Cờ `FileFormatInfo.isEncrypted()` xác định các tệp được mã hoá, cho phép bạn di chuyển chúng vào thư mục an toàn mà không cần mở.

**Q: Có ảnh hưởng đến hiệu năng khi quét các thư mục lớn không?**  
A: Phát hiện chỉ đọc tiêu đề tệp, vì vậy ngay cả hàng nghìn tệp cũng được xử lý nhanh chóng. Đối với các lô rất lớn, hãy xem xét sử dụng parallel streams.

**Q: Làm thế nào để mở rộng script để chuyển đổi các định dạng không được hỗ trợ?**  
A: Sau khi phát hiện, bạn có thể gọi `Document.save` với định dạng đầu ra mong muốn cho bất kỳ loại nguồn nào được hỗ trợ.

## Kết luận

Bằng cách sử dụng **detect document format java** với Aspose.Words, bạn có được một cách đáng tin cậy để tự động sắp xếp, cách ly hoặc chuyển đổi các tệp liên quan đến Word. Mã mẫu minh họa cách tạo một cấu trúc thư mục sạch sẽ, xác định định dạng của từng tệp và di chuyển chúng một cách phù hợp—giúp bạn tiết kiệm thời gian và giảm lỗi thủ công.

---

**Cập nhật lần cuối:** 2026-02-22  
**Kiểm tra với:** Aspose.Words for Java 24.12 (latest)  
**Tác giả:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}