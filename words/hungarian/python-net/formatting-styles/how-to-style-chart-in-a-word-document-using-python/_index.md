---
category: general
date: 2026-08-11
description: Hogyan formázzuk a diagramot egy Word-dokumentumban Python segítségével
  – töltsük be a Word-dokumentumot Pythonban, és alkalmazzuk gyorsan az előre definiált
  diagramstílust.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to style chart
- load word document python
- apply predefined chart style
- apply chart style word
language: hu
lastmod: 2026-08-11
og_description: Hogyan formázzuk a diagramot egy Word-dokumentumban Python segítségével.
  Tanulja meg, hogyan töltsön be egy Word-dokumentumot Pythonban, alkalmazzon előre
  definiált diagramstílust, és mentse el a frissített fájlt.
og_image_alt: Screenshot of Python code applying a chart style to a Word document
og_title: Hogyan formázzuk a diagramot Wordben Python segítségével – lépésről lépésre
  útmutató
schemas:
- author: Aspose
  dateModified: '2026-08-11'
  description: How to style chart in a Word document using Python – load Word document
    python and apply predefined chart style quickly.
  headline: How to style chart in a Word document using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Chart styling
- Word automation
title: Hogyan formázzuk a diagramot egy Word-dokumentumban Python segítségével
url: /hu/python/formatting-styles/how-to-style-chart-in-a-word-document-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan formázzuk a diagramot egy Word dokumentumban Python használatával

Ha **hogyan formázzuk a diagramot** egy Word fájlban szeretnéd megtudni, ez a bemutató pontos lépéseket mutat. Az első két mondat végére már tudni fogod, hogyan tölts be egy Word dokumentumot Python‑nal, hogyan szerezz meg egy diagramot, és hogyan alkalmazz egy előre definiált diagramstílust. A megoldás az Aspose.Words for Python könyvtárral működik, és nem igényel manuális szerkesztést.

Megtanulod, hogyan **load word document python**, hogyan válaszd ki az első diagram alakzatot, állíts be egy beépített stílust, és mentsd el a módosított fájlt. A útmutató kitér a gyakori buktatókra is, például a diagram nélküli dokumentumok kezelésére és a megfelelő stílus‑enumeráció kiválasztására. Az Aspose.Words csomagon kívül nincs szükség külső eszközökre.

## Hogyan formázzuk a diagramot egy Word dokumentumban Python használatával

Egy diagram stílusának alkalmazása egyetlen soros művelet, amint rendelkezel egy `Chart` objektummal. A könyvtár a `ChartStyle` enumerációt teszi elérhetővé, amely tucatnyi előre definiált megjelenést tartalmaz (Style 1 … Style 50). Ebben a szakaszban a **Style 5**‑öt állítjuk be, de az enumerációs értéket bármely, a tervezési irányelveidnek megfelelő stílusra cserélheted.

```python
import aspose.words as aw

# Load the Word document that contains a chart
doc = aw.Document("YOUR_DIRECTORY/input.docx")

# Retrieve the first chart shape in the document
chart_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
chart = chart_shape.as_chart()

# Apply a predefined chart style (Style 5) to the chart
chart.style = aw.drawing.ChartStyle.STYLE_5

# Save the modified document
doc.save("YOUR_DIRECTORY/output.docx")
```

**Miért működik ez:**  
* `aw.Document` beolvassa a .docx fájlt és felépíti az objektummodellt.  
* `get_child(..., aw.NodeType.SHAPE, ...)` megtalálja az első alakzatot, amely a diagram konténer.  
* `as_chart()` a alakzatot `Chart` objektummá konvertálja, így elérhető a `style` tulajdonság.  
* A `ChartStyle.STYLE_5` hozzárendelése azt mondja az Aspose.Words‑nek, hogy cserélje le a diagram vizuális témáját az előre definiált definícióra.

A `output.docx` kimeneti fájl ugyanazt az adatot tartalmazza, mint az eredeti, de a diagram a kiválasztott stílussal jelenik meg.

