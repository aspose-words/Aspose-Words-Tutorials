---
title: استدعاء الوصلة
linktitle: استدعاء الوصلة
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعلم كيفية تنفيذ استدعاء الواصلة في Aspose.Words for .NET لتحسين تنسيق المستندات باستخدام هذا الدليل الشامل خطوة بخطوة.
weight: 10
url: /ar/net/working-with-hyphenation/hyphenation-callback/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# استدعاء الوصلة


## مقدمة

مرحبًا! هل وجدت نفسك متورطًا في تعقيدات تنسيق النص، وخاصة عند التعامل مع اللغات التي تتطلب الوصل بين السطور؟ لست وحدك. فالوصل بين السطور، على الرغم من أهميته لتخطيط النص بشكل صحيح، قد يكون أمرًا مزعجًا بعض الشيء. ولكن ماذا تتوقع؟ توفر لك Aspose.Words for .NET الدعم. تتيح لك هذه المكتبة القوية إدارة تنسيق النص بسلاسة، بما في ذلك التعامل مع الوصل بين السطور من خلال آلية استدعاء. هل أنت مهتم؟ دعنا نتعمق في التفاصيل الدقيقة لكيفية تنفيذ استدعاء الوصل بين السطور باستخدام Aspose.Words for .NET.

## المتطلبات الأساسية

قبل أن نبدأ في التعامل مع التعليمات البرمجية، دعونا نتأكد من أنك حصلت على كل ما تحتاجه:

1. Aspose.Words for .NET: تأكد من أن لديك المكتبة. يمكنك[تحميله هنا](https://releases.aspose.com/words/net/).
2. IDE: بيئة تطوير مثل Visual Studio.
3. المعرفة الأساسية بلغة C#: فهم لغة C# وإطار عمل .NET.
4. قواميس الوصل: قواميس الوصل للغات التي تخطط لاستخدامها.
5.  ترخيص Aspose: ترخيص Aspose صالح. يمكنك الحصول على[رخصة مؤقتة](https://purchase.aspose.com/temporary-license/) إذا لم يكن لديك واحدة.

## استيراد مساحات الأسماء

أولاً وقبل كل شيء، دعنا نستورد مساحات الأسماء الضرورية. وهذا يضمن أن الكود الخاص بنا لديه إمكانية الوصول إلى جميع الفئات والطرق التي نحتاجها من Aspose.Words.

```csharp
using Aspose.Words;
using System;
using System.IO;
```

## الخطوة 1: تسجيل استدعاء التهجئة

للبدء، نحتاج إلى تسجيل استدعاء التهجئة. هنا نخبر Aspose.Words باستخدام منطق التهجئة المخصص لدينا.

```csharp
try
{
    // تسجيل استدعاء الوصلة.
    Hyphenation.Callback = new CustomHyphenationCallback();
}
catch (Exception e)
{
    Console.WriteLine($"Error registering hyphenation callback: {e.Message}");
}
```

 هنا، نقوم بإنشاء مثيل لاستدعاء مخصص لدينا وتعيينه إلى`Hyphenation.Callback`.

## الخطوة 2: تحديد مسار المستند

بعد ذلك، نحتاج إلى تحديد الدليل الذي سيتم تخزين مستنداتنا فيه. وهذا أمر بالغ الأهمية لأننا سنقوم بتحميل المستندات وحفظها من هذا المسار.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 يستبدل`"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي لمستنداتك.

## الخطوة 3: تحميل المستند

الآن، دعونا نحمل المستند الذي يتطلب الوصل.

```csharp
Document document = new Document(dataDir + "German text.docx");
```

هنا، نقوم بتحميل مستند نصي باللغة الألمانية. يمكنك استبدال`"German text.docx"` مع اسم ملف المستند الخاص بك.

## الخطوة 4: حفظ المستند

بعد تحميل المستند، نقوم بحفظه في ملف جديد، ونطبق استدعاء الواصلة في هذه العملية.

```csharp
document.Save(dataDir + "TreatmentByCesureWithRecall.pdf");
```

يحفظ هذا السطر المستند بصيغة PDF مع تطبيق الوصلة.

## الخطوة 5: التعامل مع استثناء القاموس المتعلق بعلامات الوصل المفقودة

في بعض الأحيان، قد تواجه مشكلة عدم وجود قاموس علامات الترقيم. دعنا نتعامل مع هذه المشكلة.

```csharp
catch (Exception e) when (e.Message.StartsWith("Missing hyphenation dictionary"))
{
    Console.WriteLine(e.Message);
}
finally
{
    Hyphenation.Callback = null;
}
```

في هذه الكتلة، نقوم بالتقاط الاستثناء المحدد المتعلق بالقواميس المفقودة وطباعة الرسالة.

## الخطوة 6: تنفيذ فئة استدعاء الواصلة المخصصة

 الآن، دعونا ننفذ`CustomHyphenationCallback` الفئة التي تتعامل مع طلب قواميس الوصل.

```csharp
public class CustomHyphenationCallback : IHyphenationCallback
{
    public void RequestDictionary(string language)
    {
        string dictionaryFolder = MyDir;
        string dictionaryFullFileName;
        switch (language)
        {
            case "en-US":
                dictionaryFullFileName = Path.Combine(dictionaryFolder, "hyph_en_US.dic");
                break;
            case "de-CH":
                dictionaryFullFileName = Path.Combine(dictionaryFolder, "hyph_de_CH.dic");
                break;
            default:
                throw new Exception($"Missing hyphenation dictionary for {language}.");
        }
        // تسجيل القاموس للغة المطلوبة.
        Hyphenation.RegisterDictionary(language, dictionaryFullFileName);
    }
}
```

 في هذه الفئة،`RequestDictionary` يتم استدعاء الطريقة كلما كانت هناك حاجة إلى قاموس الوصلات. وهي تتحقق من اللغة وتسجل القاموس المناسب.

## خاتمة

والآن، لقد تعلمت للتو كيفية تنفيذ استدعاء الوصلة في Aspose.Words لـ .NET. باتباع هذه الخطوات، يمكنك ضمان تنسيق مستنداتك بشكل جميل، بغض النظر عن اللغة. سواء كنت تتعامل مع اللغة الإنجليزية أو الألمانية أو أي لغة أخرى، تتيح لك هذه الطريقة التعامل مع الوصلة بسهولة.

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟
Aspose.Words for .NET هي مكتبة قوية لمعالجة المستندات تتيح للمطورين إنشاء المستندات وتعديلها وتحويلها برمجيًا.

### لماذا تعتبر علامة الوصل مهمة في تنسيق المستندات؟
تعمل ميزة الوصل على تحسين تخطيط النص من خلال تقسيم الكلمات في الأماكن المناسبة، مما يضمن مستندًا أكثر قابلية للقراءة وجاذبية بصريًا.

### هل يمكنني استخدام Aspose.Words مجانًا؟
 يقدم Aspose.Words نسخة تجريبية مجانية. يمكنك الحصول عليها[هنا](https://releases.aspose.com/).

### كيف أحصل على قاموس الوصل؟
يمكنك تنزيل قواميس الوصل من مصادر مختلفة عبر الإنترنت أو إنشاء قواميسك الخاصة إذا لزم الأمر.

### ماذا يحدث إذا كان قاموس الوصل مفقودًا؟
 إذا كان القاموس مفقودًا،`RequestDictionary`ترمي الطريقة استثناءً، ويمكنك التعامل معه لإعلام المستخدم أو تقديم حل بديل.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
