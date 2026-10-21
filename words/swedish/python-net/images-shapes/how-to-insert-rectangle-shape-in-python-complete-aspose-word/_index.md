---
category: general
date: 2026-06-27
description: Lär dig hur du infogar en rektangel i Python med Aspose.Words, ändrar
  skuggfärgen, lägger till en yttre skugga och applicerar skuggeffekt på formen –
  allt i en handledning.
draft: false
keywords:
- how to insert rectangle shape
- how to change shadow color
- how to add outer shadow
- apply shadow effect to shape
language: sv
og_description: Lär dig hur du infogar en rektangel i Python, ändrar dess skuggfärg,
  lägger till en yttre skugga och applicerar en skuggeffekt på formen med Aspose.Words.
og_title: Hur man infogar en rektangelform i Python – Aspose.Words-handledning
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  headline: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  name: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: Pro tip
    text: If you need the rectangle positioned at a specific location, use `builder.move_to`
      before inserting, or adjust `rectangle.left` and `rectangle.top` after creation.
  - name: Edge case
    text: If you forget to set `shadow.opacity`, the default is fully opaque, which
      can make the shadow look like a solid shape. Always pair a color change with
      an appropriate opacity level.
  - name: Common pitfalls
    text: '- **Missing directory:** `doc.save` will raise an error if the folder doesn’t
      exist. Create it first or use `os.makedirs`. - **Version mismatch:** The shadow
      API requires Aspose.Words 22.9+; older versions silently ignore shadow settings.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
title: Hur man infogar en rektangel i Python – Komplett Aspose.Words-guide
url: /sv/python/images-shapes/how-to-insert-rectangle-shape-in-python-complete-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man infogar en rektangel i Python – Komplett Aspose.Words‑guide

Har du någonsin undrat **hur man infogar en rektangel** i ett Word‑dokument med Python? Du är inte ensam—många utvecklare stöter på detta när de automatiserar rapporter eller skapar mallar. Den goda nyheten är att Aspose.Words gör det enkelt, och i den här handledningen går vi igenom hela processen, från att rita rektangeln till att ge den en snygg yttre skugga.

Vi kommer också att gå igenom **hur man ändrar skuggans färg**, **hur man lägger till en yttre skugga**, och det sista steget **att applicera skuggeffekten på formen**. När du är klar har du en fullt stylad rektangel som du kan släppa in i vilken .docx‑fil som helst programmässigt.

## Förutsättningar

- Python 3.8+ installerat på din maskin  
- Aspose.Words för Python via `pip install aspose-words`  
- Grundläggande kunskap om Python‑skriptning (ingen djup Word‑API‑kunskap krävs)  

Om du redan har detta, bra—låt oss dyka ner. Om inte, hämta först biblioteket; resten av guiden förutsätter att importen fungerar utan problem.

## Hur man infogar en rektangel med Aspose.Words för Python

Det första steget är exakt vad nyckelordet lovar: **hur man infogar en rektangel**. Vi skapar ett nytt dokument, startar en `DocumentBuilder` och placerar en rektangel på sidan.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a fresh document and a builder to add content
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Insert a rectangle shape of 200x100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# Optional: give the rectangle a light fill so the shadow is visible
rectangle.fill_color = aw.drawing.Color.light_blue
```

> **Varför detta är viktigt:** Anropet `insert_shape` är kärnan i *hur man infogar en rektangel*. Det returnerar ett `Shape`‑objekt som du senare kan manipulera—storlek, position, fyllning, kanter, du bestämmer. Observera att vi också sätter en `fill_color`; utan den kan skuggan smälta in i en vit sida och bli svår att se.

### Pro‑tips
Om du behöver rektangeln på en specifik plats, använd `builder.move_to` innan du infogar, eller justera `rectangle.left` och `rectangle.top` efter skapandet.

## Ändra skuggans färg på en form

Nu när rektangeln finns i dokumentet, låt oss svara på **hur man ändrar skuggans färg**. Aspose.Words exponerar ett `ShadowEffect`‑objekt där du kan sätta `color`‑egenskapen till vilket RGB‑värde som helst.

```python
# Create a shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # we’ll also cover outer shadow later
shadow.blur_radius = 8.0                  # smooth edges
shadow.distance = 6.0                     # how far the shadow sits from the shape
shadow.direction = 45                     # angle in degrees
shadow.opacity = 0.6                      # semi‑transparent

# Change the shadow color to a deep gray instead of black
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)

