---
category: general
date: 2026-10-04
description: Come creare un documento in Python e aggiungere un'ombra a una forma
  usando Aspose.Words. Impara a impostare il colore dell'ombra, inserire una forma
  rettangolare e personalizzare l'ombra esterna.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create document
- add shadow to shape
- set shadow color
- insert rectangle shape
- how to add shadow
language: it
lastmod: 2026-10-04
og_description: Come creare un documento in Python e aggiungere un'ombra a una forma.
  Questa guida mostra come impostare il colore dell'ombra, inserire una forma rettangolare
  e applicare un'ombra esterna usando Aspose.Words.
og_image_alt: Python code inserting a rectangle shape with a visible shadow into a
  Word document
og_title: Come creare un documento con una forma rettangolare e ombra in Python
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  headline: How to create document with a rectangle shape and shadow in Python
  type: TechArticle
- description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  name: How to create document with a rectangle shape and shadow in Python
  steps:
  - name: Why does the shadow sometimes appear invisible?
    text: The shadow is only rendered if `shadow.visible` is set to `True` **and**
      the shape’s `wrap_type` allows it to be displayed. An inline shape works reliably;
      floating shapes may require additional layout adjustments.
  - name: How can I change the shadow color to match a brand palette?
    text: 'Replace `aw.drawing.Color.black` with a custom RGB value:'
  - name: What if I need the shape to appear behind text?
    text: Set the wrap type to `WrapType.BEHIND` and adjust the `z_order_position`
      if necessary. Keep in mind that some viewers may render behind‑text shapes differently.
  - name: Can I apply the same shadow settings to multiple shapes?
    text: Yes. Create a helper function that configures the shadow and call it for
      each shape you insert. This promotes code reuse and ensures consistent styling.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Come creare un documento con una forma rettangolare e ombra in Python
url: /it/python/images-shapes/how-to-create-document-with-a-rectangle-shape-and-shadow-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un documento con una forma rettangolare e ombra in Python

Se hai bisogno di **come creare un documento** che contenga un rettangolo stilizzato, questa guida fornisce una soluzione completa. Vedrai come **aggiungere ombra alla forma**, impostare il colore dell'ombra e controllare il suo offset e sfocatura—tutto con Aspose.Words per Python. Alla fine del tutorial potrai generare un file `.docx` dall'aspetto curato e pronto per la distribuzione.

I passaggi seguenti coprono tutto, dall'installazione della libreria alla personalizzazione dell'aspetto dell'ombra. Non è necessaria alcuna documentazione esterna; il codice è pronto per essere copiato, eseguito e adattato ai tuoi progetti. Imparerai anche come **inserire una forma rettangolare**, scegliere uno **stile di ombra esterna** e gestire problemi comuni come ombre invisibili o impostazioni di avvolgimento errate.

## Prerequisiti

* Python 3.8 o versioni successive installato.
* Una licenza attiva di Aspose.Words per Python (o una chiave di valutazione gratuita).
* Familiarità di base con lo scripting Python.
* Accesso a una posizione del file system dove il documento generato sarà salvato.

Puoi installare l'SDK con pip:

```bash
pip install aspose-words
```

## Passo 1: Importare la libreria e creare un nuovo documento vuoto

Creare un nuovo documento è la prima azione in qualsiasi scenario di automazione Word. Il costruttore `aw.Document()` ti fornisce un file vuoto che puoi popolare con testo, immagini o forme.

```python
import aspose.words as aw

# Create a new blank document
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

L'oggetto `DocumentBuilder` semplifica l'inserimento di contenuti. Tiene traccia della posizione corrente del cursore, così puoi aggiungere elementi in sequenza senza gestire manualmente le sezioni.

## Passo 2: Inserire una forma rettangolare delle dimensioni desiderate

Una forma rettangolare funge da contenitore per elementi visivi. Puoi definire la sua larghezza e altezza in punti (1 pt ≈ 1/72 in).

```python
# Insert a rectangle shape that is 150 pt wide and 80 pt tall
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

A questo punto la forma non ha alcuno stile visivo, quindi appare come un semplice contorno. I passaggi successivi le daranno profondità e colore.

## Passo 3: Impostare la forma per fluire inline con il testo circostante

Quando una forma è **inline**, si comporta come un carattere in un paragrafo. Questo garantisce che il rettangolo rimanga dove ti aspetti nel layout del documento.

```python
# Make the shape inline so it follows the text flow
rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE
```

Se preferisci che la forma fluttui sopra il testo, potresti usare `WrapType.SQUARE` o `WrapType.TOP_BOTTOM`, ma per la maggior parte dei report una forma inline mantiene il layout prevedibile.

## Passo 4: Rendere l'ombra visibile e scegliere il suo colore

Un'ombra che non è visibile non offre alcun beneficio visivo. Il flag `visible` attiva l'effetto, e la proprietà `color` determina la sua tonalità. Usare il nero fornisce una profondità classica e sottile.

```python
# Enable the shadow and set its color to black
rectangle_shape.shadow.visible = True
rectangle_shape.shadow.color = aw.drawing.Color.black
```

Puoi sostituire `aw.drawing.Color.black` con qualsiasi altro colore, come `aw.drawing.Color.gray` o un valore RGB personalizzato (`aw.drawing.Color.from_argb(255, 128, 128, 128)`).

## Passo 5: Definire offset e sfocatura dell'ombra per darle profondità

L'offset controlla quanto l'ombra è spostata dalla forma, mentre il raggio di sfocatura ammorbidisce i bordi. Valori piccoli creano un'ombra nitida; valori più grandi producono un aspetto più morbido.

