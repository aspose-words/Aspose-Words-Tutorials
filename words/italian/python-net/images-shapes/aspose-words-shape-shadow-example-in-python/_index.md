---
category: general
date: 2026-11-18
description: L'esempio di ombra per forme di Aspose.Words mostra come aggiungere un'ombra
  a una forma Word usando Python. Segui questa guida passo‑passo per modificare e
  salvare il documento.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words shape shadow example
- python shape shadow
- Aspose.Words for Python
- modify shape shadow
- document manipulation Aspose
language: it
lastmod: 2026-11-18
og_description: L'esempio di ombra per forme di Aspose.Words dimostra come aggiungere
  un'ombra a una forma Word con Python. Scopri il codice completo, perché ogni passaggio
  è importante e come adattarlo.
og_image_alt: Aspose.Words shape shadow example – Word document displaying a shape
  with a shadow applied using Python
og_title: Esempio di ombra della forma Aspose.Words – Guida Python
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Aspose.Words shape shadow example shows how to add a shadow to a Word
    shape using Python. Follow this step‑by‑step guide to modify and save the document.
  headline: Aspose.Words shape shadow example in Python
  type: TechArticle
- description: Aspose.Words shape shadow example shows how to add a shadow to a Word
    shape using Python. Follow this step‑by‑step guide to modify and save the document.
  name: Aspose.Words shape shadow example in Python
  steps:
  - name: Expected outcome
    text: Open `output.docx` in Microsoft Word. The first shape you added should now
      display a soft shadow that is offset by 2 pt horizontally and vertically, with
      a blur radius of 5 pt. All other content remains unchanged.
  - name: 'Alternative: Find a shape by name'
    text: 'If your document contains several shapes, you might prefer to locate a
      specific one:'
  - name: Working with multiple shapes
    text: 'If you need to apply the same shadow to every shape, iterate over the node
      collection:'
  - name: Applying a shadow to a specific shape type
    text: You can filter by `ShapeType` (e.g., `aw.ShapeType.IMAGE`). This is useful
      when you only want to affect pictures, not AutoShapes.
  - name: Handling documents without shapes
    text: The script already raises a clear `ValueError` if no shape is found. In
      production code you might log the issue and continue processing other files.
  - name: Compatibility notes
    text: '* The code works with **Aspose.Words for Python via .NET** version 23.10
      and later. * The shadow effect is supported in Word 2007+ (`.docx`). Older formats
      (`.doc`) will lose the effect after conversion.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Esempio di ombra di forma Aspose.Words in Python
url: /it/python/images-shapes/aspose-words-shape-shadow-example-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Esempio di ombra per forma Aspose.Words in Python

L'esempio di ombra per forma Aspose.Words dimostra come aggiungere un effetto ombra a una forma in un documento Word usando Python. In questo tutorial otterrai uno script completo e eseguibile che carica un documento, configura l'ombra e salva il risultato.

Applicare un'ombra a una forma è un modo comune per migliorare la gerarchia visiva in report, brochure o fatture. Il codice qui sotto funziona con Aspose.Words for Python via .NET e non richiede librerie di terze parti aggiuntive.

## Cosa imparerai

