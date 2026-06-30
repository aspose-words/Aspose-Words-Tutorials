---
category: general
date: 2026-06-30
description: Lägg till skugga på en form med Aspose.Words för Python. Lär dig hur
  du ställer in skuggavstånd, anpassar suddighet och snabbt sparar en PDF med formens
  skugga.
draft: false
keywords:
- add shadow to shape
- how to set shadow distance
- how to add shape shadow
- Aspose.Words Python shadow
- shape formatting Python
language: sv
og_description: Lägg till skugga på en form i ett Word‑dokument med Aspose.Words för
  Python. Den här handledningen visar hur du ställer in skuggavstånd, oskärpa och
  färg och sedan sparar som PDF.
og_title: Lägg till skugga på form i Python – Komplett Aspose.Words-guide
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Add shadow to shape using Aspose.Words for Python. Learn how to set
    shadow distance, customize blur, and save a PDF with shape shadow quickly.
  headline: Add Shadow to Shape in Python with Aspose.Words – Full Guide
  type: TechArticle
- description: Add shadow to shape using Aspose.Words for Python. Learn how to set
    shadow distance, customize blur, and save a PDF with shape shadow quickly.
  name: Add Shadow to Shape in Python with Aspose.Words – Full Guide
  steps:
  - name: What if I need a different shape?
    text: Replace `aw.drawing.ShapeType.RECTANGLE` with any other enum value, e.g.,
      `aw.drawing.ShapeType.ELLIPSE`. The same shadow properties apply—no extra code
      needed.
  - name: Can I apply a shadow to multiple shapes at once?
    text: 'Yes. Loop over the shapes you create and configure each `shadow_format`
      individually. Here’s a quick snippet:'
  - name: How do I change the shadow’s opacity?
    text: 'Use the `shadow.transparency` property (0 = opaque, 1 = fully transparent):'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: Lägg till skugga på form i Python med Aspose.Words – Fullständig guide
url: /sv/python/images-shapes/add-shadow-to-shape-in-python-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lägg till skugga på form i Python med Aspose.Words – Fullständig guide

Att lägga till skugga på en form i ett Word‑dokument med Aspose.Words för Python är enklare än du tror. Om du någonsin har undrat **hur man ställer in skuggavstånd** eller **hur man lägger till formskugga** för ett polerat utseende, så har den här guiden svaret.

Under de kommande minuterna går vi igenom allt du behöver: från att skapa ett nytt dokument, infoga en rektangel, justera dess skugginställningar, till att slutligen spara en PDF som visar effekten. I slutet kommer du kunna lägga en skugga på vilken form som helst — rektangel, ellips eller egen ritning — utan att rota i API‑dokumentationen.

> **Förutsättningar** – Du bör ha Python 3.7+ installerat, en Aspose.Words för Python‑licens (eller en gratis utvärdering), och grundläggande kunskaper i Python‑skriptning. Inga andra externa bibliotek krävs.

---

## Lägg till skugga på form – Steg‑för‑steg‑översikt

Nedan är en snabb färdplan för vad vi ska åstadkomma:

1. **Skapa ett nytt dokument** och en `DocumentBuilder` för att redigera det.  
2. **Infoga en rektangel‑form** i önskad storlek.  
3. **Aktivera och anpassa skuggan** – här glänser huvudnyckelordet.  
4. **Spara dokumentet** som en PDF som behåller formens skugga.

Varje steg är uppdelat i sin egen sektion, så du kan kopiera‑klistra kodsnuttarna direkt i din IDE.

---

## Steg 1: Initiera dokumentet och byggaren

Först och främst—utan ett `Document` har du inget att arbeta med. `DocumentBuilder` är din pensel.

```python
import aspose.words as aw

# Create a new, empty Word document
document = aw.Document()

# Attach a builder to the document for easy editing
builder = aw.DocumentBuilder(document)
```

*Varför detta är viktigt*: `Document`‑objektet representerar hela filen, medan `DocumentBuilder` förenklar insättning av text, tabeller och former. Tänk på byggaren som en markör du kan flytta runt på sidan.

---

## Steg 2: Infoga en rektangel‑form

Nu lägger vi till en rektangel—vår duk för skuggeffekten. Du kan ersätta `RECTANGLE` med `ELLIPSE`, `STAR` eller någon annan `ShapeType` om du behöver en annan geometri.

```python
# Insert a rectangle with width=200pt and height=100pt
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

*Proffstips*: Dimensionerna är i punkter (1 pt ≈ 1/72 tum). Anpassa dem efter din layout; skuggan skalas automatiskt.

---

## Hur man ställer in skuggavstånd

Skuggans **avstånd** bestämmer hur långt den visas från formen. Ett större avstånd efterliknar en ljuskälla längre bort, medan ett mindre värde ger en subtil lyftning.

```python
# Access the shadow format of the shape
shadow = rectangle_shape.shadow_format

