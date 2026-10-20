---
category: general
date: 2026-05-04
description: Leer hoe je een rechthoekvorm maakt, hoe je een vorm met schaduwen toevoegt,
  de schaduwkleur wijzigt, de schaduwafstand instelt en het document opslaat als PDF
  met Aspose.Words voor Python.
draft: false
keywords:
- create rectangle shape
- how to add shape
- change shadow color
- save document as pdf
- set shadow distance
language: nl
og_description: Maak een rechthoekvorm met Aspose.Words voor Python, leer hoe je een
  vorm toevoegt, de schaduwkleur wijzigt, de schaduwafstand instelt en het document
  opslaat als PDF.
og_title: Maak rechthoekvorm – Voeg schaduw toe, wijzig kleur & sla op als PDF
tags:
- Aspose.Words
- Python
- PDF generation
title: Rechthoekvorm maken in Python – Complete gids voor het toevoegen van schaduwen
  en opslaan als PDF
url: /nl/python/images-shapes/create-rectangle-shape-in-python-full-guide-to-adding-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechthoekvorm maken – Complete tutorial voor Python‑ontwikkelaars

Heb je ooit **een rechthoekvorm** moeten maken in een Word‑document en je afgevraagd hoe je er een gepolijste schaduw aan kunt geven? Misschien bouw je een rapportgenerator en is de visuele afwerking belangrijk—vooral wanneer de uiteindelijke output een PDF is. Het goede nieuws? Met Aspose.Words for Python kun je niet alleen **hoe je een vorm toevoegt** maar ook elke schaduweigenschap aanpassen, van kleur tot afstand, en vervolgens **het document opslaan als pdf** in één vloeiende workflow.

In deze gids lopen we stap voor stap het volledige proces door. Je ziet de exacte code die je kunt copy‑paste, begrijpt *waarom* elke regel belangrijk is, en krijgt een paar tips voor het omgaan met randgevallen (zoals transparante schaduwen of niet‑standaard DPI). Aan het einde kun je **een rechthoekvorm maken**, de schaduw aanpassen en een scherp PDF‑bestand exporteren zonder enige moeite.

## Vereisten

- Python 3.8+ geïnstalleerd op je machine.  
- Aspose.Words for Python via `pip install aspose-words`.  
- Basiskennis van object‑georiënteerd Python (niets geavanceerd).  

Als je al een virtuele omgeving hebt opgezet, voer dan gewoon het install‑commando uit en je bent klaar om te gaan.

## Stap 1: Initialiseer het document en de builder

Voordat je **hoe je een vorm toevoegt** kunt doen, heb je een leeg document nodig om mee te werken. De `Document`‑klasse vertegenwoordigt het hele bestand, en `DocumentBuilder` is je penseel.

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder to edit it
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

*Waarom dit belangrijk is:* `Document` bevat alle secties, pagina's en bronnen. `DocumentBuilder` biedt je een vloeiende API om inhoud precies op de gewenste plaats in te voegen—denk aan een cursor in een tekstverwerker.

## Stap 2: Voeg de rechthoekvorm in

Nu voegen we daadwerkelijk **hoe je een vorm toevoegt**. De `insert_shape`‑methode heeft het vormtype en de afmetingen (in punten) nodig. Hier kiezen we een rechthoek van 200 × 100 pt en geven we deze een lichtblauwe vulling.

```python
# Step 2: Insert a rectangle shape and give it a light‑blue fill
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,  # shape type
    200,                            # width in points
    100)                            # height in points
rectangle_shape.fill_color = aw.Color.light_blue
```

*Pro tip:* Als je de vorm wilt uitlijnen met bestaande tekst, gebruik dan `builder.move_to` vóór het invoegen, of pas de `left`/`top`‑eigenschappen aan na creatie.

## Stap 3: Schakel de schaduw in

Een vorm zonder schaduw ziet er plat uit. Om **de schaduwafstand in te stellen** en het effect zichtbaar te maken, haal je het schaduwformaat op en schakel je het in.

```python
# Step 3: Access the shape's shadow format and make the shadow visible
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
```

*Waarom deze stap:* Het schaduwformaat is een apart object; het schakelen van `visible` is het eerste wat je moet doen, anders worden alle andere schaduweigenschappen genegeerd.

## Stap 4: Style de schaduw – Kleur, Vervaging, Afstand, Richting

Hier gebeurt de magie. We zullen **de schaduwkleur wijzigen**, de vervagingsradius aanpassen, instellen hoe ver de schaduw van de rechthoek af staat, en deze 45° draaien.

```python
# Step 4: Configure the appearance of the shadow
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER   # outer shadow
rectangle_shadow.blur_radius = 10.0                    # blur amount (pixels)
rectangle_shadow.distance = 5.0                        # distance from the shape
rectangle_shadow.direction = 45.0                     # angle in degrees
rectangle_shadow.color = aw.Color.gray                 # shadow colour
```

