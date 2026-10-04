---
category: general
date: 2026-10-04
description: เปิดใช้งานโหมดการกู้คืนใน Aspose.Words เพื่อกู้คืนเอกสาร Word ที่เสียหายอย่างปลอดภัย
  ปฏิบัติตามคำแนะนำแบบขั้นตอนโดยละเอียดพร้อมโค้ด Python เต็มรูปแบบและคำอธิบาย
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- enable recovery mode
- recover corrupted word document
- Aspose.Words load options
- document recovery Python
- handling damaged .docx files
language: th
lastmod: 2026-10-04
og_description: เปิดใช้งานโหมดการกู้คืนเพื่อกู้คืนเอกสาร Word ที่เสียหายด้วย Aspose.Words
  บทเรียนนี้จะแสดงโค้ด Python ที่แน่นอน เหตุผลที่ทำงานได้ และวิธีจัดการกับกรณีขอบเขต
og_image_alt: Screenshot of Python code loading a corrupted Word document with recovery
  mode enabled
og_title: เปิดใช้งานโหมดกู้คืนเพื่อกู้ไฟล์ Word ที่เสียหาย – คู่มือเต็ม
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Enable recovery mode in Aspose.Words to recover a corrupted Word document
    safely. Follow the step‑by‑step guide with full Python code and explanations.
  headline: Enable recovery mode to recover a corrupted Word document
  type: TechArticle
- description: Enable recovery mode in Aspose.Words to recover a corrupted Word document
    safely. Follow the step‑by‑step guide with full Python code and explanations.
  name: Enable recovery mode to recover a corrupted Word document
  steps:
  - name: Create `LoadOptions` and set `recovery_mode` to `RECOVER`.
    text: Create `LoadOptions` and set `recovery_mode` to `RECOVER`.
  - name: Load the `.docx` using those options.
    text: Load the `.docx` using those options.
  - name: Verify the mode and optionally save a repaired copy.
    text: Verify the mode and optionally save a repaired copy.
  type: HowTo
tags:
- Aspose.Words
- Python
- Document processing
- Error handling
title: เปิดใช้งานโหมดการกู้คืนเพื่อกู้คืนเอกสาร Word ที่เสียหาย
url: /th/python/document-options-and-settings/enable-recovery-mode-to-recover-a-corrupted-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# เปิดโหมดการกู้คืนเพื่อกู้คืนเอกสาร Word ที่เสียหาย

หากคุณต้องการ **เปิดโหมดการกู้คืน** ขณะโหลดไฟล์ Word คำแนะนำนี้จะแสดงให้คุณเห็นอย่างชัดเจนว่าจะทำอย่างไรด้วย Aspose.Words for Python โดยการเปิดโหมดการกู้คืนคุณสามารถ **กู้คืนเอกสาร Word ที่เสียหาย** ที่โดยปกติจะทำให้เกิดข้อยกเว้น

ในส่วนต่อไปนี้คุณจะได้เรียนรู้:

* คลาสและคุณสมบัติที่ควบคุมพฤติกรรมการกู้คืน  
* วิธีโหลดไฟล์ `.docx` ที่อาจเสียหายโดยไม่ทำให้แอปพลิเคชันของคุณหยุดทำงาน  
* เคล็ดลับการแก้ไขปัญหาการโหลดที่พบบ่อยและการปรับแต่งกลยุทธ์การกู้คืน

> **Prerequisite** – คุณได้ติดตั้ง Aspose.Words for Python (`pip install aspose-words`) และมีความเข้าใจพื้นฐานเกี่ยวกับการทำ I/O ของไฟล์ใน Python

## โหมดการกู้คืนทำอะไรและทำไมคุณควรเปิดใช้งาน

Aspose.Words จะทำการวิเคราะห์โครงสร้างภายในของไฟล์ Word ก่อนที่จะเปิดเผยเป็นอ็อบเจ็กต์ `Document` เมื่อไฟล์เสียหาย—ขาดส่วนบางส่วน, XML เสียหาย, หรือความสัมพันธ์ไม่ถูกต้อง—ตัวพาร์เซอร์สามารถทำได้สองอย่าง:

| โหมด | พฤติกรรม |
|------|------------|
| `STRICT` | โยนข้อยกเว้นทันทีเมื่อพบสัญญาณของความเสียหาย |
| `IGNORE_ERRORS` | ข้ามส่วนที่อ่านไม่ออกแต่อาจสูญเสียเนื้อหาโดยไม่แจ้ง |
| `RECOVER` (ตัวเลือก **enable recovery mode**) | พยายามสร้างเอกสารใหม่ใหม่โดยรักษาเนื้อหาที่ทำได้มากที่สุดและเปิดเผยโหมดที่เลือกผ่าน `load_options.recovery_mode` |

`RECOVER` เป็นตัวเลือกที่แนะนำเมื่อคุณต้อง **กู้คืนไฟล์เอกสาร Word ที่เสียหาย** เพื่อการประมวลผลต่อไป เช่น การสกัดข้อความหรือการแปลงเป็น PDF