## Word dokumentum betöltése Python‑ban

Mielőtt diagramot formáznál, helyesen kell **load word document python**. Az `aw.Document` konstruktor egy .docx, .doc vagy .rtf fájl elérési útját fogadja. Győződj meg arról, hogy az útvonal abszolút, vagy hogy a munkakönyvtár a bemeneti fájl helyére mutat.

```python
# Example: absolute path on Windows
doc_path = r"C:\Projects\Charts\input.docx"
doc = aw.Document(doc_path)
```

**Tippek a dokumentumok betöltéséhez:**

* Windowson használj nyers stringeket (`r"..."`), hogy elkerüld a visszaperjelek escape‑elését.  
* Ellenőrizd, hogy a fájl létezik-e a `os.path.isfile(doc_path)` segítségével, így elkerülheted a futási hibákat.  
* Ha a dokumentum védett szakaszokat tartalmaz, add meg a jelszót az `aw.LoadOptions`‑on keresztül.

```python
import os
if not os.path.isfile(doc_path):
    raise FileNotFoundError(f"Document not found: {doc_path}")
```

## Előre definiált diagramstílus alkalmazása

Az **apply predefined chart style** lépésben történik a vizuális átalakulás. Az Aspose.Words definiálja a `ChartStyle` enum‑t, amelynek értékei `STYLE_1`‑től `STYLE_50`‑ig terjednek. Minden stílus egy színkészlethez, jelölőkhöz és vonalformátumokhoz van rendelve, amelyek a Microsoft Office beépített diagramtémáit utánozzák.

```python
# Choose any style from STYLE_1 to STYLE_50
desired_style = aw.drawing.ChartStyle.STYLE_12
chart.style = desired_style
```

**Mikor használj előre definiált stílust:**  

* Ha egységes megjelenést szeretnél több dokumentumban.  
* Ha a diagram adatai gyakran változnak, de a vizuális téma állandó marad.  
* Ha el akarod kerülni a manuális formázást a Word felhasználói felületén.

**Szélsőséges eset – diagram nélküli dokumentum:**  
Ha a `doc.get_child(aw.NodeType.SHAPE, 0, True)` `None`‑t ad vissza, a szkript `AttributeError`‑t dob. Védd le ezt úgy, hogy a node típusát ellenőrzöd a castolás előtt.

```python
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
if shape is None or not shape.has_chart:
    raise ValueError("No chart found in the document.")
chart = shape.as_chart()
```

## A formázott dokumentum mentése

A formázás után a változások mentése egyszerű. A `doc.save` metódus visszaírja a frissített objektummodellt egy .docx fájlba. Exportálhatsz más formátumokba is, például PDF, HTML vagy PNG, ha a downstream felhasználás más ábrázolást igényel.

```python
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)          # Saves as DOCX
doc.save("output.pdf")         # Optional: export to PDF
```

**Ellenőrzés:** Nyisd meg az `output.docx`‑et a Microsoft Word‑ben. A diagramnak az új témát kell mutatnia, és minden adat sorozat megőrzi az eredeti értékeit. Ha PDF‑be exportálsz, a vizuális stílus változatlan marad.

## Gyakori buktatók és gyakorlati tippek

| Probléma | Ok | Megoldás |
|----------|----|----------|
| `AttributeError: 'NoneType' object has no attribute 'as_chart'` | Nem található diagram alakzat a 0‑s indexen | Használd a `doc.get_child(..., 0, True)`‑t try/except blokkban, vagy iterálj az összes alakzaton a `doc.get_child_nodes(aw.NodeType.SHAPE, True)`‑vel. |
| Rossz stílus alkalmazva | Nem létező enum érték használata (pl. `STYLE_0`) | Válassz egy érvényes `ChartStyle` értéket (1‑50). |
| A fájl nem mentődik | A kimeneti útvonal egy csak‑olvasású könyvtárra mutat | Győződj meg róla, hogy a folyamatnak írási joga van, vagy változtasd meg a könyvtárat. |
| A diagram eltűnik mentés után | Az alakzat nem diagram (pl. kép) | Ellenőrizd a `shape.has_chart` értékét a castolás előtt. |

