---
category: general
date: 2026-01-11
description: احفظ المستند كملف txt في بضع أسطر من الشيفرة فقط. تعلم كيفية تحويل docx
  إلى txt وتصدير المعادلات الرياضية بسهولة.
draft: false
keywords:
- save document as txt
- convert docx to txt
- how to convert docx
- how to export math
- how to save txt
language: ar
og_description: احفظ المستند كملف txt في بضع خطوات. يوضح هذا الدليل كيفية تحويل docx
  إلى txt وتصدير المحتوى الرياضي مع أمثلة شفرة واضحة.
og_title: حفظ المستند كملف TXT – دليل سريع لتصدير معادلات Word
tags:
- Aspose.Words
- Java
- Document Conversion
title: حفظ المستند كملف TXT – دليل سريع لتصدير معادلات Word
url: /ar/java/document-conversion-and-export/save-document-as-txt-quick-guide-to-exporting-word-math/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# حفظ المستند كملف TXT – دليل سريع لتصدير رياضيات Word

هل احتجت يومًا إلى **save document as txt** لكن لم تكن متأكدًا من كيفية الحفاظ على المعادلات الرياضية سليمة؟ لست وحدك. يواجه العديد من المطورين صعوبة عندما يحاولون تحويل ملف Word غني إلى نص عادي، خاصةً عندما يحتوي هذا الملف على Office Math.  

في هذا البرنامج التعليمي ستتعلم بالضبط **how to convert docx to txt** مع الحفاظ على محتوى الرياضيات (أو تسطيحه عمدًا). سنستعرض الشيفرة، نشرح لماذا كل إعداد مهم، وحتى نوضح لك كيفية التعامل مع الحالات الخاصة مثل المعادلات المخفية أو الخطوط المخصصة. في النهاية ستتمكن من إضافة طريقة واحدة إلى مشروعك وتصدير أي ملف `.docx` إلى ملف `.txt` نظيف.

## ما ستتعلمه

* الفرق بين تصدير النص العادي وتصدير الرياضيات المدركة.  
* كيفية تكوين `TxtSaveOptions` للتحكم في `OfficeMathExportMode`.  
* مثال كامل وقابل للتنفيذ بلغة Java يحفظ مستند Word كملف txt.  
* نصائح لاستكشاف الأخطاء الشائعة (رموز مفقودة، مشكلات الترميز، إلخ).  

**المتطلبات المسبقة** – تحتاج إلى مكتبة Aspose.Words for Java (أو الحزمة المكافئة لـ .NET) وبيئة تطوير Java أساسية. لا توجد أدوات خارجية أخرى مطلوبة.

---

## حفظ المستند كملف TXT – خطوة بخطوة

فيما يلي جوهر الحل. كل خطوة مفصولة في قسم خاص بها حتى يمكنك اختيار ما تحتاجه.

### الخطوة 1: تحميل المستند المصدر

أولًا نفتح ملف `.docx` الذي نريد تحويله. تتعامل فئة `Document` مع كل من صيغ `.docx` و `.doc` القديمة، لذا لا داعي للقلق بشأن التوافق.

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;

// Load the Word file from disk
LoadOptions loadOpts = new LoadOptions();
loadOpts.setLoadFormat(com.aspose.words.LoadFormat.DOCX); // optional, helps with auto‑detection
Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOpts);
```

*لماذا هذا مهم:* التحميل باستخدام خيارات صريحة يمكن أن يمنع الفشل الصامت عندما يحتوي الملف على محتوى معقد مثل كائنات OLE المدمجة. كما يضمن أن المكتبة تعرف أنك تتعامل مع DOCX حديث.

### الخطوة 2: تكوين خيارات حفظ TXT لتصدير الرياضيات

جوهر “how to export math” يكمن في تعداد `OfficeMathExportMode`. لديك ثلاث خيارات:

| الوضع | النتيجة |
|------|--------|
| **TXT** | يتم تحويل الرياضيات إلى تنسيق نص عادي خطي (مثال: `a+b=c`). |
| **IMAGE** | كل معادلة تصبح صورة PNG مدمجة في النص (نادرًا ما تكون مفيدة للنص الصافي). |
| **MATHML** | يصدر ترميز MathML – غير قابل للقراءة في عارض نص عادي. |

للحصول على تجربة **save document as txt** حقيقية عادةً ما نختار `TXT`.

```java
import com.aspose.words.TxtSaveOptions;
import com.aspose.words.OfficeMathExportMode;

