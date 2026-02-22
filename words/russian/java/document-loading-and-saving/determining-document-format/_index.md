---
date: 2026-02-22
description: Узнайте, как определять формат документа в Java с помощью Aspose.Words
  и автоматически перемещать файлы по формату. Определяйте DOC, DOCX и другие.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Определить формат документа Java с помощью Aspose.Words for Java
url: /ru/java/document-loading-and-saving/determining-document-format/
weight: 25
---

 Updated:** 2026-02-22  
**Tested With:** Aspose.Words for Java 24.12 (latest)  
**Author:** Aspose  

Translate labels but keep dates.

Then closing shortcodes.

Now produce final content.

Be careful to keep markdown formatting exactly.

Let's craft translation.

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# определение формата документа java с помощью Aspose.Words for Java

Когда вам нужно **detect document format java** в пакете файлов, возможность автоматически сортировать их по правильным папкам может сэкономить часы ручной работы. В этом руководстве мы покажем, как Aspose.Words for Java упрощает идентификацию Word, RTF, HTML, ODT и многих других форматов, а затем **move files by format** в организованные каталоги.

## Быстрые ответы
- **Что означает “detect document format java”?** Это процесс программного определения формата обработки текста файла (DOC, DOCX, RTF и т.д.) с помощью кода на Java.  
- **Какая библиотека предоставляет эту возможность?** Aspose.Words for Java предлагает API `FileFormatUtil.detectFileFormat`.  
- **Может ли утилита работать с зашифрованными файлами?** Да — флаг `FileFormatInfo.isEncrypted()` сообщает, защищён ли документ паролем.  
- **Нужна ли лицензия для использования в продакшене?** Для коммерческих развертываний требуется платная лицензия Aspose.Words.  
- **Можно ли автоматически перемещать файлы после определения?** Конечно — объедините результат определения с `FileUtils.copyFile`, чтобы сортировать файлы в пользовательские папки.

## Что такое detect document format java?
`detect document format java` относится к использованию кода на Java для анализа бинарного заголовка файла и определения, к какому формату обработки текста он относится (например, DOC, DOCX, ODT). Aspose.Words читает файл без полного его загрузки, делая операцию быстрой и экономичной по памяти.

## Почему перемещать файлы по формату?
Организация документов по их нативному формату упрощает последующую обработку:

- **Batch conversions** становятся простыми, когда все файлы DOCX находятся в одной папке.  
- **Legacy support**: вы можете изолировать файлы Word до версии 97 для специальной обработки.  
- **Security**: зашифрованные документы могут автоматически помещаться в карантин.  

## Предварительные требования

Перед началом убедитесь, что у вас есть:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/) (скачайте последнюю версию)  
- Java Development Kit (JDK) 8 или выше, установленный  
- Базовые знания Java I/O и потоков  

## Шаг 1: Настройте каталоги для каждого формата

Сначала мы создаём чистую структуру папок, куда будут перемещаться определённые файлы. Это поддерживает порядок в рабочем процессе и упрощает добавление новых категорий форматов позже.

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

> **Pro tip:** Используйте абсолютные пути или настройте базовый каталог через файл свойств, чтобы избежать жёсткого кодирования путей в продакшн‑коде.

## Шаг 2: Определите формат документа и переместите файлы

Ядро **detect document format java** находится в цикле ниже. Он сканирует каждый файл, определяет его тип и копирует его в соответствующую папку.

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

Блок `switch` можно расширить, чтобы охватить все интересующие вас форматы. Каждый случай выводит дружелюбное сообщение и затем перемещает файл в соответствующую папку.

## Полный исходный код для определения формата документа java

Ниже представлен полностью готовый к запуску пример, объединяющий настройку каталогов и логику определения. Скопируйте его в класс Java, скорректируйте базовый путь и запустите против папки со смешанными документами.

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

## Распространённые проблемы и устранение неполадок

| Issue | Why it happens | How to fix |
|-------|----------------|------------|
| **`FileFormatUtil.detectFileFormat` returns `UNKNOWN`** | Файл повреждён или использует не‑Word формат. | Проверьте расширение файла или добавьте резервный вариант перемещения в папку *Unknown* (уже присутствует в примере). |
| **Encrypted files throw an exception** | API пытается прочитать содержимое до проверки шифрования. | Всегда вызывайте `info.isEncrypted()` перед любой другой операцией с документом. |
| **Directory creation fails on Linux** | Недостаточно прав или отсутствует родительская папка. | Убедитесь, что процесс Java имеет права записи и что базовый путь существует. |

## Часто задаваемые вопросы

**Q: Как установить Aspose.Words for Java?**  
A: Вы можете скачать Aspose.Words for Java по ссылке [here](https://releases.aspose.com/words/java/) и следовать предоставленным инструкциям по установке.

**Q: Какие форматы документов поддерживаются для определения?**  
A: Aspose.Words может определять DOC, DOCX, DOT, DOTX, DOCM, DOTM, RTF, HTML, MHTML, ODT, OTT, FLAT_OPC, WORD_ML и более старые форматы до версии 97, среди прочих.

**Q: Может ли этот код работать с документами, защищёнными паролем?**  
A: Да. Флаг `FileFormatInfo.isEncrypted()` определяет зашифрованные файлы, позволяя переместить их в безопасную папку без открытия.

**Q: Есть ли влияние на производительность при сканировании больших папок?**  
A: Определение читает только заголовок файла, поэтому даже тысячи файлов обрабатываются быстро. Для очень больших пакетов рассмотрите использование параллельных потоков.

**Q: Как расширить скрипт для конвертации неподдерживаемых форматов?**  
A: После определения вы можете вызвать `Document.save` с нужным форматом вывода для любого поддерживаемого исходного типа.

## Заключение

Используя **detect document format java** с Aspose.Words, вы получаете надёжный способ автоматически сортировать, помещать в карантин или конвертировать файлы, связанные с Word. Пример кода демонстрирует, как создать чистую иерархию папок, определить формат каждого файла и переместить его соответствующим образом — экономя ваше время и снижая количество ручных ошибок.

---

**Last Updated:** 2026-02-22  
**Tested With:** Aspose.Words for Java 24.12 (latest)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}