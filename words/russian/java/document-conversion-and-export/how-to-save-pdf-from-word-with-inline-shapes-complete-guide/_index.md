---
category: general
date: 2026-06-05
description: Как сохранить PDF из DOCX, сохранив плавающие фигуры как встроенные теги.
  Узнайте, как сохранить DOCX в PDF, конвертировать Word в PDF и правильно экспортировать
  фигуры.
draft: false
keywords:
- how to save pdf
- save docx as pdf
- convert word to pdf
- how to export shapes
- save word pdf inline
language: ru
og_description: Как сохранить PDF из документа Word, экспортируя плавающие объекты
  как встроенные теги. Следуйте этому пошаговому руководству, чтобы правильно сохранить
  docx в PDF и конвертировать Word в PDF.
og_title: Как сохранить PDF из Word с встроенными объектами — полный учебник
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: How to save PDF from a DOCX while preserving floating shapes as inline
    tags. Learn to save docx as pdf, convert word to pdf, and export shapes correctly.
  headline: How to Save PDF from Word with Inline Shapes – Complete Guide
  type: TechArticle
- description: How to save PDF from a DOCX while preserving floating shapes as inline
    tags. Learn to save docx as pdf, convert word to pdf, and export shapes correctly.
  name: How to Save PDF from Word with Inline Shapes – Complete Guide
  steps:
  - name: Large Images
    text: 'If a floating shape contains a high‑resolution image, converting it to
      inline may cause the line height to expand dramatically. To keep the PDF tidy:'
  - name: Multiple Sections with Different Layouts
    text: 'When a document has sections with distinct page setups, you might need
      to apply the inline conversion only to a specific section:'
  - name: Converting Multiple DOCX Files in a Batch
    text: 'If you need to **convert word to pdf** for dozens of files, wrap the logic
      into a utility method:'
  - name: Expected Result
    text: Running the program should produce `inlineShapes.pdf`. Open it, and you’ll
      notice that any floating text boxes, callouts, or images now sit **inline**
      with the surrounding text, mirroring the layout you designed in Word.
  type: HowTo
tags:
- Aspose.Words
- Java
- PDF conversion
title: Как сохранить PDF из Word с встроенными объектами – Полное руководство
url: /ru/java/document-conversion-and-export/how-to-save-pdf-from-word-with-inline-shapes-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как сохранить PDF из Word с встроенными объектами – Полное руководство

Вы когда‑нибудь задавались вопросом, **как сохранить PDF** из файла Word, не теряя расположения плавающих изображений? Вы не одиноки. Во многих приложениях для отчетности или выставления счетов эти плавающие объекты — такие как текстовые поля, выноски или декоративные значки — часто оказываются смещенными, если просто нажать «Сохранить как PDF».  

К счастью, существует чистый программный способ сохранить эти объекты ровно там, где вы их ожидаете: настроить экспорт PDF так, чтобы плавающие объекты преобразовывались в теги `<inline>`. В этом руководстве мы пройдемся по **how to export shapes**, **save docx as pdf**, и **convert word to pdf**, используя несколько строк кода на Java. К концу вы получите готовый к запуску фрагмент, который создает PDF, где каждый объект отображается встроенно.

## Что вы узнаете

- Загрузить файл DOCX с диска (или любой поток) с помощью Aspose.Words for Java.  
- Включить параметр **save word pdf inline**, чтобы плавающие объекты становились тегами inline.  
- Сохранить документ как PDF, используя настроенный `PdfSaveOptions`.  
- Советы по обработке крайних случаев, таких как крупные изображения или сложные таблицы.  

Никаких внешних инструментов, никакой ручной настройки интерфейса Word — только чистый код, который можно добавить в любой проект Java.

---

## Требования

Прежде чем мы начнём, убедитесь, что у вас есть:

| Требование | Почему это важно |
|-------------|----------------|
| **Java 17+** (or any recent JDK) | Aspose.Words for Java работает на современных JDK. |
| **Aspose.Words for Java** library (latest version) | Предоставляет `Document`, `PdfSaveOptions` и метод `setExportFloatingShapesAsInlineTag`. |
| Файл **DOCX**, содержащий плавающие объекты (например, текстовое поле). | Без объектов вы не увидите эффект экспорта в inline. |
| IDE или система сборки (Maven/Gradle) для управления зависимостями. | Обеспечивает безболезненную компиляцию. |

