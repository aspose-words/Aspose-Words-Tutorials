---
date: 2026-02-22
description: เรียนรู้วิธีตรวจจับรูปแบบเอกสารใน Java ด้วย Aspose.Words และย้ายไฟล์โดยอัตโนมัติตามรูปแบบ
  ระบุ DOC, DOCX และอื่น ๆ
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: ตรวจจับรูปแบบเอกสารใน Java ด้วย Aspose.Words for Java
url: /th/java/document-loading-and-saving/determining-document-format/
weight: 25
---

 The `FileFormatInfo.isEncrypted()` flag identifies encrypted files, allowing you to move them to a secure folder without opening them.

Translate.

Fourth Q: **Q: Is there a performance impact when scanning large folders?**  
A: Detection reads only the file header, so even thousands of files are processed quickly. For very large batches, consider parallel streams.

Translate.

Fifth Q: **Q: How can I extend the script to convert unsupported formats?**  
A: After detection, you can call `Document.save` with the desired output format for any supported source type.

Translate.

Next heading: ## Conclusion

Translate.

Paragraph.

Then horizontal line.

Then **Last Updated:** 2026-02-22 (keep)

**Tested With:** Aspose.Words for Java 24.12 (latest) (keep)

**Author:** Aspose (keep)

Then closing shortcodes.

Make sure to preserve markdown formatting.

Now produce final content.

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# ตรวจจับรูปแบบเอกสาร Java ด้วย Aspose.Words for Java

เมื่อคุณต้อง **detect document format java** ในชุดไฟล์จำนวนมาก ความสามารถในการจัดเรียงไฟล์โดยอัตโนมัติไปยังโฟลเดอร์ที่ถูกต้องสามารถประหยัดเวลาการทำงานด้วยมือหลายชั่วโมง ในบทแนะนำนี้เราจะแสดงให้คุณเห็นว่า Aspose.Words for Java ทำให้การระบุ Word, RTF, HTML, ODT และรูปแบบอื่น ๆ ง่ายขึ้นอย่างไร และจากนั้น **move files by format** ไปยังไดเรกทอรีที่จัดระเบียบไว้

## คำตอบอย่างรวดเร็ว
- **What does “detect document format java” mean?** คือกระบวนการระบุรูปแบบการประมวลผลคำของไฟล์ (DOC, DOCX, RTF ฯลฯ) ด้วยโค้ด Java อย่างโปรแกรมเมติก  
- **Which library provides this capability?** Aspose.Words for Java มี API `FileFormatUtil.detectFileFormat` ให้บริการ  
- **Can the utility also handle encrypted files?** ใช่ – ธง `FileFormatInfo.isEncrypted()` จะบอกว่าหนังสือมีการป้องกันด้วยรหัสผ่านหรือไม่  
- **Do I need a license for production use?** จำเป็นต้องมีลิขสิทธิ์ Aspose.Words เชิงพาณิชย์สำหรับการใช้งานที่ไม่ใช่การประเมินผล  
- **Is it possible to move files automatically after detection?** แน่นอน – ผสานผลการตรวจจับกับ `FileUtils.copyFile` เพื่อจัดเรียงไฟล์ไปยังโฟลเดอร์ที่กำหนดเอง  

## อะไรคือ detect document format java?
`detect document format java` หมายถึงการใช้โค้ด Java ตรวจสอบส่วนหัวไบนารีของไฟล์และกำหนดว่ามันเป็นรูปแบบการประมวลผลคำใด (เช่น DOC, DOCX, ODT) Aspose.Words อ่านไฟล์โดยไม่ต้องโหลดเอกสารทั้งหมด ทำให้การดำเนินการเร็วและใช้หน่วยความจำน้อย

## ทำไมต้อง move files by format?
การจัดเอกสารตามรูปแบบดั้งเดิมทำให้ขั้นตอนต่อไปง่ายขึ้น:

- **Batch conversions** จะทำได้ง่ายเมื่อไฟล์ DOCX ทั้งหมดอยู่ในโฟลเดอร์เดียวกัน  
- **Legacy support**: คุณสามารถแยกไฟล์ Word รุ่นก่อน 97 เพื่อการจัดการพิเศษได้  
- **Security**: เอกสารที่เข้ารหัสสามารถแยกกักกันโดยอัตโนมัติ  

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำตามขั้นตอนต่อไปนี้ให้แน่ใจว่าคุณมี:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/) (ดาวน์โหลดเวอร์ชันล่าสุด)  
- Java Development Kit (JDK) 8 หรือสูงกว่า  
- ความคุ้นเคยพื้นฐานกับ Java I/O และ streams  

## Step 1: Set up directories for each format

เราจะสร้างโครงสร้างโฟลเดอร์ที่สะอาดเพื่อให้ไฟล์ที่ตรวจจับได้ถูกย้ายไปยังที่นั้น ทำให้เวิร์กโฟลว์เป็นระเบียบและง่ายต่อการเพิ่มประเภทรูปแบบใหม่ในภายหลัง

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