# Make the shadow visible
shadow.visible = True

# Set the distance (in points) from the shape
shadow.distance = 4.0          # <-- this is the "how to set shadow distance" part
```

> **Obs**: Avståndet fungerar tillsammans med `angle`. Att ändra vinkeln roterar skuggan runt formen, medan `distance` skjuter den utåt.

---

## Hur man lägger till formskugga – Anpassa suddighet, färg och vinkel

Att lägga till en skugga handlar inte bara om att slå på den; du vill ofta finjustera suddighet, färg och riktning för en realistisk effekt.

```python
# Define how blurry the shadow should be (larger = softer)
shadow.blur_radius = 5.0       # Soft edge for a natural look

# Choose the direction (in degrees). 45° points down‑right.
shadow.angle = 45

# Set the shadow color – black works for most cases
shadow.color = aw.drawing.Color.black
```

*Varför dessa inställningar?*  
- **Blur radius** mjukar upp kanten och förhindrar en hård siluett.  
- **Angle** simulerar ljuskällan; 45° är ett vanligt standardvärde som ser balanserat ut.  
- **Color** kan vara vilket `Color`‑objekt som helst; prova `Color.gray` för en mildare effekt.

---

## Steg 4: Spara dokumentet som PDF

När formen och dess skugga är klara är det en enkel sak att spara resultatet. Aspose.Words hanterar konverteringen till PDF automatiskt och bevarar den visuella kvaliteten.

```python
# Save the document to a PDF file (adjust the path as needed)
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
document.save(output_path)
print(f"Document saved to {output_path}")
```

*Förväntat resultat*: Öppna den genererade `ShadowShape.pdf`. Du kommer att se en enda sida med en 200 × 100 pt rektangel, vars skugga kastas 4 pt bort i en 45°‑vinkel, suddad med 5 pt. Skuggan bör visas som en subtil grå‑svart halo som omfamnar formen.

---

## Vanliga frågor & kantfall

### Vad händer om jag behöver en annan form?

Ersätt `aw.drawing.ShapeType.RECTANGLE` med vilket annat enum‑värde som helst, t.ex. `aw.drawing.ShapeType.ELLIPSE`. Samma skugginställningar gäller—ingen extra kod behövs.

### Kan jag applicera en skugga på flera former samtidigt?

Ja. Loopa över de former du skapar och konfigurera varje `shadow_format` individuellt. Här är ett snabbt kodexempel:

```python
for shape_type in [aw.drawing.ShapeType.RECTANGLE, aw.drawing.ShapeType.ELLIPSE]:
    shp = builder.insert_shape(shape_type, 150, 80)
    shp.shadow_format.visible = True
    shp.shadow_format.distance = 3.0
    shp.shadow_format.blur_radius = 4.0
```

### Hur ändrar jag skuggans opacitet?

Använd egenskapen `shadow.transparency` (0 = opak, 1 = fullt transparent):

```python
shadow.transparency = 0.3   # 30 % transparent
```

---

## Fullt fungerande exempel

Nedan är hela skriptet—kopiera det, justera utmatningsmappen och kör det. Inga delar saknas.

```python
import aspose.words as aw

# 1️⃣ Create a new document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert a rectangle shape (200 × 100 pt)
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Enable and configure the shadow (add shadow to shape)
shadow = rectangle_shape.shadow_format
shadow.visible = True                # Show the shadow
shadow.blur_radius = 5.0             # Soft edges
shadow.distance = 4.0                # How far the shadow lies from the shape
shadow.angle = 45                    # Direction of the light source
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.0            # Fully opaque (optional)

# 4️⃣ Save as PDF
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
document.save(output_path)
print(f"PDF with shape shadow saved at: {output_path}")
```

Kör skriptet, öppna sedan den resulterande PDF‑filen. Du bör se rektangeln med en skarp, förskjuten skugga—precis vad **add shadow to shape** lovar.

---

## Slutsats

Vi har just demonstrerat hur man **add shadow to shape** i ett Word‑dokument med Aspose.Words för Python, och gått igenom de väsentliga stegen för att **set shadow distance**, anpassa suddighet, vinkel och färg, samt slutligen exportera en PDF som behåller effekten. Denna teknik fungerar för alla formtyper, och du kan utöka den med loopar, opacitetsjusteringar eller till och med gradient‑skuggor.

Redo för nästa utmaning? Prova att kombinera flera skuggor, lager på lager‑former, eller generera en rapport där varje diagram får sin egen stiliserade skugga. Att experimentera kommer att befästa koncepten och avslöja nya möjligheter för dokumentautomatisering.

Om du fann den här guiden hjälpsam, dela gärna den, ge ett stjärnmärke till Aspose.Words‑repoet, eller lämna en kommentar med dina egna tips för skuggjustering. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}