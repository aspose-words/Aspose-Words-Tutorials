---
title: Определение формата документа в Aspose.Words для Java
linktitle: Определение формата документа
second_title: API обработки документов Java Aspose.Words
description: Узнайте, как определять форматы документов в Java с помощью Aspose.Words. Определите DOC, DOCX и другие. Эффективно организуйте файлы.
weight: 25
url: /ru/java/document-loading-and-saving/determining-document-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Определение формата документа в Aspose.Words для Java


## Введение в определение формата документа в Aspose.Words для Java

При работе с обработкой документов в Java крайне важно определить формат файлов, с которыми вы имеете дело. Aspose.Words для Java предоставляет мощные функции для определения форматов документов, и мы проведем вас через этот процесс.

## Предпосылки

Прежде чем начать, убедитесь, что у вас выполнены следующие предварительные условия:

- [Aspose.Words для Java](https://releases.aspose.com/words/java/)
- Java Development Kit (JDK), установленный в вашей системе
- Базовые знания программирования на Java

## Шаг 1: Настройка каталога

Во-первых, нам нужно настроить необходимые каталоги для эффективной организации наших файлов. Мы создадим каталоги для разных типов документов.

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

// Создайте каталоги, если они еще не существуют.
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

Мы создали каталоги для поддерживаемых, неизвестных, зашифрованных и до 97-го типов документов.

## Шаг 2: Определение формата документа

Теперь давайте определим формат документов в наших каталогах. Для этого мы воспользуемся Aspose.Words for Java.

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // Отображение типа документа
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // При необходимости добавьте случаи для других форматов документов.
    }

    // Обработка зашифрованных документов
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // Обработка других типов документов
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

В этом фрагменте кода мы перебираем файлы, определяем их форматы и организуем их в соответствующие каталоги.

## Полный исходный код для определения формата документа в Aspose.Words для Java

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        // Создайте каталоги, если они еще не существуют.
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
            // Отображение типа документа
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

## Заключение

Определение форматов документов в Aspose.Words для Java имеет важное значение для эффективной обработки документов. С помощью шагов, описанных в этом руководстве, вы сможете определять типы документов и обрабатывать их соответствующим образом в своих приложениях Java.

## Часто задаваемые вопросы

### Как установить Aspose.Words для Java?

 Вы можете загрузить Aspose.Words для Java с сайта[здесь](https://releases.aspose.com/words/java/)и следуйте предоставленным инструкциям по установке.

### Какие форматы документов поддерживаются?

Aspose.Words for Java поддерживает различные форматы документов, включая DOC, DOCX, RTF, HTML и др. Полный список можно найти в документации.

### Как обнаружить зашифрованные документы с помощью Aspose.Words для Java?

 Вы можете использовать`FileFormatUtil.detectFileFormat()` метод обнаружения зашифрованных документов, продемонстрированный в этом руководстве.

### Существуют ли какие-либо ограничения при работе со старыми форматами документов?

Более старые форматы документов, такие как MS Word 6 или Word 95, могут иметь ограничения в плане функций и совместимости с современными приложениями. Рассмотрите возможность обновления или преобразования этих документов при необходимости.

### Могу ли я автоматизировать определение формата документа в моем Java-приложении?

Да, вы можете автоматизировать определение формата документа, интегрировав предоставленный код в ваше приложение Java. Это позволяет обрабатывать документы на основе их обнаруженных форматов.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
