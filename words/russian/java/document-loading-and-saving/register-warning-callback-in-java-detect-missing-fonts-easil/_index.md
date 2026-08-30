---
category: general
date: 2026-07-03
description: Зарегистрировать обратный вызов предупреждения в Java для обнаружения
  отсутствующих шрифтов при обработке документов Word. Изучите обработку предупреждений
  Aspose.Words и обнаружение замены шрифтов.
draft: false
keywords:
- register warning callback
- detect missing fonts
- font substitution warning
- Aspose.Words warning callback
- Java missing font detection
- document font handling
language: ru
og_description: Зарегистрируйте обработчик предупреждений в Java для обнаружения отсутствующих
  шрифтов. Это руководство показывает, как перехватывать предупреждения о замене шрифтов
  с помощью Aspose.Words.
og_title: Регистрация обработчика предупреждений в Java – Обнаружение недостающих
  шрифтов
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Register warning callback in Java to detect missing fonts while processing
    Word docs. Learn Aspose.Words warning handling and font substitution detection.
  headline: Register warning callback in Java – Detect missing fonts easily
  type: TechArticle
- description: Register warning callback in Java to detect missing fonts while processing
    Word docs. Learn Aspose.Words warning handling and font substitution detection.
  name: Register warning callback in Java – Detect missing fonts easily
  steps:
  - name: Why this matters
    text: '* **Visibility:** Without a callback, the substitution happens silently,
      and you might ship a document with the wrong appearance. * **Automation:** In
      batch pipelines you can log every missing‑font incident and later feed the list
      to a font‑installation script. * **Compliance:** Some industries (e.g'
  - name: Expected console output
    text: 'Assuming `input.docx` references the font *“Comic Sans MS”* which isn’t
      installed, you’ll see something like:'
  - name: Multiple missing fonts
    text: If a document references several unavailable fonts, the callback will fire
      once per font. You can aggregate the messages into a list if you need a summary
      report later.
  - name: Controlling substitution behavior
    text: 'Sometimes you *do* want to force a particular fallback font. Use `FontSettings`
      before loading the document:'
  - name: Performance considerations
    text: 'Registering a warning callback introduces a tiny overhead—only a few nanoseconds
      per warning. In high‑throughput services (e.g., converting thousands of docs
      per hour) the impact is negligible. However, if you’re processing millions,
      consider disabling warnings after you’ve verified the font set is '
  - name: Cross‑platform notes
    text: The callback works identically on Windows, macOS, and Linux. The only difference
      is the set of fonts available on each OS. If you run the same job on multiple
      agents, you might see different substitution messages. To keep results deterministic,
      ship a **custom font folder** and point Aspose.Words to
  type: HowTo
tags:
- Aspose.Words
- Java
- Fonts
title: Регистрация обратного вызова предупреждения в Java — легко обнаружить недостающие
  шрифты
url: /ru/java/document-loading-and-saving/register-warning-callback-in-java-detect-missing-fonts-easil/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Зарегистрировать обратный вызов предупреждения в Java – Легко обнаруживать отсутствующие шрифты

Когда‑нибудь задумывались, как **зарегистрировать обратный вызов предупреждения**, чтобы **обнаруживать отсутствующие шрифты** при конвертации или редактировании документов Word? Вы не одиноки. Отсутствующие шрифты могут тихо испортить макеты, превратив аккуратный отчёт в неразборчивый беспорядок, и большинство разработчиков даже не замечают этого, пока финальный PDF не выглядит странно.  

В этом руководстве мы пройдём через полностью готовый к запуску пример, который покажет, как подключиться к системе предупреждений Aspose.Words for Java, перехватить назойливые оповещения о замене шрифтов и записать их в журнал или выполнить любые необходимые действия. Никаких расплывчатых «см. документацию»‑шорткатов — только чистый, готовый к копированию код и объяснение каждой строки.

## Требования

Прежде чем погрузиться в детали, убедитесь, что у вас есть:

* **Java 17** (или любой современный JDK) установлен и переменная `JAVA_HOME` настроена.  
* **Aspose.Words for Java** JAR (скачайте с официального сайта или подключите через Maven).  
* Пример файла `.docx`, в котором используется шрифт, **не установленный** на вашей машине — это вызовет предупреждение.  
* Ваш любимый IDE или простой текстовый редактор и инструменты сборки командной строки.

Вот и всё. Никаких дополнительных фреймворков, никаких внешних сервисов. Готовы? Поехали.

## Шаг 1: Настройте проект и добавьте Aspose.Words

Если вы используете Maven, добавьте следующую зависимость в ваш `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- use the latest stable version -->
</dependency>
```

Для Gradle поместите это в `build.gradle`:

```groovy
implementation 'com.aspose:aspose-words:24.10'
```

Если вы предпочитаете ручной способ, просто разместите `aspose-words-24.10.jar` в пути к классам.  
**Совет:** держите JAR рядом с папкой `src`; это упростит команду `javac` позже.

## Шаг 2: Загрузите документ, который может содержать отсутствующие шрифты

Первое, что нужно сделать — создать объект `Document`, указывающий на исходный файл. Этот шаг прост, но именно здесь библиотека сканирует файл и *возмож​но* обнаруживает отсутствующие шрифты.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {
        // Adjust the path to point at your test document
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – Aspose.Words will start parsing it now
        Document doc = new Document(inputPath);
```

Здесь `Document` — точка входа для всех операций Aspose.Words. Когда вызывается конструктор, библиотека разбирает XML документа, разрешает шрифты и, если какие‑то шрифты недоступны, *ставит в очередь* предупреждение, которое мы позже сможем перехватить.

## Шаг 3: Зарегистрировать обратный вызов предупреждения для перехвата оповещений о замене шрифтов

А теперь главная часть: **зарегистрировать обратный вызов предупреждения**. Aspose.Words позволяет подключить реализацию интерфейса `IWarningCallback`. Каждый раз, когда движок сталкивается с ситуацией, требующей внимания — например, отсутствующим шрифтом — он вызывает ваш метод `warning`.

```java
        // Register the warning callback
        doc.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We’re only interested in font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substituted: " + info.getDescription());
                }
            }
        });
