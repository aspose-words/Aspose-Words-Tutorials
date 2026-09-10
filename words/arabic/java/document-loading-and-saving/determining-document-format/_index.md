---
date: 2025-12-20
description: تعلم كيفية تنظيم الملفات حسب النوع واكتشاف صيغ المستندات في Java باستخدام
  Aspose.Words. يدعم DOC و DOCX و RTF والمزيد.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: تنظيم الملفات حسب النوع باستخدام Aspose.Words للجافا
url: /ar/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تنظيم الملفات حسب النوع باستخدام Aspose.Words for Java

عند الحاجة إلى **تنظيم الملفات حسب النوع** في تطبيق Java، تكون الخطوة الأولى هي تحديد تنسيق كل مستند بدقة. تجعل Aspose.Words for Java ذلك بسيطًا، حيث تسمح لك باكتشاف DOC و DOCX و RTF و HTML و ODT والعديد من الصيغ الأخرى – حتى الملفات المشفرة أو غير المعروفة. في هذا الدليل سنستعرض إعداد المجلدات، اكتشاف صيغ الملفات، وترتيب ملفاتك تلقائيًا.

## إجابات سريعة
- **ما معنى “تنظيم الملفات حسب النوع”؟** يعني نقل المستندات تلقائيًا إلى مجلدات بناءً على تنسيقها المكتشف (مثل DOCX، PDF، RTF).  
- **أي مكتبة تساعد في اكتشاف تنسيق الملف في Java؟** توفر Aspose.Words for Java الدالة `FileFormatUtil.detectFileFormat()`.  
- **هل يمكن للـ API التعرف على أنواع الملفات غير المعروفة؟** نعم – تُعيد `LoadFormat.UNKNOWN` للملفات غير المدعومة أو غير القابلة للتعرف.  
- **هل يدعم اكتشاف المستندات المشفرة؟** بالتأكيد؛ علم `FileFormatInfo.isEncrypted()` يُظهر ما إذا كان الملف محميًا بكلمة مرور.  
- **هل أحتاج إلى ترخيص للاستخدام في الإنتاج؟** يلزم وجود ترخيص صالح لـ Aspose.Words للنشر التجاري.

## مقدمة: تنظيم الملفات حسب النوع باستخدام Aspose.Words for Java

عند العمل على معالجة المستندات في Java، من الضروري تحديد تنسيق الملفات التي تتعامل معها. توفر Aspose.Words for Java ميزات قوية لـ **detect file format java**، وسنرشدك خلال عملية تنظيم ملفاتك بكفاءة.

## المتطلبات المسبقة

قبل أن نبدأ، تأكد من توفر المتطلبات التالية:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/)
- Java Development Kit (JDK) مثبت على نظامك
- معرفة أساسية ببرمجة Java

## الخطوة 1: إعداد الدليل

أولاً، نحتاج إلى إعداد الأدلة اللازمة لتنظيم ملفاتنا بفعالية. سننشئ أدلة لأنواع المستندات المختلفة.

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

لقد أنشأنا أدلة للملفات المدعومة، غير المعروفة، المشفرة، والملفات من إصدارات ما قبل 97.

## الخطوة 2: اكتشاف تنسيق المستند

الآن، لنكتشف تنسيق المستندات في أدلتنا. سنستخدم Aspose.Words for Java لتحقيق ذلك.

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

في هذا المقتطف نقوم بالتكرار عبر الملفات، **detect file format java**، وننظمها في المجلدات المناسبة.

## شفرة المصدر الكاملة لتحديد تنسيق المستند في Aspose.Words for Java

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

## كيفية اكتشاف تنسيق الملف Java

تقوم الدالة `FileFormatUtil.detectFileFormat()` بفحص رأس الملف وتعيد كائنًا من نوع `FileFormatInfo`. هذا الكائن يخبرك بـ **load format**، ما إذا كان الملف مشفرًا، ومعلومات تعريفية أخرى مفيدة. باستخدام هذه المعلومات يمكنك برمجيًا **identify unknown file types** وتحديد كيفية معالجة كل ملف.

## التعرف على أنواع الملفات غير المعروفة

عندما تُعيد الـ API القيمة `LoadFormat.UNKNOWN`، يكون الملف إما تالفًا أو يستخدم صيغة لا تدعمها Aspose.Words. في مثالنا البرمجي ننقل تلك الملفات إلى مجلد **Unknown** لتتمكن من مراجعتها لاحقًا.

## المشكلات الشائعة والحلول

| المشكلة | السبب | الحل |
|-------|--------|-----|
| الملفات تُوضع دائمًا في مجلد *Supported* | `FileFormatUtil` لا يستطيع قراءة الرأس (مثلاً، الملف فارغ) | تأكد من تمرير مسار الملف الصحيح وأن الملف ليس بحجم صفر بايت. |
| استثناء عند معالجة الملفات المشفرة | محاولة القراءة دون التعامل مع التشفير | استخدم فحص `info.isEncrypted()` قبل أي معالجة أخرى، كما هو موضح في الشفرة. |
| عدم اكتشاف مستندات Word ما قبل 97 | الصيغ القديمة تحتاج حالة `DOC_PRE_WORD_60` | احتفظ بكتلة `case LoadFormat.DOC_PRE_WORD_60` لتوجيهها إلى مجلد *Pre97*. |

## الأسئلة المتكررة

### كيف أقوم بتثبيت Aspose.Words for Java؟

يمكنك تنزيل Aspose.Words for Java من [هنا](https://releases.aspose.com/words/java/) واتباع تعليمات التثبيت المتوفرة.

### ما هي صيغ المستندات المدعومة؟

تدعم Aspose.Words for Java صيغ مستندات متعددة، بما في ذلك DOC و DOCX و RTF و HTML و ODT وغيرها. راجع الوثائق الرسمية للحصول على القائمة الكاملة.

### كيف يمكنني اكتشاف المستندات المشفرة باستخدام Aspose.Words for Java؟

استخدم الدالة `FileFormatUtil.detectFileFormat()`؛ علم `FileFormatInfo.isEncrypted()` المُرجع يشير إلى التشفير، كما هو موضح في هذا الدليل.

### هل هناك أي قيود عند العمل مع صيغ المستندات القديمة؟

الصيغ القديمة مثل MS Word 6 أو Word 95 قد تفتقر إلى الميزات الحديثة وقد تواجه مشكلات توافق. يُنصح بتحويلها إلى صيغ أحدث عندما يكون ذلك ممكنًا.

### هل يمكنني أتمتة اكتشاف تنسيق المستند في تطبيق Java الخاص بي؟

نعم، يمكنك دمج الشفرة المقدمة في خط أنابيب معالجة تطبيقك. هذا يتيح الفرز التلقائي والتعامل بناءً على التنسيقات المكتشفة.

**آخر تحديث:** 2025-12-20  
**تم الاختبار مع:** Aspose.Words for Java 24.12 (latest)  
**المؤلف:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}