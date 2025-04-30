---
"description": "تعلّم كيفية تعديل وسوم المستندات المنظمة في Word باستخدام Aspose.Words لـ .NET. حدّث النصوص والقوائم المنسدلة والصور خطوة بخطوة."
"linktitle": "تعديل عناصر التحكم في المحتوى"
"second_title": "واجهة برمجة تطبيقات معالجة المستندات Aspose.Words"
"title": "تعديل عناصر التحكم في المحتوى"
"url": "/ar/net/programming-with-sdt/modify-content-controls/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تعديل عناصر التحكم في المحتوى

## مقدمة

إذا سبق لك العمل مع مستندات Word واحتجت إلى تعديل عناصر تحكم المحتوى المُهيكلة، مثل النص العادي أو القوائم المنسدلة أو الصور، باستخدام Aspose.Words لـ .NET، فأنت في المكان المناسب! تُعدّ علامات المستندات المُهيكلة (SDTs) أدوات فعّالة تُسهّل أتمتة المستندات وتزيد من مرونتها. في هذا البرنامج التعليمي، سنشرح بالتفصيل كيفية تعديل علامات المستندات المُهيكلة هذه لتناسب احتياجاتك. سواءً كنت تُحدّث نصًا، أو تُغيّر اختيارات القوائم المنسدلة، أو تُبدّل الصور، سيُرشدك هذا الدليل خلال العملية خطوة بخطوة.

## المتطلبات الأساسية

قبل أن ننتقل إلى التفاصيل الدقيقة لتعديل عناصر التحكم في المحتوى، تأكد من أن لديك ما يلي:

1. تثبيت Aspose.Words لـ .NET: تأكد من تثبيت مكتبة Aspose.Words. إذا لم تكن مثبتة، يمكنك [قم بتحميله هنا](https://releases.aspose.com/words/net/).

2. المعرفة الأساسية بلغة C#: يفترض هذا البرنامج التعليمي أنك على دراية بمفاهيم برمجة C# الأساسية.

3. بيئة تطوير .NET: يجب أن يكون لديك بيئة تطوير متكاملة مثل Visual Studio مهيأة لتشغيل تطبيقات .NET.

4. مستند نموذجي: سنستخدم مستند Word نموذجيًا يحتوي على أنواع مختلفة من أدوات التنسيق. يمكنك استخدام المستند المذكور في المثال أو إنشاء مستندك الخاص.

5. الوصول إلى وثائق Aspose: للحصول على معلومات أكثر تفصيلاً، راجع [توثيق Aspose.Words](https://reference.aspose.com/words/net/).

## استيراد مساحات الأسماء

لبدء العمل مع Aspose.Words، عليك استيراد مساحات الأسماء ذات الصلة إلى مشروع C# الخاص بك. إليك الطريقة:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

ستتيح لك هذه المساحات الاسمية الوصول إلى الفئات والطرق اللازمة لمعالجة علامات المستندات المنظمة في مستندات Word الخاصة بك.

## الخطوة 1: إعداد مسار المستند الخاص بك

قبل إجراء أي تغييرات، يجب عليك تحديد مسار مستندك. استبدل `"YOUR DOCUMENT DIRECTORY"` مع المسار الفعلي الذي يتم تخزين مستندك فيه.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Structured document tags.docx");
```

## الخطوة 2: تكرار علامات المستند المنظم

لتعديل SDTs، عليك أولاً المرور على جميع SDTs في المستند. يتم ذلك باستخدام `GetChildNodes` طريقة للحصول على جميع العقد من النوع `StructuredDocumentTag`.

```csharp
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    // تعديل SDTs بناءً على نوعها
}
```

## الخطوة 3: تعديل SDTs النصية العادية

إذا كان SDT نصًا عاديًا، فيمكنك استبدال محتواه. أولًا، امسح المحتوى الموجود، ثم أضف نصًا جديدًا.

```csharp
if (sdt.SdtType == SdtType.PlainText)
{
    sdt.RemoveAllChildren();
    Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
    Run run = new Run(doc, "new text goes here");
    para.AppendChild(run);
}
```

التوضيح: هنا، `RemoveAllChildren()` يمسح محتوى SDT الحالي. ثم ننشئ ملفًا جديدًا `Paragraph` و `Run` كائن لإدراج النص الجديد.

## الخطوة 4: تعديل SDTs القائمة المنسدلة

بالنسبة لقوائم SDT المنسدلة، يمكنك تغيير العنصر المحدد عن طريق الوصول إلى `ListItems` المجموعة. هنا، نختار العنصر الثالث في القائمة.

```csharp
if (sdt.SdtType == SdtType.DropDownList)
{
    SdtListItem secondItem = sdt.ListItems[2];
    sdt.ListItems.SelectedValue = secondItem;
}
```

شرح: هذا الكود المقتطف يحدد العنصر في الفهرس ٢ (العنصر الثالث) من القائمة المنسدلة. عدّل الفهرس حسب احتياجاتك.

## الخطوة 5: تعديل SDTs للصور

لتحديث صورة داخل صورة SDT، يمكنك استبدال الصورة الموجودة بأخرى جديدة.

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

الشرح: يتحقق هذا الكود مما إذا كان الشكل يحتوي على صورة ثم يستبدلها بصورة جديدة تقع في `ImagesDir`.

## الخطوة 6: احفظ المستند المعدّل

بعد إجراء كافة التغييرات اللازمة، احفظ المستند المعدل باسم جديد للحفاظ على المستند الأصلي سليمًا.

```csharp
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");
```

التوضيح: يؤدي هذا إلى حفظ المستند باسم ملف جديد حتى تتمكن من التمييز بسهولة بينه وبين المستند الأصلي.

## خاتمة

يُعد تعديل عناصر تحكم المحتوى في مستند Word باستخدام Aspose.Words لـ .NET أمرًا سهلاً بمجرد فهم الخطوات اللازمة. سواءً كنت تُحدّث نصًا، أو تُغيّر اختيارات القائمة المنسدلة، أو تُبدّل الصور، يُوفّر Aspose.Words واجهة برمجة تطبيقات فعّالة لهذه المهام. باتباع هذا البرنامج التعليمي، يُمكنك إدارة عناصر تحكم المحتوى المُهيكلة في مستندك وتخصيصها بفعالية، مما يجعل مستنداتك أكثر ديناميكيةً وتكيّفًا مع احتياجاتك.

## الأسئلة الشائعة

1. ما هي علامة المستند المنظم (SDT)؟

SDTs هي عناصر في مستندات Word تساعد في إدارة وتنسيق محتوى المستند، مثل مربعات النص أو القوائم المنسدلة أو الصور.

2. كيف يمكنني إضافة عنصر منسدلة جديد إلى SDT؟

لإضافة عنصر جديد، استخدم `ListItems` الملكية وإضافة جديد `SdtListItem` إلى المجموعة.

3. هل يمكنني استخدام Aspose.Words لإزالة SDTs من مستند؟

نعم، يمكنك إزالة SDTs عن طريق الوصول إلى عقد المستند وحذف SDT المطلوب.

4. كيف يمكنني التعامل مع SDTs المتداخلة ضمن عناصر أخرى؟

استخدم `GetChildNodes` الطريقة مع المعلمات المناسبة للوصول إلى SDTs المتداخلة.

5. ماذا يجب أن أفعل إذا لم يكن SDT الذي أحتاج إلى تعديله مرئيًا في المستند؟

تأكد من أن SDT غير مخفي أو محمي. تحقق من إعدادات المستند وتأكد من أن الكود يستهدف نوع SDT بشكل صحيح.


### مثال على كود المصدر لتعديل عناصر التحكم في المحتوى باستخدام Aspose.Words لـ .NET 

```csharp
// المسار إلى دليل المستندات الخاص بك 
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

هذا كل شيء! لقد نجحت في تعديل أنواع مختلفة من عناصر التحكم بالمحتوى في مستند Word باستخدام Aspose.Words لـ .NET.

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}