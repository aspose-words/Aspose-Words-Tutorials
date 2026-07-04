---
category: general
date: 2026-05-04
description: Tạo tài liệu Word bằng Java sử dụng Aspose.Words và học cách kiểm tra
  ngữ pháp với LLM tùy chỉnh. Hướng dẫn chi tiết từng bước cho các nhà phát triển
  Java.
draft: false
keywords:
- create word document java
- how to create docx
- how to check grammar
- use custom llm
language: vi
og_description: Tạo tài liệu Word bằng Java và xem cách kiểm tra ngữ pháp bằng mô
  hình ngôn ngữ tùy chỉnh. Hướng dẫn Java đầy đủ với mã có thể chạy.
og_title: Tạo tài liệu Word bằng Java với Kiểm tra Ngữ pháp LLM tùy chỉnh
tags:
- Java
- Aspose.Words
- LLM
title: Tạo tài liệu Word bằng Java với Kiểm tra Ngữ pháp LLM tùy chỉnh
url: /vi/java/ai-machine-learning-integration/create-word-document-java-with-custom-llm-grammar-check/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu word java với Kiểm tra Ngữ pháp LLM Tùy chỉnh

Bạn đã bao giờ tự hỏi làm thế nào để **create word document java** mà tự kiểm tra lại nội dung chưa? Bạn không đơn độc—nhiều nhà phát triển muốn có một quy trình duy nhất tạo ra file *.docx* hoàn chỉnh mà không cần dùng nhiều công cụ. Trong hướng dẫn này, chúng tôi sẽ chỉ cho bạn cách **how to create docx** bằng Aspose.Words, kết nối với một LLM được lưu trữ cục bộ, và cuối cùng là **how to check grammar** một cách tự động. Khi hoàn thành, bạn sẽ có một chương trình Java tự chứa, có khả năng viết, xác thực và lưu tài liệu Word—tất cả trong khi **using custom LLM** các endpoint mà bạn kiểm soát.

## Những gì bạn cần

| Yêu cầu | Lý do quan trọng |
|--------------|----------------|
| Java 17+ (hoặc bất kỳ JDK mới nào) | Các tính năng ngôn ngữ hiện đại và hỗ trợ mô-đun tốt hơn |
| Aspose.Words for Java (phiên bản mới nhất) | Thư viện cho phép bạn **create word document java** file một cách lập trình |
| Máy chủ LLM được lưu trữ cục bộ (ví dụ: Ollama, LMStudio) lắng nghe tại `http://localhost:11434/api/generate` | Cần thiết cho bước **use custom llm** hỗ trợ kiểm tra ngữ pháp |
| Maven hoặc Gradle (chúng tôi sẽ dùng Maven trong ví dụ) | Đơn giản hoá việc quản lý phụ thuộc |
| IDE hoặc trình soạn thảo văn bản (IntelliJ IDEA, VS Code, v.v.) | Giúp việc lập trình và gỡ lỗi dễ dàng hơn |

Nếu bất kỳ mục nào trong số này còn lạ với bạn, đừng lo—mỗi mục đều miễn phí hoặc có phiên bản cộng đồng đủ cho mục đích học tập.

## Bước 1 – Thiết lập dự án Maven của bạn

Để **create word document java** nhanh chóng, bắt đầu với một `pom.xml` Maven tối thiểu. Tệp này sẽ kéo thư viện Aspose.Words và bất kỳ client HTTP nào bạn thích (chúng tôi sẽ dùng Apache HttpClient).

```xml
<!-- pom.xml -->
<project xmlns="http://maven.apache.org/POM/4.0.0" 
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-llm-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- replace with the latest -->
        </dependency>

        <!-- Apache HttpClient for calling the LLM endpoint -->
        <dependency>
            <groupId>org.apache.httpcomponents.client5</groupId>
            <artifactId>httpclient5</artifactId>
            <version>5.2</version>
        </dependency>
    </dependencies>
</project>
```

> **Pro tip:** Nếu bạn đang dùng Gradle, các phụ thuộc tương tự sẽ nằm dưới `implementation` trong `build.gradle`.

Bây giờ chạy `mvn clean install` để tải các jar. Khi quá trình build thành công, bạn đã sẵn sàng viết mã Java để **creates word document java**.

## Bước 2 – Viết lớp Java mà **Creates word document java**

Dưới đây là tệp nguồn đầy đủ, sẵn sàng chạy. Nó thể hiện toàn bộ luồng: khởi tạo tài liệu trống, cấu hình endpoint LLM tùy chỉnh, gọi kiểm tra ngữ pháp, và cuối cùng lưu kết quả.

