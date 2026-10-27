---
category: general
date: 2026-06-27
description: Scopri come inserire una forma rettangolare in Python usando Aspose.Words,
  cambiare il colore dell'ombra, aggiungere l'ombra esterna e applicare l'effetto
  ombra alla forma—tutto in un unico tutorial.
draft: false
keywords:
- how to insert rectangle shape
- how to change shadow color
- how to add outer shadow
- apply shadow effect to shape
language: it
og_description: Impara a inserire una forma rettangolare in Python, a cambiare il
  colore dell'ombra, ad aggiungere un'ombra esterna e ad applicare un effetto ombra
  alla forma con Aspose.Words.
og_title: Come inserire una forma rettangolare in Python – Tutorial Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  headline: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  name: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: Pro tip
    text: If you need the rectangle positioned at a specific location, use `builder.move_to`
      before inserting, or adjust `rectangle.left` and `rectangle.top` after creation.
  - name: Edge case
    text: If you forget to set `shadow.opacity`, the default is fully opaque, which
      can make the shadow look like a solid shape. Always pair a color change with
      an appropriate opacity level.
  - name: Common pitfalls
    text: '- **Missing directory:** `doc.save` will raise an error if the folder doesn’t
      exist. Create it first or use `os.makedirs`. - **Version mismatch:** The shadow
      API requires Aspose.Words 22.9+; older versions silently ignore shadow settings.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
title: Come inserire una forma rettangolare in Python – Guida completa ad Aspose.Words
url: /it/python/images-shapes/how-to-insert-rectangle-shape-in-python-complete-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come inserire una forma rettangolare in Python – Guida completa ad Aspose.Words

Ti sei mai chiesto **come inserire una forma rettangolare** in un documento Word usando Python? Non sei l'unico—molti sviluppatori incontrano questo ostacolo quando automatizzano report o creano modelli. La buona notizia è che Aspose.Words lo rende un gioco da ragazzi, e in questo tutorial percorreremo l'intero processo, dal disegnare il rettangolo al dargli un elegante ombra esterna.  

Tratteremo anche **come cambiare il colore dell'ombra**, **come aggiungere un'ombra esterna**, e l'ultimo passaggio di **applicare l'effetto ombra alla forma**. Alla fine, avrai un rettangolo completamente stilizzato che potrai inserire in qualsiasi file .docx in modo programmatico.

## Prerequisiti

- Python 3.8+ installato sulla tua macchina  
- Aspose.Words per Python tramite `pip install aspose-words`  
- Familiarità di base con lo scripting Python (non è necessario una conoscenza approfondita dell'API di Word)  

Se hai già tutto questo, ottimo—tuffiamoci. Altrimenti, prima scarica la libreria; il resto della guida presume che l'importazione funzioni senza problemi.

## Come inserire una forma rettangolare con Aspose.Words per Python

Il primo passo è esattamente quello che promette la parola chiave principale: **come inserire una forma rettangolare**. Creeremo un nuovo documento, avvieremo un `DocumentBuilder` e inseriremo un rettangolo nella pagina.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a fresh document and a builder to add content
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Insert a rectangle shape of 200x100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# Optional: give the rectangle a light fill so the shadow is visible
rectangle.fill_color = aw.drawing.Color.light_blue
```

> **Perché è importante:** La chiamata `insert_shape` è il fulcro di *come inserire una forma rettangolare*. Restituisce un oggetto `Shape` che puoi manipolare in seguito—dimensione, posizione, riempimento, bordi, come preferisci. Nota che impostiamo anche un `fill_color`; senza di esso l'ombra potrebbe confondersi con una pagina bianca, rendendola difficile da vedere.

### Consiglio professionale
Se hai bisogno che il rettangolo sia posizionato in un punto specifico, usa `builder.move_to` prima dell'inserimento, oppure regola `rectangle.left` e `rectangle.top` dopo la creazione.

## Cambiare il colore dell'ombra di una forma

Ora che il rettangolo è presente nel documento, rispondiamo a **come cambiare il colore dell'ombra**. Aspose.Words espone un oggetto `ShadowEffect` dove puoi impostare la proprietà `color` a qualsiasi valore RGB.

```python
# Create a shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # we’ll also cover outer shadow later
shadow.blur_radius = 8.0                  # smooth edges
shadow.distance = 6.0                     # how far the shadow sits from the shape
shadow.direction = 45                     # angle in degrees
shadow.opacity = 0.6                      # semi‑transparent

# Change the shadow color to a deep gray instead of black
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)

