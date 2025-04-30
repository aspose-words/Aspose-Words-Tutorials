---
"description": "تعلّم كيفية البحث عن نص واستبداله في مستندات Word باستخدام Aspose.Words لجافا. دليل خطوة بخطوة مع أمثلة برمجية. حسّن مهاراتك في التعامل مع مستندات جافا."
"linktitle": "البحث عن النص واستبداله"
"second_title": "واجهة برمجة تطبيقات معالجة مستندات Java Aspose.Words"
"title": "البحث عن نص واستبداله في Aspose.Words لـ Java"
"url": "/ar/java/document-manipulation/finding-and-replacing-text/"
"weight": 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# البحث عن نص واستبداله في Aspose.Words لـ Java


## مقدمة للبحث عن النص واستبداله في Aspose.Words لـ Java

Aspose.Words for Java هي واجهة برمجة تطبيقات Java فعّالة تُمكّنك من العمل مع مستندات Word برمجيًا. من المهام الشائعة عند التعامل مع مستندات Word البحث عن نص واستبداله. سواءً كنت بحاجة إلى تحديث العناصر النائبة في القوالب أو إجراء عمليات معالجة نصية أكثر تعقيدًا، يُمكن لـ Aspose.Words for Java مساعدتك في تحقيق أهدافك بكفاءة.

## المتطلبات الأساسية

قبل أن نتعمق في تفاصيل البحث عن النص واستبداله، تأكد من توفر المتطلبات الأساسية التالية:

- بيئة تطوير جافا
- Aspose.Words لمكتبة Java
- نموذج مستند Word للعمل عليه

