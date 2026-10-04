---
category: general
date: 2026-10-04
description: Hoe een document te maken in Python en een schaduw toe te voegen aan
  een vorm met Aspose.Words. Leer hoe je de schaduwkleur instelt, een rechthoekige
  vorm invoegt en de buitenste schaduw aanpast.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create document
- add shadow to shape
- set shadow color
- insert rectangle shape
- how to add shadow
language: nl
lastmod: 2026-10-04
og_description: Hoe een document te maken in Python en een schaduw aan een vorm toe
  te voegen. Deze gids laat zien hoe je de schaduwkleur instelt, een rechthoekvorm
  invoegt en een buitenschaduw toepast met Aspose.Words.
og_image_alt: Python code inserting a rectangle shape with a visible shadow into a
  Word document
og_title: Hoe maak je een document met een rechthoekvorm en schaduw in Python
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  headline: How to create document with a rectangle shape and shadow in Python
  type: TechArticle
- description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  name: How to create document with a rectangle shape and shadow in Python
  steps:
  - name: Why does the shadow sometimes appear invisible?
    text: The shadow is only rendered if `shadow.visible` is set to `True` **and**
      the shape’s `wrap_type` allows it to be displayed. An inline shape works reliably;
      floating shapes may require additional layout adjustments.
  - name: How can I change the shadow color to match a brand palette?
    text: 'Replace `aw.drawing.Color.black` with a custom RGB value:'
  - name: What if I need the shape to appear behind text?
    text: Set the wrap type to `WrapType.BEHIND` and adjust the `z_order_position`
      if necessary. Keep in mind that some viewers may render behind‑text shapes differently.
  - name: Can I apply the same shadow settings to multiple shapes?
    text: Yes. Create a helper function that configures the shadow and call it for
      each shape you insert. This promotes code reuse and ensures consistent styling.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Hoe maak je een document met een rechthoekvorm en schaduw in Python
url: /nl/python/images-shapes/how-to-create-document-with-a-rectangle-shape-and-shadow-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een document met een rechthoekige vorm en schaduw te maken in Python

Als je **hoe een document te maken** nodig hebt dat een gestylede rechthoek bevat, biedt deze gids een volledige oplossing. Je ziet hoe je **schaduw aan vorm toevoegt**, de kleur van de schaduw instelt en de offset en vervaging ervan regelt — allemaal met Aspose.Words for Python. Aan het einde van de tutorial kun je een `.docx`‑bestand genereren dat er gepolijst uitziet en klaar is voor distributie.

De stappen hieronder behandelen alles, van het installeren van de bibliotheek tot het aanpassen van het uiterlijk van de schaduw. Er is geen externe documentatie nodig; de code is klaar om te kopiëren, uit te voeren en aan je eigen projecten aan te passen. Je leert ook hoe je **rechthoekige vorm invoegt**, een **outer shadow‑stijl** kiest en veelvoorkomende valkuilen zoals onzichtbare schaduwen of onjuiste wrap‑instellingen aanpakt.

## Vereisten

* Python 3.8 of nieuwer geïnstalleerd.
* Een actieve Aspose.Words for Python‑licentie (of een gratis evaluatiesleutel).
* Basiskennis van Python‑scripting.
* Toegang tot een bestandslocatie waar het gegenereerde document wordt opgeslagen.

Je kunt de SDK installeren met pip:

```bash
pip install aspose-words
```

## Stap 1: Importeer de bibliotheek en maak een nieuw leeg document

Het maken van een nieuw document is de eerste handeling in elk Word‑automatiseringsscenario. De `aw.Document()`‑constructor geeft je een leeg bestand dat je kunt vullen met tekst, afbeeldingen of vormen.

```python
import aspose.words as aw

# Create a new blank document
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

Het `DocumentBuilder`‑object vereenvoudigt het invoegen van inhoud. Het houdt de huidige cursorpositie bij, zodat je elementen opeenvolgend kunt toevoegen zonder handmatig secties te beheren.

## Stap 2: Voeg een rechthoekige vorm van de gewenste grootte in

Een rechthoekige vorm dient als container voor visuele elementen. Je kunt de breedte en hoogte definiëren in punten (1 pt ≈ 1/72 in).

```python
# Insert a rectangle shape that is 150 pt wide and 80 pt tall
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

