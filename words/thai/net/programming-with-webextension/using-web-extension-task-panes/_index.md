---
"description": "เรียนรู้วิธีการเพิ่มและกำหนดค่าบานหน้าต่างงานส่วนขยายเว็บในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ในบทช่วยสอนทีละขั้นตอนโดยละเอียดนี้"
"linktitle": "การใช้บานหน้าต่างงานส่วนขยายเว็บ"
"second_title": "API การประมวลผลเอกสาร Aspose.Words"
"title": "การใช้บานหน้าต่างงานส่วนขยายเว็บ"
"url": "/th/net/programming-with-webextension/using-web-extension-task-panes/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การใช้บานหน้าต่างงานส่วนขยายเว็บ

## การแนะนำ

ยินดีต้อนรับสู่บทช่วยสอนเชิงลึกเกี่ยวกับการใช้บานหน้าต่างงานส่วนขยายเว็บในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET หากคุณต้องการปรับปรุงเอกสาร Word ของคุณด้วยบานหน้าต่างงานแบบโต้ตอบ คุณมาถูกที่แล้ว คู่มือนี้จะแนะนำคุณทุกขั้นตอนเพื่อให้บรรลุเป้าหมายดังกล่าวได้อย่างราบรื่น

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเจาะลึก เรามาตรวจสอบกันก่อนว่าคุณมีทุกสิ่งที่คุณต้องการ:

- Aspose.Words สำหรับ .NET: คุณสามารถดาวน์โหลดได้ [ที่นี่](https://releases-aspose.com/words/net/).
- สภาพแวดล้อมการพัฒนา .NET: Visual Studio หรือ IDE อื่น ๆ ที่คุณต้องการ
- ความรู้พื้นฐานเกี่ยวกับ C#: จะช่วยให้คุณติดตามตัวอย่างโค้ดได้
- ใบอนุญาตสำหรับ Aspose.คำพูด: คุณสามารถซื้อได้หนึ่งอัน [ที่นี่](https://purchase.aspose.com/buy) หรือรับใบอนุญาตชั่วคราว [ที่นี่](https://purchase-aspose.com/temporary-license/).

## นำเข้าเนมสเปซ

ก่อนที่เราจะเริ่มเขียนโค้ด ให้แน่ใจว่าคุณได้นำเนมสเปซต่อไปนี้เข้าสู่โปรเจ็กต์ของคุณแล้ว:

```csharp
using Aspose.Words;
using Aspose.Words.WebExtensions;
```

## คำแนะนำทีละขั้นตอน

ตอนนี้มาแบ่งกระบวนการออกเป็นขั้นตอนที่ทำตามได้ง่าย ๆ กัน

### ขั้นตอนที่ 1: การตั้งค่าไดเรกทอรีเอกสารของคุณ

ขั้นแรก เราต้องตั้งค่าเส้นทางไปยังไดเร็กทอรีเอกสารของคุณ นี่คือที่ที่เอกสาร Word ของคุณจะถูกบันทึก

```csharp
// เส้นทางไปยังไดเร็กทอรีเอกสาร
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

แทนที่ `"YOUR DOCUMENT DIRECTORY"` พร้อมเส้นทางจริงไปยังโฟลเดอร์เอกสารของคุณ

### ขั้นตอนที่ 2: การสร้างเอกสารใหม่

ต่อไปเราจะสร้างเอกสาร Word ใหม่โดยใช้ Aspose.Words

```csharp
Document doc = new Document();
```

บรรทัดนี้จะเริ่มต้นอินสแตนซ์ใหม่ของ `Document` คลาสซึ่งแสดงถึงเอกสาร Word

### ขั้นตอนที่ 3: การเพิ่มบานหน้าต่างงาน

ตอนนี้เราจะเพิ่มบานหน้าต่างงานลงในเอกสารของเรา บานหน้าต่างงานมีประโยชน์สำหรับการให้ฟังก์ชันและเครื่องมือเพิ่มเติมภายในเอกสาร Word

```csharp
TaskPane taskPane = new TaskPane();
doc.WebExtensionTaskPanes.Add(taskPane);
```

ที่นี่เราสร้างใหม่ `TaskPane` วัตถุและเพิ่มเข้าไปในเอกสาร `WebExtensionTaskPanes` ของสะสม.

### ขั้นตอนที่ 4: การกำหนดค่าบานหน้าต่างงาน

เพื่อทำให้แผงงานของเรามองเห็นได้และตั้งค่าคุณสมบัติ เราใช้โค้ดดังต่อไปนี้:

```csharp
taskPane.DockState = TaskPaneDockState.Right;
taskPane.IsVisible = true;
taskPane.Width = 300;
```

- `DockState` กำหนดตำแหน่งที่แผงงานจะปรากฏขึ้น ในกรณีนี้จะอยู่ทางด้านขวา
- `IsVisible` ทำให้แน่ใจว่าบานหน้าต่างงานจะมองเห็นได้
- `Width` กำหนดความกว้างของบานหน้าต่างงาน

### ขั้นตอนที่ 5: การตั้งค่าการอ้างอิงส่วนขยายเว็บ

ขั้นต่อไป เราจะตั้งค่าการอ้างอิงส่วนขยายเว็บ ซึ่งรวมถึง ID, เวอร์ชัน, ประเภทร้านค้า และร้านค้า

```csharp
taskPane.WebExtension.Reference.Id = "wa102923726";
taskPane.WebExtension.Reference.Version = "1.0.0.0";
taskPane.WebExtension.Reference.StoreType = WebExtensionStoreType.OMEX;
taskPane.WebExtension.Reference.Store = "th-TH";
```

- `Id` เป็นตัวระบุเฉพาะสำหรับส่วนขยายเว็บ
- `Version` ระบุเวอร์ชันของส่วนขยาย
- `StoreType` ระบุประเภทของร้านค้า (ในกรณีนี้คือ OMEX)
- `Store` ระบุรหัสภาษา/วัฒนธรรมของร้านค้า

### ขั้นตอนที่ 6: การเพิ่มคุณสมบัติให้กับส่วนขยายเว็บ

คุณสามารถเพิ่มคุณสมบัติให้กับส่วนขยายเว็บของคุณเพื่อกำหนดพฤติกรรมหรือเนื้อหาของมันได้

```csharp
taskPane.WebExtension.Properties.Add(new WebExtensionProperty("mailchimpCampaign", "mailchimpCampaign"));
```

ที่นี่เราเพิ่มคุณสมบัติชื่อ `mailchimpCampaign`-

### ขั้นตอนที่ 7: การผูกส่วนขยายเว็บ

ในที่สุด เราก็เพิ่มการผูกมัดให้กับส่วนขยายเว็บของเรา การผูกมัดช่วยให้คุณสามารถเชื่อมโยงส่วนขยายกับส่วนเฉพาะของเอกสารได้

```csharp
taskPane.WebExtension.Bindings.Add(new WebExtensionBinding("UnnamedBinding_0_1506535429545", WebExtensionBindingType.Text, "194740422"));
```

- `UnnamedBinding_0_1506535429545` เป็นชื่อของการผูกมัด
- `WebExtensionBindingType.Text` ระบุว่าการผูกนั้นเป็นแบบชนิดข้อความ
- `194740422` คือรหัสของส่วนของเอกสารที่ส่วนขยายถูกผูกไว้

### ขั้นตอนที่ 8: การบันทึกเอกสาร

หลังจากตั้งค่าทุกอย่างแล้วให้บันทึกเอกสารของคุณ

```csharp
doc.Save(dataDir + "WorkingWithWebExtension.UsingWebExtensionTaskPanes.docx");
```

บรรทัดนี้จะบันทึกเอกสารไปยังไดเร็กทอรีที่ระบุโดยมีชื่อไฟล์ที่กำหนดไว้

### ขั้นตอนที่ 9: การโหลดและการแสดงข้อมูลบานหน้าต่างงาน

เพื่อตรวจสอบและแสดงข้อมูลบานหน้าต่างงาน เราจะโหลดเอกสารและทำซ้ำผ่านบานหน้าต่างงาน

```csharp
doc = new Document(dataDir + "WorkingWithWebExtension.UsingWebExtensionTaskPanes.docx");

Console.WriteLine("Task panes sources:\n");

foreach (TaskPane taskPaneInfo in doc.WebExtensionTaskPanes)
{
    WebExtensionReference reference = taskPaneInfo.WebExtension.Reference;
    Console.WriteLine($"Provider: \"{reference.Store}\", version: \"{reference.Version}\", catalog identifier: \"{reference.Id}\";");
}
```

โค้ดนี้จะโหลดเอกสารและพิมพ์ผู้ให้บริการ เวอร์ชัน และตัวระบุแค็ตตาล็อกของบานงานแต่ละบานในคอนโซล

## บทสรุป

เพียงเท่านี้ คุณก็สามารถเพิ่มและกำหนดค่าแถบงานส่วนขยายเว็บในเอกสาร Word ได้สำเร็จแล้วโดยใช้ Aspose.Words สำหรับ .NET ฟีเจอร์อันทรงพลังนี้จะช่วยปรับปรุงเอกสาร Word ของคุณได้อย่างมากโดยเพิ่มฟังก์ชันเพิ่มเติมโดยตรงภายในเอกสาร 

## คำถามที่พบบ่อย

### บานหน้าต่างงานใน Word คืออะไร?
บานหน้าต่างงานเป็นองค์ประกอบของอินเทอร์เฟซที่ให้เครื่องมือและฟังก์ชันเพิ่มเติมภายในเอกสาร Word เพื่อเพิ่มประสิทธิภาพการโต้ตอบและประสิทธิผลของผู้ใช้

### ฉันสามารถปรับแต่งลักษณะของบานหน้าต่างงานได้หรือไม่
ใช่ คุณสามารถปรับแต่งลักษณะของบานหน้าต่างงานได้โดยตั้งค่าคุณสมบัติ เช่น `DockState`- `IsVisible`, และ `Width`-

### คุณสมบัติส่วนขยายเว็บคืออะไร
คุณสมบัติส่วนขยายเว็บเป็นคุณสมบัติที่กำหนดเองซึ่งคุณสามารถเพิ่มลงในส่วนขยายเว็บเพื่อกำหนดลักษณะการทำงานหรือเนื้อหาได้

### ฉันจะผูกส่วนขยายเว็บกับส่วนหนึ่งของเอกสารได้อย่างไร
คุณสามารถผูกส่วนขยายเว็บกับส่วนหนึ่งของเอกสารโดยใช้ `WebExtensionBinding` คลาส โดยระบุชนิดการผูกและ ID เป้าหมาย

### ฉันสามารถหาข้อมูลเพิ่มเติมเกี่ยวกับ Aspose.Words สำหรับ .NET ได้จากที่ไหน
คุณสามารถค้นหาเอกสารรายละเอียดได้ [ที่นี่](https://reference-aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}