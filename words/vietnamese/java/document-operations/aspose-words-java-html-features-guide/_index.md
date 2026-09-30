---
date: '2026-02-06'
description: Tìm hiểu cách tải HTML VML với Aspose.Words for Java, mã hóa các tệp
  HTML Java, đặt URI cơ sở HTML và cấu hình các tùy chọn điều khiển HTML.
keywords:
- Aspose.Words for Java
- HTML document processing
- document encryption
title: Tải HTML VML bằng Aspose.Words cho Java – Hướng dẫn đầy đủ
url: /vi/java/document-operations/aspose-words-java-html-features-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Các tính năng HTML toàn diện với Aspose.Words cho Java: Hướng dẫn dành cho nhà phát triển

## Giới thiệu

Việc điều hướng thế giới phức tạp của xử lý tài liệu có thể gây khó khăn, đặc biệt khi làm việc với nhiều tính năng HTML khác nhau. Dù bạn đang xử lý hỗ trợ Vector Markup Language (VML), tài liệu được mã hoá, hay các hành vi nhập HTML cụ thể, **Aspose.Words for Java** cung cấp một giải pháp mạnh mẽ. Trong hướng dẫn này, bạn sẽ học **how to load html vml** một cách hiệu quả và an toàn, đồng thời bao phủ các nhiệm vụ liên quan như **encrypt html java**, **set html base uri**, và **configure html control**.

**Bạn sẽ học được:**
- Cách tải tài liệu HTML với hỗ trợ VML.
- Kỹ thuật xử lý HTML dạng trang cố định và các cảnh báo.
- Phương pháp mã hoá và tải tài liệu HTML có bảo vệ bằng mật khẩu.
- Sử dụng base URI trong HTML Load Options.
- Nhập các phần tử input HTML dưới dạng structured document tags hoặc form fields.
- Bỏ qua các phần tử `<noscript>` khi tải HTML.
- Cấu hình chế độ nhập block để kiểm soát việc bảo tồn cấu trúc HTML.
- Hỗ trợ các quy tắc `@font-face` cho phông chữ tùy chỉnh.

## Câu trả lời nhanh
- **Cách chính để bật VML khi tải HTML là gì?** Đặt `loadOptions.setSupportVml(true)`.
- **Tôi có thể tải các tệp HTML được bảo vệ bằng mật khẩu không?** Có, truyền mật khẩu vào `HtmlLoadOptions`.
- **Làm sao để giải quyết các đường dẫn ảnh tương đối?** Sử dụng `loadOptions.setBaseUri("your/base/uri")`.
- **Có thể nhập `<select>` dưới dạng trường biểu mẫu không?** Đặt `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)`.
- **Lớp nào ghi lại các cảnh báo trong quá trình tải?** Triển khai `IWarningCallback` và gán nó cho `loadOptions.setWarningCallback(...)`.

## Yêu cầu trước

Trước khi chúng ta bắt đầu triển khai các tính năng HTML khác nhau với Aspose.Words cho Java, hãy đảm bảo môi trường của bạn đã được thiết lập đúng cách:

- **Thư viện yêu cầu:** Bạn cần thư viện Aspose.Words phiên bản 25.3 trở lên.
- **Môi trường phát triển:** Hướng dẫn này giả định bạn đang sử dụng Maven hoặc Gradle để quản lý phụ thuộc.
- **Kiến thức nền:** Hiểu biết cơ bản về Java và quen thuộc với tài liệu HTML sẽ có lợi.

## Cài đặt Aspose.Words

Để bắt đầu làm việc với Aspose.Words, trước tiên bạn cần đưa nó vào dự án của mình. Dưới đây là các bước để thiết lập thư viện bằng Maven và Gradle:

### Maven

Thêm phụ thuộc sau vào tệp `pom.xml` của bạn:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle

Bao gồm đoạn này trong tệp `build.gradle` của bạn:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### Nhận giấy phép

