---
category: general
date: 2026-07-06
description: Создайте DocumentConfig на Java для отслеживания отсутствующих шрифтов
  с помощью Aspose.Words — полное пошаговое руководство для разработчиков.
draft: false
keywords:
- create documentconfig
- track missing fonts
language: ru
og_description: Создайте DocumentConfig на Java, чтобы отслеживать отсутствующие шрифты
  с помощью Aspose.Words. Узнайте полный рабочий процесс, от настройки до обработки
  предупреждений.
og_title: Создать DocumentConfig в Java – Отслеживание отсутствующих шрифтов
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Create DocumentConfig in Java to track missing fonts using Aspose.Words
    – a complete, step‑by‑step guide for developers.
  headline: Create DocumentConfig in Java – Track Missing Fonts with Aspose.Words
  type: TechArticle
- description: Create DocumentConfig in Java to track missing fonts using Aspose.Words
    – a complete, step‑by‑step guide for developers.
  name: Create DocumentConfig in Java – Track Missing Fonts with Aspose.Words
  steps:
  - name: Prerequisites
    text: '| Requirement | Reason | |-------------|--------| | Java 8 or newer | Aspose.Words
      for Java supports JDK 8+. | | Aspose.Words for Java library (latest version)
      | Provides `DocumentConfig`, `IWarningCallback`, etc. | | An IDE or build tool
      (IntelliJ, Eclipse, Maven/Gradle) | To compile and run the sa'
  - name: Maven
    text: '```xml <dependency> <groupId>com.aspose</groupId> <artifactId>aspose-words</artifactId>
      <version>23.12</version> <!-- use the latest version --> </dependency> ```'
  - name: Gradle (Kotlin DSL)
    text: '```kotlin implementation("com.aspose:aspose-words:23.12") ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Font Substitution
title: Создайте DocumentConfig в Java – Отслеживание отсутствующих шрифтов с Aspose.Words
url: /ru/java/licensing-and-configuration/create-documentconfig-in-java-track-missing-fonts-with-aspos/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание DocumentConfig в Java – Отслеживание отсутствующих шрифтов с Aspose.Words

**Create DocumentConfig in Java** для мониторинга предупреждений о замене шрифтов при загрузке Word‑документа. Когда вы открываете DOCX и замечаете странные символы, скорее всего оригинальный шрифт отсутствует на машине, и Aspose.Words тихо заменяет его. В этом руководстве мы покажем, как **отслеживать отсутствующие шрифты**, чтобы больше никогда не удивляться неожиданным глифам.

Мы пройдёмся по всему, что вам нужно: настройка Maven/Gradle, код, создающий `DocumentConfig`, пользовательский `IWarningCallback`, фильтрующий только предупреждения о замене шрифтов, и быстрый способ записать эти сообщения в журнал. К концу вы получите готовый пример, который выводит каждое предупреждение об отсутствующем шрифте в консоль (или в файл, если хотите).

---

## Что вы узнаете

- Почему `DocumentConfig` — правильное место для перехвата событий замены шрифтов.  
- Как **отслеживать отсутствующие шрифты**, не заполняя логи посторонними предупреждениями.  
- Полный, готовый к копированию Java‑пример, демонстрирующий технику.  
- Советы по расширению решения — например, запись предупреждений в базу данных или отправка email‑уведомлений.

### Предварительные требования

| Требование | Причина |
|------------|---------|
| Java 8 или новее | Aspose.Words for Java поддерживает JDK 8+. |
| Библиотека Aspose.Words for Java (последняя версия) | Предоставляет `DocumentConfig`, `IWarningCallback` и т.д. |
| IDE или система сборки (IntelliJ, Eclipse, Maven/Gradle) | Для компиляции и запуска примера. |
| DOCX‑файл, ссылающийся на шрифты, которых у вас нет | Чтобы увидеть предупреждение в действии. |

Если у вас уже есть проект, просто добавьте зависимость Aspose и всё готово.

---

## Шаг 1: Добавьте Aspose.Words в сборку

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- use the latest version -->
</dependency>
```

### Gradle (Kotlin DSL)

```kotlin
implementation("com.aspose:aspose-words:23.12")
```

> **Pro tip:** Бесплатная trial‑версия полностью подходит для тестирования, но не забудьте применить лицензию для продакшна, чтобы убрать водяной знак оценки.

---

## Шаг 2: Создайте DocumentConfig и зарегистрируйте обратный вызов предупреждений

Сердце решения находится в этом фрагменте. Мы **создаём DocumentConfig**, привязываем пользовательский `IWarningCallback` и указываем ему **отслеживать только отсутствующие шрифты**.

```java
import com.aspose.words.*;

public class FontSubstitutionDiagnostics {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a configuration object.
        DocumentConfig config = new DocumentConfig();

        // 2️⃣ Attach a warning callback that reacts only to font‑substitution warnings.
        config.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // 3️⃣ Filter for FONT_SUBSTITUTION type.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // 4️⃣ This is where we **track missing fonts**.
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // 5️⃣ Load the document using the configuration we just prepared.
        Document doc = new Document("YOUR_DIRECTORY/input.docx", config);

