---
category: general
date: 2026-06-21
description: Crea una forma rettangolare in Python usando Aspose.Words. Scopri come
  aggiungere l'ombra alla forma, impostare il colore di riempimento della forma e
  salvare il documento come PDF in pochi minuti.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- set shape fill color
language: it
og_description: Crea una forma rettangolare in Python con Aspose.Words. Questa guida
  mostra come aggiungere l'ombra alla forma, impostare il colore di riempimento della
  forma e salvare il documento come PDF.
og_title: Crea una forma rettangolare in Python – tutorial Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-21'
  description: Create rectangle shape in Python using Aspose.Words. Learn how to add
    shadow to shape, set shape fill color, and save document as PDF in minutes.
  headline: Create rectangle shape in Python – Aspose.Words tutorial
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF generation
title: Crea forma rettangolare in Python – tutorial Aspose.Words
url: /it/python/images-shapes/create-rectangle-shape-in-python-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea forma rettangolare in Python – tutorial Aspose.Words

Ti sei mai chiesto **come creare una forma rettangolare** in un documento Word mentre programmi in Python? Non sei l'unico. Molti sviluppatori si trovano in difficoltà quando hanno bisogno di un elemento visivo rapido—come una casella colorata con un'ombra sottile—e poi esportano il tutto in PDF.  

In questa guida percorreremo un esempio completo e eseguibile che **crea una forma rettangolare**, **imposta il colore di riempimento della forma**, **aggiunge un'ombra alla forma** e infine **salva il documento come PDF**. Nessun riferimento vago, solo codice concreto che puoi copiare‑incollare ed eseguire oggi.

## Cosa ti servirà

Prima di iniziare, assicurati di avere quanto segue sulla tua macchina:

- Python 3.8 o successivo (la sintassi che usiamo funziona su qualsiasi versione recente).
- Una licenza attiva di Aspose.Words per Python o una prova gratuita (la libreria è pure‑Python, non richiede interop COM).
- Un editor di testo o un IDE con cui ti trovi a tuo agio—VS Code funziona benissimo, ma va bene qualsiasi altro.

Tutto qui. Nessun framework pesante, nessuna dipendenza a livello di OS. Iniziamo.

## Passo 1: Installa Aspose.Words per Python

Prima di tutto. Se non l’hai già fatto, scarica il pacchetto da PyPI:

```bash
pip install aspose-words
```

Perché questo passo è importante: Aspose.Words fornisce le classi `Document` e `DocumentBuilder` su cui faremo affidamento. Senza la libreria, nessuna delle chiamate successive—come `insert_shape`—esiste, quindi lo script crasherebbe prima ancora di disegnare una linea.

> **Suggerimento:** Mantieni pulito il tuo ambiente virtuale. Esegui `python -m venv .venv && source .venv/bin/activate` prima di installare, così la libreria rimane isolata dai pacchetti di sistema.

## Passo 2: Crea un nuovo documento e un DocumentBuilder

Ora creiamo effettivamente **la forma rettangolare** – ma prima ci serve una tela vuota.

```python
import aspose.words as aw

# Initialize a new, empty Word document
doc = aw.Document()
# DocumentBuilder lets us add content programmatically
builder = aw.DocumentBuilder(doc)
```

L’oggetto `Document` rappresenta l’intero file, mentre `DocumentBuilder` è un comodo helper che sa dove si trova il cursore e può inserire elementi in quel punto. Pensa al builder come a una penna che scrive sulla pagina.

## Passo 3: Inserisci la forma rettangolare

Qui avviene l’azione principale. **Creeremo una forma rettangolare** con larghezza e altezza fisse, poi la posizioneremo sulla pagina.

```python
# Insert a rectangle 200 points wide and 100 points tall
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

Perché un rettangolo? È la forma più semplice che ci permette comunque di mostrare colori di riempimento e ombre. Se in seguito ti servisse un cerchio o una stella, basta sostituire `ShapeType.RECTANGLE` con un altro valore enum.

## Passo 4: Imposta il colore di riempimento della forma

Una casella bianca non è molto eccitante, quindi **impostiamo il colore di riempimento della forma** su qualcosa di delicato—un azzurro chiaro funziona bene per i report.

```python
# Apply a light‑blue background to the rectangle
rectangle.fill_color = aw.Color.light_blue
```

Puoi usare qualsiasi membro predefinito di `aw.Color` (`red`, `green`, `dark_gray`, ecc.) o passare una tupla RGB (`aw.Color.from_argb(255, 30, 144, 255)`). Il colore di riempimento è ciò che l’utente vede prima che venga applicata un’ombra o un bordo.

## Passo 5: Aggiungi un’ombra alla forma

Ora il tocco finale visivo: **aggiungi un’ombra alla forma**. Le ombre danno profondità e fanno risaltare il rettangolo sulla pagina.

```python
# Grab the shadow format object
shadow = rectangle.shadow_format

