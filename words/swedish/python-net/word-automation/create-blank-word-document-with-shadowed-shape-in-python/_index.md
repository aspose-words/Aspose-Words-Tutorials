---
category: general
date: 2026-10-16
description: Skapa ett tomt Word‑dokument, infoga en form i Word, lägg till yttre
  skugga och spara som PDF med Python.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert shape in word
- save as pdf python
- add outer shadow shape
- create pdf with shape
language: sv
lastmod: 2026-10-16
og_description: Skapa ett tomt Word-dokument med en yttre skuggform med Aspose.Words
  för Python. Denna guide visar hur du infogar formen, applicerar skuggan och sparar
  filen som en PDF.
og_image_alt: Screenshot of a Word document containing a rectangle shape with an outer
  shadow, saved as PDF
og_title: Skapa ett tomt Word‑dokument med formskugga – Python‑guide
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
title: Skapa tomt Word-dokument med skuggad form i Python
url: /sv/python/word-automation/create-blank-word-document-with-shadowed-shape-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa tomt Word-dokument med skuggad form i Python

Om du behöver **create blank Word document** och lägga till en anpassad grafik, så har den här guiden dig täckt. Vi går igenom hur du **insert shape in Word**, applicerar en **outer shadow shape**, och slutligen **save as PDF using Python**.

Du kommer att lära dig hur du konfigurerar Aspose.Words for Python, bygger en rektangel, stiliserar dess skugga och genererar en PDF som bevarar den visuella effekten. Ingen tidigare erfarenhet av Aspose API krävs, men du bör ha grundläggande kunskaper i Python och en fungerande installation av Python 3.10 eller senare.

## Förutsättningar

Innan du börjar, se till att du har:

* Python 3.10 eller nyare installerat.
* En aktiv Aspose.Words for Python-licens (en gratis provperiod fungerar för utvärdering).
* `pip`-åtkomst för att installera paketet `aspose-words`.
* Skrivbehörighet till den katalog där PDF-filen kommer att sparas.

Du kan installera biblioteket med ett enda kommando:

```bash
pip install aspose-words
```

## Skapa tomt Word-dokument – miljöinställning

Det första steget är att skapa en tom Word-fil som kommer att fungera som en duk för formen.

```python
import aspose.words as aw

# Initialize a new, empty document
doc = aw.Document()
# DocumentBuilder provides convenient methods for adding content
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` representerar en helt tom Word-fil. Genom att använda `DocumentBuilder` får du tillgång till metoder som `insert_shape`, som vi kommer att använda i nästa steg.

## Infoga form i Word och ange dimensioner

Nu lägger vi till en rektangel som senare kommer att få en yttre skugga. Storleken anges i punkter (1 pt ≈ 1/72 tum).

```python
# Insert a rectangle shape with a width of 200 pt and a height of 100 pt
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)
```

`insert_shape`-anropet returnerar ett `Shape`-objekt som du kan anpassa ytterligare. Vid detta tillfälle innehåller dokumentet redan en synlig rektangel när det öppnas i Microsoft Word.

## Lägg till yttre skugga – anpassa effekten

Aspose.Words tillhandahåller en `ShadowEffect`-klass för att definiera skuggegenskaper som stil, oskärpa, avstånd och färg.

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

Att sätta `style` till `OUTER` säkerställer att skuggan visas utanför rektangelns kant, vilket ger ett subtilt 3‑D‑utseende. Du kan experimentera med `blur` och `distance` för att uppnå en tajtare eller mer diffus skugga.

## Spara som PDF med Python – slutför dokumentet

Efter att ha stylat formen kan dokumentet sparas direkt som en PDF. Aspose.Words hanterar konverteringen internt och bevarar skuggeffekten.

```python
output_path = "output/shape_with_shadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

När du öppnar `shape_with_shadow.pdf` i någon PDF-läsare kommer du att se rektangeln med den yttre skuggan exakt som den såg ut i Word.

## Fullt fungerande exempel

Nedan är det kompletta skriptet som kombinerar alla steg. Kopiera det till en fil med namnet `create_word_with_shadow.py` och kör den.

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

**Förväntad output**

Kör du skriptet skrivs en bekräftelsesrad ut, t.ex.:

```
PDF generated at: output/shape_with_shadow.pdf
```

Att öppna den resulterande PDF-filen visar en enda sida som innehåller en 200 pt × 100 pt rektangel med en mjuk svart yttre skugga.

## Vanliga variationer och kantfall

* **Changing shadow color** – Ersätt `aw.Color.black` med något annat `aw.Color`-värde, såsom `aw.Color.red` eller `aw.Color.from_argb(255, 0, 120, 215)`.
* **Using a different shape** – Ändra `aw.drawing.ShapeType.RECTANGLE` till `OVAL`, `DIAMOND` eller något annat stödjande enum‑värde.
* **Saving as DOCX instead of PDF** – Anropa `doc.save("output/shape.docx")` för att behålla Word-formatet.
* **Multiple shapes** – Skapa ytterligare former genom att anropa `builder.insert_shape` igen; varje form kan ha sin egen `ShadowEffect`.

**Pro tip:** Om du behöver placera formen på en specifik plats, sätt `rectangle.left` och `rectangle.top` efter insättningen. Detta ger dig pixel‑perfekt kontroll över placeringen.

## Slutsats

Du vet nu hur du **create blank Word document**, **insert shape in Word**, **add outer shadow shape**, och **save as PDF using Python**. Det kompletta kodexemplet demonstrerar hela arbetsflödet, och förklaringarna klargör varför varje API‑anrop är nödvändigt.

Från detta kan du utforska mer avancerade stilalternativ, lägga till text i formen, eller kombinera flera former för att bygga komplexa diagram. Experimentera med olika skuggeparametrar för att matcha ditt varumärkes visuella språk, och integrera detta tillvägagångssätt i större dokument‑genereringspipelines.

Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa rektangelform, lägg till skugga & spara PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Skapa PDF från Word – Komplett Python‑guide med Aspose.Words](/words/english/python-net/document-conversion/create-pdf-from-word-complete-python-guide-with-aspose-words/)
- [Lägg till skugga på form i Word med Aspose.Words – Steg‑för‑steg](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}