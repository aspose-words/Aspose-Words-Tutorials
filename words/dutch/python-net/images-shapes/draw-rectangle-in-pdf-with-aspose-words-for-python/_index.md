---
category: general
date: 2026-08-07
description: Teken een rechthoek in PDF met Aspose.Words voor Python en leer hoe je
  een schaduw aan een vorm toevoegt, de vormschaduw configureert en het document opslaat
  als PDF.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle in pdf
- add shadow to shape
- save document as pdf
- configure shape shadow
language: nl
lastmod: 2026-08-07
og_description: Teken een rechthoek in PDF met Aspose.Words voor Python. Deze tutorial
  laat zien hoe je een schaduw aan een vorm toevoegt, de vormschaduw configureert
  en het document opslaat als PDF voor professionele documentgeneratie.
og_image_alt: PDF page showing a rectangle shape with a visible shadow created by
  Aspose.Words for Python
og_title: Rechthoek tekenen in PDF met Aspose.Words voor Python – gids
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
title: Teken een rechthoek in PDF met Aspose.Words voor Python
url: /nl/python/images-shapes/draw-rectangle-in-pdf-with-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechthoek tekenen in PDF met Aspose.Words voor Python

Als je een **rechthoek in PDF** moet tekenen tijdens het werken in Python, biedt deze gids een complete, kant‑klaar oplossing. Je ziet precies hoe je **schaduw aan vorm toevoegt**, die schaduw configureert, en uiteindelijk **document opslaat als PDF** voor distributie of archivering.

Een rechthoek met schaduw maken is een veelvoorkomende eis voor rapporten, facturen of visuele annotaties. Aan het einde van deze tutorial heb je een enkel script dat een PDF genereert met een rechthoek met een realistische schaduw, en begrijp je hoe je grootte, kleur en offset kunt aanpassen aan elk ontwerp.

## Vereisten

* Python 3.8+ geïnstalleerd.
* Het Aspose.Words for Python via .NET pakket (`aspose-words`) – installeren met:

```bash
pip install aspose-words
```

* Schrijfrechten op de map waar je de PDF wilt opslaan.

Er zijn geen extra bibliotheken nodig; Aspose.Words behandelt het maken van vormen, het configureren van schaduw en de PDF-export intern.

## Stap 1: Maak een nieuw leeg document (rechthoek in PDF – initialiseren)

De eerste stap is het instantieren van een `Document`‑object. Dit object vertegenwoordigt het volledige PDF‑bestand en biedt een container voor secties, alinea's en vormen.

```python
import aspose.words as aw

# Create an empty Word document – it will become a PDF later
doc = aw.Document()
```

**Waarom dit belangrijk is:** Aspose.Words beschouwt PDF‑generatie als een conversie vanuit een Word‑documentmodel, dus beginnen we met een `Document` hoewel de uiteindelijke output een PDF is.

## Stap 2: Voeg een rechthoekvorm toe aan de documentbody

Een rechthoek is een specifiek `ShapeType`. We voegen deze toe aan de body van de eerste sectie, die automatisch een nieuwe pagina creëert bij het opslaan als PDF.

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

**Uitleg:** De `width`‑ en `height`‑eigenschappen bepalen de visuele grootte van de vorm in de PDF. Het toevoegen van tekst maakt de rechthoek makkelijker te verifiëren tijdens het testen.

## Stap 3: Voeg schaduw toe aan vorm – inschakelen en aanpassen

Nu schakelen we het schaduweffect in en verfijnen we het uiterlijk. Dit is waar het trefwoord **add shadow to shape** van pas komt.

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

**Waarom vormschaduw configureren?** Het aanpassen van `blur`, `distance` en `angle` stelt je in staat realistische verlichting te simuleren, wat de leesbaarheid en visuele hiërarchie in gegenereerde PDF's verbetert.

## Stap 4: Document opslaan als PDF – eindoutput

Met de rechthoek en zijn schaduw gedefinieerd, is de laatste stap het exporteren van het Word‑document naar PDF. Dit voldoet aan de **save document as pdf**‑vereiste.

```python
# Define the output path – replace YOUR_DIRECTORY with an actual folder
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)
print(f"PDF saved to {output_path}")
```

Wanneer je `shadow_rectangle.pdf` opent, zie je een enkele pagina met een grijs-omrandeerde rechthoek met de titel “Shadow demo” en een scherpe, diagonale schaduw.

### Verwachte output

* Een PDF‑bestand genaamd `shadow_rectangle.pdf`.
* Eén pagina met een rechthoek van 200 pt × 100 pt.
* Een zichtbare schaduw met een offset van 5 pt onder een hoek van 45°, vervaagd met 8 pt.

## Stap 5: Verken variaties en randgevallen (optioneel)

Hieronder staan veelvoorkomende aanpassingen die je mogelijk nodig hebt in real‑world projecten:

| Variatie | Codefragment | Wanneer te gebruiken |
|-----------|--------------|----------------------|
| **Ander vormtype** (bijv. ellips) | `aw.drawing.ShapeType.OVAL` instead of `RECTANGLE` | Voor ronde grafische elementen of badges |
| **Aangepaste schaduwkleur** | `shadow.color = aw.drawing.Color.from_argb(255, 100, 100, 100)` | Wanneer een grijze of merk‑specifieke schaduw vereist is |
| **Meerdere vormen** | Repeat the shape‑creation block and adjust `left`/`top` properties | Om complexe diagrammen te bouwen |
| **Geen tekst in vorm** | Omit `rectangle.text = "..."` | Wanneer de vorm puur decoratief is |
| **Hogere DPI output** | `doc.save(output_path, aw.SaveFormat.PDF, aw.PdfSaveOptions())` with `PdfSaveOptions` set for image quality | Voor print‑klare PDF's |

**Pro tip:** Stel altijd `shadow.visible = True` in voordat je andere eigenschappen aanpast; anders worden de wijzigingen stilletjes genegeerd.

## Volledig script – kopiëren, plakken en uitvoeren

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

Voer het script uit vanuit je terminal of IDE. Vervang `YOUR_DIRECTORY` door een echt mappad, zoals `"/tmp"` of `"C:\\Users\\Me\\Documents"`.

## Conclusie

Je weet nu hoe je een **rechthoek in PDF** tekent met Aspose.Words voor Python, **schaduw aan vorm toevoegt**, **vormschaduw configureert**, en **document opslaat als PDF**. Het volledige voorbeeld toont elke stap van het maken van een document tot de uiteindelijke export, en de optionele variaties laten zien hoe je de code kunt aanpassen voor complexere scenario's.

Vervolgens kun je verkennen:

* Andere vormtypes toevoegen (`ShapeType.LINE`, `ShapeType.ELLIPSE`).
* Een verloopvulling of randen toepassen om de visuele aantrekkingskracht te vergroten.
* `PdfSaveOptions` gebruiken om lettertypen in te sluiten of de beeldcompressie te regelen.

Voel je vrij om te experimenteren met de parameters om ze af te stemmen op je merk of ontwerprichtlijnen. Veel plezier met PDF‑scripting!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [PDF-bladwijzers optimaliseren met Aspose.Words voor Python](/words/english/python-net/performance-optimization/optimize-pdf-bookmarks-aspose-words-python/)
- [PDF-laden optimaliseren Python Aspose Words Sla afbeeldingen over](/words/hindi/python-net/performance-optimization/optimize-pdf-loading-python-aspose-words-skip-images/)
- [Aspose Words Python PDF-manipulatie](/words/hongkong/python-net/document-operations/aspose-words-python-pdf-manipulation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}