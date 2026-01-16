---
date: 2026-01-16
description: เรียนรู้วิธีเน้นข้อผิดพลาดการสะกดใน Word ด้วย Aspose.Words for Java และค้นหาวิธีตั้งค่าตัวอักษรต่อบรรทัด
  ปรับแต่งตัวเลือกการมองเห็น และทำความสะอาดสไตล์
linktitle: Using Document Options and Settings
second_title: Aspose.Words Java Document Processing API
title: ไฮไลท์ข้อผิดพลาดการสะกดใน Word ด้วย Aspose.Words Java
url: /th/java/document-manipulation/using-document-options-and-settings/
weight: 31
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การใช้ตัวเลือกและการตั้งค่าเอกสารใน Aspose.Words for Java

## บทนำการใช้ตัวเลือกและการตั้งค่าเอกสารใน Aspose.Words for Java

ในคู่มือฉบับครอบคลุมนี้ คุณจะได้เรียนรู้ **วิธีเน้นคำที่สะกดผิดใน Word** ด้วย Aspose.Words for Java พร้อมกับการควบคุมการตั้งค่าอื่น ๆ เช่น ตัวเลือกการดู, การจัดหน้า, และการทำความสะอาดสไตล์ ไม่ว่าคุณจะเป็นนักพัฒนาที่มีประสบการณ์หรือเพิ่งเริ่มต้น ตัวอย่างด้านล่างจะช่วยให้คุณสร้างเอกสารที่แข็งแรงและตรวจจับข้อผิดพลาดที่ทำงานได้กับหลายเวอร์ชันของ Word

## Quick Answers
- **How can I highlight spelling errors in Word?** Use `setShowSpellingErrors(true)` on the `Document` object.  
- **Can I also show grammatical errors?** Yes—call `setShowGrammaticalErrors(true)`.  
- **What method sets characters per line?** `getPageSetup().setCharactersPerLine(int)`.  
- **Which API optimizes for a specific Word version?** `doc.getCompatibilityOptions().optimizeFor(MsWordVersion)`.  
- **Is there a way to clean unused styles?** Use `CleanupOptions` with `setUnusedStyles(true)` and call `doc.cleanup(options)`.

## วิธีเน้นคำที่สะกดผิดใน Word?

Aspose.Words ทำให้การเปิดใช้งานการเน้นคำที่สะกดผิดเป็นเรื่องง่าย เมื่อเปิดเอกสารใน Microsoft Word คำที่สะกดผิดจะปรากฏด้วยเส้นขีดสีแดงที่คุ้นเคย ช่วยให้ผู้ใช้เห็นปัญหาได้ทันที

## วิธีตั้งค่าจำนวนอักขระต่อบรรทัด

การควบคุมจำนวนอักขระต่อบรรทัดเป็นสิ่งสำคัญสำหรับการจัดรูปแบบความกว้างคงที่ (เช่น รายการโค้ดหรือแบบฟอร์มเก่า) คลาส `PageSetup` มีเมธอด `setCharactersPerLine(int)` ที่ให้คุณกำหนดค่าดังกล่าวได้อย่างแม่นยำ

## วิธีแสดงข้อผิดพลาดทางไวยากรณ์

นอกจากการสะกดคำแล้ว คุณยังสามารถเปิดการแสดงข้อผิดพลาดทางไวยากรณ์ได้ ซึ่งมีประโยชน์สำหรับการร่างเนื้อหาที่ต้องปฏิบัติตามแนวทางการเขียนหรือสำหรับการสร้างเครื่องมือการตรวจทาน

