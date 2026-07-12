---
category: general
date: 2026-06-24
description: Как обрабатывать предупреждения при работе с Word‑файлами в Java. Узнайте,
  как захватывать шрифты, выводить сообщения о шрифтах и плавно обрабатывать отсутствующие
  шрифты.
draft: false
keywords:
- how to handle warnings
- how to capture fonts
- print font messages
- handle missing fonts
language: ru
og_description: как обрабатывать предупреждения в Aspose.Words для Java. Это руководство
  показывает, как захватывать шрифты, выводить сообщения о шрифтах и эффективно управлять
  отсутствующими шрифтами.
og_title: Как обрабатывать предупреждения в Aspose.Words – Полный учебник по Java
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: how to handle warnings when processing Word files in Java. Learn how
    to capture fonts, print font messages, and handle missing fonts smoothly.
  headline: how to handle warnings in Aspose.Words for Java – Full Guide
  type: TechArticle
- description: how to handle warnings when processing Word files in Java. Learn how
    to capture fonts, print font messages, and handle missing fonts smoothly.
  name: how to handle warnings in Aspose.Words for Java – Full Guide
  steps:
  - name: The document actually references a missing font.
    text: The document actually references a missing font.
  - name: The path to `input.docx` is correct.
    text: The path to `input.docx` is correct.
  - name: You’re using a recent version of Aspose.Words (older builds sometimes suppress
      certain warnings).
    text: You’re using a recent version of Aspose.Words (older builds sometimes suppress
      certain warnings).
  type: HowTo
tags:
- Aspose.Words
- Java
- Font Substitution
title: Как обрабатывать предупреждения в Aspose.Words for Java – полное руководство
url: /ru/java/document-rendering/how-to-handle-warnings-in-aspose-words-for-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# как обрабатывать предупреждения в Aspose.Words for Java – Полное руководство

Вы когда‑нибудь задавались вопросом **как обрабатывать предупреждения**, которые появляются при загрузке Word‑документа с помощью Aspose.Words? Возможно, вы видели загадочные сообщения о недостающих шрифтах и подумали: «Отлично, мой PDF смещён — что теперь делать?» Вы не одиноки. Во многих реальных проектах предупреждения о замене шрифтов являются тихими виновниками, портящими точность макета.

В этом руководстве мы пройдём практическое решение: зарегистрируем обратный вызов предупреждений, будем обнаруживать оповещения, связанные со шрифтами, и **выводить сообщения о шрифтах**, чтобы вы могли решить, встраивать ли запасной шрифт или поставлять пользовательский файл шрифта. К концу вы узнаете **как захватывать шрифты**, элегантно **обрабатывать недостающие шрифты** и поддерживать ваш конвейер конвертации документов надёжным.

## Что вы узнаете

- Назначение обратных вызовов предупреждений Aspose.Words.
- Как обнаруживать и фильтровать предупреждения *замены шрифтов*.
- Способы журналировать или отображать **сообщения о шрифтах** для отладки.
- Стратегии **обработки недостающих шрифтов** в производственных средах.
- Полный, готовый к запуску пример на Java, который можно добавить в любой проект Maven или Gradle.

### Предварительные требования

- Java 8 или новее (код также работает с JDK 11).
- Библиотека Aspose.Words for Java (скачайте с сайта Aspose или добавьте зависимость Maven/Gradle).
- Пример `input.docx`, который использует шрифт, не установленный локально (идеально для тестирования обратного вызова).

---

## Шаг 1: Настройте проект и импортируйте Aspose.Words

Прежде чем вы сможете **обрабатывать предупреждения**, вам нужен Java‑проект, знакомый с Aspose.Words. Если вы используете Maven, добавьте следующий фрагмент в ваш `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version> <!-- Use the latest stable version -->
</dependency>
```

Для Gradle эквивалент выглядит так:

```gradle
implementation 'com.aspose:aspose-words:23.10'
```

После того как зависимость будет разрешена, импортируйте необходимые классы в ваш Java‑файл:

```java
import com.aspose.words.*;
```

> **Совет:** Держите библиотеки Aspose в актуальном состоянии. Новые релизы часто улучшают обработку предупреждений и добавляют более подробные сведения в `WarningInfo`.

