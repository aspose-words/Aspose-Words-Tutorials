---
category: general
date: 2026-08-11
description: Hur man formaterar diagram i ett Word-dokument med Python – ladda Word-dokument
  i Python och snabbt tillämpa en fördefinierad diagramstil.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to style chart
- load word document python
- apply predefined chart style
- apply chart style word
language: sv
lastmod: 2026-08-11
og_description: Hur man formaterar diagram i ett Word‑dokument med Python. Lär dig
  hur du laddar ett Word‑dokument med Python, tillämpar en fördefinierad diagramstil
  och sparar den uppdaterade filen.
og_image_alt: Screenshot of Python code applying a chart style to a Word document
og_title: Hur du formaterar diagram i Word med Python – steg-för-steg guide
schemas:
- author: Aspose
  dateModified: '2026-08-11'
  description: How to style chart in a Word document using Python – load Word document
    python and apply predefined chart style quickly.
  headline: How to style chart in a Word document using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Chart styling
- Word automation
title: Hur man formaterar diagram i ett Word‑dokument med Python
url: /sv/python/formatting-styles/how-to-style-chart-in-a-word-document-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så stylar du diagram i ett Word‑dokument med Python

Om du behöver **styla diagram** i en Word‑fil visar den här handledningen exakt hur du går tillväga. Efter de två första meningarna vet du hur du laddar ett Word‑dokument med Python, hämtar ett diagram och tillämpar en fördefinierad diagramstil. Lösningen fungerar med Aspose.Words för Python‑biblioteket och kräver ingen manuell redigering av dokumentet.

Du kommer att lära dig hur du **laddar Word‑dokument Python**, väljer den första diagramformen, sätter en inbyggd stil och sparar den ändrade filen. Guiden tar också upp vanliga fallgropar, såsom hantering av dokument utan diagram och val av rätt stil‑enumeration. Inga externa verktyg behövs utöver Aspose.Words‑paketet.

## Så stylar du diagram i ett Word‑dokument med Python

Att tillämpa en stil på ett diagram är en endaste‑rad‑operation när du har ett `Chart`‑objekt. Biblioteket exponerar `ChartStyle`‑enumerationen, som innehåller dussintals fördefinierade utseenden (Style 1 … Style 50). I detta avsnitt sätter vi **Style 5**, men du kan ersätta enum‑värdet med vilken stil som helst som passar dina designriktlinjer.

```python
import aspose.words as aw

# Load the Word document that contains a chart
doc = aw.Document("YOUR_DIRECTORY/input.docx")

# Retrieve the first chart shape in the document
chart_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
chart = chart_shape.as_chart()

# Apply a predefined chart style (Style 5) to the chart
chart.style = aw.drawing.ChartStyle.STYLE_5

# Save the modified document
doc.save("YOUR_DIRECTORY/output.docx")
```

**Varför detta fungerar:**  
* `aw.Document` analyserar .docx‑filen och bygger en objektmodell.  
* `get_child(..., aw.NodeType.SHAPE, ...)` hittar den första formen, som är diagrambehållaren.  
* `as_chart()` kastar formen till ett `Chart`‑objekt och exponerar egenskapen `style`.  
* Att tilldela `ChartStyle.STYLE_5` säger åt Aspose.Words att ersätta diagrammets visuella tema med den fördefinierade definitionen.

Utdatafilen `output.docx` innehåller samma data som originalet men med diagrammet renderat med den valda stilen.

## Ladda ett Word‑dokument i Python

Innan du kan styla ett diagram måste du **ladda Word‑dokument Python** korrekt. `aw.Document`‑konstruktorn accepterar en sökväg till en .docx-, .doc- eller .rtf‑fil. Säkerställ att filsökvägen är absolut eller att arbetskatalogen pekar på platsen för din indatafil.

```python
# Example: absolute path on Windows
doc_path = r"C:\Projects\Charts\input.docx"
doc = aw.Document(doc_path)
```

**Tips för att ladda dokument:**

* Använd råa strängar (`r"..."`) på Windows för att undvika att backslashes måste escape‑as.  
* Verifiera att filen finns med `os.path.isfile(doc_path)` för att förhindra körfel.  
* Om dokumentet innehåller skyddade sektioner, ange lösenordet via `aw.LoadOptions`.

```python
import os
if not os.path.isfile(doc_path):
    raise FileNotFoundError(f"Document not found: {doc_path}")
```

## Tillämpa en fördefinierad diagramstil

Steget **tillämpa fördefinierad diagramstil** är där den visuella omvandlingen sker. Aspose.Words definierar `ChartStyle`‑enum med värden från `STYLE_1` till `STYLE_50`. Varje stil motsvarar en uppsättning färger, markörer och linjeformat som efterliknar Microsoft Offices inbyggda diagramteman.

```python
# Choose any style from STYLE_1 to STYLE_50
desired_style = aw.drawing.ChartStyle.STYLE_12
chart.style = desired_style
```

**När du ska använda en fördefinierad stil:**  

* Du behöver ett enhetligt utseende över flera dokument.  
* Diagramdata förändras ofta, men det visuella temat ska förbli fast.  
* Du vill undvika manuell formatering i Word‑gränssnittet.

