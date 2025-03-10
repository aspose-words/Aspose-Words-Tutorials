---
title: مراجعة الشكل
linktitle: مراجعة الشكل
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية التعامل مع تعديلات الأشكال في مستندات Word باستخدام Aspose.Words for .NET من خلال هذا الدليل الشامل. أتقن تتبع التغييرات وإدراج الأشكال والمزيد.
weight: 10
url: /ar/net/working-with-revisions/shape-revision/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# مراجعة الشكل

## مقدمة

قد يكون تحرير مستندات Word برمجيًا مهمة شاقة، خاصة عندما يتعلق الأمر بالتعامل مع الأشكال. سواء كنت تقوم بإنشاء تقارير أو تصميم قوالب أو أتمتة إنشاء المستندات ببساطة، فإن القدرة على تتبع وإدارة مراجعات الأشكال أمر بالغ الأهمية. يوفر Aspose.Words for .NET واجهة برمجة تطبيقات قوية لجعل هذه العملية سلسة وفعالة. في هذا البرنامج التعليمي، سنتعمق في تفاصيل مراجعة الأشكال في مستندات Word، مما يضمن حصولك على الأدوات والمعرفة اللازمة لإدارة مستنداتك بسهولة.

## المتطلبات الأساسية

قبل أن نتعمق في الكود، دعنا نتأكد من أن لديك كل ما تحتاجه:

-  Aspose.Words لـ .NET: تأكد من تثبيت مكتبة Aspose.Words. يمكنك[تحميله هنا](https://releases.aspose.com/words/net/).
- بيئة التطوير: يجب أن يكون لديك بيئة تطوير تم إعدادها، مثل Visual Studio.
- الفهم الأساسي للغة C#: الإلمام بلغة البرمجة C# والمفاهيم الأساسية للبرمجة الموجهة للكائنات.
- مستند Word: مستند Word للعمل عليه، أو يمكنك إنشاء واحد أثناء البرنامج التعليمي.

## استيراد مساحات الأسماء

أولاً، دعنا نستورد مساحات الأسماء الضرورية. ستتيح لنا هذه المساحات الوصول إلى الفئات والطرق المطلوبة للتعامل مع مستندات Word والأشكال.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## الخطوة 1: إعداد دليل المستندات الخاص بك

قبل أن نبدأ العمل بالأشكال، نحتاج إلى تحديد المسار إلى دليل المستندات. هذا هو المكان الذي سنحفظ فيه المستندات المعدلة.

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## الخطوة 2: إنشاء مستند جديد

لنقم بإنشاء مستند Word جديد حيث سنقوم بإدراج الأشكال ومراجعتها.

```csharp
Document doc = new Document();
```

## الخطوة 3: إدراج شكل مضمن

سنبدأ بإدراج شكل مضمّن في مستندنا دون تتبع المراجعات. الشكل المضمّن هو الشكل الذي يتدفق مع النص.

```csharp
Shape shape = new Shape(doc, ShapeType.Cube);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## الخطوة 4: البدء في تتبع المراجعات

لتتبع التغييرات في مستندنا، نحتاج إلى تمكين تتبع المراجعة. وهذا ضروري لتحديد التعديلات التي تم إجراؤها على الأشكال.

```csharp
doc.StartTrackRevisions("John Doe");
```

## الخطوة 5: إدراج شكل آخر باستخدام المراجعات

الآن بعد تمكين تتبع المراجعة، دعنا ندرج شكلاً آخر. هذه المرة، سيتم تتبع أي تغييرات.

```csharp
shape = new Shape(doc, ShapeType.Sun);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## الخطوة 6: استرداد الأشكال وتعديلها

يمكننا استرجاع كافة الأشكال الموجودة في المستند وتعديلها حسب الحاجة. هنا، سنحصل على الأشكال ونزيل الشكل الأول.

```csharp
List<Shape> shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
shapes[0].Remove();
```

## الخطوة 7: حفظ المستند

بعد إجراء التغييرات، نحتاج إلى حفظ المستند. وهذا يضمن تخزين كافة المراجعات والتعديلات.

```csharp
doc.Save(dataDir + "Revision shape.docx");
```

## الخطوة 8: التعامل مع مراجعات تحريك الشكل

عند تحريك شكل، يتتبع Aspose.Words هذا باعتباره مراجعة. وهذا يعني أنه سيكون هناك مثيلان للشكل: واحد في موقعه الأصلي وواحد في موقعه الجديد.

```csharp
doc = new Document(dataDir + "Revision shape.docx");
shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
```

## خاتمة

والآن، لقد تعلمت بنجاح كيفية التعامل مع مراجعات الأشكال في مستندات Word باستخدام Aspose.Words for .NET. سواء كنت تدير قوالب المستندات أو تقوم بأتمتة التقارير أو تتبع التغييرات ببساطة، فإن هذه المهارات لا تقدر بثمن. باتباع هذا الدليل التفصيلي، لم تتقن الأساسيات فحسب، بل اكتسبت أيضًا نظرة ثاقبة لتقنيات التعامل مع المستندات الأكثر تقدمًا.

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟
Aspose.Words for .NET هي مكتبة قوية تسمح للمطورين بإنشاء وتعديل وتحويل مستندات Word برمجيًا باستخدام C#.

### هل يمكنني تتبع التغييرات التي أجريت على عناصر أخرى في مستند Word؟
نعم، يدعم Aspose.Words for .NET تتبع التغييرات على عناصر مختلفة، بما في ذلك النصوص والجداول والمزيد.

### كيف يمكنني الحصول على نسخة تجريبية مجانية من Aspose.Words لـ .NET؟
 يمكنك الحصول على نسخة تجريبية مجانية من Aspose.Words لـ .NET[هنا](https://releases.aspose.com/).

### هل من الممكن قبول أو رفض المراجعات برمجيا؟
نعم، يوفر Aspose.Words لـ .NET طرقًا لقبول أو رفض المراجعات برمجيًا.

### هل يمكنني استخدام Aspose.Words لـ .NET مع لغات .NET أخرى بالإضافة إلى C#؟
بالتأكيد! يمكن استخدام Aspose.Words for .NET مع أي لغة .NET، بما في ذلك VB.NET وF#.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
