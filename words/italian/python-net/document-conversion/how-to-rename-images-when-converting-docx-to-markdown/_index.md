---
category: general
date: 2026-06-30
description: Come rinominare le immagini durante la conversione da DOCX a markdown.
  Impara a cambiare i nomi delle immagini e a salvare Word come markdown con nomi
  di file immagine personalizzati.
draft: false
keywords:
- how to rename images
- convert docx to markdown
- change image names
- save word as markdown
- custom image filenames
language: it
og_description: Come rinominare le immagini durante la conversione da DOCX a markdown.
  Questa guida ti mostra come cambiare i nomi delle immagini, salvare Word in markdown
  e utilizzare nomi file personalizzati per le immagini.
og_title: Come rinominare le immagini durante la conversione da DOCX a Markdown
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: How to rename images while converting DOCX to markdown. Learn to change
    image names and save Word as markdown with custom image filenames.
  headline: How to Rename Images When Converting DOCX to Markdown
  type: TechArticle
- description: How to rename images while converting DOCX to markdown. Learn to change
    image names and save Word as markdown with custom image filenames.
  name: How to Rename Images When Converting DOCX to Markdown
  steps:
  - name: Why Use a GUID?
    text: '* **Uniqueness** – A GUID (`uuid4`) guarantees that two images will never
      clash, even across multiple runs. * **Traceability** – If you need to debug
      later, the GUID can be logged alongside the original Word paragraph number.
      * **Portability** – No reliance on the original Word naming scheme, which '
  - name: Expected Output (excerpt)
    text: '```markdown # Sample Document'
  - name: What if the document contains non‑image resources?
    text: Our callback already checks the file extension and returns `True` for anything
      that isn’t an image. This means CSS files, fonts, or embedded OLE objects keep
      their original names, which is usually what you want when you **save word as
      markdown**.
  - name: Can I use a custom naming scheme instead of GUIDs?
    text: 'Absolutely. Replace the `uuid.uuid4()` call with any function that returns
      a string. For example, you could prepend the original paragraph index:'
  - name: How does this affect performance on large documents?
    text: The callback runs once per resource, so the overhead is minimal—mostly the
      time to generate a GUID. Even a 200‑page report with dozens of images finishes
      in under a second on a modern laptop.
  - name: What if I need the image filenames to be deterministic (e.g., for CI builds)?
    text: 'Swap `uuid.uuid4()` for a hash of the original image bytes:'
  type: HowTo
tags:
- Aspose.Words
- Python
- Markdown
- Image Processing
title: Come rinominare le immagini durante la conversione da DOCX a Markdown
url: /it/python/document-conversion/how-to-rename-images-when-converting-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come rinominare le immagini durante la conversione da DOCX a Markdown

Ti sei mai chiesto **come rinominare le immagini** automaticamente quando converti un file DOCX in Markdown? Non sei l'unico. In molte pipeline di documentazione i nomi di immagine predefiniti (come `image1.png`) diventano un incubo da gestire, soprattutto quando lo stesso markdown è sotto controllo di versione tra i team.  

La buona notizia è che Aspose.Words per Python rende un gioco da ragazzi **cambiare i nomi delle immagini** al volo, e puoi mantenere il tuo Markdown pulito preservando una cartella ordinata di risorse con nomi personalizzati.  

In questo tutorial imparerai a:

* Caricare un documento Word (`.docx`) in Python.  
* Collegare un callback al processo di salvataggio Markdown che assegna a ogni immagine un nome basato su GUID.  
* Salvare il documento come Markdown in modo che il file generato faccia riferimento alle immagini appena rinominate.  

Se hai dimestichezza con Python di base e hai installato Aspose.Words, sarai operativo in meno di cinque minuti. Nessuno script esterno, nessuna rinomina manuale—solo un unico programma autonomo che fa il lavoro pesante per te.

---

## Prerequisiti — Cosa serve prima di iniziare

| Requisito | Perché è importante |
|-------------|----------------|
| **Python 3.7+** | L'esempio utilizza le f‑string e le annotazioni di tipo introdotte in 3.6, ma 3.7+ ti offre le comodità di `os.path.splitext`. |
| **Aspose.Words for Python via .NET** (`pip install aspose-words`) | Questa libreria fornisce la classe `aw.Document` e le `MarkdownSaveOptions` su cui facciamo affidamento. |
| **Write permission** to the output folder | Il callback creerà nuovi file immagine, quindi lo script deve avere il permesso di scriverli. |
| **A DOCX file** you want to convert | Qualsiasi cosa, da un semplice report a un manuale complesso, funzionerà. |

> **Consiglio professionale:** Se stai usando un ambiente virtuale, attivalo prima di installare Aspose.Words. Isola le dipendenze ed evita conflitti di versione.

---

## Passo 1: Carica il documento Word  

La prima cosa da fare quando vuoi **convertire docx in markdown** è aprire il file sorgente. Aspose.Words astrae tutta la gestione OPC a basso livello, quindi una sola riga fa il lavoro.

