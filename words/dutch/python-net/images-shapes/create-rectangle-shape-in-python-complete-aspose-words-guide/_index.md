---
category: general
date: 2026-06-24
description: Maak een rechthoekvorm in Python met Aspose.Words, leer hoe je een schaduw
  aan de vorm toevoegt, de schaduwhoek instelt en het document binnen enkele minuten
  als PDF opslaat.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shape shadow
- set shadow angle
language: nl
og_description: Maak een rechthoekvorm in Python, voeg een schaduw toe aan de vorm,
  stel de schaduwhoek in en sla het document op als PDF met Aspose.Words. Volg deze
  stapsgewijze handleiding.
og_title: Rechthoekvorm maken in Python – Volledige Aspose.Words tutorial
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
title: Rechthoekvorm maken in Python – Complete Aspose.Words-gids
url: /nl/python/images-shapes/create-rectangle-shape-in-python-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechthoekvorm maken in Python – Complete Aspose.Words‑gids

Heb je je ooit afgevraagd hoe je **een rechthoekvorm** in een Word‑document kunt **maken** met Python? Misschien heb je een opvallende call‑out‑box nodig, een visuele aanwijzing voor een diagram, of gewoon een mooie rechthoek voor een rapport. Hoe het ook zij, je bent op de juiste plek. In deze tutorial lopen we het volledige proces door – van het invoegen van de rechthoek, tot het toevoegen van een subtiele schaduw, het aanpassen van de schaduwhoek, en uiteindelijk **het document opslaan als PDF** zodat je het met iedereen kunt delen.

We gebruiken **Aspose.Words for Python via .NET**, een krachtige bibliotheek waarmee je Word‑bestanden kunt manipuleren zonder Word zelf te openen. Aan het einde van deze gids kun je vol vertrouwen de vraag *“hoe voeg ik een vormschaduw toe”* beantwoorden, en heb je een kant‑klaar script dat je in elk project kunt gebruiken.

---

## Wat je nodig hebt

Voordat we beginnen, zorg dat je het volgende hebt:

- **Python 3.8+** geïnstalleerd op je machine.  
- **Aspose.Words for Python via .NET** (`aspose-words`‑package). Installeer het met:

  ```bash
  pip install aspose-words
  ```

- Een schrijfbare map waar de gegenereerde PDF wordt opgeslagen.  
- (Optioneel) Een IDE of teksteditor – VS Code werkt uitstekend.

Dat is alles. Geen extra DLL‑s, geen Office‑installatie, alleen één pip‑package.

---

## Stap 1: Document en Builder instellen

Het eerste wat je moet doen is **rechthoekvorm‑vriendelijke** objecten maken: een `Document` en een `DocumentBuilder`. Beschouw de builder als je pen; hij tekent alles voor je.

```python
import aspose.words as aw

# Initialize a new blank document
document = aw.Document()

# DocumentBuilder gives us a convenient way to add content
builder = aw.DocumentBuilder(document)
```

> **Waarom dit belangrijk is:** Het `Document`‑object vertegenwoordigt het volledige .docx‑bestand, terwijl de `DocumentBuilder` methoden biedt zoals `insert_shape` die het tekenen van vormen een fluitje van een cent maken.

---

## Stap 2: De rechthoekvorm invoegen

Nu we een builder hebben, kunnen we eindelijk **een rechthoekvorm maken**. De methode `insert_shape` vereist drie argumenten: het vormtype, de breedte en de hoogte. We gebruiken een breedte van 200 pt en een hoogte van 100 pt voor een mooie proportie.

```python
# Insert a rectangle with a width of 200 points and a height of 100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

Op dit punt heb je met succes **een rechthoekvorm gemaakt** in je document. Als je later het gegenereerde DOCX‑bestand opent (dat doen we later), zie je een eenvoudige rechthoek op de plek waar de cursor stond.

---

## Stap 3: Toegang krijgen tot het schaduw‑opmaakobject

Om **schaduw aan een vorm toe te voegen**, moeten we eerst de schaduw‑opmaak van de vorm ophalen. Elke vorm in Aspose.Words heeft een `shadow_format`‑eigenschap die alle schaduw‑gerelateerde instellingen blootlegt.

```python
# Grab the shadow formatting object for later tweaks
shadow = rectangle.shadow_format
```

Met de `shadow`‑referentie kunnen we zichtbaarheid, vervaging, afstand, hoek, kleur en transparantie in een paar regels code in- en uitschakelen.

---

## Stap 4: Schaduw inschakelen en uiterlijk configureren

Hier gebeurt de magie. We **voegen schaduw toe aan de vorm**, maken deze licht vervaagd, verschuiven hem een beetje, stellen de richting in (het **instellen van de schaduwhoek**‑deel), en geven hem een halfdoorzichtige zwarte tint.

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

> **Pro‑tip:** Als je een dramatischer effect wilt, verhoog dan `blur_radius` of verlaag `transparency`. Omgekeerd kun je een scherpe, volledig ondoorzichtige schaduw krijgen met `blur_radius = 0` en `transparency = 0`.

---

## Stap 5: Het document opslaan als PDF

We hebben **een rechthoekvorm gemaakt**, we hebben **schaduw aan de vorm toegevoegd**, en nu **slaan we het document op als PDF** zodat het resultaat er op elk apparaat identiek uitziet. Aspose.Words maakt dit een één‑regelige opdracht.

```python
# Define where you want the PDF to land
output_path = "output/shadowed_rectangle.pdf"

