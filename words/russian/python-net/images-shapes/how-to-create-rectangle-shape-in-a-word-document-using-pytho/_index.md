---
category: general
date: 2026-09-30
description: Узнайте, как создать прямоугольную форму, применить к ней тень и сохранить
  документ Word с формой, используя Aspose.Words для Python.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- how to add shape
- apply shadow to shape
- set shadow blur
- save word with shape
language: ru
lastmod: 2026-09-30
og_description: Быстро создайте прямоугольную форму в документе Word. Этот учебник
  показывает, как добавить форму, применить к ней тень, установить размытие тени и
  сохранить документ Word с формой.
og_image_alt: Screenshot of a Word document showing a rectangle shape with a soft
  shadow
og_title: Создание прямоугольной формы в Word с помощью Python – пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Learn how to create rectangle shape, apply shadow to shape, and save
    Word with shape using Aspose.Words for Python.
  headline: How to create rectangle shape in a Word document using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- Shapes
title: Как создать прямоугольную форму в документе Word с помощью Python
url: /ru/python/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать прямоугольную форму в документе Word с помощью Python

Если вам нужно **создать прямоугольную форму** в файле Word, это руководство покажет полное, готовое к запуску решение. Вы увидите, как добавить форму, применить эффект тени, настроить размытие и, наконец, **сохранить Word с формой**, чтобы результат можно было открыть в Microsoft Word или любом совместимом просмотрщике.

В примере используется **Aspose.Words for Python via .NET**, библиотека, позволяющая работать с документами Word без установленного Microsoft Office. Предыдущий опыт работы с API не требуется — достаточно базовых знаний Python.

## Что вы получите

- Вставите прямоугольник в первый раздел нового документа.  
- Настроите мягкую тень, задав её размытие, смещение и цвет.  
- Сохраните документ на диск и проверите визуальный результат.

## Предварительные требования

- Python 3.8 или новее.  
- Пакет `aspose-words`, установленный (`pip install aspose-words`).  
- Права записи в каталог вывода.

## Создание прямоугольной формы и настройка её внешнего вида

Первый шаг — создать пустой документ и добавить в него прямоугольную форму. Форма будет служить холстом для эффекта тени.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Step 1: Create a new blank document
doc = aw.Document()

# Step 2: Add a rectangle shape to the first section
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Optional: Define the shape’s size and position (in points)
shape.width = aw.ConvertUtil.inch_to_point(2)   # 2 inches wide
shape.height = aw.ConvertUtil.inch_to_point(1)  # 1 inch tall
shape.left = aw.ConvertUtil.inch_to_point(1)    # 1 inch from the left margin
shape.top = aw.ConvertUtil.inch_to_point(1)     # 1 inch from the top margin
```

**Почему это важно:**  
Создание прямоугольника дает вам конкретный объект (`shape`), который позже можно стилизовать. Явное указание размеров гарантирует одинаковый вид формы на любой платформе.

## Как добавить форму в документ Word

Хотя приведённый выше код уже добавляет прямоугольник, позже вам может потребоваться добавить другие формы (например, круги, стрелки). Применяется тот же шаблон: вызывайте `append_child` у тела документа и передавайте нужный `ShapeType`.

```python
# Example: Adding a second shape – an ellipse
ellipse = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.ELLIPSE)
)
ellipse.width = aw.ConvertUtil.inch_to_point(1.5)
ellipse.height = aw.ConvertUtil.inch_to_point(1)
ellipse.left = aw.ConvertUtil.inch_to_point(3.5)
ellipse.top = aw.ConvertUtil.inch_to_point(1)
```

**Подсказка:** Используйте перечисление `ShapeType`, чтобы изучить все поддерживаемые формы. Это делает код читаемым и избавляет от «магических» чисел.

## Применение тени к форме и настройка размытия тени

Тень добавляет глубину и визуальный интерес. Класс `ShadowEffect` позволяет управлять размытием, смещением и цветом. Ниже мы применяем мягкую чёрную тень к прямоугольнику.

```python
# Step 3: Configure a shadow effect for the rectangle
shadow = ShadowEffect()
shadow.blur = 5.0          # Sets the softness of the shadow edge
shadow.offset_x = 2.0      # Horizontal displacement from the shape
shadow.offset_y = 2.0      # Vertical displacement from the shape
shadow.color = aw.Color.black

