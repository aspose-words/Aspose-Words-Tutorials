---
category: general
date: 2026-11-25
description: Schaduw toevoegen aan een vorm in een Word‑document met Python. Leer
  hoe je een rechthoekvorm in Word invoegt en een transparante schaduw toepast met
  Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- insert rectangle shape word
- how to create word document python
- Aspose.Words Python
- shape formatting Python
language: nl
lastmod: 2026-11-25
og_description: Voeg een schaduw toe aan een vorm in een Word‑document met Python.
  Deze tutorial laat zien hoe je een rechthoekvorm in Word invoegt en een 30 % transparante
  schaduw instelt met Aspose.Words.
og_image_alt: Add shadow to shape example in a Word document created by Python
og_title: Schaduw toevoegen aan vorm in een Word‑document met Python – stapsgewijze
  handleiding
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Add shadow to shape in a Word document with Python. Learn how to insert
    rectangle shape in Word and apply a transparent shadow using Aspose.Words.
  headline: How to add shadow to shape in a Word document using Python
  type: TechArticle
tags:
- Python
- Aspose.Words
- Word automation
title: Hoe voeg je een schaduw toe aan een vorm in een Word‑document met Python
url: /nl/python/images-shapes/how-to-add-shadow-to-shape-in-a-word-document-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe voeg je een schaduw toe aan een vorm in een Word‑document met Python

Als je **schaduw wilt toevoegen aan een vorm** in een Word‑document, laat deze gids je een complete, uitvoerbare oplossing zien. Je ziet hoe je een Word‑bestand maakt, een rechthoekige vorm invoegt en een 30 % transparante schaduw toepast — allemaal met de Aspose.Words for Python‑bibliotheek.

Werken met Word‑documenten via code bespaart je handmatige opmaak en stelt je in staat om rapporten, contracten of marketingfolders op schaal te genereren. Aan het einde van deze tutorial kun je de vraag “**how to create Word document python**” beantwoorden met een kant‑klaar code‑voorbeeld.

## Vereisten

* Python 3.8 of nieuwer geïnstalleerd.
* Een actieve Aspose.Words for Python‑licentie (de gratis proefversie werkt voor evaluatie).
* `aspose-words`‑pakket geïnstalleerd via `pip install aspose-words`.
* Een map waarin het uitvoerbestand kan worden weggeschreven (vervang `YOUR_DIRECTORY` in de code).

Er zijn geen extra afhankelijkheden nodig.

## Stap 1: Maak een nieuw Word‑document

De eerste stap is het aanmaken van een `Document`‑object. Dit object vertegenwoordigt het volledige .docx‑bestand in het geheugen.

```python
import aspose.words as aw

# Create an empty Word document
doc = aw.Document()
# DocumentBuilder provides a convenient API for adding content
builder = aw.DocumentBuilder(doc)
```

`DocumentBuilder` werkt als een virtuele cursor. Wanneer je zijn methoden aanroept, voegt de bibliotheek de overeenkomstige elementen in op de huidige cursorpositie.

## Stap 2: Voeg een rechthoekige vorm toe aan Word

Vervolgens **voeg je een rechthoekige vorm toe aan Word** met de `insert_shape`‑methode van de builder. De methode vereist het vormtype en de grootte in punten (1 punt = 1/72 inch).

```python
# Insert a rectangle shape that is 100 points wide and 50 points tall
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)
```

Je kunt de afmetingen aanpassen aan je ontwerp. De rechthoek wordt onderdeel van de tekenlaag van het document, wat betekent dat je later de vulling, omtrek of schaduw kunt aanpassen.

## Stap 3: Toegang tot het schaduwformaat van de vorm

Elk tekenobject heeft een `shadow_format`‑eigenschap die het uiterlijk van de schaduw regelt. Haal deze op zodat je transparantie, offset, vervaging en kleur kunt aanpassen.

```python
# Get the ShadowFormat object for the rectangle
shadow = shape.shadow_format
```

Op dit moment heeft de vorm de standaard schaduw (geen schaduw). Het `ShadowFormat`‑object bevat alle parameters die je nodig hebt om een realistisch effect te creëren.

## Stap 4: Maak de schaduw 30 % transparant

Transparantie wordt uitgedrukt als een waarde tussen `0` (volledig ondoorzichtig) en `1` (volledig transparant). Instellen op `0.3` levert een 30 % transparante schaduw op, wat vaak voldoende is om diepte toe te voegen zonder de tekst te overweldigen.

```python
# Apply a 30 % transparent shadow
shadow.transparency = 0.3
# Optional: adjust other shadow properties for a nicer look
shadow.visible = True               # Ensure the shadow is turned on
shadow.distance = 4                 # Distance of the shadow from the shape (points)
shadow.blur = 4                     # Amount of blur applied to the shadow
shadow.color = aw.Color.black       # Shadow color
```

Deze extra eigenschappen zijn niet vereist, maar ze illustreren hoe je het effect fijn kunt afstemmen. De `visible`‑vlag is essentieel; als je die vergeet, verschijnt de schaduw niet, zelfs als de andere instellingen zijn geconfigureerd.

