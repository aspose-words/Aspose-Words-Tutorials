---
category: general
date: 2026-10-04
description: Hogyan hozzunk létre dokumentumot Pythonban, és adjunk árnyékot alakzatnak
  az Aspose.Words segítségével. Tanulja meg beállítani az árnyék színét, beszúrni
  egy téglalap alakzatot, és testre szabni a külső árnyékot.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create document
- add shadow to shape
- set shadow color
- insert rectangle shape
- how to add shadow
language: hu
lastmod: 2026-10-04
og_description: Hogyan hozzunk létre dokumentumot Pythonban, és adjunk árnyékot egy
  alakzathoz. Ez az útmutató megmutatja, hogyan állítsuk be az árnyék színét, szúrjunk
  be téglalap alakzatot, és alkalmazzunk külső árnyékot az Aspose.Words segítségével.
og_image_alt: Python code inserting a rectangle shape with a visible shadow into a
  Word document
og_title: Hogyan készítsünk dokumentumot egy téglalap alakzattal és árnyékkal Pythonban
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  headline: How to create document with a rectangle shape and shadow in Python
  type: TechArticle
- description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  name: How to create document with a rectangle shape and shadow in Python
  steps:
  - name: Why does the shadow sometimes appear invisible?
    text: The shadow is only rendered if `shadow.visible` is set to `True` **and**
      the shape’s `wrap_type` allows it to be displayed. An inline shape works reliably;
      floating shapes may require additional layout adjustments.
  - name: How can I change the shadow color to match a brand palette?
    text: 'Replace `aw.drawing.Color.black` with a custom RGB value:'
  - name: What if I need the shape to appear behind text?
    text: Set the wrap type to `WrapType.BEHIND` and adjust the `z_order_position`
      if necessary. Keep in mind that some viewers may render behind‑text shapes differently.
  - name: Can I apply the same shadow settings to multiple shapes?
    text: Yes. Create a helper function that configures the shadow and call it for
      each shape you insert. This promotes code reuse and ensures consistent styling.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Hogyan készítsünk dokumentumot egy téglalap alakzattal és árnyékkal Pythonban
url: /hu/python/images-shapes/how-to-create-document-with-a-rectangle-shape-and-shadow-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozzunk létre dokumentumot téglalap alakzattal és árnyékkal Pythonban

Ha **hogyan hozzunk létre dokumentumot**-ra van szükséged, amely egy stílusos téglalapot tartalmaz, ez az útmutató teljes megoldást nyújt. Meg fogod látni, hogyan **árnyék hozzáadása alakzathoz**, állíthatod be az árnyék színét, és szabályozhatod annak eltolását és elmosódását – mindezt az Aspose.Words for Python segítségével. A tutorial végére képes leszel egy `.docx` fájlt generálni, amely kifinomult és készen áll a terjesztésre.

Az alábbi lépések mindent lefednek a könyvtár telepítésétől az árnyék megjelenésének testreszabásáig. Nem szükséges külső dokumentáció; a kód készen áll a másolásra, futtatásra és saját projektjeidhez való adaptálásra. Emellett megtanulod, hogyan **téglalap alakzat beszúrása**, **külső árnyék stílus kiválasztása**, és hogyan kezeld a gyakori buktatókat, mint a láthatatlan árnyékok vagy a helytelen körbefuttatás beállítások.

## Előfeltételek

* Python 3.8 vagy újabb telepítve.  
* Aktív Aspose.Words for Python licenc (vagy ingyenes értékelő kulcs).  
* Alapvető ismeretek a Python szkriptekhez.  
* Hozzáférés egy fájlrendszer helyhez, ahol a generált dokumentum mentésre kerül.

A SDK-t pip‑pel telepítheted:

```bash
pip install aspose-words
```

## 1. lépés: A könyvtár importálása és egy új üres dokumentum létrehozása

Egy új dokumentum létrehozása az első művelet minden Word‑automatizálási szcenárióban. Az `aw.Document()` konstruktor egy üres fájlt ad, amelyet szöveggel, képekkel vagy alakzatokkal tölthetsz fel.

```python
import aspose.words as aw

# Create a new blank document
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

A `DocumentBuilder` objektum egyszerűsíti a tartalom beszúrását. Nyomon követi az aktuális kurzorpozíciót, így elemeket sorban adhatsz hozzá anélkül, hogy manuálisan kezelnéd a szakaszokat.

## 2. lépés: A kívánt méretű téglalap alakzat beszúrása

A téglalap alakzat vizuális elemek tárolójaként működik. Meghatározhatod a szélességét és magasságát pontban (1 pt ≈ 1/72 in).

```python
# Insert a rectangle shape that is 150 pt wide and 80 pt tall
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

