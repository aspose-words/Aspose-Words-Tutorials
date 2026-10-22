---
category: general
date: 2026-10-07
description: تعلم كيفية إضافة عنصر تحكم المحتوى في مستند Word باستخدام Aspose.Words.
  يشرح هذا الدليل أيضًا كيفية إنشاء عنصر تحكم المحتوى لحقل معرف الموظف.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add content control word
- how to create content control
- add employee id field
- Aspose.Words content control
- C# Structured Document Tag
language: ar
lastmod: 2026-10-07
og_description: أضف عنصر تحكم المحتوى في مستند Word باستخدام Aspose.Words. اتبع هذا
  الدرس الكامل لتتعلم كيفية إنشاء عنصر تحكم المحتوى وإضافة حقل معرف الموظف.
og_image_alt: Screenshot of a Word document showing an employee ID content control
  created with Aspose.Words
og_title: إضافة عنصر تحكم المحتوى في Word باستخدام Aspose.Words – دليل خطوة بخطوة
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to add content control word in a Word document with Aspose.Words.
    This guide also explains how to create content control for an employee ID field.
  headline: How to add content control word in a Word document using Aspose.Words
  type: TechArticle
- description: Learn how to add content control word in a Word document with Aspose.Words.
    This guide also explains how to create content control for an employee ID field.
  name: How to add content control word in a Word document using Aspose.Words
  steps:
  - name: Open `EmployeeForm.docx` in Word.
    text: Open `EmployeeForm.docx` in Word.
  - name: Click the gray box that says **Enter ID** – it should be replaced by **12345**.
    text: Click the gray box that says **Enter ID** – it should be replaced by **12345**.
  - name: Open the **Developer** tab → **Design Mode** to see the control’s properties
      (Title = *EmployeeID*).
    text: Open the **Developer** tab → **Design Mode** to see the control’s properties
      (Title = *EmployeeID*).
  type: HowTo
tags:
- Aspose.Words
- content control
- C#
title: كيفية إضافة عنصر تحكم المحتوى في مستند Word باستخدام Aspose.Words
url: /ar/net/programming-with-sdt/how-to-add-content-control-word-in-a-word-document-using-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إضافة كلمة تحكم المحتوى في مستند Word باستخدام Aspose.Words

إذا كنت بحاجة إلى **إضافة كلمة تحكم المحتوى** إلى ملف Word، يوضح لك هذا الدرس بالضبط كيفية القيام بذلك باستخدام مكتبة Aspose.Words لـ .NET. سواءً كنت تبني مستندًا شبيهًا بنموذج أو تقوم بأتمتة إدخال البيانات، ستتعلم **كيفية إنشاء تحكم محتوى** يلتقط معرف الموظف في خطوة واحدة.

في هذا الدليل ستقوم بـ:

* إنشاء مستند Word فارغ برمجيًا.  
* إدراج Structured Document Tag (SDT) نص عادي يعمل كتحكم محتوى.  
* ملء التحكم بمعرف الموظف وحفظ الملف.  

المتطلبات المسبقة الوحيدة هي نسخة حديثة من .NET (يفضل 4.6+) ورخصة Aspose.Words (أو النسخة التجريبية المجانية). لا توجد حزم NuGet إضافية مطلوبة بخلاف `Aspose.Words`.

## إضافة كلمة تحكم المحتوى باستخدام Aspose.Words

الخطوة الرئيسية الأولى هي إنشاء تحكم المحتوى نفسه. في Aspose.Words يُمثَّل **تحكم المحتوى** بواسطة الفئة `StructuredDocumentTag`. بإضافة SDT إلى المستند، فإنك فعليًا **تضيف كلمة تحكم المحتوى** التي يمكن تحريرها لاحقًا في Microsoft Word أو معالجتها برمجيًا.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// 1️⃣ Create a new blank document and a DocumentBuilder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*لماذا هذا مهم*: يوفر لك `DocumentBuilder` واجهة تشبه المؤشر تتيح لك إدراج العقد (فقرات، جداول، SDTs، إلخ) في الموضع الحالي. بدءًا من مستند نظيف يضمن ظهور تحكم المحتوى بالضبط حيث تريد.

## كيفية إنشاء تحكم محتوى لحقل معرف الموظف

بعد ذلك، قم بتهيئة الـ SDT ليعمل كتحكم محتوى نص عادي سيحمل معرف الموظف. خاصية `Title` هي ما يعرضه Word في لوحة **Properties**، بينما `PlaceholderName` تقدم تلميحًا للمستخدم.

```csharp
// 2️⃣ Create a plain‑text Structured Document Tag (SDT) and set its metadata
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true);
sdt.Title = "EmployeeID";            // Visible title in Word's UI
sdt.PlaceholderName = "Enter ID";    // Placeholder text shown when empty
```