## Optimizing Documents for Compatibility

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.OptimizeForMsWord.docx");
```

หนึ่งในด้านสำคัญของการจัดการเอกสารคือการทำให้เข้ากันได้กับเวอร์ชันต่าง ๆ ของ Microsoft Word Aspose.Words for Java มีวิธีที่ง่ายต่อการปรับเอกสารให้เข้ากับเวอร์ชัน Word เฉพาะ ในตัวอย่างข้างต้น เราปรับเอกสารให้เข้ากับ Word 2016 เพื่อให้การทำงานเป็นไปอย่างราบรื่น

## Identifying Grammatical and Spelling Errors

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

ความแม่นยำเป็นสิ่งสำคัญเมื่อทำงานกับเอกสาร Aspose.Words for Java ช่วยให้คุณเน้นข้อผิดพลาดทางไวยากรณ์และการสะกดในเอกสารของคุณ ทำให้การตรวจทานและการแก้ไขมีประสิทธิภาพมากขึ้น

## Cleaning Up Unused Styles and Lists

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

การจัดการสไตล์และรายการในเอกสารอย่างมีประสิทธิภาพเป็นสิ่งจำเป็นสำหรับการรักษาความสอดคล้องของเอกสาร Aspose.Words for Java ช่วยให้คุณทำความสะอาดสไตล์และรายการที่ไม่ได้ใช้ เพื่อให้โครงสร้างเอกสารเป็นระเบียบและเป็นระบบ

## Removing Duplicate Styles

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

สไตล์ที่ซ้ำกันอาจทำให้เกิดความสับสนและความไม่สอดคล้องในเอกสารของคุณ ด้วย Aspose.Words for Java คุณสามารถลบสไตล์ที่ซ้ำกันได้อย่างง่ายดาย เพื่อรักษาความชัดเจนและความเป็นหนึ่งเดียวของเอกสาร

## Customizing Document Viewing Options

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

การปรับประสบการณ์การดูเอกสารของคุณเป็นสิ่งสำคัญ Aspose.Words for Java ให้คุณตั้งค่าตัวเลือกการดูต่าง ๆ เช่น การจัดหน้าและเปอร์เซ็นต์การซูม เพื่อเพิ่มความอ่านง่ายของเอกสาร

## Configuring Document Page Setup

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

การตั้งค่าหน้ากระดาษอย่างแม่นยำเป็นสิ่งสำคัญสำหรับการจัดรูปแบบเอกสาร Aspose.Words for Java ช่วยให้คุณตั้งค่าโหมดการจัดวาง, **จำนวนอักขระต่อบรรทัด**, และจำนวนบรรทัดต่อหน้า เพื่อให้เอกสารของคุณดูสวยงาม

## Setting Editing Languages

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

ภาษาการแก้ไขมีบทบาทสำคัญในการประมวลผลเอกสาร ด้วย Aspose.Words for Java คุณสามารถตั้งค่าและปรับแต่งภาษาการแก้ไขให้สอดคล้องกับความต้องการทางภาษาของเอกสารของคุณ

## Conclusion

ในคู่มือนี้ เราได้สำรวจตัวเลือกและการตั้งค่าเอกสารต่าง ๆ ที่มีใน Aspose.Words for Java ตั้งแต่การปรับให้เข้ากับเวอร์ชัน, การแสดงข้อผิดพลาด, การทำความสะอาดสไตล์, จนถึงตัวเลือกการดู ไลบรารีที่ทรงพลังนี้ให้ความสามารถที่หลากหลายสำหรับการจัดการและปรับแต่งเอกสารของคุณ

## FAQ's

### How do I optimize a document for a specific Word version?

เพื่อปรับเอกสารให้เข้ากับเวอร์ชัน Word เฉพาะ ให้ใช้เมธอด `optimizeFor` และระบุเวอร์ชันที่ต้องการ ตัวอย่างเช่น เพื่อปรับให้เข้ากับ Word 2016:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "OptimizedForWord2016.docx");
```

### How can I highlight grammatical and spelling errors in a document?

คุณสามารถเปิดการแสดงข้อผิดพลาดทางไวยากรณ์และการสะกดในเอกสารได้โดยใช้โค้ดต่อไปนี้:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.setShowGrammaticalErrors(true);
doc.setShowSpellingErrors(true);
doc.save("Your Directory Path" + "ShowErrors.docx");
```

### What is the purpose of cleaning up unused styles and lists?

การทำความสะอาดสไตล์และรายการที่ไม่ได้ใช้ช่วยให้โครงสร้างเอกสารสะอาดและเป็นระเบียบ มันลบความรกที่ไม่จำเป็นออกไป ทำให้การอ่านและความสอดคล้องของเอกสารดีขึ้น

### How can I remove duplicate styles from a document?

เพื่อเอาสตไลล์ที่ซ้ำกันออกจากเอกสาร ให้ใช้เมธอด `cleanup` พร้อมตั้งค่า `duplicateStyle` เป็น `true` ตัวอย่างเช่น:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
CleanupOptions options = new CleanupOptions();
options.setDuplicateStyle(true);
doc.cleanup(options);
doc.save("Your Directory Path" + "CleanedDocument.docx");
```

### How do I customize the viewing options for a document?

คุณสามารถปรับตัวเลือกการดูเอกสารได้โดยใช้คลาส `ViewOptions` ตัวอย่างเช่น เพื่อตั้งค่าประเภทการดูเป็นการจัดหน้าและซูมที่ 50%:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
doc.getViewOptions().setZoomPercent(50);
doc.save("Your Directory Path" + "CustomView.docx");
```

## Additional Tips & Common Pitfalls

- **เปิดการตรวจสอบการสะกดและไวยากรณ์พร้อมกัน** เมื่อคุณต้องการการตรวจทานที่ครอบคลุม การลืมตั้งค่าใดค่าหนึ่ง (`setShowGrammaticalErrors` หรือ `setShowSpellingErrors`) อาจทำให้ข้อผิดพลาดไม่ถูกตรวจพบ
- **เมื่อกำหนดจำนวนอักขระต่อบรรทัด** จำไว้ว่าค่าดังกล่าวทำงานร่วมกับฟอนต์และระยะขอบของหน้า ทดสอบกับเลย์เอาต์จริงของเอกสารเพื่อหลีกเลี่ยงการตัดบรรทัดที่ไม่คาดคิด
- **การทำความสะอาดเป็นการกระทำที่ย้อนกลับไม่ได้** บนไฟล์ต้นฉบับ ควรทำงานบนสำเนาหรือใช้ระบบควบคุมเวอร์ชันเพื่อรักษาสตไลล์เดิมไว้
- **การตั้งค่าภาษาการแก้ไข** มีผลต่อพฤติกรรมการตรวจสอบการสะกด หากคุณทำงานกับเอกสารหลายภาษา ให้เพิ่มภาษาที่เกี่ยวข้องทั้งหมดใน `LanguagePreferences`

---

**Last Updated:** 2026-01-16  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}