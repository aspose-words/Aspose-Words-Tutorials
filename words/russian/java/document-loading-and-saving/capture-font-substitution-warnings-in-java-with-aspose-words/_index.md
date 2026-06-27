---
category: general
date: 2026-06-27
description: Узнайте, как перехватывать предупреждения о замене шрифтов в Java с помощью
  Aspose.Words. Этот пошаговый учебник также охватывает обратные вызовы предупреждений
  и использование LoadOptions.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words warning callback
- Java LoadOptions example
- font substitution handling
- document processing with Aspose
language: ru
og_description: Отслеживайте предупреждения о замене шрифтов в Java с помощью Aspose.Words.
  Следуйте этому руководству, чтобы настроить обратные вызовы предупреждений, использовать
  LoadOptions и обрабатывать отсутствующие шрифты.
og_title: Перехват предупреждений о замене шрифтов в Java – учебник Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to capture font substitution warnings in Java using Aspose.Words.
    This step‑by‑step tutorial also covers warning callbacks and LoadOptions usage.
  headline: Capture Font Substitution Warnings in Java with Aspose.Words – Complete
    Guide
  type: TechArticle
- questions:
  - answer: Yes. The warning callback is format‑agnostic; it fires for any document
      type that Aspose.Words loads (DOC, DOCX, RTF, HTML, etc.). The only difference
      is the set of warnings that may appear.
    question: Does this work with PDF or other formats?
  - answer: Absolutely. Inside the `warning` method, inspect `info.getWarningType()`
      for other enum values such as `WarningType.IMAGE_RESOLUTION`. Then handle them
      accordingly.
    question: Can I capture other warning types, like *image resolution* warnings?
  - answer: 'Store each `info.getDescription()` in a `List<String>` inside the callback.
      After loading, you’ll have a collection you can log, send to a monitoring service,
      or use to trigger a font‑download routine. ## Conclusion You now know **how
      to capture font substitution warnings** in Java using Aspose.Word'
    question: What if I need the list of substituted fonts after the document loads?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Document Conversion
title: Перехват предупреждений о замене шрифтов в Java с Aspose.Words – Полное руководство
url: /ru/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Захват предупреждений о замене шрифтов в Java с Aspose.Words – Полное руководство

Когда‑нибудь нужно было **захватывать предупреждения о замене шрифтов** при загрузке DOCX, использующего экзотические типы шрифтов? Вы не одиноки. Во многих реальных проектах — будь то автоматические генераторы отчетов или пакетные конвертеры документов — отсутствие шрифтов приводит к тихой замене, которая может испортить точность макета.  

К счастью, Aspose.Words предоставляет удобный способ прослушивать такие предупреждения. В этом руководстве мы пройдем настройку **LoadOptions**, подключим **callback предупреждений Aspose.Words** и выведем каждое уведомление о *замене шрифта* в консоль. К концу вы будете точно знать, когда шрифт был заменён и как реагировать программно.

> **Что вы получите:** полностью рабочий фрагмент кода на Java, объяснение *почему* каждый элемент важен и советы по обработке крайних случаев, таких как пользовательские каталоги шрифтов.

## Предварительные требования и что понадобится

Прежде чем приступить, убедитесь, что у вас есть:

- Java 8 или новее (код также работает с Java 11+).
- Последний JAR Aspose.Words for Java (скачайте с официального сайта или Maven Central).
- Файл DOCX, который ссылается на шрифты, не установленные на вашем компьютере (например, *font‑rich.docx* из набора демо‑примеров Aspose).
- Удобная IDE (IntelliJ IDEA, Eclipse или даже VS Code с Java‑расширениями).

Никаких внешних библиотек, кроме Aspose.Words, не требуется, пример работает в обычном `main`‑методе.

## Шаг 1: Настройка LoadOptions – точка входа для пользовательской загрузки

`LoadOptions` — это «мешок» конфигураций Aspose.Words, который указывает библиотеке *как* читать документ. По умолчанию она тихо заменяет недостающие шрифты, но вы можете изменить это поведение с помощью callback‑а предупреждений.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions to customize loading behavior
        LoadOptions loadOptions = new LoadOptions();
```

**Почему это важно:** Без `LoadOptions` документ загружается без вывода, и вы теряете видимость недостающих шрифтов. Создав экземпляр, вы получаете точку подключения к системе предупреждений.

## Шаг 2: Определите callback предупреждений для *захвата предупреждений о замене шрифтов*

Aspose.Words отправляет события предупреждений через интерфейс `IWarningCallback`. Реализуйте его inline (или в отдельном классе) и отфильтруйте `WarningType.FONT_SUBSTITUTION`.

```java
        // Step 2: Define a warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Only react to font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });
```

**Пояснение:**  
- `info.getWarningType()` сообщает категорию предупреждения.  
- `WarningType.FONT_SUBSTITUTION` — это значение перечисления, которое нас интересует.  
- `info.getDescription()` содержит человекочитаемое сообщение, например *“Font 'Comic Sans MS' not found, substituted with 'Arial'.”*  

Выводя описание, вы **захватываете предупреждения о замене шрифтов** в реальном времени.

## Шаг 3: Загрузите документ, используя настроенный LoadOptions

Теперь, когда callback установлен, загрузите ваш DOCX. Callback предупреждений срабатывает автоматически во время парсинга.

```java
        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);
