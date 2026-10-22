---
category: general
date: 2026-10-07
description: Узнайте, как сохранить документ в PDF, добавив прямоугольную фигуру и
  пользовательскую тень с помощью Aspose.Words для Python. Пошаговый код включён.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save document as pdf
- add rectangle shape
- export word to pdf
- set rectangle dimensions
- draw rectangle word
language: ru
lastmod: 2026-10-07
og_description: Сохраните документ в PDF с пользовательской прямоугольной фигурой,
  используя Aspose.Words для Python. Следуйте полному примеру, чтобы нарисовать, оформить
  и экспортировать Word в PDF.
og_image_alt: Screenshot of the generated PDF showing the rectangle shape after save
  document as pdf
og_title: Сохранить документ в PDF с прямоугольной фигурой — полный гид по Python
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  headline: How to save document as PDF with a custom rectangle shape in Python
  type: TechArticle
- description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  name: How to save document as PDF with a custom rectangle shape in Python
  steps:
  - name: Initialize a new blank document
    text: '```python import aspose.words as aw'
  - name: Add rectangle shape to the document
    text: '```python # Create a rectangle shape and attach it to the document. rectangle
      = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)'
  - name: Set rectangle dimensions
    text: '```python # Define width and height in points (1 point = 1/72 inch). rectangle.width
      = 200 # 200 points ≈ 2.78 inches rectangle.height = 100 # 100 points ≈ 1.39
      inches ```'
  - name: (Optional) Apply a visible custom shadow
    text: '```python shadow = rectangle.shadow_format shadow.visible = True # Show
      the shadow shadow.blur = 5.0 # Softness of the shadow edge shadow.distance =
      3.0 # How far the shadow is offset shadow.angle = 45 # Direction in degrees
      shadow.color = aw.drawing.Color.black ```'
  - name: Save document as PDF
    text: '```python output_path = "output/shadow_rectangle.pdf" document.save(output_path)
      print(f"PDF saved to {output_path}") ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Word automation
title: Как сохранить документ в PDF с пользовательским прямоугольником в Python
url: /ru/python/document-conversion/how-to-save-document-as-pdf-with-a-custom-rectangle-shape-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как сохранить документ в PDF с пользовательской прямоугольной формой в Python

Если вам нужно **save document as PDF**, добавляя пользовательскую графику, это руководство покажет, как это сделать. Мы пройдём процесс создания пустого файла Word, **drawing a rectangle shape**, установки его размеров, применения видимой тени и, наконец, **export Word to PDF** с помощью библиотеки Aspose.Words for Python.

В результате вы получите PDF, содержащий идеально расположенный прямоугольник, готовый для отчетов, счетов или любой сценарий автоматизации документов. Не требуются внешние инструменты — только Python и пакет Aspose.Words.

## Что понадобится

| Requirement | Why it matters |
|-------------|----------------|
| Python 3.8+ | API Aspose.Words for Python ориентирован на современные интерпретаторы. |
| `aspose-words` package (`pip install aspose-words`) | Предоставляет пространство имён `aw`, используемое в примерах кода. |
| Basic familiarity with Python and object‑oriented programming | В руководстве манипулируются объекты, такие как `Document` и `Shape`. |
| Write permission to a folder where the PDF will be saved | `save document as pdf` шаг записывает файл на диск. |

> **Pro tip:** Используйте виртуальное окружение (`python -m venv venv`), чтобы изолировать зависимости.

## Как сохранить документ в PDF с прямоугольной формой

Ниже приведён полный, исполняемый пример. Каждый шаг объясняется, чтобы вы понимали **почему** мы выполняем действие, а не только **что** делает код.

### Шаг 1: Инициализировать новый пустой документ

```python
import aspose.words as aw

# Create an empty Word document – this is the canvas for our shape.
document = aw.Document()
```

Создание нового объекта `Document` даёт вам чистую коллекцию страниц. Вы также можете загрузить существующий *.docx*, если хотите позже **export Word to PDF**, но начало с пустого документа делает пример более сфокусированным.

### Шаг 2: Добавить прямоугольную форму в документ

```python
# Create a rectangle shape and attach it to the document.
rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

# The shape must be placed inside a paragraph before it appears.
paragraph = document.first_section.body.first_paragraph
paragraph.append_child(rectangle)
```

Шаг `add rectangle shape` использует `ShapeType.RECTANGLE`. Добавляя форму к абзацу, Aspose.Words знает, где отобразить её в конечном PDF.

### Шаг 3: Установить размеры прямоугольника

```python
# Define width and height in points (1 point = 1/72 inch).
rectangle.width = 200   # 200 points ≈ 2.78 inches
rectangle.height = 100  # 100 points ≈ 1.39 inches
```

