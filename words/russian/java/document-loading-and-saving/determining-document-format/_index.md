---
date: 2025-12-20
description: Узнайте, как организовать файлы по типу и определять форматы документов
  в Java с помощью Aspose.Words. Поддерживает DOC, DOCX, RTF и другие.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Организуйте файлы по типу с помощью Aspose.Words для Java
url: /ru/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Организация файлов по типу с помощью Aspose.Words для Java

Когда вам необходимо **организовать файлы по типу** в Java‑приложении, первым шагом является надёжное определение формата каждого документа. Aspose.Words для Java делает это простым, позволяя обнаруживать DOC, DOCX, RTF, HTML, ODT и многие другие форматы — даже зашифрованные или неизвестные файлы. В этом руководстве мы пройдёмся по настройке папок, определению форматов файлов и автоматической сортировке ваших файлов.

## Быстрые ответы
- **Что означает “организовать файлы по типу”?** Это означает автоматическое перемещение документов в папки на основе их обнаруженного формата (например, DOCX, PDF, RTF).  
- **Какая библиотека помогает определять формат файла в Java?** Aspose.Words для Java предоставляет `FileFormatUtil.detectFileFormat()`.  
- **Может ли API определять неизвестные типы файлов?** Да — он возвращает `LoadFormat.UNKNOWN` для неподдерживаемых или нераспознаваемых файлов.  
- **Поддерживается ли определение зашифрованных документов?** Абсолютно; флаг `FileFormatInfo.isEncrypted()` указывает, защищён ли файл паролем.  
- **Нужна ли лицензия для использования в продакшене?** Для коммерческих развертываний требуется действующая лицензия Aspose.Words.

## Введение: Организация файлов по типу с Aspose.Words для Java

При работе с обработкой документов в Java важно определить формат обрабатываемых файлов. Aspose.Words для Java предоставляет мощные возможности для **detect file format java**, и мы проведём вас через процесс эффективной организации ваших файлов.

## Предварительные требования

Прежде чем начать, убедитесь, что у вас есть следующие требования:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/)
- Java Development Kit (JDK), установленный в вашей системе
- Базовые знания программирования на Java

## Шаг 1: Настройка каталогов

Сначала нам нужно создать необходимые каталоги для эффективной организации наших файлов. Мы создадим каталоги для разных типов документов.

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

Мы создали каталоги для поддерживаемых, неизвестных, зашифрованных и документов до версии 97.

## Шаг 2: Определение формата документа

Теперь определим формат документов в наших каталогах. Мы будем использовать Aspose.Words для Java для этого.

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

В этом фрагменте кода мы перебираем файлы, **detect file format java**, и размещаем их в соответствующих папках.

## Полный исходный код для определения формата документа в Aspose.Words для Java

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

## Как определить формат файла Java

Метод `FileFormatUtil.detectFileFormat()` проверяет заголовок файла и возвращает объект `FileFormatInfo`. Этот объект сообщает вам **load format**, зашифрован ли файл, а также другую полезную метаинформацию. Используя эти данные, вы можете программно **identify unknown file types** и решить, как обрабатывать каждый из них.

## Идентификация неизвестных типов файлов

Когда API возвращает `LoadFormat.UNKNOWN`, файл либо повреждён, либо использует формат, который Aspose.Words не поддерживает. В нашем примере кода мы перемещаем такие файлы в папку **Unknown**, чтобы вы могли позже их проверить.

## Распространённые проблемы и решения

| Проблема | Причина | Решение |
|----------|---------|---------|
| Файлы всегда помещаются в папку *Supported* | `FileFormatUtil` не смог прочитать заголовок (например, файл пустой) | Убедитесь, что вы передаёте правильный путь к файлу и что файл не пустой (не имеет нулевого размера). |
| Зашифрованные файлы вызывают исключение | Попытка чтения без обработки шифрования | Используйте проверку `info.isEncrypted()` перед любой дальнейшей обработкой, как показано в коде. |
| Документы Word до версии 97 не обнаруживаются | Для старых форматов нужен случай `DOC_PRE_WORD_60` | Оставьте блок `case LoadFormat.DOC_PRE_WORD_60`, чтобы направлять их в папку *Pre97*. |

## Часто задаваемые вопросы

### Как установить Aspose.Words для Java?

Вы можете скачать Aspose.Words для Java по ссылке [here](https://releases.aspose.com/words/java/) и следовать предоставленным инструкциям по установке.

### Какие форматы документов поддерживаются?

Aspose.Words для Java поддерживает различные форматы документов, включая DOC, DOCX, RTF, HTML, ODT и другие. Обратитесь к официальной документации для полного списка.

### Как определить зашифрованные документы с помощью Aspose.Words для Java?

Используйте метод `FileFormatUtil.detectFileFormat()`; возвращаемый флаг `FileFormatInfo.isEncrypted()` указывает на наличие шифрования, как продемонстрировано в этом руководстве.

### Есть ли ограничения при работе со старыми форматами документов?

Старые форматы, такие как MS Word 6 или Word 95, могут не иметь современных функций и могут иметь проблемы совместимости. По возможности рассматривайте их конвертацию в более новые форматы.

### Могу ли я автоматизировать определение формата документа в моём Java‑приложении?

Да, внедрите предоставленный код в конвейер обработки вашего приложения. Это позволит автоматически сортировать и обрабатывать файлы на основе обнаруженных форматов.

---

**Последнее обновление:** 2025-12-20  
**Тестировано с:** Aspose.Words for Java 24.12 (latest)  
**Автор:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}