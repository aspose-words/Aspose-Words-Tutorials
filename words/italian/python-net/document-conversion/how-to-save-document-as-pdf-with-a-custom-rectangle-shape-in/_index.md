---
category: general
date: 2026-10-07
description: Scopri come salvare un documento come PDF aggiungendo una forma rettangolare
  e un'ombra personalizzata usando Aspose.Words per Python. Codice passo‑passo incluso.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save document as pdf
- add rectangle shape
- export word to pdf
- set rectangle dimensions
- draw rectangle word
language: it
lastmod: 2026-10-07
og_description: Salva il documento come PDF con una forma rettangolare personalizzata
  usando Aspose.Words per Python. Segui l'esempio completo per disegnare, stilizzare
  ed esportare Word in PDF.
og_image_alt: Screenshot of the generated PDF showing the rectangle shape after save
  document as pdf
og_title: Salva il documento come PDF con una forma rettangolare – guida completa
  Python
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
title: Come salvare un documento come PDF con una forma rettangolare personalizzata
  in Python
url: /it/python/document-conversion/how-to-save-document-as-pdf-with-a-custom-rectangle-shape-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come salvare un documento come PDF con una forma rettangolare personalizzata in Python

Se hai bisogno di **salvare un documento come PDF** aggiungendo grafiche personalizzate, questa guida ti mostra come. Passeremo in rassegna la creazione di un file Word vuoto, **disegnare una forma rettangolare**, impostarne le dimensioni, applicare un'ombra visibile e infine **esportare Word in PDF** utilizzando la libreria Aspose.Words per Python.

Otterrai un PDF che contiene un rettangolo perfettamente posizionato, pronto per report, fatture o qualsiasi scenario di automazione dei documenti. Non sono necessari strumenti esterni: solo Python e il pacchetto Aspose.Words.

## Cosa ti serve

| Requisito | Perché è importante |
|-------------|----------------|
| Python 3.8+ | L'API Aspose.Words per Python è destinata a interpreti moderni. |
| `aspose-words` package (`pip install aspose-words`) | Fornisce lo spazio dei nomi `aw` usato negli esempi di codice. |
| Basic familiarity with Python and object‑oriented programming | Il tutorial manipola oggetti come `Document` e `Shape`. |
| Write permission to a folder where the PDF will be saved | Il passaggio `save document as pdf` scrive un file su disco. |

> **Consiglio professionale:** usa un ambiente virtuale (`python -m venv venv`) per mantenere le dipendenze isolate.

## Come salvare un documento come PDF con una forma rettangolare

Di seguito trovi un esempio completo e eseguibile. Ogni passaggio è spiegato così capirai **perché** eseguiamo l'azione, non solo **cosa** fa il codice.

### Passo 1: Inizializzare un nuovo documento vuoto

```python
import aspose.words as aw

# Create an empty Word document – this is the canvas for our shape.
document = aw.Document()
```

Creare un nuovo oggetto `Document` ti fornisce una collezione di pagine pulita. Potresti anche caricare un *.docx* esistente se volessi **esportare Word in PDF** in seguito, ma partire da zero mantiene l'esempio concentrato.

### Passo 2: Aggiungere una forma rettangolare al documento

```python
# Create a rectangle shape and attach it to the document.
rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

# The shape must be placed inside a paragraph before it appears.
paragraph = document.first_section.body.first_paragraph
paragraph.append_child(rectangle)
```

Il passaggio `add rectangle shape` utilizza `ShapeType.RECTANGLE`. Aggiungendo la forma a un paragrafo, Aspose.Words sa dove renderizzarla nel PDF finale.

### Passo 3: Impostare le dimensioni del rettangolo

```python
# Define width and height in points (1 point = 1/72 inch).
rectangle.width = 200   # 200 points ≈ 2.78 inches
rectangle.height = 100  # 100 points ≈ 1.39 inches
```

