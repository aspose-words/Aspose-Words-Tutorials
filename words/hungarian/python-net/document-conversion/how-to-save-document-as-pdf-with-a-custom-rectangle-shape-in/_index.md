---
category: general
date: 2026-10-07
description: Ismerje meg, hogyan menthet dokumentumot PDF formátumban, miközben egy
  téglalap alakzatot és egyedi árnyékot ad hozzá az Aspose.Words for Python használatával.
  Lépésről‑lépésre kód is mellékelve.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save document as pdf
- add rectangle shape
- export word to pdf
- set rectangle dimensions
- draw rectangle word
language: hu
lastmod: 2026-10-07
og_description: Mentse a dokumentumot PDF‑ként egy egyedi téglalap alakzattal az Aspose.Words
  for Python segítségével. Kövesse a teljes példát a rajzoláshoz, a formázáshoz és
  a Word PDF‑be exportálásához.
og_image_alt: Screenshot of the generated PDF showing the rectangle shape after save
  document as pdf
og_title: Dokumentum mentése PDF-ként téglalap alakúval – teljes Python útmutató
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  headline: How to save document as PDF with a custom rectangle shape in Python
  type: TechArticle
- description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  name: How to save document as PDF with a custom rectangle shape in Python
  steps:
  - name: Initialize a new blank document
    text: '```python import aspose.words as aw'
  - name: Add rectangle shape to the document
    text: '```python # Create a rectangle shape and attach it to the document. rectangle
      = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)'
  - name: Set rectangle dimensions
    text: '```python # Define width and height in points (1 point = 1/72 inch). rectangle.width
      = 200 # 200 points ≈ 2.78 inches rectangle.height = 100 # 100 points ≈ 1.39
      inches ```'
  - name: (Optional) Apply a visible custom shadow
    text: '```python shadow = rectangle.shadow_format shadow.visible = True # Show
      the shadow shadow.blur = 5.0 # Softness of the shadow edge shadow.distance =
      3.0 # How far the shadow is offset shadow.angle = 45 # Direction in degrees
      shadow.color = aw.drawing.Color.black ```'
  - name: Save document as PDF
    text: '```python output_path = "output/shadow_rectangle.pdf" document.save(output_path)
      print(f"PDF saved to {output_path}") ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Word automation
title: Hogyan menthetünk dokumentumot PDF-ként egy egyedi téglalap alakzattal Pythonban
url: /hu/python/document-conversion/how-to-save-document-as-pdf-with-a-custom-rectangle-shape-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan mentse el a dokumentumot PDF‑ként egy egyedi téglalap alakzattal Pythonban

Ha **save document as PDF**-t kell elvégeznie egyedi grafikák hozzáadásával, ez az útmutató megmutatja, hogyan. Lépésről lépésre végigvezetünk egy üres Word fájl létrehozásán, **drawing a rectangle shape**, méretének beállításán, látható árnyék alkalmazásán, és végül **export Word to PDF** használatával az Aspose.Words for Python könyvtár segítségével.

A végeredmény egy PDF lesz, amely tökéletesen elhelyezett téglalapot tartalmaz, készen áll jelentésekhez, számlákhoz vagy bármilyen dokumentum‑automatizálási szcenárióhoz. Nem szükséges külső eszköz – csak Python és az Aspose.Words csomag.

## Amire szüksége lesz

| Requirement | Why it matters |
|-------------|----------------|
| Python 3.8+ | Az Aspose.Words for Python API a modern értelmezőket célozza. |
| `aspose-words` package (`pip install aspose-words`) | Biztosítja a `aw` névtér használatát a kódrészletekben. |
| Basic familiarity with Python and object‑oriented programming | Az útmutató olyan objektumokkal dolgozik, mint a `Document` és a `Shape`. |
| Write permission to a folder where the PDF will be saved | A `save document as pdf` lépés fájlt ír a lemezre. |

> **Pro tip:** Használjon virtuális környezetet (`python -m venv venv`), hogy a függőségek izoláltak maradjanak.

## Hogyan mentse el a dokumentumot PDF‑ként egy téglalap alakzattal

Az alábbiakban egy teljes, futtatható példát talál. Minden lépést részletezünk, hogy megértse, **miért** hajtjuk végre a műveletet, ne csak **mit** csinál a kód.

### 1. lépés: Új üres dokumentum inicializálása

```python
import aspose.words as aw

# Create an empty Word document – this is the canvas for our shape.
document = aw.Document()
```

Egy új `Document` objektum létrehozása tiszta oldalak gyűjteményét biztosítja. Betölthet egy meglévő *.docx* fájlt is, ha később **export Word to PDF**-t szeretne, de az üres kezdés a példát fókuszáltan tartja.

### 2. lépés: Téglalap alakzat hozzáadása a dokumentumhoz

```python
# Create a rectangle shape and attach it to the document.
rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

# The shape must be placed inside a paragraph before it appears.
paragraph = document.first_section.body.first_paragraph
paragraph.append_child(rectangle)
```

A `add rectangle shape` lépés a `ShapeType.RECTANGLE` értéket használja. A forma beillesztésével egy bekezdésbe, az Aspose.Words tudja, hol jelenítse meg a végső PDF-ben.

### 3. lépés: Téglalap méretének beállítása

```python
# Define width and height in points (1 point = 1/72 inch).
rectangle.width = 200   # 200 points ≈ 2.78 inches
rectangle.height = 100  # 100 points ≈ 1.39 inches
```

