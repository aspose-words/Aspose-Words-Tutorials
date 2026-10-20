---
category: general
date: 2026-08-01
description: Hoe je een schaduw instelt op een Word‑vorm met Aspose.Words voor Python.
  Leer de doorzichtigheid te wijzigen, de vervaging aan te passen en de schaduwafstand
  snel te veranderen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to set shadow
- how to change opacity
- how to adjust blur
- change shadow distance
- how to use aspose.words
language: nl
lastmod: 2026-08-01
og_description: Hoe je een schaduw op een vorm instelt met Aspose.Words voor Python.
  Volg deze stap‑voor‑stap tutorial om de doorzichtigheid te wijzigen, de vervaging
  aan te passen en de afstand van de schaduw te veranderen.
og_image_alt: Screenshot showing how to set shadow on a shape using Aspose.Words in
  Python
og_title: Hoe schaduw instellen in Aspose.Words – Snelle Python-gids
schemas:
- author: Aspose
  dateModified: '2026-08-01'
  description: How to set shadow on a Word shape using Aspose.Words for Python. Learn
    to change opacity, adjust blur, and change shadow distance quickly.
  headline: How to Set Shadow in Aspose.Words – Python Example
  type: TechArticle
- description: How to set shadow on a Word shape using Aspose.Words for Python. Learn
    to change opacity, adjust blur, and change shadow distance quickly.
  name: How to Set Shadow in Aspose.Words – Python Example
  steps:
  - name: '**Create the document** (or load a template).'
    text: '**Create the document** (or load a template).'
  - name: '**Insert the logo shape** (via `DocumentBuilder.insert_image` or `Shape`).'
    text: '**Insert the logo shape** (via `DocumentBuilder.insert_image` or `Shape`).'
  - name: '**Call `apply_shadow`** with your brand’s shadow specs.'
    text: '**Call `apply_shadow`** with your brand’s shadow specs.'
  - name: '**Export** to DOCX, PDF, or HTML with a single line of code.'
    text: '**Export** to DOCX, PDF, or HTML with a single line of code.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Shadow Formatting
- Word Automation
title: Hoe schaduw instellen in Aspose.Words – Python-voorbeeld
url: /nl/python/images-shapes/how-to-set-shadow-in-aspose-words-python-example/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe schaduw instellen in Aspose.Words – Python voorbeeld

Heb je je ooit afgevraagd **hoe je schaduw instelt** op een Word‑vorm zonder het document handmatig te openen? Je bent niet de enige—veel ontwikkelaars lopen tegen dit probleem aan bij het automatiseren van rapporten of het maken van merkon‑consistent sjablonen. Het goede nieuws? Met Aspose.Words voor Python kun je de schaduw, doorzichtigheid, vervaging en afstand van een vorm aanpassen in slechts een paar regels code.

In deze tutorial lopen we een compleet, uitvoerbaar voorbeeld door dat laat zien **hoe je schaduw instelt**, **hoe je de doorzichtigheid wijzigt**, **hoe je vervaging aanpast**, en zelfs **de schaduwafstand wijzigt**. Aan het einde heb je een stevige grip op **hoe je Aspose.Words gebruikt** om vormen programmatisch te stylen.

---

![How to set shadow on a shape using Aspose.Words](image-placeholder.png){alt="Hoe schaduw instellen op een vorm met Aspose.Words"}

## Vereisten

Voordat we beginnen, zorg dat je het volgende hebt:

| Vereiste | Reden |
|-------------|--------|
| Python 3.8+ | Moderne syntaxis, type hints |
| `aspose-words` package (pip install aspose-words) | Kernbibliotheek voor Word-manipulatie |
| Een voorbeeld `input.docx` met ten minste één vorm | De vorm die we zullen schaduwen |
| Schrijfrechten voor de map waarin je `output.docx` opslaat | Om wijzigingen op te slaan |

Geen extra DLL's of COM-interoperabiliteit—Aspose.Words is pure‑Python, dus je kunt dit uitvoeren op Windows, macOS of Linux.

---

## Hoe schaduw instellen op een vorm met Aspose.Words

Hieronder staat het **complete** script. Het laadt een document, vindt de eerste vorm (recursief), configureert de schaduw, en slaat het resultaat op. Elke regel is becommentarieerd zodat je begrijpt **waarom** het er is, en niet alleen **wat** het doet.

