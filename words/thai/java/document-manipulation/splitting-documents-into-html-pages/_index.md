---
title: การแบ่งเอกสารออกเป็นหน้า HTML ใน Aspose.Words สำหรับ Java
linktitle: การแยกเอกสารออกเป็นหน้า HTML
second_title: API การประมวลผลเอกสาร Java ของ Aspose.Words
description: เรียนรู้วิธีแบ่งเอกสารออกเป็นหน้า HTML ด้วย Aspose.Words สำหรับ Java ปฏิบัติตามคำแนะนำทีละขั้นตอนของเราเพื่อการแปลงเอกสารอย่างราบรื่น
weight: 25
url: /th/java/document-manipulation/splitting-documents-into-html-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# การแบ่งเอกสารออกเป็นหน้า HTML ใน Aspose.Words สำหรับ Java


## บทนำสู่การแยกเอกสารเป็นหน้า HTML ใน Aspose.Words สำหรับ Java

ในคู่มือทีละขั้นตอนนี้ เราจะมาดูวิธีแบ่งเอกสารออกเป็นหน้า HTML โดยใช้ Aspose.Words สำหรับ Java Aspose.Words เป็น Java API ที่ทรงพลังสำหรับการทำงานกับเอกสาร Microsoft Word และมีคุณสมบัติมากมายสำหรับการจัดการเอกสาร รวมถึงความสามารถในการแปลงเอกสารเป็นรูปแบบต่างๆ รวมถึง HTML

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม โปรดตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:

- Java Development Kit (JDK) ติดตั้งอยู่บนระบบของคุณ
-  ไลบรารี Aspose.Words สำหรับ Java คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.aspose.com/words/java/).

## ขั้นตอนที่ 1: นำเข้าแพ็คเกจที่จำเป็น

```java
import com.aspose.words.*;
import java.io.*;
import java.util.ArrayList;
```

## ขั้นตอนที่ 2: สร้างวิธีการแปลง Word เป็น HTML

```java
class WordToHtmlConverter
{
    // รายละเอียดการใช้งานสำหรับการแปลง Word เป็น HTML
    // -
}
```

## ขั้นตอนที่ 3: เลือกย่อหน้าหัวข้อเมื่อหัวข้อเริ่มต้น

```java
private ArrayList<Paragraph> selectTopicStarts()
{
    NodeCollection paras = mDoc.getChildNodes(NodeType.PARAGRAPH, true);
    ArrayList<Paragraph> topicStartParas = new ArrayList<Paragraph>();
    for (Paragraph para : (Iterable<Paragraph>) paras)
    {
        int style = para.getParagraphFormat().getStyleIdentifier();
        if (style == StyleIdentifier.HEADING_1)
            topicStartParas.add(para);
    }
    return topicStartParas;
}
```

## ขั้นตอนที่ 4: แทรกตัวแบ่งส่วนก่อนย่อหน้าหัวข้อ

```java
private void insertSectionBreaks(ArrayList<Paragraph> topicStartParas)
{
    DocumentBuilder builder = new DocumentBuilder(mDoc);
    for (Paragraph para : topicStartParas)
    {
        Section section = para.getParentSection();
        if (para != section.getBody().getFirstParagraph())
        {
            builder.moveTo(para.getFirstChild());
            builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
            section.getBody().getLastParagraph().remove();
        }
    }
}
```

## ขั้นตอนที่ 5: แบ่งเอกสารออกเป็นหัวข้อ

```java
private ArrayList<Topic> saveHtmlTopics() throws Exception
{
    ArrayList<Topic> topics = new ArrayList<Topic>();
    for (int sectionIdx = 0; sectionIdx < mDoc.getSections().getCount(); sectionIdx++)
    {
        Section section = mDoc.getSections().get(sectionIdx);
        String paraText = section.getBody().getFirstParagraph().getText();
        String fileName = makeTopicFileName(paraText);
        if ("".equals(fileName))
            fileName = "UNTITLED SECTION " + sectionIdx;
        fileName = mDstDir + fileName + ".html";
        String title = makeTopicTitle(paraText);
        if ("".equals(title))
            title = "UNTITLED SECTION " + sectionIdx;
        Topic topic = new Topic(title, fileName);
        topics.add(topic);
        saveHtmlTopic(section, topic);
    }
    return topics;
}
```

## ขั้นตอนที่ 6: บันทึกหัวข้อแต่ละหัวข้อเป็นไฟล์ HTML

