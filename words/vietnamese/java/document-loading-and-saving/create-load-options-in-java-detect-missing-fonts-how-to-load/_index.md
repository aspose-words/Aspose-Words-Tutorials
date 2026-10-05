---
category: general
date: 2026-02-18
description: Tạo các tùy chọn tải trong Java để phát hiện phông chữ thiếu và tìm hiểu
  cách tải tệp DOCX với callback cảnh báo.
draft: false
keywords:
- create load options
- detect missing fonts
- how to load docx
- Aspose.Words warning callback
- Java document processing
language: vi
og_description: Tạo các tùy chọn tải trong Java để phát hiện phông chữ thiếu và tìm
  hiểu cách tải tệp DOCX với callback cảnh báo.
og_title: Tạo tùy chọn tải trong Java – Phát hiện phông chữ thiếu và cách tải DOCX
tags:
- java
- aspose-words
- document-processing
title: Tạo tùy chọn tải trong Java – Phát hiện phông chữ thiếu và cách tải DOCX
url: /vi/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo Load Options trong Java – Phát hiện Phông chữ Thiếu & Cách Tải DOCX

Bạn đã bao giờ tự hỏi làm thế nào **tạo load options** không chỉ đọc một file DOCX mà còn thông báo khi một phông chữ bị thiếu chưa? Bạn không phải là người duy nhất. Các phông chữ thiếu có thể biến một tài liệu được định dạng hoàn hảo thành một mớ hỗn độn, và việc phát hiện sớm chúng sẽ tiết kiệm hàng giờ gỡ lỗi. Trong tutorial này, chúng ta sẽ đi qua các bước chính xác để **phát hiện phông chữ thiếu** đồng thời chỉ cho bạn **cách tải file DOCX** bằng một callback cảnh báo tùy chỉnh.

## Những gì bạn sẽ học

- Cách khởi tạo `LoadOptions` và cấu hình một warning handler.  
- Tại sao callback cảnh báo lại quan trọng để bắt các vấn đề thay thế phông chữ.  
- Đoạn mã chính xác để **tải một file DOCX** một cách an toàn, cùng một vài mẹo thực tiễn cho các dự án thực tế.  
- Xử lý các trường hợp biên, như đối phó với các loại warning khác hoặc tải PDF bằng cùng một cách tiếp cận.

Không cần tài liệu bên ngoài—mọi thứ bạn cần đều có ở đây.

## Điều kiện tiên quyết

- Java 17 hoặc mới hơn (API vẫn hoạt động trên các phiên bản cũ hơn, nhưng 17 là lựa chọn tối ưu).  
- Thư viện Aspose.Words for Java đã được thêm vào dự án (`aspose-words-x.x.jar`).  
- Hiểu biết cơ bản về xử lý ngoại lệ trong Java.  

Nếu bạn đã có những điều trên, hãy bắt đầu.

![Sơ đồ hiển thị luồng tạo load options, thiết lập callback cảnh báo và tải file DOCX](/images/create-load-options-diagram.png){: .center-image alt="Sơ đồ luồng tạo Load Options"}

## Bước 1: Tạo Load Options (Cách tải DOCX)

Điều đầu tiên bạn cần làm là **tạo load options**. Đối tượng này chỉ cho Aspose.Words cách hành xử khi mở một file. Hãy nghĩ nó như một bộ hướng dẫn bạn đưa cho thư viện trước khi nó thậm chí nhìn thấy file DOCX.

```java
// Step 1: Instantiate LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

Tại sao không chỉ gọi `new Document("file.docx")`? Bởi vì nếu không có `LoadOptions` bạn sẽ mất khả năng phản hồi các cảnh báo—như phông chữ thiếu—cho đến khi tài liệu đã được tải, điều này có thể quá muộn đối với một số quy trình làm việc.

## Bước 2: Thiết lập Warning Callback để Phát hiện Phông chữ Thiếu

Bây giờ chúng ta gắn một callback sẽ được gọi mỗi khi Aspose.Words gặp một tình huống muốn cảnh báo bạn. Trong trường hợp của chúng ta, chúng ta quan tâm đến `WarningType.FONT_SUBSTITUTION`.

```java
// Step 2: Register a warning callback
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // React only to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Missing font detected: " + info.getDescription());
        }
    }
});
```

Một vài lưu ý:

- **Tại sao cần callback?** Nó chạy *trong quá trình* tải, cho bạn cơ hội ghi log hoặc thậm chí hủy thao tác trước khi tài liệu được tạo hoàn toàn.  
- **Tại sao kiểm tra `WarningType.FONT_SUBSTITUTION`?** Đó là giá trị enum chính xác mà Aspose.Words dùng cho các trường hợp phông chữ thiếu. Các loại warning khác (ví dụ, `TABLE_STRUCTURE`) cũng có thể được lọc tương tự nếu bạn cần.  
- **Mẹo hiệu năng:** Callback nhẹ, tránh thực hiện I/O nặng bên trong. Nếu cần ghi vào file, hãy xếp hàng các thông điệp và flush chúng sau khi tải xong.

## Bước 3: Tải file DOCX với các Options đã cấu hình

Với các options và callback đã sẵn sàng, bạn cuối cùng có thể tải DOCX. Đây là phần trả lời **cách tải docx** đồng thời tôn trọng các cảnh báo bạn đã thiết lập.

```java
// Step 3: Load the document using the configured LoadOptions
try {
    Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
    System.out.println("Document loaded successfully.");
} catch (Exception e) {
    System.err.println("Failed to load document: " + e.getMessage());
}
```

**Điều gì xảy ra phía sau?** Khi file được stream vào, Aspose.Words kiểm tra từng tham chiếu phông chữ. Nếu một phông chữ được tham chiếu chưa được cài đặt, nó sẽ kích hoạt callback cảnh báo mà chúng ta đã định nghĩa trước đó. Bạn sẽ thấy đầu ra như:

```
Missing font detected: Font 'Calibri' is not installed. Substituted with 'Arial'.
Document loaded successfully.
```

Phản hồi ngay lập tức này vô giá khi bạn xử lý hàng loạt file trên server.

## Ví dụ Hoàn chỉnh

Kết hợp tất cả lại, đây là một chương trình tự chứa bạn có thể sao chép‑dán vào IDE.

```java
import com.aspose.words.*;

