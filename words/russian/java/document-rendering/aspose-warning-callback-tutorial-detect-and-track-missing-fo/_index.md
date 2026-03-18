---
category: general
date: 2026-03-17
description: Изучите учебник по обработке предупреждений Aspose, чтобы обнаруживать
  отсутствующие шрифты и отслеживать их в Java‑документах, используя полный, готовый
  к запуску пример.
draft: false
keywords:
- aspose warning callback tutorial
- detect missing fonts
- track missing fonts
language: ru
og_description: Освойте руководство по обработке предупреждений Aspose, чтобы обнаруживать
  отсутствующие шрифты и отслеживать их в вашем Java‑рабочем процессе обработки Word‑документов.
og_title: Учебник по обратному вызову предупреждений Aspose – обнаружение отсутствующих
  шрифтов
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Учебник по обратному вызову предупреждений Aspose – обнаружение и отслеживание
  отсутствующих шрифтов
url: /ru/java/document-rendering/aspose-warning-callback-tutorial-detect-and-track-missing-fo/
---

Make sure to keep headings (# etc). Also keep blockquotes.

Proceed to translate.

Let's produce final answer.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# aspose warning callback tutorial – Detect and Track Missing Fonts

Когда‑нибудь задумывались, как **обнаружить отсутствующие шрифты** при конвертации или редактировании Word‑файлов с помощью Aspose.Words? Вы не одиноки. Во многих реальных проектах случайный шрифт может вызвать сбои в макете, и вам нужен надёжный способ **отслеживать отсутствующие шрифты**, пока они не принесли проблем.  

Хорошие новости? **aspose warning callback tutorial** предоставляет чистый программный хук, который выводит именно те предупреждения о замене шрифтов в момент их возникновения. В этом руководстве мы пройдёмся по настройке колбэка, загрузке документа и просмотру предупреждений в действии — всё на Java.

К концу статьи вы сможете автоматически выявлять отсутствующие шрифты, фиксировать их в журнале и решать, встраивать замену или корректировать исходные файлы. Никаких внешних инструментов не требуется.

## Prerequisites

- **Java 8+** (код компилируется любой современной JDK)
- **Aspose.Words for Java** версии 23.10 или новее — скачайте с портала Aspose или добавьте зависимость Maven.
- Пример DOCX, который намеренно ссылается на шрифт, которого у вас нет (например, “Comic Sans MS” на Linux‑машине).

И всё — никаких дополнительных библиотек, сложных шагов сборки.

## Step 1: Register a Warning Callback – The Core of the aspose warning callback tutorial

Первое, чему учит руководство, — как присоединить слушатель предупреждений. Aspose.Words генерирует объект `WarningInfo` для каждой найденной проблемы, а флаг `WarningSource.FONT_SUBSTITUTION` сообщает нам точно, когда происходит замена шрифта.

```java
import com.aspose.words.*;

public class FontDiagnostics {
    public static void main(String[] args) throws Exception {

        // Step 1: Register a warning callback to capture font substitution warnings.
        Document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about font‑substitution events.
                if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution warning:");
                    System.out.println("  Original:   " + info.getDescription());
                    System.out.println("  Substituted:" + info.getAdditionalInfo());
                }
            }
        });
```

**Почему это важно:** без колбэка Aspose молча заменяет отсутствующие шрифты, и вы никогда не узнаете, какие глифы могут выглядеть некорректно. Записывая предупреждение, вы можете **обнаружить отсутствующие шрифты** заранее и решить, встраивать правильный шрифт или нет.

> **Pro tip:** Если нужно собрать предупреждения для последующего отчёта, сохраняйте их в `List<WarningInfo>` вместо прямого вывода в консоль.

## Step 2: Load the Document – Where missing fonts might hide

Теперь загружаем DOCX, который может ссылаться на шрифты, отсутствующие в системе. Сам процесс загрузки вызывает колбэк предупреждений, если какие‑то шрифты недоступны.

```java
        // Step 2: Load a document that may contain missing fonts.
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

**Что происходит за кулисами?** Aspose разбирает определения стилей документа, сканирует каждый фрагмент текста и проверяет репозиторий шрифтов ОС. Когда точное совпадение не найдено, он переключается на замену и генерирует предупреждение, которое мы только что подключили.

## Step 3: Save the Document – Flushing the warnings

Наконец, сохраняем документ. Операция сохранения также переоценивает шрифты, поэтому любые предупреждения, не сгенерированные при загрузке, появятся сейчас.

```java
        // Step 3: Save the document; any font substitution warnings will be printed by the callback.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

При запуске программы вы увидите вывод в консоль, похожий на:

```
Font substitution warning:
  Original:   Font "Comic Sans MS" not found.
  Substituted: Using "Arial" as fallback.
```

Этот вывод подтверждает, что **aspose warning callback tutorial** работает, и вы успешно **обнаружили отсутствующие шрифты** и теперь **отслеживаете отсутствующие шрифты** через журнал.

## How to Detect Missing Fonts in a Word Document – Beyond the Basics

Подход с колбэком отлично подходит для одноразовых запусков, но иногда нужен переиспользуемый утилитный класс. Вот быстрый обёртка, которую можно добавить в любой проект:

```java
public class FontMissingChecker {
    private final List<String> missingFonts = new ArrayList<>();

    public FontMissingChecker() {
        Document.setWarningCallback((WarningInfo info) -> {
            if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                missingFonts.add(info.getDescription());
            }
        });
    }

    public List<String> check(String path) throws Exception {
        new Document(path); // triggers warnings
        return missingFonts;
    }
}
```

Вызов выглядит так:

```java
FontMissingChecker checker = new FontMissingChecker();
List<String> fonts = checker.check("input.docx");
if (!fonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    fonts.forEach(System.out::println);
}
```

Теперь у вас есть переиспользуемый метод **detect missing fonts**, который возвращает список, который можно передать в CI‑конвейер или UI.

## Tracking Missing Fonts with Aspose.Words – Reporting for Teams

В большой команде может потребоваться CSV‑отчёт обо всех отсутствующих шрифтах в множестве документов. Скомбинируйте предыдущую утилиту с простой итерацией по файлам:

```java
import java.nio.file.*;
import java.io.*;

public class BulkFontReporter {
    public static void main(String[] args) throws Exception {
        Path folder = Paths.get("YOUR_DIRECTORY");
        try (BufferedWriter writer = Files.newBufferedWriter(folder.resolve("missing-fonts-report.csv"))) {
            writer.write("Document,Missing Font\n");
            Files.list(folder)
                 .filter(p -> p.toString().endsWith(".docx"))
                 .forEach(p -> {
                     try {
                         FontMissingChecker checker = new FontMissingChecker();
                         List<String> missing = checker.check(p.toString());
                         for (String msg : missing) {
                             // Extract font name from description
                             String font = msg.replaceAll("Font \"(.*?)\".*", "$1");
                             writer.write(p.getFileName() + "," + font + "\n");
                         }
                     } catch (Exception e) {
                         // In a real app, log the error
                     }
                 });
        }
        System.out.println("Report generated at missing-fonts-report.csv");
    }
}
```

Запуск этого скрипта даст вам CSV‑файл **track missing fonts**, который каждый разработчик может быстро просмотреть перед тем, как отправить документ в продакшн.

## Common Pitfalls & How to Avoid Them

| Pitfall | Why it Happens | Fix |
|---------|----------------|-----|
| **Callback not firing** | Вы забыли установить колбэк **до** загрузки документа. | Поместите `Document.setWarningCallback` в самое начало `main`. |
| **Only first warning appears** | Aspose кэширует предупреждения на уровне экземпляра `Document`. | Используйте новый объект `Document` для каждого файла или сбрасывайте колбэк между запусками. |
| **Wrong font name in log** | Описание содержит лишний текст (“Font … not found”). | Удаляйте его с помощью regex, как показано в примере CSV. |
| **Performance hit on large batches** | Колбэк вызывается для каждого текстового фрагмента, что может быть дорого. | Ограничьте проверку предварительным шагом; пропустите сохранение, если нужна только детекция. |

## Expected Results & Verification

1. **Console output** — вы должны увидеть хотя бы одну строку “Font substitution warning” для каждого отсутствующего шрифта.  
2. **CSV report** — после завершения пакетного скрипта откройте `missing-fonts-report.csv` и убедитесь, что каждая строка содержит имя документа и точное название отсутствующего шрифта.  
3. **Saved document** — итоговый DOCX будет отображаться с заменёнными шрифтами, но визуальный макет может отличаться от оригинала.

Если какой‑либо из шагов не соответствует описанию, проверьте, что JAR‑файл Aspose.Words находится в classpath, и что `input.docx` действительно ссылается на шрифт, отсутствующий в вашей ОС.

## Conclusion

Вы только что завершили **aspose warning callback tutorial**, показывающее, как **обнаружить отсутствующие шрифты** и **отслеживать отсутствующие шрифты** в Java‑приложениях. Зарегистрировав слушатель предупреждений, загрузив документ и при необходимости экспортировав результаты, вы получаете полную видимость проблем, связанных со шрифтами, до их появления в продакшн.

Дальше вы можете изучить:

- Встраивание отсутствующего шрифта напрямую через `LoadOptions.setFontSubstitution`.
- Использование класса `FontSettings` для сопоставления недостающих шрифтов конкретным заменам.
- Интеграцию CSV‑отчёта в CI/CD‑конвейер для провала сборки при появлении незадокументированных шрифтов.

Попробуйте, настройте колбэки под ваш логгер и наблюдайте, как ваш документооборот становится гораздо надёжнее. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}