        // Optional: do something with the document, e.g., save as PDF.
        // doc.save("output.pdf");
    }
}
```

**Почему это работает:** Когда Aspose.Words разбирает документ, он генерирует объекты `WarningInfo` для любых несоответствий. Предоставив обратный вызов, вы перехватываете эти предупреждения *до* того, как они исчезнут в пустоту. Проверка `if` гарантирует, что мы **отслеживаем только отсутствующие шрифты**, игнорируя другие предупреждения, такие как устаревшие теги или неподдерживаемые функции.

---

## Шаг 3: Запустите пример и посмотрите вывод

Поместите DOCX, который ссылается на шрифт, которого у вас нет (например, “Comic Sans MS” на Linux). Выполните программу:

```bash
$ javac -cp "aspose-words-23.12.jar" FontSubstitutionDiagnostics.java
$ java -cp ".:aspose-words-23.12.jar" FontSubstitutionDiagnostics
```

Вы должны увидеть что‑то вроде:

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

Каждая строка соответствует отсутствующему шрифту, который Aspose автоматически заменил. Если отсутствующих шрифтов нет, программа молчит — именно то, что нужно для чистого лога.

---

## Шаг 4: Сохраните список отсутствующих шрифтов (по желанию)

Вывод в консоль удобен для демонстраций, но в реальном сервисе, скорее всего, данные будут сохраняться. Ниже показан быстрый способ записать предупреждения в текстовый файл.

```java
import java.io.FileWriter;
import java.io.IOException;

public class FontSubstitutionDiagnostics {

    private static final String LOG_PATH = "missing-fonts.log";

    public static void main(String[] args) throws Exception {
        DocumentConfig config = new DocumentConfig();

        config.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) throws IOException {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substituted: " + info.getDescription();
                    System.out.println(message);
                    try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                        fw.write(message + System.lineSeparator());
                    }
                }
            }
        });

        Document doc = new Document("YOUR_DIRECTORY/input.docx", config);
    }
}
```

Теперь каждое событие отсутствующего шрифта добавляет строку в `missing-fonts.log`. Позже вы можете проанализировать этот файл, подключить его к панели мониторинга или даже сгенерировать оповещение, если критический шрифт исчезнет с вашего сервера.

---

## Шаг 5: Распространённые ошибки и как их избежать

| Симптом | Возможная причина | Решение |
|---------|-------------------|---------|
| Предупреждения не появляются, хотя DOCX использует неизвестные шрифты | Обратный вызов не зарегистрирован или `setWarningCallback` вызван после загрузки документа | Убедитесь, что `config.setWarningCallback(...)` выполняется **до** создания экземпляра `Document`. |
| Приложение падает с `NullPointerException` | `info.getDescription()` возвращает `null` для некоторых редких типов предупреждений | Защититесь от null: `String desc = info.getDescription(); if (desc != null) …` |
| Слишком много нерелевантных предупреждений заполняют консоль | Фильтрация в обратном вызове только `FONT_SUBSTITUTION`? | Проверьте условие `if (info.getWarningType() == WarningType.FONT_SUBSTITUTION)`. |
| Замедление производительности при больших пакетах | Синхронная запись в файл для каждого предупреждения | Пакетная запись или использование `BufferedWriter` для снижения нагрузки на I/O. |

---

## Шаг 6: Расширение решения – от консоли к корпоративному уровню

- **Запись в базу данных:** Замените `FileWriter` на JDBC‑вставку; храните `documentName`, `missingFont` и `timestamp`.  
- **Email‑оповещения:** Подключите JavaMail; отправляйте сводку после обработки пакета документов.  
- **Собственная логика подстановки:** Вместо того чтобы позволять Aspose выбирать запасной шрифт, вы можете загрузить локальную коллекцию шрифтов через `FontSettings.setFontsFolder()` и повторно загрузить документ, если произошла подстановка.

Эти расширения сохраняют основную идею — **создать DocumentConfig** и **отслеживать отсутствующие шрифты** — и позволяют масштабировать решение под производственные нужды.

---

## Заключение

Теперь у вас есть надёжный, готовый к копированию шаблон для **создания DocumentConfig** в Java и использования его для **отслеживания отсутствующих шрифтов** с Aspose.Words. Подход лёгок, требует всего несколько строк кода и даёт полный контроль над обработкой предупреждений о замене шрифтов. Независимо от того, создаёте ли вы сервис конвертации документов, автоматический генератор отчётов или инструмент аудита соответствия, знание того, какие шрифты отсутствуют, может сэкономить часы отладки.

Следующие шаги? Попробуйте заменить вывод в консоль на структурированный JSON‑лог, или интегрировать обратный вызов в микросервис Spring Boot, обрабатывающий загрузки в реальном времени. А если столкнётесь с редкими случаями — например, пользовательским OpenType‑шрифтом, который Aspose не может разобрать — оставляйте комментарий ниже; разберём вместе.

Счастливого кодинга, и пусть ваши PDF‑файлы всегда отображаются с ожидаемыми шрифтами!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом гайде. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Using Fonts in Aspose.Words for Java](/words/english/java/using-document-elements/using-fonts/)
- [Customize Theme Colors & Fonts in Aspose.Words Java: A Comprehensive Guide](/words/english/java/formatting-styles/customize-theme-colors-fonts-aspose-words-java/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}