**Edge case – dokument utan diagram:**  
Om `doc.get_child(aw.NodeType.SHAPE, 0, True)` returnerar `None` kommer skriptet att kasta ett `AttributeError`. Skydda mot detta genom att kontrollera nodtypen innan du kastar.

```python
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
if shape is None or not shape.has_chart:
    raise ValueError("No chart found in the document.")
chart = shape.as_chart()
```

## Spara det stylade dokumentet

Efter styling är det enkelt att persistera ändringarna. `doc.save`‑metoden skriver tillbaka den uppdaterade objektmodellen till en .docx‑fil. Du kan också exportera till andra format som PDF, HTML eller PNG om efterföljande konsumtion kräver en annan representation.

```python
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)          # Saves as DOCX
doc.save("output.pdf")         # Optional: export to PDF
```

**Verifiering:** Öppna `output.docx` i Microsoft Word. Diagrammet bör visa det nya temat, och alla dataserier behåller sina ursprungliga värden. Om du exporterar till PDF förblir den visuella stilen identisk.

## Vanliga fallgropar och praktiska tips

| Problem | Orsak | Lösning |
|-------|-------|-----|
| `AttributeError: 'NoneType' object has no attribute 'as_chart'` | Ingen diagramform hittades på index 0 | Använd `doc.get_child(..., 0, True)` i ett try/except‑block eller iterera över alla former med `doc.get_child_nodes(aw.NodeType.SHAPE, True)`. |
| Fel stil tillämpad | Ett enum‑värde som inte finns (t.ex. `STYLE_0`) | Välj ett giltigt `ChartStyle`‑värde (1‑50). |
| Filen sparas inte | Utdatasökvägen pekar på en skrivskyddad katalog | Säkerställ att processen har skrivbehörighet eller ändra katalogen. |
| Diagrammet försvinner efter sparning | Formen var inte ett diagram (t.ex. en bild) | Verifiera `shape.has_chart` innan du kastar. |

**Proffstips:** Cachea den `ChartStyle` du använder oftast i en konstant så att du kan återanvända den i flera skript utan att skriva in enum‑värdet varje gång.

```python
DEFAULT_CHART_STYLE = aw.drawing.ChartStyle.STYLE_5
chart.style = DEFAULT_CHART_STYLE
```

## Fullständigt end‑to‑end‑exempel

Nedan är det kompletta, körbara skriptet som innehåller alla bästa praxis som diskuterats ovan. Ersätt `YOUR_DIRECTORY` med den faktiska mappen som innehåller dina Word‑filer.

```python
import os
import aspose.words as aw

# ----------------------------------------------------------------------
# Configuration
# ----------------------------------------------------------------------
INPUT_PATH = r"YOUR_DIRECTORY/input.docx"
OUTPUT_PATH = r"YOUR_DIRECTORY/output.docx"
DEFAULT_STYLE = aw.drawing.ChartStyle.STYLE_5

# ----------------------------------------------------------------------
# Load the document
# ----------------------------------------------------------------------
if not os.path.isfile(INPUT_PATH):
    raise FileNotFoundError(f"Input file not found: {INPUT_PATH}")

doc = aw.Document(INPUT_PATH)

# ----------------------------------------------------------------------
# Locate the first chart
# ----------------------------------------------------------------------
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
if shape is None or not shape.has_chart:
    raise ValueError("No chart shape found in the document.")

chart = shape.as_chart()

# ----------------------------------------------------------------------
# Apply the predefined chart style
# ----------------------------------------------------------------------
chart.style = DEFAULT_STYLE

# ----------------------------------------------------------------------
# Save the modified document
# ----------------------------------------------------------------------
doc.save(OUTPUT_PATH)

print(f"Chart style applied successfully. Saved to {OUTPUT_PATH}")
```

**Förväntat resultat:**  
När du öppnar `output.docx` visas den första diagrammet med det visuella temat definierat av `STYLE_5`. Alla datapunkter, axlar och förklaringar förblir oförändrade, vilket visar att styling är oberoende av den underliggande datan.

## Slutsats

Du vet nu **hur du stylar diagram** i ett Word‑dokument med Python. Handledningen gick igenom hur du **laddar Word‑dokument Python**, hämtar diagramformen, **tillämpa fördefinierad diagramstil** och sparar den uppdaterade filen. Med dessa byggstenar kan du automatisera rapportgenerering, upprätthålla företagsbranding eller batch‑processa dussintals dokument utan manuellt arbete.

Nästa steg är att utforska andra diagramanpassningar såsom att ändra seriefärger, lägga till datalabels eller exportera diagrammet som en bild. Läs i Aspose.Words‑dokumentationen om ämnen som **apply chart style word**, **chart data manipulation** och **document conversion** för att bredda dina automatiseringsmöjligheter.

Känn dig fri att experimentera med olika `ChartStyle`‑värden och integrera detta skript i större pipelines som genererar Word‑rapporter från databaser eller API:er. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

De följande handledningarna täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstrerats i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Insert Simple Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-simple-column-chart/)
- [Insert Area Chart Into A Word Document](/words/english/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}