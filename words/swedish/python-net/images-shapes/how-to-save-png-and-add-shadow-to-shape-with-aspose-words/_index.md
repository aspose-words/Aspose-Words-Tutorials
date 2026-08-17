---
category: general
date: 2026-08-17
description: Hur man sparar PNG med Aspose.Words för Python. Lär dig att lägga till
  skugga på en form, spara dokument som PDF och exportera Word till PNG i en guide.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save png
- add shadow to shape
- save document as pdf
- export word to png
- convert word to pdf
language: sv
lastmod: 2026-08-17
og_description: Hur man sparar PNG med Aspose.Words. Denna handledning visar hur man
  lägger till en skugga på en form, sparar dokumentet som PDF och exporterar Word
  till PNG.
og_image_alt: Screenshot of a Word document with a rectangle shape that has a shadow,
  saved as PNG and PDF
og_title: Hur man sparar PNG och lägger till skugga på en form med Aspose.Words
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
title: Hur man sparar PNG och lägger till skugga på en form med Aspose.Words
url: /sv/python/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man sparar PNG och lägger till skugga på en form med Aspose.Words

Om du behöver **how to save PNG** från en Word‑fil, ger den här guiden dig en komplett, körbar lösning. Du kommer också att se hur du **add shadow to shape**, **save document as PDF** och **export Word to PNG** utan att lämna Aspose.Words‑miljön.

Handledningen täcker allt som krävs för att omvandla ett tomt Word‑dokument till en PDF‑ och en PNG‑bild, samtidigt som en enkel skuggeffekt appliceras på en rektangel‑form. Inga externa verktyg behövs, och koden fungerar med Aspose.Words for Python via .NET 7 eller senare.

## Vad du kommer att uppnå

* Skapa ett nytt Word‑dokument programatiskt.  
* Infoga en rektangel‑form och konfigurera en skuggeffekt.  
* Spara samma dokument som en PDF‑fil.  
* Exportera dokumentet som en PNG‑bild.  

Dessa steg svarar på den vanliga frågan **how to save PNG** samtidigt som de hanterar **add shadow to shape** och **save document as PDF** i ett enda arbetsflöde.

## Förutsättningar

* Python 3.9 eller nyare.  
* Aspose.Words for Python via .NET installerat (`pip install aspose-words`).  
* Skrivrättighet till den utdata‑katalog du anger.  

Om du ännu inte har installerat Aspose.Words, kör:

```bash
pip install aspose-words
```

## Så sparar du PNG med Aspose.Words

Det första stora steget är att skapa ett dokument och en `DocumentBuilder`. Buildern ger dig ett flytande API för att infoga innehåll såsom former, tabeller eller text.

```python
import aspose.words as aw

# Create a new blank document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` representerar hela Word‑filen i minnet. `aw.DocumentBuilder` pekar på den aktuella infogningsplatsen, som initialt är början av den första (och enda) sektionen.

## Lägg till skugga på form innan export

En form kan vara vilket ritobjekt som helst—rektangel, ellips eller anpassad polygon. Här skapar vi en 100 × 100 punkt‑rektangel och applicerar en mjuk skugga.

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

Varför konfigurera skuggan innan sparande? Aspose.Words renderar skuggan under PDF‑ och PNG‑exportfaserna, så den visuella effekten bevaras i båda utdataformaten.

### Proffstips
Om du behöver en skarpare skugga, minska `blur`. För ett mer uttalat avstånd, öka `distance`. `Shadow`‑klassen exponerar även `angle` och `transparency` för finjusterad kontroll.

## Spara dokument som PDF

Att spara ett Word‑dokument som PDF är en enradig operation när innehållet är klart. Konstanten `SaveFormat.PDF` talar om för Aspose.Words att utföra konverteringen.

```python
# Save the document as PDF (shadow is rendered in the output)
pdf_path = "output/output.pdf"
doc.save(pdf_path, aw.SaveFormat.PDF)
```

