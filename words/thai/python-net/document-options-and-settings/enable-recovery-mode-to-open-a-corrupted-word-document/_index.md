---
category: general
date: 2026-09-30
description: เปิดโหมดการกู้คืนเพื่อเปิดเอกสาร Word ที่เสียหายโดยใช้ Aspose.Words.
  เรียนรู้วิธีกู้คืนไฟล์ docx ที่เสียหายอย่างปลอดภัยและเชื่อถือได้.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- enable recovery mode
- open corrupted word document
- recover corrupted docx
- how to open corrupted docx
- load document with recovery
language: th
lastmod: 2026-09-30
og_description: เปิดใช้งานโหมดการกู้คืนเพื่อเปิดเอกสาร Word ที่เสียหายด้วย Aspose.Words
  คู่มือนี้แสดงขั้นตอนทีละขั้นตอนในการกู้คืนไฟล์ docx ที่เสียหายและทำให้กระบวนการทำงานของคุณมั่นคง
og_image_alt: Code snippet showing Aspose.Words recovery mode enabled for a corrupted
  DOCX
og_title: เปิดใช้งานโหมดกู้คืนเพื่อเปิดเอกสาร Word ที่เสียหาย
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Enable recovery mode to open a corrupted Word document using Aspose.Words.
    Learn how to recover corrupted docx files safely and reliably.
  headline: Enable recovery mode to open a corrupted Word document
  type: TechArticle
tags:
- Aspose.Words
- Python
- Document recovery
title: เปิดใช้งานโหมดการกู้คืนเพื่อเปิดเอกสาร Word ที่เสียหาย
url: /th/python/document-options-and-settings/enable-recovery-mode-to-open-a-corrupted-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# เปิดโหมดการกู้คืนเพื่อเปิดไฟล์ Word ที่เสียหาย

หากคุณต้องการ **เปิดโหมดการกู้คืน** ขณะเปิดไฟล์ Word ที่เสียหาย, บทแนะนำนี้จะแสดงให้คุณเห็นขั้นตอนอย่างละเอียดโดยใช้ Aspose.Words for Python ไม่ว่ไฟล์จะเสียหายระหว่างการถ่ายโอนหรือถูกแก้ไขโดยโปรแกรมที่ไม่เข้ากัน การเปิดโหมดการกู้คืนจะทำให้ไลบรารีพยายามซ่อมแซมเอกสารแทนการโยนข้อยกเว้น

ในคู่มือนี้คุณจะได้เรียนรู้วิธี **เปิดไฟล์ word ที่เสียหาย** , **กู้คืนเนื้อหา docx ที่เสียหาย** และทำความเข้าใจตัวเลือกที่ควบคุมกระบวนการ **โหลดเอกสารพร้อมการกู้คืน** ขั้นตอนเหล่านี้ทำงานกับ Aspose.Words 23.10 (รุ่นล่าสุดขณะเขียน) และต้องการเพียงสภาพแวดล้อม Python มาตรฐาน

## ข้อกำหนดเบื้องต้น

* ติดตั้ง Python 3.9 หรือใหม่กว่า
* ติดตั้ง Aspose.Words for Python ผ่าน .NET (`aspose-words`) (`pip install aspose-words`).
* ไฟล์ DOCX ที่ทราบว่าเสียหาย (สำหรับการทดสอบคุณสามารถเปลี่ยนชื่อไฟล์ `.docx` ที่ใช้งานได้เป็น `.zip` แล้วทำให้ XML เสียหายด้วยตนเอง)

> **เคล็ดลับ:** เก็บสำเนาสำรองของไฟล์ต้นฉบับไว้ โหมดการกู้คืนจะปรับเปลี่ยนเอกสารในหน่วยความจำเท่านั้นและจะไม่เขียนกลับไปยังแหล่งที่มาจนกว่าคุณจะบันทึกโดยเจตนา

## ขั้นตอนที่ 1: นำเข้าห้องสมุดและสร้างตัวเลือกการโหลด

สิ่งแรกที่คุณต้องทำคือ import `aspose.words` และสร้างอ็อบเจ็กต์ `LoadOptions` อ็อบเจ็กต์นี้เก็บการตั้งค่าทั้งหมดที่มีผลต่อการอ่านไฟล์

```python
import aspose.words as aw

# Create load options – this is where we will enable recovery mode
load_options = aw.loading.LoadOptions()
```

*ทำไมเรื่องนี้สำคัญ:* `LoadOptions` เป็นประตูสู่การปรับแต่งพาร์เซอร์อย่างละเอียด หากไม่มีมัน Aspose.Words จะใช้โหมดเข้มงวดค่าเริ่มต้น ซึ่งจะหยุดทำงานเมื่อพบข้อผิดพลาดโครงสร้างใด ๆ