Aspose.Words yêu cầu giấy phép để có đầy đủ chức năng. Bạn có thể nhận bản dùng thử miễn phí, yêu cầu giấy phép tạm thời, hoặc mua bản vĩnh viễn. Truy cập [trang mua hàng](https://purchase.aspose.com/buy) để biết thêm chi tiết.

Để khởi tạo Aspose.Words trong dự án Java của bạn, hãy chắc chắn rằng bạn đã thiết lập giấy phép đúng cách:

```java
import com.aspose.words.License;

public class InitializeAspose {
    public static void main(String[] args) throws Exception {
        License license = new License();
        license.setLicense("path/to/your/license/file.lic");
        
        System.out.println("Aspose.Words is ready to use!");
    }
}
```

## Hướng dẫn triển khai

Chúng tôi sẽ chia triển khai thành các phần dựa trên các tính năng mà chúng ta muốn thực hiện.

### Cách tải html vml với Aspose.Words

**Tổng quan:**  
Việc tải tài liệu HTML có hỗ trợ VML cho phép hiển thị đa dạng các đồ họa vector như biểu đồ và hình dạng. Đây là bước cốt lõi cho từ khóa chính **load html vml**.

#### Các bước thực hiện

1. **Cấu hình Load Options**

```java
import com.aspose.words.Document;
import com.aspose.words.HtmlLoadOptions;

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
loadOptions.setSupportVml(true); // Enable VML support
```

2. **Tải tài liệu**

```java
Document doc = new Document("path/to/VML conditional.htm", loadOptions);
```

3. **Xác minh loại ảnh**

```java
import com.aspose.words.NodeType;
import com.aspose.words.Shape;

Shape imageShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
String expectedImageType = "JPG"; // Adjust based on actual logic

if (!imageShape.getImageData().getImageType().toString().equals(expectedImageType)) {
    throw new AssertionError("Unexpected image type loaded.");
}
```

### Tải HTML dạng cố định và Xử lý Cảnh báo

**Tổng quan:**  
Việc tải tài liệu HTML dạng trang cố định có thể tạo ra các cảnh báo cần được quản lý để xử lý chính xác.

#### Các bước thực hiện

1. **Định nghĩa Warning Callback**

```java
import com.aspose.words.IWarningCallback;
import com.aspose.words.WarningInfo;
import java.util.ArrayList;

private static class ListDocumentWarnings implements IWarningCallback {
    private final ArrayList<WarningInfo> mWarnings = new ArrayList<>();

    public void warning(WarningInfo info) { 
        mWarnings.add(info); 
    }

    public ArrayList<WarningInfo> warnings() { return mWarnings; }
}
```

2. **Cấu hình Load Options**

```java
HtmlLoadOptions loadOptions = new HtmlLoadOptions();
ListDocumentWarnings warningCallback = new ListDocumentWarnings();
loadOptions.setWarningCallback(warningCallback);
```

3. **Tải tài liệu và kiểm tra cảnh báo**

```java
Document doc = new Document("path/to/HtmlFixed.html", loadOptions);

if (warningCallback.warnings().size() != 1) {
    throw new AssertionError("Unexpected number of warnings.");
}
```

### Mã hoá tài liệu HTML

**Tổng quan:**  
Mã hoá tài liệu HTML bằng mật khẩu đảm bảo truy cập an toàn, điều này rất quan trọng đối với thông tin nhạy cảm—điều này đáp ứng kịch bản **encrypt html java**.

#### Các bước thực hiện

1. **Chuẩn bị tùy chọn chữ ký số**

```java
import com.aspose.words.CertificateHolder;
import com.aspose.words.DigitalSignatureUtil;
import com.aspose.words.SignOptions;

CertificateHolder certificateHolder = CertificateHolder.create("path/to/morzal.pfx", "aw");
SignOptions signOptions = new SignOptions();
signOptions.setComments("Comment");
signOptions.setSignTime(new Date());
signOptions.setDecryptionPassword("docPassword");
```

2. **Ký và mã hoá tài liệu**

```java
String inputFileName = "path/to/Encrypted.docx";
String outputFileName = "path/to/output/directory/HtmlLoadOptions.EncryptedHtml.html";

DigitalSignatureUtil.sign(inputFileName, outputFileName, certificateHolder, signOptions);
```

3. **Tải tài liệu đã mã hoá**

```java
import com.aspose.words.Document;

HtmlLoadOptions loadOptions = new HtmlLoadOptions("docPassword");
Document doc = new Document(outputFileName, loadOptions);

if (!doc.getText().trim().equals("Test encrypted document.")) {
    throw new AssertionError("Unexpected document text.");
}
```

### Base URI cho HTML Load Options

**Tổng quan:**  
Việc chỉ định **set html base uri** giúp giải quyết các URI tương đối, đặc biệt khi làm việc với ảnh hoặc các tài nguyên liên kết khác.

#### Các bước thực hiện

1. **Cấu hình Load Options với Base URI**

```java
HtmlLoadOptions loadOptions = new HtmlLoadOptions(LoadFormat.HTML, "", "path/to/imageDir");
```

2. **Tải tài liệu và xác minh ảnh**

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;

Document doc = new Document("path/to/Missing image.html", loadOptions);
Shape imageShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);

