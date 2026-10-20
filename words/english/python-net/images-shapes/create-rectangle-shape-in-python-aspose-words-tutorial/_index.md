---
category: general
date: 2026-06-21
description: Create rectangle shape in Python using Aspose.Words. Learn how to add
  shadow to shape, set shape fill color, and save document as PDF in minutes.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- set shape fill color
language: en
og_description: Create rectangle shape in Python with Aspose.Words. This guide shows
  how to add shadow to shape, set shape fill color, and save document as PDF.
og_title: Create rectangle shape in Python – Aspose.Words tutorial
schemas:
- author: Aspose
  dateModified: '2026-06-21'
  description: Create rectangle shape in Python using Aspose.Words. Learn how to add
    shadow to shape, set shape fill color, and save document as PDF in minutes.
  headline: Create rectangle shape in Python – Aspose.Words tutorial
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF generation
title: Create rectangle shape in Python – Aspose.Words tutorial
url: /python/images-shapes/create-rectangle-shape-in-python-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create rectangle shape in Python – Aspose.Words tutorial

Ever wondered **how to create rectangle shape** in a Word document while you’re coding in Python? You’re not the only one. Many developers hit a wall when they need a quick visual element—like a colored box with a subtle shadow—and then export the whole thing as a PDF.  

In this guide we’ll walk through a complete, runnable example that **creates rectangle shape**, **sets shape fill color**, **adds shadow to shape**, and finally **saves document as PDF**. No vague references, just concrete code you can copy‑paste and run today.

## What You’ll Need

Before we dive in, make sure you have the following on your machine:

- Python 3.8 or newer (the syntax we use works on any recent version).
- An active Aspose.Words for Python license or a free trial (the library is pure‑Python, no COM interop required).
- A text editor or IDE you’re comfortable with—VS Code works great, but any will do.

That’s it. No heavy frameworks, no additional OS‑level dependencies. Let’s get started.

## Step 1: Install Aspose.Words for Python

First things first. If you haven’t already, pull the package from PyPI:

```bash
pip install aspose-words
```

Why this step matters: Aspose.Words provides the `Document` and `DocumentBuilder` classes we’ll rely on. Without the library, none of the later calls—like `insert_shape`—exist, so the script would crash before it even draws a line.

> **Pro tip:** Keep your virtual environment tidy. Run `python -m venv .venv && source .venv/bin/activate` before installing, so the library stays isolated from system packages.

## Step 2: Create a New Document and a DocumentBuilder

Now we actually **create rectangle shape** – but first we need a blank canvas.

```python
import aspose.words as aw

# Initialize a new, empty Word document
doc = aw.Document()
# DocumentBuilder lets us add content programmatically
builder = aw.DocumentBuilder(doc)
```

The `Document` object represents the whole file, while `DocumentBuilder` is a handy helper that knows where the cursor is and can insert elements at that point. Think of the builder as a pen that writes on the page.

## Step 3: Insert the Rectangle Shape

Here’s where the primary action happens. We’ll **create rectangle shape** with a fixed width and height, then position it on the page.

```python
# Insert a rectangle 200 points wide and 100 points tall
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

Why a rectangle? It’s the simplest shape that still lets us showcase fill colors and shadows. If you need a circle or a star later, just swap `ShapeType.RECTANGLE` for another enum value.

## Step 4: Set Shape Fill Color

A plain white box isn’t very exciting, so let’s **set shape fill color** to something gentle—light blue works well for reports.

```python
# Apply a light‑blue background to the rectangle
rectangle.fill_color = aw.Color.light_blue
```

You can use any of the predefined `aw.Color` members (`red`, `green`, `dark_gray`, etc.) or pass an RGB tuple (`aw.Color.from_argb(255, 30, 144, 255)`). The fill color is what the user sees before any shadow or border is applied.

## Step 5: Add Shadow to Shape

Now for the visual polish: **add shadow to shape**. Shadows give depth and make the rectangle pop on the page.

```python
# Grab the shadow format object
shadow = rectangle.shadow_format

