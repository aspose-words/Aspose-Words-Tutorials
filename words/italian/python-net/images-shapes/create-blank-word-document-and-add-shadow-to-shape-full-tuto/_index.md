---
category: general
date: 2026-07-20
description: Crea un documento Word vuoto con Aspose.Words e aggiungi un'ombra alla
  forma. Scopri come modificare l'opacità e la trasparenza dell'ombra in pochi passaggi.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add shadow to shape
- add shadow effect
- change shadow transparency
- change shadow opacity
language: it
lastmod: 2026-07-20
og_description: Crea un documento Word vuoto utilizzando Aspose.Words e aggiungi un
  effetto ombra a una forma. Modifica l'opacità e la trasparenza dell'ombra con esempi
  di codice chiari.
og_image_alt: Screenshot showing a Word document with a shape that has a semi‑transparent
  shadow
og_title: Crea un documento Word vuoto e aggiungi l'ombra alla forma – Guida passo
  passo
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Create blank Word document with Aspose.Words and add shadow to shape.
    Learn how to change shadow opacity and transparency in just a few steps.
  headline: Create Blank Word Document and Add Shadow to Shape – Full Tutorial
  type: TechArticle
- description: Create blank Word document with Aspose.Words and add shadow to shape.
    Learn how to change shadow opacity and transparency in just a few steps.
  name: Create Blank Word Document and Add Shadow to Shape – Full Tutorial
  steps:
  - name: Expected Output
    text: When you open **ShadowedShape.docx**, you should see a rectangle with a
      gray, semi‑transparent shadow that has a gentle blur. The shadow will be offset
      slightly down and to the right, giving the illusion that the shape is lifted
      off the page.
  - name: What if the document already contains multiple shapes?
    text: 'The current script grabs the *first* shape (`index 0`). To target a specific
      shape, change the index or iterate over all shapes:'
  - name: Can I change the shadow color?
    text: 'Absolutely. Shadow color is another property:'
  - name: How do I make the shadow offset differently?
    text: 'Adjust `distance_x` and `distance_y`:'
  - name: Does this work with older Word versions?
    text: Aspose.Words writes the modern OOXML format (`.docx`). Word 2007+ can open
      it without issues. For legacy `.doc` files, call `doc.save("file.doc", aw.SaveFormat.DOC)`—the
      shadow properties will still be preserved.
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
- Word Shapes
title: Crea un documento Word vuoto e aggiungi l'ombra alla forma – Tutorial completo
url: /it/python/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-tuto/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea un documento Word vuoto e aggiungi ombra alla forma – Tutorial completo

Hai mai avuto bisogno di **creare un documento Word vuoto** e poi far risaltare una forma con un'ombra sottile? Non sei l'unico. In molti report, volantini o dashboard interne, un po' di profondità può trasformare un rettangolo piatto in un'indicazione visiva che attira l'attenzione.  

In questa guida vedremo come creare un nuovo file Word con Aspose.Words per Python, estrarre la prima forma e poi **aggiungere ombra alla forma** regolando la sua opacità e sfocatura. Alla fine avrai un documento dall'aspetto curato—senza necessità di interventi manuali.

> **Cosa otterrai** – uno script completo e eseguibile, spiegazioni del *perché* di ogni riga, e consigli per gestire documenti che non contengono già una forma.

## Prerequisiti

- Python 3.8+ installato (qualsiasi versione recente va bene)
- Aspose.Words per Python tramite `pip install aspose-words`
- Familiarità di base con Python e il concetto di “forma” in Word (pensa a casella di testo, immagine o auto‑forma)

Non sono necessarie altre librerie; il codice è autonomo.

## Passo 1: Crea un documento Word vuoto con Aspose.Words

Prima di tutto, abbiamo bisogno di una tela pulita. Aspose.Words rende questo banale—basta istanziare un oggetto `Document`.

```python
import aspose.words as aw

# Step 1: Create a new blank document
doc = aw.Document()
print("✅ Blank Word document created.")
```

*Perché è importante*: la classe `Document` è il punto di ingresso per ogni operazione. Iniziare con un documento nuovo garantisce che non ci siano sorprese di formattazione nascoste in seguito.

## Passo 2: Inserisci una forma di esempio (così abbiamo qualcosa da ombreggiare)

Se esegui lo script su un file vuoto incontrerai un problema quando cercherai di recuperare una forma—non ce n'è semplicemente una. Aggiungiamo un rettangolo semplice così i passaggi successivi avranno un obiettivo.

```python
# Step 2: Add a rectangle shape to the first page
builder = aw.DocumentBuilder(doc)
builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
print("🔲 Rectangle shape inserted.")
```

> **Consiglio professionale**: Regola i valori di larghezza/altezza (200, 100) per adattarli alle tue esigenze di design. Le forme più grandi mostrano le ombre più chiaramente.

## Passo 3: Recupera la prima forma nel documento

Ora che abbiamo una forma, possiamo estrarla in sicurezza. Il metodo `get_child` percorre l'albero dei nodi e restituisce il primo nodo del tipo richiesto.

```python
# Step 3: Retrieve the first shape (index 0) – true = deep search
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

if shape is None:
    raise ValueError("No shape found in the document.")
print(f"🕵️ Retrieved shape of type: {shape.shape_type}")
```

*Perché controlliamo `None`*: in scenari reali il documento potrebbe essere generato altrove, e una forma mancante causerebbe altrimenti un criptico `AttributeError`. Lanciare un'eccezione chiara fa risparmiare tempo di debug.

## Passo 4: Aggiungi effetto ombra – Modifica l'opacità dell'ombra

