---
category: general
date: 2026-05-30
description: Hogyan szúrjunk be téglalapot és adjunk árnyékot a Wordben az Aspose
  használatával – egy lépésről‑lépésre Python útmutató a Word dokumentum alakzatárnyék‑hatásának
  létrehozásához.
draft: false
keywords:
- how to insert rectangle
- add shadow to shape
- how to add shape shadow
- apply shadow effect word
- create word document aspose
language: hu
og_description: Hogyan szúrjunk be egy téglalapot és adjunk hozzá árnyékot a Wordben
  az Aspose segítségével – tanulja meg, hogyan hozhatunk létre egy Word dokumentumot
  alakzatárnyék‑effekttel Pythonban.
og_title: Hogyan szúrjunk be egy téglalapot, és adjunk hozzá árnyékot a Wordben az
  Aspose segítségével
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: How to insert rectangle and add shadow in Word using Aspose – a step‑by‑step
    Python guide to create a Word document with shape shadow effect.
  headline: How to insert rectangle and add shadow in Word using Aspose
  type: TechArticle
- description: How to insert rectangle and add shadow in Word using Aspose – a step‑by‑step
    Python guide to create a Word document with shape shadow effect.
  name: How to insert rectangle and add shadow in Word using Aspose
  steps:
  - name: What each property does
    text: '| Property | Effect | Typical Range | |----------|--------|---------------|
      | `visible` | Turns the shadow on/off | `True` / `False` | | `distance` | How
      far the shadow sits from the shape | 2 – 10 pts | | `blur` | Softness of the
      shadow edges | 4 – 12 pts | | `color` | Shadow hue; dark gray is a sa'
  - name: Adding Multiple Shapes
    text: If you need more than one rectangle, simply repeat the `insert_shape` call.
      Remember to move the builder’s cursor (`builder.move_to(shape)`) or adjust `shape.left`/`shape.top`
      to avoid overlap.
  - name: Changing the Shape Type
    text: While this guide focuses on rectangles, the same pattern works for ovals,
      stars, or custom free‑form shapes. Replace `ShapeType.RECTANGLE` with `ShapeType.OVAL`,
      `ShapeType.CLOUD`, etc., and the shadow settings remain identical.
  - name: Saving to Other Formats
    text: 'Aspose.Words can export to PDF, PNG, or even XPS with a single line:'
  - name: Handling Large Documents
    text: When generating massive reports, consider calling `doc.update_page_layout()`
      after inserting all shapes. This forces a layout pass and can improve performance
      when you later convert to PDF.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word Automation
title: Hogyan szúrjunk be téglalapot és adjunk árnyékot a Wordben az Aspose használatával
url: /hu/python/images-shapes/how-to-insert-rectangle-and-add-shadow-in-word-using-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan szúrjunk be téglalapot és adjunk árnyékot a Wordben az Aspose használatával

Gondolkodtál már azon, **hogyan szúrj be egy téglalapot** egy Word fájlba anélkül, hogy megnyitnád a felhasználói felületet? Nem vagy egyedül. Sok fejlesztőnek kell gyorsan jelentéseket, számlákat vagy tanúsítványokat generálnia, és egy egyszerű téglalap megrajzolása szép árnyékkal a kimenetet kifinomulttá teheti. Ebben az útmutatóban lépésről lépésre bemutatjuk, hogyan hozhatsz létre egy Word dokumentumot, helyezhetsz el egy téglalap alakzatot, és alkalmazhatsz egy valósághű árnyékot az Aspose.Words for Python segítségével.

Mindent lefedünk a Aspose csomag beállításától az árnyék távolságának, elmosódásának és átlátszatlanságának finomhangolásáig. A végére egy újrahasználható kódrészletet kapsz, amelyet bármely automatizálási folyamatba beilleszthetsz. Nincs varázslat, csak tiszta kód és néhány gyakorlati tipp.

## Előfeltételek

Mielőtt belemerülnénk, győződj meg róla, hogy rendelkezel a következőkkel:

- Python 3.8+ telepítve (a kód működik 3.9, 3.10 és újabb verziókon)
- Aktív Aspose.Words for Python licenc vagy egy ingyenes értékelő kulcs
- `aspose-words` csomag telepítve a `pip install aspose-words` paranccsal
- Írási jogosultsággal rendelkező mappa, ahová a generált **create word document aspose** mentésre kerül

Ennyi—nincs extra DLL, nincs COM interop, csak tiszta Python.

## 1. lépés: A dokumentum inicializálása (How to create word document aspose)

Először is: szükséged van egy új `Document` objektumra. Gondolj rá, mint egy üres vászonra. Az alábbi kód létrehozza a dokumentumot és egy `DocumentBuilder`‑t, amely lehetővé teszi alakzatok beszúrását.

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

*Miért fontos:* A `DocumentBuilder` egy magas szintű API‑t biztosít a bekezdések, táblázatok és – igen – alakzatok hozzáadásához anélkül, hogy alacsony szintű csomópontfákkal kellene foglalkoznod. Ha kihagyod a buildert és közvetlenül manipulálod a csomópontokat, akkor bőbeszédű, nehezebben karbantartható kóddal végzel.

## 2. lépés: Téglalap beszúrása (how to insert rectangle)

Most már ténylegesen **hogyan szúrj be egy téglalapot**. Az Aspose.Words a téglalapot egy általános alakzattípusként kezeli. A szélességet és magasságot pontban adod meg (1 pont ≈ 1/72 hüvelyk). Nyugodtan módosítsd a számokat, hogy illeszkedjenek a elrendezésedhez.

```python
# Step 2: Insert a rectangle shape of the desired size
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

> **Pro tipp:** Ha a téglalapot a lap egy adott helyére szeretnéd pozícionálni, állítsd be a `shape.left` és `shape.top` értékeket a beszúrás után. Ez pixel‑pontos vezérlést biztosít.

## 3. lépés: Az alakzat árnyékformátumának elérése (add shadow to shape)

Az alakzat vizuális hatását a `ShadowFormat` határozza meg. Ennek lekérdezésével hozzáférünk minden olyan tulajdonsághoz, amely az árnyék megjelenését definiálja.

```python
# Step 3: Access the shape's shadow format
shadow = shape.shadow_format
```

Ekkor az árnyék láthatatlan – tekintsd úgy, mint egy rejtett réteget, amely a te utasításaidra vár.

## 4. lépés: Az árnyék beállítása (how to add shape shadow, apply shadow effect word)

Itt történik a varázslat. Bekapcsoljuk az árnyékot és finomhangoljuk a megjelenését. Az alábbi értékek egy lágy, átlós árnyékot eredményeznek, amely a legtöbb dokumentumban jól működik, de nyugodtan kísérletezhetsz.

```python
# Step 4: Make the shadow visible and configure its appearance
shadow.visible = True                # Show the shadow
shadow.distance = 5.0                # Distance from the shape (points)
shadow.blur = 8.0                    # Blur radius (points)
shadow.color = aw.Color.dark_grey   # Shadow color
shadow.opacity = 0.6                 # Opacity (0‑1)
shadow.angle = 45.0                  # Direction in degrees
```

### Mit jelent minden egyes tulajdonság

| Property | Hatás | Tipikus tartomány |
|----------|--------|-------------------|
| `visible` | Turns the shadow on/off | `True` / `False` |
| `distance` | How far the shadow sits from the shape | 2 – 10 pts |
| `blur` | Softness of the shadow edges | 4 – 12 pts |
| `color` | Shadow hue; dark gray is a safe default | Any `aw.Color` |
| `opacity` | Transparency; 0 = invisible, 1 = solid | 0.3 – 0.8 for subtle look |
| `angle` | Direction the light comes from | 0 – 360° |

**Miért érdemes ezeket módosítani?** Egy jól beállított árnyék a lapos téglalapot úgy mutathatja, mintha a lapról kiemelkedne, mélységet adva képek nélkül. Ha a `opacity`‑t túl magasra állítod, az árnyék kemény lesz; ha túl alacsony, akkor eltűnik.

## 5. lépés: A dokumentum mentése (create word document aspose)

Végül írd a fájlt a lemezre. Bármely, az Aspose.Words által támogatott kiterjesztést használhatod (`.docx`, `.pdf`, `.html`). Ebben az útmutatóban a `.docx`-et fogjuk használni.

```python
# Step 5: Save the document with the shaped shadow
output_path = "output/ShapeWithShadow.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Nyisd meg a kapott fájlt a Microsoft Wordben, és egy tiszta téglalapot látsz majd egy finom árnyékkal – pontosan azt, amit egy professzionálisan tervezett sablontól várnál.

