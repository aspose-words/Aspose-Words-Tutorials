---
category: general
date: 2026-09-11
description: Mail merge ของ Aspose ช่วยให้คุณโหลดเทมเพลต Word และเติมข้อมูลลงในเทมเพลต
  Word โดยอัตโนมัติ เพื่อสร้างเอกสารสำหรับจดหมายส่วนบุคคล.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- mail merge aspose
- populate word template
- load word template
- automate document generation
- create personalized letters
language: th
lastmod: 2026-09-11
og_description: Mail merge ของ aspose ช่วยให้คุณโหลดเทมเพลต Word และเติมข้อมูลในเทมเพลต
  Word ได้อย่างง่ายดาย ทำให้กระบวนการสร้างเอกสารเป็นไปอย่างราบรื่น เพื่อให้คุณสร้างจดหมายส่วนบุคคลได้อย่างรวดเร็ว.
og_image_alt: Screenshot of C# code using Aspose.Words to perform a mail merge on
  a Word template
og_title: 'Mail merge Aspose: เติมข้อมูลเทมเพลต Word ภายในไม่กี่นาที'
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Mail merge aspose lets you load word template and populate word template
    with data, automating document generation for creating personalized letters.
  headline: How to perform mail merge aspose to populate a Word template
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
title: วิธีทำเมลเมิร์จด้วย Aspose เพื่อเติมข้อมูลในเทมเพลต Word
url: /th/net/working-with-fields/how-to-perform-mail-merge-aspose-to-populate-a-word-template/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# วิธีทำ Mail Merge ด้วย Aspose เพื่อเติมข้อมูลลงในเทมเพลต Word

หากคุณต้องการ **mail merge aspose** เพื่อสร้างจดหมายส่วนบุคคลหลายฉบับ คำแนะนำนี้จะแสดงให้คุณเห็นขั้นตอนการโหลดเทมเพลต Word, เติมข้อมูลลงในเทมเพลต, และทำอัตโนมัติการสร้างเอกสารด้วยเพียงไม่กี่บรรทัดของ C# ไม่ว่าคุณจะสร้างระบบส่งจดหมายหรือเครื่องมือรายงาน ตัวอย่างเต็มด้านล่างจะช่วยให้คุณสร้างจดหมายส่วนบุคคลโดยไม่ต้องเขียนตรรกะการรวมข้อมูลด้วยตนเอง

คุณจะได้เรียนรู้วิธี **load word template**, ใช้คลาส low‑code `MailMerger`, และ **populate word template** ด้วยแหล่งข้อมูลแบบไม่ระบุชื่อ (anonymous). เมื่อจบบทเรียนคุณจะมีแอปคอนโซลที่พร้อมรันและสร้างไฟล์ Word ที่รวมข้อมูลแล้ว ซึ่งคุณสามารถส่งอีเมล, พิมพ์, หรือเก็บเป็นเอกสารได้

## Prerequisites

ก่อนเริ่มทำงาน โปรดตรวจสอบว่าคุณมี:

* .NET 6.0 SDK หรือใหม่กว่า  
* ใบอนุญาต Aspose.Words for .NET ที่ถูกต้อง (หรือคีย์ทดลองใช้ฟรี)  
* แพคเกจ NuGet `Aspose.Words` (เวอร์ชัน 23.10 หรือใหม่กว่า) ที่ติดตั้งในโปรเจกต์ของคุณ  
* ไฟล์ Word (`MailMergeTemplate.docx`) ที่มีตัวแปร MERGEFIELD เช่น **«Name»** และ **«Age»**  

คุณสามารถสร้างเทมเพลตนี้ใน Microsoft Word โดยเลือก *Insert → Quick Parts → Field → MergeField* แล้วตั้งชื่อฟิลด์ให้ตรงกับชื่อคุณสมบัติในแหล่งข้อมูลของคุณ

## Step 1 – Prepare the data source for the mail merge

