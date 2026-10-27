---
category: general
date: 2026-10-16
description: Hozzon létre egy üres Word-dokumentumot, szúrjon be alakzatot a Wordben,
  adjon hozzá külső árnyékot, és mentse PDF-ként Python segítségével.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert shape in word
- save as pdf python
- add outer shadow shape
- create pdf with shape
language: hu
lastmod: 2026-10-16
og_description: Készítsen egy üres Word-dokumentumot külső árnyékú alakzattal az Aspose.Words
  for Python segítségével. Ez az útmutató bemutatja, hogyan szúrja be az alakzatot,
  alkalmazza az árnyékot, és mentse a fájlt PDF formátumban.
og_image_alt: Screenshot of a Word document containing a rectangle shape with an outer
  shadow, saved as PDF
og_title: Üres Word-dokumentum alakzatárnyékkal – Python útmutató
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document, insert shape in Word, add outer shadow,
    and save as PDF using Python.
  headline: Create blank Word document with shadowed shape in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- PDF generation
- Shape styling
title: Üres Word-dokumentum létrehozása árnyékolt alakzattal Pythonban
url: /hu/python/word-automation/create-blank-word-document-with-shadowed-shape-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Üres Word dokumentum létrehozása árnyékolt alakzattal Pythonban

Ha **üres Word dokumentumot** kell létrehoznod, és egy egyedi grafikát szeretnél hozzáadni, ez az útmutató mindezt lefedi. Lépésről lépésre bemutatjuk, hogyan **szúrj be alakzatot a Wordbe**, alkalmazz **külső árnyékot az alakzatra**, és végül **mentsd PDF‑ként Python segítségével**.

Megtanulod, hogyan állítsd be az Aspose.Words for Python‑t, hogyan építs fel egy téglalapot, hogyan formázd meg az árnyékát, és hogyan generálj egy PDF‑et, amely megőrzi a vizuális hatást. Nem szükséges előzetes tapasztalat az Aspose API‑val, de alapvető Python ismeretekkel és egy működő Python 3.10‑es vagy újabb telepítéssel kell rendelkezned.

## Előfeltételek

Mielőtt elkezdenéd, győződj meg róla, hogy a következők rendelkezésre állnak:

* Python 3.10 vagy újabb telepítve.
* Aktív Aspose.Words for Python licenc (az ingyenes próba is elegendő értékeléshez).
* `pip` hozzáférés a `aspose-words` csomag telepítéséhez.
* Írási jogosultság a könyvtárban, ahová a PDF‑et menteni fogod.

A könyvtár telepíthető egyetlen paranccsal:

```bash
pip install aspose-words
```

## Üres Word dokumentum létrehozása – környezet beállítása

Az első lépés egy üres Word fájl létrehozása, amely a vászonként szolgál az alakzat számára.

```python
import aspose.words as aw

# Initialize a new, empty document
doc = aw.Document()
# DocumentBuilder provides convenient methods for adding content
builder = aw.DocumentBuilder(doc)
```

Az `aw.Document()` egy teljesen üres Word fájlt reprezentál. A `DocumentBuilder` használatával hozzáférhetsz olyan metódusokhoz, mint az `insert_shape`, amelyet a következő lépésben fogunk használni.

## Alakzat beszúrása a Wordbe és méretek beállítása

Most hozzáadunk egy téglalapot, amely később külső árnyékot kap. A méret pontban van megadva (1 pt ≈ 1/72 hüvelyk).

```python
# Insert a rectangle shape with a width of 200 pt and a height of 100 pt
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)
```

Az `insert_shape` hívás egy `Shape` objektumot ad vissza, amelyet tovább testreszabhatunk. Ebben a pontban a dokumentum már tartalmaz egy látható téglalapot, amikor Microsoft Word‑ben megnyitod.

## Külső árnyék hozzáadása – az effektus testreszabása

Az Aspose.Words egy `ShadowEffect` osztályt biztosít az árnyék tulajdonságainak meghatározásához, például stílus, elmosódás, távolság és szín.

```python
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a new shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # Choose an outer shadow
shadow.blur = 5.0                         # Softness of the shadow edges
shadow.distance = 3.0                     # Offset distance from the shape
shadow.color = aw.Color.black             # Shadow color

# Apply the shadow to the rectangle
rectangle.shadow = shadow
```

