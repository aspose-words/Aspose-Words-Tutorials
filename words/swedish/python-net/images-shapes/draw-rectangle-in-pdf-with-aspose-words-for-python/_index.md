---
category: general
date: 2026-08-07
description: Rita en rektangel i PDF med Aspose.Words för Python och lär dig hur du
  lägger till skugga på formen, konfigurerar formens skugga och sparar dokumentet
  som PDF.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle in pdf
- add shadow to shape
- save document as pdf
- configure shape shadow
language: sv
lastmod: 2026-08-07
og_description: Rita rektangel i PDF med Aspose.Words för Python. Denna handledning
  visar hur man lägger till skugga på en form, konfigurerar formens skugga och sparar
  dokumentet som PDF för professionell dokumentgenerering.
og_image_alt: PDF page showing a rectangle shape with a visible shadow created by
  Aspose.Words for Python
og_title: Rita rektangel i PDF med Aspose.Words för Python – guide
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Draw rectangle in PDF using Aspose.Words for Python and learn how to
    add shadow to shape, configure shape shadow, and save document as PDF.
  headline: Draw rectangle in PDF with Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF
- Shape
- Shadow
title: Rita rektangel i PDF med Aspose.Words för Python
url: /sv/python/images-shapes/draw-rectangle-in-pdf-with-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rita rektangel i PDF med Aspose.Words för Python

Om du behöver **draw rectangle in PDF** medan du arbetar i Python, ger den här guiden en komplett, färdig‑att‑köra lösning. Du kommer att se exakt hur du **add shadow to shape**, konfigurerar den skuggan och slutligen **save document as PDF** för distribution eller arkivering.

Att skapa en skuggad rektangel är ett vanligt krav för rapporter, fakturor eller visuella annotationer. I slutet av den här handledningen har du ett enda skript som producerar en PDF som innehåller en rektangel med en realistisk skugga, och du kommer att förstå hur du justerar storlek, färg och offset för att passa vilken design som helst.

## Förutsättningar

* Python 3.8+ installerat.
* Aspose.Words for Python via .NET-paketet (`aspose-words`) – installera med:

```bash
pip install aspose-words
```

* Skrivbehörighet till den mapp där du avser att spara PDF-filen.

Inga ytterligare bibliotek krävs; Aspose.Words hanterar skapande av former, konfiguration av skugga och PDF-export internt.

## Steg 1: Skapa ett nytt tomt dokument (draw rectangle in PDF – initialize)

Det första steget är att instansiera ett `Document`-objekt. Detta objekt representerar hela PDF-filen och tillhandahåller en behållare för sektioner, stycken och former.

```python
import aspose.words as aw

# Create an empty Word document – it will become a PDF later
doc = aw.Document()
```

**Varför detta är viktigt:** Aspose.Words behandlar PDF-generering som en konvertering från en Word-dokumentmodell, så vi börjar med ett `Document` även om slutresultatet är en PDF.

## Steg 2: Infoga en rektangel‑form i dokumentets kropp

En rektangel är en specifik `ShapeType`. Vi lägger till den i den första sektionens kropp, vilket automatiskt skapar en ny sida när den sparas som PDF.

```python
# Append a rectangle shape to the first section's body
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Set the rectangle's dimensions (points = 1/72 inch)
rectangle.width = 200   # 200 pt ≈ 2.78 in
rectangle.height = 100  # 100 pt ≈ 1.39 in

# Optional: give the shape some visible text
rectangle.text = "Shadow demo"
```

**Förklaring:** `width`- och `height`-egenskaperna styr den visuella storleken på formen i PDF:en. Att lägga till text gör rektangeln enklare att verifiera under testning.

## Steg 3: Lägg till skugga på formen – aktivera och anpassa

Nu slår vi på skuggeffekten och finjusterar dess utseende. Det är här nyckelordet **add shadow to shape** kommer i spel.

```python
# Access the shape's shadow effect object
shadow = rectangle.shadow_effect

# Make the shadow visible
shadow.visible = True

# Configure blur radius (pt) – higher values produce a softer edge
shadow.blur = 8

# Set the distance (offset) from the shape in points
shadow.distance = 5

# Define the direction of the shadow in degrees (0 = right, 90 = down)
shadow.angle = 45

# Choose a shadow color – black works for most documents
shadow.color = aw.drawing.Color.black
```

