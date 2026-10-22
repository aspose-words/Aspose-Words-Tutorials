---
category: general
date: 2026-08-04
description: Sérült docx fájlok helyreállítása az Aspose.Words helyreállítási módjával,
  és a docx konvertálása markdown formátumba, a képletek LaTeX‑ként való exportálásával.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- recover corrupted docx
- convert docx to markdown
- how to use recovery mode
- export equations latex
language: hu
lastmod: 2026-08-04
og_description: Állítsd helyre a sérült docx fájlokat az Aspose.Words helyreállítási
  móddal, majd konvertáld a docx-et markdown formátumba, miközben a képleteket LaTeX‑ként
  exportálod. Kövesd ezt a lépésről‑lépésre útmutatót, hogy PDF és TXT kimeneteket
  is készíts.
og_image_alt: Screenshot of Aspose.Words Python code converting a corrupted docx to
  markdown with LaTeX equations
og_title: Sérült docx helyreállítása és markdown formátumba konvertálása – Aspose
  útmutató
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
title: Sérült docx helyreállítása és markdownra konvertálás Aspose-szal
url: /hu/python/document-conversion/recover-corrupted-docx-and-convert-to-markdown-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Sérült docx helyreállítása és konvertálása markdownra az Aspose segítségével

Ha **sérült docx** fájlokat kell helyreállítania, az Aspose.Words beépített helyreállítási módot kínál, amely automatikusan megjavítja a sérült Word dokumentumokat. A fájl visszaállítása után **konvertálhatja a docx-et markdownra**, sőt **exportálhatja a képleteket LaTeX‑ként** a tudományos dokumentumok zökkenőmentes használatához. Ez a bemutató pontosan megmutatja, hogyan teheti ezt meg Pythonban, valamint néhány extra lehetőséget a PDF és a sima szöveg (TXT) kimenethez.

Megtanulja, hogyan:

* Betöltsön egy esetlegesen sérült DOCX‑et a helyreállítási móddal.  
* Mentse a helyreállított dokumentumot Markdown formátumban LaTeX‑formázott egyenletekkel.  
* Készítsen egy egyszerű szöveges (TXT) verziót, amely szintén tartalmazza a LaTeX egyenleteket.  
* Exportáljon PDF‑be, miközben a lebegő alakzatokat inline elemekként jelöli.  
* Állítson be egy alakzat árnyékát, és állítson elő egy végleges PDF‑et.

Nem szükséges külső eszköz – csak az ingyenes Aspose.Words for Python könyvtár.

## Előfeltételek

| Követelmény | Miért fontos |
|-------------|--------------|
| Python 3.8+ | Az Aspose.Words for Python által megkövetelt verzió |
| `aspose-words` csomag (`pip install aspose-words`) | Biztosítja a kódban használt `aw` névteret |
| Egy esetlegesen sérült DOCX fájl (pl. `corrupted.docx`) | A helyreállítási munkafolyamat bemutatásához |
| Írási jogosultság a kimeneti könyvtárban | A szkript több fájlt (`.md`, `.txt`, `.pdf`) ír |

Győződjön meg róla, hogy az Aspose.Words licenc (ingyenes próba vagy megvásárolt) megfelelően van beállítva, ha túllépi a kiértékelési korlátokat.

## Sérült docx helyreállítása az Aspose.Words segítségével

Az első lépés, hogy az Aspose.Words‑nek jelezzük, hogy a bemeneti fájl potenciálisan sérült. Ehhez a `LoadOptions.recovery_mode` használatos.

```python
import aspose.words as aw

# Step 1: Load a possibly corrupted document using recovery mode
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER   # Enables automatic recovery of damaged files
doc = aw.Document("YOUR_DIRECTORY/corrupted.docx", load_options)
```

**Miért működik:**  
A `RecoveryMode.RECOVER` arra kényszeríti a betöltőt, hogy figyelmen kívül hagyja a strukturális hibákat, és megpróbálja újraépíteni a dokumentumfát. Ha a fájl csak részben sérült, a legtöbb tartalom – beleértve a szöveget, képeket és egyenleteket – helyreáll.

**Tipp:** Ha csak ellenőrizni szeretne egy dokumentumot javítás nélkül, használja a `RecoveryMode.NO_RECOVERY` értéket. Teljes helyreállításhoz hagyja meg a fenti beállítást.

## docx konvertálása markdownra LaTeX egyenletekkel

Miután a dokumentum a memóriában van, menthető Markdown formátumban. Az `office_math_export_mode` `LATEX`‑re állítása azt mondja az Aspose.Words‑nek, hogy minden Word‑egyenletet LaTeX karakterláncként rendereljen.

