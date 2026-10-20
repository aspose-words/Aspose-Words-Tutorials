---
category: general
date: 2026-08-01
description: Come impostare l'ombra su una forma di Word usando Aspose.Words per Python.
  Impara a modificare l'opacità, regolare la sfocatura e cambiare rapidamente la distanza
  dell'ombra.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to set shadow
- how to change opacity
- how to adjust blur
- change shadow distance
- how to use aspose.words
language: it
lastmod: 2026-08-01
og_description: Come impostare l'ombra su una forma con Aspose.Words per Python. Segui
  questo tutorial passo‑passo per modificare l'opacità, regolare la sfocatura e cambiare
  la distanza dell'ombra.
og_image_alt: Screenshot showing how to set shadow on a shape using Aspose.Words in
  Python
og_title: Come impostare l'ombra in Aspose.Words – Guida rapida Python
schemas:
- author: Aspose
  dateModified: '2026-08-01'
  description: How to set shadow on a Word shape using Aspose.Words for Python. Learn
    to change opacity, adjust blur, and change shadow distance quickly.
  headline: How to Set Shadow in Aspose.Words – Python Example
  type: TechArticle
- description: How to set shadow on a Word shape using Aspose.Words for Python. Learn
    to change opacity, adjust blur, and change shadow distance quickly.
  name: How to Set Shadow in Aspose.Words – Python Example
  steps:
  - name: '**Create the document** (or load a template).'
    text: '**Create the document** (or load a template).'
  - name: '**Insert the logo shape** (via `DocumentBuilder.insert_image` or `Shape`).'
    text: '**Insert the logo shape** (via `DocumentBuilder.insert_image` or `Shape`).'
  - name: '**Call `apply_shadow`** with your brand’s shadow specs.'
    text: '**Call `apply_shadow`** with your brand’s shadow specs.'
  - name: '**Export** to DOCX, PDF, or HTML with a single line of code.'
    text: '**Export** to DOCX, PDF, or HTML with a single line of code.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Shadow Formatting
- Word Automation
title: Come impostare l'ombra in Aspose.Words – Esempio Python
url: /it/python/images-shapes/how-to-set-shadow-in-aspose-words-python-example/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come impostare l'ombra in Aspose.Words – Esempio Python

Ti sei mai chiesto **come impostare l'ombra** su una forma di Word senza aprire manualmente il documento? Non sei il solo—molti sviluppatori incontrano questo ostacolo quando automatizzano report o creano modelli coerenti con il branding. La buona notizia? Con Aspose.Words per Python puoi modificare l'ombra di una forma, l'opacità, la sfocatura e la distanza con poche righe di codice.

In questo tutorial percorreremo un esempio completo e eseguibile che mostra **come impostare l'ombra**, **come cambiare l'opacità**, **come regolare la sfocatura**, e persino **come modificare la distanza dell'ombra**. Alla fine avrai una solida comprensione di **come usare Aspose.Words** per stilizzare le forme programmaticamente.

---

