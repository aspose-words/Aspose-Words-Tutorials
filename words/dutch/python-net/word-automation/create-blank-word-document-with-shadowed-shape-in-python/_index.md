---
category: general
date: 2026-10-16
description: Maak een leeg Word‑document, voeg een vorm in Word in, voeg een buitenschaduw
  toe en sla op als PDF met Python.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert shape in word
- save as pdf python
- add outer shadow shape
- create pdf with shape
language: nl
lastmod: 2026-10-16
og_description: Maak een leeg Word‑document met een buitenschaduwvorm met behulp van
  Aspose.Words voor Python. Deze gids laat zien hoe je de vorm invoegt, de schaduw
  toepast en het bestand opslaat als PDF.
og_image_alt: Screenshot of a Word document containing a rectangle shape with an outer
  shadow, saved as PDF
og_title: Maak een leeg Word‑document met vormschaduw – Python‑gids
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
title: Maak een leeg Word‑document met een vorm met schaduw in Python
url: /nl/python/word-automation/create-blank-word-document-with-shadowed-shape-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak een leeg Word‑document met een vorm met schaduw in Python

Als je een **leeg Word‑document wilt maken** en een aangepaste grafiek wilt toevoegen, dan biedt deze gids alles wat je nodig hebt. We lopen stap voor stap door hoe je een **vorm in Word invoegt**, een **buitenste schaduw aan de vorm toepast**, en uiteindelijk **opslaat als PDF met Python**.

Je leert hoe je Aspose.Words voor Python instelt, een rechthoek bouwt, de schaduw ervan stijlt, en een PDF genereert die het visuele effect behoudt. Er is geen voorafgaande ervaring met de Aspose‑API vereist, maar je moet basiskennis van Python hebben en een werkende installatie van Python 3.10 of hoger.

## Vereisten

* Python 3.10 of nieuwer geïnstalleerd.
* Een actieve Aspose.Words voor Python‑licentie (een gratis proefversie werkt voor evaluatie).
* `pip`‑toegang om het `aspose-words`‑pakket te installeren.
* Schrijfrechten voor de map waarin de PDF wordt opgeslagen.

Je kunt de bibliotheek met één commando installeren:

```bash
pip install aspose-words
```

## Maak een leeg Word‑document – omgeving instellen

De eerste stap is het maken van een leeg Word‑bestand dat dient als canvas voor de vorm.

```python
import aspose.words as aw

# Initialize a new, empty document
doc = aw.Document()
# DocumentBuilder provides convenient methods for adding content
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` vertegenwoordigt een volledig leeg Word‑bestand. Door `DocumentBuilder` te gebruiken krijg je toegang tot methoden zoals `insert_shape`, die we in de volgende stap zullen gebruiken.

## Vorm invoegen in Word en afmetingen instellen

Nu voegen we een rechthoek toe die later een buitenste schaduw krijgt. De grootte wordt uitgedrukt in punten (1 pt ≈ 1/72 inch).

```python
# Insert a rectangle shape with a width of 200 pt and a height of 100 pt
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)
```

De `insert_shape`‑aanroep retourneert een `Shape`‑object dat je verder kunt aanpassen. Op dit punt bevat het document al een zichtbare rechthoek wanneer het wordt geopend in Microsoft Word.

## Buitenste schaduw toevoegen – het effect aanpassen

Aspose.Words biedt een `ShadowEffect`‑klasse om schaduweigenschappen zoals stijl, vervaging, afstand en kleur te definiëren.

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

Het instellen van `style` op `OUTER` zorgt ervoor dat de schaduw buiten de rand van de rechthoek verschijnt, waardoor een subtiele 3‑D‑look ontstaat. Je kunt experimenteren met `blur` en `distance` om een strakkere of meer diffuse schaduw te krijgen.

## Opslaan als PDF met Python – het document afronden

Na het stijlen van de vorm kan het document direct als PDF worden opgeslagen. Aspose.Words verwerkt de conversie intern en behoudt het schaduweffect.

```python
output_path = "output/shape_with_shadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Wanneer je `shape_with_shadow.pdf` opent in een PDF‑viewer, zie je de rechthoek met de buitenste schaduw precies zoals deze in Word verscheen.

## Volledig werkend voorbeeld

Hieronder staat het volledige script dat alle stappen combineert. Kopieer het naar een bestand met de naam `create_word_with_shadow.py` en voer het uit.

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

**Verwachte output**

Het uitvoeren van het script geeft een bevestigingsregel weer, bijvoorbeeld:

```
PDF generated at: output/shape_with_shadow.pdf
```

Het openen van de resulterende PDF toont een enkele pagina met een 200 pt × 100 pt‑rechthoek met een zachte zwarte buitenste schaduw.

## Veelvoorkomende variaties en randgevallen

* **Changing shadow color** – Vervang `aw.Color.black` door een andere `aw.Color`‑waarde, zoals `aw.Color.red` of `aw.Color.from_argb(255, 0, 120, 215)`.
* **Using a different shape** – Verander `aw.drawing.ShapeType.RECTANGLE` in `OVAL`, `DIAMOND` of een andere ondersteunde enum‑waarde.
* **Saving as DOCX instead of PDF** – Roep `doc.save("output/shape.docx")` aan om het Word‑formaat te behouden.
* **Multiple shapes** – Maak extra vormen door opnieuw `builder.insert_shape` aan te roepen; elke vorm kan zijn eigen `ShadowEffect` hebben.

**Pro tip:** Als je de vorm op een specifieke locatie wilt plaatsen, stel dan `rectangle.left` en `rectangle.top` in na het invoegen. Dit geeft je pixel‑perfecte controle over de plaatsing.

## Conclusie

Je weet nu hoe je een **leeg Word‑document maakt**, een **vorm in Word invoegt**, een **buitenste schaduw aan de vorm toevoegt**, en **opslaat als PDF met Python**. Het volledige code‑voorbeeld toont de end‑to‑end‑workflow, en de uitleg verduidelijkt waarom elke API‑aanroep nodig is.

Vanaf hier kun je meer geavanceerde stijlopties verkennen, tekst binnen de vorm toevoegen, of meerdere vormen combineren om complexe diagrammen te bouwen. Experimenteer met verschillende schaduwparameters om ze af te stemmen op de visuele taal van je merk, en integreer deze aanpak in grotere document‑generatie‑pijplijnen.

Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Rechthoekvorm maken, schaduw toevoegen & PDF opslaan](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [PDF maken vanuit Word – Complete Python‑gids met Aspose.Words](/words/english/python-net/document-conversion/create-pdf-from-word-complete-python-guide-with-aspose-words/)
- [Schaduw toevoegen aan vorm in Word met Aspose.Words – Stap‑voor‑stap](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}