```python
# Step 2: Save the document as Markdown while exporting equations in LaTeX format
markdown_save_options = aw.saving.MarkdownSaveOptions()
markdown_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.md", markdown_save_options)
```

Az eredményül kapott `output.md` egy hagyományos Markdown fájl lesz, de minden egyenlet `$...$` (inline) vagy `$$...$$` (display) LaTeX kódként jelenik meg. Ez elengedhetetlen a Pandoc vagy Jupyter notebookokhoz, amelyek a LaTeX szintaxist értik.

## Hogyan használjuk a helyreállítási módot sérült fájlokhoz

A helyreállítási mód újra felhasználható bármely betöltési művelethez. Az alábbi kompakt mintát más szkriptekbe is beillesztheti:

```python
def load_with_recovery(path: str) -> aw.Document:
    opts = aw.loading.LoadOptions()
    opts.recovery_mode = aw.loading.RecoveryMode.RECOVER
    return aw.Document(path, opts)
```

A `load_with_recovery("myfile.docx")` hívás egy `Document` objektumot ad vissza, amelyet az Aspose.Words már megpróbált javítani. Ez a függvény **biztonságos helyreállítási mód használatát** demonstrálja projektek között.

## Egyenletek exportálása LaTeX‑ként markdown és txt mentésekor

Ha egyszerű szöveges verzióra is szüksége van, ugyanaz a `office_math_export_mode` kapcsoló működik a `TxtSaveOptions`‑szel.

```python
# Step 3: Save the same document as plain‑text (TXT) with LaTeX equations
txt_save_options = aw.saving.TxtSaveOptions()
txt_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.txt", txt_save_options)
```

A `.txt` fájl a Word dokumentum nyers szövegét tartalmazza, és minden egyenlet LaTeX kódként jelenik meg. Ez a formátum hasznos indexeléshez vagy keresőmotoroknak, amelyek a LaTeX‑et értik.

## További lehetőségek: PDF inline alakzatokkal és alakzati árnyékkal

### Lebegő alakzatok exportálása inline címkékkel

A lebegő képek vagy szövegdobozok elrendezési problémákat okozhatnak PDF‑re konvertáláskor. Az `export_floating_shapes_as_inline_tag` beállítása arra kényszeríti az Aspose.Words‑t, hogy ezeket az alakzatokat szabályos inline elemekként kezelje, megőrizve a vizuális folyamatot.

```python
# Step 4: Export the document to PDF and tag floating shapes as inline elements
pdf_save_options = aw.saving.PdfSaveOptions()
pdf_save_options.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_save_options)
```

### Az első alakzat árnyékának beállítása

Lehet, hogy egy adott alakzat megjelenését szeretné javítani a végső PDF mentése előtt. Az alábbi kód eléri az első `Shape` csomópontot, engedélyezi az árnyékot, és finomhangolja a vizuális paramétereket.

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

**Eredmény:** A `shadowed.pdf` azonos a `output.pdf`‑vel, de az első alakzat most egy finom fekete árnyékot vet, ami javíthatja az olvashatóságot prezentációkban.

## Teljesen futtatható szkript

Az alábbi teljes szkript egyesíti az összes lépést. Másolja egy `recover_and_convert.py` nevű fájlba, cserélje le a `YOUR_DIRECTORY`‑t a tényleges útvonalra, és futtassa a `python recover_and_convert.py` parancsot.

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

### Várható kimenet

| Fájl | Leírás |
|------|--------|
| `output.md` | Az eredeti DOCX markdown változata. Minden egyenlet LaTeX‑ként jelenik meg (`$...$` vagy `$$...$$`). |
| `output.txt` | Plain‑text kiíratás |

## Mit érdemes még megtanulni?

A következő oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljesen működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API‑funkciókat és alternatív megvalósítási megközelítéseket saját projektjeiben.

- [Hogyan használjuk a Markdown‑ot: DOCX konvertálása markdownra LaTeX egyenletekkel](/words/english/net/programming-with-markdownsaveoptions/how-to-use-markdown-convert-docx-to-markdown-with-latex-equa/)
- [hogyan állítsuk helyre a docx‑et az Aspose.Words‑szel – lépésről‑lépésre](/words/english/net/programming-with-loadoptions/how-to-recover-docx-with-aspose-words-step-by-step/)
- [Sérült DOCX helyreállítása és Word konvertálása markdownra](/words/english/python-net/document-conversion/recover-corrupted-docx-convert-word-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}