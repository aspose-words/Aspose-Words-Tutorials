---
category: general
date: 2026-10-20
description: Настройте кодировку LoadOptions в Java, чтобы правильно считывать документы,
  и измените кодировку документа на UTF-8 с помощью Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- configure LoadOptions encoding
- change document encoding to utf-8
- Aspose.Words Java encoding
- Java document conversion
- character set handling Java
language: ru
lastmod: 2026-10-20
og_description: Настройте кодировку LoadOptions в Java, чтобы обеспечить правильную
  обработку символов, и узнайте, как изменить кодировку документа на UTF‑8 с помощью
  Aspose.Words.
og_image_alt: Screenshot showing Java code that configures LoadOptions encoding and
  saves a document
og_title: Настройка кодировки LoadOptions в Java — полное руководство
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Configure LoadOptions encoding in Java to correctly read documents
    and change document encoding to UTF-8 with Aspose.Words.
  headline: How to configure LoadOptions encoding in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Encoding
title: Как настроить кодировку LoadOptions в Java
url: /ru/java/document-loading-and-saving/how-to-configure-loadoptions-encoding-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как настроить кодировку LoadOptions в Java

Если вам нужно **настроить кодировку LoadOptions** в Java, это руководство покажет, как задать правильный набор символов и затем **изменить кодировку документа на UTF-8** с помощью Aspose.Words. Правильная кодировка предотвращает искажение текста при загрузке файлов, использующих устаревшие кодовые страницы, такие как Big5, Shift_JIS или Windows‑1252.

Вы узнаете, как:

* создать экземпляр `LoadOptions` с конкретной кодировкой,
* загрузить исходный документ, использующий эту кодировку,
* сохранить документ в другой кодировке (UTF‑8) без потери данных,
* проверить, что конверсия прошла успешно.

В руководстве предполагается наличие базовой среды разработки Java и действующей лицензии Aspose.Words for Java. Внешние инструменты не требуются.

## Предварительные требования

| Требование | Почему это важно |
|------------|------------------|
| Java 17 или новее | Обеспечивает современные возможности языка и долгосрочную поддержку. |
| Aspose.Words for Java (v23.9 или новее) | Класс `LoadOptions` находится в этой библиотеке. |
| Исходный документ, закодированный устаревшей кодовой страницей (например, Big5) | Показывает необходимость пользовательской кодировки. |
| IDE или система сборки (Maven/Gradle) | Обеспечивает простоту компиляции и запуска примера. |

Добавьте зависимость Aspose.Words в ваш `pom.xml`, если используете Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Настройка кодировки LoadOptions

Первый шаг — указать Aspose.Words, какой набор символов ожидать при чтении файла. Это делается путем конфигурирования объекта `LoadOptions`.

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import java.nio.charset.Charset;

// Step 1: Create LoadOptions and set the desired encoding (Big5 in this example)
LoadOptions loadOptions = new LoadOptions();
loadOptions.setEncoding(Charset.forName("Big5"));
```

**Почему это важно:** Когда документ сохраняется с устаревшей кодировкой, загрузчик по умолчанию предполагает UTF‑8. Явно задав кодировку, вы избегаете mojibake (искажённых символов) и сохраняете оригинальный текст.

### Совет профессионала
Если вы не уверены, какую кодировку использует файл, можно проверить его маркер порядка байтов (BOM) или уточнить у поставщика документа. Распространённые устаревшие кодировки включают `Big5`, `Shift_JIS` и `Windows-1252`.

## Загрузка документа с настроенными параметрами

Теперь, когда `LoadOptions` готов, загрузите исходный файл. Конструктор, принимающий путь к файлу и экземпляр `LoadOptions`, гарантирует применение пользовательской кодировки.

```java
// Step 2: Load the document using the configured LoadOptions
String sourcePath = "C:/Docs/big5_doc.docx";
Document doc = new Document(sourcePath, loadOptions);
```

**Почему это важно:** Объект `Document` теперь содержит текст точно так, как он выглядит в оригинальном файле, потому что загрузчик учёл указанную кодовую страницу Big5.

## Изменение кодировки документа на UTF-8

Aspose.Words хранит текст внутренне в виде Unicode, поэтому процесс сохранения определяет внешнюю кодировку. Чтобы получить файл UTF‑8, просто сохраните без указания дополнительной кодировки — UTF‑8 является значением по умолчанию для современных форматов Office Open XML. При желании можно задать её явно для ясности.

```java
// Step 3: Save the document using UTF-8 encoding (default for .docx)
String outputPath = "C:/Docs/Converted.docx";
doc.save(outputPath);
```

Если требуется получить простое текстовое представление (например, `.txt`) в UTF‑8, передайте объект `SaveOptions`:

```java
import com.aspose.words.TxtSaveOptions;

