---
category: general
date: 2026-08-23
description: แปลสตริงเป็นภาษาสเปนใน C# โดยใช้ Aspose.Words AI Translator และผู้ให้บริการ
  Google. ทำตามคู่มือขั้นตอนต่อขั้นตอนเพื่อแปลสตริงใน C# อย่างรวดเร็ว.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate string to spanish
- translate string in c#
language: th
lastmod: 2026-08-23
og_description: แปลสตริงเป็นภาษาสเปนใน C# ด้วย Aspose.Words AI บทเรียนนี้แสดงวิธีตั้งค่าผู้ให้บริการ
  Google, แปลสตริง และแสดงผลลัพธ์
og_image_alt: Console screenshot showing translate string to spanish output in a C#
  application
og_title: แปลสตริงเป็นภาษาสเปนใน C# – ตัวอย่างโค้ดเต็ม
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Translate string to Spanish in C# using Aspose.Words AI Translator
    and Google provider. Follow the step‑by‑step guide to translate string in C# quickly.
  headline: Translate string to Spanish in C# with Aspose.Words AI
  type: TechArticle
- description: Translate string to Spanish in C# using Aspose.Words AI Translator
    and Google provider. Follow the step‑by‑step guide to translate string in C# quickly.
  name: Translate string to Spanish in C# with Aspose.Words AI
  steps:
  - name: '**Obtain an API key** from the Google Cloud Console → APIs & Services →
      Credentials.'
    text: '**Obtain an API key** from the Google Cloud Console → APIs & Services →
      Credentials.'
  - name: '**Enable the Cloud Translation API** for your project.'
    text: '**Enable the Cloud Translation API** for your project.'
  - name: Store the key securely (environment variable, secret manager, etc.). The
      example uses a literal for clarity, but production code should avoid hard‑coding
      secrets.
    text: Store the key securely (environment variable, secret manager, etc.). The
      example uses a literal for clarity, but production code should avoid hard‑coding
      secrets.
  - name: Open a terminal in the project folder.
    text: Open a terminal in the project folder.
  - name: Execute `dotnet run`.
    text: Execute `dotnet run`.
  - name: Confirm that the console displays the Spanish phrase.
    text: Confirm that the console displays the Spanish phrase.
  type: HowTo
tags:
- Aspose.Words
- C#
- Localization
title: แปลสตริงเป็นภาษาสเปนใน C# ด้วย Aspose.Words AI
url: /th/net/ai-powered-document-processing/translate-string-to-spanish-in-c-with-aspose-words-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# แปลสตริงเป็นภาษาสเปนใน C# ด้วย Aspose.Words AI

หากคุณต้องการ **แปลสตริงเป็นภาษาสเปน** ในแอปพลิเคชัน .NET คู่มือนี้จะแสดงวิธีทำอย่างละเอียด คุณจะได้เห็นตัวอย่างที่สมบูรณ์และสามารถรันได้ซึ่งสร้างตัวแปล, เรียกบริการของ Google, และพิมพ์ข้อความภาษาสเปนออกมา

บทแนะนำนี้ยังครอบคลุม **การแปลสตริงใน C#** ด้วยการใช้ไลบรารี Aspose.Words AI เพื่อให้คุณสามารถรวมการแปลภาษาตรงเข้าสู่โค้ดของคุณได้โดยไม่ต้องใช้สคริปต์ภายนอก

## สิ่งที่คุณต้องการ

- .NET 6.0 SDK หรือเวอร์ชันใหม่กว่า (โค้ดสามารถคอมไพล์กับ .NET Core และ .NET Framework)
- คีย์ API ของ Google Cloud Translation ที่ใช้งานได้
- แพคเกจ NuGet `Aspose.Words.AI` (ติดตั้งด้วย `dotnet add package Aspose.Words.AI`)
- ตัวแก้ไขโค้ดหรือ IDE เช่น Visual Studio 2022

ข้อกำหนดเบื้องต้นเหล่านี้ทำให้ตัวอย่างสามารถทำงานได้ทันที

## แปลสตริงเป็นภาษาสเปนด้วย Aspose.Words AI

ส่วนนี้สร้างอ็อบเจกต์ `Translator` ที่กำหนดค่าสำหรับผู้ให้บริการ Google ผู้ให้บริการจะจัดการคำขอ HTTP ไปยัง endpoint การแปลของ Google

```csharp
using System;
using Aspose.Words.AI;          // Namespace for Translator
using Aspose.Words.AI.Translator; // Contains TranslationProvider and Language enums

class Program
{
    static void Main()
    {
        // Step 1: Create a translator that uses Google as the provider
        var translator = new Translator(
            provider: TranslationProvider.Google,
            apiKey: "YOUR_GOOGLE_KEY");   // Replace with your real API key

        // Step 2: Translate the source text into Spanish
        string spanishText = translator.Translate(
            "Hello world",
            Language.Spanish);

        // Step 3: Use the translated text (display it in the console)
        Console.WriteLine(spanishText);
    }
}
```

**ทำไมวิธีนี้ถึงได้ผล:**  
- `Translator` แยกการเรียก HTTP ออกมา, จัดการการยืนยันตัวตนด้วยคีย์ API ที่คุณให้  
- `TranslationProvider.Google` บอก SDK ให้ส่งคำขอไปยัง Google Cloud Translation  
- `Language.Spanish` เลือกโค้ดภาษาปลายทาง (`es`)  
- เมธอด `Translate` จะคืนค่าสตริงที่แปลแล้ว, ซึ่งคุณสามารถใช้ได้ทุกที่ในแอปพลิเคชันของคุณ  

## ตั้งค่าผู้ให้บริการการแปลของ Google

