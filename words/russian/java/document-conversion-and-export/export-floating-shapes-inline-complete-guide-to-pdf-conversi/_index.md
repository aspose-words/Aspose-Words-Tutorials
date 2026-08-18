---
category: general
date: 2026-07-03
description: Экспортировать плавающие объекты как встроенные при конвертации Word
  в PDF. Узнайте, как задавать параметры PDF и сохранять Word в PDF с помощью Java.
draft: false
keywords:
- export floating shapes inline
- convert word to pdf inline
- how to set pdf options
- save word as pdf options
language: ru
og_description: Экспортировать плавающие объекты как встроенные при конвертации документа
  Word в PDF. Этот учебник показывает, как настроить параметры PDF и параметры сохранения
  Word в PDF.
og_title: Экспорт плавающих фигур в строке – Руководство по конвертации PDF на Java
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  headline: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  type: TechArticle
- description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  name: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  steps:
  - name: 1. “What if my document contains complex SmartArt?”
    text: SmartArt is treated as a drawing object. The inline flag works for most
      vector shapes, but very intricate SmartArt may still be rendered as an image.
      In those cases, consider flattening the SmartArt in Word before conversion,
      or use `pdfOptions.setExportSmartArtAsImage(true)` to force image export.
  - name: 2. “Can I combine inline and block exports in the same document?”
    text: Unfortunately the API applies the setting globally. If you need mixed behavior,
      split the document into sections, export each section separately with different
      options, then merge the PDFs using `PdfMerger`.
  - name: 3. “Does this affect font embedding?”
    text: No. Font embedding is controlled by `pdfOptions.setEmbedFullFonts(true)`
      (default). You can safely enable or disable it without touching the inline shape
      flag.
  - name: 4. “How do I verify that shapes are really `<span>`?”
    text: Open the resulting PDF in a tool like **PDF.js** or **Adobe Acrobat** →
      **Edit PDF** → **Object Inspector**. You’ll see the shape wrapped in a `<span>`
      element in the underlying XML. If you see `<div>`, the option wasn’t applied.
  type: HowTo
tags:
- Java
- PDF
- Aspose.Words
title: Экспорт плавающих фигур в строке — Полное руководство по конвертации в PDF
url: /ru/java/document-conversion-and-export/export-floating-shapes-inline-complete-guide-to-pdf-conversi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Экспорт плавающих фигур в строку – Полное руководство по конвертации в PDF

Когда‑то вам нужно **экспортировать плавающие фигуры в строку** при конвертации документа Word в PDF? Вы не одиноки — многие разработчики сталкиваются с этой проблемой, когда их диаграммы или значки неожиданно перемещаются в отдельные слои. Хорошая новость в том, что одна настройка PDF может удержать эти фигуры внутри тегов `<span>`, сохраняя макет точно таким, каким он выглядит в Word.

В этом руководстве мы пройдемся по **настройке параметров PDF** в Java, покажем точный код для **сохранения Word как PDF с параметрами**, и объясним, почему может потребоваться **конвертировать Word в PDF в строке** вместо экспорта по умолчанию на уровне блока. К концу вы получите готовый фрагмент кода, который можно вставить в любой проект Maven или Gradle.

## Что вы узнаете

- Разницу между экспортом в строку `<span>` и блоком `<div>` для плавающих фигур.  
- Как настроить `PdfSaveOptions`, чтобы принудительно использовать строковый рендеринг.  
- Пошаговый код, который загружает `.docx`, применяет параметр и записывает PDF.  
- Распространённые подводные камни (отсутствующие шрифты, неподдерживаемые фигуры) и как их избежать.  
- Советы по тестированию результата и расширению подхода на другие элементы документа.

**Prerequisites** – вам понадобится Java 8 или новее, библиотека Aspose.Words for Java (или любой API, реализующий класс `PdfSaveOptions`), а также пример файла Word с плавающими фигурами (в руководстве используется `FloatingShapes.docx`). Другие внешние инструменты не требуются.

