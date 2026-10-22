---
category: general
date: 2026-08-17
description: Сохраните документ как изображение и экспортируйте все страницы в PNG
  с помощью Aspose.Words для Python. Узнайте, как преобразовать DOCX в PNG одной командой.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save document as image
- convert docx to png
- export docx to png
- export all pages png
- export word pages image
language: ru
lastmod: 2026-08-17
og_description: Сохраните документ как изображение и экспортируйте все страницы в
  PNG с помощью Aspose.Words для Python. Это руководство показывает, как эффективно
  преобразовать DOCX в PNG.
og_image_alt: Diagram showing a multi‑page Word document converted into a single PNG
  grid preview
og_title: Сохранить документ как изображение и конвертировать DOCX в PNG в Python
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: Save document as image and export all pages PNG using Aspose.Words
    for Python. Learn to convert DOCX to PNG with a single command.
  headline: 'Save document as image: convert DOCX to PNG in Python'
  type: TechArticle
- description: Save document as image and export all pages PNG using Aspose.Words
    for Python. Learn to convert DOCX to PNG with a single command.
  name: 'Save document as image: convert DOCX to PNG in Python'
  steps:
  - name: '**Save format** – PNG is lossless and widely supported.'
    text: '**Save format** – PNG is lossless and widely supported.'
  - name: '**Page set** – defines the range of pages to export; using `0, document.page_count`
      captures every page.'
    text: '**Page set** – defines the range of pages to export; using `0, document.page_count`
      captures every page.'
  - name: '**Layout** – `GRID` arranges all exported pages into a single image, which
      is ideal for preview scenarios.'
    text: '**Layout** – `GRID` arranges all exported pages into a single image, which
      is ideal for preview scenarios.'
  type: HowTo
tags:
- Aspose.Words
- Python
- DOCX
title: 'Сохранить документ как изображение: конвертировать DOCX в PNG в Python'
url: /ru/python/document-conversion/save-document-as-image-convert-docx-to-png-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Сохранить документ как изображение: конвертация DOCX в PNG в Python

Если вам нужно **сохранить документ как изображение** и создать единственный превью для многостраничного файла Word, это руководство покажет, как сделать это с помощью Aspose.Words for Python. Вы также узнаете, как **конвертировать DOCX в PNG** одной простой операцией.

Экспорт каждой страницы Word‑документа в PNG может быть утомительным, если писать цикл вручную. Aspose.Words предоставляет встроенные возможности, позволяющие **экспортировать все страницы PNG** одним вызовом, при этом давая контроль над макетом, разрешением и диапазоном страниц. К концу этого урока у вас будет готовый к запуску скрипт, который создаст PNG‑изображение в виде сетки, содержащей все страницы исходного документа.

## Требования

Прежде чем начать, убедитесь, что у вас есть:

* Python 3.8 или новее.
* Пакет `aspose-words` (`pip install aspose-words`).
* Файл Word (`.docx`) с минимум двумя страницами.
* Права записи в каталог, куда вы хотите сохранить полученный PNG.

Дополнительные внешние инструменты не требуются; Aspose.Words полностью обрабатывает конвертацию в памяти.

## Шаг 1: Загрузка Word‑документа

Первый шаг — создать объект `aw.Document`, представляющий исходный DOCX‑файл. Этот объект дает доступ ко всем страницам, разделам и ресурсам внутри документа.

```python
import aspose.words as aw

# Load the multi‑page Word document
doc_path = "YOUR_DIRECTORY/multi_page.docx"
document = aw.Document(doc_path)
```

*Почему это важно*: Загрузка документа один раз предоставляет полную объектную модель, которую Aspose.Words позже может отрисовать в любой поддерживаемый формат изображения. Класс `aw.Document` также проверяет файл, поэтому вы получаете раннее уведомление, если DOCX повреждён.

## Шаг 2: Создание параметров сохранения PNG и их настройка

Aspose.Words использует `ImageSaveOptions` для управления процессом растеризации документа. На этом этапе мы задаём три важных свойства:

1. **Формат сохранения** – PNG без потерь и широко поддерживается.
2. **Набор страниц** – определяет диапазон страниц для экспорта; использование `0, document.page_count` захватывает каждую страницу.
3. **Макет** – `GRID` размещает все экспортированные страницы в одном изображении, что идеально подходит для превью.

```python
# Configure PNG export options
png_options = aw.saving.ImageSaveOptions(aw.SaveFormat.PNG)

# Export all pages (page index starts at 0)
png_options.page_set = aw.saving.PageSet(0, document.page_count)

# Arrange pages in a grid layout (rows × columns are auto‑calculated)
png_options.layout = aw.saving.ImageSaveOptions.PageLayout.GRID

# Optional: increase resolution for sharper output (default is 96 DPI)
png_options.resolution = 150  # DPI
```