Den resulterande PDF‑filen innehåller rektangeln med exakt den skugga du definierade. Aspose.Words hanterar vektorgrafik, så PDF‑filens storlek förblir måttlig.

## Exportera Word till PNG

Export till PNG skapar en rasterbild av varje sida. Som standard använder Aspose.Words 96 DPI; du kan öka detta värde för högre upplösning genom att tillhandahålla ett `PngSaveOptions`‑objekt.

```python
# Export the same document as PNG
png_path = "output/output.png"
doc.save(png_path, aw.SaveFormat.PNG)
```

När du **export Word to PNG**, sparas varje sida som en separat PNG‑fil. Eftersom vårt exempel‑dokument bara har en sida, visas endast en enda PNG‑fil.

### Valfritt: högupplöst PNG

```python
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI
doc.save("output/high_res_output.png", png_options)
```

Högre DPI är användbart när PNG‑filen ska användas i tryck eller när du behöver en skarp miniatyrbild.

## Fullt skript – kopiera, klistra in och kör

Nedan är det kompletta, fristående skriptet som implementerar varje steg som beskrivits ovan. Spara det som `generate_assets.py` och kör det från kommandoraden.

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

### Förväntad output

När skriptet körs skapas tre filer:

* `output/output.pdf` – en PDF med en rektangel som kastar en svart skugga.  
* `output/output.png` – en 96 DPI PNG‑rendering av samma sida.  
* `output/high_res_output.png` – en 300 DPI PNG för högre kvalitet.

Öppna någon av filerna i din föredragna visare för att verifiera att skuggan visas exakt som definierad.

## Vanliga frågor och edge cases

**What if the output directory does not exist?**  
Skriptet anropar `os.makedirs(output_dir, exist_ok=True)`, vilket skapar mappen automatiskt. Detta förhindrar ett `FileNotFoundError` under sparoperationerna.

**Can I add multiple shapes with different shadows?**  
Ja. Skapa ytterligare `Shape`‑objekt, konfigurera varje `shadow`‑egenskap oberoende och infoga dem med `builder.insert_node(shape)` innan du sparar.

**Will the shadow be preserved when converting to other raster formats (e.g., JPEG)?**  
Aspose.Words renderar skuggan för alla rasterformat som stöds av `SaveFormat`. Du kan ersätta `aw.SaveFormat.PNG` med `aw.SaveFormat.JPEG` och skuggan kommer fortfarande att visas.

**How does this differ from “convert word to pdf”?**  
`convert word to pdf` är i princip samma operation som utförs i steg 4. Samma `doc.save`‑anrop med `SaveFormat.PDF` hanterar konverteringen internt, och bevarar layout, teckensnitt och grafik såsom skuggor.

**Is there a limit on shape size?**  
Former mäts i punkter (1 pt ≈ 1/72 tum). Mycket stora dimensioner kan öka den resulterande filstorleken, men Aspose.Words har ingen hård gräns. Justera `width` och `height`‑argumenten när du konstruerar `aw.Shape` för att passa din layout.

## Slutsats

Du vet nu **how to save PNG** från ett Word‑dokument samtidigt som du har lärt dig att **add shadow to shape**, **save document as PDF** och **export Word to PNG** med Aspose.Words för Python. Det kompletta skriptet demonstrerar ett rent, återanvändbart mönster som du kan anpassa för större dokument, flera sidor eller mer komplexa grafiska effekter.

Nästa steg kan inkludera:

* Experimentera med andra `ShapeType`‑värden (ellipse, moln osv.).  
* Using `

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [How to Convert DOCX to PNG in Java – Aspose.Words](/words/english/java/document-converting/converting-documents-images/)
- [Save Word Documents as PostScript in Python Using Aspose.Words: A Comprehensive Guide](/words/english/python-net/document-operations/save-docs-as-postscript-using-aspose-words-python/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}