// Save as UTF-8 encoded plain text
TxtSaveOptions txtOptions = new TxtSaveOptions();
txtOptions.setEncoding(Charset.forName("UTF-8"));
doc.save("C:/Docs/Converted.txt", txtOptions);
```

**Почему это важно:** Сохранение в UTF‑8 гарантирует, что любые последующие системы — веб‑службы, базы данных или современные редакторы — смогут прочитать файл без дополнительных шагов преобразования.

## Проверка конверсии

Быстрый способ убедиться, что изменение кодировки прошло успешно, — прочитать сохранённый файл обратно с помощью UTF‑8‑ридера и вывести несколько символов.

```java
import java.nio.file.Files;
import java.nio.file.Paths;

byte[] utf8Bytes = Files.readAllBytes(Paths.get(outputPath));
String content = new String(utf8Bytes, Charset.forName("UTF-8"));
System.out.println("First 200 characters of the converted file:");
System.out.println(content.substring(0, Math.min(200, content.length())));
```

Если вывод содержит читаемые символы (без знаков �), конверсия выполнена как ожидалось.

## Полный исполняемый пример

Ниже приведена автономная программа, объединяющая все шаги. Замените пути к файлам на свои собственные.

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import com.aspose.words.TxtSaveOptions;
import java.nio.charset.Charset;
import java.nio.file.Files;
import java.nio.file.Paths;

public class EncodingDemo {
    public static void main(String[] args) throws Exception {
        // 1. Configure LoadOptions with the source encoding (Big5)
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setEncoding(Charset.forName("Big5"));

        // 2. Load the legacy‑encoded document
        String sourcePath = "C:/Docs/big5_doc.docx";
        Document doc = new Document(sourcePath, loadOptions);

        // 3. Save as UTF‑8 encoded .docx (default) and .txt for verification
        String docxOutput = "C:/Docs/Converted.docx";
        doc.save(docxOutput); // UTF‑8 by default

        String txtOutput = "C:/Docs/Converted.txt";
        TxtSaveOptions txtOptions = new TxtSaveOptions();
        txtOptions.setEncoding(Charset.forName("UTF-8"));
        doc.save(txtOutput, txtOptions);

        // 4. Verify the .txt file content
        byte[] utf8Bytes = Files.readAllBytes(Paths.get(txtOutput));
        String content = new String(utf8Bytes, Charset.forName("UTF-8"));
        System.out.println("First 200 characters of the UTF‑8 text file:");
        System.out.println(content.substring(0, Math.min(200, content.length())));
    }
}
```

**Ожидаемый вывод**

```
First 200 characters of the UTF-8 text file:
[Readable Chinese characters from the original Big5 document...]
```

Если символы отображаются корректно, вы успешно **настроили кодировку LoadOptions** и **изменили кодировку документа на UTF-8**.

## Распространённые ошибки и как их избежать

| Симптом | Причина | Решение |
|---------|---------|---------|
| Искажённые символы после загрузки | `LoadOptions` не установлен или указано неверное имя кодировки | Убедитесь, что `loadOptions.setEncoding(Charset.forName("Big5"))` соответствует кодовой странице исходного файла. |
| `UnsupportedEncodingException` | Опечатка в имени кодировки | Используйте точное имя, указанное в `Charset.availableCharsets()`. |
| Файл вывода всё ещё содержит искажения | Сохранён в устаревшем формате (например, `.rtf`) без параметров UTF‑8 | Используйте `TxtSaveOptions` с `setEncoding("UTF-8")` или сохраняйте как `.docx`. |
| Снижение производительности на больших файлах | Создание нового `LoadOptions` для каждого документа | Переиспользуйте один экземпляр `LoadOptions` при обработке множества файлов с одинаковой исходной кодировкой. |

## Заключение

Теперь вы знаете, как **настроить кодировку LoadOptions** в Java для чтения документов с устаревшей кодировкой и как **изменить кодировку документа на UTF-8** для безопасного дальнейшего использования. Этот подход работает с любой кодовой страницей, поддерживаемой классом `Charset` в Java, что делает его гибким решением для многоязычных приложений.

Далее вы можете изучить:

* **Пакетную конверсию** — цикл по папке документов и применение той же логики кодировки.
* **Определение кодировки** — используйте библиотеки, такие как juniversalchardet, для автоматического определения исходной кодировки перед настройкой `LoadOptions`.
* **Сохранение форматирования** — поэкспериментируйте с сохранением в PDF или HTML, сохраняя совместимость с UTF‑8.

Не стесняйтесь адаптировать код под архитектуру вашего проекта, а надёжный API Aspose.Words позаботится о тяжёлой работе по манипуляции документами.

![Настройка кодировки LoadOptions и сохранение документа](/images/encoding-demo.png){: .align-center alt="Настройка кодировки LoadOptions в примере кода Java"}

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Как установить LoadOptions в Aspose.Words для Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Как конвертировать RTF‑текст с кодировкой UTF-8 в Java с помощью Aspose.Words](/words/english/java/document-operations/load-rtf-with-utf8-java-asposewords/)
- [Восстановление повреждённого DOCX‑документа Word с использованием Aspose.Words LoadOptions – Руководство для Java](/words/english/java/document-loading-and-saving/recover-corrupted-word-document-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}