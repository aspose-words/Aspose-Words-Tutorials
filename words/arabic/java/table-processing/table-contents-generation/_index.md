---
title: جدول المحتويات الجيل
linktitle: جدول المحتويات الجيل
second_title: واجهة برمجة تطبيقات معالجة المستندات في Java Aspose.Words
description: تعرف على كيفية إنشاء جدول محتويات ديناميكي باستخدام Aspose.Words للغة Java. أتقن إنشاء جدول المحتويات من خلال الإرشادات خطوة بخطوة وأمثلة التعليمات البرمجية المصدرية.
weight: 14
url: /ar/java/table-processing/table-contents-generation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# جدول المحتويات الجيل

## مقدمة

هل واجهت صعوبة في إنشاء جدول محتويات (TOC) ديناميكي واحترافي المظهر في مستندات Word الخاصة بك؟ لا داعي للبحث أكثر! باستخدام Aspose.Words for Java، يمكنك أتمتة العملية بالكامل، مما يوفر الوقت ويضمن الدقة. سواء كنت تقوم بإنشاء تقرير شامل أو ورقة أكاديمية، فسيرشدك هذا البرنامج التعليمي خلال إنشاء جدول محتويات (TOC) برمجيًا باستخدام Java. هل أنت مستعد للبدء؟ لنبدأ!

## المتطلبات الأساسية

قبل أن نبدأ في الترميز، تأكد من أن لديك ما يلي:

1.  مجموعة تطوير Java (JDK): مثبتة على نظامك. يمكنك تنزيلها من[موقع أوراكل](https://www.oracle.com/java/technologies/javase-downloads.html).
2.  Aspose.Words for Java Library: قم بتنزيل أحدث إصدار من[صفحة الإصدار](https://releases.aspose.com/words/java/).
3. بيئة التطوير المتكاملة (IDE): مثل IntelliJ IDEA، أو Eclipse، أو NetBeans.
4.  ترخيص Aspose المؤقت: لتجنب قيود التقييم، احصل على[رخصة مؤقتة](https://purchase.aspose.com/temporary-license/).

## استيراد الحزم

لاستخدام Aspose.Words for Java بشكل فعال، تأكد من استيراد الفئات المطلوبة. فيما يلي الاستيرادات:

```java
import com.aspose.words.*;
```

اتبع الخطوات التالية لإنشاء جدول محتويات ديناميكي في مستند Word الخاص بك.

## الخطوة 1: تهيئة المستند وDocumentBuilder

 الخطوة الأولى هي إنشاء مستند جديد واستخدامه`DocumentBuilder` فئة للتلاعب بها.


```java
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

- `Document`:يمثل مستند Word.
- `DocumentBuilder`:فئة مساعدة تسمح بالتعامل بسهولة مع المستند.

## الخطوة 2: إدراج جدول المحتويات

الآن، دعونا نقوم بإدراج جدول المحتويات في بداية المستند.


```java
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");
builder.insertBreak(BreakType.PAGE_BREAK);
```

- `insertTableOfContents`:يُدرج حقل جدول المحتويات. تحدد المعلمات ما يلي:
  - `\o "1-3"`:تتضمن عناوين المستويات من 1 إلى 3.
  - `\h`:إنشاء روابط تشعبية للمدخلات.
  - `\z`:قم بإخفاء أرقام الصفحات لمستندات الويب.
  - `\u`:الحفاظ على أنماط الارتباطات التشعبية.
- `insertBreak`:يضيف فاصل الصفحة بعد جدول المحتويات.

## الخطوة 3: إضافة عناوين لملء جدول المحتويات

لتعبئة جدول المحتويات، تحتاج إلى إضافة فقرات ذات أنماط عناوين.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 1");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_2);
builder.writeln("Heading 1.1");
builder.writeln("Heading 1.2");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 2");
```

- `setStyleIdentifier` :يضبط نمط الفقرة إلى مستوى عنوان محدد (على سبيل المثال،`HEADING_1`, `HEADING_2`).
- `writeln`:يضيف النص إلى المستند بالنمط المحدد.

## الخطوة 4: إضافة عناوين متداخلة

لإظهار مستويات جدول المحتويات، قم بتضمين العناوين المتداخلة.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_3);
builder.writeln("Heading 3.1.1");
builder.writeln("Heading 3.1.2");
builder.writeln("Heading 3.1.3");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_4);
builder.writeln("Heading 3.1.3.1");
builder.writeln("Heading 3.1.3.2");
```

- أضف عناوين ذات مستويات أعمق لإظهار التسلسل الهرمي في جدول المحتويات.

## الخطوة 5: تحديث حقول جدول المحتويات

يجب تحديث حقل جدول المحتويات لعرض أحدث العناوين.


```java
doc.updateFields();
```

- `updateFields`:تحديث كافة الحقول في المستند، مما يضمن أن يعكس جدول المحتويات العناوين المضافة.

## الخطوة 6: حفظ المستند

وأخيرًا، احفظ المستند بالتنسيق المطلوب.


```java
doc.save(dataDir + "DocumentBuilder.InsertToc.docx");
```

- `save` :تصدير المستند إلى`.docx` الملف. يمكنك تحديد تنسيقات أخرى مثل`.pdf` أو`.txt` إذا لزم الأمر.

## خاتمة

تهانينا! لقد نجحت في إنشاء جدول محتويات ديناميكي في مستند Word باستخدام Aspose.Words for Java. باستخدام بضعة أسطر فقط من التعليمات البرمجية، قمت بأتمتة مهمة كان من الممكن أن تستغرق ساعات. إذن، ما الخطوة التالية؟ حاول تجربة أنماط وتنسيقات عناوين مختلفة لتخصيص جدول المحتويات الخاص بك وفقًا لاحتياجات محددة.

## الأسئلة الشائعة

### هل يمكنني تخصيص تنسيق جدول المحتويات بشكل أكبر؟
بالتأكيد! يمكنك تعديل معلمات جدول المحتويات مثل تضمين أرقام الصفحات أو محاذاة النص أو استخدام أنماط العناوين المخصصة.

### هل الترخيص إلزامي لـ Aspose.Words لـ Java؟
 نعم، يلزم الحصول على ترخيص للحصول على الوظائف الكاملة. يمكنك البدء بـ[رخصة مؤقتة](https://purchase.aspose.com/temporary-license/).

### هل يمكنني إنشاء جدول محتويات لمستند موجود؟
 نعم! قم بتحميل المستند إلى`Document` الكائن واتبع نفس الخطوات لإدراج جدول المحتويات وتحديثه.

### هل يعمل هذا لتصدير ملفات PDF؟
 نعم، سيظهر جدول المحتويات في ملف PDF إذا قمت بحفظ المستند في`.pdf` شكل.

### أين يمكنني العثور على مزيد من الوثائق؟
 تحقق من[توثيق Aspose.Words للغة Java](https://reference.aspose.com/words/java/) لمزيد من الأمثلة والتفاصيل.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