---

## Шаг 1: Загрузка исходного документа Word

Первое, что нужно сделать — открыть `.docx`, который вы собираетесь преобразовать. Это просто, но убедитесь, что путь абсолютный или правильно разрешён из вашего classpath.

```java
import com.aspose.words.Document;

// Step 1: Load the source Word document
Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");
```

*Почему это важно:*  
Если документ не загрузится корректно, последующая конвертация в PDF вызовет `FileNotFoundException`. Использование `Document` гарантирует, что внутренняя модель объекта полностью заполнена, включая любые плавающие фигуры, находящиеся на странице.

---

## Шаг 2: Создание параметров сохранения PDF и установка плавающих фигур в строку

Здесь происходит магия. По умолчанию Aspose.Words экспортирует плавающие фигуры как блок‑уровневые элементы `<div>`, что может нарушить поток в HTML‑основанных PDF. Вызов `setExportFloatingShapesAsInlineTag(true)` заставляет движок оборачивать каждую фигуру в строковый тег `<span>`.

```java
import com.aspose.words.PdfSaveOptions;

// Step 2: Create PDF save options and set floating shapes to be exported as inline <span> elements
PdfSaveOptions pdfOptions = new PdfSaveOptions();
pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → <span>, false → <div>
```

*Почему это важно:*  
- **Точность макета** — строковые теги удерживают фигуру выровненной с окружающим текстом, избегая нежелательных пробелов.  
- **Поисковая индексация** — строковые элементы с большей вероятностью будут правильно проиндексированы PDF‑читалками.  
- **Контроль стилей** — вы можете нацеливаться на `<span>` с помощью CSS, если позже конвертируете PDF обратно в HTML.

> **Pro tip:** Если когда‑нибудь понадобится старое блочное поведение для конкретного документа, просто передайте `false` или полностью опустите вызов.

---

## Шаг 3: Сохранение документа как PDF с использованием настроенных параметров

Теперь вы объединяете загруженный `Document` с `PdfSaveOptions` и записываете файл. Эта одна строка делает всю тяжёлую работу.

```java
// Step 3: Save the document as a PDF using the configured options
doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);
```

*Почему это важно:*  
Метод `save` учитывает каждый флаг, установленный в `pdfOptions`. Если не передать параметры, будет использован экспорт блоков по умолчанию, и цель **export floating shapes inline** будет потеряна.

---

## Полный рабочий пример

Собрав всё вместе, получаем компактную программу, которую можно сразу скомпилировать и запустить. Замените `YOUR_DIRECTORY` реальным путём на вашей машине.