# Apply the shadow to our rectangle
rectangle.shadow = shadow
```

> **Varför du skulle vilja detta:** En mörk svart skugga kan bli för hård, särskilt i ljusa dokument. Genom att justera färgen kan du matcha företagets varumärke eller helt enkelt uppnå en mjukare visuell effekt.

### Särskilt fall
Om du glömmer att sätta `shadow.opacity`, är standardvärdet helt ogenomskinligt, vilket kan få skuggan att se ut som en solid form. Para alltid en färgändring med en lämplig opacitetsnivå.

## Lägga till en yttre skuggeffekt

Nästa fråga många ställer är **hur man lägger till en yttre skugga**. Flaggan `ShadowStyle.OUTER` talar om för Aspose.Words att rendera skuggan utanför formens kontur snarare än inuti den.

Kodsnutten ovan använder redan `ShadowStyle.OUTER`, men låt oss isolera denna inställning för tydlighet:

```python
# Ensure the shadow style is outer
shadow.style = ShadowStyle.OUTER
```

Om du byter till `ShadowStyle.INNER` kommer skuggan att visas *inuti* rektangeln, vilket är användbart för präglade effekter. För de flesta dokumentdesign‑scenarier ger den yttre stilen ett naturligt drop‑shadow‑utseende.

## Applicera skuggeffekten på din form

Vi har redan **applicerat skuggeffekten på formen** genom att tilldela `rectangle.shadow = shadow`. Låt oss samla allt och spara dokumentet, så att vi kan bekräfta att effekten kvarstår.

```python
# Save the document – choose a folder you have write access to
output_path = "output/RectangleWithShadow.docx"
doc.save(output_path)

print(f"Document saved to {output_path}. Open it to see the rectangle with its outer shadow.")
```

När du öppnar `RectangleWithShadow.docx` i Microsoft Word bör du se en ljusblå rektangel med en subtil grå yttre skugga som kastas i en 45°‑vinkel. Skuggan kommer att vara lätt suddig och förskjuten, precis som vi konfigurerade.

### Vanliga fallgropar
- **Saknad katalog:** `doc.save` ger ett fel om mappen inte finns. Skapa den först eller använd `os.makedirs`.
- **Versionsmismatch:** Skugg‑API:t kräver Aspose.Words 22.9+; äldre versioner ignorerar skugginställningarna tyst.

## Fullt fungerande exempel

Nedan är det kompletta, körklara skriptet som kombinerar alla stegen. Kopiera‑klistra in det i en fil som heter `rectangle_shadow.py` och kör med `python rectangle_shadow.py`.

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Create a new document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2️⃣ Insert the rectangle shape (how to insert rectangle shape)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle.fill_color = aw.drawing.Color.light_blue   # make the shape visible

# 3️⃣ Define the shadow (how to change shadow color, how to add outer shadow)
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # outer shadow
shadow.blur_radius = 8.0
shadow.distance = 6.0
shadow.direction = 45
shadow.opacity = 0.6
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)  # custom gray

# 4️⃣ Apply the shadow (apply shadow effect to shape)
rectangle.shadow = shadow

# 5️⃣ Save the file
output_path = os.path.join(output_dir, "RectangleWithShadow.docx")
doc.save(output_path)

print(f"✅ Document generated: {output_path}")
```

**Förväntat resultat:** Ett Word‑dokument (`RectangleWithShadow.docx`) som innehåller en enda rektangel med en grå yttre skugga. Öppna det i Word för att verifiera den visuella effekten.

## Vanliga frågor

| Fråga | Svar |
|----------|--------|
| *Kan jag använda en annan formtyp?* | Absolut—byt ut `ShapeType.RECTANGLE` mot `ShapeType.OVAL`, `ShapeType.TRIANGLE`, osv., och samma skugglogik gäller. |
| *Vad händer om jag behöver en tjockare kant?* | Sätt `rectangle.line_width = 2.0` (points) innan du applicerar skuggan. |
| *Är det möjligt att animera skuggan?* | Inte direkt med Aspose.Words; du måste exportera till HTML/CSS för animation. |
| *Fungerar detta på macOS?* | Ja—Aspose.Words är plattformsoberoende så länge Python körs. |

## Slutsats

Vi har gått igenom **hur man infogar en rektangel**, demonstrerat **hur man ändrar skuggans färg**, förklarat **hur man lägger till en yttre skugga**, och slutligen visat dig **hur man applicerar skuggeffekten på formen** med Aspose.Words för Python. Det kompletta skriptet är redo att släppas in i vilken automatiseringspipeline som helst, och ger dig en professionell rektangel med en polerad skugga på några sekunder.

Redo för nästa steg? Prova att byta fyllningsfärg, experimentera med olika `direction`‑vinklar, eller lägga till flera former på samma sida. Du kan också utforska Aspose.Words rika textformaterings‑API för att kombinera skuggor med formaterad text—perfekt för iögonfallande rapporter.

Om du tyckte att den här handledningen var hjälpsam, ge den en tumme upp, dela den med kollegor, eller lämna en kommentar med dina egna varianter. Lycka till med kodandet!

![Diagram som visar hur man infogar en rektangel med en yttre skugga i ett Word‑dokument](/images/rectangle-shadow.png)


## Vad bör du lära dig härnäst?


Följande handledningar täcker närliggande ämnen som bygger vidare på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}