---
category: general
date: 2026-08-07
description: تعلم كيفية إضافة عنصر تحكم ActiveX في مستند Word باستخدام C#. يتضمن ربط
  ماكرو بزر وإضافة أمثلة لأزرار قابلة للنقر في Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex control
- associate macro with button
- add clickable button word
- add command button word
language: ar
lastmod: 2026-08-07
og_description: كيفية إضافة عنصر تحكم ActiveX في مستند Word باستخدام Aspose.Words.
  اتبع هذا الدليل لإدراج زر، وربط ماكرو بالزر، وإضافة كلمة زر قابلة للنقر.
og_image_alt: Screenshot showing a Word document with an ActiveX command button inserted
  via Aspose.Words
og_title: كيفية إضافة عنصر تحكم ActiveX في Word – دليل كامل بلغة C#
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  headline: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  name: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  steps:
  - name: Why each line matters
    text: '| Line | Purpose | |------|---------| | `Document doc = new Document();`
      | Instantiates a fresh Word package in memory. | | `DocumentBuilder builder
      = new DocumentBuilder(doc);` | Provides a fluent API for inserting content,
      including ActiveX controls. | | `InsertForms2OleControl` | The only Aspose.'
  - name: Common pitfalls when associating a macro
    text: '* **Macro security settings** – If the document is opened on a machine
      with strict security policies, the macro may be blocked. Provide instructions
      to lower the security level or sign the macro. * **Naming conflicts** – The
      macro name must be unique within the document’s VBA project; otherwise Word'
  - name: 'Edge case: Long captions'
    text: Word truncates captions that exceed the button’s width. To avoid clipping,
      either increase the width argument in `InsertForms2OleControl` or shorten the
      text. Testing with different languages (e.g., German or Japanese) is advisable
      because character width varies.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: كيفية إضافة عنصر تحكم ActiveX في Word باستخدام Aspose.Words – دليل خطوة بخطوة
url: /ar/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إضافة عنصر تحكم ActiveX في Word باستخدام Aspose.Words

إذا كنت بحاجة إلى **كيفية إضافة عنصر تحكم ActiveX** في ملف Microsoft Word برمجيًا، فإن هذا الدليل يوضح لك الخطوات الدقيقة باستخدام Aspose.Words for .NET. ستتعرف على كيفية إدراج زر أمر، تعيين تسميته، و**ربط ماكرو بالزر** بحيث يتفاعل العنصر عندما ينقر المستخدم عليه. في النهاية ستحصل على ملف `.docm` مُمكّن للماكرو يحتوي على زر يعمل بالكامل.

إضافة زر ActiveX هو طلب شائع عند بناء نماذج تفاعلية مثل طلبات القروض، نماذج توظيف الموظفين، أو التقارير الآلية. يشرح هذا الدليل كل سطر من الشيفرة، ويوضح **لماذا** كل خطوة مهمة، ويغطي المشكلات الشائعة التي قد تواجهها.

## المتطلبات المسبقة

