---
category: general
date: 2026-10-26
description: تعلم كيفية إنشاء مستند Word باستخدام C# وإضافة زر ActiveX برمجيًا. يغطي
  هذا الدليل خطوة بخطوة إدراج زر أمر، إخفائه أثناء التصميم، وحفظ الملف.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to add activex button
- create command button word
- programmatically add command button
language: ar
lastmod: 2026-10-26
og_description: إنشاء مستند Word باستخدام C# وإضافة زر ActiveX برمجياً. اتبع هذا الدرس
  الكامل لتضمين زر أمر يظهر فقط أثناء التشغيل.
og_image_alt: Screenshot of a Word document created with C# that contains an ActiveX
  command button
og_title: إنشاء مستند Word باستخدام C# مع زر أمر ActiveX – دليل كامل
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document C# and add an ActiveX button programmatically.
    This step‑by‑step guide covers inserting a command button, hiding it at design
    time, and saving the file.
  headline: How to create Word document C# with an ActiveX command button
  type: TechArticle
tags:
- C#
- Aspose.Words
- ActiveX
- Word automation
title: كيفية إنشاء مستند Word باستخدام C# وزر أمر ActiveX
url: /ar/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء مستند Word C# مع زر أمر ActiveX

إذا كنت بحاجة إلى **إنشاء مستند Word C#** يحتوي على زر تفاعلي، فإن هذا الدليل يوضح لك بالضبط كيفية القيام بذلك. بحلول نهاية الجملتين الأوليين ستعرف النهج العام، وستقودك الخطوات التالية عبر كل سطر من الشيفرة التي يجب عليك كتابتها.

سوف تتعلم كيفية إضافة زر ActiveX، إخفاؤه أثناء التصميم، وجعله مرئياً فقط عندما يفتح المستخدم الملف. يغطي الدليل أيضاً المشكلات الشائعة مثل تحذيرات الأمان وتوافق الإصدارات، حتى تتمكن من نشر مستندات موثوقة.

## المتطلبات المسبقة

* .NET 6.0 أو أحدث مثبت  
* نسخة مرخصة من **Aspose.Words for .NET** (الإصدار التجريبي المجاني يكفي للتجربة)  
* إلمام أساسي بـ C# و Visual Studio (أي بيئة تطوير تدعم .NET تكفي)

لا توجد حزم NuGet إضافية مطلوبة بخلاف `Aspose.Words`.

## الخطوة 1: إنشاء مستند Word C# وتهيئة DocumentBuilder

الخطوة الأولى هي إنشاء كائن `Document` و `DocumentBuilder`. يمثل `Document` ملف .docx بالكامل، بينما يوفر `DocumentBuilder` أساليب سلسة لإضافة المحتوى.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document document = new Document();

        // Attach a builder to the document so we can insert nodes.
        DocumentBuilder builder = new DocumentBuilder(document);
```

**لماذا هذا مهم:** بدون `DocumentBuilder` سيتعين عليك تعديل شجرة OpenXML DOM يدوياً، وهو أمر عرضة للأخطاء وأكثر صعوبة في القراءة. يقوم الـ builder بتجريد تلك التفاصيل ويضمن ملف Word مُشكل بشكل صحيح.

## الخطوة 2: كيفية إضافة زر ActiveX – إدراج عنصر تحكم CommandButton

الآن نقوم بإدراج **عنصر تحكم CommandButton ActiveX** في موقع محدد. يحدد المستطيل موضع الزر (X, Y) وحجمه (العرض، الارتفاع) بالنقاط.

```csharp
        // Define the button's position and size.
        RectangleF buttonRect = new RectangleF(100, 100, 120, 30);

        // Insert the ActiveX CommandButton control.
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,   // Type of ActiveX control
            buttonRect,                          // Geometry
            "ClickMe");                          // Caption shown at design time
```

**لماذا هذا مهم:** `InsertForms2OleControl` هي الطريقة الوحيدة في Aspose.Words التي تنشئ كائن ActiveX OLE حقيقي. قيمة تعداد `Forms2OleControlType.CommandButton` تخبر Word بدمج زر قابل للنقر بدلاً من حاوية OLE عامة.

## الخطوة 3: إضافة زر الأمر برمجياً – إخفاؤه حتى وقت التشغيل

يتعامل Word مع أي شكل مدرج على أنه مرئي افتراضياً. لإبقاء الزر غير مرئي أثناء تصميم القالب، قم بتعيين الخاصية `Hidden` على الشكل الذي أنشأه الـ builder للتو.

```csharp
        // Retrieve the shape that represents the newly added control.
        Shape oleShape = (Shape)builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)[0];

        // Hide the shape; it will become visible when the document is opened.
        oleShape.Hidden = true;