Un'ombra non è solo un ornamento visivo; può trasmettere gerarchia. Rendiamola semi‑trasparente impostando l'opacità al 75 %.

```python
# Step 4: Set shadow opacity (0.0 = fully transparent, 1.0 = fully opaque)
shape.shadow.opacity = 0.75
print(f"🌫️ Shadow opacity set to {shape.shadow.opacity}")
```

**Comprendere l'opacità**: il valore è un float compreso tra 0 e 1. Numeri più bassi fanno svanire l'ombra nello sfondo, numeri più alti la fanno risaltare. Per la maggior parte dei documenti in stile UI, 0.5–0.8 appare naturale.

## Passo 5: Definisci la sfocatura dell'ombra – Modifica la trasparenza dell'ombra

Il raggio di sfocatura controlla quanto morbido appare il bordo dell'ombra. Un raggio più grande produce una dissolvenza più delicata, imitazione della diffusione della luce naturale.

```python
# Step 5: Define blur radius (in points) for a softer edge
shape.shadow.blur_radius = 8.0
print(f"🔍 Blur radius set to {shape.shadow.blur_radius} points")
```

*Perché la sfocatura è importante*: un'ombra a bordo netto può apparire di scarsa qualità, mentre una sfocatura sottile aggiunge profondità senza sovraccaricare il contenuto.

## Passo 6: Salva il documento e verifica il risultato

Infine, scriviamo il documento su disco. Apri il `.docx` risultante in Word per vedere il rettangolo con la sua nuova ombra.

```python
output_path = "ShadowedShape.docx"
doc.save(output_path)
print(f"💾 Document saved as '{output_path}'. Open it in Word to see the effect.")
```

### Output previsto

Quando apri **ShadowedShape.docx**, dovresti vedere un rettangolo con un'ombra grigia, semi‑trasparente, che presenta una leggera sfocatura. L'ombra sarà spostata leggermente verso il basso e a destra, creando l'illusione che la forma sia sollevata dalla pagina.

## Casi limite e domande comuni

### E se il documento contiene già più forme?

Lo script attuale prende la *prima* forma (`indice 0`). Per mirare a una forma specifica, cambia l'indice o itera su tutte le forme:

```python
for i in range(doc.get_child_nodes(aw.NodeType.SHAPE, True).count):
    shp = doc.get_child(aw.NodeType.SHAPE, i, True)
    # Apply shadow settings to each shape
    shp.shadow.opacity = 0.6
    shp.shadow.blur_radius = 5.0
```

### Posso cambiare il colore dell'ombra?

Assolutamente. Il colore dell'ombra è un'altra proprietà:

```python
shape.shadow.color = aw.drawing.Color.black
```

### Come posso modificare l'offset dell'ombra?

Regola `distance_x` e `distance_y`:

```python
shape.shadow.distance_x = 5   # shift right
shape.shadow.distance_y = 5   # shift down
```

### Funziona con versioni più vecchie di Word?

Aspose.Words scrive il moderno formato OOXML (`.docx`). Word 2007+ può aprirlo senza problemi. Per file legacy `.doc`, chiama `doc.save("file.doc", aw.SaveFormat.DOC)`—le proprietà dell'ombra saranno comunque preservate.

## Riepilogo script completo

Mettendo tutto insieme, ecco l'esempio completo, pronto per l'esecuzione:

```python
import aspose.words as aw

# Create a new blank document
doc = aw.Document()
print("✅ Blank Word document created.")

# Insert a rectangle shape (so we have something to shadow)
builder = aw.DocumentBuilder(doc)
builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
print("🔲 Rectangle shape inserted.")

# Retrieve the first shape in the document
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
if shape is None:
    raise ValueError("No shape found in the document.")
print(f"🕵️ Retrieved shape of type: {shape.shape_type}")

# Add shadow effect – change opacity
shape.shadow.opacity = 0.75
print(f"🌫️ Shadow opacity set to {shape.shadow.opacity}")

# Change shadow transparency – define blur radius
shape.shadow.blur_radius = 8.0
print(f"🔍 Blur radius set to {shape.shadow.blur_radius} points")

# Optional: tweak color and offset
shape.shadow.color = aw.drawing.Color.gray
shape.shadow.distance_x = 4
shape.shadow.distance_y = 4

# Save the document
output_path = "ShadowedShape.docx"
doc.save(output_path)
print(f"💾 Document saved as '{output_path}'. Open it in Word to see the effect.")
```

Esegui questo script, apri il file generato, e vedrai la forma avvolta da un'ombra elegante—esattamente ciò di cui ha bisogno un report curato.

## Conclusione

Ora sai **come creare un documento Word vuoto** con Aspose.Words, inserire una forma e **aggiungere ombra alla forma** padroneggiando *modifica dell'opacità dell'ombra* e *modifica della trasparenza dell'ombra*. I passaggi sono semplici, ma il risultato visivo è notevole.  

Successivamente, potresti esplorare **l'aggiunta di effetto ombra** alle immagini, sperimentare con diversi valori di `blur_radius`, o combinare più forme in un'unica grafica composita. Per approfondimenti, consulta la documentazione di Aspose su [Shape Formatting](https://docs.aspose.com/words/python-net/shape/) e la più ampia guida [Document Automation](https://docs.aspose.com/words/python-net/).

Hai provato una variante? Lascia un commento qui sotto—condividere modifiche reali rende la community più forte. Buon coding!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea un documento Word vuoto con forma rettangolare ombreggiata – Guida passo‑passo](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Tutorial ombra forma Aspose.Words – Aggiungi un'ombra a una forma Word in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Crea forma rettangolare in Word con Aspose.Words – Guida passo‑passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}