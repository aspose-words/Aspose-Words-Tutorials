---
category: general
date: 2026-06-20
description: Lưu tài liệu Word bằng Aspose.Words trong Java, đồng thời thêm một hình
  chữ nhật và áp dụng bóng. Tìm hiểu cách chèn hình dạng từng bước.
draft: false
keywords:
- save word document
- add rectangle shape
- apply shadow to shape
- how to add shadow
- how to insert shape
language: vi
og_description: Lưu tài liệu Word bằng Aspose.Words Java. Hướng dẫn này chỉ cách thêm
  hình chữ nhật, áp dụng bóng đổ và chèn nó vào đoạn văn.
og_title: Lưu tài liệu Word – Thêm hình chữ nhật và bóng trong Java
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Save Word document using Aspose.Words in Java while adding a rectangle
    shape and applying a shadow. Learn how to insert shape step‑by‑step.
  headline: Save Word Document – Add Rectangle Shape & Shadow in Java
  type: TechArticle
- description: Save Word document using Aspose.Words in Java while adding a rectangle
    shape and applying a shadow. Learn how to insert shape step‑by‑step.
  name: Save Word Document – Add Rectangle Shape & Shadow in Java
  steps:
  - name: '**Compile** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`'
    text: '**Compile** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`'
  - name: '**Execute** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`'
    text: '**Execute** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`'
  - name: '**Open** `shadow.docx` in Microsoft Word or LibreOffice. You should see
      the rectangle with a soft black shadow anchored at the start of the first paragraph.'
    text: '**Open** `shadow.docx` in Microsoft Word or LibreOffice. You should see
      the rectangle with a soft black shadow anchored at the start of the first paragraph.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the target `Section` or `PageSetup` and insert the shape
      into a paragraph located on that page.
    question: Can I add the shape to a specific page?
  - answer: Absolutely. Aspose.Words abstracts the format, so the same code **saves
      a Word document** whether it’s `.doc` or `.docx`.
    question: Does this work with .doc files?
  - answer: 'Replace `ShapeType.RECTANGLE` with `ShapeType.ELLIPSE`. All shadow properties
      remain the same. --- ## Conclusion You now know how to **save a Word document**
      while **adding a rectangle shape**, **applying a shadow**, and **inserting the
      shape** into the first paragraph—all with a handful of clean Ja'
    question: What if I need a different shape, like an ellipse?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word Automation
title: Lưu tài liệu Word – Thêm hình chữ nhật và bóng trong Java
url: /vi/java/images-shapes/save-word-document-add-rectangle-shape-shadow-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lưu tài liệu Word – Thêm hình chữ nhật và bóng trong Java

Bạn đã bao giờ tự hỏi làm thế nào để **lưu một tài liệu Word** sau khi bạn đã tùy chỉnh bố cục của nó? Bạn không đơn độc—hầu hết các nhà phát triển gặp khó khăn này khi họ cần làm giàu một tệp DOCX một cách lập trình. Tin tốt là với Aspose.Words for Java bạn có thể **lưu một tài liệu Word**, chèn một hình chữ nhật ngay nơi bạn muốn, và thậm chí thêm một bóng nhẹ cho hình đó.

Trong tutorial này chúng ta sẽ đi qua toàn bộ quy trình: tải một tệp hiện có, **thêm một hình chữ nhật**, cấu hình **bóng**, chèn hình vào đoạn văn đầu tiên, và cuối cùng **lưu tài liệu Word**. Khi kết thúc, bạn sẽ có một chương trình Java có thể chạy được tạo ra tệp `shadow.docx` hoàn chỉnh—không cần chỉnh sửa thủ công.

> **Bạn sẽ cần**  
> * Java 17 (hoặc bất kỳ JDK nào mới)  
> * Thư viện Aspose.Words for Java (Maven/Gradle hoặc file JAR)  
> * Một tệp DOCX đầu vào (`input.docx`) trong thư mục đã biết  

Nếu bạn đã chuẩn bị những yếu tố cơ bản này, hãy bắt đầu.

---

## Lưu tài liệu Word – Ví dụ Java đầy đủ