Если вы используете Maven, добавьте зависимость:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Check for the latest version -->
</dependency>
```

---

## Шаг 1: Загрузка исходного документа

Первое, что вам нужно, — объект `Document`, представляющий ваш файл Word. Считайте его холстом, на котором Aspose.Words позже нарисует PDF.

```java
// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Почему это важно:* Загрузка файла в память дает полный доступ к его объектной модели — абзацам, пробегам, объектам, всему. Если путь неверен, вы получите `FileNotFoundException`, поэтому проверьте, что файл существует.

> **Совет:** Если вы получаете DOCX из базы данных или веб‑сервиса, можно использовать конструктор `InputStream` вместо пути к файлу.

---

## Шаг 2: Настройка параметров сохранения PDF для экспорта плавающих объектов как inline‑тегов

По умолчанию Aspose.Words пытается оставить плавающие объекты плавающими в PDF, что может вызвать смещение, когда просмотрщик PDF интерпретирует макет иначе. Класс `PdfSaveOptions` позволяет изменить это поведение.

```java
// Step 2: Configure PDF save options to export floating shapes as <inline> tags
PdfSaveOptions pdfOptions = new PdfSaveOptions();
pdfOptions.setExportFloatingShapesAsInlineTag(true);
```

*Почему это важно:* Установка `setExportFloatingShapesAsInlineTag(true)` сообщает экспортеру рассматривать каждый плавающий объект как часть окружающего абзаца. В результате PDF, где объект перемещается вместе с текстом, устраняя пробелы или перекрывающиеся элементы.

> **Распространённый вопрос:** *Что если я всё ещё хочу, чтобы некоторые объекты оставались плавающими?*  
> Вы можете выборочно установить `WrapType` отдельных объектов в документе Word перед экспортом, либо отключить конвертацию в inline для всего документа и обрабатывать такие объекты вручную.

---

## Шаг 3: Сохранение документа как PDF с настроенными параметрами

Теперь, когда документ загружен и поведение экспорта настроено, пришло время записать PDF‑файл на диск.

```java
// Step 3: Save the document as a PDF with the configured options
doc.save("YOUR_DIRECTORY/inlineShapes.pdf", pdfOptions);
```

*Почему это важно:* Метод `save` принимает как путь вывода, так и экземпляр `PdfSaveOptions`, гарантируя, что ваш параметр inline‑shape будет учтён. Если опции опустить, будет использовано поведение по умолчанию (плавающие объекты останутся плавающими).

> **Ожидаемый результат:** Откройте `inlineShapes.pdf` в любом просмотрщике PDF. Все ранее плавающие текстовые поля или изображения теперь должны отображаться **inline** с текстом абзаца, сохраняя визуальный макет, который вы видели в Word.

---

## Обработка крайних случаев и вариантов

### Большие изображения

Если плавающий объект содержит изображение высокого разрешения, преобразование его в inline может сильно увеличить высоту строки. Чтобы PDF оставался аккуратным:

```java
// Reduce image size before export (optional)
Shape shape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
shape.getImageData().setImageBytes(resizeImage(shape.getImageData().getImageBytes(), 800, 600));
```

*Объяснение:* Изменение размера изображения уменьшает его размеры, предотвращая слишком большие строки в конечном PDF.

### Несколько разделов с разными макетами

Когда документ имеет разделы с различными настройками страниц, возможно, потребуется применять конвертацию в inline только к определённому разделу:

```java
for (Section sec : doc.getSections()) {
    PdfSaveOptions opts = new PdfSaveOptions();
    opts.setExportFloatingShapesAsInlineTag(sec.getPageSetup().getPaperSize() == PaperSize.A4);
    doc.save("section_" + sec.getId() + ".pdf", opts);
}
```

*Почему это работает:* Цикл создаёт отдельный PDF для каждого раздела, применяя конвертацию в inline условно, в зависимости от размера бумаги.

### Пакетное преобразование нескольких файлов DOCX

