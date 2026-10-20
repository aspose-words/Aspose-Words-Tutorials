---
category: general
date: 2026-08-07
description: Disegna un rettangolo in PDF usando Aspose.Words per Python e impara
  come aggiungere un'ombra alla forma, configurare l'ombra della forma e salvare il
  documento come PDF.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle in pdf
- add shadow to shape
- save document as pdf
- configure shape shadow
language: it
lastmod: 2026-08-07
og_description: Disegna un rettangolo in PDF con Aspose.Words per Python. Questo tutorial
  mostra come aggiungere l'ombra a una forma, configurare l'ombra della forma e salvare
  il documento come PDF per la generazione professionale di documenti.
og_image_alt: PDF page showing a rectangle shape with a visible shadow created by
  Aspose.Words for Python
og_title: Disegna un rettangolo in PDF con Aspose.Words per Python – guida
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Draw rectangle in PDF using Aspose.Words for Python and learn how to
    add shadow to shape, configure shape shadow, and save document as PDF.
  headline: Draw rectangle in PDF with Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF
- Shape
- Shadow
title: Disegnare un rettangolo in PDF con Aspose.Words per Python
url: /it/python/images-shapes/draw-rectangle-in-pdf-with-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Disegnare un rettangolo in PDF con Aspose.Words per Python

Se hai bisogno di **draw rectangle in PDF** mentre lavori in Python, questa guida ti offre una soluzione completa, pronta all'uso. Vedrai esattamente come **add shadow to shape**, configurare quell'ombra e infine **save document as PDF** per distribuzione o archiviazione.

Creare un rettangolo ombreggiato è una necessità comune per report, fatture o annotazioni visive. Alla fine di questo tutorial avrai uno script unico che produce un PDF contenente un rettangolo con un'ombra realistica, e comprenderai come regolare dimensione, colore e offset per adattarlo a qualsiasi design.

## Prerequisiti

* Python 3.8+ installato.
* Il pacchetto Aspose.Words for Python via .NET (`aspose-words`) – installa con:

```bash
pip install aspose-words
```

* Permessi di scrittura sulla cartella in cui intendi salvare il PDF.

Non sono richieste librerie aggiuntive; Aspose.Words gestisce internamente la creazione di forme, la configurazione dell'ombra e l'esportazione in PDF.

## Passo 1: Creare un nuovo documento vuoto (draw rectangle in PDF – initialize)

Il primo passo è istanziare un oggetto `Document`. Questo oggetto rappresenta l'intero file PDF e fornisce un contenitore per sezioni, paragrafi e forme.

```python
import aspose.words as aw

# Create an empty Word document – it will become a PDF later
doc = aw.Document()
```

**Perché è importante:** Aspose.Words tratta la generazione del PDF come una conversione da un modello di documento Word, quindi iniziamo con un `Document` anche se l'output finale è un PDF.

## Passo 2: Inserire una forma rettangolare nel corpo del documento

Un rettangolo è un `ShapeType` specifico. Lo aggiungiamo al corpo della prima sezione, che crea automaticamente una nuova pagina quando salvato come PDF.

```python
# Append a rectangle shape to the first section's body
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Set the rectangle's dimensions (points = 1/72 inch)
rectangle.width = 200   # 200 pt ≈ 2.78 in
rectangle.height = 100  # 100 pt ≈ 1.39 in

# Optional: give the shape some visible text
rectangle.text = "Shadow demo"
```

**Spiegazione:** Le proprietà `width` e `height` controllano le dimensioni visive della forma nel PDF. Aggiungere del testo rende più facile verificare il rettangolo durante i test.

## Passo 3: Aggiungere ombra alla forma – abilitare e personalizzare

Ora attiviamo l'effetto ombra e ne affiniamo l'aspetto. È qui che entra in gioco la keyword **add shadow to shape**.

```python
# Access the shape's shadow effect object
shadow = rectangle.shadow_effect

# Make the shadow visible
shadow.visible = True

# Configure blur radius (pt) – higher values produce a softer edge
shadow.blur = 8

# Set the distance (offset) from the shape in points
shadow.distance = 5

# Define the direction of the shadow in degrees (0 = right, 90 = down)
shadow.angle = 45

# Choose a shadow color – black works for most documents
shadow.color = aw.drawing.Color.black
```

