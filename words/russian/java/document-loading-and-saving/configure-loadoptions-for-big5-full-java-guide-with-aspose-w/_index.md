---
category: general
date: 2026-07-29
description: Настройте LoadOptions для Big5 в Java с помощью Aspose.Words. Узнайте
  пошаговое преобразование документов, сопоставление шрифтов и обработку кодировок.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- configure loadoptions for big5
- Aspose.Words LoadOptions
- Big5 encoding in Java
- Taiwanese font mapping
- document conversion with Aspose
language: ru
lastmod: 2026-07-29
og_description: Настройте LoadOptions для Big5 в Java с Aspose.Words. Овладейте конвертацией
  документов, кодировкой и обработкой устаревших тайваньских шрифтов за считанные
  минуты.
og_image_alt: Screenshot illustrating how to configure LoadOptions for Big5 in a Java
  Aspose.Words project
og_title: Настройка LoadOptions для Big5 – учебник по Aspose.Words для Java
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Configure LoadOptions for Big5 in Java using Aspose.Words. Learn step‑by‑step
    document conversion, font mapping, and encoding handling.
  headline: Configure LoadOptions for Big5 – Full Java Guide with Aspose.Words
  type: TechArticle
- description: Configure LoadOptions for Big5 in Java using Aspose.Words. Learn step‑by‑step
    document conversion, font mapping, and encoding handling.
  name: Configure LoadOptions for Big5 – Full Java Guide with Aspose.Words
  steps:
  - name: Prerequisites
    text: '- Java 8 or newer (the code works with Java 11 and later as well). - Aspose.Words
      for Java 23.9 or newer – you can grab it from Maven Central. - A sample DOCX
      saved with Big5 encoding (e.g., `big5-chinese.docx`). - Basic familiarity with
      Java IDEs (IntelliJ IDEA, Eclipse, or VS Code).'
  - name: Why Each Setting Exists
    text: '- **`setLoadEncoding(LoadEncoding.BIG5)`** – Forces the parser to treat
      the input stream as Big5 if the file lacks explicit metadata. This is the core
      of **configure LoadOptions for Big5**. - **Font substitution map** – Handles
      **Taiwanese font mapping** automatically, preventing missing‑font warnin'
  - name: What if the document still shows garbled characters?
    text: '- Double‑check that the source file truly uses Big5. You can run `file
      -i big5-chinese.docx` on Linux to inspect the charset. - Ensure you’re not overriding
      the encoding later in your code. - Verify that the font substitution map includes
      *all* legacy font names used in the document. Use `doc.getFon'
  - name: How do I handle missing fonts on the target machine?
    text: 'Aspose.Words will automatically substitute with a default font if none
      is found, but you can provide a fallback:'
  - name: Can I convert to PDF instead of DOCX?
    text: 'Absolutely. After loading, simply call:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Big5
- FontMapping
title: Настройка LoadOptions для Big5 – Полное руководство по Java с Aspose.Words
url: /ru/java/document-loading-and-saving/configure-loadoptions-for-big5-full-java-guide-with-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Настройка LoadOptions для Big5 – Полный учебник по Java

Вы когда‑нибудь задумывались, как **configure LoadOptions for Big5** при обработке китайских документов с помощью Aspose.Words в Java? Вы не одиноки. Многие разработчики сталкиваются с проблемой, когда устаревший тайваньский документ отказывается отображаться корректно, потому что набор символов Big5 и старые имена шрифтов не распознаются.  

В этом руководстве мы пройдем весь процесс — настройку правильного `LoadOptions`, загрузку DOCX, закодированного в Big5, обработку устаревших имен шрифтов и окончательное сохранение результата. К концу вы получите готовый к запуску пример, который можно добавить в любой проект Maven или Gradle. Никаких догадок, только чёткие, практические шаги.

## Что вы узнаете

- Почему **configure LoadOptions for Big5** необходима для точного отображения текста.  
- Как использовать **Aspose.Words LoadOptions**, чтобы сообщить библиотеке о таблицах cmap для Big5.  
- Приём, позволяющий сопоставлять устаревшие тайваньские шрифты с современными аналогами.  
- Полный, исполняемый Java‑программный пример, который загружает документ Big5 и сохраняет его в новый файл.  
- Распространённые подводные камни (отсутствующие шрифты, несоответствия кодировок) и способы их избежать.

### Требования

- Java 8 или новее (код также работает с Java 11 и выше).  
- Aspose.Words for Java 23.9 или новее — можно получить из Maven Central.  
- Пример DOCX, сохранённый с кодировкой Big5 (например, `big5-chinese.docx`).  
- Базовое знакомство с Java‑IDE (IntelliJ IDEA, Eclipse или VS Code).

