---
"description": "تعرف على كيفية إدراج FieldIncludeText دون استخدام DocumentBuilder في Aspose.Words for .NET باستخدام دليلنا المفصل خطوة بخطوة."
"linktitle": "إدراج FieldIncludeText بدون منشئ المستندات"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "إدراج حقل تضمين النص بدون منشئ المستندات"
"url": "/ar/net/working-with-fields/insert-field-include-text-without-document-builder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# إدراج حقل تضمين النص بدون منشئ المستندات

## مقدمة

في عالم أتمتة المستندات ومعالجتها، يُعدّ Aspose.Words for .NET أداةً فعّالة. اليوم، نستعرض دليلاً مُفصّلاً حول كيفية إدراج نص FieldIncludeText دون استخدام DocumentBuilder. سيشرح هذا البرنامج التعليمي العملية خطوة بخطوة، لضمان فهمك لكل جزء من الشيفرة البرمجية والغرض منها.

## المتطلبات الأساسية

قبل أن نتعمق في الكود، دعنا نتأكد من أن لديك كل ما تحتاجه:

1. Aspose.Words لـ .NET: تأكد من تثبيت أحدث إصدار. يمكنك تنزيله من [هنا](https://releases.aspose.com/words/net/).
2. بيئة تطوير .NET: أي بيئة تطوير متكاملة متوافقة مع .NET مثل Visual Studio.
3. المعرفة الأساسية بلغة C#: ستساعدك المعرفة ببرمجة C# على المتابعة.

## استيراد مساحات الأسماء

أولاً، علينا استيراد مساحات الأسماء اللازمة. تتيح هذه المساحات الوصول إلى الفئات والأساليب اللازمة لمعالجة مستندات Word.

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
```

الآن، لنُقسّم المثال إلى عدة خطوات. سيتم شرح كل خطوة بالتفصيل لضمان الوضوح.

## الخطوة 1: تعيين مسار الدليل

الخطوة الأولى هي تحديد مسار مجلد المستندات. هنا سيتم تخزين مستندات Word والوصول إليها.

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

## الخطوة 2: إنشاء المستند والفقرة

بعد ذلك، ننشئ مستندًا جديدًا وفقرةً داخله. ستحتوي هذه الفقرة على حقل "نص تضمين الحقل".

```csharp
// إنشاء المستند والفقرة.
Document doc = new Document();
Paragraph para = new Paragraph(doc);
```

## الخطوة 3: إدراج حقل FieldIncludeText

الآن، نُدرج حقل "FieldIncludeText" في الفقرة. يسمح لك هذا الحقل بتضمين نص من مستند آخر.

```csharp
// إدراج حقل FieldIncludeText.
FieldIncludeText fieldIncludeText = (FieldIncludeText)para.AppendField(FieldType.FieldIncludeText, false);
```

## الخطوة 4: تعيين خصائص الحقل

نحتاج إلى تحديد خصائص حقل "FieldIncludeText". يتضمن ذلك تحديد اسم الإشارة المرجعية والمسار الكامل للمستند المصدر.

```csharp
fieldIncludeText.BookmarkName = "bookmark";
fieldIncludeText.SourceFullName = dataDir + "IncludeText.docx";
```

## الخطوة 5: إضافة فقرة إلى المستند

بعد إعداد الحقل، نضيف الفقرة إلى نص القسم الأول من المستند.

```csharp
doc.FirstSection.Body.AppendChild(para);
```

## الخطوة 6: تحديث الحقل

قبل حفظ المستند، نحتاج إلى تحديث FieldIncludeText للتأكد من أنه يسحب المحتوى الصحيح من المستند المصدر.

```csharp
fieldIncludeText.Update();
```

## الخطوة 7: حفظ المستند

وأخيرًا، نقوم بحفظ المستند في الدليل المحدد.

```csharp
doc.Save(dataDir + "InsertionFieldFieldIncludeTextWithoutDocumentBuilder.docx");
```

## خاتمة

وهكذا تكون قد انتهيت! باتباع هذه الخطوات، يمكنك بسهولة إدراج نص FieldIncludeText دون استخدام DocumentBuilder في Aspose.Words لـ .NET. يوفر هذا النهج طريقة مبسطة لتضمين محتوى من مستند إلى آخر، مما يُبسط مهام أتمتة المستندات بشكل كبير.

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟  
Aspose.Words for .NET هي مكتبة فعّالة للعمل مع مستندات Word في تطبيقات .NET. تتيح لك إنشاء المستندات وتحريرها وتحويلها برمجيًا.

### لماذا تستخدم FieldIncludeText؟  
يُعد FieldIncludeText مفيدًا لإدراج المحتوى بشكل ديناميكي من مستند إلى آخر، مما يتيح مستندات أكثر قابلية للتعديل والصيانة.

### هل يمكنني استخدام هذه الطريقة لتضمين نص من تنسيقات ملفات أخرى؟  
يعمل FieldIncludeText خصيصًا مع مستندات Word. بالنسبة للتنسيقات الأخرى، قد تحتاج إلى أساليب أو فئات مختلفة يوفرها Aspose.Words.

### هل Aspose.Words for .NET متوافق مع .NET Core؟  
نعم، يدعم Aspose.Words لـ .NET .NET Framework، و.NET Core، و.NET 5/6.

### كيف يمكنني الحصول على نسخة تجريبية مجانية من Aspose.Words لـ .NET؟  
يمكنك الحصول على نسخة تجريبية مجانية من [هنا](https://releases.aspose.com/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}