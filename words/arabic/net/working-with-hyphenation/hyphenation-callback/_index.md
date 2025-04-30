---
"description": "تعلم كيفية تنفيذ استدعاء الواصلة في Aspose.Words for .NET لتحسين تنسيق المستندات باستخدام هذا الدليل الشامل خطوة بخطوة."
"linktitle": "استدعاء الوصلة"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "استدعاء الوصلة"
"url": "/ar/net/working-with-hyphenation/hyphenation-callback/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# استدعاء الوصلة


## مقدمة

أهلاً! هل سبق لك أن وجدت نفسك متورطاً في تعقيدات تنسيق النصوص، خاصةً عند التعامل مع اللغات التي تتطلب الواصلة؟ لست وحدك. الواصلة، على الرغم من أهميتها لتنسيق النص بشكل صحيح، قد تكون مزعجة بعض الشيء. ولكن، تخيل ماذا؟ Aspose.Words for .NET ستوفر لك الحل. تتيح لك هذه المكتبة القوية إدارة تنسيق النصوص بسلاسة، بما في ذلك التعامل مع الواصلة من خلال آلية استدعاء. هل أنت مهتم؟ دعنا نتعمق في كيفية تنفيذ استدعاء الواصلة باستخدام Aspose.Words for .NET.

## المتطلبات الأساسية

قبل أن نبدأ في التعامل مع الكود، دعنا نتأكد من أنك حصلت على كل ما تحتاجه:

1. Aspose.Words لـ .NET: تأكد من توفر المكتبة لديك. يمكنك [قم بتحميله هنا](https://releases.aspose.com/words/net/).
2. IDE: بيئة تطوير مثل Visual Studio.
3. المعرفة الأساسية بلغة C#: فهم لغة C# وإطار عمل .NET.
4. قواميس الوصل: قواميس الوصل للغات التي تخطط لاستخدامها.
5. ترخيص Aspose: ترخيص Aspose ساري المفعول. يمكنك الحصول عليه [رخصة مؤقتة](https://purchase.aspose.com/temporary-license/) إذا لم يكن لديك واحدة.

## استيراد مساحات الأسماء

أولاً، لنستورد مساحات الأسماء اللازمة. هذا يضمن وصول كودنا إلى جميع الفئات والأساليب التي نحتاجها من Aspose.Words.

```csharp
using Aspose.Words;
using System;
using System.IO;
```

## الخطوة 1: تسجيل استدعاء الواصلة

للبدء، نحتاج إلى تسجيل دالة استدعاء الواصلة. هنا نطلب من Aspose.Words استخدام منطق الواصلة المخصص لدينا.

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

هنا، نقوم بإنشاء مثيل لاستدعاءنا المخصص وتعيينه إلى `Hyphenation.Callback`.

## الخطوة 2: تحديد مسار المستند

بعد ذلك، علينا تحديد المجلد الذي تُخزَّن فيه مستنداتنا. هذا أمر بالغ الأهمية لأننا سنحمّل ونحفظ المستندات من هذا المسار.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

يستبدل `"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي إلى مستنداتك.

## الخطوة 3: تحميل المستند

الآن، دعنا نحمل المستند الذي يتطلب الوصل.

```csharp
Document document = new Document(dataDir + "German text.docx");
```

هنا، نقوم بتحميل مستند نصي ألماني. يمكنك استبدال `"German text.docx"` مع اسم ملف المستند الخاص بك.

## الخطوة 4: حفظ المستند

بعد تحميل المستند، نقوم بحفظه في ملف جديد، ونطبق استدعاء الواصلة في هذه العملية.

```csharp
document.Save(dataDir + "TreatmentByCesureWithRecall.pdf");
```

يحفظ هذا السطر المستند بصيغة PDF مع تطبيق الواصلة.

## الخطوة 5: التعامل مع استثناء قاموس الوصلة المفقودة

قد تواجه أحيانًا مشكلةً تتعلق بفقدان قاموس الواصلات. لنحل هذه المشكلة.

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

الآن، دعونا ننفذ `CustomHyphenationCallback` الفئة التي تتعامل مع طلب قواميس الوصل.

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

في هذه الفئة، `RequestDictionary` تُستدعى هذه الطريقة عند الحاجة إلى قاموس الواصلات. تتحقق هذه الطريقة من اللغة وتُسجل القاموس المناسب.

## خاتمة

ها قد انتهيت! لقد تعلمت للتو كيفية تنفيذ استدعاء الواصلة في Aspose.Words لـ .NET. باتباع هذه الخطوات، يمكنك ضمان تنسيق مستنداتك بشكل جميل، بغض النظر عن اللغة. سواء كنت تتعامل مع الإنجليزية أو الألمانية أو أي لغة أخرى، تتيح لك هذه الطريقة التعامل مع الواصلة بسهولة.

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟
Aspose.Words for .NET هي مكتبة قوية لمعالجة المستندات تتيح للمطورين إنشاء المستندات وتعديلها وتحويلها برمجيًا.

### لماذا تعتبر علامة الوصل مهمة في تنسيق المستندات؟
تعمل ميزة الوصل على تحسين تخطيط النص من خلال تقسيم الكلمات في الأماكن المناسبة، مما يضمن مستندًا أكثر قابلية للقراءة وجاذبية بصريًا.

### هل يمكنني استخدام Aspose.Words مجانًا؟
يقدم Aspose.Words نسخة تجريبية مجانية. يمكنك الحصول عليها. [هنا](https://releases.aspose.com/).

### كيف أحصل على قاموس الوصلات؟
يمكنك تنزيل قواميس الوصل من مصادر مختلفة عبر الإنترنت أو إنشاء قواميسك الخاصة إذا لزم الأمر.

### ماذا يحدث إذا كان قاموس الوصل مفقودًا؟
إذا كان القاموس مفقودًا، `RequestDictionary` تطرح الطريقة استثناءً، ويمكنك التعامل معه لإعلام المستخدم أو تقديم حل بديل.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}