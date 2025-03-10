---
title: วิธีช่วยเหลือในการแยกเนื้อหาใน Aspose.Words สำหรับ Java
linktitle: วิธีช่วยเหลือในการแยกเนื้อหา
second_title: API การประมวลผลเอกสาร Java ของ Aspose.Words
description: เรียนรู้วิธีแยกเนื้อหาจากเอกสาร Word อย่างมีประสิทธิภาพโดยใช้ Aspose.Words สำหรับ Java สำรวจวิธีการช่วยเหลือ การจัดรูปแบบแบบกำหนดเอง และอื่นๆ อีกมากมายในคู่มือที่ครอบคลุมนี้
weight: 14
url: /th/java/document-manipulation/helper-methods-for-extracting-content/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีช่วยเหลือในการแยกเนื้อหาใน Aspose.Words สำหรับ Java


## การแนะนำวิธีช่วยเหลือในการแยกเนื้อหาใน Aspose.Words สำหรับ Java

Aspose.Words for Java เป็นไลบรารีที่มีประสิทธิภาพที่ช่วยให้นักพัฒนาสามารถทำงานกับเอกสาร Word ได้ด้วยการเขียนโปรแกรม งานทั่วไปอย่างหนึ่งเมื่อทำงานกับเอกสาร Word คือการแยกเนื้อหาจากเอกสาร ในบทความนี้ เราจะมาสำรวจวิธีช่วยเหลือบางอย่างสำหรับการแยกเนื้อหาอย่างมีประสิทธิภาพโดยใช้ Aspose.Words for Java

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเจาะลึกตัวอย่างโค้ด ให้แน่ใจว่าคุณได้ติดตั้งและตั้งค่า Aspose.Words สำหรับ Java ในโปรเจ็กต์ Java ของคุณแล้ว คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.aspose.com/words/java/).

## วิธีช่วยเหลือ 1: การแยกย่อหน้าตามรูปแบบ

```java
public static ArrayList<Paragraph> paragraphsByStyleName(Document doc, String styleName) {
    // สร้างอาร์เรย์เพื่อรวบรวมย่อหน้าที่มีรูปแบบที่ระบุ
    ArrayList<Paragraph> paragraphsWithStyle = new ArrayList<Paragraph>();
    NodeCollection paragraphs = doc.getChildNodes(NodeType.PARAGRAPH, true);

    // ดูผ่านย่อหน้าทั้งหมดเพื่อค้นหาย่อหน้าที่มีรูปแบบที่กำหนด
    for (Paragraph paragraph : (Iterable<Paragraph>) paragraphs) {
        if (paragraph.getParagraphFormat().getStyle().getName().equals(styleName))
            paragraphsWithStyle.add(paragraph);
    }
    return paragraphsWithStyle;
}
```

คุณสามารถใช้วิธีนี้เพื่อแยกย่อหน้าที่มีรูปแบบเฉพาะในเอกสาร Word ของคุณได้ ซึ่งมีประโยชน์เมื่อคุณต้องการแยกเนื้อหาที่มีการจัดรูปแบบเฉพาะ เช่น หัวเรื่องหรือเครื่องหมายคำพูดแบบบล็อก

## วิธีช่วยเหลือ 2: การแยกเนื้อหาโดยโหนด

