---
date: '2025-11-12'
description: Tìm hiểu cách chèn ký tự điều khiển, quản lý ký tự xuống dòng và thêm
  ngắt trang hoặc cột trong Java bằng Aspose.Words để định dạng tài liệu một cách
  chính xác.
keywords:
- Aspose.Words control characters
- Java document formatting with Aspose.Words
- inserting control characters in Java
- insert control characters java
- manage carriage returns
- add page break aspose
- insert non‑breaking space
- create multi‑column layout
language: vi
title: Chèn ký tự điều khiển trong Java bằng Aspose.Words
url: /java/advanced-text-processing/aspose-words-java-control-characters-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Chèn ký tự điều khiển trong Java với Aspose.Words
## Giới thiệu
Bạn có cần kiểm soát chính xác từng pixel đối với ngắt dòng, tab hoặc phân trang khi tạo hoá đơn, báo cáo hoặc bản tin không?  
Ký tự điều khiển là các khối xây dựng vô hình cho phép bạn định dạng bố cục tài liệu một cách lập trình.  
Trong hướng dẫn này, bạn sẽ học cách **chèn**, **xác minh** và **quản lý** các ký tự điều khiển như ký tự xuống dòng, dấu cách không ngắt và ngắt cột bằng API Aspose.Words for Java.

**Bạn sẽ đạt được:**
1. Chèn và xác thực ký tự xuống dòng, ký tự line feed và ngắt trang.  
2. Thêm dấu cách, tab, dấu cách không ngắt và ngắt cột để tạo bố cục đa cột.  
3. Áp dụng các mẹo tối ưu hiệu năng cho tự động hoá tài liệu quy mô lớn.

## Yêu cầu trước
Trước khi bắt đầu, hãy chắc chắn bạn đã chuẩn bị các mục sau:

| Yêu cầu | Chi tiết |
|-------------|----------|
| **Aspose.Words for Java** | Phiên bản 25.3 hoặc mới hơn (API vẫn ổn định trong các phiên bản sau). |
| **JDK** | Java 8 + (khuyến nghị Java 11 hoặc 17). |
| **IDE** | IntelliJ IDEA, Eclipse hoặc bất kỳ trình soạn thảo nào hỗ trợ Java. |
| **Công cụ xây dựng** | Maven **hoặc** Gradle để quản lý phụ thuộc. |
| **Giấy phép** | Tệp giấy phép Aspose.Words tạm thời hoặc đã mua. |

### Danh sách kiểm tra nhanh môi trường
1. Maven **hoặc** Gradle đã được cài đặt.  
2. Tệp giấy phép có thể truy cập được (ví dụ: `src/main/resources/aspose.words.lic`).  
3. Dự án biên dịch không lỗi.

## Cài đặt Aspose.Words
Chúng ta sẽ đầu tiên thêm thư viện vào dự án, sau đó tải giấy phép. Chọn hệ thống xây dựng phù hợp với quy trình làm việc của bạn.

### Phụ thuộc Maven
Thêm đoạn mã sau vào file `pom.xml` của bạn trong thẻ `<dependencies>`:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Phụ thuộc Gradle
Chèn dòng này vào khối `dependencies` của `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Khởi tạo giấy phép (mã Java)
```java
License license = new License();
license.setLicense("path/to/aspose.words.lic");
```

> **Lưu ý:** Thay `"path/to/aspose.words.lic"` bằng đường dẫn thực tế tới tệp giấy phép của bạn.

## Tính năng 1: Xử lý ký tự xuống dòng và ngắt trang
Ký tự xuống dòng (`ControlChar.CR`) và ngắt trang (`ControlChar.PAGE_BREAK`) rất quan trọng khi bạn cần văn bản đầu ra phản ánh bố cục trực quan của tài liệu.

### Thực hiện từng bước
1. **Tạo một Document và DocumentBuilder mới.**  
2. **Viết hai đoạn văn.**  
3. **Xác minh rằng văn bản được tạo chứa các ký tự điều khiển mong đợi.**  
4. **Cắt bỏ khoảng trắng và kiểm tra lại kết quả.**

#### 1. Tạo Document
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

#### 2. Chèn đoạn văn
```java
builder.writeln("Hello world!");
builder.writeln("Hello again!");
```

#### 3. Xác minh ký tự điều khiển
```java
String expectedTextWithCR = MessageFormat.format("Hello world!{0}", ControlChar.CR) +
        MessageFormat.format("Hello again!{0}", ControlChar.CR) +
        ControlChar.PAGE_BREAK;
assert doc.getText().equals(expectedTextWithCR) :
        "Text does not match expected value with control characters.";
```

#### 4. Cắt và kiểm tra văn bản
```java
String expectedTrimmedText = MessageFormat.format("Hello world!{0}", ControlChar.CR) + "Hello again!";
assert doc.getText().trim().equals(expectedTrimmedText) :
        "Trimmed text does not match expected value.";
```

**Kết quả:** Chuỗi `doc.getText()` hiện chứa các ký hiệu CR và ngắt trang rõ ràng, đảm bảo các hệ thống hạ nguồn (ví dụ: bộ xuất plain‑text) giữ nguyên bố cục.

## Tính năng 2: Ch