---
category: general
date: 2026-07-19
description: كيفية إخفاء الشكل في Word باستخدام Aspose.Words C#. تعلم كيفية جعل الشكل
  غير مرئي فورًا وأتمتة تنظيف المستند.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- make shape invisible
language: ar
lastmod: 2026-07-19
og_description: كيفية إخفاء الشكل في Word باستخدام Aspose.Words C#. اتبع هذا الدليل
  لجعل الشكل غير مرئي وتبسيط مستنداتك.
og_image_alt: Screenshot showing a Word document where a shape has been hidden using
  C#
og_title: كيفية إخفاء الشكل في Word – دليل C# الكامل
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: How to hide shape in Word using Aspose.Words C#. Learn to make shape
    invisible instantly and automate document cleanup.
  headline: How to Hide Shape in Word with C# – Step‑by‑Step Guide
  type: TechArticle
- description: How to hide shape in Word using Aspose.Words C#. Learn to make shape
    invisible instantly and automate document cleanup.
  name: How to Hide Shape in Word with C# – Step‑by‑Step Guide
  steps:
  - name: Does the hidden flag survive conversion to PDF?
    text: Yes. When you export the document to PDF (`doc.Save("out.pdf")`), any shape
      marked as hidden is omitted from the PDF rendering. This makes the technique
      handy for creating “clean” PDFs from templates that contain optional graphics.
  - name: What if the shape is inside a header or footer?
    text: 'The same approach works. You just need to navigate to the header/footer’s
      child nodes:'
  - name: Can I toggle visibility at runtime based on user input?
    text: 'Absolutely. Since `Hidden` is a regular Boolean, you can set it conditionally:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shape manipulation
title: كيفية إخفاء الشكل في Word باستخدام C# – دليل خطوة بخطوة
url: /ar/net/programming-with-shapes/how-to-hide-shape-in-word-with-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية إخفاء الشكل في Word – دليل C# كامل

هل تساءلت يومًا **عن كيفية إخفاء الشكل** في ملف Word دون حذفه يدويًا؟ لست وحدك. في العديد من سيناريوهات التقارير الآلية قد ترغب في الاحتفاظ بصورة عنصر نائب لأغراض التخطيط ولكن منع ظهورها في ملف PDF أو DOCX النهائي الذي ترسله إلى العملاء.  

في هذا الدليل سنستعرض حلًا مختصرًا وجاهزًا للإنتاج باستخدام **Aspose.Words for .NET** يتيح لك **إخفاء الشكل في Word** برمجيًا. بنهاية القراءة ستعرف بالضبط كيف تجعل الشكل غير مرئي، ولماذا تُعد خاصية الإخفاء مهمة، وكيفية التحقق من النتيجة بسطر واحد من الشيفرة.

> **نصيحة احترافية:** خاصية الإخفاء تعمل على أي كائن رسم—صور، مربعات نص، أو حتى WordArt—لذا فإن التقنية تتجاوز المثال البسيط الذي سنستخدمه.

---

## المتطلبات المسبقة

قبل الغوص في التفاصيل، تأكد من وجود ما يلي:

- نسخة حديثة من **.NET 6** أو أحدث (تعمل الواجهة البرمجية أيضًا على .NET Framework).
- **Aspose.Words for .NET** مثبت عبر NuGet (`Install-Package Aspose.Words`).
- مستند Word (`WithShape.docx`) يحتوي بالفعل على شكل واحد على الأقل.
- Visual Studio، Rider، أو أي محرر C# تفضله.

لا توجد مكتبات إضافية مطلوبة؛ كل شيء آخر موجود داخل تجميع Aspose.Words.

---

## الخطوة 1: تحميل المستند – نقطة الانطلاق لإخفاء الشكل

