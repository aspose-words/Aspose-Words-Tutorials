---
category: general
date: 2026-06-21
description: Maak een rechthoekvorm in Python met Aspose.Words. Leer hoe je een schaduw
  aan de vorm toevoegt, de vulkleur van de vorm instelt en het document binnen enkele
  minuten als PDF opslaat.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- set shape fill color
language: nl
og_description: Maak een rechthoekvorm in Python met Aspose.Words. Deze gids laat
  zien hoe je een schaduw aan de vorm toevoegt, de vulkleur van de vorm instelt en
  het document opslaat als PDF.
og_title: Rechthoekvorm maken in Python – Aspose.Words tutorial
schemas:
- author: Aspose
  dateModified: '2026-06-21'
  description: Create rectangle shape in Python using Aspose.Words. Learn how to add
    shadow to shape, set shape fill color, and save document as PDF in minutes.
  headline: Create rectangle shape in Python – Aspose.Words tutorial
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF generation
title: Maak een rechthoekvorm in Python – Aspose.Words‑tutorial
url: /nl/python/images-shapes/create-rectangle-shape-in-python-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechthoekvorm maken in Python – Aspose.Words tutorial

Heb je je ooit afgevraagd **hoe je een rechthoekvorm** in een Word‑document kunt maken terwijl je in Python code schrijft? Je bent niet de enige. Veel ontwikkelaars lopen tegen een muur aan wanneer ze een snel visueel element nodig hebben — zoals een gekleurde doos met een subtiele schaduw — en vervolgens het geheel als PDF exporteren.  

In deze gids lopen we stap voor stap door een volledig, uitvoerbaar voorbeeld dat **een rechthoekvorm maakt**, **de vulkleur van de vorm instelt**, **een schaduw aan de vorm toevoegt**, en uiteindelijk **het document opslaat als PDF**. Geen vage verwijzingen, alleen concrete code die je vandaag kunt kopiëren‑plakken en uitvoeren.

## Wat je nodig hebt

- Python 3.8 of nieuwer (de syntaxis die we gebruiken werkt op elke recente versie).
- Een actieve Aspose.Words for Python‑licentie of een gratis proefversie (de bibliotheek is pure‑Python, geen COM‑interop vereist).
- Een teksteditor of IDE waar je je prettig bij voelt — VS Code werkt uitstekend, maar elke zal volstaan.

Dat is alles. Geen zware frameworks, geen extra OS‑niveau afhankelijkheden. Laten we beginnen.

## Stap 1: Installeer Aspose.Words voor Python

Allereerst. Als je dat nog niet gedaan hebt, haal het pakket van PyPI:

```bash
pip install aspose-words
```

Waarom deze stap belangrijk is: Aspose.Words levert de `Document`‑ en `DocumentBuilder`‑klassen waar we op vertrouwen. Zonder de bibliotheek bestaan geen van de latere aanroepen — zoals `insert_shape` —, waardoor het script crasht voordat het zelfs maar een lijn tekent.

> **Pro tip:** Houd je virtuele omgeving netjes. Voer `python -m venv .venv && source .venv/bin/activate` uit vóór het installeren, zodat de bibliotheek geïsoleerd blijft van systeempakketten.

## Stap 2: Maak een nieuw document en een DocumentBuilder

Nu maken we daadwerkelijk **een rechthoekvorm** — maar eerst hebben we een leeg canvas nodig.

```python
import aspose.words as aw

# Initialize a new, empty Word document
doc = aw.Document()
# DocumentBuilder lets us add content programmatically
builder = aw.DocumentBuilder(doc)
```

Het `Document`‑object vertegenwoordigt het volledige bestand, terwijl `DocumentBuilder` een handige helper is die weet waar de cursor staat en op dat punt elementen kan invoegen. Beschouw de builder als een pen die op de pagina schrijft.

## Stap 3: Voeg de rechthoekvorm in

Hier gebeurt de hoofdactie. We zullen **een rechthoekvorm maken** met een vaste breedte en hoogte, en deze vervolgens op de pagina positioneren.

