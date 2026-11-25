---
category: general
date: 2026-11-25
description: Add shadow to shape in a Word document with Python. Learn how to insert
  rectangle shape in Word and apply a transparent shadow using Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- insert rectangle shape word
- how to create word document python
- Aspose.Words Python
- shape formatting Python
language: en
lastmod: 2026-11-25
og_description: Add shadow to shape in a Word document using Python. This tutorial
  shows how to insert a rectangle shape in Word and set a 30 % transparent shadow
  with Aspose.Words.
og_image_alt: Add shadow to shape example in a Word document created by Python
og_title: Add shadow to shape in a Word document with Python – step‑by‑step guide
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
title: How to add shadow to shape in a Word document using Python
url: /python/images-shapes/how-to-add-shadow-to-shape-in-a-word-document-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to add shadow to shape in a Word document using Python

If you need to **add shadow to shape** in a Word document, this guide shows you a complete, runnable solution. You’ll see how to create a Word file, insert a rectangle shape, and apply a 30 % transparent shadow—all with the Aspose.Words for Python library.

Working with Word documents programmatically saves you from manual formatting and lets you generate reports, contracts, or marketing flyers at scale. By the end of this tutorial you’ll be able to answer “**how to create Word document python**” with a ready‑to‑run code sample.

## Prerequisites

Before you start, make sure you have:

* Python 3.8 or newer installed.
* An active Aspose.Words for Python license (the free trial works for evaluation).
* `aspose-words` package installed via `pip install aspose-words`.
* A folder where the output file can be written (replace `YOUR_DIRECTORY` in the code).

No additional dependencies are required.

## Step 1: Create a new Word document

The first step is to instantiate a `Document` object. This object represents the entire .docx file in memory.

```python
import aspose.words as aw

# Create an empty Word document
doc = aw.Document()
# DocumentBuilder provides a convenient API for adding content
builder = aw.DocumentBuilder(doc)
```

`DocumentBuilder` works like a virtual cursor. When you call its methods, the library inserts the corresponding elements at the current cursor location.

## Step 2: Insert rectangle shape word

Next you **insert rectangle shape word** using the builder’s `insert_shape` method. The method requires the shape type and its size in points (1 point = 1/72 inch).

```python
# Insert a rectangle shape that is 100 points wide and 50 points tall
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)
```

You can change the dimensions to match your design. The rectangle becomes part of the document’s drawing layer, which means you can later modify its fill, outline, or shadow.

## Step 3: Access the shape’s shadow format

Every drawing object exposes a `shadow_format` property that controls shadow appearance. Retrieve it so you can adjust transparency, offset, blur, and color.

```python
# Get the ShadowFormat object for the rectangle
shadow = shape.shadow_format
```

At this point the shape has the default shadow (no shadow). The `ShadowFormat` object holds all the parameters you need to create a realistic effect.

## Step 4: Make the shadow 30 % transparent

Transparency is expressed as a value between `0` (fully opaque) and `1` (fully transparent). Setting it to `0.3` yields a 30 % transparent shadow, which is often enough to add depth without overwhelming the text.

```python
# Apply a 30 % transparent shadow
shadow.transparency = 0.3
# Optional: adjust other shadow properties for a nicer look
shadow.visible = True               # Ensure the shadow is turned on
shadow.distance = 4                 # Distance of the shadow from the shape (points)
shadow.blur = 4                     # Amount of blur applied to the shadow
shadow.color = aw.Color.black       # Shadow color
```

These additional properties are not required, but they illustrate how you can fine‑tune the effect. The `visible` flag is essential; if you forget it, the shadow will not appear even though other settings are configured.

## Step 5: Save the document to view the result

Finally, write the document to disk. Opening the resulting `.docx` file in Microsoft Word or any compatible viewer shows the rectangle with the transparent shadow applied.

```python
# Save the document to the desired location
output_path = r"YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

When you open `output.docx`, you’ll see a plain rectangle with a subtle gray shadow offset to the bottom‑right. The shadow’s 30 % transparency makes the shape appear lifted off the page.

![Add shadow to shape example](placeholder-image.png){: .align-center alt="Add shadow to shape example in a Word document created with Python"}

## Full, runnable script

Putting all the pieces together gives you a self‑contained script you can copy, paste, and run immediately.

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

**Expected output:** Opening the generated `output.docx` displays a single page with a rectangle that casts a light, semi‑transparent shadow. No additional formatting is required.

## Common variations and edge cases

| Situation | How to adapt the code |
|-----------|-----------------------|
| **Different shape type** (e.g., ellipse) | Change `aw.drawing.ShapeType.RECTANGLE` to `aw.drawing.ShapeType.ELLIPSE`. |
| **Custom shadow color** | Set `shadow.color = aw.Color.from_argb(255, 128, 0, 0)` for a reddish shadow. |
| **Multiple shapes** | Call `builder.insert_shape` repeatedly; each call returns a separate `Shape` object you can style independently. |
| **Saving as PDF** | Replace `doc.save(output_path)` with `doc.save(output_path.replace('.docx', '.pdf'))` and use the `.pdf` extension. |
| **Running without a license** | The free trial adds a watermark to the first page. Acquire a license to remove it for production use. |

These variations demonstrate that the same pattern—create a document, insert a shape, adjust `shadow_format`, save—covers most automation scenarios.

## Tips and best practices

* **Reuse the builder**: Keep a single `DocumentBuilder` instance for the entire document to avoid unnecessary object creation.
* **Dispose resources**: In long‑running services, call `doc.dispose()` after saving to free native memory.
* **Validate output**: Use `doc.validate(aw.ValidationType.FULL_VALIDATION)` before saving if you need to ensure compliance with the Open XML standard.
* **Version compatibility**: The code works with Aspose.Words for Python ≥ 22.9. Ensure your package is up‑to‑date with `pip install --upgrade aspose-words`.

## Conclusion

You now know how to **add shadow to shape** in a Word document using Python. By following the five steps—create a document, **insert rectangle shape word**, configure the shadow, and save—you can automate polished document generation for reports, invoices, or marketing materials.  

From here you might explore other formatting options such as gradient fills, text wrapping, or converting the document to PDF. Each of those topics builds on the same `DocumentBuilder` and shape‑formatting concepts introduced in this tutorial.

Happy coding, and enjoy the visual depth that a simple shadow can bring to your automated Word documents!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to create rectangle shape in a Word document using Python](/words/english/python-net/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/)
- [Add Shadow to Shape in Python – Complete Aspose.Words Tutorial](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [Create Blank Word Document and Add Shadow to Shape – Full Python Guide](/words/english/python-net/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-pyth/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}