أول ما عليك فعله هو فتح ملف Word الذي يحتوي على الشكل الذي تريد إخفائه. هذه هي الأساس لأي عملية **إخفاء شكل في Word** لأن الواجهة البرمجية تعمل على نموذج في الذاكرة للمستند.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load the existing document that already has a shape.
Document doc = new Document(@"C:\Docs\WithShape.docx");
```

> **لماذا هذا مهم:** تحميل المستند يُنشئ كائن `Document` يعكس بنية الملف (الأقسام، الفقرات، الرسومات). بدون هذا الكائن لا يمكنك الوصول إلى عقدة الشكل لتعيين رؤيته.

---

## الخطوة 2: استرجاع الشكل – استهداف الكائن المحدد للإخفاء

بعد ذلك، حدد الشكل الذي تنوي إخفائه. تتعامل Aspose.Words مع كل عنصر رسم كعقدة `Shape`، ويمكنك جلبها حسب الفهرس أو الاسم. للتبسيط، سنأخذ أول شكل في المستند.

```csharp
// Retrieve the first shape node (index 0) from the document tree.
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
```

> **تنبيه حالة حافة:** إذا كان المستند لا يحتوي على أي أشكال، فإن `GetChild` تُعيد `null` وستؤدي عملية التحويل إلى استثناء. احرص دائمًا على التعامل مع هذا في الشيفرة الإنتاجية:

```csharp
if (shape == null)
{
    Console.WriteLine("No shape found – nothing to hide.");
    return;
}
```

---

## الخطوة 3: إخفاء الشكل – جعله غير مرئي في الناتج

الآن نصل إلى جوهر الدرس: **جعل الشكل غير مرئي**. تُوفر Aspose.Words خاصية منطقية `Hidden` في فئة `Shape`. تعيينها إلى `true` يخبر Word بمعاملة الرسم كخفي، مما يعني أنه لن يظهر عند فتح الملف في الواجهة ولا عند حفظه بصيغة أخرى.

```csharp
// Mark the shape as hidden so it won't be displayed.
shape.Hidden = true;
```

> **لماذا نستخدم `Hidden` بدلًا من الحذف؟** الحذف يزيل العقدة تمامًا، ما قد يُعطل حسابات التخطيط التي تعتمد على أبعاد الشكل. الأشكال المخفية تبقى في شجرة DOM، تحافظ على المسافات بينما تظل غير مرئية—مثالية للمحتوى الشرطي.

---

## الخطوة 4: حفظ المستند – التحقق من أن الشكل لم يعد مرئيًا

أخيرًا، اكتب المستند المعدل مرة أخرى إلى القرص (أو إلى تدفق). عند فتح الملف المحفوظ، ستلاحظ أن الشكل قد اختفى، مما يؤكد أنك نجحت في **جعل الشكل غير مرئي**.

```csharp
// Save the updated document; the shape will now be hidden.
doc.Save(@"C:\Docs\ShapeHidden.docx");
Console.WriteLine("Document saved – the shape is now hidden.");
```

> **الناتج المتوقع:** افتح `ShapeHidden.docx` في Microsoft Word. المنطقة التي كان فيها الشكل ستكون فارغة، لكن النص المحيط سيحتفظ بتخطيطه الأصلي.

---

## إضافي: إخفاء عدة أشكال مرة واحدة

غالبًا ما تحتاج إلى إخفاء **جميع الأشكال** التي تستوفي شرطًا معينًا (مثل الأشكال ذات `AlternativeText` محدد). إليك حلقة سريعة توضح النمط:

```csharp
// Hide every shape whose AlternativeText contains "temp".
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape s in shapes)
{
    if (s.AlternativeText?.Contains("temp") == true)
        s.Hidden = true;
}
doc.Save(@"C:\Docs\AllTempShapesHidden.docx");
```

> **اجعل الشكل غير مرئي** على نطاق واسع دون الحاجة للبحث عن كل فهرس يدويًا—مثالي للتقارير الكبيرة.

---

## تأكيد بصري (اختياري)

إذا كنت تفضل إشارة بصرية، يمكنك تضمين لقطة شاشة في وثائقك. أدناه صورة بديلة تُظهر حالة قبل/بعد.

![How to hide shape in Word](/images/hide-shape-word.png "How to hide shape in Word – before and after the hidden flag")

*النص البديل:* *كيفية إخفاء الشكل في Word – يختفي الشكل بعد تعيين خاصية Hidden.*

---

## أسئلة شائعة ومشكلات محتملة

### هل تبقى خاصية الإخفاء بعد التحويل إلى PDF؟

نعم. عند تصدير المستند إلى PDF (`doc.Save("out.pdf")`)، أي شكل مُعلم كخفي يُستبعد من عرض PDF. تجعل هذه التقنية مفيدة لإنشاء ملفات PDF “نظيفة” من قوالب تحتوي على رسومات اختيارية.

### ماذا لو كان الشكل داخل رأس أو تذييل الصفحة؟

نفس النهج يعمل. عليك فقط الانتقال إلى عقد الأطفال في الرأس/التذييل:

```csharp
HeaderFooter header = (HeaderFooter)doc.GetChild(NodeType.HeaderFooter, 0, true);
Shape headerShape = (Shape)header.GetChild(NodeType.Shape, 0, true);
headerShape.Hidden = true;
```

### هل يمكن تبديل الرؤية في وقت التشغيل بناءً على مدخلات المستخدم؟

بالطبع. بما أن `Hidden` هو قيمة منطقية عادية، يمكنك تعيينه شرطيًا:

```csharp
shape.Hidden = userWantsShape ? false : true;
```

---

## ملخص

غطينا **كيفية إخفاء الشكل** في مستند Word باستخدام Aspose.Words for .NET:

1. تحميل المستند الذي يحتوي على الشكل.  
2. استرجاع عقدة `Shape` المستهدفة.  
3. تعيين `shape.Hidden = true` لجعل الشكل غير مرئي.  
4. حفظ الملف والتحقق من النتيجة.

هذه الخطوات الأربعة تمنحك طريقة موثوقة وقابلة للتكرار **لإخفاء الشكل في Word** دون كسر التخطيط أو فقدان العقدة الأساسية.

---

## الخطوات التالية

- **استكشاف التنسيق الشرطي:** دمج خاصية الإخفاء مع حقول دمج البريد لإظهار أو إخفاء الرسومات بناءً على البيانات.  
- **أتمتة المعالجة الدفعية:** حلقة عبر مجلد من المستندات وتطبيق نفس المنطق على كل ملف.  
- **التعمق في Aspose.Words:** التعرف على خصائص `Shape` مثل `WrapType`، `Rotation`، و`ImageData` للتحكم الكامل في كائنات الرسم.

إذا وجدت هذا الدليل مفيدًا، يمكنك الاطلاع على دليلنا حول **كيفية استبدال الصور في Word باستخدام C#** أو المقالة حول **إنشاء جداول ديناميكيًا باستخدام Aspose.Words**. كلا الموضوعين يبنيان على مفاهيم نموذج كائن المستند التي استخدمناها هنا.

برمجة سعيدة، وتمتع بملفات Word منظمة ومهنية!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شاملة مع شيفرات تعمل خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}