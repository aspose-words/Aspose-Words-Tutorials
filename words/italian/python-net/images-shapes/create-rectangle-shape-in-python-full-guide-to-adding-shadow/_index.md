---
category: general
date: 2026-05-04
description: Scopri come creare una forma rettangolare, come aggiungere una forma
  con ombre, cambiare il colore dell'ombra, impostare la distanza dell'ombra e salvare
  il documento come PDF utilizzando Aspose.Words per Python.
draft: false
keywords:
- create rectangle shape
- how to add shape
- change shadow color
- save document as pdf
- set shadow distance
language: it
og_description: Crea una forma rettangolare con Aspose.Words per Python, scopri come
  aggiungere una forma, cambiare il colore dell'ombra, impostare la distanza dell'ombra
  e salvare il documento in PDF.
og_title: Crea forma rettangolare – Aggiungi ombra, cambia colore e salva come PDF
tags:
- Aspose.Words
- Python
- PDF generation
title: Crea una forma rettangolare in Python – Guida completa per aggiungere ombre
  e salvare in PDF
url: /it/python/images-shapes/create-rectangle-shape-in-python-full-guide-to-adding-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea forma rettangolare – Tutorial completo per sviluppatori Python

Hai mai dovuto **creare una forma rettangolare** in un documento Word e ti sei chiesto come aggiungere un’ombra curata? Forse stai costruendo un generatore di report e l’aspetto visivo è importante—soprattutto quando il risultato finale è un PDF. La buona notizia? Con Aspose.Words per Python puoi non solo **come aggiungere una forma** ma anche regolare ogni proprietà dell’ombra, dal colore alla distanza, e poi **salvare il documento come pdf** in un unico flusso fluido.

In questa guida percorreremo l’intero processo passo‑passo. Vedrai il codice esatto da copiare‑incollare, comprenderai *perché* ogni riga è importante e apprenderai qualche trucco per gestire casi particolari (come ombre trasparenti o DPI non standard). Alla fine sarai in grado di **creare una forma rettangolare**, personalizzare la sua ombra e esportare un PDF nitido senza sforzo.

## Prerequisiti

- Python 3.8+ installato sulla tua macchina.  
- Aspose.Words per Python tramite `pip install aspose-words`.  
- Familiarità di base con la programmazione orientata agli oggetti in Python (nulla di complicato).  

Se hai già un ambiente virtuale configurato, esegui semplicemente il comando di installazione e sei pronto.

## Passo 1: Inizializzare il Documento e il Builder

Prima di poter **come aggiungere una forma**, ti serve un documento vuoto su cui lavorare. La classe `Document` rappresenta l’intero file, e `DocumentBuilder` è il tuo pennello.

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder to edit it
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

*Perché è importante:* `Document` contiene tutte le sezioni, le pagine e le risorse. `DocumentBuilder` ti offre un’API fluida per inserire contenuti esattamente dove ti serve—pensala come un cursore in un elaboratore di testi.

## Passo 2: Inserire la Forma Rettangolare

Ora aggiungiamo effettivamente **come aggiungere una forma**. Il metodo `insert_shape` richiede il tipo di forma e le sue dimensioni (in punti). Qui scegliamo un rettangolo 200 × 100 pt e gli diamo un riempimento azzurro chiaro.

```python
# Step 2: Insert a rectangle shape and give it a light‑blue fill
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,  # shape type
    200,                            # width in points
    100)                            # height in points
rectangle_shape.fill_color = aw.Color.light_blue
```

*Consiglio professionale:* Se la forma deve allinearsi al testo esistente, usa `builder.move_to` prima dell’inserimento, o regola le proprietà `left`/`top` dopo la creazione.

## Passo 3: Attivare l’Ombra

Una forma senza ombra appare piatta. Per **impostare la distanza dell’ombra** e rendere l’effetto visibile, recupera il formato ombra e abilitalo.

```python
# Step 3: Access the shape's shadow format and make the shadow visible
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
```

*Perché questo passo:* Il formato ombra è un oggetto separato; impostare `visible` è la prima cosa da fare, altrimenti tutte le altre proprietà dell’ombra vengono ignorate.

## Passo 4: Stilizzare l’Ombra – Colore, Sfocatura, Distanza, Direzione

Qui avviene la magia. **Cambieremo il colore dell’ombra**, regoleremo il raggio di sfocatura, imposteremo quanto lontano l’ombra è dal rettangolo e la ruoteremo di 45°.

```python
# Step 4: Configure the appearance of the shadow
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER   # outer shadow
rectangle_shadow.blur_radius = 10.0                    # blur amount (pixels)
rectangle_shadow.distance = 5.0                        # distance from the shape
rectangle_shadow.direction = 45.0                     # angle in degrees
rectangle_shadow.color = aw.Color.gray                 # shadow colour
```

*Spiegazione di ogni proprietà:*