**Varför konfigurera formens skugga?** Genom att justera `blur`, `distance` och `angle` kan du simulera realistisk belysning, vilket förbättrar läsbarhet och visuell hierarki i genererade PDF‑filer.

## Steg 4: Spara dokument som PDF – slutligt resultat

Med rektangeln och dess skugga definierade är sista steget att exportera Word-dokumentet till PDF. Detta uppfyller kravet **save document as pdf**.

```python
# Define the output path – replace YOUR_DIRECTORY with an actual folder
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)
print(f"PDF saved to {output_path}")
```

När du öppnar `shadow_rectangle.pdf` kommer du att se en enda sida som innehåller en grå‑ramad rektangel med titeln “Shadow demo” och en skarp, diagonal skugga.

### Förväntat resultat

* En PDF‑fil med namnet `shadow_rectangle.pdf`.
* En sida med en 200 pt × 100 pt rektangel.
* En synlig skugga med offset 5 pt i en 45° vinkel, oskärpt med 8 pt.

## Steg 5: Utforska variationer och kantfall (valfritt)

Nedan följer vanliga justeringar du kan behöva i verkliga projekt:

| Variation | Kodsnutt | När den ska användas |
|-----------|----------|----------------------|
| **Olika formtyp** (t.ex. ellips) | `aw.drawing.ShapeType.OVAL` instead of `RECTANGLE` | För rundade grafik eller märken |
| **Anpassad skuggfärg** | `shadow.color = aw.drawing.Color.from_argb(255, 100, 100, 100)` | När en grå eller varumärkes‑specifik skugga krävs |
| **Flera former** | Repeat the shape‑creation block and adjust `left`/`top` properties | För att bygga komplexa diagram |
| **Ingen text i formen** | Omit `rectangle.text = "..."` | När formen är enbart dekorativ |
| **Högre DPI‑utdata** | `doc.save(output_path, aw.SaveFormat.PDF, aw.PdfSaveOptions())` with `PdfSaveOptions` set for image quality | För utskriftsklara PDF‑filer |

**Proffstips:** Sätt alltid `shadow.visible = True` innan du justerar andra egenskaper; annars ignoreras ändringarna tyst.

## Fullt skript – kopiera, klistra in och kör

```python
import aspose.words as aw

# 1️⃣ Create a new blank document
doc = aw.Document()

# 2️⃣ Add a rectangle shape
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
rectangle.width = 200          # width in points
rectangle.height = 100         # height in points
rectangle.text = "Shadow demo"

# 3️⃣ Configure a visible shadow effect
shadow = rectangle.shadow_effect
shadow.visible = True
shadow.blur = 8                # blur radius (pt)
shadow.distance = 5            # offset distance (pt)
shadow.angle = 45              # direction (degrees)
shadow.color = aw.drawing.Color.black

# 4️⃣ Save the document as a PDF
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)

print(f"PDF successfully created at: {output_path}")
```

Kör skriptet från din terminal eller IDE. Ersätt `YOUR_DIRECTORY` med en riktig sökväg, till exempel `"/tmp"` eller `"C:\\Users\\Me\\Documents"`.

## Slutsats

Du vet nu hur du **draw rectangle in PDF** med Aspose.Words för Python, **add shadow to shape**, **configure shape shadow** och **save document as PDF**. Det kompletta exemplet visar varje steg från dokumentskapande till slutlig export, och de valfria variationerna visar hur du anpassar koden för mer komplexa scenarier.

Nästa steg kan vara att utforska:

* Att lägga till andra formtyper (`ShapeType.LINE`, `ShapeType.ELLIPSE`).
* Att applicera gradientfyllningar eller kanter för att förbättra det visuella intrycket.
* Att använda `PdfSaveOptions` för att bädda in typsnitt eller kontrollera bildkomprimering.

Känn dig fri att experimentera med parametrarna för att matcha ditt varumärke eller dina designriktlinjer. Lycka till med PDF‑skriptning!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Optimera PDF-bokmärken med Aspose.Words för Python](/words/english/python-net/performance-optimization/optimize-pdf-bookmarks-aspose-words-python/)
- [Optimera PDF‑laddning i Python med Aspose Words – Hoppa över bilder](/words/hindi/python-net/performance-optimization/optimize-pdf-loading-python-aspose-words-skip-images/)
- [Aspose Words Python PDF‑manipulering](/words/hongkong/python-net/document-operations/aspose-words-python-pdf-manipulation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}