```

### Почему это важно

* **Видимость:** Без обратного вызова замена происходит молча, и вы можете отправить документ с неправильным внешним видом.  
* **Автоматизация:** В пакетных конвейерах вы можете записывать каждый случай отсутствующего шрифта и позже передавать список в скрипт установки шрифтов.  
* **Соответствие требованиям:** В некоторых отраслях (например, юридической) требуется доказательство того, что использовались оригинальные шрифты или они были корректно заменены.

Обратите внимание, что мы фильтруем `WarningType.FONT_SUBSTITUTION`. Aspose.Words генерирует множество типов предупреждений — переполнение макета, устаревшие функции и т.д., но нам нужны только те, которые сообщают об отсутствии шрифта. Это сохраняет консоль чистой и сосредотачивает внимание на цели **обнаружения отсутствующих шрифтов**.

## Шаг 4: Сохраните документ и дайте обратному вызову сработать

Когда вы вызываете `save`, движок завершает любую отложенную загрузку и инициирует обратный вызов предупреждения для каждого отсутствующего шрифта, обнаруженного во время операции сохранения.

```java
        // Save the document – this is where the warning callback gets invoked
        String outputPath = "YOUR_DIRECTORY/output.docx";
        doc.save(outputPath);

        System.out.println("✅ Document saved to " + outputPath);
    }
}
```

### Ожидаемый вывод в консоль

Предположим, `input.docx` ссылается на шрифт *«Comic Sans MS»*, который не установлен. Вы увидите примерно следующее:

```
⚠️ Font substituted: Font 'Comic Sans MS' is not available. Substituted with 'Arial'.
✅ Document saved to YOUR_DIRECTORY/output.docx
```

Если в исходном документе уже используются только установленные шрифты, строка предупреждения просто не появится — то есть **обнаружение отсутствующих шрифтов** прошло без шума.

![Вывод консоли, показывающий работу обратного вызова предупреждения и обнаружение отсутствующих шрифтов](register-warning-callback-output.png)

*Текст альтернативного изображения: вывод обратного вызова предупреждения, показывающий обнаружение отсутствующих шрифтов*

## Шаг 5: Обработка граничных случаев и рекомендации по лучшим практикам

### Несколько отсутствующих шрифтов

Если документ ссылается на несколько недоступных шрифтов, обратный вызов сработает один раз для каждого шрифта. Вы можете собрать сообщения в список, если позже понадобится сводный отчёт.

```java
List<String> missingFonts = new ArrayList<>();
doc.setWarningCallback(info -> {
    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
        missingFonts.add(info.getDescription());
    }
});
// After saving
if (!missingFonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    missingFonts.forEach(System.out::println);
}
```

### Управление поведением замены

Иногда вы **хотите** принудительно задать конкретный запасной шрифт. Используйте `FontSettings` перед загрузкой документа:

```java
FontSettings settings = new FontSettings();
settings.setSubstitutionSettings(new FontSubstitutionSettings()
        .addSubstitutes("Comic Sans MS", "Times New Roman"));
