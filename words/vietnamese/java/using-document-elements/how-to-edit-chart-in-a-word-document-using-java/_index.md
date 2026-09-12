---
category: general
date: 2026-09-11
description: Cách chỉnh sửa biểu đồ trong tài liệu Word bằng Java – học cách cập nhật
  cài đặt biểu đồ, bật lưới biểu đồ, thay đổi tùy chọn biểu đồ và lưu tài liệu đã
  cập nhật.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- update chart settings
- save updated document
- change chart options
- enable chart gridlines
language: vi
lastmod: 2026-09-11
og_description: Cách chỉnh sửa biểu đồ trong tài liệu Word bằng Java. Hãy làm theo
  hướng dẫn này để cập nhật cài đặt biểu đồ, bật lưới biểu đồ, thay đổi tùy chọn biểu
  đồ và lưu tài liệu đã cập nhật.
og_image_alt: Screenshot of a Word document showing a chart with gridlines enabled
og_title: Cách chỉnh sửa biểu đồ trong tài liệu Word bằng Java – hướng dẫn đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  headline: How to edit chart in a Word document using Java
  type: TechArticle
- description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  name: How to edit chart in a Word document using Java
  steps:
  - name: Expected result
    text: 'When you open `output.docx`:'
  - name: What if the document has no chart?
    text: 'Attempting to cast a non‑chart shape will throw a `ClassCastException`.
      Guard against this by checking the shape type:'
  - name: How to edit a specific chart instead of the first one?
    text: 'Iterate through `shapes` and match a known title or an alternative identifier:'
  - name: Can I disable gridlines again later?
    text: 'Yes, simply set the property to `false`:'
  - name: Does this work with `.doc` (binary) files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. However, some newer chart features (like graduations) are only
      stored in the OOXML format, so you’ll see the effect only when saving as `.docx`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Cách chỉnh sửa biểu đồ trong tài liệu Word bằng Java
url: /vi/java/using-document-elements/how-to-edit-chart-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách chỉnh sửa biểu đồ trong tài liệu Word bằng Java

Nếu bạn cần **cách chỉnh sửa biểu đồ** trong một tệp Word, hướng dẫn này sẽ chỉ cho bạn các bước chính xác. Bạn sẽ học cách cập nhật cài đặt biểu đồ, bật lưới biểu đồ, thay đổi các tùy chọn biểu đồ và cuối cùng **lưu tài liệu đã cập nhật** mà không làm mất bất kỳ định dạng nào.

Làm việc với biểu đồ một cách lập trình thường cảm thấy như một thao tác hộp đen, đặc biệt khi bạn muốn tinh chỉnh các chi tiết hình ảnh như các đường chia (graduations) hoặc lưới. Bài hướng dẫn này bao gồm mọi thứ bạn cần biết, từ việc tải tài liệu đến việc lưu các thay đổi. Không cần công cụ bên ngoài—chỉ cần thư viện Aspose.Words for Java (phiên bản 24.9 trở lên).

Khi đọc xong bài viết này, bạn sẽ có thể:

* Tải một tệp `.docx` có chứa biểu đồ.
* Xác định hình dạng biểu đồ và sửa đổi các thuộc tính của nó.
* Bật lưới biểu đồ (graduations) và điều chỉnh các tùy chọn khác.
* **Lưu tài liệu đã cập nhật** vào một tệp mới.

## Yêu cầu trước

* Java 17 hoặc mới hơn đã được cài đặt trên máy của bạn.  
* Maven hoặc Gradle để quản lý các phụ thuộc.  
* Aspose.Words for Java 24.9+ (phiên bản đã giới thiệu `setShowGraduations`).  
* Một tài liệu Word (`input.docx`) đã chứa ít nhất một biểu đồ.

Nếu bạn chưa quen với Aspose.Words, hãy nghĩ tới nó như một API đầy đủ tính năng cho phép bạn đọc, sửa đổi và ghi lại các tài liệu Word một cách lập trình—tương tự như cách bạn thao tác DOM trong trình duyệt web.

## Bước 1: Thiết lập dự án và nhập thư viện