การรวมข้อมูลแบบ low‑code ทำงานกับคอลเลกชันที่สามารถวนซ้ำได้ทุกประเภท ในตัวอย่างนี้เราใช้ array ของอ็อบเจ็กต์แบบไม่ระบุชื่อ แต่คุณก็สามารถส่ง `DataTable`, รายการ POCO, หรือข้อมูลที่อ่านจากฐานข้อมูลได้เช่นกัน

```csharp
using Aspose.Words;
using Aspose.Words.LowCode;

// Sample data that will replace the MERGEFIELDs in the template
var data = new[]
{
    new { Name = "Alice",   Age = 30 },
    new { Name = "Bob",     Age = 45 },
    new { Name = "Charlie", Age = 28 }
};
```

**ทำไมเรื่องนี้ถึงสำคัญ:**  
ชื่อคุณสมบัติของแต่ละอ็อบเจ็กต์ (`Name`, `Age`) ต้องตรงกับ MERGEFIELD ในเทมเพลต คลาส `MailMerger` จะทำการแมปคุณสมบัติเหล่านั้นกับฟิลด์โดยอัตโนมัติ ทำให้ไม่ต้องเขียนเหตุการณ์ `FieldMerging` ด้วยตนเอง

## Step 2 – Load the Word template that contains MERGEFIELDs

การโหลดเทมเพลตทำได้ง่ายด้วยคลาส `Document` เส้นทางไฟล์สามารถเป็นแบบ absolute หรือ relative ไปยังไดเรกทอรีทำงานของไฟล์ executable

```csharp
// Load the Word template that contains MERGEFIELDs
Document template = new Document("YOUR_DIRECTORY/MailMergeTemplate.docx");
```

**เคล็ดลับ:**  
หากคุณรันโค้ดจาก Visual Studio ให้ตั้งค่า *Copy to Output Directory* ของไฟล์เทมเพลตเป็น **Copy always** เพื่อให้แน่ใจว่าไฟล์พร้อมใช้งานเมื่อไบนารีที่คอมไพล์แล้วทำงาน

## Step 3 – Create a MailMerger instance bound to the template

คลาส `MailMerger` อยู่ใน namespace `Aspose.Words.LowCode` และให้เมธอด `Execute` เพียงหนึ่งตัวที่รับแหล่งข้อมูลเป็นพารามิเตอร์

```csharp
// Bind the template to a MailMerger instance
MailMerger merger = new MailMerger(template);
```

**ทำไมต้องใช้ MailMerger?**  
`MailMerger` ทำหน้าที่ซ่อนการเรียก `MailMerge.Execute` ที่ต้องเขียนโค้ดซ้ำ ๆ, จัดการการตรวจจับฟิลด์, การผูกข้อมูล, และการคล cloning เอกสารภายใน ทำให้โค้ดเหมาะกับสถานการณ์ **automate document generation** ที่ต้องการโซลูชัน low‑code ที่สะอาดและง่ายต่อการบำรุงรักษา

## Step 4 – Execute the low‑code merge using the prepared data

การเรียก `Execute` จะคืนค่า `Document` ใหม่ที่มีข้อมูลรวมแล้ว

## What Should You Learn Next?

บทเรียนต่อไปนี้ครอบคลุมหัวข้อที่เกี่ยวข้องอย่างใกล้ชิดและต่อยอดจากเทคนิคที่แสดงในคู่มือนี้ แต่ละแหล่งข้อมูลมีตัวอย่างโค้ดทำงานเต็มรูปแบบพร้อมคำอธิบายขั้นตอนเพื่อช่วยให้คุณเชี่ยวชาญฟีเจอร์ API เพิ่มเติมและสำรวจวิธีการทำงานแบบอื่นในโปรเจกต์ของคุณ

- [เปลี่ยนชื่อ Word Merge Fields ด้วย Aspose.Words for Java](/words/english/java/mail-merge-reporting/rename-word-merge-fields-aspose-words-java/)
- [สร้างเอกสาร Word พร้อม Header และ Footer ด้วย Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [สร้างและจัดรูปแบบเอกสาร Word ใน Aspose.Words for .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}