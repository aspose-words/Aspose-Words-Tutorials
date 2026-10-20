---
category: general
date: 2026-10-20
description: إنشاء مستند Word برمجيًا وإضافة زر أمر باستخدام Aspose.Words. تعلم كيفية
  إدراج عنصر تحكم ActiveX وتعيين تسمية الزر.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add command button
- add activex control
- insert activex button
- set button caption
language: ar
lastmod: 2026-10-20
og_description: إنشاء مستند Word برمجيًا وإدراج زر أمر ActiveX. يشرح هذا الدرس كيفية
  إدراج التحكم وتعيين التسمية الخاصة به باستخدام Aspose.Words.
og_image_alt: Word file showing an ActiveX command button inserted by Aspose.Words
og_title: إنشاء مستند Word برمجيًا – إضافة زر ActiveX
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  headline: Create Word document programmatically with an ActiveX button
  type: TechArticle
- description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  name: Create Word document programmatically with an ActiveX button
  steps:
  - name: 'Open a terminal or Visual Studio and create a new console project:'
    text: 'Open a terminal or Visual Studio and create a new console project:'
  - name: 'Add the Aspose.Words package:'
    text: 'Add the Aspose.Words package:'
  - name: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
    text: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
  - name: Open `ActiveXCommandButton.docx` in Microsoft Word.
    text: Open `ActiveXCommandButton.docx` in Microsoft Word.
  - name: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
    text: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
  - name: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
    text: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
  - name: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
    text: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: إنشاء مستند Word برمجيًا باستخدام زر ActiveX
url: /ar/net/working-with-oleobjects-and-activex/create-word-document-programmatically-with-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word برمجيًا باستخدام زر ActiveX

أنشئ مستند Word برمجيًا باستخدام Aspose.Words، ثم أضف زر أمر يمكن للمستخدمين النقر عليه. يوضح لك هذا الدليل كيفية إدراج عنصر تحكم ActiveX، وتكوين خصائصه، وحفظ النتيجة كملف **.docx**.

سترى مثالًا كاملًا قابلاً للتنفيذ يمكنك نسخه إلى تطبيق كونسول. بحلول نهاية الدليل ستتمكن من إنشاء ملف Word يحتوي على زر أمر يعمل بالكامل، وستفهم كيفية **add command button**، **add activex control**، **insert activex button**، و **set button caption** دون مغادرة كود C# الخاص بك.

## المتطلبات المسبقة

* .NET 6.0 SDK أو أحدث مثبت  
* Visual Studio 2022 (أو أي بيئة تطوير متوافقة مع C#)  
* ملف ترخيص Aspose.Words لـ .NET (الإصدار التجريبي المجاني يعمل لهذا المثال)  
* إلمام أساسي بـ C# ونظام مشاريع .NET  

لا توجد حزم NuGet إضافية مطلوبة بخلاف **Aspose.Words** لأن دعم ActiveX مدمج في المكتبة.

## الخطوة 1: إعداد المشروع وإضافة Aspose.Words

1. افتح الطرفية أو Visual Studio وأنشئ مشروع كونسول جديد:

   ```bash
   dotnet new console -n WordActiveXDemo
   cd WordActiveXDemo
   ```

2. أضف حزمة Aspose.Words:

   ```bash
   dotnet add package Aspose.Words
   ```

3. (اختياري) إذا كان لديك ملف ترخيص، ضعّه في جذر المشروع وأضف السطر التالي في بداية `Program.cs` لتجنب علامات مائية التقييم:

   ```csharp
   Aspose.Words.License license = new Aspose.Words.License();
   license.SetLicense("Aspose.Words.lic");
   ```

## الخطوة 2: إنشاء مستند Word برمجيًا – تهيئة المستند

العملية الأولى هي **create Word document programmatically**. تقوم بذلك بإنشاء كائن `Document` و`DocumentBuilder` يتيح لك تعديل محتوى المستند.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;   // Provides ActiveX control types
using System.Drawing;        // For Point and Size structs

// Initialize a new blank document
Document document = new Document();

// DocumentBuilder gives a cursor‑based API for inserting elements
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` يمثل الملف بالكامل، بينما `DocumentBuilder` يحتفظ بمؤشر يمكنك تحريكه إلى أي موقع في المستند. هذا الفصل يحافظ على نظافة الـ API ويسمح لك بـ **add activex control** لاحقًا دون الحاجة لإدارة الهياكل منخفضة المستوى يدويًا.

## الخطوة 3: إضافة زر أمر – إدراج عنصر تحكم ActiveX

الآن ستقوم بـ **add command button** عن طريق إدراج عنصر تحكم ActiveX من النوع `OleControlType.CommandButton`. تتطلب طريقة `InsertForms2OleControl` نوع العنصر، موقعًا (`Point`)، وحجمًا (`Size`).

```csharp
// Define where the button will appear (X = 100 pt, Y = 150 pt)
Point buttonPosition = new Point(100, 150);

// Define the button dimensions (width = 120 pt, height = 30 pt)
Size buttonSize = new Size(120, 30);

// Insert the ActiveX command button at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton, // control type
    buttonPosition,              // position
    buttonSize);                 // size
