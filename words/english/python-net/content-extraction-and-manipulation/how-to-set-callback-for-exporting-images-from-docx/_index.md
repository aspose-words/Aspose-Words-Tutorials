---
category: general
date: 2026-06-24
description: How to set callback to export images from DOCX when saving as Markdown.
  Learn how to extract images, extract SVG from Word, and save DOCX as Markdown with
  custom handling.
draft: false
keywords:
- how to set callback
- export images from docx
- how to extract images
- save docx as markdown
- extract svg from word
language: en
og_description: How to set callback to export images from DOCX when converting to
  Markdown. This guide shows you how to extract images and SVGs efficiently.
og_title: How to Set Callback for Exporting Images from DOCX
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  headline: How to Set Callback for Exporting Images from DOCX
  type: TechArticle
- description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  name: How to Set Callback for Exporting Images from DOCX
  steps:
  - name: '**Deterministic names** – useful for version control or CDN publishing.'
    text: '**Deterministic names** – useful for version control or CDN publishing.'
  - name: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
    text: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
  - name: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
    text: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Conversion
title: How to Set Callback for Exporting Images from DOCX
url: /python/content-extraction-and-manipulation/how-to-set-callback-for-exporting-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to Set Callback for Exporting Images from DOCX

Ever wondered **how to set callback** so you can **export images from DOCX** while converting it to Markdown? You're not the only one. Many developers hit a wall when the default conversion dumps all images into a generic folder or, worse, loses SVG graphics entirely.  

In this tutorial we’ll walk through a complete, ready‑to‑run solution that answers that “how to set callback” question, shows **how to extract images**, and even covers **extract SVG from Word**. By the end you’ll be able to **save DOCX as Markdown** with a custom naming scheme for every image resource—no manual fiddling required.

## What You’ll Learn

- Why a callback is the cleanest way to control image filenames during conversion.  
- How to hook into Aspose.Words’ `MarkdownSaveOptions.resource_saving_callback`.  
- Step‑by‑step code that extracts **PNG**, **JPG**, **SVG**, and any other embedded resource.  
- Tips for handling name collisions, large files, and cross‑platform path quirks.  

> **Pro tip:** If you’re already using Aspose.Words in a larger pipeline, you can drop this callback in without touching the rest of your code.

---

