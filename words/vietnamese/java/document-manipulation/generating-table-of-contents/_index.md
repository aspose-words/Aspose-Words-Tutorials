---
title: Tạo Mục lục trong Aspose.Words cho Java
linktitle: Tạo mục lục
second_title: API xử lý tài liệu Java Aspose.Words
description: Tìm hiểu cách tạo và tùy chỉnh Mục lục (TOC) bằng Aspose.Words cho Java. Tạo tài liệu có tổ chức và chuyên nghiệp một cách dễ dàng.
weight: 21
url: /vi/java/document-manipulation/generating-table-of-contents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo Mục lục trong Aspose.Words cho Java


## Giới thiệu về Tạo Mục lục trong Aspose.Words cho Java

Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn quy trình tạo Mục lục (TOC) bằng Aspose.Words for Java. TOC là một tính năng quan trọng để tạo tài liệu có tổ chức. Chúng tôi sẽ đề cập đến cách tùy chỉnh giao diện và bố cục của TOC.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn đã cài đặt và thiết lập Aspose.Words for Java trong dự án Java của mình.

## Bước 1: Tạo một tài liệu mới

Đầu tiên, hãy tạo một tài liệu mới để làm việc.

```java
Document doc = new Document();
```

## Bước 2: Tùy chỉnh Kiểu Mục lục

Để tùy chỉnh giao diện của TOC, bạn có thể sửa đổi các kiểu liên quan đến nó. Trong ví dụ này, chúng tôi sẽ làm cho các mục TOC cấp một được in đậm.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

## Bước 3: Thêm nội dung vào tài liệu của bạn

Bạn có thể thêm nội dung của mình vào tài liệu. Nội dung này sẽ được sử dụng để tạo mục lục.

## Bước 4: Tạo mục lục

Để tạo mục lục, hãy chèn trường mục lục vào vị trí mong muốn trong tài liệu của bạn. Trường này sẽ tự động điền dựa trên các tiêu đề và kiểu trong tài liệu của bạn.

```java
// Chèn trường Mục lục vào vị trí mong muốn trong tài liệu của bạn.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

## Bước 5: Lưu tài liệu

Cuối cùng, lưu tài liệu cùng với TOC.

```java
doc.save("your_output_path_here");
```

## Tùy chỉnh Tab Stop trong TOC

Bạn cũng có thể tùy chỉnh các điểm dừng tab trong TOC của mình để kiểm soát cách bố trí số trang. Sau đây là cách bạn có thể thay đổi các điểm dừng tab:

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Nhận tab đầu tiên được sử dụng trong đoạn văn này để căn chỉnh số trang.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Xóa tab cũ.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        //Chèn một tab mới vào vị trí đã sửa đổi (ví dụ: 50 đơn vị về bên trái).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

Bây giờ bạn đã có Mục lục tùy chỉnh trong tài liệu với các điểm dừng tab được điều chỉnh để căn chỉnh số trang.


## Phần kết luận

Trong hướng dẫn này, chúng tôi đã khám phá cách tạo Mục lục (TOC) bằng Aspose.Words for Java, một thư viện mạnh mẽ để làm việc với các tài liệu Word. Một TOC có cấu trúc tốt là điều cần thiết để sắp xếp và điều hướng các tài liệu dài và Aspose.Words cung cấp các công cụ để tạo và tùy chỉnh TOC dễ dàng.

## Câu hỏi thường gặp

### Làm thế nào để thay đổi định dạng của mục lục?

 Bạn có thể sửa đổi các kiểu liên quan đến mức mục lục bằng cách sử dụng`doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`, trong đó X là mức TOC.

### Làm thế nào tôi có thể thêm nhiều cấp độ hơn vào TOC của mình?

Để đưa thêm nhiều cấp độ vào mục lục, bạn có thể sửa đổi trường mục lục và chỉ định số lượng cấp độ mong muốn.

### Tôi có thể thay đổi vị trí dừng tab cho các mục lục cụ thể không?

Có, như được hiển thị trong ví dụ mã ở trên, bạn có thể thay đổi vị trí dừng tab cho các mục lục cụ thể bằng cách lặp qua các đoạn văn và sửa đổi vị trí dừng tab cho phù hợp.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