Op dit moment heeft de vorm geen visuele opmaak, dus verschijnt hij als een eenvoudige omtrek. De volgende stappen geven hem diepte en kleur.

## Stap 3: Stel de vorm in om inline te vloeien met de omringende tekst

Wanneer een vorm **inline** is, gedraagt ze zich als een teken in een alinea. Dit zorgt ervoor dat de rechthoek blijft waar je hem verwacht in de documentlay-out.

```python
# Make the shape inline so it follows the text flow
rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE
```

Als je de vorm liever zwevend boven de tekst wilt hebben, kun je `WrapType.SQUARE` of `WrapType.TOP_BOTTOM` gebruiken, maar voor de meeste rapporten houdt een inline‑vorm de lay-out voorspelbaar.

## Stap 4: Maak de schaduw zichtbaar en kies de kleur

Een schaduw die niet zichtbaar is, levert geen visueel voordeel op. Het `visible`‑vlaggetje activeert het effect, en de `color`‑eigenschap bepaalt de tint. Zwart geeft een klassieke, subtiele diepte.

```python
# Enable the shadow and set its color to black
rectangle_shape.shadow.visible = True
rectangle_shape.shadow.color = aw.drawing.Color.black
```

Je kunt `aw.drawing.Color.black` vervangen door elke andere kleur, zoals `aw.drawing.Color.gray` of een aangepaste RGB‑waarde (`aw.drawing.Color.from_argb(255, 128, 128, 128)`).

## Stap 5: Definieer de offset en vervaging van de schaduw om diepte te geven

De offset bepaalt hoe ver de schaduw van de vorm wordt verplaatst, terwijl de vervagingsradius de randen verzacht. Kleine waarden creëren een scherpe schaduw; grotere waarden geven een zachtere uitstraling.

```python
# Horizontal and vertical offset of 5 pt each
rectangle_shape.shadow.offset_x = 5
rectangle_shape.shadow.offset_y = 5

# Blur radius of 3 pt for a gentle feather
rectangle_shape.shadow.blur = 3
```

Experimenteer met deze getallen om aan je ontwerprichtlijnen te voldoen. Voor een zware dropschaduw kun je zowel offset als blur verhogen.

## Stap 6: Kies een outer shadow‑stijl

Aspose.Words biedt verschillende schaduwstijlen, zoals `INNER`, `OUTER` en `PERSPECTIVE`. De **outer**‑stijl plaatst de schaduw buiten de rand van de vorm, wat ideaal is voor een nette, professionele uitstraling.

```python
# Apply an outer shadow style
rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

Als je een dramatischer effect wilt, probeer dan `ShadowStyle.PERSPECTIVE` — het voegt een driedimensionale kanteling toe.

## Stap 7: Sla het document op met de vorm met schaduw

Opslaan finaliseert het bestand en schrijft alle opmaak naar schijf. Kies een map waarvoor je schrijfrechten hebt en geef het bestand een beschrijvende naam.

```python
# Save the document to the desired location
output_path = "output/ShapeWithShadow.docx"
document.save(output_path)
print(f"Document saved to {output_path}")
```

Het uitvoeren van het script levert een Word‑bestand op dat een rechthoek bevat met een zichtbare, gekleurde schaduw. Open het bestand in Microsoft Word of LibreOffice om het resultaat te verifiëren.

## Volledig uitvoerbaar voorbeeld

Hieronder staat het volledige script dat elke besproken stap combineert. Kopieer de code naar een bestand genaamd `create_shadowed_shape.py` en voer het uit met `python create_shadowed_shape.py`.

```python
import aspose.words as aw
import os

