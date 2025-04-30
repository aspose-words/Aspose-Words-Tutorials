---
"date": "2025-03-28"
"description": "Tìm hiểu cách tự động ký tài liệu bằng Aspose.Words for Java. Hướng dẫn này bao gồm thiết lập môi trường, tạo dữ liệu thử nghiệm, thêm dòng chữ ký và ký tài liệu kỹ thuật số."
"title": "Tự động ký tài liệu trong Java với Aspose.Words&#58; Hướng dẫn toàn diện"
"url": "/vi/java/mail-merge-reporting/aspose-words-java-document-signing-tutorial/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# Tự động ký tài liệu trong Java với Aspose.Words: Hướng dẫn toàn diện

## Giới thiệu

Trong thế giới kinh doanh phát triển nhanh chóng ngày nay, quản lý tài liệu hiệu quả là điều cần thiết. Tự động hóa việc tạo và ký tài liệu kỹ thuật số có thể tiết kiệm thời gian và giảm thiểu lỗi. Hướng dẫn này sẽ hướng dẫn bạn sử dụng Aspose.Words cho Java để tạo dữ liệu thử nghiệm cho người ký, thêm dòng chữ ký và ký tài liệu kỹ thuật số.

**Những gì bạn sẽ học được:**
- Thiết lập Aspose.Words trong một dự án Java
- Tạo dữ liệu người ký thử nghiệm bằng Java
- Thêm dòng chữ ký vào tài liệu Word
- Ký số tài liệu bằng chứng chỉ số

Hãy bắt đầu bằng cách chuẩn bị môi trường phát triển của bạn!

## Điều kiện tiên quyết

Trước khi bắt đầu hướng dẫn, hãy đảm bảo thiết lập của bạn đáp ứng các yêu cầu sau:

- **Bộ phát triển Java (JDK):** Phiên bản 8 trở lên.
- **Môi trường phát triển tích hợp (IDE):** Chẳng hạn như IntelliJ IDEA hoặc Eclipse.
- **Aspose.Words dành cho Java:** Thư viện này có thể được đưa vào thông qua Maven hoặc Gradle.

### Điều kiện tiên quyết về kiến thức

Hiểu biết cơ bản về lập trình Java và quen thuộc với việc xử lý tệp và luồng sẽ có lợi. Nếu bạn mới sử dụng Aspose, đừng lo lắng—chúng tôi sẽ hướng dẫn những điều cần thiết.

## Thiết lập Aspose.Words

Để sử dụng Aspose.Words for Java trong dự án của bạn, hãy làm theo các bước sau:

### Phụ thuộc Maven

Thêm phụ thuộc sau vào `pom.xml` tài liệu:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Phụ thuộc Gradle

Đối với các dự án Gradle, hãy bao gồm dòng này trong `build.gradle` tài liệu:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Mua lại giấy phép

Aspose cung cấp nhiều tùy chọn cấp phép khác nhau:

- **Dùng thử miễn phí:** Tải xuống phiên bản dùng thử miễn phí để kiểm tra các tính năng.
- **Giấy phép tạm thời:** Xin giấy phép tạm thời để đánh giá.
- **Mua:** Để có quyền truy cập đầy đủ, hãy mua giấy phép từ trang web của Aspose.

Đảm bảo dự án của bạn được cấu hình với các phụ thuộc cần thiết và bất kỳ giấy phép nào được yêu cầu. Thiết lập này sẽ cho phép bạn tận dụng khả năng xử lý tài liệu mạnh mẽ của Aspose một cách liền mạch.

## Hướng dẫn thực hiện

Chúng tôi sẽ hướng dẫn từng tính năng theo từng bước, bắt đầu bằng việc tạo dữ liệu người ký thử nghiệm.

### Tính năng 1: Tạo dữ liệu thử nghiệm cho người ký

#### Tổng quan

Tính năng này tạo ra danh sách người ký có ID, tên, chức vụ và hình ảnh duy nhất. Điều này rất cần thiết để kiểm tra các tình huống ký tài liệu mà không cần sử dụng dữ liệu thực.

##### Bước 1: Thiết lập lớp Java của bạn

Tạo một lớp có tên `SignPersonCreator` và nhập các thư viện cần thiết:

```java
import java.io.ByteArrayOutputStream;
import java.io.FileInputStream;
import java.io.IOException;
import java.io.InputStream;
import java.util.ArrayList;
import java.util.UUID;

class DocumentHelper {
    public static byte[] getBytesFromStream(InputStream inputStream) throws IOException {
        int numRead; 
        byte[] buffer = new byte[1024]; 
        ByteArrayOutputStream baos = new ByteArrayOutputStream();

        while ((numRead = inputStream.read(buffer)) != -1) {
            baos.write(buffer, 0, numRead);
        }
        return baos.toByteArray();
    }
}

public class SignPersonCreator {
    private static ArrayList<SignPersonTestClass> gSignPersonList;

    public static void main(String[] args) throws IOException {
        createSignPersonData();
        System.out.println("Test data successfully added!");
    }

    private static void createSignPersonData() throws IOException {
        InputStream inputStream = new FileInputStream(YOUR_DOCUMENT_DIRECTORY + "Logo.jpg");

        gSignPersonList = new ArrayList<>();
        gSignPersonList.add(new SignPersonTestClass(UUID.randomUUID(), "Ron Williams", "Chief Executive Officer",
                DocumentHelper.getBytesFromStream(inputStream)));
        gSignPersonList.add(new SignPersonTestClass(UUID.randomUUID(), "Stephen Morse", "Head of Compliance",
                DocumentHelper.getBytesFromStream(inputStream)));
    }
}
```

