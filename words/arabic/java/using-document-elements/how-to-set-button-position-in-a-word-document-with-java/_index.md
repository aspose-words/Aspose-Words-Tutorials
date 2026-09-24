---
category: general
date: 2026-09-24
description: تحديد موضع الزر في مستند Word باستخدام Java و Aspose.Words. تعلم كيفية
  إدراج زر، إضافة عنصر تحكم ActiveX، وإنشاء مستند Word بأسلوب Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button position
- how to insert button
- add activex control
- add button to word
- create word document java
language: ar
lastmod: 2026-09-24
og_description: تحديد موضع الزر في مستند Word باستخدام Java. يوضح هذا الدليل كيفية
  إدراج زر، إضافة عنصر تحكم ActiveX، وإنشاء مستند Word باستخدام Java مع Aspose.Words.
og_image_alt: Screenshot of a Word document showing a CommandButton positioned at
  100 px left and 150 px top
og_title: تحديد موضع الزر في مستند Word باستخدام Java – دليل كامل
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  headline: How to set button position in a Word document with Java
  type: TechArticle
- description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  name: How to set button position in a Word document with Java
  steps:
  - name: Expected output
    text: '* A `.docx` file named **CommandButtonDemo.docx**. * Inside the document,
      a **CommandButton** labeled “Click Me” appears 100 px from the left margin and
      150 px from the top margin. * The button responds to clicks when the document
      is opened in Word (it will display a default ActiveX message unless y'
  - name: Adding multiple buttons
    text: If you need to **add button to Word** more than once, repeat steps 3‑5 with
      a new `Forms2OleControl` instance each time. Remember to adjust the `setTop`
      value so buttons don’t overlap.
  - name: Working without a license
    text: 'Aspose.Words adds a watermark when used without a license. For production
      code, purchase a license and apply it at the start of `main`:'
  - name: Compatibility with older Office versions
    text: 'ActiveX controls are supported in the `.doc` (Word 97‑2003) format. To
      create a legacy file, change the save format:'
  - name: Next steps
    text: '* Explore other `Forms2OleControl.ControlType` values (e.g., `CHECKBOX`,
      `TEXTBOX`) to build richer forms. * Combine the button with VBA macros for custom
      click handling. * Use Aspose.Words’ mail‑merge feature to generate personalized
      documents that already contain interactive controls.'
  type: HowTo
- questions:
  - answer: Yes. Aspose.Words is pure Java and runs on any JDK 8+ implementation,
      including OpenJDK.
    question: Does this work with OpenJDK?
  - answer: ActiveX button appearance is controlled by the host application (Word).
      You can attach VBA code to modify properties at runtime, but the static appearance
      is limited to the default style.
    question: Can I change the button’s font or color?
  - answer: 'Move the `DocumentBuilder` cursor into the cell before calling `insertForms2OleControl`.
      The control will inherit the cell’s layout, and you can still use `setLeft`/`setTop`
      for fine‑tuning. ## Conclusion You now know how to **set button position** in
      a Word document using Java, how to **how to inse'
    question: What if I need to place the button inside a table cell?
  type: FAQPage
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- CommandButton
title: كيفية تعيين موضع الزر في مستند Word باستخدام Java
url: /ar/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية ضبط موضع الزر في مستند Word باستخدام Java

إذا كنت بحاجة إلى **ضبط موضع الزر** داخل ملف Word، فإن هذا الدليل يوضح لك حلاً كاملاً وقابلاً للتنفيذ. سواءً كنت تبني قالبًا يتطلب تفاعل المستخدم أو تقوم بأتمتة نموذج، ستتعلم بالضبط **كيفية إدراج زر** باستخدام Aspose.Words for Java والتحكم في وضعه.

يغطي الدليل كل ما تحتاجه **لإضافة تحكم ActiveX** إلى مستند Word، ويشرح كيفية **إضافة زر إلى Word**، ويظهر العملية الكاملة لإنشاء مستند Word باستخدام Java. لا توجد مراجع خارجية مطلوبة—فقط قم بالنسخ، التشغيل، والتحقق من النتيجة.

## المتطلبات المسبقة

* تثبيت Java 17 (أو أي بيئة تشغيل Java 8+).
* Maven أو Gradle لإدارة التبعيات.
* رخصة Aspose.Words for Java (الإصدار التجريبي المجاني يعمل للتقييم).
* فهم أساسي لبنية جافا.

