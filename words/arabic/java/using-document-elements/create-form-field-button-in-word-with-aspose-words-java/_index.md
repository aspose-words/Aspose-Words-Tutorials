---
category: general
date: 2026-10-13
description: إنشاء زر حقل نموذج في Word باستخدام Aspose.Words للغة Java. تعلم كيفية
  إدراج أزرار الأوامر في حقول نماذج Word وتعيين تسمية زر الأمر في بضع خطوات سهلة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create form field button
- insert command button word
- set command button caption
language: ar
lastmod: 2026-10-13
og_description: إنشاء زر حقل نموذج في Word باستخدام Aspose.Words للـ Java. يوضح هذا
  الدرس كيفية إدراج حقول زر الأوامر في Word وتعيين تسمية زر الأوامر بسرعة.
og_image_alt: Screenshot of a Word document containing an inserted command button
  form field created with Aspose.Words Java
og_title: إنشاء زر حقل نموذج في Word – دليل Aspose.Words Java
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create form field button in Word using Aspose.Words for Java. Learn
    how to insert command button word form fields and set command button caption in
    a few easy steps.
  headline: Create form field button in Word with Aspose.Words Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: إنشاء زر حقل نموذج في Word باستخدام Aspose.Words Java
url: /ar/java/using-document-elements/create-form-field-button-in-word-with-aspose-words-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# إنشاء زر حقل نموذج في Word باستخدام Aspose.Words Java

إذا كنت بحاجة إلى **create form field button** في مستند Word، فإن هذا الدليل يشرح لك العملية بالكامل باستخدام Aspose.Words for Java. سواءً كنت تبني قالب نموذج تعبئة أو تضيف عناصر تحكم تفاعلية إلى تقرير، ستتعلم كيفية **insert command button word** و **set command button caption** بأقل قدر من الشيفرة.

يغطي هذا البرنامج التعليمي كل شيء من إعداد Maven إلى مثال قابل للتنفيذ بالكامل، بحيث يمكنك نسخ‑اللصق الشيفرة، تشغيلها، ورؤية ملف `.docx` يحتوي على زر قابل للنقر جاهز لمزيد من التخصيص.

## المتطلبات المسبقة

- Java 17 (أو أحدث) مثبت ومُكوَّن على جهازك.
- Maven 3.6+ لإدارة التبعيات.
- بيئة تطوير متكاملة أو محرر نصوص من اختيارك (مثل IntelliJ IDEA، VS Code).
- ترخيص صالح لـ Aspose.Words for Java (الإصدار التجريبي المجاني يعمل للتقييم).

## الخطوة 1: إضافة Aspose.Words إلى مشروع Maven الخاص بك

أنشئ ملف `pom.xml` (أو حرّر الملف الموجود) وأدرج تبعية Aspose.Words:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.9</version> <!-- Use the latest version available -->
    </dependency>
</dependencies>
```

> **نصيحة احترافية:** احرص على تحديث رقم الإصدار. الإصدارات الجديدة تضيف دعمًا لأحدث ميزات Word وتحسن الأداء.

## الخطوة 2: تهيئة مستند فارغ و`DocumentBuilder`

توفر الفئة `DocumentBuilder` واجهة برمجة تطبيقات سلسة لتحرير مستند Word. في هذه الخطوة ننشئ `Document` فارغًا ونربط به مُنشئًا.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder lets us add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

إنشاء المستند هو الأساس لكائنات **create form field button** لاحقًا في البرنامج التعليمي.

## الخطوة 3: إدراج حقل نموذج زر أمر

تُظهر Aspose.Words الفئة `Forms2OleControl` للتحكم في نماذج OLE. لإدراج حقول نموذج **insert command button word**، استدعِ `insertForms2OleControl` مع قيمة التعداد `COMMANDBUTTON`.

```java
        // Insert a Command Button form field at the current cursor position
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

تُعيد الطريقة كائن `Forms2OleControl` يمكننا تكوينه قبل الحفظ.

## الخطوة 4: تحديد حجم وموقع الزر

يحتاج زر الأمر إلى أبعاد وموقع صريحين على الصفحة. اضبط العرض والارتفاع والإحداثيات لتناسب تخطيطك.

```java
        // Set the button's visual size (in points)
        commandButton.setWidth(120);   // 120 points ≈ 1.67 inches
        commandButton.setHeight(30);   // 30 points ≈ 0.42 inches

        // Position the button relative to the page margins
        commandButton.setLeft(50);   // 50 points from the left margin
        commandButton.setTop(100);   // 100 points from the top margin
```

