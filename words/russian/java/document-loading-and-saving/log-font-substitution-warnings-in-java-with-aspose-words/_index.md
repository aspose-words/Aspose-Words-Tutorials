---
category: general
date: 2026-06-17
description: Ведите журнал предупреждений о замене шрифтов в Java с помощью Aspose.Words —
  фиксируйте отсутствующие шрифты при загрузке документа и сохраняйте согласованность
  вывода.
draft: false
keywords:
- log font substitution warnings
- Aspose.Words Java
- font substitution
- warning callback
- LoadOptions
- document loading
language: ru
og_description: Ведите журнал предупреждений о замене шрифтов в Java с Aspose.Words.
  Узнайте, как фиксировать оповещения об отсутствующих шрифтах при загрузке документа
  и сохранять ваши PDF в идеальном виде.
og_title: Логирование предупреждений о замене шрифтов в Java — Полное руководство
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  headline: Log Font Substitution Warnings in Java with Aspose.Words
  type: TechArticle
- description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  name: Log Font Substitution Warnings in Java with Aspose.Words
  steps:
  - name: Prerequisites
    text: '- Java 8 or newer (the code works with Java 11+ as well). - Aspose.Words
      for Java library (version 23.10 or later is recommended). - A sample `.docx`
      that references a font not installed on your machine (e.g., `MissingFont.docx`).'
  - name: Logging to a File Instead of the Console
    text: 'If you prefer a persistent log, replace the `System.out.println` call with
      a `FileWriter`:'
  - name: Capturing Multiple Documents in a Loop
    text: 'When processing a folder of documents, you can reuse the same callback:'
  - name: Dealing with Embedded Fonts
    text: 'Aspose.Words can embed missing fonts if you enable it:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Processing
title: Ведение журнала предупреждений о замене шрифтов в Java с Aspose.Words
url: /ru/java/document-loading-and-saving/log-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Логирование предупреждений о замене шрифтов в Java – Полное руководство

Вы когда‑нибудь задумывались, как **логировать предупреждения о замене шрифтов**, когда документ Word пытается использовать шрифт, которого нет на сервере? Вы не единственный, кто ломает голову над отсутствующими шрифтами, которые тихо заменяются. Хорошая новость? Aspose.Words for Java предоставляет простой способ отлавливать такие замены в момент загрузки документа.

В этом руководстве мы пройдем практический пример, который показывает, как зарегистрировать обратный вызов предупреждений, отфильтровать оповещения о замене шрифтов и записать их в консоль (или любой другой логгер по вашему выбору). К концу вы получите переиспользуемый фрагмент кода, который можно добавить в любой Java‑проект, использующий **Aspose.Words Java**.

## Что вы узнаете

- Как настроить **LoadOptions** для захвата предупреждений.  
- Как реализовать **IWarningCallback**, реагирующий только на события **font substitution**.  
- Как безопасно загрузить документ, сохранив чёткую историю отсутствующих шрифтов.  
- Советы по расширению решения для файловых логов или систем мониторинга.  

### Требования

- Java 8 или новее (код также работает с Java 11+).  
- Библиотека Aspose.Words for Java (рекомендуется версия 23.10 или новее).  
- Пример файла `.docx`, в котором используется шрифт, не установленный на вашей машине (например, `MissingFont.docx`).  

Никакие дополнительные фреймворки не требуются — только чистый Java и JAR‑файлы Aspose.

---

## Шаг 1: Настройка LoadOptions для Aspose.Words Java

Прежде чем перехватывать любые предупреждения, вам нужен экземпляр **LoadOptions**. Этот объект указывает Aspose.Words, как вести себя при разборе входного файла.

```java
// Step 1: Create LoadOptions to enable warning capture
LoadOptions loadOptions = new LoadOptions();
```

Почему этот шаг критически важен? Без объекта `LoadOptions` библиотека молча заменяет отсутствующие шрифты, и вы никогда не увидите следов. Создав его явно, вы открываете возможность использовать пользовательский **warning callback**, который может логировать именно то, что вам нужно.

> **Pro tip:** Если вы загружаете много документов пакетно, переиспользуйте один экземпляр `LoadOptions`, чтобы избежать лишних расходов на создание объектов.

---

## Шаг 2: Реализация обратного вызова предупреждений для замены шрифтов

Aspose.Words поставляется с интерфейсом `IWarningCallback`. Его реализация позволяет решить, что делать, когда движок генерирует `WarningInfo`. В нашем случае мы реагируем только на `WarningType.FONT_SUBSTITUTION`.

```java
// Step 2: Register a warning callback that logs only font‑substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Filter for font‑substitution warnings only
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Simple console output – replace with a logger if you prefer
            System.out.println("Font substitution: " + info.getMessage());
        }
    }
});
```

Несколько замечаний:

1. **Фильтрация** – условие `if` гарантирует, что мы игнорируем нерелевантные предупреждения (например, проблемы с разметкой) и сохраняем журнал чистым.  
2. **Потокобезопасность** – обратный вызов выполняется в том же потоке, где загружается документ, поэтому для простого вывода в консоль дополнительная синхронизация не нужна. Если вы пишете в общий логгер, убедитесь, что он потокобезопасен.  
3. **Расширяемость** – хотите писать в файл? Замените `System.out.println` на `java.util.logging.Logger` или любой сторонний фреймворк логирования.  

