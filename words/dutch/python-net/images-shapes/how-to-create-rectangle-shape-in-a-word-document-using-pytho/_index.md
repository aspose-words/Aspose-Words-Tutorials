---
category: general
date: 2026-09-30
description: Leer hoe je een rechthoekvorm maakt, een schaduw op de vorm toepast en
  Word met de vorm opslaat met Aspose.Words voor Python.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- how to add shape
- apply shadow to shape
- set shadow blur
- save word with shape
language: nl
lastmod: 2026-09-30
og_description: Maak snel een rechthoekvorm in een Word‑document. Deze tutorial laat
  zien hoe je een vorm toevoegt, schaduw op de vorm toepast, de schaduwvervaging instelt
  en Word opslaat met de vorm.
og_image_alt: Screenshot of a Word document showing a rectangle shape with a soft
  shadow
og_title: Maak een rechthoekvorm in Word met Python – stap‑voor‑stap gids
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Learn how to create rectangle shape, apply shadow to shape, and save
    Word with shape using Aspose.Words for Python.
  headline: How to create rectangle shape in a Word document using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- Shapes
title: Hoe maak je een rechthoekvorm in een Word‑document met Python
url: /nl/python/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een rechthoekvorm te maken in een Word‑document met Python

Als je een **rechthoekvorm** in een Word‑bestand moet **maken**, laat deze gids je een volledige, uitvoerbare oplossing zien. Je ziet hoe je de vorm toevoegt, een schaduweffect toepast, de vervaging aanpast en uiteindelijk **Word met vorm opslaat** zodat het resultaat kan worden geopend in Microsoft Word of een compatibele viewer.

Het voorbeeld maakt gebruik van **Aspose.Words for Python via .NET**, een bibliotheek die je in staat stelt Word‑documenten te manipuleren zonder Microsoft Office geïnstalleerd te hebben. Er is geen voorafgaande ervaring met de API vereist – alleen basiskennis van Python.

## Wat je zult bereiken

- Een rechthoek invoegen in de eerste sectie van een nieuw document.  
- Een zachte schaduw configureren door de vervaging, offset en kleur in te stellen.  
- Het document opslaan op schijf en het visuele resultaat verifiëren.

## Vereisten

- Python 3.8 of nieuwer.  
- `aspose-words`‑pakket geïnstalleerd (`pip install aspose-words`).  
- Schrijfrechten voor de uitvoermap.

## Rechthoekvorm maken en het uiterlijk configureren

De eerste stap is een leeg document aanmaken en een rechthoekvorm toevoegen. De vorm dient als canvas voor het schaduweffect.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Step 1: Create a new blank document
doc = aw.Document()

# Step 2: Add a rectangle shape to the first section
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Optional: Define the shape’s size and position (in points)
shape.width = aw.ConvertUtil.inch_to_point(2)   # 2 inches wide
shape.height = aw.ConvertUtil.inch_to_point(1)  # 1 inch tall
shape.left = aw.ConvertUtil.inch_to_point(1)    # 1 inch from the left margin
shape.top = aw.ConvertUtil.inch_to_point(1)     # 1 inch from the top margin
```

**Waarom dit belangrijk is:**  
Het maken van de rechthoek geeft je een concreet object (`shape`) dat je later kunt stijlen. Expliciete afmetingen zorgen ervoor dat de vorm er op elk platform hetzelfde uitziet.

## Hoe een vorm aan een Word‑document toe te voegen

Hoewel de bovenstaande code de rechthoek al toevoegt, moet je later mogelijk extra vormen (bijv. cirkels, pijlen) toevoegen. Hetzelfde patroon geldt: roep `append_child` aan op de body van het document en geef het gewenste `ShapeType` door.

```python
# Example: Adding a second shape – an ellipse
ellipse = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.ELLIPSE)
)
ellipse.width = aw.ConvertUtil.inch_to_point(1.5)
ellipse.height = aw.ConvertUtil.inch_to_point(1)
ellipse.left = aw.ConvertUtil.inch_to_point(3.5)
ellipse.top = aw.ConvertUtil.inch_to_point(1)
```

**Tip:** Gebruik de `ShapeType`‑enumeratie om alle ondersteunde vormen te verkennen. Dit houdt je code leesbaar en voorkomt “magic numbers”.

## Schaduw toepassen op de vorm en schaduwvervaging instellen

Een schaduw voegt diepte en visueel belang toe. De `ShadowEffect`‑klasse laat je vervaging, offset en kleur regelen. Hieronder passen we een zachte zwarte schaduw toe op de rechthoek.

```python
# Step 3: Configure a shadow effect for the rectangle
shadow = ShadowEffect()
shadow.blur = 5.0          # Sets the softness of the shadow edge
shadow.offset_x = 2.0      # Horizontal displacement from the shape
shadow.offset_y = 2.0      # Vertical displacement from the shape
shadow.color = aw.Color.black

