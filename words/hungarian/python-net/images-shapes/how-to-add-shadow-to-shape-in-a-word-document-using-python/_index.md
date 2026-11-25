---
category: general
date: 2026-11-25
description: Adj árnyékot a formához egy Word dokumentumban Python segítségével. Tanulja
  meg, hogyan szúrjon be téglalap alakzatot a Wordben, és hogyan alkalmazzon átlátszó
  árnyékot az Aspose.Words használatával.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- insert rectangle shape word
- how to create word document python
- Aspose.Words Python
- shape formatting Python
language: hu
lastmod: 2026-11-25
og_description: Árnyék hozzáadása alakzathoz egy Word-dokumentumban Python használatával.
  Ez az útmutató bemutatja, hogyan szúrjunk be egy téglalap alakzatot a Wordbe, és
  állítsunk be 30 %-os átlátszó árnyékot az Aspose.Words segítségével.
og_image_alt: Add shadow to shape example in a Word document created by Python
og_title: Árnyék hozzáadása alakzathoz egy Word-dokumentumban Python segítségével
  – lépésről lépésre útmutató
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Add shadow to shape in a Word document with Python. Learn how to insert
    rectangle shape in Word and apply a transparent shadow using Aspose.Words.
  headline: How to add shadow to shape in a Word document using Python
  type: TechArticle
tags:
- Python
- Aspose.Words
- Word automation
title: Hogyan adjunk árnyékot egy alakzathoz egy Word-dokumentumban Python használatával
url: /hu/python/images-shapes/how-to-add-shadow-to-shape-in-a-word-document-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan adjunk árnyékot alakzatnak egy Word dokumentumban Python segítségével

Ha **árnyékot kell adni egy alakzathoz** egy Word dokumentumban, ez az útmutató egy teljes, futtatható megoldást mutat be. Megmutatjuk, hogyan hozhatsz létre egy Word fájlt, hogyan szúrj be egy téglalap alakzatot, és hogyan alkalmazz 30 %-os átlátszó árnyékot – mindezt az Aspose.Words for Python könyvtárral.

A Word dokumentumok programozott kezelése megkímél a kézi formázástól, és lehetővé teszi jelentések, szerződések vagy marketing szórólapok tömeges generálását. A tutorial végére képes leszel megválaszolni a „**how to create Word document python**” kérdést egy azonnal futtatható kódrészlettel.

## Előfeltételek

* Telepített Python 3.8 vagy újabb.
* Aktív Aspose.Words for Python licenc (az ingyenes próba a kiértékeléshez használható).
* `aspose-words` csomag telepítve a `pip install aspose-words` paranccsal.
* Egy mappa, ahová az output fájlt írhatod (cseréld le a kódban a `YOUR_DIRECTORY` értéket).

További függőségek nem szükségesek.

## 1. lépés: Új Word dokumentum létrehozása

Az első lépés egy `Document` objektum példányosítása. Ez az objektum a teljes .docx fájlt képviseli a memóriában.

```python
import aspose.words as aw

# Create an empty Word document
doc = aw.Document()
# DocumentBuilder provides a convenient API for adding content
builder = aw.DocumentBuilder(doc)
```

`DocumentBuilder` úgy működik, mint egy virtuális kurzor. Amikor meghívod a metódusait, a könyvtár a megfelelő elemeket a jelenlegi kurzorpozícióba illeszti.

## 2. lépés: Téglalap alakzat beszúrása a Word dokumentumba

Ezután a **téglalap alakzat beszúrása a Word dokumentumba** a builder `insert_shape` metódusával történik. A metódus megköveteli az alakzat típusát és méretét pontban (1 pont = 1/72 hüvelyk).

```python
# Insert a rectangle shape that is 100 points wide and 50 points tall
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)
```

A méreteket a saját tervezésedhez igazíthatod. A téglalap a dokumentum rajzrétegének részévé válik, ami azt jelenti, hogy később módosíthatod a kitöltését, körvonalát vagy árnyékát.

## 3. lépés: Az alakzat árnyékformátumának elérése

Minden rajzobjektum rendelkezik egy `shadow_format` tulajdonsággal, amely az árnyék megjelenését szabályozza. Szerezd meg ezt, hogy beállíthasd az átlátszóságot, eltolást, elmosódást és a színt.

```python
# Get the ShadowFormat object for the rectangle
shadow = shape.shadow_format
```

Ekkor az alakzat az alapértelmezett árnyékkal rendelkezik (valójában nincs árnyék). A `ShadowFormat` objektum tartalmazza az összes paramétert, amely a realisztikus hatás létrehozásához szükséges.

## 4. lépés: Az árnyék 30 %-os átlátszóvá tétele

Az átlátszóság `0` (teljesen átlátszatlan) és `1` (teljesen átlátszó) közötti értékkel van megadva. `0.3` beállítása 30 %-os átlátszó árnyékot eredményez, ami gyakran elegendő a mélység hozzáadásához anélkül, hogy elnyomná a szöveget.

```python
# Apply a 30 % transparent shadow
shadow.transparency = 0.3
# Optional: adjust other shadow properties for a nicer look
shadow.visible = True               # Ensure the shadow is turned on
shadow.distance = 4                 # Distance of the shadow from the shape (points)
shadow.blur = 4                     # Amount of blur applied to the shadow
shadow.color = aw.Color.black       # Shadow color
```

Ezek a további tulajdonságok nem kötelezőek, de bemutatják, hogyan finomhangolhatod a hatást. A `visible` jelző elengedhetetlen; ha elfelejted, az árnyék nem jelenik meg, még ha a többi beállítás is meg van adva.