**Pro tipp:** Tárold a leggyakrabban használt `ChartStyle`‑t egy állandóban, így több szkriptben is újra felhasználhatod anélkül, hogy minden alkalommal be kellene írnod az enumerációt.

```python
DEFAULT_CHART_STYLE = aw.drawing.ChartStyle.STYLE_5
chart.style = DEFAULT_CHART_STYLE
```

## Teljes, vég‑től‑végig példakód

Az alábbiakban a teljes, futtatható szkript látható, amely tartalmazza a fent tárgyalt legjobb gyakorlatokat. Cseréld ki a `YOUR_DIRECTORY`‑t a Word fájljaidat tartalmazó tényleges mappára.

```python
import os
import aspose.words as aw

# ----------------------------------------------------------------------
# Configuration
# ----------------------------------------------------------------------
INPUT_PATH = r"YOUR_DIRECTORY/input.docx"
OUTPUT_PATH = r"YOUR_DIRECTORY/output.docx"
DEFAULT_STYLE = aw.drawing.ChartStyle.STYLE_5

# ----------------------------------------------------------------------
# Load the document
# ----------------------------------------------------------------------
if not os.path.isfile(INPUT_PATH):
    raise FileNotFoundError(f"Input file not found: {INPUT_PATH}")

doc = aw.Document(INPUT_PATH)

# ----------------------------------------------------------------------
# Locate the first chart
# ----------------------------------------------------------------------
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
if shape is None or not shape.has_chart:
    raise ValueError("No chart shape found in the document.")

chart = shape.as_chart()

# ----------------------------------------------------------------------
# Apply the predefined chart style
# ----------------------------------------------------------------------
chart.style = DEFAULT_STYLE

# ----------------------------------------------------------------------
# Save the modified document
# ----------------------------------------------------------------------
doc.save(OUTPUT_PATH)

print(f"Chart style applied successfully. Saved to {OUTPUT_PATH}")
```

**Várható eredmény:**  
Amikor megnyitod a `output.docx`‑et, az első diagram a `STYLE_5` által definiált vizuális témát mutatja. Minden adatpont, tengely és jelmagyarázat változatlan marad, ami azt bizonyítja, hogy a formázás független az alapadatoktól.

## Összegzés

Most már tudod, **hogyan formázzuk a diagramot** egy Word dokumentumban Python‑nal. A bemutató lefedte, hogyan **load word document python**, hogyan szerezzük meg a diagram alakzatot, hogyan **apply predefined chart style**, és hogyan mentsük el a frissített fájlt. Ezekkel az építőelemekkel automatizálhatod a jelentéskészítést, érvényesítheted a vállalati arculatot, vagy tömegesen feldolgozhatsz tucatnyi dokumentumot manuális munka nélkül.

Ezután fedezd fel a további diagramtestreszabásokat, például a sorok színének módosítását, adatcímkék hozzáadását vagy a diagram képként való exportálását. Tekintsd át az Aspose.Words dokumentációját olyan témákért, mint **apply chart style word**, **chart data manipulation**, és **document conversion**, hogy bővítsd az automatizálási képességeidet.

Nyugodtan kísérletezz különböző `ChartStyle` értékekkel, és integráld ezt a szkriptet nagyobb adatcsővezetékekbe, amelyek adatbázisokból vagy API‑kból generálnak Word jelentéseket. Boldog kódolást!

## Mit érdemes még megtanulni?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás komplett, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy elsajátíthasd a további API‑funkciókat, és alternatív megvalósítási megközelítéseket fedezhess fel saját projektjeidben.

- [Oszlopdiagram beszúrása Word dokumentumba](/words/english/net/programming-with-charts/insert-column-chart/)
- [Egyszerű oszlopdiagram beszúrása Word dokumentumba](/words/english/net/programming-with-charts/insert-simple-column-chart/)
- [Területdiagram beszúrása Word dokumentumba](/words/english/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}