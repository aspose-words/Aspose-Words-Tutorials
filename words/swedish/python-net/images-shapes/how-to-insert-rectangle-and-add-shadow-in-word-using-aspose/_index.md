---
category: general
date: 2026-05-30
description: Hur man infogar en rektangel och lägger till skugga i Word med Aspose
  – en steg‑för‑steg Python‑guide för att skapa ett Word‑dokument med skuggeffekt
  på formen.
draft: false
keywords:
- how to insert rectangle
- add shadow to shape
- how to add shape shadow
- apply shadow effect word
- create word document aspose
language: sv
og_description: Hur man infogar en rektangel och lägger till skugga i Word med Aspose
  – lär dig att skapa ett Word‑dokument med skuggeffekt för former i Python.
og_title: Hur man infogar en rektangel och lägger till skugga i Word med Aspose
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: How to insert rectangle and add shadow in Word using Aspose – a step‑by‑step
    Python guide to create a Word document with shape shadow effect.
  headline: How to insert rectangle and add shadow in Word using Aspose
  type: TechArticle
- description: How to insert rectangle and add shadow in Word using Aspose – a step‑by‑step
    Python guide to create a Word document with shape shadow effect.
  name: How to insert rectangle and add shadow in Word using Aspose
  steps:
  - name: What each property does
    text: '| Property | Effect | Typical Range | |----------|--------|---------------|
      | `visible` | Turns the shadow on/off | `True` / `False` | | `distance` | How
      far the shadow sits from the shape | 2 – 10 pts | | `blur` | Softness of the
      shadow edges | 4 – 12 pts | | `color` | Shadow hue; dark gray is a sa'
  - name: Adding Multiple Shapes
    text: If you need more than one rectangle, simply repeat the `insert_shape` call.
      Remember to move the builder’s cursor (`builder.move_to(shape)`) or adjust `shape.left`/`shape.top`
      to avoid overlap.
  - name: Changing the Shape Type
    text: While this guide focuses on rectangles, the same pattern works for ovals,
      stars, or custom free‑form shapes. Replace `ShapeType.RECTANGLE` with `ShapeType.OVAL`,
      `ShapeType.CLOUD`, etc., and the shadow settings remain identical.
  - name: Saving to Other Formats
    text: 'Aspose.Words can export to PDF, PNG, or even XPS with a single line:'
  - name: Handling Large Documents
    text: When generating massive reports, consider calling `doc.update_page_layout()`
      after inserting all shapes. This forces a layout pass and can improve performance
      when you later convert to PDF.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word Automation
title: Hur man infogar en rektangel och lägger till skugga i Word med Aspose
url: /sv/python/images-shapes/how-to-insert-rectangle-and-add-shadow-in-word-using-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så här infogar du en rektangel och lägger till skugga i Word med Aspose

Har du någonsin funderat **hur man infogar en rektangel** i en Word‑fil utan att öppna användargränssnittet? Du är inte ensam. Många utvecklare behöver generera rapporter, fakturor eller certifikat i farten, och att rita en enkel rektangel med en fin skugga kan få resultatet att se professionellt ut. I den här handledningen går vi igenom exakt hur du skapar ett Word‑dokument, lägger till en rektangel‑form och applicerar en realistisk skugga med Aspose.Words för Python.

Vi täcker allt från att installera Aspose‑paketet till att finjustera skuggans avstånd, oskärpa och opacitet. När du är klar har du ett återanvändbart kodexempel som du kan slänga in i vilken automatiseringspipeline som helst. Ingen magi, bara tydlig kod och några praktiska tips.

## Förutsättningar

Innan vi dyker ner, se till att du har:

- Python 3.8+ installerat (koden fungerar på 3.9, 3.10 och nyare)
- En aktiv Aspose.Words för Python‑licens eller en gratis utvärderingsnyckel
- `aspose-words`‑paketet installerat via `pip install aspose-words`
- En skrivbar mapp där den genererade **create word document aspose** kommer att sparas

Det är allt—inga extra DLL‑filer, ingen COM‑interop, bara ren Python.

## Steg 1: Initiera dokumentet (How to create word document aspose)

Först och främst: du behöver ett nytt `Document`‑objekt. Tänk på det som en tom duk. Följande kod skapar dokumentet och en `DocumentBuilder` som låter oss infoga former.

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

**Varför detta är viktigt:** `DocumentBuilder` ger dig ett hög‑nivå‑API för att lägga till stycken, tabeller och—ja—former utan att behöva hantera lågnivå‑nodträd. Om du hoppar över buildern och manipulerar noder direkt får du en omständig kod som är svårare att underhålla.

## Steg 2: Infoga rektangeln (how to insert rectangle)

Nu infogar vi faktiskt **how to insert rectangle**. Aspose.Words behandlar en rektangel som en generisk formtyp. Du anger bredd och höjd i punkter (1 punkt ≈ 1/72 tum). Anpassa gärna siffrorna efter ditt layoutbehov.

