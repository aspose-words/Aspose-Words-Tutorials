---
title: تطبيق حدود المخطط التفصيلي
linktitle: تطبيق حدود المخطط التفصيلي
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية تطبيق حدود تفصيلية على جدول في Word باستخدام Aspose.Words for .NET. اتبع دليلنا خطوة بخطوة لتنسيق الجدول بشكل مثالي.
weight: 10
url: /ar/net/programming-with-table-styles-and-formatting/apply-outline-border/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تطبيق حدود المخطط التفصيلي

## مقدمة

في درس اليوم، سنتعمق في عالم معالجة المستندات باستخدام Aspose.Words for .NET. على وجه التحديد، سنتعلم كيفية تطبيق حدود مخطط تفصيلي على جدول في مستند Word. هذه مهارة رائعة يجب أن تكون في مجموعة أدواتك إذا كنت تعمل بشكل متكرر مع إنشاء المستندات وتنسيقها تلقائيًا. لذا، فلنبدأ هذه الرحلة لجعل جداولك ليس فقط عملية ولكن أيضًا جذابة بصريًا.

## المتطلبات الأساسية

قبل أن ننتقل إلى الكود، هناك بعض الأشياء التي ستحتاجها:

1.  Aspose.Words for .NET: يجب أن يكون لديك Aspose.Words for .NET مثبتًا. يمكنك تنزيله[هنا](https://releases.aspose.com/words/net/).
2. بيئة التطوير: بيئة تطوير مناسبة مثل Visual Studio.
3. المعرفة الأساسية بلغة C#: إن الفهم الأساسي للغة C# سيساعدك على متابعة البرنامج التعليمي.

## استيراد مساحات الأسماء

للبدء، تأكد من استيراد مساحات الأسماء الضرورية. يعد هذا أمرًا بالغ الأهمية للوصول إلى وظائف Aspose.Words.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

دعونا نقسم العملية إلى خطوات بسيطة وقابلة للإدارة.

## الخطوة 1: تحميل المستند

أولاً، علينا تحميل مستند Word الذي يحتوي على الجدول الذي نريد تنسيقه.

```csharp
// المسار إلى دليل المستند الخاص بك
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Tables.docx");
```

 في هذه الخطوة، نستخدم`Document` استخدم فئة من Aspose.Words لتحميل مستند موجود. استبدل`"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي الذي يتم تخزين مستندك فيه.

## الخطوة 2: الوصول إلى الجدول

بعد ذلك، نحتاج إلى الوصول إلى الجدول المحدد الذي نريد تنسيقه. 

```csharp
Table table = (Table)doc.GetChild(NodeType.Table, 0, true);
```

 هنا،`GetChild` تقوم الطريقة بجلب الجدول الأول في المستند. المعلمات`NodeType.Table, 0, true` تأكد من أننا حصلنا على نوع العقدة الصحيح.

## الخطوة 3: محاذاة الجدول

الآن، دعونا نقوم بمحاذاة الجدول في منتصف الصفحة.

```csharp
table.Alignment = TableAlignment.Center;
```

تضمن هذه الخطوة أن يكون الجدول في المنتصف بشكل أنيق، مما يمنحه مظهرًا احترافيًا.

## الخطوة 4: مسح الحدود الموجودة

قبل أن نقوم بتطبيق حدود جديدة، علينا مسح أي حدود موجودة.

```csharp
table.ClearBorders();
```

إن إزالة الحدود تضمن تطبيق حدودنا الجديدة بشكل نظيف دون تداخل الأنماط القديمة.

## الخطوة 5: تعيين حدود المخطط التفصيلي

الآن، دعونا نطبق حدود المخطط الأخضر على الجدول.

```csharp
table.SetBorder(BorderType.Left, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Right, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Top, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Bottom, LineStyle.Single, 1.5, Color.Green, true);
```

 يتم تعيين كل نوع من أنواع الحدود (يسار، يمين، أعلى، أسفل) بشكل فردي. نستخدم`LineStyle.Single` لخط متصل،`1.5` لعرض الخط، و`Color.Green` للون الحدود.

## الخطوة 6: تطبيق تظليل الخلايا

لجعل الجدول أكثر جاذبية بصريًا، دعنا نملأ الخلايا باللون الأخضر الفاتح.

```csharp
table.SetShading(TextureIndex.TextureSolid, Color.LightGreen, Color.Empty);
```

 هنا،`SetShading` يتم استخدامه لتطبيق لون أخضر فاتح ثابت على الخلايا، مما يجعل الجدول بارزًا.

## الخطوة 7: حفظ المستند

وأخيرًا، احفظ المستند المعدّل.

```csharp
doc.Save(dataDir + "WorkingWithTableStylesAndFormatting.ApplyOutlineBorder.docx");
```

تحفظ هذه الخطوة مستندك بالتنسيق المطبق. ويمكنك فتحه لرؤية الجدول المنسق بشكل جميل.

## خاتمة

والآن، لقد انتهيت! باتباع هذه الخطوات، تكون قد نجحت في تطبيق حدود مخطط تفصيلي على جدول في مستند Word باستخدام Aspose.Words for .NET. وقد تناول هذا البرنامج التعليمي تحميل المستند، والوصول إلى الجدول، ومحاذاته، ومسح الحدود الموجودة، وتطبيق حدود جديدة، وإضافة تظليل الخلايا، وأخيرًا حفظ المستند. 

بفضل هذه المهارات، يمكنك تحسين العرض المرئي لجداولك، مما يجعل مستنداتك أكثر احترافية وجاذبية. استمتع بالبرمجة!

## الأسئلة الشائعة

### هل يمكنني تطبيق أنماط مختلفة على كل حدود الجدول؟  
 نعم، يمكنك تطبيق أنماط وألوان مختلفة على كل حد عن طريق ضبط المعلمات في`SetBorder` طريقة.

### كيف يمكنني تغيير عرض الحدود؟  
 يمكنك تغيير العرض عن طريق تعديل المعلمة الثالثة في`SetBorder` الطريقة. على سبيل المثال،`1.5` يحدد عرضًا بمقدار 1.5 نقطة.

### هل من الممكن تطبيق التظليل على الخلايا الفردية؟  
 نعم، يمكنك تطبيق التظليل على الخلايا الفردية عن طريق الوصول إلى كل خلية واستخدام`SetShading` طريقة.

### هل يمكنني استخدام ألوان أخرى للحدود والتظليل؟  
 بالتأكيد! يمكنك استخدام أي لون متوفر في`System.Drawing.Color` فصل.

### كيف أقوم بمحاذاة الجدول أفقياً؟  
 ال`table.Alignment = TableAlignment.Center;` يقوم السطر الموجود في الكود بمركز الجدول أفقياً على الصفحة.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
