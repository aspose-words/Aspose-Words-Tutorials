---
category: general
date: 2026-11-25
description: Добавьте тень к фигуре в документе Word с помощью Python. Узнайте, как
  вставить прямоугольную форму в Word и применить прозрачную тень с использованием
  Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- insert rectangle shape word
- how to create word document python
- Aspose.Words Python
- shape formatting Python
language: ru
lastmod: 2026-11-25
og_description: Добавьте тень к фигуре в документе Word с помощью Python. Этот учебник
  показывает, как вставить прямоугольную форму в Word и установить 30 % прозрачную
  тень с помощью Aspose.Words.
og_image_alt: Add shadow to shape example in a Word document created by Python
og_title: Добавьте тень к фигуре в документе Word с помощью Python — пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Add shadow to shape in a Word document with Python. Learn how to insert
    rectangle shape in Word and apply a transparent shadow using Aspose.Words.
  headline: How to add shadow to shape in a Word document using Python
  type: TechArticle
tags:
- Python
- Aspose.Words
- Word automation
title: Как добавить тень к фигуре в документе Word с помощью Python
url: /ru/python/images-shapes/how-to-add-shadow-to-shape-in-a-word-document-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как добавить тень к фигуре в документе Word с помощью Python

Если вам нужно **добавить тень к фигуре** в документе Word, это руководство покажет полное, готовое к запуску решение. Вы увидите, как создать файл Word, вставить прямоугольную фигуру и применить 30 % прозрачную тень — всё с помощью библиотеки Aspose.Words for Python.

Программная работа с документами Word экономит время на ручном форматировании и позволяет генерировать отчёты, контракты или рекламные листовки в масштабе. К концу этого урока вы сможете ответить на вопрос «**как создать документ Word python**», представив готовый пример кода.

## Требования

Прежде чем начать, убедитесь, что у вас есть:

* Установлен Python 3.8 или новее.  
* Активная лицензия Aspose.Words for Python (бесплатная пробная версия подходит для оценки).  
* Пакет `aspose-words`, установленный командой `pip install aspose-words`.  
* Папка, в которую можно записать выходной файл (замените `YOUR_DIRECTORY` в коде).

Дополнительные зависимости не требуются.

## Шаг 1: Создать новый документ Word

Первый шаг — создать объект `Document`. Этот объект представляет весь файл .docx в памяти.

```python
import aspose.words as aw

# Create an empty Word document
doc = aw.Document()
# DocumentBuilder provides a convenient API for adding content
builder = aw.DocumentBuilder(doc)
```

`DocumentBuilder` работает как виртуальный курсор. При вызове его методов библиотека вставляет соответствующие элементы в текущую позицию курсора.

## Шаг 2: Вставить прямоугольную фигуру

Далее вы **вставляете прямоугольную фигуру** с помощью метода `insert_shape` билдера. Метод требует тип фигуры и её размеры в пунктах (1 пункт = 1/72 дюйма).

```python
# Insert a rectangle shape that is 100 points wide and 50 points tall
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)
```

Вы можете изменить размеры, чтобы они соответствовали вашему дизайну. Прямоугольник становится частью слоя рисунков документа, что позволяет позже изменять его заливку, контур или тень.

## Шаг 3: Получить формат тени фигуры

Каждый объект рисунка раскрывает свойство `shadow_format`, которое управляет внешним видом тени. Получите его, чтобы настроить прозрачность, смещение, размытие и цвет.

```python
# Get the ShadowFormat object for the rectangle
shadow = shape.shadow_format
```

На данный момент у фигуры стоит тень по умолчанию (отсутствует тень). Объект `ShadowFormat` содержит все параметры, необходимые для создания реалистичного эффекта.

## Шаг 4: Сделать тень 30 % прозрачной

Прозрачность задаётся значением от `0` (полностью непрозрачно) до `1` (полностью прозрачно). Установка `0.3` даёт 30 % прозрачную тень, чего обычно достаточно, чтобы добавить глубину, не перегружая текст.

```python
# Apply a 30 % transparent shadow
shadow.transparency = 0.3
# Optional: adjust other shadow properties for a nicer look
shadow.visible = True               # Ensure the shadow is turned on
shadow.distance = 4                 # Distance of the shadow from the shape (points)
shadow.blur = 4                     # Amount of blur applied to the shadow
shadow.color = aw.Color.black       # Shadow color
```

Эти дополнительные свойства не обязательны, но они показывают, как можно точно настроить эффект. Флаг `visible` важен; если его забыть, тень не появится, даже если остальные параметры заданы.

## Шаг 5: Сохранить документ и посмотреть результат

