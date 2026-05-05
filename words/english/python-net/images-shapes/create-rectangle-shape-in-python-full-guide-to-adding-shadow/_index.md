---
category: general
date: 2026-05-04
description: Learn how to create rectangle shape, how to add shape with shadows, change
  shadow color, set shadow distance and save document as PDF using Aspose.Words for
  Python.
draft: false
keywords:
- create rectangle shape
- how to add shape
- change shadow color
- save document as pdf
- set shadow distance
language: en
og_description: Create rectangle shape with Aspose.Words for Python, learn how to
  add shape, change shadow color, set shadow distance, and save the document as PDF.
og_title: Create rectangle shape – Add Shadow, Change Color & Save as PDF
tags:
- Aspose.Words
- Python
- PDF generation
title: Create rectangle shape in Python – Full Guide to Adding Shadows & Saving as
  PDF
url: /python/images-shapes/create-rectangle-shape-in-python-full-guide-to-adding-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create rectangle shape – Complete Tutorial for Python Developers

Ever needed to **create rectangle shape** in a Word document and wonder how to give it a polished shadow? Maybe you’re building a report generator and the visual polish matters—especially when the final output is a PDF. The good news? With Aspose.Words for Python you can not only **how to add shape** but also tweak every shadow property, from colour to distance, and then **save document as pdf** in one smooth flow.

In this guide we’ll walk through the entire process step‑by‑step. You’ll see the exact code you can copy‑paste, understand *why* each line matters, and pick up a few tips for handling edge cases (like transparent shadows or non‑standard DPI). By the end you’ll be able to **create rectangle shape**, customise its shadow, and export a crisp PDF without breaking a sweat.

## Prerequisites

- Python 3.8+ installed on your machine.  
- Aspose.Words for Python via `pip install aspose-words`.  
- Basic familiarity with object‑oriented Python (nothing fancy).  

If you already have a virtual environment set up, just run the install command and you’re good to go.

## Step 1: Initialise the Document and Builder

Before you can **how to add shape**, you need a blank document to work with. The `Document` class represents the whole file, and `DocumentBuilder` is your paintbrush.

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder to edit it
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

*Why this matters:* `Document` holds all sections, pages, and resources. `DocumentBuilder` gives you a fluent API to insert content exactly where you need it—think of it as a cursor in a word processor.

## Step 2: Insert the Rectangle Shape

Now we actually **how to add shape**. The `insert_shape` method needs the shape type and its dimensions (in points). Here we choose a 200 × 100 pt rectangle and give it a light‑blue fill.

```python
# Step 2: Insert a rectangle shape and give it a light‑blue fill
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,  # shape type
    200,                            # width in points
    100)                            # height in points
rectangle_shape.fill_color = aw.Color.light_blue
```

*Pro tip:* If you need the shape to align with existing text, use `builder.move_to` before inserting, or adjust `left`/`top` properties after creation.

## Step 3: Turn the Shadow On

A shape without a shadow looks flat. To **set shadow distance** and make the effect visible, grab the shadow format and enable it.

```python
# Step 3: Access the shape's shadow format and make the shadow visible
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
```

*Why this step:* The shadow format is a separate object; toggling `visible` is the first thing you must do, otherwise all other shadow properties are ignored.

## Step 4: Style the Shadow – Colour, Blur, Distance, Direction

This is where the magic happens. We’ll **change shadow color**, adjust the blur radius, set how far the shadow sits from the rectangle, and rotate it 45°.

```python
# Step 4: Configure the appearance of the shadow
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER   # outer shadow
rectangle_shadow.blur_radius = 10.0                    # blur amount (pixels)
rectangle_shadow.distance = 5.0                        # distance from the shape
rectangle_shadow.direction = 45.0                     # angle in degrees
rectangle_shadow.color = aw.Color.gray                 # shadow colour
```

*Explanation of each property:*

