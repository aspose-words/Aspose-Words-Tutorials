---
title: การใช้ตัวเลือกและการตั้งค่าเอกสารใน Aspose.Words สำหรับ Java
linktitle: การใช้ตัวเลือกและการตั้งค่าเอกสาร
second_title: API การประมวลผลเอกสาร Java ของ Aspose.Words
description: ปลดล็อกพลังของ Aspose.Words สำหรับ Java เลือกและตั้งค่าเอกสารอย่างชาญฉลาดเพื่อการจัดการเอกสารที่ราบรื่น ปรับแต่ง และอื่นๆ อีกมากมาย
weight: 31
url: /th/java/document-manipulation/using-document-options-and-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# การใช้ตัวเลือกและการตั้งค่าเอกสารใน Aspose.Words สำหรับ Java


## บทนำเกี่ยวกับการใช้ตัวเลือกเอกสารและการตั้งค่าใน Aspose.Words สำหรับ Java

ในคู่มือที่ครอบคลุมนี้ เราจะมาสำรวจวิธีใช้ประโยชน์จากฟีเจอร์อันทรงพลังของ Aspose.Words สำหรับ Java เพื่อทำงานกับตัวเลือกและการตั้งค่าเอกสาร ไม่ว่าคุณจะเป็นนักพัฒนาที่มีประสบการณ์หรือเพิ่งเริ่มต้น คุณจะพบกับข้อมูลเชิงลึกอันมีค่าและตัวอย่างเชิงปฏิบัติเพื่อปรับปรุงงานประมวลผลเอกสารของคุณ

## การปรับปรุงเอกสารเพื่อความเข้ากันได้

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.OptimizeForMsWord.docx");
```

ประเด็นสำคัญประการหนึ่งของการจัดการเอกสารคือการรับรองความเข้ากันได้กับ Microsoft Word เวอร์ชันต่างๆ Aspose.Words สำหรับ Java มอบวิธีง่ายๆ ในการปรับแต่งเอกสารให้เหมาะกับ Word เวอร์ชันต่างๆ ในตัวอย่างข้างต้น เราปรับแต่งเอกสารให้เหมาะกับ Word 2016 เพื่อให้แน่ใจว่าเข้ากันได้อย่างราบรื่น

## การระบุข้อผิดพลาดทางไวยากรณ์และการสะกดคำ

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

ความถูกต้องเป็นสิ่งสำคัญที่สุดเมื่อต้องจัดการกับเอกสาร Aspose.Words สำหรับ Java ช่วยให้คุณสามารถเน้นข้อผิดพลาดด้านไวยากรณ์และการสะกดคำในเอกสารของคุณ ทำให้การตรวจทานและแก้ไขมีประสิทธิภาพมากขึ้น

## การทำความสะอาดสไตล์และรายการที่ไม่ได้ใช้

```java
@Test
public void cleanupUnusedStylesAndLists() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Unused styles.docx");
    // กำหนดตัวเลือกการล้างข้อมูล
    CleanupOptions cleanupOptions = new CleanupOptions();
    cleanupOptions.setUnusedLists(false);
    cleanupOptions.setUnusedStyles(true);
    doc.cleanup(cleanupOptions);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupUnusedStylesAndLists.docx");
}
```

การจัดการรูปแบบและรายการเอกสารอย่างมีประสิทธิภาพถือเป็นสิ่งสำคัญสำหรับการรักษาความสอดคล้องของเอกสาร Aspose.Words สำหรับ Java ช่วยให้คุณสามารถล้างรูปแบบและรายการที่ไม่ได้ใช้ เพื่อให้แน่ใจว่าโครงสร้างเอกสารจะกระชับและเป็นระเบียบ

## การลบสไตล์ที่ซ้ำกัน

```java
@Test
public void cleanupDuplicateStyle() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // ทำความสะอาดสไตล์ที่ซ้ำกัน
    CleanupOptions options = new CleanupOptions();
    options.setDuplicateStyle(true);
    doc.cleanup(options);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupDuplicateStyle.docx");
}
```

สไตล์ที่ซ้ำกันอาจทำให้เกิดความสับสนและความไม่สอดคล้องในเอกสารของคุณ ด้วย Aspose.Words สำหรับ Java คุณสามารถลบสไตล์ที่ซ้ำกันได้อย่างง่ายดาย โดยรักษาความชัดเจนและความสอดคล้องของเอกสาร

## การปรับแต่งตัวเลือกการดูเอกสาร

```java
@Test
public void viewOptions() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // ปรับแต่งตัวเลือกการดู
    doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
    doc.getViewOptions().setZoomPercent(50);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ViewOptions.docx");
}
```

การปรับแต่งประสบการณ์การดูเอกสารของคุณถือเป็นสิ่งสำคัญ Aspose.Words สำหรับ Java ช่วยให้คุณตั้งค่าตัวเลือกการดูต่างๆ เช่น เค้าโครงหน้าและเปอร์เซ็นต์การซูม เพื่อปรับปรุงการอ่านเอกสาร

## การกำหนดค่าการตั้งค่าหน้าเอกสาร

```java
@Test
public void documentPageSetup() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // กำหนดค่าตัวเลือกการตั้งค่าหน้า
    doc.getFirstSection().getPageSetup().setLayoutMode(SectionLayoutMode.GRID);
    doc.getFirstSection().getPageSetup().setCharactersPerLine(30);
    doc.getFirstSection().getPageSetup().setLinesPerPage(10);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.DocumentPageSetup.docx");
}
```

การตั้งค่าหน้ากระดาษอย่างแม่นยำเป็นสิ่งสำคัญสำหรับการจัดรูปแบบเอกสาร Aspose.Words สำหรับ Java ช่วยให้คุณสามารถตั้งค่าโหมดเค้าโครง อักขระต่อบรรทัด และบรรทัดต่อหน้า เพื่อให้แน่ใจว่าเอกสารของคุณดูน่าสนใจ

## การตั้งค่าการแก้ไขภาษา

```java
@Test
public void addJapaneseAsEditingLanguages() throws Exception
{
    LoadOptions loadOptions = new LoadOptions();
    // ตั้งค่าภาษาสำหรับการแก้ไข
    loadOptions.getLanguagePreferences().addEditingLanguage(EditingLanguage.JAPANESE);
    Document doc = new Document("Your Directory Path" + "No default editing language.docx", loadOptions);
    // ตรวจสอบภาษาการแก้ไขที่ถูกแทนที่
    int localeIdFarEast = doc.getStyles().getDefaultFont().getLocaleIdFarEast();
    System.out.println(localeIdFarEast == (int) EditingLanguage.JAPANESE
            ? "The document either has no any FarEast language set in defaults or it was set to Japanese originally."
            : "The document default FarEast language was set to another than Japanese language originally, so it is not overridden.");
}
```

การแก้ไขภาษามีบทบาทสำคัญในการประมวลผลเอกสาร ด้วย Aspose.Words สำหรับ Java คุณสามารถตั้งค่าและปรับแต่งภาษาการแก้ไขให้เหมาะกับความต้องการทางภาษาของเอกสารของคุณได้


## บทสรุป

ในคู่มือนี้ เราได้เจาะลึกตัวเลือกและการตั้งค่าเอกสารต่างๆ ที่มีอยู่ใน Aspose.Words สำหรับ Java ตั้งแต่การเพิ่มประสิทธิภาพและการแสดงข้อผิดพลาด ไปจนถึงการล้างรูปแบบและตัวเลือกการดู ไลบรารีอันทรงพลังนี้มีความสามารถมากมายสำหรับการจัดการและปรับแต่งเอกสารของคุณ

## คำถามที่พบบ่อย

### ฉันจะเพิ่มประสิทธิภาพเอกสารสำหรับ Word เวอร์ชันเฉพาะได้อย่างไร

 หากต้องการเพิ่มประสิทธิภาพเอกสารสำหรับ Word เวอร์ชันเฉพาะ ให้ใช้`optimizeFor` วิธีการและระบุเวอร์ชันที่ต้องการ ตัวอย่างเช่น หากต้องการเพิ่มประสิทธิภาพสำหรับ Word 2016:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "OptimizedForWord2016.docx");
```

