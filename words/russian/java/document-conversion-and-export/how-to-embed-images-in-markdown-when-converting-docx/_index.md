---
category: general
date: 2026-01-11
description: Узнайте, как встраивать изображения в Markdown при конвертации файла
  DOCX, используя Base64 для небольших картинок и сохраняя более крупные ресурсы отдельно.
draft: false
keywords:
- how to embed images
- convert docx to markdown
- how to convert docx
- embed images as base64
- export word document markdown
language: ru
og_description: Узнайте, как встраивать изображения в Markdown при конвертации файла
  DOCX, используя Base64 для небольших картинок и сохраняя более крупные ресурсы отдельно.
og_title: Как вставлять изображения в Markdown при конвертации DOCX
tags:
- Aspose.Words
- Java
- Markdown
- Image Embedding
title: Как вставлять изображения в Markdown при конвертации DOCX
url: /ru/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как встраивать изображения в Markdown при конвертации DOCX

Когда‑то задавались вопросом **как встраивать изображения** в файл Markdown, полученный из Word‑документа? Вы не одиноки. Большинство разработчиков сталкиваются с проблемой, когда при конвертации картинки исчезают или сохраняются так, что ломают итоговое оформление.

В этом руководстве мы пройдём полный, готовый к запуску пример, показывающий **как встраивать изображения** в виде Base64‑data URI для небольших графиков, а более крупные ресурсы сохраняются в отдельную папку. По пути мы также рассмотрим **конвертацию docx в markdown**, коснёмся **как конвертировать docx** с помощью Aspose.Words и объясним разницу между встраиванием изображений как Base64 и экспортом их в отдельные файлы.

> **Pro tip:** Если вам нужен лишь быстрый прототип, код ниже работает «из коробки» с одной зависимостью Maven.

---

## Что понадобится

- **Java 17** (или любой современный JDK) – API ориентировано на Java, но концепции применимы и к другим языкам.  
- **Aspose.Words for Java** – коммерческая библиотека, поддерживающая конвертацию DOCX → Markdown.  
- **Пример DOCX**, содержащий смесь небольших иконок и более крупных фотографий.  
- Папка, в которой вы хотите разместить Markdown‑файл и его ресурсы.

Никаких дополнительных фреймворков, никаких внешних скриптов. Просто чистый Java и Aspose.Words.

---

## Шаг 1 – Добавьте Aspose.Words в проект (convert docx to markdown)

Если вы используете Maven, вставьте следующий фрагмент в ваш `pom.xml`. При желании замените версию на актуальную на момент чтения.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for newer versions -->
</dependency>
```

> **Почему это важно:** Aspose.Words берёт на себя тяжёлую работу по разбору структуры DOCX, извлечению изображений и генерации синтаксиса Markdown. Писать собственный парсер – это кроличья нора, в которую, скорее всего, не стоит лезть.

---

## Шаг 2 – Загрузите исходный DOCX‑документ

Сначала укажите API путь к Word‑файлу, который нужно преобразовать. Конструктор `Document` делает всю работу — ручной разбор XML не требуется.

```java
import com.aspose.words.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Step 2: Load the source DOCX document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Обратите внимание, комментарий объясняет *почему* эта строка критична: без экземпляра `Document` нечего конвертировать.

---

## Шаг 3 – Подготовьте MarkdownSaveOptions с обратным вызовом сохранения ресурсов

Это ядро **как правильно встраивать изображения**. Обратный вызов предоставляет вам точку входа для каждого ресурса (изображения, стилей и т.д.), который конвертер хочет записать.

```java
        // Step 3: Create Markdown save options and define a resource‑saving callback
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
        saveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            public void resourceSaving(ResourceSavingArgs args) {
                // Step 4: Decide how to handle each image
                if (args.getResourceType() == ResourceType.IMAGE && args.getData().length < 10_000) {
                    // Small image – embed as Base64
                    String base64 = java.util.Base64.getEncoder()
                            .encodeToString(args.getData());
                    args.setUri("data:image/png;base64," + base64);
                    args.setKeepResourceStreamOpen(false);
                } else {
                    // Larger image – write to a folder
                    Path outPath = Paths.get("markdown_resources", args.getFileName());
                    try {
                        Files.createDirectories(outPath.getParent());
                        Files.write(outPath, args.getData());
                        // Normalize path for Markdown (use forward slashes)
                        args.setUri(outPath.toString().replace('\\', '/'));
                    } catch (Exception e) {
                        throw new RuntimeException(e);
                    }
                }
            }
        });
```