```python
import aspose.words as aw

# Replace YOUR_DIRECTORY with the folder that holds your .docx file
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

*Perché è importante:* Senza caricare il documento non puoi ispezionare le sue risorse, e l'esportatore Markdown non avrà nulla da scrivere. L'oggetto `aw.Document` contiene l'intero pacchetto Word in memoria, rendendo sicura la manipolazione prima del salvataggio.

---

## Passo 2: Scrivi un callback che **rinomina le risorse immagine**  

Aspose.Words ti permette di inserire un `resource_saving_callback` nelle `MarkdownSaveOptions`. Il callback riceve ogni risorsa (immagini, CSS, ecc.) proprio prima che venga scritta su disco. Mutando `resource.file_name` possiamo imporre **nomi immagine personalizzati**.

```python
def rename_image_resource(resource):
    """
    Rename image resources with a unique GUID before saving.
    This is where we implement how to rename images.
    """
    import uuid, os

    # Guard: only process image resources, ignore CSS or other files
    if not resource.file_name.lower().endswith(('.png', '.jpg', '.jpeg', '.gif', '.bmp')):
        return True  # Let Aspose handle non‑image resources unchanged

    # Extract the original extension so we keep PNG as PNG, JPG as JPG, etc.
    _, ext = os.path.splitext(resource.file_name)

    # Generate a globally unique identifier and tack the original extension on
    new_name = f"{uuid.uuid4()}{ext}"
    resource.file_name = new_name

    # Returning True tells Aspose to proceed with the default saving logic
    return True
```

### Perché usare un GUID?

* **Unicità** – Un GUID (`uuid4`) garantisce che due immagini non entrino mai in conflitto, anche tra più esecuzioni.  
* **Tracciabilità** – Se devi fare debug in seguito, il GUID può essere registrato insieme al numero del paragrafo originale di Word.  
* **Portabilità** – Nessuna dipendenza dallo schema di denominazione originale di Word, che potrebbe contenere spazi o caratteri speciali che rompono i collegamenti Markdown.

---

## Passo 3: Collega il callback alle opzioni di salvataggio Markdown  

Ora diciamo ad Aspose di usare la nostra logica di rinomina ogni volta che scrive un'immagine nella cartella di output.

```python
md_options = aw.saving.MarkdownSaveOptions()
md_options.resource_saving_callback = rename_image_resource

# Optional: control where images are placed relative to the markdown file
md_options.images_folder = "images"  # creates a sub‑folder called 'images'
```

*Spiegazione:* La classe `MarkdownSaveOptions` controlla tutto, dalle interruzioni di riga alla posizione della cartella immagini. Impostando `resource_saving_callback`, ottieni un **hook** che si attiva per ogni risorsa incorporata, dandoti la possibilità di **cambiare i nomi delle immagini** prima che il file venga scritto su disco.

---

## Passo 4: Salva il documento come Markdown – L'ultimo pezzo  

Con il callback in atto, l'ultimo passo è diretto.

```python
output_path = "YOUR_DIRECTORY/CustomResources.md"
doc.save(output_path, md_options)
print(f"Markdown saved to {output_path}")
```

Al termine dello script troverai:

* `CustomResources.md` – la rappresentazione Markdown del tuo file Word.  
* Una cartella `images/` (o quella che hai impostato) contenente file come `d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e.png`.  

Il file Markdown farà riferimento ai nuovi nomi basati su GUID, così qualsiasi processore a valle (GitHub, MkDocs, ecc.) prenderà le immagini corrette senza che tu debba rinominarle manualmente.

### Output previsto (estratto)

```markdown
# Sample Document

Here is an image that was originally called `image1.png` in the DOCX:

![d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e](images/d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e.png)

And another one:

![a1b2c3d4-e5f6-7a8b-9c0d-e1f2a3b4c5d6](images/a1b2c3d4-e5f6-7a8b-9c0d-e1f2a3b4c5d6.jpg)
```

I GUID varieranno a ogni esecuzione, ma il modello rimane lo stesso.

---

## Gestione dei casi limite e domande comuni  

### E se il documento contiene risorse non‑immagine?  

Il nostro callback verifica già l'estensione del file e restituisce `True` per tutto ciò che non è un'immagine. Questo significa che file CSS, font o oggetti OLE incorporati mantengono i loro nomi originali, il che è solitamente ciò che desideri quando **salvi word come markdown**.

### Posso usare uno schema di denominazione personalizzato invece dei GUID?  

Assolutamente. Sostituisci la chiamata `uuid.uuid4()` con qualsiasi funzione che restituisca una stringa. Per esempio, potresti anteporre l'indice del paragrafo originale:

```python
new_name = f"para{resource.resource_id}{ext}"
```

Assicurati solo che il nome risultante sia unico nell'intero documento.

### Come influisce sulle prestazioni con documenti di grandi dimensioni?  

Il callback viene eseguito una volta per risorsa, quindi il sovraccarico è minimo—principalmente il tempo necessario a generare un GUID. Anche un report di 200 pagine con decine di immagini termina in meno di un secondo su un laptop moderno.

### E se ho bisogno che i nomi dei file immagine siano deterministici (ad esempio, per build CI)?  

Sostituisci `uuid.uuid4()` con un hash dei byte originali dell'immagine:

```python
import hashlib
hash = hashlib.sha256(resource.raw_bytes).hexdigest()[:12]
new_name = f"{hash}{ext}"
```

Questo produce lo stesso nome file ogni volta che esegui lo script sulla stessa immagine di origine.

---

## Script completo funzionante – Copia, incolla, esegui  



## Cosa dovresti imparare dopo?

I tutorial seguenti coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [salva docx come markdown – Guida completa C# con estrazione immagini](/words/english/net/programming-with-markdownsaveoptions/save-docx-as-markdown-full-c-guide-with-image-extraction/)
- [Come salvare Markdown da DOCX – Guida passo‑passo](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}