```java
public static ArrayList<Node> extractContentBetweenNodes(Node startNode, Node endNode, boolean isInclusive) {
    // ก่อนอื่น ตรวจสอบว่าโหนดที่ส่งผ่านมายังวิธีนี้สามารถใช้ได้หรือไม่
    verifyParameterNodes(startNode, endNode);
    
    // สร้างรายการเพื่อจัดเก็บโหนดที่แยกออกมา
    ArrayList<Node> nodes = new ArrayList<Node>();

    // หากเครื่องหมายใดเครื่องหมายหนึ่งเป็นส่วนหนึ่งของความคิดเห็น รวมถึงความคิดเห็นนั้นเอง เราจำเป็นต้องย้ายตัวชี้
    // ส่งต่อไปยังโหนดความคิดเห็นที่พบหลังจากโหนด CommentRangeEnd
    if (endNode.getNodeType() == NodeType.COMMENT_RANGE_END && isInclusive) {
        Node node = findNextNode(NodeType.COMMENT, endNode.getNextSibling());
        if (node != null)
            endNode = node;
    }
    
    // เก็บบันทึกของโหนดดั้งเดิมที่ส่งไปยังวิธีการนี้เพื่อแยกโหนดมาร์กเกอร์หากจำเป็น
    Node originalStartNode = startNode;
    Node originalEndNode = endNode;

    //แยกเนื้อหาตามโหนดระดับบล็อก (ย่อหน้าและตาราง) สำรวจโหนดหลักเพื่อค้นหา
    // เราจะแยกเนื้อหาของโหนดแรกและโหนดสุดท้าย ขึ้นอยู่กับว่าโหนดมาร์กเกอร์เป็นแบบอินไลน์หรือไม่
    startNode = getAncestorInBody(startNode);
    endNode = getAncestorInBody(endNode);
    boolean isExtracting = true;
    boolean isStartingNode = true;
    // โหนดปัจจุบันที่เรากำลังแยกออกมาจากเอกสาร
    Node currNode = startNode;

    // เริ่มแยกเนื้อหา ประมวลผลโหนดระดับบล็อกทั้งหมดและแยกส่วนแรกโดยเฉพาะ
    // และโหนดสุดท้ายเมื่อจำเป็นเพื่อให้การจัดรูปแบบย่อหน้ายังคงอยู่
    // วิธีนี้ซับซ้อนกว่าเครื่องสกัดปกติเล็กน้อย เนื่องจากเราจำเป็นต้องแยกปัจจัย
    // ในการดึงข้อมูลโดยใช้โหนดอินไลน์, ฟิลด์, บุ๊กมาร์ก ฯลฯ เพื่อให้เป็นประโยชน์
    while (isExtracting) {
        // โคลนโหนดปัจจุบันและโหนดย่อยเพื่อรับสำเนา
        Node cloneNode = currNode.deepClone(true);
        boolean isEndingNode = currNode.equals(endNode);
        if (isStartingNode || isEndingNode) {
            // เราจำเป็นต้องประมวลผลเครื่องหมายแต่ละตัวแยกกัน ดังนั้นจึงส่งต่อไปยังวิธีการแยกกันแทน
            // ควรดำเนินการขั้นแรกเพื่อคงดัชนีโหนดไว้
            if (isEndingNode) {
                // !isStartingNode: อย่าเพิ่มโหนดสองครั้ง หากเครื่องหมายเป็นโหนดเดียวกัน
                processMarker(cloneNode, nodes, originalEndNode, currNode, isInclusive,
                        false, !isStartingNode, false);
                isExtracting = false;
            }
            //เงื่อนไขจะต้องแยกจากกัน เนื่องจากเครื่องหมายเริ่มต้นและสิ้นสุดที่ระดับบล็อกอาจเป็นโหนดเดียวกัน
            if (isStartingNode) {
                processMarker(cloneNode, nodes, originalStartNode, currNode, isInclusive,
                        true, true, false);
                isStartingNode = false;
            }
        } else
            // โหนดไม่ใช่เครื่องหมายเริ่มต้นหรือจุดสิ้นสุด เพียงเพิ่มสำเนาลงในรายการ
            nodes.add(cloneNode);

        // ย้ายไปยังโหนดถัดไปและแยกข้อมูลออกมา หากโหนดถัดไปเป็นค่าว่าง
        // เนื้อหาที่เหลือจะอยู่ในส่วนอื่น
        if (currNode.getNextSibling() == null && isExtracting) {
            // ย้ายไปยังส่วนถัดไป
            Section nextSection = (Section) currNode.getAncestor(NodeType.SECTION).getNextSibling();
            currNode = nextSection.getBody().getFirstChild();
        } else {
            // ย้ายไปยังโหนดถัดไปในเนื้อหา
            currNode = currNode.getNextSibling();
        }
    }

    // เพื่อให้เข้ากันได้กับโหมดที่มีบุ๊กมาร์กแบบอินไลน์ ให้เพิ่มย่อหน้าถัดไป (ว่างเปล่า)
    if (isInclusive && originalEndNode == endNode && !originalEndNode.isComposite())
        includeNextParagraph(endNode, nodes);

    // ส่งคืนโหนดระหว่างเครื่องหมายโหนด
    return nodes;
}
```

