---
title: إنشاء قسم متكرر في الجدول مرتبط بجزء XML مخصص
linktitle: إنشاء قسم متكرر في الجدول مرتبط بجزء XML مخصص
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إنشاء جدول يحتوي على قسم متكرر مرتبط بـ CustomXmlPart في مستند Word باستخدام Aspose.Words لـ .NET.
weight: 10
url: /ar/net/programming-with-sdt/creating-table-repeating-section-mapped-to-custom-xml-part/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء قسم متكرر في الجدول مرتبط بجزء XML مخصص

## مقدمة

في هذا البرنامج التعليمي، سنستعرض عملية إنشاء جدول يحتوي على قسم متكرر يتم تعيينه إلى جزء XML مخصص باستخدام Aspose.Words for .NET. وهذا مفيد بشكل خاص لإنشاء مستندات بشكل ديناميكي استنادًا إلى بيانات منظمة.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:
1.  تم تثبيت مكتبة Aspose.Words لـ .NET. يمكنك تنزيلها من[موقع اسبوس](https://releases.aspose.com/words/net/).
2. فهم أساسي لـ C# وXML.

## استيراد مساحات الأسماء

تأكد من تضمين المساحات الأساسية اللازمة في مشروعك:

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
using Aspose.Words.Tables;
```

## الخطوة 1: تهيئة المستند وDocumentBuilder

 أولاً، قم بإنشاء مستند جديد وقم بتشغيله`DocumentBuilder`:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## الخطوة 2: إضافة جزء XML مخصص

أضف جزءًا مخصصًا من XML إلى المستند. يحتوي هذا الجزء من XML على البيانات التي نريد تعيينها إلى جدولنا:

```csharp
CustomXmlPart xmlPart = doc.CustomXmlParts.Add("Books",
    "<books><book><title>Everyday Italian</title><author>Giada De Laurentiis</author></book>" +
    "<book><title>Harry Potter</title><author>J K. Rowling</author></book>" +
    "<book><title>Learning XML</title><author>Erik T. Ray</author></book></books>");
```

## الخطوة 3: إنشاء هيكل الجدول

 بعد ذلك، استخدم`DocumentBuilder` لإنشاء رأس الجدول:

```csharp
Table table = builder.StartTable();
builder.InsertCell();
builder.Write("Title");
builder.InsertCell();
builder.Write("Author");
builder.EndRow();
builder.EndTable();
```

## الخطوة 4: إنشاء قسم متكرر

 إنشاء`StructuredDocumentTag` (SDT) للقسم المتكرر وربطه ببيانات XML:

```csharp
StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSection, MarkupLevel.Row);
repeatingSectionSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book", "");
table.AppendChild(repeatingSectionSdt);
```

## الخطوة 5: إنشاء عنصر قسم متكرر

قم بإنشاء SDT لعنصر القسم المتكرر وأضفه إلى القسم المتكرر:

```csharp
StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSectionItem, MarkupLevel.Row);
repeatingSectionSdt.AppendChild(repeatingSectionItemSdt);
Row row = new Row(doc);
repeatingSectionItemSdt.AppendChild(row);
```

## الخطوة 6: تعيين بيانات XML إلى خلايا الجدول

قم بإنشاء SDTs للعنوان والمؤلف، وقم بربطهما ببيانات XML، ثم قم بإضافتهما إلى الصف:

```csharp
StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
titleSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.AppendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
authorSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.AppendChild(authorSdt);
```

## الخطوة 7: حفظ المستند

وأخيرًا، قم بحفظ المستند في الدليل المحدد:

```csharp
doc.Save(dataDir + "WorkingWithSdt.CreatingTableRepeatingSectionMappedToCustomXmlPart.docx");
```

## خاتمة

باتباع هذه الخطوات، تكون قد نجحت في إنشاء جدول يحتوي على قسم متكرر مرتبط بجزء XML مخصص باستخدام Aspose.Words for .NET. يتيح هذا إنشاء محتوى ديناميكي استنادًا إلى بيانات منظمة، مما يجعل إنشاء المستندات أكثر مرونة وقوة.

## الأسئلة الشائعة

### ما هو StructuredDocumentTag (SDT)؟
SDT، المعروف أيضًا باسم عنصر التحكم في المحتوى، هو منطقة محدودة في مستند تُستخدم لاحتواء البيانات المنظمة.

### هل يمكنني استخدام أنواع بيانات أخرى في جزء XML المخصص؟
نعم، يمكنك هيكلة جزء XML المخصص الخاص بك باستخدام أي أنواع بيانات وتعيينها وفقًا لذلك.

### كيف أضيف المزيد من الصفوف إلى القسم المتكرر؟
يقوم القسم المتكرر بتكرار بنية الصف تلقائيًا لكل عنصر في مسار XML المحدد.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