## ขั้นตอนที่ 2: เปิดโหมดการกู้คืน

ตั้งค่า property `recovery_mode` เป็น `RecoveryMode.RECOVER` ซึ่งบอกให้ตัวโหลดพยายามซ่อมแซมอัตโนมัติส่วนที่เสีย เช่น โหนด XML ที่หายไป ความสัมพันธ์ที่ขาดหาย หรือสตรีมที่ถูกตัด

```python
# Enable recovery mode – the core of “enable recovery mode” for this tutorial
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER
```

การเปิดโหมดการกู้คืน **ไม่ได้** รับประกันว่าเอกสารจะสมบูรณ์แบบ แต่จะเพิ่มโอกาสอย่างมากที่คุณยังสามารถดึงข้อความ รูปภาพ หรือ ตารางออกมาได้

## ขั้นตอนที่ 3: โหลด DOCX ที่อาจเสียหายด้วยตัวเลือกที่กำหนดไว้

ต่อไปใช้คอนสตรัคเตอร์ `Document` ที่รับทั้งเส้นทางไฟล์และอินสแตนซ์ `LoadOptions`

```python
# Path to the corrupted file – replace with your actual location
corrupted_path = "YOUR_DIRECTORY/corrupted.docx"

try:
    # Load the document using the recovery‑enabled options
    document = aw.Document(corrupted_path, load_options)
    print("Document loaded successfully with recovery mode.")
except aw.core.exceptions.InvalidOperationException as ex:
    # If recovery fails, the library throws an exception
    print(f"Failed to load document even with recovery mode: {ex}")
```

*ทำไมเรื่องนี้สำคัญ:* บล็อก `try/except` แสดง **วิธีเปิด docx ที่เสียหาย** อย่างปลอดภัย หากไม่มีโหมดการกู้คืน การเรียกเดียวกันจะโยนข้อยกเว้นทันทีและทำให้โปรแกรมหยุดทำงาน

## ขั้นตอนที่ 4: ตรวจสอบเนื้อหาที่กู้คืน (ไม่บังคับแต่แนะนำ)

หลังจากโหลดแล้ว คุณควรตรวจสอบว่าเอกสารมีเนื้อหาที่มีความหมายหรือไม่ วิธีที่เร็วคือดึงข้อความธรรมดาและพิมพ์อักขระแรก ๆ

```python
# Extract plain text to verify recovery
text = document.get_text()
if text.strip():
    print("Recovered text preview (first 200 chars):")
    print(text[:200])
else:
    print("Document appears empty after recovery – further inspection may be needed.")
```

หากผลลัพธ์แสดงตัวอย่างที่สมเหตุสมผล คุณสามารถดำเนินการต่อกับเอกสาร (เช่น แปลงเป็น PDF, ดึงตาราง ฯลฯ) หากข้อความว่างเปล่า ไฟล์อาจอยู่เกินกว่าที่จะซ่อมได้และคุณอาจต้องขอสำเนาใหม่

## ขั้นตอนที่ 5: บันทึกเอกสารที่ซ่อมแล้ว (หากต้องการสำเนาที่สะอาด)

เมื่อคุณพอใจกับเนื้อหาที่กู้คืนแล้ว คุณสามารถบันทึก DOCX ใหม่ที่สะอาด ขั้นตอนนี้ไม่บังคับแต่มักเป็นประโยชน์สำหรับกระบวนการต่อไป

```python
repaired_path = "YOUR_DIRECTORY/repaired.docx"
document.save(repaired_path)
print(f"Repaired document saved to {repaired_path}")
```

การบันทึกจะสร้างไฟล์ใหม่ที่ไม่มีความเสียหายที่ทำให้โหมดการกู้คืนทำงานอีกต่อไป

## กรณีขอบและเคล็ดลับเพิ่มเติม

| สถานการณ์                               | แนวทางที่แนะนำ |
|----------------------------------------|----------------------|
| **ไฟล์ไม่ใช่ DOCX** (เช่น `.doc`) | ใช้ `aw.loading.LoadOptions.file_format = aw.LoadFormat.DOC` ก่อนทำการโหลด. |
| **กู้คืนบางส่วนเท่านั้น**              | หลังจากโหลด ให้ตรวจสอบ `document.get_text()` และ `document.get_page_count()` หากจำนวนหน้าเป็น 0 เอกสารอาจไม่สามารถกู้คืนได้. |
| **เอกสารขนาดใหญ่**                    | เปิดใช้งาน `load_options.memory_optimization = aw.loading.MemoryOptimizationMode.OPTIMIZE` เพื่อลดการใช้ RAM ระหว่างการกู้คืน. |
| **ต้องการบันทึกสิ่งที่ถูกซ่อม**      | ตั้งค่า `load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER` แล้วอ่าน `document.get_last_save_options().recovery_log` (หากมี) เพื่อดูรายละเอียด. |

