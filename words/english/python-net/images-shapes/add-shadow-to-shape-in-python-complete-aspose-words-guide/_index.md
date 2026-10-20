---
category: general
date: 2026-08-11
description: Add shadow to shape using Aspose.Words for Python. Learn how to add shape
  shadow, apply blur to shape, and customize offset and color.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- add shape shadow
- apply blur to shape
- Aspose.Words shadow effect
- Python Word shape styling
language: en
lastmod: 2026-08-11
og_description: Add shadow to shape with Aspose.Words for Python. This guide shows
  you how to apply blur to shape, set offsets, and choose shadow colors in just a
  few lines of code.
og_image_alt: Word document screenshot showing a shape with a black shadow applied
og_title: Add shadow to shape in Python – step‑by‑step Aspose.Words tutorial
schemas:
- author: Aspose
  dateModified: '2026-08-11'
  description: Add shadow to shape using Aspose.Words for Python. Learn how to add
    shape shadow, apply blur to shape, and customize offset and color.
  headline: Add shadow to shape in Python – complete Aspose.Words guide
  type: TechArticle
- description: Add shadow to shape using Aspose.Words for Python. Learn how to add
    shape shadow, apply blur to shape, and customize offset and color.
  name: Add shadow to shape in Python – complete Aspose.Words guide
  steps:
  - name: Adding shadow to a specific shape by name
    text: 'If your document contains several shapes, you may want to target one by
      its `name` property:'
  - name: Skipping non‑visual nodes
    text: Sometimes a shape node can be a placeholder (e.g., a drawing canvas without
      visual content). Guard against this by checking `shape.is_image` or `shape.is_picture_frame`
      before applying the shadow.
  - name: Working with grouped shapes
    text: When shapes are grouped, the group itself is a `Shape` node. To apply a
      shadow to each member, iterate through `shape.get_child_nodes(aw.NodeType.SHAPE,
      True)`.
  - name: What’s next?
    text: '- Explore **apply blur to shape** for other effects like glow or soft edges.
      - Combine shadows with **shape borders** or **reflection** to create richer
      graphics. - Convert the edited document to PDF (`doc.save("output.pdf", aw.SaveFormat.PDF)`)
      for distribution.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Add shadow to shape in Python – complete Aspose.Words guide
url: /python/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Add shadow to shape in Python – complete Aspose.Words guide

If you need to **add shadow to shape** in a Word document, this tutorial shows you exactly how to do it with Aspose.Words for Python. Whether you’re building a report generator or a document‑templating service, you’ll learn to add shape shadow, apply blur to shape, and fine‑tune the shadow’s appearance in just a few lines of code.

The guide covers everything you need: required imports, locating the target shape (including nested nodes), configuring shadow properties, handling common edge cases, and saving the modified document. By the end you’ll have a reusable snippet you can drop into any Python project that works with .docx files.

## Prerequisites

Before you start, make sure you have:

- **Python 3.8+** installed.
- **Aspose.Words for Python via .NET** (install with `pip install aspose-words`).
- A Word document (`input.docx`) that contains at least one shape (e.g., a rectangle, picture, or SmartArt).
- Basic familiarity with Python and the Aspose.Words object model.

## Step 1: Import Aspose.Words and open the document

The first step is to import the `aspose.words` package (commonly aliased as `aw`) and load the source document.

```python
import aspose.words as aw

# Load the Word document from the file system
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)
```

*Why this matters*: Opening the document gives you access to the node tree where shapes live. The `aw.Document` class is the entry point for all further manipulations.

## Step 2: Locate the first shape (including nested nodes)

Shapes can be direct children of a `Paragraph` or nested inside other containers (like tables). Using `get_child` with the `is_deep` flag set to `True` ensures you retrieve the first shape regardless of nesting.

```python
# Retrieve the first shape in the document, searching recursively
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

if shape is None:
    raise ValueError("No shape found in the document. Add a shape before applying a shadow.")
```

*Why this matters*: The `add shape shadow` operation requires a `Shape` object. The deep search prevents you from missing shapes that are hidden inside tables or group containers.

## Step 3: Enable the shadow and set basic properties

Aspose.Words represents a shadow with several properties. First, turn the shadow on by setting `shadow_visible` to `True`.

```python
# Enable the shadow effect
shape.shadow_visible = True
```

Now you can configure the blur radius, offsets, and color.

## Step 4: Apply blur to shape and define offset values

The blur radius controls how soft the shadow appears. A value of `5.0` gives a noticeable but not overwhelming blur. Offsets move the shadow horizontally and vertically.

```python
# Apply blur to shape – this is the "apply blur to shape" part
shape.shadow_blur = 5.0          # Blur radius in points

# Define horizontal (X) and vertical (Y) offsets
shape.shadow_offset_x = 2.0     # Move shadow 2 points to the right
shape.shadow_offset_y = 2.0     # Move shadow 2 points down
```

*Why this matters*: Adjusting `shadow_blur` and the offset values lets you create realistic depth effects that match your document’s visual style.

## Step 5: Choose the shadow color (add shape shadow with custom color)