* .NET 6 (أو .NET Core 3.1 / .NET Framework 4.8) مثبت.  
* رخصة صالحة لـ Aspose.Words for .NET أو مفتاح تقييم مؤقت.  
* Visual Studio 2022 (أو أي بيئة تطوير تدعم C#).  
* إلمام أساسي بماكروات Word (VBA) إذا كنت تخطط لكتابة الماكرو الذي سيُفعّل الزر.

> **نصيحة احترافية:** عند تشغيل العينة، احفظ الناتج في مجلد لديك صلاحية كتابة فيه، وإلا سيتسبب `doc.Save` في رمي استثناء.

## كيفية إضافة عنصر تحكم ActiveX في مستند Word باستخدام Aspose.Words

النواة في الحل هي برنامج C# قصير ينشئ مستندًا جديدًا، يُدرج عنصر تحكم ActiveX **CommandButton**، ويحفظ الملف كمستند مُمكّن للماكرو (`.docm`). الشيفرة كاملة وجاهزة للنسخ‑اللصق.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert an ActiveX CommandButton control (Forms2OleControl)
        // Parameters: control type, left, top, width, height (in points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            0,   // left position (points)
            0,   // top position (points)
            150, // width (points)
            30   // height (points)
        );

        // Step 3: Set the button's visible caption – this is the add clickable button word
        commandButton.Caption = "Click Me";

        // Step 4 (optional): Associate a macro with the button's click action
        // This demonstrates how to associate macro with button
        commandButton.OnAction = "MyMacro";

        // Step 5: Save the document as a macro‑enabled file to preserve the button reference
        // The file extension .docm tells Word to keep ActiveX controls and macros
        doc.Save("CommandButton.docm");
    }
}
```

### لماذا كل سطر مهم

| السطر | الغرض |
|------|---------|
| `Document doc = new Document();` | ينشئ حزمة Word جديدة في الذاكرة. |
| `DocumentBuilder builder = new DocumentBuilder(doc);` | يوفر API سلس لإدراج المحتوى، بما في ذلك عناصر تحكم ActiveX. |
| `InsertForms2OleControl` | الطريقة الوحيدة في Aspose.Words التي تنشئ عنصر تحكم ActiveX؛ تقوم بتحديد نوع العنصر (`CommandButton`) وأبعاده. |
| `commandButton.Caption = "Click Me";` | يضبط **النص المعروض على الزر القابل للنقر** الذي يراه المستخدم النهائي. بدون تسمية يظهر الزر فارغًا. |
| `commandButton.OnAction = "MyMacro";` | **ربط ماكرو بالزر** – يخبر Word أي ماكرو VBA يجب تشغيله عند النقر على العنصر. |
| `doc.Save("CommandButton.docm");` | يحفظ المستند كملف مُمكّن للماكرو؛ ملف `.docx` عادي سيزيل العنصر والماكرو. |

> **ملاحظة:** الإحداثيات (اليسار، الأعلى) تُقاس بالنقاط (1 pt ≈ 1/72 in). عدّلها لتحديد موضع الزر حيث تحتاجه في الصفحة.

## كيفية ربط ماكرو بالزر

خاصية `OnAction` تربط الزر بماكرو VBA يُدعى `MyMacro`. لا يزال عليك إنشاء ذلك الماكرو داخل ملف Word، إما يدويًا أو عن طريق حقن شيفرة VBA برمجيًا (Aspose.Words لا يكتب شيفرة VBA). إليك ماكرو بسيط يمكنك إضافته باستخدام محرر Word **Developer → Visual Basic**:

```vba
Sub MyMacro()
    MsgBox "Button clicked!", vbInformation, "ActiveX Demo"
End Sub
```

عند فتح المستخدم للملف `CommandButton.docm` والنقر على الزر، يقوم Word بتنفيذ `MyMacro` ويظهر صندوق رسالة. إذا تم ضبط أمان الماكرو على **Disable all macros without notification**, سيظهر الزر معطلاً. ننصح المستخدمين بتمكين الماكرو للمستند أو توقيع الماكرو بشهادة موثوقة.

### المشكلات الشائعة عند ربط ماكرو

* **إعدادات أمان الماكرو** – إذا تم فتح المستند على جهاز بسياسات أمان صارمة، قد يتم حظر الماكرو. قدم تعليمات لتخفيض مستوى الأمان أو توقيع الماكرو.  
* **تعارض الأسماء** – يجب أن يكون اسم الماكرو فريدًا داخل مشروع VBA الخاص بالمستند؛ وإلا سيظهر Word خطأ “duplicate procedure name”.  
* **Word 64‑bit مقابل 32‑bit** – تعمل عناصر تحكم ActiveX بنفس الطريقة، لكن محرر VBA قد يعرض رسائل تحذير مختلفة حسب نسخة Office.

## كيفية إضافة نص زر قابل للنقر إلى نموذج Word

خاصية `Caption` هي ما يراه المستخدمون على الزر. يمكنك تخصيصها أكثر:

```csharp
commandButton.Caption = "Submit Form";
commandButton.Font.Size = 10;      // Adjust font size
commandButton.Font.Name = "Arial"; // Choose a readable font
```

إذا كنت بحاجة إلى تغيير التسمية ديناميكيًا بناءً على إدخال المستخدم، يمكنك لاحقًا الوصول إلى العنصر عبر نموذج كائنات Word:

```vba
Sub UpdateButtonCaption()
    Dim btn As InlineShape
    Set btn = ActiveDocument.InlineShapes(1).OLEFormat.Object
    btn.Caption = "Updated Text"
