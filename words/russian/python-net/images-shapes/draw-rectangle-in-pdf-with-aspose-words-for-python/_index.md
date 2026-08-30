---
category: general
date: 2026-08-07
description: Нарисуйте прямоугольник в PDF с помощью Aspose.Words для Python и узнайте,
  как добавить тень к фигуре, настроить её тень и сохранить документ в PDF.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle in pdf
- add shadow to shape
- save document as pdf
- configure shape shadow
language: ru
lastmod: 2026-08-07
og_description: Рисуем прямоугольник в PDF с помощью Aspose.Words для Python. Этот
  учебник показывает, как добавить тень к фигуре, настроить тень фигуры и сохранить
  документ в PDF для профессионального создания документов.
og_image_alt: PDF page showing a rectangle shape with a visible shadow created by
  Aspose.Words for Python
og_title: Рисуем прямоугольник в PDF с помощью Aspose.Words для Python – руководство
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Draw rectangle in PDF using Aspose.Words for Python and learn how to
    add shadow to shape, configure shape shadow, and save document as PDF.
  headline: Draw rectangle in PDF with Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF
- Shape
- Shadow
title: Рисуем прямоугольник в PDF с помощью Aspose.Words для Python
url: /ru/python/images-shapes/draw-rectangle-in-pdf-with-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Рисуем прямоугольник в PDF с помощью Aspose.Words для Python

Если вам нужно **draw rectangle in PDF** при работе с Python, это руководство предоставляет полное, готовое к запуску решение. Вы увидите, как именно **add shadow to shape**, настроить эту тень и, наконец, **save document as PDF** для распространения или архивирования.

Создание затенённого прямоугольника — частая задача для отчётов, счетов‑фактур или визуальных аннотаций. К концу этого урока у вас будет один скрипт, генерирующий PDF с прямоугольником и реалистичной тенью, а также понимание того, как менять размер, цвет и смещение под любой дизайн.

## Предварительные требования

* Установлен Python 3.8+.
* Пакет Aspose.Words for Python via .NET (`aspose-words`) – установить с помощью:

```bash
pip install aspose-words
```

* Права записи в папку, куда планируется сохранять PDF.

Дополнительные библиотеки не требуются; Aspose.Words самостоятельно обрабатывает создание фигур, настройку тени и экспорт в PDF.

## Шаг 1: Создать новый пустой документ (draw rectangle in PDF – инициализация)

Первый шаг — создать объект `Document`. Этот объект представляет весь PDF‑файл и служит контейнером для разделов, абзацев и фигур.

```python
import aspose.words as aw

# Create an empty Word document – it will become a PDF later
doc = aw.Document()
```

**Почему это важно:** Aspose.Words рассматривает генерацию PDF как преобразование из модели Word‑документа, поэтому мы начинаем с `Document`, даже если конечный результат — PDF.

## Шаг 2: Вставить форму прямоугольника в тело документа

Прямоугольник — это конкретный `ShapeType`. Мы добавляем его в тело первого раздела, что автоматически создаёт новую страницу при сохранении в PDF.

```python
# Append a rectangle shape to the first section's body
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Set the rectangle's dimensions (points = 1/72 inch)
rectangle.width = 200   # 200 pt ≈ 2.78 in
rectangle.height = 100  # 100 pt ≈ 1.39 in

# Optional: give the shape some visible text
rectangle.text = "Shadow demo"
```

**Объяснение:** Свойства `width` и `height` управляют визуальными размерами фигуры в PDF. Добавление текста упрощает проверку прямоугольника во время тестирования.

## Шаг 3: Добавить тень к форме – включить и настроить

Теперь включаем эффект тени и точно настраиваем её внешний вид. Здесь и вступает в действие ключевое слово **add shadow to shape**.

```python
# Access the shape's shadow effect object
shadow = rectangle.shadow_effect

# Make the shadow visible
shadow.visible = True

# Configure blur radius (pt) – higher values produce a softer edge
shadow.blur = 8

# Set the distance (offset) from the shape in points
shadow.distance = 5

# Define the direction of the shadow in degrees (0 = right, 90 = down)
shadow.angle = 45

# Choose a shadow color – black works for most documents
shadow.color = aw.drawing.Color.black
```

**Зачем настраивать тень фигуры?** Регулировка `blur`, `distance` и `angle` позволяет имитировать реалистичное освещение, улучшая читаемость и визуальную иерархию в генерируемых PDF‑файлах.

