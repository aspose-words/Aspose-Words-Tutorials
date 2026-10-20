---
category: general
date: 2026-06-21
description: Hozzon létre téglalap alakzatot Pythonban az Aspose.Words segítségével.
  Tanulja meg, hogyan adjon árnyékot az alakzathoz, állítsa be az alakzat kitöltőszínét,
  és mentse a dokumentumot PDF‑ként percek alatt.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- set shape fill color
language: hu
og_description: Hozzon létre téglalap alakzatot Pythonban az Aspose.Words segítségével.
  Ez az útmutató bemutatja, hogyan adjon árnyékot az alakzathoz, állítsa be az alakzat
  kitöltőszínét, és mentse a dokumentumot PDF formátumban.
og_title: Téglalap alakzat létrehozása Pythonban – Aspose.Words útmutató
schemas:
- author: Aspose
  dateModified: '2026-06-21'
  description: Create rectangle shape in Python using Aspose.Words. Learn how to add
    shadow to shape, set shape fill color, and save document as PDF in minutes.
  headline: Create rectangle shape in Python – Aspose.Words tutorial
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF generation
title: Téglalap alakzat létrehozása Pythonban – Aspose.Words útmutató
url: /hu/python/images-shapes/create-rectangle-shape-in-python-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rectangle alakzat létrehozása Pythonban – Aspose.Words oktatóanyag

Gondolkodtál már **hogyan lehet rectangle alakzatot** létrehozni egy Word dokumentumban Python kóddal? Nem vagy egyedül. Sok fejlesztő akad el, amikor gyors vizuális elemet – például egy színes dobozt enyhe árnyékkal – kell hozzáadni, majd az egészet PDF‑ként exportálni.  

Ebben az útmutatóban egy teljes, futtatható példán keresztül mutatjuk be, hogyan **hozzunk létre rectangle alakzatot**, **állítsuk be a kitöltő színt**, **adjunk árnyékot az alakzathoz**, és végül **mentsük a dokumentumot PDF‑ként**. Nincs homályos hivatkozás, csak konkrét kód, amit ma másolhatsz‑beilleszthetsz és futtathatsz.

## Amire szükséged lesz

Mielőtt belevágnánk, győződj meg róla, hogy a következők telepítve vannak a gépeden:

- Python 3.8 vagy újabb (a használt szintaxis bármely friss verzión működik).
- Aktív Aspose.Words for Python licenc vagy ingyenes próba (a könyvtár tisztán Python, nincs COM interop szükség).
- Szövegszerkesztő vagy IDE, amivel kényelmesen dolgozol – a VS Code remek, de bármelyik megfelel.

Ennyi. Nincs nehéz keretrendszer, nincs extra operációs rendszer‑szintű függőség. Kezdjünk is bele.

## 1. lépés: Aspose.Words for Python telepítése

Először is. Ha még nem tetted, húzd le a csomagot a PyPI‑ról:

```bash
pip install aspose-words
```

Miért fontos ez a lépés: az Aspose.Words biztosítja a `Document` és `DocumentBuilder` osztályokat, amikre támaszkodni fogunk. A könyvtár nélkül a későbbi hívások – például az `insert_shape` – nem léteznek, így a szkript már a vonal megrajzolása előtt összeomlik.

> **Pro tipp:** Tartsd tisztán a virtuális környezetet. Futtasd a `python -m venv .venv && source .venv/bin/activate` parancsot a telepítés előtt, hogy a könyvtár elkülönüljön a rendszer‑csomagoktól.

## 2. lépés: Új dokumentum és DocumentBuilder létrehozása

Most ténylegesen **létrehozzuk a rectangle alakzatot** – de előbb szükségünk van egy üres vászonra.

```python
import aspose.words as aw

# Initialize a new, empty Word document
doc = aw.Document()
# DocumentBuilder lets us add content programmatically
builder = aw.DocumentBuilder(doc)
```

A `Document` objektum a teljes fájlt képviseli, míg a `DocumentBuilder` egy kényelmes segédeszköz, amely tudja, hol van a kurzor, és képes elemeket beilleszteni abban a pontban. Gondolj a builderre úgy, mint egy tollra, ami a lapra ír.

## 3. lépés: A rectangle alakzat beillesztése

Itt történik a fő akció. **Létrehozzuk a rectangle alakzatot** rögzített szélességgel és magassággal, majd elhelyezzük az oldalon.

