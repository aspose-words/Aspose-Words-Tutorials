---
date: 2026-01-16
description: Tìm hiểu cách làm nổi bật lỗi chính tả trong Word bằng Aspose.Words cho
  Java, và khám phá cách đặt số ký tự mỗi dòng, tùy chỉnh các tùy chọn hiển thị, và
  dọn dẹp các kiểu dáng.
linktitle: Using Document Options and Settings
second_title: Aspose.Words Java Document Processing API
title: Làm nổi bật lỗi chính tả trong Word bằng Aspose.Words Java
url: /vi/java/document-manipulation/using-document-options-and-settings/
weight: 31
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sử dụng các tùy chọn và cài đặt tài liệu trong Aspose.Words cho Java

## Giới thiệu về việc sử dụng các tùy chọn và cài đặt tài liệu trong Aspose.Words cho Java

Trong hướng dẫn toàn diện này, bạn sẽ học **cách làm nổi bật lỗi chính tả trong Word** bằng Aspose.Words cho Java đồng thời nắm vững các cài đặt liên quan như tùy chọn hiển thị, bố cục trang và dọn dẹp kiểu dáng. Dù bạn là nhà phát triển dày dặn kinh nghiệm hay mới bắt đầu, các ví dụ dưới đây sẽ giúp bạn tạo ra các tài liệu mạnh mẽ, nhận biết lỗi và hoạt động tốt trên mọi phiên bản Word.

## Trả lời nhanh
- **Làm sao tôi có thể làm nổi bật lỗi chính tả trong Word?** Sử dụng `setShowSpellingErrors(true)` trên đối tượng `Document`.  
- **Tôi có thể hiển thị lỗi ngữ pháp không?** Có—gọi `setShowGrammaticalErrors(true)`.  
- **Phương thức nào đặt số ký tự mỗi dòng?** `getPageSetup().setCharactersPerLine(int)`.  
- **API nào tối ưu cho một phiên bản Word cụ thể?** `doc.getCompatibilityOptions().optimizeFor(MsWordVersion)`.  
- **Có cách nào dọn dẹp các kiểu không sử dụng không?** Sử dụng `CleanupOptions` với `setUnusedStyles(true)` và gọi `doc.cleanup(options)`.

## Cách làm nổi bật lỗi chính tả trong Word?

Aspose.Words giúp bạn bật tính năng làm nổi bật lỗi chính tả một cách đơn giản. Khi tài liệu được mở trong Microsoft Word, các từ sai chính tả sẽ xuất hiện với gạch chân đỏ quen thuộc, giúp người dùng cuối nhanh chóng phát hiện vấn đề.

## Cách đặt số ký tự mỗi dòng

Kiểm soát số ký tự mỗi dòng là điều cần thiết cho các bố cục độ rộng cố định (ví dụ: danh sách mã hoặc biểu mẫu cũ). Lớp `PageSetup` cung cấp `setCharactersPerLine(int)` cho phép bạn xác định giá trị này một cách chính xác.

## Cách hiển thị lỗi ngữ pháp

Ngoài lỗi chính tả, bạn cũng có thể bật hiển thị lỗi ngữ pháp. Tính năng này hữu ích cho việc soạn thảo nội dung phải tuân thủ các hướng dẫn phong cách hoặc để xây dựng công cụ kiểm tra lỗi.

