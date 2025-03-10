---
title: تعديل عناصر التحكم في المحتوى
linktitle: تعديل عناصر التحكم في المحتوى
second_title: واجهة برمجة تطبيقات معالجة المستندات Aspose.Words
description: تعرف على كيفية تعديل علامات المستند المنظمة في Word باستخدام Aspose.Words for .NET. قم بتحديث النص والقوائم المنسدلة والصور خطوة بخطوة.
weight: 10
url: /ar/net/programming-with-sdt/modify-content-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تعديل عناصر التحكم في المحتوى

## مقدمة

إذا سبق لك العمل باستخدام مستندات Word وكنت بحاجة إلى تعديل عناصر التحكم في المحتوى المنظم - مثل النص العادي أو القوائم المنسدلة أو الصور - باستخدام Aspose.Words for .NET، فأنت في المكان المناسب! تعد علامات المستندات المنظمة (SDTs) أدوات قوية تجعل أتمتة المستندات أسهل وأكثر مرونة. في هذا البرنامج التعليمي، سنتعمق في كيفية تعديل علامات المستندات المنظمة هذه لتناسب احتياجاتك. سواء كنت تقوم بتحديث النص أو تغيير اختيارات القائمة المنسدلة أو تبديل الصور، فإن هذا الدليل سيرشدك خلال العملية خطوة بخطوة.

## المتطلبات الأساسية

قبل أن ننتقل إلى التفاصيل الدقيقة لتعديل عناصر التحكم في المحتوى، تأكد من توفر ما يلي:

1.  تم تثبيت Aspose.Words لـ .NET: تأكد من تثبيت مكتبة Aspose.Words. إذا لم يكن الأمر كذلك، فيمكنك[تحميله هنا](https://releases.aspose.com/words/net/).

2. المعرفة الأساسية بلغة C#: يفترض هذا البرنامج التعليمي أنك على دراية بمفاهيم برمجة C# الأساسية.

3. بيئة تطوير .NET: يجب أن يكون لديك بيئة تطوير متكاملة مثل Visual Studio مهيأة لتشغيل تطبيقات .NET.

4. مستند نموذجي: سنستخدم مستند Word نموذجيًا يحتوي على أنواع مختلفة من SDTs. يمكنك استخدام المستند من المثال أو إنشاء مستندك الخاص.

5.  الوصول إلى وثائق Aspose: لمزيد من المعلومات التفصيلية، راجع[توثيق Aspose.Words](https://reference.aspose.com/words/net/).

## استيراد مساحات الأسماء

للبدء في العمل مع Aspose.Words، تحتاج إلى استيراد المساحات ذات الصلة إلى مشروع C# الخاص بك. إليك كيفية القيام بذلك:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

ستتيح لك هذه المساحات الاسمية الوصول إلى الفئات والطرق اللازمة للتعامل مع علامات المستندات المنظمة في مستندات Word الخاصة بك.

## الخطوة 1: إعداد مسار المستند الخاص بك

 قبل إجراء أي تغييرات، يجب عليك تحديد المسار إلى مستندك. استبدل`"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي الذي يتم تخزين مستندك فيه.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Structured document tags.docx");
```

## الخطوة 2: تكرار علامات المستند المنظم

 لتعديل SDTs، تحتاج أولاً إلى المرور عبر جميع SDTs في المستند. يتم ذلك باستخدام`GetChildNodes` طريقة للحصول على جميع العقد من النوع`StructuredDocumentTag`.

```csharp
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    // تعديل SDTs بناءً على نوعها
}
```

## الخطوة 3: تعديل SDTs النصية العادية

إذا كان SDT عبارة عن نوع نص عادي، فيمكنك استبدال محتواه. أولاً، قم بمسح المحتوى الموجود، ثم أضف نصًا جديدًا.

```csharp
if (sdt.SdtType == SdtType.PlainText)
{
    sdt.RemoveAllChildren();
    Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
    Run run = new Run(doc, "new text goes here");
    para.AppendChild(run);
}
```

 التوضيح: هنا،`RemoveAllChildren()`يقوم بمسح المحتوى الموجود في SDT. ثم نقوم بإنشاء ملف جديد`Paragraph` و`Run` كائن لإدراج النص الجديد.

## الخطوة 4: تعديل قائمة المنسدلة SDTs

 بالنسبة لقوائم SDT المنسدلة، يمكنك تغيير العنصر المحدد من خلال الوصول إلى`ListItems` المجموعة. هنا، نختار العنصر الثالث في القائمة.

```csharp
if (sdt.SdtType == SdtType.DropDownList)
{
    SdtListItem secondItem = sdt.ListItems[2];
    sdt.ListItems.SelectedValue = secondItem;
}
```

الشرح: يقوم مقتطف التعليمات البرمجية هذا بتحديد العنصر الموجود في الفهرس 2 (العنصر الثالث) من القائمة المنسدلة. اضبط الفهرس وفقًا لاحتياجاتك.

## الخطوة 5: تعديل SDTs الصورة

لتحديث صورة داخل صورة SDT، يمكنك استبدال الصورة الحالية بأخرى جديدة.

```csharp
if (sdt.SdtType == SdtType.Picture)
{
    Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
    if (shape.HasImage)
    {
        shape.ImageData.SetImage(ImagesDir + "Watermark.png");
    }
}
```

 الشرح: يتحقق هذا الكود مما إذا كان الشكل يحتوي على صورة ثم يستبدلها بصورة جديدة تقع في`ImagesDir`.

## الخطوة 6: احفظ المستند المعدّل

بعد إجراء كافة التغييرات اللازمة، احفظ المستند المعدّل باسم جديد للحفاظ على المستند الأصلي سليمًا.

```csharp
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");
```

التوضيح: يؤدي هذا إلى حفظ المستند باسم ملف جديد حتى تتمكن من التمييز بينه وبين المستند الأصلي بسهولة.

## خاتمة

إن تعديل عناصر التحكم في المحتوى في مستند Word باستخدام Aspose.Words for .NET أمر بسيط بمجرد فهم الخطوات المتضمنة. سواء كنت تقوم بتحديث النص أو تغيير اختيارات القائمة المنسدلة أو تبديل الصور، فإن Aspose.Words يوفر واجهة برمجة تطبيقات قوية لهذه المهام. باتباع هذا البرنامج التعليمي، يمكنك إدارة عناصر التحكم في المحتوى المنظم في مستندك وتخصيصها بفعالية، مما يجعل مستنداتك أكثر ديناميكية ومصممة خصيصًا لتلبية احتياجاتك.

## الأسئلة الشائعة

1. ما هي علامة المستند المنظم (SDT)؟

SDTs هي عناصر في مستندات Word تساعد في إدارة وتنسيق محتوى المستند، مثل مربعات النص أو القوائم المنسدلة أو الصور.

2. كيف يمكنني إضافة عنصر قائمة منسدلة جديد إلى SDT؟

 لإضافة عنصر جديد، استخدم`ListItems` الملكية وإضافة جديدة`SdtListItem` إلى المجموعة.

3. هل يمكنني استخدام Aspose.Words لإزالة SDTs من مستند؟

نعم، يمكنك إزالة SDTs عن طريق الوصول إلى عقد المستند وحذف SDT المطلوب.

4. كيف أتعامل مع SDTs المتداخلة داخل عناصر أخرى؟

 استخدم`GetChildNodes` الطريقة مع المعلمات المناسبة للوصول إلى SDTs المتداخلة.

5. ماذا يجب أن أفعل إذا لم يكن SDT الذي أحتاج إلى تعديله مرئيًا في المستند؟

تأكد من عدم إخفاء SDT أو حمايته. تحقق من إعدادات المستند وتأكد من أن الكود الخاص بك يستهدف نوع SDT بشكل صحيح.


### مثال على كود المصدر لتعديل عناصر التحكم في المحتوى باستخدام Aspose.Words لـ .NET 

```csharp
// المسار إلى دليل المستند الخاص بك
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Structured document tags.docx");
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
	switch (sdt.SdtType)
	{
		case SdtType.PlainText:
		{
			sdt.RemoveAllChildren();
			Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
			Run run = new Run(doc, "new text goes here");
			para.AppendChild(run);
			break;
		}
		case SdtType.DropDownList:
		{
			SdtListItem secondItem = sdt.ListItems[2];
			sdt.ListItems.SelectedValue = secondItem;
			break;
		}
		case SdtType.Picture:
		{
			Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
			if (shape.HasImage)
			{
				shape.ImageData.SetImage(ImagesDir + "Watermark.png");
			}
			break;
		}
	}
}
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");

```

هذا كل شيء! لقد نجحت في تعديل أنواع مختلفة من عناصر التحكم في المحتوى في مستند Word الخاص بك باستخدام Aspose.Words for .NET.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