Tạo một dự án Maven mới hoặc thêm phụ thuộc vào dự án hiện có:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

> **Mẹo chuyên nghiệp:** Sử dụng phiên bản ổn định mới nhất để đảm bảo bạn có phương thức `setShowGraduations`. Các phiên bản cũ hơn sẽ không biên dịch được.

## Bước 2: Tải tài liệu Word có chứa biểu đồ

Hành động đầu tiên trong bất kỳ quy trình **cách chỉnh sửa biểu đồ** nào là tải tệp nguồn. Aspose.Words đại diện cho toàn bộ tài liệu bằng lớp `Document`.

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // Replace with the actual path to your input file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document into memory
        Document doc = new Document(inputPath);
```

Đối tượng `Document` cho phép bạn truy cập mọi nút bên trong tệp, bao gồm hình dạng, bảng và đoạn văn.  

## Bước 3: Xác định hình dạng biểu đồ đầu tiên trong tài liệu

Biểu đồ được lưu dưới dạng các nút `Shape` mà trình render của chúng là một `Chart`. Để chỉnh sửa biểu đồ, bạn phải lấy được nút đó trước.

```java
        // Find all shape nodes (including charts)
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);

        // Assume the first shape is a chart; adjust the index if needed
        Shape chartShape = (Shape) shapes.get(0);

        // Cast the shape renderer to Chart
        Chart chart = (Chart) chartShape.getChart();
```

Nếu tài liệu chứa nhiều biểu đồ, hãy lặp qua `shapes` và kiểm tra `chartShape.getChart() != null` trước khi ép kiểu. Điều này ngăn ngừa `ClassCastException` và đảm bảo bạn **thay đổi tùy chọn biểu đồ** chỉ trên các đối tượng biểu đồ hợp lệ.

## Bước 4: Bật lưới biểu đồ (graduations) – thuộc tính mới trong phiên bản 24.9

Thuộc tính `setShowGraduations` bật/tắt hiển thị các đường lưới phụ trên trục giá trị. Việc bật chúng thường cải thiện khả năng đọc cho các bộ dữ liệu dày đặc.

```java
        // Turn on gridlines (graduations) for the value axis
        chart.setShowGraduations(true);
```

> **Tại sao lại quan trọng:** Lưới cung cấp cho người xem một tham chiếu trực quan cho mỗi điểm dữ liệu, giúp nhận diện xu hướng dễ dàng hơn. Mặc định là `false`, vì vậy bạn phải bật chúng một cách rõ ràng khi cần.

Bạn cũng có thể tùy chỉnh các khía cạnh khác, chẳng hạn như lưới chính, tiêu đề trục, hoặc vị trí chú giải. Dưới đây là ví dụ thay đổi tiêu đề biểu đồ và vị trí chú giải—cả hai đều thuộc **thay đổi tùy chọn biểu đồ**.

```java
        // Change the chart title
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);

        // Move the legend to the bottom
        chart.getLegend().setPosition(LegendPosition.BOTTOM);
```

## Bước 5: Lưu tài liệu với các cài đặt biểu đồ đã cập nhật

Sau khi chỉnh sửa biểu đồ, hãy lưu các thay đổi. Bước này hoàn thành giai đoạn **lưu tài liệu đã cập nhật**.

```java
        // Replace with the desired output path
        String outputPath = "YOUR_DIRECTORY/output.docx";

        // Save the modified document
        doc.save(outputPath);
        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

Chạy chương trình sẽ tạo ra `output.docx` trong đó biểu đồ hiện hiển thị lưới, tiêu đề mới và chú giải được di chuyển. Mở tệp trong Microsoft Word để xác nhận các thay đổi về hình ảnh.

## Mã nguồn đầy đủ (có thể chạy)

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the Word document that contains a chart
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Locate the first chart shape in the document
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
        Shape chartShape = (Shape) shapes.get(0);
        Chart chart = (Chart) chartShape.getChart();

        // 3️⃣ Enable chart gridlines (graduations)
        chart.setShowGraduations(true);

        // 4️⃣ Change chart options (title and legend)
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);
        chart.getLegend().setPosition(LegendPosition.BOTTOM);

        // 5️⃣ Save the document with the updated chart settings
        String outputPath = "YOUR_DIRECTORY/output.docx";
        doc.save(outputPath);

        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

