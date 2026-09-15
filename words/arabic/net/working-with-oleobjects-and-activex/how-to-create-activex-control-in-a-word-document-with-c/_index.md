---
category: general
date: 2026-09-14
description: إنشاء عنصر تحكم ActiveX في مستند Word باستخدام C#. تعلّم كيفية إدراج
  ActiveX، إضافة زر تفاعلي، وتوليد ملف .docx برمجيًا.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- how to insert activex
- add interactive button
- create word document
- create button with code
language: ar
lastmod: 2026-09-14
og_description: إنشاء عنصر تحكم ActiveX في مستند Word باستخدام C#. اتبع هذا المثال
  الكامل لإدراج ActiveX، وإضافة زر تفاعلي، وحفظ الملف.
og_image_alt: Screenshot of a Word document containing a newly created ActiveX CommandButton
og_title: إنشاء عنصر تحكم ActiveX في Word باستخدام C# – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Create ActiveX control in a Word document with C#. Learn how to insert
    ActiveX, add interactive button, and generate the .docx file programmatically.
  headline: How to create ActiveX control in a Word document with C#
  type: TechArticle
tags:
- ActiveX
- C#
- Word automation
title: كيفية إنشاء عنصر تحكم ActiveX في مستند Word باستخدام C#
url: /ar/net/working-with-oleobjects-and-activex/how-to-create-activex-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إنشاء عنصر تحكم ActiveX في مستند Word باستخدام C#

إذا كنت بحاجة إلى **إنشاء عنصر تحكم ActiveX** داخل ملف Microsoft Word، فإن هذا الدليل يوضح لك حلاً كاملاً وجاهزًا للتنفيذ. ستشاهد بالضبط كيفية إدراج زر CommandButton من نوع ActiveX، وضبط خصائصه، وحفظ ملف `.docx` الناتج باستخدام كود C# فقط.

إضافة زر تفاعلي إلى مستند Word هو طلب شائع عندما تريد من المستخدمين النهائيين تشغيل ماكرو أو منطق مخصص مباشرةً من واجهة المستند. المثال أدناه يوضح **كيفية إدراج ActiveX** دون الاعتماد على أدوات طرف ثالث، كما يغطي **كيفية إنشاء مستند Word** برمجيًا.

بنهاية هذا الشرح ستكون قادرًا على **إنشاء زر باستخدام الكود**، تخصيص النص الظاهر له، وإنتاج ملف Word قابل للنقل يحافظ على عنصر التحكم ActiveX.

## المتطلبات المسبقة

- .NET 6.0 أو أحدث (مكتبة Aspose.Words for .NET تعمل مع .NET Core و .NET Framework)
- إشارة إلى حزمة NuGet `Aspose.Words`  
  ```bash
  dotnet add package Aspose.Words
  ```
- معرفة أساسية بـ C# والبرمجة الكائنية التوجه

## الخطوة 1: إعداد المشروع واستيراد المساحات الاسمية

أنشئ مشروع وحدة تحكم جديد (أو دمج الكود في أي تطبيق C# موجود). استورد المساحات الاسمية المطلوبة حتى يتمكن المترجم من العثور على فئات معالجة Word.

```csharp
using System;
using System.Drawing;               // Provides RectangleF
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
```

> **لماذا هذه الخطوة مهمة** – توفر API الخاصة بـ `Aspose.Words` الفئات `Document` و `DocumentBuilder` و `Forms2OleControl` التي تسمح لك بالتعامل مع ملفات Word على مستوى الكائن. بدون هذه الإشارات لن يتم تجميع باقي الكود.

## الخطوة 2: إنشاء مستند Word جديد وDocumentBuilder

كائن `Document` يمثل حزمة `.docx` بالكامل، بينما يقدم `DocumentBuilder` API سلسًا لإدراج المحتوى.

```csharp
// Step 2: Initialize a fresh Word document
Document document = new Document();

// Attach a builder to the document – the builder knows where to write next
DocumentBuilder builder = new DocumentBuilder(document);
```

> **شرح** – إنشاء كائن `Document` جديد يمنحك لوحة رسم نظيفة. يبدأ مؤشر الـ builder في بداية القسم الأول، جاهزًا للإدراج التالي.

## الخطوة 3: إدراج زر CommandButton من نوع ActiveX

استخدم `InsertForms2OleControl` لوضع عنصر تحكم ActiveX في موقع محدد. تتطلب الطريقة نوع العنصر، و`RectangleF` يحدد إحداثيات X/Y والحجم (بالنقاط).

```csharp
// Step 3: Add an ActiveX CommandButton at (100,100) with width 120 and height 30
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **لماذا يعمل هذا** – `OleControlType.CommandButton` يخبر الـ API بإنشاء زر CommandButton قياسي لنظام Windows. يحدد المستطيل موضع الزر نسبةً إلى الزاوية العلوية اليسرى للصفحة، مما يتيح لك **إضافة زر تفاعلي** بالضبط حيث تحتاجه.

## الخطوة 4: ضبط خصائص الزر

الآن قم بتعيين النص الظاهر للزر (`Caption`) واسمه الداخلي (`Name`). هذه الخصائص هي ما يراه المستخدمون وما يمكن لكود VBA الإشارة إليه لاحقًا.

```csharp
// Step 4: Define the button’s caption and programmatic name
commandButton.Caption = "Click Me";
commandButton.Name = "btnClick";
```

> **نصيحة عملية** – يجب أن يكون `Name` فريدًا داخل المستند؛ وإلا قد تشير ماكروهات VBA إلى العنصر الخطأ.

## الخطوة 5: حفظ المستند

أخيرًا، اكتب الملف إلى القرص. يتم تخزين عنصر التحكم ActiveX داخل حزمة Word، لذا سيحتفظ الملف المحفوظ بالوظيفة الكاملة عند فتحه في Microsoft Word.

```csharp
// Step 5: Persist the document – the ActiveX control stays embedded
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **النتيجة** – عند فتح `CommandButton.docx` في Word يظهر زر CommandButton قابل للنقر يحمل النص “Click Me”. يمكن ربط العنصر ماكروًا عبر واجهة Word (`Developer → Design Mode → Properties`).

## قائمة المصدر الكاملة

دمج جميع الخطوات معًا ينتج برنامجًا واحدًا مستقلًا يمكنك نسخه، لصقه، وتشغيله.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an ActiveX CommandButton at the desired location
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new RectangleF(100, 100, 120, 30));

        // Set the button's caption and internal name
        commandButton.Caption = "Click Me";
        commandButton.Name = "btnClick";

        // Save the document – the control is preserved
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### الناتج المتوقع