Установка явных **rectangle dimensions** гарантирует, что форма будет выглядеть одинаково на разных платформах. Вы также можете использовать вспомогательные функции `convert_to_inches`, если предпочитаете имперские единицы.

### Шаг 4: (Опционально) Применить видимую пользовательскую тень

```python
shadow = rectangle.shadow_format
shadow.visible = True          # Show the shadow
shadow.blur = 5.0              # Softness of the shadow edge
shadow.distance = 3.0          # How far the shadow is offset
shadow.angle = 45              # Direction in degrees
shadow.color = aw.drawing.Color.black
```

Тень делает прямоугольник более заметным в PDF. Флаг `shadow.visible` обязателен; без него остальные свойства не влияют.

### Шаг 5: Сохранить документ в PDF

```python
output_path = "output/shadow_rectangle.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Вызов `document.save` с расширением **.pdf** автоматически **save document as pdf** с использованием встроенного PDF‑рендерера Aspose.Words. Дополнительные шаги конвертации не требуются, поэтому этот метод рекомендуется для **export Word to PDF**.

> **Why this works:** Aspose.Words записывает макет документа, включая прямоугольник и его тень, непосредственно в поток PDF. Процесс без потерь и сохраняет векторное качество.

## Полный исходный код (один скрипт)

```python
import aspose.words as aw

def create_pdf_with_rectangle(output_path: str):
    """
    Creates a PDF that contains a single rectangle shape with a custom shadow.
    The function demonstrates:
    • add rectangle shape
    • set rectangle dimensions
    • export Word to PDF (save document as pdf)
    """
    # 1️⃣ Create a new blank document
    document = aw.Document()

    # 2️⃣ Insert a rectangle shape
    rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

    # 3️⃣ Set the shape's size
    rectangle.width = 200   # points
    rectangle.height = 100  # points

    # 4️⃣ Configure a visible shadow
    shadow = rectangle.shadow_format
    shadow.visible = True
    shadow.blur = 5.0
    shadow.distance = 3.0
    shadow.angle = 45
    shadow.color = aw.drawing.Color.black

    # 5️⃣ Add shape to the first paragraph
    paragraph = document.first_section.body.first_paragraph
    paragraph.append_child(rectangle)

    # 6️⃣ Save the document as PDF
    document.save(output_path)
    print(f"PDF successfully saved to: {output_path}")

if __name__ == "__main__":
    create_pdf_with_rectangle("output/shadow_rectangle.pdf")
```

Запуск этого скрипта создаёт `shadow_rectangle.pdf`, который выглядит так:

![Диаграмма сгенерированного PDF, показывающая форму прямоугольника после save document as pdf](placeholder-image.png)

*PDF содержит одну страницу с прямоугольником с чёрной тенью, центрированным в документе.*

## Часто задаваемые вопросы и особые случаи

| Question | Answer |
|----------|--------|
| **Могу ли я разместить прямоугольник в определённом месте?** | Да. Установите `rectangle.left` и `rectangle.top` (в пунктах) перед сохранением. |
| **Что если мне нужно несколько форм?** | Создайте дополнительные объекты `Shape`, настройте каждый и добавьте их в тот же или в разные абзацы. |
| **Влияет ли тень на размер PDF?** | Только незначительно; тень хранится как векторные метаданные, а не как растровое изображение. |
| **Можно ли использовать это для конвертации существующих *.docx* файлов?** | Конечно. Замените `aw.Document()` на `aw.Document("input.docx")`, остальные шаги останутся без изменений. |
| **Можно ли изменить цвет заливки прямоугольника?** | Установите `rectangle.fill_color = aw.drawing.Color.light_blue` (или любой другой `Color`, который вам нужен). |

## Следующие шаги

Теперь, когда вы знаете, как **save document as PDF** с пользовательским прямоугольником, вы можете изучить:

* **Export Word to PDF** с заголовками, нижними колонтитулами и номерами страниц.  
* **Add other drawing objects** (`Ellipse`, `Polygon`) с использованием того же класса `Shape`.  
* **Batch process** папку файлов Word, применяя тот же прямоугольный наложение к каждому.  

Эти расширения следуют той же схеме: создайте форму, настройте её свойства и **save document as pdf**.

---

**Summary:** В этом руководстве показано, как **save document as PDF**, одновременно **add rectangle shape**, **set rectangle dimensions** и применить пользовательскую тень с помощью Aspose.Words for Python. Полный скрипт готов к копированию, запуску и адаптации под ваши собственные конвейеры автоматизации документов. Приятного кодирования!

## Что стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полные работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Создать прямоугольную форму, добавить тень и сохранить PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Добавить прямоугольник в PDF с Aspose.Words – пошаговое руководство](/words/english/python-net/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/)
- [Сохранить документ в PDF с Aspose.Words – полное руководство C#](/words/english/net/programming-with-pdfsaveoptions/save-document-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}