---
category: general
date: 2026-08-17
description: Hoe PNG op te slaan met Aspose.Words voor Python. Leer hoe je een schaduw
  aan een vorm toevoegt, een document als PDF opslaat en Word naar PNG exporteert
  in één gids.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save png
- add shadow to shape
- save document as pdf
- export word to png
- convert word to pdf
language: nl
lastmod: 2026-08-17
og_description: Hoe PNG opslaan met Aspose.Words. Deze tutorial laat zien hoe je een
  schaduw aan een vorm toevoegt, het document opslaat als PDF en Word exporteert naar
  PNG.
og_image_alt: Screenshot of a Word document with a rectangle shape that has a shadow,
  saved as PNG and PDF
og_title: Hoe PNG opslaan en schaduw toevoegen aan vorm met Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  headline: How to save PNG and add shadow to shape with Aspose.Words
  type: TechArticle
- description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  name: How to save PNG and add shadow to shape with Aspose.Words
  steps:
  - name: Pro tip
    text: If you need a sharper shadow, reduce `blur`. For a more pronounced offset,
      increase `distance`. The `Shadow` class also exposes `angle` and `transparency`
      for fine‑tuned control.
  - name: 'Optional: higher‑resolution PNG'
    text: '```python png_options = aw.image.PngSaveOptions() png_options.resolution
      = 300 # DPI doc.save("output/high_res_output.png", png_options) ```'
  - name: Expected output
    text: 'Running the script creates three files:'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Image export
title: Hoe PNG opslaan en een schaduw aan een vorm toevoegen met Aspose.Words
url: /nl/python/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe PNG op te slaan en schaduw toe te voegen aan vorm met Aspose.Words

Als je **how to save PNG** vanuit een Word‑bestand nodig hebt, biedt deze gids een complete, uitvoerbare oplossing. Je ziet ook hoe je **add shadow to shape**, **save document as PDF**, en **export Word to PNG** kunt uitvoeren zonder de Aspose.Words‑omgeving te verlaten.

De tutorial behandelt alles wat nodig is om een leeg Word‑document om te zetten naar een PDF‑ en een PNG‑afbeelding, terwijl een eenvoudig schaduweffect op een rechthoekige vorm wordt toegepast. Er zijn geen externe tools nodig, en de code werkt met Aspose.Words for Python via .NET 7 of later.

## Wat je zult bereiken

* Maak een nieuw Word‑document programmatisch.  
* Voeg een rechthoekige vorm toe en configureer een schaduweffect.  
* Sla hetzelfde document op als een PDF‑bestand.  
* Exporteer het document als een PNG‑afbeelding.  

Deze stappen beantwoorden de veelvoorkomende vraag **how to save PNG** terwijl ook **add shadow to shape** en **save document as PDF** in één workflow worden afgehandeld.

## Vereisten

* Python 3.9 of nieuwer.  
* Aspose.Words for Python via .NET geïnstalleerd (`pip install aspose-words`).  
* Schrijfrechten voor de opgegeven uitvoermap.  

Als je Aspose.Words nog niet hebt geïnstalleerd, voer dan uit:

```bash
pip install aspose-words
```

## Hoe PNG op te slaan met Aspose.Words

De eerste belangrijke stap is het maken van een document en een `DocumentBuilder`. De builder biedt een vloeiende API voor het invoegen van inhoud zoals vormen, tabellen of tekst.

```python
import aspose.words as aw

# Create a new blank document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` vertegenwoordigt het volledige Word‑bestand in het geheugen. `aw.DocumentBuilder` wijst naar de huidige invoeglocatie, die aanvankelijk het begin van de eerste (en enige) sectie is.

## Schaduw toevoegen aan vorm vóór het exporteren

Een vorm kan elk tekenobject zijn — rechthoek, ellips of aangepaste veelhoek. Hier maken we een rechthoek van 100 × 100 point en passen we een zachte schaduw toe.

```python
# Insert a rectangle shape (100x100 points)
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

# Configure a simple shadow
shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Softness of the shadow edges
shape.shadow.distance = 3.0      # Distance from the shape
shape.shadow.color = aw.Color.black
```

Waarom de schaduw vóór het opslaan configureren? Aspose.Words rendert de schaduw tijdens de PDF‑ en PNG‑exportfasen, zodat het visuele effect in beide uitvoerformaten behouden blijft.

### Pro‑tip
Als je een scherpere schaduw nodig hebt, verlaag dan `blur`. Voor een meer uitgesproken offset, verhoog `distance`. De `Shadow`‑klasse biedt ook `angle` en `transparency` voor fijnmazige controle.

## Document opslaan als PDF

Het opslaan van een Word‑document als PDF is een één‑regelige bewerking zodra de inhoud klaar is. De constante `SaveFormat.PDF` vertelt Aspose.Words de conversie uit te voeren.

```python
# Save the document as PDF (shadow is rendered in the output)
pdf_path = "output/output.pdf"
doc.save(pdf_path, aw.SaveFormat.PDF)
```

De resulterende PDF bevat de rechthoek met de exacte schaduw die je hebt gedefinieerd. Aspose.Words verwerkt vectorafbeeldingen, waardoor de PDF‑grootte bescheiden blijft.

## Word exporteren naar PNG

Exporteren naar PNG maakt een rasterafbeelding van elke pagina. Standaard gebruikt Aspose.Words 96 DPI; je kunt deze waarde verhogen voor een hogere resolutie door een `PngSaveOptions`‑object te leveren.

