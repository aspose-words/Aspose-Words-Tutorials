---
category: general
date: 2026-06-24
description: Come impostare un callback per esportare le immagini da DOCX durante
  il salvataggio in Markdown. Scopri come estrarre le immagini, estrarre SVG da Word
  e salvare DOCX come Markdown con gestione personalizzata.
draft: false
keywords:
- how to set callback
- export images from docx
- how to extract images
- save docx as markdown
- extract svg from word
language: it
og_description: Come impostare il callback per esportare le immagini da DOCX durante
  la conversione in Markdown. Questa guida ti mostra come estrarre immagini e SVG
  in modo efficiente.
og_title: Come impostare il callback per l'esportazione delle immagini da DOCX
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  headline: How to Set Callback for Exporting Images from DOCX
  type: TechArticle
- description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  name: How to Set Callback for Exporting Images from DOCX
  steps:
  - name: '**Deterministic names** – useful for version control or CDN publishing.'
    text: '**Deterministic names** – useful for version control or CDN publishing.'
  - name: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
    text: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
  - name: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
    text: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Conversion
title: Come impostare il callback per l'esportazione delle immagini da DOCX
url: /it/python/content-extraction-and-manipulation/how-to-set-callback-for-exporting-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come impostare il callback per l'esportazione delle immagini da DOCX

Ti sei mai chiesto **come impostare il callback** in modo da poter **esportare le immagini da DOCX** durante la conversione in Markdown? Non sei l'unico. Molti sviluppatori si trovano in difficoltà quando la conversione predefinita scarica tutte le immagini in una cartella generica o, peggio, perde completamente le grafiche SVG.  

In questo tutorial percorreremo una soluzione completa, pronta‑all'uso, che risponde alla domanda “come impostare il callback”, mostra **come estrarre le immagini**, e copre anche **l'estrazione di SVG da Word**. Alla fine sarai in grado di **salvare DOCX come Markdown** con uno schema di denominazione personalizzato per ogni risorsa immagine—senza alcuna manipolazione manuale.

## Cosa imparerai

- Perché un callback è il modo più pulito per controllare i nomi dei file immagine durante la conversione.  
- Come collegarsi al `MarkdownSaveOptions.resource_saving_callback` di Aspose.Words.  
- Codice passo‑passo che estrae **PNG**, **JPG**, **SVG** e qualsiasi altra risorsa incorporata.  
- Suggerimenti per gestire collisioni di nomi, file di grandi dimensioni e particolarità dei percorsi cross‑platform.  

> **Consiglio professionale:** Se stai già usando Aspose.Words in una pipeline più ampia, puoi inserire questo callback senza modificare il resto del tuo codice.

---

