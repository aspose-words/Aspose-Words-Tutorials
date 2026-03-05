---
category: general
date: 2026-03-04
description: Cách cấu hình LLM cho Document AI và thay thế văn bản trong DOCX bằng
  AI – hướng dẫn từng bước với mã Java đầy đủ.
draft: false
keywords:
- how to configure llm
- replace text in docx
- how to replace text
- how to use document ai
- replace phrase with ai
language: vi
og_description: Cách cấu hình LLM cho Document AI và thay thế văn bản trong DOCX bằng
  AI – hướng dẫn đầy đủ với mã Java có thể chạy.
og_title: Cách cấu hình LLM – Thay thế văn bản trong DOCX bằng AI
tags:
- LLM
- Document AI
- Java
- DOCX
title: How to Configure LLM – Replace Text in DOCX with AI
url: /vi/java/ai-machine-learning-integration/how-to-configure-llm-replace-text-in-docx-with-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách cấu hình LLM – Thay thế văn bản trong DOCX bằng AI

Bạn đã bao giờ tự hỏi **cách cấu hình LLM** để nó có thể chỉnh sửa một tệp Word cho bạn chưa? Bạn không phải là người duy nhất. Nhiều nhà phát triển gặp khó khăn khi cần thay thế một cụm từ trong file `.docx` một cách lập trình mà không mở Microsoft Word. Tin tốt? Với một LLM cục bộ và một lớp bao Document AI nhỏ gọn, bạn có thể thay đổi văn bản trong file DOCX chỉ bằng vài dòng Java.

Trong hướng dẫn này, chúng ta sẽ đi qua toàn bộ quy trình: từ việc thiết lập kết nối LLM, tải một DOCX, đến việc sử dụng **Document AI** để thay thế một cụm từ mục tiêu. Khi kết thúc, bạn sẽ có một ví dụ tự chứa, có thể chạy được mà bạn có thể đưa vào bất kỳ dự án Maven hoặc Gradle nào. Không cần khóa API bên ngoài, không phí đám mây—chỉ cần mô hình của bạn lắng nghe tại `http://localhost:8080/v1`.

> **Cơ hội nhanh:** Nếu bạn đã có một LLM cục bộ (như Llama 3 hoặc Mistral) cung cấp endpoint tương thích OpenAI, đoạn mã dưới đây sẽ hoạt động ngay lập tức.

![Diagram of how to configure LLM for Document AI](/images/configure-llm-diagram.png){: .center-image alt="how to configure llm diagram"}

## Những gì bạn cần

- **Java 17** (hoặc bất kỳ JDK gần đây nào)  
- Một **local LLM** cung cấp endpoint kiểu OpenAI `/v1` (ví dụ: Ollama, LMStudio)  
- **Document AI Java library** (giả sử `com.example:document-ai:1.2.0` trên Maven Central)  
- Một file DOCX mẫu (`input.docx`) được đặt trong một thư mục đã biết  

Nếu bạn thiếu bất kỳ mục nào trong số này, hãy khởi động Ollama nhanh chóng:

```bash
ollama serve &
ollama run llama3
```

Điều này sẽ khởi động một server tại `http://localhost:8080/v1` sẵn sàng nhận yêu cầu.

## Cách cấu hình LLM cho Document AI

Điều đầu tiên chúng ta làm là cho client `DocumentAi` biết nơi tìm mô hình và mô hình nào sẽ sử dụng. Đây là bước **cách cấu hình LLM** mà nhiều hướng dẫn thường bỏ qua.

```java
// Step 1: Set up the LLM connection details
AiModelConfig modelConfig = new AiModelConfig();
modelConfig.setBaseUrl("http://localhost:8080/v1");   // Local server address
modelConfig.setApiKey("dummy");                       // Not needed for local models, but the client expects a value
modelConfig.setModelName("local-llm");                // Replace with your model's identifier
```

*​Tại sao điều này quan trọng:*  
Đối tượng `AiModelConfig` trừu tượng hoá các chi tiết HTTP, cho phép `DocumentAi` tập trung vào nội dung. Nếu bạn chuyển sang nhà cung cấp dịch vụ, bạn chỉ cần thay đổi `baseUrl` và `apiKey`—phần còn lại của mã vẫn không thay đổi.

## Tải và chuẩn bị tài liệu DOCX

Tiếp theo chúng ta đưa file Word vào bộ nhớ. Lớp `Document` xử lý cả `.docx` và `.pdf` ở phía sau, nhưng ở đây chúng ta chỉ quan tâm đến DOCX.

```java
// Step 2: Load the DOCX you want to edit
Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
Document inputDocument = new Document(docPath.toFile());
```

*Mẹo chuyên nghiệp:* Sử dụng đường dẫn tuyệt đối trong quá trình gỡ lỗi để tránh lỗi “file not found”. Khi đã chắc chắn, chuyển lại sang đường dẫn tương đối để tăng tính di động.

## Thay thế văn bản trong DOCX bằng AI

Bây giờ là phần cốt lõi của hướng dẫn—**cách thay thế văn bản** trong file DOCX bằng sự hỗ trợ của AI. Phương thức `replaceText` gửi nội dung tài liệu tới LLM, yêu cầu nó thực hiện việc thay thế, và trả về văn bản đã chỉnh sửa.

```java
// Step 3: Initialise the Document AI client
DocumentAi documentAi = new DocumentAi(modelConfig);

// Step 4: Ask the LLM to replace the target phrase
String oldPhrase = "old phrase";
String newPhrase = "new phrase";

String revisedText = documentAi.replaceText(
        inputDocument,
        oldPhrase,
        newPhrase
);
```