Ezen a ponton az alakzatnak nincs vizuális stílusa, ezért egyszerű körvonalként jelenik meg. A következő lépések mélységet és színt adnak neki.

## 3. lépés: Az alakzat beállítása, hogy inline módon folyjon a környező szöveggel

Amikor egy alakzat **inline**, úgy viselkedik, mint egy karakter egy bekezdésben. Ez biztosítja, hogy a téglalap ott maradjon, ahol a dokumentum elrendezésében elvárnád.

```python
# Make the shape inline so it follows the text flow
rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE
```

Ha inkább azt szeretnéd, hogy az alakzat a szöveg felett lebegjen, használhatod a `WrapType.SQUARE` vagy `WrapType.TOP_BOTTOM` beállítást, de a legtöbb jelentésnél egy inline alakzat előre jelezhető elrendezést biztosít.

## 4. lépés: Az árnyék láthatóvá tétele és a szín kiválasztása

Az árnyék, ha nem látható, nem nyújt vizuális előnyt. A `visible` jelző aktiválja a hatást, a `color` tulajdonság pedig meghatározza a színét. A fekete használata klasszikus, finom mélységet ad.

```python
# Enable the shadow and set its color to black
rectangle_shape.shadow.visible = True
rectangle_shape.shadow.color = aw.drawing.Color.black
```

A `aw.drawing.Color.black` helyett bármely más színt használhatsz, például `aw.drawing.Color.gray` vagy egy egyedi RGB értéket (`aw.drawing.Color.from_argb(255, 128, 128, 128)`).

## 5. lépés: Az árnyék eltolásának és elmosódásának meghatározása a mélység érdekében

Az eltolás szabályozza, milyen messze kerül az árnyék az alakzattól, míg a elmosódási sugár lágyítja a széleket. Kis értékek éles árnyékot eredményeznek; nagyobb értékek lágyabb megjelenést adnak.

```python
# Horizontal and vertical offset of 5 pt each
rectangle_shape.shadow.offset_x = 5
rectangle_shape.shadow.offset_y = 5

# Blur radius of 3 pt for a gentle feather
rectangle_shape.shadow.blur = 3
```

Kísérletezz ezekkel a számokkal, hogy megfeleljenek a tervezési irányelveidnek. Egy erőteljes drop‑shadow esetén növelheted mind az eltolást, mind az elmosódást.

## 6. lépés: Külső árnyék stílus kiválasztása

Az Aspose.Words több árnyékstílust kínál, például `INNER`, `OUTER` és `PERSPECTIVE`. A **outer** stílus az árnyékot az alakzat szegélye kívül helyezi el, ami ideális egy tiszta, professzionális megjelenéshez.

```python
# Apply an outer shadow style
rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

Ha drámaibb hatást szeretnél, próbáld ki a `ShadowStyle.PERSPECTIVE`‑t – háromdimenziós dőlést ad hozzá.

## 7. lépés: A dokumentum mentése az árnyékolt alakzattal

A mentés befejezi a fájlt és leírja az összes formázást a lemezre. Válassz egy olyan könyvtárat, amelybe írási jogosultsággal rendelkezel, és adj a fájlnak egy leíró nevet.

```python
# Save the document to the desired location
output_path = "output/ShapeWithShadow.docx"
document.save(output_path)
print(f"Document saved to {output_path}")
```

A szkript futtatása egy Word‑fájlt hoz létre, amely egy téglalapot tartalmaz látható, színezett árnyékkal. Nyisd meg a fájlt a Microsoft Word‑ben vagy a LibreOffice‑ban, hogy ellenőrizd az eredményt.

## Teljes futtatható példa

Az alábbiakban a teljes szkript látható, amely magában foglalja a megbeszélt összes lépést. Másold a kódot egy `create_shadowed_shape.py` nevű fájlba, és futtasd a `python create_shadowed_shape.py` paranccsal.

```python
import aspose.words as aw
import os

