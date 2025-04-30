---
"description": "تعرف على كيفية اكتشاف تنسيقات ملفات المستندات باستخدام Aspose.Words لـ .NET باستخدام هذا الدليل الشامل خطوة بخطوة."
"linktitle": "الكشف عن تنسيق ملف المستند"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "الكشف عن تنسيق ملف المستند"
"url": "/ar/net/programming-with-fileformat/detect-file-format/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# الكشف عن تنسيق ملف المستند

## مقدمة

في عالمنا الرقمي اليوم، تُعدّ إدارة تنسيقات المستندات المختلفة بكفاءة أمرًا بالغ الأهمية. سواء كنت تتعامل مع Word أو PDF أو HTML أو غيرها من التنسيقات، فإنّ القدرة على اكتشاف هذه الملفات ومعالجتها بشكل صحيح تُوفّر عليك الكثير من الوقت والجهد. في هذا البرنامج التعليمي، سنستكشف كيفية اكتشاف تنسيقات ملفات المستندات باستخدام Aspose.Words لـ .NET. سيُرشدك هذا الدليل إلى كل ما تحتاج لمعرفته، بدءًا من المتطلبات الأساسية ووصولًا إلى دليل مُفصّل خطوة بخطوة.

## المتطلبات الأساسية

قبل أن نتعمق في الكود، دعنا نتأكد من أن لديك كل ما تحتاجه:

- Aspose.Words for .NET: يمكنك تنزيله من [هنا](https://releases.aspose.com/words/net/)تأكد من أن لديك رخصة سارية المفعول. إذا لم تكن كذلك، يمكنك الحصول على [رخصة مؤقتة](https://purchase.aspose.com/temporary-license/).
- Visual Studio: أي إصدار حديث سيعمل بشكل جيد.
- .NET Framework: تأكد من تثبيت الإصدار الصحيح.

## استيراد مساحات الأسماء

للبدء، ستحتاج إلى استيراد المساحات الأساسية اللازمة في مشروعك:

```csharp
using Aspose.Words;
using Aspose.Words.FileFormats;
using Aspose.Words.FileFormats.Util;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
```

دعونا نقسم المثال إلى خطوات متعددة لتسهيل متابعته.

## الخطوة 1: إعداد الدلائل

أولاً، نحتاج إلى إعداد الدلائل التي سيتم فيها فرز الملفات بناءً على تنسيقها.

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENT DIRECTORY";
string supportedDir = dataDir + "Supported";
string unknownDir = dataDir + "Unknown";
string encryptedDir = dataDir + "Encrypted";
string pre97Dir = dataDir + "Pre97";

// قم بإنشاء الدلائل إذا لم تكن موجودة بالفعل.
if (!Directory.Exists(supportedDir))
    Directory.CreateDirectory(supportedDir);
if (!Directory.Exists(unknownDir))
    Directory.CreateDirectory(unknownDir);
if (!Directory.Exists(encryptedDir))
    Directory.CreateDirectory(encryptedDir);
if (!Directory.Exists(pre97Dir))
    Directory.CreateDirectory(pre97Dir);
```

## الخطوة 2: الحصول على قائمة الملفات

بعد ذلك، سنحصل على قائمة بالملفات الموجودة في الدليل، باستثناء أي مستندات تالفة.

```csharp
IEnumerable<string> fileList = Directory.GetFiles(dataDir).Where(name => !name.EndsWith("Corrupted document.docx"));
```

## الخطوة 3: اكتشاف تنسيقات الملفات

الآن، نقوم بتكرار كل ملف واكتشاف تنسيقه باستخدام Aspose.Words.

```csharp
foreach (string fileName in fileList)
{
    string nameOnly = Path.GetFileName(fileName);

    Console.Write(nameOnly);

    FileFormatInfo info = FileFormatUtil.DetectFileFormat(fileName);

    // عرض نوع المستند
    switch (info.LoadFormat)
    {
        case LoadFormat.Doc:
            Console.WriteLine("\tMicrosoft Word 97-2003 document.");
            break;
        case LoadFormat.Dot:
            Console.WriteLine("\tMicrosoft Word 97-2003 template.");
            break;
        case LoadFormat.Docx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Document.");
            break;
        case LoadFormat.Docm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
            break;
        case LoadFormat.Dotx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Template.");
            break;
        case LoadFormat.Dotm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
            break;
        case LoadFormat.FlatOpc:
            Console.WriteLine("\tFlat OPC document.");
            break;
        case LoadFormat.Rtf:
            Console.WriteLine("\tRTF format.");
            break;
        case LoadFormat.WordML:
            Console.WriteLine("\tMicrosoft Word 2003 WordprocessingML format.");
            break;
        case LoadFormat.Html:
            Console.WriteLine("\tHTML format.");
            break;
        case LoadFormat.Mhtml:
            Console.WriteLine("\tMHTML (Web archive) format.");
            break;
        case LoadFormat.Odt:
            Console.WriteLine("\tOpenDocument Text.");
            break;
        case LoadFormat.Ott:
            Console.WriteLine("\tOpenDocument Text Template.");
            break;
        case LoadFormat.DocPreWord60:
            Console.WriteLine("\tMS Word 6 or Word 95 format.");
            break;
        case LoadFormat.Unknown:
            Console.WriteLine("\tUnknown format.");
            break;
    }

    if (info.IsEncrypted)
    {
        Console.WriteLine("\tAn encrypted document.");
        File.Copy(fileName, Path.Combine(encryptedDir, nameOnly), true);
    }
    else
    {
        switch (info.LoadFormat)
        {
            case LoadFormat.DocPreWord60:
                File.Copy(fileName, Path.Combine(pre97Dir, nameOnly), true);
                break;
            case LoadFormat.Unknown:
                File.Copy(fileName, Path.Combine(unknownDir, nameOnly), true);
                break;
            default:
                File.Copy(fileName, Path.Combine(supportedDir, nameOnly), true);
                break;
        }
    }
}
```

## خاتمة

يُعدّ اكتشاف تنسيقات ملفات المستندات باستخدام Aspose.Words لـ .NET عمليةً سهلةً وبسيطةً. من خلال إعداد المجلدات، والحصول على قائمة الملفات، واستخدام Aspose.Words لاكتشاف تنسيقات الملفات، يمكنك تنظيم وإدارة مستنداتك بكفاءة. هذا النهج لا يوفر الوقت فحسب، بل يضمن أيضًا التعامل مع تنسيقات المستندات المختلفة بشكل صحيح.

## الأسئلة الشائعة

### ما هو Aspose.Words لـ .NET؟
Aspose.Words for .NET هي مكتبة فعّالة للعمل مع مستندات Word برمجيًا. تتيح للمطورين إنشاء وتعديل وتحويل المستندات بتنسيقات مختلفة.

### هل يمكن لـ Aspose.Words اكتشاف المستندات المشفرة؟
نعم، يمكن لـ Aspose.Words اكتشاف ما إذا كان المستند مشفرًا ويمكنك التعامل مع هذه المستندات وفقًا لذلك.

### ما هي التنسيقات التي يمكن لـ Aspose.Words اكتشافها؟
يمكن لبرنامج Aspose.Words اكتشاف مجموعة واسعة من التنسيقات بما في ذلك DOC، وDOCX، وRTF، وHTML، وMHTML، وODT، وغيرها الكثير.

### كيف يمكنني الحصول على ترخيص مؤقت لـ Aspose.Words؟
يمكنك الحصول على ترخيص مؤقت من [شراء Aspose](https://purchase.aspose.com/temporary-license/) صفحة.

### أين يمكنني العثور على الوثائق الخاصة بـ Aspose.Words؟
يمكن العثور على وثائق Aspose.Words [هنا](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}