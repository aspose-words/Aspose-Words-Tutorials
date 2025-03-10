---
title: توسيع التنسيق على الخلايا والصفوف من النمط
linktitle: توسيع التنسيق على الخلايا والصفوف من النمط
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية توسيع التنسيق في الخلايا والصفوف من الأنماط في مستندات Word باستخدام Aspose.Words for .NET. يتضمن دليل خطوة بخطوة.
weight: 10
url: /ar/net/programming-with-table-styles-and-formatting/expand-formatting-on-cells-and-row-from-style/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# توسيع التنسيق على الخلايا والصفوف من النمط

## مقدمة

هل وجدت نفسك يومًا في حاجة إلى تطبيق تنسيق متسق عبر الجداول في مستندات Word الخاصة بك؟ قد يكون تعديل كل خلية يدويًا أمرًا مرهقًا وعرضة للأخطاء. وهنا يأتي دور Aspose.Words for .NET. سيرشدك هذا البرنامج التعليمي خلال عملية توسيع التنسيق على الخلايا والصفوف من نمط الجدول، مما يضمن أن تبدو مستنداتك مصقولة واحترافية دون أي متاعب إضافية.

## المتطلبات الأساسية

قبل أن ننتقل إلى التفاصيل الدقيقة، تأكد من أنك قمت بما يلي:

-  Aspose.Words for .NET: يمكنك تنزيله[هنا](https://releases.aspose.com/words/net/).
- Visual Studio: أي إصدار حديث سوف يعمل.
- المعرفة الأساسية بلغة C#: تعتبر المعرفة ببرمجة C# أمرًا ضروريًا.
- مستند نموذجي: قم بإعداد مستند Word يحتوي على جدول، أو يمكنك استخدام المستند المقدم في مثال الكود.

## استيراد مساحات الأسماء

أولاً وقبل كل شيء، دعنا نستورد مساحات الأسماء الضرورية. سيضمن هذا أن جميع الفئات والطرق المطلوبة متاحة للاستخدام في الكود الخاص بنا.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

الآن، دعونا نقوم بتقسيم العملية إلى خطوات بسيطة وسهلة المتابعة.

## الخطوة 1: قم بتحميل مستندك

في هذه الخطوة، سنقوم بتحميل مستند Word الذي يحتوي على الجدول الذي تريد تنسيقه. 

```csharp
// المسار إلى دليل المستند الخاص بك
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Tables.docx");
```

## الخطوة 2: الوصول إلى الجدول

بعد ذلك، نحتاج إلى الوصول إلى الجدول الأول في المستند. سيكون هذا الجدول هو محور عمليات التنسيق لدينا.

```csharp
// احصل على الجدول الأول في الوثيقة.
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## الخطوة 3: استرداد الخلية الأولى

الآن، لنسترد الخلية الأولى من الصف الأول في الجدول. سيساعدنا هذا في توضيح كيفية تغير تنسيق الخلية عند توسيع الأنماط.

```csharp
// احصل على الخلية الأولى من الصف الأول في الجدول.
Cell firstCell = table.FirstRow.FirstCell;
```

## الخطوة 4: التحقق من تظليل الخلية الأولي

قبل تطبيق أي تنسيق، دعنا نتحقق من لون التظليل الأولي للخلية ونطبعه. سيوفر لنا هذا خط الأساس للمقارنة به بعد توسيع النمط.

```csharp
// اطبع لون تظليل الخلية الأولي.
Color cellShadingBefore = firstCell.CellFormat.Shading.BackgroundPatternColor;
Console.WriteLine("Cell shading before style expansion: " + cellShadingBefore);
```

## الخطوة 5: توسيع أنماط الجدول

 وهنا يحدث السحر. سنسميه`ExpandTableStylesToDirectFormatting` طريقة لتطبيق أنماط الجدول مباشرة على الخلايا.

```csharp
// توسيع أنماط الجدول لتوجيه التنسيق.
doc.ExpandTableStylesToDirectFormatting();
```

## الخطوة 6: التحقق من تظليل الخلية النهائي

أخيرًا، سنتحقق من لون تظليل الخلية ونطبعه بعد توسيع الأنماط. يجب أن ترى التنسيق المحدث المطبق من نمط الجدول.

```csharp
// اطبع لون تظليل الخلية بعد توسيع النمط.
Color cellShadingAfter = firstCell.CellFormat.Shading.BackgroundPatternColor;
Console.WriteLine("Cell shading after style expansion: " + cellShadingAfter);
```

## خاتمة

والآن، إليك ما تريد! باتباع هذه الخطوات، يمكنك بسهولة توسيع التنسيق في الخلايا والصفوف من الأنماط الموجودة في مستندات Word باستخدام Aspose.Words for .NET. وهذا لا يوفر الوقت فحسب، بل يضمن أيضًا الاتساق عبر مستنداتك. استمتع بالبرمجة!

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟
Aspose.Words for .NET عبارة عن واجهة برمجة تطبيقات قوية تتيح للمطورين إنشاء مستندات Word وتحريرها وتحويلها ومعالجتها برمجيًا.

### لماذا أحتاج إلى توسيع التنسيق من الأنماط؟
يضمن توسيع التنسيق من الأنماط تطبيق التصميم مباشرة على الخلايا، مما يجعل من الأسهل صيانة المستند وتحديثه.

### هل يمكنني تطبيق هذه الخطوات على جداول متعددة في مستند واحد؟
بالتأكيد! يمكنك تكرار كل الجداول في مستندك وتطبيق نفس الخطوات على كل منها.

### هل هناك طريقة لإرجاع الأنماط الموسعة؟
بمجرد توسيع الأنماط، يتم تطبيقها مباشرة على الخلايا. وللرجوع إلى الوضع السابق، ستحتاج إلى إعادة تحميل المستند أو إعادة تطبيق الأنماط يدويًا.

### هل تعمل هذه الطريقة مع جميع إصدارات Aspose.Words لـ .NET؟
 نعم،`ExpandTableStylesToDirectFormatting` تتوفر الطريقة في الإصدارات الحديثة من Aspose.Words لـ .NET. تحقق دائمًا من[التوثيق](https://reference.aspose.com/words/net/) للحصول على آخر التحديثات.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
