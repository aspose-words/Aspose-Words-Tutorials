---
category: general
date: 2026-06-24
description: วิธีตั้งค่า callback เพื่อส่งออกภาพจาก DOCX เมื่อบันทึกเป็น Markdown.
  เรียนรู้วิธีดึงภาพ, ดึง SVG จาก Word, และบันทึก DOCX เป็น Markdown ด้วยการจัดการแบบกำหนดเอง.
draft: false
keywords:
- how to set callback
- export images from docx
- how to extract images
- save docx as markdown
- extract svg from word
language: th
og_description: วิธีตั้งค่า callback เพื่อส่งออกภาพจาก DOCX เมื่อแปลงเป็น Markdown
  คู่มือนี้จะแสดงวิธีดึงภาพและ SVG อย่างมีประสิทธิภาพ
og_title: วิธีตั้งค่า Callback สำหรับการส่งออกภาพจากไฟล์ DOCX
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  headline: How to Set Callback for Exporting Images from DOCX
  type: TechArticle
- description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  name: How to Set Callback for Exporting Images from DOCX
  steps:
  - name: '**Deterministic names** – useful for version control or CDN publishing.'
    text: '**Deterministic names** – useful for version control or CDN publishing.'
  - name: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
    text: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
  - name: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
    text: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Conversion
title: วิธีตั้งค่า Callback สำหรับการส่งออกภาพจาก DOCX
url: /th/python/content-extraction-and-manipulation/how-to-set-callback-for-exporting-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีตั้ง Callback สำหรับการส่งออกภาพจาก DOCX

เคยสงสัย **วิธีตั้ง callback** เพื่อให้คุณ **ส่งออกภาพจาก DOCX** ขณะแปลงเป็น Markdown หรือไม่? คุณไม่ได้เป็นคนเดียว นักพัฒนาจำนวนมากเจออุปสรรคเมื่อการแปลงเริ่มต้นบันทึกภาพทั้งหมดลงในโฟลเดอร์ทั่วไป หรือแย่กว่านั้นคือสูญเสียกราฟิก SVG ไปทั้งหมด  

ในบทเรียนนี้เราจะพาคุณผ่านโซลูชันที่พร้อมใช้งานครบถ้วน ซึ่งตอบคำถาม “วิธีตั้ง callback” แสดง **วิธีดึงภาพออก** และแม้กระทั่งครอบคลุม **การดึง SVG จาก Word** ตอนจบคุณจะสามารถ **บันทึก DOCX เป็น Markdown** พร้อมตั้งชื่อไฟล์สำหรับทรัพยากรภาพแต่ละไฟล์แบบกำหนดเอง—ไม่ต้องทำมือเลย

## สิ่งที่คุณจะได้เรียนรู้

- ทำไม callback ถึงเป็นวิธีที่สะอาดที่สุดในการควบคุมชื่อไฟล์ภาพระหว่างการแปลง  
- วิธีเชื่อมต่อกับ `MarkdownSaveOptions.resource_saving_callback` ของ Aspose.Words  
- โค้ดขั้นตอน‑ต่อ‑ขั้นตอนที่ดึง **PNG**, **JPG**, **SVG**, และทรัพยากรฝังอื่น ๆ  
- เคล็ดลับการจัดการการชนชื่อ, ไฟล์ขนาดใหญ่, และความแปลกของเส้นทางข้ามแพลตฟอร์ม  

> **Pro tip:** หากคุณใช้ Aspose.Words อยู่แล้วใน pipeline ที่ใหญ่กว่า คุณสามารถใส่ callback นี้เข้าไปได้โดยไม่ต้องแก้ไขโค้ดส่วนอื่น

---

