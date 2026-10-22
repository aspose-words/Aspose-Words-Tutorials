---
category: general
date: 2026-08-17
description: Hogyan mentse el a PNG-t az Aspose.Words for Python segítségével. Tanulja
  meg, hogyan adjon árnyékot az alakzatokhoz, mentse a dokumentumot PDF-ként, és exportálja
  a Word-et PNG formátumba egyetlen útmutatóban.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save png
- add shadow to shape
- save document as pdf
- export word to png
- convert word to pdf
language: hu
lastmod: 2026-08-17
og_description: Hogyan mentse el a PNG-t az Aspose.Words segítségével. Ez az útmutató
  bemutatja, hogyan adhat árnyékot egy alakzathoz, hogyan mentheti a dokumentumot
  PDF-ként, és hogyan exportálhatja a Word-et PNG formátumba.
og_image_alt: Screenshot of a Word document with a rectangle shape that has a shadow,
  saved as PNG and PDF
og_title: Hogyan menthet PNG-t és adhat árnyékot a formához az Aspose.Words használatával
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  headline: How to save PNG and add shadow to shape with Aspose.Words
  type: TechArticle
- description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  name: How to save PNG and add shadow to shape with Aspose.Words
  steps:
  - name: Pro tip
    text: If you need a sharper shadow, reduce `blur`. For a more pronounced offset,
      increase `distance`. The `Shadow` class also exposes `angle` and `transparency`
      for fine‑tuned control.
  - name: 'Optional: higher‑resolution PNG'
    text: '```python png_options = aw.image.PngSaveOptions() png_options.resolution
      = 300 # DPI doc.save("output/high_res_output.png", png_options) ```'
  - name: Expected output
    text: 'Running the script creates three files:'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Image export
title: Hogyan menthetünk PNG-t és adhatunk árnyékot alakzathoz az Aspose.Words segítségével
url: /hu/python/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan mentse el a PNG-t és adjon árnyékot az alakzathoz az Aspose.Words segítségével

Ha **hogyan mentse el a PNG-t** egy Word fájlból, ez az útmutató egy teljes, futtatható megoldást nyújt. Emellett megmutatja, hogyan **adjunk árnyékot az alakzathoz**, **mentsük el a dokumentumot PDF‑ként**, és **exportáljuk a Word‑ot PNG‑be** anélkül, hogy elhagynánk az Aspose.Words környezetet.

Az oktatóanyag mindent lefed, ami ahhoz szükséges, hogy egy üres Word dokumentumot PDF‑vé és PNG képpé alakítsunk, miközben egyszerű árnyékhatást alkalmazunk egy téglalap alakzatra. Külső eszközökre nincs szükség, és a kód az Aspose.Words for Python via .NET 7 vagy újabb verzióval működik.

## Mit fog elérni

* Új Word dokumentum létrehozása programozott módon.  
* Téglalap alakzat beszúrása és árnyékhatás konfigurálása.  
* Ugyanazon dokumentum mentése PDF fájlként.  
* Dokumentum exportálása PNG képként.  

Ezek a lépések megválaszolják a gyakori **hogyan mentse el a PNG-t** kérdést, miközben kezelik a **árnyék hozzáadása az alakzathoz** és a **dokumentum mentése PDF‑ként** feladatokat egyetlen munkafolyamatban.

## Előfeltételek

* Python 3.9 vagy újabb.  
* Aspose.Words for Python via .NET telepítve (`pip install aspose-words`).  
* Írási jogosultság a megadott kimeneti könyvtárhoz.  

Ha még nem telepítette az Aspose.Words‑t, futtassa:

```bash
pip install aspose-words
```

## Hogyan mentse el a PNG-t az Aspose.Words segítségével

Az első nagy lépés egy dokumentum és egy `DocumentBuilder` létrehozása. A builder egy folyékony API‑t biztosít tartalom, például alakzatok, táblázatok vagy szöveg beszúrásához.

