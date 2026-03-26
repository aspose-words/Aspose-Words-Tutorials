---
category: general
date: 2026-03-25
description: Tạo mô hình AI tùy chỉnh để chỉnh sửa tài liệu Word – học cách làm cho
  văn bản trang trọng hơn, thay thế nội dung đoạn văn và viết lại một đoạn Word bằng
  Aspose.Words AI.
draft: false
keywords:
- create custom ai model
- make text more formal
- replace paragraph text
- edit paragraph with ai
- rewrite word paragraph
language: vi
og_description: Tạo mô hình AI tùy chỉnh để chỉnh sửa tài liệu Word. Tìm hiểu cách
  làm cho văn bản trở nên trang trọng hơn, thay thế nội dung đoạn văn và viết lại
  một đoạn Word bằng Aspose.Words AI.
og_title: Tạo mô hình AI tùy chỉnh – Chỉnh sửa các đoạn văn Word trong Java
tags:
- Aspose.Words
- Java
- AI integration
title: Tạo mô hình AI tùy chỉnh – Chỉnh sửa đoạn văn Word trong Java
url: /vi/java/ai-machine-learning-integration/create-custom-ai-model-edit-word-paragraphs-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo Mô Hình AI Tùy Chỉnh – Chỉnh Sửa Đoạn Văn Bản Word trong Java

Bạn đã bao giờ **tạo mô hình AI tùy chỉnh** để làm mượt một đoạn văn trong tệp Word chưa? Có thể bạn có một loạt hợp đồng nghe hơi thân mật, và bạn muốn làm cho văn bản trở nên trang trọng hơn chỉ bằng một dòng lệnh. Tin tốt là bạn có thể làm điều đó—không cần dịch vụ bên ngoài, không cần SDK nặng, chỉ cần Aspose.Words for Java và một endpoint tương thích OpenAI.

Trong hướng dẫn này, chúng ta sẽ đi qua từng bước cần thiết để **tạo mô hình AI tùy chỉnh**, kết nối nó với máy chủ LLM cục bộ, và sau đó sử dụng nó để *thay thế văn bản đoạn* bằng một phiên bản trang trọng hơn. Khi hoàn thành, bạn sẽ có một chương trình Java có thể **chỉnh sửa đoạn văn bản bằng AI**, viết lại một đoạn Word, và lưu kết quả trở lại đĩa. Không có phần thừa, chỉ có giải pháp thực tế bạn có thể sao chép‑dán vào dự án của mình.

> **Bạn sẽ cần**  
> • Java 17 trở lên (mã có thể biên dịch với các phiên bản cũ hơn, nhưng 17 là lựa chọn tối ưu)  
> • Aspose.Words for Java 23.9 (hoặc bản phát hành mới nhất)  
> • Một máy chủ LLM tương thích OpenAI đang chạy (ví dụ: Ollama, LocalAI) lắng nghe tại `http://localhost:8000/v1`  
> • Tài liệu Word đầu vào (`input.docx`) được đặt trong một thư mục bạn kiểm soát  

Nếu bạn tự hỏi *tại sao phải xây dựng mô hình tùy chỉnh* thay vì gọi trực tiếp OpenAI, câu trả lời là tính linh hoạt: bạn kiểm soát endpoint, có thể thay đổi mô hình mà không cần sửa mã, và giữ các khóa API ra khỏi kho mã nguồn. Hãy bắt đầu.

---

## Tạo Mô Hình AI Tùy Chỉnh – Cài Đặt và Cấu Hình

Đầu tiên chúng ta cần chỉ cho Aspose.Words biết LLM của chúng ta nằm ở đâu. Lớp `AiModelEndpoint` chứa URL và khóa API tùy chọn. Vì chúng ta đang dùng máy chủ cục bộ, khóa có thể để chuỗi rỗng, nhưng tham số này vẫn bắt buộc.

```java
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required
```

> **Mẹo chuyên nghiệp:** Nếu bạn chuyển sang một mô hình được lưu trữ (ví dụ: Azure OpenAI), chỉ cần thay đổi URL và khóa—không cần sửa đổi bất kỳ mã nào khác.

