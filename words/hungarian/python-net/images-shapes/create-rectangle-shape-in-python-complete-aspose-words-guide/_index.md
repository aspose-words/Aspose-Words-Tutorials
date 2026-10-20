---
category: general
date: 2026-06-24
description: Hozzon létre téglalap alakzatot Pythonban az Aspose.Words segítségével,
  tanulja meg, hogyan adjon árnyékot az alakzathoz, állítsa be az árnyék szögét, és
  mentse a dokumentumot PDF‑ként percek alatt.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shape shadow
- set shadow angle
language: hu
og_description: Hozzon létre téglalap alakzatot Pythonban, adjon árnyékot az alakzathoz,
  állítsa be az árnyék szögét, és mentse a dokumentumot PDF formátumban az Aspose.Words
  segítségével. Kövesse ezt a lépésről‑lépésre útmutatót.
og_title: Téglalap alakzat létrehozása Pythonban – Teljes Aspose.Words útmutató
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  headline: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  name: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: What if I need a different shape?
    text: Aspose.Words supports many `ShapeType` values (ellipse, star, callout, etc.).
      Simply replace `aw.drawing.ShapeType.RECTANGLE` with the desired enum, like
      `aw.drawing.ShapeType.ELLIPSE`.
  - name: Can I add multiple shadows?
    text: The API exposes only one `ShadowFormat` per shape, but you can simulate
      multiple shadows by duplicating the shape, offsetting each copy, and adjusting
      transparency.
  - name: How do I change the shadow color to match my brand?
    text: Just set `shadow.color` to any `aw.drawing.Color`. For a brand blue, use
      `aw.drawing.Color.from_argb(255, 0, 120, 215)`.
  - name: What about saving as DOCX instead of PDF?
    text: Replace `document.save(pdf_path)` with `document.save("output/shadowed_rectangle.docx")`.
      The shadow rendering is preserved across both formats.
  - name: Does the shadow work on older PDF viewers?
    text: Aspose.Words renders the shadow as a vector effect, which is widely supported.
      However, very old viewers might flatten the effect; testing on your target audience’s
      devices is always a good habit.
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: Téglalap alakzat létrehozása Pythonban – Teljes Aspose.Words útmutató
url: /hu/python/images-shapes/create-rectangle-shape-in-python-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Téglalap alakzat létrehozása Pythonban – Teljes Aspose.Words útmutató

Valaha is elgondolkodtál, hogyan **create rectangle shape** alakzatot hozhatsz létre egy Word dokumentumban Python segítségével? Lehet, hogy egy merész felhívó dobozra, egy diagram vizuális jelzésére, vagy egyszerűen csak egy elegáns téglalapra van szükséged egy jelentéshez. Bármelyik is legyen, a megfelelő helyen vagy. Ebben az útmutatóban végigvezetünk a teljes folyamaton – a téglalap beszúrásától, egy finom árnyék hozzáadásáig, az árnyék szögének finomhangolásáig, és végül a **save document as PDF** műveletig, hogy megoszthasd bárkivel.

A **Aspose.Words for Python via .NET** könyvtárat fogjuk használni, amely lehetővé teszi a Word fájlok manipulálását anélkül, hogy a Word programot megnyitnánk. A útmutató végére magabiztosan tudni fogod megválaszolni a *“how to add shape shadow”* kérdést, és lesz egy kész‑futtatható szkripted, amelyet bármely projektbe beilleszthetsz.

---

## Amire szükséged lesz

Before we dive in, make sure you have the following:

- **Python 3.8+** telepítve van a gépeden.  
- **Aspose.Words for Python via .NET** (`aspose-words` csomag). Telepítsd a következővel:

  ```bash
  pip install aspose-words
  ```

- Egy írható mappa, ahová a generált PDF mentésre kerül.  
- (Opcionális) Egy IDE vagy szövegszerkesztő – a VS Code remekül működik.

Ennyi. Nincs szükség extra DLL‑ekre, Office telepítésre, csak egyetlen pip csomagra.

## 1. lépés: A dokumentum és a builder beállítása

Az első dolog, amit tenned kell, hogy **create rectangle shape**‑barát objektumokat hozz létre: egy `Document` és egy `DocumentBuilder`. Gondolj a builderre, mint a tolladra; mindennek a rajzolását elvégzi.