// Create save options and set the math export mode
TxtSaveOptions txtOpts = new TxtSaveOptions();
txtOpts.setOfficeMathExportMode(OfficeMathExportMode.TXT);
```

*لماذا هذا مهم:* إذا تخطيت هذه الخطوة، فإن المكتبة تستخدم `OfficeMathExportMode.IMAGE` كإعداد افتراضي، مما يترك لك نواقل غير قابلة للقراءة مثل `[Image: Equation]`. ضبطها إلى `TXT` يقوم بتسطيح المعادلات إلى سلسلة خطية قابلة للبحث.

### الخطوة 3: حفظ المستند كملف TXT

الآن نكتب الناتج. طريقة `save` تأخذ مسار الهدف والخيارات التي قمنا بتكوينها للتو.

```java
import com.aspose.words.SaveFormat;

// Save as plain text
doc.save("YOUR_DIRECTORY/MathSample.txt", txtOpts);
System.out.println("Document successfully saved as txt!");
```

هذا كل شيء—ثلاث خطوات مختصرة، وستحصل على تمثيل نص عادي لملف Word الخاص بك، مع تعبيرات رياضية خطية.

### مثال كامل يعمل

بجمع كل ذلك معًا، إليك فئة جاهزة للتنفيذ. لا تتردد في نسخها ولصقها في بيئة التطوير المتكاملة الخاصة بك.

```java
import com.aspose.words.*;