---

## Tải Tài Liệu Word

Bây giờ chúng ta đưa tệp nguồn vào bộ nhớ. `Document` có thể đọc `.docx`, `.doc`, `.rtf`, và nhiều định dạng khác, nhưng trong ví dụ này chúng ta chỉ dùng `.docx`.

```java
        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

Đảm bảo `YOUR_DIRECTORY` trỏ tới một thư mục thực; nếu không bạn sẽ gặp `FileNotFoundException`. Trong một ứng dụng thực tế, bạn có thể truyền đường dẫn qua tham số dòng lệnh hoặc đọc từ tệp cấu hình.

---

## Khởi Tạo Mô Hình AI Tùy Chỉnh

Chúng ta tạo một `AiModel` loại `CUSTOM` và gán endpoint đã định nghĩa ở trên. Điều này báo cho Aspose.Words rằng mọi lời gọi AI sẽ được định tuyến qua máy chủ của chúng ta.

```java
        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);
```

Ở phía sau, Aspose.Words xây dựng một client HTTP nhỏ để giao tiếp với LLM theo schema chat/completion chuẩn của OpenAI. Đó là lý do endpoint phải *tương thích OpenAI*.

---

## Lấy và Viết Lại Đoạn Văn Bản Đầu Tiên

Đây là nơi chúng ta **làm cho văn bản trở nên trang trọng hơn**. Chúng ta lấy đoạn đầu tiên, gửi văn bản thô của nó tới mô hình cùng một prompt, và nhận lại phiên bản đã chỉnh sửa.

```java
        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");
```

Tham số thứ hai (`"Make it more formal"`) là chỉ dẫn chúng ta đưa cho mô hình. Bạn có thể thay thế bằng bất kỳ chỉ thị nào—**thay thế văn bản đoạn**, **tóm tắt**, **dịch**, v.v. Phương thức trả về một chuỗi thuần, mà sau này chúng ta sẽ chèn lại vào tài liệu.

> **Tại sao cách này hoạt động:** `editText` gửi một payload JSON dạng `{ "model": "...", "messages": [{ "role":"user", "content":"<text>\nMake it more formal"}] }`. LLM nhận được đoạn gốc và chỉ dẫn, sau đó trả lời bằng văn bản đã chỉnh sửa.

---

## Thay Thế Nội Dung Đoạn Gốc

Bây giờ chúng ta **thay thế văn bản đoạn** trong mô hình đối tượng Word. Chúng ta xóa mọi `Run` hiện có (các phần tử văn bản cấp thấp) và chèn một `Run` mới chứa chuỗi do AI tạo ra.

```java
        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));
```

Hãy cẩn thận không gọi `firstParagraph.setText()`—phương thức này sẽ xóa mọi định dạng. Việc dùng `Run` giữ nguyên kiểu đoạn (heading, bullet, v.v.) trong khi thay đổi các ký tự thực tế.

---

## Lưu Tài Liệu Đã Chỉnh Sửa

Cuối cùng, chúng ta ghi tài liệu đã sửa trở lại đĩa. Bạn có thể ghi đè lên tệp gốc hoặc, như trong ví dụ này, tạo một bản sao mới.

```java
        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Khi mở `output.docx` bạn sẽ thấy đoạn đầu tiên giờ đã nghe rất trang trọng. Nếu LLM không thực hiện chỉ dẫn một cách hoàn hảo, bạn có thể tinh chỉnh prompt hoặc thử phiên bản mô hình khác.

---

## Ví Dụ Hoàn Chỉnh

Dưới đây là chương trình đầy đủ—sao chép nó vào `LlmDemo.java`, điều chỉnh các đường dẫn, và chạy bằng `javac` + `java`.

