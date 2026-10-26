---
category: general
date: 2026-10-26
description: เรียนรู้วิธีกำหนดการเข้ารหัสใน Java ด้วย LoadOptions คู่มือนี้ครอบคลุมการเข้ารหัสอักขระ
  วิธี setEncoding และตัวเลือกการโหลดเอกสาร
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to specify encoding
- character encoding in Java
- LoadOptions encoding
- setEncoding method
- document loading options
- Aspose.Words for Java
language: th
lastmod: 2026-10-26
og_description: วิธีระบุการเข้ารหัสใน Java ด้วย Aspose.Words. ติดตามบทแนะนำเต็มรูปแบบนี้เพื่อโหลดเอกสารด้วยชุดอักขระที่ถูกต้อง.
og_image_alt: Screenshot showing how to specify encoding in Java LoadOptions
og_title: วิธีระบุการเข้ารหัสใน Java ด้วย Aspose.Words – คู่มือแบบทีละขั้นตอน
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to specify encoding in Java using LoadOptions. This guide
    covers character encoding, setEncoding method, and document loading options.
  headline: How to specify encoding when loading a document with Aspose.Words for
    Java
  type: TechArticle
- description: Learn how to specify encoding in Java using LoadOptions. This guide
    covers character encoding, setEncoding method, and document loading options.
  name: How to specify encoding when loading a document with Aspose.Words for Java
  steps:
  - name: 5.1 Loading from an `InputStream`
    text: 'Sometimes you receive a document as a stream (e.g., from a web service).
      You can still control the encoding by passing the stream together with `LoadOptions`:'
  - name: 5.2 Fallback when the encoding is unknown
    text: If you cannot determine the source file’s charset, you can attempt a detection
      library (such as ICU4J) before setting the encoding. Once you have a guess,
      invoke `setEncoding` with that value. This approach reduces the risk of mis‑decoded
      text.
  - name: 5.3 Dealing with unsupported encodings
    text: Java supports a wide range of code pages, but a few legacy encodings may
      be missing. In that case, consider converting the file to UTF‑8 externally (e.g.,
      using `iconv`) before loading it with Aspose.Words. After conversion, you can
      omit the `setEncoding` call because UTF‑8 is the default for most m
  type: HowTo
tags:
- Java
- Encoding
- Aspose.Words
title: วิธีระบุการเข้ารหัสเมื่อโหลดเอกสารด้วย Aspose.Words for Java
url: /th/java/document-loading-and-saving/how-to-specify-encoding-when-loading-a-document-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีระบุการเข้ารหัสเมื่อโหลดเอกสารด้วย Aspose.Words for Java

หากคุณต้องการ **วิธีระบุการเข้ารหัส** สำหรับไฟล์ต้นทางใน Java บทแนะนำนี้จะแสดงขั้นตอนที่ชัดเจน ไม่ว่ากรณีเอกสารจะใช้ Big5, UTF‑8 หรือชุดอักขระอื่น ๆ คุณก็สามารถควบคุมกระบวนการอ่านด้วย `LoadOptions` ได้ เมื่อจบคู่มือคุณจะเข้าใจว่าการเข้ารหัสอักขระสำคัญอย่างไร วิธีใช้เมธอด `setEncoding` และวิธีตรวจสอบว่าเอกสารถูกโหลดอย่างถูกต้องหรือไม่

การโหลดเอกสารด้วยการเข้ารหัสอักขระที่ถูกต้องช่วยป้องกันข้อความแสดงผลเป็นอักขระผสมและทำให้เนื้อหาหลายภาษาแสดงผลตามที่ต้องการ บทแนะนำนี้ครอบคลุม:

* บทบาทของ **character encoding in Java** ขณะอ่านไฟล์
* วิธีกำหนด **LoadOptions encoding** สำหรับ Aspose.Words
* โค้ดตัวอย่างที่คุณสามารถคัดลอกไปใช้ในโปรเจกต์
* ข้อผิดพลาดทั่วไป เช่น การเข้ารหัสไม่ตรงกันและวิธีแก้ไข

## ข้อกำหนดเบื้องต้น

ก่อนเริ่มทำตามขั้นตอน ให้ตรวจสอบว่าคุณมี:

* Java Development Kit (JDK) 8 หรือสูงกว่า
* Maven หรือ Gradle เพื่อจัดการ dependencies
* Aspose.Words for Java 23.10 หรือใหม่กว่า (เวอร์ชันที่ใช้ในคู่มือนี้)
* ตัวอย่างไฟล์ข้อความ (`input.doc`) ที่บันทึกด้วยการเข้ารหัสที่ต้องการ (เช่น Big5)

คุณไม่จำเป็นต้องใช้ไลบรารีเพิ่มเติม; ตัวอย่างนี้ใช้เฉพาะ API หลักของ Aspose.Words เท่านั้น

## ขั้นตอนที่ 1: เพิ่ม Aspose.Words ไปยังโปรเจกต์ของคุณ

หากคุณใช้ Maven ให้เพิ่ม dependency ต่อไปนี้ในไฟล์ `pom.xml` ของคุณ:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

สำหรับ Gradle ให้ใส่บรรทัดนี้ในไฟล์ `build.gradle` ของคุณ:

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

การรวมไลบรารีนี้ทำให้คลาส `LoadOptions`, `Document` และ `Encoding` พร้อมใช้งาน

## ขั้นตอนที่ 2: สร้างอินสแตนซ์ `LoadOptions`

`LoadOptions` ให้คุณปรับแต่งวิธีที่ Aspose.Words เปิดไฟล์ การสร้างอ็อบเจกต์นี้เป็นส่วนแรกของ **วิธีระบุการเข้ารหัส**  

```java
// Step 2: Create load options to customize how the document is opened
LoadOptions loadOptions = new LoadOptions();
```

อ็อบเจกต์ `LoadOptions` จะเริ่มต้นด้วยการตั้งค่าเริ่มต้น คุณจะทำการปรับคุณสมบัติต่าง ๆ ในขั้นตอนต่อไป

## ขั้นตอนที่ 3: ตั้งค่าการเข้ารหัสอักขระที่ต้องการ

เมธอด `setEncoding` กำหนด **character encoding in Java** ที่ตัวโหลดควรใช้ ในตัวอย่างนี้เราเลือกหน้าโค้ด Big5 ซึ่งเป็นที่นิยมสำหรับไฟล์ข้อความภาษาจีนดั้งเดิม  

```java
// Step 3: Specify the character encoding (Big5) for the source file
loadOptions.setEncoding(Encoding.getEncoding("Big5"));
```

*ทำไมจึงสำคัญ*: หากไบต์ของไฟล์ถูกตีความด้วยหน้าโค้ดที่ผิด ตัวอักขระจะปรากฏเป็นเครื่องหมายคำถามหรือข้อความผสมโดยไม่มีความหมาย การเรียก `setEncoding` อย่างชัดเจนบอกให้ Aspose.Words ถอดรหัสสตรีมไบต์โดยใช้ตารางแมปปิ้งของ Big5

คุณสามารถเปลี่ยน `"Big5"` เป็นชื่อ charset ใด ๆ ที่ Java รองรับ เช่น `"UTF-8"`, `"ISO-8859-1"` หรือ `"Windows-1252"` เมธอดจะโยน `UnsupportedEncodingException` หากชื่อไม่ถูกต้อง ดังนั้นคุณอาจต้องจับข้อยกเว้นนี้ในโค้ดการผลิต

## ขั้นตอนที่ 4: โหลดเอกสารด้วยตัวเลือกที่กำหนด

เมื่อ **LoadOptions encoding** ถูกตั้งค่าแล้ว ให้ส่งตัวเลือกไปยังคอนสตรัคเตอร์ของ `Document` ขั้นตอนนี้จะสรุปกระบวนการ **วิธีระบุการเข้ารหัส**  

```java
// Step 4: Load the document using the configured options
Document doc = new Document("YOUR_DIRECTORY/input.doc", loadOptions);
```

แทนที่ `YOUR_DIRECTORY` ด้วยพาธแบบ absolute หรือ relative ไปยังไฟล์ของคุณ อินสแตนซ์ `Document` ตอนนี้จะมีเนื้อหาที่ถูกแยกวิเคราะห์อย่างเต็มที่ตามการเข้ารหัสที่คุณระบุ

## ขั้นตอนที่ 5: ตรวจสอบว่าข้อความโหลดอย่างถูกต้อง

การตรวจสอบอย่างรวดเร็วช่วยให้คุณมั่นใจว่าการเข้ารหัสถูกนำไปใช้ตามที่คาดไว้ คุณสามารถดึงข้อความของเอกสารและพิมพ์ออกคอนโซลได้ดังนี้  