public class DetectMissingFonts {
    public static void main(String[] args) {
        // 1️⃣ Create LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register warning callback to detect missing fonts
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Missing font: " + info.getDescription());
                }
            }
        });

        // 3️⃣ Load the DOCX using the configured options
        try {
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
            System.out.println("DOCX loaded – you can now work with it.");
        } catch (Exception ex) {
            System.err.println("Error loading DOCX: " + ex.getMessage());
        }
    }
}
```

**Kết quả mong đợi**

```
Missing font: Font 'Times New Roman' is not installed. Substituted with 'Arial'.
DOCX loaded – you can now work with it.
```

Nếu file không có phông chữ thiếu, callback sẽ im lặng và dòng “DOCX loaded” sẽ xuất hiện.

## Mẹo Chuyên nghiệp & Các Trường hợp Biên

| Tình huống | Cách xử lý |
|-----------|------------|
| **Nhiều phông chữ thiếu** | Callback sẽ được kích hoạt cho mỗi phông chữ, vì vậy bạn sẽ nhận được một dòng cho mỗi phông. Gom chúng vào một `List<String>` nếu cần tóm tắt sau này. |
| **Bạn cũng muốn bắt các warning khác** | Thêm các nhánh `else if` cho `WarningType.TABLE_STRUCTURE`, `WarningType.UNKNOWN_FILE_FORMAT`, v.v. |
| **Tải các file DOCX lớn** | Sử dụng `LoadOptions.setLoadFormat(LoadFormat.DOCX)` để gợi ý định dạng và tăng tốc độ phát hiện. |
| **Chạy trong dịch vụ web** | Tránh `System.out.println`; thay vào đó, tiêm một logger (`SLF4J`, `Log4j`) vào bên trong callback. |
| **Phông chữ được cài đặt tại thời gian chạy** | Sau khi phát hiện phông chữ thiếu, bạn có thể tải chúng một cách lập trình qua `GraphicsEnvironment.registerFont(...)` và tải lại tài liệu. |

## Tại sao Cách Tiếp Cận Này Thắng hơn Phương pháp “Chỉ Try‑Catch”

Nhiều nhà phát triển chỉ bọc `new Document(...)` trong một khối try‑catch, hy vọng một ngoại lệ sẽ thông báo về phông chữ thiếu. Thật không may, Aspose.Words xem việc thay thế phông chữ là một *warning*, không phải lỗi, vì vậy không có ngoại lệ nào được ném. Bằng cách **tạo load options** và gắn một warning callback, bạn có được cái nhìn quyết đoán về các vấn đề phông chữ mà không làm giảm hiệu năng.

## Các Bước Tiếp Theo

- **Phát hiện phông chữ thiếu trong PDF** – mẫu `LoadOptions` tương tự cũng hoạt động cho PDF, chỉ cần thay đổi đường dẫn file và định dạng tải.  
- **Tự động cài đặt phông chữ** – kết hợp callback với script tải phông chữ thiếu từ kho chung.  
- **Khám phá các loại warning khác** – Aspose.Words có thể cảnh báo về các thẻ đã lỗi thời, bảng phức tạp, và nhiều hơn nữa.  

Hãy thử nghiệm: thay thế constructor `Document` bằng một stream (`new Document(InputStream, loadOptions)`) nếu bạn đang làm việc với dữ liệu trong bộ nhớ, hoặc chuỗi nhiều callback bằng mẫu composite cho các pipeline xử lý quy mô lớn.

---

### TL;DR

Chúng tôi đã chỉ cho bạn cách **tạo load options** trong Java, thiết lập một callback **phát hiện phông chữ thiếu**, và cuối cùng **tải một file DOCX** một cách an toàn. Chỉ với ba bước ngắn gọn, bạn đã có một mẫu có thể tái sử dụng trong bất kỳ dự án Aspose.Words nào.

Có câu hỏi về các định dạng file khác hoặc cần trợ giúp tùy chỉnh callback cho môi trường của bạn? Hãy để lại bình luận bên dưới, và chúc bạn lập trình vui vẻ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}