*Điều gì đang diễn ra phía sau?*  
`DocumentAi` chuyển đổi DOCX thành văn bản thuần, tạo một prompt như:

> “Trong tài liệu sau, thay thế mọi lần xuất hiện của ‘old phrase’ bằng ‘new phrase’ và chỉ trả về văn bản đã cập nhật.”

LLM xử lý yêu cầu và gửi lại nội dung đã chỉnh sửa. Cách tiếp cận này hoạt động ngay cả khi cụm từ trải dài qua nhiều run hoặc đoạn—điều mà việc thay thế chuỗi thông thường thường bỏ qua.

## Xác minh và xuất văn bản đã chỉnh sửa

Cuối cùng chúng ta in văn bản đã được AI chỉnh sửa ra console. Trong một ứng dụng thực tế, bạn có thể ghi kết quả trở lại một file DOCX mới, nhưng việc in ra giúp bạn nhanh chóng xác minh.

```java
// Step 5: Show the AI‑revised output
System.out.println("AI‑revised text:");
System.out.println("-----------------------------------");
System.out.println(revisedText);
```

**Kết quả mong đợi** (giả sử DOCX gốc chứa “This is the old phrase we want to change.”):

```
AI‑revised text:
-----------------------------------
This is the new phrase we want to change.
```

Nếu bạn thấy cụm từ mới xuất hiện, chúc mừng—**bạn vừa học cách sử dụng Document AI để thay thế một cụm từ bằng AI**.

## Ví dụ hoàn chỉnh hoạt động

Kết hợp mọi thứ lại, đây là một lớp Java đầy đủ, sẵn sàng chạy. Bạn có thể sao chép‑dán vào `src/main/java/com/example/ReplaceInDocx.java`.

```java
package com.example;

import com.example.documentai.AiModelConfig;
import com.example.documentai.DocumentAi;
import com.example.documentai.Document;

import java.nio.file.Path;
import java.nio.file.Paths;

/**
 * Demonstrates how to configure LLM, load a DOCX, and replace a phrase using Document AI.
 */
public class ReplaceInDocx {

    public static void main(String[] args) {
        // 1️⃣ Configure the local LLM connection
        AiModelConfig modelConfig = new AiModelConfig();
        modelConfig.setBaseUrl("http://localhost:8080/v1");
        modelConfig.setApiKey("dummy");               // Not required for local models
        modelConfig.setModelName("local-llm");        // Change if needed

        // 2️⃣ Load the DOCX you want to modify
        Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
        Document inputDocument = new Document(docPath.toFile());

        // 3️⃣ Create the Document AI client using the configuration
        DocumentAi documentAi = new DocumentAi(modelConfig);

        // 4️⃣ Replace the target phrase with the new phrase using the AI model
        String oldPhrase = "old phrase";
        String newPhrase = "new phrase";

        String revisedText = documentAi.replaceText(
                inputDocument,
                oldPhrase,
                newPhrase
        );

        // 5️⃣ Output the AI‑revised text
        System.out.println("AI‑revised text:");
        System.out.println("-----------------------------------");
        System.out.println(revisedText);
    }
}
```

### Cách chạy

```bash
# Compile
mvn clean compile

# Execute
mvn exec:java -Dexec.mainClass="com.example.ReplaceInDocx"
```

Đảm bảo server LLM đang chạy trước khi bạn thực thi chương trình; nếu không bạn sẽ gặp lỗi timeout kết nối.

## Các trường hợp góc cạnh & những lỗi thường gặp

| Tình huống | Điều cần chú ý | Giải pháp đề xuất |
|-----------|-------------------|---------------|
| **Cụm từ không tìm thấy** | LLM trả về văn bản gốc không thay đổi. | Kiểm tra lại chính tả và phân biệt chữ hoa/thường; bạn có thể thêm `ignoreCase:true` vào prompt nếu wrapper của bạn hỗ trợ. |
| **Tài liệu lớn (>5 MB)** | Kích thước prompt có thể vượt quá giới hạn token của mô hình. | Chia DOCX thành các phần, xử lý từng phần riêng biệt, sau đó nối kết quả lại. |
| **LLM cục bộ trả lỗi** | Thường do tên mô hình không khớp. | Xác minh tên mô hình trong giao diện LLM (`ollama list`) khớp với `modelConfig.setModelName`. |
| **Ký tự Unicode bị lỗi** | Vấn đề mã hoá khi đọc DOCX. | Đảm bảo runtime Java của bạn sử dụng UTF‑8 (thêm `-Dfile.encoding=UTF-8` vào tham số JVM). |

## Các bước tiếp theo

Bây giờ bạn đã biết **cách thay thế văn bản trong DOCX** bằng AI, bạn có thể muốn khám phá:

- **Cách sử dụng Document AI** cho các tác vụ phức tạp hơn như trích xuất bảng hoặc bảo toàn kiểu dáng.  
- **Thay thế cụm từ bằng AI** trong PDF bằng cách thay đổi đối số của hàm khởi tạo `Document`.  
- **Xử lý hàng loạt**: lặp qua một thư mục chứa các file DOCX và áp dụng cùng một phép thay thế.  

Mỗi mục này dựa trên cùng nền tảng `AiModelConfig` và `DocumentAi`, vì vậy bạn không cần bắt đầu từ đầu.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}