# Save the whole document (including the rectangle with its shadow) as PDF
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Het uitvoeren van het script genereert `shadowed_rectangle.pdf` in de map `output`. Open het met een PDF‑viewer en je ziet een nette rechthoek met een zachte, 45‑graden schaduw – precies zoals we hebben geconfigureerd.

---

## Volledig werkend voorbeeld

Hieronder vind je het complete, kant‑klaar script dat alle bovenstaande stappen combineert. Kopieer‑en‑plak het in een bestand met de naam `create_rectangle_with_shadow.py` en voer `python create_rectangle_with_shadow.py` uit.

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

**Verwacht resultaat:** Een PDF‑bestand met één rechthoek en een zachte, diagonale schaduw. Geen extra pagina’s, geen verborgen artefacten – alleen de vorm die we hebben gemaakt.

---

## Veelgestelde vragen & randgevallen

### Wat als ik een andere vorm nodig heb?

Aspose.Words ondersteunt veel `ShapeType`‑waarden (ellipse, ster, callout, enz.). Vervang simpelweg `aw.drawing.ShapeType.RECTANGLE` door de gewenste enum, bijvoorbeeld `aw.drawing.ShapeType.ELLIPSE`.

### Kan ik meerdere schaduwen toevoegen?

De API biedt slechts één `ShadowFormat` per vorm, maar je kunt meerdere schaduwen simuleren door de vorm te dupliceren, elke kopie te verschuiven en de transparantie aan te passen.

### Hoe wijzig ik de schaduwkleur zodat deze bij mijn merk past?

Stel gewoon `shadow.color` in op een willekeurige `aw.drawing.Color`. Voor een merk‑blauw gebruik je `aw.drawing.Color.from_argb(255, 0, 120, 215)`.

### Wat als ik wil opslaan als DOCX in plaats van PDF?

Vervang `document.save(pdf_path)` door `document.save("output/shadowed_rectangle.docx")`. De schaduwweergave blijft behouden in beide formaten.

### Werkt de schaduw in oudere PDF‑viewers?

Aspose.Words rendert de schaduw als een vector‑effect, wat breed ondersteund wordt. Zeer oude viewers kunnen het effect echter flatten; testen op de apparaten van je doelgroep blijft een goede gewoonte.

---

## Tips om je PDF te verfijnen

- **Rand toevoegen:** `rectangle.line_format.width = 1.5` en een kleur instellen voor een scherpe omlijning.  
- **De rechthoek centreren:** Gebruik `builder.move_to_document_start()` vóór het invoegen, daarna `builder.paragraph_format.alignment = aw.ParagraphAlignment.CENTER`.  
- **Combineren met tekst:** Voeg een `TextFragment` toe na de rechthoek om deze te labelen, bijvoorbeeld `"Belangrijke sectie"`.

Deze kleine aanpassingen kunnen van een eenvoudige rechthoek een gepolijste call‑out‑box maken die er professioneel uitziet in rapporten, voorstellen of e‑books.

---

## Conclusie

Je beschikt nu over een solide, end‑to‑end‑recept om **een rechthoekvorm te maken** in Python, **schaduw aan de vorm toe te voegen**, **de schaduwhoek in te stellen**, en **het document op te slaan als PDF** met Aspose.Words. De stappen zijn duidelijk, de code is volledig zelfstandig, en je hebt gezien waarom elke regel belangrijk is – van het initialiseren van het document tot het perfectioneren van de uiteindelijke PDF.

Vervolgens kun je **verkennen hoe je vormschaduw toevoegt** aan complexere tekeningen, experimenteren met gradient‑vullingen, of tabellen binnen je vormen genereren. De bibliotheek ondersteunt ook het koppelen van vormen aan bladwijzers, wat handig kan zijn voor interactieve PDF‑s.

Heb je een eigen twist geprobeerd? Deel het in de reacties, of stel je resterende vragen. Veel programmeerplezier, en geniet van die extra diepte in je documenten! 

![Rectangle shape with shadow – example of create rectangle shape in Python](/images/rectangle-shadow.png)


## Wat kun je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementaties in je eigen projecten te verkennen.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}