---
category: general
date: 2026-09-30
description: Tanulja meg, hogyan hozhat létre téglalap alakzatot, hogyan alkalmazhat
  árnyékot az alakzatra, és hogyan mentheti el a Word dokumentumot az alakzattal az
  Aspose.Words for Python segítségével.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- how to add shape
- apply shadow to shape
- set shadow blur
- save word with shape
language: hu
lastmod: 2026-09-30
og_description: Gyorsan hozzon létre téglalap alakzatot egy Word dokumentumban. Ez
  az útmutató bemutatja, hogyan adjon hozzá alakzatot, hogyan alkalmazzon árnyékot
  az alakzatra, hogyan állítsa be az árnyék elmosódását, és hogyan mentse a Word dokumentumot
  az alakzattal.
og_image_alt: Screenshot of a Word document showing a rectangle shape with a soft
  shadow
og_title: Téglalap alakzat létrehozása Wordben Python segítségével – lépésről lépésre
  útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Learn how to create rectangle shape, apply shadow to shape, and save
    Word with shape using Aspose.Words for Python.
  headline: How to create rectangle shape in a Word document using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- Shapes
title: Hogyan hozhatunk létre téglalap alakzatot egy Word-dokumentumban Python segítségével
url: /hu/python/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozzunk létre téglalap alakzatot egy Word dokumentumban Python segítségével

Ha **téglalap alakzatot** kell létrehoznod egy Word fájlban, ez az útmutató egy teljes, futtatható megoldást mutat be. Megtanulod, hogyan adj hozzá alakzatot, alkalmazz árnyékhatást, állítsd be a elmosódást, és végül **mentsd el a Word dokumentumot alakzattal**, hogy az eredmény megnyitható legyen a Microsoft Word vagy bármely kompatibilis megjelenítő programban.

A példában **Aspose.Words for Python via .NET** kerül felhasználásra, egy olyan könyvtár, amely lehetővé teszi a Word dokumentumok manipulálását a Microsoft Office telepítése nélkül. Nem szükséges előzetes tapasztalat az API-val – csak alapvető Python ismeretekre van szükség.

## Mit fogsz elérni

- Téglalap beszúrása az új dokumentum első szakaszába.  
- Lágy árnyék konfigurálása az elmosódás, eltolás és szín beállításával.  
- A dokumentum lemezre mentése és a vizuális eredmény ellenőrzése.

## Előfeltételek

- Python 3.8 vagy újabb.  
- `aspose-words` csomag telepítve (`pip install aspose-words`).  
- Írási jogosultság a kimeneti könyvtárban.

## Téglalap alakzat létrehozása és megjelenésének beállítása

Az első lépés egy üres dokumentum példányosítása és egy téglalap alakzat hozzáadása. Az alakzat szolgál majd a vászonként az árnyékhatáshoz.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Step 1: Create a new blank document
doc = aw.Document()

# Step 2: Add a rectangle shape to the first section
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Optional: Define the shape’s size and position (in points)
shape.width = aw.ConvertUtil.inch_to_point(2)   # 2 inches wide
shape.height = aw.ConvertUtil.inch_to_point(1)  # 1 inch tall
shape.left = aw.ConvertUtil.inch_to_point(1)    # 1 inch from the left margin
shape.top = aw.ConvertUtil.inch_to_point(1)     # 1 inch from the top margin
```

**Miért fontos:**  
A téglalap létrehozása egy konkrét objektumot (`shape`) ad, amelyet később stílusozhatsz. Az explicit méretek beállítása biztosítja, hogy az alakzat minden platformon ugyanúgy nézzen ki.

## Hogyan adjunk hozzá alakzatot egy Word dokumentumhoz

Míg a fenti kód már hozzáadja a téglalapot, később további alakzatokat (például köröket, nyilakat) is hozzáadhatsz. Ugyanaz a minta alkalmazandó: hívd meg a `append_child` metódust a dokumentum `body` részén, és add át a kívánt `ShapeType` értéket.

```python
# Example: Adding a second shape – an ellipse
ellipse = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.ELLIPSE)
)
ellipse.width = aw.ConvertUtil.inch_to_point(1.5)
ellipse.height = aw.ConvertUtil.inch_to_point(1)
ellipse.left = aw.ConvertUtil.inch_to_point(3.5)
ellipse.top = aw.ConvertUtil.inch_to_point(1)
```

**Tipp:** Használd a `ShapeType` felsorolást az összes támogatott alakzat felfedezéséhez. Ez olvashatóbbá teszi a kódot, és elkerüli a varázsszámok használatát.

## Árnyék alkalmazása az alakzatra és árnyék elmosódásának beállítása

Az árnyék mélységet és vizuális érdeklődést ad. A `ShadowEffect` osztály lehetővé teszi az elmosódás, eltolás és szín vezérlését. Az alábbiakban egy lágy fekete árnyékot alkalmazunk a téglalapra.

```python
# Step 3: Configure a shadow effect for the rectangle
shadow = ShadowEffect()
shadow.blur = 5.0          # Sets the softness of the shadow edge
shadow.offset_x = 2.0      # Horizontal displacement from the shape
shadow.offset_y = 2.0      # Vertical displacement from the shape
shadow.color = aw.Color.black