```java
// Step 5: Output the document text to verify correct decoding
System.out.println(doc.getText());
```

หากคอนโซลแสดงอักขระจีนที่อ่านได้ (หรือภาษาที่คุณคาดหวัง) การเข้ารหัสทำงานสำเร็จ หากยังเห็นข้อความผสม ให้ตรวจสอบการเข้ารหัสของไฟล์ต้นฉบับอีกครั้งและยืนยันว่าชื่อ charset ตรงกันอย่างแม่นยำ

## การจัดการกรณีขอบทั่วไป

### 5.1 โหลดจาก `InputStream`

บางครั้งคุณอาจได้รับเอกสารเป็นสตรีม (เช่น จากเว็บเซอร์วิส) คุณยังคงควบคุมการเข้ารหัสได้โดยส่งสตรีมพร้อมกับ `LoadOptions`  

```java
try (InputStream stream = new FileInputStream("YOUR_DIRECTORY/input.doc")) {
    Document docFromStream = new Document(stream, loadOptions);
    System.out.println(docFromStream.getText());
}
```

ตัวเลือก **document loading options** ยังคงใช้ได้เหมือนเดิม และการเรียก `setEncoding` ไม่เปลี่ยนแปลง

### 5.2 วิธีสำรองเมื่อไม่ทราบการเข้ารหัส

หากคุณไม่สามารถระบุ charset ของไฟล์ต้นทางได้ คุณอาจใช้ไลบรารีตรวจจับ (เช่น ICU4J) เพื่อคาดเดาก่อนตั้งค่าเข้ารหัส เมื่อได้ค่าคาดเดาแล้ว ให้เรียก `setEncoding` ด้วยค่านั้น วิธีนี้ช่วยลดความเสี่ยงของข้อความที่ถอดรหัสผิดพลาด

### 5.3 จัดการกับการเข้ารหัสที่ไม่รองรับ

Java รองรับหน้าโค้ดหลายร้อยแบบ แต่บาง charset เก่าอาจไม่มีในระบบ ในกรณีนั้นพิจารณาแปลงไฟล์เป็น UTF‑8 ภายนอก (เช่น ใช้ `iconv`) ก่อนโหลดด้วย Aspose.Words หลังจากแปลงแล้วคุณสามารถละเว้นการเรียก `setEncoding` ได้ เนื่องจาก UTF‑8 เป็นค่าเริ่มต้นของ API สมัยใหม่ส่วนใหญ่

## เคล็ดลับพิเศษ: ใช้ `LoadOptions` ซ้ำสำหรับการประมวลผลเป็นชุด

หากคุณต้องโหลดเอกสารหลายไฟล์ที่ใช้ charset เดียวกัน ให้สร้างอินสแตนซ์ `LoadOptions` เพียงหนึ่งตัวและใช้ซ้ำ  

```java
LoadOptions sharedOptions = new LoadOptions();
sharedOptions.setEncoding(Encoding.getEncoding("Big5"));

String[] files = {"doc1.doc", "doc2.doc", "doc3.doc"};
for (String file : files) {
    Document d = new Document("YOUR_DIRECTORY/" + file, sharedOptions);
    // Process each document...
}
```

การใช้ซ้ำอ็อบเจกต์ช่วยลดภาระการสร้างอ็อบเจกต์และรับประกันการเข้ารหัสที่สอดคล้องกันทั่วทั้งชุด

## ตัวอย่างโปรแกรมที่สามารถรันได้เต็มรูปแบบ

ด้านล่างเป็นโปรแกรมสมบูรณ์ที่รวมทุกขั้นตอน รวมถึงการ import ที่จำเป็นและการจัดการข้อยกเว้นที่อาจเกิดขึ้น  

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import com.aspose.words.Encoding;

import java.io.FileInputStream;
import java.io.InputStream;
import java.io.UnsupportedEncodingException;

