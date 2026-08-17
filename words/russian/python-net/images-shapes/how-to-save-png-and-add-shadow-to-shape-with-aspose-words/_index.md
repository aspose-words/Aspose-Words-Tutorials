---
category: general
date: 2026-08-17
description: Как сохранить PNG с помощью Aspose.Words для Python. Узнайте, как добавить
  тень к фигуре, сохранить документ в PDF и экспортировать Word в PNG в одном руководстве.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save png
- add shadow to shape
- save document as pdf
- export word to png
- convert word to pdf
language: ru
lastmod: 2026-08-17
og_description: Как сохранить PNG с помощью Aspose.Words. В этом руководстве показано,
  как добавить тень к фигуре, сохранить документ в PDF и экспортировать Word в PNG.
og_image_alt: Screenshot of a Word document with a rectangle shape that has a shadow,
  saved as PNG and PDF
og_title: Как сохранить PNG и добавить тень к фигуре с помощью Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  headline: How to save PNG and add shadow to shape with Aspose.Words
  type: TechArticle
- description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  name: How to save PNG and add shadow to shape with Aspose.Words
  steps:
  - name: Pro tip
    text: If you need a sharper shadow, reduce `blur`. For a more pronounced offset,
      increase `distance`. The `Shadow` class also exposes `angle` and `transparency`
      for fine‑tuned control.
  - name: 'Optional: higher‑resolution PNG'
    text: '```python png_options = aw.image.PngSaveOptions() png_options.resolution
      = 300 # DPI doc.save("output/high_res_output.png", png_options) ```'
  - name: Expected output
    text: 'Running the script creates three files:'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Image export
title: Как сохранить PNG и добавить тень к фигуре с помощью Aspose.Words
url: /ru/python/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как сохранить PNG и добавить тень к фигуре с Aspose.Words

Если вам нужно **how to save PNG** из файла Word, это руководство предоставляет полное, готовое к запуску решение. Вы также увидите, как **add shadow to shape**, **save document as PDF**, и **export Word to PNG** без выхода из среды Aspose.Words.

В этом руководстве описано всё, что необходимо, чтобы превратить пустой документ Word в PDF и PNG‑изображение, одновременно применив простой эффект тени к прямоугольной фигуре. Внешние инструменты не требуются, а код работает с Aspose.Words for Python via .NET 7 или более новой версией.

## Что вы достигнете

* Создать новый документ Word программно.  
* Вставить прямоугольную фигуру и настроить эффект тени.  
* Сохранить тот же документ в виде PDF‑файла.  
* Экспортировать документ в PNG‑изображение.  

Эти шаги отвечают на часто задаваемый вопрос **how to save PNG**, одновременно решая задачи **add shadow to shape** и **save document as PDF** в одном рабочем процессе.

## Требования

* Python 3.9 или новее.  
* Aspose.Words for Python via .NET установлен (`pip install aspose-words`).  
* Разрешение на запись в указанный вами каталог вывода.  

Если вы ещё не установили Aspose.Words, выполните:

```bash
pip install aspose-words
```

## Как сохранить PNG с помощью Aspose.Words

Первый важный шаг — создать документ и `DocumentBuilder`. Builder предоставляет удобный API для вставки содержимого, такого как фигуры, таблицы или текст.

```python
import aspose.words as aw

# Create a new blank document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` представляет весь файл Word в памяти. `aw.DocumentBuilder` указывает текущую позицию вставки, которая изначально находится в начале первой (и единственной) секции.

## Добавление тени к фигуре перед экспортом

Фигура может быть любым графическим объектом — прямоугольником, эллипсом или пользовательским многоугольником. Здесь мы создаём прямоугольник размером 100 × 100 point и применяем мягкую тень.

```python
# Insert a rectangle shape (100x100 points)
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

# Configure a simple shadow
shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Softness of the shadow edges
shape.shadow.distance = 3.0      # Distance from the shape
shape.shadow.color = aw.Color.black
```

Почему тень настраивается до сохранения? Aspose.Words рендерит тень во время экспорта в PDF и PNG, поэтому визуальный эффект сохраняется в обоих форматах вывода.

### Профессиональный совет
Если нужна более резкая тень, уменьшите `blur`. Для более заметного смещения увеличьте `distance`. Класс `Shadow` также предоставляет свойства `angle` и `transparency` для точной настройки.

## Сохранить документ как PDF

Сохранить документ Word как PDF можно одной строкой, когда содержимое готово. Константа `SaveFormat.PDF` указывает Aspose.Words выполнить конвертацию.

```python
# Save the document as PDF (shadow is rendered in the output)
pdf_path = "output/output.pdf"
doc.save(pdf_path, aw.SaveFormat.PDF)
```

Полученный PDF содержит прямоугольник с точно такой же тенью, как вы задали. Aspose.Words работает с векторной графикой, поэтому размер PDF остаётся умеренным.

## Экспортировать Word в PNG

