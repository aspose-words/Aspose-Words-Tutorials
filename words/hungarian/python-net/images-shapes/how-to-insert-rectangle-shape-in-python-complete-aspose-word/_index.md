---
category: general
date: 2026-06-27
description: Tanulja meg, hogyan szúrjon be téglalap alakzatot Pythonban az Aspose.Words
  használatával, hogyan változtassa meg az árnyék színét, hogyan adjon hozzá külső
  árnyékot, és hogyan alkalmazzon árnyékhatást az alakzatra – mindezt egyetlen oktatóanyagon
  keresztül.
draft: false
keywords:
- how to insert rectangle shape
- how to change shadow color
- how to add outer shadow
- apply shadow effect to shape
language: hu
og_description: Tanulja meg, hogyan szúrjon be téglalap alakzatot Pythonban, módosítsa
  az árnyék színét, adjon hozzá külső árnyékot, és alkalmazzon árnyékhatást az alakzatra
  az Aspose.Words segítségével.
og_title: Hogyan szúrjunk be téglalap alakzatot Pythonban – Aspose.Words útmutató
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  headline: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  name: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: Pro tip
    text: If you need the rectangle positioned at a specific location, use `builder.move_to`
      before inserting, or adjust `rectangle.left` and `rectangle.top` after creation.
  - name: Edge case
    text: If you forget to set `shadow.opacity`, the default is fully opaque, which
      can make the shadow look like a solid shape. Always pair a color change with
      an appropriate opacity level.
  - name: Common pitfalls
    text: '- **Missing directory:** `doc.save` will raise an error if the folder doesn’t
      exist. Create it first or use `os.makedirs`. - **Version mismatch:** The shadow
      API requires Aspose.Words 22.9+; older versions silently ignore shadow settings.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
title: Hogyan illesszünk be téglalap alakzatot Pythonban – Teljes Aspose.Words útmutató
url: /hu/python/images-shapes/how-to-insert-rectangle-shape-in-python-complete-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan illesszünk be téglalap alakzatot Pythonban – Teljes Aspose.Words útmutató

Gondolkodtál már azon, **hogyan illesszünk be téglalap alakzatot** egy Word dokumentumba Python segítségével? Nem vagy egyedül – sok fejlesztő ütközik ebbe a problémába jelentések automatizálásakor vagy sablonok létrehozásakor. A jó hír, hogy az Aspose.Words ezt gyerekjátékká teszi, és ebben az útmutatóban végigvezetünk a teljes folyamaton, a téglalap megrajzolásától a külső árnyék hozzáadásáig.

Kitérünk arra is, **hogyan változtassuk meg az árnyék színét**, **hogyan adjunk hozzá külső árnyékot**, és a végső lépésre, **hogyan alkalmazzuk az árnyékhatást az alakzatra**. A végére egy teljesen stílusos téglalapot kapsz, amelyet programozottan beilleszthetsz bármely .docx fájlba.

## Előfeltételek

- Python 3.8+ telepítve a gépeden  
- Aspose.Words for Python a `pip install aspose-words` paranccsal  
- Alapvető ismeretek a Python szkriptek írásáról (mély Word‑API tudás nem szükséges)  

Ha már megvannak ezek, nagyszerű – vágjunk bele. Ha nem, először szerezd be a könyvtárat; a további útmutató feltételezi, hogy az import hibátlanul működik.

## Hogyan illesszünk be téglalap alakzatot az Aspose.Words for Python segítségével

Az első lépés pontosan azt ígéri a kulcsszó: **hogyan illesszünk be téglalap alakzatot**. Létrehozunk egy új dokumentumot, példányosítunk egy `DocumentBuilder`‑t, és egy téglalapot helyezünk el az oldalon.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a fresh document and a builder to add content
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Insert a rectangle shape of 200x100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# Optional: give the rectangle a light fill so the shadow is visible
rectangle.fill_color = aw.drawing.Color.light_blue
```

> **Miért fontos:** Az `insert_shape` hívás a *hogyan illesszünk be téglalap alakzatot* központja. Egy `Shape` objektumot ad vissza, amelyet később manipulálhatsz – méret, pozíció, kitöltés, szegélyek, bármit. Figyeljük meg, hogy beállítunk egy `fill_color`‑t; enélkül az árnyék egy fehér oldalon elmosódhat, és nehezen látható lesz.

### Profi tipp
Ha a téglalapot egy konkrét helyre szeretnéd pozícionálni, használd a `builder.move_to`‑t a beillesztés előtt, vagy állítsd be a `rectangle.left` és `rectangle.top` értékeket a létrehozás után.

## Az alakzat árnyékának színének módosítása

Most, hogy a téglalap már a dokumentumban van, válaszoljuk meg a **hogyan változtassuk meg az árnyék színét** kérdést. Az Aspose.Words egy `ShadowEffect` objektumot biztosít, ahol a `color` tulajdonságot bármely RGB értékre állíthatod.

```python
# Create a shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # we’ll also cover outer shadow later
shadow.blur_radius = 8.0                  # smooth edges
shadow.distance = 6.0                     # how far the shadow sits from the shape
shadow.direction = 45                     # angle in degrees
shadow.opacity = 0.6                      # semi‑transparent

# Change the shadow color to a deep gray instead of black
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)

