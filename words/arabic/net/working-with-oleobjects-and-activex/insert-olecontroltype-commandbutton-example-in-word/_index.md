---
category: general
date: 2026-08-17
description: إدراج مثال OleControlType.CommandButton في Word باستخدام Aspose.Words.
  تعلّم كيفية إضافة عناصر تحكم النماذج إلى مستند Word برمجيًا.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert olecontroltype.commandbutton example
- how to add form controls to word document
- Aspose.Words ActiveX button
- C# Word automation
- programmatic form controls
language: ar
lastmod: 2026-08-17
og_description: إدراج مثال OleControlType.CommandButton في Word باستخدام Aspose.Words.
  اتبع هذا الدليل لإضافة عناصر التحكم في النماذج إلى مستند Word.
og_image_alt: Screenshot showing an ActiveX CommandButton inserted into a Word document
  using Aspose.Words
og_title: إدراج مثال OleControlType.CommandButton في Word
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: Insert OleControlType.CommandButton example in Word using Aspose.Words.
    Learn how to add form controls to a Word document programmatically.
  headline: Insert OleControlType.CommandButton example in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: إدراج مثال OleControlType.CommandButton في Word
url: /ar/net/working-with-oleobjects-and-activex/insert-olecontroltype-commandbutton-example-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إدراج مثال OleControlType.CommandButton في Word

إذا كنت بحاجة إلى **إدراج مثال OleControlType.CommandButton** في ملف Word، فإن هذا الدليل يوضح لك كيفية القيام بذلك. ستتعلم **كيفية إضافة عناصر تحكم النماذج إلى مستند Word** باستخدام Aspose.Words، مع برنامج C# كامل وقابل للتنفيذ.

تسمح لك عناصر التحكم مثل أزرار ActiveX بإنشاء قوالب Word تفاعلية—مفيدة للعقود، الاستبيانات، أو الأدوات الداخلية. تغطي الخطوات أدناه كل شيء من إعداد المشروع إلى التحقق من ظهور الزر بشكل صحيح في ملف `.docx` المحفوظ.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

- .NET 6.0 SDK أو أحدث مثبت  
- Visual Studio 2022 (أو أي بيئة تطوير C#)  
- ترخيص Aspose.Words for .NET أو ترخيص تجريبي مؤقت مجاني  
- إلمام أساسي بـ C# ومفاهيم ملفات Word  

> **نصيحة احترافية:** إذا كنت تستخدم النسخة التجريبية المجانية، ضع ملف الترخيص في نفس المجلد مع الملف التنفيذي وحمّله في بداية `Main`.

## الخطوة 1: إنشاء مشروع وحدة تحكم جديد وإضافة Aspose.Words

افتح الطرفية ونفّذ:

```bash
dotnet new console -n OleCommandButtonDemo
cd OleCommandButtonDemo
dotnet add package Aspose.Words
```

هذا ينشئ مشروعًا نظيفًا ويسحب أحدث حزمة Aspose.Words، التي توفر واجهات `Document`، `DocumentBuilder`، و`InsertForms2OleControl` اللازمة لـ **إدراج مثال OleControlType.CommandButton**.

## الخطوة 2: كتابة البرنامج الكامل

أنشئ أو استبدل `Program.cs` بالكود التالي. يحتوي على جميع توجيهات `using` المطلوبة، تحميل الترخيص، وسير العمل المكوَّن من أربع خطوات كما في المقتطف الأصلي.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;          // For OleControlType

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Optional: load a trial or commercial license.
        // -------------------------------------------------
        // var license = new Aspose.Words.License();
        // license.SetLicense("Aspose.Words.lic");

        // -------------------------------------------------
        // Step 1: Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // Step 2: Initialize a DocumentBuilder to work with the document
        // -------------------------------------------------
        DocumentBuilder builder = new DocumentBuilder(doc);

        // -------------------------------------------------
        // Step 3: Insert an ActiveX CommandButton control
        // -------------------------------------------------
        // OleControlType.CommandButton creates a CommandButton.
        // "ClickMe" is the control's name.
        // The Rectangle defines the button's position (x, y) and size (width, height).
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "ClickMe",
            new Rectangle(100, 100, 80, 30));

        // -------------------------------------------------
        // Step 4: Save the document containing the ActiveX button
        // -------------------------------------------------
        string outputPath = "ActiveXButton.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### لماذا كل سطر مهم

