---
category: general
date: 2026-06-24
description: Как установить обратный вызов для экспорта изображений из DOCX при сохранении
  в Markdown. Узнайте, как извлекать изображения, извлекать SVG из Word и сохранять
  DOCX в Markdown с пользовательской обработкой.
draft: false
keywords:
- how to set callback
- export images from docx
- how to extract images
- save docx as markdown
- extract svg from word
language: ru
og_description: Как установить callback для экспорта изображений из DOCX при конвертации
  в Markdown. Это руководство покажет, как эффективно извлекать изображения и SVG.
og_title: Как установить обратный вызов для экспорта изображений из DOCX
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  headline: How to Set Callback for Exporting Images from DOCX
  type: TechArticle
- description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  name: How to Set Callback for Exporting Images from DOCX
  steps:
  - name: '**Deterministic names** – useful for version control or CDN publishing.'
    text: '**Deterministic names** – useful for version control or CDN publishing.'
  - name: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
    text: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
  - name: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
    text: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Conversion
title: Как установить обратный вызов для экспорта изображений из DOCX
url: /ru/python/content-extraction-and-manipulation/how-to-set-callback-for-exporting-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как установить callback для экспорта изображений из DOCX

Вы когда‑нибудь задумывались **как установить callback**, чтобы **экспортировать изображения из DOCX** при конвертации в Markdown? Вы не одиноки. Многие разработчики сталкиваются с проблемой, когда стандартная конвертация сохраняет все изображения в общую папку или, что ещё хуже, полностью теряет SVG‑графику.  

В этом руководстве мы пройдёмся по полностью готовому решению, которое отвечает на вопрос «как установить callback», показывает **как извлекать изображения**, и даже охватывает **извлечение SVG из Word**. К концу вы сможете **сохранять DOCX как Markdown** с пользовательской схемой именования для каждого ресурса изображения — без ручных правок.

## Что вы узнаете

- Почему callback — самый чистый способ управлять именами файлов изображений во время конвертации.  
- Как подключиться к `MarkdownSaveOptions.resource_saving_callback` в Aspose.Words.  
- Пошаговый код, который извлекает **PNG**, **JPG**, **SVG** и любые другие встроенные ресурсы.  
- Советы по обработке конфликтов имён, больших файлов и особенностей путей на разных платформах.  

> **Pro tip:** Если вы уже используете Aspose.Words в более крупном конвейере, вы можете добавить этот callback, не меняя остальной код.

---