```python
import aspose.words as aw

# Create a new blank document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` a teljes Word fájlt reprezentálja memóriában. `aw.DocumentBuilder` a jelenlegi beszúrási helyre mutat, amely kezdetben az első (és egyetlen) szakasz eleje.

## Árnyék hozzáadása az alakzathoz exportálás előtt

Egy alakzat lehet bármilyen rajzobjektum — téglalap, ellipszis vagy egyedi sokszög. Itt egy 100 × 100 pont méretű téglalapot hozunk létre, és egy lágy árnyékot alkalmazunk.

```python
# Insert a rectangle shape (100x100 points)
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

# Configure a simple shadow
shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Softness of the shadow edges
shape.shadow.distance = 3.0      # Distance from the shape
shape.shadow.color = aw.Color.black
```

Miért konfiguráljuk az árnyékot a mentés előtt? Az Aspose.Words a PDF és PNG exportálási fázisok során rendereli az árnyékot, így a vizuális hatás mindkét kimeneti formátumban megmarad.

### Profi tipp
Ha élesebb árnyékra van szüksége, csökkentse a `blur` értékét. Kiemeltebb eltolásért növelje a `distance` értékét. A `Shadow` osztály továbbá elérhetővé teszi az `angle` és `transparency` beállításokat a finomhangoláshoz.

## Dokumentum mentése PDF‑ként

A Word dokumentum PDF‑ként való mentése egyetlen sor, amint a tartalom készen áll. A `SaveFormat.PDF` konstans azt mondja az Aspose.Words‑nek, hogy végezze el a konverziót.

```python
# Save the document as PDF (shadow is rendered in the output)
pdf_path = "output/output.pdf"
doc.save(pdf_path, aw.SaveFormat.PDF)
```

Az eredményül kapott PDF tartalmazza a téglalapot a pontosan definiált árnyékkal. Az Aspose.Words vektoros grafikát kezel, így a PDF mérete mérsékelt marad.

## Word exportálása PNG‑be

A PNG exportálás minden oldalról raszteres képet hoz létre. Alapértelmezés szerint az Aspose.Words 96 DPI‑t használ; ezt az értéket növelheti a magasabb felbontású kimenethez egy `PngSaveOptions` objektum megadásával.

```python
# Export the same document as PNG
png_path = "output/output.png"
doc.save(png_path, aw.SaveFormat.PNG)
```

Amikor **exportálja a Word‑ot PNG‑be**, minden oldal külön PNG fájlként kerül mentésre. Mivel a példadokumentumunk csak egy oldalt tartalmaz, csak egyetlen PNG fájl jelenik meg.

### Opcionális: magasabb felbontású PNG

```python
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI
doc.save("output/high_res_output.png", png_options)
```

A magasabb DPI akkor hasznos, ha a PNG‑t nyomtatásra vagy éles bélyegképhez használják.

## Teljes szkript – másolja, illessze be és futtassa

Az alábbiakban a teljes, önálló szkript található, amely megvalósítja a fent leírt minden lépést. Mentse el `generate_assets.py` néven, és futtassa a parancssorból.

```python
import os
import aspose.words as aw

# ------------------------------------------------------------------
# 1. Prepare output folder
# ------------------------------------------------------------------
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# ------------------------------------------------------------------
# 2. Create a new blank document and a builder
# ------------------------------------------------------------------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ------------------------------------------------------------------
# 3. Insert a rectangle shape and add a shadow
# ------------------------------------------------------------------
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Soft edges
shape.shadow.distance = 3.0      # Offset from shape
shape.shadow.color = aw.Color.black

# ------------------------------------------------------------------
# 4. Save as PDF (demonstrates "save document as pdf")
# ------------------------------------------------------------------
pdf_path = os.path.join(output_dir, "output.pdf")
doc.save(pdf_path, aw.SaveFormat.PDF)

# ------------------------------------------------------------------
# 5. Export as PNG (demonstrates "how to save png")
# ------------------------------------------------------------------
png_path = os.path.join(output_dir, "output.png")
doc.save(png_path, aw.SaveFormat.PNG)

# ------------------------------------------------------------------
# 6. Optional high‑resolution PNG (demonstrates "export word to png")
# ------------------------------------------------------------------
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI for sharper output
high_res_png_path = os.path.join(output_dir, "high_res_output.png")
doc.save(high_res_png_path, png_options)

print(f"Files written to {os.path.abspath(output_dir)}")
```

