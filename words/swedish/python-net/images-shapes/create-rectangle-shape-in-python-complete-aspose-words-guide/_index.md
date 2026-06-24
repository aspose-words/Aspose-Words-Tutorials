---
category: general
date: 2026-06-24
description: Skapa en rektangel i Python med Aspose.Words, lär dig hur du lägger till
  skugga på formen, ställer in skuggvinkeln och sparar dokumentet som PDF på några
  minuter.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shape shadow
- set shadow angle
language: sv
og_description: Skapa rektangel i Python, lägg till skugga på formen, ställ in skuggvinkeln
  och spara dokumentet som PDF med Aspose.Words. Följ den här steg‑för‑steg‑guiden.
og_title: Skapa rektangelform i Python – Fullständig Aspose.Words-handledning
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  headline: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  name: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: What if I need a different shape?
    text: Aspose.Words supports many `ShapeType` values (ellipse, star, callout, etc.).
      Simply replace `aw.drawing.ShapeType.RECTANGLE` with the desired enum, like
      `aw.drawing.ShapeType.ELLIPSE`.
  - name: Can I add multiple shadows?
    text: The API exposes only one `ShadowFormat` per shape, but you can simulate
      multiple shadows by duplicating the shape, offsetting each copy, and adjusting
      transparency.
  - name: How do I change the shadow color to match my brand?
    text: Just set `shadow.color` to any `aw.drawing.Color`. For a brand blue, use
      `aw.drawing.Color.from_argb(255, 0, 120, 215)`.
  - name: What about saving as DOCX instead of PDF?
    text: Replace `document.save(pdf_path)` with `document.save("output/shadowed_rectangle.docx")`.
      The shadow rendering is preserved across both formats.
  - name: Does the shadow work on older PDF viewers?
    text: Aspose.Words renders the shadow as a vector effect, which is widely supported.
      However, very old viewers might flatten the effect; testing on your target audience’s
      devices is always a good habit.
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: Skapa rektangelform i Python – Komplett Aspose.Words-guide
url: /sv/python/images-shapes/create-rectangle-shape-in-python-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa rektangelform i Python – Komplett Aspose.Words-guide

Har du någonsin undrat hur man **create rectangle shape** i ett Word-dokument med Python? Kanske du behöver en fet call‑out‑ruta, en visuell ledtråd för ett diagram, eller bara en snygg rektangel för en rapport. Oavsett så har du hamnat på rätt plats. I den här handledningen går vi igenom hela processen—från att infoga rektangeln, till att lägga till en subtil skugga, justera skuggvinkeln, och slutligen **save document as PDF** så att du kan dela den med vem som helst.

Vi kommer att använda **Aspose.Words for Python via .NET**, ett kraftfullt bibliotek som låter dig manipulera Word-filer utan att någonsin öppna Word själv. I slutet av den här guiden kommer du att kunna svara på frågan *“how to add shape shadow”* med självförtroende, och du kommer att ha ett färdigt skript som du kan släppa in i vilket projekt som helst.

---

## Vad du behöver

- **Python 3.8+** installerat på din maskin.  
- **Aspose.Words for Python via .NET** (`aspose-words`-paketet). Installera det med:

  ```bash
  pip install aspose-words
  ```

- En skrivbar mapp där den genererade PDF-filen kommer att sparas.  
- (Valfritt) En IDE eller textredigerare—VS Code fungerar bra.

Det är allt. Inga extra DLL-filer, ingen Office-installation, bara ett enda pip‑paket.

## Steg 1: Ställ in dokumentet och byggaren

Det första du behöver göra är **create rectangle shape**‑vänliga objekt: ett `Document` och en `DocumentBuilder`. Tänk på byggaren som din penna; den ritar allt åt dig.

```python
import aspose.words as aw

# Initialize a new blank document
document = aw.Document()

# DocumentBuilder gives us a convenient way to add content
builder = aw.DocumentBuilder(document)
```

> **Varför detta är viktigt:** `Document`‑objektet representerar hela .docx‑filen, medan `DocumentBuilder` tillhandahåller metoder som `insert_shape` som gör det enkelt att rita former.

## Steg 2: Infoga rektangelformen

Nu när vi har en byggare kan vi äntligen **create rectangle shape**. Metoden `insert_shape` kräver tre argument: formtypen, bredd och höjd. Vi kommer att använda 200 pt bredd och 100 pt höjd för en fin proportion.

```python
# Insert a rectangle with a width of 200 points and a height of 100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

Vid detta tillfälle har du lyckats **create rectangle shape** i ditt dokument. Om du öppnar den genererade DOCX‑filen (det gör vi senare) kommer du att se en enkel rektangel där markören var.

## Steg 3: Åtkomst till skuggformatobjektet

För att **add shadow to shape** måste vi först hämta formens skuggformat. Varje form i Aspose.Words har en egenskap `shadow_format` som exponerar alla skuggrelaterade inställningar.

```python
# Grab the shadow formatting object for later tweaks
shadow = rectangle.shadow_format
```

Att ha `shadow`‑referensen låter oss växla synlighet, oskärpa, avstånd, vinkel, färg och transparens—allt i några kodrader.

## Steg 4: Aktivera skuggan och konfigurera dess utseende

Här händer magin. Vi kommer att **add shadow to shape**, göra den lite oskarp, förskjuta den lite, sätta riktningen (delen **set shadow angle**), och ge den en halvtransparent svart nyans.

```python
# Turn the shadow on
shadow.visible = True

# Soften the edges – a blur radius of 8 points looks natural
shadow.blur_radius = 8.0

