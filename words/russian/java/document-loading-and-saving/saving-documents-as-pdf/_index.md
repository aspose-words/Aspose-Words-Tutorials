---
"description": "Узнайте, как сохранять документы Word в формате PDF с помощью Aspose.Words for Java. Настройте шрифты, свойства и качество изображения. Подробное руководство по конвертации PDF."
"linktitle": "Сохранение документов в формате PDF"
"second_title": "API обработки документов Java Aspose.Words"
"title": "Сохранение документов в формате PDF в Aspose.Words для Java"
"url": "/ru/java/document-loading-and-saving/saving-documents-as-pdf/"
"weight": 22
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Сохранение документов в формате PDF в Aspose.Words для Java


## Введение в сохранение документов в формате PDF в Aspose.Words для Java

В этом пошаговом руководстве мы рассмотрим, как сохранять документы в формате PDF с помощью Aspose.Words for Java. Мы рассмотрим различные аспекты преобразования PDF и предоставим примеры кода, чтобы упростить процесс.

## Предпосылки

Прежде чем начать, убедитесь, что у вас выполнены следующие предварительные условия:

- В вашей системе установлен Java Development Kit (JDK).
- Библиотека Aspose.Words for Java. Вы можете скачать ее здесь [здесь](https://releases.aspose.com/words/java/).

## Преобразование документа в PDF

Чтобы преобразовать документ Word в PDF, вы можете использовать следующий фрагмент кода:

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

Заменять `"input.docx"` с путем к вашему документу Word и `"output.pdf"` с желаемым путем к выходному PDF-файлу.

## Управление параметрами сохранения PDF-файла

Вы можете управлять различными параметрами сохранения PDF-файла с помощью `PdfSaveOptions` класс. Например, вы можете задать отображаемый заголовок для документа PDF следующим образом:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDisplayDocTitle(true);
doc.save("output.pdf", saveOptions);
```

## Встраивание шрифтов в PDF

Чтобы встроить шрифты в сгенерированный PDF-файл, используйте следующий код:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

## Настройка свойств документа

Вы можете настроить свойства документа в сгенерированном PDF. Например:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

## Экспорт структуры документа

Чтобы экспортировать структуру документа, установите `exportDocumentStructure` возможность `true`:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setExportDocumentStructure(true);
doc.save("output.pdf", saveOptions);
```

## Сжатие изображения

Вы можете управлять сжатием изображения, используя следующий код:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setImageCompression(PdfImageCompression.JPEG);
doc.save("output.pdf", saveOptions);
```

## Обновление последнего напечатанного свойства

Чтобы обновить свойство «Последняя печать» в PDF-файле, используйте:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setUpdateLastPrintedProperty(true);
doc.save("output.pdf", saveOptions);
```

## Рендеринг 3D-эффектов DML

Для расширенного рендеринга 3D-эффектов DML установите режим рендеринга:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDml3DEffectsRenderingMode(Dml3DEffectsRenderingMode.ADVANCED);
doc.save("output.pdf", saveOptions);
```

## Интерполяция изображений

Вы можете включить интерполяцию изображения для улучшения его качества:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setInterpolateImages(true);
doc.save("output.pdf", saveOptions);
```

## Заключение

Aspose.Words for Java предоставляет комплексные возможности для преобразования документов Word в формат PDF с гибкостью и возможностями настройки. Вы можете управлять различными аспектами вывода PDF, включая шрифты, свойства документа, сжатие изображений и многое другое.

## Часто задаваемые вопросы

### Как преобразовать документ Word в PDF с помощью Aspose.Words для Java?

Чтобы преобразовать документ Word в PDF, используйте следующий код:

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

Заменять `"input.docx"` с путем к вашему документу Word и `"output.pdf"` с желаемым путем к выходному PDF-файлу.

### Можно ли встраивать шрифты в PDF-файл, созданный Aspose.Words для Java?

Да, вы можете встроить шрифты в PDF-файл, установив `setEmbedFullFonts` возможность `true` в `PdfSaveOptions`. Вот пример:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

### Как настроить свойства документа в созданном PDF-файле?

Вы можете настроить свойства документа в PDF с помощью `setCustomPropertiesExport` вариант в `PdfSaveOptions`. Например:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

### Какова цель сжатия изображений в Aspose.Words для Java?

Сжатие изображений позволяет контролировать качество и размер изображений в сгенерированном PDF-файле. Вы можете задать режим сжатия изображений с помощью `setImageCompression` в `PdfSaveOptions`.

### Как обновить свойство «Последняя печать» в PDF-файле?

Вы можете обновить свойство «Последняя печать» в PDF-файле, установив `setUpdateLastPrintedProperty` к `true` в `PdfSaveOptions`. Это отразит последнюю напечатанную дату в метаданных PDF.

### Как улучшить качество изображения при конвертации в PDF?

Чтобы улучшить качество изображения, включите интерполяцию изображения, установив `setInterpolateImages` к `true` в `PdfSaveOptions`. Это приведет к более гладким и качественным изображениям в PDF-файле.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}