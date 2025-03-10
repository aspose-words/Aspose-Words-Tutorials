---
title: نوع التحكم المفضل في مستند Word
linktitle: نوع التحكم المفضل في مستند Word
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إدراج حقل نموذج مربع التحرير والسرد في مستند Word باستخدام Aspose.Words for .NET. اتبع هذا الدليل خطوة بخطوة للتكامل السلس لمحتوى HTML.
weight: 10
url: /ar/net/programming-with-htmlloadoptions/preferred-control-type/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# نوع التحكم المفضل في مستند Word

## مقدمة

سنبدأ في درس تعليمي مثير حول كيفية العمل مع خيارات تحميل HTML في Aspose.Words for .NET، مع التركيز بشكل خاص على تعيين نوع التحكم المفضل عند إدراج حقل نموذج مربع التحرير والسرد في مستند Word. سيساعدك هذا الدليل التفصيلي على فهم كيفية التعامل مع محتوى HTML وعرضه بفعالية داخل مستندات Word باستخدام Aspose.Words for .NET.

## المتطلبات الأساسية

قبل أن ننتقل إلى الكود، هناك بعض الأشياء التي تحتاج إلى وضعها في مكانها:

1.  Aspose.Words for .NET: تأكد من تثبيت مكتبة Aspose.Words for .NET. يمكنك تنزيلها من[موقع إلكتروني](https://releases.aspose.com/words/net/).
2. بيئة التطوير: يجب أن يكون لديك بيئة تطوير تم إعدادها، مثل Visual Studio.
3. المعرفة الأساسية بلغة C#: من الضروري أن يكون لديك فهم أساسي لبرمجة C# لمتابعة البرنامج التعليمي.
4. محتوى HTML: المعرفة الأساسية بلغة HTML مفيدة لأننا سنعمل مع محتوى HTML في هذا المثال.

## استيراد مساحات الأسماء

أولاً، دعنا نستورد مساحات الأسماء اللازمة للبدء:

```csharp
using System;
using System.IO;
using System.Text;
using Aspose.Words;
using Aspose.Words.Loading;
```

الآن، دعونا نقسم المثال إلى خطوات متعددة لضمان الوضوح والفهم.

## الخطوة 1: إعداد محتوى HTML الخاص بك

أولاً، نحتاج إلى تحديد محتوى HTML الذي نريد إدراجه في مستند Word. إليك مقتطف HTML الذي سنستخدمه:

```csharp
const string html = @"
    <html>
        <select name='ComboBox' size='1'>
            <option value='val1'>item1</option>
            <option value='val2'></option>                        
        </select>
    </html>
";
```

يحتوي هذا النص HTML على مربع تركيبة بسيط به خياران. سنقوم بتحميل هذا النص HTML إلى مستند Word وتحديد كيفية عرضه.

## الخطوة 2: تحديد دليل المستندات

بعد ذلك، حدد الدليل الذي سيتم حفظ مستند Word فيه. يساعد هذا في تنظيم ملفاتك والحفاظ على إدارة المسار نظيفة.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 يستبدل`"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي الذي تريد حفظ مستند Word الخاص بك فيه.

## الخطوة 3: تكوين خيارات تحميل HTML

 هنا، نقوم بتكوين خيارات تحميل HTML، مع التركيز بشكل خاص على`PreferredControlType`الخاصية. يحدد هذا كيفية عرض المربع المنسدل في مستند Word.

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions { PreferredControlType = HtmlControlType.StructuredDocumentTag };
```

 عن طريق الإعداد`PreferredControlType` ل`HtmlControlType.StructuredDocumentTag`نحن نضمن أن يتم عرض المربع المنسدل كعلامة مستند منظم (SDT) في مستند Word.

## الخطوة 4: تحميل محتوى HTML إلى المستند

باستخدام خيارات التحميل المخصصة، نقوم بتحميل محتوى HTML إلى مستند Word جديد.

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(html)), loadOptions);
```

هنا، نقوم بتحويل سلسلة HTML إلى مصفوفة بايتات وتحميلها في المستند باستخدام دفق ذاكرة. وهذا يضمن أن يتم تفسير محتوى HTML بشكل صحيح وتقديمه بواسطة Aspose.Words.

## الخطوة 5: احفظ المستند

وأخيرًا، قم بحفظ المستند في الدليل المحدد بتنسيق DOCX.

```csharp
doc.Save(dataDir + "WorkingWithHtmlLoadOptions.PreferredControlType.docx", SaveFormat.Docx);
```

يؤدي هذا إلى حفظ مستند Word مع عنصر التحكم في المربع المنسدل المقدم في الموقع المحدد.

## خاتمة

والآن، لقد نجحنا في إدراج حقل نموذج مربع التحرير والسرد في مستند Word باستخدام Aspose.Words for .NET من خلال الاستفادة من خيارات تحميل HTML. سيساعدك هذا الدليل التفصيلي على فهم العملية وتطبيقها على مشاريعك. سواء كنت تقوم بأتمتة إنشاء المستندات أو معالجة محتوى HTML، فإن Aspose.Words for .NET يوفر أدوات قوية لتحقيق أهدافك.

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟
Aspose.Words for .NET هي مكتبة قوية لمعالجة المستندات تتيح للمطورين إنشاء مستندات Word وتحريرها وتحويلها وعرضها برمجيًا.

### هل يمكنني استخدام أنواع أخرى من عناصر التحكم HTML مع Aspose.Words لـ .NET؟
نعم، يدعم Aspose.Words for .NET أنواعًا مختلفة من عناصر التحكم HTML. يمكنك تخصيص كيفية عرض عناصر التحكم المختلفة في مستند Word.

### كيف أتعامل مع محتوى HTML المعقد في Aspose.Words لـ .NET؟
 يوفر Aspose.Words for .NET دعمًا شاملاً لـ HTML، بما في ذلك العناصر المعقدة. تأكد من تكوين`HtmlLoadOptions`للتعامل بشكل مناسب مع محتوى HTML الخاص بك.

### أين يمكنني العثور على المزيد من الأمثلة والوثائق؟
 يمكنك العثور على وثائق وأمثلة مفصلة على[صفحة توثيق Aspose.Words لـ .NET](https://reference.aspose.com/words/net/).

### هل هناك نسخة تجريبية مجانية متاحة لـ Aspose.Words لـ .NET؟
 نعم، يمكنك تنزيل نسخة تجريبية مجانية من[موقع اسبوس](https://releases.aspose.com/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
