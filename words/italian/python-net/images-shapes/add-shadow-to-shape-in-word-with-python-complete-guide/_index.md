---
category: general
date: 2026-07-29
description: Aggiungi ombra a una forma in Word usando Python e Aspose.Words. Scopri
  come applicare rapidamente l'effetto ombra ai documenti Word con un esempio di codice
  completo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- apply shadow effect word
language: it
lastmod: 2026-07-29
og_description: Aggiungi ombra alla forma nei documenti Word con Python. Questa guida
  mostra come applicare l'effetto ombra ai file Word utilizzando Aspose.Words, completa
  di codice e consigli.
og_image_alt: Word document displaying a rectangle shape with a soft gray shadow applied
og_title: Aggiungi ombra alla forma in Word – Tutorial Python
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Add shadow to shape in Word using Python and Aspose.Words. Learn how
    to apply shadow effect Word documents quickly with a full code example.
  headline: Add Shadow to Shape in Word with Python – Complete Guide
  type: TechArticle
- description: Add shadow to shape in Word using Python and Aspose.Words. Learn how
    to apply shadow effect Word documents quickly with a full code example.
  name: Add Shadow to Shape in Word with Python – Complete Guide
  steps:
  - name: '**No shape found** – If your document only contains text, the script will
      raise a `ValueError`. Add a shape first or extend the script to iterate over
      all `Shape` nodes.'
    text: '**No shape found** – If your document only contains text, the script will
      raise a `ValueError`. Add a shape first or extend the script to iterate over
      all `Shape` nodes.'
  - name: '**License watermark** – Running the code without a proper license inserts
      an “Aspose.Words Evaluation” watermark on each page. Grab a trial license from
      the Aspose portal to keep the output clean.'
    text: '**License watermark** – Running the code without a proper license inserts
      an “Aspose.Words Evaluation” watermark on each page. Grab a trial license from
      the Aspose portal to keep the output clean.'
  - name: '**Incorrect file paths** – Using relative paths can cause `FileNotFoundError`
      when the script’s working directory differs. Prefer `os.path.abspath` or pass
      absolute paths.'
    text: '**Incorrect file paths** – Using relative paths can cause `FileNotFoundError`
      when the script’s working directory differs. Prefer `os.path.abspath` or pass
      absolute paths.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word Automation
title: Aggiungi ombra alla forma in Word con Python – Guida completa
url: /it/python/images-shapes/add-shadow-to-shape-in-word-with-python-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aggiungere Ombra a una Forma in Word con Python – Guida Completa

Hai mai dovuto **aggiungere ombra a una forma** in un documento Word ma non sapevi da dove cominciare? In questo tutorial ti guideremo passo passo su come **applicare l'effetto ombra in Word** usando la libreria Aspose.Words per Python.  

Se hai mai sperimentato con l'interfaccia utente e ti sei chiesto: “Deve esserci un modo programmatico per farlo”, sei nel posto giusto. Alla fine avrai uno script eseguibile che aggiunge un'ombra a bordi morbidi a qualsiasi forma tu scelga.

## Prerequisiti

Prima di iniziare, assicurati di avere:

- Python 3.8+ installato (qualsiasi versione recente va bene)
- Una licenza attiva di Aspose.Words per Python o una prova gratuita (l'API funziona senza licenza ma aggiunge una filigrana)
- Un documento Word (`.docx`) che contenga già almeno una forma (un rettangolo, un'immagine o uno SmartArt)
- Familiarità di base con le importazioni Python e la gestione delle eccezioni

> **Suggerimento:** Se non hai ancora una forma, apri Word, inserisci un semplice rettangolo e salva il file come `input.docx` in una cartella a cui il tuo script possa fare riferimento.

## Installa Aspose.Words per Python

Esegui il seguente comando pip nel terminale:

```bash
pip install aspose-words
```

Questo scarica l'ultima versione 23.x, che supporta le proprietà di ombra sui nodi `Shape`.

## Passo 1: Carica il Documento Word

La prima cosa che facciamo è aprire il `.docx` esistente. È qui che inizia l'operazione **add shadow to shape**.

```python
import aspose.words as aw

# Load the source document
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)
```

> **Perché è importante:** `aw.Document` analizza l'intero file Word in una struttura simile a un DOM, permettendoci di attraversare nodi come forme, paragrafi e tabelle.

## Passo 2: Individua la Forma di Destinazione

Aspose.Words offre il metodo di ricerca profonda `get_child` che può recuperare la prima forma indipendentemente dal livello di nidificazione. Se hai più forme, puoi modificare l'indice o iterare su tutte.

```python
# Retrieve the first shape (deep search = True)
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

if shape is None:
    raise ValueError("No shape found in the document. Add a shape and try again.")
```

> **Caso limite:** Alcuni documenti contengono solo oggetti di disegno (ad esempio immagini). Anche questi sono rappresentati come nodi `Shape`, quindi questo codice funziona sia per rettangoli che per immagini.

## Passo 3: Configura l'Aspetto dell'Ombra

Ora arriva il cuore di **add shadow to shape**—impostare le proprietà dell'ombra. I valori seguenti forniscono un aspetto sottile e professionale:

```python
# Softness of the shadow edges
shape.shadow_blur = 5.0

# Horizontal and vertical offsets (in points)
shape.shadow_offset_x = 2.0
shape.shadow_offset_y = 2.0

# Transparency – 0 is invisible, 1 is solid
shape.shadow_opacity = 0.7
```

Puoi sperimentare con questi numeri:

- Aumenta `shadow_blur` per un bordo più sfocato.
- Usa offset negativi per spostare l'ombra a sinistra o verso l'alto.
- Regola `shadow_opacity` per rendere l'ombra più marcata.

> **Perché questi valori predefiniti?** Un blur di 5 punti imita l'ombra predefinita di Word, mentre un'opacità di 0,7 mantiene l'effetto visibile senza sovrastare il colore di riempimento della forma.

## Passo 4: Salva il Documento Modificato

Infine, scrivi le modifiche in un nuovo file. Mantenere intatto l'originale semplifica il debug.

```python
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Shadow applied! Saved updated file to {output_path}")
```

A questo punto hai completato con successo **add shadow to shape** e puoi aprire `output.docx` per vedere l'effetto.

## Esempio Completo Funzionante

Mettendo tutto insieme, ecco uno script autonomo che puoi copiare‑incollare ed eseguire subito:

```python
import aspose.words as aw
import os

def add_shadow_to_first_shape(input_file: str, output_file: str) -> None:
    """
    Loads a Word document, adds a soft shadow to the first shape,
    and saves the result to a new file.

    Parameters
    ----------
    input_file : str
        Path to the source .docx file.
    output_file : str
        Destination path for the modified document.
    """
    # Verify the input exists
    if not os.path.isfile(input_file):
        raise FileNotFoundError(f"Input file not found: {input_file}")

    # Load the document
    doc = aw.Document(input_file)

    # Find the first shape (deep search)
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

    if shape is None:
        raise ValueError("No shape found in the document. Insert a shape and retry.")

    # Apply shadow settings
    shape.shadow_blur = 5.0
    shape.shadow_offset_x = 2.0
    shape.shadow_offset_y = 2.0
    shape.shadow_opacity = 0.7

    # Save the updated document
    doc.save(output_file)

if __name__ == "__main__":
    INPUT_DOC = "YOUR_DIRECTORY/input.docx"
    OUTPUT_DOC = "YOUR_DIRECTORY/output.docx"
    add_shadow_to_first_shape(INPUT_DOC, OUTPUT_DOC)
    print("✅ Shadow added successfully.")
```

### Output Previsto

Apri `output.docx` e dovresti vedere la forma originale ora dotata di una delicata ombra grigia, leggermente spostata verso destra e in basso. L'effetto rispecchia quello che ottieni applicando manualmente **apply shadow effect word** tramite l'interfaccia.

![Esempio di forma con ombra](https://example.com/shadowed_shape.png "Forma Word con un'ombra morbida"){: .center-image width="600" alt="Screenshot che mostra una forma con un'ombra in un documento Word"}

## Applicare l'Effetto Ombra in Word – Opzioni Avanzate

Se hai bisogno di più controllo, Aspose.Words ti consente di modificare proprietà aggiuntive:

| Proprietà | Descrizione | Intervallo Tipico |
|----------|-------------|-------------------|
| `shadow_color` | Il colore dell'ombra (predefinito è nero) | Qualsiasi `aw.Color` |
| `shadow_type` | Determina se l'ombra è **esterna**, **interna** o **prospettica** | Enum `aw.ShadowType` |
| `shadow_transform` | Applica una matrice di trasformazione personalizzata per ombre inclinate | Avanzato – da usare con parsimonia |

Esempio di impostazione di un'ombra blu:

```python
shape.shadow_color = aw.Color.from_argb(255, 0, 0, 255)  # Opaque blue
shape.shadow_type = aw.ShadowType.OUTER
```

Queste impostazioni ti permettono di **apply shadow effect Word** nei documenti in modo creativo, ad esempio aggiungendo un'ombra colorata a un logo.

## Problemi Comuni & Come Evitarli

1. **Nessuna forma trovata** – Se il tuo documento contiene solo testo, lo script solleverà un `ValueError`. Aggiungi prima una forma o estendi lo script per iterare su tutti i nodi `Shape`.
2. **Filigrana di licenza** – Eseguire il codice senza licenza inserisce una filigrana “Aspose.Words Evaluation” su ogni pagina. Ottieni una licenza di prova dal portale Aspose per mantenere l'output pulito.
3. **Percorsi file errati** – L'uso di percorsi relativi può causare `FileNotFoundError` quando la directory di lavoro dello script è diversa. Preferisci `os.path.abspath` o passa percorsi assoluti.

## Prossimi Passi

Ora che hai padroneggiato **add shadow to shape**, potresti voler esplorare argomenti correlati:

- **Apply shadow effect Word** a più forme in un ciclo
- Convertire il documento con ombra in PDF (`doc.save("output.pdf")`)
- Cambiare il colore dell'ombra in base al riempimento della forma (stilizzazione dinamica)
- Usare Aspose.Words per inserire programmaticamente nuove forme prima di applicare le ombre

Ognuna di queste estensioni si basa sugli stessi concetti API, quindi la curva di apprendimento rimane dolce.

## Conclusione

Abbiamo coperto tutto ciò che ti serve per **add shadow to shape** in un file Word usando Python: caricamento del documento, individuazione della forma, configurazione dei parametri dell'ombra e salvataggio del risultato. Lo script completo sopra è pronto per essere inserito in qualsiasi pipeline di automazione, e i consigli aggiuntivi ti aiutano a **apply shadow effect Word** in scenari più sofisticati.

Provalo, modifica i valori di blur e opacità, e scopri come una piccola ombra può fare una grande differenza visiva. Buon coding!

## Cosa Dovresti Imparare Dopo?


I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell'API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}