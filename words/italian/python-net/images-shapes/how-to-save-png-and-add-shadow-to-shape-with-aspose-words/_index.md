---
category: general
date: 2026-08-17
description: Come salvare PNG usando Aspose.Words per Python. Impara ad aggiungere
  l'ombra a una forma, salvare il documento come PDF ed esportare Word in PNG in una
  sola guida.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save png
- add shadow to shape
- save document as pdf
- export word to png
- convert word to pdf
language: it
lastmod: 2026-08-17
og_description: Come salvare PNG con Aspose.Words. Questo tutorial mostra come aggiungere
  un'ombra a una forma, salvare il documento come PDF ed esportare Word in PNG.
og_image_alt: Screenshot of a Word document with a rectangle shape that has a shadow,
  saved as PNG and PDF
og_title: Come salvare PNG e aggiungere ombra alla forma con Aspose.Words
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
title: Come salvare PNG e aggiungere ombra alla forma con Aspose.Words
url: /it/python/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come salvare PNG e aggiungere ombra a una forma con Aspose.Words

Se hai bisogno di **how to save PNG** da un file Word, questa guida ti offre una soluzione completa e eseguibile. Vedrai anche come **add shadow to shape**, **save document as PDF** e **export Word to PNG** senza uscire dall'ambiente Aspose.Words.

Il tutorial copre tutto il necessario per trasformare un documento Word vuoto in un PDF e un'immagine PNG, applicando un semplice effetto ombra a una forma rettangolare. Non sono necessari strumenti esterni e il codice funziona con Aspose.Words for Python via .NET 7 o versioni successive.

## Cosa otterrai

* Crea un nuovo documento Word programmaticamente.  
* Inserisci una forma rettangolare e configura un effetto ombra.  
* Salva lo stesso documento come file PDF.  
* Esporta il documento come immagine PNG.  

Questi passaggi rispondono alla comune domanda **how to save PNG** gestendo anche **add shadow to shape** e **save document as PDF** in un unico flusso di lavoro.

## Prerequisiti

* Python 3.9 o versioni successive.  
* Aspose.Words for Python via .NET installato (`pip install aspose-words`).  
* Permessi di scrittura sulla directory di output specificata.  

Se non hai ancora installato Aspose.Words, esegui:

```bash
pip install aspose-words
```

## Come salvare PNG con Aspose.Words

Il primo passo importante è creare un documento e un `DocumentBuilder`. Il builder ti fornisce un'API fluida per inserire contenuti come forme, tabelle o testo.

```python
import aspose.words as aw

# Create a new blank document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` rappresenta l'intero file Word in memoria. `aw.DocumentBuilder` punta alla posizione corrente di inserimento, che inizialmente è l'inizio della prima (e unica) sezione.

## Aggiungere ombra alla forma prima dell'esportazione

Una forma può essere qualsiasi oggetto di disegno—rettangolo, ellisse o poligono personalizzato. Qui creiamo un rettangolo di 100 × 100 punti e applichiamo un'ombra morbida.

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

Perché configurare l'ombra prima del salvataggio? Aspose.Words rende l'ombra durante le fasi di esportazione in PDF e PNG, così l'effetto visivo viene preservato in entrambi i formati di output.

### Consiglio professionale
Se ti serve un'ombra più netta, riduci `blur`. Per un offset più marcato, aumenta `distance`. La classe `Shadow` espone anche `angle` e `transparency` per un controllo fine.

## Salva il documento come PDF

Salvare un documento Word come PDF è una singola riga di codice una volta che il contenuto è pronto. La costante `SaveFormat.PDF` indica ad Aspose.Words di eseguire la conversione.

```python
# Save the document as PDF (shadow is rendered in the output)
pdf_path = "output/output.pdf"
doc.save(pdf_path, aw.SaveFormat.PDF)
```

Il PDF risultante contiene il rettangolo con l'ombra esatta che hai definito. Aspose.Words gestisce la grafica vettoriale, quindi la dimensione del PDF rimane contenuta.