### Kết quả mong đợi

Khi bạn mở `output.docx`:

* Biểu đồ hiển thị các đường lưới phụ trên trục giá trị.  
* Tiêu đề là **“Sales Overview 2026”**.  
* Chú giải xuất hiện ở phía dưới biểu đồ.

Nếu biểu đồ gốc đã có lưới, giao diện sẽ không thay đổi, chứng tỏ mã của bạn **idempotent**.

## Câu hỏi thường gặp và xử lý các trường hợp đặc biệt

### Nếu tài liệu không có biểu đồ thì sao?

Cố gắng ép kiểu một hình dạng không phải biểu đồ sẽ gây ra `ClassCastException`. Hãy kiểm tra loại hình dạng trước:

```java
if (chartShape.getShapeType() == ShapeType.CHART) {
    Chart chart = (Chart) chartShape.getChart();
    // proceed with modifications
}
```

### Làm sao chỉnh sửa một biểu đồ cụ thể thay vì biểu đồ đầu tiên?

Lặp qua `shapes` và so sánh tiêu đề đã biết hoặc một định danh thay thế:

```java
for (Node node : shapes) {
    Shape shape = (Shape) node;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart c = (Chart) shape.getChart();
        if ("Revenue Q1".equals(c.getTitle().getText())) {
            // modify this chart
        }
    }
}
```

### Có thể tắt lưới lại sau này không?

Có, chỉ cần đặt thuộc tính về `false`:

```java
chart.setShowGraduations(false);
```

### Điều này có hoạt động với tệp `.doc` (binary) không?

Aspose.Words trừu tượng hoá định dạng tệp, vì vậy cùng một đoạn mã hoạt động cho cả `.doc` và `.docx`. Tuy nhiên, một số tính năng biểu đồ mới (như graduations) chỉ được lưu trong định dạng OOXML, vì vậy bạn sẽ chỉ thấy hiệu ứng khi lưu dưới dạng `.docx`.

## Mẹo cho mã chuẩn sản xuất

* **Xác thực đường dẫn đầu vào** – sử dụng `Files.exists(Paths.get(inputPath))` trước khi tải.  
* **Bọc các lời gọi API** trong khối try‑catch để hiển thị chi tiết `Exception`, đặc biệt khi làm việc với tài liệu bị hỏng.  
* **Giải phóng tài nguyên** – mặc dù Aspose.Words quản lý bộ nhớ, việc gọi `doc.close()` (hoặc dùng try‑with‑resources nếu có) có thể giải phóng các handle native sớm hơn.  
* **Kiểm tra phiên bản** – đảm bảo phiên bản thư viện runtime ≥ 24.9 trước khi gọi `setShowGraduations`. Bạn có thể truy vấn `License.getVersion()` nếu cần một biện pháp bảo vệ lập trình.

## Kết luận

Bây giờ bạn đã biết **cách chỉnh sửa biểu đồ** trong tài liệu Word bằng Java. Quy trình—tải tài liệu, xác định biểu đồ, bật lưới biểu đồ, thay đổi tùy chọn biểu đồ, và **lưu tài liệu đã cập nhật**—bao quát các kịch bản phổ biến nhất cho việc thao tác biểu đồ một cách lập trình.  

Từ đây, bạn có thể khám phá các tùy chỉnh bổ sung như thay đổi màu sắc của series dữ liệu, áp dụng kiểu biểu đồ, hoặc xuất biểu đồ ra hình ảnh. Mỗi tác vụ đều theo cùng một mẫu: lấy đối tượng `Chart`, điều chỉnh các thuộc tính, và **lưu tài liệu đã cập nhật**.

Chúc bạn lập trình vui vẻ, và đừng ngại thử nghiệm các cài đặt biểu đồ khác để phù hợp với nhu cầu báo cáo của mình!

## Bạn Nên Học Gì Tiếp Theo?


Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}