```java
package com.example.wordllmdemo;

import com.aspose.words.*;
import com.aspose.words.ai.*;

import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;

/**
 * Demonstrates how to create a Word document in Java and run a grammar‑check
 * using a self‑hosted LLM (e.g., Ollama). This example is fully self‑contained
 * and can be executed with a single `java -cp` command after Maven builds.
 */
public class SelfHostedLLMDemo {

    public static void main(String[] args) throws Exception {
        // -----------------------------------------------------------------
        // Step 2.1 – Create an empty Word document
        // -----------------------------------------------------------------
        Document document = new Document(); // this is the object that will become your .docx

        // Add a simple paragraph so the grammar engine has something to work with
        DocumentBuilder builder = new DocumentBuilder(document);
        builder.writeln("Ths sentence has a typo and a grammer error.");

        // -----------------------------------------------------------------
        // Step 2.2 – Configure the custom LLM endpoint (use custom llm)
        // -----------------------------------------------------------------
        AiEndpoint llmEndpoint = new AiEndpoint();
        llmEndpoint.setBaseUrl("http://localhost:11434/api/generate");
        llmEndpoint.setModel("llama3.1:8b"); // make sure this model is available locally

        // Initialise the Document AI engine with the endpoint we just set up
        DocumentAi documentAi = new DocumentAi(llmEndpoint);

        // -----------------------------------------------------------------
        // Step 2.3 – Run grammar checking (how to check grammar)
        // -----------------------------------------------------------------
        // AiModelType.CUSTOM tells the API to forward the request to our LLM
        documentAi.checkGrammar(document, AiModelType.CUSTOM);

        // -----------------------------------------------------------------
        // Step 2.4 – Save the corrected file
        // -----------------------------------------------------------------
        String outputPath = "output/GrammarChecked.docx";
        // Ensure the directory exists
        Files.createDirectories(Path.of("output"));
        document.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

> **Why this works:**  
> * `Document` là lớp cốt lõi của Aspose.Words đại diện cho một *.docx* trong bộ nhớ.  
> * `AiEndpoint` cho mô-đun AI của Aspose biết nơi gửi prompt. Bằng cách chỉ tới `localhost:11434` chúng ta **use custom llm** thay vì dịch vụ đám mây.  
> * `checkGrammar` với `AiModelType.CUSTOM` chuyển văn bản tài liệu tới LLM, nhận văn bản đã sửa và ghi lại các nút Word bên dưới.  
> * Cuối cùng chúng ta gọi `save` để ghi file ra đĩa, cung cấp cho bạn một file Word đã được chỉnh sửa.

### Kết quả mong đợi

Sau khi chạy `mvn exec:java -Dexec.mainClass="com.example.wordllmdemo.SelfHostedLLMDemo"` bạn sẽ thấy:

```
Document saved to output/GrammarChecked.docx
```

Mở file `GrammarChecked.docx` vừa tạo trong Microsoft Word (hoặc LibreOffice). Câu gốc *“Ths sentence has a typo and a grammer error.”* sẽ bây giờ là *“This sentence has a typo and a grammar error.”* – chứng minh rằng bước **how to check grammar** đã thành công.

## Bước 3 – Cách tạo docx với Nội dung Khác nhau (Tùy chọn)

Nếu bạn muốn tạo tài liệu phong phú hơn—bảng, hình ảnh, hoặc văn bản có kiểu dáng—chỉ cần tiếp tục dùng `DocumentBuilder`. Dưới đây là một đoạn mã nhanh minh họa cách thêm tiêu đề và bảng:

```java
// Adding a heading
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Demo Report");

// Adding a 2x2 table
Table table = builder.startTable();
builder.insertCell();
builder.write("Item");
builder.insertCell();
builder.write("Quantity");
builder.endRow();

builder.insertCell();
builder.write("Apples");
builder.insertCell();
builder.write("42");
builder.endRow();
builder.endTable();
```

Bạn có thể chèn đoạn mã này ở bất kỳ vị trí nào giữa khối tạo tài liệu (Bước 2.1) và lời gọi kiểm tra ngữ pháp (Bước 2.3). LLM vẫn sẽ nhận toàn bộ văn bản, vì vậy nó có thể sửa các phần ngôn ngữ tự nhiên trong khi để nguyên các bảng.

## Bước 4 – Xử lý các vấn đề về Endpoint (Sử dụng Custom LLM An toàn)

Khi **using custom llm** các endpoint, một số trục trặc thường gặp:

| Triệu chứng | Nguyên nhân có thể | Cách khắc phục |
|---------|--------------|-----|
| `Connection refused` error | Máy chủ LLM không chạy hoặc cổng sai | Khởi động Ollama (`ollama serve`) và xác minh `http://localhost:11434/api/generate` hoạt động với `curl`. |
| Response JSON missing `completion` field | Tên mô hình không khớp | Đảm bảo mô hình bạn đã thiết lập (`llama3.1:8b`) đã được cài đặt (`ollama list`). |
| Grammar check returns the original text unchanged | Prompt không được LLM nhận diện | Điều chỉnh hệ thống của mô hình |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}