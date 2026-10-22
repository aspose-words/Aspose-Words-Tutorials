---
category: general
date: 2026-10-16
description: Создайте пустой документ Word, вставьте форму, добавьте внешнюю тень
  и сохраните как PDF с помощью Python.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert shape in word
- save as pdf python
- add outer shadow shape
- create pdf with shape
language: ru
lastmod: 2026-10-16
og_description: Создайте пустой документ Word с фигурой внешней тени, используя Aspose.Words
  для Python. Это руководство показывает, как вставить фигуру, применить тень и сохранить
  файл в формате PDF.
og_image_alt: Screenshot of a Word document containing a rectangle shape with an outer
  shadow, saved as PDF
og_title: Создайте пустой документ Word с теневой фигурой – руководство по Python
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document, insert shape in Word, add outer shadow,
    and save as PDF using Python.
  headline: Create blank Word document with shadowed shape in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- PDF generation
- Shape styling
title: Создать пустой документ Word с фигурой с тенью в Python
url: /ru/python/word-automation/create-blank-word-document-with-shadowed-shape-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создать пустой документ Word с фигурой в тени на Python

Если вам нужно **создать пустой документ Word** и добавить пользовательскую графику, это руководство вам поможет. Мы пройдёмся по тому, как **вставить фигуру в Word**, применить **внешнюю тень к фигуре** и, наконец, **сохранить как PDF с помощью Python**.

Вы узнаете, как настроить Aspose.Words for Python, построить прямоугольник, оформить его тень и сгенерировать PDF, сохраняющий визуальный эффект. Предыдущий опыт работы с API Aspose не требуется, но необходимо базовое знание Python и установленный Python 3.10 или новее.

## Требования

Прежде чем начать, убедитесь, что у вас есть:

* Установленный Python 3.10 или новее.  
* Действующая лицензия Aspose.Words for Python (для оценки подойдёт бесплатная пробная версия).  
* Доступ к `pip` для установки пакета `aspose-words`.  
* Права на запись в каталог, где будет сохранён PDF.

Библиотеку можно установить одной командой:

```bash
pip install aspose-words
```

## Создание пустого документа Word – настройка окружения

Первый шаг – создать пустой файл Word, который будет служить холстом для фигуры.

```python
import aspose.words as aw

# Initialize a new, empty document
doc = aw.Document()
# DocumentBuilder provides convenient methods for adding content
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` представляет полностью пустой файл Word. С помощью `DocumentBuilder` вы получаете доступ к методам, таким как `insert_shape`, которые будем использовать в следующем шаге.

## Вставка фигуры в Word и задание размеров

Теперь добавим прямоугольник, которому позже будет присвоена внешняя тень. Размер задаётся в пунктах (1 pt ≈ 1/72 дюйма).

```python
# Insert a rectangle shape with a width of 200 pt and a height of 100 pt
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)
```

Вызов `insert_shape` возвращает объект `Shape`, который можно дальше настраивать. На этом этапе документ уже содержит видимый прямоугольник при открытии в Microsoft Word.

## Добавление внешней тени – настройка эффекта

Aspose.Words предоставляет класс `ShadowEffect` для определения свойств тени, таких как стиль, размытие, расстояние и цвет.

```python
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a new shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # Choose an outer shadow
shadow.blur = 5.0                         # Softness of the shadow edges
shadow.distance = 3.0                     # Offset distance from the shape
shadow.color = aw.Color.black             # Shadow color

# Apply the shadow to the rectangle
rectangle.shadow = shadow
```

Установка `style` в `OUTER` гарантирует, что тень будет отображаться за границей прямоугольника, придавая лёгкий 3‑D‑вид. Вы можете экспериментировать с параметрами `blur` и `distance`, чтобы получить более плотную или более рассеянную тень.

## Сохранение как PDF python – финализация документа

После стилизации фигуры документ можно сразу сохранить как PDF. Aspose.Words выполняет конвертацию внутри, сохраняя эффект тени.

```python
output_path = "output/shape_with_shadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

При открытии `shape_with_shadow.pdf` в любом PDF‑просмотрщике вы увидите прямоугольник с внешней тенью точно так же, как он выглядел в Word.

## Полный рабочий пример

Ниже представлен полный скрипт, объединяющий все шаги. Сохраните его в файл `create_word_with_shadow.py` и запустите.

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1. Create a blank Word document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2. Insert a rectangle shape
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)

# 3. Define and apply an outer shadow
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER
shadow.blur = 5.0
shadow.distance = 3.0
shadow.color = aw.Color.black
rectangle.shadow = shadow

# 4. Save the document as PDF
pdf_path = os.path.join(output_dir, "shape_with_shadow.pdf")
doc.save(pdf_path)

print(f"PDF generated at: {pdf_path}")
```

**Ожидаемый вывод**

Запуск скрипта выводит строку подтверждения, например:

```
PDF generated at: output/shape_with_shadow.pdf
```

Открытие полученного PDF показывает одну страницу с прямоугольником 200 pt × 100 pt и мягкой чёрной внешней тенью.

## Распространённые варианты и граничные случаи

* **Изменение цвета тени** – замените `aw.Color.black` на любой другой `aw.Color`, например `aw.Color.red` или `aw.Color.from_argb(255, 0, 120, 215)`.  
* **Использование другой фигуры** – замените `aw.drawing.ShapeType.RECTANGLE` на `OVAL`, `DIAMOND` или любой поддерживаемый enum.  
* **Сохранение как DOCX вместо PDF** – вызовите `doc.save("output/shape.docx")`, чтобы оставить формат Word.  
* **Несколько фигур** – создавайте дополнительные фигуры, вызывая `builder.insert_shape` повторно; у каждой фигуры может быть собственный `ShadowEffect`.

**Совет:** Если нужно разместить фигуру в определённом месте, задайте `rectangle.left` и `rectangle.top` после вставки. Это даст вам пиксель‑точный контроль над позиционированием.

## Заключение

Теперь вы знаете, как **создать пустой документ Word**, **вставить фигуру в Word**, **добавить внешнюю тень к фигуре** и **сохранить как PDF с помощью Python**. Полный пример кода демонстрирует сквозной процесс, а пояснения объясняют, зачем нужен каждый вызов API.

Дальше вы можете исследовать более продвинутые варианты стилизации, добавить текст внутри фигуры или комбинировать несколько фигур для построения сложных диаграмм. Экспериментируйте с параметрами тени, чтобы они соответствовали визуальному стилю вашего бренда, и интегрируйте этот подход в более крупные конвейеры генерации документов.

Удачной разработки!

## Что изучать дальше?

Следующие учебные материалы охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и изучить альтернативные подходы в собственных проектах.

- [Создать прямоугольную фигуру, добавить тень и сохранить PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Создать PDF из Word – Полное руководство по Python с Aspose.Words](/words/english/python-net/document-conversion/create-pdf-from-word-complete-python-guide-with-aspose-words/)
- [Добавить тень к фигуре в Word с Aspose.Words – Пошагово](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}