## ขั้นตอนที่ 1: สร้าง LoadOptions และเปิดโหมดการกู้คืน

ขั้นตอนแรกคือการสร้างอ็อบเจ็กต์ `LoadOptions` และตั้งค่าคุณสมบัติ `recovery_mode` เป็น `RecoveryMode.RECOVER` ซึ่งบอกไลบรารีให้เข้าสู่เส้นทางการกู้คืนระหว่างการพาร์ส

```python
import aspose.words as aw

# Step 1: Create load options and enable recovery mode
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER  # alternatives: .IGNORE_ERRORS, .STRICT
```

**ทำไมจึงสำคัญ:**  
หากคุณข้ามขั้นตอนนี้และเอกสารถูกทำลาย ตัวสร้าง `aw.Document(...)` จะโยน `InvalidOperationException` การเปิดใช้งานโหมดการกู้คืนจะป้องกันการหยุดทำงานและให้คุณได้อ็อบเจ็กต์ `Document` ที่ซ่อมแซมบางส่วนซึ่งยังคงใช้งานได้

## ขั้นตอนที่ 2: โหลดเอกสารที่อาจเสียหายโดยใช้ตัวเลือกที่กำหนด

ส่งอ็อบเจ็กต์ `load_options` ไปยังคอนสตรัคเตอร์ของ `Document` ตัวโหลดจะนำอัลกอริทึมการกู้คืนไปใช้โดยอัตโนมัติ

```python
# Step 2: Load the potentially corrupted document using the specified options
doc_path = "YOUR_DIRECTORY/Corrupted.docx"
doc = aw.Document(doc_path, load_options)
```

**เคล็ดลับ:** แทนที่ `YOUR_DIRECTORY` ด้วยพาธแบบสัมบูรณ์หรือสัมพัทธ์ที่ runtime ของคุณสามารถเข้าถึงได้ หากไฟล์ไม่พบ Aspose.Words จะโยน `FileNotFoundError` ก่อนที่โลจิกการกู้คืนจะทำงาน

## ขั้นตอนที่ 3: ตรวจสอบว่าโหมดการกู้คืนได้ถูกนำไปใช้แล้ว

คุณสามารถยืนยันโหมดที่ทำงานอยู่โดยตรวจสอบ `load_options.recovery_mode` ซึ่งเป็นประโยชน์สำหรับการบันทึกล็อกหรือการจัดการเงื่อนไขในขั้นตอนต่อไปของ pipeline

```python
# Step 3: Confirm that the document was loaded with the chosen recovery mode
print("Document loaded with recovery mode:", load_options.recovery_mode)
```

**ผลลัพธ์ที่คาดหวัง**

```
Document loaded with recovery mode: RecoveryMode.RECOVER
```

หากผลลัพธ์แสดง `RECOVER` คุณได้ **เปิดโหมดการกู้คืน** สำเร็จและเอกสารพร้อมสำหรับการประมวลผลต่อ (เช่น การสกัดข้อความ, การแปลงเป็น PDF, หรือการบันทึกสำเนาที่ซ่อมแซมแล้ว)

## ขั้นตอนที่ 4 (ทางเลือก): บันทึกสำเนาที่ซ่อมแซมเพื่อใช้ในอนาคต

หลังจากโหลดแล้ว คุณอาจต้องการบันทึกเอกสารที่กู้คืนเพื่อไม่ต้องทำขั้นตอนการกู้คืนซ้ำ

```python
# Optional: Save the repaired document
repaired_path = "YOUR_DIRECTORY/Corrupted_Repaired.docx"
doc.save(repaired_path)
print(f"Repaired document saved to {repaired_path}")
```

การบันทึกจะสร้างไฟล์ `.docx` ใหม่ที่ Aspose.Words พิจารณาว่าเป็นไฟล์ที่ถูกต้อง ซึ่งสามารถเปิดใน Microsoft Word ได้โดยไม่มีคำเตือน

## คำถามที่พบบ่อยและการจัดการกรณีขอบ

| คำถาม | คำตอบ |
|----------|--------|
| **ถ้าเอกสารอ่านไม่ได้เลยจะทำอย่างไร?** | แม้ในโหมด `RECOVER` บางไฟล์ก็อาจอยู่เกินกว่าจะซ่อมได้ `Document` จะถูกสร้างขึ้นแต่อาจมีเพียงหน้าเปล่าเดียว ตรวจสอบด้วย `doc.get_page_count()` เพื่อยืนยันเนื้อหา |
| **ฉันสามารถสลับไปใช้ `IGNORE_ERRORS` หลังจากโหลดได้หรือไม่?** | ไม่ได้ โหมดการกู้คืนต้องตั้ง **ก่อน** ที่คอนสตรัคเตอร์ `Document` ทำงาน หากต้องการกลยุทธ์อื่นให้สร้าง `LoadOptions` ใหม่ |
| **โหมดการกู้คืนส่งผลต่อประสิทธิภาพหรือไม่?** | มีผลเพิ่มค่าโอเวอร์เฮดเล็กน้อยเนื่องจากไลบรารีพยายามสร้างส่วนที่เสียหายใหม่ ผลกระทบมักไม่สำคัญสำหรับไฟล์ส่วนใหญ่ (< 2 MB) |
| **วิธีนี้เป็นภาษาที่ไม่ขึ้นกับภาษาใช่หรือไม่?** | แนวคิดเดียวกันมีใน .NET, Java, และ Node.js APIs (`LoadOptions.RecoveryMode`) โค้ดอาจแตกต่างกันแต่ตรรกะเหมือนกัน |

