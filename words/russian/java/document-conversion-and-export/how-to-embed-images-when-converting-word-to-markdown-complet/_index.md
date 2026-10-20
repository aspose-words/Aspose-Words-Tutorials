---
category: general
date: 2026-02-28
description: Узнайте, как встраивать изображения при конвертации doc в markdown. Экспортируйте
  markdown с изображениями и получайте встроенные изображения в markdown с помощью
  Java.
draft: false
keywords:
- how to embed images
- convert doc to markdown
- convert word to markdown
- export markdown with images
- inline images in markdown
language: ru
og_description: Узнайте, как встраивать изображения при конвертации документа Word
  в Markdown. Это руководство покажет, как экспортировать markdown с изображениями
  и сохранять их в строке.
og_title: Как вставлять изображения при конвертации Word в Markdown
tags:
- markdown
- java
- Aspose.Words
- image handling
title: Как вставлять изображения при конвертации Word в Markdown — Полное руководство
url: /ru/java/document-conversion-and-export/how-to-embed-images-when-converting-word-to-markdown-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как встраивать изображения при конвертации Word в Markdown – Полное руководство

Вы когда‑нибудь задумывались **как встраивать изображения** в файл Markdown, который генерируется из документа Word? Возможно, вы пробовали быстрый экспорт, но в итоге получили кучу висячих файлов изображений и сломанные ссылки. Это распространённая проблема — особенно когда нужен один, переносимый `.md`, который можно разместить в генераторе статических сайтов или в README на GitHub.

Хорошая новость? Вы можете указать экспортеру встраивать каждую картинку как строку, закодированную в Base64, так что полученный Markdown будет самодостаточным. В этом руководстве мы пройдём по точным шагам, покажем полный Java‑код и объясним, почему каждый элемент важен. К концу вы сможете **convert doc to markdown** с встраиваемыми изображениями и также узнаете, как настроить процесс для других сценариев, таких как «export markdown with images» или «inline images in markdown».

## Что вы узнаете

- Необходимые библиотеки и минимальная настройка проекта.  
- Как настроить `MarkdownSaveOptions`, чтобы изображения становились Base64‑data URIs.  
- Почему использование `ResourceSavingCallback` — самый чистый способ контролировать обработку изображений.  
- Как проверить, что файл Markdown действительно содержит встроенные изображения.  
- Советы для граничных случаев (большие изображения, разные MIME‑типы и соображения производительности).  

Предыдущий опыт работы с Aspose.Words не требуется; достаточно базовых знаний Java.

---

## Требования

Прежде чем погрузиться в код, убедитесь, что у вас есть:

| Требование | Почему это важно |
|------------|-------------------|
| **Java 17+** (или любой современный JDK) | API Aspose.Words for Java ориентировано на Java 8+, но использование последнего JDK даёт встроенные утилиты `Base64`. |
| **Aspose.Words for Java** (последняя версия) | Эта библиотека предоставляет `MarkdownSaveOptions` и инфраструктуру обратных вызовов, которые мы будем использовать. |
| **Документ Word** (`.docx`), содержащий хотя бы одно изображение | Нам нужно что‑то конвертировать; в примере предполагается файл `sample.docx`. |
| **IDE или текстовый редактор** (IntelliJ, VS Code и т.д.) | Чтобы быстро собрать и запустить пример. |