### Várt kimenet

A szkript futtatása három fájlt hoz létre:

* `output/output.pdf` – egy PDF, amely egy téglalapot tartalmaz, amely fekete árnyékot vet.  
* `output/output.png` – egy 96 DPI‑s PNG renderelés ugyanarról az oldalról.  
* `output/high_res_output.png` – egy 300 DPI‑s PNG a magasabb minőségért.  

Nyissa meg bármelyik fájlt a kedvenc megjelenítőjében, hogy ellenőrizze, az árnyék pontosan úgy jelenik meg, ahogy definiálta.

## Gyakori kérdések és szélhelyzetek

**Mi van, ha a kimeneti könyvtár nem létezik?**  
A szkript meghívja az `os.makedirs(output_dir, exist_ok=True)` parancsot, amely automatikusan létrehozza a mappát. Ez megakadályozza a `FileNotFoundError` kivételt a mentési műveletek során.

**Hozzáadhatok több alakzatot különböző árnyékokkal?**  
Igen. Hozzon létre további `Shape` objektumokat, konfigurálja minden `shadow` tulajdonságát önállóan, és szúrja be őket a `builder.insert_node(shape)` hívással a mentés előtt.

**Megmarad-e az árnyék más raszteres formátumokra (pl. JPEG) történő konvertáláskor?**  
Az Aspose.Words minden, a `SaveFormat` által támogatott raszteres formátumra rendereli az árnyékot. A `aw.SaveFormat.PNG` helyett `aw.SaveFormat.JPEG` használatával az árnyék továbbra is megjelenik.

**Miben különbözik a „convert word to pdf” művelettől?**  
A `convert word to pdf` lényegében ugyanaz a művelet, amely a 4. lépésben történik. Az ugyanaz a `doc.save` hívás `SaveFormat.PDF` paraméterrel belsőleg kezeli a konverziót, megőrizve az elrendezést, betűtípusokat és grafikai elemeket, például az árnyékokat.

**Van korlátozás az alakzat méretére?**  
Az alakzatok pontban vannak mérve (1 pt ≈ 1/72 hüvelyk). Nagyon nagy méretek növelhetik a végső fájlméretet, de az Aspose.Words nem alkalmaz szigorú korlátot. Állítsa be a `width` és `height` argumentumokat az `aw.Shape` létrehozásakor a kívánt elrendezéshez.

## Következtetés

Most már tudja, **hogyan mentse el a PNG-t** egy Word dokumentumból, miközben megtanulta a **árnyék hozzáadását az alakzathoz**, a **dokumentum PDF‑ként való mentését**, és a **Word exportálását PNG‑be** az Aspose.Words for Python segítségével. A teljes szkript egy tiszta, újrahasználható mintát mutat be, amelyet nagyobb dokumentumokra, több oldalra vagy összetettebb grafikai hatásokra is adaptálhat.

A következő lépések lehetnek:

* Kísérletezés más `ShapeType` értékekkel (ellipse, cloud, stb.).  
* Using `

## Mit kellene legközelebb megtanulnia?

A következő oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API‑funkciókat és alternatív megvalósítási megközelítéseket saját projektjeiben.

- [Aspose.Words alakzat árnyék tutorial – Árnyék hozzáadása Word alakzathoz C#‑ban](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Hogyan konvertáljunk DOCX‑t PNG‑be Java‑ban – Aspose.Words](/words/english/java/document-converting/converting-documents-images/)
- [Word dokumentumok mentése PostScript‑ként Python‑ban az Aspose.Words használatával: Átfogó útmutató](/words/english/python-net/document-operations/save-docs-as-postscript-using-aspose-words-python/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}