Impostare esplicitamente le **dimensioni del rettangolo** garantisce che la forma abbia un aspetto coerente su tutte le piattaforme. Puoi anche usare le funzioni di supporto `convert_to_inches` se preferisci le unità imperiali.

### Passo 4: (Opzionale) Applicare un'ombra personalizzata visibile

```python
shadow = rectangle.shadow_format
shadow.visible = True          # Show the shadow
shadow.blur = 5.0              # Softness of the shadow edge
shadow.distance = 3.0          # How far the shadow is offset
shadow.angle = 45              # Direction in degrees
shadow.color = aw.drawing.Color.black
```

Un'ombra fa risaltare il rettangolo nel PDF. È necessario il flag `shadow.visible`; senza di esso le altre proprietà non hanno effetto.

### Passo 5: Salvare il documento come PDF

```python
output_path = "output/shadow_rectangle.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Chiamare `document.save` con un'estensione **.pdf** salva automaticamente **save document as pdf** usando il renderer PDF integrato di Aspose.Words. Non sono necessari passaggi di conversione aggiuntivi, motivo per cui questo metodo è il modo consigliato per **esportare Word in PDF**.

> **Perché funziona:** Aspose.Words scrive il layout del documento, includendo il rettangolo e la sua ombra, direttamente nel flusso PDF. Il processo è senza perdita e mantiene la qualità vettoriale.

## Codice sorgente completo (script unico)

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

Eseguendo questo script si genera `shadow_rectangle.pdf` che appare così:

![Diagramma del PDF generato che mostra la forma rettangolare dopo il salvataggio del documento come PDF](placeholder-image.png)

*Il PDF contiene una singola pagina con un rettangolo con ombra nera centrato nel documento.*

## Domande frequenti e casi particolari

| Domanda | Risposta |
|----------|--------|
| **Posso posizionare il rettangolo in una posizione specifica?** | Sì. Imposta `rectangle.left` e `rectangle.top` (in punti) prima di salvare. |
| **E se ho bisogno di più forme?** | Crea oggetti `Shape` aggiuntivi, configura ciascuno e aggiungili allo stesso o a diversi paragrafi. |
| **L'ombra influisce sulla dimensione del PDF?** | Solo marginalmente; l'ombra è memorizzata come metadati vettoriali, non come immagine raster. |
| **Posso usare questo per convertire file *.docx* esistenti?** | Assolutamente. Sostituisci `aw.Document()` con `aw.Document("input.docx")` e il resto dei passaggi rimane invariato. |
| **C'è un modo per cambiare il colore di riempimento del rettangolo?** | Imposta `rectangle.fill_color = aw.drawing.Color.light_blue` (o qualsiasi `Color` preferisci). |

## Prossimi passi

Ora che sai come **salvare un documento come PDF** con un rettangolo personalizzato, potresti esplorare:

* **Esporta Word in PDF** con intestazioni, piè di pagina e numeri di pagina.  
* **Aggiungi altri oggetti di disegno** (`Ellipse`, `Polygon`) usando la stessa classe `Shape`.  
* **Elabora in batch** una cartella di file Word, applicando la stessa sovrapposizione di rettangolo a ciascuno.  

Queste estensioni seguono lo stesso schema: crea una forma, configura le sue proprietà e **save document as pdf**.

---

**Riepilogo:** Questo tutorial ti ha mostrato come **salvare un documento come PDF** aggiungendo una **forma rettangolare**, impostando le **dimensioni del rettangolo** e applicando un'ombra personalizzata usando Aspose.Words per Python. Lo script completo è pronto per essere copiato, eseguito e adattato alle tue pipeline di automazione dei documenti. Buon coding!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea forma rettangolare, aggiungi ombra e salva PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Aggiungi rettangolo a PDF con Aspose.Words – Guida passo‑passo](/words/english/python-net/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/)
- [Salva documento come PDF con Aspose.Words – Guida completa C#](/words/english/net/programming-with-pdfsaveoptions/save-document-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}