```python
# Insert a rectangle 200 points wide and 100 points tall
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

Miért rectangle? Ez a legegyszerűbb alakzat, amely mégis lehetővé teszi a kitöltő színek és árnyékok bemutatását. Ha később kör vagy csillag kell, cseréld ki a `ShapeType.RECTANGLE`‑t egy másik enum értékre.

## 4. lépés: Alakzat kitöltő színének beállítása

Egy egyszerű fehér doboz nem túl izgalmas, ezért **állítsuk be az alakzat kitöltő színét** valami enyhe színre – a világoskék jól működik jelentésekhez.

```python
# Apply a light‑blue background to the rectangle
rectangle.fill_color = aw.Color.light_blue
```

Használhatsz bármely előre definiált `aw.Color` tagot (`red`, `green`, `dark_gray` stb.) vagy megadhatsz egy RGB tuple‑t (`aw.Color.from_argb(255, 30, 144, 255)`). A kitöltő szín az, amit a felhasználó lát, mielőtt az árnyék vagy a keret alkalmazásra kerülne.

## 5. lépés: Árnyék hozzáadása az alakzathoz

Most jön a vizuális csiszolás: **adjunk árnyékot az alakzathoz**. Az árnyékok mélységet adnak, és kiemelik a rectangle‑t az oldalon.

```python
# Grab the shadow format object
shadow = rectangle.shadow_format

# Turn the shadow on
shadow.visible = True
# Choose a dark gray tone for realism
shadow.color = aw.Color.dark_gray
# Blur radius controls softness (5 points is a nice middle ground)
shadow.blur = 5
# Horizontal and vertical offsets shift the shadow relative to the shape
shadow.offset_x = 3
shadow.offset_y = 3
# Slight transparency makes the shadow feel natural
shadow.transparency = 0.2
# Use an outer shadow – you could also try INSET for a different effect
shadow.type = aw.drawing.ShadowType.OUTER
```

**Hogyan adunk hozzá árnyékot**? A fenti kód pontosan ezt teszi, de bontsuk le, miért fontos minden tulajdonság:

- `visible` – be‑ vagy kikapcsolja a hatást.
- `color` – meghatározza a színárnyalatot; egy sötétszürke természetes megvilágítást imitál.
- `blur` – magasabb értékek lágyabb szélű árnyékot eredményeznek.
- `offset_x` / `offset_y` – eltolják az árnyékot az alakzattól; ezekkel szimulálhatod a különböző fényirányokat.
- `transparency` – 0 = átlátszatlan, 1 = láthatatlan; 0.2 finom benyomást kelt.
- `type` – `OUTER` az árnyékot az alakzat külső oldalára vetíti, míg `INNER` belülre helyezné.

Ha drámai drop‑shadowra van szükséged, növeld a `blur` értékét 10‑15‑re, és állítsd az `offset_x`/`offset_y`‑t 6‑8‑ra.

## 6. lépés: Dokumentum mentése PDF‑ként

Minden erőfeszítés értelmetlen, ha nem tudjuk **menteni a dokumentumot PDF‑ként**, és megosztani. Az Aspose.Words ezt egyetlen sorra redukálja:

```python
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Miért PDF? A PDF megőrzi a layoutot platformok között, így ideális jelentésekhez, számlákhoz vagy bármilyen nyomtatható anyaghoz. A `save` metódus automatikusan felismeri a fájlkiterjesztést, és a megfelelő formátumot választja – csak ügyelj arra, hogy az útvonal `.pdf`‑re végződjön.

### Várt eredmény

Nyisd meg a létrehozott `ShapeWithShadow.pdf` fájlt, és egy világoskék rectangle‑t kell látnod, amely a első oldal teteje közelében középre helyezkedik, enyhe sötétszürke árnyékkal, amely kissé jobbra és lejjebb van eltolva. Az alakzat élei élesek, az árnyék finom, a fájlméret általában 100 KB alatt van.

## Bónusz: Árnyék finomhangolása – Válaszok a „hogyan adjunk árnyékot” kérdésre

Lehet, hogy azon tűnődsz, *„Meg tudom változtatni az árnyék irányát anélkül, hogy az alakzatot mozgatnám?”* Természetesen. Az árnyék pozíciója független az alakzat koordinátáitól; csak állítsd be az `offset_x` és `offset_y` értékeket. Pozitív értékek jobbra/lefelfelé mozgatják az árnyékot, negatívak balra/felfelé. Egy bal‑felső fényforrás esetén használd az `offset_x = -3` és `offset_y = -3` értékeket.