# Apply the shadow to our rectangle
rectangle.shadow = shadow
```

> **Perché potresti volerne uno:** Un'ombra nera scura può risultare troppo dura, soprattutto su documenti di colore chiaro. Regolare il colore ti permette di abbinare il branding aziendale o semplicemente ottenere un effetto visivo più morbido.

### Caso limite
Se dimentichi di impostare `shadow.opacity`, il valore predefinito è completamente opaco, il che può far sembrare l'ombra una forma solida. Associa sempre un cambiamento di colore a un livello di opacità appropriato.

## Aggiungere un effetto ombra esterna

La prossima domanda che molti pongono è **come aggiungere un'ombra esterna**. Il flag `ShadowStyle.OUTER` indica ad Aspose.Words di renderizzare l'ombra al di fuori del contorno della forma anziché all'interno.

Il frammento di codice sopra utilizza già `ShadowStyle.OUTER`, ma isoliamo questa impostazione per chiarezza:

```python
# Ensure the shadow style is outer
shadow.style = ShadowStyle.OUTER
```

Se passi a `ShadowStyle.INNER`, l'ombra apparirà *all'interno* del rettangolo, utile per effetti di embossing. Per la maggior parte degli scenari di design di documenti, lo stile esterno offre un aspetto naturale di ombra cadente.

## Applicare l'effetto ombra alla tua forma

Abbiamo già **applicato l'effetto ombra alla forma** assegnando `rectangle.shadow = shadow`. Mettiamo tutto insieme e salviamo il documento, confermando che l'effetto persiste.

```python
# Save the document – choose a folder you have write access to
output_path = "output/RectangleWithShadow.docx"
doc.save(output_path)

print(f"Document saved to {output_path}. Open it to see the rectangle with its outer shadow.")
```

Quando apri `RectangleWithShadow.docx` in Microsoft Word, dovresti vedere un rettangolo azzurro chiaro con una sottile ombra grigia esterna proiettata a un angolo di 45°. L'ombra sarà leggermente sfocata e spostata, esattamente come l'abbiamo configurata.

### Trappole comuni
- **Directory mancante:** `doc.save` genererà un errore se la cartella non esiste. Creala prima o usa `os.makedirs`.
- **Mancata corrispondenza di versione:** L'API ombra richiede Aspose.Words 22.9+; versioni più vecchie ignorano silenziosamente le impostazioni dell'ombra.

## Esempio completo funzionante

Di seguito trovi lo script completo, pronto per l'esecuzione, che combina tutti i passaggi. Copialo in un file chiamato `rectangle_shadow.py` ed eseguilo con `python rectangle_shadow.py`.

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Create a new document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2️⃣ Insert the rectangle shape (how to insert rectangle shape)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle.fill_color = aw.drawing.Color.light_blue   # make the shape visible

# 3️⃣ Define the shadow (how to change shadow color, how to add outer shadow)
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # outer shadow
shadow.blur_radius = 8.0
shadow.distance = 6.0
shadow.direction = 45
shadow.opacity = 0.6
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)  # custom gray

# 4️⃣ Apply the shadow (apply shadow effect to shape)
rectangle.shadow = shadow

# 5️⃣ Save the file
output_path = os.path.join(output_dir, "RectangleWithShadow.docx")
doc.save(output_path)

print(f"✅ Document generated: {output_path}")
```

**Output previsto:** Un documento Word (`RectangleWithShadow.docx`) contenente un singolo rettangolo con un'ombra grigia esterna. Aprilo in Word per verificare l'effetto visivo.

## Domande frequenti

| Domanda | Risposta |
|----------|--------|
| *Posso usare un tipo di forma diverso?* | Assolutamente—sostituisci `ShapeType.RECTANGLE` con `ShapeType.OVAL`, `ShapeType.TRIANGLE`, ecc., e la stessa logica dell'ombra si applica. |
| *E se ho bisogno di un bordo più spesso?* | Imposta `rectangle.line_width = 2.0` (punti) prima di applicare l'ombra. |
| *È possibile animare l'ombra?* | Non direttamente con Aspose.Words; dovresti esportare in HTML/CSS per l'animazione. |
| *Funziona su macOS?* | Sì—Aspose.Words è indipendente dalla piattaforma purché Python sia in esecuzione. |

## Conclusione

Abbiamo illustrato **come inserire una forma rettangolare**, dimostrato **come cambiare il colore dell'ombra**, spiegato **come aggiungere un'ombra esterna**, e infine mostrato come **applicare l'effetto ombra alla forma** usando Aspose.Words per Python. Lo script completo è pronto per essere inserito in qualsiasi pipeline di automazione, fornendoti un rettangolo dall'aspetto professionale con un'ombra rifinita in pochi secondi.

Pronto per il passo successivo? Prova a cambiare il colore di riempimento, sperimentare con diversi angoli di `direction`, o aggiungere più forme nella stessa pagina. Puoi anche esplorare l'API di formattazione del testo di Aspose.Words per combinare ombre con testo formattato—perfetto per report accattivanti.

Se hai trovato utile questo tutorial, metti un like, condividilo con i colleghi, o lascia un commento con le tue varianti. Buona programmazione!

![Diagramma che mostra come inserire una forma rettangolare con un'ombra esterna applicata in un documento Word](/images/rectangle-shadow.png)


## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea documento Word Java – Aggiungi forma rettangolare con effetto ombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Tutorial ombra forma Aspose.Words – Aggiungi un'ombra a una forma Word in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Crea forma rettangolare in Word usando C# – Guida passo‑passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}