public class LoadDocumentWithEncoding {
    public static void main(String[] args) {
        // Path to the input document
        String inputPath = "YOUR_DIRECTORY/input.doc";

        try {
            // Create LoadOptions and set the desired charset (Big5 in this case)
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setEncoding(Encoding.getEncoding("Big5"));

            // Load the document using the configured options
            Document doc = new Document(inputPath, loadOptions);

            // Output the document text to verify correct decoding
            System.out.println("Document text:");
            System.out.println(doc.getText());

            // Optional: load from InputStream using the same options
            try (InputStream stream = new FileInputStream(inputPath)) {
                Document docFromStream = new Document(stream, loadOptions);
                System.out.println("Text from stream:");
                System.out.println(docFromStream.getText());
            }

        } catch (UnsupportedEncodingException e) {
            System.err.println("The specified encoding is not supported: " + e.getMessage());
        } catch (Exception e) {
            System.err.println("Error loading document: " + e.getMessage());
        }
    }
}
```

**ผลลัพธ์ที่คาดหวัง** (สมมติว่าไฟล์ต้นทางมีข้อความจีนที่เข้ารหัสเป็น Big5)  

```
Document text:
【此處顯示正確的中文內容】...
Text from stream:
【此處顯示正確的中文內容】...
```

หากผลลัพธ์แสดงสัญลักษณ์ที่อ่านไม่ออก ให้ตรวจสอบชื่อ charset อีกครั้งหรือยืนยันการเข้ารหัสดั้งเดิมของไฟล์

## คำถามที่พบบ่อย

**วิธีนี้ทำงานกับรูปแบบเอกสารอื่น (DOCX, RTF, HTML) หรือไม่?**  
ใช่. อ็อบเจกต์ `LoadOptions` เดียวกันใช้ได้กับทุกฟอร์แมตที่ Aspose.Words รองรับ เงื่อนไขเดียวคือไฟล์พื้นฐานต้องใช้ charset ที่ระบุจริง ๆ

**ถ้าต้องการเปลี่ยนการเข้ารหัสหลังจากโหลดเอกสารแล้วทำอย่างไร?**  
การเข้ารหัสมีผลเฉพาะขั้นตอนการอ่านเท่านั้น เมื่ออ็อบเจกต์ `Document` ถูกสร้างขึ้น ตัวแทน Unicode ภายในจะเป็นอิสระจาก charset ดั้งเดิม หากต้องการเปลี่ยนการเข้ารหัสของผลลัพธ์ ให้ปรับ `SaveOptions` ตอนบันทึกไฟล์

**สามารถใช้วิธีนี้กับไลบรารีอื่น (เช่น Apache POI) ได้หรือไม่?**  
Apache POI มีการตรวจจับ charset ของตนเองสำหรับฟอร์แมตไบนารีเก่า แต่แนวคิดของการส่ง charset ให้ loader นั้นคล้ายกัน สำหรับ Aspose.Words `LoadOptions` คือวิธีทางการในการควบคุม **วิธีระบุการเข้ารหัส**

## สรุป

คุณได้เรียนรู้ **วิธีระบุการเข้ารหัส** เมื่อโหลดเอกสารด้วย Aspose.Words for Java โดยการสร้างอ็อบเจกต์ `LoadOptions` เรียกเมธอด `setEncoding` และส่งตัวเลือกไปยังคอนสตรัคเตอร์ของ `Document` คุณจะมั่นใจได้ว่าไบต์ของไฟล์ถูกตีความอย่างถูกต้อง วิธีนี้ช่วยขจัดข้อความแสดงผลเป็นอักขระผสม รองรับเนื้อหาหลายภาษา และทำงานร่วมกับการประมวลผลเป็นชุดหรือการทำงานกับสตรีมได้อย่างราบรื่น

สำรวจหัวข้อที่เกี่ยวข้อง เช่น **document loading options**, **saving with specific encodings**, และ **handling Unicode in Java** เพื่อเพิ่มพูนความเชี่ยวชาญด้านการประมวลผลข้อความ ทดลองใช้ charset ชื่ออื่น ๆ ผสานวิธีนี้กับการแปลงเป็น PDF หรือรวมเข้าในเว็บเซอร์วิสที่รับไฟล์อัปโหลดในหลายรูปแบบ

Happy coding!

## สิ่งที่คุณควรเรียนต่อไป

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานอื่น ๆ ในโปรเจกต์ของคุณ

- [How to Convert RTF Text with UTF-8 Encoding in Java Using Aspose.Words](/words/english/java/document-operations/load-rtf-with-utf8-java-asposewords/)
- [How to set options in Aspose.Words for Java – complete guide](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [Recover Corrupted DOCX Word Document Using Aspose.Words LoadOptions – Java Guide](/words/english/java/document-loading-and-saving/recover-corrupted-word-document-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}