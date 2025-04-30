---
"description": "تعرّف على كيفية ربط بيانات XML ديناميكيًا بعلامات المستندات المنظمة في Word باستخدام Aspose.Words لـ .NET. اتبع دليلنا خطوة بخطوة."
"linktitle": "نطاق علامات المستند المنظم - بدء تعيين XML"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "نطاق علامات المستند المنظم - بدء تعيين XML"
"url": "/ar/net/programming-with-sdt/structured-document-tag-range-start-xml-mapping/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# نطاق علامات المستند المنظم - بدء تعيين XML

## مقدمة

هل رغبتَ يومًا في إدراج بيانات XML ديناميكيًا في مستند Word؟ حسنًا، أنت محظوظ! يُسهّل Aspose.Words for .NET هذه المهمة. في هذا البرنامج التعليمي، سنتعمق في ربط نطاق علامات المستند المُهيكلة بـ XML. تتيح لك هذه الميزة ربط أجزاء XML مُخصصة بعناصر تحكم المحتوى، مما يضمن تحديث محتوى مستندك بسلاسة مع بيانات XML. جاهز لتحويل مستنداتك إلى روائع ديناميكية.

## المتطلبات الأساسية

قبل أن ننتقل إلى جزء الترميز، دعنا نتأكد من أن لديك كل ما تحتاجه:

1. مكتبة Aspose.Words لـ .NET: تأكد من حصولك على أحدث إصدار. يمكنك تنزيله. [هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: Visual Studio أو أي بيئة تطوير متكاملة أخرى تدعم C#.
3. المعرفة الأساسية بلغة C#: المعرفة ببرمجة C# أمر ضروري.
4. مستند Word: نموذج مستند Word للعمل عليه.

## استيراد مساحات الأسماء

أولاً، لنستورد مساحات الأسماء اللازمة. سيضمن هذا وصولنا إلى جميع الفئات والأساليب المطلوبة في Aspose.Words لـ .NET.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
using System.Text;
```

## الخطوة 1: إعداد دليل المستندات الخاص بك

كل مشروع يحتاج إلى أساس، أليس كذلك؟ هنا، نُنشئ المسار إلى دليل مستنداتك.

```csharp
// المسار إلى دليل المستندات الخاص بك 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## الخطوة 2: تحميل مستند Word

بعد ذلك، نحمّل مستند Word. هذا هو المستند الذي سنُدخل فيه بيانات XML.

```csharp
Document doc = new Document(dataDir + "Multi-section structured document tags.docx");
```

## الخطوة 3: إضافة جزء XML مخصص

نحتاج إلى إنشاء جزء XML يحتوي على البيانات التي نريد إدراجها، وإضافته إلى مجموعة CustomXmlPart للمستند. سيُستخدم هذا الجزء كمصدر بيانات لوسوم مستندنا المنظمة.

### إنشاء جزء XML

أولاً، قم بإنشاء معرف فريد لجزء XML وحدد محتواه.

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

علامة المستند المنظم (SDT) هي عنصر تحكم في المحتوى يمكن ربطه بجزء XML. هنا، نُنشئ علامة مستند منظم لعرض محتويات جزء XML المخصص.

أولاً، حدد نطاق SDT الذي يبدأ في المستند.

```csharp
StructuredDocumentTagRangeStart sdtRangeStart = (StructuredDocumentTagRangeStart)doc.GetChild(NodeType.StructuredDocumentTagRangeStart, 0, true);
```

## الخطوة 5: تعيين XML لـ SDT

الآن، حان وقت ربط جزء XML بـ SDT. بتعيين تعيين XML، نحدد أي جزء من بيانات XML يجب عرضه في SDT.

يشير مسار XPath إلى العنصر المحدد في جزء XML الذي نريد عرضه. هنا، نشير إلى العنصر الثاني `<text>` عنصر داخل `<root>` عنصر.

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

ها قد انتهيت! لقد نجحت في ربط جزء XML بعلامة مستند مُهيكلة في مستند Word باستخدام Aspose.Words لـ .NET. تُمكّنك هذه الميزة الفعّالة من إنشاء مستندات ديناميكية وقائمة على البيانات بسهولة. سواء كنت تُنشئ تقارير أو فواتير أو أي نوع آخر من المستندات، يُمكن لربط XML أن يُبسّط سير عملك بشكل كبير.

## الأسئلة الشائعة

### ما هي علامة المستند المنظم في Word؟
علامات المستندات المنظمة، والمعروفة أيضًا باسم عناصر التحكم في المحتوى، هي حاويات لأنواع محددة من المحتوى في مستندات Word. يمكن استخدامها لربط البيانات، أو تقييد التحرير، أو توجيه المستخدمين أثناء إنشاء المستندات.

### كيف يمكنني تحديث محتوى جزء XML بشكل ديناميكي؟
يمكنك تحديث محتوى جزء XML عن طريق تعديل `xmlPartContent` السلسلة قبل إضافتها إلى المستند. ما عليك سوى تحديث السلسلة بالبيانات الجديدة وإضافتها إلى `CustomXmlParts` مجموعة.

### هل يمكنني ربط أجزاء XML متعددة بـ SDTs مختلفة في نفس المستند؟
نعم، يمكنك ربط عدة أجزاء XML بملفات SDT مختلفة في نفس المستند. لكل ملف SDT جزء XML خاص به وتعيين XPath خاص به.

### هل من الممكن رسم خريطة لهياكل XML المعقدة إلى SDTs؟
بالتأكيد! يمكنك ربط هياكل XML المعقدة بـ SDTs باستخدام تعبيرات XPath مفصلة تشير بدقة إلى العناصر المطلوبة داخل جزء XML.

### كيف يمكنني إزالة جزء XML من مستند؟
يمكنك إزالة جزء XML عن طريق استدعاء `Remove` الطريقة على `CustomXmlParts` جمع، تمرير `xmlPartId` من جزء XML الذي تريد إزالته.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}