*Uitleg van elke eigenschap:*

| Property | Wat het doet | Typische waarden |
|----------|--------------|------------------|
| `style` | Bepaalt of de schaduw *inner* of *outer* is. | `OUTER` (meest gebruikelijk) |
| `blur_radius` | Regelt de zachtheid; hoger = wazigere randen. | 0–20 px is gebruikelijk |
| `distance` | Hoe ver de schaduw van de vorm is verschoven. | 0–10 pt voor subtiel, >10 voor dramatisch |
| `direction` | Hoek van de lichtbron, gemeten met de klok mee vanaf de x‑as. | 0‑360° |
| `color` | Kleur van de schaduw. | Elke `aw.Color` (bijv. `gray`, `dark_red`) |

*Randgeval:* Als je `distance` op `0` zet, zal de schaduw direct onder de vorm liggen, waardoor de vulling van de vorm effectief wordt verborgen. Houd het boven `0` voor een zichtbaar offset.

## Stap 5: Sla het document op als PDF

Tot slot **slaan we het document op als pdf**. Aspose.Words rasteriseert de schaduw automatisch, zodat de PDF er precies uitziet als de weergave in Word.

```python
# Step 5: Save the document as a PDF with the shadowed shape
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

*Waarom PDF?* PDF's behouden de lay-out op alle platformen, waardoor ze perfect zijn voor rapporten, facturen of elk afdrukbaar document.

---

![Rechthoekvorm maken met schaduw](https://example.com/images/rectangle-shadow.png){: .align-center alt="voorbeeld van rechthoekvorm met schaduw"}

*De bovenstaande afbeelding toont de uiteindelijke PDF‑output – een lichtblauwe rechthoek met een zachte grijze buitenste schaduw, precies zoals we hebben geconfigureerd.*

## Veelgestelde vragen & variaties

### Wat als ik een **transparante** schaduw nodig heb?

Stel het alfakanaal in op de schaduwkleur:

```python
transparent_gray = aw.Color.from_argb(128, 0, 0, 0)  # 50% opacity black
rectangle_shadow.color = transparent_gray
```

### Kan ik dezelfde schaduw op meerdere vormen toepassen?

Ja. Haal de `ShadowFormat` van één vorm op en wijs deze toe aan een andere:

```python
another_shape = builder.insert_shape(aw.drawing.ShapeType.ELLIPSE, 150, 150)
another_shape.shadow_format = rectangle_shadow.clone()
```

### Hoe wijzig ik de schaduw voor een **ander vormtype**?

Alle vormtypen delen dezelfde `ShadowFormat`‑eigenschappen, dus je kunt hetzelfde configuratie‑blok hergebruiken—vervang gewoon `ShapeType.RECTANGLE` door `ShapeType.OVAL`, `ShapeType.TRIANGLE`, enz.

### Wat betreft **high‑resolution PDF's** voor afdrukken?

Specificeer de `PdfSaveOptions` met een hogere DPI:

```python
options = aw.saving.PdfSaveOptions()
options.image_resolution = 300  # 300 DPI for print quality
document.save(output_path, options)
```

## Samenvatting

We hebben alles behandeld wat je nodig hebt om **een rechthoekvorm te maken**, **hoe je een vorm toevoegt**, de **schaduwkleur** aan te passen, **de schaduwafstand in te stellen**, en uiteindelijk **het document op te slaan als pdf**. Het volledige, uitvoerbare script ziet er als volgt uit:

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

Voer het script uit, open de resulterende `ShadowedShape.pdf`, en je ziet een scherpe rechthoek met een subtiele grijze schaduw—precies wat je zou verwachten van een professioneel opgemaakt rapport.

## Wat nu?

- **Verken andere vormtypen** (`ShapeType.OVAL`, `ShapeType.LINE`) om je documenten te verrijken.  
- **Combineer meerdere schaduwen** door vormen te stapelen; je kunt zelfs een “gloed”‑effect creëren door een innerlijke schaduw met een heldere kleur te gebruiken.  
- **Automatiseer batchverwerking**: loop over een verzameling gegevensrijen, genereer een vorm per rij, en voeg alles samen in één PDF.  
- **Integreer met andere Aspose‑bibliotheken** (bijv. Aspose.Slides) als je dezelfde visualisatie naar PowerPoint moet exporteren.

Voel je vrij om te experimenteren—verander de `blur_radius`, speel met `direction`, of vervang `gray` door een merk‑specifieke tint. De API is flexibel genoeg zodat een paar aanpassingen de visuele impact drastisch kunnen veranderen.

Heb je vragen of een lastig scenario? Laat een reactie achter hieronder of ping de Aspose‑communityforums. Veel plezier met coderen, en geniet van die prachtig gearceerde rechthoeken!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}