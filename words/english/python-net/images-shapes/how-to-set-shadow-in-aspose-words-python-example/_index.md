---
category: general
date: 2026-08-01
description: How to set shadow on a Word shape using Aspose.Words for Python. Learn
  to change opacity, adjust blur, and change shadow distance quickly.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to set shadow
- how to change opacity
- how to adjust blur
- change shadow distance
- how to use aspose.words
language: en
lastmod: 2026-08-01
og_description: How to set shadow on a shape with Aspose.Words for Python. Follow
  this step‑by‑step tutorial to change opacity, adjust blur, and change shadow distance.
og_image_alt: Screenshot showing how to set shadow on a shape using Aspose.Words in
  Python
og_title: How to Set Shadow in Aspose.Words – Quick Python Guide
schemas:
- author: Aspose
  dateModified: '2026-08-01'
  description: How to set shadow on a Word shape using Aspose.Words for Python. Learn
    to change opacity, adjust blur, and change shadow distance quickly.
  headline: How to Set Shadow in Aspose.Words – Python Example
  type: TechArticle
- description: How to set shadow on a Word shape using Aspose.Words for Python. Learn
    to change opacity, adjust blur, and change shadow distance quickly.
  name: How to Set Shadow in Aspose.Words – Python Example
  steps:
  - name: '**Create the document** (or load a template).'
    text: '**Create the document** (or load a template).'
  - name: '**Insert the logo shape** (via `DocumentBuilder.insert_image` or `Shape`).'
    text: '**Insert the logo shape** (via `DocumentBuilder.insert_image` or `Shape`).'
  - name: '**Call `apply_shadow`** with your brand’s shadow specs.'
    text: '**Call `apply_shadow`** with your brand’s shadow specs.'
  - name: '**Export** to DOCX, PDF, or HTML with a single line of code.'
    text: '**Export** to DOCX, PDF, or HTML with a single line of code.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Shadow Formatting
- Word Automation
title: How to Set Shadow in Aspose.Words – Python Example
url: /python/images-shapes/how-to-set-shadow-in-aspose-words-python-example/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to Set Shadow in Aspose.Words – Python Example

Ever wondered **how to set shadow** on a Word shape without opening the document manually? You're not the only one—many developers hit this snag when automating reports or creating branding‑consistent templates. The good news? With Aspose.Words for Python you can tweak a shape’s shadow, opacity, blur, and distance in just a few lines of code.

In this tutorial we’ll walk through a complete, runnable example that shows **how to set shadow**, **how to change opacity**, **how to adjust blur**, and even **change shadow distance**. By the end you’ll have a solid grasp of **how to use Aspose.Words** to style shapes programmatically.

---

![How to set shadow on a shape using Aspose.Words](image-placeholder.png){alt="How to set shadow on a shape using Aspose.Words"}

## Prerequisites

Before we dive in, make sure you have:

| Requirement | Reason |
|-------------|--------|
| Python 3.8+ | Modern syntax, type hints |
| `aspose-words` package (pip install aspose-words) | Core library for Word manipulation |
| A sample `input.docx` with at least one shape | The shape we’ll shadow |
| Write permission to the folder where you’ll save `output.docx` | To persist changes |

No extra DLLs or COM interop—Aspose.Words is pure‑Python, so you can run this on Windows, macOS, or Linux.

---

## How to Set Shadow on a Shape with Aspose.Words

Below is the **complete** script. It loads a document, finds the first shape (recursively), configures the shadow, and saves the result. Every line is commented so you understand **why** it’s there, not just **what** it does.

```python
# ------------------------------------------------------------
# How to Set Shadow – Full Python Example using Aspose.Words
# ------------------------------------------------------------
import aspose.words as aw  # Import the Aspose.Words namespace

def apply_shadow(
    input_path: str,
    output_path: str,
    distance: int = 5,
    blur: float = 4.0,
    opacity: float = 0.6
) -> None:
    """
    Demonstrates how to set shadow on the first shape in a Word document.
    
    Parameters
    ----------
    input_path : str
        Path to the source .docx file.
    output_path : str
        Path where the modified .docx will be saved.
    distance : int, optional
        How far the shadow is offset from the shape (default = 5 points).
    blur : float, optional
        Blur radius of the shadow (default = 4.0 points).
    opacity : float, optional
        Opacity of the shadow (0 = fully transparent, 1 = fully opaque).
    """
    # Step 1: Load the Word document
    doc = aw.Document(input_path)

    # Step 2: Retrieve the first shape in the document (searches recursively)
    # The `True` flag makes the search go deep into headers, footers, and groups.
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

    if shape is None:
        raise ValueError("No shape found in the document. Add a shape and try again.")

    # Step 3: Configure the shadow appearance for the shape
    # ----------------------------------------------------
    # distance → how far the shadow sits away from the shape edge
    # blur     → softness of the shadow edge
    # opacity  → transparency level (0‑1 range)
    shape.shadow_format.distance = distance          # change shadow distance
    shape.shadow_format.blur = blur                  # how to adjust blur
    shape.shadow_format.opacity = opacity            # how to change opacity

    # Optional: tweak color and style if you need more control
    shape.shadow_format.color = aw.Color.black
    shape.shadow_format.style = aw.ShadowStyle.OUTER_SHADOW

    # Step 4: Save the modified document
    doc.save(output_path)

# -----------------------------------------------------------------
# Example usage – adjust the parameters to see different results
# -----------------------------------------------------------------
if __name__ == "__main__":
    apply_shadow(
        input_path="YOUR_DIRECTORY/input.docx",
        output_path="YOUR_DIRECTORY/output.docx",
        distance=8,       # increase distance for a more pronounced offset
        blur=6.5,         # higher blur makes the shadow softer
        opacity=0.75      # make the shadow a bit more solid
    )
```

