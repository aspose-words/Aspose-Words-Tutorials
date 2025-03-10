---
title: استخدام أجزاء مهام ملحق الويب
linktitle: استخدام أجزاء مهام ملحق الويب
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية إضافة وتكوين أجزاء مهام ملحقات الويب في مستندات Word باستخدام Aspose.Words لـ .NET في هذا البرنامج التعليمي المفصل خطوة بخطوة.
weight: 10
url: /ar/net/programming-with-webextension/using-web-extension-task-panes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# استخدام أجزاء مهام ملحق الويب

## مقدمة

مرحبًا بك في هذا البرنامج التعليمي المتعمق حول استخدام أجزاء مهام ملحق الويب في مستند Word باستخدام Aspose.Words for .NET. إذا كنت ترغب في تحسين مستندات Word الخاصة بك باستخدام أجزاء مهام تفاعلية، فأنت في المكان المناسب. سيرشدك هذا الدليل خلال كل خطوة لتحقيق ذلك بسلاسة.

## المتطلبات الأساسية

قبل أن نبدأ، دعونا نتأكد من أن لديك كل ما تحتاجه:

-  Aspose.Words for .NET: يمكنك تنزيله[هنا](https://releases.aspose.com/words/net/).
- بيئة تطوير .NET: Visual Studio أو أي بيئة تطوير متكاملة أخرى تفضلها.
- المعرفة الأساسية بلغة C#: سوف تساعدك هذه المعرفة على متابعة أمثلة التعليمات البرمجية.
-  ترخيص Aspose.Words: يمكنك شراء واحد[هنا](https://purchase.aspose.com/buy) أو الحصول على ترخيص مؤقت[هنا](https://purchase.aspose.com/temporary-license/).

## استيراد مساحات الأسماء

قبل أن نبدأ في الترميز، تأكد من استيراد المساحات الأسماء التالية في مشروعك:

```csharp
using Aspose.Words;
using Aspose.Words.WebExtensions;
```

## دليل خطوة بخطوة

الآن، دعونا نقوم بتقسيم العملية إلى خطوات سهلة المتابعة.

### الخطوة 1: إعداد دليل المستندات الخاص بك

أولاً وقبل كل شيء، نحتاج إلى إعداد المسار إلى دليل المستندات الخاص بك. هذا هو المكان الذي سيتم فيه حفظ مستند Word الخاص بك.

```csharp
// المسار إلى دليل المستندات.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 يستبدل`"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي لمجلد المستندات الخاص بك.

### الخطوة 2: إنشاء مستند جديد

بعد ذلك، سوف نقوم بإنشاء مستند Word جديد باستخدام Aspose.Words.

```csharp
Document doc = new Document();
```

 يقوم هذا الخط بتهيئة مثيل جديد من`Document` الفئة التي تمثل مستند Word.

### الخطوة 3: إضافة جزء المهام

الآن، سنضيف جزء المهام إلى مستندنا. تُعد أجزاء المهام مفيدة لتوفير وظائف وأدوات إضافية داخل مستند Word.

```csharp
TaskPane taskPane = new TaskPane();
doc.WebExtensionTaskPanes.Add(taskPane);
```

 هنا نقوم بإنشاء جديد`TaskPane` الكائن وإضافته إلى المستند`WebExtensionTaskPanes` مجموعة.

### الخطوة 4: تكوين جزء المهام

لجعل جزء المهام مرئيًا وتعيين خصائصه، نستخدم الكود التالي:

```csharp
taskPane.DockState = TaskPaneDockState.Right;
taskPane.IsVisible = true;
taskPane.Width = 300;
```

- `DockState` يحدد المكان الذي ستظهر فيه لوحة المهام. في هذه الحالة، تكون على اليمين.
- `IsVisible` يضمن أن يكون جزء المهام مرئيًا.
- `Width` تعيين عرض جزء المهام.

### الخطوة 5: إعداد مرجع ملحق الويب

بعد ذلك، قمنا بإعداد مرجع ملحق الويب الذي يتضمن المعرف والإصدار ونوع المتجر.

```csharp
taskPane.WebExtension.Reference.Id = "wa102923726";
taskPane.WebExtension.Reference.Version = "1.0.0.0";
taskPane.WebExtension.Reference.StoreType = WebExtensionStoreType.OMEX;
taskPane.WebExtension.Reference.Store = "th-TH";
```

- `Id`هو معرف فريد لامتداد الويب.
- `Version` يحدد إصدار الامتداد.
- `StoreType` يشير إلى نوع المتجر (في هذه الحالة، OMEX).
- `Store` يحدد رمز اللغة/الثقافة للمتجر.

### الخطوة 6: إضافة خصائص إلى ملحق الويب

بإمكانك إضافة خصائص إلى ملحق الويب الخاص بك لتحديد سلوكه أو محتواه.

```csharp
taskPane.WebExtension.Properties.Add(new WebExtensionProperty("mailchimpCampaign", "mailchimpCampaign"));
```

 هنا نضيف خاصية تسمى`mailchimpCampaign`.

### الخطوة 7: ربط امتداد الويب

أخيرًا، نضيف روابط إلى ملحق الويب الخاص بنا. تتيح لك الروابط ربط الملحق بأجزاء معينة من المستند.

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

للتحقق من معلومات جزء المهام وعرضها، نقوم بتحميل المستند وتكراره عبر أجزاء المهام.

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

وهذا كل شيء! لقد نجحت في إضافة وتكوين جزء مهام ملحق الويب في مستند Word باستخدام Aspose.Words for .NET. يمكن لهذه الميزة القوية أن تعمل على تحسين مستندات Word الخاصة بك بشكل كبير من خلال توفير وظائف إضافية مباشرة داخل المستند. 

## الأسئلة الشائعة

### ما هو جزء المهام في Word؟
جزء المهام هو عنصر واجهة يوفر أدوات ووظائف إضافية داخل مستند Word، مما يعزز تفاعل المستخدم والإنتاجية.

### هل يمكنني تخصيص مظهر جزء المهام؟
 نعم، يمكنك تخصيص مظهر جزء المهام عن طريق تعيين خصائص مثل`DockState`, `IsVisible` ، و`Width`.

### ما هي خصائص امتداد الويب؟
خصائص ملحق الويب هي خصائص مخصصة يمكنك إضافتها إلى ملحق الويب لتحديد سلوكه أو محتواه.

### كيف أقوم بربط ملحق الويب بجزء من المستند؟
 يمكنك ربط ملحق ويب بجزء من المستند باستخدام`WebExtensionBinding` الفئة، التي تحدد نوع الربط ومعرف الهدف.

### أين يمكنني العثور على مزيد من المعلومات حول Aspose.Words لـ .NET؟
 يمكنك العثور على وثائق مفصلة[هنا](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
