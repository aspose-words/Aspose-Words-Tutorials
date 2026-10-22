---
category: general
date: 2026-10-07
description: Leer hoe u een document als PDF opslaat terwijl u een rechthoekvorm en
  aangepaste schaduw toevoegt met Aspose.Words voor Python. Stap‑voor‑stap code inbegrepen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save document as pdf
- add rectangle shape
- export word to pdf
- set rectangle dimensions
- draw rectangle word
language: nl
lastmod: 2026-10-07
og_description: Sla document op als PDF met een aangepaste rechthoekvorm met Aspose.Words
  voor Python. Volg het volledige voorbeeld om Word te tekenen, te stijlen en te exporteren
  naar PDF.
og_image_alt: Screenshot of the generated PDF showing the rectangle shape after save
  document as pdf
og_title: Document opslaan als PDF met een rechthoekvorm – volledige Python‑gids
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  headline: How to save document as PDF with a custom rectangle shape in Python
  type: TechArticle
- description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  name: How to save document as PDF with a custom rectangle shape in Python
  steps:
  - name: Initialize a new blank document
    text: '```python import aspose.words as aw'
  - name: Add rectangle shape to the document
    text: '```python # Create a rectangle shape and attach it to the document. rectangle
      = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)'
  - name: Set rectangle dimensions
    text: '```python # Define width and height in points (1 point = 1/72 inch). rectangle.width
      = 200 # 200 points ≈ 2.78 inches rectangle.height = 100 # 100 points ≈ 1.39
      inches ```'
  - name: (Optional) Apply a visible custom shadow
    text: '```python shadow = rectangle.shadow_format shadow.visible = True # Show
      the shadow shadow.blur = 5.0 # Softness of the shadow edge shadow.distance =
      3.0 # How far the shadow is offset shadow.angle = 45 # Direction in degrees
      shadow.color = aw.drawing.Color.black ```'
  - name: Save document as PDF
    text: '```python output_path = "output/shadow_rectangle.pdf" document.save(output_path)
      print(f"PDF saved to {output_path}") ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Word automation
title: Hoe een document opslaan als PDF met een aangepaste rechthoekvorm in Python
url: /nl/python/document-conversion/how-to-save-document-as-pdf-with-a-custom-rectangle-shape-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een document opslaan als PDF met een aangepaste rechthoekvorm in Python

Als je een **document wilt opslaan als PDF** terwijl je aangepaste graphics toevoegt, laat deze gids je zien hoe. We lopen door het maken van een leeg Word‑bestand, **een rechthoekvorm tekenen**, de grootte instellen, een zichtbare schaduw toepassen, en uiteindelijk **Word exporteren naar PDF** met de Aspose.Words for Python‑bibliotheek.

Je eindigt met een PDF die een perfect gepositioneerde rechthoek bevat, klaar voor rapporten, facturen of elke document‑automatiseringsscenario. Er zijn geen externe tools nodig—alleen Python en het Aspose.Words‑pakket.

## Wat je nodig hebt

| Vereiste | Waarom het belangrijk is |
|----------|--------------------------|
| Python 3.8+ | De Aspose.Words for Python API richt zich op moderne interpreters. |
| `aspose-words` package (`pip install aspose-words`) | Levert de `aw` namespace die in de code‑voorbeelden wordt gebruikt. |
| Basiskennis van Python en object‑georiënteerd programmeren | De tutorial manipuleert objecten zoals `Document` en `Shape`. |
| Schrijfrechten voor een map waar de PDF wordt opgeslagen | De stap `save document as pdf` schrijft een bestand naar de schijf. |

> **Pro tip:** Gebruik een virtuele omgeving (`python -m venv venv`) om afhankelijkheden geïsoleerd te houden.

## Hoe een document opslaan als PDF met een rechthoekvorm

Hieronder staat een volledig, uitvoerbaar voorbeeld. Elke stap wordt uitgelegd zodat je begrijpt **waarom** we de actie uitvoeren, en niet alleen **wat** de code doet.

### Stap 1: Een nieuw leeg document initialiseren

```python
import aspose.words as aw

# Create an empty Word document – this is the canvas for our shape.
document = aw.Document()
```

Het maken van een nieuw `Document`‑object geeft je een schone paginaverzameling. Je kunt ook een bestaand *.docx* laden als je later **Word wilt exporteren naar PDF**, maar beginnen met een leeg document houdt het voorbeeld gefocust.

### Stap 2: Een rechthoekvorm aan het document toevoegen

```python
# Create a rectangle shape and attach it to the document.
rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

# The shape must be placed inside a paragraph before it appears.
paragraph = document.first_section.body.first_paragraph
paragraph.append_child(rectangle)
```

De stap `add rectangle shape` gebruikt `ShapeType.RECTANGLE`. Door de vorm aan een alinea toe te voegen, weet Aspose.Words waar het moet renderen in de uiteindelijke PDF.

### Stap 3: De afmetingen van de rechthoek instellen

```python
# Define width and height in points (1 point = 1/72 inch).
rectangle.width = 200   # 200 points ≈ 2.78 inches
rectangle.height = 100  # 100 points ≈ 1.39 inches
```

Het expliciet instellen van **rechthoekafmetingen** zorgt ervoor dat de vorm er consistent uitziet op verschillende platforms. Je kunt ook `convert_to_inches`‑helpers gebruiken als je de imperiale eenheden verkiest.