You can use any `aw.Color`. Here we select black, but you can replace it with `aw.Color.red`, `aw.Color.from_argb(255, 0, 120, 215)`, etc.

```python
# Set the shadow color – black in this example
shape.shadow_color = aw.Color.black
```

*Why this matters*: The color determines how the shadow interacts with surrounding content. Darker shadows are more visible on light backgrounds, while lighter shades work better on dark pages.

## Step 6: Save the updated document

Finally, write the changes back to disk. You can overwrite the original file or create a new one.

```python
output_path = "YOUR_DIRECTORY/output_with_shadow.docx"
doc.save(output_path)

print(f"Shadow applied successfully. Saved to {output_path}")
```

When you open `output_with_shadow.docx` in Microsoft Word, the first shape will display a soft black shadow with the specified blur and offset.

## Full, runnable example

Putting everything together, here’s a self‑contained script you can run immediately:

```python
import aspose.words as aw

def add_shadow_to_first_shape(input_path: str, output_path: str,
                              blur: float = 5.0,
                              offset_x: float = 2.0,
                              offset_y: float = 2.0,
                              color: aw.Color = aw.Color.black) -> None:
    """
    Loads a Word document, finds the first shape (deep search),
    and applies a shadow effect.

    Parameters
    ----------
    input_path : str
        Path to the source .docx file.
    output_path : str
        Path where the modified document will be saved.
    blur : float, optional
        Blur radius for the shadow. Default is 5.0 points.
    offset_x : float, optional
        Horizontal offset of the shadow. Default is 2.0 points.
    offset_y : float, optional
        Vertical offset of the shadow. Default is 2.0 points.
    color : aw.Color, optional
        Shadow color. Default is black.
    """
    # Load the document
    doc = aw.Document(input_path)

    # Retrieve the first shape, searching recursively
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

    if shape is None:
        raise ValueError("No shape found in the document. Insert a shape before calling this function.")

    # Enable shadow and configure its appearance
    shape.shadow_visible = True
    shape.shadow_blur = blur
    shape.shadow_offset_x = offset_x
    shape.shadow_offset_y = offset_y
    shape.shadow_color = color

    # Save the result
    doc.save(output_path)

if __name__ == "__main__":
    INPUT_DOC = "YOUR_DIRECTORY/input.docx"
    OUTPUT_DOC = "YOUR_DIRECTORY/output_with_shadow.docx"
    add_shadow_to_first_shape(INPUT_DOC, OUTPUT_DOC)
```

**Expected output**: Opening `output_with_shadow.docx` shows the first shape with a subtle black shadow that is blurred, offset by 2 pt horizontally and vertically, matching the parameters you passed.

## Handling multiple shapes and edge cases

### Adding shadow to a specific shape by name

If your document contains several shapes, you may want to target one by its `name` property:

```python
target_name = "MyRectangle"
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)  # start with first shape
while shape is not None and shape.name != target_name:
    shape = shape.next_sibling(aw.NodeType.SHAPE)

if shape is None:
    raise ValueError(f"Shape named '{target_name}' not found.")
```

### Skipping non‑visual nodes

Sometimes a shape node can be a placeholder (e.g., a drawing canvas without visual content). Guard against this by checking `shape.is_image` or `shape.is_picture_frame` before applying the shadow.

```python
if not shape.is_image and not shape.is_picture_frame:
    # Proceed only if the shape can display a shadow
    shape.shadow_visible = True
```

### Working with grouped shapes

When shapes are grouped, the group itself is a `Shape` node. To apply a shadow to each member, iterate through `shape.get_child_nodes(aw.NodeType.SHAPE, True)`.

```python
if shape.is_group:
    for child in shape.get_child_nodes(aw.NodeType.SHAPE, True):
        child.shadow_visible = True
        child.shadow_blur = blur
        child.shadow_offset_x = offset_x
        child.shadow_offset_y = offset_y
        child.shadow_color = color
```

These variations ensure your code works robustly across different document layouts.

## Pro tips for perfect shadows

- **Consistency**: Use the same blur radius and offset for all shapes in a report to keep the visual language consistent.
- **Performance**: Applying shadows to dozens of high‑resolution pictures can increase file size. Test the output size if you plan to generate PDFs later.
- **Color contrast**: On dark page backgrounds, consider a lighter shadow (`aw.Color.gray`) to maintain visibility.
- **Preview**: Word’s “Shadow” UI mirrors the Aspose.Words properties, so you can experiment manually, then copy the resulting values into your script.

## Conclusion

You now know how to **add shadow to shape** in a Word document using Aspose.Words for Python. The guide covered locating a shape, enabling the shadow, **add shape shadow** with custom blur, offsets, and color, and saving the result. With the reusable function above, you can integrate this effect into any document‑generation pipeline.

### What’s next?

- Explore **apply blur to shape** for other effects like glow or soft edges.
- Combine shadows with **shape borders** or **reflection** to create richer graphics.
- Convert the edited document to PDF (`doc.save("output.pdf", aw.SaveFormat.PDF)`) for distribution.

Feel free to experiment with different colors, blur levels, and offset values to match your branding guidelines. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}