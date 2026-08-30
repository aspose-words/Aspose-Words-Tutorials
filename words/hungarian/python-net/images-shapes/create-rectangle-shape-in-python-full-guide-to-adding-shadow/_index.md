---
category: general
date: 2026-05-04
description: Tanulja meg, hogyan hozhat létre téglalap alakzatot, hogyan adhat hozzá
  árnyékos alakzatot, hogyan változtathatja meg az árnyék színét, hogyan állíthatja
  be az árnyék távolságát, és hogyan mentheti a dokumentumot PDF formátumban az Aspose.Words
  for Python használatával.
draft: false
keywords:
- create rectangle shape
- how to add shape
- change shadow color
- save document as pdf
- set shadow distance
language: hu
og_description: Hozzon létre téglalap alakzatot az Aspose.Words for Python segítségével,
  tanulja meg, hogyan adjon hozzá alakzatot, változtassa meg az árnyék színét, állítsa
  be az árnyék távolságát, és mentse a dokumentumot PDF formátumban.
og_title: Készítsen téglalap alakzatot – Adjon árnyékot, változtassa a színt és mentse
  PDF‑ként
tags:
- Aspose.Words
- Python
- PDF generation
title: Téglalap alakzat létrehozása Pythonban – Teljes útmutató az árnyékok hozzáadásához
  és PDF-be mentéshez
url: /hu/python/images-shapes/create-rectangle-shape-in-python-full-guide-to-adding-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Téglalap alak létrehozása – Teljes útmutató Python fejlesztőknek

Volt már szükséged **téglalap alak létrehozására** egy Word dokumentumban, és azon tűnődtél, hogyan adhatnál neki kifinomult árnyékot? Lehet, hogy jelentésgenerátort építesz, és a vizuális megjelenés fontos – különösen, ha a végső kimenet PDF. A jó hír? Az Aspose.Words for Python segítségével nem csak **hogyan adjunk hozzá alakzatot**, hanem minden árnyék tulajdonságot is finomhangolhatsz, a színtől a távolságig, majd **mentheted a dokumentumot PDF‑ként** egy folyamatban.

Ebben az útmutatóban lépésről‑lépésre végigvezetünk a teljes folyamaton. Megmutatjuk a pontos kódot, amit egyszerűen másolhatsz‑beilleszthetsz, megértjük, *miért* fontos minden sor, és néhány tippet is adunk a szél‑esetek kezeléséhez (például átlátszó árnyékok vagy nem szabványos DPI). A végére képes leszel **téglalap alak létrehozására**, testreszabni az árnyékát, és egy tiszta PDF‑et exportálni gond nélkül.

## Előfeltételek

- Python 3.8+ telepítve van a gépeden.  
- Aspose.Words for Python a `pip install aspose-words` paranccsal.  
- Alapvető ismeretek az objektum‑orientált Pythonról (semmi bonyolult).  

Ha már van virtuális környezeted, csak futtasd a telepítési parancsot, és már indulhat is.

## 1. lépés: A Dokumentum és a Builder inicializálása

Mielőtt **hogyan adjunk hozzá alakzatot** tudnád, szükséged van egy üres dokumentumra. A `Document` osztály képviseli az egész fájlt, a `DocumentBuilder` pedig a festőecseted.

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder to edit it
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

*Miért fontos:* A `Document` tartalmazza az összes szekciót, oldalt és erőforrást. A `DocumentBuilder` egy folyékony API‑t biztosít a tartalom beillesztéséhez pontosan ott, ahol szükséges – gondolj rá úgy, mint egy kurzorra egy szövegszerkesztőben.

## 2. lépés: A Téglalap alakzat beszúrása

Most már ténylegesen **hogyan adjunk hozzá alakzatot**. Az `insert_shape` metódusnak szüksége van az alakzat típusára és méreteire (pontban). Itt egy 200 × 100 pt méretű téglalapot választunk, és világoskék kitöltést adunk neki.

```python
# Step 2: Insert a rectangle shape and give it a light‑blue fill
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,  # shape type
    200,                            # width in points
    100)                            # height in points
rectangle_shape.fill_color = aw.Color.light_blue
```

*Pro tipp:* Ha az alakzatot a meglévő szöveghez szeretnéd igazítani, használd a `builder.move_to`‑t a beszúrás előtt, vagy állítsd be a `left`/`top` tulajdonságokat a létrehozás után.

## 3. lépés: Az árnyék bekapcsolása

Az árnyék nélküli alakzat laposnak tűnik. A **árnyék távolság beállításához** és a hatás láthatóvá tételéhez szerezd meg az árnyék formátumot, és engedélyezd azt.

```python
# Step 3: Access the shape's shadow format and make the shadow visible
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
```

*Miért ez a lépés:* Az árnyék formátum egy külön objektum; a `visible` kapcsolása az első dolog, amit meg kell tenned, különben a többi árnyék tulajdonság figyelmen kívül marad.

## 4. lépés: Az árnyék stílusának beállítása – Szín, Elmosás, Távolság, Irány

Itt történik a varázslat. **Megváltoztatjuk az árnyék színét**, beállítjuk az elmosás sugarát, meghatározzuk, milyen messze helyezkedik el az árnyék a téglalaptól, és 45°‑ra forgatjuk.

```python
# Step 4: Configure the appearance of the shadow
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER   # outer shadow
rectangle_shadow.blur_radius = 10.0                    # blur amount (pixels)
rectangle_shadow.distance = 5.0                        # distance from the shape
rectangle_shadow.direction = 45.0                     # angle in degrees
rectangle_shadow.color = aw.Color.gray                 # shadow colour
```

