---
"description": "เรียนรู้วิธีการสร้างตารางที่มีส่วนที่ทำซ้ำซึ่งแมปกับ CustomXmlPart ในเอกสาร Word โดยใช้ Aspose.Words สำหรับ .NET"
"linktitle": "การสร้างตารางส่วนที่ทำซ้ำโดยแม็ปกับส่วน XML ที่กำหนดเอง"
"second_title": "API การประมวลผลเอกสาร Aspose.Words"
"title": "การสร้างตารางส่วนที่ทำซ้ำโดยแม็ปกับส่วน XML ที่กำหนดเอง"
"url": "/th/net/programming-with-sdt/creating-table-repeating-section-mapped-to-custom-xml-part/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การสร้างตารางส่วนที่ทำซ้ำโดยแม็ปกับส่วน XML ที่กำหนดเอง

## การแนะนำ

ในบทช่วยสอนนี้ เราจะแนะนำขั้นตอนการสร้างตารางที่มีส่วนที่ซ้ำกันซึ่งแมปกับส่วน XML ที่กำหนดเองโดยใช้ Aspose.Words สำหรับ .NET ซึ่งมีประโยชน์อย่างยิ่งสำหรับการสร้างเอกสารแบบไดนามิกโดยอิงจากข้อมูลที่มีโครงสร้าง

## ข้อกำหนดเบื้องต้น

ก่อนที่เราจะเริ่ม โปรดตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
1. ติดตั้งไลบรารี Aspose.Words สำหรับ .NET แล้ว คุณสามารถดาวน์โหลดได้จาก [เว็บไซต์อาโพส](https://releases-aspose.com/words/net/).
2. ความเข้าใจพื้นฐานเกี่ยวกับ C# และ XML

## นำเข้าเนมสเปซ

อย่าลืมรวมเนมสเปซที่จำเป็นในโครงการของคุณ:

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
using Aspose.Words.Tables;
```

## ขั้นตอนที่ 1: เริ่มต้นใช้งาน Document และ DocumentBuilder

ขั้นแรกให้สร้างเอกสารใหม่และเริ่มต้นใช้งาน `DocumentBuilder`-

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ขั้นตอนที่ 2: เพิ่มส่วน XML ที่กำหนดเอง

เพิ่มส่วน XML ที่กำหนดเองลงในเอกสาร XML นี้ประกอบด้วยข้อมูลที่เราต้องการแมปกับตารางของเรา:

```csharp
CustomXmlPart xmlPart = doc.CustomXmlParts.Add("Books",
    "<books><book><title>Everyday Italian</title><author>Giada De Laurentiis</author></book>" +
    "<book><title>Harry Potter</title><author>J K. Rowling</author></book>" +
    "<book><title>Learning XML</title><author>Erik T. Ray</author></book></books>");
```

## ขั้นตอนที่ 3: สร้างโครงสร้างตาราง

ถัดไปใช้ `DocumentBuilder` เพื่อสร้างส่วนหัวของตาราง:

```csharp
Table table = builder.StartTable();
builder.InsertCell();
builder.Write("Title");
builder.InsertCell();
builder.Write("Author");
builder.EndRow();
builder.EndTable();
```

## ขั้นตอนที่ 4: สร้างส่วนที่ทำซ้ำ

สร้าง `StructuredDocumentTag` (SDT) สำหรับส่วนที่ทำซ้ำและแมปไปยังข้อมูล XML:

```csharp
StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSection, MarkupLevel.Row);
repeatingSectionSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book", "");
table.AppendChild(repeatingSectionSdt);
```

## ขั้นตอนที่ 5: สร้างรายการส่วนที่ซ้ำกัน

สร้าง SDT สำหรับรายการส่วนที่ทำซ้ำและเพิ่มลงในส่วนที่ทำซ้ำ:

```csharp
StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSectionItem, MarkupLevel.Row);
repeatingSectionSdt.AppendChild(repeatingSectionItemSdt);
Row row = new Row(doc);
repeatingSectionItemSdt.AppendChild(row);
```

## ขั้นตอนที่ 6: แมปข้อมูล XML ไปยังเซลล์ตาราง

สร้าง SDT สำหรับชื่อเรื่องและผู้เขียน แมปไปยังข้อมูล XML และผนวกเข้ากับแถว:

```csharp
StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
titleSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.AppendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
authorSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.AppendChild(authorSdt);
```

## ขั้นตอนที่ 7: บันทึกเอกสาร

สุดท้ายให้บันทึกเอกสารไปยังไดเร็กทอรีที่ระบุ:

```csharp
doc.Save(dataDir + "WorkingWithSdt.CreatingTableRepeatingSectionMappedToCustomXmlPart.docx");
```

## บทสรุป

หากทำตามขั้นตอนเหล่านี้ คุณจะสร้างตารางที่มีส่วนที่ซ้ำกันซึ่งแมปกับส่วน XML ที่กำหนดเองได้สำเร็จโดยใช้ Aspose.Words สำหรับ .NET วิธีนี้ช่วยให้สร้างเนื้อหาแบบไดนามิกโดยอิงตามข้อมูลที่มีโครงสร้าง ทำให้การสร้างเอกสารมีความยืดหยุ่นและทรงพลังมากขึ้น

## คำถามที่พบบ่อย

### StructuredDocumentTag (SDT) คืออะไร?
SDT หรือที่เรียกอีกอย่างว่าการควบคุมเนื้อหา คือบริเวณที่มีขอบเขตในเอกสารซึ่งใช้เพื่อเก็บข้อมูลที่มีโครงสร้าง

### ฉันสามารถใช้ประเภทข้อมูลอื่นในส่วน XML ที่กำหนดเองได้หรือไม่
ใช่ คุณสามารถสร้างโครงสร้างส่วน XML ที่กำหนดเองด้วยประเภทข้อมูลใดๆ ก็ได้และแมปตามนั้นได้

### ฉันจะเพิ่มแถวเพิ่มเติมลงในส่วนที่ทำซ้ำได้อย่างไร
ส่วนที่ทำซ้ำจะจำลองโครงสร้างแถวสำหรับแต่ละรายการในเส้นทาง XML ที่แมปโดยอัตโนมัติ


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}