```python
# Insert a rectangle 200 points wide and 100 points tall
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

Waarom een rechthoek? Het is de eenvoudigste vorm die ons toch in staat stelt vulkleuren en schaduwen te tonen. Als je later een cirkel of ster nodig hebt, verwissel je gewoon `ShapeType.RECTANGLE` voor een andere enum‑waarde.

## Stap 4: Stel de vulkleur van de vorm in

Een eenvoudige witte doos is niet erg spannend, dus laten we **de vulkleur van de vorm instellen** op iets zachts — lichtblauw werkt goed voor rapporten.

```python
# Apply a light‑blue background to the rectangle
rectangle.fill_color = aw.Color.light_blue
```

Je kunt een van de vooraf gedefinieerde `aw.Color`‑leden gebruiken (`red`, `green`, `dark_gray`, enz.) of een RGB‑tuple doorgeven (`aw.Color.from_argb(255, 30, 144, 255)`). De vulkleur is wat de gebruiker ziet voordat een schaduw of rand wordt toegepast.

## Stap 5: Voeg een schaduw toe aan de vorm

Nu de visuele afwerking: **schaduw toevoegen aan de vorm**. Schaduwen geven diepte en laten de rechthoek op de pagina opvallen.

```python
# Grab the shadow format object
shadow = rectangle.shadow_format

# Turn the shadow on
shadow.visible = True
# Choose a dark gray tone for realism
shadow.color = aw.Color.dark_gray
# Blur radius controls softness (5 points is a nice middle ground)
shadow.blur = 5
# Horizontal and vertical offsets shift the shadow relative to the shape
shadow.offset_x = 3
shadow.offset_y = 3
# Slight transparency makes the shadow feel natural
shadow.transparency = 0.2
# Use an outer shadow – you could also try INSET for a different effect
shadow.type = aw.drawing.ShadowType.OUTER
```

**Hoe voeg je een schaduw toe**? De bovenstaande code doet precies dat, maar laten we uitleggen waarom elke eigenschap belangrijk is:

- `visible` – schakelt het effect in/uit.
- `color` – bepaalt de tint; een donkergrijs bootst natuurlijk licht na.
- `blur` – hogere waarden geven een zachtere rand.
- `offset_x` / `offset_y` – verplaatst de schaduw van de vorm; pas deze aan om verschillende lichthoeken te simuleren.
- `transparency` – 0 is ondoorzichtig, 1 is onzichtbaar; 0.2 geeft een subtiele indruk.
- `type` – `OUTER` werpt de schaduw buiten de vorm, terwijl `INNER` deze naar binnen zou brengen.

Als je ooit een dramatische slagschaduw nodig hebt, verhoog dan `blur` naar 10‑15 en zet `offset_x`/`offset_y` op 6‑8.

## Stap 6: Sla het document op als PDF

Al dat werk is zinloos tenzij we **het document kunnen opslaan als PDF** en delen. Aspose.Words maakt dit een één‑regelige opdracht:

```python
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Waarom PDF? PDF's behouden de lay-out op verschillende platforms, waardoor ze ideaal zijn voor rapporten, facturen of ander afdrukbaar materiaal. De `save`‑methode detecteert automatisch de bestandsextensie en kiest het juiste formaat — zorg er alleen voor dat het pad eindigt op `.pdf`.

### Verwacht resultaat

Open de gegenereerde `ShapeWithShadow.pdf` en je zou een lichtblauwe rechthoek moeten zien, gecentreerd nabij de bovenkant van de eerste pagina, met een zachte donkergrijze schaduw die iets naar rechts en omlaag is verschoven. De randen van de vorm zijn scherp, de schaduw is subtiel, en de bestandsgrootte is doorgaans onder de 100 KB.

## Bonus: Schaduwen aanpassen – Antwoorden op “hoe voeg je een schaduw toe”

Je vraagt je misschien af, *“Kan ik de richting van de schaduw wijzigen zonder de vorm te verplaatsen?”* Absoluut. De positie van de schaduw is onafhankelijk van de coördinaten van de vorm; pas gewoon `offset_x` en `offset_y` aan. Positieve waarden verplaatsen de schaduw naar rechts/onder, negatieve waarden naar links/boven. Voor een lichtbron links‑boven, gebruik `offset_x = -3` en `offset_y = -3`.