# Step 4: Apply the shadow effect to the shape
shape.shadow = shadow
```

**Miért állítsuk be az elmosódást?**  
A `blur` határozza meg, mennyire diffúz az árnyék. Alacsony érték (pl. 1.0) éles szegélyt eredményez, míg magasabb érték (pl. 5.0) lágy elhalványulást, ami gyakran esztétikusabb.

**Szélső eset:** Ha a `blur` értéke 0, az árnyék szilárd sziluett lesz. Egyes megjelenítők aliasing hibákat produkálhatnak, ezért válassz 0‑nál nagyobb értéket a simább kimenethez.

## Word mentése alakzattal

A dokumentum mentése véglegesíti a módosításokat. A `save` metódus egy `.docx` fájlt ír, amelyet bármely modern Word processzor megnyithat.

```python
# Step 5: Save the document to see the result
output_path = "output.docx"   # Adjust the path as needed
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Amikor megnyitod a `output.docx` fájlt, egy téglalapot látsz, amely egy hüvelyknyire helyezkedik el a bal‑felső saroktól, egy lágy fekete árnyékkal, amely két ponttal jobbra és lejjebb van eltolva. Az árnyék elmosódása azt a benyomást kelti, mintha az alakzat a lapról kiemelkedne.

**Pro tipp:** Ha sok dokumentumot kell generálnod egy ciklusban, használd újra ugyanazt a `Document` példányt, és töröld a `body` tartalmát az iterációk között a memóriaigény csökkentése érdekében.

## Gyakori változatok és hibaelhárítás

| Helyzet | Mit kell módosítani | Ok |
|-----------|----------------|--------|
| Más árnyék szín | `shadow.color = aw.Color.red` | Márkaszínek használata vagy fontos alakzatok kiemelése. |
| Nagyobb árnyék eltolás | Növeld a `shadow.offset_x`/`offset_y` értékét | Mélység hangsúlyozása UI makettekhez. |
| Egyáltalán nincs árnyék | Hagyd ki a `shape.shadow = shadow` sort | Minimalista jelentésekhez hasznos. |
| Exportálás PDF‑be DOCX helyett | `doc.save("output.pdf")` | A PDF ideális csak‑olvasásra szánt terjesztéshez. |

Ha az alakzat nem jelenik meg, ellenőrizd, hogy a megfelelő szakaszhoz (`get_first_section()`) adtad-e hozzá, és hogy a dokumentum a módosítások után mentésre került-e.

## Teljes, futtatható példa

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Create a new blank document
doc = aw.Document()

# Add a rectangle shape
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
shape.width = aw.ConvertUtil.inch_to_point(2)
shape.height = aw.ConvertUtil.inch_to_point(1)
shape.left = aw.ConvertUtil.inch_to_point(1)
shape.top = aw.ConvertUtil.inch_to_point(1)

# Configure and apply a shadow
shadow = ShadowEffect()
shadow.blur = 5.0
shadow.offset_x = 2.0
shadow.offset_y = 2.0
shadow.color = aw.Color.black
shape.shadow = shadow

# Save the document
output_path = "output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

A szkript futtatása `output.docx` fájlt hoz létre, amely a téglalapot lágy árnyékkal tartalmazza. Nyisd meg a fájlt a Microsoft Wordben, hogy megerősítsd, a vizuális hatás megegyezik a leírással.

## Összegzés

Most már tudod, hogyan **hozz létre téglalap alakzatot**, **adj hozzá alakzatot** egy Word dokumentumhoz, **alkalmazz árnyékot az alakzatra**, **állítsd be az árnyék elmosódását**, és végül **mentsd el a Word dokumentumot alakzattal** az Aspose.Words for Python segítségével. Ugyanaz a minta kiterjeszthető más alakzat típusokra, színekre és hatásokra, így teljes irányítást kapsz a dokumentumgrafika felett, anélkül, hogy Office automatizálásra támaszkodnál.

**Következő lépések**

- Kísérletezz a `Shape.fill` használatával, hogy gradient vagy kép hátteret adj hozzá.  
- Használj `Paragraph` objektumokat szöveg elhelyezéséhez a téglalapon belül.  
- Kombinálj több alakzatot komplex diagramok építéséhez, majd exportáld PDF‑be a terjesztéshez.  

Nyugodtan igazítsd a kódot saját jelentés- vagy sablonkészítési igényeidhez, és oszd meg az eredményeidet a hozzászólásokban!

## Mit érdemes még megtanulni?

A következő oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}