if (!imageShape.isImage()) {
    throw new AssertionError("Expected an image shape.");
}
```

### Nhập HTML Select dưới dạng Structured Document Tag

**Tổng quan:**  
Để **configure html control** hành vi, bạn có thể nhập các phần tử `<select>` dưới dạng Structured Document Tags, cho phép bạn kiểm soát chi tiết hơn các trường biểu mẫu trong tài liệu Word.

#### Các bước thực hiện

1. **Đặt loại điều khiển ưu tiên**

```java
import com.aspose.words.HtmlLoadOptions;
import com.aspose.words.ControlType;

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag);
```

2. **Tải tài liệu và xác minh cấu trúc**

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;
import com.aspose.words.StructuredDocumentTag;

Document doc = new Document("path/to/Input HTML with select element.html", loadOptions);
StructuredDocumentTag sdt = (StructuredDocumentTag)doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (!sdt.getTagName().equals("Select")) {
    throw new AssertionError("Expected a Structured Document Tag with tag name 'Select'.");
}
```

## Các vấn đề thường gặp và giải pháp

| Vấn đề | Nguyên nhân | Giải pháp |
|-------|------------|----------|
| Đồ họa VML không hiển thị | Cờ `supportVml` để mặc định (`false`) | Đảm bảo gọi `loadOptions.setSupportVml(true)` trước khi tải. |
| Ảnh bị thiếu sau khi tải | Không thể giải quyết các đường dẫn tương đối | Sử dụng **set html base uri** (`loadOptions.setBaseUri(...)`) để chỉ tới thư mục đúng. |
| HTML được bảo vệ bằng mật khẩu gây ra ngoại lệ | Chưa cung cấp mật khẩu | Truyền mật khẩu vào `new HtmlLoadOptions("yourPassword")`. |
| Các điều khiển biểu mẫu hiển thị dưới dạng văn bản thường | `HtmlControlType` sai | Đặt `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)` hoặc `FormField` theo nhu cầu. |
| Cảnh báo không mong muốn | Các phần tử HTML chưa được xử lý | Triển khai `IWarningCallback` để ghi lại và xem lại các cảnh báo. |

## Câu hỏi thường gặp

**Q: Tôi có thể tải các tệp HTML chứa cả đồ họa VML và SVG hiện đại không?**  
A: Có. Bật VML bằng `setSupportVml(true)`; SVG được Aspose.Words xử lý tự động.

**Q: Làm sao để mã hoá một tài liệu HTML mà không dùng chứng chỉ số?**  
A: Sử dụng hàm khởi tạo `HtmlLoadOptions` nhận mật khẩu và lưu tài liệu bằng `Document.save(..., SaveFormat.HTML)` sau khi đã đặt mật khẩu.

**Q: Điều gì sẽ xảy ra nếu base URI trỏ tới thư mục không tồn tại?**  
A: Aspose.Words sẽ ném ra `FileNotFoundException` cho các tài nguyên bị thiếu. Kiểm tra đường dẫn trước khi tải.

**Q: Có thể thay đổi loại điều khiển mặc định cho tất cả các phần tử biểu mẫu HTML không?**  
A: Có. Sử dụng `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)` để áp dụng toàn cục.

**Q: Các callback cảnh báo có an toàn với đa luồng không?**  
A: Việc triển khai callback nên an toàn với đa luồng nếu bạn dự định tải tài liệu đồng thời. Sử dụng các collection đồng bộ hoặc lưu trữ thread‑local.

---

**Cập nhật lần cuối:** 2026-02-06  
**Đã kiểm tra với:** Aspose.Words for Java 25.3  
**Tác giả:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}