ضبط هذه القيم بدقة يضمن ظهور الزر في المكان المحدد بالضبط في المستند النهائي.

## الخطوة 5: **set command button caption**

النص الظاهر على الزر يتحكم فيه طريقة `setCaption`. هنا نقوم بـ **set command button caption** لتوجيه المستخدم.

```java
        // Define the text that appears on the button
        commandButton.setCaption("Click Me");
```

يمكنك استبدال `"Click Me"` بأي تسمية تتناسب مع هدف النموذج، مثل `"Submit"` أو `"Approve"`.

## الخطوة 6: حفظ المستند

أخيرًا، احفظ المستند على القرص. الملف الناتج يحتوي على الزر التفاعلي ويمكن فتحه في Microsoft Word أو LibreOffice.

```java
        // Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

تشغيل البرنامج ينتج `CommandButtonDemo.docx`. فتحه في Word يظهر زرًا مُعنونًا **Click Me** موضعه 50 نقطة من اليسار و100 نقطة من أعلى الصفحة.

### النتيجة المتوقعة

- ملف `.docx` يُدعى `CommandButtonDemo.docx`.
- المستند يحتوي على صفحة واحدة مع حقل نموذج زر أمر.
- الزر يعرض التسمية التي قمت بتعيينها (مثال: **Click Me**).

## الاختلافات الشائعة وحالات الحافة

| الحالة | كيفية التكيف |
|-----------|--------------|
| **Multiple buttons** | استدعِ `insertForms2OleControl` بشكل متكرر، مع تعديل `setLeft`/`setTop` لكل زر جديد. |
| **Different caption per button** | استخدم `setCaption` مع سلسلة فريدة بعد كل إدراج. |
| **Button inside a table cell** | انقل المؤشر إلى الخلية المطلوبة باستخدام `builder.moveTo(cell.getFirstParagraph())` قبل إدراج التحكم. |
| **Legacy Word formats (.doc)** | احفظ باستخدام `doc.save("Demo.doc", SaveFormat.DOC);` – يتم الحفاظ على زر الأمر. |
| **Read‑only forms** | بعد الإدراج، عيّن `commandButton.setEnabled(false);` لمنع تفاعل المستخدم. |

## نصائح لتنفيذ قوي

- **Validate dimensions**: قد تتسبب العروض الكبيرة جدًا في تجاوز الزر لهامش الصفحة.
- **License enforcement**: بدون ترخيص صالح، تضيف Aspose.Words علامة مائية إلى المستند المُولد. طبّق الترخيص مبكرًا باستخدام `License license = new License(); license.setLicense("Aspose.Words.lic");`.
- **Testing**: افتح الملف المُولد في Word وفعّل **Design Mode** (Developer → Design Mode) لرؤية خصائص الزر.

## ملخص الكود المصدر الكامل

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a Command Button form field
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3: Define the button's size and position on the page
        commandButton.setWidth(120);
        commandButton.setHeight(30);
        commandButton.setLeft(50);
        commandButton.setTop(100);

        // Step 4: Set the text that appears on the button
        commandButton.setCaption("Click Me");

        // Step 5: Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

انسخ الشيفرة إلى ملف يُدعى `InsertCommandButtonDemo.java`، ثمّ قم بتجميعه باستخدام Maven (`mvn compile`)، وشغّله (`mvn exec:java -Dexec.mainClass=InsertCommandButtonDemo`). سيظهر المستند المُولد في مجلد جذر مشروعك.

## الخلاصة

أنت الآن تعرف كيفية **create form field button** في Word باستخدام Aspose.Words for Java، وكيفية **insert command button word**، وكيفية **set command button caption** برمجيًا. هذا المثال الشامل يمنحك أساسًا قويًا لبناء مستندات Word أكثر غنى وتفاعلية—سواءً كنت تحتاج إلى زر إرسال واحد أو مجموعة كاملة من عناصر التحكم في النماذج.

### ما التالي؟

- [كيفية إنشاء حقول نموذج وإضافة محتوى باستخدام DocumentBuilder في Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [إضافة حقل نموذج صندوق اختيار (Combo Box) إلى مستند Word باستخدام Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [إضافة حقل نموذج مربع اختيار (Check Box) إلى مستند Word باستخدام Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}