```python
# Step 2: Insert a rectangle shape of the desired size
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

> **Proffstips:** Om du vill att rektangeln ska placeras på en specifik plats på sidan, sätt `shape.left` och `shape.top` efter infogandet. Detta ger dig pixel‑perfekt kontroll.

## Steg 3: Åtkomst till formens ShadowFormat (add shadow to shape)

En forms visuella stil lever i dess `ShadowFormat`. Genom att hämta den får vi tillgång till varje egenskap som definierar skuggans utseende.

```python
# Step 3: Access the shape's shadow format
shadow = shape.shadow_format
```

Vid detta tillfälle är skuggan osynlig—tänk på den som ett dolt lager som väntar på dina instruktioner.

## Steg 4: Konfigurera skuggan (how to add shape shadow, apply shadow effect word)

Här händer magin. Vi slår på skuggan och justerar dess utseende. Värdena nedan ger en mjuk, diagonal skugga som fungerar bra i de flesta dokument, men du kan experimentera.

```python
# Step 4: Make the shadow visible and configure its appearance
shadow.visible = True                # Show the shadow
shadow.distance = 5.0                # Distance from the shape (points)
shadow.blur = 8.0                    # Blur radius (points)
shadow.color = aw.Color.dark_grey   # Shadow color
shadow.opacity = 0.6                 # Opacity (0‑1)
shadow.angle = 45.0                  # Direction in degrees
```

### Vad varje egenskap gör

| Egenskap | Effekt | Typiskt intervall |
|----------|--------|-------------------|
| `visible` | Slår på/av skuggan | `True` / `False` |
| `distance` | Hur långt skuggan sitter från formen | 2 – 10 pts |
| `blur` | Mjukhet på skuggans kanter | 4 – 12 pts |
| `color` | Skuggans färg; mörkgrå är ett säkert standardval | Any `aw.Color` |
| `opacity` | Transparens; 0 = osynlig, 1 = solid | 0.3 – 0.8 för subtil look |
| `angle` | Riktning på ljuset | 0 – 360° |

**Varför justera dessa?** En väl‑tuned skugga kan få en platt rektangel att verka lyftad från sidan, vilket ger djup utan bilder. Om du sätter `opacity` för högt blir skuggan hård; för lågt försvinner den.

## Steg 5: Spara dokumentet (create word document aspose)

Till sist skriver vi filen till disk. Du kan använda vilket filformat som helst som stöds av Aspose.Words (`.docx`, `.pdf`, `.html`). I den här handledningen håller vi oss till `.docx`.

```python
# Step 5: Save the document with the shaped shadow
output_path = "output/ShapeWithShadow.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Öppna den resulterande filen i Microsoft Word, så ser du en skarp rektangel med en subtil skugga—precis vad du förväntar dig av en professionellt designad mall.

![how to insert rectangle shape with shadow using Aspose.Words](/images/rectangle-shadow.png){alt="hur man infogar rektangel med skugga med Aspose.Words"}

*Skärmdumpen (ovan) visar rektangeln med skuggan applicerad. Lägg märke till den mjuka oskärpan och 45°‑vinkeln, vilket ger ett naturligt intryck.*

## Vanliga variationer och kantfall

### Lägga till flera former

Om du behöver mer än en rektangel, upprepa helt enkelt `insert_shape`‑anropet. Kom ihåg att flytta builderns markör (`builder.move_to(shape)`) eller justera `shape.left`/`shape.top` för att undvika överlappning.

```python
# Example: Insert a second rectangle 200 points to the right
second_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
second_shape.left = shape.left + 200
second_shape.top = shape.top
```

### Ändra formtypen

Även om den här guiden fokuserar på rektanglar fungerar samma mönster för ovaler, stjärnor eller anpassade fri‑form‑former. Byt ut `ShapeType.RECTANGLE` mot `ShapeType.OVAL`, `ShapeType.CLOUD` osv., och skugginställningarna förblir identiska.

### Spara till andra format

Aspose.Words kan exportera till PDF, PNG eller till och med XPS med en enda rad:

```python
doc.save("output/ShapeWithShadow.pdf")
```

Skuggrenderingen bevaras över format, så din PDF ser exakt likadan ut som Word‑filen.

### Hantera stora dokument

När du genererar massiva rapporter, överväg att anropa `doc.update_page_layout()` efter att alla former har infogats. Detta tvingar ett layoutpass och kan förbättra prestandan när du senare konverterar till PDF.

## Fullt fungerande exempel (Alla steg kombinerade)

Nedan är det kompletta skriptet som du kan kopiera‑klistra in i en fil med namnet `rectangle_shadow.py`. Kör det med `python rectangle_shadow.py` och kontrollera mappen `output`.

```python
import aspose.words as aw
import os

# Ensure the output directory exists
os.makedirs("output", exist_ok=True)

# Initialize the document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Insert a rectangle
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

# Configure the shadow
shadow = shape.shadow_format
shadow.visible = True
shadow.distance = 5.0
shadow.blur = 8.0
shadow.color = aw.Color.dark_grey
shadow.opacity = 0.6
shadow.angle = 45.0

# Save the document
output_path = "output/ShapeWithShadow.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

När du kör detta skript får du exakt samma dokument som vi diskuterade tidigare. Känn dig fri att justera siffrorna; koden är avsiktligt enkel så att du kan experimentera utan rädsla.

## Vanliga frågor

**Q: Fungerar detta på Linux?**


## Vad bör du lära dig härnäst?

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}