```

النداء أعلاه **insert activex button** في المستند عند الإحداثيات الدقيقة التي تحددها. تُقاس الإحداثيات بالنقاط (1 pt ≈ 1/72 in). إذا كنت بحاجة إلى الزر في فقرة محددة، حرّك مؤشر الـ builder أولاً:

```csharp
builder.Writeln("Click the button below:");
builder.MoveToDocumentEnd(); // places the cursor after the paragraph
```

## الخطوة 4: تعيين تسمية الزر – تخصيص نص زر الأمر

الزر بدون تسمية يسبب ارتباكًا، لذا ستقوم بـ **set button caption** إلى شيء ذي معنى. خاصية `Caption` تحدد النص المعروض على الزر، بينما `Name` يمنح العنصر معرفًا برمجيًا.

```csharp
// Give the button a unique name for later reference
commandButton.Name = "btnSubmit";

// Set the visible text on the button
commandButton.Caption = "Submit";

// Optional: assign a macro name that Word will call when the button is clicked
commandButton.OnClick = "SubmitForm()";
```

إذا صدرت المستند لاحقًا إلى تنسيق يدعم الماكرو (`.docm`)، يجب أن تتطابق قيمة `OnClick` مع اسم ماكرو VBA. بالنسبة إلى ملف `.docx` عادي، تُحفظ الخاصية ولكن لا تُنفّذ، وهذا مناسب لمعظم سيناريوهات الأتمتة.

## الخطوة 5: حفظ المستند الذي يحتوي على زر ActiveX

بعد تكوين العنصر، يمكنك **save the document**. اختر دليلًا لديك صلاحية كتابة فيه، واستخدم امتداد `.docx` لأقصى توافق.

```csharp
// Replace with your desired output folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ActiveXCommandButton.docx");

// Save the document to disk
document.Save(outputPath);
```

عند فتح الملف المُنشأ في Microsoft Word، سترى زرًا مُسمى **Submit** عند الإحداثيات التي حددتها. النقر على الزر في عميل سطح المكتب سيحاول تشغيل ماكرو `SubmitForm` (إذا كان موجودًا).

## الخطوة 6: التحقق من النتيجة وحل المشكلات الشائعة

1. افتح `ActiveXCommandButton.docx` في Microsoft Word.  
2. انتقل إلى **Design Mode** (علامة تبويب Developer → **Design Mode**) لرؤية حدود الزر.  
3. إذا لم يظهر الزر، تحقق من تمكين علامة تبويب **Developer** وأن نسخة Word الخاصة بك تدعم عناصر تحكم ActiveX.  
4. بالنسبة للملفات التي تدعم الماكرو (`.docm`)، تأكد من أن اسم الماكرو في `OnClick` يتطابق مع روتين VBA؛ وإلا سيظهر تحذير أمان في Word.

### نصيحة احترافية

عناصر تحكم ActiveX متاحة فقط على Windows. إذا كنت بحاجة إلى تفاعل عبر المنصات، فكر في استخدام **Content Controls** (`RichTextContentControl`) بدلاً من زر ActiveX.

## الكود الكامل

فيما يلي البرنامج الكامل الجاهز للتنفيذ. انسخه إلى `Program.cs` وشغّل `dotnet run`.



## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مصدر يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إنشاء مستند Word مع زر ActiveX – دليل C#](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)
- [إضافة زر أمر إلى مستند Word باستخدام Aspose.Words – دليل كامل](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)
- [إنشاء زر مستند Word باستخدام Aspose.Words – مثال كامل على الكود](/words/english/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}