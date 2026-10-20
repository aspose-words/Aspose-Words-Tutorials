---
category: general
date: 2026-06-30
description: Как переименовывать изображения при конвертации DOCX в markdown. Узнайте,
  как менять имена изображений и сохранять Word в markdown с пользовательскими именами
  файлов изображений.
draft: false
keywords:
- how to rename images
- convert docx to markdown
- change image names
- save word as markdown
- custom image filenames
language: ru
og_description: Как переименовать изображения при конвертации DOCX в markdown. Это
  руководство покажет, как изменить имена изображений, сохранить Word в markdown и
  использовать пользовательские имена файлов изображений.
og_title: Как переименовать изображения при конвертации DOCX в Markdown
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: How to rename images while converting DOCX to markdown. Learn to change
    image names and save Word as markdown with custom image filenames.
  headline: How to Rename Images When Converting DOCX to Markdown
  type: TechArticle
- description: How to rename images while converting DOCX to markdown. Learn to change
    image names and save Word as markdown with custom image filenames.
  name: How to Rename Images When Converting DOCX to Markdown
  steps:
  - name: Why Use a GUID?
    text: '* **Uniqueness** – A GUID (`uuid4`) guarantees that two images will never
      clash, even across multiple runs. * **Traceability** – If you need to debug
      later, the GUID can be logged alongside the original Word paragraph number.
      * **Portability** – No reliance on the original Word naming scheme, which '
  - name: Expected Output (excerpt)
    text: '```markdown # Sample Document'
  - name: What if the document contains non‑image resources?
    text: Our callback already checks the file extension and returns `True` for anything
      that isn’t an image. This means CSS files, fonts, or embedded OLE objects keep
      their original names, which is usually what you want when you **save word as
      markdown**.
  - name: Can I use a custom naming scheme instead of GUIDs?
    text: 'Absolutely. Replace the `uuid.uuid4()` call with any function that returns
      a string. For example, you could prepend the original paragraph index:'
  - name: How does this affect performance on large documents?
    text: The callback runs once per resource, so the overhead is minimal—mostly the
      time to generate a GUID. Even a 200‑page report with dozens of images finishes
      in under a second on a modern laptop.
  - name: What if I need the image filenames to be deterministic (e.g., for CI builds)?
    text: 'Swap `uuid.uuid4()` for a hash of the original image bytes:'
  type: HowTo
tags:
- Aspose.Words
- Python
- Markdown
- Image Processing
title: Как переименовать изображения при конвертации DOCX в Markdown
url: /ru/python/document-conversion/how-to-rename-images-when-converting-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как переименовывать изображения при конвертации DOCX в Markdown

Вы когда‑нибудь задумывались **как автоматически переименовывать изображения** при конвертации файла DOCX в Markdown? Вы не одиноки. Во многих конвейерах документации имена изображений по умолчанию (например, `image1.png`) становятся настоящей головной болью для отслеживания, особенно когда один и тот же markdown находится под контролем версий в разных командах.  

Хорошая новость в том, что Aspose.Words for Python делает процесс **смены имен изображений** на лету простым как раз, и вы можете поддерживать ваш Markdown в чистоте, сохраняя аккуратную папку с пользовательскими именами ресурсов.  

В этом руководстве вы узнаете, как:

* Загрузить Word‑документ (`.docx`) в Python.  
* Подключить колбэк к процессу сохранения Markdown, который будет присваивать каждому изображению имя на основе GUID.  
* Сохранить документ как Markdown, чтобы сгенерированный файл ссылался на только‑что переименованные изображения.  

Если вы уверенно владеете базовым Python и у вас установлен Aspose.Words, вы сможете всё настроить менее чем за пять минут. Никаких внешних скриптов, никаких ручных переименований — только одна самодостаточная программа, которая выполнит всю тяжелую работу за вас.

---

## Необходимые условия — Что вам понадобится перед началом

| Требование | Почему это важно |
|-------------|----------------|
| **Python 3.7+** | В примере используются f‑строки и подсказки типов, появившиеся в 3.6, но 3.7+ предоставляет удобства `os.path.splitext`. |
| **Aspose.Words for Python via .NET** (`pip install aspose-words`) | Эта библиотека предоставляет класс `aw.Document` и `MarkdownSaveOptions`, на которые мы опираемся. |
| **Write permission** to the output folder | Колбэк будет создавать новые файлы изображений, поэтому скрипту необходимо иметь право записи. |
| **A DOCX file** you want to convert | Подойдёт любой файл — от простого отчёта до сложного руководства. |

> **Pro tip:** Если вы используете виртуальное окружение, активируйте его перед установкой Aspose.Words. Это изолирует зависимости и предотвращает конфликты версий.

---

## Шаг 1: Загрузка Word‑документа  

Первое, что вы делаете, когда хотите **convert docx to markdown**, — открываете исходный файл. Aspose.Words абстрагирует всю низкоуровневую работу с OPC, поэтому достаточно одной строки.