# Turn the shadow on
shadow.visible = True
# Choose a dark gray tone for realism
shadow.color = aw.Color.dark_gray
# Blur radius controls softness (5 points is a nice middle ground)
shadow.blur = 5
# Horizontal and vertical offsets shift the shadow relative to the shape
shadow.offset_x = 3
shadow.offset_y = 3
# Slight transparency makes the shadow feel natural
shadow.transparency = 0.2
# Use an outer shadow – you could also try INSET for a different effect
shadow.type = aw.drawing.ShadowType.OUTER
```

**How to add shadow**? The code above does exactly that, but let’s unpack why each property matters:

- `visible` – toggles the effect on/off.
- `color` – defines the hue; a dark gray mimics natural lighting.
- `blur` – higher values produce a softer edge.
- `offset_x` / `offset_y` – move the shadow away from the shape; tweak these to simulate different light angles.
- `transparency` – 0 is solid, 1 is invisible; 0.2 gives a subtle impression.
- `type` – `OUTER` casts the shadow outside the shape, while `INNER` would inset it.

If you ever need a dramatic drop shadow, increase `blur` to 10‑15 and bump `offset_x`/`offset_y` to 6‑8.

## Step 6: Save the Document as PDF

All that work is pointless unless we can **save document as PDF** and share it. Aspose.Words makes this a one‑liner:

```python
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Why PDF? PDFs preserve layout across platforms, making them ideal for reports, invoices, or any printable material. The `save` method automatically detects the file extension and chooses the right format—just ensure the path ends with `.pdf`.

### Expected Result

Open the resulting `ShapeWithShadow.pdf` and you should see a light‑blue rectangle centered near the top of the first page, with a soft dark gray shadow offset slightly to the right and down. The shape’s edges are crisp, the shadow is subtle, and the file size is typically under 100 KB.

## Bonus: Tweaking Shadows – Answers to “how to add shadow”

You might be wondering, *“Can I change the shadow direction without moving the shape?”* Absolutely. The shadow’s position is independent of the shape’s coordinates; just adjust `offset_x` and `offset_y`. Positive values move the shadow right/down, negative values move it left/up. For a top‑left light source, use `offset_x = -3` and `offset_y = -3`.

Another frequent question: *“What if I need multiple shadows on the same shape?”* Aspose.Words only supports a single shadow per shape. If you need layered effects, create a duplicate shape, offset it slightly, and apply a different shadow to each. It’s a bit of a hack, but it works.

## Full Script – Ready to Run

Below is the complete, self‑contained script. Copy it into a file named `create_rectangle_with_shadow.py` and run it with `python create_rectangle_with_shadow.py`.

```python
import aspose.words as aw

# ---------- Initialize document ----------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ---------- Insert rectangle ----------
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# ---------- Set fill color ----------
rectangle.fill_color = aw.Color.light_blue

# ---------- Configure shadow ----------
shadow = rectangle.shadow_format
shadow.visible = True
shadow.color = aw.Color.dark_gray
shadow.blur = 5
shadow.offset_x = 3
shadow.offset_y = 3
shadow.transparency = 0.2
shadow.type = aw.drawing.ShadowType.OUTER

# ---------- Save as PDF ----------
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

> **Note:** Replace `YOUR_DIRECTORY` with an absolute or relative path that exists on your machine. If the folder doesn’t exist, Python will raise a `FileNotFoundError`.

## Common Pitfalls & How to Avoid Them

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| Shadow not appearing | `shadow.visible` left at default `False` | Ensure `shadow.visible = True` |
| Shape is invisible | Fill color set to `aw.Color.transparent` or `None` | Use a solid color like `aw.Color.light_blue` |
| PDF is empty | Forgot to call `doc.save` or saved with wrong extension | Call `doc.save("output.pdf")` and verify the path |
| Runtime error `ImportError` | Aspose.Words not installed or wrong Python env | Run `pip install aspose-words` inside the active venv |

## Next Steps – Explore More Shapes and Formatting

Now that you’ve mastered **create rectangle shape**, you can:

- Replace `ShapeType.RECTANGLE` with `ShapeType.ELLIPSE` or `ShapeType.PENTAGON` to experiment with other geometries.
- Add text inside the shape using `builder.move_to(rectangle.absolute_position)` and then `builder.writeln("Hello World")`.
- Combine multiple shapes into a group with `group = aw.drawing.GroupShape(doc)` for complex diagrams.
- Export to other formats like DOCX (`doc.save("output.docx")`) or HTML (`doc.save("output.html")`) to see how the shadow translates.

Each of these extensions builds on the same core concepts: **add shadow to shape**, **set shape fill color**, and **save document as PDF** (or another format).

---

### Image Preview *(optional)*

![Create rectangle shape with shadow in Python](https://example.com/rectangle-shadow.png "Create rectangle shape with shadow in Python")

*The screenshot shows the final PDF output with a light‑blue rectangle and a subtle outer shadow.*

---

## Conclusion

We’ve walked through every step needed to **create rectangle shape** in Python, apply a custom fill, **add shadow to shape**, and finally **save document as PDF**. The code is fully runnable, the explanations cover the *why* behind each property, and we’ve touched on common edge cases and next‑


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}