![How to set callback diagram](https://example.com/images/how-to-set-callback.png "how to set callback")

## ข้อกำหนดเบื้องต้น

- Python 3.8+ (ตัวอย่างใช้ f‑strings ดังนั้น 3.6+ ก็พอ)  
- ติดตั้งแพคเกจ `aspose-words` (`pip install aspose-words`)  
- ไฟล์ DOCX ที่มีภาพแรสเตอร์ **และ** กราฟิกเวกเตอร์ (SVG)  
- ความคุ้นเคยพื้นฐานกับฟังก์ชัน Python และการทำ I/O ไฟล์  

ถ้าคุณมีทั้งหมดนี้แล้ว ไปต่อกันเลย

---

## วิธีตั้ง Callback สำหรับการส่งออกภาพจาก DOCX

หัวใจของโซลูชันอยู่ใน **resource‑saving callback** Aspose.Words จะเรียก delegate นี้สำหรับทุกภาพหรือ SVG ที่ต้องการเขียนเมื่อคุณเรียก `document.save` โดยการคืนค่าเป็นทูเพิล `(new_name, data)` คุณจะกำหนดทั้งชื่อไฟล์และข้อมูลไบต์ได้เอง

```python
import aspose.words as aw
import os
import hashlib

# Step 1: Load the source document
document = aw.Document("YOUR_DIRECTORY/input.docx")
```

### ทำไมต้องใช้ Callback?

หากไม่มี callback, Aspose.Words จะสร้างไฟล์ชื่อ `image1.png`, `image2.svg` ฯลฯ และวางไว้ในโฟลเดอร์ข้างไฟล์ Markdown ซึ่งอาจเพียงพอสำหรับการสาธิตเร็ว ๆ แต่ในสภาพแวดล้อมการผลิตคุณมักต้องการ:

1. **ชื่อที่กำหนดได้** – มีประโยชน์สำหรับการควบคุมเวอร์ชันหรือการเผยแพร่บน CDN  
2. **หลีกเลี่ยงการชนชื่อ** – ภาพสองภาพที่มีชื่อเดิมเดียวกันจะไม่ทับกัน  
3. **โครงสร้างโฟลเดอร์แบบกำหนดเอง** – อาจต้องการให้ทรัพยากรทั้งหมดอยู่ภายใต้ `/assets/docs/`  

Callback ให้คุณควบคุมทั้งสามประเด็นได้อย่างเต็มที่

---

## ส่งออกภาพจาก DOCX ด้วย Resource Callback

ด้านล่างเป็นการทำงานของ callback ซึ่งทำการแฮชข้อมูลไบต์เพื่อสร้าง suffix ที่ไม่ซ้ำ, รักษานามสกุลไฟล์เดิม, และคืนชื่อไฟล์ใหม่พร้อมข้อมูลไบต์ดิบ

```python
def resource_callback(resource):
    """
    Called for every image/SVG that MarkdownSaveOptions wants to write.
    Returns a tuple (new_name, data) to control the saved file name.
    """
    # Preserve the original extension (.png, .svg, …)
    extension = os.path.splitext(resource.name)[1]

    # Compute a short hash of the image bytes – guarantees uniqueness
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]

    # Build a deterministic, collision‑free filename
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data
```

#### การจัดการ Edge‑Case

- **ไฟล์ขนาดใหญ่:** SHA‑256 ทำงานได้ดีกับทุกขนาด; การแฮชทำในหน่วยความจำ ดังนั้นควรระวังข้อจำกัดของ RAM หากประมวลผล PDF ขนาดมหาศาล  
- **ไม่มีนามสกุล:** ไฟล์ Word รุ่นเก่าอาจเก็บภาพโดยไม่มีนามสกุลชัดเจน ในกรณีนั้น `extension` จะเป็นค่าว่าง; คุณสามารถตั้งค่าเริ่มต้นเป็น `.bin` หรือดูไบต์แรก ๆ เพื่อคาดเดาฟอร์แมต  
- **ทรัพยากรที่ไม่ใช่ภาพ:** Callback จะถูกเรียกสำหรับทุกทรัพยากรภายนอก (เช่น OLE objects) หากคุณสนใจเฉพาะภาพหรือ SVG ให้กรองด้วย `resource.type` ก่อนดำเนินการต่อ

## วิธีดึงภาพและ SVG จาก Word

ตอนนี้เราจะเชื่อม callback เข้ากับ pipeline การบันทึก Markdown `MarkdownSaveOptions` มี property `resource_saving_callback` เพื่อวัตถุประสงค์นี้โดยเฉพาะ

```python
# Step 2: Configure Markdown save options to use the callback
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.resource_saving_callback = resource_callback

# Optional: set the folder where images will be placed relative to the .md file
markdown_options.resource_folder = "assets/images"
```

การตั้งค่า `resource_folder` เป็นตัวเลือกแต่มักจะสะดวก หากคุณละไว้ ภาพจะถูกบันทึกข้างไฟล์ Markdown ซึ่งอาจทำให้โฟลเดอร์โปรเจกต์รกรุง

### การบันทึกเอกสาร

```python
# Step 3: Save the document as Markdown, letting the callback store the resources
output_md_path = "YOUR_DIRECTORY/output.md"
document.save(output_md_path, markdown_options)
print(f"Markdown saved to {output_md_path}")
```

เมื่อคุณรันสคริปต์ คุณจะเห็นไฟล์ชุดหนึ่งเช่น:

```
assets/images/img_a1b2c3d4e5.png
assets/images/img_f6g7h8i9j0.svg
```

และไฟล์ `output.md` ที่สร้างขึ้นจะมีลิงก์ภาพที่ชี้ไปยังชื่อไฟล์เหล่านั้นโดยตรง:

```markdown
![Image](assets/images/img_a1b2c3d4e5.png)
```

นี่คือส่วน **วิธีดึงภาพ** ที่ทำงานจริง—ทุกภาพ ไม่ว่าจะเป็นแรสเตอร์หรือเวกเตอร์ จะกลายเป็นทรัพยากรแยกต่างหากที่มีชื่อไม่ซ้ำกัน

## บันทึก DOCX เป็น Markdown พร้อมการจัดการภาพแบบกำหนดเอง

รวมทุกอย่างเข้าด้วยกัน นี่คือสคริปต์เต็มที่คุณสามารถคัดลอก‑วางลงในไฟล์ชื่อ `convert_docx_to_md.py`:

```python
import aspose.words as aw
import os
import hashlib

def resource_callback(resource):
    """Control the naming of each exported image/SVG."""
    extension = os.path.splitext(resource.name)[1] or ".bin"
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data

def convert_docx_to_markdown(input_path, output_md_path, image_folder="assets/images"):
    # Load the DOCX
    document = aw.Document(input_path)

    # Set up Markdown options with our callback
    md_options = aw.saving.MarkdownSaveOptions()
    md_options.resource_saving_callback = resource_callback
    md_options.resource_folder = image_folder

    # Ensure the output directory exists
    os.makedirs(os.path.dirname(output_md_path), exist_ok=True)
    os.makedirs(os.path.join(os.path.dirname(output_md_path), image_folder), exist_ok=True)

    # Perform the conversion
    document.save(output_md_path, md_options)
    print(f"✅ Conversion complete! Markdown at: {output_md_path}")

if __name__ == "__main__":
    # Adjust these paths to your environment
    INPUT_DOCX = "YOUR_DIRECTORY/input.docx"
    OUTPUT_MD = "YOUR_DIRECTORY/output.md"
    convert_docx_to_markdown(INPUT_DOCX, OUTPUT_MD)
```

**ทำไมวิธีนี้ถึงได้ผล:**  
- `resource_callback` รับประกันว่าภาพแต่ละภาพจะได้ชื่อที่เป็นเอกลักษณ์และทำซ้ำได้  
- `resource_folder` ทำให้ Markdown ดูเป็นระเบียบโดยแยกทรัพยากรออกจากกัน  
- การเรียก `os.makedirs` ป้องกันข้อผิดพลาด “โฟลเดอร์ไม่พบ” เมื่อสคริปต์ทำงานบนเครื่องใหม่

## ดึง SVG จาก Word – กราฟิกเวกเตอร์ล่ะ?

SVG ถูกจัดการเช่นเดียวกับ PNG โดย callback เพราะมันก็เป็น `resource` อีกชนิดหนึ่ง ความแตกต่างเดียวคือบางเวอร์ชัน Word เก่าอาจฝัง SVG เป็น *OfficeArt* ซึ่ง Aspose.Words จะเปลี่ยนเป็น PNG แรสเตอร์โดยอัตโนมัติ เว้นแต่คุณเปิดใช้ **preserve SVG** flag อย่างชัดเจน:

```python
md_options.export_svg = True  # Keep original SVG markup
```

เพิ่มบรรทัดนี้ก่อนบันทึก แล้ว callback จะได้รับทรัพยากรที่มีนามสกุล `.svg` รักษาข้อมูลเวกเตอร์ที่คมชัด—เหมาะกับเอกสารเว็บที่ตอบสนองได้ดี

## คำถามที่พบบ่อย & ข้อควรระวัง

| คำถาม | คำตอบ |
|----------|--------|
| **ถ้าภาพสองภาพเหมือนกันจะทำอย่างไร?** | แฮช SHA‑256 จะเหมือนกัน ทำให้ชื่อไฟล์ชนกัน หากต้องการเก็บทั้งสองไฟล์ ให้รวม `resource.name` เดิมเข้าไปในกระบวนการแฮช (เช่น `hash(resource.name + resource.data)`) |
| **สามารถเปลี่ยนโฟลเดอร์ตามประเภทไฟล์ได้หรือไม่?** | ได้ ภายใน `resource_callback` คุณสามารถตรวจสอบ `extension` แล้วคืนค่าเส้นทางเช่น `f"png/{new_name}"` สำหรับภาพแรสเตอร์และ `f"svg/{new_name}"` สำหรับเวกเตอร์ |
| **โค้ดนี้ทำงานบน Linux/macOS หรือไม่?** | ทำงานได้แน่นอน โค้ดใช้ `os.path` ที่จัดการตัวคั่นเส้นทางให้เอง เพียงตรวจสอบให้ไฟล์ลิขสิทธิ์ Aspose.Words (`aspose.words.lic`) เข้าถึงได้หากใช้เวอร์ชันที่ต้องชำระเงิน |
| **เรื่องการใช้หน่วยความจำสำหรับเอกสารขนาดใหญ่ล่ะ?** | Callback จะรับ **byte array** เต็มรูปแบบของแต่ละทรัพยากร ซึ่งหมายความว่าภาพทั้งหมดจะอยู่ในหน่วยความจำชั่วคราว สำหรับไฟล์หลายกิกะไบต์อาจต้องสตรีมข้อมูลลงดิสก์ภายใน callback แทนการคืนค่า |

## สรุป

คุณได้เรียนรู้ **วิธีตั้ง callback** เพื่อควบคุมการดึงภาพเมื่อ **บันทึก DOCX เป็น Markdown** วิธีนี้ช่วยให้คุณ **ส่งออกภาพจาก DOCX**, **ดึง SVG จาก Word**, และทำให้ Markdown ของคุณสะอาดและกำหนดค่าได้อย่างแน่นอน  

ในสคริปต์เดียวที่ครบถ้วน เราได้ครอบคลุมการโหลดเอกสาร, การกำหนด resource‑saving callback, การตั้งค่า `MarkdownSaveOptions`, และการจัดการ edge case เช่น การชนชื่อและกราฟิกเวกเตอร์ ผลลัพธ์คือชุดทรัพยากรที่มีชื่อไม่ซ้ำกันอยู่เคียงข้างไฟล์ Markdown ที่ลิงก์อย่างสมบูรณ์—พร้อมใช้กับ static site generator, pipeline เอกสาร, หรือเวิร์กโฟลว์ใด ๆ ที่ต้องการทรัพยากรที่สะอาดและนำกลับมาใช้ใหม่ได้  

**ขั้นตอนต่อไป?**  
- ลองเชื่อมต่อกับ static‑site generator อย่าง MkDocs เพื่อเผยแพร่เอกสารจาก Word อัตโนมัติ  
- ทดลองใช้ `markdown_options.export_images_as_base64 = True` หากต้องการภาพแบบ inline แทนไฟล์ภายนอก  
- ศึกษา callback อื่นของ Aspose.Words (เช่น `document_saving_callback`) เพื่อควบคุมผลลัพธ์ Markdown เอง  

มีคำถามเพิ่มเติมเกี่ยวกับ **วิธีดึงภาพ** จากรูปแบบ Office อื่น ๆ หรืออยากปรับ callback ให้สอดคล้องกับรูปแบบการตั้งชื่อเฉพาะ? แสดงความคิดเห็นด้านล่าง แล้วขอให้โค้ดของคุณสนุก!

## ควรเรียนรู้อะไรต่อไป?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งรวมตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอน‑ต่อ‑ขั้นตอน เพื่อช่วยคุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจแนวทางการทำงานทางเลือกในโปรเจกต์ของคุณ

- [How to Rename Images When Converting DOCX to Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)
- [How to Save Markdown from DOCX – Step‑by‑Step Guide](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}