> **Pro tip:** ใช้เส้นทางแบบ absolute หรือกำหนดค่า base directory ผ่านไฟล์ properties เพื่อหลีกเลี่ยงการ hard‑code เส้นทางในโค้ดการผลิต

## Step 2: Detect the document format and move files

แกนหลักของ **detect document format java** อยู่ในลูปด้านล่าง มันสแกนทุกไฟล์ กำหนดประเภทของไฟล์ แล้วคัดลอกไปยังโฟลเดอร์ที่เหมาะสม

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

บล็อก `switch` สามารถขยายเพื่อรองรับรูปแบบที่คุณต้องการได้แต่ละ case จะพิมพ์ข้อความที่เป็นมิตรแล้วย้ายไฟล์ไปยังโฟลเดอร์ที่ตรงกัน

## Complete source code for detecting document format java

ด้านล่างเป็นตัวอย่างโค้ดเต็มที่พร้อมรัน ซึ่งรวมการตั้งค่าโฟลเดอร์และตรรกะการตรวจจับ คัดลอกไปยังคลาส Java ปรับ base path แล้วรันกับโฟลเดอร์ที่มีเอกสารผสมกัน

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

## Common issues and troubleshooting

| ปัญหา | สาเหตุ | วิธีแก้ไข |
|-------|--------|-----------|
| **`FileFormatUtil.detectFileFormat` returns `UNKNOWN`** | ไฟล์เสียหายหรือใช้รูปแบบที่ไม่ใช่ Word | ตรวจสอบนามสกุลไฟล์ หรือเพิ่ม fallback เพื่อย้ายไฟล์ไปยังโฟลเดอร์ *Unknown* (มีในตัวอย่าง) |
| **Encrypted files throw an exception** | API พยายามอ่านเนื้อหาก่อนตรวจสอบการเข้ารหัส | เรียก `info.isEncrypted()` ก่อนทำการดำเนินการอื่นใดกับเอกสาร |
| **Directory creation fails on Linux** | สิทธิ์ไม่เพียงพอหรือไม่มีโฟลเดอร์แม่ | ตรวจสอบให้แน่ใจว่าโปรเซส Java มีสิทธิ์เขียนและ base path มีอยู่ |

## Frequently Asked Questions

**Q: ฉันจะติดตั้ง Aspose.Words for Java อย่างไร?**  
A: คุณสามารถดาวน์โหลด Aspose.Words for Java จาก [here](https://releases.aspose.com/words/java/) และทำตามคำแนะนำการติดตั้งที่ให้มา

**Q: รูปแบบเอกสารใดบ้างที่รองรับการตรวจจับ?**  
A: Aspose.Words สามารถตรวจจับ DOC, DOCX, DOT, DOTX, DOCM, DOTM, RTF, HTML, MHTML, ODT, OTT, FLAT_OPC, WORD_ML และรูปแบบก่อน 97 รุ่นเก่าอื่น ๆ อีกหลายประเภท

**Q: โค้ดนี้สามารถจัดการกับเอกสารที่ป้องกันด้วยรหัสผ่านได้หรือไม่?**  
A: ได้ ธง `FileFormatInfo.isEncrypted()` จะระบุไฟล์ที่เข้ารหัส ทำให้คุณสามารถย้ายไฟล์เหล่านั้นไปยังโฟลเดอร์ปลอดภัยโดยไม่ต้องเปิดไฟล์

**Q: มีผลต่อประสิทธิภาพเมื่อสแกนโฟลเดอร์ขนาดใหญ่หรือไม่?**  
A: การตรวจจับอ่านเฉพาะส่วนหัวไฟล์เท่านั้น ดังนั้นแม้จะมีไฟล์หลายพันไฟล์ก็จะประมวลผลได้อย่างรวดเร็ว สำหรับชุดข้อมูลขนาดใหญ่มาก ควรพิจารณาใช้ parallel streams

**Q: ฉันจะขยายสคริปต์เพื่อแปลงรูปแบบที่ไม่รองรับได้อย่างไร?**  
A: หลังจากตรวจจับแล้ว คุณสามารถเรียก `Document.save` พร้อมระบุรูปแบบผลลัพธ์ที่ต้องการสำหรับประเภทแหล่งที่รองรับใด ๆ

## Conclusion

ด้วยการใช้ **detect document format java** ร่วมกับ Aspose.Words คุณจะได้วิธีที่เชื่อถือได้ในการจัดเรียง, กักกัน, หรือแปลงไฟล์ที่เกี่ยวข้องกับ Word อย่างอัตโนมัติ ตัวอย่างโค้ดแสดงวิธีสร้างโครงสร้างโฟลเดอร์ที่เป็นระเบียบ, ระบุรูปแบบของแต่ละไฟล์, และย้ายไฟล์ตามนั้น—ช่วยประหยัดเวลาและลดข้อผิดพลาดจากการทำงานด้วยมือ

---

**Last Updated:** 2026-02-22  
**Tested With:** Aspose.Words for Java 24.12 (latest)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}