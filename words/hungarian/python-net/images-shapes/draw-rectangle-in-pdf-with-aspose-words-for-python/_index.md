---
category: general
date: 2026-08-07
description: Tegyen téglalapot PDF-be az Aspose.Words for Python használatával, és
  tanulja meg, hogyan adjon árnyékot az alakzathoz, hogyan konfigurálja az alakzat
  árnyékát, valamint hogyan mentse a dokumentumot PDF-ként.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle in pdf
- add shadow to shape
- save document as pdf
- configure shape shadow
language: hu
lastmod: 2026-08-07
og_description: Tegyen téglalapot PDF-be az Aspose.Words for Python segítségével.
  Ez az útmutató bemutatja, hogyan adhat árnyékot az alakzatnak, hogyan konfigurálhatja
  az alakzat árnyékát, és hogyan mentheti a dokumentumot PDF formátumban a professzionális
  dokumentumgenerálás érdekében.
og_image_alt: PDF page showing a rectangle shape with a visible shadow created by
  Aspose.Words for Python
og_title: Téglalap rajzolása PDF-ben az Aspose.Words for Python segítségével – útmutató
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Draw rectangle in PDF using Aspose.Words for Python and learn how to
    add shadow to shape, configure shape shadow, and save document as PDF.
  headline: Draw rectangle in PDF with Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF
- Shape
- Shadow
title: Téglalap rajzolása PDF-ben az Aspose.Words for Python segítségével
url: /hu/python/images-shapes/draw-rectangle-in-pdf-with-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Téglalap rajzolása PDF-ben az Aspose.Words for Python segítségével

Ha Pythonban kell **draw rectangle in PDF**, ez az útmutató egy teljes, azonnal futtatható megoldást nyújt. Megmutatja pontosan, hogyan **add shadow to shape**, hogyan konfigurálja azt az árnyékot, és végül hogyan **save document as PDF** a terjesztéshez vagy archiváláshoz.

Árnyékolt téglalap létrehozása gyakori igény jelentések, számlák vagy vizuális megjegyzések esetén. A tutorial végére egyetlen szkriptet fogsz birtokolni, amely PDF-et generál egy valósághű árnyékkal ellátott téglalappal, és megérted, hogyan állíthatod be a méretet, színt és eltolást bármilyen dizájnhoz.

## Előfeltételek

* Python 3.8+ telepítve.
* Az Aspose.Words for Python via .NET csomag (`aspose-words`) – telepítés:

```bash
pip install aspose-words
```

* Írási jogosultság a mappához, ahová a PDF-et menteni szeretnéd.

Nem szükséges további könyvtár; az Aspose.Words belsőleg kezeli az alakzatok létrehozását, az árnyék konfigurálását és a PDF exportálást.

## 1. lépés: Új üres dokumentum létrehozása (draw rectangle in PDF – inicializálás)

Az első lépés egy `Document` objektum példányosítása. Ez az objektum képviseli a teljes PDF-fájlt, és tárolóként szolgál a szakaszok, bekezdések és alakzatok számára.

```python
import aspose.words as aw

# Create an empty Word document – it will become a PDF later
doc = aw.Document()
```

**Why this matters:** Az Aspose.Words a PDF-generálást a Word-dokumentummodell konverziójaként kezeli, ezért egy `Document`‑tal kezdünk, még akkor is, ha a végső kimenet PDF.

## 2. lépés: Téglalap alakzat beszúrása a dokumentum törzsébe

A téglalap egy konkrét `ShapeType`. Az első szakasz testére helyezzük, ami PDF‑ként mentve automatikusan új oldalt hoz létre.

```python
# Append a rectangle shape to the first section's body
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Set the rectangle's dimensions (points = 1/72 inch)
rectangle.width = 200   # 200 pt ≈ 2.78 in
rectangle.height = 100  # 100 pt ≈ 1.39 in

# Optional: give the shape some visible text
rectangle.text = "Shadow demo"
```

**Explanation:** A `width` és `height` tulajdonságok szabályozzák az alakzat vizuális méretét a PDF-ben. Szöveg hozzáadása megkönnyíti a téglalap ellenőrzését a tesztelés során.

## 3. lépés: Árnyék hozzáadása az alakzathoz – engedélyezés és testreszabás

Most bekapcsoljuk az árnyékhatást, és finomhangoljuk a megjelenését. Itt jön képbe a **add shadow to shape** kulcsszó.

```python
# Access the shape's shadow effect object
shadow = rectangle.shadow_effect

# Make the shadow visible
shadow.visible = True

# Configure blur radius (pt) – higher values produce a softer edge
shadow.blur = 8

# Set the distance (offset) from the shape in points
shadow.distance = 5

# Define the direction of the shadow in degrees (0 = right, 90 = down)
shadow.angle = 45

# Choose a shadow color – black works for most documents
shadow.color = aw.drawing.Color.black
```