Наконец, запишите документ на диск. Открытие полученного файла `.docx` в Microsoft Word или любом совместимом просмотрщике покажет прямоугольник с применённой полупрозрачной тенью.

```python
# Save the document to the desired location
output_path = r"YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Когда вы откроете `output.docx`, вы увидите простой прямоугольник с лёгкой серой тенью, смещённой вниз‑вправо. Прозрачность тени в 30 % создаёт ощущение, что фигура поднята над страницей.

![Add shadow to shape example](placeholder-image.png){: .align-center alt="Пример добавления тени к фигуре в документе Word, созданном с помощью Python"}

## Полный, готовый к запуску скрипт

Собрав все части вместе, вы получаете автономный скрипт, который можно скопировать, вставить и сразу выполнить.

```python
import aspose.words as aw

def create_word_with_shadow(output_path: str):
    """
    Creates a Word document that contains a rectangle shape
    with a 30 % transparent shadow.
    """
    # Step 1: Initialize document and builder
    doc = aw.Document()
    builder = aw.DocumentBuilder(doc)

    # Step 2: Insert rectangle shape
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)

    # Step 3: Access shadow format
    shadow = shape.shadow_format

    # Step 4: Configure shadow properties
    shadow.visible = True
    shadow.transparency = 0.3
    shadow.distance = 4
    shadow.blur = 4
    shadow.color = aw.Color.black

    # Step 5: Save the document
    doc.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    # Replace with a valid folder on your machine
    create_word_with_shadow(r"YOUR_DIRECTORY/output.docx")
```

**Ожидаемый результат:** Открытие сгенерированного `output.docx` показывает одну страницу с прямоугольником, отбрасывающим лёгкую полупрозрачную тень. Дополнительное форматирование не требуется.

## Распространённые варианты и граничные случаи

| Ситуация | Как адаптировать код |
|-----------|-----------------------|
| **Другой тип фигуры** (например, эллипс) | Замените `aw.drawing.ShapeType.RECTANGLE` на `aw.drawing.ShapeType.ELLIPSE`. |
| **Пользовательский цвет тени** | Установите `shadow.color = aw.Color.from_argb(255, 128, 0, 0)` для красноватой тени. |
| **Несколько фигур** | Вызывайте `builder.insert_shape` многократно; каждый вызов возвращает отдельный объект `Shape`, который можно стилизовать независимо. |
| **Сохранение в PDF** | Замените `doc.save(output_path)` на `doc.save(output_path.replace('.docx', '.pdf'))` и используйте расширение `.pdf`. |
| **Запуск без лицензии** | Бесплатная пробная версия добавляет водяной знак на первую страницу. Приобретите лицензию, чтобы убрать его в продакшн‑использовании. |

Эти варианты показывают, что один и тот же шаблон — создать документ, вставить фигуру, настроить `shadow_format`, сохранить — покрывает большинство сценариев автоматизации.

## Советы и лучшие практики

* **Повторное использование билдера**: Держите один экземпляр `DocumentBuilder` на весь документ, чтобы избежать лишнего создания объектов.  
* **Освобождение ресурсов**: В длительно работающих сервисах вызывайте `doc.dispose()` после сохранения, чтобы освободить нативную память.  
* **Проверка вывода**: При необходимости убедиться в соответствии Open XML используйте `doc.validate(aw.ValidationType.FULL_VALIDATION)` перед сохранением.  
* **Совместимость версий**: Код работает с Aspose.Words for Python ≥ 22.9. Убедитесь, что ваш пакет обновлён командой `pip install --upgrade aspose-words`.  

## Заключение

Теперь вы знаете, как **добавить тень к фигуре** в документе Word с помощью Python. Следуя пяти шагам — создать документ, **вставить прямоугольную фигуру**, настроить тень и сохранить — вы сможете автоматизировать создание профессионально выглядящих документов для отчётов, счетов или маркетинговых материалов.  

Дальше вы можете изучать другие варианты форматирования, такие как градиентные заливки, обтекание текстом или конвертация документа в PDF. Все эти темы опираются на те же концепции `DocumentBuilder` и форматирования фигур, представленные в этом руководстве.

Удачной разработки и наслаждайтесь визуальной глубиной, которую простая тень может добавить к вашим автоматизированным документам Word!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом пособии. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [How to create rectangle shape in a Word document using Python](/words/english/python-net/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/)
- [Add Shadow to Shape in Python – Complete Aspose.Words Tutorial](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [Create Blank Word Document and Add Shadow to Shape – Full Python Guide](/words/english/python-net/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-pyth/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}