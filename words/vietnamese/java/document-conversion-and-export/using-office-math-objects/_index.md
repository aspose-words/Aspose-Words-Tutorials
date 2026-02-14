---
date: 2026-02-14
description: Tìm hiểu cách hiển thị công thức toán học nội dòng, chèn phương trình
  toán học và thao tác các đối tượng Office Math một cách dễ dàng với Aspose.Words
  for Java.
linktitle: Using Office Math Objects
second_title: Aspose.Words Java Document Processing API
title: Hiển thị công thức toán học nội tuyến với Office Math trong Aspose.Words cho
  Java
url: /vi/java/document-conversion-and-export/using-office-math-objects/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hiển thị Toán học Inline với Office Math trong Aspose.Words cho Java

Trong hướng dẫn toàn diện này, bạn sẽ khám phá cách **hiển thị toán học inline** bằng cách sử dụng các đối tượng Office Math trong Aspose.Words cho Java. Cho dù bạn cần **chèn phương trình toán học** vào báo cáo hay tinh chỉnh định dạng của các công thức phức tạp, hướng dẫn này sẽ dẫn bạn qua từng bước — từ việc tải tài liệu Word đến lưu kết quả cuối cùng.

## Câu trả lời nhanh
- **“display math inline” có nghĩa là gì?** Phương trình xuất hiện trong luồng văn bản, không trên một dòng riêng.  
- **Lớp nào đại diện cho đối tượng toán học?** `OfficeMath` trong API Aspose.Words.  
- **Tôi có thể thay đổi căn chỉnh không?** Có, sử dụng `setJustification` với LEFT, CENTER hoặc RIGHT.  
- **Tôi có cần giấy phép cho tính năng này không?** Cần một giấy phép Aspose.Words cho Java hợp lệ để sử dụng trong môi trường sản xuất.  
- **Phiên bản nào được trình diễn?** Mã hoạt động với phiên bản mới nhất của Aspose.Words cho Java (2026).

## “display math inline” là gì?
Hiển thị toán học inline có nghĩa là phương trình được coi là một phần của văn bản đoạn, cho phép nó tự động xuống dòng cùng với các từ xung quanh. Điều này hữu ích cho các công thức ngắn không nên làm gián đoạn luồng đọc.

## Tại sao sử dụng các đối tượng Office Math trong Aspose.Words cho Java?
- **Kiểm soát chính xác** bố cục phương trình (inline vs. display).  
- **Thao tác lập trình** các phương trình mà không cần mở Word thủ công.  
- **Kết xuất nhất quán** trên các nền tảng, hoàn hảo cho việc tạo báo cáo tự động.

## Yêu cầu trước
Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

- Aspose.Words cho Java đã được cài đặt và tham chiếu trong dự án của bạn.  
- Một tệp Word đã chứa sẵn một phương trình Office Math (ví dụ, `OfficeMath.docx`).  
- Một giấy phép hợp lệ nếu bạn dự định chạy mã ngoài chế độ đánh giá.

## Hướng dẫn từng bước

### Tải tài liệu
Đầu tiên, tải tài liệu chứa phương trình Office Math mà bạn muốn làm việc:

```java
Document doc = new Document("Your Directory Path" + "OfficeMath.docx");
```

### Truy cập đối tượng Office Math
Lấy node Office Math đầu tiên từ tài liệu:

```java
OfficeMath officeMath = (OfficeMath) doc.getChild(NodeType.OFFICE_MATH, 0, true);
```

### Đặt kiểu hiển thị (Inline vs. Display)
Kiểm soát việc phương trình xuất hiện inline cùng với văn bản xung quanh hay trên một dòng riêng. Đối với **display math inline**, sử dụng enum `INLINE`; đối với một dòng riêng, sử dụng `DISPLAY`:

```java
officeMath.setDisplayType(OfficeMathDisplayType.DISPLAY);
```

*Nếu bạn muốn phương trình giữ ở dạng inline, thay `DISPLAY` bằng `INLINE`.*

### Đặt căn chỉnh
Điều chỉnh căn chỉnh của phương trình. Dưới đây chúng tôi căn trái, nhưng bạn cũng có thể chọn `CENTER` hoặc `RIGHT`:

```java
officeMath.setJustification(OfficeMathJustification.LEFT);
```

### Lưu tài liệu đã chỉnh sửa
Cuối cùng, ghi các thay đổi vào một tệp mới:

```java
doc.save("Your Directory Path" + "ModifiedOfficeMath.docx");
```

## Mã nguồn hoàn chỉnh cho việc sử dụng đối tượng Office Math trong Aspose.Words cho Java

```java
        Document doc = new Document("Your Directory Path" + "Office math.docx");
        OfficeMath officeMath = (OfficeMath) doc.getChild(NodeType.OFFICE_MATH, 0, true);
        // OfficeMath display type represents whether an equation is displayed inline with the text or displayed on its line.
        officeMath.setDisplayType(OfficeMathDisplayType.DISPLAY);
        officeMath.setJustification(OfficeMathJustification.LEFT);
        doc.save("Your Directory Path" + "WorkingWithOfficeMath.MathEquations.docx");
```

## Các vấn đề thường gặp & Khắc phục
- **Không tìm thấy phương trình:** Đảm bảo tài liệu thực sự chứa đối tượng Office Math; nếu không, `doc.getChild` sẽ trả về `null`.  
- **Kiểu hiển thị không có hiệu lực:** Kiểm tra bạn đang sử dụng phiên bản mới của Aspose.Words; các phiên bản cũ có thể không hỗ trợ đầy đủ `OfficeMathDisplayType`.  
- **Lỗi giấy phép:** Nếu bạn gặp lỗi giấy phép, hãy kiểm tra lại rằng tệp giấy phép của bạn đã được tải đúng trước khi tạo đối tượng `Document`.

## Câu hỏi thường gặp

**Q: Mục đích của các đối tượng Office Math trong Aspose.Words cho Java là gì?**  
A: Các đối tượng Office Math cho phép bạn đại diện và thao tác các phương trình toán học một cách lập trình, cung cấp cho bạn kiểm soát đầy đủ về hiển thị và định dạng.

**Q: Tôi có thể căn chỉnh các phương trình Office Math khác nhau trong tài liệu không?**  
A: Có, sử dụng phương thức `setJustification` để căn trái, phải hoặc trung tâm.

**Q: Aspose.Words cho Java có phù hợp để xử lý các tài liệu toán học phức tạp không?**  
A: Chắc chắn. Thư viện hỗ trợ đầy đủ các phương trình phức tạp, phân số lồng nhau, ma trận và hơn thế nữa.

**Q: Làm thế nào tôi có thể tìm hiểu thêm về Aspose.Words cho Java?**  
A: Để có tài liệu đầy đủ và tải xuống, hãy truy cập [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

**Q: Tôi có thể tải Aspose.Words cho Java ở đâu?**  
A: Bạn có thể tải Aspose.Words cho Java từ trang web: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/).

---

**Cập nhật lần cuối:** 2026-02-14  
**Kiểm tra với:** Aspose.Words cho Java 24.12 (phiên bản mới nhất tính đến Tháng 2 2026)  
**Tác giả:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}