> **نصيحة احترافية:** احتفظ بملفات Aspose.Words JAR في مجلد `libs/` وأضفها إلى مسار الفئة (classpath) لمشروعك لتجنب تعارض الإصدارات.

## الخطوة 1: إعداد مشروع Maven

أنشئ مشروع Maven بسيط (أو استخدم Gradle) وأضف تبعية Aspose.Words:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-button-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest at time of writing -->
        </dependency>
    </dependencies>
</project>
```

تشغيل الأمر `mvn clean compile` يقوم بتنزيل المكتبة وإعداد مسار البناء.

## الخطوة 2: إنشاء مستند Word جديد

العملية الأولى هي **إنشاء مستند Word باستخدام Java**. تقوم بإنشاء كائن `Document` و`DocumentBuilder` يتيح لك تحرير الملف.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

تمثل فئة `Document` الملف .docx بالكامل، بينما يوفر `DocumentBuilder` واجهة برمجة تطبيقات سلسة لإدراج المحتوى.

## الخطوة 3: كيفية إدراج زر – إضافة تحكم ActiveX

تُظهر Aspose.Words فئة `Forms2OleControl` لإدراج تحكمات ActiveX القديمة مثل CommandButton. تُظهر هذه الخطوة الطريقة الدقيقة **كيفية إدراج زر** في المستند.

```java
        // Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
```

طريقة `insertForms2OleControl` تُعيد كائن `Forms2OleControl` يمكنك تكوينه. هذا هو جوهر عملية **إضافة تحكم ActiveX**.

## الخطوة 4: ضبط موضع الزر

الآن نقوم فعليًا **بتحديد موضع الزر**. طرق التحكم `setLeft` و `setTop` تقبل قيمًا بوحدات النقاط (1 pt = 1/72 in). لضبط الزر وفق إحداثيات الشاشة المعتادة، يمكنك تحويل البكسل إلى نقاط (1 px ≈ 0.75 pt). في المثال نضع الزر على بعد 100 px من الحافة اليسرى و150 px من الحافة العليا.

```java
        // Position the button on the page
        commandButton.setLeft(100 * 0.75);   // 75 pt ≈ 100 px
        commandButton.setTop(150 * 0.75);    // 112.5 pt ≈ 150 px
```

نظرًا لأن منطق **تحديد موضع الزر** مُغلق هنا، يمكنك إعادة استخدام هذه الأسطر كلما احتجت إلى نقل التحكم. عدّل الأرقام لتناسب متطلبات التخطيط الخاصة بك.

## الخطوة 5: تحديد الحجم والعنوان

زر بدون تسمية يكون مربكًا. استخدم `setWidth` و `setHeight` و `setCaption` لإعطائه مظهرًا مرئيًا.

```java
        // Define size and caption
        commandButton.setWidth(120 * 0.75);   // 90 pt width
        commandButton.setHeight(30 * 0.75);   // 22.5 pt height
        commandButton.setCaption("Click Me");
```

الحجم يُعبّر عنه أيضًا بوحدات النقاط، لذا نقوم بالتحويل من البكسل للحفاظ على التناسق.

## الخطوة 6: حفظ المستند – إكمال تدفق إنشاء مستند Word باستخدام Java

أخيرًا، احفظ الملف على القرص. يمكن أن يكون المسار مطلقًا أو نسبيًا إلى جذر المشروع.

```java
        // Save the document containing the CommandButton
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

تشغيل البرنامج ينتج ملف `CommandButtonDemo.docx` داخل مجلد `output`. فتح الملف في Microsoft Word يظهر زرًا قابلًا للنقر موضعه بالضبط حيث قمت بتحديده.

### النتيجة المتوقعة

* ملف `.docx` باسم **CommandButtonDemo.docx**.
* داخل المستند، يظهر **CommandButton** مع تسمية “Click Me” على بعد 100 px من الهامش الأيسر و150 px من الهامش العلوي.
* الزر يستجيب للنقرات عند فتح المستند في Word (سيعرض رسالة ActiveX افتراضية ما لم تقم بإرفاق كود VBA مخصص).

## الخطوة 7: الاختلافات الشائعة وحالات الحافة