### Stap 4: (Optioneel) Een zichtbare aangepaste schaduw toepassen

```python
shadow = rectangle.shadow_format
shadow.visible = True          # Show the shadow
shadow.blur = 5.0              # Softness of the shadow edge
shadow.distance = 3.0          # How far the shadow is offset
shadow.angle = 45              # Direction in degrees
shadow.color = aw.drawing.Color.black
```

Een schaduw laat de rechthoek opvallen in de PDF. De `shadow.visible`‑vlag is vereist; zonder deze hebben de andere eigenschappen geen effect.

### Stap 5: Document opslaan als PDF

```python
output_path = "output/shadow_rectangle.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Het aanroepen van `document.save` met een **.pdf**‑extensie slaat automatisch **document op als pdf** op met de ingebouwde PDF‑renderer van Aspose.Words. Er zijn geen extra conversiestappen nodig, daarom is deze methode de aanbevolen manier om **Word te exporteren naar PDF**.

> **Waarom dit werkt:** Aspose.Words schrijft de lay-out van het document, inclusief de rechthoek en zijn schaduw, direct naar de PDF‑stroom. Het proces is verliesvrij en behoudt vectorkwaliteit.

## Volledige broncode (enkel script)

```python
import aspose.words as aw

def create_pdf_with_rectangle(output_path: str):
    """
    Creates a PDF that contains a single rectangle shape with a custom shadow.
    The function demonstrates:
    • add rectangle shape
    • set rectangle dimensions
    • export Word to PDF (save document as pdf)
    """
    # 1️⃣ Create a new blank document
    document = aw.Document()

    # 2️⃣ Insert a rectangle shape
    rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

    # 3️⃣ Set the shape's size
    rectangle.width = 200   # points
    rectangle.height = 100  # points

    # 4️⃣ Configure a visible shadow
    shadow = rectangle.shadow_format
    shadow.visible = True
    shadow.blur = 5.0
    shadow.distance = 3.0
    shadow.angle = 45
    shadow.color = aw.drawing.Color.black

    # 5️⃣ Add shape to the first paragraph
    paragraph = document.first_section.body.first_paragraph
    paragraph.append_child(rectangle)

    # 6️⃣ Save the document as PDF
    document.save(output_path)
    print(f"PDF successfully saved to: {output_path}")

if __name__ == "__main__":
    create_pdf_with_rectangle("output/shadow_rectangle.pdf")
```

Het uitvoeren van dit script produceert `shadow_rectangle.pdf` die er als volgt uitziet:

![Diagram van de gegenereerde PDF die de rechthoekvorm toont na het opslaan van het document als pdf](placeholder-image.png)

*De PDF bevat één pagina met een zwart‑schaduwde rechthoek gecentreerd in het document.*

## Veelgestelde vragen en randgevallen

| Vraag | Antwoord |
|-------|----------|
| **Kan ik de rechthoek op een specifieke locatie plaatsen?** | Ja. Stel `rectangle.left` en `rectangle.top` (in points) in vóór het opslaan. |
| **Wat als ik meerdere vormen nodig heb?** | Maak extra `Shape`‑objecten, configureer elk, en voeg ze toe aan dezelfde of verschillende alinea's. |
| **Heeft de schaduw invloed op de PDF‑grootte?** | Alleen marginaal; de schaduw wordt opgeslagen als vectormetadata, niet als rasterafbeelding. |
| **Kan ik dit gebruiken om bestaande *.docx*‑bestanden te converteren?** | Absoluut. Vervang `aw.Document()` door `aw.Document("input.docx")` en de rest van de stappen blijven ongewijzigd. |
| **Is er een manier om de vulkleur van de rechthoek te wijzigen?** | Stel `rectangle.fill_color = aw.drawing.Color.light_blue` in (of elke `Color` die je verkiest). |

## Volgende stappen

Nu je weet hoe je **document kunt opslaan als PDF** met een aangepaste rechthoek, kun je het volgende verkennen:

* **Word exporteren naar PDF** met kopteksten, voetteksten en paginanummers.  
* **Andere tekenobjecten toevoegen** (`Ellipse`, `Polygon`) met dezelfde `Shape`‑klasse.  
* **Batch‑verwerking** van een map met Word‑bestanden, waarbij dezelfde rechthoek‑overlay op elk wordt toegepast.  

Deze uitbreidingen volgen hetzelfde patroon: maak een vorm, configureer de eigenschappen, en **document opslaan als pdf**.

---

**Samenvatting:** Deze tutorial liet zien hoe je **document kunt opslaan als PDF** terwijl je **een rechthoekvorm toevoegt**, **de rechthoekafmetingen instelt**, en een aangepaste schaduw toepast met Aspose.Words voor Python. Het volledige script is klaar om te kopiëren, uit te voeren en aan te passen aan je eigen document‑automatiseringspijplijnen. Veel plezier met coderen!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Rechthoekvorm maken, schaduw toevoegen & PDF opslaan](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Rechthoek toevoegen aan PDF met Aspose.Words – Stapsgewijze gids](/words/english/python-net/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/)
- [Document opslaan als PDF met Aspose.Words – Complete C#‑gids](/words/english/net/programming-with-pdfsaveoptions/save-document-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}