**Perché configurare l'ombra della forma?** Regolare `blur`, `distance` e `angle` consente di simulare un'illuminazione realistica, migliorando la leggibilità e la gerarchia visiva nei PDF generati.

## Passo 4: Salvare il documento come PDF – output finale

Con il rettangolo e la sua ombra definiti, l'ultimo passo è esportare il documento Word in PDF. Questo soddisfa il requisito **save document as pdf**.

```python
# Define the output path – replace YOUR_DIRECTORY with an actual folder
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)
print(f"PDF saved to {output_path}")
```

Quando apri `shadow_rectangle.pdf`, vedrai una singola pagina contenente un rettangolo con bordo grigio intitolato “Shadow demo” con un'ombra diagonale nitida.

### Output previsto

* Un file PDF chiamato `shadow_rectangle.pdf`.
* Una pagina con un rettangolo di 200 pt × 100 pt.
* Un'ombra visibile con offset di 5 pt a un angolo di 45°, sfocata di 8 pt.

## Passo 5: Esplorare variazioni e casi limite (opzionale)

Di seguito sono riportate le modifiche comuni che potresti necessitare in progetti reali:

| Variazione | Snippet di codice | Quando usarlo |
|-----------|--------------|-------------|
| **Tipo di forma diverso** (ad es., ellisse) | `aw.drawing.ShapeType.OVAL` instead of `RECTANGLE` | Per grafiche arrotondate o badge |
| **Colore ombra personalizzato** | `shadow.color = aw.drawing.Color.from_argb(255, 100, 100, 100)` | Quando è necessaria un'ombra grigia o specifica del brand |
| **Forme multiple** | Repeat the shape‑creation block and adjust `left`/`top` properties | Per creare diagrammi complessi |
| **Nessun testo all'interno della forma** | Omit `rectangle.text = "..."` | Quando la forma è puramente decorativa |
| **Output a DPI più alto** | `doc.save(output_path, aw.SaveFormat.PDF, aw.PdfSaveOptions())` with `PdfSaveOptions` set for image quality | Per PDF pronti per la stampa |

**Pro tip:** Imposta sempre `shadow.visible = True` prima di modificare altre proprietà; altrimenti le modifiche vengono ignorate silenziosamente.

## Script completo – copia, incolla e esegui

```python
import aspose.words as aw

# 1️⃣ Create a new blank document
doc = aw.Document()

# 2️⃣ Add a rectangle shape
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
rectangle.width = 200          # width in points
rectangle.height = 100         # height in points
rectangle.text = "Shadow demo"

# 3️⃣ Configure a visible shadow effect
shadow = rectangle.shadow_effect
shadow.visible = True
shadow.blur = 8                # blur radius (pt)
shadow.distance = 5            # offset distance (pt)
shadow.angle = 45              # direction (degrees)
shadow.color = aw.drawing.Color.black

# 4️⃣ Save the document as a PDF
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)

print(f"PDF successfully created at: {output_path}")
```

Esegui lo script dal tuo terminale o IDE. Sostituisci `YOUR_DIRECTORY` con un percorso di cartella reale, ad esempio `"/tmp"` o `"C:\\Users\\Me\\Documents"`.

## Conclusione

Ora sai come **draw rectangle in PDF** usando Aspose.Words per Python, **add shadow to shape**, **configure shape shadow** e **save document as PDF**. L'esempio completo dimostra ogni passaggio dalla creazione del documento all'esportazione finale, e le variazioni opzionali mostrano come adattare il codice a scenari più complessi.

Successivamente, potresti esplorare:

* [Ottimizzare i segnalibri PDF usando Aspose.Words per Python](/words/english/python-net/performance-optimization/optimize-pdf-bookmarks-aspose-words-python/)
* [Ottimizzare il caricamento PDF in Python con Aspose Words - Saltare le immagini](/words/hindi/python-net/performance-optimization/optimize-pdf-loading-python-aspose-words-skip-images/)
* [Manipolazione PDF con Aspose Words Python](/words/hongkong/python-net/document-operations/aspose-words-python-pdf-manipulation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}