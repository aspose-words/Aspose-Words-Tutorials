---
category: general
date: 2026-06-05
description: Обнаружение отсутствующей замены шрифтов в Java с использованием Aspose.Words.
  Узнайте, как настроить LoadOptions, FontSettings и обратные вызовы предупреждений
  для надёжной обработки документов.
draft: false
keywords:
- detect missing font substitution
- Java Aspose.Words
- LoadOptions configuration
- FontSettings warning callback
- document loading Java
language: ru
og_description: Обнаружить замену отсутствующего шрифта в Java с Aspose.Words. Это
  руководство пошагово показывает, как настроить LoadOptions, FontSettings и обратный
  вызов предупреждений для отслеживания отсутствующих шрифтов.
og_title: Обнаружение отсутствующей замены шрифтов в Java – Полный учебник по Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: detect missing font substitution in Java using Aspose.Words. Learn
    how to configure LoadOptions, FontSettings, and warning callbacks for reliable
    document processing.
  headline: detect missing font substitution in Java – Complete Aspose.Words Guide
  type: TechArticle
- description: detect missing font substitution in Java using Aspose.Words. Learn
    how to configure LoadOptions, FontSettings, and warning callbacks for reliable
    document processing.
  name: detect missing font substitution in Java – Complete Aspose.Words Guide
  steps:
  - name: 4.1 Quick verification
    text: Run the program from your IDE or via `java -cp .;aspose-words-23.12.jar
      MissingFontDetector`. If the document references a font you don’t have, you’ll
      see the warning message printed. If the console stays silent, either the font
      exists on your machine or the document doesn’t request any missing font
  - name: 4.2 Logging instead of `System.out`
    text: 'In production code you probably want a logger:'
  - name: 4.3 Handling other warning types
    text: 'The callback receives *all* warnings, not just font issues. If you’d like
      to keep an eye on other problems (e.g., `UNKNOWN_STYLE`), add extra `if` branches.
      Here’s a quick example:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Font handling
title: Обнаружение отсутствующей подстановки шрифтов в Java – Полное руководство по
  Aspose.Words
url: /ru/java/document-loading-and-saving/detect-missing-font-substitution-in-java-complete-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# обнаружение отсутствующей подстановки шрифтов в Java – Полное руководство Aspose.Words

Когда‑нибудь задумывались, как **detect missing font substitution** при загрузке Word‑документа в Java? Вы не одиноки. Отсутствующие шрифты могут незаметно испортить ваши PDF‑файлы или отрисованные страницы, а их раннее обнаружение экономит часы отладки. В этом руководстве мы пройдем практическое решение, которое не только загружает документ, но и точно сообщает, когда происходит подстановка шрифта.

Мы рассмотрим всё: от создания `LoadOptions` до подключения `WarningCallback`, который выводит понятное сообщение каждый раз, когда Aspose.Words заменяет недостающий шрифт. К концу вы получите переиспользуемый фрагмент кода, работающий с любым файлом `.docx`, и поймёте *почему* каждый элемент важен. Никаких дополнительных библиотек, только чистый Java и Aspose.Words.

## Что вы узнаете

- Как настроить **LoadOptions** для использования пользовательских **FontSettings**.  
- Как реализовать **IWarningCallback**, который перехватывает предупреждения `FONT_SUBSTITUTION`.  
- Как загрузить документ, одновременно отслеживая отсутствие шрифтов.  
- Ожидаемый вывод в консоль и как адаптировать код под системы логирования.  

**Prerequisites**: установленный Java 8+, Aspose.Words for Java (v23.12 или новее) в classpath и пример `.docx`, в котором используется шрифт, отсутствующий в системе. Всё, что нужно — без дополнительных инструментов сборки.

---

## Step 1: Set Up the Project and Add Aspose.Words

Прежде чем погрузиться в код, убедитесь, что Aspose.Words доступен. Если вы используете Maven, добавьте следующую зависимость в ваш `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

Если предпочитаете Gradle, эквивалент выглядит так:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

После того как библиотека окажется в classpath, вы готовы к **detect missing font substitution** одним вызовом метода.

---

## Step 2: Create LoadOptions and Attach FontSettings

Суть решения заключается в подготовке экземпляра `LoadOptions`, который умеет отслеживать проблемы со шрифтами. Ниже код, разбитый построчно.

```java
import com.aspose.words.*;

public class MissingFontDetector {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Prepare load options – this object controls how the document is read.
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Create FontSettings – it holds font‑related configuration.
        FontSettings fontSettings = new FontSettings();

        // 3️⃣ Register a warning callback that will be invoked on font substitution.
        fontSettings.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about FONT_SUBSTITUTION warnings.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substitution detected: " + info.getMessage());
                }
            }
        });

        // 4️⃣ Attach the FontSettings to the LoadOptions.
        loadOptions.setFontSettings(fontSettings);
