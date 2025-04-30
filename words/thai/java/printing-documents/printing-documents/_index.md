---
"description": "เรียนรู้วิธีพิมพ์เอกสารโดยใช้ Aspose.Words สำหรับ Java คำแนะนำทีละขั้นตอนสำหรับการพิมพ์ที่ราบรื่นในแอปพลิเคชัน Java ของคุณ"
"linktitle": "การพิมพ์เอกสาร"
"second_title": "API การประมวลผลเอกสาร Java ของ Aspose.Words"
"title": "การพิมพ์เอกสารใน Aspose.Words สำหรับ Java"
"url": "/th/java/printing-documents/printing-documents/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การพิมพ์เอกสารใน Aspose.Words สำหรับ Java


หากคุณต้องการพิมพ์เอกสารโดยใช้ Aspose.Words สำหรับ Java คุณมาถูกที่แล้ว ในคู่มือทีละขั้นตอนนี้ เราจะแนะนำคุณเกี่ยวกับกระบวนการพิมพ์เอกสารโดยใช้ Aspose.Words สำหรับ Java โดยใช้โค้ดต้นฉบับที่ให้มา

## การแนะนำ

การพิมพ์เอกสารเป็นงานทั่วไปในแอปพลิเคชันจำนวนมาก Aspose.Words สำหรับ Java มอบ API ที่ทรงพลังสำหรับทำงานกับเอกสาร Word รวมถึงความสามารถในการพิมพ์เอกสาร ในบทช่วยสอนนี้ เราจะแนะนำคุณตลอดขั้นตอนการพิมพ์เอกสาร Word ทีละขั้นตอน

## การตั้งค่าสภาพแวดล้อมของคุณ

ก่อนที่จะเจาะลึกโค้ด โปรดตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:

- ติดตั้ง Java Development Kit (JDK) แล้ว
- ดาวน์โหลดไลบรารี Aspose.Words สำหรับ Java และเพิ่มลงในโปรเจ็กต์ของคุณแล้ว

## การโหลดเอกสาร