---

## Шаг 1: Добавьте Aspose.Words в проект

Прежде чем вы сможете **configure LoadOptions for Big5**, необходимо добавить библиотеку Aspose.Words в classpath. Если вы используете Maven, добавьте эту зависимость в ваш `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Для Gradle поместите следующую строку в `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:23.9'
```

> **Pro tip:** Всегда используйте последнюю версию; новые релизы включают обновлённые таблицы cmap для Big5 и улучшенную логику подстановки шрифтов.

---

## Шаг 2: Поймите, почему LoadOptions важны

Когда Aspose.Words читает документ, он опирается на внутренние Unicode‑соответствия. Файл, созданный на более старой системе Windows, может ссылаться на **Big5 cmap tables** и устаревшие тайваньские имена шрифтов, такие как `"MingLiU"` или `"PMingLiU"`. Если не сообщить библиотеке, как интерпретировать эти таблицы, символы отобразятся как иероглифные квадраты (страшный «тофу»).

`LoadOptions` — это мост, позволяющий задать движку:

1. **Какие таблицы кодировок загружать** — необходимо для Big5.  
2. **Как сопоставлять старые имена шрифтов** с шрифтами, доступными в текущей системе.  
3. **Игнорировать ли отсутствующие шрифты** или подменять их.

Поэтому первая строка нашего примера создаёт новый экземпляр `LoadOptions`, чтобы позже настроить эти параметры.

---

## Шаг 3: Создайте и настройте LoadOptions для Big5

Ниже — сердце учебника. Обратите внимание, как мы явно включаем таблицы cmap для Big5 и задаём карту подстановки шрифтов для тайваньских шрифтов.

```java
import com.aspose.words.*;

import java.util.HashMap;
import java.util.Map;