## Шаг 4: Сохранить документ как PDF – окончательный результат

После определения прямоугольника и его тени последний шаг — экспортировать Word‑документ в PDF. Это удовлетворяет требование **save document as pdf**.

```python
# Define the output path – replace YOUR_DIRECTORY with an actual folder
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)
print(f"PDF saved to {output_path}")
```

Когда вы откроете `shadow_rectangle.pdf`, вы увидите одну страницу с серой рамкой прямоугольника под заголовком «Shadow demo» и чёткой диагональной тенью.

### Ожидаемый результат

* PDF‑файл с именем `shadow_rectangle.pdf`.
* Одна страница с прямоугольником 200 pt × 100 pt.
* Видимая тень со смещением 5 pt под углом 45°, размытие — 8 pt.

## Шаг 5: Исследовать варианты и граничные случаи (необязательно)

Ниже перечислены типичные настройки, которые могут понадобиться в реальных проектах:

| Variation | Code snippet | When to use |
|-----------|--------------|-------------|
| **Different shape type** (e.g., ellipse) | `aw.drawing.ShapeType.OVAL` instead of `RECTANGLE` | Для округлых графических элементов или бейджей |
| **Custom shadow color** | `shadow.color = aw.drawing.Color.from_argb(255, 100, 100, 100)` | Когда требуется серая или фирменная тень |
| **Multiple shapes** | Repeat the shape‑creation block and adjust `left`/`top` properties | Для построения сложных диаграмм |
| **No text inside shape** | Omit `rectangle.text = "..."` | Когда фигура используется только как декоративный элемент |
| **Higher DPI output** | `doc.save(output_path, aw.SaveFormat.PDF, aw.PdfSaveOptions())` with `PdfSaveOptions` set for image quality | Для PDF‑файлов, готовых к печати |

**Pro tip:** Сначала установите `shadow.visible = True`, а затем меняйте остальные свойства; иначе изменения будут проигнорированы без предупреждения.

## Полный скрипт – скопируйте, вставьте и запустите

```python
import aspose.words as aw

# 1️⃣ Create a new blank document
doc = aw.Document()

# 2️⃣ Add a rectangle shape
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
rectangle.width = 200          # width in points
rectangle.height = 100         # height in points
rectangle.text = "Shadow demo"

# 3️⃣ Configure a visible shadow effect
shadow = rectangle.shadow_effect
shadow.visible = True
shadow.blur = 8                # blur radius (pt)
shadow.distance = 5            # offset distance (pt)
shadow.angle = 45              # direction (degrees)
shadow.color = aw.drawing.Color.black

# 4️⃣ Save the document as a PDF
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)

print(f"PDF successfully created at: {output_path}")
```

Запустите скрипт из терминала или IDE. Замените `YOUR_DIRECTORY` реальным путём к папке, например `"/tmp"` или `"C:\\Users\\Me\\Documents"`.

## Заключение

Теперь вы знаете, как **draw rectangle in PDF** с помощью Aspose.Words for Python, **add shadow to shape**, **configure shape shadow** и **save document as PDF**. Полный пример демонстрирует каждый шаг от создания документа до финального экспорта, а дополнительные варианты показывают, как адаптировать код для более сложных сценариев.

Далее вы можете изучить:

* Добавление других типов фигур (`ShapeType.LINE`, `ShapeType.ELLIPSE`).
* Применение градиентных заливок или границ для улучшения визуального восприятия.
* Использование `PdfSaveOptions` для встраивания шрифтов или управления сжатием изображений.

Не стесняйтесь экспериментировать с параметрами, чтобы они соответствовали вашему бренду или дизайнерским требованиям. Приятного скриптинга PDF!

## Что изучить дальше?

Следующие учебники охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс содержит полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Optimize PDF Bookmarks Using Aspose.Words for Python](/words/english/python-net/performance-optimization/optimize-pdf-bookmarks-aspose-words-python/)
- [Optimize Pdf Loading Python Aspose Words Skip Images](/words/hindi/python-net/performance-optimization/optimize-pdf-loading-python-aspose-words-skip-images/)
- [Aspose Words Python Pdf Manipulation](/words/hongkong/python-net/document-operations/aspose-words-python-pdf-manipulation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}