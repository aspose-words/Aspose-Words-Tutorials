---
category: general
date: 2026-06-24
description: Создайте прямоугольную форму в Python с помощью Aspose.Words, узнайте,
  как добавить тень к форме, задать угол тени и сохранить документ в PDF за несколько
  минут.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shape shadow
- set shadow angle
language: ru
og_description: Создайте прямоугольную форму в Python, добавьте к ней тень, задайте
  угол тени и сохраните документ в PDF с помощью Aspose.Words. Следуйте этому пошаговому
  руководству.
og_title: Создание прямоугольной фигуры в Python – Полный учебник по Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  headline: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  name: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: What if I need a different shape?
    text: Aspose.Words supports many `ShapeType` values (ellipse, star, callout, etc.).
      Simply replace `aw.drawing.ShapeType.RECTANGLE` with the desired enum, like
      `aw.drawing.ShapeType.ELLIPSE`.
  - name: Can I add multiple shadows?
    text: The API exposes only one `ShadowFormat` per shape, but you can simulate
      multiple shadows by duplicating the shape, offsetting each copy, and adjusting
      transparency.
  - name: How do I change the shadow color to match my brand?
    text: Just set `shadow.color` to any `aw.drawing.Color`. For a brand blue, use
      `aw.drawing.Color.from_argb(255, 0, 120, 215)`.
  - name: What about saving as DOCX instead of PDF?
    text: Replace `document.save(pdf_path)` with `document.save("output/shadowed_rectangle.docx")`.
      The shadow rendering is preserved across both formats.
  - name: Does the shadow work on older PDF viewers?
    text: Aspose.Words renders the shadow as a vector effect, which is widely supported.
      However, very old viewers might flatten the effect; testing on your target audience’s
      devices is always a good habit.
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: Создание прямоугольной формы в Python – Полное руководство по Aspose.Words
url: /ru/python/images-shapes/create-rectangle-shape-in-python-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание прямоугольной фигуры в Python – Полное руководство по Aspose.Words

Когда‑нибудь задумывались, как **create rectangle shape** в документе Word с помощью Python? Возможно, вам нужен яркий выноска‑бокс, визуальный маркер для схемы или просто стильный прямоугольник для отчёта. Как бы то ни было, вы попали в нужное место. В этом руководстве мы пройдем весь процесс — от вставки прямоугольника, до добавления лёгкой тени, настройки угла тени и, наконец, **save document as PDF**, чтобы поделиться им с кем угодно.

Мы будем использовать **Aspose.Words for Python via .NET**, мощную библиотеку, позволяющую манипулировать файлами Word без открытия самого Word. К концу этого руководства вы сможете уверенно ответить на вопрос *“how to add shape shadow”* и получите готовый к запуску скрипт, который можно добавить в любой проект.

---

## Что вам понадобится

- **Python 3.8+** установленный на вашем компьютере.  
- **Aspose.Words for Python via .NET** (`aspose-words` package). Установите его с помощью:

  ```bash
  pip install aspose-words
  ```

- Папка с правом записи, куда будет сохраняться сгенерированный PDF.  
- (Опционально) IDE или текстовый редактор — VS Code отлично подходит.

Это всё. Никаких дополнительных DLL, без установки Office, только один pip‑пакет.

---

## Шаг 1: Настройка документа и Builder

Первое, что нужно сделать, — создать объекты, дружелюбные к **create rectangle shape**: `Document` и `DocumentBuilder`. Думайте о Builder как о вашей ручке; он рисует всё за вас.

```python
import aspose.words as aw

# Initialize a new blank document
document = aw.Document()

# DocumentBuilder gives us a convenient way to add content
builder = aw.DocumentBuilder(document)
```

> **Почему это важно:** Объект `Document` представляет весь файл .docx, а `DocumentBuilder` предоставляет методы вроде `insert_shape`, которые упрощают рисование фигур.

---

## Шаг 2: Вставка прямоугольной фигуры

Теперь, когда у нас есть Builder, мы наконец‑то можем **create rectangle shape**. Метод `insert_shape` принимает три аргумента: тип фигуры, ширину и высоту. Мы используем ширину 200 pt и высоту 100 pt для хороших пропорций.

```python
# Insert a rectangle with a width of 200 points and a height of 100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

На этом этапе вы успешно **create rectangle shape** в вашем документе. Если открыть сгенерированный DOCX (мы сделаем это позже), вы увидите простой прямоугольник, расположенный там, где был курсор.

---

## Шаг 3: Доступ к объекту форматирования тени

Чтобы **add shadow to shape**, нам сначала нужно получить объект форматирования тени фигуры. Каждая фигура в Aspose.Words имеет свойство `shadow_format`, которое раскрывает все параметры, связанные с тенью.

```python
# Grab the shadow formatting object for later tweaks
shadow = rectangle.shadow_format
```

Имея ссылку `shadow`, мы можем переключать видимость, размытие, расстояние, угол, цвет и прозрачность — все это в нескольких строках кода.

---

## Шаг 4: Включение тени и настройка её внешнего вида

Вот где происходит магия. Мы **add shadow to shape**, сделаем её слегка размытой, сместим немного, зададим направление (часть **set shadow angle**) и придадим полупрозрачный чёрный оттенок.

```python
# Turn the shadow on
shadow.visible = True