A `style` értékének `OUTER` beállítása biztosítja, hogy az árnyék a téglalap szegélye kívül jelenjen meg, így egy finom 3‑D hatást kölcsönöz. Kísérletezhetsz a `blur` és a `distance` értékekkel, hogy szorosabb vagy szórtabb árnyékot érj el.

## PDF‑ként mentés Pythonban – a dokumentum befejezése

Az alakzat stílusának beállítása után a dokumentum közvetlenül PDF‑ként menthető. Az Aspose.Words belsőleg kezeli a konverziót, megőrizve az árnyék hatását.

```python
output_path = "output/shape_with_shadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Amikor a `shape_with_shadow.pdf` fájlt bármely PDF‑olvasóban megnyitod, a téglalap pontosan úgy jelenik meg, ahogy a Wordben láttad, külső árnyékkal.

## Teljes működő példa

Az alábbiakban a teljes szkript látható, amely egyesíti az összes lépést. Másold be egy `create_word_with_shadow.py` nevű fájlba, majd futtasd.

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1. Create a blank Word document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2. Insert a rectangle shape
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)

# 3. Define and apply an outer shadow
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER
shadow.blur = 5.0
shadow.distance = 3.0
shadow.color = aw.Color.black
rectangle.shadow = shadow

# 4. Save the document as PDF
pdf_path = os.path.join(output_dir, "shape_with_shadow.pdf")
doc.save(pdf_path)

print(f"PDF generated at: {pdf_path}")
```

**Várt kimenet**

A szkript futtatása egy megerősítő sorral zárul, például:

```
PDF generated at: output/shape_with_shadow.pdf
```

A létrejött PDF megnyitásakor egyetlen oldalon egy 200 pt × 100 pt méretű téglalap látható, amelynek puha fekete külső árnyéka van.

## Gyakori variációk és szélhelyzetek

* **Árnyék színének módosítása** – Cseréld le az `aw.Color.black`‑t bármely más `aw.Color` értékre, például `aw.Color.red` vagy `aw.Color.from_argb(255, 0, 120, 215)`.
* **Másik alakzat használata** – Változtasd meg az `aw.drawing.ShapeType.RECTANGLE`‑t `OVAL`, `DIAMOND` vagy bármely támogatott enum értékre.
* **Mentés DOCX‑ként PDF helyett** – Hívd meg a `doc.save("output/shape.docx")`‑t a Word formátum megtartásához.
* **Több alakzat** – Hozz létre további alakzatokat a `builder.insert_shape` újbóli meghívásával; minden alakzat saját `ShadowEffect`‑et kaphat.

**Pro tipp:** Ha egy adott helyre szeretnéd pozícionálni az alakzatot, állítsd be a `rectangle.left` és `rectangle.top` értékeket a beszúrás után. Így pixel‑pontos kontrollt kapsz a elhelyezés felett.

## Összegzés

Most már tudod, hogyan **hozz létre üres Word dokumentumot**, **szúrj be alakzatot a Wordbe**, **adj hozzá külső árnyékot az alakzathoz**, és **mentsd PDF‑ként Python segítségével**. A teljes kódminta bemutatja az elejétől a végéig tartó munkafolyamatot, a magyarázatok pedig tisztázzák, miért szükséges minden egyes API‑hívás.

Innen tovább felfedezheted a fejlettebb stíluslehetőségeket, hozzáadhatsz szöveget az alakzathoz, vagy több alakzatot kombinálhatsz komplex diagramok építéséhez. Kísérletezz a különböző árnyékparaméterekkel, hogy megfeleljenek márkád vizuális nyelvének, és integráld ezt a megközelítést nagyobb dokumentum‑generálási folyamatokba.

Boldog kódolást!


## Mit érdemes még megtanulni?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljesen működő kódpéldákat tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API‑funkciókat és alternatív megvalósítási módokat a saját projektjeidben.

- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Create PDF from Word – Complete Python Guide with Aspose.Words](/words/english/python-net/document-conversion/create-pdf-from-word-complete-python-guide-with-aspose-words/)
- [Add Shadow to Shape in Word with Aspose.Words – Step‑by‑Step](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}