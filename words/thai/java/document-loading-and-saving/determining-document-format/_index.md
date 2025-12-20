---
date: 2025-12-20
description: เรียนรู้วิธีจัดระเบียบไฟล์ตามประเภทและตรวจจับรูปแบบเอกสารใน Java ด้วย
  Aspose.Words รองรับ DOC, DOCX, RTF และอื่น ๆ
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: จัดระเบียบไฟล์ตามประเภทโดยใช้ Aspose.Words สำหรับ Java
url: /th/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# จัดระเบียบไฟล์ตามประเภทโดยใช้ Aspose.Words สำหรับ Java

เมื่อคุณต้องการ **จัดระเบียบไฟล์ตามประเภท** ในแอปพลิเคชัน Java ขั้นตอนแรกคือการกำหนดรูปแบบของเอกสารแต่ละไฟล์อย่างแม่นยำ Aspose.Words สำหรับ Java ทำให้เรื่องนี้ง่ายขึ้น โดยสามารถตรวจจับ DOC, DOCX, RTF, HTML, ODT และรูปแบบอื่น ๆ มากมาย – รวมถึงไฟล์ที่เข้ารหัสหรือไฟล์ที่ไม่รู้จัก ในคู่มือนี้เราจะอธิบายการตั้งค่าโฟลเดอร์, การตรวจจับรูปแบบไฟล์, และการจัดเรียงไฟล์ของคุณโดยอัตโนมัติ

## คำตอบสั้น
- **“จัดระเบียบไฟล์ตามประเภท” หมายถึงอะไร?** หมายถึงการย้ายเอกสารไปยังโฟลเดอร์ตามรูปแบบที่ตรวจจับได้โดยอัตโนมัติ (เช่น DOCX, PDF, RTF)  
- **ไลบรารีใดช่วยตรวจจับรูปแบบไฟล์ใน Java?** Aspose.Words สำหรับ Java มีเมธอด `FileFormatUtil.detectFileFormat()`  
- **API สามารถระบุไฟล์ประเภทที่ไม่รู้จักได้หรือไม่?** ได้ – จะคืนค่า `LoadFormat.UNKNOWN` สำหรับไฟล์ที่ไม่รองรับหรือไม่สามารถระบุได้  
- **การตรวจจับเอกสารที่เข้ารหัสได้รับการสนับสนุนหรือไม่?** แน่นอน; ธง `FileFormatInfo.isEncrypted()` บอกว่ไฟล์ถูกป้องกันด้วยรหัสผ่านหรือไม่  
- **ต้องใช้ไลเซนส์สำหรับการใช้งานในโปรดักชันหรือไม่?** จำเป็นต้องมีไลเซนส์ Aspose.Words ที่ถูกต้องสำหรับการใช้งานเชิงพาณิชย์

## บทนำ: จัดระเบียบไฟล์ตามประเภทด้วย Aspose.Words สำหรับ Java

เมื่อทำงานกับการประมวลผลเอกสารใน Java การกำหนดรูปแบบของไฟล์ที่คุณจัดการเป็นสิ่งสำคัญ Aspose.Words สำหรับ Java มีฟีเจอร์ที่ทรงพลังสำหรับ **detect file format java** และเราจะพาคุณผ่านกระบวนการจัดระเบียบไฟล์อย่างมีประสิทธิภาพ

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มต้น โปรดตรวจสอบว่าคุณมีสิ่งต่อไปนี้พร้อมใช้งาน:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/)
- Java Development Kit (JDK) ที่ติดตั้งบนระบบของคุณ
- ความรู้พื้นฐานเกี่ยวกับการเขียนโปรแกรม Java

## ขั้นตอนที่ 1: การตั้งค่าไดเรกทอรี

แรกสุด เราต้องตั้งค่าไดเรกทอรีที่จำเป็นเพื่อจัดระเบียบไฟล์ของเราอย่างมีประสิทธิภาพ เราจะสร้างไดเรกทอรีสำหรับประเภทเอกสารต่าง ๆ

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

// Create the directories if they do not already exist.
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

