---
category: general
date: 2026-10-04
description: تعلم كيفية تهيئة DocumentBuilder لإنشاء مستند جديد وإضافة زر ActiveX
  باستخدام Aspose.Words في Java. دليل خطوة بخطوة مع الشيفرة الكاملة.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- initialize DocumentBuilder for new document
- insert ActiveX button
- Forms2OleControl command button
- Aspose.Words DocumentBuilder example
- create Word document with ActiveX
language: ar
lastmod: 2026-10-04
og_description: قم بتهيئة DocumentBuilder للمستند الجديد ودمج زر أمر ActiveX باستخدام
  Aspose.Words Java API. اتبع هذا الدرس المختصر.
og_image_alt: Screenshot showing DocumentBuilder initialized for a new document with
  an ActiveX button
og_title: تهيئة DocumentBuilder للمستند الجديد – دليل Aspose.Words الكامل
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to initialize DocumentBuilder for new document and add an
    ActiveX button with Aspose.Words in Java. Step‑by‑step guide with full code.
  headline: How to initialize DocumentBuilder for new document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- DocumentBuilder
- ActiveX
title: كيفية تهيئة DocumentBuilder لمستند جديد باستخدام Aspose.Words
url: /ar/java/using-document-elements/how-to-initialize-documentbuilder-for-new-document-using-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية تهيئة DocumentBuilder لإنشاء مستند جديد باستخدام Aspose.Words

إذا كنت بحاجة إلى **initialize DocumentBuilder for new document** في مشروع Java، فإن هذا الدليل يوضح لك الخطوات الدقيقة. ستتعرف على كيفية إنشاء ملف Word فارغ، وإرفاق زر أمر ActiveX، وحفظ النتيجة — كل ذلك بعينة كود واحدة متكاملة.

التعامل مع مستندات Word برمجياً غالبًا ما يعني التعامل مع تفاصيل منخفضة المستوى مثل عناصر التحكم في النماذج. بنهاية هذا الدليل ستتمكن من تضمين زر ActiveX دون مغادرة بيئة التطوير المتكاملة (IDE)، وهو ما يكون مفيدًا لإنشاء القوالب، التقارير الآلية، أو النماذج التفاعلية.

## المتطلبات المسبقة

قبل أن تبدأ، تأكد من وجود ما يلي:

* Java 17 أو أحدث مثبتة  
* Maven 3.8+ (أو Gradle إذا كنت تفضله)  
* ترخيص Aspose.Words for Java (الإصدار التجريبي المجاني يكفي للاختبار)  
* إلمام أساسي بصياغة Java  

إذا كنت جديدًا على Aspose.Words، فإن المكتبة توفر API عالي المستوى لإنشاء وتحرير وحفظ مستندات Word. تُعد فئة `DocumentBuilder` النقطة الأساسية لبناء محتوى المستند.

## الخطوة 1: إعداد مشروع Maven

أنشئ مشروع Maven جديد (أو أضف إلى مشروع موجود) وضمّن اعتماد Aspose.Words:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- Use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **نصيحة احترافية:** حافظ على تحديث نسخة المكتبة؛ الإصدارات الأحدث تضيف دعمًا لعناصر تحكم إضافية وتحسّن الأداء.

## الخطوة 2: تهيئة `DocumentBuilder` لإنشاء مستند جديد

جوهر الدليل هو عملية **initialize DocumentBuilder for new document**. أولاً تقوم بإنشاء كائن `Document` فارغ، ثم تمرره إلى مُنشئ `DocumentBuilder`.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new empty document
        Document doc = new Document();

        // Step 2.2: Initialize DocumentBuilder for new document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*لماذا هذا مهم:* ربط `DocumentBuilder` بكائن `Document` محدد يتيح لك إضافة فقرات، جداول، أو عناصر تحكم النماذج مباشرةً إلى ذلك المستند. بدون هذه الخطوة لن يكون لدى الـ builder هدف للعمل عليه.

## الخطوة 3: إدراج عنصر تحكم زر أمر ActiveX

تُظهر Aspose.Words فئة `Forms2OleControl` لتضمين عناصر تحكم ActiveX القديمة. يضيف الكود التالي **Forms2OleControl command button** إلى موضع المؤشر الحالي.

```java
        // Step 3.1: Insert an ActiveX command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3.2: Set the button caption (the text displayed on the button)
        commandButton.setCaption("Click Me");
```

### ما هو زر أمر ActiveX؟

زر أمر ActiveX هو عنصر واجهة مستخدم قديم يمكنه تشغيل ماكرو أو إطلاق أحداث عندما ينقر المستخدم عليه داخل مستند Word. رغم أن إصدارات Office الحديثة تفضّل عناصر التحكم بالمحتوى (Content Controls)، لا تزال العديد من القوالب المؤسسية تعتمد على ActiveX لضمان التوافقية العكسية.

