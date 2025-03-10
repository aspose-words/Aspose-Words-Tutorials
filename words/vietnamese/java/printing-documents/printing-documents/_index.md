---
title: In tài liệu trong Aspose.Words cho Java
linktitle: In ấn tài liệu
second_title: API xử lý tài liệu Java Aspose.Words
description: Tìm hiểu cách in tài liệu bằng Aspose.Words cho Java. Hướng dẫn từng bước để in liền mạch trong các ứng dụng Java của bạn.
weight: 10
url: /vi/java/printing-documents/printing-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# In tài liệu trong Aspose.Words cho Java


Nếu bạn đang muốn in tài liệu bằng Aspose.Words for Java, bạn đã đến đúng nơi rồi. Trong hướng dẫn từng bước này, chúng tôi sẽ hướng dẫn bạn quy trình in tài liệu bằng Aspose.Words for Java bằng mã nguồn được cung cấp.

## Giới thiệu

In tài liệu là một tác vụ phổ biến trong nhiều ứng dụng. Aspose.Words for Java cung cấp một API mạnh mẽ để làm việc với các tài liệu Word, bao gồm khả năng in chúng. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn từng bước trong quy trình in tài liệu Word.

## Thiết lập môi trường của bạn

Trước khi tìm hiểu sâu hơn về mã, hãy đảm bảo bạn đã đáp ứng đủ các điều kiện tiên quyết sau:

- Đã cài đặt Java Development Kit (JDK)
- Thư viện Aspose.Words cho Java đã được tải xuống và thêm vào dự án của bạn