*Az egyes tulajdonságok magyarázata:*

| Tulajdonság | Mit csinál | Tipikus értékek |
|-------------|------------|-----------------|
| `style` | Meghatározza, hogy az árnyék *belső* vagy *külső* legyen. | `OUTER` (leggyakoribb) |
| `blur_radius` | A lágyaságot szabályozza; magasabb = homályosabb szélek. | 0–20 px szokásos |
| `distance` | Milyen messze van az árnyék az alakzattól. | 0–10 pt finom, >10 drámai |
| `direction` | A fényforrás szöge, óramutató járásával megegyező irányban az x‑tengelytől mérve. | 0‑360° |
| `color` | Az árnyék színe. | Bármely `aw.Color` (pl. `gray`, `dark_red`) |

*Szél eset:* Ha a `distance` értéke `0`, az árnyék közvetlenül az alakzat alatt helyezkedik el, így gyakorlatilag elrejti a kitöltést. Tartsd `0`‑nál nagyobbnak a látható eltoláshoz.

## 5. lépés: A dokumentum mentése PDF‑ként

Végül **mentjük a dokumentumot PDF‑ként**. Az Aspose.Words automatikusan rasterizálja az árnyékot, így a PDF pontosan úgy néz ki, mint a Word nézet.

```python
# Step 5: Save the document as a PDF with the shadowed shape
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

*Miért PDF?* A PDF‑ek megőrzik az elrendezést különböző platformokon, így tökéletesek jelentésekhez, számlákhoz vagy bármilyen nyomtatható anyaghoz.

---

![Create rectangle shape with shadow](https://example.com/images/rectangle-shadow.png){: .align-center alt="téglalap alak létrehozása árnyékkal példa"}

*A fenti kép a végső PDF kimenetet mutatja – egy világoskék téglalap lágy szürke külső árnyékkal, pontosan úgy, ahogy beállítottuk.*

## Gyakori kérdések és változatok

### Mi van, ha **átlátszó** árnyékra van szükségem?

Állítsd be az alfa csatornát az árnyék színén:

```python
transparent_gray = aw.Color.from_argb(128, 0, 0, 0)  # 50% opacity black
rectangle_shadow.color = transparent_gray
```

### Alkalmazhatom ugyanazt az árnyékot több alakzatra?

Igen. Vedd ki a `ShadowFormat`‑ot egy alakzatból, és rendeld hozzá egy másikhoz:

```python
another_shape = builder.insert_shape(aw.drawing.ShapeType.ELLIPSE, 150, 150)
another_shape.shadow_format = rectangle_shadow.clone()
```

### Hogyan változtathatom meg az árnyékot egy **másik alakzat típus** esetén?

Minden alakzat típus ugyanazokat a `ShadowFormat` tulajdonságokat használja, így újra felhasználhatod ugyanazt a konfigurációs blokkot – csak cseréld le a `ShapeType.RECTANGLE`‑t `ShapeType.OVAL`, `ShapeType.TRIANGLE` stb.-re.

### És a **magas felbontású PDF** nyomtatáshoz?

Add meg a `PdfSaveOptions`‑t magasabb DPI‑vel:

```python
options = aw.saving.PdfSaveOptions()
options.image_resolution = 300  # 300 DPI for print quality
document.save(output_path, options)
```

## Összefoglalás

Átbeszéltük mindent, ami szükséges a **téglalap alak létrehozásához**, **hogyan adjunk hozzá alakzatot**, az **árnyék színének** testreszabásához, a **árnyék távolság beállításához**, és végül a **dokumentum PDF‑ként mentéséhez**. A teljes, futtatható szkript a következő:

```python
import aspose.words as aw

# Initialise document
document = aw.Document()
builder = aw.DocumentBuilder(document)

# Insert rectangle shape
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle_shape.fill_color = aw.Color.light_blue

# Enable and style shadow
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER
rectangle_shadow.blur_radius = 10.0
rectangle_shadow.distance = 5.0
rectangle_shadow.direction = 45.0
rectangle_shadow.color = aw.Color.gray

# Save as PDF
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Futtasd a szkriptet, nyisd meg a keletkezett `ShadowedShape.pdf`‑t, és egy tiszta téglalapot látsz majd egy finom szürke árnyékkal – pontosan azt, amit egy professzionálisan formázott jelentéstől várnál.

## Mi a következő lépés?

- **Fedezd fel a többi alakzat típust** (`ShapeType.OVAL`, `ShapeType.LINE`) a dokumentumaid gazdagításához.  
- **Kombinálj több árnyékot** alakzatok rétegezésével; akár „fénylő” hatást is létrehozhatsz egy belső árnyék és élénk szín használatával.  
- **Automatizáld a kötegelt feldolgozást**: iterálj egy adat sorok gyűjteményén, generálj egy alakzatot soronként, és egyesíts mindent egyetlen PDF‑be.  
- **Integráld más Aspose könyvtárakkal** (pl. Aspose.Slides), ha ugyanazt a vizuális elemet PowerPointba szeretnéd exportálni.

Nyugodtan kísérletezz – változtasd meg a `blur_radius`‑t, játszd a `direction`‑t, vagy cseréld le a `gray`‑t egy márkaspecifikus színre. Az API elég rugalmas, hogy néhány finomhangolás drámaian megváltoztassa a vizuális hatást.

Van kérdésed vagy bonyolult helyzeted? Hagyj egy megjegyzést alább, vagy jelezd az Aspose közösségi fórumain. Boldog kódolást, és élvezd a gyönyörűen árnyékolt téglalapokat!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}