*لماذا هذا مهم*: ضبط `Title` إلى **EmployeeID** يجعل التحكم يصف نفسه، وهو مفيد عندما تقوم باستخراج القيم لاحقًا باستخدام `StructuredDocumentTag.GetText()`. يُحسّن العنصر النائب تجربة المستخدم النهائي من خلال الإشارة إلى الصيغة المتوقعة.

### إضافة حقل معرف الموظف داخل تحكم المحتوى

الآن قم بإدراج الـ SDT في المستند عند الموقع الحالي للـ builder واكتب رقم الموظف الافتراضي.

```csharp
// 3️⃣ Insert the SDT into the document at the current builder position
builder.InsertNode(sdt);

// 4️⃣ Add default content inside the SDT (e.g., an employee ID)
builder.Writeln("12345");   // This text becomes the initial value of the control
```

*لماذا هذا مهم*: تقوم `InsertNode` بوضع الـ SDT في شجرة المستند. الـ `Writeln` اللاحق يكتب المحتوى **داخل** التحكم لأن مؤشر الـ builder لا يزال داخل عقدة الـ SDT. إذا استدعيت `Writeln` قبل إدراج الـ SDT، سيظهر النص خارج التحكم.

## حفظ المستند والتحقق من تحكم المحتوى

أخيرًا، احفظ المستند على القرص. سيحتوي ملف `.docx` المحفوظ على تحكم المحتوى الذي يمكنك فتحه في Microsoft Word لرؤية العنصر النائب ومعرف الموظف الافتراضي.

```csharp
// 5️⃣ Save the document with the SDT to a file
doc.Save(@"C:\Temp\EmployeeForm.docx");
```

*لماذا هذا مهم*: استخدام مسار مطلق أو نسبي يتيح لك التحكم في مكان حفظ الملف. تقوم Aspose.Words تلقائيًا بكتابة أجزاء XML اللازمة لتحكم المحتوى، لذا لا خطوات إضافية مطلوبة.

### خطوات التحقق السريعة

1. افتح `EmployeeForm.docx` في Word.  
2. انقر على الصندوق الرمادي الذي يقول **Enter ID** – يجب أن يُستبدل بـ **12345**.  
3. افتح تبويب **Developer** → **Design Mode** لرؤية خصائص التحكم (Title = *EmployeeID*).

إذا لم يظهر التحكم، تأكد من أنك تستخدم Aspose.Words ≥ 23.10؛ الإصدارات الأقدم كان لديها توقيع مُنشئ مختلف لـ `StructuredDocumentTag`.

## تنويعات اختيارية وحالات حافة

| السيناريو | كيفية تعديل الشيفرة |
|----------|-----------------------|
| **استخدام تحكم نص غني** بدلاً من نص عادي | غيّر `SdtType.PlainText` إلى `SdtType.RichText`. |
| **إضافة التحكم إلى مستند موجود** | حمّل الملف باستخدام `new Document("Existing.docx")` وضع الـ builder عند العلامة المرجعية المطلوبة قبل إدراج الـ SDT. |
| **قفل تحكم المحتوى بحيث لا يتمكن المستخدمون من تعديل القيمة** | اضبط `sdt.LockContentControl = true;` بعد إنشاء الـ SDT. |
| **تطبيق علامة مخصصة لاستخراج لاحق** | استخدم `sdt.Tag = "EmpIdTag";` ثم استرجعها لاحقًا بـ `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`. |
| **تعيين تحكم محتوى متكرر (معرفات متعددة)** | أنشئ الـ SDT داخل صف جدول وكرّر الصف حسب الحاجة. |

**نصيحة احترافية**: احرص دائمًا على تحرير كائن `Document` (أو وضعه داخل كتلة `using`) عند العمل في خدمة طويلة التشغيل لتحرير الموارد الأصلية بسرعة.

## الخلاصة

أنت الآن تعرف **كيفية إضافة كلمة تحكم المحتوى** إلى مستند Word باستخدام Aspose.Words، وكيف **إنشاء تحكم محتوى** يلتقط معرف الموظف، وكيف **إضافة حقل معرف الموظف** برمجيًا. باتباع الخطوات أعلاه يمكنك دمج حقول منظمة وقابلة للتحرير في أي مستند تُنشئه، مما يسهل جمع أو عرض البيانات بصيغة متسقة.

بعد ذلك، استكشف المواضيع ذات الصلة مثل **ربط تحكمات المحتوى ببيانات XML**، **إنشاء تحكمات محتوى متكررة للجداول**، أو **استخدام Aspose.Words API لاستخراج القيم من التحكمات المملوءة**. هذه الإضافات تتيح لك بناء نماذج Word مدفوعة بالبيانات دون الحاجة إلى فتح الملف يدويًا. Happy coding!

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Add a Check Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}