วิธีนี้ช่วยให้คุณแยกเนื้อหาระหว่างโหนดที่ระบุสองโหนด ไม่ว่าจะเป็นย่อหน้า ตาราง หรือองค์ประกอบระดับบล็อกอื่น ๆ ก็ได้ โดยสามารถจัดการสถานการณ์ต่าง ๆ ได้ เช่น มาร์กเกอร์อินไลน์ ฟิลด์ และบุ๊กมาร์ก

## วิธีช่วยเหลือที่ 3: การสร้างเอกสารใหม่

```java
public static Document generateDocument(Document srcDoc, ArrayList<Node> nodes) throws Exception {
    Document dstDoc = new Document();
    
    // ลบย่อหน้าแรกออกจากเอกสารเปล่า
    dstDoc.getFirstSection().getBody().removeAllChildren();
    
    // นำเข้าแต่ละโหนดจากรายการไปยังเอกสารใหม่ โดยคงรูปแบบดั้งเดิมของโหนดไว้
    NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
    for (Node node : nodes) {
        Node importNode = importer.importNode(node, true);
        dstDoc.getFirstSection().getBody().appendChild(importNode);
    }
    
    return dstDoc;
}
```

วิธีนี้ช่วยให้คุณสร้างเอกสารใหม่ได้โดยการนำเข้ารายการโหนดจากเอกสารต้นฉบับ โดยจะคงรูปแบบดั้งเดิมของโหนดเอาไว้ ทำให้มีประโยชน์ในการสร้างเอกสารใหม่ที่มีเนื้อหาเฉพาะ

## บทสรุป

การแยกเนื้อหาจากเอกสาร Word อาจเป็นส่วนสำคัญของงานประมวลผลเอกสารมากมาย Aspose.Words สำหรับ Java มีวิธีช่วยเหลืออันทรงพลังที่ทำให้กระบวนการนี้ง่ายขึ้น ไม่ว่าคุณจะต้องแยกย่อหน้าตามรูปแบบ เนื้อหาระหว่างโหนด หรือสร้างเอกสารใหม่ วิธีการเหล่านี้จะช่วยให้คุณทำงานกับเอกสาร Word ในแอปพลิเคชัน Java ได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย

### ฉันจะติดตั้ง Aspose.Words สำหรับ Java ได้อย่างไร?

 หากต้องการติดตั้ง Aspose.Words สำหรับ Java คุณสามารถดาวน์โหลดได้จากเว็บไซต์ Aspose เข้าไปที่[ที่นี่](https://releases.aspose.com/words/java/) เพื่อรับเวอร์ชันล่าสุด

### ฉันสามารถแยกเนื้อหาจากส่วนที่เจาะจงของเอกสาร Word ได้หรือไม่

ใช่ คุณสามารถแยกเนื้อหาจากส่วนที่ต้องการของเอกสาร Word ได้โดยใช้ขั้นตอนที่กล่าวถึงในบทความนี้ เพียงระบุโหนดเริ่มต้นและโหนดสิ้นสุดที่กำหนดส่วนที่คุณต้องการแยก

### Aspose.Words สำหรับ Java เข้ากันได้กับ Java 11 หรือไม่

ใช่ Aspose.Words สำหรับ Java เข้ากันได้กับ Java 11 และเวอร์ชันที่สูงกว่า คุณสามารถใช้ในแอปพลิเคชัน Java ได้โดยไม่มีปัญหาใดๆ

### ฉันสามารถปรับแต่งการจัดรูปแบบของเนื้อหาที่แยกออกมาได้หรือไม่

ใช่ คุณสามารถปรับแต่งการจัดรูปแบบของเนื้อหาที่แยกออกมาได้โดยแก้ไขโหนดที่นำเข้าในเอกสารที่สร้างขึ้น Aspose.Words สำหรับ Java มีตัวเลือกการจัดรูปแบบมากมายเพื่อตอบสนองความต้องการของคุณ

### ฉันสามารถหาเอกสารและตัวอย่างเพิ่มเติมสำหรับ Aspose.Words สำหรับ Java ได้ที่ไหน

 คุณสามารถค้นหาเอกสารประกอบและตัวอย่างที่ครอบคลุมสำหรับ Aspose.Words สำหรับ Java ได้ที่เว็บไซต์ Aspose เข้าไปที่[https://reference.aspose.com/words/java/](https://reference.aspose.com/words/java/) สำหรับเอกสารและทรัพยากรโดยละเอียด
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
