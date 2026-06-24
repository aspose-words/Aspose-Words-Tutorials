---
category: general
date: 2026-06-24
description: Crea una forma rettangolare in Python con Aspose.Words, impara come aggiungere
  l'ombra alla forma, impostare l'angolo dell'ombra e salvare il documento come PDF
  in pochi minuti.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shape shadow
- set shadow angle
language: it
og_description: Crea una forma rettangolare in Python, aggiungi un'ombra alla forma,
  imposta l'angolo dell'ombra e salva il documento come PDF con Aspose.Words. Segui
  questa guida passo passo.
og_title: Crea forma rettangolare in Python – Tutorial completo di Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  headline: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  name: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: What if I need a different shape?
    text: Aspose.Words supports many `ShapeType` values (ellipse, star, callout, etc.).
      Simply replace `aw.drawing.ShapeType.RECTANGLE` with the desired enum, like
      `aw.drawing.ShapeType.ELLIPSE`.
  - name: Can I add multiple shadows?
    text: The API exposes only one `ShadowFormat` per shape, but you can simulate
      multiple shadows by duplicating the shape, offsetting each copy, and adjusting
      transparency.
  - name: How do I change the shadow color to match my brand?
    text: Just set `shadow.color` to any `aw.drawing.Color`. For a brand blue, use
      `aw.drawing.Color.from_argb(255, 0, 120, 215)`.
  - name: What about saving as DOCX instead of PDF?
    text: Replace `document.save(pdf_path)` with `document.save("output/shadowed_rectangle.docx")`.
      The shadow rendering is preserved across both formats.
  - name: Does the shadow work on older PDF viewers?
    text: Aspose.Words renders the shadow as a vector effect, which is widely supported.
      However, very old viewers might flatten the effect; testing on your target audience’s
      devices is always a good habit.
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: Crea forma rettangolare in Python – Guida completa ad Aspose.Words
url: /it/python/images-shapes/create-rectangle-shape-in-python-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea Forma Rettangolare in Python – Guida Completa ad Aspose.Words

Ti sei mai chiesto come **creare forma rettangolare** in un documento Word usando Python? Forse ti serve una casella di richiamo in grassetto, un indizio visivo per un diagramma, o semplicemente un rettangolo elegante per un report. Qualunque sia il caso, sei nel posto giusto. In questo tutorial percorreremo l’intero processo—dall’inserimento del rettangolo, all’aggiunta di un’ombra sottile, alla regolazione dell’angolo dell’ombra, e infine **salvare il documento come PDF** così da poterlo condividere con chiunque.

Useremo **Aspose.Words for Python via .NET**, una libreria potente che permette di manipolare file Word senza mai aprire Word stesso. Alla fine di questa guida sarai in grado di rispondere alla domanda *“come aggiungere ombra alla forma”* con sicurezza, e avrai a disposizione uno script pronto all’uso da inserire in qualsiasi progetto.

---

## Cosa Ti Serve

Prima di iniziare, assicurati di avere quanto segue:

- **Python 3.8+** installato sulla tua macchina.  
- **Aspose.Words for Python via .NET** (pacchetto `aspose-words`). Installalo con:

  ```bash
  pip install aspose-words
  ```

- Una cartella scrivibile dove verrà salvato il PDF generato.  
- (Opzionale) Un IDE o un editor di testo—VS Code funziona benissimo.

Tutto qui. Nessun DLL aggiuntivo, nessuna installazione di Office, solo un singolo pacchetto pip.

---

## Passo 1: Configura il Documento e il Builder

La prima cosa da fare è **creare forma rettangolare**‑friendly objects: un `Document` e un `DocumentBuilder`. Pensa al builder come alla tua penna; disegna tutto per te.

```python
import aspose.words as aw

# Initialize a new blank document
document = aw.Document()

# DocumentBuilder gives us a convenient way to add content
builder = aw.DocumentBuilder(document)
```