```python
# Export the same document as PNG
png_path = "output/output.png"
doc.save(png_path, aw.SaveFormat.PNG)
```

Wanneer je **export Word to PNG** uitvoert, wordt elke pagina opgeslagen als een afzonderlijk PNG‑bestand. Omdat ons voorbeeld‑document slechts één pagina heeft, verschijnt er slechts één PNG‑bestand.

### Optioneel: hogere‑resolutie PNG

```python
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI
doc.save("output/high_res_output.png", png_options)
```

Een hogere DPI is nuttig wanneer de PNG wordt gebruikt voor afdrukken of wanneer je een scherpe miniatuur nodig hebt.

## Volledig script – kopiëren, plakken en uitvoeren

Hieronder staat het volledige, zelfstandige script dat elke stap hierboven beschrijft implementeert. Sla het op als `generate_assets.py` en voer het uit via de opdrachtregel.

```python
import os
import aspose.words as aw

# ------------------------------------------------------------------
# 1. Prepare output folder
# ------------------------------------------------------------------
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# ------------------------------------------------------------------
# 2. Create a new blank document and a builder
# ------------------------------------------------------------------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ------------------------------------------------------------------
# 3. Insert a rectangle shape and add a shadow
# ------------------------------------------------------------------
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Soft edges
shape.shadow.distance = 3.0      # Offset from shape
shape.shadow.color = aw.Color.black

# ------------------------------------------------------------------
# 4. Save as PDF (demonstrates "save document as pdf")
# ------------------------------------------------------------------
pdf_path = os.path.join(output_dir, "output.pdf")
doc.save(pdf_path, aw.SaveFormat.PDF)

# ------------------------------------------------------------------
# 5. Export as PNG (demonstrates "how to save png")
# ------------------------------------------------------------------
png_path = os.path.join(output_dir, "output.png")
doc.save(png_path, aw.SaveFormat.PNG)

# ------------------------------------------------------------------
# 6. Optional high‑resolution PNG (demonstrates "export word to png")
# ------------------------------------------------------------------
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI for sharper output
high_res_png_path = os.path.join(output_dir, "high_res_output.png")
doc.save(high_res_png_path, png_options)

print(f"Files written to {os.path.abspath(output_dir)}")
```

### Verwachte output

Het uitvoeren van het script maakt drie bestanden aan:

* `output/output.pdf` – een PDF met een rechthoek die een zwarte schaduw werpt.  
* `output/output.png` – een 96 DPI PNG‑rendering van dezelfde pagina.  
* `output/high_res_output.png` – een 300 DPI PNG voor hogere kwaliteit.

Open een van de bestanden in je favoriete viewer om te verifiëren dat de schaduw precies zoals gedefinieerd verschijnt.

## Veelgestelde vragen en randgevallen

**Wat als de uitvoermap niet bestaat?**  
Het script roept `os.makedirs(output_dir, exist_ok=True)` aan, waardoor de map automatisch wordt aangemaakt. Dit voorkomt een `FileNotFoundError` tijdens de opslaan‑bewerkingen.

**Kan ik meerdere vormen met verschillende schaduwen toevoegen?**  
Ja. Maak extra `Shape`‑objecten, configureer elke `shadow`‑eigenschap onafhankelijk, en voeg ze in met `builder.insert_node(shape)` vóór het opslaan.

**Wordt de schaduw behouden bij conversie naar andere rasterformaten (bijv. JPEG)?**  
Aspose.Words rendert de schaduw voor alle rasterformaten die worden ondersteund door `SaveFormat`. Je kunt `aw.SaveFormat.PNG` vervangen door `aw.SaveFormat.JPEG` en de schaduw zal nog steeds verschijnen.

**Hoe verschilt dit van “convert word to pdf”?**  
`convert word to pdf` is in wezen dezelfde bewerking die in stap 4 wordt uitgevoerd. Dezelfde `doc.save`‑aanroep met `SaveFormat.PDF` verwerkt de conversie intern, waarbij lay-out, lettertypen en grafische elementen zoals schaduwen behouden blijven.

**Is er een limiet aan de grootte van vormen?**  
Vormen worden gemeten in points (1 pt ≈ 1/72 inch). Zeer grote afmetingen kunnen de resulterende bestandsgrootte vergroten, maar Aspose.Words hanteert geen harde limiet. Pas de argumenten `width` en `height` aan bij het construeren van `aw.Shape` om aan je lay-out te voldoen.

## Conclusie

Je weet nu **how to save PNG** vanuit een Word‑document en hebt tevens geleerd hoe je **add shadow to shape**, **save document as PDF**, en **export Word to PNG** kunt uitvoeren met Aspose.Words for Python. Het volledige script toont een schoon, herhaalbaar patroon dat je kunt aanpassen voor grotere documenten, meerdere pagina's of complexere grafische effecten.

Volgende stappen kunnen omvatten:

* Experimenteren met andere `ShapeType`‑waarden (ellipse, wolk, enz.).  
* Using `

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [How to Convert DOCX to PNG in Java – Aspose.Words](/words/english/java/document-converting/converting-documents-images/)
- [Save Word Documents as PostScript in Python Using Aspose.Words: A Comprehensive Guide](/words/english/python-net/document-operations/save-docs-as-postscript-using-aspose-words-python/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}