* Come caricare un file `.docx` con **Aspose.Words for Python**.  
* Come individuare la prima forma (incluse le forme all'interno di tabelle o gruppi).  
* Come configurare la sfocatura, lo spostamento orizzontale e quello verticale dell'ombra.  
* Come salvare il documento modificato preservando tutto il resto del contenuto.  

**Prerequisiti**

* Python 3.8 o successivo.  
* Aspose.Words for Python via .NET installato (`pip install aspose-words`).  
* Un documento Word (`input.docx`) che contiene almeno una forma (ad es., un'immagine, AutoShape o casella di testo).  

Se devi installare la libreria, esegui:

```bash
pip install aspose-words
```

## Esempio di ombra per forma Aspose.Words – panoramica

Lo script seguente è la soluzione completa. Segue i quattro passaggi logici di un tipico flusso di lavoro **document manipulation Aspose**: caricare, individuare, modificare e salvare.

```python
import aspose.words as aw

# ----------------------------------------------------------------------
# Step 1: Load the Word document
# ----------------------------------------------------------------------
# Replace YOUR_DIRECTORY with the path that contains input.docx.
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)

# ----------------------------------------------------------------------
# Step 2: Access the first shape (including descendants)
# ----------------------------------------------------------------------
# NodeType.SHAPE searches for any shape node. The third argument (True)
# tells Aspose.Words to search recursively through all child nodes.
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# Verify that a shape was found; raise a clear error if not.
if shape is None:
    raise ValueError("No shape found in the document. Ensure input.docx contains a shape.")

# ----------------------------------------------------------------------
# Step 3: Configure the shape's shadow
# ----------------------------------------------------------------------
# The Shadow object controls visual appearance. Adjust the properties
# to achieve the desired effect.
shape.shadow.blur = 5          # Softness of the shadow (0‑15 is typical)
shape.shadow.offset_x = 2      # Horizontal displacement in points
shape.shadow.offset_y = 2      # Vertical displacement in points

# Optional: Change shadow color or transparency if needed.
# shape.shadow.color = aw.Color.black
# shape.shadow.transparency = 0.5

# ----------------------------------------------------------------------
# Step 4: Save the modified document
# ----------------------------------------------------------------------
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)

print(f"Shadow applied successfully. Saved to {output_path}")
```

### Risultato previsto

Apri `output.docx` in Microsoft Word. La prima forma aggiunta dovrebbe ora mostrare un'ombra morbida spostata di 2 pt orizzontalmente e verticalmente, con un raggio di sfocatura di 5 pt. Tutto il resto del contenuto rimane invariato.

## Passo 1: Caricare il documento Word

Caricare un documento è la prima operazione in qualsiasi flusso di lavoro **Aspose.Words for Python**. La classe `Document` analizza il file e costruisce un modello di oggetti in memoria. Poiché la libreria funziona sulla piattaforma .NET, può gestire file di grandi dimensioni in modo efficiente.

*Perché è importante:* Caricare il documento una sola volta e mantenere un riferimento (`doc`) evita I/O ripetuti, migliorando le prestazioni quando è necessario applicare più modifiche.

## Passo 2: Accedere alla forma

Le forme possono essere figli diretti del corpo del documento, oppure possono essere annidate all'interno di tabelle, gruppi o canvas di disegno. L'uso di `get_child(NodeType.SHAPE, 0, True)` ricerca ricorsivamente e restituisce la prima forma corrispondente.

*Perché è importante:* Il flag `True` garantisce di non perdere forme nascoste all'interno di altri nodi. Se lo ometti, verrebbero considerate solo le forme di livello superiore, e molti documenti reali restituirebbero `None`.

### Alternativa: Trovare una forma per nome

Se il tuo documento contiene diverse forme, potresti preferire individuare una specifica:

```python
shape = doc.get_child(aw.NodeType.SHAPE, lambda n: n.name == "MyLogo", True)
```

Questo frammento dimostra una variazione **python shape shadow** che filtra per la proprietà `name` della forma.

## Passo 3: Configurare l'ombra della forma

La proprietà `shadow` di un oggetto `Shape` ti offre un controllo dettagliato sull'effetto visivo. I tre attributi più comunemente regolati sono:

| Proprietà | Intervallo tipico | Impatto visivo |
|----------|-------------------|----------------|
| `blur`   | 0 – 15            | Valori più alti creano un bordo più morbido. |
| `offset_x` | –10 – 10       | Valori positivi spostano l'ombra verso destra. |
| `offset_y` | –10 – 10       | Valori positivi spostano l'ombra verso il basso. |

Puoi anche modificare `color`, `transparency`, `visible` e `style`. L'esempio imposta una sfocatura moderata e un leggero offset per mantenere l'ombra discreta.

**Consiglio professionale:** Quando una forma ha già un'ombra, le proprietà sopra sovrascrivono le impostazioni esistenti. Se devi preservare lo stile originale, leggi i valori correnti prima di modificarli.

## Passo 4: Salvare il documento modificato

Chiamare `doc.save()` scrive la rappresentazione in memoria nuovamente in un file `.docx`. Aspose.Words aggiorna automaticamente tutte le relazioni interne, quindi il file di output rimane pienamente compatibile con Microsoft Word.

*Perché è importante:* Salvare una sola volta alla fine del processo riduce il rischio di corruzione del file e migliora la velocità complessiva, specialmente quando si elaborano molti documenti in un lavoro batch.

## Variazioni comuni e casi limite

### Lavorare con più forme

Se devi applicare la stessa ombra a ogni forma, itera sulla collezione di nodi:

```python
for shp in doc.get_child_nodes(aw.NodeType.SHAPE, True):
    shp.shadow.blur = 5
    shp.shadow.offset_x = 2
    shp.shadow.offset_y = 2
```

### Applicare un'ombra a un tipo di forma specifico

Puoi filtrare per `ShapeType` (ad es., `aw.ShapeType.IMAGE`). Questo è utile quando vuoi influenzare solo le immagini, non le AutoShape.

```python
for shp in doc.get_child_nodes(aw.NodeType.SHAPE, True):
    if shp.shape_type == aw.ShapeType.IMAGE:
        shp.shadow.blur = 4
```

### Gestire documenti senza forme

Lo script solleva già un chiaro `ValueError` se non viene trovata alcuna forma. Nel codice di produzione potresti registrare il problema e continuare a elaborare altri file.

### Note di compatibilità

- Il codice funziona con **Aspose.Words for Python via .NET** versione 23.10 e successive.  
- L'effetto ombra è supportato in Word 2007+ (`.docx`). I formati più vecchi (`.doc`) perderanno l'effetto dopo la conversione.

## Conclusione

Questo **aspose.words shape shadow example** ti guida attraverso il caricamento di un file Word, l'individuazione di una forma, la configurazione della sua ombra e il salvataggio del risultato con **Aspose.Words for Python**. Ora hai un modello riutilizzabile per qualsiasi scenario **document manipulation Aspose** che coinvolge miglioramenti visivi.

Successivamente, potresti esplorare:

* Aggiungere riempimenti a gradiente o stili di linea alle forme (`modify shape shadow` e altre proprietà visive).  
* Combinare la configurazione dell'ombra con la formattazione del testo per creare modelli completamente stilizzati.  
* Automatizzare il processo per un batch di documenti usando `os.listdir` e il modello mostrato sopra.

Sentiti libero di sperimentare con diversi livelli di sfocatura, offset e colori per adeguarli alle linee guida del tuo brand. Buon coding!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Add Shadow to Shape in Python – Complete Aspose.Words Tutorial](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [How to set shadow on a shape in Aspose.Words for Python](/words/english/python-net/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-for-python/)
- [How to save PNG and add shadow to shape with Aspose.Words](/words/english/python-net/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}