1. **รับคีย์ API** จาก Google Cloud Console → APIs & Services → Credentials.  
2. **เปิดใช้งาน Cloud Translation API** สำหรับโปรเจกต์ของคุณ.  
3. เก็บคีย์อย่างปลอดภัย (ตัวแปรสภาพแวดล้อม, secret manager, ฯลฯ). ตัวอย่างใช้ค่าคงที่เพื่อความชัดเจน, แต่โค้ดในสภาพแวดล้อมจริงควรหลีกเลี่ยงการฝังคีย์โดยตรง  

## แปลสตริงใน C# – ทีละขั้นตอน

| ขั้นตอน | การกระทำ | เหตุผล |
|------|--------|--------|
| 1 | สร้างอินสแตนซ์ `Translator` ด้วย `TranslationProvider.Google` | เชื่อมต่อ SDK กับบริการของ Google |
| 2 | เรียก `Translate(source, Language.Spanish)` | ส่งข้อความต้นฉบับและรับผลลัพธ์เป็นภาษาสเปน |
| 3 | แสดงผลลัพธ์ด้วย `Console.WriteLine` | ตรวจสอบการแปลและสาธิตการใช้งาน |

การรันโปรแกรมจะพิมพ์:

```
¡Hola mundo!
```

> **หมายเหตุ:** ผลลัพธ์ที่ได้อาจแตกต่างกันเล็กน้อยขึ้นอยู่กับโมเดลการแปลของ Google (เช่น “Hola mundo” กับ “¡Hola mundo!”). ทั้งสองเป็นคำแปลภาษาสเปนที่ถูกต้อง  

## รันและตรวจสอบผลลัพธ์

1. เปิดเทอร์มินัลในโฟลเดอร์ของโปรเจกต์.  
2. รันคำสั่ง `dotnet run`.  
3. ยืนยันว่าคอนโซลแสดงประโยคภาษาสเปน  

หากคอนโซลแสดงข้อผิดพลาดเช่น *“401 Unauthorized”* ให้ตรวจสอบอีกครั้งว่าคีย์ API ถูกต้องและว่า Cloud Translation API ถูกเปิดใช้งานสำหรับโปรเจกต์  

## ข้อผิดพลาดทั่วไปและแนวทางปฏิบัติที่ดีที่สุด

- **ขีดจำกัดโควต้าของ API** – Google กำหนดขีดจำกัดการร้องขอต่อบัญชีการชำระเงิน ตรวจสอบการใช้งานใน Cloud Console เพื่อหลีกเลี่ยงการจำกัดที่ไม่คาดคิด  
- **ความหน่วงของเครือข่าย** – การเรียกแปลเป็นการร้องขอ HTTP ระยะไกล พิจารณาแคชสตริงที่แปลบ่อยเพื่อลดความหน่วง  
- **ปัญหาเรื่องการเข้ารหัส** – SDK ทำงานกับสตริง UTF‑8; ตรวจสอบว่าไฟล์ต้นฉบับของคุณบันทึกด้วยการเข้ารหัส UTF‑8 เพื่อรักษาอักขระพิเศษ  
- **การจัดการข้อผิดพลาด** – ห่อการเรียก `Translate` ด้วยบล็อก try‑catch เพื่อจัดการ `ApiException` และให้ข้อความสำรอง  

```csharp
try
{
    string spanishText = translator.Translate("Hello world", Language.Spanish);
    Console.WriteLine(spanishText);
}
catch (ApiException ex)
{
    Console.Error.WriteLine($"Translation failed: {ex.Message}");
    // Fallback to original text
    Console.WriteLine("Hello world");
}
```

## ขยายตัวอย่าง

- **แปลเป็นภาษอื่น** – แทนที่ `Language.Spanish` ด้วย `Language.French`, `Language.German` เป็นต้น  
- **การแปลแบบกลุ่ม** – เรียก `Translate` ภายในลูปเพื่อประมวลผลรายการสตริงหลายรายการ  
- **รวมเข้ากับ UI** – ใช้สตริงที่แปลในหน้า ASP.NET Core Razor, Windows Forms, หรือแอปพลิเคชัน WPF  

## สรุป

ตอนนี้คุณรู้วิธี **แปลสตริงเป็นภาษาสเปน** ใน C# ด้วย Aspose.Words AI และบริการ Google Translation แล้ว โซลูชันครบถ้วนนี้ครอบคลุมการตั้งค่าผู้ให้บริการ, การเรียกแปล, การจัดการข้อผิดพลาด, และการตรวจสอบผลลัพธ์  

จากนี้คุณสามารถทดลองใช้ภาษาต่าง ๆ เพิ่มเติม, แคชผลลัพธ์เพื่อประสิทธิภาพ, และรวมตัวแปลเข้ากับกระบวนการแปลภาษาขนาดใหญ่ได้  

--- 

*พร้อมที่จะทำการแปลเนื้อหาเพิ่มเติมหรือยัง? ดูบทแนะนำต่อไปเกี่ยวกับ **การแปลสตริงใน C# ด้วย Azure Cognitive Services** เพื่อใช้ผู้ให้บริการคลาวด์ทางเลือก*  

## คุณควรเรียนรู้อะไรต่อไป?

บทแนะนำต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดซึ่งต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดที่ทำงานได้ครบถ้วนพร้อมคำอธิบายทีละขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานทางเลือกในโปรเจกต์ของคุณ  

- [แทนที่ด้วยสตริง](/words/spanish/net/find-and-replace-text/replace-with-string/)
- [แทนที่ด้วยสตริง](/words/english/net/find-and-replace-text/replace-with-string/)
- [สร้างเอกสาร Word ด้วย Aspose.Words – คู่มือทีละขั้นตอน](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}