# Soften the edges – a blur radius of 8 points looks natural
shadow.blur_radius = 8.0

# Push the shadow away from the rectangle by 5 points
shadow.distance = 5.0

# Set the direction of the light source – 45 degrees creates a diagonal drop
shadow.angle = 45

# Choose a color; black works well for most documents
shadow.color = aw.drawing.Color.black

# Make the shadow 30 % transparent for a subtle effect
shadow.transparency = 0.3
```

> **Pro tip:** Если нужен более драматичный эффект, увеличьте `blur_radius` или уменьшите `transparency`. И наоборот, резкую полностью непрозрачную тень можно получить, задав `blur_radius = 0` и `transparency = 0`.

---

## Шаг 5: Сохранение документа в PDF

Мы **create rectangle shape**, мы **add shadow to shape**, и теперь мы **save document as PDF**, чтобы результат выглядел одинаково на любом устройстве. Aspose.Words делает это одной строкой.

```python
# Define where you want the PDF to land
output_path = "output/shadowed_rectangle.pdf"

# Save the whole document (including the rectangle with its shadow) as PDF
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Запуск скрипта сгенерирует `shadowed_rectangle.pdf` в папке `output`. Откройте его в любом PDF‑просмотрщике, и вы увидите чистый прямоугольник с мягкой тенью под углом 45° — именно то, что мы настроили.

---

## Полный рабочий пример

Ниже полностью готовый к запуску скрипт, объединяющий все описанные шаги. Скопируйте его в файл `create_rectangle_with_shadow.py` и выполните `python create_rectangle_with_shadow.py`.

```python
import aspose.words as aw
import os

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Initialize document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert the rectangle shape (200 pt × 100 pt)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Access shadow formatting
shadow = rectangle.shadow_format

# 4️⃣ Configure shadow – visible, blurred, offset, angled, colored, semi‑transparent
shadow.visible = True
shadow.blur_radius = 8.0          # softer edges
shadow.distance = 5.0            # how far the shadow sits from the shape
shadow.angle = 45                # direction in degrees – this is the **set shadow angle** step
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.3        # 30 % transparent

# 5️⃣ Save the document as PDF
pdf_path = os.path.join(output_dir, "shadowed_rectangle.pdf")
document.save(pdf_path)

print(f"✅ PDF created at: {pdf_path}")
```

**Expected output:** PDF‑файл, показывающий один прямоугольник с нежной диагональной тенью. Никаких лишних страниц, никаких скрытых артефактов — только созданная нами фигура.

---

## Часто задаваемые вопросы и особые случаи

### Что делать, если нужен другой тип фигуры?

Aspose.Words поддерживает множество значений `ShapeType` (эллипс, звезда, выноска и т.д.). Просто замените `aw.drawing.ShapeType.RECTANGLE` на нужный enum, например `aw.drawing.ShapeType.ELLIPSE`.

### Можно ли добавить несколько теней?

API предоставляет только один `ShadowFormat` на фигуру, но можно имитировать несколько теней, дублируя фигуру, смещая каждую копию и регулируя прозрачность.

### Как изменить цвет тени, чтобы он соответствовал бренду?

Достаточно установить `shadow.color` в любой `aw.drawing.Color`. Для фирменного синего используйте `aw.drawing.Color.from_argb(255, 0, 120, 215)`.

### Как сохранить документ в DOCX вместо PDF?

Замените `document.save(pdf_path)` на `document.save("output/shadowed_rectangle.docx")`. Отображение тени сохраняется в обоих форматах.

### Работает ли тень в старых PDF‑просмотрщиках?

Aspose.Words рендерит тень как векторный эффект, который поддерживается большинством программ. Однако очень старые просмотрщики могут «сплющить» эффект; тестирование на целевых устройствах всегда полезно.

---

## Советы по полировке вашего PDF

- **Add a border:** `rectangle.line_format.width = 1.5` и задайте цвет для чёткой обводки.  
- **Center the rectangle:** Вызовите `builder.move_to_document_start()` перед вставкой, затем `builder.paragraph_format.alignment = aw.ParagraphAlignment.CENTER`.  
- **Combine with text:** Вставьте `TextFragment` после прямоугольника, чтобы подписать его, например, `"Important Section"`.

Эти небольшие штрихи могут превратить обычный прямоугольник в отшлифованный выноска‑бокс, выглядящий профессионально в отчётах, предложениях или электронных книгах.

---

## Заключение

Теперь у вас есть надёжный сквозной рецепт для **create rectangle shape** в Python, **add shadow to shape**, **set shadow angle** и **save document as PDF** с помощью Aspose.Words. Шаги просты, код полностью автономен, и вы увидели, почему каждая строка важна — от инициализации документа до полировки финального PDF.

Далее вы можете исследовать **how to add shape shadow** в более сложных рисунках, поэкспериментировать с градиентными заливками или генерировать таблицы внутри фигур. Библиотека также поддерживает привязку фигур к закладкам, что удобно для интерактивных PDF.

Есть свои находки? Делитесь в комментариях или задавайте оставшиеся вопросы. Приятного кодинга и наслаждайтесь добавлением глубины вашим документам! 

![Прямоугольник с тенью – пример создания rectangle shape в Python](/images/rectangle-shadow.png)


## Что изучать дальше?


Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}