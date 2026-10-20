---
category: general
date: 2026-06-30
description: Voeg een schaduw toe aan een vorm met Aspose.Words voor Python. Leer
  hoe je de schaduwafstand instelt, de vervaging aanpast en snel een PDF met vormschaduw
  opslaat.
draft: false
keywords:
- add shadow to shape
- how to set shadow distance
- how to add shape shadow
- Aspose.Words Python shadow
- shape formatting Python
language: nl
og_description: Schaduw toevoegen aan een vorm in een Word‑document met Aspose.Words
  voor Python. Deze tutorial laat zien hoe je de schaduwafstand, vervaging en kleur
  instelt en vervolgens opslaat als PDF.
og_title: Schaduw toevoegen aan vorm in Python – Complete Aspose.Words-gids
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Add shadow to shape using Aspose.Words for Python. Learn how to set
    shadow distance, customize blur, and save a PDF with shape shadow quickly.
  headline: Add Shadow to Shape in Python with Aspose.Words – Full Guide
  type: TechArticle
- description: Add shadow to shape using Aspose.Words for Python. Learn how to set
    shadow distance, customize blur, and save a PDF with shape shadow quickly.
  name: Add Shadow to Shape in Python with Aspose.Words – Full Guide
  steps:
  - name: What if I need a different shape?
    text: Replace `aw.drawing.ShapeType.RECTANGLE` with any other enum value, e.g.,
      `aw.drawing.ShapeType.ELLIPSE`. The same shadow properties apply—no extra code
      needed.
  - name: Can I apply a shadow to multiple shapes at once?
    text: 'Yes. Loop over the shapes you create and configure each `shadow_format`
      individually. Here’s a quick snippet:'
  - name: How do I change the shadow’s opacity?
    text: 'Use the `shadow.transparency` property (0 = opaque, 1 = fully transparent):'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: Schaduw toevoegen aan vorm in Python met Aspose.Words – Volledige gids
url: /nl/python/images-shapes/add-shadow-to-shape-in-python-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Schaduw toevoegen aan vorm in Python met Aspose.Words – Volledige gids

Schaduw toevoegen aan een vorm in een Word‑document met Aspose.Words voor Python is makkelijker dan je denkt. Als je je ooit hebt afgevraagd **hoe je de schaduwdistance instelt** of **hoe je een vormschaduw toevoegt** voor een gepolijste uitstraling, dan biedt deze gids alles wat je nodig hebt.

In de komende paar minuten lopen we alles door wat je nodig hebt: van het maken van een nieuw document, het invoegen van een rechthoek, het aanpassen van de schaduweigenschappen, tot het uiteindelijk opslaan van een PDF die het effect laat zien. Aan het einde kun je een schaduw op elke vorm – rechthoek, ellips of aangepaste tekening – toepassen zonder door de API‑documentatie te hoeven graven.

> **Prerequisites** – Je moet Python 3.7+ geïnstalleerd hebben, een Aspose.Words for Python‑licentie (of een gratis evaluatie), en een basiskennis van Python‑scripting. Er zijn geen andere externe bibliotheken nodig.

---

## Schaduw toevoegen aan vorm – Stapsgewijs overzicht

Hieronder een snel overzicht van wat we gaan doen:

1. **Maak een nieuw document** en een `DocumentBuilder` om het te bewerken.  
2. **Voeg een rechthoekvorm** toe van de gewenste grootte.  
3. **Schakel de schaduw in en pas deze aan** – hier komt het belangrijkste trefwoord om de hoek.  
4. **Sla het document op** als een PDF die de schaduw van de vorm behoudt.

Elke stap staat in een eigen sectie, zodat je de code‑fragmenten direct kunt kopiëren‑plakken in je IDE.

---

## Stap 1: Initialiseer het document en de builder

Allereerst—zonder een `Document` heb je niets om aan te werken. De `DocumentBuilder` is je penseel.

```python
import aspose.words as aw

# Create a new, empty Word document
document = aw.Document()

# Attach a builder to the document for easy editing
builder = aw.DocumentBuilder(document)
```

*Waarom dit belangrijk is*: Het `Document`‑object vertegenwoordigt het volledige bestand, terwijl de `DocumentBuilder` het invoegen van tekst, tabellen en vormen vereenvoudigt. Beschouw de builder als een cursor die je over de pagina kunt verplaatsen.

---

## Stap 2: Rechthoekvorm invoegen

Nu voegen we een rechthoek toe — ons canvas voor het schaduweffect. Je kunt `RECTANGLE` vervangen door `ELLIPSE`, `STAR` of een andere `ShapeType` als je een andere geometrie nodig hebt.

```python
# Insert a rectangle with width=200pt and height=100pt
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

*Pro tip*: De afmetingen zijn in points (1 pt ≈ 1/72 inch). Pas ze aan om bij je lay‑out te passen; de schaduw schaalt automatisch.

---

## Hoe schaduwdistance instellen

De **distance** van de schaduw bepaalt hoe ver deze van de vorm af lijkt te staan. Een grotere afstand bootst een lichtbron die verder weg staat, terwijl een kleinere waarde een subtiele lift geeft.

```python
# Access the shadow format of the shape
shadow = rectangle_shape.shadow_format

# Make the shadow visible
shadow.visible = True

