---
category: general
date: 2026-09-27
description: Learn how to set shadow on a shape with Aspose.Words for Python. This
  guide covers add shadow to shape, apply shadow effect, and set shadow color.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to set shadow
- add shadow to shape
- apply shadow effect
- set shadow color
- how to add shadow
language: en
lastmod: 2026-09-27
og_description: How to set shadow on a shape using Aspose.Words for Python. Follow
  the step‑by‑step guide to add shadow to shape, apply shadow effect, and set shadow
  color.
og_image_alt: Screenshot showing how to set shadow on a shape in a Word document
og_title: How to set shadow on a shape in Aspose.Words for Python
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to set shadow on a shape with Aspose.Words for Python. This
    guide covers add shadow to shape, apply shadow effect, and set shadow color.
  headline: How to set shadow on a shape in Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Shapes
- Shadow effect
title: How to set shadow on a shape in Aspose.Words for Python
url: /python/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to set shadow on a shape in Aspose.Words for Python

If you need to **how to set shadow** for a drawing object, this guide shows the complete process. You’ll see how to add shadow to shape, configure the shadow’s blur, offset, and color, and save the updated document without leaving the code.

The tutorial assumes you already have a basic Aspose.Words for Python environment. By the end of the article you will be able to apply a professional‑looking shadow effect to any shape in a DOCX file.

## Prerequisites

Before you start, make sure you have:

* Python 3.8+ installed.
* Aspose.Words for Python via .NET (`pip install aspose-words`) installed.
* A Word document (`input.docx`) that contains at least one shape (e.g., a rectangle or picture).  
  If the document is empty, the code will create a new shape for demonstration.

These items guarantee that the subsequent steps run without import errors.

## Step 1: Load or create the Word document

The first operation is to obtain a `Document` object. You can either load an existing file or create a fresh one.

```python
import aspose.words as aw

# Load an existing document, or create a new blank document if the file does not exist.
try:
    doc = aw.Document("YOUR_DIRECTORY/input.docx")
except Exception:
    doc = aw.Document()          # Creates an empty document
    # Optional: add a paragraph so the document is not completely empty.
    builder = aw.DocumentBuilder(doc)
    builder.writeln("Document created for shadow demo.")
```

*Why this step matters*: The `Document` object is the entry point for all Word‑processing operations. Without it you cannot access shapes or apply visual effects.

## Step 2: Retrieve the target shape

To manipulate a shape’s appearance you need a reference to the shape node. The example below fetches the first shape found in the document hierarchy.

```python
# Retrieve the first shape in the document tree.
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# If the document has no shapes, create one for demonstration purposes.
if shape is None:
    builder = aw.DocumentBuilder(doc)
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 100)
    shape.wrap_type = aw.drawing.WrapType.INLINE
```

*Why this step matters*: `add shadow to shape` requires a concrete shape object. The code safely handles the edge case where the document contains no shapes, ensuring the tutorial works for every reader.

## Step 3: Configure the shadow appearance

Now you can **apply shadow effect** by adjusting the `shadow` property of the shape. The following settings give a subtle, dark shadow.

```python
# Set the shadow blur radius (softness). Larger values produce a more diffused shadow.
shape.shadow.blur = 5.0

# Horizontal displacement of the shadow in points.
shape.shadow.offset_x = 2.0

# Vertical displacement of the shadow in points.
shape.shadow.offset_y = 2.0

# Set the shadow color. This demonstrates **set shadow color** to black.
shape.shadow.color = aw.Color.black

# Enable the shadow (some older versions require explicit visibility).
shape.shadow.visible = True
```

*Why each property matters*:

| Property | Effect |
|----------|--------|
| `blur`   | Controls how fuzzy the shadow looks. |
| `offset_x` / `offset_y` | Determines the direction and distance from the shape. |
| `color`  | Defines the hue of the shadow; you can use any `aw.Color`. |
| `visible`| Ensures the shadow is rendered in the output file. |

You can replace `aw.Color.black` with `aw.Color.from_argb(255, 0, 0, 0)` for a custom RGBA value, or any other predefined color.

## Step 4: Save the modified document

After configuring the shadow, persist the changes to a new file.

```python
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved with shadow effect at: {output_path}")
```

When you open `output.docx` in Microsoft Word, the selected shape will display a soft black shadow displaced 2 pt right and 2 pt down.

## Full working example

Putting all steps together gives a self‑contained script you can copy‑paste into your IDE.

```python
import aspose.words as aw

def add_shadow_to_first_shape(input_path: str, output_path: str):
    # Load or create the document.
    try:
        doc = aw.Document(input_path)
    except Exception:
        doc = aw.Document()
        builder = aw.DocumentBuilder(doc)
        builder.writeln("Document created for shadow demo.")

    # Retrieve the first shape; create one if none exist.
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
    if shape is None:
        builder = aw.DocumentBuilder(doc)
        shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 100)
        shape.wrap_type = aw.drawing.WrapType.INLINE

    # Apply shadow settings.
    shape.shadow.blur = 5.0
    shape.shadow.offset_x = 2.0
    shape.shadow.offset_y = 2.0
    shape.shadow.color = aw.Color.black
    shape.shadow.visible = True

    # Save the result.
    doc.save(output_path)
    print(f"Shadow applied and saved to {output_path}")

# Example usage
if __name__ == "__main__":
    add_shadow_to_first_shape(
        input_path="YOUR_DIRECTORY/input.docx",
        output_path="YOUR_DIRECTORY/output.docx"
    )
```

Running the script produces `output.docx` where the first shape carries the configured shadow.

## Common pitfalls and how to avoid them

| Issue | Reason | Fix |
|-------|--------|-----|
| `shape` is `None` even after loading a document | The document contains no drawing objects. | Use the fallback shape creation block shown in Step 2. |
| Shadow does not appear in Word | `shape.shadow.visible` left as `False` or the document was saved in an older format (e.g., `.doc`). | Ensure `visible = True` and save as `.docx`. |
| Color looks different than expected | The document’s theme overrides explicit colors. | Set `shape.shadow.color` after disabling theme overrides, or use `aw.Color.from_argb`. |

Addressing these edge cases makes the solution robust for production code.

## Extending the effect (next steps)

Now that you know **how to add shadow**, you can explore related enhancements:

* **apply shadow effect** with gradient or multiple shadows by adjusting `shape.shadow` sub‑properties.
* Use **set shadow color** dynamically based on user input or theme colors.
* Combine **add shadow to shape** with other formatting actions such as rotation, line style, or 3‑D effects.
* Automate shadow addition for every shape in a document by iterating through `doc.get_child_nodes(aw.NodeType.SHAPE, True)`.

These extensions let you build sophisticated document‑generation pipelines that produce polished, visually consistent outputs.

## Conclusion

You now have a complete, runnable solution for **how to set shadow** on a shape using Aspose.Words for Python. The guide covered loading a document, retrieving or creating a shape, configuring blur, offset, and **set shadow color**, and finally saving the file. Apply the pattern to any shape in your automation projects and experiment with additional visual tweaks to meet your design requirements.

--- 

*Feel free to adapt the code for other shape types, colors, or offset values. If you encounter any issues, reviewing the “Common pitfalls” table is a good first step.*


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Add shadow to shape in C# – Complete Guide to Apply Shadow Effect](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-c-complete-guide-to-apply-shadow-effe/)
- [Add shadow to shape in Word – Complete Aspose.Words Guide](/words/english/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/)
- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}