Egy másik gyakori kérdés: *„Mi van, ha több árnyékot szeretnék ugyanazon az alakzaton?”* Az Aspose.Words csak egy árnyékot támogat alakzatonként. Ha rétegezett hatást akarsz, hozz létre egy másolatot az alakzatról, helyezd el kicsit eltolva, és minden példányra alkalmazz különböző árnyékot. Ez egy kis trükk, de működik.

## Teljes szkript – Kész a futtatásra

Az alábbiakban a komplett, önálló szkript található. Másold be egy `create_rectangle_with_shadow.py` nevű fájlba, és futtasd a `python create_rectangle_with_shadow.py` paranccsal.

```python
import aspose.words as aw

# ---------- Initialize document ----------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ---------- Insert rectangle ----------
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# ---------- Set fill color ----------
rectangle.fill_color = aw.Color.light_blue

# ---------- Configure shadow ----------
shadow = rectangle.shadow_format
shadow.visible = True
shadow.color = aw.Color.dark_gray
shadow.blur = 5
shadow.offset_x = 3
shadow.offset_y = 3
shadow.transparency = 0.2
shadow.type = aw.drawing.ShadowType.OUTER

# ---------- Save as PDF ----------
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

> **Megjegyzés:** Cseréld le a `YOUR_DIRECTORY`‑t egy olyan abszolút vagy relatív útvonalra, amely létezik a gépeden. Ha a mappa nem létezik, a Python `FileNotFoundError`‑t dob.

## Gyakori hibák és elkerülésük

| Probléma | Miért fordul elő | Megoldás |
|----------|------------------|----------|
| Az árnyék nem jelenik meg | `shadow.visible` alapértelmezett értéke `False` | Állítsd be `shadow.visible = True` |
| Az alakzat láthatatlan | Kitöltő szín `aw.Color.transparent` vagy `None` | Használj szilárd színt, pl. `aw.Color.light_blue` |
| A PDF üres | Elfelejtetted meghívni a `doc.save`‑t, vagy rossz kiterjesztéssel mentettél | Hívd meg `doc.save("output.pdf")` és ellenőrizd az útvonalat |
| Futásidejű `ImportError` | Az Aspose.Words nincs telepítve vagy rossz Python környezet | Futtasd a `pip install aspose-words` parancsot az aktív venv‑ben |

## Következő lépések – További alakzatok és formázás

Miután elsajátítottad a **rectangle alakzat létrehozását**, megteheted, hogy:

- A `ShapeType.RECTANGLE`‑t `ShapeType.ELLIPSE` vagy `ShapeType.PENTAGON`‑ra cseréled, hogy más geometriákat próbálj ki.
- Szöveget helyezel az alakzatba a `builder.move_to(rectangle.absolute_position)` és azt követően a `builder.writeln("Hello World")` használatával.
- Több alakzatot csoportosítasz a `group = aw.drawing.GroupShape(doc)` segítségével összetett diagramokhoz.
- Más formátumokba exportálsz, például DOCX‑be (`doc.save("output.docx")`) vagy HTML‑be (`doc.save("output.html")`), hogy lásd, hogyan viselkedik az árnyék.

Ezek a kiterjesztések mind ugyanazon alapelveken nyugszanak: **árnyék hozzáadása az alakzathoz**, **alakzat kitöltő színének beállítása**, és **dokumentum mentése PDF‑ként** (vagy más formátumban).

---

### Kép előnézet *(opcionális)*

![Rectangle alakzat árnyékkal Pythonban](https://example.com/rectangle-shadow.png "Rectangle alakzat árnyékkal Pythonban")

*A képernyőképen a végső PDF kimenet látható, egy világoskék rectangle‑tal és egy finom külső árnyékkal.*

---

## Összegzés

Végigjártuk a **rectangle alakzat létrehozásának** minden lépését Pythonban, egyedi kitöltés alkalmazását, **árnyék hozzáadását az alakzathoz**, és végül a **dokumentum PDF‑ként való mentését**. A kód teljesen futtatható, a magyarázatok lefedik az egyes tulajdonságok mögötti „miért” kérdést, és kitértünk a gyakori edge‑case‑kre és a következő lépésekre is.

---

## Mit tanulj meg legközelebb?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás komplett, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy további API‑funkciókat saját projektjeidben is elsajátíthasd.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}