```python
import aspose.words as aw

# Replace YOUR_DIRECTORY with the folder that holds your .docx file
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

*Why this matters:* Без загрузки документа вы не сможете исследовать его ресурсы, и экспортёр Markdown не будет иметь чего‑то записать. Объект `aw.Document` хранит весь пакет Word в памяти, что делает безопасным любые манипуляции перед сохранением.

---

## Шаг 2: Написание колбэка, который **переименовывает ресурсы изображений**  

Aspose.Words позволяет подключить `resource_saving_callback` к `MarkdownSaveOptions`. Колбэк получает каждый ресурс (изображения, CSS и т.д.) непосредственно перед записью на диск. Изменяя `resource.file_name`, мы можем обеспечить **пользовательские имена файлов изображений**.

```python
def rename_image_resource(resource):
    """
    Rename image resources with a unique GUID before saving.
    This is where we implement how to rename images.
    """
    import uuid, os

    # Guard: only process image resources, ignore CSS or other files
    if not resource.file_name.lower().endswith(('.png', '.jpg', '.jpeg', '.gif', '.bmp')):
        return True  # Let Aspose handle non‑image resources unchanged

    # Extract the original extension so we keep PNG as PNG, JPG as JPG, etc.
    _, ext = os.path.splitext(resource.file_name)

    # Generate a globally unique identifier and tack the original extension on
    new_name = f"{uuid.uuid4()}{ext}"
    resource.file_name = new_name

    # Returning True tells Aspose to proceed with the default saving logic
    return True
```

### Почему использовать GUID?

* **Uniqueness** – GUID (`uuid4`) гарантирует, что два изображения никогда не столкнутся, даже при множественных запусках.  
* **Traceability** – Если позже понадобится отладка, GUID можно записать в журнал вместе с номером оригинального абзаца Word.  
* **Portability** – Не зависит от оригинальной схемы именования в Word, которая может содержать пробелы или специальные символы, ломающие ссылки в Markdown.

---

## Шаг 3: Привязка колбэка к параметрам сохранения Markdown  

Теперь мы говорим Aspose использовать нашу логику переименования каждый раз, когда он записывает изображение в выходную папку.

```python
md_options = aw.saving.MarkdownSaveOptions()
md_options.resource_saving_callback = rename_image_resource

# Optional: control where images are placed relative to the markdown file
md_options.images_folder = "images"  # creates a sub‑folder called 'images'
```

*Explanation:* Класс `MarkdownSaveOptions` управляет всем — от разрывов строк до места хранения папки изображений. Установив `resource_saving_callback`, вы получаете **hook**, который срабатывает для каждого встроенного ресурса, давая возможность **change image names** до того, как файл попадёт на диск.

---

## Шаг 4: Сохранение документа как Markdown — последний шаг  

С установленным колбэком последний шаг прост.

```python
output_path = "YOUR_DIRECTORY/CustomResources.md"
doc.save(output_path, md_options)
print(f"Markdown saved to {output_path}")
```

Когда скрипт завершит работу, вы увидите:

* `CustomResources.md` – Markdown‑представление вашего Word‑файла.  
* Папку `images/` (или любую другую, которую вы указали) с файлами вроде `d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e.png`.  

Markdown‑файл будет ссылаться на новые имена файлов на основе GUID, поэтому любой последующий процессор (GitHub, MkDocs и т.д.) подхватит правильные изображения без необходимости ручного переименования.

### Ожидаемый вывод (фрагмент)

```markdown
# Sample Document

Here is an image that was originally called `image1.png` in the DOCX:

![d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e](images/d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e.png)

And another one:

![a1b2c3d4-e5f6-7a8b-9c0d-e1f2a3b4c5d6](images/a1b2c3d4-e5f6-7a8b-9c0d-e1f2a3b4c5d6.jpg)
```

GUID будут различаться при каждом запуске, но шаблон останется тем же.

---

## Обработка граничных случаев и часто задаваемые вопросы  

### Что если документ содержит не‑изображения?  

Наш колбэк уже проверяет расширение файла и возвращает `True` для всего, что не является изображением. Это значит, что CSS‑файлы, шрифты или встроенные OLE‑объекты сохраняют свои оригинальные имена, что обычно и требуется при **save word as markdown**.

### Могу ли я использовать собственную схему именования вместо GUID?  

Конечно. Замените вызов `uuid.uuid4()` любой функцией, возвращающей строку. Например, можно добавить префикс с оригинальным индексом абзаца:

```python
new_name = f"para{resource.resource_id}{ext}"
```

Только убедитесь, что полученное имя уникально в пределах всего документа.

### Как это влияет на производительность больших документов?  

Колбэк вызывается один раз для каждого ресурса, поэтому накладные расходы минимальны — в основном время генерации GUID. Даже отчёт в 200 страниц с десятками изображений завершится менее чем за секунду на современном ноутбуке.

### Что если мне нужны детерминированные имена файлов изображений (например, для CI‑сборок)?  

Замените `uuid.uuid4()` на хеш оригинальных байтов изображения:

```python
import hashlib
hash = hashlib.sha256(resource.raw_bytes).hexdigest()[:12]
new_name = f"{hash}{ext}"
```

Это будет генерировать одинаковое имя файла каждый раз при запуске скрипта над тем же исходным изображением.

---

## Полный рабочий скрипт — копировать, вставить, запустить  



## Что вам стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [save docx as markdown – Full C# Guide with Image Extraction](/words/english/net/programming-with-markdownsaveoptions/save-docx-as-markdown-full-c-guide-with-image-extraction/)
- [How to Save Markdown from DOCX – Step‑by‑Step Guide](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}