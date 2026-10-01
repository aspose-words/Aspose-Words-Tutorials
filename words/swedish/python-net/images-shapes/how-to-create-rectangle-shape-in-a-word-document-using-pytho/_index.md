---
category: general
date: 2026-09-30
description: Lär dig hur du skapar en rektangulär form, applicerar skugga på formen
  och sparar Word med formen med Aspose.Words för Python.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- how to add shape
- apply shadow to shape
- set shadow blur
- save word with shape
language: sv
lastmod: 2026-09-30
og_description: Skapa en rektangulär form i ett Word‑dokument snabbt. Denna handledning
  visar hur du lägger till en form, applicerar skugga på formen, ställer in skuggans
  oskärpa och sparar Word med formen.
og_image_alt: Screenshot of a Word document showing a rectangle shape with a soft
  shadow
og_title: Skapa rektangelform i Word med Python – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Learn how to create rectangle shape, apply shadow to shape, and save
    Word with shape using Aspose.Words for Python.
  headline: How to create rectangle shape in a Word document using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- Shapes
title: Hur man skapar en rektangel i ett Word‑dokument med Python
url: /sv/python/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så skapar du en rektangelform i ett Word-dokument med Python

Om du behöver **create rectangle shape** i en Word‑fil, visar den här guiden en komplett, körbar lösning. Du får se hur du lägger till formen, applicerar en skuggeffekt, justerar suddigheten och slutligen **save Word with shape** så att resultatet kan öppnas i Microsoft Word eller någon kompatibel visare.

Exemplet använder **Aspose.Words for Python via .NET**, ett bibliotek som låter dig manipulera Word‑dokument utan att Microsoft Office är installerat. Ingen förhandskunskap om API:et krävs—bara grundläggande Python‑kunskaper.

## Vad du kommer att uppnå

- Infoga en rektangel i det första avsnittet i ett nytt dokument.  
- Konfigurera en mjuk skugga genom att sätta dess suddighet, förskjutning och färg.  
- Spara dokumentet till disk och verifiera det visuella resultatet.

## Förutsättningar

- Python 3.8 eller nyare.  
- `aspose-words`‑paketet installerat (`pip install aspose-words`).  
- Skrivbehörighet till utmatningskatalogen.

## Skapa rektangelform och konfigurera dess utseende

Det första steget är att skapa ett tomt dokument och lägga till en rektangelform i det. Formen fungerar som en duk för skuggeffekten.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Step 1: Create a new blank document
doc = aw.Document()

# Step 2: Add a rectangle shape to the first section
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Optional: Define the shape’s size and position (in points)
shape.width = aw.ConvertUtil.inch_to_point(2)   # 2 inches wide
shape.height = aw.ConvertUtil.inch_to_point(1)  # 1 inch tall
shape.left = aw.ConvertUtil.inch_to_point(1)    # 1 inch from the left margin
shape.top = aw.ConvertUtil.inch_to_point(1)     # 1 inch from the top margin
```

**Varför detta är viktigt:**  
Att skapa rektangeln ger dig ett konkret objekt (`shape`) som du senare kan formatera. Att ange explicita dimensioner säkerställer att formen ser likadan ut på alla plattformar.

## Hur man lägger till en form i ett Word-dokument

Även om koden ovan redan lägger till rektangeln, kan du behöva lägga till ytterligare former (t.ex. cirklar, pilar) senare. Samma mönster gäller: anropa `append_child` på dokumentets kropp och skicka den önskade `ShapeType`.

```python
# Example: Adding a second shape – an ellipse
ellipse = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.ELLIPSE)
)
ellipse.width = aw.ConvertUtil.inch_to_point(1.5)
ellipse.height = aw.ConvertUtil.inch_to_point(1)
ellipse.left = aw.ConvertUtil.inch_to_point(3.5)
ellipse.top = aw.ConvertUtil.inch_to_point(1)
```

**Tips:** Använd `ShapeType`‑enumerationen för att utforska alla stödda former. Detta gör koden läsbar och undviker magiska tal.

## Applicera skugga på formen och sätt skuggans suddighet

En skugga ger djup och visuellt intresse. Klassen `ShadowEffect` låter dig kontrollera suddighet, förskjutning och färg. Nedan applicerar vi en mjuk svart skugga på rektangeln.

```python
# Step 3: Configure a shadow effect for the rectangle
shadow = ShadowEffect()
shadow.blur = 5.0          # Sets the softness of the shadow edge
shadow.offset_x = 2.0      # Horizontal displacement from the shape
shadow.offset_y = 2.0      # Vertical displacement from the shape
shadow.color = aw.Color.black

