---
"description": "تعرّف على كيفية اكتشاف تنسيقات المستندات في جافا باستخدام Aspose.Words. حدّد صيغ DOC وDOCX وغيرها. نظّم ملفاتك بكفاءة."
"linktitle": "تحديد تنسيق المستند"
"second_title": "واجهة برمجة تطبيقات معالجة مستندات Java Aspose.Words"
"title": "تحديد تنسيق المستند في Aspose.Words لـ Java"
"url": "/ar/java/document-loading-and-saving/determining-document-format/"
"weight": 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# تحديد تنسيق المستند في Aspose.Words لـ Java


## مقدمة لتحديد تنسيق المستند في Aspose.Words لـ Java

عند العمل على معالجة المستندات في جافا، من الضروري تحديد تنسيق الملفات التي تتعامل معها. يوفر Aspose.Words for Java ميزات فعّالة لتحديد تنسيقات المستندات، وسنرشدك خلال العملية.

## المتطلبات الأساسية

قبل أن نبدأ، تأكد من أن لديك المتطلبات الأساسية التالية:

- [كلمات Aspose لجافا](https://releases.aspose.com/words/java/)
- مجموعة تطوير Java (JDK) مثبتة على نظامك
- المعرفة الأساسية ببرمجة جافا

## الخطوة 1: إعداد الدليل

أولاً، علينا إعداد الأدلة اللازمة لتنظيم ملفاتنا بفعالية. سننشئ أدلة لأنواع مختلفة من المستندات.

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

// قم بإنشاء الدلائل إذا لم تكن موجودة بالفعل.
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

لقد قمنا بإنشاء أدلة لأنواع المستندات المدعومة، وغير المعروفة، والمشفرة، وأنواع المستندات التي سبقت 97.

## الخطوة 2: اكتشاف تنسيق المستند

الآن، لنكتشف تنسيق المستندات في مجلداتنا. سنستخدم Aspose.Words لجافا لتحقيق ذلك.

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // عرض نوع المستند
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // أضف حالات لتنسيقات المستندات الأخرى حسب الحاجة
    }

    // التعامل مع المستندات المشفرة
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // التعامل مع أنواع المستندات الأخرى
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

في مقتطف التعليمات البرمجية هذا، نقوم بالتكرار خلال الملفات، واكتشاف تنسيقاتها، وتنظيمها في الدلائل الخاصة بها.

## الكود المصدري الكامل لتحديد تنسيق المستند في Aspose.Words لـ Java

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        // قم بإنشاء الدلائل إذا لم تكن موجودة بالفعل.
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
            // عرض نوع المستند
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

## خاتمة

يُعد تحديد تنسيقات المستندات في Aspose.Words لجافا أمرًا أساسيًا لمعالجة المستندات بكفاءة. باتباع الخطوات الموضحة في هذا الدليل، يمكنك تحديد أنواع المستندات ومعالجتها وفقًا لذلك في تطبيقات جافا.

## الأسئلة الشائعة

### كيف أقوم بتثبيت Aspose.Words لـ Java؟

يمكنك تنزيل Aspose.Words for Java من [هنا](https://releases.aspose.com/words/java/) واتبع تعليمات التثبيت المقدمة.

### ما هي تنسيقات المستندات المدعومة؟

يدعم Aspose.Words لجافا تنسيقات مستندات متنوعة، بما في ذلك DOC وDOCX وRTF وHTML وغيرها. يمكنك مراجعة الوثائق للاطلاع على القائمة الكاملة.

### كيف يمكنني اكتشاف المستندات المشفرة باستخدام Aspose.Words لـ Java؟

يمكنك استخدام `FileFormatUtil.detectFileFormat()` طريقة للكشف عن المستندات المشفرة، كما هو موضح في هذا الدليل.

### هل هناك أية قيود عند العمل مع تنسيقات المستندات القديمة؟

قد تكون تنسيقات المستندات القديمة، مثل MS Word 6 أو Word 95، محدودة من حيث الميزات والتوافق مع التطبيقات الحديثة. فكّر في ترقية أو تحويل هذه المستندات عند الحاجة.

### هل يمكنني أتمتة اكتشاف تنسيق المستند في تطبيق Java الخاص بي؟

نعم، يمكنك أتمتة اكتشاف تنسيقات المستندات بدمج الكود المُقدّم في تطبيق جافا. يتيح لك هذا معالجة المستندات بناءً على التنسيقات المُكتشفة.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}