| Proprietà | Cosa fa | Valori tipici |
|----------|--------------|----------------|
| `style` | Determina se l’ombra è *interna* o *esterna*. | `OUTER` (il più comune) |
| `blur_radius` | Controlla la morbidezza; valori più alti = bordi più sfumati. | 0–20 px è usuale |
| `distance` | Quanto è spostata l’ombra dalla forma. | 0–10 pt per un effetto sottile, >10 per un effetto drammatico |
| `direction` | Angolo della sorgente luminosa, misurato in senso orario dall’asse x. | 0‑360° |
| `color` | Tinta dell’ombra. | Qualsiasi `aw.Color` (es. `gray`, `dark_red`) |

*Caso limite:* Se imposti `distance` a `0` l’ombra si troverà direttamente sotto la forma, nascondendo efficacemente il riempimento. Mantienila sopra `0` per un offset visibile.

## Passo 5: Salvare il Documento come PDF

Infine, **salviamo il documento come pdf**. Aspose.Words rasterizza automaticamente l’ombra, così il PDF appare esattamente come nella visualizzazione di Word.

```python
# Step 5: Save the document as a PDF with the shadowed shape
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

*Perché il PDF?* I PDF mantengono il layout su tutte le piattaforme, rendendoli perfetti per report, fatture o qualsiasi artefatto stampabile.

---

![Create rectangle shape with shadow](https://example.com/images/rectangle-shadow.png){: .align-center alt="esempio di creazione di forma rettangolare con ombra"}

*L’immagine sopra mostra l’output PDF finale – un rettangolo azzurro chiaro con un’ombra grigia esterna soffusa, esattamente come l’abbiamo configurata.*

## Domande frequenti e varianti

### E se avessi bisogno di un’ombra **trasparente**?

Imposta il canale alfa sul colore dell’ombra:

```python
transparent_gray = aw.Color.from_argb(128, 0, 0, 0)  # 50% opacity black
rectangle_shadow.color = transparent_gray
```

### Posso applicare la stessa ombra a più forme?

Sì. Estrai il `ShadowFormat` da una forma e assegnalo a un’altra:

```python
another_shape = builder.insert_shape(aw.drawing.ShapeType.ELLIPSE, 150, 150)
another_shape.shadow_format = rectangle_shadow.clone()
```

### Come cambio l’ombra per un **tipo di forma diverso**?

Tutti i tipi di forma condividono le stesse proprietà `ShadowFormat`, quindi puoi riutilizzare lo stesso blocco di configurazione—basta sostituire `ShapeType.RECTANGLE` con `ShapeType.OVAL`, `ShapeType.TRIANGLE`, ecc.

### Cosa fare per **PDF ad alta risoluzione** per la stampa?

Specifica le `PdfSaveOptions` con un DPI più alto:

```python
options = aw.saving.PdfSaveOptions()
options.image_resolution = 300  # 300 DPI for print quality
document.save(output_path, options)
```

## Riepilogo

Abbiamo coperto tutto ciò che ti serve per **creare una forma rettangolare**, **come aggiungere una forma**, personalizzare il **colore dell’ombra**, **impostare la distanza dell’ombra**, e infine **salvare il documento come pdf**. Lo script completo, eseguibile, è il seguente:

```python
import aspose.words as aw

# Initialise document
document = aw.Document()
builder = aw.DocumentBuilder(document)

# Insert rectangle shape
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle_shape.fill_color = aw.Color.light_blue

# Enable and style shadow
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER
rectangle_shadow.blur_radius = 10.0
rectangle_shadow.distance = 5.0
rectangle_shadow.direction = 45.0
rectangle_shadow.color = aw.Color.gray

# Save as PDF
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Esegui lo script, apri il file `ShadowedShape.pdf` generato, e vedrai un rettangolo nitido con una leggera ombra grigia—esattamente quello che ti aspetti da un report formattato professionalmente.

## E ora?

- **Esplora altri tipi di forma** (`ShapeType.OVAL`, `ShapeType.LINE`) per arricchire i tuoi documenti.  
- **Combina più ombre** sovrapponendo forme; puoi persino creare un effetto “glow” usando un’ombra interna con un colore brillante.  
- **Automatizza l’elaborazione batch**: cicla su una collezione di righe di dati, genera una forma per ogni riga e unisci tutto in un unico PDF.  
- **Integra con altre librerie Aspose** (es. Aspose.Slides) se devi esportare lo stesso visual in PowerPoint.

Sentiti libero di sperimentare—cambia il `blur_radius`, gioca con `direction`, o sostituisci `gray` con una tonalità specifica del tuo brand. L’API è sufficientemente flessibile che pochi aggiustamenti possono cambiare drasticamente l’impatto visivo.

Hai domande o uno scenario difficile? Lascia un commento qui sotto o contatta i forum della community Aspose. Buona programmazione e goditi quei rettangoli splendidamente ombreggiati!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}