| Property | What it does | Typical values |
|----------|--------------|----------------|
| `style` | Determines whether the shadow is *inner* or *outer*. | `OUTER` (most common) |
| `blur_radius` | Controls softness; higher = fuzzier edges. | 0–20 px is usual |
| `distance` | How far the shadow is offset from the shape. | 0–10 pt for subtle, >10 for dramatic |
| `direction` | Angle of the light source, measured clockwise from the x‑axis. | 0‑360° |
| `color` | Shadow hue. | Any `aw.Color` (e.g., `gray`, `dark_red`) |

*Edge case:* If you set `distance` to `0` the shadow will sit directly under the shape, effectively hiding the shape’s fill. Keep it above `0` for a visible offset.

## Step 5: Save the Document as a PDF

Finally, we **save document as pdf**. Aspose.Words automatically rasterises the shadow, so the PDF looks exactly like the Word view.

```python
# Step 5: Save the document as a PDF with the shadowed shape
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

*Why PDF?* PDFs preserve layout across platforms, making them perfect for reports, invoices, or any printable artifact.

---

![Create rectangle shape with shadow](https://example.com/images/rectangle-shadow.png){: .align-center alt="create rectangle shape with shadow example"}

*The image above shows the final PDF output – a light‑blue rectangle with a soft gray outer shadow, exactly as we configured.*

## Common Questions & Variations

### What if I need a **transparent** shadow?

Set the alpha channel on the shadow colour:

```python
transparent_gray = aw.Color.from_argb(128, 0, 0, 0)  # 50% opacity black
rectangle_shadow.color = transparent_gray
```

### Can I apply the same shadow to multiple shapes?

Yes. Extract the `ShadowFormat` from one shape and assign it to another:

```python
another_shape = builder.insert_shape(aw.drawing.ShapeType.ELLIPSE, 150, 150)
another_shape.shadow_format = rectangle_shadow.clone()
```

### How do I change the shadow for a **different shape type**?

All shape types share the same `ShadowFormat` properties, so you can reuse the same configuration block—just replace `ShapeType.RECTANGLE` with `ShapeType.OVAL`, `ShapeType.TRIANGLE`, etc.

### What about **high‑resolution PDFs** for print?

Specify the `PdfSaveOptions` with a higher DPI:

```python
options = aw.saving.PdfSaveOptions()
options.image_resolution = 300  # 300 DPI for print quality
document.save(output_path, options)
```

## Recap

We’ve covered everything you need to **create rectangle shape**, **how to add shape**, customise its **shadow colour**, **set shadow distance**, and finally **save document as pdf**. The complete, runnable script looks like this:

```python
import aspose.words as aw

# Initialise document
document = aw.Document()
builder = aw.DocumentBuilder(document)

# Insert rectangle shape
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle_shape.fill_color = aw.Color.light_blue

# Enable and style shadow
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER
rectangle_shadow.blur_radius = 10.0
rectangle_shadow.distance = 5.0
rectangle_shadow.direction = 45.0
rectangle_shadow.color = aw.Color.gray

# Save as PDF
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Run the script, open the resulting `ShadowedShape.pdf`, and you’ll see a crisp rectangle with a subtle gray shadow—exactly what you’d expect from a professionally formatted report.

## What Next?

- **Explore other shape types** (`ShapeType.OVAL`, `ShapeType.LINE`) to enrich your documents.  
- **Combine multiple shadows** by layering shapes; you can even create a “glow” effect by using an inner shadow with a bright colour.  
- **Automate batch processing**: loop over a collection of data rows, generate a shape per row, and merge everything into a single PDF.  
- **Integrate with other Aspose libraries** (e.g., Aspose.Slides) if you need to export the same visual to PowerPoint.

Feel free to experiment—change the `blur_radius`, play with `direction`, or swap `gray` for a brand‑specific hue. The API is flexible enough that a few tweaks can dramatically change the visual impact.

Got questions or a tricky scenario? Drop a comment below or ping the Aspose community forums. Happy coding, and enjoy those beautifully shadowed rectangles!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}