# Step 4: Apply the shadow effect to the shape
shape.shadow = shadow
```

**Зачем задавать размытие?**  
`blur` определяет, насколько рассеянной будет тень. Низкое значение (например, 1.0) даёт резкую границу, а более высокое (например, 5.0) создаёт плавный переход, что часто выглядит эстетичнее.

**Пограничный случай:** Если задать `blur` = 0, тень превращается в сплошной силуэт. Некоторые просмотрщики могут отобразить её с артефактами aliasing, поэтому выбирайте значение больше 0 для более гладкого результата.

## Сохранить Word с формой

Сохранение документа фиксирует все изменения. Метод `save` записывает файл `.docx`, который может открыть любой современный процессор Word.

```python
# Step 5: Save the document to see the result
output_path = "output.docx"   # Adjust the path as needed
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Когда вы откроете `output.docx`, вы увидите прямоугольник, расположенный в одном дюйме от верхнего‑левого угла, с мягкой чёрной тенью, смещённой на два пункта вправо и вниз. Размытие тени создаёт ощущение, что форма поднята над страницей.

**Профессиональный совет:** Если нужно генерировать множество документов в цикле, переиспользуйте один экземпляр `Document` и очищайте его тело между итерациями, чтобы снизить нагрузку на память.

## Общие варианты и устранение неполадок

| Ситуация | Что изменить | Причина |
|-----------|----------------|--------|
| Другая цветовая тень | `shadow.color = aw.Color.red` | Используйте фирменные цвета или выделяйте важные формы. |
| Большое смещение тени | Увеличьте `shadow.offset_x`/`offset_y` | Подчеркните глубину для макетов UI. |
| Полностью без тени | Удалите строку `shape.shadow = shadow` | Подходит для минималистичных отчётов. |
| Экспорт в PDF вместо DOCX | `doc.save("output.pdf")` | PDF идеален для распределения только для чтения. |

Если форма не отображается, проверьте, что вы добавляете её в правильный раздел (`get_first_section()`) и что документ сохраняется после внесения изменений.

## Полный, готовый к запуску пример

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Create a new blank document
doc = aw.Document()

# Add a rectangle shape
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
shape.width = aw.ConvertUtil.inch_to_point(2)
shape.height = aw.ConvertUtil.inch_to_point(1)
shape.left = aw.ConvertUtil.inch_to_point(1)
shape.top = aw.ConvertUtil.inch_to_point(1)

# Configure and apply a shadow
shadow = ShadowEffect()
shadow.blur = 5.0
shadow.offset_x = 2.0
shadow.offset_y = 2.0
shadow.color = aw.Color.black
shape.shadow = shadow

# Save the document
output_path = "output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Запуск скрипта создаст `output.docx`, содержащий прямоугольник с мягкой тенью. Откройте файл в Microsoft Word, чтобы убедиться, что визуальный эффект соответствует описанию.

## Заключение

Теперь вы знаете, как **создать прямоугольную форму**, **как добавить форму** в документ Word, **применить тень к форме**, **задать размытие тени** и, наконец, **сохранить Word с формой** с помощью Aspose.Words for Python. Тот же подход можно расширить на другие типы форм, цвета и эффекты, получая полный контроль над графикой документа без необходимости автоматизации Office.

**Следующие шаги**

- Поэкспериментируйте с `Shape.fill`, чтобы добавить градиентные или картинные фоны.  
- Используйте объекты `Paragraph` для размещения текста внутри прямоугольника.  
- Комбинируйте несколько форм, чтобы построить сложные диаграммы, а затем экспортируйте в PDF для распространения.  

Не стесняйтесь адаптировать код под свои задачи по отчётности или шаблонизации и делиться результатами в комментариях!

## Что вам стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}