> **ระวัง:** โหมดการกู้คืนอาจละทิ้งองค์ประกอบที่ไม่รองรับโดยไม่มีการแจ้ง (เช่น ฟอนต์ที่หายไป) หากความเที่ยงตรงของภาพสำคัญ ให้เปรียบเทียบไฟล์ที่ซ่อมแล้วกับเวอร์ชันที่รู้ว่าดี

## ตัวอย่างทำงานเต็มรูปแบบ

รวมทุกอย่างเข้าด้วยกัน นี่คือสคริปต์อิสระที่คุณสามารถรันได้ทันที:

```python
import aspose.words as aw

def open_corrupted_docx(path: str, output_path: str = None):
    """Load a corrupted DOCX with recovery mode and optionally save a repaired copy."""
    # 1. Configure load options
    load_options = aw.loading.LoadOptions()
    load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER

    # 2. Attempt to load the document
    try:
        doc = aw.Document(path, load_options)
        print("✅ Document loaded with recovery mode.")
    except aw.core.exceptions.InvalidOperationException as err:
        print(f"❌ Unable to recover document: {err}")
        return None

    # 3. Verify recovered content
    txt = doc.get_text()
    if txt.strip():
        print("📄 Text preview (first 200 chars):")
        print(txt[:200])
    else:
        print("⚠️ Document appears empty after recovery.")

    # 4. Save a clean copy if requested
    if output_path:
        doc.save(output_path)
        print(f"💾 Repaired file saved to {output_path}")

    return doc

if __name__ == "__main__":
    corrupted_file = "YOUR_DIRECTORY/corrupted.docx"
    repaired_file = "YOUR_DIRECTORY/repaired.docx"
    open_corrupted_docx(corrupted_file, repaired_file)
```

การรันสคริปต์จะแสดงข้อความสำเร็จ ข้อความสั้น ๆ ของข้อความ และสร้างไฟล์ `repaired.docx` ในโฟลเดอร์เดียวกัน

## สรุป

ตอนนี้คุณรู้วิธี **เปิดโหมดการกู้คืน** เพื่อ **เปิดไฟล์ word ที่เสียหาย** , **กู้คืนเนื้อหา docx ที่เสียหาย** และอย่างปลอดภัย **โหลดเอกสารพร้อมการกู้คืน** ด้วย Aspose.Words for Python ขั้นตอนหลัก—การสร้าง `LoadOptions` การเปิด `RecoveryMode.RECOVER` และการจัดการข้อยกเว้น—เป็นรูปแบบที่เชื่อถือได้ที่คุณสามารถนำกลับมาใช้ใหม่ในสายงานอัตโนมัติใด ๆ

ต่อไปให้พิจารณาศึกษาหัวข้อที่เกี่ยวข้อง เช่น **แปลงเอกสารที่กู้คืนเป็น PDF**, **ดึงตารางด้วย `DocumentVisitor`**, หรือ **ประมวลผลเป็นชุดของโฟลเดอร์ไฟล์ที่เสียหาย** ทั้งหมดนี้อิงจากพื้นฐานโหมดการกู้คืนเดียวกันที่แสดงในที่นี้

ขอให้เขียนโค้ดอย่างสนุกสนานและเอกสารของคุณคงอยู่ในสภาพดี!

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานครบถ้วนพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้ทางเลือกในโครงการของคุณ

- [วิธีกู้คืน docx – ตั้งค่าโหมดการกู้คืนและเปิดไฟล์ Word ที่เสียหาย](/words/english/net/programming-with-loadoptions/how-to-recover-docx-set-recovery-mode-open-corrupted-word-fi/)
- [กู้คืน docx ที่เสียหายด้วย Aspose.Words – ตั้งค่าโหมดการกู้คืนและตัวเลือกการโหลด](/words/english/net/programming-with-loadoptions/recover-damaged-docx-with-aspose-words-set-recovery-mode-and/)
- [กู้คืน DOCX ที่เสียหายด้วย Aspose.Words LoadOptions – คู่มือ C# ฉบับสมบูรณ์](/words/english/net/programming-with-loadoptions/recover-corrupted-docx-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}