เราได้สร้างไดเรกทอรีสำหรับไฟล์ที่รองรับ, ไฟล์ที่ไม่รู้จัก, ไฟล์ที่เข้ารหัส, และไฟล์ประเภท Pre‑97 แล้ว

## ขั้นตอนที่ 2: การตรวจจับรูปแบบเอกสาร

ต่อไป เราจะตรวจจับรูปแบบของเอกสารในไดเรกทอรีของเรา เราจะใช้ Aspose.Words สำหรับ Java เพื่อทำเช่นนี้

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // Display the document type
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // Add cases for other document formats as needed
    }

    // Handle encrypted documents
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // Handle other document types
        switch (info.getLoadFormat()) {
            case LoadFormat.DOC_PRE_WORD_60:
                FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                break;
            case LoadFormat.UNKNOWN:
                FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                break;
            default:
                FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                break;
        }
    }
}
```

ในโค้ดสแนปนี้ เราไล่ไฟล์ทั้งหมด, **detect file format java**, และจัดเรียงไฟล์เหล่านั้นไปยังโฟลเดอร์ที่เหมาะสม

## โค้ดต้นฉบับทั้งหมดสำหรับการกำหนดรูปแบบเอกสารใน Aspose.Words สำหรับ Java

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        // Create the directories if they do not already exist.
        if (supportedDir.exists() == false)
            supportedDir.mkdir();
        if (unknownDir.exists() == false)
            unknownDir.mkdir();
        if (encryptedDir.exists() == false)
            encryptedDir.mkdir();
        if (pre97Dir.exists() == false)
            pre97Dir.mkdir();
        Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
                .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
                .map(File::getPath)
                .collect(Collectors.toSet());
        for (String fileName : listFiles) {
            String nameOnly = Paths.get(fileName).getFileName().toString();
            System.out.println(nameOnly);
            FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);
            // Display the document type
            switch (info.getLoadFormat()) {
                case LoadFormat.DOC:
                    System.out.println("\tMicrosoft Word 97-2003 document.");
                    break;
                case LoadFormat.DOT:
                    System.out.println("\tMicrosoft Word 97-2003 template.");
                    break;
                case LoadFormat.DOCX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Document.");
                    break;
                case LoadFormat.DOCM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
                    break;
                case LoadFormat.DOTX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Template.");
                    break;
                case LoadFormat.DOTM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
                    break;
                case LoadFormat.FLAT_OPC:
                    System.out.println("\tFlat OPC document.");
                    break;
                case LoadFormat.RTF:
                    System.out.println("\tRTF format.");
                    break;
                case LoadFormat.WORD_ML:
                    System.out.println("\tMicrosoft Word 2003 WordprocessingML format.");
                    break;
                case LoadFormat.HTML:
                    System.out.println("\tHTML format.");
                    break;
                case LoadFormat.MHTML:
                    System.out.println("\tMHTML (Web archive) format.");
                    break;
                case LoadFormat.ODT:
                    System.out.println("\tOpenDocument Text.");
                    break;
                case LoadFormat.OTT:
                    System.out.println("\tOpenDocument Text Template.");
                    break;
                case LoadFormat.DOC_PRE_WORD_60:
                    System.out.println("\tMS Word 6 or Word 95 format.");
                    break;
                case LoadFormat.UNKNOWN:
                    System.out.println("\tUnknown format.");
                    break;
            }
            if (info.isEncrypted()) {
                System.out.println("\tAn encrypted document.");
                FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
            } else {
                switch (info.getLoadFormat()) {
                    case LoadFormat.DOC_PRE_WORD_60:
                        FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                        break;
                    case LoadFormat.UNKNOWN:
                        FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                        break;
                    default:
                        FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                        break;
                }
            }
        }

```

## วิธีการตรวจจับรูปแบบไฟล์ใน Java

เมธอด `FileFormatUtil.detectFileFormat()` ตรวจสอบส่วนหัวของไฟล์และคืนค่าอ็อบเจกต์ `FileFormatInfo` อ็อบเจกต์นี้บอกคุณเกี่ยวกับ **load format**, ว่าไฟล์ถูกเข้ารหัสหรือไม่, และเมตาดาต้าอื่น ๆ ที่เป็นประโยชน์ ด้วยข้อมูลนี้คุณสามารถ **identify unknown file types** อย่างโปรแกรมเมติกและตัดสินใจว่าจะประมวลผลไฟล์แต่ละไฟล์อย่างไร