```java
import com.aspose.words.*;

public class ExportFloatingShapesInlineDemo {
    public static void main(String[] args) {
        try {
            // Load the source Word document
            Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");

            // Configure PDF options to export floating shapes as inline <span>
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true);

            // Save as PDF with the above options
            doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);

            System.out.println("PDF created successfully with inline floating shapes.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Ожидаемый результат** — после запуска программы откройте `FloatingShapes.pdf`. Вы увидите, что фигуры находятся вплотную к тексту, без лишних пробелов, а HTML‑представление (если вы исследуете внутреннюю структуру PDF) будет содержать теги `<span>` вокруг каждой фигуры.

![Export floating shapes inline example](https://example.com/export-inline.png "Скриншот, показывающий плавающие фигуры, отрисованные в строке в PDF")

*Текст альтернативного изображения:* **export floating shapes inline** скриншот PDF с фигурами в строке.

---

## Часто задаваемые вопросы и особые случаи

### 1. “Что если мой документ содержит сложный SmartArt?”

SmartArt рассматривается как объект рисунка. Флаг inline работает для большинства векторных фигур, но очень сложный SmartArt может всё равно быть отрисован как изображение. В таких случаях рекомендуется «упростить» SmartArt в Word перед конвертацией или использовать `pdfOptions.setExportSmartArtAsImage(true)`, чтобы принудительно экспортировать его как изображение.

### 2. “Можно ли комбинировать экспорт в строку и в блок в одном документе?”

К сожалению, API применяет настройку глобально. Если нужен смешанный режим, разбейте документ на секции, экспортируйте каждую секцию отдельно с разными параметрами, а затем объедините PDF‑файлы с помощью `PdfMerger`.

### 3. “Влияет ли это на встраивание шрифтов?”

Нет. Встраивание шрифтов контролируется `pdfOptions.setEmbedFullFonts(true)` (по умолчанию). Вы можете безопасно включать или отключать его, не затрагивая флаг inline‑фигур.

### 4. “Как проверить, что фигуры действительно находятся в `<span>`?”

Откройте полученный PDF в таком инструменте, как **PDF.js** или **Adobe Acrobat** → **Edit PDF** → **Object Inspector**. Вы увидите, что фигура обёрнута в элемент `<span>` во внутреннем XML. Если видите `<div>`, параметр не был применён.

---

## Расширение подхода – связанные параметры

Поскольку вы уже здесь, возможно, захотите изучить и другие «ручки» конвертации PDF:

| Параметр | Что делает | Типичный сценарий |
|----------|------------|-------------------|
| `setCompressImages(true)` | Уменьшает размер изображений | Быстрая загрузка |
| `setUseHighQualityRendering(true)` | Улучшает рендеринг векторов | PDF для печати |
| `setExportDocumentStructure(true)` | Добавляет структурные теги для доступности | Соответствие WCAG |
| `setSaveFormat(SaveFormat.PDF)` | Явно задаёт формат (редко требуется) | Многоформатные конвейеры |

Эти настройки хорошо сочетаются с сценариями **convert word to pdf inline**, где важны как точность макета, так и производительность.

---

## Тестирование вашей конверсии

1. **Визуальная проверка** — откройте PDF в двух просмотрщиках (Chrome и Adobe Reader), чтобы убедиться, что фигуры выровнены.  
2. **Автоматический дифф** — используйте библиотеку, например `pdfbox`, чтобы извлечь XML и убедиться в наличии тегов `<span>`.  
3. **Бенчмарк производительности** — измерьте время с и без `setCompressImages`, чтобы увидеть компромисс.

Пример JUnit‑теста:

```java
@Test
public void testInlineExport() throws Exception {
    Document doc = new Document("src/test/resources/FloatingShapes.docx");
    PdfSaveOptions opts = new PdfSaveOptions();
    opts.setExportFloatingShapesAsInlineTag(true);
    ByteArrayOutputStream out = new ByteArrayOutputStream();
    doc.save(out, opts);
    String pdfXml = new String(out.toByteArray(), StandardCharsets.UTF_8);
    assertTrue(pdfXml.contains("<span"));
}
```

---

## Заключение

Теперь у вас есть надёжное сквозное решение для **export floating shapes inline** при **convert Word to PDF inline**. Настраивая `PdfSaveOptions`, вы контролируете, какой HTML‑тег будет использоваться для каждой фигуры, делая PDF‑файлы аккуратными и удобными для поиска. Не забывайте проверять результат, подстраивать сопутствующие параметры, такие как сжатие изображений, и учитывать особые случаи, например сложный SmartArt.

Готовы к следующему шагу? Попробуйте применить тот же приём к **export floating tables inline** или поэкспериментируйте с PDF, стилизованными через CSS, используя `HtmlSaveOptions` от Aspose. Тот же шаблон — загрузить, настроить, сохранить — подходит почти для любого сценария «документ‑в‑PDF».

Есть вопросы о **how to set pdf options** или нужна помощь с **save word as pdf options** для другой библиотеки? Оставляйте комментарий, и happy coding!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, развивая техники, продемонстрированные в этом гиде. Каждый ресурс содержит полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Convert Word to PDF with Aspose.Words for Java](/words/english/java/document-converting/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Export Word Document Structure to PDF Document](/words/english/net/programming-with-pdfsaveoptions/export-document-structure/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}