def main():
    # Ensure the output directory exists
    output_dir = "output"
    os.makedirs(output_dir, exist_ok=True)

    # Step 1: Create a new blank document
    document = aw.Document()
    builder = aw.DocumentBuilder(document)

    # Step 2: Insert a rectangle shape of the desired size
    rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

    # Step 3: Set the shape to be inline with the text flow
    rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE

    # Step 4: Make the shadow visible and choose its color
    rectangle_shape.shadow.visible = True
    rectangle_shape.shadow.color = aw.drawing.Color.black

    # Step 5: Define the shadow's offset and blur to give it depth
    rectangle_shape.shadow.offset_x = 5   # horizontal offset in points
    rectangle_shape.shadow.offset_y = 5   # vertical offset in points
    rectangle_shape.shadow.blur = 3       # blur radius in points

    # Step 6: Choose an outer shadow style
    rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER

    # Step 7: Save the document with the shaped shadow
    output_path = os.path.join(output_dir, "ShapeWithShadow.docx")
    document.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    main()
```

**Várható kimenet**

Amikor megnyitod a `ShapeWithShadow.docx` fájlt, egyetlen téglalapot látsz, amely a lap közepén helyezkedik el. A téglalapot egy finom fekete árnyék kíséri, amely a jobb‑alsó irányba van eltolva, enyhén elmosódva a mélység érdekében. Az árnyék az outer stílust követi, ezért nem érinti a téglalap belsejét.

## Gyakori kérdések és szélhelyzetek

### Miért tűnik néha az árnyék láthatatlannak?

Az árnyék csak akkor jelenik meg, ha a `shadow.visible` értéke `True` **és** az alakzat `wrap_type` beállítása lehetővé teszi a megjelenítését. Egy inline alakzat megbízhatóan működik; a lebegő alakzatok további elrendezési módosításokat igényelhetnek.

### Hogyan változtathatom meg az árnyék színét, hogy illeszkedjen egy márka palettához?

Cseréld le a `aw.drawing.Color.black` értéket egy egyedi RGB értékre:

```python
rectangle_shape.shadow.color = aw.drawing.Color.from_argb(255, 0, 120, 215)  # corporate blue
```

### Mi van, ha a alakzatot a szöveg mögött kell megjeleníteni?

Állítsd be a wrap típust `WrapType.BEHIND`‑ra, és szükség esetén módosítsd a `z_order_position`‑t. Ne feledd, hogy egyes megjelenítők másként renderelhetik a szöveg mögötti alakzatokat.

### Alkalmazhatom ugyanazokat az árnyék beállításokat több alakzatra is?

Igen. Hozz létre egy segédfunkciót, amely beállítja az árnyékot, és hívd meg minden egyes beszúrt alakzatra. Ez elősegíti a kód újrahasználatát és a konzisztens stílus biztosítását.

```python
def apply_shadow(shape, color=aw.drawing.Color.black, offset=5, blur=3):
    shape.shadow.visible = True
    shape.shadow.color = color
    shape.shadow.offset_x = offset
    shape.shadow.offset_y = offset
    shape.shadow.blur = blur
    shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

## Következtetés

Most már tudod, **hogyan hozzunk létre dokumentumot**, amely téglalap alakzatot tartalmaz testreszabott árnyékkal az Aspose.Words for Python használatával. A tutorial bemutatta a téglalap beszúrását, az alakzat inline beállítását, az árnyék engedélyezését, a szín, eltolás, elmosódás és stílus beállítását, valamint a fájl mentését.

Innen tovább felfedezheted a kapcsolódó témákat, például **árnyék hozzáadása alakzathoz** más alakzattípusoknál, **árnyék szín beállítása** dinamikusan adatok alapján, vagy **hogyan adjunk árnyékot** képekhez és szövegdobozokhoz. Kísérletezz különböző méretekkel, színekkel és árnyékstílusokkal, hogy megfeleljenek a márka irányelveidnek vagy a tervezési rendszerednek.

Készen állsz több Word‑dokumentum automatizálására? Próbálj meg táblázatokat, fejléceket vagy dinamikus tartalmat hozzáadni – minden lépés az itt bemutatott elvekre épül. Boldog kódolást!

## Mit érdemes legközelebb megtanulni?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódpéldákat lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API‑funkciókat és alternatív megvalósítási megközelítéseket saját projektjeidben.

- [Téglalap alakzat létrehozása, árnyék hozzáadása és PDF mentése](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Üres Word dokumentum létrehozása árnyékolt téglalap alakzattal – Lépésről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Hogyan kezeljünk dokumentumváltozókat az Aspose.Words segítségével Pythonban: Teljes útmutató](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}