# Apply the shadow to our rectangle
rectangle.shadow = shadow
```

> **Miért lehet erre szükség:** Egy sötét fekete árnyék túl erőteljes lehet, különösen világos színű dokumentumoknál. A szín finomhangolásával illesztheted a vállalati arculathoz, vagy egyszerűen lágyabb vizuális hatást érhetsz el.

### Szélsőséges eset
Ha elfelejted beállítani a `shadow.opacity`‑t, az alapértelmezett teljesen átlátszatlan, ami azt eredményezheti, hogy az árnyék szilárd alakzatként jelenik meg. Mindig párosítsd a színváltoztatást egy megfelelő átlátszósági szinttel.

## Külső árnyék effektus hozzáadása

A következő gyakori kérdés: **hogyan adjunk hozzá külső árnyékot**. A `ShadowStyle.OUTER` jelző azt mondja az Aspose.Words‑nek, hogy az árnyékot az alakzat körvonalán kívül, ne pedig belül jelenítse meg.

A fenti kódrészlet már használja a `ShadowStyle.OUTER`‑t, de a tisztaság kedvéért külön kiemeljük ezt a beállítást:

```python
# Ensure the shadow style is outer
shadow.style = ShadowStyle.OUTER
```

Ha `ShadowStyle.INNER`‑re váltasz, az árnyék a téglalap *belsejében* jelenik meg, ami például domború hatásokhoz hasznos. A legtöbb dokumentum‑tervezési szituációban a külső stílus természetes vetett árnyékot biztosít.

## Árnyék effektus alkalmazása az alakzatra

Már **alkalmaztuk az árnyék effektust az alakzatra** a `rectangle.shadow = shadow` hozzárendeléssel. Most csomagoljuk össze mindent, és mentsük el a dokumentumot, ellenőrizve, hogy a hatás megmarad-e.

```python
# Save the document – choose a folder you have write access to
output_path = "output/RectangleWithShadow.docx"
doc.save(output_path)

print(f"Document saved to {output_path}. Open it to see the rectangle with its outer shadow.")
```

Amikor megnyitod a `RectangleWithShadow.docx` fájlt a Microsoft Wordben, egy világoskék téglalapot kell látnod, amelynek finom szürke külső árnyéka 45° szöggel vetül. Az árnyék enyhén elmosódott és eltolódott, pontosan úgy, ahogy konfiguráltuk.

### Gyakori buktatók
- **Hiányzó könyvtár:** A `doc.save` hibát dob, ha a mappa nem létezik. Hozd létre előbb, vagy használd az `os.makedirs`‑t.
- **Verzióeltérés:** Az árnyék API az Aspose.Words 22.9+ verziót igényli; a régebbi verziók csendben figyelmen kívül hagyják az árnyék beállításait.

## Teljes működő példa

Az alábbiakban megtalálod a kész, futtatható szkriptet, amely egyesíti az összes lépést. Másold be egy `rectangle_shadow.py` nevű fájlba, majd futtasd a `python rectangle_shadow.py` paranccsal.

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Create a new document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2️⃣ Insert the rectangle shape (how to insert rectangle shape)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle.fill_color = aw.drawing.Color.light_blue   # make the shape visible

# 3️⃣ Define the shadow (how to change shadow color, how to add outer shadow)
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # outer shadow
shadow.blur_radius = 8.0
shadow.distance = 6.0
shadow.direction = 45
shadow.opacity = 0.6
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)  # custom gray

# 4️⃣ Apply the shadow (apply shadow effect to shape)
rectangle.shadow = shadow

# 5️⃣ Save the file
output_path = os.path.join(output_dir, "RectangleWithShadow.docx")
doc.save(output_path)

print(f"✅ Document generated: {output_path}")
```

**Várt eredmény:** Egy Word dokumentum (`RectangleWithShadow.docx`) egyetlen téglalappal és egy szürke külső árnyékkal. Nyisd meg Wordben, hogy ellenőrizd a vizuális hatást.

## Gyakran Ismételt Kérdések

| Kérdés | Válasz |
|----------|--------|
| *Használhatok másik alakzat típust?* | Természetesen – cseréld le a `ShapeType.RECTANGLE`‑t `ShapeType.OVAL`, `ShapeType.TRIANGLE` stb.-re, és ugyanaz a árnyéklogika érvényes. |
| *Mi van, ha vastagabb szegélyre van szükség?* | Állítsd be a `rectangle.line_width = 2.0` (pont) értéket az árnyék alkalmazása előtt. |
| *Lehet-e animálni az árnyékot?* | Közvetlenül az Aspose.Words‑szal nem; animációhoz exportálni kell HTML/CSS formátumba. |
| *Működik ez macOS‑en?* | Igen – az Aspose.Words platform‑független, amíg a Python fut. |

## Következtetés

Áttekintettük, **hogyan illesszünk be téglalap alakzatot**, bemutattuk, **hogyan változtassuk meg az árnyék színét**, elmagyaráztuk, **hogyan adjunk hozzá külső árnyékot**, és végül megmutattuk, **hogyan alkalmazzuk az árnyékhatást az alakzatra** az Aspose.Words for Python segítségével. A teljes szkript készen áll, hogy bármely automatizálási folyamatba beilleszd, így néhány másodperc alatt professzionális megjelenésű téglalapot kapsz egy elegáns árnyékkal.

Készen állsz a következő lépésre? Próbáld ki a kitöltő szín cseréjét, kísérletezz különböző `direction` szögekkel, vagy adj hozzá több alakzatot ugyanarra az oldalra. Felfedezheted továbbá az Aspose.Words gazdag szövegformázó API‑ját, hogy árnyékokat kombinálj formázott szöveggel – tökéletes a figyelemfelkeltő jelentésekhez.

Ha hasznosnak találtad ezt az útmutatót, nyomj egy lájkot, oszd meg a csapattagokkal, vagy hagyj egy megjegyzést a saját variációiddal. Boldog kódolást!

![Diagram showing how to insert rectangle shape with an outer shadow applied in a Word document](/images/rectangle-shadow.png)


## Mit érdemes még tanulni?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljesen működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}