---
title: Sử dụng danh sách trong Aspose.Words cho Java
linktitle: Sử dụng danh sách
second_title: API xử lý tài liệu Java Aspose.Words
description: Học cách sử dụng danh sách trong Aspose.Words cho Java với hướng dẫn từng bước này. Tổ chức và định dạng tài liệu của bạn một cách hiệu quả.
weight: 18
url: /vi/java/using-document-elements/using-lists/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Sử dụng danh sách trong Aspose.Words cho Java


Trong hướng dẫn toàn diện này, chúng ta sẽ khám phá cách sử dụng danh sách hiệu quả trong Aspose.Words for Java, một API mạnh mẽ để làm việc với các tài liệu Microsoft Word theo chương trình. Danh sách rất cần thiết để cấu trúc và sắp xếp nội dung trong tài liệu của bạn. Chúng ta sẽ đề cập đến hai khía cạnh chính của việc làm việc với danh sách: khởi động lại danh sách ở mỗi phần và chỉ định các cấp danh sách. Hãy cùng tìm hiểu!

## Giới thiệu về Aspose.Words cho Java

Trước khi bắt đầu làm việc với danh sách, hãy làm quen với Aspose.Words for Java. API này cung cấp cho các nhà phát triển các công cụ để tạo, sửa đổi và thao tác các tài liệu Word trong môi trường Java. Đây là giải pháp đa năng cho các tác vụ từ tạo tài liệu đơn giản đến định dạng phức tạp và quản lý nội dung.

### Thiết lập môi trường của bạn

 Để bắt đầu, hãy đảm bảo bạn đã cài đặt và thiết lập Aspose.Words for Java trong môi trường phát triển của mình. Bạn có thể tải xuống[đây](https://releases.aspose.com/words/java/). 

## Khởi động lại danh sách tại mỗi phần

Trong nhiều trường hợp, bạn có thể cần phải khởi động lại danh sách ở mỗi phần của tài liệu. Điều này có thể hữu ích khi tạo tài liệu có cấu trúc với nhiều phần, chẳng hạn như báo cáo, hướng dẫn hoặc bài báo học thuật.

Sau đây là hướng dẫn từng bước về cách thực hiện điều này bằng Aspose.Words cho Java:

### Khởi tạo tài liệu của bạn: 
Bắt đầu bằng cách tạo một đối tượng tài liệu mới.

```java
Document doc = new Document();
```

### Thêm danh sách được đánh số: 
Thêm danh sách được đánh số vào tài liệu của bạn. Chúng tôi sẽ sử dụng kiểu đánh số mặc định.

```java
doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
```

### Cấu hình cài đặt danh sách: 
\Cho phép danh sách khởi động lại ở mỗi phần.

```java
List list = doc.getLists().get(0);
list.isRestartAtEachSection(true);
```

### Thiết lập DocumentBuilder: 
Tạo DocumentBuilder để thêm nội dung vào tài liệu của bạn.

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.getListFormat().setList(list);
```

### Thêm mục danh sách: 
Sử dụng vòng lặp để thêm các mục danh sách vào tài liệu của bạn. Chúng tôi sẽ chèn ngắt phần sau mục thứ 15.

```java
for (int i = 1; i < 45; i++) {
    builder.writeln(MessageFormat.format("List Item {0}", i));
    if (i == 15)
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
}
```

### Lưu tài liệu của bạn: 
Lưu tài liệu với các tùy chọn mong muốn.

```java
OoxmlSaveOptions options = new OoxmlSaveOptions();
options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);
doc.save(outPath + "RestartListAtEachSection.docx", options);
```

Bằng cách làm theo các bước này, bạn có thể tạo tài liệu với danh sách bắt đầu lại ở mỗi phần, duy trì cấu trúc nội dung rõ ràng và có tổ chức.

## Chỉ định mức danh sách

Aspose.Words for Java cho phép bạn chỉ định các cấp độ danh sách, đặc biệt hữu ích khi bạn cần các định dạng danh sách khác nhau trong tài liệu của mình. Hãy cùng khám phá cách thực hiện điều này:

### Khởi tạo tài liệu của bạn: 
Tạo một đối tượng tài liệu mới.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Tạo danh sách được đánh số: 
Áp dụng mẫu danh sách đánh số từ Microsoft Word.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
```