### Why This Works

* **`doc.get_child(..., True)`** – The `True` flag tells Aspose.Words to search **recursively**, so even shapes inside headers, footers, or grouped objects are found. That’s crucial when you don’t know exactly where the shape lives.
* **`shadow_format`** – This property groups all shadow‑related settings. By setting `distance`, `blur`, and `opacity` you control the visual depth of the shape. Changing any of these values demonstrates **how to change opacity**, **how to adjust blur**, and **change shadow distance** in a single, cohesive call.
* **Saving** – `doc.save` writes a brand‑new `.docx`. The original stays untouched, which is a safe pattern for batch processing.

---

## How to Change Opacity of a Shape’s Shadow

Opacity determines how see‑through the shadow appears. The range is 0.0 (completely invisible) to 1.0 (fully solid). In the code above you can simply modify the `opacity` argument:

```python
shape.shadow_format.opacity = 0.85  # 85% opaque – looks richer on dark backgrounds
```

> **Pro tip:** When generating PDFs later, a higher opacity often translates to a deeper, more printable shadow. Experiment with values between 0.4 and 0.9 to find the sweet spot for your brand guidelines.

---

## How to Adjust Blur for a Softer Look

Blur is the radius of the Gaussian blur applied to the shadow edges. A larger number yields a feathered effect:

```python
shape.shadow_format.blur = 10.0  # Very soft, almost hazy shadow
```

If you need a crisp, drop‑shadow look (think “Microsoft PowerPoint” style), set `blur` to a low value like `1.0`.

---

## Change Shadow Distance to Create Depth

Distance is measured in points (1 pt = 1/72 in). Moving the shadow further away makes the shape appear to float higher:

```python
shape.shadow_format.distance = 12  # Shadow shifts 12 pt away from the shape
```

Combine a larger `distance` with a modest `blur` for a dramatic, “lifted” effect.

---

## Putting It All Together – A Mini‑Project

Imagine you’re building an automated report generator that inserts a company logo inside a text box. You want every logo to have a subtle shadow that matches the corporate style. Using the function `apply_shadow` you can:

1. **Create the document** (or load a template).
2. **Insert the logo shape** (via `DocumentBuilder.insert_image` or `Shape`).
3. **Call `apply_shadow`** with your brand’s shadow specs.
4. **Export** to DOCX, PDF, or HTML with a single line of code.

Because the function accepts parameters, you can store your shadow settings in a JSON file and apply them across dozens of documents—no manual tweaking required.

---

## Common Questions & Edge Cases

| Question | Answer |
|----------|--------|
| **What if the document has multiple shapes?** | The example targets the *first* shape. To affect all shapes, loop with `doc.get_child_nodes(aw.NodeType.SHAPE, True)` and apply the same `shadow_format` settings to each node. |
| **Can I set a different shadow color?** | Absolutely. Use `shape.shadow_format.color = aw.Color(255, 0, 0)` for a red shadow, or any `aw.Color` you like. |
| **Do these settings survive a conversion to PDF?** | Yes. Aspose.Words preserves shadow properties when rendering to PDF, though very high blur values may be approximated. |
| **Is there a performance hit for large documents?** | The shadow API touches only the shape objects, so even a 500‑page report processes in milliseconds. The bottleneck is usually I/O, not the shadow configuration. |
| **Can I remove the shadow later?** | Set `shape.shadow_format.is_visible = False` or simply reset the properties to defaults. |

---

## Full Working Example Recap

Here’s the entire script again, stripped of comments for quick copy‑paste:

```python
import aspose.words as aw

def apply_shadow(input_path, output_path, distance=5, blur=4.0, opacity=0.6):
    doc = aw.Document(input_path)
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
    if shape is None:
        raise ValueError("No shape found.")
    shape.shadow_format.distance = distance
    shape.shadow_format.blur = blur
    shape.shadow_format.opacity = opacity
    shape.shadow_format.color = aw.Color.black
    shape.shadow_format.style = aw.ShadowStyle.OUTER_SHADOW
    doc.save(output_path)

if __name__ == "__main__":
    apply_shadow(
        "YOUR_DIRECTORY/input.docx",
        "YOUR_DIRECTORY/output.docx",
        distance=8,
        blur=6.5,
        opacity=0.75
    )
```

Run the script, open `output.docx`, and you’ll see the shape sporting a neat shadow that matches the parameters you set.

---

## Conclusion

We’ve covered **


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [How to Implement Comments and Replies in Word Documents using Aspose.Words for Python](/words/english/python-net/annotations-comments/aspose-words-python-comments-replies/)
- [How to Manage Document Variables with Aspose.Words in Python: A Complete Guide](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}