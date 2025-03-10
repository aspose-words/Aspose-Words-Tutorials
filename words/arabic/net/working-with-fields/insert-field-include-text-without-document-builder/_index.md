---
title: إدراج حقل يتضمن نصًا بدون منشئ المستندات
linktitle: إدراج FieldIncludeText بدون منشئ المستندات
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إدراج FieldIncludeText دون استخدام DocumentBuilder في Aspose.Words لـ .NET من خلال دليلنا المفصل خطوة بخطوة.
weight: 10
url: /ar/net/working-with-fields/insert-field-include-text-without-document-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إدراج حقل يتضمن نصًا بدون منشئ المستندات

## مقدمة

في عالم أتمتة المستندات ومعالجتها، يعد Aspose.Words for .NET أداة قوية. اليوم، سنتناول دليلاً مفصلاً حول كيفية إدراج FieldIncludeText دون استخدام DocumentBuilder. سيرشدك هذا البرنامج التعليمي خلال العملية خطوة بخطوة، مما يضمن فهمك لكل جزء من الكود والغرض منه.

## المتطلبات الأساسية

قبل أن نتعمق في الكود، دعنا نتأكد من أن لديك كل ما تحتاجه:

1.  Aspose.Words for .NET: تأكد من تثبيت أحدث إصدار. يمكنك تنزيله من[هنا](https://releases.aspose.com/words/net/).
2. بيئة تطوير .NET: أي بيئة تطوير متكاملة متوافقة مع .NET مثل Visual Studio.
3. المعرفة الأساسية بلغة C#: ستساعدك المعرفة ببرمجة C# على المتابعة.

## استيراد مساحات الأسماء

أولاً وقبل كل شيء، نحتاج إلى استيراد مساحات الأسماء الضرورية. توفر هذه المساحات الأسماء الوصول إلى الفئات والطرق المطلوبة للتعامل مع مستندات Word.

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
```

الآن، دعنا نقسم المثال إلى عدة خطوات. سيتم شرح كل خطوة بالتفصيل لضمان الوضوح.

## الخطوة 1: تعيين مسار الدليل

الخطوة الأولى هي تحديد المسار إلى دليل المستندات الخاص بك. هذا هو المكان الذي سيتم فيه تخزين مستندات Word الخاصة بك والوصول إليها.

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

## الخطوة 2: إنشاء المستند والفقرة

بعد ذلك، نقوم بإنشاء مستند جديد وفقرة داخل هذا المستند. ستحتوي هذه الفقرة على الحقل FieldIncludeText.

```csharp
// إنشاء المستند والفقرة.
Document doc = new Document();
Paragraph para = new Paragraph(doc);
```

## الخطوة 3: إدراج حقل "FieldIncludeText"

الآن، نقوم بإدراج الحقل FieldIncludeText في الفقرة. يسمح لك هذا الحقل بإدراج النص من مستند آخر.

```csharp
// إدراج حقل FieldIncludeText.
FieldIncludeText fieldIncludeText = (FieldIncludeText)para.AppendField(FieldType.FieldIncludeText, false);
```

## الخطوة 4: تعيين خصائص الحقل

نحن بحاجة إلى تحديد خصائص الحقل FieldIncludeText. ويتضمن ذلك تعيين اسم الإشارة المرجعية والمسار الكامل للمستند المصدر.

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

وأخيرا، نقوم بحفظ المستند في الدليل المحدد.

```csharp
doc.Save(dataDir + "InsertionFieldFieldIncludeTextWithoutDocumentBuilder.docx");
```

## خاتمة

والآن، إليك ما تريد! باتباع هذه الخطوات، يمكنك بسهولة إدراج FieldIncludeText دون استخدام DocumentBuilder في Aspose.Words for .NET. يوفر هذا النهج طريقة مبسطة لتضمين المحتوى من مستند إلى آخر، مما يجعل مهام أتمتة المستندات الخاصة بك أبسط كثيرًا.

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟  
Aspose.Words for .NET هي مكتبة قوية للعمل مع مستندات Word في تطبيقات .NET. وهي تسمح بإنشاء المستندات وتحريرها وتحويلها برمجيًا.

### لماذا استخدام FieldIncludeText؟  
يعد FieldIncludeText مفيدًا لتضمين المحتوى بشكل ديناميكي من مستند إلى آخر، مما يتيح مستندات أكثر قابلية للتعديل والصيانة.

### هل يمكنني استخدام هذه الطريقة لتضمين نص من تنسيقات ملفات أخرى؟  
يعمل FieldIncludeText بشكل خاص مع مستندات Word. بالنسبة للتنسيقات الأخرى، قد تحتاج إلى طرق أو فئات مختلفة يوفرها Aspose.Words.

### هل Aspose.Words for .NET متوافق مع .NET Core؟  
نعم، يدعم Aspose.Words for .NET .NET Framework، و.NET Core، و.NET 5/6.

### كيف يمكنني الحصول على نسخة تجريبية مجانية من Aspose.Words لـ .NET؟  
 يمكنك الحصول على نسخة تجريبية مجانية من[هنا](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
