---
category: general
date: 2026-09-11
description: دليل تحرير تسمية المخطط يوضح كيفية تغيير موضع تسمية المخطط، تخصيص تسمية
  بيانات المخطط، إخفاء اسم فئة المخطط، وعرض قيمة تسمية المخطط باستخدام Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit chart label tutorial
- change chart label position
- customize chart data label
- hide chart category name
- show chart label value
language: ar
lastmod: 2026-09-11
og_description: يُرشدك برنامج تعليمي لتعديل تسمية المخطط إلى تغيير موضع تسمية المخطط،
  وتخصيص تسمية بيانات المخطط، وإخفاء اسم فئة المخطط، وعرض قيمة تسمية المخطط باستخدام
  Aspose.Words لـ .NET.
og_image_alt: Screenshot of a Word document displaying a chart with customized data
  labels
og_title: دليل تحرير تسمية المخطط – تخصيص تسميات مخططات Word في C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Edit chart label tutorial showing how to change chart label position,
    customize chart data label, hide chart category name, and show chart label value
    with Aspose.Words.
  headline: Edit chart label tutorial – modify Word chart labels in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart manipulation
title: دليل تعديل تسمية المخطط – تعديل تسميات مخططات Word باستخدام C#
url: /ar/net/programming-with-charts/edit-chart-label-tutorial-modify-word-chart-labels-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تحرير دليل تسمية المخطط – تعديل تسميات مخططات Word في C#

إذا كنت بحاجة إلى **تحرير دليل تسمية المخطط** لمستند Word، يوضح لك هذا الدليل بالضبط كيفية تغيير موضع تسمية المخطط، تخصيص تسمية بيانات المخطط، إخفاء اسم فئة المخطط، وعرض قيمة تسمية المخطط باستخدام Aspose.Words for .NET. سترى مثالًا كاملاً قابلاً للتنفيذ يمكنك إدراجه في أي مشروع C#.

العمل مع تسميات المخططات هو طلب شائع عند إنشاء التقارير، الفواتير، أو لوحات التحكم برمجيًا. يغطي هذا الدرس كل خطوة — من تحميل المستند إلى حفظ التغييرات — بحيث يمكنك إنتاج مخططات مصقولة دون تعديل يدوي.

## المتطلبات المسبقة

* .NET 6.0 أو أحدث مثبت  
* ترخيص صالح لـ Aspose.Words for .NET (أو مفتاح تقييم مؤقت)  
* Visual Studio 2022 أو أي بيئة تطوير متوافقة مع C#  
* ملف Word (`Chart.docx`) يحتوي على مخطط واحد على الأقل  

لا توجد حزم NuGet إضافية مطلوبة بخلاف `Aspose.Words`.

## الخطوة 1: إعداد المشروع واستيراد المساحات الاسمية

أنشئ تطبيقًا جديدًا من نوع console وأضف حزمة Aspose.Words عبر NuGet:

```bash
dotnet new console -n ChartLabelEditor
cd ChartLabelEditor
dotnet add package Aspose.Words
```

افتح `Program.cs` واستورد المساحات الاسمية المطلوبة:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
```

تمنحك هذه المساحات الاسمية إمكانية الوصول إلى فئة `Document` للتعامل مع ملفات Word وفئات `Chart` للتلاعب بعناصر المخطط.

## الخطوة 2: تحميل مستند Word الذي يحتوي على مخطط

السطر القابل للتنفيذ الأول يقوم بتحميل المستند المصدر. استبدل `YOUR_DIRECTORY` بالمسار الفعلي حيث يقع `Chart.docx`.

```csharp
// Load the Word document containing the chart
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");
```

إن تحميل المستند يُنشئ تمثيلًا في الذاكرة يمكنك استعراضه وتعديله.

## الخطوة 3: استرجاع أول مخطط في المستند

يتم تخزين المخططات كعُقد فرعية من النوع `NodeType.Chart`. طريقة `GetChild` تبحث في شجرة المستند وتعيد المخطط الذي تريد تحريره.

```csharp
// Retrieve the first chart object (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

إذا كان المستند يحتوي على عدة مخططات، يمكنك تغيير الفهرس لاستهداف مخطط مختلف.

## الخطوة 4: الوصول إلى وتخصيص تسمية البيانات للسلسلة الأولى

كل سلسلة في المخطط لديها كائن `DataLabel` يتحكم في طريقة ظهور التسمية. يوضح الكود أدناه أربع تخصيصات رئيسية مطلوبة وفقًا للكلمات المفتاحية الثانوية للدرس.

```csharp
// Access the data label of the first series (index 0)
ChartDataLabel label = chart.Series[0].DataLabel;

// Change chart label position – place the label in the center of each data point
label.Position = DataLabelPosition.Center;

// Customize chart data label – use a custom separator between label parts
label.Separator = "; ";

// Hide chart category name – the category text will not be shown
label.ShowCategoryName = false;

// Show chart label value – the numeric value of the point will be displayed
label.ShowValue = true;
```

**لماذا هذه الإعدادات مهمة**