public class DocxToTxtExporter {
    public static void main(String[] args) {
        try {
            // 1️⃣ Load the source DOCX
            LoadOptions loadOpts = new LoadOptions();
            loadOpts.setLoadFormat(LoadFormat.DOCX);
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOpts);

            // 2️⃣ Configure TXT options – this is how to export math as plain text
            TxtSaveOptions txtOpts = new TxtSaveOptions();
            txtOpts.setOfficeMathExportMode(OfficeMathExportMode.TXT);

            // 3️⃣ Save the file
            doc.save("YOUR_DIRECTORY/MathSample.txt", txtOpts);
            System.out.println("✅ Save document as txt completed successfully.");
        } catch (Exception e) {
            System.err.println("❌ An error occurred while converting the file:");
            e.printStackTrace();
        }
    }
}
```

**الناتج المتوقع** – بعد التشغيل، افتح `MathSample.txt` في أي محرر نصوص. يجب أن ترى شيئًا مثل:

```
This is a sample paragraph.
Equation: a + b = c
Another line of text.
```

لاحظ كيف تظهر المعادلة كتعبير خطي (`a + b = c`). هذا هو نتيجة **how to export math** باستخدام وضع `TXT`.

---

## كيفية تحويل DOCX إلى TXT – تنويعات شائعة

بينما يغطي الكود أعلاه السيناريو الأكثر شيوعًا، غالبًا ما تحتاج المشاريع الواقعية إلى معالجة إضافية. أدناه بعض حالات “ماذا لو” التي قد تواجهها.

### تحويل ملفات متعددة دفعة واحدة

إذا كان لديك مجلد مليء بمستندات Word، غلف منطق التحويل داخل حلقة:

```java
File folder = new File("YOUR_DIRECTORY");
for (File file : folder.listFiles((dir, name) -> name.endsWith(".docx"))) {
    Document d = new Document(file.getPath());
    TxtSaveOptions opts = new TxtSaveOptions();
    opts.setOfficeMathExportMode(OfficeMathExportMode.TXT);
    String outPath = file.getPath().replace(".docx", ".txt");
    d.save(outPath, opts);
}
```

**نصيحة احترافية:** استخدم `java.nio.file.Files` للحصول على معالجة أخطاء أفضل وأداء أعلى عند التعامل مع آلاف الملفات.

### معالجة مشكلات الترميز

الملفات النصية العادية تكون افتراضيًا UTF‑8 في Aspose.Words، لكن الأنظمة القديمة قد تتوقع ANSI أو ISO‑8859‑1. يمكنك فرض ترميز كالتالي:

```java
txtOpts.setEncoding(java.nio.charset.StandardCharsets.ISO_8859_1);
```

### الحفاظ على فواصل الأسطر

أحيانًا يدمج منطق فواصل الأسطر التلقائي الفقرات الطويلة. للحفاظ على فواصل الأسطر الأصلية في Word، فعّل:

```java
txtOpts.setPreserveTableLayout(true); // keeps tables as plain‑text grids
txtOpts.setExportHeadersFootersMode(TxtSaveOptions.ExportHeadersFootersMode.CUSTOM);
```

هذه العلامات الإضافية اختيارية، لكنها يمكن أن تُحدث فرقًا كبيرًا عند **how to convert docx** لمعالجة الأنابيب اللاحقة.

---

## الأسئلة المتكررة

**س: هل سيزيل التحويل الصور؟**  
**ج:** نعم. بما أننا نحفظ إلى نص عادي، تُحذف الصور عن قصد. إذا كنت تحتاجها، فكر في التصدير إلى HTML بدلاً من ذلك.

**س: ماذا لو كان مستندي يحتوي على MathML معقد؟**  
**ج:** وضع `TXT` سيقوم بتسطيحه إلى سلسلة خطية، مما قد يفقد بعض التفاصيل الهيكلية. للحصول على تمثيل كامل، استخدم `OfficeMathExportMode.MATHML` ثم عالج MathML باستخدام محول XSLT.

**س: هل يمكن تشغيل هذا على Android؟**  
**ج:** تدعم Aspose.Words for Android نفس الـ API، لذا يعمل الكود نفسه—فقط تذكر تضمين المكتبة مع ملف APK الخاص بك.

**س: كيف يمكنني تتبع فشل صامت حيث يكون ملف الإخراج فارغًا؟**  
**ج:** افحص وحدة التحكم للعثور على استثناءات، تحقق من أن ملف `.docx` المصدر يحتوي فعليًا على محتوى مرئي، وتأكد من أن مسار الإخراج قابل للكتابة. كما تأكد من أنك لا تقوم بالكتابة فوق الملف بطرفية صفرية في مكان آخر من الشيفرة.

---

## توضيح الصورة

فيما يلي مخطط توضيحي لسلسلة تحويل البيانات. يتضمن نص alt الكلمة المفتاحية الأساسية لتحسين محركات البحث.

![مخطط تدفق تحويل حفظ المستند كملف txt – يُظهر تحميل DOCX، ضبط خيارات TXT، وكتابة الملف TXT](/images/save-doc-as-txt-flow.png)

---

## الخلاصة

أنت الآن تعرف **how to save document as txt** باستخدام Aspose.Words، ورأيت عدة طرق لـ **convert docx to txt** مع التحكم في سلوك تصدير الرياضيات. النمط الأساسي—التحميل، تكوين `TxtSaveOptions`، الحفظ—يغطي 95 % من السيناريوهات الواقعية.  

إذا كنت مستعدًا للغوص أعمق، جرّب استبدال `OfficeMathExportMode.TXT` بـ `MATHML` ومرّر النتيجة إلى محلل MathML. أو جرب علامة `PreserveTableLayout` للحفاظ على قابلية قراءة البيانات الجدولية. في كلتا الحالتين، الأساس الذي بنيته سيفيدك في أي مهام معالجة مستندات مستقبلية.

### الخطوات التالية والمواضيع ذات الصلة

* **How to export math** بصيغ أخرى (HTML, PDF) – فقط غيّر `SaveFormat`.  
* **How to convert docx** عبر سطر الأوامر باستخدام Aspose.Words for Java CLI.  
* **How to save txt** مع صيغ نهاية سطر مخصصة لـ Windows مقابل Unix.  

لا تتردد في ترك تعليق إذا واجهت مشكلة، أو مشاركة نصائحك الخاصة للتعامل مع المعادلات الصعبة. برمجة سعيدة!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}