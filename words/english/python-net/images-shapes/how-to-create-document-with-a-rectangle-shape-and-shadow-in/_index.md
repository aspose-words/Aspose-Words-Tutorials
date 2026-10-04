---
category: general
date: 2026-10-04
description: How to create document in Python and add shadow to shape using Aspose.Words.
  Learn to set shadow color, insert rectangle shape, and customize outer shadow.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create document
- add shadow to shape
- set shadow color
- insert rectangle shape
- how to add shadow
language: en
lastmod: 2026-10-04
og_description: How to create document in Python and add shadow to shape. This guide
  shows you how to set shadow color, insert rectangle shape, and apply an outer shadow
  using Aspose.Words.
og_image_alt: Python code inserting a rectangle shape with a visible shadow into a
  Word document
og_title: How to create document with a rectangle shape and shadow in Python
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  headline: How to create document with a rectangle shape and shadow in Python
  type: TechArticle
- description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  name: How to create document with a rectangle shape and shadow in Python
  steps:
  - name: Why does the shadow sometimes appear invisible?
    text: The shadow is only rendered if `shadow.visible` is set to `True` **and**
      the shape’s `wrap_type` allows it to be displayed. An inline shape works reliably;
      floating shapes may require additional layout adjustments.
  - name: How can I change the shadow color to match a brand palette?
    text: 'Replace `aw.drawing.Color.black` with a custom RGB value:'
  - name: What if I need the shape to appear behind text?
    text: Set the wrap type to `WrapType.BEHIND` and adjust the `z_order_position`
      if necessary. Keep in mind that some viewers may render behind‑text shapes differently.
  - name: Can I apply the same shadow settings to multiple shapes?
    text: Yes. Create a helper function that configures the shadow and call it for
      each shape you insert. This promotes code reuse and ensures consistent styling.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: How to create document with a rectangle shape and shadow in Python
url: /python/images-shapes/how-to-create-document-with-a-rectangle-shape-and-shadow-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create document with a rectangle shape and shadow in Python

If you need to **how to create document** that contains a styled rectangle, this guide provides a complete solution. You’ll see how to **add shadow to shape**, set the shadow’s color, and control its offset and blur—all with Aspose.Words for Python. By the end of the tutorial you can generate a `.docx` file that looks polished and ready for distribution.

The steps below cover everything from installing the library to customizing the shadow appearance. No external documentation is required; the code is ready to copy, run, and adapt to your own projects. You’ll also learn how to **insert rectangle shape**, choose an **outer shadow style**, and handle common pitfalls such as invisible shadows or incorrect wrap settings.

## Prerequisites

Before you start, make sure you have:

* Python 3.8 or newer installed.
* An active Aspose.Words for Python license (or a free evaluation key).
* Basic familiarity with Python scripting.
* Access to a file system location where the generated document will be saved.

You can install the SDK with pip:

```bash
pip install aspose-words
```

## Step 1: Import the library and create a new blank document

Creating a new document is the first action in any Word automation scenario. The `aw.Document()` constructor gives you an empty file that you can populate with text, images, or shapes.

```python
import aspose.words as aw

# Create a new blank document
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

The `DocumentBuilder` object simplifies the insertion of content. It keeps track of the current cursor position, so you can add elements sequentially without manually managing sections.

## Step 2: Insert a rectangle shape of the desired size

A rectangle shape acts as a container for visual elements. You can define its width and height in points (1 pt ≈ 1/72 in).

```python
# Insert a rectangle shape that is 150 pt wide and 80 pt tall
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

At this point the shape has no visual styling, so it appears as a plain outline. The next steps will give it depth and color.

## Step 3: Set the shape to flow inline with the surrounding text

When a shape is **inline**, it behaves like a character in a paragraph. This ensures the rectangle stays where you expect it in the document layout.

```python
# Make the shape inline so it follows the text flow
rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE
```

If you prefer the shape to float over the text, you could use `WrapType.SQUARE` or `WrapType.TOP_BOTTOM`, but for most reports an inline shape keeps the layout predictable.

## Step 4: Make the shadow visible and choose its color

A shadow that is not visible provides no visual benefit. The `visible` flag activates the effect, and the `color` property determines its hue. Using black gives a classic, subtle depth.

```python
# Enable the shadow and set its color to black
rectangle_shape.shadow.visible = True
rectangle_shape.shadow.color = aw.drawing.Color.black
```

You can replace `aw.drawing.Color.black` with any other color, such as `aw.drawing.Color.gray` or a custom RGB value (`aw.drawing.Color.from_argb(255, 128, 128, 128)`).

## Step 5: Define the shadow’s offset and blur to give it depth

