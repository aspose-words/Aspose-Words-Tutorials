---
"date": "2025-03-29"
"description": "เรียนรู้วิธีเพิ่มประสิทธิภาพการบันทึกเอกสารด้วย Aspose.Words สำหรับ Python โดยใช้รูปแบบกระแสข้อมูล XAML และคอลแบ็กความคืบหน้า เพิ่มประสิทธิภาพในการจัดการเอกสาร"
"title": "การเพิ่มประสิทธิภาพการบันทึกเอกสารใน Python โดยใช้ Aspose.Words XAML Flow และ Progress Callbacks"
"url": "/th/python-net/performance-optimization/python-aspose-words-xaml-flow-progress-callbacks/"
"weight": 1
---
{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}
# วิธีเพิ่มประสิทธิภาพการบันทึกเอกสารใน Python โดยใช้ Aspose.Words: XAML Flow และ Progress Callbacks

## การแนะนำ

คุณกำลังมองหาวิธีจัดการการแปลงเอกสารอย่างมีประสิทธิภาพโดยใช้ Python หรือไม่? ประสบปัญหาในการจัดการรูปภาพและติดตามความคืบหน้าระหว่างการบันทึกเอกสารหรือไม่? บทช่วยสอนนี้จะแนะนำคุณตลอดกระบวนการเพิ่มประสิทธิภาพการบันทึกเอกสารด้วย Aspose.Words สำหรับ Python โดยเน้นที่คุณลักษณะอันทรงพลังสองประการ: `XamlFlowSaveOptions` พร้อมด้วยโฟลเดอร์รูปภาพและการโทรกลับความคืบหน้าการบันทึกเอกสาร

คู่มือที่ครอบคลุมนี้เหมาะอย่างยิ่งสำหรับนักพัฒนาที่ต้องการปรับปรุงเวิร์กโฟลว์การประมวลผลเอกสารของตนโดยใช้ไลบรารี Aspose.Words

**สิ่งที่คุณจะได้เรียนรู้:**
- วิธีบันทึกเอกสารในรูปแบบกระแสข้อมูล XAML ขณะจัดการทรัพยากรรูปภาพ
- การนำการเรียกกลับความคืบหน้ามาใช้ในระหว่างการบันทึกเอกสารเพื่อป้องกันการดำเนินการที่ยาวนาน
- การตั้งค่าและกำหนดค่า Aspose.Words สำหรับ Python ในสภาพแวดล้อมการพัฒนาของคุณ
- การประยุกต์ใช้งานจริงของคุณลักษณะเหล่านี้ในระบบการจัดการเอกสาร

มาเจาะลึกข้อกำหนดเบื้องต้นก่อนที่เราจะเริ่มเขียนโค้ดกัน!

## ข้อกำหนดเบื้องต้น

ก่อนที่คุณจะเริ่มต้น ให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:

### ไลบรารีและเวอร์ชันที่จำเป็น
- **Aspose.Words สำหรับ Python**: ให้แน่ใจว่าคุณมีเวอร์ชัน 23.3 ขึ้นไป
- **งูหลาม**:แนะนำเวอร์ชัน 3.6 ขึ้นไป

### ข้อกำหนดการตั้งค่าสภาพแวดล้อม
- โปรแกรมแก้ไขโค้ด เช่น VSCode หรือ PyCharm
- ความรู้พื้นฐานเกี่ยวกับการเขียนโปรแกรม Python

### ข้อกำหนดเบื้องต้นของความรู้
- ความคุ้นเคยกับแนวคิดการประมวลผลเอกสาร
- ความเข้าใจเกี่ยวกับการจัดการไฟล์และการจัดการไดเร็กทอรีใน Python

## การตั้งค่า Aspose.Words สำหรับ Python

หากต้องการเริ่มใช้ Aspose.Words คุณต้องติดตั้งผ่าน pip เปิดเทอร์มินัลหรือพรอมต์คำสั่งแล้วรัน:

```bash
pip install aspose-words
```

