---
category: general
date: 2026-07-23
description: إنشاء مستند Word فارغ وإضافة شكل مستطيل باستخدام C#. تعلم كيفية إدراج
  الأشكال وتجميعها في Word باستخدام Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- group shapes word
- how to insert shapes
- how to group shapes
language: ar
lastmod: 2026-07-23
og_description: إنشاء مستند Word فارغ في C# وتعلم كيفية إدراج الأشكال، إضافة شكل مستطيل،
  وتجميع الأشكال في Word باستخدام Aspose.Words.
og_image_alt: Screenshot showing a blank Word document with two rectangle shapes grouped
  together
og_title: إنشاء مستند Word فارغ مع مستطيلات مُجمَّعة – دليل C#
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  headline: Create blank word document with grouped rectangles – C# guide
  type: TechArticle
- description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  name: Create blank word document with grouped rectangles – C# guide
  steps:
  - name: What if I need more than two shapes?
    text: Just keep calling `builder.InsertShape(...)` and `group.AppendChild(...)`
      for each new shape. The group can hold any number of children.
  - name: Can I set fill colour or border on the rectangles?
    text: 'Absolutely. After creating a rectangle you can tweak its `FillColor`, `OutlineColor`,
      and `LineWidth`:'
  - name: How do I move the whole group after it’s been created?
    text: 'Use the group''s `Left` and `Top` properties, measured in points:'
  - name: What about scaling the group?
    text: Set `group.Width` and `group.Height` or use `group.ScaleX` / `group.ScaleY`.
      The child rectangles retain their proportions relative to the group.
  - name: Does this work with older .doc files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. The only limitation is that some newer shape features may be down‑sampled
      when saving to the older binary format.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: إنشاء مستند Word فارغ مع مستطيلات مجمعة – دليل C#
url: /ar/java/images-shapes/create-blank-word-document-with-grouped-rectangles-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء مستند Word فارغ مع مستطيلات مجمعة – دليل C#

هل احتجت يوماً إلى **إنشاء مستند Word فارغ** يحتوي بالفعل على مجموعة من الأشكال، لكنك لم تكن متأكدًا من كيفية تجميعها بشكل جميل؟ لست وحدك. في العديد من سيناريوهات التقارير أو إنشاء القوالب، تريد لوحة نظيفة مع بعض المستطيلات التي تعمل كعناصر نائبة، وتود أن تتحرك معًا كوحدة واحدة.

في هذا الدرس سنستعرض الخطوات الدقيقة لـ **إنشاء مستند Word فارغ**، **إضافة شكل مستطيل**، ثم **تجميع الأشكال في Word** باستخدام مكتبة Aspose.Words. في النهاية ستحصل على ملف `.docx` جاهز للاستخدام حيث يكون المستطيلان جزءًا من مجموعة، بحيث أي تعديل في الموضع أو الحجم يؤثر عليهما معًا مرة واحدة.  

سنجيب أيضًا على الأسئلة الشائعة “**كيفية إدراج الأشكال**” و “**كيفية تجميع الأشكال**” التي تظهر في المنتديات وStack Overflow. لا حاجة إلى مستندات خارجية—كل ما تحتاجه موجود هنا.

---

## المتطلبات المسبقة

- .NET 6 أو أحدث (الكود يتوافق أيضًا مع .NET Core)  
- Aspose.Words for .NET (حزمة NuGet `Aspose.Words`)  
- فهم أساسي لصياغة C# (إذا كتبت “Hello World”، فأنت جاهز)  

إذا لم تقم بتثبيت Aspose.Words بعد، نفّذ:

```bash
dotnet add package Aspose.Words
```

هذا كل شيء—لا ملفات DLL إضافية، ولا COM interop، فقط مرجع NuGet نظيف.

---

## الخطوة 1: إنشاء مستند Word فارغ وتهيئة الـ builder

أول شيء نقوم به هو إنشاء كائن `Document` فارغ. فكر فيه كصفحة ورق جديدة. ثم نرفق `DocumentBuilder`، وهو الأداة المفيدة التي توفرها Aspose لإدراج المحتوى.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();               // <-- create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **لماذا هذا مهم:** بدون `DocumentBuilder` سيتعين عليك تعديل شجرة العقد منخفضة المستوى يدويًا، وهذا عرضة للأخطاء. الـ builder يبسط تعقيدات XML لملف `.docx`.

---

## الخطوة 2: كيفية إدراج الأشكال – إضافة حاوية مجموعة أولاً

تتيح لك Aspose إدراج *group shape* يمكنه لاحقًا احتواء أشكال أخرى. هذا هو الأساس لـ **group shapes word**.  

```csharp
        // Step 2: Insert a group shape that will act as a container
        Shape group = builder.InsertGroupShape();
```

> **نصيحة محترف:** المجموعة نفسها غير مرئية حتى تضيف أشكالًا فرعية، لذا لن ترى أي آثار في المستند الناتج حتى الخطوة التالية.

---

## الخطوة 3: إضافة شكل مستطيل – الكائنات المرئية الفعلية

الآن سنقوم **بإضافة شكل مستطيل** مرتين، كل مرة بحجم مختلف. طريقة `InsertShape` تأخذ `ShapeType` والأبعاد بالنقاط (1 pt ≈ 1/72 inch).

```csharp
        // Step 3: Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); // 100 pt × 50 pt
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);  // 80 pt × 40 pt
```

> **لماذا المستطيلات؟** إنها أبسط شكل هندسي، مثالية كعناصر نائبة، أو نماذج واجهات تشبه الأزرار، أو عناصر رسومية بسيطة.

