---
"date": "2025-03-28"
"description": "Tìm hiểu cách tận dụng Aspose.Words for Java để làm chủ quá trình xử lý tài liệu, bao gồm hỗ trợ VML, mã hóa, tùy chọn nhập HTML, v.v."
"title": "Aspose.Words cho Java&#58; Các tính năng HTML toàn diện và Hướng dẫn xử lý tài liệu"
"url": "/vi/java/document-operations/aspose-words-java-html-features-guide/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# Các tính năng HTML toàn diện với Aspose.Words cho Java: Hướng dẫn dành cho nhà phát triển

## Giới thiệu

Việc điều hướng thế giới phức tạp của quá trình xử lý tài liệu có thể rất khó khăn, đặc biệt là khi xử lý nhiều tính năng HTML khác nhau. Cho dù bạn đang xử lý hỗ trợ Ngôn ngữ đánh dấu vectơ (VML), tài liệu được mã hóa hay các hành vi nhập HTML cụ thể, **Aspose.Words cho Java** cung cấp giải pháp mạnh mẽ. Trong hướng dẫn này, chúng tôi sẽ khám phá cách triển khai các chức năng này một cách liền mạch bằng Aspose.Words, nâng cao khả năng xử lý tài liệu của bạn.

**Những gì bạn sẽ học được:**
- Cách tải tài liệu HTML có hỗ trợ VML.
- Các kỹ thuật xử lý HTML trang cố định và cảnh báo.
- Phương pháp mã hóa và tải các tài liệu HTML được bảo vệ bằng mật khẩu.
- Sử dụng URI cơ sở trong Tùy chọn tải HTML.
- Nhập các phần tử đầu vào HTML dưới dạng thẻ tài liệu có cấu trúc hoặc trường biểu mẫu.
- Bỏ qua `<noscript>` các thành phần trong quá trình tải HTML.
- Cấu hình chế độ nhập khối để kiểm soát việc bảo toàn cấu trúc HTML.
- Hỗ trợ `@font-face` quy tắc cho phông chữ tùy chỉnh.

Với những hiểu biết sâu sắc này, bạn sẽ được trang bị tốt để giải quyết nhiều tác vụ xử lý HTML. Hãy cùng tìm hiểu các điều kiện tiên quyết và thiết lập trước!

## Điều kiện tiên quyết

Trước khi chúng ta bắt đầu triển khai nhiều tính năng HTML khác nhau với Aspose.Words cho Java, hãy đảm bảo rằng môi trường của bạn được thiết lập đúng cách:

- **Thư viện bắt buộc:** Bạn cần thư viện Aspose.Words phiên bản 25.3 trở lên.
- **Môi trường phát triển:** Hướng dẫn này giả định rằng bạn đang sử dụng Maven hoặc Gradle để quản lý phụ thuộc.
- **Cơ sở kiến thức:** Hiểu biết cơ bản về Java và quen thuộc với các tài liệu HTML sẽ rất có lợi.

## Thiết lập Aspose.Words

Để bắt đầu làm việc với Aspose.Words, trước tiên bạn cần đưa nó vào dự án của mình. Sau đây là các bước để thiết lập thư viện bằng Maven và Gradle:

### Maven

Thêm phụ thuộc sau vào `pom.xml` tài liệu:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Tốt nghiệp

Bao gồm điều này trong của bạn `build.gradle` tài liệu:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### Mua lại giấy phép