Если вам нужно **convert word to pdf** для десятков файлов, оберните логику в вспомогательный метод:

```java
public static void convertDocxToPdfInline(String inputPath, String outputPath) throws Exception {
    Document doc = new Document(inputPath);
    PdfSaveOptions options = new PdfSaveOptions();
    options.setExportFloatingShapesAsInlineTag(true);
    doc.save(outputPath, options);
}
```

Затем вы можете вызвать этот метод внутри потока `Files.list(Paths.get("batch_folder"))`.

---

## Полный рабочий пример (все шаги вместе)

Ниже представлен полный, готовый к запуску Java‑программ, демонстрирующий **how to save pdf** с встроенными объектами из файла DOCX.

```java
import com.aspose.words.*;

public class InlineShapePdfExporter {
    public static void main(String[] args) {
        try {
            // Load the source DOCX
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Set PDF options to export floating shapes as inline tags
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true);

            // Save as PDF
            doc.save("YOUR_DIRECTORY/inlineShapes.pdf", pdfOptions);

            System.out.println("PDF saved successfully with inline shapes!");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

### Ожидаемый результат

Запуск программы должен создать `inlineShapes.pdf`. Откройте его, и вы заметите, что любые плавающие текстовые поля, выноски или изображения теперь находятся **inline** с окружающим текстом, повторяя макет, который вы создали в Word.

---

## Часто задаваемые вопросы

| Вопрос | Ответ |
|----------|--------|
| **Работает ли это с файлами .doc?** | Да. Aspose.Words может загружать старые форматы `.doc`; те же `PdfSaveOptions` применимы. |
| **Могу ли я оставить некоторые объекты плавающими?** | Вам понадобится вручную изменить `WrapType` объекта на `INLINE` перед экспортом, либо выполнить второй экспорт без флага inline для этих разделов. |
| **Есть ли влияние на производительность?** | Дополнительный шаг конвертации добавляет незначительные накладные расходы — обычно несколько миллисекунд на документ. |
| **А как насчёт DOCX, защищённого паролем?** | Загрузите документ с помощью `LoadOptions`, включающих пароль, затем продолжайте как обычно. |
| **Будет ли это работать на Linux/macOS?** | Абсолютно. Aspose.Words for Java не зависит от платформы. |

---

## Следующие шаги и связанные темы

Теперь, когда вы освоили **how to export shapes** и **save docx as pdf**, рассмотрите возможность изучения:

- **Styling PDFs** – используйте `PdfSaveOptions.setCompliance(PdfCompliance.PDF_A_1_B)` для архивных PDF.  
- **Adding Watermarks** – внедрите объекты `Watermark` перед сохранением.  
- **Converting to other formats** – попробуйте `doc.save("output.html", SaveFormat.HTML)` для веб‑готового вывода.  
- **Batch processing** – объедините вспомогательный метод с планировщиком для автоматизированных конвейеров документов.  

Каждый из этих пунктов опирается на уже построенный фундамент, расширяя вашу возможность **convert word to pdf** сложными способами.

---

## Заключение

Мы рассмотрели **how to save pdf** из документа Word, гарантируя, что плавающие объекты становятся inline‑тегами, что устраняет сюрпризы в макете конечного PDF. Загрузив DOCX, настроив `PdfSaveOptions` с `setExportFloatingShapesAsInlineTag(true)` и сохранив результат, вы получаете чистую, надёжную конвертацию — идеальную для отчетов, счетов или любого автоматизированного документооборота.

Попробуйте, настройте параметры, и вы быстро поймёте, почему этот подход является предпочтительным решением для разработчиков, которым нужно **save word pdf inline** без проблем. Приятного кодинга, и пусть ваши PDF всегда выглядят точно так, как вы задумали!

## Что вам стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, которые опираются на техники, продемонстрированные в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [aspose word to pdf – Конвертация DOCX в PDF на Java](/words/english/java/document-conversion-and-export/aspose-word-to-pdf-convert-docx-to-pdf-in-java/)
- [Как конвертировать Word в PDF с помощью Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)
- [save docx as pdf с Aspose.Words – Полное руководство C#](/words/english/net/basic-conversions/save-docx-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}