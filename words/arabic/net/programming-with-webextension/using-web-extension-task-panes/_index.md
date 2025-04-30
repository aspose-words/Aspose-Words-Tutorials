---
"description": "تعرف على كيفية إضافة وتكوين أجزاء مهام ملحقات الويب في مستندات Word باستخدام Aspose.Words لـ .NET في هذا البرنامج التعليمي المفصل خطوة بخطوة."
"linktitle": "استخدام أجزاء مهام امتداد الويب"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "استخدام أجزاء مهام امتداد الويب"
"url": "/ar/net/programming-with-webextension/using-web-extension-task-panes/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# استخدام أجزاء مهام امتداد الويب

## مقدمة

مرحبًا بكم في هذا الدليل الشامل حول استخدام أجزاء مهام إضافات الويب في مستندات Word باستخدام Aspose.Words لـ .NET. إذا كنت ترغب في تحسين مستندات Word لديك بأجزاء مهام تفاعلية، فأنت في المكان المناسب. سيرشدك هذا الدليل خطوة بخطوة لتحقيق ذلك بسلاسة.

## المتطلبات الأساسية

قبل أن نبدأ، دعونا نتأكد من أن لديك كل ما تحتاجه:

- Aspose.Words for .NET: يمكنك تنزيله [هنا](https://releases.aspose.com/words/net/).
- بيئة تطوير .NET: Visual Studio أو أي بيئة تطوير متكاملة أخرى تفضلها.
- المعرفة الأساسية بلغة C#: سوف تساعدك هذه المعرفة على متابعة أمثلة التعليمات البرمجية.
- ترخيص Aspose.Words: يمكنك شراء واحد [هنا](https://purchase.aspose.com/buy) أو الحصول على ترخيص مؤقت [هنا](https://purchase.aspose.com/temporary-license/).

## استيراد مساحات الأسماء

قبل أن نبدأ في الترميز، تأكد من استيراد المساحات التالية في مشروعك:

```csharp
using Aspose.Words;
using Aspose.Words.WebExtensions;
```

## دليل خطوة بخطوة

الآن، دعونا نقسم العملية إلى خطوات سهلة المتابعة.

### الخطوة 1: إعداد دليل المستندات الخاص بك

أولاً، علينا تحديد مسار مجلد المستندات. هذا هو المكان الذي سيتم حفظ مستند Word فيه.

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

يستبدل `"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي لمجلد المستندات الخاص بك.

### الخطوة 2: إنشاء مستند جديد

بعد ذلك، سنقوم بإنشاء مستند Word جديد باستخدام Aspose.Words.

```csharp
Document doc = new Document();
```

يقوم هذا الخط بتهيئة مثيل جديد لـ `Document` الفئة التي تمثل مستند Word.

### الخطوة 3: إضافة جزء المهام

الآن، سنضيف لوحة مهام إلى مستندنا. تُعدّ لوحات المهام مفيدةً لتوفير وظائف وأدوات إضافية في مستند Word.

```csharp
TaskPane taskPane = new TaskPane();
doc.WebExtensionTaskPanes.Add(taskPane);
```

هنا نقوم بإنشاء جديد `TaskPane` الكائن وإضافته إلى المستند `WebExtensionTaskPanes` مجموعة.

### الخطوة 4: تكوين جزء المهام

لجعل جزء المهام مرئيًا وتعيين خصائصه، نستخدم الكود التالي:

```csharp
taskPane.DockState = TaskPaneDockState.Right;
taskPane.IsVisible = true;
taskPane.Width = 300;
```

- `DockState` يُحدد مكان ظهور لوحة المهام. في هذه الحالة، تكون على اليمين.
- `IsVisible` يتأكد من أن جزء المهام مرئي.
- `Width` تعيين عرض جزء المهام.

### الخطوة 5: إعداد مرجع امتداد الويب

بعد ذلك، قمنا بإعداد مرجع ملحق الويب الذي يتضمن المعرف والإصدار ونوع المتجر.

```csharp
taskPane.WebExtension.Reference.Id = "wa102923726";
taskPane.WebExtension.Reference.Version = "1.0.0.0";
taskPane.WebExtension.Reference.StoreType = WebExtensionStoreType.OMEX;
taskPane.WebExtension.Reference.Store = "th-TH";
```

- `Id` هو معرف فريد لامتداد الويب.
- `Version` يحدد إصدار الامتداد.
- `StoreType` يشير إلى نوع المتجر (في هذه الحالة، OMEX).
- `Store` يحدد رمز اللغة/الثقافة للمتجر.

### الخطوة 6: إضافة خصائص إلى ملحق الويب

بإمكانك إضافة خصائص إلى ملحق الويب الخاص بك لتحديد سلوكه أو محتواه.

```csharp
taskPane.WebExtension.Properties.Add(new WebExtensionProperty("mailchimpCampaign", "mailchimpCampaign"));
```

هنا نضيف خاصية تسمى `mailchimpCampaign`.

### الخطوة 7: ربط امتداد الويب

أخيرًا، نضيف روابط إلى ملحق الويب الخاص بنا. تتيح لك هذه الروابط ربط الملحق بأجزاء محددة من المستند.

```csharp
taskPane.WebExtension.Bindings.Add(new WebExtensionBinding("UnnamedBinding_0_1506535429545", WebExtensionBindingType.Text, "194740422"));
```

- `UnnamedBinding_0_1506535429545` هو اسم الربط.
- `WebExtensionBindingType.Text` يشير إلى أن الربط من نوع النص.
- `194740422` هو معرف جزء المستند الذي يرتبط به الامتداد.

### الخطوة 8: حفظ المستند

بعد إعداد كل شيء، احفظ مستندك.

```csharp
doc.Save(dataDir + "WorkingWithWebExtension.UsingWebExtensionTaskPanes.docx");
```

يحفظ هذا السطر المستند في الدليل المحدد باسم الملف المحدد.

### الخطوة 9: تحميل معلومات جزء المهام وعرضها

للتحقق من معلومات جزء المهام وعرضها، نقوم بتحميل المستند والتكرار خلال أجزاء المهام.

```csharp
doc = new Document(dataDir + "WorkingWithWebExtension.UsingWebExtensionTaskPanes.docx");

Console.WriteLine("Task panes sources:\n");

foreach (TaskPane taskPaneInfo in doc.WebExtensionTaskPanes)
{
    WebExtensionReference reference = taskPaneInfo.WebExtension.Reference;
    Console.WriteLine($"Provider: \"{reference.Store}\", version: \"{reference.Version}\", catalog identifier: \"{reference.Id}\";");
}
```

يقوم هذا الكود بتحميل المستند وطباعة الموفر والإصدار ومعرف الكتالوج لكل جزء مهام في وحدة التحكم.

## خاتمة

وهذا كل شيء! لقد نجحت في إضافة وتكوين لوحة مهام ملحق الويب في مستند Word باستخدام Aspose.Words لـ .NET. تُحسّن هذه الميزة الفعّالة مستندات Word بشكل ملحوظ من خلال توفير وظائف إضافية مباشرةً داخل المستند. 

## الأسئلة الشائعة

### ما هو جزء المهام في Word؟
جزء المهام هو عنصر واجهة يوفر أدوات ووظائف إضافية داخل مستند Word، مما يعزز تفاعل المستخدم والإنتاجية.

### هل يمكنني تخصيص مظهر جزء المهام؟
نعم، يمكنك تخصيص مظهر جزء المهام عن طريق تعيين خصائص مثل `DockState`، `IsVisible`، و `Width`.

### ما هي خصائص امتداد الويب؟
خصائص ملحق الويب هي خصائص مخصصة يمكنك إضافتها إلى ملحق الويب لتحديد سلوكه أو محتواه.

### كيف أقوم بربط ملحق الويب بجزء من المستند؟
يمكنك ربط ملحق الويب بجزء من المستند باستخدام `WebExtensionBinding` الفئة، التي تحدد نوع الربط ومعرف الهدف.

### أين يمكنني العثور على مزيد من المعلومات حول Aspose.Words لـ .NET؟
يمكنك العثور على وثائق مفصلة [هنا](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}