# Step 4: Apply the shadow effect to the shape
shape.shadow = shadow
```

**Waarom vervaging instellen?**  
`blur` bepaalt hoe diffuus de schaduw verschijnt. Een lage waarde (bijv. 1.0) geeft een scherpe rand, terwijl een hogere waarde (bijv. 5.0) een zachte overgang creëert, wat vaak esthetischer is.

**Randgeval:** Als je `blur` op 0 zet, wordt de schaduw een solide silhouet. Sommige viewers kunnen dit weergeven met alias‑artefacten, dus kies een waarde groter dan 0 voor een vloeiender resultaat.

## Word met vorm opslaan

Het document opslaan maakt alle wijzigingen definitief. De `save`‑methode schrijft een `.docx`‑bestand dat elke moderne tekstverwerker kan openen.

```python
# Step 5: Save the document to see the result
output_path = "output.docx"   # Adjust the path as needed
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Wanneer je `output.docx` opent, zie je een rechthoek die één inch van de linkerbovenhoek is gepositioneerd, met een zachte zwarte schaduw die twee punten naar rechts en omlaag is verplaatst. De vervaging van de schaduw laat de vorm lijken alsof deze van de pagina is opgetild.

**Pro‑tip:** Als je veel documenten in een lus moet genereren, hergebruik dan dezelfde `Document`‑instantie en maak de body tussen iteraties leeg om het geheugenverbruik te verminderen.

## Veelvoorkomende variaties en probleemoplossing

| Situatie | Wat te wijzigen | Reden |
|-----------|----------------|--------|
| Andere schaduwkleur | `shadow.color = aw.Color.red` | Gebruik merkkleuren of markeer belangrijke vormen. |
| Grotere schaduwoffset | Verhoog `shadow.offset_x`/`offset_y` | Benadruk diepte voor UI‑mock‑ups. |
| Geen schaduw | Laat de regel `shape.shadow = shadow` weg | Handig voor minimalistische rapporten. |
| Exporteren naar PDF in plaats van DOCX | `doc.save("output.pdf")` | PDF is ideaal voor alleen‑lezen distributie. |

Als de vorm niet verschijnt, controleer dan of je deze toevoegt aan de juiste sectie (`get_first_section()`) en of het document is opgeslagen na de wijzigingen.

## Volledig, uitvoerbaar voorbeeld

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Create a new blank document
doc = aw.Document()

# Add a rectangle shape
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
shape.width = aw.ConvertUtil.inch_to_point(2)
shape.height = aw.ConvertUtil.inch_to_point(1)
shape.left = aw.ConvertUtil.inch_to_point(1)
shape.top = aw.ConvertUtil.inch_to_point(1)

# Configure and apply a shadow
shadow = ShadowEffect()
shadow.blur = 5.0
shadow.offset_x = 2.0
shadow.offset_y = 2.0
shadow.color = aw.Color.black
shape.shadow = shadow

# Save the document
output_path = "output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Het uitvoeren van het script produceert `output.docx` met de rechthoek en een zachte schaduw. Open het bestand in Microsoft Word om te bevestigen dat het visuele effect overeenkomt met de beschrijving.

## Conclusie

Je weet nu hoe je **een rechthoekvorm maakt**, **een vorm toevoegt** aan een Word‑document, **schaduw toepast op een vorm**, **schaduwvervaging instelt**, en uiteindelijk **Word met vorm opslaat** met Aspose.Words for Python. Hetzelfde patroon kan worden uitgebreid naar andere vormtypen, kleuren en effecten, waardoor je volledige controle krijgt over documentgrafieken zonder afhankelijk te zijn van Office‑automatisering.

**Volgende stappen**

- Experimenteer met `Shape.fill` om gradient‑ of afbeeldingsachtergronden toe te voegen.  
- Gebruik `Paragraph`‑objecten om tekst binnen de rechthoek te plaatsen.  
- Combineer meerdere vormen om complexe diagrammen te bouwen en exporteer vervolgens naar PDF voor distributie.  

Voel je vrij om de code aan te passen aan je eigen rapportage‑ of templating‑behoeften, en deel je resultaten in de reacties!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}