### Chỉ định mức danh sách: 
Lặp lại qua các cấp danh sách khác nhau và thêm nội dung.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### Tạo danh sách có dấu đầu dòng: 
Bây giờ, chúng ta hãy tạo một danh sách có dấu đầu dòng.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
```

### Chỉ định các cấp độ danh sách có dấu đầu dòng: 
Tương tự như danh sách được đánh số, hãy chỉ định các cấp độ và thêm nội dung.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### Định dạng danh sách dừng: 
Để dừng định dạng danh sách, hãy đặt danh sách thành null.

```java
builder.getListFormat().setList(null);
```

### Lưu tài liệu của bạn: 
Lưu tài liệu.

```java
builder.getDocument().save(outPath + "SpecifyListLevel.docx");
```

Bằng cách làm theo các bước sau, bạn có thể tạo tài liệu với các mức danh sách tùy chỉnh, cho phép bạn kiểm soát định dạng danh sách trong tài liệu của mình.

## Mã nguồn đầy đủ
```java
	string outPath = "Your Output Directory";
 public void restartListAtEachSection() throws Exception
    {
        Document doc = new Document();
        doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
        List list = doc.getLists().get(0);
        list.isRestartAtEachSection(true);
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.getListFormat().setList(list);
        for (int i = 1; i < 45; i++)
        {
            builder.writeln(MessageFormat.format("List Item {0}", i));
            if (i == 15)
                builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        }
        // IsRestartAtEachSection sẽ chỉ được viết nếu mức độ tuân thủ cao hơn OoxmlComplianceCore.Ecma376.
        OoxmlSaveOptions options = new OoxmlSaveOptions(); { options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL); }
        doc.save(outPath + "WorkingWithList.RestartListAtEachSection.docx", options);
    }
    @Test
    public void specifyListLevel() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Tạo danh sách được đánh số dựa trên một trong các mẫu danh sách của Microsoft Word
        //và áp dụng nó vào đoạn văn hiện tại của trình tạo tài liệu.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
        // Có chín cấp độ trong danh sách này, chúng ta hãy thử tất cả nhé.
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // Tạo danh sách có dấu đầu dòng dựa trên một trong các mẫu danh sách của Microsoft Word
        //và áp dụng nó vào đoạn văn hiện tại của trình tạo tài liệu.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // Đây là cách để dừng định dạng danh sách.
        builder.getListFormat().setList(null);
        builder.getDocument().save(outPath + "WorkingWithList.SpecifyListLevel.docx");
    }
    @Test
    public void restartListNumber() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Tạo danh sách dựa trên mẫu.
        List list1 = doc.getLists().add(ListTemplate.NUMBER_ARABIC_PARENTHESIS);
        list1.getListLevels().get(0).getFont().setColor(Color.RED);
        list1.getListLevels().get(0).setAlignment(ListLevelAlignment.RIGHT);
        builder.writeln("List 1 starts below:");
        builder.getListFormat().setList(list1);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        // Để sử dụng lại danh sách đầu tiên, chúng ta cần bắt đầu lại việc đánh số bằng cách tạo một bản sao của định dạng danh sách gốc.
        List list2 = doc.getLists().addCopy(list1);
        // Chúng ta có thể sửa đổi danh sách mới theo bất kỳ cách nào, bao gồm cả việc thiết lập số bắt đầu mới.
        list2.getListLevels().get(0).setStartAt(10);
        builder.writeln("List 2 starts below:");
        builder.getListFormat().setList(list2);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        builder.getDocument().save(outPath + "WorkingWithList.RestartListNumber.docx");
	}
```

## Phần kết luận

Xin chúc mừng! Bạn đã học được cách làm việc với danh sách trong Aspose.Words for Java hiệu quả. Danh sách rất quan trọng để sắp xếp và trình bày nội dung trong tài liệu của bạn. Cho dù bạn cần khởi động lại danh sách ở mỗi phần hay chỉ định cấp độ danh sách, Aspose.Words for Java cung cấp các công cụ bạn cần để tạo tài liệu trông chuyên nghiệp.

Bây giờ bạn có thể tự tin sử dụng các tính năng này để nâng cao nhiệm vụ tạo và định dạng tài liệu của mình. Nếu bạn có bất kỳ câu hỏi nào hoặc cần hỗ trợ thêm, đừng ngần ngại liên hệ với[Diễn đàn cộng đồng Aspose](https://forum.aspose.com/) để được hỗ trợ.

## Câu hỏi thường gặp

### Làm thế nào để cài đặt Aspose.Words cho Java?
 Bạn có thể tải xuống Aspose.Words cho Java từ[đây](https://releases.aspose.com/words/java/) và làm theo hướng dẫn cài đặt trong tài liệu.

### Tôi có thể tùy chỉnh định dạng đánh số của danh sách không?
Có, Aspose.Words for Java cung cấp nhiều tùy chọn để tùy chỉnh định dạng đánh số danh sách. Bạn có thể tham khảo tài liệu API để biết chi tiết.

### Aspose.Words for Java có tương thích với các tiêu chuẩn tài liệu Word mới nhất không?
Có, bạn có thể cấu hình Aspose.Words for Java để tuân thủ nhiều tiêu chuẩn tài liệu Word khác nhau, bao gồm cả ISO 29500.

### Tôi có thể tạo các tài liệu phức tạp với bảng và hình ảnh bằng Aspose.Words cho Java không?
Chắc chắn rồi! Aspose.Words for Java hỗ trợ định dạng tài liệu nâng cao, bao gồm bảng, hình ảnh và nhiều hơn nữa. Kiểm tra tài liệu để biết ví dụ.

### Tôi có thể lấy giấy phép tạm thời cho Aspose.Words cho Java ở đâu?
Bạn có thể xin giấy phép tạm thời[đây](https://purchase.aspose.com/temporary-license/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
