---
title: تعيين نطاق علامات المستند المنظم في بداية XML
linktitle: تعيين نطاق علامات المستند المنظم في بداية XML
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية ربط بيانات XML ديناميكيًا بعلامات المستندات المنظمة في Word باستخدام Aspose.Words for .NET. اتبع دليلنا خطوة بخطوة.
weight: 10
url: /ar/net/programming-with-sdt/structured-document-tag-range-start-xml-mapping/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تعيين نطاق علامات المستند المنظم في بداية XML

## مقدمة

هل سبق لك أن أردت إدراج بيانات XML بشكل ديناميكي في مستند Word؟ حسنًا، أنت محظوظ! يجعل برنامج Aspose.Words for .NET هذه المهمة سهلة للغاية. في هذا البرنامج التعليمي، نتعمق في تعيين نطاق علامات المستند المنظم. تتيح لك هذه الميزة ربط أجزاء XML مخصصة بعناصر التحكم في المحتوى، مما يضمن تحديث محتوى المستند بسلاسة باستخدام بيانات XML. جاهز لتحويل مستنداتك إلى روائع ديناميكية.

## المتطلبات الأساسية

قبل أن ننتقل إلى جزء الترميز، دعنا نتأكد من أن لديك كل ما تحتاجه:

1.  Aspose.Words for .NET Library: تأكد من حصولك على أحدث إصدار. يمكنك تنزيله[هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: Visual Studio أو أي بيئة تطوير متكاملة أخرى تدعم C#.
3. المعرفة الأساسية بلغة C#: المعرفة ببرمجة C# أمر ضروري.
4. مستند Word: نموذج لمستند Word للعمل عليه.

## استيراد مساحات الأسماء

أولاً وقبل كل شيء، دعنا نستورد مساحات الأسماء الضرورية. سيضمن هذا إمكانية الوصول إلى جميع الفئات والطرق المطلوبة في Aspose.Words لـ .NET.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
using System.Text;
```

## الخطوة 1: إعداد دليل المستندات الخاص بك

يحتاج كل مشروع إلى أساس، أليس كذلك؟ هنا، نقوم بإعداد المسار إلى دليل المستندات الخاص بك.

```csharp
// المسار إلى دليل المستند الخاص بك
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## الخطوة 2: تحميل مستند Word

بعد ذلك، نقوم بتحميل مستند Word. هذا هو المستند الذي سنقوم بإدخال بيانات XML فيه.

```csharp
Document doc = new Document(dataDir + "Multi-section structured document tags.docx");
```

## الخطوة 3: إضافة جزء XML مخصص

نحتاج إلى إنشاء جزء XML يحتوي على البيانات التي نريد إدراجها وإضافتها إلى مجموعة CustomXmlPart الخاصة بالمستند. سيعمل جزء XML المخصص هذا كمصدر بيانات لعلامات المستند المنظمة.

### إنشاء جزء XML

أولاً، قم بإنشاء معرف فريد للجزء XML وقم بتحديد محتواه.

```csharp
// إنشاء جزء XML يحتوي على بيانات وإضافته إلى مجموعة CustomXmlPart الخاصة بالمستند.
string xmlPartId = Guid.NewGuid().ToString("B");
string xmlPartContent = "<root><text>Text element #1</text><text>Text element #2</text></root>";
CustomXmlPart xmlPart = doc.CustomXmlParts.Add(xmlPartId, xmlPartContent);
```

### التحقق من محتوى جزء XML

للتأكد من إضافة جزء XML بشكل صحيح، نقوم بطباعة محتواه.

```csharp
Console.WriteLine(Encoding.UTF8.GetString(xmlPart.Data));
```

## الخطوة 4: إنشاء علامة مستند منظمة

علامة المستند المنظم (SDT) عبارة عن عنصر تحكم في المحتوى يمكنه الارتباط بجزء XML. هنا، نقوم بإنشاء SDT لعرض محتويات جزء XML المخصص لدينا.

أولاً، حدد بداية نطاق SDT في المستند.

```csharp
StructuredDocumentTagRangeStart sdtRangeStart = (StructuredDocumentTagRangeStart)doc.GetChild(NodeType.StructuredDocumentTagRangeStart, 0, true);
```

## الخطوة 5: تعيين تعيين XML لـ SDT

الآن، حان الوقت لربط جزء XML الخاص بنا بـ SDT. من خلال تعيين تعيين XML، نحدد الجزء من بيانات XML الذي يجب عرضه في SDT.

 يشير XPath إلى العنصر المحدد في جزء XML الذي نريد عرضه. هنا، نشير إلى العنصر الثاني`<text>` عنصر داخل`<root>` عنصر.

```csharp
// تعيين تعيين لعلامة StructuredDocumentTag الخاصة بنا
sdtRangeStart.XmlMapping.SetMapping(xmlPart, "/root[1]/text[2]", null);
```

## الخطوة 6: حفظ المستند

أخيرًا، احفظ المستند لمشاهدة التغييرات أثناء العمل. سيعرض SDT في مستند Word الآن محتوى XML المحدد.

```csharp
doc.Save(dataDir + "WorkingWithSdt.StructuredDocumentTagRangeStartXmlMapping.docx");
```

## خاتمة

والآن، لقد نجحت في ربط جزء XML بعلامة مستند منظمة في مستند Word باستخدام Aspose.Words for .NET. تتيح لك هذه الميزة القوية إنشاء مستندات ديناميكية تعتمد على البيانات دون عناء. سواء كنت تقوم بإنشاء تقارير أو فواتير أو أي نوع آخر من المستندات، فإن ربط XML يمكن أن يبسط سير عملك بشكل كبير.

## الأسئلة الشائعة

### ما هي علامة المستند المنظم في Word؟
العلامات المنظمة للمستندات، والمعروفة أيضًا باسم عناصر التحكم في المحتوى، هي حاويات لأنواع معينة من المحتوى في مستندات Word. ويمكن استخدامها لربط البيانات أو تقييد التحرير أو توجيه المستخدمين في إنشاء المستندات.

### كيف يمكنني تحديث محتوى جزء XML بشكل ديناميكي؟
 يمكنك تحديث محتوى جزء XML عن طريق تعديل`xmlPartContent` السلسلة قبل إضافتها إلى المستند. ما عليك سوى تحديث السلسلة بالبيانات الجديدة وإضافتها إلى`CustomXmlParts` مجموعة.

### هل يمكنني ربط أجزاء XML متعددة بـ SDTs مختلفة في نفس المستند؟
نعم، يمكنك ربط أجزاء XML متعددة بـ SDTs مختلفة في نفس المستند. يمكن أن يكون لكل SDT جزء XML فريد خاص به وتعيين XPath.

### هل من الممكن رسم هياكل XML المعقدة إلى SDTs؟
بالتأكيد! يمكنك تعيين هياكل XML المعقدة إلى SDTs باستخدام تعبيرات XPath التفصيلية التي تشير بدقة إلى العناصر المطلوبة داخل جزء XML.

### كيف يمكنني إزالة جزء XML من مستند؟
 يمكنك إزالة جزء XML عن طريق استدعاء`Remove` الطريقة على`CustomXmlParts` جمع، تمرير`xmlPartId` من جزء XML الذي تريد إزالته.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