## 5. lépés: Dokumentum mentése az eredmény megtekintéséhez

Végül írd a dokumentumot a lemezre. A keletkezett `.docx` fájl megnyitása a Microsoft Wordben vagy bármely kompatibilis megjelenítőben a téglalapot mutatja, amelyre az átlátszó árnyék alkalmazva van.

```python
# Save the document to the desired location
output_path = r"YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Amikor megnyitod a `output.docx` fájlt, egy egyszerű téglalapot látsz, amelynek finom szürke árnyéka a jobb alsó irányba van eltolva. Az árnyék 30 %-os átlátszósága azt a benyomást kelti, mintha az alakzat a lapról kiemelkedne.

![Add shadow to shape example](placeholder-image.png){: .align-center alt="Árnyék hozzáadása alakzathoz példa egy Python‑nal létrehozott Word dokumentumban"}

## Teljes, futtatható szkript

Az összes részegység egyesítése egy önálló szkriptet eredményez, amelyet azonnal másolhatsz, beilleszthetsz és futtathatsz.

```python
import aspose.words as aw

def create_word_with_shadow(output_path: str):
    """
    Creates a Word document that contains a rectangle shape
    with a 30 % transparent shadow.
    """
    # Step 1: Initialize document and builder
    doc = aw.Document()
    builder = aw.DocumentBuilder(doc)

    # Step 2: Insert rectangle shape
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)

    # Step 3: Access shadow format
    shadow = shape.shadow_format

    # Step 4: Configure shadow properties
    shadow.visible = True
    shadow.transparency = 0.3
    shadow.distance = 4
    shadow.blur = 4
    shadow.color = aw.Color.black

    # Step 5: Save the document
    doc.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    # Replace with a valid folder on your machine
    create_word_with_shadow(r"YOUR_DIRECTORY/output.docx")
```

**Várható kimenet:** A generált `output.docx` megnyitása egyetlen oldalt mutat egy téglalappal, amely enyhe, félig átlátszó árnyékot vet. További formázás nem szükséges.

## Gyakori változatok és szélhelyzetek

| Helyzet | Hogyan módosítsuk a kódot |
|-----------|-----------------------|
| **Másik alakzat típus** (pl. ellipszis) | Cseréld le a `aw.drawing.ShapeType.RECTANGLE`-t `aw.drawing.ShapeType.ELLIPSE`-ra. |
| **Egyéni árnyék szín** | Állítsd be a `shadow.color = aw.Color.from_argb(255, 128, 0, 0)`-t egy vöröses árnyékhoz. |
| **Több alakzat** | Hívd meg többször a `builder.insert_shape`-t; minden hívás egy külön `Shape` objektumot ad vissza, amelyet önállóan formázhatsz. |
| **Mentés PDF‑ként** | Cseréld le a `doc.save(output_path)`-t `doc.save(output_path.replace('.docx', '.pdf'))`-re, és használd a `.pdf` kiterjesztést. |
| **Licenc nélkül futtatás** | Az ingyenes próba egy vízjelet helyez az első oldalra. Szerezz licencet a vízjel eltávolításához a termelésben való használathoz. |

Ezek a változatok azt mutatják, hogy ugyanaz a minta – dokumentum létrehozása, alakzat beszúrása, `shadow_format` beállítása, mentés – a legtöbb automatizálási forgatókönyvre alkalmazható.

## Tippek és bevált gyakorlatok

* **A builder újrahasználata**: Tarts egyetlen `DocumentBuilder` példányt a teljes dokumentumhoz, hogy elkerüld a felesleges objektumok létrehozását.
* **Erőforrások felszabadítása**: Hosszú távú szolgáltatásokban hívd meg a `doc.dispose()`-t a mentés után a natív memória felszabadításához.
* **Kimenet ellenőrzése**: Használd a `doc.validate(aw.ValidationType.FULL_VALIDATION)`-t a mentés előtt, ha biztosítani szeretnéd a megfelelőséget az Open XML szabványnak.
* **Verziókompatibilitás**: A kód az Aspose.Words for Python ≥ 22.9 verzióval működik. Győződj meg róla, hogy a csomagod naprakész a `pip install --upgrade aspose-words` paranccsal.

## Következtetés

Most már tudod, hogyan **adj árnyékot egy alakzathoz** egy Word dokumentumban Python segítségével. Az öt lépés – dokumentum létrehozása, **téglalap alakzat beszúrása a Word dokumentumba**, az árnyék konfigurálása és mentés – követésével automatizálhatod a kifinomult dokumentumgenerálást jelentések, számlák vagy marketing anyagok számára.

Innen tovább felfedezheted a többi formázási lehetőséget, például a színátmenetes kitöltéseket, a szöveg körbefuttatását vagy a dokumentum PDF‑be konvertálását. Ezek a témák mind a tutorialban bemutatott `DocumentBuilder` és alakzat‑formázási koncepciókra épülnek.

Boldog kódolást, és élvezd a vizuális mélységet, amelyet egy egyszerű árnyék hozhat automatizált Word dokumentumaidba!

## Mit érdemes még megtanulni?

A következő tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Hogyan hozz létre téglalap alakzatot egy Word dokumentumban Python segítségével](/words/english/python-net/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/)
- [Árnyék hozzáadása alakzathoz Pythonban – Teljes Aspose.Words tutorial](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [Üres Word dokumentum létrehozása és árnyék hozzáadása alakzathoz – Teljes Python útmutató](/words/english/python-net/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-pyth/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}