---
category: general
date: 2026-04-28
description: วนซ้ำคำเตือนของเอกสารในไฟล์ Word เพื่อตรวจจับฟอนต์ที่หายไป ดึงชื่อฟอนต์ที่หายไปและพิมพ์รายละเอียดฟอนต์ที่หายไปโดยใช้
  Aspose.Words for Java.
draft: false
keywords:
- iterate document warnings
- detect missing fonts
- load word document
- retrieve missing font
- print missing font
language: th
og_description: วนซ้ำคำเตือนของเอกสารเพื่อค้นหาแบบอักษรที่หายไป ดึงชื่อแบบอักษรที่หายไป
  และพิมพ์รายละเอียดของแบบอักษรที่หายไปพร้อมตัวอย่าง Java แบบครบถ้วน.
og_title: 'วนซ้ำคำเตือนเอกสาร: ตรวจจับฟอนต์ที่หายไปใน Java'
tags:
- Aspose.Words
- Java
- Document Processing
title: 'วนลูปคำเตือนเอกสาร: ตรวจจับฟอนต์ที่หายไปใน Java'
url: /th/java/document-operations/iterate-document-warnings-detect-missing-fonts-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วนซ้ำคำเตือนเอกสาร – ตรวจจับฟอนต์ที่หายไปใน Java

เคยต้องการ **วนซ้ำคำเตือนเอกสาร** ขณะเปิดไฟล์ Word แล้วสงสัยว่าฟอนต์ใดหายไปบ้างหรือไม่? คุณไม่ได้เป็นคนเดียว ฟอนต์ที่หายไปอาจทำให้รูปแบบของรายงานเสียหาย และหากไม่มีวิธีตรวจจับคุณอาจส่งเอกสารที่ดูไม่เหมือนต้นฉบับเลย  

ในบทแนะนำนี้เราจะสาธิตวิธี **detect missing fonts** โดยการโหลดเอกสาร Word, วนซ้ำคำเตือน, ดึงชื่อฟอนต์ที่หายไป, และสุดท้ายพิมพ์ข้อมูลฟอนต์ที่หายไป—ทั้งหมดนี้ด้วย Aspose.Words for Java  

เราจะครอบคลุมตั้งแต่บรรทัดแรกของโค้ดจนถึงผลลัพธ์คอนโซลที่คาดหวัง เพื่อให้คุณสามารถคัดลอก‑วางโซลูชันที่ทำงานได้ลงในโปรเจกต์ของคุณได้ทันที ไม่ต้องอ้างอิงเอกสารเพิ่มเติม

## Prerequisites

- ติดตั้ง Java 8 หรือใหม่กว่า
- ไลบรารี Aspose.Words for Java (รุ่นล่าสุด ณ วันที่ 2026‑04‑28)
- ไฟล์ Word ที่อาจมีฟอนต์ที่ไม่ได้ติดตั้งบนเครื่องของคุณ (เช่น `doc-with-missing-font.docx`)

หากคุณมีทั้งหมดแล้ว ยอดเยี่ยม—คุณพร้อมที่จะ **load word document** และเริ่มวนซ้ำแล้ว

## Step 1 – Load Word Document with Default Options

ก่อนที่เราจะ **iterate document warnings** ไฟล์ต้องถูกโหลดเข้าสู่หน่วยความจำ Aspose.Words ให้คุณทำเช่นนี้ด้วยการเรียกคอนสตรัคเตอร์เพียงหนึ่งครั้ง การใช้ `LoadOptions` เริ่มต้นมักเพียงพอ แต่เราจะสาธิตการสร้างอย่างชัดเจนเพื่อความเข้าใจ

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {

        // Step 1: Prepare load options (default settings are fine for this example)
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/doc-with-missing-font.docx", loadOptions);
```

> **ทำไมเรื่องนี้ถึงสำคัญ:**  
> การโหลดเอกสารทำให้ Aspose.Words สแกนไฟล์เพื่อหาทรัพยากรที่ไม่สามารถแก้ไขได้ เช่น ฟอนต์ที่ไม่ได้ติดตั้งในเครื่อง ปัญหาเหล่านี้จะถูกเก็บเป็น **warnings** ซึ่งเราจะ **iterate document warnings** ในขั้นตอนต่อไป

## Step 2 – Iterate Document Warnings to Find Font Issues

ตอนนี้มาถึงหัวใจของวิธีแก้: เราจะวนลูปผ่านทุก warning ที่ไลบรารีเก็บไว้ขณะโหลด `WarningInfo` จะบอกว่าอะไรผิดพลาดและเราสามารถกรอง `FontSubstitutionWarning` เพื่อ **detect missing fonts** ได้

```java
        // Step 3: Iterate over all warnings generated during loading
        for (WarningInfo warningInfo : document.getWarnings()) {
            // Step 4: Identify font substitution warnings
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;

                // Step 5: Output the missing font name and the font that was used as a substitute
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }
    }
}
```

> **เคล็ดลับ:** การตรวจสอบ `instanceof` ทำให้เราจัดการเฉพาะ warning ที่เกี่ยวกับฟอนต์เท่านั้น ไม่สนใจ warning ประเภทอื่นเช่นปัญหาโหลดรูปภาพ ทำให้ลูปทำงานได้อย่างมีประสิทธิภาพและผลลัพธ์มุ่งเน้นที่ฟอนต์ที่คุณต้อง **retrieve missing font** จริง ๆ

### Expected Console Output

```
Missing font: Arial Black
Substituted with: Liberation Sans
Missing font: Calibri
Substituted with: Liberation Sans
```

หากเอกสารไม่มีฟอนต์ที่หายไป ลูปจะจบอย่างเงียบ ๆ — ไม่มีอะไรให้ **print missing font**  

## Step 3 – Why Not Just Catch an Exception?

คุณอาจสงสัย “ทำไมไม่ห่อ `new Document(...)` ด้วย try‑catch แล้วตรวจหา Exception?” คำตอบมีสองประการ:

1. **ข้อมูลละเอียด:** Exception เพียงบอกว่ามีบางอย่างล้มเหลว Warning จะให้ชื่อฟอนต์ที่หายไปและฟอนต์สำรองที่ Aspose.Words เลือกใช้
2. **ปัญหาไม่ทำให้โปรแกรมหยุดทำงาน:** ฟอนต์ที่หายไปมักไม่ทำให้การโหลดล้มเหลว เอกสารยังโหลดได้ แต่ความแม่นยำของการแสดงผลอาจเสียหาย โดยการ **วนซ้ำคำเตือนเอกสาร** คุณยังคงสามารถประมวลผลส่วนที่เหลือของไฟล์ได้

## Step 4 – Extending the Example: Collecting Missing Fonts into a List

บางครั้งคุณต้องการฟอนต์ที่หายไปเพื่อการประมวลผลต่อไป — อาจจะฝังฟอนต์หรือแจ้งผู้ใช้ผ่าน UI นี่คือตัวอย่างการปรับเล็กน้อยที่รวบรวมชื่อฟอนต์ลงใน `Set<String>`

```java
        // Collect missing fonts for later use
        Set<String> missingFonts = new HashSet<>();

        for (WarningInfo warningInfo : document.getWarnings()) {
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;
                missingFonts.add(fontWarning.getMissingFontName());

                // Still print for immediate feedback
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }

        // Example of using the collected data
        System.out.println("Total missing fonts: " + missingFonts.size());