* `DataLabelPosition.Center` ينقل التسمية من الموقع الافتراضي خارج النقطة إلى وسط نقطة البيانات، مما يجعل المخطط أسهل قراءة عندما تكون النقاط مكتظة.  
* ضبط `Separator` مخصص يتيح لك التحكم في كيفية دمج اسم السلسلة، القيمة، والأجزاء الأخرى.  
* إخفاء اسم الفئة (`ShowCategoryName = false`) يقلل الفوضى البصرية عندما يكون الفئة واضحة بالفعل من المحور.  
* تمكين `ShowValue` يضمن ظهور القيمة الفعلية للبيانات، وهو غالبًا ما يكون مطلوبًا في التقارير المالية أو الإحصائية.

## الخطوة 5: حفظ المستند المعدل

بعد تعديل خصائص التسمية، احفظ التغييرات في ملف جديد:

```csharp
// Save the updated document with customized chart labels
doc.Save(@"YOUR_DIRECTORY\CustomLabelChart.docx");
```

الملف الجديد (`CustomLabelChart.docx`) يحتوي على نفس تخطيط المخطط لكن بمظهر التسمية الذي حددته.

## الكود الكامل

فيما يلي البرنامج الكامل الجاهز للتنفيذ. انسخه إلى `Program.cs`، عدل مسارات الملفات، ثم شغّل المشروع.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the Word document that contains a chart
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label of the first series
            ChartDataLabel label = chart.Series[0].DataLabel;

            // 4️⃣ Customize the label appearance
            label.Position = DataLabelPosition.Center;   // change chart label position
            label.Separator = "; ";                      // customize chart data label
            label.ShowValue = true;                      // show chart label value
            label.ShowCategoryName = false;              // hide chart category name

            // 5️⃣ Save the modified document
            doc.Save(@"YOUR_DIRECTORY\CustomLabelChart.docx");

            Console.WriteLine("Chart label customization complete.");
        }
    }
}
```

### النتيجة المتوقعة

افتح `CustomLabelChart.docx` في Microsoft Word. يجب أن ترى تسمية السلسلة الأولى للمخطط متمركزة على كل نقطة بيانات، تعرض القيمة الرقمية فقط، وتستخدم “; ” كفاصل. لن تظهر أسماء الفئات بجوار القيم بعد الآن.

## الأسئلة الشائعة والحالات الخاصة

| السؤال | الجواب |
|----------|--------|
| **ماذا لو لم يحتوي المستند على أي مخطط؟** | يتحقق المثال من وجود مخطط `null` ويخرج برفق مع رسالة في وحدة التحكم. |
| **هل يمكنني تحرير تسميات لعدة سلاسل؟** | نعم. قم بالتكرار عبر `chart.Series` وطبق نفس إعدادات `DataLabel` على كل `Series[i].DataLabel`. |
| **كيف أغيّر نمط خط التسمية؟** | استخدم `label.Font` (مثال: `label.Font.Size = 10; label.Font.Color = Color.Blue;`). |
| **هل `DataLabelPosition.Center` مدعوم لجميع أنواع المخططات؟** | معظم أنواع المخططات ثنائية الأبعاد تدعمه. بالنسبة للمخططات ثلاثية الأبعاد، قد يتم تجاهل بعض المواضع من قبل Word. |
| **هل أحتاج إلى ترخيص لـ Aspose.Words؟** | وضع التقييم يعمل لكنه يضيف علامة مائية. الترخيص يزيل العلامة المائية ويفتح جميع الوظائف. |

## نصائح احترافية

* **معالجة دفعات:** غلف منطق التحميل والحفظ في طريقة تستقبل مسارات الإدخال والإخراج. هذا يسهل معالجة العشرات من المستندات داخل حلقة.  
* **الأداء:** أعد استخدام كائن `Document` واحد عند تعديل عدة مخططات في نفس الملف لتجنب عمليات I/O المتكررة.  
* **الاختبار:** تحقق من تغييرات التسمية عبر أتمتة مقارنة بصرية (مثال: باستخدام عارض Word بدون واجهة) إذا كنت تحتاج إلى تأكيد النتيجة في خطوط CI.

## الخطوات التالية

الآن بعد أن أصبحت قادرًا على أساسيات **تحرير دليل تسمية المخطط**، فكر في استكشاف ما يلي:

* **تغيير موضع تسمية المخطط** لسلاسل أخرى أو لأنواع مخططات مختلفة  
* **تخصيص تنسيق تسمية بيانات المخطط** مثل صيغ الأرقام، ألوان الخط، أو تعبئة الخلفية  
* **إخفاء اسم فئة المخطط** مع الاستمرار في إظهار اسم السلسلة للمخططات متعددة السلاسل  
* **عرض قيمة تسمية المخطط** مع القيم النسبية للمخططات الدائرية  

هذه المواضيع تعمق سيطرتك على مظهر مخططات Word وتجهزك لسيناريوهات تقارير متقدمة.

---

*برمجة سعيدة! إذا وجدت هذا الدرس مفيدًا، شاركه مع زملائك أو ساهم بتحسينات على GitHub.*

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [تخصيص تسمية بيانات المخطط](/words/english/net/programming-with-charts/chart-data-label/)
- [تسمية بيانات المخطط](/words/german/net/programming-with-charts/chart-data-label/)
- [تسمية بيانات المخطط](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}