```python
# ------------------------------------------------------------
# How to Set Shadow – Full Python Example using Aspose.Words
# ------------------------------------------------------------
import aspose.words as aw  # Import the Aspose.Words namespace

def apply_shadow(
    input_path: str,
    output_path: str,
    distance: int = 5,
    blur: float = 4.0,
    opacity: float = 0.6
) -> None:
    """
    Demonstrates how to set shadow on the first shape in a Word document.
    
    Parameters
    ----------
    input_path : str
        Path to the source .docx file.
    output_path : str
        Path where the modified .docx will be saved.
    distance : int, optional
        How far the shadow is offset from the shape (default = 5 points).
    blur : float, optional
        Blur radius of the shadow (default = 4.0 points).
    opacity : float, optional
        Opacity of the shadow (0 = fully transparent, 1 = fully opaque).
    """
    # Step 1: Load the Word document
    doc = aw.Document(input_path)

    # Step 2: Retrieve the first shape in the document (searches recursively)
    # The `True` flag makes the search go deep into headers, footers, and groups.
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

    if shape is None:
        raise ValueError("No shape found in the document. Add a shape and try again.")

    # Step 3: Configure the shadow appearance for the shape
    # ----------------------------------------------------
    # distance → how far the shadow sits away from the shape edge
    # blur     → softness of the shadow edge
    # opacity  → transparency level (0‑1 range)
    shape.shadow_format.distance = distance          # change shadow distance
    shape.shadow_format.blur = blur                  # how to adjust blur
    shape.shadow_format.opacity = opacity            # how to change opacity

    # Optional: tweak color and style if you need more control
    shape.shadow_format.color = aw.Color.black
    shape.shadow_format.style = aw.ShadowStyle.OUTER_SHADOW

    # Step 4: Save the modified document
    doc.save(output_path)

# -----------------------------------------------------------------
# Example usage – adjust the parameters to see different results
# -----------------------------------------------------------------
if __name__ == "__main__":
    apply_shadow(
        input_path="YOUR_DIRECTORY/input.docx",
        output_path="YOUR_DIRECTORY/output.docx",
        distance=8,       # increase distance for a more pronounced offset
        blur=6.5,         # higher blur makes the shadow softer
        opacity=0.75      # make the shadow a bit more solid
    )
```

### Waarom dit werkt

* **`doc.get_child(..., True)`** – De `True`‑vlag vertelt Aspose.Words om **recursief** te zoeken, zodat zelfs vormen in kopteksten, voetteksten of gegroepeerde objecten worden gevonden. Dat is cruciaal wanneer je niet precies weet waar de vorm zich bevindt.  
* **`shadow_format`** – Deze eigenschap groepeert alle schaduw‑gerelateerde instellingen. Door `distance`, `blur` en `opacity` in te stellen, beheer je de visuele diepte van de vorm. Het wijzigen van een van deze waarden demonstreert **hoe je de doorzichtigheid wijzigt**, **hoe je vervaging aanpast**, en **schaduwafstand wijzigt** in één samenhangende aanroep.  
* **Saving** – `doc.save` schrijft een gloednieuwe `.docx`. Het origineel blijft onaangeroerd, wat een veilig patroon is voor batchverwerking.

## Hoe de doorzichtigheid van de schaduw van een vorm wijzigen

Doorzichtigheid bepaalt hoe doorschijnend de schaduw lijkt. Het bereik is 0.0 (volledig onzichtbaar) tot 1.0 (volledig solide). In de bovenstaande code kun je eenvoudig het `opacity`‑argument aanpassen:

```python
shape.shadow_format.opacity = 0.85  # 85% opaque – looks richer on dark backgrounds
```

> **Pro tip:** Bij het later genereren van PDF's resulteert een hogere doorzichtigheid vaak in een diepere, beter afdrukbare schaduw. Experimenteer met waarden tussen 0.4 en 0.9 om de optimale instelling voor je merkrichtlijnen te vinden.

## Hoe vervaging aanpassen voor een zachtere uitstraling

Vervaging is de radius van de Gaussiaanse vervaging die op de schaduwranden wordt toegepast. Een groter getal geeft een veerachtig effect:

```python
shape.shadow_format.blur = 10.0  # Very soft, almost hazy shadow
```