```

ตอนนี้คุณมีวิธีที่สะอาดในการ **retrieve missing font** อย่างโปรแกรมเมติก ซึ่งสามารถส่งต่อให้โมดูลรายงานหรือวิซาร์ดติดตั้งฟอนต์ได้  

## Step 5 – Real‑World Considerations

- **การแทนที่หลายแบบ:** ฟอนต์ที่หายไปหนึ่งตัวอาจถูกแทนที่ด้วยฟอนต์ต่าง ๆ ในส่วนต่าง ๆ ของเอกสาร รายการ Warning จะบันทึกแต่ละกรณี ดังนั้นคุณอาจเห็นรายการฟอนต์ที่หายซ้ำกัน
- **ประสิทธิภาพ:** การโหลดเอกสารขนาดใหญ่อาจสร้าง Warning เป็นพันรายการ หากคุณสนใจเฉพาะฟอนต์เท่านั้น ควรกรองตั้งแต่ต้นเพื่อให้ลูปทำงานเร็ว
- **ฟอนต์ข้ามแพลตฟอร์ม:** บน Linux ฟอนต์สำรองเริ่มต้นมักเป็น *Liberation Sans* ส่วนบน Windows อาจเป็น *Arial* การรู้ฟอนต์สำรองช่วยให้คุณตัดสินใจได้ว่าต้องจัดเตรียมฟอนต์แบบกำหนดเองกับแอปพลิเคชันของคุณหรือไม่

## Step 6 – Visual Aid

ด้านล่างเป็นภาพหน้าจอของผลลัพธ์คอนโซล (ข้อความ alt มีคีย์เวิร์ดหลักสำหรับ SEO)

![แสดงผลคอนโซลของการวนซ้ำคำเตือนเอกสารที่แสดงฟอนต์ที่หายไปและฟอนต์สำรอง](/images/iterate-document-warnings.png)

*Alt text:* *ตัวอย่างการวนซ้ำคำเตือนเอกสารแสดงชื่อฟอนต์ที่หายไปและรายละเอียดการแทนที่*  

## Conclusion

คุณเพิ่งเรียนรู้วิธี **iterate document warnings** ใน Aspose.Words for Java, **detect missing fonts**, **load word document** อย่างปลอดภัย, **retrieve missing font** อย่างเป็นระบบ, และ **print missing font** ไปยังคอนโซล โค้ดเต็มทำงานได้ทันทีและคุณสามารถปรับให้บันทึกลงไฟล์, แสดงใน UI dialog, หรือแม้กระทั่งฝังฟอนต์ที่หายไปโดยอัตโนมัติได้  

ต่อไปคุณอาจอยากสำรวจวิธี **load word document** ด้วยแหล่งฟอนต์กำหนดเอง (เช่นเพิ่มโฟลเดอร์ฟอนต์ของบริษัท) หรือวิธีฝังฟอนต์ที่หายไปโดยตรงลงในไฟล์เพื่อรักษาเลย์เอาต์ข้ามเครื่อง ทั้งสองหัวข้อสร้างต่อเนื่องจากสิ่งที่เราได้ครอบคลุมไว้ที่นี่  

Happy coding, and may your PDFs always look exactly as you intended!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}