*Почему это важно*: Установка `page_set` на полный диапазон позволяет **экспортировать docx в png** без ручного перебора страниц. Макет `GRID` создаёт одно изображение, содержащее все страницы рядом, удовлетворяя требование **export word pages image** в компактной форме. Регулировка `resolution` помогает, когда исходный документ содержит мелкие детали.

## Шаг 3: Сохранение документа как единого PNG‑превью

После подготовки параметров сохранение сводится к одной строке кода. Aspose.Words записывает PNG‑файл на диск, используя указанные настройки.

```python
# Destination path for the combined PNG image
output_path = "YOUR_DIRECTORY/preview.png"

# Perform the export – this creates one PNG that contains all pages
document.save(output_path, png_options)
print(f"Document successfully saved as image: {output_path}")
```

**Ожидаемый результат**

Запуск скрипта создаёт `preview.png`. Если исходный DOCX имел три страницы, PNG покажет эти три страницы, размещённые в сетке (например, 2 × 2, при этом последняя ячейка будет пустой). Открытие файла в любом просмотрщике изображений подтверждает, что каждая страница была правильно растеризована.

### Профессиональный совет

Если нужны только отдельные страницы, измените аргументы `PageSet`, например:

```python
# Export pages 2‑4 only (zero‑based index)
png_options.page_set = aw.saving.PageSet(1, 4)
```

Это всё равно сохраняет логику **export all pages png** для выбранного диапазона, уменьшая потребление памяти при работе с очень большими документами.

## Работа с большими документами и ограничениями памяти

При работе с документами, содержащими десятки или сотни страниц, полученный PNG может стать очень большим. Рассмотрите следующие стратегии:

* **Увеличивайте `resolution` только при необходимости** – более высокое DPI приводит к большим файлам.
* **Используйте `PageLayout.SINGLE_COLUMN`** – создаёт вертикальную полосу вместо сетки, что может быть удобнее для прокрутки.
* **Потоковая передача вывода** – Aspose.Words также поддерживает сохранение в поток `BytesIO`, если нужно отправить изображение по сети без записи на диск.

```python
import io

stream = io.BytesIO()
document.save(stream, png_options)
# Now `stream.getvalue()` holds the PNG bytes
```

## Полный скрипт для быстрого копирования‑вставки

Ниже приведён полностью готовый пример, включающий все описанные шаги. Замените `YOUR_DIRECTORY` реальным путём к папке на вашем компьютере.

```python
import aspose.words as aw

# ----------------------------------------------------------------------
# 1. Load the source DOCX file
# ----------------------------------------------------------------------
doc_path = "YOUR_DIRECTORY/multi_page.docx"
document = aw.Document(doc_path)

# ----------------------------------------------------------------------
# 2. Configure PNG export options (save document as image)
# ----------------------------------------------------------------------
png_options = aw.saving.ImageSaveOptions(aw.SaveFormat.PNG)

# Export every page (export docx to png)
png_options.page_set = aw.saving.PageSet(0, document.page_count)

# Arrange pages in a grid (export word pages image)
png_options.layout = aw.saving.ImageSaveOptions.PageLayout.GRID

# Optional: higher DPI for sharper output
png_options.resolution = 150

# ----------------------------------------------------------------------
# 3. Save the combined PNG file
# ----------------------------------------------------------------------
output_path = "YOUR_DIRECTORY/preview.png"
document.save(output_path, png_options)

print(f"Document successfully saved as image: {output_path}")
```

Запуск этого скрипта создаёт один PNG, содержащий все страницы `multi_page.docx`. Подход работает с любым DOCX‑файлом, независимо от сложности содержимого (таблицы, изображения, сложные макеты).

## Заключение

Теперь вы знаете, как **сохранить документ как изображение**, **конвертировать DOCX в PNG** и **экспортировать все страницы PNG** с помощью Aspose.Words for Python. Используя `ImageSaveOptions`, вы избегаете ручных циклов, получаете превью в виде сетки и сохраняете контроль над разрешением и макетом.  

Дальше вы можете изучить:

* Экспорт в другие растровые форматы (JPEG, BMP) – просто измените `SaveFormat`.
* Добавление водяных знаков или аннотаций перед экспортом – манипулируйте объектом `Document`.
* Интеграцию этого скрипта в веб‑службу для генерации превью «на лету».

Экспериментируйте с различными значениями `layout` и `resolution`, чтобы найти оптимальный баланс между производительностью и качеством для вашего приложения. Приятного кодинга!

## Что изучать дальше?


Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом пособии. Каждый ресурс содержит полностью работающие примеры кода с пошаговыми объяснениями, помогающие освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Optimize RTF Image Handling in Python using Aspose.Words API: Save as WMF and Ensure Compatibility](/words/english/python-net/images-shapes/optimize-rtf-image-handling-aspose-words-python/)
- [Convert DOCX to Fixed-Form XAML in Python Using Aspose.Words: A Comprehensive Guide](/words/english/python-net/document-operations/python-docx-to-xaml-aspose-tutorial/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}