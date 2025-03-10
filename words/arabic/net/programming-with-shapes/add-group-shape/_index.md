---
title: إضافة شكل المجموعة
linktitle: إضافة شكل المجموعة
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إضافة أشكال المجموعة إلى مستندات Word باستخدام Aspose.Words for .NET من خلال هذا البرنامج التعليمي الشامل خطوة بخطوة.
weight: 10
url: /ar/net/programming-with-shapes/add-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إضافة شكل المجموعة

## مقدمة

إن إنشاء مستندات معقدة تحتوي على عناصر مرئية غنية قد يكون مهمة شاقة في بعض الأحيان، وخاصة عند التعامل مع أشكال المجموعات. ولكن لا تقلق! يعمل برنامج Aspose.Words for .NET على تبسيط هذه العملية، مما يجعلها سهلة للغاية. في هذا البرنامج التعليمي، سنوضح لك الخطوات اللازمة لإضافة أشكال المجموعات إلى مستندات Word. هل أنت مستعد للبدء؟ لنبدأ!

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك ما يلي:

1.  Aspose.Words for .NET: يمكنك تنزيله من[صفحة إصدارات Aspose](https://releases.aspose.com/words/net/).
2. بيئة التطوير: Visual Studio أو أي بيئة تطوير متكاملة أخرى متوافقة مع .NET.
3. الفهم الأساسي للغة C#: المعرفة ببرمجة C# تعتبر ميزة إضافية.

## استيراد مساحات الأسماء

للبدء، نحتاج إلى استيراد المساحات الأساسية اللازمة في مشروعنا. توفر هذه المساحات الأساسية الوصول إلى الفئات والطرق المطلوبة لمعالجة مستندات Word باستخدام Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## الخطوة 1: تهيئة المستند

أولاً وقبل كل شيء، دعنا ننشئ مستند Word جديدًا. فكر في هذا الأمر باعتباره إنشاء لوحة قماشية فارغة حيث سنضيف أشكال مجموعتنا.

```csharp
// المسار إلى دليل المستند الخاص بك
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
doc.EnsureMinimum();
```

 هنا،`EnsureMinimum()` يضيف مجموعة صغيرة من العقد المطلوبة للمستند.

## الخطوة 2: إنشاء كائن GroupShape

 بعد ذلك، نحتاج إلى إنشاء`GroupShape`هذا الكائن. سيعمل هذا الكائن كحاوية للأشكال الأخرى، مما يسمح لنا بتجميعها معًا.

```csharp
GroupShape groupShape = new GroupShape(doc);
```

## الخطوة 3: إضافة الأشكال إلى GroupShape

 الآن، دعنا نضيف أشكالاً فردية إلى`GroupShape` الحاوية. سنبدأ بشكل حدود مميزة ثم نضيف شكل زر إجراء.

### إضافة شكل حدود مميز

```csharp
Shape accentBorderShape = new Shape(doc, ShapeType.AccentBorderCallout1)
{
    Width = 100,
    Height = 100
};
groupShape.AppendChild(accentBorderShape);
```

 يقوم مقتطف التعليمات البرمجية هذا بإنشاء شكل حدود مميز بعرض وارتفاع 100 وحدة وإضافته إلى`GroupShape`.

### إضافة شكل زر الإجراء

```csharp
Shape actionButtonShape = new Shape(doc, ShapeType.ActionButtonBeginning)
{
    Left = 100,
    Width = 100,
    Height = 200
};
groupShape.AppendChild(actionButtonShape);
```

 هنا، نقوم بإنشاء شكل زر الإجراء، ووضعه، وإضافته إلى`GroupShape`.

## الخطوة 4: تحديد أبعاد GroupShape

 لضمان أن تتناسب أشكالنا بشكل جيد داخل المجموعة، نحتاج إلى ضبط أبعاد`GroupShape`.

```csharp
groupShape.Width = 200;
groupShape.Height = 200;
groupShape.CoordSize = new Size(200, 200);
```

 يحدد هذا العرض والارتفاع`GroupShape` كـ 200 وحدة ويتم ضبط حجم الإحداثيات وفقًا لذلك.

## الخطوة 5: إدراج GroupShape في المستند

 الآن، دعونا ندخل`GroupShape` في المستند باستخدام`DocumentBuilder`.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.InsertNode(groupShape);
```

`DocumentBuilder` يوفر طريقة سهلة لإضافة العقد، بما في ذلك الأشكال، إلى المستند.

## الخطوة 6: حفظ المستند

وأخيرًا، قم بحفظ المستند في الدليل المحدد.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddGroupShape.docx");
```

وها أنت ذا قد انتهيت! مستندك الذي يحتوي على أشكال المجموعة أصبح جاهزًا.

## خاتمة

لا يلزم أن تكون إضافة أشكال المجموعات إلى مستندات Word عملية معقدة. باستخدام Aspose.Words for .NET، يمكنك إنشاء الأشكال والتلاعب بها بسهولة، مما يجعل مستنداتك أكثر جاذبية من الناحية البصرية ووظيفية. اتبع الخطوات الموضحة في هذا البرنامج التعليمي، وستصبح محترفًا في وقت قصير!

## الأسئلة الشائعة

### هل يمكنني إضافة أكثر من شكلين إلى GroupShape؟
 نعم، يمكنك إضافة عدد الأشكال التي تحتاجها إلى`GroupShape` . فقط استخدم`AppendChild` طريقة لكل شكل.

### هل من الممكن تصميم الأشكال داخل GroupShape؟
 بالتأكيد! يمكن تصميم كل شكل على حدة باستخدام الخصائص المتوفرة في`Shape` فصل.

### كيف أقوم بوضع GroupShape داخل المستند؟
 يمكنك وضع`GroupShape` من خلال ضبطها`Left` و`Top` ملكيات.

### هل يمكنني إضافة نص إلى الأشكال الموجودة داخل GroupShape؟
 نعم، يمكنك إضافة نص إلى الأشكال باستخدام`AppendChild` طريقة إضافة`Paragraph` يحتوي على`Run` العقد مع النص.

### هل من الممكن تجميع الأشكال بشكل ديناميكي استنادًا إلى إدخال المستخدم؟
نعم، يمكنك إنشاء الأشكال وتجميعها بشكل ديناميكي استنادًا إلى إدخال المستخدم عن طريق ضبط الخصائص والطرق وفقًا لذلك.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