![How to set callback diagram](https://example.com/images/how-to-set-callback.png "how to set callback")

## Prerequisites

- Python 3.8+ (the example uses f‑strings, so 3.6+ is fine).  
- `aspose-words` package installed (`pip install aspose-words`).  
- A DOCX file that contains raster images **and** vector graphics (SVG).  
- Basic familiarity with Python functions and file I/O.

If you’ve got those, let’s dive in.

---

## How to Set Callback for Exporting Images from DOCX

The core of the solution lives in a **resource‑saving callback**. Aspose.Words calls this delegate for every image or SVG it wants to write when you invoke `document.save`. By returning a tuple `(new_name, data)` you dictate both the filename and the byte payload.

```python
import aspose.words as aw
import os
import hashlib

# Step 1: Load the source document
document = aw.Document("YOUR_DIRECTORY/input.docx")
```

### Why a Callback?

Without a callback, Aspose.Words creates files named `image1.png`, `image2.svg`, etc., and places them in a folder next to the Markdown file. This is fine for quick demos, but in production you often need:

1. **Deterministic names** – useful for version control or CDN publishing.  
2. **Collision avoidance** – two images with the same original name won’t overwrite each other.  
3. **Custom folder structures** – maybe you want all assets under `/assets/docs/`.

The callback gives you full control over those three concerns.

---

## Export Images from DOCX Using a Resource Callback

Below is the callback implementation. It hashes the binary data to produce a unique suffix, preserves the original file extension, and returns the new filename together with the raw bytes.

```python
def resource_callback(resource):
    """
    Called for every image/SVG that MarkdownSaveOptions wants to write.
    Returns a tuple (new_name, data) to control the saved file name.
    """
    # Preserve the original extension (.png, .svg, …)
    extension = os.path.splitext(resource.name)[1]

    # Compute a short hash of the image bytes – guarantees uniqueness
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]

    # Build a deterministic, collision‑free filename
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data
```

#### Edge‑Case Handling

- **Large files:** SHA‑256 works fine for any size; the hash is computed in memory, so be mindful of memory constraints if you’re processing huge PDFs.  
- **Missing extensions:** Some older Word files may store images without an explicit extension. In that case `extension` will be empty; you can default to `.bin` or inspect the first few bytes to guess the format.  
- **Non‑image resources:** The callback is invoked for every external resource (e.g., OLE objects). If you only care about images/SVGs, filter by `resource.type` before proceeding.

---

## How to Extract Images and SVGs from Word

Now we wire the callback into the Markdown saving pipeline. The `MarkdownSaveOptions` object exposes the `resource_saving_callback` property exactly for this purpose.

```python
# Step 2: Configure Markdown save options to use the callback
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.resource_saving_callback = resource_callback

# Optional: set the folder where images will be placed relative to the .md file
markdown_options.resource_folder = "assets/images"
```

Setting `resource_folder` is optional but often handy. If you omit it, the images end up beside the Markdown file, which can clutter your project root.

### Saving the Document

```python
# Step 3: Save the document as Markdown, letting the callback store the resources
output_md_path = "YOUR_DIRECTORY/output.md"
document.save(output_md_path, markdown_options)
print(f"Markdown saved to {output_md_path}")
```

When you run the script, you’ll see a series of files like:

```
assets/images/img_a1b2c3d4e5.png
assets/images/img_f6g7h8i9j0.svg
```

And the generated `output.md` will contain image links that point to those exact filenames:

```markdown
![Image](assets/images/img_a1b2c3d4e5.png)
```

That’s the **how to extract images** part in action—every picture, raster or vector, is now a separate, uniquely named asset.

---

## Save DOCX as Markdown with Custom Image Handling

Putting it all together, here’s the full script you can copy‑paste into a file called `convert_docx_to_md.py`:

```python
import aspose.words as aw
import os
import hashlib

def resource_callback(resource):
    """Control the naming of each exported image/SVG."""
    extension = os.path.splitext(resource.name)[1] or ".bin"
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data

def convert_docx_to_markdown(input_path, output_md_path, image_folder="assets/images"):
    # Load the DOCX
    document = aw.Document(input_path)

    # Set up Markdown options with our callback
    md_options = aw.saving.MarkdownSaveOptions()
    md_options.resource_saving_callback = resource_callback
    md_options.resource_folder = image_folder

    # Ensure the output directory exists
    os.makedirs(os.path.dirname(output_md_path), exist_ok=True)
    os.makedirs(os.path.join(os.path.dirname(output_md_path), image_folder), exist_ok=True)

    # Perform the conversion
    document.save(output_md_path, md_options)
    print(f"✅ Conversion complete! Markdown at: {output_md_path}")

if __name__ == "__main__":
    # Adjust these paths to your environment
    INPUT_DOCX = "YOUR_DIRECTORY/input.docx"
    OUTPUT_MD = "YOUR_DIRECTORY/output.md"
    convert_docx_to_markdown(INPUT_DOCX, OUTPUT_MD)
```

**Why this works:**  
- The `resource_callback` guarantees that every image gets a unique, reproducible name.  
- `resource_folder` keeps the Markdown tidy by separating assets.  
- The `os.makedirs` calls protect you from “folder not found” errors when the script runs on a fresh machine.

---

## Extract SVG from Word – What About Vector Graphics?

SVGs are treated the same as PNGs by the callback because they’re just another `resource`. The only nuance is that some older Word versions embed SVGs as *OfficeArt* objects, which Aspose.Words automatically converts to a raster PNG unless you explicitly enable the **preserve SVG** flag:

```python
md_options.export_svg = True  # Keep original SVG markup
```

Add that line before saving, and the callback will receive resources with a `.svg` extension, preserving crisp vector data—perfect for responsive web docs.

---

## Common Questions & Gotchas

| Question | Answer |
|----------|--------|
| **What if two images are identical?** | The SHA‑256 hash will be identical, so the filenames collide. If you need both copies, include the original `resource.name` in the hash calculation (e.g., `hash(resource.name + resource.data)`). |
| **Can I change the folder per file type?** | Yes. Inside `resource_callback` you can inspect `extension` and return a path like `f"png/{new_name}"` for raster images and `f"svg/{new_name}"` for vectors. |
| **Does this work on Linux/macOS?** | Absolutely. The code uses `os.path` which abstracts away path separators. Just ensure you have the Aspose.Words license file (`aspose.words.lic`) accessible if you’re on a paid version. |
| **What about memory usage for huge documents?** | The callback receives the **full byte array** for each resource, which means the whole image lives in memory temporarily. For multi‑gigabyte files you might want to stream the data to disk inside the callback instead of returning it. |

---

## Conclusion

You now know **how to set callback** to control image extraction when you **save DOCX as Markdown**. The approach lets you **export images from DOCX**, **extract SVG from Word**, and keep your Markdown clean and deterministic.  

In a single, self‑contained script we covered loading a document, defining a resource‑saving callback, configuring `MarkdownSaveOptions`, and handling edge cases like name collisions and vector graphics. The result is a set of uniquely named assets alongside a perfectly linked Markdown file—ready for static site generators, documentation pipelines, or any workflow that needs clean, reusable assets.

**Next steps?**  
- Try chaining this with a static‑site generator like MkDocs to automatically publish Word‑based docs.  
- Experiment with `markdown_options.export_images_as_base64 = True` if you prefer inline images instead of external files.  
- Dive deeper into Aspose.Words’ other callbacks (e.g., `document_saving_callback`) to control the Markdown output itself.

Got more questions about **how to extract images** from other Office formats, or need help tweaking the callback for a specific naming convention? Drop a comment below, and happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to Rename Images When Converting DOCX to Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)
- [How to Save Markdown from DOCX – Step‑by‑Step Guide](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}