The offset controls how far the shadow is displaced from the shape, while the blur radius softens the edges. Small values create a crisp shadow; larger values produce a softer look.

```python
# Horizontal and vertical offset of 5 pt each
rectangle_shape.shadow.offset_x = 5
rectangle_shape.shadow.offset_y = 5

# Blur radius of 3 pt for a gentle feather
rectangle_shape.shadow.blur = 3
```

Experiment with these numbers to match your design guidelines. For a heavy drop shadow you might increase both offset and blur.

## Step 6: Choose an outer shadow style

Aspose.Words offers several shadow styles, such as `INNER`, `OUTER`, and `PERSPECTIVE`. The **outer** style places the shadow outside the shape’s border, which is ideal for a clean, professional appearance.

```python
# Apply an outer shadow style
rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

If you need a more dramatic effect, try `ShadowStyle.PERSPECTIVE`—it adds a three‑dimensional tilt.

## Step 7: Save the document with the shaped shadow

Saving finalizes the file and writes all formatting to disk. Choose a directory you have write permissions for, and give the file a descriptive name.

```python
# Save the document to the desired location
output_path = "output/ShapeWithShadow.docx"
document.save(output_path)
print(f"Document saved to {output_path}")
```

Running the script produces a Word file that contains a rectangle with a visible, colored shadow. Open the file in Microsoft Word or LibreOffice to verify the result.

## Full runnable example

Below is the complete script that incorporates every step discussed. Copy the code into a file named `create_shadowed_shape.py` and execute it with `python create_shadowed_shape.py`.

```python
import aspose.words as aw
import os

def main():
    # Ensure the output directory exists
    output_dir = "output"
    os.makedirs(output_dir, exist_ok=True)

    # Step 1: Create a new blank document
    document = aw.Document()
    builder = aw.DocumentBuilder(document)

    # Step 2: Insert a rectangle shape of the desired size
    rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

    # Step 3: Set the shape to be inline with the text flow
    rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE

    # Step 4: Make the shadow visible and choose its color
    rectangle_shape.shadow.visible = True
    rectangle_shape.shadow.color = aw.drawing.Color.black

    # Step 5: Define the shadow's offset and blur to give it depth
    rectangle_shape.shadow.offset_x = 5   # horizontal offset in points
    rectangle_shape.shadow.offset_y = 5   # vertical offset in points
    rectangle_shape.shadow.blur = 3       # blur radius in points

    # Step 6: Choose an outer shadow style
    rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER

    # Step 7: Save the document with the shaped shadow
    output_path = os.path.join(output_dir, "ShapeWithShadow.docx")
    document.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    main()
```

**Expected output**

When you open `ShapeWithShadow.docx`, you will see a single rectangle centered on the page. The rectangle is accompanied by a subtle black shadow offset to the bottom‑right, blurred slightly to create depth. The shadow respects the outer style, so it does not intersect the rectangle’s interior.

## Common questions and edge cases

### Why does the shadow sometimes appear invisible?

The shadow is only rendered if `shadow.visible` is set to `True` **and** the shape’s `wrap_type` allows it to be displayed. An inline shape works reliably; floating shapes may require additional layout adjustments.

### How can I change the shadow color to match a brand palette?

Replace `aw.drawing.Color.black` with a custom RGB value:

```python
rectangle_shape.shadow.color = aw.drawing.Color.from_argb(255, 0, 120, 215)  # corporate blue
```

### What if I need the shape to appear behind text?

Set the wrap type to `WrapType.BEHIND` and adjust the `z_order_position` if necessary. Keep in mind that some viewers may render behind‑text shapes differently.

### Can I apply the same shadow settings to multiple shapes?

Yes. Create a helper function that configures the shadow and call it for each shape you insert. This promotes code reuse and ensures consistent styling.

```python
def apply_shadow(shape, color=aw.drawing.Color.black, offset=5, blur=3):
    shape.shadow.visible = True
    shape.shadow.color = color
    shape.shadow.offset_x = offset
    shape.shadow.offset_y = offset
    shape.shadow.blur = blur
    shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

## Conclusion

You now know **how to create document** files that contain a rectangle shape with a customized shadow using Aspose.Words for Python. The tutorial covered inserting a rectangle, making the shape inline, enabling the shadow, setting its color, offset, blur, and style, and finally saving the file. 

From here you can explore related topics such as **add shadow to shape** for other shape types, **set shadow color** dynamically based on data, or **how to add shadow** to images and text boxes. Experiment with different dimensions, colors, and shadow styles to match your brand guidelines or design system.

Ready to automate more Word documents? Try adding tables, headers, or dynamic content next—each step builds on the same principles demonstrated here. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [How to Manage Document Variables with Aspose.Words in Python&#58; A Complete Guide](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}