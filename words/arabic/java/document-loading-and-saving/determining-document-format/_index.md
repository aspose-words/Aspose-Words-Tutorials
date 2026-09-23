---
date: 2026-02-22
description: تعلم كيفية اكتشاف تنسيق المستند في جافا باستخدام Aspose.Words ونقل الملفات
  تلقائيًا حسب التنسيق. حدد DOC و DOCX والمزيد.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: اكتشاف تنسيق المستند في جافا باستخدام Aspose.Words for Java
url: /ar/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# اكتشاف تنسيق المستند java باستخدام Aspose.Words for Java

عند الحاجة إلى **detect document format java** في مجموعة من الملفات، فإن القدرة على فرزها تلقائيًا إلى المجلدات الصحيحة يمكن أن توفر ساعات من العمل اليدوي. في هذا البرنامج التعليمي سنوضح لك كيف تجعل Aspose.Words for Java من السهل تحديد Word و RTF و HTML و ODT والعديد من التنسيقات الأخرى، ثم **move files by format** إلى أدلة منظمة.

## إجابات سريعة
- **ما معنى “detect document format java”؟** هو عملية تحديد تنسيق ملف معالجة النصوص (DOC، DOCX، RTF، إلخ) برمجيًا باستخدام كود Java.  
- **أي مكتبة توفر هذه القدرة؟** تقدم Aspose.Words for Java واجهة برمجة التطبيقات `FileFormatUtil.detectFileFormat`.  
- **هل يمكن للأداة أيضًا التعامل مع الملفات المشفرة؟** نعم – علم `FileFormatInfo.isEncrypted()` يخبرك إذا كان المستند محميًا بكلمة مرور.  
- **هل أحتاج إلى ترخيص للاستخدام في الإنتاج؟** يتطلب نشر غير تجريبي ترخيص تجاري لـ Aspose.Words.  
- **هل من الممكن نقل الملفات تلقائيًا بعد الاكتشاف؟** بالتأكيد – اجمع نتيجة الاكتشاف مع `FileUtils.copyFile` لفرز الملفات إلى مجلدات مخصصة.

## ما هو detect document format java؟
`detect document format java` يشير إلى استخدام كود Java لفحص رأس الملف الثنائي وتحديد أي تنسيق معالجة نصوص ينتمي إليه (مثل DOC، DOCX، ODT). تقوم Aspose.Words بقراءة الملف دون تحميل المستند بالكامل، مما يجعل العملية سريعة وفعّالة من حيث الذاكرة.

## لماذا نقل الملفات حسب التنسيق؟
تنظيم المستندات حسب تنسيقها الأصلي يبسط المعالجة اللاحقة:

- **تحويلات الدفعات** تصبح سهلة عندما تكون جميع ملفات DOCX في مجلد واحد.  
- **الدعم القديم**: يمكنك عزل ملفات Word قبل إصدار 97 للمعالجة الخاصة.  
- **الأمان**: يمكن حجز المستندات المشفرة تلقائيًا.  

## المتطلبات المسبقة

قبل أن نبدأ، تأكد من وجود ما يلي:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/) (حمّل أحدث نسخة)  
- Java Development Kit (JDK) 8 أو أعلى مثبت  
- إلمام أساسي بـ Java I/O و streams  

## الخطوة 1: إعداد الأدلة لكل تنسيق

نقوم أولاً بإنشاء بنية مجلدات نظيفة حيث سيتم نقل الملفات المكتشفة. هذا يحافظ على سير العمل منظمًا ويسهل إضافة فئات تنسيقات جديدة لاحقًا.

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

// Create the directories if they do not already exist.
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

> **نصيحة احترافية:** استخدم مسارات مطلقة أو قم بتكوين الدليل الأساسي عبر ملف خصائص لتجنب ترميز المسارات صراحة في كود الإنتاج.

## الخطوة 2: اكتشاف تنسيق المستند ونقل الملفات