![Come impostare l'ombra su una forma usando Aspose.Words](image-placeholder.png){alt="Come impostare l'ombra su una forma usando Aspose.Words"}

## Prerequisiti

Prima di immergerci, assicurati di avere:

| Requisito | Motivo |
|-----------|--------|
| Python 3.8+ | Sintassi moderna, type hints |
| `aspose-words` package (pip install aspose-words) | Libreria principale per la manipolazione di Word |
| Un file di esempio `input.docx` con almeno una forma | La forma a cui aggiungeremo l'ombra |
| Permesso di scrittura nella cartella dove salverai `output.docx` | Per persistere le modifiche |

Nessun DLL aggiuntivo o interop COM—Aspose.Words è puro‑Python, quindi puoi eseguirlo su Windows, macOS o Linux.

---

## Come impostare l'ombra su una forma con Aspose.Words

Di seguito trovi lo script **completo**. Carica un documento, trova la prima forma (ricorsivamente), configura l'ombra e salva il risultato. Ogni riga è commentata così capisci **perché** è presente, non solo **cosa** fa.

```python
# ------------------------------------------------------------
# How to Set Shadow – Full Python Example using Aspose.Words
# ------------------------------------------------------------
import aspose.words as aw  # Import the Aspose.Words namespace

def apply_shadow(
    input_path: str,
    output_path: str,
    distance: int = 5,
    blur: float = 4.0,
    opacity: float = 0.6
) -> None:
    """
    Demonstrates how to set shadow on the first shape in a Word document.
    
    Parameters
    ----------
    input_path : str
        Path to the source .docx file.
    output_path : str
        Path where the modified .docx will be saved.
    distance : int, optional
        How far the shadow is offset from the shape (default = 5 points).
    blur : float, optional
        Blur radius of the shadow (default = 4.0 points).
    opacity : float, optional
        Opacity of the shadow (0 = fully transparent, 1 = fully opaque).
    """
    # Step 1: Load the Word document
    doc = aw.Document(input_path)

    # Step 2: Retrieve the first shape in the document (searches recursively)
    # The `True` flag makes the search go deep into headers, footers, and groups.
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

    if shape is None:
        raise ValueError("No shape found in the document. Add a shape and try again.")

    # Step 3: Configure the shadow appearance for the shape
    # ----------------------------------------------------
    # distance → how far the shadow sits away from the shape edge
    # blur     → softness of the shadow edge
    # opacity  → transparency level (0‑1 range)
    shape.shadow_format.distance = distance          # change shadow distance
    shape.shadow_format.blur = blur                  # how to adjust blur
    shape.shadow_format.opacity = opacity            # how to change opacity

    # Optional: tweak color and style if you need more control
    shape.shadow_format.color = aw.Color.black
    shape.shadow_format.style = aw.ShadowStyle.OUTER_SHADOW

    # Step 4: Save the modified document
    doc.save(output_path)

# -----------------------------------------------------------------
# Example usage – adjust the parameters to see different results
# -----------------------------------------------------------------
if __name__ == "__main__":
    apply_shadow(
        input_path="YOUR_DIRECTORY/input.docx",
        output_path="YOUR_DIRECTORY/output.docx",
        distance=8,       # increase distance for a more pronounced offset
        blur=6.5,         # higher blur makes the shadow softer
        opacity=0.75      # make the shadow a bit more solid
    )
```

### Perché funziona

* **`doc.get_child(..., True)`** – Il flag `True` indica ad Aspose.Words di cercare **ricorsivamente**, così anche le forme all'interno di intestazioni, piè di pagina o oggetti raggruppati vengono trovate. È fondamentale quando non sai esattamente dove si trovi la forma.  
* **`shadow_format`** – Questa proprietà raggruppa tutte le impostazioni relative all'ombra. Impostando `distance`, `blur` e `opacity` controlli la profondità visiva della forma. Modificando uno di questi valori dimostri **come cambiare l'opacità**, **come regolare la sfocatura**, e **modificare la distanza dell'ombra** in una singola chiamata coerente.  
* **`Saving`** – `doc.save` scrive un nuovo file `.docx`. L'originale rimane intatto, il che è un modello sicuro per l'elaborazione batch.

---

## Come cambiare l'opacità dell'ombra di una forma

L'opacità determina quanto trasparente appare l'ombra. L'intervallo è da 0.0 (completamente invisibile) a 1.0 (completamente solida). Nel codice sopra puoi semplicemente modificare l'argomento `opacity`:

```python
shape.shadow_format.opacity = 0.85  # 85% opaque – looks richer on dark backgrounds
```

> **Consiglio professionale:** Quando generi PDF successivamente, un'opacità più alta spesso si traduce in un'ombra più profonda e più stampabile. Sperimenta valori tra 0.4 e 0.9 per trovare il punto ideale per le linee guida del tuo brand.

---

## Come regolare la sfocatura per un aspetto più morbido

La sfocatura è il raggio della sfocatura gaussiana applicata ai bordi dell'ombra. Un numero più grande produce un effetto sfumato:

```python
shape.shadow_format.blur = 10.0  # Very soft, almost hazy shadow
```

Se ti serve un aspetto nitido, tipo ombra proiettata (pensa allo stile “Microsoft PowerPoint”), imposta `blur` a un valore basso come `1.0`.

---

## Modifica la distanza dell'ombra per creare profondità

La distanza è misurata in punti (1 pt = 1/72 in). Spostare l'ombra più lontano fa apparire la forma più sospesa:

```python
shape.shadow_format.distance = 12  # Shadow shifts 12 pt away from the shape
```

Combina una `distance` più grande con una `blur` moderata per un effetto drammatico, “sollevato”.

---

## Mettere tutto insieme – Un mini‑progetto

Immagina di costruire un generatore di report automatizzato che inserisce il logo aziendale all'interno di una casella di testo. Vuoi che ogni logo abbia un'ombra sottile che corrisponda allo stile aziendale. Usando la funzione `apply_shadow` puoi:

1. **Crea il documento** (o carica un modello).
2. **Inserisci la forma del logo** (tramite `DocumentBuilder.insert_image` o `Shape`).
3. **Chiama `apply_shadow`** con le specifiche dell'ombra del tuo brand.
4. **Esporta** in DOCX, PDF o HTML con una singola riga di codice.

Poiché la funzione accetta parametri, puoi memorizzare le impostazioni dell'ombra in un file JSON e applicarle a decine di documenti—senza necessità di interventi manuali.

---

## Domande comuni e casi particolari

| Domanda | Risposta |
|----------|--------|
| **E se il documento contiene più forme?** | L'esempio prende di mira la *prima* forma. Per influenzare tutte le forme, itera con `doc.get_child_nodes(aw.NodeType.SHAPE, True)` e applica le stesse impostazioni `shadow_format` a ciascun nodo. |
| **Posso impostare un colore dell'ombra diverso?** | Assolutamente. Usa `shape.shadow_format.color = aw.Color(255, 0, 0)` per un'ombra rossa, o qualsiasi `aw.Color` desideri. |
| **Queste impostazioni sopravvivono a una conversione in PDF?** | Sì. Aspose.Words conserva le proprietà dell'ombra durante il rendering in PDF, anche se valori di sfocatura molto alti possono essere approssimati. |
| **C'è un impatto sulle prestazioni per documenti di grandi dimensioni?** | L'API dell'ombra agisce solo sugli oggetti forma, quindi anche un report di 500 pagine viene elaborato in millisecondi. Il collo di bottiglia è solitamente I/O, non la configurazione dell'ombra. |
| **Posso rimuovere l'ombra in seguito?** | Imposta `shape.shadow_format.is_visible = False` o semplicemente reimposta le proprietà ai valori predefiniti. |

---

## Riepilogo dell'esempio completo funzionante

Ecco di nuovo l'intero script, privo di commenti per un rapido copia‑incolla:

```python
import aspose.words as aw

def apply_shadow(input_path, output_path, distance=5, blur=4.0, opacity=0.6):
    doc = aw.Document(input_path)
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
    if shape is None:
        raise ValueError("No shape found.")
    shape.shadow_format.distance = distance
    shape.shadow_format.blur = blur
    shape.shadow_format.opacity = opacity
    shape.shadow_format.color = aw.Color.black
    shape.shadow_format.style = aw.ShadowStyle.OUTER_SHADOW
    doc.save(output_path)

if __name__ == "__main__":
    apply_shadow(
        "YOUR_DIRECTORY/input.docx",
        "YOUR_DIRECTORY/output.docx",
        distance=8,
        blur=6.5,
        opacity=0.75
    )
```

Esegui lo script, apri `output.docx` e vedrai la forma con una pulita ombra che corrisponde ai parametri impostati.

---

## Conclusione

Abbiamo coperto **

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Tutorial Ombra Forma Aspose.Words – Aggiungi un'ombra a una forma Word in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Come implementare commenti e risposte nei documenti Word usando Aspose.Words per Python](/words/english/python-net/annotations-comments/aspose-words-python-comments-replies/)
- [Come gestire le variabili del documento con Aspose.Words in Python: Guida completa](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}