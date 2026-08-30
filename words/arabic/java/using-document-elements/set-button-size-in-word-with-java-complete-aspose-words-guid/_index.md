---
category: general
date: 2026-07-16
description: ضبط حجم الزر برمجيًا في مستند Word باستخدام Aspose.Words للغة Java. تعلّم
  كيفية إدراج زر ActiveX، وضبط موقع الزر والمزيد.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size
- insert activex button
- programmatically add button
- set button location
- create word document button
language: ar
lastmod: 2026-07-16
og_description: تعيين حجم الزر في مستند Word باستخدام Java. يوضح هذا الدليل خطوة بخطوة
  كيفية إدراج زر ActiveX، وتحديد موقع الزر، وإضافة الزر برمجيًا.
og_image_alt: Screenshot of a Word document where the button size has been set using
  Aspose.Words for Java
og_title: تحديد حجم الزر في Word باستخدام Java – دليل Aspose.Words الكامل
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  headline: Set Button Size in Word with Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  name: Set Button Size in Word with Java – Complete Aspose.Words Guide
  steps:
  - name: Expected Output Screenshot
    text: '![Word document showing the inserted button with the set button size](https://example.com/images/set-button-size.png
      "Screenshot of a Word file where the button size has been set using Aspose.Words
      for Java")'
  - name: “Can I set the button size using centimeters instead of points?”
    text: Word’s API only accepts points, but you can convert centimeters to points
      (`points = cm * 28.3465`). Write a small helper method if you prefer metric
      units.
  - name: “What if I need the button to appear on a specific page?”
    text: After inserting the button, you can move the cursor to a particular page
      using `builder.moveToPage(pageNumber)`. Insert the control right after the move,
      then set its location as shown above.
  - name: “Does this work with .doc (Word 97‑2003) files?”
    text: Yes—Aspose.Words automatically handles older formats. Just change the file
      extension in `doc.save("Demo.doc")`.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: تحديد حجم الزر في Word باستخدام Java – دليل Aspose.Words الكامل
url: /ar/java/using-document-elements/set-button-size-in-word-with-java-complete-aspose-words-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تعيين حجم الزر في Word باستخدام Java – دليل Aspose.Words الكامل

هل تساءلت يومًا كيف **set button size** داخل ملف Word دون فتح الواجهة؟ لست وحدك. عندما تحتاج إلى إنشاء مستند نموذج مملوء في الوقت الفعلي — مثل حزمة الانضمام مع زر “Submit” — فإن القيام بذلك برمجيًا يوفر ساعات من العمل اليدوي.

في هذا الدرس سنستعرض الخطوات الدقيقة **insert ActiveX button**، تعديل أبعاده، وضعه في الموضع الصحيح، وأخيرًا حفظ الملف. في النهاية ستتمكن من **programmatically add button** إلى أي مستند Word باستخدام Aspose.Words for Java.

## المتطلبات المسبقة – ما تحتاجه قبل البدء

- **Java Development Kit (JDK) 8+** – الكود يعمل على أي JDK حديث.
- مكتبة **Aspose.Words for Java** (حمّل أحدث JAR من الموقع الرسمي).  
- **IDE** من اختيارك — IntelliJ IDEA، Eclipse، أو حتى محرر نصوص بسيط.
- إلمام أساسي بصياغة Java؛ لا تحتاج إلى معرفة عميقة بأتمتة Word.

> *نصيحة محترف:* احرص على وجود ملف Aspose.Words JAR في مسار الـ classpath الخاص بالمشروع، وإلا ستواجه `ClassNotFoundException` في اللحظة التي تحاول فيها استيراد `com.aspose.words.*`.

## الخطوة 1: إنشاء مستند Word جديد

أول ما نقوم به هو إنشاء مستند فارغ و`DocumentBuilder`. فكر في الـ builder كقلم يتيح لنا رسم أي شيء داخل الملف.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty document.
        Document doc = new Document();

        // DocumentBuilder gives us a fluent API to add content.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **لماذا هذا مهم:** كائن `Document` يمثل ملف .docx بالكامل، بينما `DocumentBuilder` هو العامل الأساسي الذي يتيح لنا إدراج فقرات، جداول، و—نعم—ActiveX controls.

## الخطوة 2: إدراج زر ActiveX – لحظة “Insert ActiveX Button”

الآن نقوم فعليًا **insert activex button** داخل المستند. توفر Aspose.Words طريقة مريحة `insertForms2OleControl` تُعيد كائن `Forms2OleControl`.

```java
        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");   // Programmatic name.
        commandButton.setCaption("Submit");   // Text shown on the button.
```

> *ما الذي يحدث خلف الكواليس؟* `Forms2OleControlType.COMMAND_BUTTON` يخبر Word أننا نريد CommandButton كلاسيكي، وهو نفس النوع الذي يمكنك سحبه من تبويب Developer في الواجهة.

## الخطوة 3: تعيين حجم الزر وموقعه – منطق “Set Button Size” الأساسي

هنا يبرز الكلمة المفتاحية الأساسية. سنقوم **set button size** وكذلك **set button location** حتى يظهر التحكم بالضبط حيث نريد على الصفحة.

```java
        // Position the button (distance from the left/top edges in points).
        commandButton.setLeft(100);   // 100 points from the left margin.
        commandButton.setTop(150);    // 150 points from the top margin.

        // Set the button's dimensions.
        commandButton.setWidth(80);   // Width = 80 points.
        commandButton.setHeight(30);  // Height = 30 points.
```