![hogyan szúrjunk be téglalap alakzatot árnyékkal az Aspose.Words használatával](/images/rectangle-shadow.png){alt="hogyan szúrjunk be téglalap alakzatot árnyékkal az Aspose.Words használatával"}

*A fenti képernyőfotó a téglalapot mutatja az alkalmazott árnyékkal. Figyeld meg a lágy elmosódást és a 45°-os szöget, amely természetes megjelenést kölcsönöz.*

## Gyakori változatok és szélhelyzetek

### Több alakzat hozzáadása

Ha egynél több téglalapra van szükséged, egyszerűen ismételd meg az `insert_shape` hívást. Ne feledd, hogy a builder kurzorát (`builder.move_to(shape)`) át kell mozgatni, vagy állítsd be a `shape.left`/`shape.top` értékeket a átfedés elkerülése érdekében.

```python
# Example: Insert a second rectangle 200 points to the right
second_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
second_shape.left = shape.left + 200
second_shape.top = shape.top
```

### Az alakzat típusának módosítása

Bár ez az útmutató a téglalapokra koncentrál, ugyanaz a minta működik oválisok, csillagok vagy egyedi szabad formájú alakzatok esetén is. Cseréld le a `ShapeType.RECTANGLE`-t `ShapeType.OVAL`, `ShapeType.CLOUD` stb.-re, és az árnyék beállítások változatlanok maradnak.

### Mentés más formátumokba

Az Aspose.Words egyetlen sorral exportálhat PDF, PNG vagy akár XPS formátumba:

```python
doc.save("output/ShapeWithShadow.pdf")
```

Az árnyék megjelenítése megmarad a különböző formátumokban, így a PDF pontosan úgy néz ki, mint a Word fájl.

### Nagy dokumentumok kezelése

Nagy jelentések generálásakor érdemes a `doc.update_page_layout()` metódust meghívni az összes alakzat beszúrása után. Ez kényszeríti a layout átfutást, és javíthatja a teljesítményt, amikor később PDF-be konvertálsz.

## Teljes működő példa (Minden lépés egyben)

Az alábbiakban a teljes szkript található, amelyet beilleszthetsz egy `rectangle_shadow.py` nevű fájlba. Futtasd a `python rectangle_shadow.py` paranccsal, és ellenőrizd az `output` mappát.

```python
import aspose.words as aw
import os

# Ensure the output directory exists
os.makedirs("output", exist_ok=True)

# Initialize the document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Insert a rectangle
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

# Configure the shadow
shadow = shape.shadow_format
shadow.visible = True
shadow.distance = 5.0
shadow.blur = 8.0
shadow.color = aw.Color.dark_grey
shadow.opacity = 0.6
shadow.angle = 45.0

# Save the document
output_path = "output/ShapeWithShadow.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

A szkript futtatása pontosan ugyanazt a dokumentumot hozza létre, amiről korábban beszéltünk. Nyugodtan módosítsd a számokat; a kód szándékosan egyszerű, hogy félelem nélkül kísérletezhess.

## Gyakran Ismételt Kérdések

**K: Működik ez Linuxon?**


## Mit érdemes legközelebb megtanulni?

- [Word dokumentum létrehozása Java – Téglalap alakzat hozzáadása árnyékhatással](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Üres Word dokumentum létrehozása árnyékolt téglalap alakzattal – Lépésről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words alakzat árnyék tutorial – Árnyék hozzáadása Word alakzathoz C#‑ban](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}