Dưới đây là mã nguồn đầy đủ, sẵn sàng để chạy. Sao chép vào IDE của bạn, điều chỉnh đường dẫn, và nhấn **Run**.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class ShadowShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the existing document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Create a rectangle shape (the core of add rectangle shape step)
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);
        rectangle.setHeight(50.0);

        // 3️⃣ Apply shadow to shape – how to add shadow in Aspose.Words
        rectangle.getShadow().setVisible(true);
        rectangle.getShadow().setColor(java.awt.Color.BLACK);
        rectangle.getShadow().setBlurRadius(5.0);
        rectangle.getShadow().setOffsetX(4.0);
        rectangle.getShadow().setOffsetY(4.0);
        rectangle.getShadow().setTransparency(0.3);

        // 4️⃣ Insert shape into the first paragraph – how to insert shape
        Paragraph firstPara = doc.getFirstSection().getBody().getParagraphs().get(0);
        firstPara.appendChild(rectangle);

        // 5️⃣ Save the modified document – the final save word document step
        doc.save("YOUR_DIRECTORY/shadow.docx");
        System.out.println("Document saved successfully as shadow.docx");
    }
}
```

**Kết quả mong đợi:** Sau khi chạy chương trình, mở `shadow.docx`. Bạn sẽ thấy nội dung gốc cộng thêm một hình chữ nhật đen 100 × 50 pt với bóng mềm ngay ở đầu đoạn văn đầu tiên.

---

## Thêm hình chữ nhật vào tài liệu Word

Tại sao lại dùng hình chữ nhật? Hãy nghĩ nó như một điểm neo trực quan—hoàn hảo cho các chú thích, chỗ giữ chỗ, hoặc đồ họa đơn giản. Trong Aspose.Words, lớp `Shape` trừu tượng hoá tất cả các đối tượng vẽ, và `ShapeType.RECTANGLE` cung cấp cho bạn một khung sạch sẽ mà không cần phiền phức nào.

**Các điểm quan trọng khi thêm hình chữ nhật**

- **Đơn vị là điểm** (1 pt = 1/72 in). Điều chỉnh `setWidth`/`setHeight` để phù hợp với bố cục.  
- Hình tồn tại trong cây node của tài liệu, vì vậy bạn có thể chèn nó ở bất kỳ nơi nào cho phép `Paragraph` hoặc `Run`.  
- Bạn có thể tạo kiểu cho hình chữ nhật (đổ màu, màu viền, v.v.) trước khi áp dụng bóng.

> **Mẹo:** Nếu bạn cần nền trong suốt, gọi `rectangle.getFill().setTransparent(true);`.

---

## Áp dụng bóng cho hình

Bóng tạo độ sâu. Đối tượng `Shadow` gắn vào một `Shape` cung cấp các thuộc tính tương ứng trực tiếp với các tùy chọn trong giao diện Word.

| Thuộc tính | Chức năng | Giá trị điển hình |
|------------|-----------|-------------------|
| `setVisible(true)` | Bật bóng | `true` |
| `setColor(Color.BLACK)` | Màu bóng | `Color.BLACK` |
| `setBlurRadius(5.0)` | Độ mềm của các cạnh | `5.0` |
| `setOffsetX(4.0)` / `setOffsetY(4.0)` | Dịch chuyển ngang/dọc | `4.0` mỗi |
| `setTransparency(0.3)` | Độ trong suốt (0 = đục, 1 = trong suốt) | `0.3` |

Khi bạn hỏi **cách áp dụng bóng cho hình**, câu trả lời đơn giản là điều chỉnh sáu thuộc tính này. Bạn có thể thử nghiệm—dịch chuyển lớn hơn tạo cảm giác “nổi lên”, trong khi bán kính mờ cao hơn tạo bóng lan tỏa hơn.

> **Những lỗi thường gặp:** Quên `setVisible(true)` sẽ khiến hình không có bóng ngay cả khi bạn đã cấu hình các thuộc tính khác.

---

## Cách chèn hình vào đoạn văn

Chèn hình không phải là ma thuật; chỉ là thao tác trên node. Phương thức `appendChild` đặt hình ở cuối các node con của đoạn văn. Nếu bạn cần hình trước văn bản, hãy dùng `insertBefore` thay thế.

```java
Paragraph para = doc.getFirstSection().getBody().getParagraphs().get(0);
para.insertBefore(rectangle, para.getFirstChild());
```

Thay đổi nhỏ này trả lời **cách chèn hình** đúng nơi bạn cần—trước bất kỳ run nào hiện có, sau một tiêu đề, hoặc thậm chí bên trong một ô bảng (chỉ cần lấy node `Cell` thích hợp trước).

---

## Chạy mã và xác minh đầu ra

1. **Compile** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`  
2. **Execute** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`  
3. **Open** `shadow.docx` trong Microsoft Word hoặc LibreOffice. Bạn sẽ thấy hình chữ nhật với bóng đen mềm được neo ở đầu đoạn văn đầu tiên.

Nếu hình không xuất hiện, hãy kiểm tra lại:

- Đường dẫn tệp đầu vào có đúng không.  
- Bạn đang dùng phiên bản mới của Aspose.Words (API đã thay đổi nhẹ trước 20.12).  
- Tài liệu thực sự có ít nhất một đoạn văn (nếu không `getParagraphs().get(0)` sẽ ném `IndexOutOfBoundsException`).

---

## Câu hỏi thường gặp (FAQ)

**Q: Tôi có thể thêm hình vào một trang cụ thể không?**  
A: Có. Lấy `Section` hoặc `PageSetup` mục tiêu và chèn hình vào một đoạn văn nằm trên trang đó.

**Q: Điều này có hoạt động với tệp .doc không?**  
A: Hoàn toàn có. Aspose.Words trừu tượng hoá định dạng, vì vậy cùng một đoạn mã **lưu một tài liệu Word** dù là `.doc` hay `.docx`.

**Q: Nếu tôi cần một hình khác, chẳng hạn như hình elip thì sao?**  
A: Thay `ShapeType.RECTANGLE` bằng `ShapeType.ELLIPSE`. Tất cả các thuộc tính bóng vẫn giữ nguyên.

---

## Kết luận

Bây giờ bạn đã biết cách **lưu một tài liệu Word** đồng thời **thêm một hình chữ nhật**, **áp dụng bóng**, và **chèn hình** vào đoạn văn đầu tiên—tất cả chỉ với vài dòng Java sạch sẽ. Mô hình này có thể mở rộng: thay đổi loại hình, tinh chỉnh cài đặt bóng, hoặc đặt hình trong bảng và header. Các khả năng rộng mở tùy theo nhu cầu tự động hoá tài liệu của bạn.

Sẵn sàng cho thử thách tiếp theo? Hãy thử xếp chồng nhiều hình, thêm văn bản bên trong hình chữ nhật, hoặc tạo báo cáo đầy đủ với biểu đồ và watermark. Mỗi nhiệm vụ đều dựa trên những nền tảng đã được trình bày ở đây—vì vậy bạn đã đi trước một bước.

Chúc lập trình vui vẻ, và hy vọng tự động hoá Word của bạn sẽ **không có lỗi bóng**!

## Bạn nên học gì tiếp theo?

Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn thành thạo các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [How to save word as pcl with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pcl-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}