> **لماذا يجب أن يهمك:** النقاط هي وحدة القياس الأصلية في Word (نقطة واحدة = 1/72 بوصة). من خلال تعديل `setLeft`، `setTop`، `setWidth`، و`setHeight` تحصل على تحكم دقيق بالبكسل — لا مزيد من “يبدو صحيحًا على شاشتي لكنه ليس كذلك على الطابعة”.

> *مشكلة شائعة:* نسيان تعيين العرض أو الارتفاع سيترك الزر بالحجم الافتراضي، والذي قد يكون صغيرًا جدًا للنقر. احرص دائمًا على تحديد كلا القيمتين.

## الخطوة 4: حفظ المستند – إكمال “Create Word Document Button”

أخيرًا، نكتب الملف إلى القرص. الاسم يشير إلى أننا **creating a Word document button** داخل ملف .docx.

```java
        // Persist the document to the file system.
        doc.save("CommandButtonDemo.docx");
    }
}
```

عند فتح `CommandButtonDemo.docx` في Microsoft Word، ستظهر لك زر **Submit** موضعه 100 pt من الحافة اليسرى و150 pt من الأعلى، بحجم 80 × 30 pt. النقر عليه في الواجهة سيُفعل السلوك الافتراضي لـ ActiveX (يمكنك ربطه بـ VBA لاحقًا إذا لزم الأمر).

### لقطة الشاشة المتوقعة

![مستند Word يظهر الزر المدرج مع حجم الزر المحدد](https://example.com/images/set-button-size.png "لقطة شاشة لملف Word حيث تم تعيين حجم الزر باستخدام Aspose.Words for Java")

*نص بديل:* تعيين حجم الزر في مستند Word باستخدام Java

## الخطوة 5 (اختياري): إضافة المزيد من العناصر أو تنسيق الزر

إذا كنت بحاجة إلى **programmatically add button** أكثر من زر Submit واحد، ما عليك سوى تكرار كتلة الإدراج بأسماء وعناوين جديدة. يمكنك أيضًا تعديل الخط، لون الخلفية، أو حتى ربط ماكرو VBA لاحقًا.

```java
        // Example: Adding a Cancel button next to Submit.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);   // Position it 90 points to the right of Submit.
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);
```

> *نصيحة:* حافظ على تناسق أبعاد جميع الأزرار للحصول على مظهر احترافي. طريقة سريعة هي تخزين العرض/الارتفاع في ثوابت.

## الأسئلة الشائعة والحالات الخاصة

### “هل يمكنني تعيين حجم الزر بالسنتيمترات بدلاً من النقاط؟”

واجهة Word API تقبل النقاط فقط، لكن يمكنك تحويل السنتيمترات إلى نقاط (`points = cm * 28.3465`). اكتب طريقة مساعدة صغيرة إذا كنت تفضّل الوحدات المترية.

### “ماذا لو أردت أن يظهر الزر في صفحة محددة؟”

بعد إدراج الزر، يمكنك نقل المؤشر إلى صفحة معينة باستخدام `builder.moveToPage(pageNumber)`. أدخل التحكم مباشرة بعد النقل، ثم عيّن موقعه كما هو موضح أعلاه.

### “هل يعمل هذا مع ملفات .doc (Word 97‑2003)؟”

نعم — Aspose.Words يتعامل تلقائيًا مع الصيغ القديمة. فقط غيّر امتداد الملف في `doc.save("Demo.doc")`.

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه‑ولصقه في فئة Java وتشغيله فورًا (مع افتراض وجود Aspose.Words JAR في الـ classpath).

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first ActiveX CommandButton.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");

        // 3️⃣ Set button location and size – the core set button size logic.
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // 4️⃣ (Optional) Add a second button for illustration.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);

        // 5️⃣ Save the document – you’ve now created a Word document button.
        doc.save("CommandButtonDemo.docx");
    }
}
```

شغّل البرنامج، افتح `CommandButtonDemo.docx` المُولَّد، وسترى زرين بحجم منسق جاهزين للتفاعل.

## الخلاصة – لقد أتقنت تعيين حجم الزر في Word

لقد استعرضنا حلًا كاملاً من البداية إلى النهاية لـ **set button size** و**set button location** باستخدام Aspose.Words for Java. باتباع الخطوات يمكنك **insert activex button**، **programmatically add button**، وفي النهاية **create word document button** التي تعمل تمامًا كما تحتاج.

ما الخطوة التالية؟ جرّب وضع الزر داخل خلية جدول، أو أرفق ماكرو VBA يتحقق من حقول النموذج قبل الإرسال. نفس النمط يعمل مع عناصر ActiveX أخرى مثل مربعات الاختيار أو القوائم المنسدلة — فقط استبدل `Forms2OleControlType.COMMAND_BUTTON` بالقيمة المناسبة من الـ enum.

إذا واجهت أي صعوبات، اترك تعليقًا أدناه. برمجة سعيدة، واستمتع بقوة إنشاء مستندات Word تلقائيًا!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة شفرة كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف نهج تنفيذ بديلة في مشاريعك.

- [كيفية تعيين LoadOptions في Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [كيفية إزالة التذييلات من مستندات Word باستخدام Aspose.Words for Java](/words/english/java/document-manipulation/removing-content-from-documents/)
- [Aspose.Words Java: دليل شامل لمعالجة مستندات Word](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}