# Turn the shadow on
shadow.visible = True
# Choose a dark gray tone for realism
shadow.color = aw.Color.dark_gray
# Blur radius controls softness (5 points is a nice middle ground)
shadow.blur = 5
# Horizontal and vertical offsets shift the shadow relative to the shape
shadow.offset_x = 3
shadow.offset_y = 3
# Slight transparency makes the shadow feel natural
shadow.transparency = 0.2
# Use an outer shadow – you could also try INSET for a different effect
shadow.type = aw.drawing.ShadowType.OUTER
```

**Come si aggiunge l’ombra**? Il codice sopra lo fa esattamente, ma analizziamo perché ogni proprietà è importante:

- `visible` – attiva/disattiva l’effetto.
- `color` – definisce la tonalità; un grigio scuro imita l’illuminazione naturale.
- `blur` – valori più alti producono un bordo più morbido.
- `offset_x` / `offset_y` – spostano l’ombra rispetto alla forma; modifica questi valori per simulare diverse angolazioni di luce.
- `transparency` – 0 è opaco, 1 è invisibile; 0.2 dà un’impressione sottile.
- `type` – `OUTER` proietta l’ombra all’esterno della forma, mentre `INNER` la inserirebbe all’interno.

Se ti serve un’ombra drammatica, aumenta `blur` a 10‑15 e alza `offset_x`/`offset_y` a 6‑8.

## Passo 6: Salva il documento come PDF

Tutto questo lavoro è inutile se non possiamo **salvare il documento come PDF** e condividerlo. Aspose.Words lo rende un’unica riga di codice:

```python
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Perché PDF? I PDF mantengono il layout su tutte le piattaforme, rendendoli ideali per report, fatture o qualsiasi materiale stampabile. Il metodo `save` rileva automaticamente l’estensione del file e sceglie il formato corretto—basta assicurarsi che il percorso termini con `.pdf`.

### Risultato atteso

Apri il file `ShapeWithShadow.pdf` generato e dovresti vedere un rettangolo azzurro chiaro centrato vicino alla parte superiore della prima pagina, con un’ombra grigia scura morbida spostata leggermente verso destra e in basso. I bordi della forma sono nitidi, l’ombra è sottile, e la dimensione del file è tipicamente inferiore a 100 KB.

## Bonus: Regolare le ombre – Risposte a “come aggiungere ombra”

Potresti chiederti, *“Posso cambiare la direzione dell’ombra senza spostare la forma?”* Assolutamente. La posizione dell’ombra è indipendente dalle coordinate della forma; basta modificare `offset_x` e `offset_y`. Valori positivi spostano l’ombra a destra/giù, valori negativi a sinistra/su. Per una fonte di luce in alto a sinistra, usa `offset_x = -3` e `offset_y = -3`.

Un’altra domanda frequente: *“E se avessi bisogno di più ombre sulla stessa forma?”* Aspose.Words supporta una sola ombra per forma. Se ti servono effetti a strati, crea una forma duplicata, spostala leggermente e applica un’ombra diversa a ciascuna. È un piccolo trucco, ma funziona.

## Script completo – Pronto da eseguire

Di seguito trovi lo script completo e autonomo. Copialo in un file chiamato `create_rectangle_with_shadow.py` ed eseguilo con `python create_rectangle_with_shadow.py`.

```python
import aspose.words as aw

# ---------- Initialize document ----------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ---------- Insert rectangle ----------
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# ---------- Set fill color ----------
rectangle.fill_color = aw.Color.light_blue

# ---------- Configure shadow ----------
shadow = rectangle.shadow_format
shadow.visible = True
shadow.color = aw.Color.dark_gray
shadow.blur = 5
shadow.offset_x = 3
shadow.offset_y = 3
shadow.transparency = 0.2
shadow.type = aw.drawing.ShadowType.OUTER

# ---------- Save as PDF ----------
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

> **Nota:** Sostituisci `YOUR_DIRECTORY` con un percorso assoluto o relativo che esiste sulla tua macchina. Se la cartella non esiste, Python solleverà un `FileNotFoundError`.

## Problemi comuni e come evitarli

| Problema | Perché accade | Soluzione |
|----------|---------------|-----------|
| L’ombra non appare | `shadow.visible` lasciato al valore predefinito `False` | Assicurati che `shadow.visible = True` |
| La forma è invisibile | Colore di riempimento impostato su `aw.Color.transparent` o `None` | Usa un colore solido come `aw.Color.light_blue` |
| Il PDF è vuoto | Dimenticato di chiamare `doc.save` o salvato con estensione sbagliata | Chiama `doc.save("output.pdf")` e verifica il percorso |
| Errore di runtime `ImportError` | Aspose.Words non installato o ambiente Python errato | Esegui `pip install aspose-words` all’interno del venv attivo |

## Prossimi passi – Esplora altre forme e formattazioni

Ora che hai padroneggiato **creare forma rettangolare**, puoi:

- Sostituire `ShapeType.RECTANGLE` con `ShapeType.ELLIPSE` o `ShapeType.PENTAGON` per sperimentare altre geometrie.
- Aggiungere testo all’interno della forma usando `builder.move_to(rectangle.absolute_position)` e poi `builder.writeln("Hello World")`.
- Combinare più forme in un gruppo con `group = aw.drawing.GroupShape(doc)` per diagrammi complessi.
- Esportare in altri formati come DOCX (`doc.save("output.docx")`) o HTML (`doc.save("output.html")`) per vedere come l’ombra viene tradotta.

Ognuna di queste estensioni si basa sugli stessi concetti di base: **aggiungere ombra alla forma**, **impostare il colore di riempimento della forma**, e **salvare il documento come PDF** (o in un altro formato).

---

### Anteprima immagine *(opzionale)*

![Create rectangle shape with shadow in Python](https://example.com/rectangle-shadow.png "Create rectangle shape with shadow in Python")

*Lo screenshot mostra l’output PDF finale con un rettangolo azzurro chiaro e una leggera ombra esterna.*

---

## Conclusione

Abbiamo percorso tutti i passaggi necessari per **creare forma rettangolare** in Python, applicare un riempimento personalizzato, **aggiungere ombra alla forma**, e infine **salvare il documento come PDF**. Il codice è completamente eseguibile, le spiegazioni coprono il *perché* di ogni proprietà, e abbiamo affrontato casi limite comuni e i prossimi passi.

## Cosa dovresti imparare dopo?


I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell’API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}