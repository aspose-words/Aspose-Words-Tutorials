---
date: 2026-01-06
description: Tìm hiểu cách xóa chân trang khỏi tài liệu Word bằng Aspose.Words cho
  Java, cùng cách xóa ngắt đoạn, ngắt trang và nhiều hơn nữa.
linktitle: Removing Content from Documents
second_title: Aspose.Words Java Document Processing API
title: Cách xóa phần chân trang khỏi tài liệu Word bằng Aspose.Words cho Java
url: /vi/java/document-manipulation/removing-content-from-documents/
weight: 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cách xóa chân trang khỏi tài liệu Word bằng Aspose.Words cho Java

## Giới thiệu về Aspose.Words cho Java

Trong hướng dẫn này, bạn sẽ khám phá **cách xóa chân trang khỏi Word** một cách lập trình bằng Aspose.Words cho Java. Cho dù bạn cần làm sạch các báo cáo đã tạo, loại bỏ thông tin mật, hoặc chỉ đơn giản là dọn dẹp một mẫu, hướng dẫn này sẽ đưa bạn qua các kịch bản xóa nội dung phổ biến nhất—ngắt trang, ngắt đoạn, chân trang và mục lục. Hãy bắt đầu!

## Câu trả lời nhanh
- **Tôi có thể xóa chân trang mà không ảnh hưởng đến nội dung khác không?** Có, API cho phép bạn chỉ mục tiêu các nút chân trang.
- **Tôi có cần giấy phép để chạy các ví dụ này không?** Bản dùng thử miễn phí hoạt động cho phát triển; giấy phép cần thiết cho môi trường sản xuất.
- **Các định dạng Word nào được hỗ trợ?** DOC, DOCX, DOCM và các định dạng dựa trên OOXML.
- **Mã có tương thích với Java 8 và các phiên bản sau không?** Hoàn toàn, thư viện tương thích với Java từ phiên bản 8 trở lên.
- **Làm thế nào để xóa ngắt đoạn?** Xem phần “Cách xóa ngắt đoạn” bên dưới.

## Cái gì là “xóa chân trang khỏi Word”?

Xóa chân trang khỏi tài liệu Word có nghĩa là xóa các nút `HeaderFooter` xuất hiện ở cuối mỗi trang. Thao tác này thường được thực hiện khi bạn muốn tạo bố cục sạch sẽ, chỉ có tiêu đề hoặc khi chân trang chứa dữ liệu nhạy cảm không được chia sẻ.

## Tại sao nên sử dụng Aspose.Words cho Java cho nhiệm vụ này?

Aspose.Words cung cấp mô hình đối tượng cấp cao trừu tượng hoá độ phức tạp của định dạng tệp DOCX. Bạn có thể thao tác các đoạn văn, run, phần, và chân trang chỉ với vài dòng mã Java, mà không cần cài đặt Microsoft Word trên máy chủ.

## Yêu cầu trước
- Java Development Kit (JDK) 8 hoặc mới hơn.
- Thư viện Aspose.Words cho Java (tải xuống từ trang web Aspose).
- Một tài liệu Word mẫu (`Document.docx`) được đặt trong thư mục đã biết.

## Xóa ngắt trang