## الخطوة 4: حفظ المستند

بعد إدراج عنصر التحكم، ما عليك سوى استدعاء `save`. سيحتوي الملف على زر ActiveX ويمكن فتحه في Microsoft Word.

```java
        // Step 4: Save the document containing the ActiveX button
        String outputPath = "output/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

عند فتح `ActiveXButton.docx` في Word، ستظهر لك زر مكتوب عليه **Click Me**. النقر على الزر لن يفعل شيئًا ما لم تُرفق ماكرو، لكن العنصر نفسه يعمل بالكامل.

## مثال كامل قابل للتنفيذ

فيما يلي البرنامج الكامل الذي يمكنك نسخه‑ولصقه في `src/main/java/com/example/ActiveXButtonDemo.java`. يتضمن جميع الاستيرادات ومعالجة الأخطاء اللازمة لاختبار سريع.

```java
package com.example;

import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder for new document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX command button control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMANDBUTTON);
            commandButton.setCaption("Click Me");

            // Step 4: Save the document
            String outputPath = "output/ActiveXButton.docx";
            doc.save(outputPath);
            System.out.println("Document saved to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error creating document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**الناتج المتوقع**

```
Document saved to output/ActiveXButton.docx
```

افتح الملف المُنشأ في Microsoft Word 2016 أو أحدث؛ يجب أن ترى زرًا مكتوبًا *Click Me* في أعلى الصفحة الأولى.

## الاختلافات الشائعة والحالات الخاصة

| السيناريو | التعديل |
|----------|------------|
| **إضافة الزر إلى فقرة محددة** | حرك مؤشر الـ builder باستخدام `builder.moveToParagraph(index, NodeType.PARAGRAPH);` قبل استدعاء `insertForms2OleControl`. |
| **تحديد حجم الزر** | استخدم `commandButton.setWidth(100);` و `commandButton.setHeight(30);` لتحديد الأبعاد بالنقاط. |
| **إرفاق ماكرو بالزر** | بعد حفظ المستند، افتحه في Word، فعّل تبويب المطور، وأرفق ماكرو VBA يدويًا (لا يمكن برمجة عناصر تحكم ActiveX مباشرةً من Aspose.Words). |
| **استهداف تنسيق .doc (ثنائي)** | غيّر `doc.save(outputPath, SaveFormat.DOC);` لإنتاج ملف Word 97‑2003 قديم. |
| **التشغيل على Android** | استخدم Aspose.Words for Android عبر API Java؛ يعمل نفس الكود طالما تم تضمين المكتبة في ملف APK. |

## نصائح استكشاف الأخطاء وإصلاحها

* **`java.lang.NoClassDefFoundError`** – تأكد من أن ملف JAR الخاص بـ Aspose.Words موجود في مسار الفئة (classpath). يضيف Maven الملف تلقائيًا؛ بالنسبة للبناء اليدوي، ضع الـ JAR في `libs/` وأضفه إلى مكتبات IDE.  
* **الزر لا يظهر في Word** – تحقق من تمكين خيار *Show legacy forms* في مركز الثقة بـ Word (`File → Options → Trust Center → Trust Center Settings → Macro Settings`).  
* **استثناء الترخيص** – إذا شغلت الكود بدون ترخيص صالح، سيضيف Aspose.Words علامة مائية. سجّل للحصول على نسخة تجريبية مجانية أو اشترِ ترخيصًا لإزالتها.

## الخلاصة

أنت الآن تعرف كيف **initialize DocumentBuilder for new document**، وتدرج زر أمر ActiveX، وتحفظ النتيجة باستخدام Aspose.Words for Java. يتيح لك هذا النمط إنشاء قوالب Word تفاعلية برمجيًا، وهو مفيد بشكل خاص للتقارير الآلية أو سير العمل القائم على النماذج.

من هنا يمكنك استكشاف عناصر تحكم إضافية (`Forms2OleControlType.CHECKBOX`, `COMBOBOX`, إلخ)، دمج الزر مع ماكرو VBA مخصص، أو إنشاء مستندات متكاملة تشمل جداول، صور، وتنسيقات—all باستخدام نفس سير عمل `DocumentBuilder`.

---

*هل ترغب في بناء أتمتة Word أكثر تعقيدًا؟ اطلع على أدلتنا حول **insert table with DocumentBuilder**, **apply styles programmatically**, و **export to PDF with Aspose.Words**.*

## ما الذي يجب أن تتعلمه بعد ذلك؟

الدروس التالية تغطي مواضيع ذات صلة وثيقة تبني على التقنيات الموضحة في هذا الدليل. كل مورد يتضمن أمثلة كود كاملة مع شروحات خطوة‑بخطوة لمساعدتك على إتقان ميزات API إضافية واستكشاف أساليب تنفيذ بديلة في مشاريعك.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Add a watermark to a document using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}