### Зачем нужен обратный вызов?

- **Контроль:** Вы решаете, будет ли изображение встроено как Base64‑строка или сохранено в отдельный файл.  
- **Производительность:** Маленькие иконки становятся частью Markdown, избавляя от лишних HTTP‑запросов.  
- **Переносимость:** Большие картинки остаются внешними файлами, что сохраняет разумный размер Markdown‑файла.

---

## Шаг 4 – Сохраните документ как Markdown

Наконец, попросите Aspose.Words записать файл Markdown, используя только что настроенные параметры.

```java
        // Step 5: Save the document as Markdown using the configured options
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

Запуск программы создаёт два результата:

1. `output.md` – Markdown‑представление вашего оригинального DOCX.  
2. Папка `markdown_resources` с любыми большими изображениями, которые не были встроены.

---

## Полный рабочий пример (Все шаги в одном месте)

Ниже полный исходный файл, готовый к копированию в вашу IDE. Замените `YOUR_DIRECTORY` на реальный путь на вашем компьютере.

```java
import com.aspose.words.*;
import java.nio.file.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the source DOCX document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Create Markdown save options and define a resource‑saving callback
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
        saveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            public void resourceSaving(ResourceSavingArgs args) {
                // Small images (<10 KB) become Base64 data URIs
                if (args.getResourceType() == ResourceType.IMAGE && args.getData().length < 10_000) {
                    String base64 = java.util.Base64.getEncoder()
                            .encodeToString(args.getData());
                    args.setUri("data:image/png;base64," + base64);
                    args.setKeepResourceStreamOpen(false);
                } else {
                    // Larger images are written to a dedicated folder
                    Path outPath = Paths.get("markdown_resources", args.getFileName());
                    try {
                        Files.createDirectories(outPath.getParent());
                        Files.write(outPath, args.getData());
                        args.setUri(outPath.toString().replace('\\', '/'));
                    } catch (Exception e) {
                        throw new RuntimeException(e);
                    }
                }
            }
        });

        // Step 3: Save the document as Markdown
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

**Ожидаемый результат:** Откройте `output.md` в любом просмотрщике Markdown. Маленькие иконки появляются встроенными, например:

```markdown
![Embedded Icon](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
```

Большие изображения будут ссылаться так:

```markdown
![Photo](markdown_resources/photo1.jpg)
```

Это именно то, что нужно, чтобы **встраивать изображения**, одновременно удерживая размер файла в разумных пределах.

---

## Часто задаваемые вопросы и особые случаи

### Что если изображение JPEG, а не PNG?

Обратный вызов выше всегда добавляет префикс `image/png`. Для JPEG вы можете проанализировать первые байты `args.getData()` или воспользоваться `args.getFileName()`, чтобы определить правильный MIME‑тип:

```java
String mime = args.getFileName().toLowerCase().endsWith(".jpg") ||
              args.getFileName().toLowerCase().endsWith(".jpeg")
              ? "image/jpeg" : "image/png";
args.setUri("data:" + mime + ";base64," + base64);
```

### Можно изменить пороговый размер?

Конечно. Ограничение в `10_000` байт – лишь пример. Если у вас достаточно пропускной способности, поднимите его до 50 KB или больше. И наоборот, уменьшите, если нужны сверхлёгкие Markdown‑файлы.

### Работает ли это с таблицами или другими объектами Word?

Да. Aspose.Words автоматически конвертирует таблицы, списки и даже сноски в Markdown. Обратный вызов ресурсов перехватывает только изображения, так что дополнительный код для остальных элементов не требуется.

### Как насчёт имён файлов с не‑ASCII символами?

API безопасно кодирует Unicode‑имена файлов при записи в папку `markdown_resources`. Просто убедитесь, что ваша файловая система поддерживает UTF‑8 (это так у большинства современных ОС).

---

## Pro Tips для гладкой конвертации

- **Поддерживайте чистоту папки вывода.** Вызывайте `Files.createDirectories` только один раз за конвертацию или удаляйте папку перед каждым запуском, если нужен «чистый старт».  
- **Проверяйте Markdown.** Инструменты вроде `markdownlint` могут выявить лишние символы, появившиеся из‑за некорректных Base64‑строк.  
- **Фиксируйте версию Aspose.Words.** Конкретная версия гарантирует, что ваш код будет работать даже после крупного обновления, меняющего поведение по умолчанию.  
- **Добавьте в .gitignore** запись для `markdown_resources/`

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}