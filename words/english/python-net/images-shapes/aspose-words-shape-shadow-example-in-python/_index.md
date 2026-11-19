---
category: general
date: 2026-11-18
description: Aspose.Words shape shadow example shows how to add a shadow to a Word
  shape using Python. Follow this step‑by‑step guide to modify and save the document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words shape shadow example
- python shape shadow
- Aspose.Words for Python
- modify shape shadow
- document manipulation Aspose
language: en
lastmod: 2026-11-18
og_description: Aspose.Words shape shadow example demonstrates adding a shadow to
  a Word shape with Python. Learn the complete code, why each step matters, and how
  to adapt it.
og_image_alt: Aspose.Words shape shadow example – Word document displaying a shape
  with a shadow applied using Python
og_title: Aspose.Words shape shadow example – Python guide
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Aspose.Words shape shadow example shows how to add a shadow to a Word
    shape using Python. Follow this step‑by‑step guide to modify and save the document.
  headline: Aspose.Words shape shadow example in Python
  type: TechArticle
- description: Aspose.Words shape shadow example shows how to add a shadow to a Word
    shape using Python. Follow this step‑by‑step guide to modify and save the document.
  name: Aspose.Words shape shadow example in Python
  steps:
  - name: Expected outcome
    text: Open `output.docx` in Microsoft Word. The first shape you added should now
      display a soft shadow that is offset by 2 pt horizontally and vertically, with
      a blur radius of 5 pt. All other content remains unchanged.
  - name: 'Alternative: Find a shape by name'
    text: 'If your document contains several shapes, you might prefer to locate a
      specific one:'
  - name: Working with multiple shapes
    text: 'If you need to apply the same shadow to every shape, iterate over the node
      collection:'
  - name: Applying a shadow to a specific shape type
    text: You can filter by `ShapeType` (e.g., `aw.ShapeType.IMAGE`). This is useful
      when you only want to affect pictures, not AutoShapes.
  - name: Handling documents without shapes
    text: The script already raises a clear `ValueError` if no shape is found. In
      production code you might log the issue and continue processing other files.
  - name: Compatibility notes
    text: '* The code works with **Aspose.Words for Python via .NET** version 23.10
      and later. * The shadow effect is supported in Word 2007+ (`.docx`). Older formats
      (`.doc`) will lose the effect after conversion.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Aspose.Words shape shadow example in Python
url: /python/images-shapes/aspose-words-shape-shadow-example-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words shape shadow example in Python

Aspose.Words shape shadow example demonstrates how to add a shadow effect to a shape in a Word document using Python. In this tutorial you’ll get a complete, runnable script that loads a document, configures the shadow, and saves the result.

Applying a shadow to a shape is a common way to improve visual hierarchy in reports, brochures, or invoices. The code below works with Aspose.Words for Python via .NET and requires no additional third‑party libraries.

## What you will learn

* How to load a `.docx` file with **Aspose.Words for Python**.  
* How to locate the first shape (including shapes inside tables or groups).  
* How to configure the shadow’s blur, horizontal offset, and vertical offset.  
* How to save the modified document while preserving all other content.  

**Prerequisites**

* Python 3.8 or later.  
* Aspose.Words for Python via .NET installed (`pip install aspose-words`).  
* A Word document (`input.docx`) that contains at least one shape (e.g., a picture, AutoShape, or text box).  

If you need to install the library, run:

```bash
pip install aspose-words
```

## Aspose.Words shape shadow example – overview

The following script is the full solution. It follows the four logical steps of a typical **document manipulation Aspose** workflow: load, locate, modify, and save.

```python
import aspose.words as aw

# ----------------------------------------------------------------------
# Step 1: Load the Word document
# ----------------------------------------------------------------------
# Replace YOUR_DIRECTORY with the path that contains input.docx.
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)

# ----------------------------------------------------------------------
# Step 2: Access the first shape (including descendants)
# ----------------------------------------------------------------------
# NodeType.SHAPE searches for any shape node. The third argument (True)
# tells Aspose.Words to search recursively through all child nodes.
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# Verify that a shape was found; raise a clear error if not.
if shape is None:
    raise ValueError("No shape found in the document. Ensure input.docx contains a shape.")

# ----------------------------------------------------------------------
# Step 3: Configure the shape's shadow
# ----------------------------------------------------------------------
# The Shadow object controls visual appearance. Adjust the properties
# to achieve the desired effect.
shape.shadow.blur = 5          # Softness of the shadow (0‑15 is typical)
shape.shadow.offset_x = 2      # Horizontal displacement in points
shape.shadow.offset_y = 2      # Vertical displacement in points

# Optional: Change shadow color or transparency if needed.
# shape.shadow.color = aw.Color.black
# shape.shadow.transparency = 0.5

# ----------------------------------------------------------------------
# Step 4: Save the modified document
# ----------------------------------------------------------------------
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)

print(f"Shadow applied successfully. Saved to {output_path}")
```

