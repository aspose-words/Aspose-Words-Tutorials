---
category: general
date: 2026-06-24
description: Create rectangle shape in Python with Aspose.Words, learn how to add
  shadow to shape, set shadow angle, and save document as PDF in minutes.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shape shadow
- set shadow angle
language: en
og_description: Create rectangle shape in Python, add shadow to shape, set shadow
  angle, and save document as PDF with Aspose.Words. Follow this step‑by‑step guide.
og_title: Create Rectangle Shape in Python – Full Aspose.Words Tutorial
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  headline: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  name: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: What if I need a different shape?
    text: Aspose.Words supports many `ShapeType` values (ellipse, star, callout, etc.).
      Simply replace `aw.drawing.ShapeType.RECTANGLE` with the desired enum, like
      `aw.drawing.ShapeType.ELLIPSE`.
  - name: Can I add multiple shadows?
    text: The API exposes only one `ShadowFormat` per shape, but you can simulate
      multiple shadows by duplicating the shape, offsetting each copy, and adjusting
      transparency.
  - name: How do I change the shadow color to match my brand?
    text: Just set `shadow.color` to any `aw.drawing.Color`. For a brand blue, use
      `aw.drawing.Color.from_argb(255, 0, 120, 215)`.
  - name: What about saving as DOCX instead of PDF?
    text: Replace `document.save(pdf_path)` with `document.save("output/shadowed_rectangle.docx")`.
      The shadow rendering is preserved across both formats.
  - name: Does the shadow work on older PDF viewers?
    text: Aspose.Words renders the shadow as a vector effect, which is widely supported.
      However, very old viewers might flatten the effect; testing on your target audience’s
      devices is always a good habit.
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: Create Rectangle Shape in Python – Complete Aspose.Words Guide
url: /python/images-shapes/create-rectangle-shape-in-python-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create Rectangle Shape in Python – Complete Aspose.Words Guide

Ever wondered how to **create rectangle shape** in a Word document using Python? Maybe you need a bold call‑out box, a visual cue for a diagram, or just a fancy rectangle for a report. Whatever the case, you’ve landed in the right spot. In this tutorial we’ll walk through the entire process—from inserting the rectangle, to adding a subtle shadow, tweaking the shadow angle, and finally **save document as PDF** so you can share it with anyone.

We’ll be using **Aspose.Words for Python via .NET**, a powerful library that lets you manipulate Word files without ever opening Word itself. By the end of this guide you’ll be able to answer the question *“how to add shape shadow”* with confidence, and you’ll have a ready‑to‑run script that you can drop into any project.

---

## What You’ll Need

Before we dive in, make sure you have the following:

- **Python 3.8+** installed on your machine.  
- **Aspose.Words for Python via .NET** (`aspose-words` package). Install it with:

  ```bash
  pip install aspose-words
  ```

- A writeable folder where the generated PDF will be saved.  
- (Optional) An IDE or text editor—VS Code works great.

That’s it. No extra DLLs, no Office installation, just a single pip package.

---

## Step 1: Set Up the Document and Builder

The first thing you need to do is **create rectangle shape**‑friendly objects: a `Document` and a `DocumentBuilder`. Think of the builder as your pen; it draws everything for you.

```python
import aspose.words as aw

# Initialize a new blank document
document = aw.Document()

# DocumentBuilder gives us a convenient way to add content
builder = aw.DocumentBuilder(document)
```

> **Why this matters:** The `Document` object represents the whole .docx file, while the `DocumentBuilder` provides methods like `insert_shape` that make drawing shapes a breeze.

---

## Step 2: Insert the Rectangle Shape

Now that we have a builder, we can finally **create rectangle shape**. The `insert_shape` method needs three arguments: the shape type, width, and height. We’ll use 200 pt width and 100 pt height for a nice proportion.

```python
# Insert a rectangle with a width of 200 points and a height of 100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

At this point you’ve successfully **create rectangle shape** in your document. If you open the generated DOCX (we’ll do that later), you’ll see a plain rectangle sitting where the cursor was.

---

## Step 3: Access the Shadow Formatting Object

To **add shadow to shape**, we first need to grab the shape’s shadow formatting. Every shape in Aspose.Words has a `shadow_format` property that exposes all the shadow‑related settings.

```python
# Grab the shadow formatting object for later tweaks
shadow = rectangle.shadow_format
```

Having the `shadow` reference lets us toggle visibility, blur, distance, angle, color, and transparency—all in a few lines of code.

---

## Step 4: Enable the Shadow and Configure Its Appearance

Here’s where the magic happens. We’ll **add shadow to shape**, make it slightly blurred, offset it a bit, set the direction (the **set shadow angle** part), and give it a semi‑transparent black hue.

```python
# Turn the shadow on
shadow.visible = True

