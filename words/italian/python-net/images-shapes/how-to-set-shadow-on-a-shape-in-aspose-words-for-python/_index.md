---
category: general
date: 2026-09-27
description: Scopri come impostare l'ombra su una forma con Aspose.Words per Python.
  Questa guida copre l'aggiunta dell'ombra alla forma, l'applicazione dell'effetto
  ombra e l'impostazione del colore dell'ombra.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to set shadow
- add shadow to shape
- apply shadow effect
- set shadow color
- how to add shadow
language: it
lastmod: 2026-09-27
og_description: Come impostare l'ombra su una forma usando Aspose.Words per Python.
  Segui la guida passo‑passo per aggiungere l'ombra alla forma, applicare l'effetto
  ombra e impostare il colore dell'ombra.
og_image_alt: Screenshot showing how to set shadow on a shape in a Word document
og_title: Come impostare l'ombra su una forma in Aspose.Words per Python
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to set shadow on a shape with Aspose.Words for Python. This
    guide covers add shadow to shape, apply shadow effect, and set shadow color.
  headline: How to set shadow on a shape in Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Shapes
- Shadow effect
title: Come impostare l'ombra su una forma in Aspose.Words per Python
url: /it/python/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come impostare l'ombra su una forma in Aspose.Words per Python

Se hai bisogno di **impostare l'ombra** per un oggetto di disegno, questa guida mostra l'intero processo. Vedrai come aggiungere l'ombra a una forma, configurare la sfocatura, lo spostamento e il colore dell'ombra, e salvare il documento aggiornato senza uscire dal codice.