## Esporta Word in PNG

L'esportazione in PNG crea un'immagine raster di ogni pagina. Per impostazione predefinita Aspose.Words utilizza 96 DPI; è possibile aumentare questo valore per un output ad alta risoluzione fornendo un oggetto `PngSaveOptions`.

```python
# Export the same document as PNG
png_path = "output/output.png"
doc.save(png_path, aw.SaveFormat.PNG)
```

Quando **export Word to PNG**, ogni pagina viene salvata come file PNG separato. Poiché il nostro documento di esempio ha una sola pagina, appare un unico file PNG.

### Opzionale: PNG ad alta risoluzione

```python
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI
doc.save("output/high_res_output.png", png_options)
```

Un DPI più alto è utile quando il PNG verrà usato per la stampa o quando è necessaria una miniatura nitida.

## Script completo – copia, incolla e esegui

Di seguito trovi lo script completo e autonomo che implementa tutti i passaggi descritti sopra. Salvalo come `generate_assets.py` ed eseguilo dalla riga di comando.

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

### Output previsto

Eseguendo lo script vengono creati tre file:

* `output/output.pdf` – un PDF con un rettangolo che proietta un'ombra nera.  
* `output/output.png` – un PNG a 96 DPI della stessa pagina.  
* `output/high_res_output.png` – un PNG a 300 DPI per una qualità superiore.  

Apri uno dei file con il tuo visualizzatore preferito per verificare che l'ombra appaia esattamente come definita.

## Domande frequenti e casi particolari

**Che succede se la directory di output non esiste?**  
Lo script chiama `os.makedirs(output_dir, exist_ok=True)`, che crea automaticamente la cartella. Questo evita un `FileNotFoundError` durante le operazioni di salvataggio.

**Posso aggiungere più forme con ombre diverse?**  
Sì. Crea ulteriori oggetti `Shape`, configura ogni proprietà `shadow` in modo indipendente e inseriscili con `builder.insert_node(shape)` prima di salvare.

**L'ombra verrà preservata convertendo in altri formati raster (ad es., JPEG)?**  
Aspose.Words rende l'ombra per tutti i formati raster supportati da `SaveFormat`. Puoi sostituire `aw.SaveFormat.PNG` con `aw.SaveFormat.JPEG` e l'ombra sarà comunque presente.

**In che modo questo differisce da “convert word to pdf”?**  
`convert word to pdf` è sostanzialmente la stessa operazione eseguita al passo 4. La stessa chiamata `doc.save` con `SaveFormat.PDF` gestisce la conversione internamente, preservando layout, font e grafica come le ombre.

**Esiste un limite alle dimensioni della forma?**  
Le forme sono misurate in punti (1 pt ≈ 1/72 pollice). Dimensioni molto grandi possono aumentare la dimensione del file risultante, ma Aspose.Words non impone limiti rigidi. Regola gli argomenti `width` e `height` quando costruisci `aw.Shape` per adattarli al tuo layout.

## Conclusione

Ora sai **how to save PNG** da un documento Word e hai imparato a **add shadow to shape**, **save document as PDF** e **export Word to PNG** usando Aspose.Words per Python. Lo script completo dimostra un modello pulito e ripetibile che puoi adattare per documenti più grandi, più pagine o effetti grafici più complessi.

I prossimi passi potrebbero includere:

* Sperimentare con altri valori `ShapeType` (ellipse, cloud, ecc.).  
* Using `

## Cosa dovresti imparare dopo?

I tutorial seguenti coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare ulteriori funzionalità dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [How to Convert DOCX to PNG in Java – Aspose.Words](/words/english/java/document-converting/converting-documents-images/)
- [Save Word Documents as PostScript in Python Using Aspose.Words: A Comprehensive Guide](/words/english/python-net/document-operations/save-docs-as-postscript-using-aspose-words-python/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}