**Why configure shape shadow?** A `blur`, `distance` és `angle` beállítása lehetővé teszi a valósághű megvilágítás szimulálását, ami javítja az olvashatóságot és a vizuális hierarchiát a generált PDF-ekben.

## 4. lépés: Dokumentum mentése PDF‑ként – végső kimenet

Miután a téglalap és az árnyéka definiálva van, az utolsó lépés a Word-dokumentum exportálása PDF‑be. Ez teljesíti a **save document as pdf** követelményt.

```python
# Define the output path – replace YOUR_DIRECTORY with an actual folder
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)
print(f"PDF saved to {output_path}")
```

Amikor megnyitod a `shadow_rectangle.pdf`‑t, egyetlen oldalt látsz, amelyen egy szürke szegélyű téglalap szerepel „Shadow demo” címmel és egy tiszta, átlós árnyékkal.

### Várt kimenet

* Egy `shadow_rectangle.pdf` nevű PDF‑fájl.
* Egy oldal 200 pt × 100 pt méretű téglalappal.
* Egy látható árnyék, amely 5 pt‑el el van tolva 45°‑os szöggel, 8 pt‑es elmosással.

## 5. lépés: Változatok és szélhelyzetek felfedezése (opcionális)

Az alábbiakban gyakori finomhangolásokat találsz, amelyekre valós projektekben szükség lehet:

| Változat | Code snippet | Mikor használjuk |
|-----------|--------------|-------------------|
| **Másik alakzattípus** (pl. ellipszis) | `aw.drawing.ShapeType.OVAL` instead of `RECTANGLE` | Kerekített grafikák vagy jelvények esetén |
| **Egyedi árnyék szín** | `shadow.color = aw.drawing.Color.from_argb(255, 100, 100, 100)` | Amikor szürke vagy márkaspecifikus árnyék szükséges |
| **Több alakzat** | Repeat the shape‑creation block and adjust `left`/`top` properties | Komplex diagramok építéséhez |
| **Nincs szöveg az alakzatban** | Omit `rectangle.text = "..."` | Ha az alakzat csak dekoratív |
| **Magasabb DPI kimenet** | `doc.save(output_path, aw.SaveFormat.PDF, aw.PdfSaveOptions())` with `PdfSaveOptions` set for image quality | Nyomtatásra kész PDF‑ekhez |

**Pro tip:** Mindig állítsd be a `shadow.visible = True` értéket, mielőtt más tulajdonságokat módosítanál; különben a változtatások csendben figyelmen kívül maradnak.

## Teljes szkript – másold, illeszd be és futtasd

```python
import aspose.words as aw

# 1️⃣ Create a new blank document
doc = aw.Document()

# 2️⃣ Add a rectangle shape
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
rectangle.width = 200          # width in points
rectangle.height = 100         # height in points
rectangle.text = "Shadow demo"

# 3️⃣ Configure a visible shadow effect
shadow = rectangle.shadow_effect
shadow.visible = True
shadow.blur = 8                # blur radius (pt)
shadow.distance = 5            # offset distance (pt)
shadow.angle = 45              # direction (degrees)
shadow.color = aw.drawing.Color.black

# 4️⃣ Save the document as a PDF
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)

print(f"PDF successfully created at: {output_path}")
```

Futtasd a szkriptet a terminálodból vagy IDE‑ből. Cseréld le a `YOUR_DIRECTORY`‑t egy valós mappára, például `"/tmp"` vagy `"C:\\Users\\Me\\Documents"`.

## Összegzés

Most már tudod, hogyan **draw rectangle in PDF** az Aspose.Words for Python segítségével, hogyan **add shadow to shape**, hogyan **configure shape shadow**, és hogyan **save document as PDF**. A teljes példa minden lépést bemutat a dokumentum létrehozásától a végső exportig, az opcionális változatok pedig megmutatják, hogyan lehet a kódot összetettebb forgatókönyvekhez igazítani.

A következőket is érdemes felfedezni:

* Más alakzattípusok hozzáadása (`ShapeType.LINE`, `ShapeType.ELLIPSE`).
* Gradiens kitöltések vagy szegélyek alkalmazása a vizuális hatás fokozásához.
* `PdfSaveOptions` használata betűtípusok beágyazásához vagy a képtömörítés szabályozásához.

Nyugodtan kísérletezz a paraméterekkel, hogy megfeleljenek a márkád vagy a tervezési irányelveidnek. Boldog PDF‑szkriptelést!

## Mi legyen a következő tanulnivalód?

Az alábbi tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás komplett, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API‑funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [PDF könyvjelzők optimalizálása Aspose.Words for Python használatával](/words/english/python-net/performance-optimization/optimize-pdf-bookmarks-aspose-words-python/)
- [PDF betöltés optimalizálása Pythonban Aspose Words Képek kihagyásával](/words/hindi/python-net/performance-optimization/optimize-pdf-loading-python-aspose-words-skip-images/)
- [Aspose Words Python PDF manipuláció](/words/hongkong/python-net/document-operations/aspose-words-python-pdf-manipulation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}