# Soften the edges – a blur radius of 8 points looks natural
shadow.blur_radius = 8.0

# Push the shadow away from the rectangle by 5 points
shadow.distance = 5.0

# Set the direction of the light source – 45 degrees creates a diagonal drop
shadow.angle = 45

# Choose a color; black works well for most documents
shadow.color = aw.drawing.Color.black

# Make the shadow 30 % transparent for a subtle effect
shadow.transparency = 0.3
```

> **Pro tip:** If you ever need a more dramatic effect, increase `blur_radius` or lower `transparency`. Conversely, a sharp, fully opaque shadow can be achieved with `blur_radius = 0` and `transparency = 0`.

---

## Step 5: Save the Document as a PDF

We’ve **create rectangle shape**, we’ve **add shadow to shape**, and now we’ll **save document as PDF** so the result looks identical on any device. Aspose.Words makes this a one‑liner.

```python
# Define where you want the PDF to land
output_path = "output/shadowed_rectangle.pdf"

# Save the whole document (including the rectangle with its shadow) as PDF
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Running the script will generate `shadowed_rectangle.pdf` in the `output` folder. Open it with any PDF viewer and you’ll see a clean rectangle with a soft, 45‑degree shadow—exactly what we configured.

---

## Full Working Example

Below is the complete, ready‑to‑run script that combines all the steps above. Copy‑paste it into a file named `create_rectangle_with_shadow.py` and execute `python create_rectangle_with_shadow.py`.

```python
import aspose.words as aw
import os

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Initialize document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert the rectangle shape (200 pt × 100 pt)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Access shadow formatting
shadow = rectangle.shadow_format

# 4️⃣ Configure shadow – visible, blurred, offset, angled, colored, semi‑transparent
shadow.visible = True
shadow.blur_radius = 8.0          # softer edges
shadow.distance = 5.0            # how far the shadow sits from the shape
shadow.angle = 45                # direction in degrees – this is the **set shadow angle** step
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.3        # 30 % transparent

# 5️⃣ Save the document as PDF
pdf_path = os.path.join(output_dir, "shadowed_rectangle.pdf")
document.save(pdf_path)

print(f"✅ PDF created at: {pdf_path}")
```

**Expected output:** A PDF file showing a single rectangle with a gentle, diagonal shadow. No extra pages, no hidden artifacts—just the shape we crafted.

---

## Common Questions & Edge Cases

### What if I need a different shape?

Aspose.Words supports many `ShapeType` values (ellipse, star, callout, etc.). Simply replace `aw.drawing.ShapeType.RECTANGLE` with the desired enum, like `aw.drawing.ShapeType.ELLIPSE`.

### Can I add multiple shadows?

The API exposes only one `ShadowFormat` per shape, but you can simulate multiple shadows by duplicating the shape, offsetting each copy, and adjusting transparency.

### How do I change the shadow color to match my brand?

Just set `shadow.color` to any `aw.drawing.Color`. For a brand blue, use `aw.drawing.Color.from_argb(255, 0, 120, 215)`.

### What about saving as DOCX instead of PDF?

Replace `document.save(pdf_path)` with `document.save("output/shadowed_rectangle.docx")`. The shadow rendering is preserved across both formats.

### Does the shadow work on older PDF viewers?

Aspose.Words renders the shadow as a vector effect, which is widely supported. However, very old viewers might flatten the effect; testing on your target audience’s devices is always a good habit.

---

## Tips for Polishing Your PDF

- **Add a border:** `rectangle.line_format.width = 1.5` and set a color for a crisp outline.  
- **Center the rectangle:** Use `builder.move_to_document_start()` before inserting, then `builder.paragraph_format.alignment = aw.ParagraphAlignment.CENTER`.  
- **Combine with text:** Insert a `TextFragment` after the rectangle to label it, e.g., `"Important Section"`.

These small tweaks can turn a plain rectangle into a polished call‑out box that looks professional in reports, proposals, or e‑books.

---

## Conclusion

You now have a solid, end‑to‑end recipe to **create rectangle shape** in Python, **add shadow to shape**, **set shadow angle**, and **save document as PDF** using Aspose.Words. The steps are straightforward, the code is fully self‑contained, and you’ve seen why each line matters—from initializing the document to polishing the final PDF.

Next, you might explore **how to add shape shadow** to more complex drawings, experiment with gradient fills, or generate tables inside your shapes. The library also supports linking shapes to bookmarks, which can be handy for interactive PDFs.

Got a twist you tried? Share it in the comments, or fire away with any lingering questions. Happy coding, and enjoy adding that extra depth to your documents! 

![Rectangle shape with shadow – example of create rectangle shape in Python](/images/rectangle-shadow.png)


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}