Az explicit **rectangle dimensions** beállítása biztosítja, hogy a forma minden platformon konzisztens legyen. Használhatja a `convert_to_inches` segédfüggvényeket is, ha az angolszász mértékegységeket részesíti előnyben.

### 4. lépés: (Opcionális) Látható egyedi árnyék alkalmazása

```python
shadow = rectangle.shadow_format
shadow.visible = True          # Show the shadow
shadow.blur = 5.0              # Softness of the shadow edge
shadow.distance = 3.0          # How far the shadow is offset
shadow.angle = 45              # Direction in degrees
shadow.color = aw.drawing.Color.black
```

Az árnyék kiemeli a téglalapot a PDF-ben. A `shadow.visible` jelző szükséges; nélküle a többi tulajdonság nem hat.

### 5. lépés: Dokumentum mentése PDF‑ként

```python
output_path = "output/shadow_rectangle.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

`document.save` hívása **.pdf** kiterjesztéssel automatikusan **save document as pdf**-t hajt végre az Aspose.Words beépített PDF renderelőjével. Nem szükséges további konverziós lépés, ezért ez a módszer a javasolt módja a **export Word to PDF**-nek.

> **Miért működik:** Az Aspose.Words a dokumentum elrendezését, beleértve a téglalapot és annak árnyékát, közvetlenül a PDF adatfolyamba írja. A folyamat veszteségmentes, és megőrzi a vektoros minőséget.

## Teljes forráskód (egyetlen szkript)

```python
import aspose.words as aw

def create_pdf_with_rectangle(output_path: str):
    """
    Creates a PDF that contains a single rectangle shape with a custom shadow.
    The function demonstrates:
    • add rectangle shape
    • set rectangle dimensions
    • export Word to PDF (save document as pdf)
    """
    # 1️⃣ Create a new blank document
    document = aw.Document()

    # 2️⃣ Insert a rectangle shape
    rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

    # 3️⃣ Set the shape's size
    rectangle.width = 200   # points
    rectangle.height = 100  # points

    # 4️⃣ Configure a visible shadow
    shadow = rectangle.shadow_format
    shadow.visible = True
    shadow.blur = 5.0
    shadow.distance = 3.0
    shadow.angle = 45
    shadow.color = aw.drawing.Color.black

    # 5️⃣ Add shape to the first paragraph
    paragraph = document.first_section.body.first_paragraph
    paragraph.append_child(rectangle)

    # 6️⃣ Save the document as PDF
    document.save(output_path)
    print(f"PDF successfully saved to: {output_path}")

if __name__ == "__main__":
    create_pdf_with_rectangle("output/shadow_rectangle.pdf")
```

A szkript futtatásával a `shadow_rectangle.pdf` jön létre, amely így néz ki:

![Diagram a generált PDF‑ről, amely a téglalap alakzatot mutatja a save document as pdf után](placeholder-image.png)

*A PDF egyetlen oldalt tartalmaz, amelyen egy fekete árnyékú téglalap középen helyezkedik el a dokumentumban.*

## Gyakori kérdések és szélhelyzetek

| Question | Answer |
|----------|--------|
| **Elhelyezhetem a téglalapot egy adott helyen?** | Igen. A mentés előtt állítsa be a `rectangle.left` és `rectangle.top` értékeket (pontokban). |
| **Mi van, ha több alakzatra van szükségem?** | Hozzon létre további `Shape` objektumokat, konfigurálja őket, és fűzze hozzá ugyanahhoz vagy különböző bekezdésekhez. |
| **Az árnyék befolyásolja a PDF méretét?** | Csak csekély mértékben; az árnyék vektor metaadatként, nem raszteres képként tárolódik. |
| **Használhatom ezt meglévő *.docx* fájlok konvertálására?** | Természetesen. Cserélje le a `aw.Document()`-et `aw.Document("input.docx")`-ra, a többi lépés változatlan marad. |
| **Van mód a téglalap kitöltőszínének megváltoztatására?** | Állítsa be a `rectangle.fill_color = aw.drawing.Color.light_blue` értéket (vagy bármelyik `Color`-t, amelyet szeretne). |

## Következő lépések

Most, hogy tudja, hogyan **save document as PDF** egy egyedi téglalappal, érdemes felfedezni:

* **Export Word to PDF** fejlécekkel, láblécekkel és oldalszámokkal.  
* **Add other drawing objects** (`Ellipse`, `Polygon`) a ugyanazzal a `Shape` osztállyal.  
* **Batch process** egy mappát Word fájlokkal, ugyanazt a téglalap réteget alkalmazva mindegyikre.  

Ezek a kiterjesztések ugyanazt a mintát követik: alakzat létrehozása, tulajdonságainak beállítása, és **save document as pdf**.

---

**Summary:** Ez az útmutató bemutatta, hogyan **save document as PDF** miközben **add rectangle shape**, **set rectangle dimensions**, és egy egyedi árnyékot alkalmaz a Aspose.Words for Python segítségével. A teljes szkript készen áll a másolásra, futtatásra és saját dokumentum‑automatizálási folyamatainak testreszabására. Boldog kódolást!

## Mit érdemes legközelebb megtanulni?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket saját projektjeiben.

- [Téglalap alakzat létrehozása, árnyék hozzáadása és PDF mentése](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Téglalap hozzáadása PDF-hez az Aspose.Words segítségével – Lépésről‑lépésre útmutató](/words/english/python-net/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/)
- [Dokumentum mentése PDF‑ként az Aspose.Words segítségével – Teljes C# útmutató](/words/english/net/programming-with-pdfsaveoptions/save-document-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}