##### Giải thích

- **Mã nhận dạng:** Tạo một mã định danh duy nhất cho mỗi người ký.
- **lấyBytesFromStream:** Chuyển đổi một tệp hình ảnh thành một mảng byte để lưu trữ.

### Tính năng 2: Thêm Dòng Chữ ký vào Tài liệu

#### Tổng quan

Tính năng này thêm dòng chữ ký vào tài liệu của bạn, liên kết nó với thông tin chi tiết của người ký.

##### Bước 1: Tạo lớp SignatureLineAdder

Thực hiện `SignatureLineAdder` lớp như sau:

```java
import com.aspose.words.*;

class SignatureLineAdder {
    public static void main(String[] args) throws Exception {
        String srcDocumentPath = YOUR_DOCUMENT_DIRECTORY + "Document.docx";
        String dstDocumentPath = YOUR_OUTPUT_DIRECTORY + "SignDocumentCustom.Sign.docx";
        
        SignPersonTestClass signPersonInfo = gSignPersonList.stream()
                .filter(x -> x.getName().equals("Ron Williams")).findFirst().orElse(null);

        if (signPersonInfo != null) {
            addSignatureLine(srcDocumentPath, dstDocumentPath, signPersonInfo);
            System.out.println("Signature line added successfully!");
        } else {
            System.out.println("Sign person does not exist, please check your parameters.");
        }
    }

    private static void addSignatureLine(final String srcDocumentPath, final String dstDocumentPath,
                                         final SignPersonTestClass signPersonInfo) throws Exception {
        Document document = new Document(srcDocumentPath);
        DocumentBuilder builder = new DocumentBuilder(document);

        SignatureLineOptions signatureLineOptions = new SignatureLineOptions();
        signatureLineOptions.setSigner(signPersonInfo.getName());
        signatureLineOptions.setSignerTitle(signPersonInfo.getPosition());

        SignatureLine signatureLine = builder.insertSignatureLine(signatureLineOptions).getSignatureLine();
        signatureLine.setId(String.valueOf(signPersonInfo.getPersonId()));

        builder.getDocument().save(dstDocumentPath);
    }
}
```

##### Giải thích

- **Tùy chọn SignatureLine:** Cấu hình tên và chức danh của người ký.
- **chèn Dòng Chữ Ký:** Chèn dòng chữ ký vào tài liệu tại vị trí con trỏ hiện tại.

### Tính năng 3: Ký tài liệu bằng chứng chỉ số

#### Tổng quan

Tính năng này sẽ ký kỹ thuật số vào tài liệu bằng chứng chỉ số, đảm bảo tính xác thực và toàn vẹn.

##### Bước 1: Tạo lớp DocumentSigner

Thực hiện `DocumentSigner` lớp học:

```java
import com.aspose.words.*;

class DocumentSigner {
    public static void main(String[] args) throws Exception {
        String srcDocumentPath = YOUR_DOCUMENT_DIRECTORY + "Document.docx";
        String dstDocumentPath = YOUR_OUTPUT_DIRECTORY + "SignDocumentCustom.Sign.docx";
        String certificatePath = YOUR_DOCUMENT_DIRECTORY + "morzal.pfx";
        String certificatePassword = "aw";

        SignPersonTestClass signPersonInfo = gSignPersonList.stream()
                .filter(x -> x.getName().equals("Ron Williams")).findFirst().orElse(null);

        if (signPersonInfo != null) {
            signDocument(srcDocumentPath, dstDocumentPath, signPersonInfo, certificatePath, certificatePassword);
            System.out.println("Document successfully signed!");
        } else {
            System.out.println("Sign person does not exist, please check your parameters.");
        }
    }

    private static void signDocument(final String srcDocumentPath, final String dstDocumentPath,
                                     final SignPersonTestClass signPersonInfo, final String certificatePath,
                                     final String certificatePassword) throws Exception {
        Document document = new Document(dstDocumentPath);

        CertificateHolder certificateHolder = CertificateHolder.create(certificatePath, certificatePassword);

        SignOptions signOptions = new SignOptions();
        signOptions.setSignatureLineId(String.valueOf(
            signPersonInfo.getPersonId()));

        document.sign(signOptions, certificateHolder);
    }
}
```

##### Giải thích

- **Người giữ chứng chỉ:** Biểu thị chứng chỉ số được sử dụng để ký.
- **dấu hiệu:** Phương pháp ký tài liệu bằng các tùy chọn và chứng chỉ được chỉ định.

## Phần kết luận

Trong hướng dẫn này, bạn đã học cách tự động tạo tài liệu và ký trong Java bằng Aspose.Words. Bằng cách làm theo các bước này, bạn có thể hợp lý hóa quy trình quản lý tài liệu, tăng cường bảo mật và đảm bảo tính toàn vẹn của dữ liệu. Để khám phá thêm, hãy cân nhắc tìm hiểu sâu hơn về các tính năng nâng cao hơn của Aspose.Words.

**Các bước tiếp theo:**
- Khám phá các tính năng bổ sung của Aspose.Words như trộn thư hoặc tạo báo cáo.
- Tham khảo tài liệu Aspose để biết hướng dẫn chi tiết và tài liệu tham khảo API.
- Thử nghiệm với các định dạng tài liệu khác nhau được Aspose.Words hỗ trợ.

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}