## Tối ưu hóa tài liệu cho tính tương thích

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.OptimizeForMsWord.docx");
```

Một khía cạnh quan trọng của quản lý tài liệu là đảm bảo tính tương thích với các phiên bản khác nhau của Microsoft Word. Aspose.Words cho Java cung cấp cách đơn giản để tối ưu hóa tài liệu cho các phiên bản Word cụ thể. Trong ví dụ trên, chúng tôi tối ưu một tài liệu cho Word 2016, đảm bảo khả năng tương thích liền mạch.

## Xác định lỗi ngữ pháp và chính tả

```java
@Test
public void showGrammaticalAndSpellingErrors() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    doc.setShowGrammaticalErrors(true);
    doc.setShowSpellingErrors(true);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ShowGrammaticalAndSpellingErrors.docx");
}
```

Độ chính xác là yếu tố tối quan trọng khi làm việc với tài liệu. Aspose.Words cho Java cho phép bạn làm nổi bật lỗi ngữ pháp và chính tả trong tài liệu, giúp quá trình hiệu đính và chỉnh sửa trở nên hiệu quả hơn.

## Dọn dẹp các kiểu và danh sách không sử dụng

```java
@Test
public void cleanupUnusedStylesAndLists() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Unused styles.docx");
    // Define cleanup options
    CleanupOptions cleanupOptions = new CleanupOptions();
    cleanupOptions.setUnusedLists(false);
    cleanupOptions.setUnusedStyles(true);
    doc.cleanup(cleanupOptions);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupUnusedStylesAndLists.docx");
}
```

Quản lý hiệu quả các kiểu và danh sách trong tài liệu là điều cần thiết để duy trì tính nhất quán. Aspose.Words cho Java cho phép bạn dọn dẹp các kiểu và danh sách không sử dụng, đảm bảo cấu trúc tài liệu gọn gàng và có tổ chức.

## Xóa các kiểu trùng lặp

```java
@Test
public void cleanupDuplicateStyle() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Clean duplicate styles
    CleanupOptions options = new CleanupOptions();
    options.setDuplicateStyle(true);
    doc.cleanup(options);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupDuplicateStyle.docx");
}
```

Các kiểu trùng lặp có thể gây ra sự nhầm lẫn và không nhất quán trong tài liệu. Với Aspose.Words cho Java, bạn có thể dễ dàng xóa các kiểu trùng lặp, duy trì sự rõ ràng và mạch lạc của tài liệu.

## Tùy chỉnh các tùy chọn hiển thị tài liệu

```java
@Test
public void viewOptions() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Customize viewing options
    doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
    doc.getViewOptions().setZoomPercent(50);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ViewOptions.docx");
}
```

Việc tùy chỉnh trải nghiệm xem tài liệu là rất quan trọng. Aspose.Words cho Java cho phép bạn đặt nhiều tùy chọn hiển thị, chẳng hạn như bố cục trang và tỷ lệ phóng đại, để nâng cao khả năng đọc tài liệu.

## Cấu hình bố cục trang tài liệu

```java
@Test
public void documentPageSetup() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Configure page setup options
    doc.getFirstSection().getPageSetup().setLayoutMode(SectionLayoutMode.GRID);
    doc.getFirstSection().getPageSetup().setCharactersPerLine(30);
    doc.getFirstSection().getPageSetup().setLinesPerPage(10);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.DocumentPageSetup.docx");
}
```

Cài đặt bố cục trang chính xác là yếu tố then chốt cho việc định dạng tài liệu. Aspose.Words cho Java cho phép bạn đặt chế độ bố cục, **số ký tự mỗi dòng**, và số dòng mỗi trang, đảm bảo tài liệu của bạn luôn hấp dẫn về mặt hình ảnh.

## Đặt ngôn ngữ chỉnh sửa

```java
@Test
public void addJapaneseAsEditingLanguages() throws Exception
{
    LoadOptions loadOptions = new LoadOptions();
    // Set language preferences for editing
    loadOptions.getLanguagePreferences().addEditingLanguage(EditingLanguage.JAPANESE);
    Document doc = new Document("Your Directory Path" + "No default editing language.docx", loadOptions);
    // Check the overridden editing language
    int localeIdFarEast = doc.getStyles().getDefaultFont().getLocaleIdFarEast();
    System.out.println(localeIdFarEast == (int) EditingLanguage.JAPANESE
            ? "The document either has no any FarEast language set in defaults or it was set to Japanese originally."
            : "The document default FarEast language was set to another than Japanese language originally, so it is not overridden.");
}
```

Ngôn ngữ chỉnh sửa đóng vai trò quan trọng trong quá trình xử lý tài liệu. Với Aspose.Words cho Java, bạn có thể đặt và tùy chỉnh ngôn ngữ chỉnh sửa để phù hợp với nhu cầu ngôn ngữ của tài liệu.

## Kết luận

Trong hướng dẫn này, chúng ta đã khám phá các tùy chọn và cài đặt tài liệu khác nhau có sẵn trong Aspose.Words cho Java. Từ tối ưu hóa và hiển thị lỗi đến dọn dẹp kiểu và tùy chọn hiển thị, thư viện mạnh mẽ này cung cấp khả năng mở rộng rộng rãi để quản lý và tùy chỉnh tài liệu của bạn.

## Câu hỏi thường gặp

### Làm thế nào tôi tối ưu một tài liệu cho một phiên bản Word cụ thể?

Để tối ưu một tài liệu cho một phiên bản Word cụ thể, sử dụng phương thức `optimizeFor` và chỉ định phiên bản mong muốn. Ví dụ, để tối ưu cho Word 2016:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "OptimizedForWord2016.docx");
```