## เคล็ดลับระดับมืออาชีพ: บันทึกข้อมูลการกู้คืนอย่างละเอียด

Aspose.Words มี `LoadOptions.recovery_callback` ที่รับข้อความรายละเอียดเกี่ยวกับแต่ละขั้นตอนการกู้คืน การเชื่อมต่อ callback นี้จะช่วยให้คุณวินิจฉัยสาเหตุที่เอกสารบางไฟล์ล้มเหลวได้

```python
def recovery_logger(message):
    print("[Recovery] ", message)

load_options.recovery_callback = recovery_logger
```

ตอนนี้การแก้ไขภายในทุกขั้นตอน (เช่น “Removed duplicate relationship”) จะถูกพิมพ์ออกที่คอนโซล

## ตัวอย่างเต็มที่สามารถรันได้

รวมทุกส่วนเข้าด้วยกัน นี่คือสคริปต์ที่พร้อมคัดลอก‑วางและรันทันที:

```python
import aspose.words as aw

def enable_recovery_and_load(doc_path: str, save_repaired: bool = False):
    # Create load options and enable recovery mode
    load_options = aw.loading.LoadOptions()
    load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER

    # Optional: attach a simple logger
    load_options.recovery_callback = lambda msg: print("[Recovery] ", msg)

    # Load the document with recovery enabled
    doc = aw.Document(doc_path, load_options)

    # Verify the mode
    print("Document loaded with recovery mode:", load_options.recovery_mode)

    # Show basic info
    print("Page count:", doc.page_count)
    print("Word count:", doc.get_text().split())

    # Optionally save a repaired copy
    if save_repaired:
        repaired_path = doc_path.replace(".docx", "_repaired.docx")
        doc.save(repaired_path)
        print(f"Repaired document saved to {repaired_path}")

    return doc

if __name__ == "__main__":
    corrupted_path = "YOUR_DIRECTORY/Corrupted.docx"
    enable_recovery_and_load(corrupted_path, save_repaired=True)
```

การรันสคริปต์จะพิมพ์โหมดการกู้คืน, จำนวนหน้า, และรายการคำที่สกัดจากเอกสารที่ซ่อมแซม หากตั้งค่า `save_repaired=True` จะมีไฟล์สะอาดใหม่ปรากฏเคียงกับไฟล์ต้นฉบับ

## สรุป

คุณได้เรียนรู้วิธี **เปิดโหมดการกู้คืน** ใน Aspose.Words for Python และสามารถ **กู้คืนไฟล์เอกสาร Word ที่เสียหาย** ได้อย่างมั่นใจ ขั้นตอนสำคัญคือ:

1. สร้าง `LoadOptions` และตั้งค่า `recovery_mode` เป็น `RECOVER`  
2. โหลดไฟล์ `.docx` ด้วยตัวเลือกเหล่านั้น  
3. ตรวจสอบโหมดและบันทึกสำเนาที่ซ่อมแซมตามต้องการ  

จากนี้คุณสามารถสำรวจหัวข้อเพิ่มเติม เช่น **การสกัดข้อความจากเอกสารที่กู้คืน**, **การแปลงเป็น PDF**, หรือ **การทำการกู้คืนแบบแบตช์สำหรับห้องสมุดเอกสารขนาดใหญ่**  

---


## คุณควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมโค้ดตัวอย่างทำงานครบถ้วนพร้อมคำอธิบายทีละขั้นตอน เพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการนำไปใช้ในโครงการของคุณเอง

- [กู้คืน DOCX ที่เสียหาย – คู่มือฉบับสมบูรณ์เพื่อเปิดโหมดการกู้คืนและรับจำนวนหน้า](/words/english/python-net/document-operations/recover-corrupted-docx-complete-guide-to-enable-recovery-mod/)
- [กู้คืน DOCX ที่เสียหาย – เปิดและโหลดเอกสาร Word](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)
- [กู้คืน docx ที่เสียหายด้วย Aspose.Words – ตั้งค่าโหมดการกู้คืนและ LoadOptions](/words/english/net/programming-with-loadoptions/recover-damaged-docx-with-aspose-words-set-recovery-mode-and/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}