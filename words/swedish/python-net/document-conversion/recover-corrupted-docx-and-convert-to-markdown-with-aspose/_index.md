---
category: general
date: 2026-08-04
description: Återställ korrupta docx‑filer med Aspose.Words återställningsläge och
  konvertera docx till markdown, exportera ekvationer som LaTeX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- recover corrupted docx
- convert docx to markdown
- how to use recovery mode
- export equations latex
language: sv
lastmod: 2026-08-04
og_description: Återställ korrupta docx‑filer med Aspose.Words återställningsläge,
  konvertera sedan docx till markdown samtidigt som du exporterar ekvationer som LaTeX.
  Följ den här steg‑för‑steg‑guiden för att även skapa PDF‑ och TXT‑utdata.
og_image_alt: Screenshot of Aspose.Words Python code converting a corrupted docx to
  markdown with LaTeX equations
og_title: Återställ skadad docx och konvertera till markdown – Aspose guide
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Recover corrupted docx files using Aspose.Words recovery mode and convert
    docx to markdown, exporting equations as LaTeX.
  headline: Recover corrupted docx and convert to markdown with Aspose
  type: TechArticle
- description: Recover corrupted docx files using Aspose.Words recovery mode and convert
    docx to markdown, exporting equations as LaTeX.
  name: Recover corrupted docx and convert to markdown with Aspose
  steps:
  - name: Export floating shapes as inline tags
    text: Floating images or text boxes can cause layout issues when converting to
      PDF. Setting `export_floating_shapes_as_inline_tag` forces Aspose.Words to treat
      those shapes as regular inline elements, preserving the visual flow.
  - name: Adjust the shadow of the first shape
    text: You might want to enhance the appearance of a specific shape before saving
      the final PDF. The code below accesses the first `Shape` node, enables its shadow,
      and tweaks visual parameters.
  - name: Expected output
    text: '| File | Description | |------|-------------| | `output.md` | Markdown
      version of the original DOCX. All equations appear as LaTeX (`$...$` or `$$...$$`).
      | | `output.txt` | Plain‑text dump'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document conversion
title: Återställ skadad docx och konvertera till markdown med Aspose
url: /sv/python/document-conversion/recover-corrupted-docx-and-convert-to-markdown-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Återställ korrupt docx och konvertera till markdown med Aspose

Om du behöver **återställa korrupta docx**‑filer, erbjuder Aspose.Words ett inbyggt återställningsläge som automatiskt kan reparera skadade Word‑dokument. När filen har återställts kan du **konvertera docx till markdown**, och till och med **exportera ekvationer latex** för sömlös användning i vetenskapliga dokument. Denna handledning visar exakt hur du gör det i Python, samt några extra alternativ för PDF‑ och vanlig‑text‑utmatning.

Du kommer att lära dig hur du:

* Ladda en potentiellt trasig DOCX med återställningsläget.  
* Spara det återställda dokumentet som Markdown med LaTeX‑formaterade ekvationer.  
* Generera en vanlig‑text (TXT)‑version som också innehåller LaTeX‑ekvationer.  
* Exportera till PDF samtidigt som flytande former märks som inline‑element.  
* Justera en forms skugga och skapa en slutlig PDF.

Inga externa verktyg krävs—bara det kostnadsfria Aspose.Words för Python‑biblioteket.

## Prerequisites

| Krav | Varför det är viktigt |
|------|------------------------|
| Python 3.8+ | Krävs av Aspose.Words för Python |
| `aspose-words` package (`pip install aspose-words`) | Tillhandahåller `aw`‑namnutrymmet som används i koden |
| A DOCX file that may be damaged (e.g., `corrupted.docx`) | En DOCX‑fil som kan vara skadad (t.ex. `corrupted.docx`) |
| Write permission to the output directory | Skrivrättighet till utmatningskatalogen |

Se till att Aspose.Words‑licensen (gratis prov eller köpt) är korrekt konfigurerad om du överskrider utvärderingsgränserna.

## Recover corrupted docx using Aspose.Words

Det första steget är att instruera Aspose.Words att behandla inmatningsfilen som potentiellt trasig. Detta görs med `LoadOptions.recovery_mode`.

```python
import aspose.words as aw

# Step 1: Load a possibly corrupted document using recovery mode
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER   # Enables automatic recovery of damaged files
doc = aw.Document("YOUR_DIRECTORY/corrupted.docx", load_options)
```

**Varför detta fungerar:**  
`RecoveryMode.RECOVER` tvingar laddaren att ignorera strukturella fel och försöka återuppbygga dokumentträdet. Om filen bara är delvis skadad kommer det mesta innehållet—inklusive text, bilder och ekvationer—att återställas.

**Tips:** Om du bara vill validera ett dokument utan att reparera det, använd `RecoveryMode.NO_RECOVERY`. För full återställning, behåll inställningen som visas.

## Convert docx to markdown with LaTeX equations

När dokumentet finns i minnet kan du spara det som Markdown. Genom att sätta `office_math_export_mode` till `LATEX` instrueras Aspose.Words att rendera varje Word‑ekvation som en LaTeX‑sträng.

```python
# Step 2: Save the document as Markdown while exporting equations in LaTeX format
markdown_save_options = aw.saving.MarkdownSaveOptions()
markdown_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.md", markdown_save_options)
```