> **Perché è importante:** L’oggetto `Document` rappresenta l’intero file .docx, mentre il `DocumentBuilder` fornisce metodi come `insert_shape` che rendono il disegno delle forme un gioco da ragazzi.

---

## Passo 2: Inserisci la Forma Rettangolare

Ora che abbiamo un builder, possiamo finalmente **creare forma rettangolare**. Il metodo `insert_shape` richiede tre argomenti: il tipo di forma, la larghezza e l’altezza. Useremo una larghezza di 200 pt e un’altezza di 100 pt per una buona proporzione.

```python
# Insert a rectangle with a width of 200 points and a height of 100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

A questo punto hai **creato forma rettangolare** con successo nel tuo documento. Se apri il DOCX generato (lo faremo più tardi), vedrai un semplice rettangolo posizionato dove era il cursore.

---

## Passo 3: Accedi all’Oggetto di Formattazione dell’Ombra

Per **aggiungere ombra alla forma**, dobbiamo prima ottenere la formattazione dell’ombra della forma. Ogni forma in Aspose.Words ha una proprietà `shadow_format` che espone tutte le impostazioni relative all’ombra.

```python
# Grab the shadow formatting object for later tweaks
shadow = rectangle.shadow_format
```

Avere il riferimento `shadow` ci permette di attivare o disattivare la visibilità, la sfocatura, la distanza, l’angolo, il colore e la trasparenza—tutto in poche righe di codice.

---

## Passo 4: Abilita l’Ombra e Configura il Suo Aspetto

Qui avviene la magia. **Aggiungeremo ombra alla forma**, la renderemo leggermente sfocata, la sposteremo un po’, imposteremo la direzione (la parte **impostare l'angolo dell'ombra**), e le daremo una tonalità nera semi‑trasparente.

```python
# Turn the shadow on
shadow.visible = True

# Soften the edges – a blur radius of 8 points looks natural
shadow.blur_radius = 8.0

# Push the shadow away from the rectangle by 5 points
shadow.distance = 5.0

# Set the direction of the light source – 45 degrees creates a diagonal drop
shadow.angle = 45

# Choose a color; black works well for most documents
shadow.color = aw.drawing.Color.black

# Make the shadow 30 % transparent for a subtle effect
shadow.transparency = 0.3
```

> **Consiglio professionale:** Se ti serve un effetto più drammatico, aumenta `blur_radius` o diminuisci `transparency`. Al contrario, un’ombra netta e completamente opaca si ottiene con `blur_radius = 0` e `transparency = 0`.

---

## Passo 5: Salva il Documento come PDF

Abbiamo **creato forma rettangolare**, abbiamo **aggiunto ombra alla forma**, e ora **salveremo il documento come PDF** così il risultato sarà identico su qualsiasi dispositivo. Aspose.Words lo rende un’unica riga di codice.

```python
# Define where you want the PDF to land
output_path = "output/shadowed_rectangle.pdf"

# Save the whole document (including the rectangle with its shadow) as PDF
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Eseguendo lo script verrà generato `shadowed_rectangle.pdf` nella cartella `output`. Aprilo con qualsiasi visualizzatore PDF e vedrai un rettangolo pulito con un’ombra morbida a 45°—esattamente come l’abbiamo configurata.

---

## Esempio Completo Funzionante

Di seguito trovi lo script completo, pronto all’esecuzione, che combina tutti i passaggi descritti sopra. Copialo in un file chiamato `create_rectangle_with_shadow.py` ed esegui `python create_rectangle_with_shadow.py`.

```python
import aspose.words as aw
import os

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Initialize document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert the rectangle shape (200 pt × 100 pt)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Access shadow formatting
shadow = rectangle.shadow_format

# 4️⃣ Configure shadow – visible, blurred, offset, angled, colored, semi‑transparent
shadow.visible = True
shadow.blur_radius = 8.0          # softer edges
shadow.distance = 5.0            # how far the shadow sits from the shape
shadow.angle = 45                # direction in degrees – this is the **set shadow angle** step
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.3        # 30 % transparent

# 5️⃣ Save the document as PDF
pdf_path = os.path.join(output_dir, "shadowed_rectangle.pdf")
document.save(pdf_path)

print(f"✅ PDF created at: {pdf_path}")
```

