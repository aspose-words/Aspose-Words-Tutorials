---
"description": "تعرّف على كيفية إدارة استبدال الخطوط بدون لاحقات في Aspose.Words لـ .NET. اتبع دليلنا خطوة بخطوة لضمان ظهور مستنداتك بشكل مثالي في كل مرة."
"linktitle": "الحصول على الاستبدال بدون لاحقات"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "الحصول على الاستبدال بدون لاحقات"
"url": "/ar/net/working-with-fonts/get-substitution-without-suffixes/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# الحصول على الاستبدال بدون لاحقات

## مقدمة

مرحبًا بكم في هذا الدليل الشامل لإدارة استبدال الخطوط باستخدام Aspose.Words لـ .NET. إذا واجهتَ يومًا مشكلة عدم ظهور الخطوط بشكل صحيح في مستنداتك، فأنتَ في المكان الصحيح. سيرشدك هذا البرنامج التعليمي خطوة بخطوة إلى كيفية إدارة استبدال الخطوط بكفاءة دون استخدام اللاحقات.

## المتطلبات الأساسية

قبل الغوص في البرنامج التعليمي، تأكد من أن لديك ما يلي:

- المعرفة الأساسية بلغة C#: إن فهم برمجة C# سيجعل من الأسهل متابعة الخطوات وتنفيذها.
- Aspose.Words لمكتبة .NET: قم بتنزيل المكتبة وتثبيتها من [رابط التحميل](https://releases.aspose.com/words/net/).
- بيئة التطوير: قم بإعداد بيئة تطوير مثل Visual Studio لكتابة وتشغيل التعليمات البرمجية الخاصة بك.
- مستند نموذجي: مستند نموذجي (على سبيل المثال، `Rendering.docx`) للعمل عليها أثناء هذا البرنامج التعليمي.

## استيراد مساحات الأسماء

أولاً، نحتاج إلى استيراد مساحات الأسماء اللازمة للوصول إلى الفئات والطرق التي يوفرها Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System.Collections.Generic;
```

## الخطوة 1: تحديد دليل المستندات

للبدء، حدد الدليل الذي يوجد فيه مستندك. هذا يساعدك في تحديد المستند الذي تريد العمل عليه.

```csharp
// المسار إلى دليل المستندات الخاص بك
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## الخطوة 2: إعداد معالج تحذير الاستبدال

بعد ذلك، نحتاج إلى إعداد مُعالج تحذير يُنبهنا عند استبدال الخط أثناء معالجة المستند. هذا ضروري لاكتشاف أي مشاكل في الخطوط ومعالجتها.

```csharp
DocumentSubstitutionWarnings substitutionWarningHandler = new DocumentSubstitutionWarnings();
Document doc = new Document(dataDir + "Rendering.docx");
doc.WarningCallback = substitutionWarningHandler;
```

## الخطوة 3: إضافة مصادر الخطوط المخصصة

في هذه الخطوة، سنضيف مصادر خطوط مخصصة لضمان قدرة Aspose.Words على تحديد الخطوط الصحيحة واستخدامها. يُعد هذا مفيدًا بشكل خاص إذا كانت لديك خطوط محددة مخزنة في مجلدات مخصصة.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(FontSettings.DefaultInstance.GetFontsSources());

FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);

FontSourceBase[] updatedFontSources = fontSources.ToArray();
FontSettings.DefaultInstance.SetFontsSources(updatedFontSources);
```

في هذا الكود:
- نقوم باسترجاع مصادر الخطوط الحالية وإضافة خط جديد `FolderFontSource` الإشارة إلى دليل الخطوط المخصص لدينا (`C:\\MyFonts\\`).
- ثم نقوم بتحديث مصادر الخطوط بهذه القائمة الجديدة.

## الخطوة 4: حفظ المستند

أخيرًا، احفظ المستند بعد تطبيق إعدادات استبدال الخط. في هذا الدرس، سنحفظه كملف PDF.

```csharp
doc.Save(dataDir + "WorkingWithFonts.GetSubstitutionWithoutSuffixes.pdf");
```

## الخطوة 5: إنشاء فئة معالج التحذير

للتعامل مع التحذيرات بشكل فعال، قم بإنشاء فئة مخصصة تنفذ `IWarningCallback` ستقوم هذه الفئة بالتقاط وتسجيل أي تحذيرات لاستبدال الخط.

```csharp
public class DocumentSubstitutionWarnings : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            FontWarnings.Warning(info);
    }

    public WarningInfoCollection FontWarnings = new WarningInfoCollection();
}
```

في هذه الفئة:
- ال `Warning` تلتقط الطريقة التحذيرات المتعلقة باستبدال الخط.
- ال `FontWarnings` تقوم المجموعة بتخزين هذه التحذيرات لمزيد من التفتيش أو التسجيل.

## خاتمة

لقد أتقنتَ الآن عملية استبدال الخطوط دون استخدام لاحقات باستخدام Aspose.Words لـ .NET. ستضمن هذه المعرفة الحفاظ على مظهر مستنداتك، بغض النظر عن الخطوط المتوفرة على النظام. استمر في تجربة إعدادات ومصادر مختلفة للاستفادة الكاملة من قوة Aspose.Words.

## الأسئلة الشائعة

### كيف يمكنني استخدام الخطوط من أدلة مخصصة متعددة؟

يمكنك إضافة متعددة `FolderFontSource` حالات إلى `fontSources` قم بإدراج مصادر الخطوط وتحديثها وفقًا لذلك.

### أين يمكنني تنزيل نسخة تجريبية مجانية من Aspose.Words لـ .NET؟

يمكنك تنزيل نسخة تجريبية مجانية من [صفحة التجربة المجانية لـ Aspose](https://releases.aspose.com/).

### هل يمكنني التعامل مع أنواع متعددة من التحذيرات باستخدام `IWarningCallback`؟

نعم، `IWarningCallback` تتيح لك الواجهة التعامل مع أنواع مختلفة من التحذيرات، وليس فقط استبدال الخط.

### أين يمكنني الحصول على الدعم لـ Aspose.Words؟

للحصول على الدعم، قم بزيارة [منتدى دعم Aspose.Words](https://forum.aspose.com/c/words/8).

### هل من الممكن شراء ترخيص مؤقت؟

نعم يمكنك الحصول على ترخيص مؤقت من [صفحة الترخيص المؤقت](https://purchase.aspose.com/temporary-license/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}