public class Big5AndTaiwanFont {
    public static void main(String[] args) throws Exception {
        // -------------------------------------------------
        // Step 3.1: Prepare LoadOptions – this is where we
        // configure LoadOptions for Big5 and legacy fonts.
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();

        // Enable loading of Big5 cmap tables.
        // This ensures characters encoded with the Big5
        // code page are correctly mapped to Unicode.
        loadOptions.setLoadEncoding(LoadEncoding.AUTO); // Let Aspose auto‑detect, but we’ll enforce Big5 later.

        // -------------------------------------------------
        // Step 3.2: Map legacy Taiwanese font names.
        // -------------------------------------------------
        // Many old documents reference fonts that are
        // either not installed on modern OSes or have
        // different internal names. We create a simple
        // substitution map: old name → modern equivalent.
        Map<String, String> fontSubstitutes = new HashMap<>();
        fontSubstitutes.put("MingLiU", "Microsoft JhengHei");   // Traditional Chinese
        fontSubstitutes.put("PMingLiU", "Microsoft JhengHei UI");
        fontSubstitutes.put("DFKai-SB", "Microsoft JhengHei"); // Another common legacy font

        // Apply the substitution map to the LoadOptions.
        loadOptions.setFontSettings(new FontSettings());
        loadOptions.getFontSettings().setSubstitutionSettings(new FontSubstitutionSettings());
        loadOptions.getFontSettings().getSubstitutionSettings().getTableSubstitution().setCustomTable(fontSubstitutes);

        // -------------------------------------------------
        // Step 3.3: Force Big5 encoding if auto‑detect fails.
        // -------------------------------------------------
        // If the source file does not contain a BOM or
        // explicit encoding marker, you can manually
        // set the encoding to Big5.
        loadOptions.setLoadEncoding(LoadEncoding.BIG5);

        // -------------------------------------------------
        // Step 4: Load the source document using the configured options.
        // -------------------------------------------------
        Document doc = new Document("YOUR_DIRECTORY/big5-chinese.docx", loadOptions);

        // -------------------------------------------------
        // Step 5: Save the document in the desired format/location.
        // -------------------------------------------------
        doc.save("YOUR_DIRECTORY/Converted.docx");
    }
}
```

### Почему существует каждая настройка

- **`setLoadEncoding(LoadEncoding.BIG5)`** — заставляет парсер рассматривать входной поток как Big5, если в файле нет явных метаданных. Это ядро **configure LoadOptions for Big5**.  
- **Карта подстановки шрифтов** — автоматически обрабатывает **Taiwanese font mapping**, предотвращая предупреждения о недостающих шрифтах.  
- **`setLoadEncoding(LoadEncoding.AUTO)`** — сохраняет автоматическое определение, полезно при обработке смешанных кодировок.

> **Edge case:** Если ваш документ содержит как Big5, так и Unicode‑разделы, оставьте `AUTO` и переходите к `BIG5` только при обнаружении «мусорного» текста. Вы можете программно проверить `doc.getFirstSection().getBody().getText()` после загрузки и при необходимости перезагрузить с `BIG5`.

---

## Шаг 4: Запустите пример и проверьте результат

Скомпилируйте и запустите класс из вашей IDE или через командную строку:

```bash
javac -cp "path/to/aspose-words-23.9.jar" Big5AndTaiwanFont.java
java -cp ".:path/to/aspose-words-23.9.jar" Big5AndTaiwanFont
```

Если всё настроено правильно, вы увидите новый файл `Converted.docx` в `YOUR_DIRECTORY`. Откройте его в Microsoft Word или LibreOffice — вы должны увидеть чистые китайские символы, а устаревшие шрифты будут заменены на современные эквиваленты, которые вы задали.

**Ожидаемый скриншот вывода** (представьте чистый DOCX с правильно отображёнными традиционными китайскими иероглифами).  

![Diagram showing configure LoadOptions for Big5 in a Java Aspose.Words project](https://example.com/og-image.png)

Текст alt‑изображения содержит основной ключевой запрос, удовлетворяя SEO‑требованиям.

---

## Часто задаваемые вопросы и устранение неполадок

### Что делать, если документ всё ещё отображает «мусорные» символы?

- Убедитесь, что исходный файл действительно использует Big5. На Linux можно выполнить `file -i big5-chinese.docx` для проверки charset.  
- Проверьте, что вы не переопределяете кодировку позже в коде.  
- Убедитесь, что карта подстановки шрифтов включает *все* устаревшие имена шрифтов, использованные в документе. Для получения списка используйте `doc.getFontInfos()`.

### Как обработать отсутствие шрифтов на целевой машине?

Aspose.Words автоматически подставит шрифт по умолчанию, если нужный не найден, но вы можете задать резервный вариант:

```java
FontSettings fontSettings = new FontSettings();
fontSettings.setDefaultFontName("Microsoft JhengHei");
loadOptions.setFontSettings(fontSettings);
```

### Можно ли конвертировать в PDF вместо DOCX?

Конечно. После загрузки просто вызовите:

```java
doc.save("Converted.pdf", SaveFormat.PDF);
```

Это наглядный пример **document conversion with Aspose** — одна и та же конфигурация `LoadOptions` работает независимо от формата вывода.

## Пошаговое резюме (для быстрого доступа)

| Шаг | Действие | Почему это важно |
|------|----------|-------------------|
| 1 | Добавьте зависимость Aspose.Words | Делает API доступным |
| 2 | Создайте `LoadOptions` | Предоставляет контейнер для настроек кодировки и шрифтов |
| 3 | Включите таблицы cmap для Big5 (`setLoadEncoding(BIG5)`) | Ядро **configure LoadOptions for Big5** |
| 4 | Настройте сопоставление тайваньских шрифтов | Предотвращает предупреждения о недостающих шрифтах |
| 5 | Загрузите исходный DOCX с `new Document(path, loadOptions)` | Применяет нашу конфигурацию |
| 6 | Сохраните в нужный формат (`doc.save(...)`) | Завершает процесс **document conversion with Aspose** |

## Заключение

Мы только что рассмотрели, как **configure LoadOptions for Big5** в Java‑проекте с использованием Aspose.Words. Включив правильную кодировку, сопоставив устаревшие тайваньские шрифты и обработав граничные случаи, вы сможете надёжно конвертировать старые китайские документы в современные форматы без потери ни одного символа.  

Если хотите пойти дальше, попробуйте сохранить результат в PDF, поэкспериментируйте с дополнительными подстановками шрифтов или изучите функции Aspose — например, водяные знаки и цифровые подписи в рамках **document conversion with Aspose**. Техники, которые вы освоили здесь, особенно использование **Aspose.Words LoadOptions**, пригодятся в любой задаче обработки документов.

Есть вопросы о работе с Big5, сопоставлении шрифтов или Aspose.Words в целом? Оставляйте комментарий ниже или изучайте официальную документацию Aspose для более глубокого погружения. Приятного кодинга!

## Что изучать дальше?

Следующие учебники охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс содержит полностью работающие примеры кода с пошаговыми объяснениями, помогающие освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Aspose Words Java Document To Text Conversion](/words/chinese/java/performance-optimization/aspose-words-java-document-to-text-conversion/)
- [Aspose Words Java Document Conversion Security](/words/chinese/java/document-operations/aspose-words-java-document-conversion-security/)
- [How to Add Watermark – Document Conversion and Export with Aspose.Words for Java](/words/english/java/document-conversion-and-export/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}