---

## الخطوة 4: كيفية تجميع الأشكال – إرفاق المستطيلات بالمجموعة

بعد إنشاء المستطيلات، الآن **كيفية تجميع الأشكال** عن طريق إلحاقها كعناصر فرعية لشكل المجموعة الذي أدخلناه مسبقًا.

```csharp
        // Step 4: Append the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);
```

> **ماذا يحدث خلف الكواليس؟** يصبح شكل المجموعة هو العقدة الأصلية في شجرة XML للمستند. نقل المجموعة ينقل المستطيلين معًا، مع الحفاظ على مواضعهما النسبية.

---

## الخطوة 5: حفظ المستند – لديك الآن ملف Word بأشكال مجمعة

أخيرًا، نقوم بحفظ المستند على القرص. غيّر المسار إلى موقع موجود على جهازك.

```csharp
        // Step 5: Save the document with the grouped shapes
        doc.Save("GroupShape.docx");   // Creates a blank word document with grouped rectangles
    }
}
```

هذا هو البرنامج بالكامل. شغّله، افتح `GroupShape.docx`، وسترى مستطيلين يجلسان معًا. إذا اخترت أحدهما، يتم تمييز المجموعة بالكامل—بالضبط ما يجب أن يفعله **group shapes word**.

---

## الشيفرة المصدرية الكاملة في مكان واحد

للتسهيل، إليك المثال الكامل جاهزًا للنسخ واللصق:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape that will contain other shapes
        Shape group = builder.InsertGroupShape();

        // Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);

        // Add the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);

        // Save the document
        doc.Save("GroupShape.docx");
    }
}
```

**الناتج المتوقع:** فتح `GroupShape.docx` يُظهر صفحة فارغة مع مستطيلين مجمّعين معًا. اختيار أحد المستطيلات يختار الآخر تلقائيًا، مما يؤكد نجاح التجميع.

---

## أسئلة شائعة ومعالجة الحالات الخاصة

### ماذا لو احتجت إلى أكثر من شكلين؟

استمر في استدعاء `builder.InsertShape(...)` و `group.AppendChild(...)` لكل شكل جديد. يمكن للمجموعة احتواء أي عدد من العناصر الفرعية.

### هل يمكنني ضبط لون التعبئة أو الحدود على المستطيلات؟

بالطبع. بعد إنشاء المستطيل يمكنك تعديل `FillColor` و `OutlineColor` و `LineWidth` الخاص به:

```csharp
rect1.FillColor = System.Drawing.Color.LightBlue;
rect1.OutlineColor = System.Drawing.Color.DarkBlue;
rect1.LineWidth = 1.5;
```

### كيف أحرك المجموعة بالكامل بعد إنشائها؟

استخدم خصائص المجموعة `Left` و `Top`، المقاسة بالنقاط:

```csharp
group.Left = 150;   // move 150 pt from the left margin
group.Top  = 200;   // move 200 pt from the top of the page
```

### ماذا عن تحجيم المجموعة؟

حدد `group.Width` و `group.Height` أو استخدم `group.ScaleX` / `group.ScaleY`. تحتفظ المستطيلات الفرعية بنسبها بالنسبة للمجموعة.

### هل يعمل هذا مع ملفات .doc القديمة؟

Aspose.Words ي抽象 تنسيق الملف، لذا يعمل نفس الكود مع `.doc` و `.docx`. القيد الوحيد هو أن بعض ميزات الأشكال الحديثة قد يتم تقليلها عند الحفظ إلى تنسيق الثنائي القديم.

---

## نصائح احترافية لكود جاهز للإنتاج

- **تحرير الموارد** – ضع `Document` داخل كتلة `using` إذا كنت تتعامل مع ملفات كبيرة لتحرير الذاكرة بسرعة.  
- **معالجة الأخطاء** – امسك `Aspose.Words.Fonts.FontSettingsException` إذا كنت تخطط لتضمين خطوط مخصصة.  
- **الأداء** – عند إدراج عدد كبير من الأشكال، عطل تحديثات التخطيط مؤقتًا باستخدام `doc.LayoutOptions = new LayoutOptions { UpdateFields = false };` ثم أعد تفعيلها لاحقًا.

---

## الخلاصة

أنت الآن تعرف **كيفية إنشاء مستند Word فارغ**، **إضافة شكل مستطيل**، و **تجميع الأشكال في Word** باستخدام Aspose.Words في C#. يغطي المثال خطوات “**كيفية إدراج الأشكال**” و “**كيفية تجميع الأشكال**” الأساسية، يوضح سبب وجود كل سطر، ويتطرق إلى التخصيص، الحالات الخاصة، وأفضل الممارسات.

بعد ذلك، قد تستكشف **كيفية إدراج الصور**، **إضافة نص داخل الأشكال المجمعة**، أو **تصدير المستند إلى PDF**—جميعها يتبع نفس نمط استخدام `DocumentBuilder` وتلاعب الأشكال. استمر في التجربة؛ واجهة برمجة تطبيقات Aspose غنية بما يكفي للتعامل مع أي سيناريو أتمتة Word يمكنك تخيله.

برمجة سعيدة، ولا تتردد في ترك تعليق إذا واجهت أي صعوبة!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شيفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [إدراج أشكال في مستندات Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [إنشاء شكل مجموعة في مستند Word باستخدام Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [إنشاء شكل مستطيل في Word باستخدام C# – دليل خطوة بخطوة](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}