```java
import com.aspose.words.*;
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required

        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);

        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");

        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));

        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Kết quả mong đợi:** Mở `output.docx` và bạn sẽ thấy đoạn gốc đã được biến đổi. Ví dụ, một câu thân mật như “We’ll get the thing done soon.” có thể trở thành “We shall complete the task promptly.” Cách diễn đạt cụ thể phụ thuộc vào mô hình bạn đang sử dụng.

---

## Câu Hỏi Thường Gặp & Trường Hợp Cạnh

### Tài liệu của tôi có nhiều phần thì sao?

Mã trên chỉ xử lý *đoạn đầu tiên* của *phần đầu tiên*. Để **chỉnh sửa đoạn văn bản bằng AI** trên toàn bộ tệp, hãy lặp qua `document.getSections()` rồi qua mỗi `section.getBody().getParagraphs()`. Nhớ bỏ qua các đoạn trống, nếu không LLM sẽ nhận chuỗi rỗng và không trả gì.

### Làm sao xử lý các đoạn quá dài vượt quá giới hạn token?

Hầu hết các LLM giới hạn đầu vào khoảng 4 000 token. Nếu một đoạn quá dài, hãy chia nó thành các phần nhỏ hơn trước khi gọi `editText`. Bạn có thể tái sử dụng cùng một instance của `AiModel`; chỉ cần chú ý tới giới hạn tốc độ của máy chủ cục bộ.

### Tôi có thể dùng chỉ thị khác, như “summarize” hoặc “translate to French” không?

Chắc chắn rồi. Tham số thứ hai của `editText` là tự do. Đối với tóm tắt, bạn có thể truyền `"Summarize in one sentence"`. Đối với dịch, `"Translate to French, keep the tone formal"` cũng hoạt động tốt. Tính linh hoạt này cho phép bạn **thay thế văn bản đoạn** trong nhiều kịch bản mà không cần thay đổi mã.

### Mô hình có giữ nguyên định dạng đoạn (phông, màu) không?

Vì chúng ta chỉ thay thế `Run` bên trong cùng một đối tượng `Paragraph`, các kiểu hiện có (cấp heading, danh sách bullet, thụt lề) vẫn được giữ nguyên. Nếu bạn muốn thay đổi kiểu, có thể thao tác với `Paragraph.getParagraphFormat()` sau khi thay thế.

### Máy chủ LLM của tôi yêu cầu HTTPS với chứng chỉ tự ký thì sao?

`AiModelEndpoint` chấp nhận URL dạng `https://`. Nếu chứng chỉ không được tin cậy, bạn cần cấu hình SSL context của Java để tin tưởng nó, hoặc chạy máy chủ với chứng chỉ hợp lệ. Cấu hình này nằm ngoài phạm vi của hướng dẫn nhưng được mô tả chi tiết trong các tài liệu Java SSL.

---

## Mẹo Để Tích Hợp Sẵn Sàng Sản Xuất

| Mẹo | Tại sao quan trọng |
|-----|--------------------|
| **Cache endpoint** | Tạo lại `AiModelEndpoint` cho mỗi yêu cầu sẽ gây overhead. |
| **Batch edits** | Nếu có nhiều đoạn, gửi chúng trong một yêu cầu duy nhất (ví dụ: mảng JSON) để giảm độ trễ. |
| **Validate LLM output** | Luôn kiểm tra chuỗi trả về có null hoặc rỗng trước khi chèn. |
| **Log prompts and responses** | Hữu ích cho việc gỡ lỗi và tuân thủ khi bạn đang viết lại văn bản pháp lý. |
| **Graceful fallback** | Nếu LLM ngưng hoạt động, hãy quay lại đoạn gốc hoặc dùng một thuật toán heuristics đơn giản. |

---

## Kết Luận

Chúng ta đã trình bày cách **tạo mô hình AI tùy chỉnh** với Aspose.Words, kết nối nó tới một endpoint tương thích OpenAI, và sau đó **chỉnh sửa đoạn văn bản bằng AI** để **làm cho văn bản trở nên trang trọng hơn**. Bằng cách thực hiện sáu bước—định nghĩa endpoint, tải tài liệu, khởi tạo mô hình,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}