### Expected outcome

Open `output.docx` in Microsoft Word. The first shape you added should now display a soft shadow that is offset by 2 pt horizontally and vertically, with a blur radius of 5 pt. All other content remains unchanged.

## Step 1: Load the Word document

Loading a document is the first operation in any **Aspose.Words for Python** workflow. The `Document` class parses the file and builds an in‑memory object model. Because the library works on the .NET platform, it can handle large files efficiently.

*Why this matters:* Loading the document once and keeping a reference (`doc`) avoids repeated I/O, which improves performance when you need to apply multiple modifications.

## Step 2: Access the shape

Shapes can be direct children of the document body, or they can be nested inside tables, groups, or drawing canvases. Using `get_child(NodeType.SHAPE, 0, True)` searches recursively and returns the first matching shape.

*Why this matters:* The `True` flag ensures you don’t miss shapes that are hidden inside other nodes. If you omitted it, only top‑level shapes would be considered, and many real‑world documents would return `None`.

### Alternative: Find a shape by name

If your document contains several shapes, you might prefer to locate a specific one:

```python
shape = doc.get_child(aw.NodeType.SHAPE, lambda n: n.name == "MyLogo", True)
```

This snippet demonstrates a **python shape shadow** variation that filters by the shape’s `name` property.

## Step 3: Configure the shape's shadow

The `shadow` property of a `Shape` object gives you fine‑grained control over the visual effect. The three most commonly adjusted attributes are:

| Property | Typical range | Visual impact |
|----------|---------------|---------------|
| `blur`   | 0 – 15        | Higher values create a softer edge. |
| `offset_x` | –10 – 10   | Positive values move the shadow to the right. |
| `offset_y` | –10 – 10   | Positive values move the shadow downward. |

You can also modify `color`, `transparency`, `visible`, and `style`. The example sets a modest blur and a slight offset to keep the shadow subtle.

**Pro tip:** When a shape already has a shadow, the properties above overwrite the existing settings. If you need to preserve the original style, read the current values before changing them.

## Step 4: Save the modified document

Calling `doc.save()` writes the in‑memory representation back to a `.docx` file. Aspose.Words automatically updates all internal relationships, so the output file remains fully compatible with Microsoft Word.

*Why this matters:* Saving only once at the end of the process reduces the risk of file corruption and improves overall speed, especially when processing many documents in a batch job.

## Common variations and edge cases

### Working with multiple shapes

If you need to apply the same shadow to every shape, iterate over the node collection:

```python
for shp in doc.get_child_nodes(aw.NodeType.SHAPE, True):
    shp.shadow.blur = 5
    shp.shadow.offset_x = 2
    shp.shadow.offset_y = 2
```

### Applying a shadow to a specific shape type

You can filter by `ShapeType` (e.g., `aw.ShapeType.IMAGE`). This is useful when you only want to affect pictures, not AutoShapes.

```python
for shp in doc.get_child_nodes(aw.NodeType.SHAPE, True):
    if shp.shape_type == aw.ShapeType.IMAGE:
        shp.shadow.blur = 4
```

### Handling documents without shapes

The script already raises a clear `ValueError` if no shape is found. In production code you might log the issue and continue processing other files.

### Compatibility notes

* The code works with **Aspose.Words for Python via .NET** version 23.10 and later.  
* The shadow effect is supported in Word 2007+ (`.docx`). Older formats (`.doc`) will lose the effect after conversion.

## Conclusion

This **aspose.words shape shadow example** walks you through loading a Word file, locating a shape, configuring its shadow, and saving the result with **Aspose.Words for Python**. You now have a reusable pattern for any **document manipulation Aspose** scenario that involves visual enhancements.

Next, you might explore:

* Adding gradient fills or line styles to shapes (`modify shape shadow` and other visual properties).  
* Combining shadow configuration with text formatting to create fully styled templates.  
* Automating the process for a batch of documents using `os.listdir` and the pattern shown above.

Feel free to experiment with different blur levels, offsets, and colors to match your branding guidelines. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Add Shadow to Shape in Python – Complete Aspose.Words Tutorial](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [How to set shadow on a shape in Aspose.Words for Python](/words/english/python-net/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-for-python/)
- [How to save PNG and add shadow to shape with Aspose.Words](/words/english/python-net/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}