Als je een scherpe, drop‑shadow‑look nodig hebt (denk aan de stijl van “Microsoft PowerPoint”), stel `blur` in op een lage waarde zoals `1.0`.

## Schaduwafstand wijzigen om diepte te creëren

Afstand wordt gemeten in punten (1 pt = 1/72 in). De schaduw verder van de vorm plaatsen maakt dat de vorm hoger lijkt te zweven:

```python
shape.shadow_format.distance = 12  # Shadow shifts 12 pt away from the shape
```

Combineer een grotere `distance` met een bescheiden `blur` voor een dramatisch, “verhoogd” effect.

## Alles samenvoegen – Een mini‑project

Stel je voor dat je een geautomatiseerde rapportgenerator bouwt die een bedrijfslogo in een tekstvak invoegt. Je wilt dat elk logo een subtiele schaduw heeft die overeenkomt met de corporate stijl. Met de functie `apply_shadow` kun je:

1. **Maak het document** (of laad een sjabloon).
2. **Voeg de logo‑vorm in** (via `DocumentBuilder.insert_image` of `Shape`).
3. **Roep `apply_shadow` aan** met de schaduw‑specificaties van je merk.
4. **Exporteer** naar DOCX, PDF of HTML met één regel code.

Omdat de functie parameters accepteert, kun je je schaduwinstellingen opslaan in een JSON‑bestand en ze toepassen op tientallen documenten—geen handmatige aanpassing nodig.

## Veelgestelde vragen & randgevallen

| Vraag | Antwoord |
|----------|--------|
| **Wat als het document meerdere vormen heeft?** | Het voorbeeld richt zich op de *eerste* vorm. Om alle vormen te beïnvloeden, loop met `doc.get_child_nodes(aw.NodeType.SHAPE, True)` en pas dezelfde `shadow_format`‑instellingen toe op elk knooppunt. |
| **Kan ik een andere schaduwkleur instellen?** | Zeker. Gebruik `shape.shadow_format.color = aw.Color(255, 0, 0)` voor een rode schaduw, of elke `aw.Color` die je wilt. |
| **Blijven deze instellingen behouden bij conversie naar PDF?** | Ja. Aspose.Words behoudt schaduweigenschappen bij het renderen naar PDF, hoewel zeer hoge vervagingswaarden mogelijk benaderd worden. |
| **Is er een prestatieverlies bij grote documenten?** | De schaduw‑API raakt alleen de vormobjecten, dus zelfs een rapport van 500 pagina's wordt in milliseconden verwerkt. De bottleneck is meestal I/O, niet de schaduwconfiguratie. |
| **Kan ik de schaduw later verwijderen?** | Stel `shape.shadow_format.is_visible = False` in of reset de eigenschappen eenvoudig naar de standaardwaarden. |

## Volledig werkend voorbeeld samenvatting

Hier is het volledige script opnieuw, zonder commentaar voor snel kopiëren‑plakken:

```python
import aspose.words as aw

def apply_shadow(input_path, output_path, distance=5, blur=4.0, opacity=0.6):
    doc = aw.Document(input_path)
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
    if shape is None:
        raise ValueError("No shape found.")
    shape.shadow_format.distance = distance
    shape.shadow_format.blur = blur
    shape.shadow_format.opacity = opacity
    shape.shadow_format.color = aw.Color.black
    shape.shadow_format.style = aw.ShadowStyle.OUTER_SHADOW
    doc.save(output_path)

if __name__ == "__main__":
    apply_shadow(
        "YOUR_DIRECTORY/input.docx",
        "YOUR_DIRECTORY/output.docx",
        distance=8,
        blur=6.5,
        opacity=0.75
    )
```

Voer het script uit, open `output.docx`, en je zult zien dat de vorm een nette schaduw heeft die overeenkomt met de door jou ingestelde parameters.

## Conclusie

We hebben behandeld **

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Aspose.Words Vorm Schaduw Tutorial – Voeg een schaduw toe aan Word‑vorm in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Hoe opmerkingen en antwoorden te implementeren in Word‑documenten met Aspose.Words voor Python](/words/english/python-net/annotations-comments/aspose-words-python-comments-replies/)
- [Hoe documentvariabelen te beheren met Aspose.Words in Python: Een complete gids](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}