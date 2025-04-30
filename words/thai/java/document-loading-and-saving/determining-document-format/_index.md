---
"description": "เรียนรู้วิธีการตรวจจับรูปแบบเอกสารใน Java ด้วย Aspose.Words ระบุ DOC, DOCX และอื่นๆ จัดระเบียบไฟล์อย่างมีประสิทธิภาพ"
"linktitle": "การกำหนดรูปแบบเอกสาร"
"second_title": "API การประมวลผลเอกสาร Java ของ Aspose.Words"
"title": "การกำหนดรูปแบบเอกสารใน Aspose.Words สำหรับ Java"
"url": "/th/java/document-loading-and-saving/determining-document-format/"
"weight": 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การกำหนดรูปแบบเอกสารใน Aspose.Words สำหรับ Java


## บทนำสู่การกำหนดรูปแบบเอกสารใน Aspose.Words สำหรับ Java

เมื่อทำงานกับการประมวลผลเอกสารใน Java สิ่งสำคัญคือการกำหนดรูปแบบของไฟล์ที่คุณกำลังจัดการ Aspose.Words สำหรับ Java มีคุณสมบัติอันทรงพลังสำหรับการระบุรูปแบบเอกสาร และเราจะแนะนำคุณตลอดกระบวนการ

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่มต้น ให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:

- [Aspose.คำศัพท์สำหรับภาษา Java](https://releases.aspose.com/words/java/)
- ติดตั้ง Java Development Kit (JDK) บนระบบของคุณ
- ความรู้พื้นฐานเกี่ยวกับการเขียนโปรแกรมภาษา Java

## ขั้นตอนที่ 1: การตั้งค่าไดเรกทอรี

ขั้นแรก เราต้องตั้งค่าไดเร็กทอรีที่จำเป็นเพื่อจัดระเบียบไฟล์อย่างมีประสิทธิภาพ เราจะสร้างไดเร็กทอรีสำหรับประเภทเอกสารต่างๆ

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

// สร้างไดเร็กทอรีหากยังไม่มีอยู่
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

เราได้สร้างไดเร็กทอรีสำหรับประเภทเอกสารที่รองรับ ไม่ทราบ เข้ารหัส และก่อนปี 97

## ขั้นตอนที่ 2: การตรวจจับรูปแบบเอกสาร

ตอนนี้เรามาตรวจสอบรูปแบบของเอกสารในไดเร็กทอรีกัน เราจะใช้ Aspose.Words สำหรับ Java เพื่อทำสิ่งนี้

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // แสดงประเภทเอกสาร
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // เพิ่มกรณีสำหรับรูปแบบเอกสารอื่น ๆ ตามความจำเป็น
    }

    // จัดการเอกสารที่เข้ารหัส
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // จัดการเอกสารประเภทอื่น ๆ
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

ในชิ้นส่วนโค้ดนี้ เราจะวนซ้ำผ่านไฟล์ ตรวจจับรูปแบบของไฟล์ และจัดระเบียบไฟล์เหล่านั้นในไดเร็กทอรีที่เกี่ยวข้อง

## โค้ดต้นฉบับที่สมบูรณ์สำหรับการกำหนดรูปแบบเอกสารใน Aspose.Words สำหรับ Java

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        // สร้างไดเร็กทอรีหากยังไม่มีอยู่
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
            // แสดงประเภทเอกสาร
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

## บทสรุป

การกำหนดรูปแบบเอกสารใน Aspose.Words สำหรับ Java ถือเป็นสิ่งสำคัญสำหรับการประมวลผลเอกสารอย่างมีประสิทธิภาพ โดยขั้นตอนต่างๆ ที่ระบุไว้ในคู่มือนี้จะช่วยให้คุณระบุประเภทเอกสารและจัดการเอกสารเหล่านั้นในแอปพลิเคชัน Java ได้อย่างเหมาะสม

## คำถามที่พบบ่อย

### ฉันจะติดตั้ง Aspose.Words สำหรับ Java ได้อย่างไร?

คุณสามารถดาวน์โหลด Aspose.Words สำหรับ Java ได้จาก [ที่นี่](https://releases.aspose.com/words/java/) และปฏิบัติตามคำแนะนำในการติดตั้งที่ให้ไว้

### รูปแบบเอกสารที่รองรับมีอะไรบ้าง?

Aspose.Words สำหรับ Java รองรับรูปแบบเอกสารต่างๆ เช่น DOC, DOCX, RTF, HTML และอื่นๆ อีกมากมาย คุณสามารถดูรายการทั้งหมดได้ในเอกสารประกอบ

### ฉันจะตรวจจับเอกสารที่เข้ารหัสโดยใช้ Aspose.Words สำหรับ Java ได้อย่างไร

คุณสามารถใช้ `FileFormatUtil.detectFileFormat()` วิธีการตรวจจับเอกสารที่เข้ารหัส ตามที่แสดงในคู่มือนี้

### มีข้อจำกัดใด ๆ เมื่อทำงานกับรูปแบบเอกสารรุ่นเก่าหรือไม่?

รูปแบบเอกสารเก่า เช่น MS Word 6 หรือ Word 95 อาจมีข้อจำกัดในแง่ของคุณลักษณะและความเข้ากันได้กับแอปพลิเคชันสมัยใหม่ ควรพิจารณาอัปเกรดหรือแปลงเอกสารเหล่านี้เมื่อจำเป็น

### ฉันสามารถตรวจจับรูปแบบเอกสารแบบอัตโนมัติในแอปพลิเคชัน Java ของฉันได้หรือไม่

ใช่ คุณสามารถทำให้การตรวจจับรูปแบบเอกสารเป็นแบบอัตโนมัติได้โดยการผสานรวมโค้ดที่ให้มาไว้ในแอปพลิเคชัน Java ของคุณ วิธีนี้ช่วยให้คุณประมวลผลเอกสารตามรูปแบบที่ตรวจพบได้


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}