---

## Шаг 2: Загрузите Word‑документ и зарегистрируйте обратный вызов предупреждений

Теперь, когда библиотека находится в classpath, мы можем **захватывать шрифты**, которые движок заменяет. Ключевой метод — `Document.setWarningCallback`, который принимает любую реализацию `IWarningCallback`. Ниже приведён лаконичный, но полный пример, выводящий каждое предупреждение о замене шрифтов в консоль.

```java
public class FontWarningDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the Word document (replace with your actual path)
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Register the warning callback – this is where we **handle warnings**
        document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo warningInfo) {
                // Filter only font‑substitution warnings
                if (warningInfo.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // 3️⃣ **Print font messages** – you could also log to a file or monitoring system
                    System.out.println("Font substitution detected: " + warningInfo.getDescription());
                }
                // Optional: handle other warning types here
            }
        });

        // Trigger the warning processing by saving or converting the document
        // For demonstration, we’ll just save to PDF (you could save to any format)
        document.save("output.pdf");
    }
}
```

### Почему это работает

- **`Document.setWarningCallback`** сообщает Aspose.Words вызывать ваш код каждый раз, когда встречается ситуация, требующая предупреждения.
- **`WarningInfo.getWarningType()`** позволяет различать разные категории (например, `FONT_SUBSTITUTION`, `DEPRECATED_FEATURE`). Сфокусировавшись на `FONT_SUBSTITUTION`, мы **обрабатываем недостающие шрифты** без захламления журнала.
- Строка `System.out.println` **выводит сообщения о шрифтах** в реальном времени, что бесценно во время разработки или отладки производственного конвейера.

---

## Шаг 3: Протестируйте обратный вызов с недостающим шрифтом

Чтобы убедиться, что наш обратный вызов действительно **захватывает шрифты**, создайте Word‑файл, использующий шрифт, не установленный на вашей машине — например, “Comic Sans MS” на Linux‑сервере, где установлен только “DejaVu Sans”. При запуске демо вы должны увидеть вывод, похожий на:

```
Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Если сообщения не появляются, проверьте следующее:

1. Документ действительно ссылается на недостающий шрифт.
2. Путь к `input.docx` указан правильно.
3. Вы используете актуальную версию Aspose.Words (старые сборки иногда подавляют некоторые предупреждения).

---

## Шаг 4: Расширенная обработка — встраивание запасных шрифтов

Вывод предупреждения — это хорошо, но в производственной системе вы, возможно, захотите **автоматически обрабатывать недостающие шрифты**. Один из распространённых подходов — встраивание запасного шрифта (например, “Liberation Sans”) перед сохранением. Ниже показано, как расширить обратный вызов для программной замены недостающего шрифта:

```java
document.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo warningInfo) {
        if (warningInfo.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            String missingFont = warningInfo.getDescription()
                .replaceAll(".*'([^']+)'.*", "$1"); // extract the font name
            System.out.println("Missing font: " + missingFont);

            // Load a fallback font from resources or a known location
            FontSettings fontSettings = document.getFontSettings();
            fontSettings.setSubstitutionSettings(new FontSubstitutionSettings() {{
                getTableSubstitution().addSubstitutes(missingFont, new String[]{"Liberation Sans"});
            }});
        }
    }
});
```

**Что происходит?**

- Мы разбираем описание предупреждения, чтобы извлечь имя недостающего шрифта.
- С помощью `FontSettings` сообщаем Aspose.Words заменять *любое* вхождение этого шрифта на “Liberation Sans”.
- При следующем рендеринге или сохранении документа запасной шрифт применяется без вывода сообщений.

> **Внимание:** Чрезмерное использование автоматической замены может скрыть реальные проблемы дизайна. Лучше журналировать замену (как мы уже **выводим сообщения о шрифтах**) и вручную проверять результат во время контроля качества.

---

## Шаг 5: Журналирование вместо вывода — подготовка к продакшну

В CI/CD конвейере, скорее всего, вам не нужен вывод в консоль. Замените `System.out.println` на полноценный логгер (например, SLF4J). Вот быстрая адаптация:

```java
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

// ...