---

## Шаг 3: Загрузка документа с использованием настроенных параметров

Теперь, когда обратный вызов готов, загрузите ваш Word‑файл. В момент, когда Aspose.Words разбирает документ, любое отсутствие шрифта вызовет наш обратный вызов.

```java
// Step 3: Load the document with the warning‑aware LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Если исходный файл ссылается на шрифт, который не установлен, вы увидите вывод, похожий на:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Эта строка и есть **логирование предупреждений о замене шрифтов**, которое вы искали. Теперь вы можете реагировать — оповестить пользователя, переключиться на запасную таблицу стилей или просто зафиксировать факт для соответствия требованиям.

---

## Шаг 4: Продолжение обычной обработки

После загрузки документ ведёт себя как любой другой объект `Document`. Вы можете исследовать секции, извлекать текст или конвертировать в PDF. Логирование предупреждений происходит автоматически во время загрузки, поэтому дополнительный код не нужен.

```java
// Example: Print the number of sections – just to prove the doc is usable
System.out.println("Document has " + doc.getSections().getCount() + " sections.");
```

Консоль теперь покажет как предупреждение о замене шрифта (если оно есть), **так и** количество секций, подтверждая, что документ полностью функционален.

---

## Расширенные советы и особые случаи

### Запись в файл вместо консоли

Если вам нужен постоянный журнал, замените вызов `System.out.println` на `FileWriter`:

```java
private static final String LOG_PATH = "logs/font_substitutions.txt";

loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                fw.write("Font substitution: " + info.getMessage() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
});
```

Не забудьте корректно обрабатывать `IOException` в продакшн‑коде.

### Обработка нескольких документов в цикле

При обработке папки документов вы можете переиспользовать один и тот же обратный вызов:

```java
File[] files = new File("input").listFiles((dir, name) -> name.endsWith(".docx"));
for (File f : files) {
    Document d = new Document(f.getAbsolutePath(), loadOptions);
    // Additional processing...
}
```

Поскольку обратный вызов привязан к `loadOptions`, каждый проход цикла автоматически логирует любые события замены шрифтов.

### Работа с внедрёнными шрифтами

Aspose.Words может внедрять недостающие шрифты, если включить соответствующую опцию:

```java
loadOptions.setLoadFormat(LoadFormat.DOCX);
loadOptions.setEnableFontSubstitution(true); // default is true
```

Даже при включённом внедрении обратный вызов предупреждений всё равно срабатывает, предоставляя видимость того, что было заменено.

---

## Полный рабочий пример

Ниже представлен полностью готовый к запуску пример программы. Скопируйте его в класс `FontSubstitutionDiagnostics.java`, укажите путь к файлу и выполните.

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

/**
 * Demonstrates how to log font substitution warnings using Aspose.Words for Java.
 */
public class FontSubstitutionDiagnostics {

    // Optional: path to a persistent log file
    private static final String LOG_FILE = "font_substitution_log.txt";

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register a warning callback that logs only font‑substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substitution: " + info.getMessage();
                    // Log to console
                    System.out.println(message);
                    // Also append to a file (optional)
                    try (FileWriter fw = new FileWriter(LOG_FILE, true)) {
                        fw.write(message + System.lineSeparator());
                    } catch (IOException e) {
                        // In a real app, use a proper logging framework
                        e.printStackTrace();
                    }
                }
            }
        });

        // 3️⃣ Load the document with the configured LoadOptions
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 4️⃣ Continue normal processing – e.g., print section count
        System.out.println("Document has " + doc.getSections().getCount() + " sections.");
    }
}
```

**Ожидаемый вывод** (при условии, что в исходном документе используется отсутствующий шрифт):

```
Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
Document has 3 sections.
```

И консоль, и файл `font_substitution_log.txt` будут содержать предупреждение, обеспечивая надёжный аудит.

---

## Заключение

Мы только что показали, как **логировать предупреждения о замене шрифтов** в Java с помощью Aspose.Words. Настроив `LoadOptions`, подключив `IWarningCallback` и загрузив документ, вы получаете полную видимость всех событий отсутствующих шрифтов, которые иначе могли бы остаться незамеченными. Дальше вы можете:

- Перенаправлять предупреждения в центральный сервис логирования.  
- Выдавать оповещения для конвейеров контроля качества.  
- Комбинировать эту технику с другими стратегиями **document loading**, такими как конвертация в PDF или слияние писем.  

Не стесняйтесь экспериментировать — замените консольный логгер на SLF4J, добавьте метки времени или даже отправляйте оповещения в панель мониторинга. Основной шаблон остаётся тем же, и теперь у вас есть надёжная база для работы с шрифтами в любой Java‑ориентированной документо‑рабочей цепочке.

Есть свой вариант реализации? Может, вы интегрировали это в Spring Boot или облачную функцию. Оставьте комментарий ниже, и давайте продолжать обсуждение. Счастливого кодинга!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом пособии. Каждый ресурс содержит полностью рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Захват предупреждений о замене шрифтов в Java с Aspose.Words – Полное руководство](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Использование параметров и настроек документа в Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Включение предупреждений о замене шрифтов в Aspose.Words – Полное руководство](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}