```python
import aspose.words as aw

# Initialize a new blank document
document = aw.Document()

# DocumentBuilder gives us a convenient way to add content
builder = aw.DocumentBuilder(document)
```

> **Miért fontos:** A `Document` objektum a teljes .docx fájlt képviseli, míg a `DocumentBuilder` olyan metódusokat biztosít, mint a `insert_shape`, amelyekkel a formák rajzolása gyerekjáték.

## 2. lépés: A téglalap alakzat beszúrása

Most, hogy van egy builderünk, végre **create rectangle shape** alakzatot hozhatunk létre. Az `insert_shape` metódus három argumentumot igényel: a forma típusát, a szélességet és a magasságot. Egy szép arányhoz 200 pt szélességet és 100 pt magasságot fogunk használni.

```python
# Insert a rectangle with a width of 200 points and a height of 100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

Ekkor már sikeresen **create rectangle shape** alakzatot hoztál létre a dokumentumban. Ha megnyitod a generált DOCX‑et (később meg fogjuk nézni), egy egyszerű téglalapot látsz, amely a kurzor helyén helyezkedik el.

## 3. lépés: Az árnyék formázási objektum elérése

A **add shadow to shape** művelethez először meg kell szereznünk a forma árnyékformázását. Minden forma az Aspose.Words‑ben rendelkezik egy `shadow_format` tulajdonsággal, amely az összes árnyék‑kapcsolódó beállítást elérhetővé teszi.

```python
# Grab the shadow formatting object for later tweaks
shadow = rectangle.shadow_format
```

A `shadow` hivatkozás birtokában ki tudjuk kapcsolni a láthatóságot, a elmosódást, a távolságot, a szöget, a színt és az átlátszóságot – mindezt néhány kódsorral.

## 4. lépés: Az árnyék engedélyezése és megjelenésének beállítása

Itt történik a varázslat. **add shadow to shape**, majd enyhén elmosódottá tesszük, egy kicsit eltoljuk, beállítjuk az irányt (a **set shadow angle** rész), és egy félig átlátszó fekete árnyalatot adunk neki.

```python
# Turn the shadow on
shadow.visible = True

# Soften the edges – a blur radius of 8 points looks natural
shadow.blur_radius = 8.0

# Push the shadow away from the rectangle by 5 points
shadow.distance = 5.0

# Set the direction of the light source – 45 degrees creates a diagonal drop
shadow.angle = 45

# Choose a color; black works well for most documents
shadow.color = aw.drawing.Color.black

# Make the shadow 30 % transparent for a subtle effect
shadow.transparency = 0.3
```

> **Pro tipp:** Ha valaha drámaibb hatásra van szükséged, növeld a `blur_radius` értékét vagy csökkentsd a `transparency`‑t. Ezzel szemben egy éles, teljesen átlátszatlan árnyék elérhető a `blur_radius = 0` és `transparency = 0` beállításokkal.

## 5. lépés: A dokumentum mentése PDF‑ként

Elvégeztük a **create rectangle shape**, elvégeztük a **add shadow to shape**, és most **save document as PDF**, hogy az eredmény minden eszközön azonos legyen. Az Aspose.Words ezt egyetlen soros kóddal megoldja.

```python
# Define where you want the PDF to land
output_path = "output/shadowed_rectangle.pdf"

# Save the whole document (including the rectangle with its shadow) as PDF
document.save(output_path)
print(f"PDF saved to {output_path}")
```

A szkript futtatása létrehozza a `shadowed_rectangle.pdf` fájlt az `output` mappában. Nyisd meg bármely PDF‑olvasóval, és egy tiszta téglalapot látsz egy lágy, 45‑fokos árnyékkal – pontosan úgy, ahogy beállítottuk.

## Teljes működő példa

Az alábbiakban a teljes, készen álló szkript található, amely egyesíti a fenti lépéseket. Másold be egy `create_rectangle_with_shadow.py` nevű fájlba, majd futtasd a `python create_rectangle_with_shadow.py` parancsot.

```python
import aspose.words as aw
import os

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Initialize document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert the rectangle shape (200 pt × 100 pt)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Access shadow formatting
shadow = rectangle.shadow_format

# 4️⃣ Configure shadow – visible, blurred, offset, angled, colored, semi‑transparent
shadow.visible = True
shadow.blur_radius = 8.0          # softer edges
shadow.distance = 5.0            # how far the shadow sits from the shape
shadow.angle = 45                # direction in degrees – this is the **set shadow angle** step
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.3        # 30 % transparent

