---
title: ตั้งค่าภาษารัสเซียเป็นภาษาแก้ไขเริ่มต้น
linktitle: ตั้งค่าภาษารัสเซียเป็นภาษาแก้ไขเริ่มต้น
second_title: API การประมวลผลเอกสาร Aspose.Words
description: เรียนรู้วิธีตั้งค่าภาษารัสเซียเป็นภาษาแก้ไขเริ่มต้นในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET ปฏิบัติตามคำแนะนำทีละขั้นตอนของเราเพื่อดูคำแนะนำโดยละเอียด
weight: 10
url: /th/net/programming-with-document-options-and-settings/set-russian-as-default-editing-language/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ตั้งค่าภาษารัสเซียเป็นภาษาแก้ไขเริ่มต้น

## การแนะนำ

ในโลกปัจจุบันที่มีหลายภาษา มักจำเป็นต้องปรับแต่งเอกสารของคุณให้ตรงตามความชอบด้านภาษาของกลุ่มเป้าหมายที่แตกต่างกัน การตั้งค่าภาษาแก้ไขเริ่มต้นในเอกสาร Word ถือเป็นการปรับแต่งอย่างหนึ่ง หากคุณใช้ Aspose.Words สำหรับ .NET บทช่วยสอนนี้จะแนะนำคุณเกี่ยวกับการตั้งค่าภาษารัสเซียเป็นภาษาแก้ไขเริ่มต้นในเอกสาร Word ของคุณ 

คู่มือทีละขั้นตอนนี้จะช่วยให้คุณเข้าใจกระบวนการทุกขั้นตอน ตั้งแต่การตั้งค่าสภาพแวดล้อมจนถึงการตรวจสอบการตั้งค่าภาษาในเอกสารของคุณ

## ข้อกำหนดเบื้องต้น

ก่อนจะเริ่มเขียนโค้ด ให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:

1.  Aspose.Words สำหรับ .NET: คุณต้องมีไลบรารี Aspose.Words สำหรับ .NET คุณสามารถดาวน์โหลดได้จาก[การเปิดตัว Aspose](https://releases.aspose.com/words/net/) หน้าหนังสือ.
2. สภาพแวดล้อมการพัฒนา: แนะนำให้ใช้ IDE เช่น Visual Studio สำหรับการเขียนโค้ดและการรันแอปพลิเคชัน .NET
3. ความรู้พื้นฐานเกี่ยวกับ C#: การทำความเข้าใจภาษาการเขียนโปรแกรม C# และกรอบงาน .NET ถือเป็นสิ่งสำคัญสำหรับการปฏิบัติตามบทช่วยสอนนี้

## นำเข้าเนมสเปซ

ก่อนที่เราจะเจาะลึกในรายละเอียด โปรดตรวจสอบให้แน่ใจว่าคุณได้นำเข้าเนมสเปซที่จำเป็นในโปรเจ็กต์ของคุณแล้ว เนมสเปซเหล่านี้ให้สิทธิ์ในการเข้าถึงคลาสและเมธอดที่จำเป็นในการจัดการเอกสาร Word

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
```

## ขั้นตอนที่ 1: การตั้งค่า LoadOptions

 ขั้นแรกเราต้องกำหนดค่า`LoadOptions` เพื่อตั้งค่าภาษาการแก้ไขเริ่มต้นเป็นภาษารัสเซีย ขั้นตอนนี้เกี่ยวข้องกับการสร้างอินสแตนซ์ของ`LoadOptions` และการตั้งค่าของมัน`LanguagePreferences.DefaultEditingLanguage` คุณสมบัติ.

### สร้างอินสแตนซ์ LoadOptions

```csharp
LoadOptions loadOptions = new LoadOptions();
```

### ตั้งค่าภาษาแก้ไขเริ่มต้นเป็นภาษารัสเซีย

```csharp
loadOptions.LanguagePreferences.DefaultEditingLanguage = EditingLanguage.Russian;
```

 ในขั้นตอนนี้ คุณจะสร้างอินสแตนซ์ของ`LoadOptions` และตั้งค่าของมัน`DefaultEditingLanguage`ทรัพย์สินที่จะ`EditingLanguage.Russian`นี่จะบอก Aspose.Words ให้ถือว่าภาษารัสเซียเป็นภาษาแก้ไขเริ่มต้นทุกครั้งที่โหลดเอกสารด้วยตัวเลือกเหล่านี้

## ขั้นตอนที่ 2: โหลดเอกสาร

 ต่อไปเราจะต้องโหลดเอกสาร Word โดยใช้`LoadOptions` กำหนดค่าไว้ในขั้นตอนก่อนหน้า ซึ่งเกี่ยวข้องกับการระบุเส้นทางไปยังเอกสารของคุณและส่งต่อ`LoadOptions` ตัวอย่างถึง`Document` ผู้สร้าง

### ระบุเส้นทางเอกสาร

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

### โหลดเอกสารด้วย LoadOptions

```csharp
Document doc = new Document(dataDir + "No default editing language.docx", loadOptions);
```

 ในขั้นตอนนี้ คุณระบุเส้นทางไดเร็กทอรีที่เอกสารของคุณตั้งอยู่และโหลดเอกสารโดยใช้`Document` ผู้สร้าง`LoadOptions` ตรวจสอบให้แน่ใจว่าได้ตั้งค่าภาษารัสเซียเป็นภาษาการแก้ไขเริ่มต้น

## ขั้นตอนที่ 3: ตรวจสอบภาษาการแก้ไขเริ่มต้น

 หลังจากโหลดเอกสารแล้ว สิ่งสำคัญคือต้องตรวจสอบว่าภาษาแก้ไขเริ่มต้นถูกตั้งค่าเป็นภาษารัสเซียหรือไม่ ซึ่งเกี่ยวข้องกับการตรวจสอบ`LocaleId` ของรูปแบบอักษรเริ่มต้นของเอกสาร

### รับ LocaleId ของฟอนต์เริ่มต้น

```csharp
int localeId = doc.Styles.DefaultFont.LocaleId;
```

### ตรวจสอบว่า LocaleId ตรงกับภาษารัสเซียหรือไม่

```csharp
Console.WriteLine(
    localeId == (int)EditingLanguage.Russian
        ? "The document either has no any language set in defaults or it was set to Russian originally."
        : "The document default language was set to another than Russian language originally, so it is not overridden.");
```

 ในขั้นตอนนี้คุณจะได้รับ`LocaleId` ของรูปแบบฟอนต์เริ่มต้นและเปรียบเทียบกับ`EditingLanguage.Russian` ตัวระบุ ข้อความเอาท์พุตจะระบุว่าภาษาเริ่มต้นถูกตั้งค่าเป็นภาษารัสเซียหรือไม่

## บทสรุป

 การตั้งค่าภาษารัสเซียเป็นภาษาแก้ไขเริ่มต้นในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET เป็นเรื่องง่ายด้วยขั้นตอนที่ถูกต้อง โดยการกำหนดค่า`LoadOptions`การโหลดเอกสาร และการตรวจสอบการตั้งค่าภาษา คุณสามารถมั่นใจได้ว่าเอกสารของคุณตรงตามความต้องการด้านภาษาของผู้อ่านของคุณ 

คู่มือนี้มีขั้นตอนที่ชัดเจนและละเอียดเพื่อช่วยให้คุณปรับแต่งได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย

### Aspose.Words สำหรับ .NET คืออะไร?

Aspose.Words สำหรับ .NET เป็นไลบรารีที่มีประสิทธิภาพสำหรับการทำงานกับเอกสาร Word ในโปรแกรมแอปพลิเคชัน .NET ช่วยให้สามารถสร้าง แก้ไข และแปลงเอกสารได้

### ฉันจะดาวน์โหลด Aspose.Words สำหรับ .NET ได้อย่างไร?

 คุณสามารถดาวน์โหลด Aspose.Words สำหรับ .NET ได้จาก[การเปิดตัว Aspose](https://releases.aspose.com/words/net/) หน้าหนังสือ.

###  อะไรคือ`LoadOptions` used for?

`LoadOptions` ใช้เพื่อระบุตัวเลือกต่าง ๆ สำหรับการโหลดเอกสาร เช่น การตั้งค่าภาษาการแก้ไขเริ่มต้น

### ฉันสามารถตั้งค่าภาษาอื่นเป็นภาษาการแก้ไขเริ่มต้นได้หรือไม่

 ใช่ คุณสามารถตั้งค่าภาษาใดๆ ก็ได้ที่รองรับโดย Aspose.Words โดยกำหนดภาษาที่เหมาะสม`EditingLanguage` มูลค่าที่จะ`DefaultEditingLanguage`.

### ฉันจะได้รับการสนับสนุนสำหรับ Aspose.Words สำหรับ .NET ได้อย่างไร

 คุณสามารถรับการสนับสนุนได้จาก[การสนับสนุน Aspose](https://forum.aspose.com/c/words/8) ฟอรัมที่คุณสามารถถามคำถามและรับความช่วยเหลือจากชุมชนและนักพัฒนา Aspose

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