private static final Logger logger = LoggerFactory.getLogger(FontWarningDemo.class);

// Inside the callback:
logger.warn("Font substitution: {}", warningInfo.getDescription());
```

Теперь ваши предупреждения интегрируются с существующими инструментами агрегации логов (ELK, Splunk и др.), что упрощает **обработку недостающих шрифтов** в множестве задач.

---

## Шаг 6: Распространённые подводные камни и как их избежать

| Подводный камень | Почему происходит | Решение |
|------------------|-------------------|---------|
| Предупреждения не появляются | Шрифт действительно установлен в системе, либо документ использует встроенные шрифты. | Убедитесь, что тестовый документ действительно ссылается на недоступный шрифт. |
| Обратный вызов не вызывается | `setWarningCallback` вызван **после** загрузки документа. | Зарегистрируйте обратный вызов **до** любой операции, которая может вызвать предупреждения (например, до `Document.save`). |
| Множество предупреждений заполняют журнал | Большие документы вызывают множество замен. | Добавьте механизм ограничения частоты или агрегируйте сообщения перед журналированием. |
| Замена не применяется | `FontSettings` не привязан к экземпляру документа. | Убедитесь, что вы задаёте `FontSettings` тому же объекту `Document`, который сохраняете. |

---

## Шаг 7: Полный готовый к запуску пример

Ниже представлена полная программа, готовая к копированию. Она включает импорты, обратный вызов, журналирование и стратегию запасного шрифта.

```java
import com.aspose.words.*;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

public class FontWarningDemo {

    private static final Logger logger = LoggerFactory.getLogger(FontWarningDemo.class);

    public static void main(String[] args) throws Exception {
        // Load the document – adjust the path as needed
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Register warning callback to capture and log font substitution warnings
        document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo warningInfo) {
                if (warningInfo.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // Extract missing font name (optional, for advanced handling)
                    String missingFont = warningInfo.getDescription()
                        .replaceAll(".*'([^']+)'.*", "$1");

                    // Log the warning – this **prints font messages** in your log files
                    logger.warn("Font substitution detected: {}", warningInfo.getDescription());

                    // OPTIONAL: automatically substitute with a known fallback
                    FontSettings fontSettings = document.getFontSettings();
                    fontSettings.setSubstitutionSettings(new FontSubstitutionSettings() {{
                        getTableSubstitution().addSubstitutes(missingFont, new String[]{"Liberation Sans"});
                    }});
                }
            }
        });

        // Save to PDF (or any other format). This triggers the warning processing.
        document.save("output.pdf");
        logger.info("Document conversion completed. Check logs for any font substitution warnings.");
    }
}
```

**Ожидаемый вывод в консоль/лог** (при отсутствии “Comic Sans MS”):

```
WARN  FontWarningDemo - Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
INFO  FontWarningDemo - Document conversion completed. Check logs for any font substitution warnings.
```

Полученный `output.pdf` будет использовать “Liberation Sans” вместо “Comic Sans MS” везде, где тот был указан, благодаря добавленной автоматической замене.

---

## Заключение

Мы только что рассмотрели **как обрабатывать предупреждения** в Aspose.Words for Java от начала до конца. Регистрация обратного вызова предупреждений, фильтрация **предупреждений о замене шрифтов** и **вывод сообщений о шрифтах** дают полную видимость сценариев с недостающими шрифтами. Добавление запасного шрифта через `FontSettings` позволяет **обрабатывать недостающие шрифты** без ручного вмешательства, а правильный фреймворк журналирования делает решение готовым к продакшну.

Следующие шаги? Попробуйте сочетать этот подход с Aspose.PDF, чтобы проверить, сохраняются ли встроенные шрифты после конвертации, или изучите другие типы предупреждений (например, `DEPRECATED_FEATURE`), чтобы подготовить код к будущим изменениям. И если вам интересно **как захватывать шрифты** из удалённого хранилища…

## Что вам стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Захват предупреждений о замене шрифтов в Java с Aspose.Words – Полное руководство](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Как обнаружить шрифты в Aspose.Words – Обработка предупреждений и настроек](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Как захватить шрифты в Aspose.Words – Полное руководство](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}