النواة في **detect document format java** تكمن في الحلقة أدناه. تقوم بمسح كل ملف، تحديد نوعه، ثم نسخه إلى المجلد المناسب.

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // Display the document type
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // Add cases for other document formats as needed
    }

    // Handle encrypted documents
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // Handle other document types
        switch (info.getLoadFormat()) {
            case LoadFormat.DOC_PRE_WORD_60:
                FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                break;
            case LoadFormat.UNKNOWN:
                FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                break;
            default:
                FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                break;
        }
    }
}
```

يمكن توسيع كتلة `switch` لتغطية كل تنسيق تهتم به. كل حالة تطبع رسالة ودية ثم تنقل الملف إلى المجلد المطابق.

## الكود الكامل لاكتشاف تنسيق المستند java

فيما يلي المثال الكامل الجاهز للتنفيذ الذي يجمع بين إعداد الأدلة ومنطق الاكتشاف. انسخه إلى فئة Java، عدّل مسار القاعدة، وشغّله على مجلد يحتوي على مستندات مختلطة.

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        // Create the directories if they do not already exist.
        if (supportedDir.exists() == false)
            supportedDir.mkdir();
        if (unknownDir.exists() == false)
            unknownDir.mkdir();
        if (encryptedDir.exists() == false)
            encryptedDir.mkdir();
        if (pre97Dir.exists() == false)
            pre97Dir.mkdir();
        Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
                .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
                .map(File::getPath)
                .collect(Collectors.toSet());
        for (String fileName : listFiles) {
            String nameOnly = Paths.get(fileName).getFileName().toString();
            System.out.println(nameOnly);
            FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);
            // Display the document type
            switch (info.getLoadFormat()) {
                case LoadFormat.DOC:
                    System.out.println("\tMicrosoft Word 97-2003 document.");
                    break;
                case LoadFormat.DOT:
                    System.out.println("\tMicrosoft Word 97-2003 template.");
                    break;
                case LoadFormat.DOCX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Document.");
                    break;
                case LoadFormat.DOCM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
                    break;
                case LoadFormat.DOTX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Template.");
                    break;
                case LoadFormat.DOTM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
                    break;
                case LoadFormat.FLAT_OPC:
                    System.out.println("\tFlat OPC document.");
                    break;
                case LoadFormat.RTF:
                    System.out.println("\tRTF format.");
                    break;
                case LoadFormat.WORD_ML:
                    System.out.println("\tMicrosoft Word 2003 WordprocessingML format.");
                    break;
                case LoadFormat.HTML:
                    System.out.println("\tHTML format.");
                    break;
                case LoadFormat.MHTML:
                    System.out.println("\tMHTML (Web archive) format.");
                    break;
                case LoadFormat.ODT:
                    System.out.println("\tOpenDocument Text.");
                    break;
                case LoadFormat.OTT:
                    System.out.println("\tOpenDocument Text Template.");
                    break;
                case LoadFormat.DOC_PRE_WORD_60:
                    System.out.println("\tMS Word 6 or Word 95 format.");
                    break;
                case LoadFormat.UNKNOWN:
                    System.out.println("\tUnknown format.");
                    break;
            }
            if (info.isEncrypted()) {
                System.out.println("\tAn encrypted document.");
                FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
            } else {
                switch (info.getLoadFormat()) {
                    case LoadFormat.DOC_PRE_WORD_60:
                        FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                        break;
                    case LoadFormat.UNKNOWN:
                        FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                        break;
                    default:
                        FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                        break;
                }
            }
        }

```

## المشكلات الشائعة واستكشاف الأخطاء

| المشكلة | سبب حدوثها | كيفية الإصلاح |
|-------|----------------|------------|
| **`FileFormatUtil.detectFileFormat` returns `UNKNOWN`** | الملف تالف أو يستخدم تنسيقًا غير Word. | تحقق من امتداد الملف، أو أضف إجراءً احتياطيًا لنقله إلى مجلد *Unknown* (موجود بالفعل في العينة). |
| **Encrypted files throw an exception** | تحاول الواجهة قراءة المحتوى قبل التحقق من التشفير. | استدعِ دائمًا `info.isEncrypted()` قبل أي عملية أخرى على المستند. |
| **Directory creation fails on Linux** | أذونات غير كافية أو مجلد أصل مفقود. | تأكد من أن عملية Java لديها صلاحية كتابة وأن مسار القاعدة موجود. |

## الأسئلة المتكررة

**س: كيف أقوم بتثبيت Aspose.Words for Java؟**  
ج: يمكنك تنزيل Aspose.Words for Java من [هنا](https://releases.aspose.com/words/java/) واتباع تعليمات التثبيت المتوفرة.

**س: ما هي تنسيقات المستندات التي تدعمها عملية الاكتشاف؟**  
ج: يمكن لـ Aspose.Words اكتشاف DOC، DOCX، DOT، DOTX، DOCM، DOTM، RTF، HTML، MHTML، ODT، OTT، FLAT_OPC، WORD_ML، والتنسيقات القديمة قبل 97، وغيرها.

**س: هل يمكن لهذا الكود التعامل مع المستندات المحمية بكلمة مرور؟**  
ج: نعم. علم `FileFormatInfo.isEncrypted()` يحدد الملفات المشفرة، مما يتيح لك نقلها إلى مجلد آمن دون فتحها.

**س: هل هناك تأثير على الأداء عند فحص مجلدات كبيرة؟**  
ج: يقرأ الاكتشاف فقط رأس الملف، لذا حتى آلاف الملفات تُعالج بسرعة. بالنسبة للدفعات الضخمة جدًا، فكر في استخدام تدفقات متوازية.

**س: كيف يمكنني توسيع السكريبت لتحويل التنسيقات غير المدعومة؟**  
ج: بعد الاكتشاف، يمكنك استدعاء `Document.save` بالتنسيق المطلوب لأي نوع مصدر مدعوم.

## الخلاصة

باستخدام **detect document format java** مع Aspose.Words، تحصل على طريقة موثوقة لفرز، عزل، أو تحويل الملفات المتعلقة بـ Word تلقائيًا. يوضح الكود النموذجي كيفية إنشاء هيكل مجلدات نظيف، تحديد تنسيق كل ملف، ونقله وفقًا لذلك—مما يوفر لك الوقت ويقلل الأخطاء اليدوية.

---

**آخر تحديث:** 2026-02-22  
**تم الاختبار مع:** Aspose.Words for Java 24.12 (latest)  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}