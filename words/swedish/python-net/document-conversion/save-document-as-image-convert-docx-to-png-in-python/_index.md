---
category: general
date: 2026-08-17
description: Spara dokumentet som bild och exportera alla sidor som PNG med Aspose.Words
  för Python. Lär dig konvertera DOCX till PNG med ett enda kommando.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save document as image
- convert docx to png
- export docx to png
- export all pages png
- export word pages image
language: sv
lastmod: 2026-08-17
og_description: Spara dokument som bild och exportera alla sidor som PNG med Aspose.Words
  för Python. Den här guiden visar hur du konverterar DOCX till PNG på ett effektivt
  sätt.
og_image_alt: Diagram showing a multi‑page Word document converted into a single PNG
  grid preview
og_title: Spara dokument som bild och konvertera DOCX till PNG i Python
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: Save document as image and export all pages PNG using Aspose.Words
    for Python. Learn to convert DOCX to PNG with a single command.
  headline: 'Save document as image: convert DOCX to PNG in Python'
  type: TechArticle
- description: Save document as image and export all pages PNG using Aspose.Words
    for Python. Learn to convert DOCX to PNG with a single command.
  name: 'Save document as image: convert DOCX to PNG in Python'
  steps:
  - name: '**Save format** – PNG is lossless and widely supported.'
    text: '**Save format** – PNG is lossless and widely supported.'
  - name: '**Page set** – defines the range of pages to export; using `0, document.page_count`
      captures every page.'
    text: '**Page set** – defines the range of pages to export; using `0, document.page_count`
      captures every page.'
  - name: '**Layout** – `GRID` arranges all exported pages into a single image, which
      is ideal for preview scenarios.'
    text: '**Layout** – `GRID` arranges all exported pages into a single image, which
      is ideal for preview scenarios.'
  type: HowTo
tags:
- Aspose.Words
- Python
- DOCX
title: 'Spara dokument som bild: konvertera DOCX till PNG i Python'
url: /sv/python/document-conversion/save-document-as-image-convert-docx-to-png-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Spara dokument som bild: konvertera DOCX till PNG i Python

Om du behöver **save document as image** och generera en enda förhandsgranskning för en flersidig Word‑fil, visar den här guiden hur du gör det med Aspose.Words för Python. Du kommer också att lära dig hur du **convert DOCX to PNG** i en enkel operation.

Att exportera varje sida i ett Word‑dokument till PNG kan vara tidskrävande när du skriver en loop själv. Aspose.Words tillhandahåller inbyggda alternativ som låter dig **export all pages PNG** med ett enda anrop, samtidigt som du får kontroll över layout, upplösning och sidintervall. I slutet av den här handledningen kommer du att ha ett färdigt skript som producerar en rutnäts‑PNG som innehåller alla sidor i källdokumentet.

## Förutsättningar

* Python 3.8 eller nyare installerat.
* `aspose-words`‑paketet (`pip install aspose-words`).
* En Word‑fil (`.docx`) som innehåller minst två sidor.
* Skrivrättighet till den katalog där du vill lagra den resulterande PNG‑filen.

Inga ytterligare externa verktyg krävs; Aspose.Words hanterar konverteringen helt i minnet.

## Steg 1: Läs in Word‑dokumentet

Det första steget är att skapa ett `aw.Document`‑objekt som representerar källdokumentet DOCX. Detta objekt ger dig åtkomst till alla sidor, sektioner och resurser i dokumentet.

```python
import aspose.words as aw

# Load the multi‑page Word document
doc_path = "YOUR_DIRECTORY/multi_page.docx"
document = aw.Document(doc_path)
```

*Varför detta är viktigt*: Att läsa in dokumentet en gång ger dig en komplett objektmodell som Aspose.Words senare kan rendera till vilket stödjande bildformat som helst. `aw.Document`‑klassen validerar också filen, så du får tidig återkoppling om DOCX‑filen är korrupt.

## Steg 2: Skapa PNG‑sparalternativ och konfigurera dem

Aspose.Words använder `ImageSaveOptions` för att styra hur ett dokument rasteriseras. I detta steg sätter vi tre viktiga egenskaper:

1. **Save format** – PNG är förlustfri och brett stödjad.
2. **Page set** – definierar intervallet av sidor som ska exporteras; att använda `0, document.page_count` fångar varje sida.
3. **Layout** – `GRID` ordnar alla exporterade sidor i en enda bild, vilket är idealiskt för förhandsgranskningsscenarier.

```python
# Configure PNG export options
png_options = aw.saving.ImageSaveOptions(aw.SaveFormat.PNG)

# Export all pages (page index starts at 0)
png_options.page_set = aw.saving.PageSet(0, document.page_count)

# Arrange pages in a grid layout (rows × columns are auto‑calculated)
png_options.layout = aw.saving.ImageSaveOptions.PageLayout.GRID

# Optional: increase resolution for sharper output (default is 96 DPI)
png_options.resolution = 150  # DPI
```

