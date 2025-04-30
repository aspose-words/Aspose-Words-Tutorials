---
"description": "تعرّف على كيفية إدراج حقل نموذج مربع التحرير والسرد في مستند Word باستخدام Aspose.Words لـ .NET. اتبع هذا الدليل خطوة بخطوة لدمج محتوى HTML بسلاسة."
"linktitle": "نوع التحكم المفضل في مستند Word"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "نوع التحكم المفضل في مستند Word"
"url": "/ar/net/programming-with-htmlloadoptions/preferred-control-type/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# نوع التحكم المفضل في مستند Word

## مقدمة

سنبدأ درسًا شيقًا حول كيفية استخدام خيارات تحميل HTML في Aspose.Words لـ .NET، مع التركيز بشكل خاص على تحديد نوع عنصر التحكم المفضل عند إدراج حقل نموذج مربع التحرير والسرد في مستند Word. سيساعدك هذا الدليل التفصيلي على فهم كيفية معالجة محتوى HTML وعرضه بفعالية في مستندات Word باستخدام Aspose.Words لـ .NET.

## المتطلبات الأساسية

قبل أن ننتقل إلى الكود، هناك بعض الأشياء التي تحتاج إلى وضعها في مكانها:

1. Aspose.Words لـ .NET: تأكد من تثبيت مكتبة Aspose.Words لـ .NET. يمكنك تنزيلها من [موقع إلكتروني](https://releases.aspose.com/words/net/).
2. بيئة التطوير: يجب أن يكون لديك بيئة تطوير مهيأة، مثل Visual Studio.
3. المعرفة الأساسية بلغة C#: من الضروري أن يكون لديك فهم أساسي لبرمجة C# لمتابعة البرنامج التعليمي.
4. محتوى HTML: المعرفة الأساسية بلغة HTML مفيدة لأننا سنعمل مع محتوى HTML في هذا المثال.

## استيراد مساحات الأسماء

أولاً، دعنا نستورد مساحات الأسماء الضرورية للبدء:

```csharp
using System;
using System.IO;
using System.Text;
using Aspose.Words;
using Aspose.Words.Loading;
```

الآن، دعونا نقسم المثال إلى خطوات متعددة لضمان الوضوح والفهم.

## الخطوة 1: إعداد محتوى HTML الخاص بك

أولاً، علينا تحديد محتوى HTML الذي نريد إدراجه في مستند Word. إليك مقتطف HTML الذي سنستخدمه:

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

يحتوي هذا النص HTML على مربع حوار بسيط بخيارين. سنحمّل هذا النص HTML إلى مستند Word ونحدد كيفية عرضه.

## الخطوة 2: تحديد دليل المستندات

بعد ذلك، حدد المجلد الذي ستحفظ فيه مستند Word. سيساعدك هذا على تنظيم ملفاتك والحفاظ على إدارة مساراتها منظمة.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

يستبدل `"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي الذي تريد حفظ مستند Word الخاص بك فيه.

## الخطوة 3: تكوين خيارات تحميل HTML

هنا، نقوم بتكوين خيارات تحميل HTML، مع التركيز بشكل خاص على `PreferredControlType` الخاصية. تحدد هذه الخاصية كيفية عرض المربع المنسدل في مستند Word.

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions { PreferredControlType = HtmlControlType.StructuredDocumentTag };
```

عن طريق الإعداد `PreferredControlType` ل `HtmlControlType.StructuredDocumentTag`نحن نضمن أن يتم عرض المربع المنسدل كعلامة مستند منظمة (SDT) في مستند Word.

## الخطوة 4: تحميل محتوى HTML في المستند

باستخدام خيارات التحميل المحددة، نقوم بتحميل محتوى HTML إلى مستند Word جديد.

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(html)), loadOptions);
```

هنا، نُحوّل سلسلة HTML إلى مصفوفة بايتات، ونُحمّلها إلى المستند باستخدام تدفق ذاكرة. هذا يضمن تفسير محتوى HTML وعرضه بشكل صحيح بواسطة Aspose.Words.

## الخطوة 5: حفظ المستند

وأخيرًا، قم بحفظ المستند في الدليل المحدد بتنسيق DOCX.

```csharp
doc.Save(dataDir + "WorkingWithHtmlLoadOptions.PreferredControlType.docx", SaveFormat.Docx);
```

يؤدي هذا إلى حفظ مستند Word مع عنصر التحكم في المربع المنسدل في الموقع المحدد.

## خاتمة

وها قد انتهينا! نجحنا في إدراج حقل نموذج مربع التحرير والسرد في مستند Word باستخدام Aspose.Words لـ .NET، مستفيدين من خيارات تحميل HTML. سيساعدك هذا الدليل المفصل على فهم العملية وتطبيقها على مشاريعك. سواء كنت تُؤتمت إنشاء المستندات أو تُعالج محتوى HTML، يوفر Aspose.Words لـ .NET أدوات فعّالة لتحقيق أهدافك.

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟
Aspose.Words for .NET هي مكتبة قوية لمعالجة المستندات تسمح للمطورين بإنشاء مستندات Word وتحريرها وتحويلها وعرضها برمجيًا.

### هل يمكنني استخدام أنواع أخرى من عناصر التحكم HTML مع Aspose.Words لـ .NET؟
نعم، يدعم Aspose.Words for .NET أنواعًا مختلفة من عناصر تحكم HTML. يمكنك تخصيص طريقة عرض عناصر التحكم المختلفة في مستند Word.

### كيف يمكنني التعامل مع محتوى HTML المعقد في Aspose.Words لـ .NET؟
يوفر Aspose.Words for .NET دعمًا شاملاً لـ HTML، بما في ذلك العناصر المعقدة. تأكد من تكوين `HtmlLoadOptions` بشكل مناسب للتعامل مع محتوى HTML الخاص بك.

### أين يمكنني العثور على المزيد من الأمثلة والوثائق؟
يمكنك العثور على وثائق وأمثلة مفصلة على [صفحة توثيق Aspose.Words لـ .NET](https://reference.aspose.com/words/net/).

### هل هناك نسخة تجريبية مجانية متاحة لـ Aspose.Words لـ .NET؟
نعم، يمكنك تنزيل نسخة تجريبية مجانية من [موقع Aspose](https://releases.aspose.com/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}