## ระบุไฟล์ประเภทที่ไม่รู้จัก

เมื่อ API คืนค่า `LoadFormat.UNKNOWN` หมายความว่าไฟล์อาจเสียหายหรือใช้รูปแบบที่ Aspose.Words ไม่รองรับ ในโค้ดตัวอย่างของเรา เราจะย้ายไฟล์เหล่านั้นไปยังโฟลเดอร์ **Unknown** เพื่อให้คุณตรวจสอบในภายหลัง

## ปัญหาที่พบบ่อยและวิธีแก้

| Issue | Reason | Fix |
|-------|--------|-----|
| ไฟล์ทั้งหมดถูกวางไว้ในโฟลเดอร์ *Supported* | `FileFormatUtil` ไม่สามารถอ่านส่วนหัวได้ (เช่น ไฟล์ว่าง) | ตรวจสอบให้แน่ใจว่าคุณส่งพาธไฟล์ที่ถูกต้องและไฟล์ไม่เป็นศูนย์ไบต์ |
| ไฟล์ที่เข้ารหัสทำให้เกิดข้อยกเว้น | พยายามอ่านโดยไม่จัดการการเข้ารหัส | ใช้การตรวจสอบ `info.isEncrypted()` ก่อนทำการประมวลผลต่อ, ตามที่แสดงในโค้ด |
| ไฟล์ Word รุ่น Pre‑97 ไม่ถูกตรวจจับ | รูปแบบเก่าต้องใช้กรณี `DOC_PRE_WORD_60` | คงบล็อก `case LoadFormat.DOC_PRE_WORD_60` เพื่อส่งไฟล์ไปยังโฟลเดอร์ *Pre97* |

## คำถามที่พบบ่อย

### วิธีการติดตั้ง Aspose.Words สำหรับ Java?

คุณสามารถดาวน์โหลด Aspose.Words สำหรับ Java ได้จาก [ที่นี่](https://releases.aspose.com/words/java/) และทำตามคำแนะนำการติดตั้งที่ให้มา

### รูปแบบเอกสารที่รองรับมีอะไรบ้าง?

Aspose.Words สำหรับ Java รองรับรูปแบบเอกสารหลายประเภท รวมถึง DOC, DOCX, RTF, HTML, ODT และอื่น ๆ ดูเอกสารอย่างเป็นทางการสำหรับรายการเต็ม

### วิธีการตรวจจับเอกสารที่เข้ารหัสด้วย Aspose.Words สำหรับ Java?

ใช้เมธอด `FileFormatUtil.detectFileFormat()`; ธง `FileFormatInfo.isEncrypted()` ที่คืนค่าจะบ่งบอกว่ามีการเข้ารหัสหรือไม่ ตามที่แสดงในคู่มือนี้

### มีข้อจำกัดใดบ้างเมื่อทำงานกับรูปแบบเอกสารเก่า?

รูปแบบเก่าเช่น MS Word 6 หรือ Word 95 อาจขาดฟีเจอร์สมัยใหม่และอาจมีปัญหาความเข้ากันได้ ควรพิจารณาแปลงเป็นรูปแบบใหม่เมื่อเป็นไปได้

### สามารถทำให้การตรวจจับรูปแบบเอกสารเป็นอัตโนมัติในแอปพลิเคชัน Java ของฉันได้หรือไม่?

ได้, นำโค้ดที่ให้ไว้ฝังเข้าไปใน pipeline การประมวลผลของแอปพลิเคชันของคุณ จะทำให้สามารถจัดเรียงและจัดการไฟล์โดยอัตโนมัติตามรูปแบบที่ตรวจจับได้

---

**อัปเดตล่าสุด:** 2025-12-20  
**ทดสอบด้วย:** Aspose.Words สำหรับ Java 24.12 (ล่าสุด)  
**ผู้เขียน:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}