## Đang tải tài liệu

 Để bắt đầu, bạn sẽ cần tải tài liệu Word mà bạn muốn in. Thay thế`"Your Document Directory"` với đường dẫn đến tài liệu của bạn và`"Your Output Directory"` với thư mục đầu ra mong muốn.

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Rendering.docx");
```

## Tạo một công việc in

Tiếp theo, chúng ta sẽ tạo một lệnh in để in tài liệu đã tải của mình. Đoạn mã dưới đây khởi tạo một lệnh in và thiết lập các cài đặt máy in mong muốn.

```java
// Tạo lệnh in để in tài liệu của chúng ta.
PrinterJob pj = PrinterJob.getPrinterJob();
// Khởi tạo tập thuộc tính với số trang trong tài liệu.
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// Truyền cài đặt máy in cùng với các thông số khác vào tài liệu in.
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
```

## In tài liệu

Bây giờ chúng ta đã thiết lập lệnh in, đã đến lúc in tài liệu. Đoạn mã sau đây liên kết tài liệu với lệnh in và bắt đầu quá trình in.

```java
// Chuyển tài liệu cần in bằng lệnh in.
pj.setPrintable(awPrintDoc);
pj.print();
```
## Mã nguồn đầy đủ
```java
string dataDir = "Your Document Directory";
Document doc = new Document(dataDir + "Rendering.docx");
// Tạo lệnh in để in tài liệu của chúng ta.
PrinterJob pj = PrinterJob.getPrinterJob();
// Khởi tạo tập thuộc tính với số trang trong tài liệu.
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// Truyền cài đặt máy in cùng với các thông số khác vào tài liệu in.
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
// Chuyển tài liệu cần in bằng lệnh in.
pj.setPrintable(awPrintDoc);
pj.print();
```
Mã nguồn của MultipagePrintDocument
```java
class MultipagePrintDocument implements Printable
{
    private final Document mDocument;
    private final int mPagesPerSheet;
    private final boolean mPrintPageBorders;
    private final AttributeSet mAttributeSet;
    /// <tóm tắt>
    /// Hàm khởi tạo của lớp PrintDocument tùy chỉnh.
    // / </tóm tắt>
    public MultipagePrintDocument(Document document, int pagesPerSheet, boolean printPageBorders,
                                  AttributeSet attributes) {
        if (document == null)
            throw new IllegalArgumentException("document");
        mDocument = document;
        mPagesPerSheet = pagesPerSheet;
        mPrintPageBorders = printPageBorders;
        mAttributeSet = attributes;
    }
    public int print(Graphics g, PageFormat pf, int page) {
        //Chỉ mục bắt đầu và kết thúc của trang được xác định trong tập thuộc tính.
        int[][] pageRanges = ((PageRanges) mAttributeSet.get(PageRanges.class)).getMembers();
        int fromPage = pageRanges[0][0] - 1;
        int toPage = pageRanges[0][1] - 1;
        Dimension thumbCount = getThumbCount(mPagesPerSheet, pf);
        // Tính toán chỉ mục trang sẽ được hiển thị tiếp theo.
        int pagesOnCurrentSheet = (int) (page * (thumbCount.getWidth() * thumbCount.getHeight()));
        // Nếu chỉ số trang lớn hơn tổng phạm vi trang thì không có gì
        // còn nhiều thứ phải hiển thị.
        if (pagesOnCurrentSheet > (toPage - fromPage))
            return Printable.NO_SUCH_PAGE;
        // Tính kích thước của mỗi chỗ giữ chỗ hình thu nhỏ theo điểm.
        Point2D.Float thumbSize = new Point2D.Float((float) (pf.getImageableWidth() / thumbCount.getWidth()),
                (float) (pf.getImageableHeight() / thumbCount.getHeight()));
        // Tính số trang đầu tiên sẽ được in trên tờ giấy này.
        int startPage = pagesOnCurrentSheet + fromPage;
        // Chọn số trang cuối cùng sẽ được in trên tờ giấy này.
        int pageTo = Math.max(startPage + mPagesPerSheet - 1, toPage);
        // Lặp qua các trang đã chọn từ trang hiện tại được lưu trữ để tính toán
        // trang cuối cùng.
        for (int pageIndex = startPage; pageIndex <= pageTo; pageIndex++) {
            // Tính chỉ số cột và chỉ số hàng.
            int rowIdx = (int) Math.floor((pageIndex - startPage) / thumbCount.getWidth());
            int columnIdx = (int) Math.floor((pageIndex - startPage) % thumbCount.getWidth());
            // Xác định vị trí hình thu nhỏ theo tọa độ thế giới (trong trường hợp này là điểm).
            float thumbLeft = columnIdx * thumbSize.x;
            float thumbTop = rowIdx * thumbSize.y;
            try {
                // Tính toán vị trí bắt đầu bên trái và trên cùng.
                int leftPos = (int) (thumbLeft + pf.getImageableX());
                int topPos = (int) (thumbTop + pf.getImageableY());
                // Hiển thị trang tài liệu cho đối tượng Đồ họa bằng cách sử dụng tọa độ đã tính toán
                // và kích thước chỗ giữ hình thu nhỏ.
                // Giá trị trả về hữu ích là tỷ lệ hiển thị của trang.
                float scale = mDocument.renderToSize(pageIndex, (Graphics2D) g, leftPos, topPos, (int) thumbSize.x,
                        (int) thumbSize.y);
                //Vẽ đường viền trang (hình thu nhỏ của trang có thể nhỏ hơn hình thu nhỏ
                // kích thước chỗ giữ chỗ).
                if (mPrintPageBorders) {
                    // Nhận được kích thước thực 100% của trang theo điểm.
                    Point2D.Float pageSize = mDocument.getPageInfo(pageIndex).getSizeInPoints();
                    // Vẽ đường viền xung quanh trang đã chia tỷ lệ bằng hệ số tỷ lệ đã biết.
                    g.setColor(Color.black);
                    g.drawRect(leftPos, topPos, (int) (pageSize.x * scale), (int) (pageSize.y * scale));
                    // Vẽ đường viền xung quanh chỗ giữ hình thu nhỏ.
                    g.setColor(Color.red);
                    g.drawRect(leftPos, topPos, (int) thumbSize.x, (int) thumbSize.y);
                }
            } catch (Exception e) {
                // Nếu có bất kỳ lỗi nào xảy ra trong quá trình kết xuất thì không cần làm gì cả.
                // Thao tác này sẽ vẽ một trang trống nếu có bất kỳ lỗi nào trong quá trình kết xuất.
            }
        }
        return Printable.PAGE_EXISTS;
    }
    private Dimension getThumbCount(int pagesPerSheet, PageFormat pf) {
        Dimension size;
        // Xác định số lượng cột và hàng trên trang tính cho
        // Giấy theo chiều ngang.
        switch (pagesPerSheet) {
            case 16:
                size = new Dimension(4, 4);
                break;
            case 9:
                size = new Dimension(3, 3);
                break;
            case 8:
                size = new Dimension(4, 2);
                break;
            case 6:
                size = new Dimension(3, 2);
                break;
            case 4:
                size = new Dimension(2, 2);
                break;
            case 2:
                size = new Dimension(2, 1);
                break;
            default:
                size = new Dimension(1, 1);
                break;
        }
        // Hoán đổi chiều rộng và chiều cao nếu giấy ở chế độ Dọc.
        if ((pf.getWidth() - pf.getImageableX()) < (pf.getHeight() - pf.getImageableY()))
            return new Dimension((int) size.getHeight(), (int) size.getWidth());
        return size;
	}
}
```

## Phần kết luận

Xin chúc mừng! Bạn đã in thành công một tài liệu Word bằng Aspose.Words for Java. Hướng dẫn từng bước này sẽ giúp bạn tích hợp chức năng in tài liệu vào các ứng dụng Java của mình một cách liền mạch.

## Câu hỏi thường gặp

### Câu hỏi 1: Tôi có thể in các trang cụ thể của tài liệu bằng Aspose.Words cho Java không?

 Có, bạn có thể chỉ định phạm vi trang khi in tài liệu. Trong ví dụ mã, chúng tôi đã sử dụng`attributes.add(new PageRanges(1, doc.getPageCount()))`để in tất cả các trang. Bạn có thể điều chỉnh phạm vi trang khi cần.

### Câu hỏi 2: Aspose.Words cho Java có phù hợp để in hàng loạt không?

Chắc chắn rồi! Aspose.Words for Java rất phù hợp cho các tác vụ in hàng loạt. Bạn có thể lặp qua danh sách các tài liệu và in từng cái một bằng cách sử dụng mã tương tự.

### Câu hỏi 3: Tôi có thể xử lý lỗi in hoặc ngoại lệ như thế nào?

Bạn nên xử lý mọi trường hợp ngoại lệ tiềm ẩn có thể xảy ra trong quá trình in. Kiểm tra tài liệu Aspose.Words for Java để biết thông tin về cách xử lý ngoại lệ.

### Câu hỏi 4: Tôi có thể tùy chỉnh thêm cài đặt in không?

Có, bạn có thể tùy chỉnh cài đặt in để đáp ứng các yêu cầu cụ thể của mình. Khám phá tài liệu Aspose.Words for Java để tìm hiểu thêm về các tùy chọn in có sẵn.

### Câu hỏi 5: Tôi có thể nhận thêm trợ giúp và hỗ trợ cho Aspose.Words for Java ở đâu?

 Để được hỗ trợ và trợ giúp thêm, bạn có thể truy cập[Diễn đàn Aspose.Words cho Java](https://forum.aspose.com/).

---

Bây giờ bạn đã học thành công cách in tài liệu bằng Aspose.Words for Java, bạn có thể bắt đầu triển khai chức năng này trong các ứng dụng Java của mình. Chúc bạn viết mã vui vẻ!
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