Добавьте зависимость Aspose в ваш `pom.xml` (Maven) или `build.gradle` (Gradle). Вот фрагмент для Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Check the latest version on Maven Central -->
</dependency>
```

Если вы предпочитаете Gradle:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Pro tip:** Aspose предлагает бесплатную 30‑дневную trial‑версию. Получите временный лицензионный ключ и зарегистрируйте его заранее, чтобы избежать сообщений о водяных знаках.

---

## Шаг 1: Создание параметров сохранения Markdown

Первое, что мы делаем, — создаём экземпляр `MarkdownSaveOptions`. Этот объект сообщает Aspose, как должна вести себя конверсия — обработка шрифтов, форматирование списков и, что самое важное для нас, обработка изображений.

```csharp
// Step 1: Create Markdown save options
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions();
```

В Java синтаксис идентичен; просто замените ключевое слово `csharp` на `java` в блоке кода позже.  
Почему это важно: без настройки параметров Aspose запишет каждое изображение в отдельный файл рядом с `.md`. Подготовив объект параметров сейчас, мы получаем точку входа для перехвата этого поведения по умолчанию.

---

## Шаг 2: Перехват ресурсов изображений и их кодирование в Base64

Aspose вызывает обратный вызов каждый раз, когда хочет записать ресурс (изображение, CSS и т.п.). Реализуя `IResourceSavingCallback`, мы можем решить, что делать с каждым ресурсом. Ниже показанный фрагмент проверяет, является ли ресурс изображением, очищает имя файла (чтобы не создавать внешний файл), кодирует бинарные данные в Base64 и задаёт правильный MIME‑тип.

```java
// Step 2: Embed all images directly as Base64 data
markdownSaveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
    @Override
    public void resourceSaving(ResourceSavingArgs args) {
        // Check if the resource being saved is an image
        if (args.getResourceType() == ResourceType.IMAGE) {
            // Suppress writing an external image file
            args.setResourceFileName(null);
            // Encode the image bytes to a Base64 string
            args.setResourceData(Base64.getEncoder()
                    .encodeToString(args.getResourceData()));
            // Set the appropriate MIME type for the embedded image
            args.setResourceContentType("image/png");
        }
    }
});
```

**Что происходит под капотом?**

1. **`args.getResourceType()`** – Aspose классифицирует каждый исходящий блоб. Нас интересует только `ResourceType.IMAGE`.  
2. **`args.setResourceFileName(null)`** – Устанавливая `null` в качестве имени файла, мы говорим библиотеке *не* писать физический файл.  
3. **`Base64.getEncoder().encodeToString(...)`** – Сырой массив байтов превращается в текстовую строку, которую можно безопасно разместить в data URI Markdown.  
4. **`args.setResourceContentType("image/png")`** – Это гарантирует, что сгенерированный тег Markdown будет выглядеть как `![alt](data:image/png;base64,…)`. Если ваш исходный документ содержит JPEG, вы можете проанализировать оригинальные байты и выбрать `"image/jpeg"`.

> **Почему Base64?**  
> Процессоры Markdown, понимающие data URI, отобразят картинку напрямую, а полученный файл останется портативным — без дополнительных ресурсов для копирования. Это особенно удобно для README на GitHub или документационных сайтов, где внешние ресурсы запрещены.

---

## Шаг 3: Выполнение конверсии

Теперь, когда параметры готовы, просто загрузите ваш документ Word и вызовите `save`. Указанный путь будет местом сохранения сгенерированного файла Markdown.

```java
// Step 3: Load the source Word document
Document doc = new Document("sample.docx");

// Step 4: Save the document as a Markdown file using the configured options
doc.save("output/doc.md", markdownSaveOptions);
```

Вот и всё — две строки кода реальной конверсии. Всё тяжёлое (чтение DOCX, извлечение изображений, преобразование абзацев) полностью обрабатывается Aspose.

---

## Шаг 4: Проверка результата – встраиваемые изображения отображаются

Откройте `output/doc.md` в любом текстовом редакторе. Вы должны увидеть что‑то вроде:

```markdown
# Sample Document

Here is an inline image:

![Image 1](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...
```

Если вставить Markdown в просмотрщик, поддерживающий data URI (GitHub, предварительный просмотр VS Code или генератор статических сайтов), картинка отобразится без каких‑либо дополнительных файлов.

**Быстрая проверка**:  

- **Поиск `data:image/`** – Если найдёте несколько длинных строк, встраивание прошло успешно.  
- **Подсчёт шаблонов `![](`** – Их количество должно совпадать с числом изображений в исходном файле Word.

---

## Обработка граничных случаев

### Большие изображения

Base64 увеличивает исходный размер примерно на **33 %**. Для очень больших картинок (например, фото высокого разрешения) файл Markdown может стать громоздким. Рассмотрите следующие стратегии:

| Стратегия | Когда использовать |
|-----------|---------------------|
| **Resize before conversion** – Use `java.awt.Image` to scale down. | Когда исходный документ содержит ресурсы высокого разрешения, которые не нужны в полном размере. |
| **Switch to JPEG** – Change `args.setResourceContentType("image/jpeg")`. | Для фотографий, где без потерь PNG избыточен. |
| **Chunk the document** – Split the Word file into sections and export each separately. | Когда необходимо удержать файл Markdown ниже определённого лимита (например, 10 MB на GitHub). |

### Изображения не‑PNG

Если ваш документ Word содержит разные форматы, вы можете динамически определять MIME‑тип:

```java
String mime = args.getResourceContentType(); // returns something like "image/jpeg"
args.setResourceContentType(mime); // keep original type
```

Aspose уже заполняет `ResourceContentType`, поэтому часто нет необходимости жёстко задавать `"image/png"`.

### Советы по производительности

- **Reuse a single `Base64.Encoder` instance** if you’re converting many images in a loop.  
- **Enable `markdownSaveOptions.setExportImagesAsBase64(true)`** (if the API version supports it) to avoid the callback entirely.  
- **Run the conversion in a background thread** when processing bulk documents in a server environment.

---

## Полный рабочий пример (все вместе)

Ниже представлена готовая к копированию Java‑программа, включающая импорты, обработку ошибок и полный поток, о котором шла речь.

```java
import com.aspose.words.*;
import java.util.Base64;
import java.nio.file.Paths;

public class WordToMarkdownWithEmbeddedImages {
    public static void main(String[] args) {
        try {
            // Load the source DOCX
            Document doc = new Document("sample.docx");

            // Configure Markdown save options
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();

            // Embed images as Base64 data URIs
            mdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
                @Override
                public void resourceSaving(ResourceSavingArgs rsArgs) {
                    if (rsArgs.getResourceType() == ResourceType.IMAGE) {
                        // Prevent external file creation
                        rsArgs.setResourceFileName(null);
                        // Encode image bytes to Base64
                        String base64 = Base64.getEncoder()
                                .encodeToString(rsArgs.getResourceData());
                        rsArgs.setResourceData(base64);
                        // Preserve original MIME type (PNG, JPEG, etc.)
                        String mime = rsArgs.getResourceContentType();
                        rsArgs.setResourceContentType(mime);
                    }
                }
            });

            // Define output path (ensure directory exists)
            String outputPath = Paths.get("output", "doc.md").toString();
            doc.save(outputPath, mdOptions);

            System.out.println("Conversion complete! Markdown saved to: " + outputPath);
        } catch (Exception e) {
            System.err.println("Error during conversion: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Ожидаемый результат**: один файл `doc.md`, содержащий встроенные Base64‑изображения, готовый к использованию в любом инструменте, поддерживающем Markdown.

---

## Часто задаваемые вопросы

**Q1: Работает ли это со старыми версиями Aspose.Words?**  
*Обычно да.* API обратного вызова стабилен, начиная с версии 19. Однако параметр `setExportImagesAsBase64` появился в более поздних релизах, поэтому если вы используете более старую сборку, вам понадобится явный callback, показанный выше.

**Q2: Что если мне нужно экспортировать в GitHub Flavored Markdown (GFM)?**  
`MarkdownSaveOptions` от Aspose уже генерирует синтаксис, совместимый с GFM. Единственный дополнительный шаг — убедиться, что движок рендеринга вашего репозитория поддерживает data URI — GitHub поддерживает.

**Q3: Можно ли использовать этот подход для других форматов, например HTML?**  
Абсолютно. Тот же `ResourceSavingCallback` работает и с `HtmlSaveOptions`. Просто замените класс параметров и оставьте логику Base64.

##

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}