Aspose.Words yêu cầu giấy phép để có đầy đủ chức năng. Bạn có thể dùng thử miễn phí, yêu cầu giấy phép tạm thời hoặc mua giấy phép vĩnh viễn. Truy cập [trang mua hàng](https://purchase.aspose.com/buy) để biết thêm chi tiết.

Để khởi tạo Aspose.Words trong dự án Java của bạn, hãy đảm bảo rằng bạn đã thiết lập cấp phép đúng cách:

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

## Hướng dẫn thực hiện

Chúng tôi sẽ chia nhỏ quá trình triển khai thành các phần dựa trên các tính năng chúng tôi muốn triển khai.

### Hỗ trợ VML trong Tài liệu HTML

**Tổng quan:**
Tải một tài liệu HTML có hoặc không có hỗ trợ VML cho phép kết xuất đồ họa vector đa dạng. Tính năng này rất quan trọng khi xử lý các tài liệu bao gồm các thành phần đồ họa như biểu đồ và hình dạng.

#### Thực hiện từng bước:

1. **Thiết lập tùy chọn tải**
   
   ```java
   import com.aspose.words.Document;
   import com.aspose.words.HtmlLoadOptions;

   HtmlLoadOptions loadOptions = new HtmlLoadOptions();
   loadOptions.setSupportVml(true); // Bật hỗ trợ VML
   ```

2. **Tải Tài liệu**
   
   ```java
   Document doc = new Document("path/to/VML conditional.htm", loadOptions);
   ```

3. **Xác minh loại hình ảnh**
   
   Đảm bảo rằng loại hình ảnh phù hợp với mong đợi của bạn:
   
   ```java
   import com.aspose.words.NodeType;
   import com.aspose.words.Shape;

   Shape imageShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
   String expectedImageType = "JPG"; // Điều chỉnh dựa trên logic thực tế

   if (!imageShape.getImageData().getImageType().toString().equals(expectedImageType)) {
       throw new AssertionError("Unexpected image type loaded.");
   }
   ```

### Tải HTML Đã sửa và Xử lý Cảnh báo

**Tổng quan:**
Việc tải các tài liệu HTML trang cố định có thể tạo ra các cảnh báo cần được quản lý để xử lý chính xác.

#### Thực hiện từng bước:

1. **Xác định cảnh báo gọi lại**
   
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

2. **Cấu hình Tùy chọn Tải**
   
   ```java
   HtmlLoadOptions loadOptions = new HtmlLoadOptions();
   ListDocumentWarnings warningCallback = new ListDocumentWarnings();
   loadOptions.setWarningCallback(warningCallback);
   ```

3. **Tải Tài Liệu và Kiểm Tra Cảnh Báo**
   
   ```java
   Document doc = new Document("path/to/HtmlFixed.html", loadOptions);

   if (warningCallback.warnings().size() != 1) {
       throw new AssertionError("Unexpected number of warnings.");
   }
   ```

### Mã hóa tài liệu HTML

**Tổng quan:**
Mã hóa tài liệu HTML bằng mật khẩu đảm bảo truy cập an toàn, điều này rất cần thiết đối với thông tin nhạy cảm.

#### Thực hiện từng bước:

1. **Chuẩn bị các tùy chọn chữ ký số**
   
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

2. **Ký và mã hóa tài liệu**
   
   ```java
   String inputFileName = "path/to/Encrypted.docx";
   String outputFileName = "path/to/output/directory/HtmlLoadOptions.EncryptedHtml.html";

   DigitalSignatureUtil.sign(inputFileName, outputFileName, certificateHolder, signOptions);
   ```

3. **Tải tài liệu được mã hóa**
   
   ```java
   import com.aspose.words.Document;

   HtmlLoadOptions loadOptions = new HtmlLoadOptions("docPassword");
   Document doc = new Document(outputFileName, loadOptions);

   if (!doc.getText().trim().equals("Test encrypted document.")) {
       throw new AssertionError("Unexpected document text.");
   }
   ```

### URI cơ sở cho Tùy chọn tải HTML

**Tổng quan:**
Việc chỉ định URI cơ sở giúp giải quyết các URI tương đối, đặc biệt khi xử lý hình ảnh hoặc các tài nguyên được liên kết khác.

#### Thực hiện từng bước:

1. **Cấu hình Tùy chọn Tải với URI Cơ sở**
   
   ```java
   HtmlLoadOptions loadOptions = new HtmlLoadOptions(LoadFormat.HTML, "", "path/to/imageDir");
   ```

2. **Tải tài liệu và xác minh hình ảnh**
   
   ```java
   import com.aspose.words.Document;
   import com.aspose.words.NodeType;

   Document doc = new Document("path/to/Missing image.html", loadOptions);
   Shape imageShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);

   if (!imageShape.isImage()) {
       throw new AssertionError("Expected an image shape.");
   }
   ```

### Nhập HTML Chọn làm Thẻ Tài liệu có cấu trúc

**Tổng quan:**
Nhập khẩu `<select>` Các thành phần như thẻ tài liệu có cấu trúc cho phép kiểm soát và định dạng tốt hơn trong các tài liệu Word.

#### Thực hiện từng bước:

1. **Đặt Loại Điều Khiển Ưa Thích**
   
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

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}