Den resulterande `output.md` kommer att se ut som en vanlig Markdown‑fil, men varje ekvation visas som `$...$` (inline) eller `$$...$$` (display) LaTeX‑kod. Detta är avgörande för efterföljande verktyg som Pandoc eller Jupyter‑anteckningsböcker som förstår LaTeX‑syntax.

## How to use recovery mode for damaged files

Återställningsläget kan återanvändas för vilken laddningsoperation som helst. Nedan är ett kompakt mönster som du kan kopiera in i andra skript:

```python
def load_with_recovery(path: str) -> aw.Document:
    opts = aw.loading.LoadOptions()
    opts.recovery_mode = aw.loading.RecoveryMode.RECOVER
    return aw.Document(path, opts)
```

Att anropa `load_with_recovery("myfile.docx")` returnerar ett `Document`‑objekt som Aspose.Words redan har försökt reparera. Denna funktion visar **hur man använder återställningsläget** säkert i olika projekt.

## Export equations latex when saving to markdown and txt

Om du också behöver en vanlig‑text‑version fungerar samma `office_math_export_mode`‑flagga med `TxtSaveOptions`.

```python
# Step 3: Save the same document as plain‑text (TXT) with LaTeX equations
txt_save_options = aw.saving.TxtSaveOptions()
txt_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.txt", txt_save_options)
```

`.txt`‑filen innehåller den råa texten från Word‑dokumentet, och varje ekvation representeras som LaTeX‑kod. Detta format är praktiskt för indexering eller för att mata in innehållet i sökmotorer som förstår LaTeX.

## Additional options: PDF with inline shapes and shape shadow

### Exportera flytande former som inline‑taggar

Flytande bilder eller textrutor kan orsaka layoutproblem vid konvertering till PDF. Genom att sätta `export_floating_shapes_as_inline_tag` tvingas Aspose.Words att behandla dessa former som vanliga inline‑element, vilket bevarar det visuella flödet.

```python
# Step 4: Export the document to PDF and tag floating shapes as inline elements
pdf_save_options = aw.saving.PdfSaveOptions()
pdf_save_options.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_save_options)
```

### Justera skuggan på den första formen

Du kanske vill förbättra utseendet på en specifik form innan du sparar den slutliga PDF‑filen. Koden nedan hämtar den första `Shape`‑noden, aktiverar dess skugga och justerar visuella parametrar.

```python
# Step 5: Adjust the shadow of the first shape and save the result
first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
shape_shadow = first_shape.shadow_format
shape_shadow.visible = True
shape_shadow.blur = 5.0          # Controls shadow softness
shape_shadow.distance = 3.0      # Distance from the shape
shape_shadow.angle = 45          # Direction of the light source
shape_shadow.color = aw.Color.black

doc.save("YOUR_DIRECTORY/shadowed.pdf")
```

**Resultat:** `shadowed.pdf` ser identisk ut som `output.pdf` men den första formen kastar nu en subtil svart skugga, vilket kan förbättra läsbarheten i presentationer.

## Complete runnable script

Nedan är det fullständiga skriptet som kombinerar alla steg. Kopiera det till en fil som heter `recover_and_convert.py`, ersätt `YOUR_DIRECTORY` med en faktisk sökväg, och kör `python recover_and_convert.py`.

```python
import aspose.words as aw

# -------------------------------------------------
# 1. Load the possibly corrupted DOCX using recovery mode
# -------------------------------------------------
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER
doc = aw.Document("YOUR_DIRECTORY/corrupted.docx", load_options)

# -------------------------------------------------
# 2. Save as Markdown with LaTeX equations
# -------------------------------------------------
markdown_save_options = aw.saving.MarkdownSaveOptions()
markdown_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.md", markdown_save_options)

# -------------------------------------------------
# 3. Save as plain‑text (TXT) with LaTeX equations
# -------------------------------------------------
txt_save_options = aw.saving.TxtSaveOptions()
txt_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.txt", txt_save_options)

# -------------------------------------------------
# 4. Export to PDF, converting floating shapes to inline
# -------------------------------------------------
pdf_save_options = aw.saving.PdfSaveOptions()
pdf_save_options.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_save_options)

# -------------------------------------------------
# 5. Add a shadow to the first shape and save a new PDF
# -------------------------------------------------
first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
shape_shadow = first_shape.shadow_format
shape_shadow.visible = True
shape_shadow.blur = 5.0
shape_shadow.distance = 3.0
shape_shadow.angle = 45
shape_shadow.color = aw.Color.black

doc.save("YOUR_DIRECTORY/shadowed.pdf")
```

### Förväntad utmatning

| Fil | Beskrivning |
|------|-------------|
| `output.md` | Markdown‑version av den ursprungliga DOCX‑filen. Alla ekvationer visas som LaTeX (`$...$` eller `$$...$$`). |
| `output.txt` | Vanlig‑text‑dump |

## What Should You Learn Next?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Hur man använder Markdown: Konvertera DOCX till Markdown med LaTeX‑ekvationer](/words/english/net/programming-with-markdownsaveoptions/how-to-use-markdown-convert-docx-to-markdown-with-latex-equa/)
- [hur man återställer docx med Aspose.Words – steg för steg](/words/english/net/programming-with-loadoptions/how-to-recover-docx-with-aspose-words-step-by-step/)
- [Återställ korrupt DOCX & konvertera Word till Markdown](/words/english/python-net/document-conversion/recover-corrupted-docx-convert-word-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}