# Set the distance (in points) from the shape
shadow.distance = 4.0          # <-- this is the "how to set shadow distance" part
```

> **Note**: De distance werkt samen met `angle`. Het wijzigen van de hoek draait de schaduw rond de vorm, terwijl `distance` deze naar buiten duwt.

---

## Hoe vormschaduw toevoegen – Blur, kleur en hoek aanpassen

Een schaduw toevoegen gaat niet alleen om het inschakelen; je wilt vaak blur, kleur en richting afstemmen voor een realistisch effect.

```python
# Define how blurry the shadow should be (larger = softer)
shadow.blur_radius = 5.0       # Soft edge for a natural look

# Choose the direction (in degrees). 45° points down‑right.
shadow.angle = 45

# Set the shadow color – black works for most cases
shadow.color = aw.drawing.Color.black
```

*Waarom deze instellingen?*  
- **Blur radius** verzacht de rand, waardoor een harde silhouet wordt voorkomen.  
- **Angle** simuleert de lichtbron; 45° is een veelgebruikt standaard dat er evenwichtig uitziet.  
- **Color** kan elk `Color`‑object zijn; probeer `Color.gray` voor een zachter effect.

---

## Stap 4: Het document opslaan als PDF

Zodra de vorm en de schaduw klaar zijn, is het opslaan een fluitje van een cent. Aspose.Words handelt de conversie naar PDF automatisch af en behoudt de visuele kwaliteit.

```python
# Save the document to a PDF file (adjust the path as needed)
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
document.save(output_path)
print(f"Document saved to {output_path}")
```

*Verwacht resultaat*: Open de gegenereerde `ShadowShape.pdf`. Je ziet een enkele pagina met een rechthoek van 200 × 100 pt, waarvan de schaduw 4 pt verwijderd is onder een hoek van 45°, vervaagd met 5 pt. De schaduw verschijnt als een subtiele grijs‑zwarte halo rondom de vorm.

---

## Veelgestelde vragen & randgevallen

### Wat als ik een andere vorm nodig heb?

Vervang `aw.drawing.ShapeType.RECTANGLE` door een andere enum‑waarde, bijvoorbeeld `aw.drawing.ShapeType.ELLIPSE`. Dezelfde schaduweigenschappen gelden — geen extra code nodig.

### Kan ik een schaduw op meerdere vormen tegelijk toepassen?

Ja. Loop over de vormen die je maakt en configureer elk `shadow_format` afzonderlijk. Hier is een kort fragment:

```python
for shape_type in [aw.drawing.ShapeType.RECTANGLE, aw.drawing.ShapeType.ELLIPSE]:
    shp = builder.insert_shape(shape_type, 150, 80)
    shp.shadow_format.visible = True
    shp.shadow_format.distance = 3.0
    shp.shadow_format.blur_radius = 4.0
```

### Hoe wijzig ik de doorzichtigheid van de schaduw?

Gebruik de eigenschap `shadow.transparency` (0 = ondoorzichtig, 1 = volledig transparant):

```python
shadow.transparency = 0.3   # 30 % transparent
```

---

## Volledig werkend voorbeeld

Hieronder staat het complete script — kopieer het, pas de output‑map aan, en voer het uit. Er ontbreken geen onderdelen.

```python
import aspose.words as aw

# 1️⃣ Create a new document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert a rectangle shape (200 × 100 pt)
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Enable and configure the shadow (add shadow to shape)
shadow = rectangle_shape.shadow_format
shadow.visible = True                # Show the shadow
shadow.blur_radius = 5.0             # Soft edges
shadow.distance = 4.0                # How far the shadow lies from the shape
shadow.angle = 45                    # Direction of the light source
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.0            # Fully opaque (optional)

# 4️⃣ Save as PDF
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
document.save(output_path)
print(f"PDF with shape shadow saved at: {output_path}")
```

Voer het script uit en open vervolgens de resulterende PDF. Je zou de rechthoek moeten zien met een scherpe, verschoven schaduw — precies wat **add shadow to shape** belooft.

---

## Conclusie

We hebben zojuist laten zien hoe je **schaduw toevoegt aan een vorm** in een Word‑document met Aspose.Words voor Python, waarbij we de essentiële stappen hebben behandeld om **schaduwdistance in te stellen**, blur, hoek en kleur aan te passen, en uiteindelijk een PDF te exporteren die het effect behoudt. Deze techniek werkt voor elk type vorm, en je kunt het uitbreiden met lussen, doorzichtigheidsaanpassingen of zelfs gradient‑schaduwen.

Klaar voor de volgende uitdaging? Probeer meerdere schaduwen te combineren, vormen te stapelen, of een rapport te genereren waarbij elke grafiek zijn eigen gestileerde schaduw krijgt. Experimenteren verankert de concepten en onthult nieuwe mogelijkheden voor documentautomatisering.

Als je deze gids nuttig vond, deel hem dan, geef een ster aan de Aspose.Words‑repository, of laat een reactie achter met je eigen tips voor het afstemmen van schaduwen. Veel programmeerplezier!

## Wat kun je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Aspose.Words Shape Shadow Tutorial – Voeg een schaduw toe aan Word‑vorm in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Rechthoekvorm maken in Word met Aspose.Words – Stapsgewijze gids](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Groepsvorm maken in Word‑document met Aspose.Words voor .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}