**Output previsto:** Un file PDF che mostra un singolo rettangolo con una leggera ombra diagonale. Nessuna pagina extra, nessun artefatto nascosto—solo la forma che abbiamo creato.

---

## Domande Frequenti & Casi Limite

### E se avessi bisogno di una forma diversa?

Aspose.Words supporta molti valori di `ShapeType` (ellisse, stella, callout, ecc.). Basta sostituire `aw.drawing.ShapeType.RECTANGLE` con l’enum desiderato, ad esempio `aw.drawing.ShapeType.ELLIPSE`.

### Posso aggiungere più ombre?

L’API espone un solo `ShadowFormat` per forma, ma puoi simulare più ombre duplicando la forma, spostando ogni copia e regolando la trasparenza.

### Come cambio il colore dell’ombra per allinearlo al mio brand?

Imposta semplicemente `shadow.color` a qualsiasi `aw.drawing.Color`. Per un blu brand, usa `aw.drawing.Color.from_argb(255, 0, 120, 215)`.

### E se volessi salvare come DOCX invece di PDF?

Sostituisci `document.save(pdf_path)` con `document.save("output/shadowed_rectangle.docx")`. La resa dell’ombra viene preservata in entrambi i formati.

### L’ombra funziona su visualizzatori PDF più vecchi?

Aspose.Words rende l’ombra come effetto vettoriale, ampiamente supportato. Tuttavia, visualizzatori molto datati potrebbero appiattire l’effetto; è sempre buona pratica testare sui dispositivi del tuo pubblico.

---

## Consigli per Rifinire il Tuo PDF

- **Aggiungi un bordo:** `rectangle.line_format.width = 1.5` e imposta un colore per un contorno nitido.  
- **Centra il rettangolo:** Usa `builder.move_to_document_start()` prima di inserire, poi `builder.paragraph_format.alignment = aw.ParagraphAlignment.CENTER`.  
- **Combina con testo:** Inserisci un `TextFragment` dopo il rettangolo per etichettarlo, ad esempio `"Sezione Importante"`.

Questi piccoli aggiustamenti possono trasformare un semplice rettangolo in una casella di richiamo raffinata, dall’aspetto professionale in report, proposte o e‑book.

---

## Conclusione

Ora disponi di una ricetta solida, end‑to‑end, per **creare forma rettangolare** in Python, **aggiungere ombra alla forma**, **impostare l'angolo dell'ombra** e **salvare il documento come PDF** usando Aspose.Words. I passaggi sono chiari, il codice è completamente autonomo, e hai visto perché ogni riga è importante—dall’inizializzazione del documento alla rifinitura del PDF finale.

Il prossimo passo potrebbe essere **come aggiungere ombra alla forma** a disegni più complessi, sperimentare riempimenti a gradiente, o generare tabelle all’interno delle tue forme. La libreria supporta anche il collegamento delle forme a segnalibri, utile per PDF interattivi.

Hai provato una variante? Condividila nei commenti, o poni le tue domande rimaste in sospeso. Buon coding, e divertiti ad aggiungere quella profondità extra ai tuoi documenti! 

![Forma rettangolare con ombra – esempio di creare forma rettangolare in Python](/images/rectangle-shadow.png)


## Cosa Dovresti Imparare Dopo?


I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell’API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea Documento Word Java – Aggiungi Forma Rettangolare con Effetto Ombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Tutorial Ombra Forma Aspose.Words – Aggiungi un’Ombra a una Forma Word in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Crea forma rettangolare in Word usando C# – Guida Passo‑per‑Passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}