Ngắt trang kiểm soát việc phân trang nhưng đôi khi cần được loại bỏ. Đoạn mã sau quét mọi đoạn văn, xóa cờ `PageBreakBefore`, và loại bỏ bất kỳ ký tự ngắt trang nào.

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
NodeCollection paragraphs = doc.getChildNodes(NodeType.PARAGRAPH, true);
for (Paragraph para : (Iterable<Paragraph>) paragraphs) {
    if (para.getParagraphFormat().getPageBreakBefore()) {
        para.getParagraphFormat().setPageBreakBefore(false);
    }
    for (Run run : para.getRuns()) {
        if (run.getText().contains(ControlChar.PAGE_BREAK)) {
            run.setText(run.getText().replace(ControlChar.PAGE_BREAK, ""));
        }
    }
}
doc.save("Your Directory Path" + "RemoveContent.RemovePageBreaks.docx");
```

*Pro tip:* Chạy đoạn này trước khi xóa chân trang nếu bạn muốn bố cục một trang.

## Cách xóa ngắt đoạn

Ngắt đoạn chia tài liệu thành các phần độc lập, mỗi phần có tiêu đề, chân trang và cài đặt trang riêng. Để hợp nhất các phần và thực sự **xóa ngắt đoạn**, lặp ngược lại, đưa nội dung của mỗi phần trước vào phần cuối cùng, sau đó xóa phần hiện đã rỗng.

```java
for (int i = doc.getSections().getCount() - 2; i >= 0; i--) {
    doc.getLastSection().prependContent(doc.getSections().get(i));
    doc.getSections().get(i).remove();
}
```

Cách tiếp cận này giữ nguyên mọi nội dung đồng thời loại bỏ sự ngắt cấu trúc.

## Xóa chân trang (Mục tiêu chính: xóa chân trang khỏi Word)

Chân trang thường chứa số trang, ngày tháng hoặc ghi chú mật. Đoạn mã dưới đây xóa **tất cả các loại chân trang**—trang đầu, chính và cả các trang khác—từ mọi phần.

```java
Document doc = new Document("Your Directory Path" + "Header and footer types.docx");
for (Section section : doc.getSections()) {
    HeaderFooter footer = section.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_FIRST);
    footer.remove();
    footer = section.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);
    footer.remove();
    footer = section.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_EVEN);
    footer.remove();
}
doc.save("Your Directory Path" + "RemoveContent.RemoveFooters.docx");
```

Sau khi chạy đoạn mã này, tài liệu kết quả sẽ **không có chân trang**, đạt được mục tiêu chính “xóa chân trang khỏi Word”.

## Xóa mục lục

Mục lục (TOC) được lưu dưới dạng một trường. Để xóa nó, tìm trường TOC theo chỉ mục và loại bỏ nút liên quan.

```java
Document doc = new Document("Your Directory Path" + "Table of contents.docx");
removeTableOfContents(doc, 0);
doc.save("Your Directory Path" + "RemoveContent.RemoveToc.doc");
```

*(Phương thức `removeTableOfContents` là một phần của các ví dụ Aspose.Words và loại bỏ nút TOC được chỉ định.)*

## Các vấn đề thường gặp & Khắc phục

| Symptom | Likely Cause | Fix |
|---------|--------------|-----|
| Chân trang vẫn xuất hiện sau khi chạy mã | Tài liệu chứa các cặp **header/footer** không được truy cập (ví dụ: thiếu `FOOTER_FIRST`) | Lặp qua tất cả các giá trị `HeaderFooterType` hoặc kiểm tra `null` trước khi gọi `remove()`. |
| Bố cục trang thay đổi không mong muốn sau khi xóa ngắt đoạn | Cài đặt trang riêng cho phần (lề, hướng) bị mất | Sao chép cài đặt phần sang phần đích trước khi xóa. |
| `ControlChar.PAGE_BREAK` không được xóa | Tài liệu sử dụng **ngắt đoạn** thay vì ký tự ngắt trang | Sử dụng phương pháp “Cách xóa ngắt đoạn” trước tiên. |

## Câu hỏi thường gặp

**Q: Tôi có thể xóa chỉ các chân trang cụ thể (ví dụ: chỉ chân trang trang đầu) không?**  
A: Có. Lấy chân trang theo loại của nó (`FOOTER_FIRST`) và gọi `remove()` chỉ trên đối tượng đó.

**Q: Làm thế nào để xóa ngắt đoạn mà không hợp nhất nội dung?**  
A: Bạn có thể xóa trực tiếp một nút `Section` nếu không cần giữ lại nội dung của nó, nhưng lưu ý rằng bất kỳ header/footer nào gắn với phần đó cũng sẽ bị mất.

**Q: Có thể lập trình phát hiện xem tài liệu có chứa TOC hay không trước khi cố gắng xóa không?**  
A: Sử dụng `doc.getRange().getFields()` và kiểm tra các trường có loại `FieldType.FIELD_TABLE_OF_CONTENTS`.

**Q: Aspose.Words có hỗ trợ xóa chân trang khỏi các tệp Word được mã hóa không?**  
A: Có, chỉ cần mở tài liệu bằng mật khẩu: `new Document(path, new LoadOptions(password))`.

**Q: Xóa chân trang có ảnh hưởng đến việc phân trang của tài liệu không?**  
A: Xóa chân trang không thay đổi số trang trừ khi chân trang tự nó chứa trường số trang. Nếu bạn cần đánh số lại các trang, hãy cập nhật các trường số trang cho phù hợp.

## Kết luận

Chúng tôi đã trình bày mọi thứ bạn cần để **xóa chân trang khỏi tài liệu Word** bằng Aspose.Words cho Java, cùng với các nhiệm vụ liên quan như xóa ngắt trang, **cách xóa ngắt đoạn**, và loại bỏ mục lục. Bằng cách tận dụng các đoạn mã này, bạn có thể tạo ra các tài liệu sạch sẽ, chuyên nghiệp, phù hợp với yêu cầu của ứng dụng của mình.

---

**Last Updated:** 2026-01-06  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