ในการเริ่มต้น คุณจะต้องโหลดเอกสาร Word ที่คุณต้องการพิมพ์ แทนที่ `"Your Document Directory"` ด้วยเส้นทางไปยังเอกสารของคุณและ `"Your Output Directory"` พร้อมไดเร็กทอรีเอาท์พุตตามต้องการ

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Rendering.docx");
```

## การสร้างงานพิมพ์

ต่อไปเราจะสร้างงานพิมพ์เพื่อพิมพ์เอกสารที่โหลดไว้ โค้ดด้านล่างนี้จะเริ่มต้นงานพิมพ์และตั้งค่าเครื่องพิมพ์ตามต้องการ

```java
// สร้างงานพิมพ์เพื่อพิมพ์เอกสารของเรา
PrinterJob pj = PrinterJob.getPrinterJob();
// เริ่มต้นชุดแอตทริบิวต์ด้วยจำนวนหน้าในเอกสาร
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// ส่งต่อการตั้งค่าเครื่องพิมพ์พร้อมกับพารามิเตอร์อื่น ๆ ไปยังเอกสารที่จะพิมพ์
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
```

## การพิมพ์เอกสาร

ตอนนี้เราได้ตั้งค่างานพิมพ์เรียบร้อยแล้ว ถึงเวลาพิมพ์เอกสารแล้ว โค้ดสั้นๆ ต่อไปนี้จะเชื่อมโยงเอกสารกับงานพิมพ์และเริ่มกระบวนการพิมพ์

```java
// ส่งเอกสารที่จะพิมพ์โดยใช้บริการพิมพ์งาน
pj.setPrintable(awPrintDoc);
pj.print();
```
## ซอร์สโค้ดที่สมบูรณ์
```java
string dataDir = "Your Document Directory";
Document doc = new Document(dataDir + "Rendering.docx");
// สร้างงานพิมพ์เพื่อพิมพ์เอกสารของเรา
PrinterJob pj = PrinterJob.getPrinterJob();
// เริ่มต้นชุดแอตทริบิวต์ด้วยจำนวนหน้าในเอกสาร
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// ส่งต่อการตั้งค่าเครื่องพิมพ์พร้อมกับพารามิเตอร์อื่น ๆ ไปยังเอกสารที่จะพิมพ์
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
// ส่งเอกสารที่จะพิมพ์โดยใช้บริการพิมพ์งาน
pj.setPrintable(awPrintDoc);
pj.print();
```
ซอร์สโค้ดของ MultipagePrintDocument
```java
class MultipagePrintDocument implements Printable
{
    private final Document mDocument;
    private final int mPagesPerSheet;
    private final boolean mPrintPageBorders;
    private final AttributeSet mAttributeSet;
    /// <สรุป>
    /// ตัวสร้างของคลาส PrintDocument แบบกำหนดเอง
    /// </สรุป> 
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
        // ดัชนีเริ่มต้นและสิ้นสุดของหน้าตามที่กำหนดไว้ในชุดแอตทริบิวต์
        int[][] pageRanges = ((PageRanges) mAttributeSet.get(PageRanges.class)).getMembers();
        int fromPage = pageRanges[0][0] - 1;
        int toPage = pageRanges[0][1] - 1;
        Dimension thumbCount = getThumbCount(mPagesPerSheet, pf);
        // คำนวณดัชนีหน้าที่จะแสดงผลถัดไป
        int pagesOnCurrentSheet = (int) (page * (thumbCount.getWidth() * thumbCount.getHeight()));
        // หากดัชนีหน้ามากกว่าช่วงหน้าทั้งหมดแสดงว่าไม่มีอะไรเกิดขึ้น
        // มีให้แสดงผลเพิ่มเติมอีก
        if (pagesOnCurrentSheet > (toPage - fromPage))
            return Printable.NO_SUCH_PAGE;
        // คำนวณขนาดของช่องว่างรูปขนาดย่อแต่ละจุดเป็นจุด
        Point2D.Float thumbSize = new Point2D.Float((float) (pf.getImageableWidth() / thumbCount.getWidth()),
                (float) (pf.getImageableHeight() / thumbCount.getHeight()));
        // คำนวณจำนวนหน้าแรกที่จะพิมพ์บนแผ่นกระดาษนี้
        int startPage = pagesOnCurrentSheet + fromPage;
        // เลือกหมายเลขหน้าสุดท้ายที่ต้องการพิมพ์บนแผ่นกระดาษนี้
        int pageTo = Math.max(startPage + mPagesPerSheet - 1, toPage);
        // วนซ้ำผ่านหน้าที่เลือกจากหน้าปัจจุบันที่เก็บไว้ไปยังหน้าที่คำนวณ
        // หน้าสุดท้าย.
        for (int pageIndex = startPage; pageIndex <= pageTo; pageIndex++) {
            // คำนวณดัชนีคอลัมน์และแถว
            int rowIdx = (int) Math.floor((pageIndex - startPage) / thumbCount.getWidth());
            int columnIdx = (int) Math.floor((pageIndex - startPage) % thumbCount.getWidth());
            // กำหนดตำแหน่งภาพขนาดย่อในพิกัดโลก (จุดในกรณีนี้)
            float thumbLeft = columnIdx * thumbSize.x;
            float thumbTop = rowIdx * thumbSize.y;
            try {
                // คำนวณตำแหน่งเริ่มต้นด้านซ้ายและด้านบน
                int leftPos = (int) (thumbLeft + pf.getImageableX());
                int topPos = (int) (thumbTop + pf.getImageableY());
                // เรนเดอร์หน้าเอกสารไปยังวัตถุกราฟิกโดยใช้พิกัดที่คำนวณได้
                // และขนาดตัวแทนภาพขนาดย่อ
                // ค่าส่งคืนที่มีประโยชน์คือมาตราส่วนที่แสดงผลหน้า
                float scale = mDocument.renderToSize(pageIndex, (Graphics2D) g, leftPos, topPos, (int) thumbSize.x,
                        (int) thumbSize.y);
                // วาดเส้นขอบหน้า (ขนาดย่อของหน้าอาจมีขนาดเล็กกว่าขนาดย่อ)
                // ขนาดตัวแทน)
                if (mPrintPageBorders) {
                    // รับขนาดจริง 100% ของหน้าในหน่วยพอยต์
                    Point2D.Float pageSize = mDocument.getPageInfo(pageIndex).getSizeInPoints();
                    // วาดขอบรอบ ๆ หน้าที่ปรับขนาดโดยใช้ปัจจัยมาตราส่วนที่ทราบ
                    g.setColor(Color.black);
                    g.drawRect(leftPos, topPos, (int) (pageSize.x * scale), (int) (pageSize.y * scale));
                    // วาดเส้นขอบรอบ ๆ ช่องว่างสำหรับรูปขนาดย่อ
                    g.setColor(Color.red);
                    g.drawRect(leftPos, topPos, (int) thumbSize.x, (int) thumbSize.y);
                }
            } catch (Exception e) {
                // หากมีข้อผิดพลาดใดๆ เกิดขึ้นระหว่างการเรนเดอร์ อย่าทำอะไร
                // ระบบจะวาดหน้าว่างหากมีข้อผิดพลาดใด ๆ ระหว่างการเรนเดอร์
            }
        }
        return Printable.PAGE_EXISTS;
    }
    private Dimension getThumbCount(int pagesPerSheet, PageFormat pf) {
        Dimension size;
        // กำหนดจำนวนคอลัมน์และแถวบนแผ่นงานสำหรับ
        // กระดาษแนวแนวนอน
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
        // สลับความกว้างและความสูงหากกระดาษอยู่ในแนวตั้ง
        if ((pf.getWidth() - pf.getImageableX()) < (pf.getHeight() - pf.getImageableY()))
            return new Dimension((int) size.getHeight(), (int) size.getWidth());
        return size;
	}
}
```

## บทสรุป

ขอแสดงความยินดี! คุณได้พิมพ์เอกสาร Word สำเร็จโดยใช้ Aspose.Words สำหรับ Java คำแนะนำทีละขั้นตอนนี้ควรช่วยให้คุณผสานการพิมพ์เอกสารเข้ากับแอปพลิเคชัน Java ของคุณได้อย่างราบรื่น

## คำถามที่พบบ่อย

### คำถามที่ 1: ฉันสามารถพิมพ์หน้าเฉพาะของเอกสารโดยใช้ Aspose.Words สำหรับ Java ได้หรือไม่

ใช่ คุณสามารถระบุช่วงหน้าเมื่อพิมพ์เอกสารได้ ในตัวอย่างโค้ด เราใช้ `attributes.add(new PageRanges(1, doc.getPageCount()))` เพื่อพิมพ์หน้าทั้งหมด คุณสามารถปรับช่วงหน้าได้ตามต้องการ

### คำถามที่ 2: Aspose.Words สำหรับ Java เหมาะสำหรับการพิมพ์แบบแบตช์หรือไม่

แน่นอน! Aspose.Words สำหรับ Java เหมาะอย่างยิ่งสำหรับงานพิมพ์แบบแบตช์ คุณสามารถทำซ้ำผ่านรายการเอกสารและพิมพ์ทีละรายการโดยใช้โค้ดที่คล้ายกัน

### คำถามที่ 3: ฉันจะจัดการกับข้อผิดพลาดในการพิมพ์หรือข้อยกเว้นได้อย่างไร

คุณควรจัดการกับข้อยกเว้นที่อาจเกิดขึ้นระหว่างกระบวนการพิมพ์ ตรวจสอบเอกสาร Aspose.Words สำหรับ Java เพื่อดูข้อมูลเกี่ยวกับการจัดการข้อยกเว้น

### คำถามที่ 4: ฉันสามารถปรับแต่งการตั้งค่าการพิมพ์เพิ่มเติมได้หรือไม่

ใช่ คุณสามารถปรับแต่งการตั้งค่าการพิมพ์เพื่อให้ตรงตามความต้องการเฉพาะของคุณได้ สำรวจเอกสาร Aspose.Words สำหรับ Java เพื่อเรียนรู้เพิ่มเติมเกี่ยวกับตัวเลือกการพิมพ์ที่มีให้

### คำถามที่ 5: ฉันสามารถรับความช่วยเหลือและการสนับสนุนเพิ่มเติมสำหรับ Aspose.Words สำหรับ Java ได้จากที่ใด

หากต้องการการสนับสนุนและความช่วยเหลือเพิ่มเติม คุณสามารถเยี่ยมชม [ฟอรั่ม Aspose.Words สำหรับ Java](https://forum-aspose.com/).

---

ตอนนี้คุณได้เรียนรู้วิธีพิมพ์เอกสารโดยใช้ Aspose.Words สำหรับ Java เรียบร้อยแล้ว คุณสามารถเริ่มต้นใช้งานฟังก์ชันนี้ในแอปพลิเคชัน Java ของคุณได้ ขอให้สนุกกับการเขียนโค้ด!


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}