![How to set callback diagram](https://example.com/images/how-to-set-callback.png "how to set callback")

## Требования

- Python 3.8+ (пример использует f‑строки, поэтому подойдёт 3.6+).  
- Установлен пакет `aspose-words` (`pip install aspose-words`).  
- DOCX‑файл, содержащий растровые изображения **и** векторную графику (SVG).  
- Базовое знакомство с функциями Python и вводом‑выводом файлов.

Если всё готово, давайте погрузимся.

---

## Как установить callback для экспорта изображений из DOCX

Суть решения заключается в **resource‑saving callback**. Aspose.Words вызывает этот делегат для каждого изображения или SVG, которое он хочет записать при вызове `document.save`. Возвращая кортеж `(new_name, data)`, вы задаёте как имя файла, так и его байтовый контент.

```python
import aspose.words as aw
import os
import hashlib

# Step 1: Load the source document
document = aw.Document("YOUR_DIRECTORY/input.docx")
```

### Почему callback?

Без callback Aspose.Words создаёт файлы с именами `image1.png`, `image2.svg` и т.д., помещая их в папку рядом с файлом Markdown. Это приемлемо для быстрых демонстраций, но в продакшене часто требуется:

1. **Детерминированные имена** — полезно для контроля версий или публикации через CDN.  
2. **Избежание конфликтов** — два изображения с одинаковым оригинальным именем не перезапишут друг друга.  
3. **Пользовательские структуры папок** — возможно, вы хотите хранить все ресурсы в `/assets/docs/`.

Callback даёт вам полный контроль над этими тремя аспектами.

---

## Экспорт изображений из DOCX с использованием resource callback

Ниже представлена реализация callback. Он хеширует бинарные данные, чтобы получить уникальный суффикс, сохраняет оригинальное расширение файла и возвращает новое имя вместе с необработанными байтами.

```python
def resource_callback(resource):
    """
    Called for every image/SVG that MarkdownSaveOptions wants to write.
    Returns a tuple (new_name, data) to control the saved file name.
    """
    # Preserve the original extension (.png, .svg, …)
    extension = os.path.splitext(resource.name)[1]

    # Compute a short hash of the image bytes – guarantees uniqueness
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]

    # Build a deterministic, collision‑free filename
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data
```

#### Обработка граничных случаев

- **Большие файлы:** SHA‑256 работает с любыми размерами; хеш вычисляется в памяти, поэтому учитывайте ограничения памяти при обработке огромных PDF.  
- **Отсутствующие расширения:** В некоторых старых файлах Word изображения могут храниться без явного расширения. В этом случае `extension` будет пустым; можно задать по умолчанию `.bin` или проанализировать первые несколько байтов, чтобы определить формат.  
- **Неизображённые ресурсы:** Callback вызывается для каждого внешнего ресурса (например, OLE‑объекты). Если вам нужны только изображения/SVG, отфильтруйте по `resource.type` перед дальнейшей обработкой.

---

## Как извлекать изображения и SVG из Word

Теперь подключим callback к конвейеру сохранения Markdown. Объект `MarkdownSaveOptions` предоставляет свойство `resource_saving_callback` именно для этой цели.

```python
# Step 2: Configure Markdown save options to use the callback
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.resource_saving_callback = resource_callback

# Optional: set the folder where images will be placed relative to the .md file
markdown_options.resource_folder = "assets/images"
```

Установка `resource_folder` необязательна, но часто удобна. Если её опустить, изображения окажутся рядом с файлом Markdown, что может захламить корень проекта.

### Сохранение документа

```python
# Step 3: Save the document as Markdown, letting the callback store the resources
output_md_path = "YOUR_DIRECTORY/output.md"
document.save(output_md_path, markdown_options)
print(f"Markdown saved to {output_md_path}")
```

При запуске скрипта вы увидите набор файлов, например:

```
assets/images/img_a1b2c3d4e5.png
assets/images/img_f6g7h8i9j0.svg
```

А сгенерированный `output.md` будет содержать ссылки на изображения, указывающие точно на эти имена файлов:

```markdown
![Image](assets/images/img_a1b2c3d4e5.png)
```

Это демонстрация **как извлекать изображения** — каждая картинка, растровая или векторная, теперь отдельный уникально именованный ресурс.

---

## Сохранить DOCX как Markdown с пользовательской обработкой изображений

Собрав всё вместе, вот полный скрипт, который можно скопировать в файл `convert_docx_to_md.py`:

```python
import aspose.words as aw
import os
import hashlib

def resource_callback(resource):
    """Control the naming of each exported image/SVG."""
    extension = os.path.splitext(resource.name)[1] or ".bin"
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data

def convert_docx_to_markdown(input_path, output_md_path, image_folder="assets/images"):
    # Load the DOCX
    document = aw.Document(input_path)

    # Set up Markdown options with our callback
    md_options = aw.saving.MarkdownSaveOptions()
    md_options.resource_saving_callback = resource_callback
    md_options.resource_folder = image_folder

    # Ensure the output directory exists
    os.makedirs(os.path.dirname(output_md_path), exist_ok=True)
    os.makedirs(os.path.join(os.path.dirname(output_md_path), image_folder), exist_ok=True)

    # Perform the conversion
    document.save(output_md_path, md_options)
    print(f"✅ Conversion complete! Markdown at: {output_md_path}")

if __name__ == "__main__":
    # Adjust these paths to your environment
    INPUT_DOCX = "YOUR_DIRECTORY/input.docx"
    OUTPUT_MD = "YOUR_DIRECTORY/output.md"
    convert_docx_to_markdown(INPUT_DOCX, OUTPUT_MD)
```

**Почему это работает:**  
- `resource_callback` гарантирует, что каждое изображение получит уникальное, воспроизводимое имя.  
- `resource_folder` поддерживает чистоту Markdown, отделяя ресурсы.  
- Вызовы `os.makedirs` защищают от ошибок «папка не найдена», когда скрипт запускается на новой машине.

---

## Извлечение SVG из Word — что насчёт векторной графики?

SVG обрабатываются так же, как PNG, потому что они просто ещё один `resource`. Единственное отличие — в некоторых старых версиях Word SVG встраиваются как *OfficeArt*‑объекты, которые Aspose.Words автоматически конвертирует в растровый PNG, если явно не включить флаг **preserve SVG**:

```python
md_options.export_svg = True  # Keep original SVG markup
```

Добавьте эту строку перед сохранением, и callback будет получать ресурсы с расширением `.svg`, сохраняя чёткие векторные данные — идеально для адаптивной веб‑документации.

---

## Часто задаваемые вопросы и подводные камни

| Вопрос | Ответ |
|----------|--------|
| **Что если два изображения идентичны?** | Хеш SHA‑256 будет одинаковым, поэтому имена файлов конфликтуют. Если нужны обе копии, включите оригинальное `resource.name` в расчёт хеша (например, `hash(resource.name + resource.data)`). |
| **Можно ли менять папку в зависимости от типа файла?** | Да. Внутри `resource_callback` можно проверить `extension` и вернуть путь вроде `f"png/{new_name}"` для растровых изображений и `f"svg/{new_name}"` для векторных. |
| **Работает ли это на Linux/macOS?** | Абсолютно. Код использует `os.path`, который абстрагирует разделители путей. Просто убедитесь, что файл лицензии Aspose.Words (`aspose.words.lic`) доступен, если вы используете платную версию. |
| **Какова нагрузка на память при работе с огромными документами?** | Callback получает **полный массив байтов** для каждого ресурса, то есть изображение временно хранится в памяти. Для многогигабайтных файлов имеет смысл потоково записывать данные на диск внутри callback, а не возвращать их полностью. |

---

## Заключение

Теперь вы знаете **как установить callback**, чтобы контролировать извлечение изображений при **сохранении DOCX как Markdown**. Этот подход позволяет **экспортировать изображения из DOCX**, **извлекать SVG из Word** и поддерживать ваш Markdown чистым и детерминированным.  

В одном самодостаточном скрипте мы рассмотрели загрузку документа, определение resource‑saving callback, настройку `MarkdownSaveOptions` и обработку граничных случаев, таких как конфликты имён и векторная графика. Результат — набор уникально именованных ресурсов рядом с идеально связанным файлом Markdown, готовый для статических генераторов сайтов, конвейеров документации или любого рабочего процесса, требующего чистых, переиспользуемых активов.  

**Следующие шаги?**  
- Попробуйте связать это со статическим генератором сайтов, например MkDocs, чтобы автоматически публиковать документы из Word.  
- Поэкспериментируйте с `markdown_options.export_images_as_base64 = True`, если предпочитаете встроенные изображения вместо внешних файлов.  
- Углубитесь в другие callback‑и Aspose.Words (например, `document_saving_callback`), чтобы управлять самим выводом Markdown.  

Есть дополнительные вопросы о **как извлекать изображения** из других форматов Office или нужна помощь в настройке callback под конкретную схему именования? Оставляйте комментарий ниже, и happy coding!

## Что стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом пособии. Каждый ресурс включает полностью рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Как переименовать изображения при конвертации DOCX в Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)
- [Как сохранить Markdown из DOCX — пошаговое руководство](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}