### ฉันจะเน้นข้อผิดพลาดด้านไวยากรณ์และการสะกดคำในเอกสารได้อย่างไร

คุณสามารถเปิดใช้งานการแสดงข้อผิดพลาดด้านไวยากรณ์และการสะกดคำในเอกสารได้โดยใช้โค้ดต่อไปนี้:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.setShowGrammaticalErrors(true);
doc.setShowSpellingErrors(true);
doc.save("Your Directory Path" + "ShowErrors.docx");
```

### จุดประสงค์ในการล้างสไตล์และรายการที่ไม่ได้ใช้คืออะไร

การทำความสะอาดรูปแบบและรายการที่ไม่ได้ใช้ช่วยรักษาโครงสร้างเอกสารให้สะอาดและเป็นระเบียบ ช่วยขจัดสิ่งไม่จำเป็น ทำให้เอกสารอ่านง่ายและมีความสอดคล้องกันมากขึ้น

### ฉันจะลบสไตล์ที่ซ้ำกันออกจากเอกสารได้อย่างไร

หากต้องการลบรูปแบบที่ซ้ำกันออกจากเอกสาร ให้ใช้`cleanup` วิธีการด้วย`duplicateStyle` ตัวเลือกที่ตั้งไว้เป็น`true`นี่คือตัวอย่าง:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
CleanupOptions options = new CleanupOptions();
options.setDuplicateStyle(true);
doc.cleanup(options);
doc.save("Your Directory Path" + "CleanedDocument.docx");
```

### ฉันจะปรับแต่งตัวเลือกการดูเอกสารได้อย่างไร

 คุณสามารถปรับแต่งตัวเลือกการดูเอกสารได้โดยใช้`ViewOptions` คลาส ตัวอย่างเช่น การตั้งค่าประเภทมุมมองเป็นรูปแบบหน้าและซูมเป็น 50%:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
doc.getViewOptions().setZoomPercent(50);
doc.save("Your Directory Path" + "CustomView.docx");
```
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