End Sub
```

### حالة خاصة: تسميات طويلة

يقص Word التسميات التي تتجاوز عرض الزر. لتجنب القطع، إما زد قيمة عرض `InsertForms2OleControl` أو اختصر النص. يُنصح بالاختبار مع لغات مختلفة (مثل الألمانية أو اليابانية) لأن عرض الأحرف يختلف.

## كيفية إضافة نص زر أمر لأتمتة النموذج

بعيدًا عن التسمية المرئية، مفهوم **add command button word** يغطي الاسم البرمجي للعنصر. لا توفر Aspose.Words خاصية `Name` مباشرة لعناصر تحكم ActiveX، لكن يمكنك تعيين حقل `AltText`، الذي يعتبره Word معرفًا للعنصر:

```csharp
commandButton.AltText = "SubmitButton";
```

لاحقًا في VBA يمكنك الإشارة إلى الزر باستخدام قيمة `AltText` الخاصة به:

```vba
Sub FindButton()
    Dim shp As Shape
    For Each shp In ActiveDocument.Shapes
        If shp.AlternativeText = "SubmitButton" Then
            MsgBox "Found the Submit button!"
        End If
    Next shp
End Sub
```

هذه التقنية مفيدة عندما يكون لديك عدة أزرار وتحتاج إلى تمييزها برمجيًا.

## مثال كامل يعمل

فيما يلي البرنامج الكامل الذي يمكنك تجميعه وتشغيله كتطبيق Console. يتضمن تنسيقًا اختياريًا، ربط ماكرو، وكتلة تعليقات تصف كل خطوة.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class AddActiveXButton
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert an ActiveX CommandButton.
        //    left=50pt, top=100pt places the button away from the margin.
        Forms2OleControl btn = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            50,   // left
            100,  // top
            200,  // width
            40    // height
        );

        // 3️⃣ Add clickable button word (caption) and style it.
        btn.Caption = "Submit Form";
        btn.Font.Size = 11;
        btn.Font.Name = "Calibri";

        // 4️⃣ Associate macro with button – this is how to associate macro with button.
        btn.OnAction = "SubmitMacro";

        // 5️⃣ Give the control a friendly identifier (add command button word).
        btn.AltText = "SubmitButton";

        // 6️⃣ Save as macro‑enabled document.
        doc.Save("SubmitForm.docm");
    }
}
```

**النتيجة المتوقعة:** عند فتح `SubmitForm.docm` في Microsoft Word يظهر زر ذو حد أزرق يحمل التسمية *Submit Form*. النقر على الزر يُفعّل ماكرو VBA `SubmitMacro` (بشرط أن تكون قد أضفت الماكرو إلى المستند). يمكن نقل الزر، تغيير حجمه، أو تنسيقه أكثر باستخدام كائن `Forms2OleControl` نفسه.

## اختبار الحل

1. قم ببناء وتشغيل تطبيق Console C#.  
2. افتح ملف `SubmitForm.docm` المُنشأ في Word.  
3. إذا طُلب منك، فعّل الماكرو.  
4. انقر زر *Submit Form* – يجب أن ترى صندوق الرسالة المُعرف في `SubmitMacro`.

إذا ظهر الزر لكنه لا يفعل شيئًا، تحقق مرة أخرى من أن اسم الماكرو يطابق تمامًا (`SubmitMacro`) وأن أمان الماكرو لا يمنع التنفيذ.

## الأسئلة الشائعة

| السؤال | الإجابة |
|----------|--------|
| *هل يمكنني إضافة أكثر من زر ActiveX؟* | نعم. استدعِ `InsertForms2OleControl` عدة مرات مع إحداثيات مختلفة. استخدم قيم `OnAction` و `AltText` مميزة لتمييزها. |
| *هل عنصر تحكم ActiveX مرئي في Word Online؟* | لا. |

## ماذا يجب أن تتعلم بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة تعمل مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Add a New Section to Word Document | Aspose.Words for .NET](/words/english/net/document-sections/add-section/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}