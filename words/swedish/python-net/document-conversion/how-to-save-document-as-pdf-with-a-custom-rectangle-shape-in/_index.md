---
category: general
date: 2026-10-07
description: Lär dig hur du sparar dokument som PDF samtidigt som du lägger till en
  rektangel och en anpassad skugga med Aspose.Words för Python. Steg‑för‑steg‑kod
  inkluderad.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save document as pdf
- add rectangle shape
- export word to pdf
- set rectangle dimensions
- draw rectangle word
language: sv
lastmod: 2026-10-07
og_description: Spara dokumentet som PDF med en anpassad rektangelform med Aspose.Words
  för Python. Följ hela exemplet för att rita, formge och exportera Word till PDF.
og_image_alt: Screenshot of the generated PDF showing the rectangle shape after save
  document as pdf
og_title: Spara dokument som PDF med en rektangelform – komplett Python‑guide
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  headline: How to save document as PDF with a custom rectangle shape in Python
  type: TechArticle
- description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  name: How to save document as PDF with a custom rectangle shape in Python
  steps:
  - name: Initialize a new blank document
    text: '```python import aspose.words as aw'
  - name: Add rectangle shape to the document
    text: '```python # Create a rectangle shape and attach it to the document. rectangle
      = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)'
  - name: Set rectangle dimensions
    text: '```python # Define width and height in points (1 point = 1/72 inch). rectangle.width
      = 200 # 200 points ≈ 2.78 inches rectangle.height = 100 # 100 points ≈ 1.39
      inches ```'
  - name: (Optional) Apply a visible custom shadow
    text: '```python shadow = rectangle.shadow_format shadow.visible = True # Show
      the shadow shadow.blur = 5.0 # Softness of the shadow edge shadow.distance =
      3.0 # How far the shadow is offset shadow.angle = 45 # Direction in degrees
      shadow.color = aw.drawing.Color.black ```'
  - name: Save document as PDF
    text: '```python output_path = "output/shadow_rectangle.pdf" document.save(output_path)
      print(f"PDF saved to {output_path}") ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Word automation
title: Hur man sparar dokument som PDF med en anpassad rektangelform i Python
url: /sv/python/document-conversion/how-to-save-document-as-pdf-with-a-custom-rectangle-shape-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man sparar dokument som PDF med en anpassad rektangelform i Python

Om du behöver **save document as PDF** medan du lägger till anpassad grafik, visar den här guiden hur du gör. Vi går igenom att skapa en tom Word‑fil, **rita en rektangelform**, ange dess storlek, applicera en synlig skugga och slutligen **export Word to PDF** med Aspose.Words för Python‑biblioteket.

Du får ett PDF‑dokument som innehåller en perfekt placerad rektangel, redo för rapporter, fakturor eller någon dokument‑automatiseringsscenario. Inga externa verktyg behövs—bara Python och Aspose.Words‑paketet.

## Vad du behöver

| Krav | Varför det är viktigt |
|------|-----------------------|
| Python 3.8+ | Aspose.Words för Python‑API:et riktar sig mot moderna tolkar. |
| `aspose-words`-paketet (`pip install aspose-words`) | Tillhandahåller `aw`‑namnutrymmet som används i kodexemplen. |
| Grundläggande kunskap om Python och objekt‑orienterad programmering | Handledningen manipulerar objekt som `Document` och `Shape`. |
| Skrivbehörighet till en mapp där PDF‑filen ska sparas | Steget `save document as pdf` skriver en fil till disk. |

> **Proffstips:** Använd en virtuell miljö (`python -m venv venv`) för att hålla beroenden isolerade.

## Så sparar du dokument som PDF med en rektangelform

Nedan följer ett komplett, körbart exempel. Varje steg förklaras så att du förstår **varför** vi utför handlingen, inte bara **vad** koden gör.

### Steg 1: Initiera ett nytt tomt dokument

```python
import aspose.words as aw

# Create an empty Word document – this is the canvas for our shape.
document = aw.Document()
```

Att skapa ett nytt `Document`‑objekt ger dig en ren sidkollektion. Du kan också läsa in en befintlig *.docx* om du senare vill **export Word to PDF**, men att börja med ett tomt dokument håller exemplet fokuserat.

### Steg 2: Lägg till rektangelform i dokumentet

```python
# Create a rectangle shape and attach it to the document.
rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

# The shape must be placed inside a paragraph before it appears.
paragraph = document.first_section.body.first_paragraph
paragraph.append_child(rectangle)
```

`add rectangle shape`‑steget använder `ShapeType.RECTANGLE`. Genom att lägga till formen i ett stycke vet Aspose.Words var den ska renderas i den slutliga PDF‑filen.

### Steg 3: Ange rektangelns dimensioner

```python
# Define width and height in points (1 point = 1/72 inch).
rectangle.width = 200   # 200 points ≈ 2.78 inches
rectangle.height = 100  # 100 points ≈ 1.39 inches
```