# Push the shadow away from the rectangle by 5 points
shadow.distance = 5.0

# Set the direction of the light source – 45 degrees creates a diagonal drop
shadow.angle = 45

# Choose a color; black works well for most documents
shadow.color = aw.drawing.Color.black

# Make the shadow 30 % transparent for a subtle effect
shadow.transparency = 0.3
```

> **Proffstips:** Om du någonsin behöver en mer dramatisk effekt, öka `blur_radius` eller sänk `transparency`. Omvänt kan en skarp, helt ogenomskinlig skugga uppnås med `blur_radius = 0` och `transparency = 0`.

## Steg 5: Spara dokumentet som PDF

Vi har **create rectangle shape**, vi har **add shadow to shape**, och nu kommer vi att **save document as PDF** så att resultatet ser identiskt ut på alla enheter. Aspose.Words gör detta till en endaste rad.

```python
# Define where you want the PDF to land
output_path = "output/shadowed_rectangle.pdf"

# Save the whole document (including the rectangle with its shadow) as PDF
document.save(output_path)
print(f"PDF saved to {output_path}")
```

När du kör skriptet kommer `shadowed_rectangle.pdf` att genereras i `output`‑mappen. Öppna den med någon PDF‑visare så ser du en ren rektangel med en mjuk, 45‑gradig skugga—precis som vi konfigurerade.

## Fullständigt fungerande exempel

Nedan är det kompletta, färdiga skriptet som kombinerar alla stegen ovan. Kopiera‑klistra in det i en fil med namnet `create_rectangle_with_shadow.py` och kör `python create_rectangle_with_shadow.py`.

```python
import aspose.words as aw
import os

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Initialize document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert the rectangle shape (200 pt × 100 pt)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Access shadow formatting
shadow = rectangle.shadow_format

# 4️⃣ Configure shadow – visible, blurred, offset, angled, colored, semi‑transparent
shadow.visible = True
shadow.blur_radius = 8.0          # softer edges
shadow.distance = 5.0            # how far the shadow sits from the shape
shadow.angle = 45                # direction in degrees – this is the **set shadow angle** step
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.3        # 30 % transparent

# 5️⃣ Save the document as PDF
pdf_path = os.path.join(output_dir, "shadowed_rectangle.pdf")
document.save(pdf_path)

print(f"✅ PDF created at: {pdf_path}")
```

**Förväntat resultat:** En PDF‑fil som visar en enda rektangel med en mjuk, diagonal skugga. Inga extra sidor, inga dolda artefakter—bara den form vi skapade.

## Vanliga frågor & kantfall

### Vad händer om jag behöver en annan form?

Aspose.Words stöder många `ShapeType`‑värden (ellipse, stjärna, callout, etc.). Byt helt enkelt ut `aw.drawing.ShapeType.RECTANGLE` mot den önskade enumen, till exempel `aw.drawing.ShapeType.ELLIPSE`.

### Kan jag lägga till flera skuggor?

API:et exponerar bara en `ShadowFormat` per form, men du kan simulera flera skuggor genom att duplicera formen, förskjuta varje kopia och justera transparensen.

### Hur ändrar jag skuggfärgen så att den matchar mitt varumärke?

Ställ bara in `shadow.color` till någon `aw.drawing.Color`. För en varumärkesblå, använd `aw.drawing.Color.from_argb(255, 0, 120, 215)`.

### Vad händer om jag sparar som DOCX istället för PDF?

Byt ut `document.save(pdf_path)` mot `document.save("output/shadowed_rectangle.docx")`. Skuggrenderingen bevaras i båda formaten.

### Fungerar skuggan i äldre PDF‑visare?

Aspose.Words renderar skuggan som en vektoreffekt, vilket är brett stödjande. Dock kan mycket gamla visare platta till effekten; testning på din målgrupps enheter är alltid en bra vana.

## Tips för att polera din PDF

- **Lägg till en kant:** `rectangle.line_format.width = 1.5` och ange en färg för en skarp kontur.  
- **Centrera rektangeln:** Använd `builder.move_to_document_start()` innan du infogar, sedan `builder.paragraph_format.alignment = aw.ParagraphAlignment.CENTER`.  
- **Kombinera med text:** Infoga en `TextFragment` efter rektangeln för att märka den, t.ex. `"Important Section"`.

Dessa små justeringar kan förvandla en enkel rektangel till en polerad call‑out‑ruta som ser professionell ut i rapporter, förslag eller e‑böcker.

## Slutsats

Du har nu ett gediget, end‑to‑end‑recept för att **create rectangle shape** i Python, **add shadow to shape**, **set shadow angle**, och **save document as PDF** med Aspose.Words. Stegen är enkla, koden är helt självständig, och du har sett varför varje rad är viktig—från att initiera dokumentet till att polera den slutgiltiga PDF‑filen.

Nästa steg kan vara att utforska **how to add shape shadow** i mer komplexa ritningar, experimentera med gradientfyllningar, eller generera tabeller i dina former. Biblioteket stödjer också att länka former till bokmärken, vilket kan vara praktiskt för interaktiva PDF‑filer.

Har du ett knep du provat? Dela det i kommentarerna, eller ställ eventuella kvarstående frågor. Lycka till med kodandet, och njut av att lägga till extra djup i dina dokument!

![Rektangel med skugga – exempel på create rectangle shape i Python](/images/rectangle-shadow.png)

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa Word-dokument Java – Lägg till rektangelform med skuggeffekt](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow‑handledning – Lägg till en skugga till Word‑form i C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Skapa rektangelform i Word med C# – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}