## Stap 5: Sla het document op om het resultaat te bekijken

Tot slot schrijf je het document naar schijf. Het openen van het resulterende `.docx`‑bestand in Microsoft Word of een andere compatibele viewer toont de rechthoek met de toegepaste transparante schaduw.

```python
# Save the document to the desired location
output_path = r"YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Wanneer je `output.docx` opent, zie je een eenvoudige rechthoek met een subtiele grijze schaduw die naar rechtsonder is verschoven. De 30 % transparantie van de schaduw laat de vorm lijken alsof hij van de pagina wordt opgetild.

![Voorbeeld van schaduw toevoegen aan vorm](placeholder-image.png){: .align-center alt="Voorbeeld van schaduw toevoegen aan vorm in een Word‑document gemaakt met Python"}

## Volledig, uitvoerbaar script

Alle onderdelen samenvoegen levert een zelfstandige script op die je direct kunt kopiëren, plakken en uitvoeren.

```python
import aspose.words as aw

def create_word_with_shadow(output_path: str):
    """
    Creates a Word document that contains a rectangle shape
    with a 30 % transparent shadow.
    """
    # Step 1: Initialize document and builder
    doc = aw.Document()
    builder = aw.DocumentBuilder(doc)

    # Step 2: Insert rectangle shape
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)

    # Step 3: Access shadow format
    shadow = shape.shadow_format

    # Step 4: Configure shadow properties
    shadow.visible = True
    shadow.transparency = 0.3
    shadow.distance = 4
    shadow.blur = 4
    shadow.color = aw.Color.black

    # Step 5: Save the document
    doc.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    # Replace with a valid folder on your machine
    create_word_with_shadow(r"YOUR_DIRECTORY/output.docx")
```

**Verwachte output:** Het openen van het gegenereerde `output.docx` toont een enkele pagina met een rechthoek die een lichte, half‑transparante schaduw werpt. Er is geen extra opmaak nodig.

## Veelvoorkomende variaties en randgevallen

| Situatie | Hoe de code aan te passen |
|----------|---------------------------|
| **Ander vormtype** (bijv. ellips) | Verander `aw.drawing.ShapeType.RECTANGLE` naar `aw.drawing.ShapeType.ELLIPSE`. |
| **Aangepaste schaduwkleur** | Stel `shadow.color = aw.Color.from_argb(255, 128, 0, 0)` in voor een roodachtige schaduw. |
| **Meerdere vormen** | Roep `builder.insert_shape` herhaaldelijk aan; elke aanroep retourneert een apart `Shape`‑object dat je onafhankelijk kunt stijlen. |
| **Opslaan als PDF** | Vervang `doc.save(output_path)` door `doc.save(output_path.replace('.docx', '.pdf'))` en gebruik de `.pdf`‑extensie. |
| **Uitvoeren zonder licentie** | De gratis proefversie voegt een watermerk toe aan de eerste pagina. Schaf een licentie aan om dit te verwijderen voor productiegebruik. |

Deze variaties laten zien dat hetzelfde patroon — een document maken, een vorm invoegen, `shadow_format` aanpassen, opslaan — de meeste automatiseringsscenario's dekt.

## Tips en best practices

* **Herbruik de builder**: Houd één enkele `DocumentBuilder`‑instantie voor het gehele document om onnodige objectcreatie te vermijden.
* **Resources vrijgeven**: Roep in langdurige services `doc.dispose()` aan na het opslaan om native geheugen vrij te maken.
* **Output valideren**: Gebruik `doc.validate(aw.ValidationType.FULL_VALIDATION)` vóór het opslaan als je moet voldoen aan de Open XML‑standaard.
* **Versie‑compatibiliteit**: De code werkt met Aspose.Words for Python ≥ 22.9. Zorg dat je pakket up‑to‑date is met `pip install --upgrade aspose-words`.

## Conclusie

Je weet nu hoe je **schaduw kunt toevoegen aan een vorm** in een Word‑document met Python. Door de vijf stappen te volgen — een document maken, **een rechthoekige vorm toevoegen aan Word**, de schaduw configureren en opslaan — kun je geautomatiseerd nette documentgeneratie voor rapporten, facturen of marketingmateriaal realiseren.

Vanaf hier kun je andere opmaakopties verkennen, zoals verloopvullingen, tekstomloop of het converteren van het document naar PDF. Elk van deze onderwerpen bouwt voort op dezelfde `DocumentBuilder`‑ en vorm‑opmaakconcepten die in deze tutorial zijn geïntroduceerd.

Veel plezier met coderen, en geniet van de visuele diepte die een eenvoudige schaduw kan geven aan je geautomatiseerde Word‑documenten!

## Wat kun je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe maak je een rechthoekige vorm in een Word‑document met Python](/words/english/python-net/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/)
- [Schaduw toevoegen aan vorm in Python – Complete Aspose.Words‑tutorial](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [Leeg Word‑document maken en schaduw toevoegen aan vorm – Volledige Python‑gids](/words/english/python-net/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-pyth/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}