Il tutorial presuppone che tu abbia già un ambiente di base Aspose.Words per Python. Alla fine dell'articolo sarai in grado di applicare un effetto ombra dall'aspetto professionale a qualsiasi forma in un file DOCX.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* Python 3.8+ installato.
* Aspose.Words per Python via .NET (`pip install aspose-words`) installato.
* Un documento Word (`input.docx`) che contiene almeno una forma (ad esempio, un rettangolo o un'immagine).  
  Se il documento è vuoto, il codice creerà una nuova forma per la dimostrazione.

Questi elementi garantiscono che i passaggi successivi vengano eseguiti senza errori di importazione.

## Passo 1: Caricare o creare il documento Word

La prima operazione è ottenere un oggetto `Document`. Puoi caricare un file esistente o crearne uno nuovo.

```python
import aspose.words as aw

# Load an existing document, or create a new blank document if the file does not exist.
try:
    doc = aw.Document("YOUR_DIRECTORY/input.docx")
except Exception:
    doc = aw.Document()          # Creates an empty document
    # Optional: add a paragraph so the document is not completely empty.
    builder = aw.DocumentBuilder(doc)
    builder.writeln("Document created for shadow demo.")
```

*Perché questo passaggio è importante*: L'oggetto `Document` è il punto di ingresso per tutte le operazioni di elaborazione Word. Senza di esso non è possibile accedere alle forme o applicare effetti visivi.

## Passo 2: Recuperare la forma target

Per manipolare l'aspetto di una forma è necessaria un riferimento al nodo della forma. L'esempio seguente recupera la prima forma trovata nella gerarchia del documento.

```python
# Retrieve the first shape in the document tree.
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# If the document has no shapes, create one for demonstration purposes.
if shape is None:
    builder = aw.DocumentBuilder(doc)
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 100)
    shape.wrap_type = aw.drawing.WrapType.INLINE
```

*Perché questo passaggio è importante*: `add shadow to shape` richiede un oggetto forma concreto. Il codice gestisce in modo sicuro il caso limite in cui il documento non contiene forme, garantendo che il tutorial funzioni per ogni lettore.

## Passo 3: Configurare l'aspetto dell'ombra

Ora puoi **applicare l'effetto ombra** regolando la proprietà `shadow` della forma. Le impostazioni seguenti forniscono un'ombra sottile e scura.

```python
# Set the shadow blur radius (softness). Larger values produce a more diffused shadow.
shape.shadow.blur = 5.0

# Horizontal displacement of the shadow in points.
shape.shadow.offset_x = 2.0

# Vertical displacement of the shadow in points.
shape.shadow.offset_y = 2.0

# Set the shadow color. This demonstrates **set shadow color** to black.
shape.shadow.color = aw.Color.black

# Enable the shadow (some older versions require explicit visibility).
shape.shadow.visible = True
```

*Perché ogni proprietà è importante*:

| Proprietà | Effetto |
|-----------|---------|
| `blur`   | Controlla quanto è sfocata l'ombra. |
| `offset_x` / `offset_y` | Determina la direzione e la distanza dalla forma. |
| `color`  | Definisce la tonalità dell'ombra; puoi usare qualsiasi `aw.Color`. |
| `visible`| Garantisce che l'ombra sia renderizzata nel file di output. |

Puoi sostituire `aw.Color.black` con `aw.Color.from_argb(255, 0, 0, 0)` per un valore RGBA personalizzato, o con qualsiasi altro colore predefinito.

## Passo 4: Salvare il documento modificato

Dopo aver configurato l'ombra, persisti le modifiche in un nuovo file.

```python
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved with shadow effect at: {output_path}")
```

Quando apri `output.docx` in Microsoft Word, la forma selezionata mostrerà un'ombra nera morbida spostata di 2 pt a destra e 2 pt in basso.

## Esempio completo funzionante

Unendo tutti i passaggi si ottiene uno script autonomo che puoi copiare‑incollare nel tuo IDE.

```python
import aspose.words as aw

def add_shadow_to_first_shape(input_path: str, output_path: str):
    # Load or create the document.
    try:
        doc = aw.Document(input_path)
    except Exception:
        doc = aw.Document()
        builder = aw.DocumentBuilder(doc)
        builder.writeln("Document created for shadow demo.")

    # Retrieve the first shape; create one if none exist.
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
    if shape is None:
        builder = aw.DocumentBuilder(doc)
        shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 100)
        shape.wrap_type = aw.drawing.WrapType.INLINE

    # Apply shadow settings.
    shape.shadow.blur = 5.0
    shape.shadow.offset_x = 2.0
    shape.shadow.offset_y = 2.0
    shape.shadow.color = aw.Color.black
    shape.shadow.visible = True

    # Save the result.
    doc.save(output_path)
    print(f"Shadow applied and saved to {output_path}")

# Example usage
if __name__ == "__main__":
    add_shadow_to_first_shape(
        input_path="YOUR_DIRECTORY/input.docx",
        output_path="YOUR_DIRECTORY/output.docx"
    )
```

Eseguendo lo script si genera `output.docx` dove la prima forma contiene l'ombra configurata.

## Problemi comuni e come evitarli

| Problema | Motivo | Soluzione |
|----------|--------|-----------|
| `shape` è `None` anche dopo aver caricato un documento | Il documento non contiene oggetti di disegno. | Usa il blocco di creazione forma di fallback mostrato al Passo 2. |
| L'ombra non appare in Word | `shape.shadow.visible` lasciato a `False` o il documento è stato salvato in un formato più vecchio (ad es., `.doc`). | Assicurati che `visible = True` e salva come `.docx`. |
| Il colore appare diverso da quanto previsto | Il tema del documento sovrascrive i colori espliciti. | Imposta `shape.shadow.color` dopo aver disabilitato le sovrascritture del tema, o usa `aw.Color.from_argb`. |

Gestire questi casi limite rende la soluzione robusta per il codice di produzione.

## Estendere l'effetto (passi successivi)

Ora che sai **come aggiungere l'ombra**, puoi esplorare miglioramenti correlati:

* **apply shadow effect** con gradiente o ombre multiple regolando le sotto‑proprietà di `shape.shadow`.
* Usa **set shadow color** in modo dinamico basandoti sull'input dell'utente o sui colori del tema.
* Combina **add shadow to shape** con altre azioni di formattazione come rotazione, stile di linea o effetti 3‑D.
* Automatizza l'aggiunta dell'ombra per ogni forma in un documento iterando su `doc.get_child_nodes(aw.NodeType.SHAPE, True)`.

## Conclusione

Ora disponi di una soluzione completa e eseguibile per **impostare l'ombra** su una forma usando Aspose.Words per Python. La guida ha coperto il caricamento di un documento, il recupero o la creazione di una forma, la configurazione della sfocatura, dello spostamento e **set shadow color**, e infine il salvataggio del file. Applica questo modello a qualsiasi forma nei tuoi progetti di automazione e sperimenta ulteriori regolazioni visive per soddisfare i requisiti di design.

--- 

*Sentiti libero di adattare il codice per altri tipi di forma, colori o valori di offset. Se incontri problemi, consultare la tabella “Problemi comuni” è un buon primo passo.*

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Aggiungi ombra a una forma in C# – Guida completa per applicare l'effetto ombra](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-c-complete-guide-to-apply-shadow-effe/)
- [Aggiungi ombra a una forma in Word – Guida completa Aspose.Words](/words/english/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/)
- [Crea forma rettangolare, aggiungi ombra e salva PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}