Экспорт в PNG создаёт растровое изображение каждой страницы. По умолчанию Aspose.Words использует 96 DPI; вы можете увеличить это значение для вывода более высокого разрешения, передав объект `PngSaveOptions`.

```python
# Export the same document as PNG
png_path = "output/output.png"
doc.save(png_path, aw.SaveFormat.PNG)
```

Когда вы **export Word to PNG**, каждая страница сохраняется в отдельный PNG‑файл. Поскольку наш примерный документ содержит только одну страницу, появляется лишь один PNG‑файл.

### Необязательно: PNG с более высоким разрешением

```python
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI
doc.save("output/high_res_output.png", png_options)
```

Большее DPI полезно, когда PNG будет использоваться для печати или когда требуется чёткая миниатюра.

## Полный скрипт — скопировать, вставить и запустить

Ниже приведён полный, автономный скрипт, реализующий каждый описанный выше шаг. Сохраните его как `generate_assets.py` и запустите из командной строки.

```python
import os
import aspose.words as aw

# ------------------------------------------------------------------
# 1. Prepare output folder
# ------------------------------------------------------------------
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# ------------------------------------------------------------------
# 2. Create a new blank document and a builder
# ------------------------------------------------------------------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ------------------------------------------------------------------
# 3. Insert a rectangle shape and add a shadow
# ------------------------------------------------------------------
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Soft edges
shape.shadow.distance = 3.0      # Offset from shape
shape.shadow.color = aw.Color.black

# ------------------------------------------------------------------
# 4. Save as PDF (demonstrates "save document as pdf")
# ------------------------------------------------------------------
pdf_path = os.path.join(output_dir, "output.pdf")
doc.save(pdf_path, aw.SaveFormat.PDF)

# ------------------------------------------------------------------
# 5. Export as PNG (demonstrates "how to save png")
# ------------------------------------------------------------------
png_path = os.path.join(output_dir, "output.png")
doc.save(png_path, aw.SaveFormat.PNG)

# ------------------------------------------------------------------
# 6. Optional high‑resolution PNG (demonstrates "export word to png")
# ------------------------------------------------------------------
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI for sharper output
high_res_png_path = os.path.join(output_dir, "high_res_output.png")
doc.save(high_res_png_path, png_options)

print(f"Files written to {os.path.abspath(output_dir)}")
```

### Ожидаемый результат

Запуск скрипта создаёт три файла:

* `output/output.pdf` — PDF с прямоугольником, отбрасывающим чёрную тень.  
* `output/output.png` — PNG‑изображение той же страницы с разрешением 96 DPI.  
* `output/high_res_output.png` — PNG с разрешением 300 DPI для более высокого качества.  

Откройте любой из файлов в предпочитаемом просмотрщике, чтобы убедиться, что тень отображается точно так, как задано.

## Часто задаваемые вопросы и особые случаи

**Что делать, если каталог вывода не существует?**  
Скрипт вызывает `os.makedirs(output_dir, exist_ok=True)`, что автоматически создаёт папку. Это предотвращает `FileNotFoundError` во время операций сохранения.

**Могу ли я добавить несколько фигур с разными тенями?**  
Да. Создайте дополнительные объекты `Shape`, независимо настройте свойство `shadow` для каждого и вставьте их с помощью `builder.insert_node(shape)` перед сохранением.

**Сохранится ли тень при конвертации в другие растровые форматы (например, JPEG)?**  
Aspose.Words рендерит тень для всех растровых форматов, поддерживаемых `SaveFormat`. Вы можете заменить `aw.SaveFormat.PNG` на `aw.SaveFormat.JPEG`, и тень всё равно будет отображаться.

**Чем это отличается от “convert word to pdf”?**  
`convert word to pdf` по сути является той же операцией, выполненной на шаге 4. Вызов `doc.save` с `SaveFormat.PDF` обрабатывает конвертацию внутри, сохраняя макет, шрифты и графику, включая тени.

**Есть ли ограничение на размер фигуры?**  
Размеры фигур измеряются в пунктах (1 pt ≈ 1/72 дюйма). Очень большие размеры могут увеличить размер получаемого файла, но Aspose.Words не накладывает жёстких ограничений. Регулируйте аргументы `width` и `height` при создании `aw.Shape` в соответствии с вашим макетом.

## Заключение

Теперь вы знаете, как **how to save PNG** из документа Word, а также как **add shadow to shape**, **save document as PDF** и **export Word to PNG** с помощью Aspose.Words for Python. Полный скрипт демонстрирует чистый, повторяемый шаблон, который можно адаптировать для более крупных документов, нескольких страниц или более сложных графических эффектов.

Дальнейшие шаги могут включать:

* Эксперименты с другими значениями `ShapeType` (ellipse, cloud и т.д.).  
* Using `

## Что вам стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, основанные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [How to Convert DOCX to PNG in Java – Aspose.Words](/words/english/java/document-converting/converting-documents-images/)
- [Save Word Documents as PostScript in Python Using Aspose.Words: A Comprehensive Guide](/words/english/python-net/document-operations/save-docs-as-postscript-using-aspose-words-python/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}