Een andere veelgestelde vraag: *“Wat als ik meerdere schaduwen op dezelfde vorm nodig heb?”* Aspose.Words ondersteunt slechts één schaduw per vorm. Als je gelaagde effecten nodig hebt, maak dan een duplicaat van de vorm, verschuif deze een beetje, en pas een andere schaduw op elk toe. Het is een beetje een truc, maar het werkt.

## Volledig script – Klaar om uit te voeren

Hieronder staat het volledige, zelfstandige script. Kopieer het naar een bestand met de naam `create_rectangle_with_shadow.py` en voer het uit met `python create_rectangle_with_shadow.py`.

```python
import aspose.words as aw

# ---------- Initialize document ----------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ---------- Insert rectangle ----------
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# ---------- Set fill color ----------
rectangle.fill_color = aw.Color.light_blue

# ---------- Configure shadow ----------
shadow = rectangle.shadow_format
shadow.visible = True
shadow.color = aw.Color.dark_gray
shadow.blur = 5
shadow.offset_x = 3
shadow.offset_y = 3
shadow.transparency = 0.2
shadow.type = aw.drawing.ShadowType.OUTER

# ---------- Save as PDF ----------
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

> **Opmerking:** Vervang `YOUR_DIRECTORY` door een absoluut of relatief pad dat bestaat op je machine. Als de map niet bestaat, zal Python een `FileNotFoundError` geven.

## Veelvoorkomende valkuilen & hoe ze te vermijden

| Probleem | Waarom het gebeurt | Oplossing |
|----------|--------------------|-----------|
| Schaduw verschijnt niet | `shadow.visible` staat op standaard `False` | Zorg ervoor dat `shadow.visible = True` |
| Vorm is onzichtbaar | Vulkleur ingesteld op `aw.Color.transparent` of `None` | Gebruik een solide kleur zoals `aw.Color.light_blue` |
| PDF is leeg | Vergeten `doc.save` aan te roepen of opgeslagen met verkeerde extensie | Roep `doc.save("output.pdf")` aan en controleer het pad |
| Runtime‑fout `ImportError` | Aspose.Words niet geïnstalleerd of verkeerde Python‑omgeving | Voer `pip install aspose-words` uit binnen de actieve venv |

## Volgende stappen – Ontdek meer vormen en opmaak

Nu je **een rechthoekvorm maken** onder de knie hebt, kun je:

- Vervang `ShapeType.RECTANGLE` door `ShapeType.ELLIPSE` of `ShapeType.PENTAGON` om met andere geometrieën te experimenteren.
- Voeg tekst toe binnen de vorm met `builder.move_to(rectangle.absolute_position)` en vervolgens `builder.writeln("Hello World")`.
- Combineer meerdere vormen tot een groep met `group = aw.drawing.GroupShape(doc)` voor complexe diagrammen.
- Exporteer naar andere formaten zoals DOCX (`doc.save("output.docx")`) of HTML (`doc.save("output.html")`) om te zien hoe de schaduw wordt overgezet.

Elk van deze uitbreidingen bouwt voort op dezelfde kernconcepten: **schaduw toevoegen aan de vorm**, **de vulkleur van de vorm instellen**, en **het document opslaan als PDF** (of een ander formaat).

---

### Voorbeeld afbeelding *(optioneel)*

![Rechthoekvorm maken met schaduw in Python](https://example.com/rectangle-shadow.png "Rechthoekvorm maken met schaduw in Python")

*De screenshot toont de uiteindelijke PDF‑output met een lichtblauwe rechthoek en een subtiele buitenste schaduw.*

---

## Conclusie

We hebben elke stap doorlopen die nodig is om **een rechthoekvorm te maken** in Python, een aangepaste vulling toe te passen, **schaduw toe te voegen aan de vorm**, en uiteindelijk **het document op te slaan als PDF**. De code is volledig uitvoerbaar, de uitleg behandelt het *waarom* achter elke eigenschap, en we hebben de veelvoorkomende randgevallen en de volgende‑

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Maak Word‑document Java – Voeg rechthoekvorm toe met schaduweffect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Rechthoekvorm maken in Word met C# – Stapsgewijze gids](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Voeg een schaduw toe aan Word‑vorm in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}