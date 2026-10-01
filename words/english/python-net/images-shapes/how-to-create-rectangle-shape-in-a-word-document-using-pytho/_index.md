---
category: general
date: 2026-09-30
description: Learn how to create rectangle shape, apply shadow to shape, and save
  Word with shape using Aspose.Words for Python.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- how to add shape
- apply shadow to shape
- set shadow blur
- save word with shape
language: en
lastmod: 2026-09-30
og_description: Create rectangle shape in a Word document quickly. This tutorial shows
  how to add shape, apply shadow to shape, set shadow blur, and save Word with shape.
og_image_alt: Screenshot of a Word document showing a rectangle shape with a soft
  shadow
og_title: Create rectangle shape in Word with Python – step‑by‑step guide
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
title: How to create rectangle shape in a Word document using Python
url: /python/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create rectangle shape in a Word document using Python

If you need to **create rectangle shape** in a Word file, this guide shows you a complete, runnable solution. You’ll see how to add the shape, apply a shadow effect, adjust the blur, and finally **save Word with shape** so the result can be opened in Microsoft Word or any compatible viewer.

The example uses **Aspose.Words for Python via .NET**, a library that lets you manipulate Word documents without Microsoft Office installed. No prior experience with the API is required—just basic Python knowledge.

## What you’ll achieve

- Insert a rectangle into the first section of a new document.  
- Configure a soft shadow by setting its blur, offset, and color.  
- Persist the document to disk and verify the visual result.

## Prerequisites

- Python 3.8 or newer.  
- `aspose-words` package installed (`pip install aspose-words`).  
- Write permission to the output directory.

## Create rectangle shape and configure its appearance

The first step is to instantiate a blank document and add a rectangle shape to it. The shape will serve as the canvas for the shadow effect.

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

**Why this matters:**  
Creating the rectangle gives you a concrete object (`shape`) that you can later style. Setting explicit dimensions ensures the shape looks the same on every platform.

## How to add shape to a Word document

While the code above already adds the rectangle, you might need to add additional shapes (e.g., circles, arrows) later. The same pattern applies: call `append_child` on the document’s body and pass the desired `ShapeType`.

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

**Tip:** Use `ShapeType` enumeration to explore all supported shapes. This keeps your code readable and avoids magic numbers.

## Apply shadow to shape and set shadow blur

A shadow adds depth and visual interest. The `ShadowEffect` class lets you control blur, offset, and color. Below we apply a soft black shadow to the rectangle.

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

**Why set blur?**  
`blur` determines how diffused the shadow appears. A low value (e.g., 1.0) yields a sharp edge, while a higher value (e.g., 5.0) creates a gentle fade, which is often more aesthetically pleasing.

**Edge case:** If you set `blur` to 0, the shadow becomes a solid silhouette. Some viewers may render it with aliasing artifacts, so choose a value greater than 0 for smoother output.

## Save Word with shape

Persisting the document finalizes all changes. The `save` method writes a `.docx` file that any modern Word processor can open.

```python
# Step 5: Save the document to see the result
output_path = "output.docx"   # Adjust the path as needed
doc.save(output_path)
print(f"Document saved to {output_path}")
```

When you open `output.docx`, you’ll see a rectangle positioned one inch from the top‑left corner, with a soft black shadow displaced two points to the right and down. The shadow’s blur makes it look like the shape is lifted off the page.

**Pro tip:** If you need to generate many documents in a loop, reuse the same `Document` instance and clear its body between iterations to reduce memory overhead.

## Common variations and troubleshooting

| Situation | What to change | Reason |
|-----------|----------------|--------|
| Different shadow color | `shadow.color = aw.Color.red` | Use brand colors or highlight important shapes. |
| Larger shadow offset | Increase `shadow.offset_x`/`offset_y` | Emphasize depth for UI mock‑ups. |
| No shadow at all | Omit the `shape.shadow = shadow` line | Useful for minimalist reports. |
| Export to PDF instead of DOCX | `doc.save("output.pdf")` | PDF is ideal for read‑only distribution. |

If the shape does not appear, verify that you are adding it to the correct section (`get_first_section()`) and that the document is saved after the modifications.

## Full, runnable example

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

Running the script produces `output.docx` containing the rectangle with a soft shadow. Open the file in Microsoft Word to confirm that the visual effect matches the description.

## Conclusion

You now know how to **create rectangle shape**, **how to add shape** to a Word document, **apply shadow to shape**, **set shadow blur**, and finally **save Word with shape** using Aspose.Words for Python. The same pattern can be extended to other shape types, colors, and effects, giving you full control over document graphics without relying on Office automation.

**Next steps**

- Experiment with `Shape.fill` to add gradient or picture backgrounds.  
- Use `Paragraph` objects to place text inside the rectangle.  
- Combine multiple shapes to build complex diagrams, then export to PDF for distribution.  

Feel free to adapt the code for your own reporting or templating needs, and share your results in the comments!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}