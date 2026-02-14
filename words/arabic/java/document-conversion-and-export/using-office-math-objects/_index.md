---
date: 2026-02-14
description: تعلم كيفية عرض الرياضيات داخل النص، وإدراج معادلة رياضية، والتعامل مع
  كائنات Office Math بسهولة مع Aspose.Words for Java.
linktitle: Using Office Math Objects
second_title: Aspose.Words Java Document Processing API
title: عرض الرياضيات داخل النص باستخدام Office Math في Aspose.Words للـ Java
url: /ar/java/document-conversion-and-export/using-office-math-objects/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# عرض الرياضيات داخل النص باستخدام Office Math في Aspose.Words for Java

في هذا الدرس الشامل ستكتشف كيفية **عرض الرياضيات داخل النص** باستخدام كائنات Office Math في Aspose.Words for Java. سواء كنت بحاجة إلى **إدراج معادلة رياضية** في تقرير أو ضبط تنسيق الصيغ المعقدة بدقة، فإن هذا الدليل يرافقك في كل خطوة — من تحميل مستند Word إلى حفظ النتيجة النهائية.

## إجابات سريعة
- **ماذا يعني “عرض الرياضيات داخل النص”؟** تظهر المعادلة داخل تدفق النص، وليس في سطر منفصل.  
- **أي فئة تمثل كائنًا رياضيًا؟** `OfficeMath` في واجهة برمجة تطبيقات Aspose.Words.  
- **هل يمكنني تغيير المحاذاة؟** نعم، استخدم `setJustification` مع LEFT أو CENTER أو RIGHT.  
- **هل أحتاج إلى ترخيص لهذه الميزة؟** يلزم وجود ترخيص صالح لـ Aspose.Words for Java للاستخدام في بيئة الإنتاج.  
- **ما هو الإصدار المعروض؟** يعمل الكود مع أحدث إصدار من Aspose.Words for Java (2026).

## ما هو “عرض الرياضيات داخل النص”؟
يعني عرض الرياضيات داخل النص أن المعادلة تُعامل كجزء من نص الفقرة، مما يسمح لها بالالتفاف طبيعيًا مع الكلمات المحيطة. هذا مفيد للمعادلات القصيرة التي لا يجب أن تعطل تدفق القراءة.

## لماذا نستخدم كائنات Office Math في Aspose.Words for Java؟
- **تحكم دقيق** في تخطيط المعادلة (inline مقابل display).  
- **معالجة برمجية** للمعادلات دون فتح Word يدويًا.  
- **عرض متسق** عبر المنصات، مثالي لإنشاء التقارير الآلية.

## المتطلبات المسبقة
قبل أن نبدأ، تأكد من أن لديك:

- Aspose.Words for Java مثبتًا ومُشارًا إليه في مشروعك.  
- ملف Word يحتوي بالفعل على معادلة Office Math (مثال: `OfficeMath.docx`).  
- ترخيص صالح إذا كنت تخطط لتشغيل الكود خارج وضع التقييم.

## دليل خطوة بخطوة

### تحميل المستند
أولاً، قم بتحميل المستند الذي يحتوي على معادلة Office Math التي تريد العمل معها:

```java
Document doc = new Document("Your Directory Path" + "OfficeMath.docx");
```

### الوصول إلى كائن Office Math
استرجع أول عقدة Office Math من المستند:

```java
OfficeMath officeMath = (OfficeMath) doc.getChild(NodeType.OFFICE_MATH, 0, true);
```

### تعيين نوع العرض (Inline مقابل Display)
تحكم فيما إذا كانت المعادلة تظهر داخل النص مع الكلمات المحيطة أو في سطر منفصل. لـ **عرض الرياضيات داخل النص**، استخدم تعداد `INLINE`؛ وللسطر المنفصل، استخدم `DISPLAY`:

```java
officeMath.setDisplayType(OfficeMathDisplayType.DISPLAY);
```

*إذا كنت تريد أن تبقى المعادلة داخل النص، استبدل `DISPLAY` بـ `INLINE`.*

### تعيين المحاذاة
ضبط محاذاة المعادلة. أدناه نُحاذيها إلى اليسار، لكن يمكنك أيضًا اختيار `CENTER` أو `RIGHT`:

```java
officeMath.setJustification(OfficeMathJustification.LEFT);
```

### حفظ المستند المعدل
أخيرًا، احفظ التغييرات في ملف جديد:

```java
doc.save("Your Directory Path" + "ModifiedOfficeMath.docx");
```

## الكود الكامل لاستخدام كائنات Office Math في Aspose.Words for Java

```java
        Document doc = new Document("Your Directory Path" + "Office math.docx");
        OfficeMath officeMath = (OfficeMath) doc.getChild(NodeType.OFFICE_MATH, 0, true);
        // OfficeMath display type represents whether an equation is displayed inline with the text or displayed on its line.
        officeMath.setDisplayType(OfficeMathDisplayType.DISPLAY);
        officeMath.setJustification(OfficeMathJustification.LEFT);
        doc.save("Your Directory Path" + "WorkingWithOfficeMath.MathEquations.docx");
```

## المشكلات الشائعة & استكشاف الأخطاء وإصلاحها
- **المعادلة غير موجودة:** تأكد من أن المستند يحتوي فعليًا على كائن Office Math؛ وإلا سيعيد `doc.getChild` القيمة `null`.  
- **نوع العرض لا يؤثر:** تحقق من أنك تستخدم نسخة حديثة من Aspose.Words؛ الإصدارات القديمة قد لا تدعم `OfficeMathDisplayType` بشكل كامل.  
- **استثناء الترخيص:** إذا ظهرت لك رسالة خطأ ترخيص، تحقق مرة أخرى من تحميل ملف الترخيص بشكل صحيح قبل إنشاء كائن `Document`.

## الأسئلة المتكررة

**س: ما هو هدف كائنات Office Math في Aspose.Words for Java؟**  
A: تتيح لك كائنات Office Math تمثيل ومعالجة المعادلات الرياضية برمجيًا، مما يمنحك تحكمًا كاملاً في العرض والتنسيق.

**س: هل يمكنني محاذاة معادلات Office Math بشكل مختلف داخل المستند؟**  
A: نعم، استخدم طريقة `setJustification` لمحاذاة إلى اليسار أو اليمين أو الوسط.

**س: هل Aspose.Words for Java مناسب للتعامل مع مستندات رياضية معقدة؟**  
A: بالتأكيد. المكتبة تدعم بالكامل المعادلات المعقدة، الكسور المتداخلة، المصفوفات، وأكثر من ذلك.

**س: كيف يمكنني معرفة المزيد عن Aspose.Words for Java؟**  
A: للحصول على وثائق شاملة وتنزيلات، زر [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

**س: أين يمكنني تنزيل Aspose.Words for Java؟**  
A: يمكنك تنزيل Aspose.Words for Java من الموقع: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/).

---

**آخر تحديث:** 2026-02-14  
**تم الاختبار مع:** Aspose.Words for Java 24.12 (latest as of Feb 2026)  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}