```

**لماذا هذا مهم:** ضبط `Hidden = true` يمنع الزر من إغراق واجهة التصميم. عندما يُفتح المستند في Word، يكشف بيئة التشغيل الزر تلقائياً، محافظاً على تجربة المستخدم المقصودة.

## الخطوة 4: حفظ الملف – إنشاء مستند Word يحتوي على زر أمر

أخيراً، احفظ المستند على القرص. اختر مساراً يمكن لتطبيقك الكتابة إليه، واستخدم امتداد `.docx` لضمان التوافق الحديث.

```csharp
        // Save the document containing the ActiveX button.
        document.Save(@"C:\Temp\ActiveXButton.docx");
    }
}
```

**لماذا هذا مهم:** حفظ الملف كـ `.docx` يضمن أن عنصر التحكم ActiveX المدمج يتوافق مع معيار Office Open XML، المدعوم من Word 2007 وما بعده. إذا كنت بحاجة إلى دعم `.doc` القديم، استبدل الامتداد واستخدم `SaveFormat.Doc`.

## مثال كامل يعمل

بجمع كل شيء معاً، إليك البرنامج الكامل الذي يمكنك نسخه، لصقه، وتشغيله:

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Step 1: Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control.
        RectangleF commandButtonRect = new RectangleF(100, 100, 120, 30);
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            commandButtonRect,
            "ClickMe");

        // Step 3: Hide the control so it appears only at runtime.
        Shape oleShape = (Shape)builder.CurrentParagraph
                                         .GetChildNodes(NodeType.Shape, true)[0];
        oleShape.Hidden = true;

        // Step 4: Save the document containing the ActiveX control.
        document.Save(@"C:\Temp\ActiveX.docx");
    }
}
```

**الناتج المتوقع:** بعد تشغيل البرنامج، افتح `C:\Temp\ActiveX.docx` في Microsoft Word. سترى مستنداً فارغاً؛ الزر غير مرئي في وضع التصميم. اضغط **Alt + F9** لتبديل رموز الحقول، ثم انقر على منطقة الزر—سيقوم Word بعرض عنصر التحكم ActiveX، ويمكنك التفاعل معه (مثلاً، انقر مزدوجاً لعرض خصائصه).

## الحالات الخاصة ونصائح الممارسات المثلى

| الحالة | ما الذي يجب مراقبته | الإصلاح الموصى به |
|-----------|-------------------|-----------------|
| **المستخدم يعطل ActiveX** | قد يعرض Word تحذيراً أمنياً أو يحظر العنصر. | وجه المستخدمين النهائيين لتمكين “ActiveX controls” في مركز الثقة، أو قدم بديلاً موقعاً بالماكرو. |
| **فتح المستند في Word Online** | لا يدعم Word Online ActiveX؛ سيتم حذف الزر. | استخدم رابطاً احتياطياً أو عنصر تحكم محتوى إذا كنت بحاجة إلى توافق سحابي. |
| **إعدادات DPI مختلفة** | قد يظهر حجم المستطيل أكبر أو أصغر على الشاشات ذات DPI عالي. | استخدم `GraphicsUnit.Point` (الإعداد الافتراضي) واختبر على إعدادات DPI الشائعة (96 dpi، 120 dpi). |
| **عدة أزرار** | استدعاء `GetChildNodes(NodeType.Shape, true)[0]` يسترجع الشكل الأول فقط. | قم بالتكرار عبر `builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)` واضبط `Hidden` لكل شكل تضيفه. |
| **تنسيق .doc القديم** | تُفقد بعض خصائص ActiveX عند الحفظ كـ `.doc`. | يفضَّل استخدام `.docx` ما لم يكن لديك متطلب صارم للنسخة القديمة. |

**نصيحة احترافية:** بعد إدراج الزر، يمكنك تعيين ماكرو لخاصية `OnAction` عبر واجهة Word. يتيح لك ذلك تعريف سلوك النقر المخصص دون كتابة كود C# إضافي.

## الأسئلة المتكررة

* **هل يعمل هذا مع .NET Core؟**  
  نعم. Aspose.Words for .NET متوافق تماماً مع .NET 5، .NET 6، وما بعدهما. فقط استدعِ حزمة NuGet نفسها.

* **هل يمكنني تغيير تسمية الزر بعد إنشاء المستند؟**  
  التسمية التي تم ضبطها في `InsertForms2OleControl` تصبح النص الافتراضي أثناء التصميم. يمكن للمستخدمين تعديلها في Word، لكن يمكنك أيضاً تحديث التسمية برمجياً عبر الوصول إلى خصائص كائن OLE باستخدام API `Shape.OleFormat`.

* **ماذا لو احتجت حجمًا مختلفًا للزر؟**  
  عدّل قيم `RectangleF`. المعاملان الأولان هما إحداثيات X و Y؛ والمعاملان الأخيران هما العرض والارتفاع بالنقاط (1 pt = 1/72 بوصة).

## الخلاصة

أنت الآن تعرف كيف **تنشئ مستند Word C#** و **تضيف زر أمر برمجياً** باستخدام Aspose.Words. غطى الدليل تهيئة المستند، إدراج زر ActiveX، إخفائه حتى وقت التشغيل، وحفظ الملف النهائي. باستخدام هذه اللبنات الأساسية يمكنك تضمين عناصر تحكم تفاعلية في أي قالب Word تقوم بإنشائه.

بعد ذلك، استكشف المواضيع ذات الصلة مثل **كيفية إضافة زر ActiveX** ومعالجة الأحداث، **إنشاء زر أمر Word** وتنسيقه باستخدام VBA، و **إضافة زر أمر برمجياً** إلى المستندات الموجودة. توسيع هذا النمط إلى مربعات اختيار، قوائم منسدلة، أو كائنات OLE مخصصة يتبع نفس الخطوات—فقط غيّر قيمة تعداد `Forms2OleControlType`.

ابدأ بالتجربة: استبدل التسمية، عدّل الموضع، أو اربط عدة عناصر تحكم معاً. كلما مارست أكثر، كلما أصبحت أكثر طلاقة في تقديم مستندات Word غنية وتفاعلية من C#. برمجة سعيدة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة شيفرة كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية إضافة زر أمر برمجياً في مستند Word](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [كيفية إضافة زر ActiveX في مستند Word باستخدام Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [إنشاء مستند Word مع زر ActiveX – دليل C#](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}