# 5️⃣ Save the document as PDF
pdf_path = os.path.join(output_dir, "shadowed_rectangle.pdf")
document.save(pdf_path)

print(f"✅ PDF created at: {pdf_path}")
```

**Expected output:** Egy PDF fájl, amely egyetlen téglalapot mutat egy enyhe, átlós árnyékkal. Nincs extra oldal, nincs rejtett művelet – csak a általunk megalkotott forma.

## Gyakori kérdések és speciális esetek

### Mi van, ha másik alakzatra van szükségem?

Az Aspose.Words számos `ShapeType` értéket támogat (ellipszis, csillag, felhívás stb.). Egyszerűen cseréld le a `aw.drawing.ShapeType.RECTANGLE` értéket a kívánt enumra, például `aw.drawing.ShapeType.ELLIPSE`‑re.

### Hozzáadhatok több árnyékot?

Az API minden formához csak egy `ShadowFormat`‑ot biztosít, de több árnyékot szimulálhatsz a forma megkettőzésével, minden másolat eltolásával és az átlátszóság beállításával.

### Hogyan változtathatom meg az árnyék színét, hogy illeszkedjen a márkámhoz?

Egyszerűen állítsd be a `shadow.color`‑t bármely `aw.drawing.Color` értékre. Márkaszín kékhez használd a `aw.drawing.Color.from_argb(255, 0, 120, 215)` kódot.

### Mi van a DOCX‑ként való mentéssel a PDF helyett?

Cseréld le a `document.save(pdf_path)` hívást `document.save("output/shadowed_rectangle.docx")`‑re. Az árnyék megjelenítése mindkét formátumban megmarad.

### Működik az árnyék régebbi PDF‑olvasókon?

Az Aspose.Words az árnyékot vektoros hatásként rendereli, ami széles körben támogatott. Azonban nagyon régi olvasók esetén a hatás laposra konvertálódhat; mindig érdemes tesztelni a célközönség eszközein.

## Tippek a PDF tökéletesítéséhez

- **Add a border:** `rectangle.line_format.width = 1.5` és állíts be egy színt a tiszta körvonalhoz.  
- **Center the rectangle:** Használd a `builder.move_to_document_start()`‑t a beszúrás előtt, majd `builder.paragraph_format.alignment = aw.ParagraphAlignment.CENTER`.  
- **Combine with text:** Szúrj be egy `TextFragment`‑et a téglalap után, hogy felcímkézd, például `"Important Section"`.

Ezek a kis finomítások egy egyszerű téglalapot egy kifinomult felhívó dobozzá alakíthatják, amely professzionális megjelenést kölcsönöz jelentéseknek, ajánlatoknak vagy e‑könyveknek.

## Összegzés

Most már egy átfogó, lépésről‑lépésre útmutatóval rendelkezel a **create rectangle shape** Pythonban, a **add shadow to shape**, a **set shadow angle**, és a **save document as PDF** végrehajtásához az Aspose.Words segítségével. A lépések egyszerűek, a kód teljesen önálló, és láttad, miért fontos minden egyes sor – a dokumentum inicializálásától a végső PDF finomhangolásáig.

Ezután érdemes lehet felfedezni a **how to add shape shadow** alkalmazását összetettebb rajzokon, kísérletezni a színátmenetes kitöltésekkel, vagy táblázatokat generálni a formákon belül. A könyvtár támogatja a formák könyvjelzőkhöz való kapcsolását is, ami hasznos lehet interaktív PDF‑ek esetén.

Van valami saját megoldásod? Oszd meg a kommentekben, vagy tedd fel a maradt kérdéseidet. Boldog kódolást, és élvezd a dokumentumaid extra mélységének hozzáadását! 

![Téglalap alakzat árnyékkal – a create rectangle shape példa Pythonban](/images/rectangle-shadow.png)

## Mi legyen a következő tanulnivalód?

Az alábbi útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes működő kódpéldákat tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API‑funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Word dokumentum létrehozása Java – Téglalap alakzat hozzáadása árnyékhatással](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words alakzat árnyék tutorial – Árnyék hozzáadása Word alakzathoz C#‑ban](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Téglalap alakzat létrehozása Wordben C# használatával – Lépésről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}