*Varför detta är viktigt*: Att sätta `page_set` till hela intervallet låter dig **export docx to png** utan att manuellt iterera över sidor. `GRID`‑layouten producerar en enda bild som innehåller varje sida sida‑vid‑sida, vilket uppfyller kravet **export word pages image** i en kompakt form. Att justera `resolution` hjälper när källdokumentet innehåller fina detaljer.

## Steg 3: Spara dokumentet som en enda PNG‑förhandsgranskning

Med alternativen förberedda är sparandet en enradare. Aspose.Words skriver PNG‑filen till disk med de inställningar som definierats ovan.

```python
# Destination path for the combined PNG image
output_path = "YOUR_DIRECTORY/preview.png"

# Perform the export – this creates one PNG that contains all pages
document.save(output_path, png_options)
print(f"Document successfully saved as image: {output_path}")
```

**Förväntat resultat**

När skriptet körs skapas `preview.png`. Om källdokumentet DOCX hade tre sidor kommer PNG‑filen att visa de tre sidorna uppradade i ett rutnät (t.ex. 2 × 2 med den sista cellen tom). Att öppna filen i någon bildvisare bekräftar att varje sida har rasteriserats korrekt.

### Pro‑tips

Om du bara behöver ett delmängd av sidorna, ändra `PageSet`‑argumenten, t.ex.:

```python
# Export pages 2‑4 only (zero‑based index)
png_options.page_set = aw.saving.PageSet(1, 4)
```

Detta respekterar fortfarande logiken **export all pages png** för det valda intervallet, vilket minskar minnesanvändningen för mycket stora dokument.

## Hantera stora dokument och minnesbegränsningar

När du arbetar med dokument som har dussintals eller hundratals sidor kan den genererade PNG‑filen bli stor. Överväg dessa strategier:

* **Increase `resolution` only as needed** – högre DPI ger större filer.
* **Use `PageLayout.SINGLE_COLUMN`** – skapar en vertikal remsa istället för ett rutnät, vilket kan vara lättare att bläddra i.
* **Stream the output** – Aspose.Words stödjer även att spara till en `BytesIO`‑ström om du behöver skicka bilden över ett nätverk utan att skriva till disk.

```python
import io

stream = io.BytesIO()
document.save(stream, png_options)
# Now `stream.getvalue()` holds the PNG bytes
```

## Fullt skript för snabb kopiera‑och‑klistra

Nedan är det kompletta, körbara exemplet som inkluderar alla stegen som diskuterats. Ersätt `YOUR_DIRECTORY` med den faktiska mappvägen på din maskin.

```python
import aspose.words as aw

# ----------------------------------------------------------------------
# 1. Load the source DOCX file
# ----------------------------------------------------------------------
doc_path = "YOUR_DIRECTORY/multi_page.docx"
document = aw.Document(doc_path)

# ----------------------------------------------------------------------
# 2. Configure PNG export options (save document as image)
# ----------------------------------------------------------------------
png_options = aw.saving.ImageSaveOptions(aw.SaveFormat.PNG)

# Export every page (export docx to png)
png_options.page_set = aw.saving.PageSet(0, document.page_count)

# Arrange pages in a grid (export word pages image)
png_options.layout = aw.saving.ImageSaveOptions.PageLayout.GRID

# Optional: higher DPI for sharper output
png_options.resolution = 150

# ----------------------------------------------------------------------
# 3. Save the combined PNG file
# ----------------------------------------------------------------------
output_path = "YOUR_DIRECTORY/preview.png"
document.save(output_path, png_options)

print(f"Document successfully saved as image: {output_path}")
```

När detta skript körs produceras en enda PNG som innehåller alla sidor i `multi_page.docx`. Metoden fungerar med vilken DOCX‑fil som helst, oavsett innehållskomplexitet (tabeller, bilder, komplexa layouter).

## Slutsats

Du vet nu hur du **save document as image**, **convert DOCX to PNG**, och **export all pages PNG** med Aspose.Words för Python. Genom att utnyttja `ImageSaveOptions` undviker du manuella loopar, får en förhandsgranskning i rutnätsstil och behåller kontroll över upplösning och layout.  

Nästa steg kan vara att utforska:

* Export till andra rasterformat (JPEG, BMP) – byt bara `SaveFormat`.
* Lägga till vattenstämplar eller annotationer före export – manipulera `Document`‑objektet.
* Integrera detta skript i en webbtjänst för att generera förhandsgranskningar i realtid.

Experimentera med olika `layout`‑ och `resolution`‑värden för att hitta den balans som bäst passar din applikations prestanda‑ och kvalitetskrav. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Optimize RTF Image Handling in Python using Aspose.Words API: Save as WMF and Ensure Compatibility](/words/english/python-net/images-shapes/optimize-rtf-image-handling-aspose-words-python/)
- [Convert DOCX to Fixed-Form XAML in Python Using Aspose.Words: A Comprehensive Guide](/words/english/python-net/document-operations/python-docx-to-xaml-aspose-tutorial/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}