# Step 4: Apply the shadow effect to the shape
shape.shadow = shadow
```

**Varför sätta suddighet?**  
`blur` bestämmer hur diffus skuggan blir. Ett lågt värde (t.ex. 1.0) ger en skarp kant, medan ett högre värde (t.ex. 5.0) skapar en mjuk övertoning, vilket ofta är mer estetiskt tilltalande.

**Särskilt fall:**  
Om du sätter `blur` till 0 blir skuggan en solid silhuett. Vissa visare kan rendera den med alias‑artefakter, så välj ett värde större än 0 för en mjukare utskrift.

## Spara Word med formen

Att spara dokumentet slutför alla ändringar. Metoden `save` skriver en `.docx`‑fil som vilken modern ordbehandlare som helst kan öppna.

```python
# Step 5: Save the document to see the result
output_path = "output.docx"   # Adjust the path as needed
doc.save(output_path)
print(f"Document saved to {output_path}")
```

När du öppnar `output.docx` ser du en rektangel placerad en tum från det övre vänstra hörnet, med en mjuk svart skugga förskjuten två punkter åt höger och neråt. Skuggans suddighet får formen att se ut som om den lyfts från sidan.

**Proffstips:**  
Om du behöver generera många dokument i en loop, återanvänd samma `Document`‑instans och rensa dess kropp mellan iterationer för att minska minnesbelastningen.

## Vanliga variationer och felsökning

| Situation | Vad som ska ändras | Orsak |
|-----------|--------------------|-------|
| Olika skuggfärg | `shadow.color = aw.Color.red` | Använd varumärkesfärger eller markera viktiga former. |
| Större skugga förskjutning | Increase `shadow.offset_x`/`offset_y` | Betona djup för UI‑mock‑ups. |
| Ingen skugga alls | Omit the `shape.shadow = shadow` line | Användbart för minimalistiska rapporter. |
| Exportera till PDF istället för DOCX | `doc.save("output.pdf")` | PDF är idealiskt för distribution i skrivskyddat format. |

Om formen inte visas, kontrollera att du lägger till den i rätt avsnitt (`get_first_section()`) och att dokumentet sparas efter ändringarna.

## Fullständigt, körbart exempel

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Create a new blank document
doc = aw.Document()

# Add a rectangle shape
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
shape.width = aw.ConvertUtil.inch_to_point(2)
shape.height = aw.ConvertUtil.inch_to_point(1)
shape.left = aw.ConvertUtil.inch_to_point(1)
shape.top = aw.ConvertUtil.inch_to_point(1)

# Configure and apply a shadow
shadow = ShadowEffect()
shadow.blur = 5.0
shadow.offset_x = 2.0
shadow.offset_y = 2.0
shadow.color = aw.Color.black
shape.shadow = shadow

# Save the document
output_path = "output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

När skriptet körs produceras `output.docx` som innehåller rektangeln med en mjuk skugga. Öppna filen i Microsoft Word för att bekräfta att den visuella effekten stämmer med beskrivningen.

## Slutsats

Du vet nu hur du **create rectangle shape**, **how to add shape** till ett Word‑dokument, **apply shadow to shape**, **set shadow blur**, och slutligen **save Word with shape** med Aspose.Words for Python. Samma mönster kan utökas till andra formtyper, färger och effekter, vilket ger dig full kontroll över dokumentgrafik utan att förlita dig på Office‑automatisering.

**Nästa steg**

- Experimentera med `Shape.fill` för att lägga till gradient‑ eller bildbakgrunder.  
- Använd `Paragraph`‑objekt för att placera text inuti rektangeln.  
- Kombinera flera former för att bygga komplexa diagram och exportera sedan till PDF för distribution.  

Känn dig fri att anpassa koden för dina egna rapporterings‑ eller mallbehov, och dela dina resultat i kommentarerna!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig behärska ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa Word-dokument Java – Lägg till rektangelform med skuggeffekt](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Skapa rektangelform, lägg till skugga & spara PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Aspose.Words Shape Shadow Tutorial – Lägg till en skugga på Word‑form i C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}