doc.setFontSettings(settings);
```

Теперь обратный вызов всё равно сработает, но вы точно знаете, какой шрифт будет использован.

### Соображения по производительности

Регистрация обратного вызова предупреждения вносит крошечную нагрузку — всего несколько наносекунд на предупреждение. В высокопроизводительных сервисах (например, конвертация тысяч документов в час) влияние пренебрежимо. Однако при обработке миллионов документов стоит рассмотреть возможность отключения предупреждений после того, как вы убедились, что набор шрифтов полностью покрыт:

```java
doc.setWarningCallback(null); // turn off after initial scan
```

### Кроссплатформенные замечания

Обратный вызов работает одинаково в Windows, macOS и Linux. Единственное различие — набор доступных шрифтов в каждой ОС. Если вы запускаете одну и ту же задачу на разных агентах, сообщения о замене могут отличаться. Чтобы обеспечить детерминированные результаты, разместите **папку пользовательских шрифтов** и укажите её Aspose.Words через `FontSettings.setFontsFolder("path/to/fonts", true);`.

## Полный, готовый к запуску пример

Ниже представлен весь Java‑класс, который можно скопировать в `src/main/java/FontWarningDemo.java`. Он включает все импорты, обработку ошибок и комментарии, необходимые для мгновенного запуска.

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

/**
 * Demonstrates how to register a warning callback in Aspose.Words for Java
 * to detect missing fonts during document processing.
 */
public class FontWarningDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Paths – adjust to your environment
        String inputPath = "YOUR_DIRECTORY/input.docx";
        String outputPath = "YOUR_DIRECTORY/output.docx";

        // 2️⃣ Load the document (parsing begins here)
        Document doc = new Document(inputPath);

        // 3️⃣ Optional: set a custom font folder if you ship fonts with your app
        // FontSettings fs = new FontSettings();
        // fs.setFontsFolder("fonts", true);
        // doc.setFontSettings(fs);

        // 4️⃣ Register the warning callback to catch missing‑font warnings
        List<String> missingFonts = new ArrayList<>();
        doc.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // Log to console
                    System.out.println("⚠️ Font substituted: " + info.getDescription());
                    // Collect for later reporting
                    missingFonts.add(info.getDescription());
                }
            }
        });

        // 5️⃣ Save the document – triggers the callback
        doc.save(outputPath);
        System.out.println("✅ Document saved to " + outputPath);

        // 6️⃣ Post‑save reporting (if any fonts were missing)
        if (!missingFonts.isEmpty()) {
            System.out.println("\nSummary of missing fonts:");
            missingFonts.forEach(System.out::println);
        } else {
            System.out.println("\nNo missing fonts detected.");
        }
    }
}
```

Скомпилировать и запустить:

```bash
javac -cp "aspose-words-24.10.jar" FontWarningDemo.java
java -cp ".:aspose-words-24.10.jar" FontWarningDemo
```

Вы должны увидеть строки предупреждений (если они есть), а затем сообщение об успешном завершении.

## Заключение

Вы только что узнали, **как зарегистрировать обратный вызов предупреждения** в Java для **обнаружения отсутствующих шрифтов** при работе с Aspose.Words. Подключившись к системе предупреждений библиотеки, вы получаете полную видимость событий замены шрифтов, можете записывать их для соответствия требованиям и даже программно заменять шрифты при необходимости.  

Дальше вы можете исследовать:

* **Обнаружение отсутствующих шрифтов** в пакетной обработке файлов с помощью цикла или параллельных потоков.  
* Интеграцию обратного вызова с системой логирования (SLF4J, Log4j) для отчётов производственного уровня.  
* Использование `FontSettings` для принудительного применения корпоративной палитры шрифтов и избежания нежелательных подстановок.

Попробуйте — замените входной документ, поэкспериментируйте с разными сценариями отсутствующих шрифтов и посмотрите, как себя ведёт обратный вызов. Если возникнут вопросы, оставляйте комментарий ниже; happy coding!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом пособии. Каждый ресурс содержит полностью рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Warning Callback In Word Document](/words/english/net/programming-with-loadoptions/warning-callback/)
- [Aspose Words Java Callback Custom Savings](/words/hindi/java/images-shapes/aspose-words-java-callback-custom-savings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}