```

Замените `YOUR_DIRECTORY` реальным путём к вашему тестовому файлу. Когда вызывается конструктор `Document`, любое отсутствие шрифта активирует ранее определённый callback, и вы увидите сообщения о замене в консоли.

## Шаг 4: Проверьте загруженный документ (необязательно, но полезно)

После загрузки вы можете подтвердить целостность документа — количество страниц, извлечение текста и т.д. Этот шаг не обязателен для захвата предупреждений, но помогает увидеть влияние замен.

```java
        // Optional: Output basic document info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + document.getPageCount());
```

Если шрифт был заменён, макет может слегка сместиться; проверка количества страниц может выявить такие изменения.

## Шаг 5: Продвинутое – программная обработка заменённых шрифтов

Иногда недостаточно просто залогировать предупреждение — может потребоваться внедрить запасной шрифт или скорректировать стили. Ниже показан быстрый шаблон, который вы можете использовать.

```java
        // Advanced: Register a fallback font folder to reduce substitutions
        FontSettings fontSettings = new FontSettings();
        // Point to a folder that contains the missing fonts
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);
```

Указав Aspose.Words папку, содержащую оригинальные шрифты, вы можете *предотвратить* замену полностью. Если папка отсутствует, callback всё равно фиксирует событие, предоставляя стратегию резервного копирования.

## Полный рабочий пример

Собрав всё вместе, получаем полностью готовую к запуску программу:

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Initialize LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // Set up warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // OPTIONAL: Register a custom fonts folder to avoid substitution
        FontSettings fontSettings = new FontSettings();
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);

        // Load the document – warnings will be printed automatically
        Document doc = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);

        // Verify basic info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + doc.getPageCount());
    }
}
```

**Ожидаемый вывод в консоль** (когда обнаружен отсутствующий шрифт):

```
Font substituted: Font 'Pacifico' not found, substituted with 'Arial'.
Document loaded successfully.
Page count: 3
```

Если все шрифты присутствуют, callback остаётся тихим — ничего не выводится, что и ожидается.

## Распространённые ошибки и профессиональные советы

| Проблема | Почему происходит | Как исправить |
|----------|-------------------|---------------|
| **Callback не срабатывает** | Вы забыли привязать callback к `LoadOptions` **или** использовали конструктор `Document` без передачи `loadOptions`. | Всегда вызывайте `loadOptions.setWarningCallback(...)` **и** используйте перегрузку `new Document(path, loadOptions)`. |
| **Слишком много предупреждений захламляют лог** | Большие документы с множеством недостающих шрифтов генерируют предупреждение на каждую замену. | Дальше фильтруйте, проверяя `info.getDescription()` на конкретные имена шрифтов, либо собирайте предупреждения в список для последующей обработки. |
| **Заменённые шрифты влияют на макет** | Запасной шрифт может иметь другие метрики (размер, интервал). | Предоставьте пользовательскую папку шрифтов (см. Шаг 5) или скорректируйте стили документа после загрузки. |
| **Запуск на безголовом сервере** | Стандартный запасной шрифт может опираться на системные шрифты, которых нет на сервере. | Поставьте необходимые шрифты вместе с приложением и укажите `FontSettings` на эту папку. |

## Часто задаваемые вопросы

**В: Работает ли это с PDF или другими форматами?**  
О: Да. Callback предупреждений не зависит от формата; он срабатывает для любого типа документа, который загружает Aspose.Words (DOC, DOCX, RTF, HTML и т.д.). Разница лишь в наборе возможных предупреждений.

**В: Могу ли я захватывать другие типы предупреждений, например *image resolution*?**  
О: Конечно. Внутри метода `warning` проверяйте `info.getWarningType()` на другие значения перечисления, такие как `WarningType.IMAGE_RESOLUTION`. Затем обрабатывайте их по‑своему.

**В: Как получить список заменённых шрифтов после загрузки документа?**  
О: Сохраняйте каждое `info.getDescription()` в `List<String>` внутри callback‑а. После загрузки у вас будет коллекция, которую можно вывести в лог, отправить в мониторинговый сервис или использовать для запуска процедуры загрузки шрифтов.

## Заключение

Теперь вы знаете **как захватывать предупреждения о замене шрифтов** в Java с помощью Aspose.Words, почему каждый элемент важен и как расширить решение для реальных сценариев. Используя `LoadOptions`, `callback предупреждений Aspose.Words` и при необходимости `FontSettings`, вы получаете полную видимость недостающих шрифтов и можете обеспечить надёжность конвейеров конвертации документов.

Готовы к следующему шагу? Попробуйте заменить `System.out.println` на логгер, например SLF4J, или интегрировать список предупреждений в UI, который оповестит пользователей перед окончательной пакетной конвертацией. Вы также можете изучить **callback предупреждений Aspose.Words** для других типов предупреждений, таких как *unsupported features* или *high‑resolution image* alerts.  

Счастливого кодинга, и пусть ваши PDF‑файлы больше никогда не страдают от неожиданной замены шрифтов! 

![Скриншот, показывающий вывод в консоль захваченных предупреждений о замене шрифтов](image-placeholder.png "захват предупреждений о замене шрифтов")


## Что изучать дальше?


Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}