```java
private void saveHtmlTopic(Section section, Topic topic) throws Exception
{
    Document dummyDoc = new Document();
    dummyDoc.removeAllChildren();
    dummyDoc.appendChild(dummyDoc.importNode(section, true, ImportFormatMode.KEEP_SOURCE_FORMATTING));
    dummyDoc.getBuiltInDocumentProperties().setTitle(topic.getTitle());
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    {
        saveOptions.setPrettyFormat(true);
        saveOptions.setAllowNegativeIndent(true);
        saveOptions.setExportHeadersFootersMode(ExportHeadersFootersMode.NONE);
    }
    dummyDoc.save(topic.getFileName(), saveOptions);
}
```

## ขั้นตอนที่ 7: สร้างสารบัญสำหรับหัวข้อต่างๆ

```java
private void saveTableOfContents(ArrayList<Topic> topics) throws Exception
{
    Document tocDoc = new Document(mTocTemplate);
    tocDoc.getMailMerge().setFieldMergingCallback(new HandleTocMergeField());
    tocDoc.getMailMerge().executeWithRegions(new TocMailMergeDataSource(topics));
    tocDoc.save(mDstDir + "contents.html");
}
```

ตอนนี้ เราได้ร่างขั้นตอนต่างๆ ไว้แล้ว คุณสามารถนำแต่ละขั้นตอนไปใช้ในโครงการ Java เพื่อแบ่งเอกสารออกเป็นหน้า HTML โดยใช้ Aspose.Words สำหรับ Java ขั้นตอนนี้จะช่วยให้คุณสร้างเอกสาร HTML ที่มีโครงสร้าง ทำให้เข้าถึงได้ง่ายขึ้นและเป็นมิตรกับผู้ใช้มากขึ้น

## บทสรุป

ในคู่มือฉบับสมบูรณ์นี้ เราได้กล่าวถึงกระบวนการแบ่งเอกสารออกเป็นหน้า HTML โดยใช้ Aspose.Words สำหรับ Java โดยทำตามขั้นตอนที่ระบุไว้ คุณจะสามารถแปลงเอกสาร Word เป็นรูปแบบ HTML ได้อย่างมีประสิทธิภาพ ทำให้เข้าถึงเนื้อหาของคุณบนเว็บได้ง่ายขึ้น

## คำถามที่พบบ่อย

### ฉันจะติดตั้ง Aspose.Words สำหรับ Java ได้อย่างไร?

 หากต้องการติดตั้ง Aspose.Words สำหรับ Java คุณสามารถดาวน์โหลดไลบรารีได้จาก[ที่นี่](https://releases.aspose.com/words/java/) และปฏิบัติตามคำแนะนำในการติดตั้งที่ระบุไว้ในเอกสาร

### ฉันสามารถปรับแต่งผลลัพธ์ HTML ได้หรือไม่

 ใช่ คุณสามารถปรับแต่งผลลัพธ์ HTML ได้โดยการปรับตัวเลือกการบันทึกใน`HtmlSaveOptions` คลาสนี้ช่วยให้คุณสามารถควบคุมการจัดรูปแบบและรูปลักษณ์ของไฟล์ HTML ที่สร้างขึ้นได้

### Aspose.Words สำหรับ Java รองรับ Microsoft Word เวอร์ชันใดบ้าง

Aspose.Words สำหรับ Java รองรับรูปแบบเอกสาร Microsoft Word มากมาย รวมถึง DOC, DOCX, RTF และอื่นๆ อีกมากมาย และยังเข้ากันได้กับ Microsoft Word เวอร์ชันต่างๆ อีกด้วย

### ฉันจะจัดการรูปภาพใน HTML ที่แปลงแล้วได้อย่างไร

Aspose.Words สำหรับ Java สามารถจัดการรูปภาพใน HTML ที่แปลงแล้วได้โดยบันทึกรูปภาพเหล่านั้นเป็นไฟล์แยกต่างหากในโฟลเดอร์เดียวกับไฟล์ HTML วิธีนี้จะช่วยให้มั่นใจว่ารูปภาพจะแสดงอย่างถูกต้องในผลลัพธ์ HTML

### มี Aspose.Words เวอร์ชันทดลองใช้งานสำหรับ Java หรือไม่

ใช่ คุณสามารถขอเวอร์ชันทดลองใช้งานฟรีของ Aspose.Words สำหรับ Java ได้จากเว็บไซต์ Aspose เพื่อประเมินคุณลักษณะและความสามารถก่อนซื้อใบอนุญาต
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