![Diagramma di come impostare il callback](https://example.com/images/how-to-set-callback.png "come impostare il callback")

## Prerequisiti

- Python 3.8+ (l'esempio utilizza le f‑string, quindi 3.6+ è sufficiente).  
- Pacchetto `aspose-words` installato (`pip install aspose-words`).  
- Un file DOCX che contiene immagini raster **e** grafiche vettoriali (SVG).  
- Familiarità di base con le funzioni Python e la gestione dei file I/O.

Se li hai, immergiamoci.

## Come impostare il callback per l'esportazione delle immagini da DOCX

Il cuore della soluzione risiede in un **callback di salvataggio risorse**. Aspose.Words chiama questo delegato per ogni immagine o SVG che vuole scrivere quando invochi `document.save`. Restituendo una tupla `(new_name, data)` decidi sia il nome del file sia il contenuto in byte.

```python
import aspose.words as aw
import os
import hashlib

# Step 1: Load the source document
document = aw.Document("YOUR_DIRECTORY/input.docx")
```

### Perché un callback?

Senza un callback, Aspose.Words crea file chiamati `image1.png`, `image2.svg`, ecc., e li colloca in una cartella accanto al file Markdown. Questo va bene per demo rapide, ma in produzione spesso è necessario:

1. **Nomi deterministici** – utili per il controllo di versione o la pubblicazione su CDN.  
2. **Evitare collisioni** – due immagini con lo stesso nome originale non si sovrascriveranno.  
3. **Strutture di cartelle personalizzate** – magari vuoi tutti gli asset sotto `/assets/docs/`.  

Il callback ti dà il pieno controllo su queste tre esigenze.

---

## Esporta immagini da DOCX usando un callback di risorsa

Di seguito trovi l'implementazione del callback. Genera un hash dei dati binari per produrre un suffisso unico, conserva l'estensione originale del file e restituisce il nuovo nome file insieme ai byte grezzi.

```python
def resource_callback(resource):
    """
    Called for every image/SVG that MarkdownSaveOptions wants to write.
    Returns a tuple (new_name, data) to control the saved file name.
    """
    # Preserve the original extension (.png, .svg, …)
    extension = os.path.splitext(resource.name)[1]

    # Compute a short hash of the image bytes – guarantees uniqueness
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]

    # Build a deterministic, collision‑free filename
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data
```

#### Gestione dei casi limite

- **File di grandi dimensioni:** SHA‑256 funziona bene per qualsiasi dimensione; l'hash è calcolato in memoria, quindi fai attenzione ai limiti di memoria se stai elaborando PDF enormi.  
- **Estensioni mancanti:** Alcuni file Word più vecchi possono memorizzare immagini senza un'estensione esplicita. In tal caso `extension` sarà vuoto; puoi impostare `.bin` come predefinito o ispezionare i primi byte per indovinare il formato.  
- **Risorse non‑immagine:** Il callback è invocato per ogni risorsa esterna (ad esempio oggetti OLE). Se ti interessano solo immagini/SVG, filtra per `resource.type` prima di procedere.

---

## Come estrarre immagini e SVG da Word

Ora colleghiamo il callback nella pipeline di salvataggio Markdown. L'oggetto `MarkdownSaveOptions` espone la proprietà `resource_saving_callback` proprio a questo scopo.

```python
# Step 2: Configure Markdown save options to use the callback
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.resource_saving_callback = resource_callback

# Optional: set the folder where images will be placed relative to the .md file
markdown_options.resource_folder = "assets/images"
```

Impostare `resource_folder` è opzionale ma spesso comodo. Se lo ometti, le immagini finiscono accanto al file Markdown, il che può ingombrare la radice del progetto.

### Salvataggio del documento

```python
# Step 3: Save the document as Markdown, letting the callback store the resources
output_md_path = "YOUR_DIRECTORY/output.md"
document.save(output_md_path, markdown_options)
print(f"Markdown saved to {output_md_path}")
```

Quando esegui lo script, vedrai una serie di file come:

```
assets/images/img_a1b2c3d4e5.png
assets/images/img_f6g7h8i9j0.svg
```

E il `output.md` generato conterrà link alle immagini che puntano a quei nomi file esatti:

```markdown
![Image](assets/images/img_a1b2c3d4e5.png)
```

Questa è la parte **come estrarre le immagini** in azione—ogni immagine, raster o vettoriale, è ora una risorsa separata con nome unico.

---

## Salva DOCX come Markdown con gestione personalizzata delle immagini

Mettendo tutto insieme, ecco lo script completo che puoi copiare‑incollare in un file chiamato `convert_docx_to_md.py`:

```python
import aspose.words as aw
import os
import hashlib

def resource_callback(resource):
    """Control the naming of each exported image/SVG."""
    extension = os.path.splitext(resource.name)[1] or ".bin"
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data

def convert_docx_to_markdown(input_path, output_md_path, image_folder="assets/images"):
    # Load the DOCX
    document = aw.Document(input_path)

    # Set up Markdown options with our callback
    md_options = aw.saving.MarkdownSaveOptions()
    md_options.resource_saving_callback = resource_callback
    md_options.resource_folder = image_folder

    # Ensure the output directory exists
    os.makedirs(os.path.dirname(output_md_path), exist_ok=True)
    os.makedirs(os.path.join(os.path.dirname(output_md_path), image_folder), exist_ok=True)

    # Perform the conversion
    document.save(output_md_path, md_options)
    print(f"✅ Conversion complete! Markdown at: {output_md_path}")

if __name__ == "__main__":
    # Adjust these paths to your environment
    INPUT_DOCX = "YOUR_DIRECTORY/input.docx"
    OUTPUT_MD = "YOUR_DIRECTORY/output.md"
    convert_docx_to_markdown(INPUT_DOCX, OUTPUT_MD)
```

**Perché funziona:**  
- Il `resource_callback` garantisce che ogni immagine ottenga un nome unico e riproducibile.  
- `resource_folder` mantiene il Markdown ordinato separando le risorse.  
- Le chiamate `os.makedirs` ti proteggono da errori “cartella non trovata” quando lo script viene eseguito su una macchina nuova.

---

## Estrai SVG da Word – Cosa succede alle grafiche vettoriali?

Gli SVG sono trattati allo stesso modo dei PNG dal callback perché sono semplicemente un altro `resource`. L'unica sfumatura è che alcune versioni più vecchie di Word incorporano gli SVG come oggetti *OfficeArt*, che Aspose.Words converte automaticamente in un PNG raster a meno che non abiliti esplicitamente il flag **preserve SVG**:

```python
md_options.export_svg = True  # Keep original SVG markup
```

Aggiungi quella riga prima del salvataggio, e il callback riceverà risorse con estensione `.svg`, preservando i dati vettoriali nitidi—perfetto per documenti web responsivi.

---

## Domande frequenti e insidie

| Domanda | Risposta |
|----------|--------|
| **E se due immagini sono identiche?** | L'hash SHA‑256 sarà identico, quindi i nomi file collidono. Se ti servono entrambe le copie, includi il `resource.name` originale nel calcolo dell'hash (ad esempio, `hash(resource.name + resource.data)`). |
| **Posso cambiare la cartella per tipo di file?** | Sì. All'interno di `resource_callback` puoi ispezionare `extension` e restituire un percorso come `f"png/{new_name}"` per le immagini raster e `f"svg/{new_name}"` per i vettoriali. |
| **Funziona su Linux/macOS?** | Assolutamente. Il codice utilizza `os.path` che astrae i separatori di percorso. Assicurati solo di avere il file di licenza Aspose.Words (`aspose.words.lic`) accessibile se usi la versione a pagamento. |
| **Cosa riguarda l'uso della memoria per documenti enormi?** | Il callback riceve l'**array di byte completo** per ogni risorsa, il che significa che l'intera immagine vive temporaneamente in memoria. Per file multi‑gigabyte potresti voler streammare i dati su disco all'interno del callback invece di restituirli. |

---

## Conclusione

Ora sai **come impostare il callback** per controllare l'estrazione delle immagini quando **salvi DOCX come Markdown**. L'approccio ti permette di **esportare immagini da DOCX**, **estrarre SVG da Word**, e mantenere il tuo Markdown pulito e deterministico.  

In un unico script autonomo abbiamo coperto il caricamento di un documento, la definizione di un callback di salvataggio risorse, la configurazione di `MarkdownSaveOptions` e la gestione di casi limite come collisioni di nomi e grafiche vettoriali. Il risultato è un insieme di risorse con nomi unici accanto a un file Markdown perfettamente collegato—pronto per generatori di siti statici, pipeline di documentazione o qualsiasi flusso di lavoro che richieda risorse pulite e riutilizzabili.  

**Prossimi passi?**  
- Prova a concatenare questo con un generatore di siti statici come MkDocs per pubblicare automaticamente documenti basati su Word.  
- Sperimenta con `markdown_options.export_images_as_base64 = True` se preferisci immagini inline invece di file esterni.  
- Approfondisci gli altri callback di Aspose.Words (ad esempio, `document_saving_callback`) per controllare direttamente l'output Markdown.  

Hai altre domande su **come estrarre immagini** da altri formati Office, o hai bisogno di aiuto per modificare il callback per una convenzione di denominazione specifica? Lascia un commento qui sotto, e buona programmazione!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come rinominare le immagini durante la conversione da DOCX a Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)
- [Come salvare Markdown da DOCX – Guida passo‑passo](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}