* **تحميل الترخيص** – يضمن عدم تقييدك بقيود التقييم.  
* **`Document doc = new Document();`** – ينشئ الحاوية لكل محتوى Word؛ هذا هو أساس **إدراج مثال OleControlType.CommandButton**.  
* **`DocumentBuilder builder = new DocumentBuilder(doc);`** – يوفر واجهة برمجة تطبيقات سلسة لإضافة النصوص، الصور، والعناصر.  
* **`InsertForms2OleControl`** – الطريقة الأساسية التي تنفّذ **كيفية إضافة عناصر تحكم النماذج إلى مستند Word**. قيمة التعداد `OleControlType.CommandButton` تخبر Aspose.Words بإنشاء زر ActiveX.  
* **`new Rectangle(100, 100, 80, 30)`** – يضع الزر على بعد 100 نقطة من الهوامش اليسرى والعلوية، بعرض 80 نقطة وارتفاع 30 نقطة. عدّل هذه القيم لتناسب تخطيطك.  
* **`doc.Save`** – يكتب ملف .docx إلى القرص؛ الملف الآن يحتوي على الزر المدمج.

## الخطوة 3: بناء البرنامج وتشغيله

من مجلد المشروع، نفّذ:

```bash
dotnet run
```

يجب أن ترى رسالة في وحدة التحكم:

```
Document saved to ActiveXButton.docx
```

افتح `ActiveXButton.docx` في Microsoft Word. سترى زرًا يحمل التسمية **ClickMe** موضعه تقريبًا في وسط الصفحة. النقر على الزر يُفعِّل السلوك الافتراضي لـ ActiveX (وهو عادةً لا يفعل شيئًا ما لم تُرفق ماكرو).

![insert olecontroltype.commandbutton example](/images/activex-button.png "تم إدراج زر ActiveX CommandButton في مستند Word")

*نص بديل للصورة:* insert olecontroltype.commandbutton example – زر ActiveX CommandButton معروض في مستند Word.

## الخطوة 4: تخصيص الزر (اختياري)

ينشئ **إدراج مثال OleControlType.CommandButton** زرًا افتراضيًا. يمكنك تعديل التسمية، الخط، أو حتى إرفاق ماكرو عن طريق تعديل كائن OLE الأساسي. فيما يلي طريقة مختصرة لتغيير تسمية الزر بعد الإدراج:

```csharp
// Retrieve the first shape (our button) from the document
Shape buttonShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

// Access the OLE format and set the caption
buttonShape.OleFormat.GetControl().SetProperty("Caption", "Submit");
```

> **ملاحظة:** يتطلب التلاعب المباشر بخصائص OLE فهم واجهة COM الأساسية. في معظم السيناريوهات، تكون التسمية الافتراضية كافية.

## الخطوة 5: المشكلات الشائعة وكيفية تجنّبها

| المشكلة | السبب | الحل |
|--------|-------|------|
| الزر لا يظهر في Word | تم حفظ المستند كـ `.docx` ولكن تم فتحه في عارض يزيل عناصر OLE (مثل Google Docs). | افتح الملف في Microsoft Word أو Word Online مع صلاحيات التحرير. |
| خطأ وقت التشغيل `ArgumentOutOfRangeException` | إحداثيات `Rectangle` خارج هوامش الصفحة. | استخدم قيمًا داخل حجم الصفحة (مثال: 0‑500 لـ A4). |
| استثناء الترخيص | ينتهي الترخيص التجريبي بعد 30 يومًا. | حمّل ملف ترخيص صالح أو اطلب نسخة تجريبية ممتدة من Aspose. |

## الخطوة 6: كيف يتناسب هذا المثال مع مشاريع الأتمتة الأكبر

عندما تحتاج إلى **كيفية إضافة عناصر تحكم النماذج إلى مستند Word** على نطاق واسع—مثل توليد مئات قوالب العقود—قم بلف منطق الإدراج في طريقة قابلة لإعادة الاستخدام:

```csharp
static void AddCommandButton(DocumentBuilder builder, string name, Rectangle bounds)
{
    builder.InsertForms2OleControl(OleControlType.CommandButton, name, bounds);
}
```

يمكنك بعد ذلك استدعاء `AddCommandButton` داخل حلقات تعالج صفوف البيانات، مما يضمن أن كل مستند مُولَّد يحتوي على زر باسم فريد (مثل `Approve_001`، `Approve_002`).

## الخلاصة

الآن لديك مثال كامل لـ **إدراج مثال OleControlType.CommandButton** يُظهر **كيفية إضافة عناصر تحكم النماذج إلى مستند Word** باستخدام Aspose.Words for .NET. غطّى الدليل إعداد المشروع، الكود الكامل، نصائح التخصيص، وخطوات استكشاف الأخطاء الشائعة.

من هنا يمكنك استكشاف:

- إضافة أنواع تحكم أخرى مثل **CheckBox** أو **ComboBox** (`OleControlType.CheckBox`، `OleControlType.ComboBox`).  
- ربط الزر بماكرو VBA لتفاعلية أغنى.  
- توليد ملفات PDF من نفس المستند مع الحفاظ على حقول النموذج.

جرّب أحجامًا، مواضع، وأسماء تحكم مختلفة لتناسب حالتك الخاصة. happy coding!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [Insert Combo Box Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-combo-box-form-field/)
- [Insert Check Box Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)
- [Insert Text Input Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}