```

**Why this matters**: `LoadOptions` сообщает Aspose.Words *how* интерпретировать входной файл. Подключив настроенный `FontSettings`, мы даём загрузчику хук (`IWarningCallback`), который срабатывает **exactly when a missing font is substituted**. Без этого обратного вызова Aspose.Words будет тихо заменять шрифт, и вы об этом никогда не узнаете.

---

## Step 3: Load the Document with the Configured Options

Теперь, когда система предупреждений настроена, загрузка документа становится простой.

```java
        // 5️⃣ Load the document using the prepared options.
        // Replace the path with the location of your test file.
        String docPath = "YOUR_DIRECTORY/docWithMissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Optional: do something with the document (e.g., save as PDF).
        // doc.save("output.pdf");
    }
}
```

Когда вызывается `new Document(...)`, Aspose.Words читает файл, проверяет каждую ссылку на шрифт и, если не может найти подходящий шрифт в системе, вызывает метод `warning`, определённый ранее. Консоль сразу покажет строку вроде:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Эта строка — вывод **detect missing font substitution**, который вы искали.

---

## Step 4: Verify the Result and Tweak the Callback (Advanced)

### 4.1 Quick verification

Запустите программу из IDE или через `java -cp .;aspose-words-23.12.jar MissingFontDetector`. Если документ ссылается на шрифт, которого у вас нет, вы увидите напечатанное сообщение‑предупреждение. Если консоль молчит, значит шрифт присутствует в системе или документ не запрашивает отсутствующие шрифты.

### 4.2 Logging instead of `System.out`

В продакшн‑коде, скорее всего, понадобится логгер:

```java
import java.util.logging.Logger;

private static final Logger logger = Logger.getLogger(MissingFontDetector.class.getName());

fontSettings.setWarningCallback(info -> {
    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
        logger.warning("Font substitution: " + info.getMessage());
    }
});
```

Это небольшое изменение делает механизм **detect missing font substitution** совместимым с существующими конвейерами логирования.

### 4.3 Handling other warning types

Обратный вызов получает *all* предупреждения, а не только проблемы со шрифтами. Если хотите следить за другими ошибками (например, `UNKNOWN_STYLE`), добавьте дополнительные ветки `if`. Вот быстрый пример:

```java
if (info.getWarningType() == WarningType.UNKNOWN_STYLE) {
    logger.info("Unknown style encountered: " + info.getMessage());
}
```

---

## Step 5: Common Pitfalls and Pro Tips

| Pitfall | Why it Happens | Fix |
|--------|----------------|-----|
| **No warning appears** | Шрифт действительно существует в ОС, либо документ использует fallback, который Aspose.Words считает «найденным». | Временно удалите шрифт из системы или используйте действительно отсутствующее имя шрифта в исходном документе. |
| **Callback never called** | `setWarningCallback` был вызван у *другого* экземпляра `FontSettings`, чем тот, что привязан к `LoadOptions`. | Убедитесь, что вызываете `loadOptions.setFontSettings(fontSettings)` **после** настройки обратного вызова. |
| **Performance slowdown** | Загрузка множества больших документов с обратными вызовами может добавить накладные расходы. | Кешируйте один экземпляр `FontSettings` и переиспользуйте его при пакетной обработке. |
| **Multiple threads** | `FontSettings` по умолчанию не является потокобезопасным. | Создайте отдельный `FontSettings` для каждого потока или синхронизируйте доступ. |

**Pro tip**: Если вы генерируете PDF для веб‑сервиса, имеет смысл собрать все предупреждения о подстановке в список и вернуть их в ответе API, вместо вывода в консоль.

---

## Full Working Example (Copy‑Paste Ready)

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {
        // Prepare load options
        LoadOptions loadOptions = new LoadOptions();

        // Configure font settings with a warning callback
        FontSettings fontSettings = new FontSettings();
        fontSettings.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substitution detected: " + info.getMessage());
                }
            }
        });

        // Attach font settings to load options
        loadOptions.setFontSettings(fontSettings);

        // Path to the document that contains a missing font
        String docPath = "YOUR_DIRECTORY/docWithMissingFont.docx";

        // Load the document – this triggers the callback if needed
        Document doc = new Document(docPath, loadOptions);

        // Optional: save as PDF to verify visual output
        // doc.save("output.pdf");

        System.out.println("Document loaded successfully.");
    }
}
```

**Expected console output** (при условии, что файл ссылается на отсутствующий шрифт):

```
⚠️ Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
Document loaded successfully.
```

Если отсутствующих шрифтов нет, вы увидите только финальную строку «Document loaded successfully.»

---

## Conclusion

Мы только что продемонстрировали, как **detect missing font substitution** в Java с помощью Aspose.Words. Настроив `LoadOptions`, создав экземпляр `FontSettings` и подключив `IWarningCallback`, вы получаете полную видимость каждой подстановки шрифта, происходящей в библиотеке. Такой подход не только предотвращает тихие артефакты рендеринга, но и предоставляет точку входа для логирования, оповещений или даже автоматического встраивания запасных шрифтов.

Дальше вы можете:

- Расширить обратный вызов, собирая предупреждения в список для ответов API.  
- Скомбинировать эту технику с **LoadOptions configuration** для других сценариев (например, пользовательская загрузка ресурсов).  
- Исследовать более широкую экосистему **Java Aspose.Words**: конвертация в PDF, извлечение текста или выполнение слияния писем.

Попробуйте, настройте логгер и позвольте вашим приложениям сигнализировать, когда шрифт исчезает. Приятного кодинга!

## Что следует изучить дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом пособии. Каждый ресурс содержит полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}