تشغيل البرنامج يطبع سطر تأكيد:

```
Document saved to C:\Temp\CommandButton.docx
```

عند فتح الملف المُنشأ في Microsoft Word، سترى **CommandButton** موضعًا عند الإحداثيات المحددة. النقر على الزر في وضع التصميم يميزه؛ وفي وضع التشغيل يتصرف كأي زر ActiveX قياسي.

## الاختلافات الشائعة وحالات الحافة

| السيناريو | التعديل |
|----------|------------|
| **نوع عنصر تحكم مختلف** | استبدل `OleControlType.CommandButton` بـ `OleControlType.CheckBox` أو `OleControlType.OptionButton`، إلخ. |
| **عدة أزرار** | استدعِ `InsertForms2OleControl` بشكل متكرر، مع تحديث إحداثيات `RectangleF` لكل زر جديد. |
| **تحديد حجم ديناميكي** | احسب أبعاد المستطيل بناءً على حجم الصفحة (`builder.PageSetup.PageWidth`). |
| **الحفظ إلى تدفق** | استخدم `document.Save(stream, SaveFormat.Docx)` عندما تحتاج لإرجاع الملف من API ويب. |
| **تنسيق Word 97‑2003** | غيّر تنسيق الحفظ إلى `SaveFormat.Doc` لإنتاج ملف `.doc` لا يزال يضم عنصر التحكم ActiveX. |

> **نصيحة احترافية:** اختبر دائمًا المستند المُولد على نسخة Word المستهدفة، لأن الإصدارات القديمة قد تفرض إعدادات أمان تعطل عناصر التحكم ActiveX بشكل افتراضي.

## الأسئلة المتكررة

**هل يعمل هذا مع .NET Core؟**  
نعم. مكتبة Aspose.Words متعددة المنصات ومتوافقة تمامًا مع .NET Core و .NET 5/6+.

**هل يمكنني تعيين ماكرو للزر برمجيًا؟**  
الـ API لا يدمج كود VBA مباشرة. بعد توليد المستند، افتحه في Word، فعّل تبويب Developer، وسجّل أو اكتب ماكروًا يشير إلى `btnClick`.

**ماذا إذا لم يظهر الزر؟**  
تحقق من أن تبويب `Developer` مفعّل في Word وأن المستند ليس مفتوحًا في **Protected View**. كما يجب التأكد من أن إحداثيات المستطيل داخل هوامش الصفحة.

## الخلاصة

أنت الآن تعرف كيف **تنشئ عنصر تحكم ActiveX** داخل ملف Word باستخدام C#. غطى الشرح **كيفية إدراج ActiveX**، وأظهر **إضافة زر تفاعلي**، وعرض **إنشاء مستند Word** من الصفر، ووضح **إنشاء زر باستخدام الكود** الذي يبقى بعد الحفظ.  

من هنا يمكنك استكشاف أنواع ActiveX إضافية، ربط الزر بماكرو VBA، أو دمج المنطق في خدمة توليد مستندات أكبر. جرّب أحجامًا ومواقعًا وخصائص تحكم مختلفة لتتناسب مع تجربة المستخدم التي تحتاجها.

---


## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء مستند Word جديد](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [إنشاء مشروع VBA في مستند Word](/words/english/net/working-with-vba-macros/create-vba-project/)
- [إنشاء وتنسيق مستند Word في Aspose.Words for .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}