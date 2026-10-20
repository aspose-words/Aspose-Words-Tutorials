---
category: general
date: 2026-05-04
description: Lär dig hur du skapar en rektangelform, hur du lägger till en form med
  skuggor, ändrar skuggfärgen, ställer in skuggavståndet och sparar dokumentet som
  PDF med Aspose.Words för Python.
draft: false
keywords:
- create rectangle shape
- how to add shape
- change shadow color
- save document as pdf
- set shadow distance
language: sv
og_description: Skapa en rektangelform med Aspose.Words för Python, lär dig hur du
  lägger till en form, ändrar skuggfärgen, ställer in skuggavståndet och sparar dokumentet
  som PDF.
og_title: Skapa rektangelform – Lägg till skugga, ändra färg och spara som PDF
tags:
- Aspose.Words
- Python
- PDF generation
title: Skapa rektangelform i Python – Fullständig guide för att lägga till skuggor
  och spara som PDF
url: /sv/python/images-shapes/create-rectangle-shape-in-python-full-guide-to-adding-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa rektangelform – Komplett handledning för Python‑utvecklare

Har du någonsin behövt **create rectangle shape** i ett Word‑dokument och undrat hur du ger det en polerad skugga? Kanske bygger du en rapportgenerator och den visuella poleringen är viktig—särskilt när slutresultatet är en PDF. Den goda nyheten? Med Aspose.Words för Python kan du inte bara **how to add shape** utan också justera varje skuggegenskap, från färg till avstånd, och sedan **save document as pdf** i ett smidigt flöde.

I den här guiden går vi igenom hela processen steg för steg. Du kommer att se den exakta koden du kan kopiera‑klistra in, förstå *why* varje rad är viktig, och få några tips för att hantera kantfall (som transparenta skuggor eller icke‑standard DPI). I slutet kommer du att kunna **create rectangle shape**, anpassa dess skugga och exportera en skarp PDF utan att svettas.

## Förutsättningar

- Python 3.8+ installerat på din maskin.  
- Aspose.Words for Python via `pip install aspose-words`.  
- Grundläggande kunskap om objekt‑orienterad Python (inget avancerat).  

Om du redan har en virtuell miljö konfigurerad, kör bara installationskommandot så är du klar.

## Steg 1: Initiera dokumentet och byggaren

Innan du kan **how to add shape** behöver du ett tomt dokument att arbeta med. Klassen `Document` representerar hela filen, och `DocumentBuilder` är din pensel.

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder to edit it
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

*Varför detta är viktigt:* `Document` innehåller alla sektioner, sidor och resurser. `DocumentBuilder` ger dig ett flytande API för att infoga innehåll exakt där du behöver det—tänk på det som en markör i en ordbehandlare.

## Steg 2: Infoga rektangelformen

Nu **how to add shape** på riktigt. Metoden `insert_shape` kräver formtypen och dess dimensioner (i punkter). Här väljer vi en 200 × 100 pt rektangel och ger den en ljusblå fyllning.

```python
# Step 2: Insert a rectangle shape and give it a light‑blue fill
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,  # shape type
    200,                            # width in points
    100)                            # height in points
rectangle_shape.fill_color = aw.Color.light_blue
```

*Proffstips:* Om du behöver att formen ska justeras med befintlig text, använd `builder.move_to` innan du infogar, eller justera egenskaperna `left`/`top` efter skapandet.

## Steg 3: Aktivera skuggan

En form utan skugga ser platt ut. För att **set shadow distance** och göra effekten synlig, hämta skuggeformatet och aktivera det.

```python
# Step 3: Access the shape's shadow format and make the shadow visible
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
```

*Varför detta steg:* Skuggeformatet är ett separat objekt; att växla `visible` är det första du måste göra, annars ignoreras alla andra skuggegenskaper.

## Steg 4: Styla skuggan – Färg, oskärpa, avstånd, riktning

Det är här magin sker. Vi kommer att **change shadow color**, justera oskärpe‑radien, ange hur långt skuggan sitter från rektangeln, och rotera den 45°.

```python
# Step 4: Configure the appearance of the shadow
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER   # outer shadow
rectangle_shadow.blur_radius = 10.0                    # blur amount (pixels)
rectangle_shadow.distance = 5.0                        # distance from the shape
rectangle_shadow.direction = 45.0                     # angle in degrees
rectangle_shadow.color = aw.Color.gray                 # shadow colour
```