### Làm sao tôi có thể làm nổi bật lỗi ngữ pháp và chính tả trong tài liệu?

Bạn có thể bật hiển thị lỗi ngữ pháp và chính tả trong tài liệu bằng đoạn mã sau:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.setShowGrammaticalErrors(true);
doc.setShowSpellingErrors(true);
doc.save("Your Directory Path" + "ShowErrors.docx");
```

### Mục đích của việc dọn dẹp các kiểu và danh sách không sử dụng là gì?

Việc dọn dẹp các kiểu và danh sách không sử dụng giúp duy trì cấu trúc tài liệu sạch sẽ và có tổ chức. Nó loại bỏ những phần thừa, cải thiện khả năng đọc và tính nhất quán của tài liệu.

### Làm sao tôi có thể xóa các kiểu trùng lặp khỏi tài liệu?

Để xóa các kiểu trùng lặp, sử dụng phương thức `cleanup` với tùy chọn `duplicateStyle` được đặt thành `true`. Dưới đây là một ví dụ:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
CleanupOptions options = new CleanupOptions();
options.setDuplicateStyle(true);
doc.cleanup(options);
doc.save("Your Directory Path" + "CleanedDocument.docx");
```

### Làm thế nào tôi tùy chỉnh các tùy chọn hiển thị cho tài liệu?

Bạn có thể tùy chỉnh các tùy chọn hiển thị tài liệu bằng lớp `ViewOptions`. Ví dụ, để đặt kiểu xem thành bố cục trang và thu phóng 50%:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
doc.getViewOptions().setZoomPercent(50);
doc.save("Your Directory Path" + "CustomView.docx");
```

## Mẹo bổ sung & Những lỗi thường gặp

- **Bật cả kiểm tra chính tả và ngữ pháp** khi bạn cần kiểm tra toàn diện. Bỏ qua một trong các cờ (`setShowGrammaticalErrors` hoặc `setShowSpellingErrors`) có thể khiến lỗi không được phát hiện.  
- **Khi đặt số ký tự mỗi dòng**, nhớ rằng giá trị này tương tác với phông chữ và lề trang đã chọn. Hãy thử nghiệm với bố cục thực tế của tài liệu để tránh các ngắt dòng bất ngờ.  
- **Các thao tác dọn dẹp không thể hoàn tác** trên tệp gốc. Luôn làm việc trên bản sao hoặc sử dụng hệ thống kiểm soát phiên bản để bảo vệ kiểu dáng gốc.  
- **Ưu tiên ngôn ngữ chỉnh sửa** ảnh hưởng đến hành vi kiểm tra chính tả. Nếu bạn làm việc với tài liệu đa ngôn ngữ, hãy thêm tất cả các ngôn ngữ liên quan vào `LanguagePreferences`.

---

**Cập nhật lần cuối:** 2026-01-16  
**Đã kiểm tra với:** Aspose.Words cho Java 24.12  
**Tác giả:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}