```python
# Horizontal and vertical offset of 5 pt each
rectangle_shape.shadow.offset_x = 5
rectangle_shape.shadow.offset_y = 5

# Blur radius of 3 pt for a gentle feather
rectangle_shape.shadow.blur = 3
```

Sperimenta con questi numeri per adeguarli alle linee guida del tuo design. Per un'ombra a caduta pesante potresti aumentare sia l'offset che la sfocatura.

## Passo 6: Scegliere uno stile di ombra esterna

Aspose.Words offre diversi stili di ombra, come `INNER`, `OUTER` e `PERSPECTIVE`. Lo stile **outer** posiziona l'ombra al di fuori del bordo della forma, ideale per un aspetto pulito e professionale.

```python
# Apply an outer shadow style
rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

Se ti serve un effetto più drammatico, prova `ShadowStyle.PERSPECTIVE`—aggiunge un'inclinazione tridimensionale.

## Passo 7: Salvare il documento con l'ombra della forma

Il salvataggio finalizza il file e scrive tutta la formattazione su disco. Scegli una directory per cui hai i permessi di scrittura e assegna al file un nome descrittivo.

```python
# Save the document to the desired location
output_path = "output/ShapeWithShadow.docx"
document.save(output_path)
print(f"Document saved to {output_path}")
```

Eseguendo lo script si ottiene un file Word che contiene un rettangolo con un'ombra visibile e colorata. Apri il file in Microsoft Word o LibreOffice per verificare il risultato.

## Esempio completo eseguibile

Di seguito lo script completo che incorpora tutti i passaggi discussi. Copia il codice in un file chiamato `create_shadowed_shape.py` ed eseguilo con `python create_shadowed_shape.py`.

```python
import aspose.words as aw
import os

def main():
    # Ensure the output directory exists
    output_dir = "output"
    os.makedirs(output_dir, exist_ok=True)

    # Step 1: Create a new blank document
    document = aw.Document()
    builder = aw.DocumentBuilder(document)

    # Step 2: Insert a rectangle shape of the desired size
    rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

    # Step 3: Set the shape to be inline with the text flow
    rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE

    # Step 4: Make the shadow visible and choose its color
    rectangle_shape.shadow.visible = True
    rectangle_shape.shadow.color = aw.drawing.Color.black

    # Step 5: Define the shadow's offset and blur to give it depth
    rectangle_shape.shadow.offset_x = 5   # horizontal offset in points
    rectangle_shape.shadow.offset_y = 5   # vertical offset in points
    rectangle_shape.shadow.blur = 3       # blur radius in points

    # Step 6: Choose an outer shadow style
    rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER

    # Step 7: Save the document with the shaped shadow
    output_path = os.path.join(output_dir, "ShapeWithShadow.docx")
    document.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    main()
```

**Output previsto**

Quando apri `ShapeWithShadow.docx`, vedrai un unico rettangolo centrato nella pagina. Il rettangolo è accompagnato da una sottile ombra nera spostata verso il basso‑destra, leggermente sfocata per creare profondità. L'ombra rispetta lo stile outer, quindi non interseca l'interno del rettangolo.

## Domande comuni e casi particolari

### Perché l'ombra a volte appare invisibile?

L'ombra viene renderizzata solo se `shadow.visible` è impostato su `True` **e** il `wrap_type` della forma lo consente. Una forma inline funziona in modo affidabile; le forme fluttuanti potrebbero richiedere aggiustamenti di layout aggiuntivi.

### Come posso cambiare il colore dell'ombra per corrispondere a una palette di brand?

Sostituisci `aw.drawing.Color.black` con un valore RGB personalizzato:

```python
rectangle_shape.shadow.color = aw.drawing.Color.from_argb(255, 0, 120, 215)  # corporate blue
```

### Cosa fare se devo far apparire la forma dietro al testo?

Imposta il tipo di avvolgimento su `WrapType.BEHIND` e regola `z_order_position` se necessario. Tieni presente che alcuni visualizzatori potrebbero renderizzare le forme dietro il testo in modo diverso.

### Posso applicare le stesse impostazioni di ombra a più forme?

Sì. Crea una funzione di supporto che configura l'ombra e chiamala per ogni forma che inserisci. Questo promuove il riutilizzo del codice e garantisce uno stile coerente.

```python
def apply_shadow(shape, color=aw.drawing.Color.black, offset=5, blur=3):
    shape.shadow.visible = True
    shape.shadow.color = color
    shape.shadow.offset_x = offset
    shape.shadow.offset_y = offset
    shape.shadow.blur = blur
    shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

## Conclusione

Ora sai **come creare un documento** che contiene una forma rettangolare con un'ombra personalizzata usando Aspose.Words per Python. Il tutorial ha coperto l'inserimento di un rettangolo, la trasformazione della forma in inline, l'abilitazione dell'ombra, l'impostazione del colore, offset, sfocatura e stile, e infine il salvataggio del file.

Da qui puoi esplorare argomenti correlati come **add shadow to shape** per altri tipi di forma, **set shadow color** in modo dinamico basato sui dati, o **how to add shadow** a immagini e caselle di testo. Sperimenta con diverse dimensioni, colori e stili di ombra per adeguarli alle linee guida del tuo brand o al sistema di design.

Pronto a automatizzare altri documenti Word? Prova ad aggiungere tabelle, intestazioni o contenuti dinamici—ogni passaggio si basa sugli stessi principi mostrati qui. Buon coding!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea forma rettangolare, aggiungi ombra e salva PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Crea documento Word vuoto con forma rettangolare ombreggiata – Guida passo‑passo](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Come gestire le variabili del documento con Aspose.Words in Python: guida completa](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}