*Förklaring av varje egenskap:*

| Egenskap | Vad den gör | Vanliga värden |
|----------|--------------|----------------|
| `style` | Bestämmer om skuggan är *inner* eller *outer*. | `OUTER` (vanligast) |
| `blur_radius` | Kontrollerar mjukhet; högre = suddigare kanter. | 0–20 px är vanligt |
| `distance` | Hur långt skuggan är förskjuten från formen. | 0–10 pt för subtil, >10 för dramatisk |
| `direction` | Vinkel på ljuskällan, mätt medurs från x‑axeln. | 0‑360° |
| `color` | Skuggans nyans. | Valfri `aw.Color` (t.ex. `gray`, `dark_red`) |

*Kantfall:* Om du sätter `distance` till `0` kommer skuggan att ligga direkt under formen, vilket i praktiken döljer formens fyllning. Håll den över `0` för ett synligt förskjutning.

## Steg 5: Spara dokumentet som PDF

Till sist **save document as pdf**. Aspose.Words rasteriserar automatiskt skuggan, så PDF‑filen ser exakt likadan ut som Word‑vyn.

```python
# Step 5: Save the document as a PDF with the shadowed shape
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

*Varför PDF?* PDF‑filer bevarar layout över plattformar, vilket gör dem perfekta för rapporter, fakturor eller andra utskrivbara artefakter.

---

![Skapa rektangelform med skugga](https://example.com/images/rectangle-shadow.png){: .align-center alt="exempel på rektangelform med skugga"}

*Bilden ovan visar den slutgiltiga PDF‑utmatningen – en ljusblå rektangel med en mjuk grå yttre skugga, exakt som vi konfigurerade.*

## Vanliga frågor & variationer

### Vad händer om jag behöver en **transparent** skugga?

Ställ in alfa‑kanalen på skuggans färg:

```python
transparent_gray = aw.Color.from_argb(128, 0, 0, 0)  # 50% opacity black
rectangle_shadow.color = transparent_gray
```

### Kan jag applicera samma skugga på flera former?

Ja. Extrahera `ShadowFormat` från en form och tilldela den till en annan:

```python
another_shape = builder.insert_shape(aw.drawing.ShapeType.ELLIPSE, 150, 150)
another_shape.shadow_format = rectangle_shadow.clone()
```

### Hur ändrar jag skuggan för en **annan formtyp**?

Alla formtyper delar samma `ShadowFormat`‑egenskaper, så du kan återanvända samma konfigurationsblock—byt bara ut `ShapeType.RECTANGLE` mot `ShapeType.OVAL`, `ShapeType.TRIANGLE` osv.

### Vad sägs om **högresolutio​​ns‑PDF‑filer** för utskrift?

Ange `PdfSaveOptions` med en högre DPI:

```python
options = aw.saving.PdfSaveOptions()
options.image_resolution = 300  # 300 DPI for print quality
document.save(output_path, options)
```

## Sammanfattning

Vi har gått igenom allt du behöver för att **create rectangle shape**, **how to add shape**, anpassa dess **shadow colour**, **set shadow distance**, och slutligen **save document as pdf**. Det kompletta, körbara skriptet ser ut så här:

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

Kör skriptet, öppna den resulterande `ShadowedShape.pdf`, och du kommer att se en skarp rektangel med en subtil grå skugga—precis vad du förväntar dig av en professionellt formaterad rapport.

## Vad blir nästa steg?

- **Utforska andra formtyper** (`ShapeType.OVAL`, `ShapeType.LINE`) för att berika dina dokument.  
- **Kombinera flera skuggor** genom att lagerlägga former; du kan till och med skapa en “glöd‑”effekt genom att använda en inre skugga med en ljus färg.  
- **Automatisera batch‑behandling**: loopa över en samling datarader, generera en form per rad och slå ihop allt till en enda PDF.  
- **Integrera med andra Aspose‑bibliotek** (t.ex. Aspose.Slides) om du behöver exportera samma visualisering till PowerPoint.

Känn dig fri att experimentera—ändra `blur_radius`, lek med `direction`, eller byt ut `gray` mot en varumärkes‑specifik nyans. API‑et är tillräckligt flexibelt så att några få justeringar kan förändra den visuella effekten dramatiskt.

Har du frågor eller ett knepigt scenario? Lämna en kommentar nedanför eller kontakta Aspose‑community‑forumet. Lycka till med kodningen, och njut av de vackert skuggade rektanglarna!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}