def main():
    # Ensure the output directory exists
    output_dir = "output"
    os.makedirs(output_dir, exist_ok=True)

    # Step 1: Create a new blank document
    document = aw.Document()
    builder = aw.DocumentBuilder(document)

    # Step 2: Insert a rectangle shape of the desired size
    rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

    # Step 3: Set the shape to be inline with the text flow
    rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE

    # Step 4: Make the shadow visible and choose its color
    rectangle_shape.shadow.visible = True
    rectangle_shape.shadow.color = aw.drawing.Color.black

    # Step 5: Define the shadow's offset and blur to give it depth
    rectangle_shape.shadow.offset_x = 5   # horizontal offset in points
    rectangle_shape.shadow.offset_y = 5   # vertical offset in points
    rectangle_shape.shadow.blur = 3       # blur radius in points

    # Step 6: Choose an outer shadow style
    rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER

    # Step 7: Save the document with the shaped shadow
    output_path = os.path.join(output_dir, "ShapeWithShadow.docx")
    document.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    main()
```

**Verwachte output**

Wanneer je `ShapeWithShadow.docx` opent, zie je een enkele rechthoek gecentreerd op de pagina. De rechthoek wordt vergezeld door een subtiele zwarte schaduw die naar rechtsonder is verplaatst en licht vervaagd is om diepte te creëren. De schaduw respecteert de outer‑stijl, zodat hij niet in het interieur van de rechthoek intersecteert.

## Veelgestelde vragen en randgevallen

### Waarom verschijnt de schaduw soms onzichtbaar?

De schaduw wordt alleen gerenderd als `shadow.visible` is ingesteld op `True` **en** het `wrap_type` van de vorm het weergeven toestaat. Een inline‑vorm werkt betrouwbaar; zwevende vormen kunnen extra lay‑out‑aanpassingen vereisen.

### Hoe kan ik de schaduwkleur aanpassen aan een merkkleurenpalet?

Vervang `aw.drawing.Color.black` door een aangepaste RGB‑waarde:

```python
rectangle_shape.shadow.color = aw.drawing.Color.from_argb(255, 0, 120, 215)  # corporate blue
```

### Wat als ik wil dat de vorm achter de tekst verschijnt?

Stel het wrap‑type in op `WrapType.BEHIND` en pas eventueel de `z_order_position` aan. Houd er rekening mee dat sommige viewers vormen achter de tekst anders kunnen weergeven.

### Kan ik dezelfde schaduwinstellingen toepassen op meerdere vormen?

Ja. Maak een hulpfunctie die de schaduw configureert en roep deze aan voor elke vorm die je invoegt. Dit bevordert code‑hergebruik en zorgt voor consistente styling.

```python
def apply_shadow(shape, color=aw.drawing.Color.black, offset=5, blur=3):
    shape.shadow.visible = True
    shape.shadow.color = color
    shape.shadow.offset_x = offset
    shape.shadow.offset_y = offset
    shape.shadow.blur = blur
    shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

## Conclusie

Je weet nu **hoe een document te maken** dat een rechthoekige vorm met een aangepaste schaduw bevat, met behulp van Aspose.Words for Python. De tutorial behandelde het invoegen van een rechthoek, het inline maken van de vorm, het inschakelen van de schaduw, het instellen van de kleur, offset, blur en stijl, en tenslotte het opslaan van het bestand.

Vanaf hier kun je gerelateerde onderwerpen verkennen, zoals **schaduw aan vorm toevoegen** voor andere vormtypen, **schaduwkleur instellen** dynamisch op basis van gegevens, of **hoe schaduw toe te voegen** aan afbeeldingen en tekstvakken. Experimenteer met verschillende afmetingen, kleuren en schaduwstijlen om aan je merkrichtlijnen of design‑systeem te voldoen.

Klaar om meer Word‑documenten te automatiseren? Probeer tabellen, kopteksten of dynamische inhoud toe te voegen — elke stap bouwt voort op dezelfde principes die hier zijn gedemonstreerd. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/) – *Rechthoekige vorm maken, schaduw toevoegen & PDF opslaan*
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/) – *Leeg Word‑document maken met rechthoekige vorm met schaduw – Stapsgewijze gids*
- [How to Manage Document Variables with Aspose.Words in Python&#58; A Complete Guide](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/) – *Hoe documentvariabelen te beheren met Aspose.Words in Python: Een volledige gids*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}