يمكنك تنزيل مكتبة Aspose.Words لـ Java من [هنا](https://releases.aspose.com/words/java/).

## البحث عن نص بسيط واستبداله

```java
// تحميل المستند
Document doc = new Document("your-document.docx");

// إنشاء DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// البحث عن النص واستبداله
builder.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// حفظ المستند المعدل
doc.save("modified-document.docx");
```

في هذا المثال، نقوم بتحميل مستند Word وإنشاء `DocumentBuilder`، واستخدم `replace` طريقة للبحث عن "النص القديم" واستبداله بـ "النص الجديد" داخل المستند.

## استخدام التعبيرات العادية

توفر التعبيرات العادية إمكانيات مطابقة أنماط فعّالة للبحث عن النصوص واستبدالها. يدعم Aspose.Words لـ Java التعبيرات العادية لعمليات بحث واستبدال أكثر تقدمًا.

```java
// تحميل المستند
Document doc = new Document("your-document.docx");

// إنشاء DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// استخدم التعبيرات العادية للبحث عن النص واستبداله
Pattern regex = Pattern.compile("your-pattern");
builder.getRange().replace(regex, "replacement-text", new FindReplaceOptions());

// حفظ المستند المعدل
doc.save("modified-document.docx");
```

في هذا المثال، نستخدم نمط تعبير عادي للبحث عن نص واستبداله داخل المستند.

## تجاهل النص الموجود داخل الحقول

يمكنك تكوين Aspose.Words لتجاهل النص الموجود داخل الحقول عند إجراء عمليات البحث والاستبدال.

```java
// تحميل المستند
Document doc = new Document("your-document.docx");

// إنشاء مثيل FindReplaceOptions وتعيين IgnoreFields إلى true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreFields(true);

// استخدم الخيارات عند استبدال النص
doc.getRange().replace("text-to-replace", "new-text", options);

// حفظ المستند المعدل
doc.save("modified-document.docx");
```

يعد هذا مفيدًا عندما تريد استبعاد النص الموجود داخل الحقول، مثل حقول الدمج، من الاستبدال.

## تجاهل النص داخل مراجعات الحذف

يمكنك تكوين Aspose.Words لتجاهل النص الموجود داخل مراجعات الحذف أثناء عمليات البحث والاستبدال.

```java
// تحميل المستند
Document doc = new Document("your-document.docx");

// إنشاء مثيل FindReplaceOptions وتعيين IgnoreDeleted إلى true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreDeleted(true);

// استخدم الخيارات عند استبدال النص
doc.getRange().replace("text-to-replace", "new-text", options);

// حفظ المستند المعدل
doc.save("modified-document.docx");
```

يتيح لك هذا استبعاد النص الذي تم وضع علامة عليه للحذف في التغييرات المتعقبة من أن يتم استبداله.

## تجاهل النص داخل مراجعات الإدراج

يمكنك تكوين Aspose.Words لتجاهل النص الموجود داخل مراجعات الإدراج أثناء عمليات البحث والاستبدال.

```java
// تحميل المستند
Document doc = new Document("your-document.docx");

// إنشاء مثيل FindReplaceOptions وتعيين IgnoreInserted إلى true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreInserted(true);

// استخدم الخيارات عند استبدال النص
doc.getRange().replace("text-to-replace", "new-text", options);

// حفظ المستند المعدل
doc.save("modified-document.docx");
```

يتيح لك هذا استبعاد النص الذي تم وضع علامة عليه كمدرج في التغييرات المتعقبة من الاستبدال.

## استبدال النص بـ HTML

بإمكانك استخدام Aspose.Words for Java لاستبدال النص بمحتوى HTML.

```java
// تحميل المستند
Document doc = new Document("your-document.docx");

// إنشاء مثيل FindReplaceOptions باستخدام استدعاء استبدال مخصص
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceWithHtmlEvaluator(options));

// استخدم الخيارات عند استبدال النص
doc.getRange().replace("text-to-replace", "new-html-content", options);

// حفظ المستند المعدل
doc.save("modified-document.docx");
```

في هذا المثال، نستخدم مخصصًا `ReplaceWithHtmlEvaluator` لاستبدال النص بمحتوى HTML.

## استبدال النص في الرؤوس والتذييلات

يمكنك العثور على النص واستبداله داخل رؤوس وتذييلات مستند Word الخاص بك.

```java
// تحميل المستند
Document doc = new Document("your-document.docx");

// احصل على مجموعة من الرؤوس والتذييلات
HeaderFooterCollection headersFooters = doc.getFirstSection().getHeadersFooters();

// اختر نوع الرأس أو التذييل الذي تريد استبدال النص فيه (على سبيل المثال، HeaderFooterType.FOOTER_PRIMARY)
HeaderFooter footer = headersFooters.getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);

// إنشاء مثيل FindReplaceOptions وتطبيقه على نطاق التذييل
FindReplaceOptions options = new FindReplaceOptions();
footer.getRange().replace("text-to-replace", "new-text", options);

// حفظ المستند المعدل
doc.save("modified-document.docx");
```

يتيح لك هذا إجراء عمليات استبدال للنصوص على وجه التحديد في الرؤوس والتذييلات.

## إظهار التغييرات لأوامر الرأس والتذييل

يمكنك استخدام Aspose.Words لإظهار التغييرات في ترتيب الرأس والتذييل في المستند الخاص بك.

```java
// تحميل المستند
Document doc = new Document("your-document.docx");

// احصل على القسم الأول
Section firstPageSection = doc.getFirstSection();

// إنشاء مثيل FindReplaceOptions وتطبيقه على نطاق المستند
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceLog());

// استبدال النص الذي يؤثر على ترتيبات الرأس والتذييل
doc.getRange().replace(Pattern.compile("(header|footer)"), "", options);

// حفظ المستند المعدل
doc.save("modified-document.docx");
```

يتيح لك هذا إمكانية تصور التغييرات المتعلقة بترتيبات الرأس والتذييل في مستندك.

## استبدال النص بالحقول

بإمكانك استبدال النص بالحقول باستخدام Aspose.Words لـ Java.

```java
// تحميل المستند
Document doc = new Document("your-document.docx");

// إنشاء مثيل FindReplaceOptions وتعيين استدعاء استبدال مخصص للحقول
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceTextWithFieldHandler(FieldType.FIELD_MERGE_FIELD));

// استخدم الخيارات عند استبدال النص
doc.getRange().replace(Pattern.compile("PlaceHolder(\\d+)"), "", options);

// حفظ المستند المعدل
doc.save("modified-document.docx");
```

في هذا المثال، نقوم باستبدال النص بالحقول وتحديد نوع الحقل (على سبيل المثال، `FieldType.FIELD_MERGE_FIELD`).

## الاستبدال بالمُقيِّم

بإمكانك استخدام مُقيِّم مخصص لتحديد النص البديل بشكل ديناميكي.

```java
// تحميل المستند
Document doc = new Document("your-document.docx");

// إنشاء مثيل FindReplaceOptions وتعيين استدعاء استبدال مخصص
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new MyReplaceEvaluator());

// استخدم الخيارات عند استبدال النص
doc.getRange().replace(Pattern.compile("[s|m]ad"), "", options);

// حفظ المستند المعدل
doc.save("modified-document.docx");
```

في هذا المثال، نستخدم مُقيِّمًا مخصصًا (`MyReplaceEvaluator`) لاستبدال النص.

## الاستبدال باستخدام Regex

يتيح لك Aspose.Words for Java استبدال النص باستخدام التعبيرات العادية.

```java
// تحميل المستند
Document doc = new Document("your-document.docx");

// استخدم التعبيرات العادية للبحث عن النص واستبداله
doc.getRange().replace(Pattern.compile("[s|m]ad"), "bad", new FindReplaceOptions());

// حفظ المستند المعدل
doc.save("modified-document.docx");
```

في هذا المثال، نستخدم نمط تعبير عادي للبحث عن نص واستبداله داخل المستند.

## التعرف على أنماط الاستبدال والاستبدالات داخلها

بإمكانك التعرف على أنماط الاستبدال وإجراء الاستبدالات فيها باستخدام Aspose.Words لـ Java.

```java
// تحميل المستند
Document doc = new Document("your-document.docx");

// إنشاء مثيل FindReplaceOptions مع تعيين UseSubstitutions على true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseSubstitutions(true);

// استخدم الخيارات عند استبدال النص بنمط
doc.getRange().replace(Pattern.compile("([A-z]+) give money to ([A-z]+)"), "$2 take money from $1", options);

// حفظ المستند المعدل
doc.save("modified-document.docx");
```

يتيح لك هذا إجراء عمليات الاستبدال داخل أنماط الاستبدال للحصول على عمليات استبدال أكثر تقدمًا.

## الاستبدال بسلسلة

بإمكانك استبدال النص بسلسلة بسيطة باستخدام Aspose.Words لـ Java.

```java
// تحميل المستند
Document doc = new Document("your-document.docx");

// استبدال النص بسلسلة
doc.getRange().replace("text-to-replace", "new-string", new FindReplaceOptions());

// حفظ المستند المعدل
doc.save("modified-document.docx");
```

في هذا المثال، نقوم باستبدال "text-to-replace" بـ "new-string" داخل المستند.

## استخدام الترتيب القديم

يمكنك استخدام الترتيب القديم عند إجراء عمليات البحث والاستبدال.

```java
// تحميل المستند
Document doc = new Document("your-document.docx");

// إنشاء مثيل FindReplaceOptions وتعيين UseLegacyOrder إلى true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseLegacyOrder(true);

// استخدم الخيارات عند استبدال النص
doc.getRange().replace(Pattern.compile("\\[(.*?)\\]"), "", options);

// حفظ المستند المعدل
doc.save("modified-document.docx");
```

يتيح لك هذا استخدام الترتيب القديم لعمليات البحث والاستبدال.

## استبدال النص في جدول

يمكنك العثور على نص واستبداله داخل الجداول في مستند Word الخاص بك.

```java
// تحميل المستند
Document doc = new Document("your-document.docx");

// احصل على جدول محدد (على سبيل المثال، الجدول الأول)
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);

// استخدم FindReplaceOptions لاستبدال النص في الجدول
table.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// حفظ المستند المعدل
doc.save("modified-document.docx");
```

يتيح لك هذا إجراء عمليات استبدال للنصوص على وجه التحديد داخل الجداول.

## خاتمة

يوفر Aspose.Words لجافا إمكانيات شاملة للبحث عن النصوص واستبدالها في مستندات Word. سواءً كنت بحاجة إلى استبدال نصوص بسيطة أو عمليات أكثر تعقيدًا باستخدام التعبيرات العادية، أو معالجة الحقول، أو أدوات التقييم المخصصة، فإن Aspose.Words لجافا يلبي احتياجاتك. احرص على استكشاف الوثائق والأمثلة الشاملة التي يوفرها Aspose للاستفادة القصوى من إمكانات مكتبة جافا القوية هذه.

## الأسئلة الشائعة

### كيف يمكنني تنزيل Aspose.Words لـ Java؟

يمكنك تنزيل Aspose.Words for Java من الموقع الإلكتروني عن طريق زيارة [هذا الرابط](https://releases.aspose.com/words/java/).

### هل يمكنني استخدام التعبيرات العادية لاستبدال النص؟

نعم، يمكنك استخدام التعبيرات العادية لاستبدال النصوص في Aspose.Words لجافا. هذا يتيح لك إجراء عمليات بحث واستبدال أكثر تقدمًا ومرونة.

### كيف يمكنني تجاهل النص الموجود داخل الحقول أثناء الاستبدال؟

لتجاهل النص الموجود داخل الحقول أثناء الاستبدال، يمكنك ضبط `IgnoreFields` ممتلكات `FindReplaceOptions` ل `true`يضمن هذا استبعاد النص الموجود داخل الحقول، مثل حقول الدمج، من الاستبدال.

### هل يمكنني استبدال النص داخل الرؤوس والتذييلات؟

نعم، يمكنك استبدال النص داخل رؤوس وتذييلات مستند Word. ما عليك سوى الوصول إلى الرأس أو التذييل المناسب واستخدام `replace` الطريقة مع المطلوب `FindReplaceOptions`.

### ما هو خيار UseLegacyOrder؟

ال `UseLegacyOrder` الخيار في `FindReplaceOptions` يسمح لك باستخدام الترتيب القديم عند إجراء عمليات البحث والاستبدال. قد يكون هذا مفيدًا في بعض الحالات التي يُفضّل فيها استخدام الترتيب القديم.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}