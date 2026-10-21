---
category: general
date: 2026-10-16
description: Crea un documento Word vuoto, inserisci una forma in Word, aggiungi un'ombra
  esterna e salva come PDF usando Python.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert shape in word
- save as pdf python
- add outer shadow shape
- create pdf with shape
language: it
lastmod: 2026-10-16
og_description: Crea un documento Word vuoto con una forma di ombra esterna usando
  Aspose.Words per Python. Questa guida mostra come inserire la forma, applicare l'ombra
  e salvare il file come PDF.
og_image_alt: Screenshot of a Word document containing a rectangle shape with an outer
  shadow, saved as PDF
og_title: Crea un documento Word vuoto con ombra della forma – Guida Python
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document, insert shape in Word, add outer shadow,
    and save as PDF using Python.
  headline: Create blank Word document with shadowed shape in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- PDF generation
- Shape styling
title: Crea un documento Word vuoto con forma ombreggiata in Python
url: /it/python/word-automation/create-blank-word-document-with-shadowed-shape-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea documento Word vuoto con forma ombreggiata in Python

Se hai bisogno di **creare un documento Word vuoto** e aggiungere una grafica personalizzata, questa guida è ciò che fa per te. Ti guideremo passo passo su come **inserire una forma in Word**, applicare una **forma con ombra esterna**, e infine **salvare come PDF usando Python**.

Imparerai a configurare Aspose.Words per Python, costruire un rettangolo, stilizzare la sua ombra e generare un PDF che conserva l’effetto visivo. Non è necessaria alcuna esperienza pregressa con l’API Aspose, ma dovresti avere conoscenze di base di Python e un’installazione funzionante di Python 3.10 o successiva.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* Python 3.10 o più recente installato.  
* Una licenza attiva di Aspose.Words per Python (una prova gratuita è sufficiente per la valutazione).  
* Accesso a `pip` per installare il pacchetto `aspose-words`.  
* Permessi di scrittura nella directory in cui verrà salvato il PDF.

Puoi installare la libreria con un unico comando:

```bash
pip install aspose-words
```

## Crea documento Word vuoto – configurazione dell’ambiente

Il primo passo è creare un file Word vuoto che servirà da tela per la forma.

```python
import aspose.words as aw

# Initialize a new, empty document
doc = aw.Document()
# DocumentBuilder provides convenient methods for adding content
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` rappresenta un file Word completamente vuoto. Utilizzando `DocumentBuilder` ottieni l’accesso a metodi come `insert_shape`, che useremo nel passo successivo.

## Inserisci forma in Word e imposta le dimensioni

Ora aggiungiamo un rettangolo che più tardi riceverà un’ombra esterna. La dimensione è espressa in punti (1 pt ≈ 1/72 pollice).

```python
# Insert a rectangle shape with a width of 200 pt and a height of 100 pt
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)
```

La chiamata `insert_shape` restituisce un oggetto `Shape` che puoi personalizzare ulteriormente. A questo punto il documento contiene già un rettangolo visibile quando viene aperto in Microsoft Word.

## Aggiungi ombra esterna – personalizzazione dell’effetto

Aspose.Words fornisce una classe `ShadowEffect` per definire le proprietà dell’ombra, come stile, sfocatura, distanza e colore.

```python
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a new shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # Choose an outer shadow
shadow.blur = 5.0                         # Softness of the shadow edges
shadow.distance = 3.0                     # Offset distance from the shape
shadow.color = aw.Color.black             # Shadow color

# Apply the shadow to the rectangle
rectangle.shadow = shadow
```

Impostare `style` su `OUTER` garantisce che l’ombra appaia al di fuori del bordo del rettangolo, conferendo un sottile aspetto 3‑D. Puoi sperimentare con `blur` e `distance` per ottenere un’ombra più stretta o più diffusa.

## Salva come PDF python – finalizzazione del documento

Dopo aver stilizzato la forma, il documento può essere salvato direttamente come PDF. Aspose.Words gestisce la conversione internamente, preservando l’effetto dell’ombra.

```python
output_path = "output/shape_with_shadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Quando apri `shape_with_shadow.pdf` in qualsiasi visualizzatore PDF, vedrai il rettangolo con l’ombra esterna esattamente come appariva in Word.

## Esempio completo funzionante

Di seguito trovi lo script completo che combina tutti i passaggi. Copialo in un file chiamato `create_word_with_shadow.py` ed eseguilo.

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1. Create a blank Word document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2. Insert a rectangle shape
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)

# 3. Define and apply an outer shadow
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER
shadow.blur = 5.0
shadow.distance = 3.0
shadow.color = aw.Color.black
rectangle.shadow = shadow

# 4. Save the document as PDF
pdf_path = os.path.join(output_dir, "shape_with_shadow.pdf")
doc.save(pdf_path)

print(f"PDF generated at: {pdf_path}")
```

**Output previsto**

L’esecuzione dello script stampa una riga di conferma, ad esempio:

```
PDF generated at: output/shape_with_shadow.pdf
```

Aprendo il PDF risultante vedrai una singola pagina contenente un rettangolo di 200 pt × 100 pt con una morbida ombra nera esterna.

## Variazioni comuni e casi limite

* **Cambiare colore dell’ombra** – Sostituisci `aw.Color.black` con qualsiasi altro valore `aw.Color`, ad esempio `aw.Color.red` o `aw.Color.from_argb(255, 0, 120, 215)`.  
* **Usare una forma diversa** – Cambia `aw.drawing.ShapeType.RECTANGLE` in `OVAL`, `DIAMOND` o qualsiasi altro valore enum supportato.  
* **Salvare come DOCX invece di PDF** – Chiama `doc.save("output/shape.docx")` per mantenere il formato Word.  
* **Forme multiple** – Crea forme aggiuntive chiamando nuovamente `builder.insert_shape`; ogni forma può avere il proprio `ShadowEffect`.

**Suggerimento professionale:** Se devi posizionare la forma in una posizione specifica, imposta `rectangle.left` e `rectangle.top` dopo l’inserimento. Questo ti dà un controllo pixel‑perfect sulla posizione.

## Conclusione

Ora sai come **creare un documento Word vuoto**, **inserire una forma in Word**, **aggiungere un’ombra esterna alla forma** e **salvare come PDF usando Python**. Il codice completo dimostra il flusso di lavoro end‑to‑end, e le spiegazioni chiariscono perché ogni chiamata API è necessaria.

Da qui puoi esplorare opzioni di stilizzazione più avanzate, aggiungere testo all’interno della forma o combinare più forme per costruire diagrammi complessi. Sperimenta con diversi parametri dell’ombra per allineare il risultato al linguaggio visivo del tuo brand e integra questo approccio in pipeline di generazione documenti più ampie.

Buon coding!

## Cosa dovresti imparare dopo?


I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell’API e a esplorare approcci alternativi di implementazione nei tuoi progetti.

- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Create PDF from Word – Complete Python Guide with Aspose.Words](/words/english/python-net/document-conversion/create-pdf-from-word-complete-python-guide-with-aspose-words/)
- [Add Shadow to Shape in Word with Aspose.Words – Step‑by‑Step](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}