Att ange explicita **rectangle dimensions** säkerställer att formen ser konsekvent ut på alla plattformar. Du kan också använda `convert_to_inches`‑hjälpfunktioner om du föredrar imperiella enheter.

### Steg 4: (Valfritt) Applicera en synlig anpassad skugga

```python
shadow = rectangle.shadow_format
shadow.visible = True          # Show the shadow
shadow.blur = 5.0              # Softness of the shadow edge
shadow.distance = 3.0          # How far the shadow is offset
shadow.angle = 45              # Direction in degrees
shadow.color = aw.drawing.Color.black
```

En skugga får rektangeln att sticka ut i PDF‑filen. Flaggan `shadow.visible` krävs; utan den har de andra egenskaperna ingen effekt.

### Steg 5: Spara dokument som PDF

```python
output_path = "output/shadow_rectangle.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Genom att anropa `document.save` med en **.pdf**‑filändelse sparas automatiskt **save document as pdf** med Aspose.Words inbyggda PDF‑renderare. Inga extra konverteringssteg behövs, vilket är anledningen till att denna metod är det rekommenderade sättet att **export Word to PDF**.

> **Varför detta fungerar:** Aspose.Words skriver dokumentets layout, inklusive rektangeln och dess skugga, direkt in i PDF‑strömmen. Processen är förlustfri och behåller vektor­kvaliteten.

## Fullständig källkod (enkelt skript)

```python
import aspose.words as aw

def create_pdf_with_rectangle(output_path: str):
    """
    Creates a PDF that contains a single rectangle shape with a custom shadow.
    The function demonstrates:
    • add rectangle shape
    • set rectangle dimensions
    • export Word to PDF (save document as pdf)
    """
    # 1️⃣ Create a new blank document
    document = aw.Document()

    # 2️⃣ Insert a rectangle shape
    rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

    # 3️⃣ Set the shape's size
    rectangle.width = 200   # points
    rectangle.height = 100  # points

    # 4️⃣ Configure a visible shadow
    shadow = rectangle.shadow_format
    shadow.visible = True
    shadow.blur = 5.0
    shadow.distance = 3.0
    shadow.angle = 45
    shadow.color = aw.drawing.Color.black

    # 5️⃣ Add shape to the first paragraph
    paragraph = document.first_section.body.first_paragraph
    paragraph.append_child(rectangle)

    # 6️⃣ Save the document as PDF
    document.save(output_path)
    print(f"PDF successfully saved to: {output_path}")

if __name__ == "__main__":
    create_pdf_with_rectangle("output/shadow_rectangle.pdf")
```

När du kör detta skript skapas `shadow_rectangle.pdf` som ser ut så här:

![Diagram av den genererade PDF‑filen som visar rektangelformen efter save document as pdf](placeholder-image.png)

*PDF‑filen innehåller en enda sida med en svartskuggad rektangel centrerad i dokumentet.*

## Vanliga frågor och kantfall

| Fråga | Svar |
|-------|------|
| **Kan jag placera rektangeln på en specifik plats?** | Ja. Ställ in `rectangle.left` och `rectangle.top` (i punkter) innan du sparar. |
| **Vad händer om jag behöver flera former?** | Skapa ytterligare `Shape`‑objekt, konfigurera var och en och lägg till dem i samma eller olika stycken. |
| **Påverkar skuggan PDF‑filens storlek?** | Endast marginellt; skuggan lagras som vektor‑metadata, inte som en rasterbild. |
| **Kan jag använda detta för att konvertera befintliga *.docx*-filer?** | Absolut. Ersätt `aw.Document()` med `aw.Document("input.docx")` och resten av stegen förblir oförändrade. |
| **Finns det ett sätt att ändra rektangelns fyllningsfärg?** | Ställ in `rectangle.fill_color = aw.drawing.Color.light_blue` (eller någon annan `Color` du föredrar). |

## Nästa steg

Nu när du vet hur du **save document as PDF** med en anpassad rektangel, kan du utforska:

* **Export Word to PDF** med sidhuvuden, sidfötter och sidnummer.  
* **Add other drawing objects** (`Ellipse`, `Polygon`) med samma `Shape`‑klass.  
* **Batch process** en mapp med Word‑filer, och applicera samma rektangel‑överlägg på varje.  

Dessa tillägg följer samma mönster: skapa en form, konfigurera dess egenskaper och **save document as pdf**.

---

**Sammanfattning:** Denna handledning visade hur du **save document as PDF** samtidigt som du **add rectangle shape**, **set rectangle dimensions**, och applicerar en anpassad skugga med Aspose.Words för Python. Det kompletta skriptet är redo att kopieras, köras och anpassas till dina egna dokument‑automatiseringspipelines. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närliggande ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa rektangelform, lägg till skugga & spara PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Lägg till rektangel i PDF med Aspose.Words – Steg‑för‑steg‑guide](/words/english/python-net/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/)
- [Spara dokument som PDF med Aspose.Words – Komplett C#‑guide](/words/english/net/programming-with-pdfsaveoptions/save-document-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}