### إضافة أزرار متعددة

إذا كنت بحاجة إلى **إضافة زر إلى Word** أكثر من مرة، كرّر الخطوات 3‑5 مع كائن `Forms2OleControl` جديد في كل مرة. تذكر تعديل قيمة `setTop` حتى لا تتداخل الأزرار.

```java
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
        secondButton.setLeft(200 * 0.75);
        secondButton.setTop(250 * 0.75);
        secondButton.setWidth(120 * 0.75);
        secondButton.setHeight(30 * 0.75);
        secondButton.setCaption("Second");
```

### العمل بدون رخصة

تضيف Aspose.Words علامة مائية عند الاستخدام بدون رخصة. للكود الإنتاجي، اشترِ رخصة وطبقها في بداية الدالة `main`:

```java
        License license = new License();
        license.setLicense("Aspose.Words.lic");
```

### التوافق مع إصدارات Office القديمة

تدعم تنسيقات `.doc` (Word 97‑2003) تحكمات ActiveX. لإنشاء ملف قديم، غيّر تنسيق الحفظ:

```java
        doc.save("CommandButtonDemo.doc", SaveFormat.DOC);
```

## الكود الكامل (قابل للتنفيذ)

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Optional: apply a license if you have one
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control (how to insert button)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);

        // Step 3: Position the button on the page (set button position)
        commandButton.setLeft(100 * 0.75);   // distance from the left edge (points)
        commandButton.setTop(150 * 0.75);    // distance from the top edge (points)

        // Step 4: Define the button's size and caption
        commandButton.setWidth(120 * 0.75);   // width in points
        commandButton.setHeight(30 * 0.75);   // height in points
        commandButton.setCaption("Click Me");

        // Step 5: Save the document containing the CommandButton (create word document java)
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

احفظ الملف باسم `src/main/java/CommandButtonDemo.java`، شغّل `mvn exec:java -Dexec.mainClass=CommandButtonDemo`، وافتح المستند المُنشأ لرؤية النتيجة.

## الأسئلة المتكررة

**س: هل يعمل هذا مع OpenJDK؟**  
ج: نعم. Aspose.Words هي جافا صافية وتعمل على أي تنفيذ JDK 8+، بما في ذلك OpenJDK.

**س: هل يمكنني تغيير خط الزر أو لونه؟**  
ج: مظهر زر ActiveX يتحكم فيه التطبيق المستضيف (Word). يمكنك إرفاق كود VBA لتعديل الخصائص أثناء التشغيل، لكن المظهر الثابت يقتصر على النمط الافتراضي.

**س: ماذا لو احتجت إلى وضع الزر داخل خلية جدول؟**  
ج: انقل مؤشر `DocumentBuilder` إلى الخلية قبل استدعاء `insertForms2OleControl`. سيتوارث التحكم تخطيط الخلية، ولا يزال بإمكانك استخدام `setLeft`/`setTop` لضبطه بدقة.

## الخلاصة

أنت الآن تعرف كيفية **ضبط موضع الزر** في مستند Word باستخدام Java، وكيفية **إدراج زر**، وكيفية **إضافة تحكم ActiveX**، وكيفية **إضافة زر إلى Word** مع اتباع أفضل الممارسات لمشاريع **إنشاء مستند Word باستخدام Java**. يوضح المثال الكامل سير العمل بالكامل—من إعداد المشروع إلى ملف `.docx` محفوظ يحتوي على زر CommandButton فعال.

### الخطوات التالية

* استكشف قيم `Forms2OleControl.ControlType` الأخرى (مثل `CHECKBOX`، `TEXTBOX`) لبناء نماذج أكثر غنى.
* دمج الزر مع ماكرو VBA لمعالجة النقرات المخصصة.
* استخدم ميزة الدمج البريدي في Aspose.Words لإنشاء مستندات مخصصة تحتوي مسبقًا على تحكمات تفاعلية.

برمجة سعيدة، واستمتع بأتمتة مستندات Word باستخدام Java!

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات التي تم توضيحها في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [كيفية إنشاء حقول نموذج وإضافة محتوى باستخدام DocumentBuilder في Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [إضافة حقل نموذج صندوق اختيار إلى مستند Word باستخدام Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [كيفية تحميل مستندات Word باستخدام Aspose.Words Java: دليل شامل](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}