### ขั้นตอนการรับใบอนุญาต
1. **ทดลองใช้งานฟรี**: การเข้าถึงใบอนุญาตชั่วคราว [ที่นี่](https://purchase.aspose.com/temporary-license/) เพื่อวัตถุประสงค์ในการทดสอบ
2. **ซื้อ**:สำหรับการใช้งานระยะยาว ควรซื้อใบอนุญาต [ที่นี่](https://purchase-aspose.com/buy).
3. **การเริ่มต้นและการตั้งค่าเบื้องต้น**-
   - โหลดเอกสารของคุณโดยใช้ `aw-Document()`.
   - กำหนดค่าตัวเลือกการบันทึกตามต้องการ

## คู่มือการใช้งาน

ในส่วนนี้จะแนะนำคุณเกี่ยวกับการใช้งานฟีเจอร์หลักสองประการของบทช่วยสอนนี้ ได้แก่ XamlFlowSaveOptions พร้อมด้วยโฟลเดอร์รูปภาพ และการเรียกกลับความคืบหน้าในการบันทึกเอกสาร

### คุณสมบัติ 1: XamlFlowSaveOptions พร้อมโฟลเดอร์รูปภาพ

#### ภาพรวม
ฟีเจอร์นี้ช่วยให้คุณบันทึกเอกสารในรูปแบบโฟลว์ XAML พร้อมระบุโฟลเดอร์รูปภาพและนามแฝง เหมาะอย่างยิ่งสำหรับการจัดการเอกสารขนาดใหญ่ที่มีรูปภาพฝังไว้อย่างมีประสิทธิภาพ

#### ขั้นตอนการดำเนินการ

##### ขั้นตอนที่ 1: นำเข้าไลบรารีที่จำเป็น
```python
import os
from datetime import datetime
import aspose.words as aw
```

##### ขั้นตอนที่ 2: กำหนดคลาสการเรียกกลับ ImageUriPrinter
คลาสนี้จะนับและเปลี่ยนเส้นทางสตรีมรูปภาพไปยังโฟลเดอร์นามแฝงที่ระบุในระหว่างการแปลง

```python
class ExXamlFlowSaveOptionsImageFolder:
    class ImageUriPrinter(aw.saving.IImageSavingCallback):
        """Counts and prints filenames of images while their parent document is converted to flow-form .xaml."""
        
        def __init__(self, images_folder_alias: str):
            self.images_folder_alias = images_folder_alias
            self.resources = []  # ประเภท: รายการ[str]

        def image_saving(self, args: aw.saving.ImageSavingArgs):
            self.resources.append(args.image_file_name)
            with open(f"{self.images_folder_alias}/{args.image_file_name}", "wb") as image_stream:
                args.image_stream = image_stream
            args.keep_image_stream_open = False

    def test_image_folder(self):
        YOUR_DOCUMENT_DIRECTORY = 'YOUR_DOCUMENT_DIRECTORY'
        YOUR_OUTPUT_DIRECTORY = 'YOUR_OUTPUT_DIRECTORY'

        doc = aw.Document(f"{YOUR_DOCUMENT_DIRECTORY}/Rendering.docx")
        callback = self.ImageUriPrinter(YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolderAlias")

        options = aw.saving.XamlFlowSaveOptions()
        options.images_folder = YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolder"
        options.images_folder_alias = YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolderAlias"
        options.image_saving_callback = callback

        os.makedirs(options.images_folder_alias, exist_ok=True)
        
        doc.save(f"{YOUR_OUTPUT_DIRECTORY}/XamlFlowSaveOptions.image_folder.xaml", options)

        for resource in callback.resources:
            print(f"{callback.images_folder_alias}/{resource}")
```
**ตัวเลือกการกำหนดค่าคีย์:**
- `images_folder`: ระบุไดเร็กทอรีที่บันทึกรูปภาพ
- `images_folder_alias`: กำหนดเส้นทางนามแฝงที่ใช้ในระหว่างการแปลงเอกสาร

##### เคล็ดลับการแก้ไขปัญหา
- ตรวจสอบให้แน่ใจว่ามีไดเร็กทอรีทั้งหมดอยู่ก่อนที่จะรันโค้ดเพื่อหลีกเลี่ยงข้อผิดพลาดไม่พบไฟล์
- ตรวจสอบสิทธิ์การเขียนในไดเร็กทอรีเอาต์พุตของคุณ

### คุณสมบัติ 2: การบันทึกเอกสารเพื่อเรียกกลับความคืบหน้า

#### ภาพรวม
ฟีเจอร์นี้จัดการกระบวนการบันทึกโดยใช้การโทรกลับความคืบหน้า ทำให้คุณสามารถยกเลิกการดำเนินการบันทึกระยะยาวได้

#### ขั้นตอนการดำเนินการ

##### ขั้นตอนที่ 1: กำหนดคลาส SavingProgressCallback
ชั้นเรียนจะตรวจสอบระยะเวลาการบันทึกเอกสาร และยกเลิกหากเกินขีดจำกัดเวลาที่ระบุ

```python
class ExXamlFlowSaveOptionsProgressCallback:
    class SavingProgressCallback(aw.saving.IDocumentSavingCallback):
        """Saving progress callback. Cancel document saving after the 'max_duration' seconds."""
        
        def __init__(self):
            self.saving_started_at = datetime.now()
            self.max_duration = 0.01  # ระยะเวลาสูงสุดที่อนุญาตเป็นวินาที

        def notify(self, args: aw.saving.DocumentSavingArgs):
            canceled_at = datetime.now()
            elapsed_seconds = (canceled_at - self.saving_started_at).total_seconds()
            if elapsed_seconds > self.max_duration:
                raise OperationCanceledException(f"estimated_progress = {args.estimated_progress}; canceled_at = {canceled_at}")

    def test_progress_callback(self):
        YOUR_DOCUMENT_DIRECTORY = 'YOUR_DOCUMENT_DIRECTORY'
        YOUR_OUTPUT_DIRECTORY = 'YOUR_OUTPUT_DIRECTORY'

        parameters = [
            (aw.SaveFormat.XAML_FLOW, "xamlflow"),
            (aw.SaveFormat.XAML_FLOW_PACK, "xamlflowpack"),
        ]

        for save_format, ext in parameters:
            doc = aw.Document(f"{YOUR_DOCUMENT_DIRECTORY}/Big document.docx")
            save_options = aw.saving.XamlFlowSaveOptions(save_format)
            save_options.progress_callback = self.SavingProgressCallback()

            try:
                doc.save(f"{YOUR_OUTPUT_DIRECTORY}/XamlFlowSaveOptions.progress_callback.{ext}", save_options)
            except OperationCanceledException as e:
                print(e)
```
**ตัวเลือกการกำหนดค่าคีย์:**
- `save_format`: เลือกระหว่าง XAML_FLOW และ XAML_FLOW_PACK
- `progress_callback`:ตรวจสอบความคืบหน้าการบันทึกเพื่อจัดการกับการดำเนินงานระยะยาว

##### เคล็ดลับการแก้ไขปัญหา
- ปรับ `max_duration` ตามขนาดและความซับซ้อนของเอกสาร
- จัดการข้อยกเว้นอย่างเหมาะสมเพื่อให้มีข้อความแสดงข้อผิดพลาดที่ให้ข้อมูล

## การประยุกต์ใช้งานจริง

ต่อไปนี้คือกรณีการใช้งานจริงสำหรับฟีเจอร์เหล่านี้:
1. **ระบบจัดการเอกสาร**:จัดการเอกสารขนาดใหญ่ที่มีรูปภาพฝังอย่างมีประสิทธิภาพ โดยระบุโฟลเดอร์รูปภาพ ช่วยเพิ่มประสิทธิภาพการทำงานและการจัดระเบียบ
2. **เครื่องมือสร้างรายงานอัตโนมัติ**:ใช้การโทรกลับความคืบหน้าเพื่อให้แน่ใจว่ารายงานสร้างขึ้นภายในกรอบเวลาที่ยอมรับได้ เพื่อปรับปรุงประสบการณ์ของผู้ใช้
3. **เครือข่ายการกระจายเนื้อหา**:ปรับปรุงการแปลงเอกสารเพื่อเผยแพร่ทางเว็บพร้อมทั้งจัดการทรัพยากรอย่างมีประสิทธิภาพ

## การพิจารณาประสิทธิภาพ

การเพิ่มประสิทธิภาพการทำงานเมื่อใช้ Aspose.Words กับ Python:
- **การจัดการหน่วยความจำ**:ตรวจสอบการใช้ทรัพยากรและจัดการหน่วยความจำอย่างมีประสิทธิภาพด้วยการกำจัดวัตถุหลังการใช้งาน
- **การดำเนินการ I/O ไฟล์**:ลดการดำเนินการอ่าน/เขียนไฟล์ให้เหลือน้อยที่สุดเพื่อเพิ่มความเร็ว
- **การประมวลผลแบบแบตช์**:ดำเนินการเอกสารเป็นชุดๆ หากเป็นไปได้ เพื่อลดค่าใช้จ่ายทางธุรกิจ

## บทสรุป

ในบทช่วยสอนนี้ เราจะมาสำรวจวิธีการเพิ่มประสิทธิภาพการบันทึกเอกสารด้วย Aspose.Words สำหรับ Python โดยใช้ XAML Flow และคอลแบ็กความคืบหน้า ด้วยการใช้ฟีเจอร์เหล่านี้ คุณสามารถปรับปรุงประสิทธิภาพของเวิร์กโฟลว์การประมวลผลเอกสาร จัดการทรัพยากรอย่างมีประสิทธิภาพ และรับรองการดำเนินงานที่ตรงเวลา
{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}