---
category: general
date: 2026-09-30
description: Scopri come creare una forma rettangolare, applicare l'ombra alla forma
  e salvare il documento Word con la forma usando Aspose.Words per Python.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- how to add shape
- apply shadow to shape
- set shadow blur
- save word with shape
language: it
lastmod: 2026-09-30
og_description: Crea rapidamente una forma rettangolare in un documento Word. Questo
  tutorial mostra come aggiungere una forma, applicare un'ombra alla forma, impostare
  la sfocatura dell'ombra e salvare il documento Word con la forma.
og_image_alt: Screenshot of a Word document showing a rectangle shape with a soft
  shadow
og_title: Crea una forma rettangolare in Word con Python – guida passo passo
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Learn how to create rectangle shape, apply shadow to shape, and save
    Word with shape using Aspose.Words for Python.
  headline: How to create rectangle shape in a Word document using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- Shapes
title: Come creare una forma rettangolare in un documento Word usando Python
url: /it/python/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare una forma rettangolare in un documento Word usando Python

Se hai bisogno di **creare una forma rettangolare** in un file Word, questa guida ti mostra una soluzione completa e eseguibile. Vedrai come aggiungere la forma, applicare un effetto ombra, regolare la sfocatura e infine **salvare Word con la forma** in modo che il risultato possa essere aperto in Microsoft Word o in qualsiasi visualizzatore compatibile.

L'esempio utilizza **Aspose.Words for Python via .NET**, una libreria che consente di manipolare documenti Word senza avere Microsoft Office installato. Non è necessaria alcuna esperienza pregressa con l'API—basta una conoscenza di base di Python.

## Cosa otterrai

- Inserire un rettangolo nella prima sezione di un nuovo documento.  
- Configurare un'ombra morbida impostando la sua sfocatura, offset e colore.  
- Persistere il documento su disco e verificare il risultato visivo.

## Prerequisiti

- Python 3.8 o superiore.  
- Pacchetto `aspose-words` installato (`pip install aspose-words`).  
- Permessi di scrittura nella directory di output.

## Creare la forma rettangolare e configurarne l'aspetto

Il primo passo è istanziare un documento vuoto e aggiungere una forma rettangolare. La forma servirà da tela per l'effetto ombra.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Step 1: Create a new blank document
doc = aw.Document()

# Step 2: Add a rectangle shape to the first section
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Optional: Define the shape’s size and position (in points)
shape.width = aw.ConvertUtil.inch_to_point(2)   # 2 inches wide
shape.height = aw.ConvertUtil.inch_to_point(1)  # 1 inch tall
shape.left = aw.ConvertUtil.inch_to_point(1)    # 1 inch from the left margin
shape.top = aw.ConvertUtil.inch_to_point(1)     # 1 inch from the top margin
```

**Perché è importante:**  
Creare il rettangolo ti fornisce un oggetto concreto (`shape`) che potrai stilizzare in seguito. Impostare dimensioni esplicite garantisce che la forma abbia lo stesso aspetto su ogni piattaforma.

## Come aggiungere una forma a un documento Word

Mentre il codice sopra aggiunge già il rettangolo, potresti dover aggiungere forme aggiuntive (ad esempio cerchi, frecce) in seguito. Lo stesso schema si applica: chiama `append_child` sul corpo del documento e passa il `ShapeType` desiderato.

```python
# Example: Adding a second shape – an ellipse
ellipse = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.ELLIPSE)
)
ellipse.width = aw.ConvertUtil.inch_to_point(1.5)
ellipse.height = aw.ConvertUtil.inch_to_point(1)
ellipse.left = aw.ConvertUtil.inch_to_point(3.5)
ellipse.top = aw.ConvertUtil.inch_to_point(1)
```

**Suggerimento:** Usa l'enumerazione `ShapeType` per esplorare tutte le forme supportate. Questo mantiene il codice leggibile ed evita numeri magici.

## Applicare l'ombra alla forma e impostare la sfocatura dell'ombra

Un'ombra aggiunge profondità e interesse visivo. La classe `ShadowEffect` ti permette di controllare sfocatura, offset e colore. Di seguito applichiamo un'ombra nera morbida al rettangolo.

```python
# Step 3: Configure a shadow effect for the rectangle
shadow = ShadowEffect()
shadow.blur = 5.0          # Sets the softness of the shadow edge
shadow.offset_x = 2.0      # Horizontal displacement from the shape
shadow.offset_y = 2.0      # Vertical displacement from the shape
shadow.color = aw.Color.black

# Step 4: Apply the shadow effect to the shape
shape.shadow = shadow
```

**Perché impostare la sfocatura?**  
`blur` determina quanto è diffusa l'ombra. Un valore basso (ad es. 1.0) produce un bordo netto, mentre un valore più alto (ad es. 5.0) crea una sfumatura delicata, spesso più gradevole estetica.

**Caso limite:** Se imposti `blur` a 0, l'ombra diventa una silhouette solida. Alcuni visualizzatori potrebbero renderla con artefatti di aliasing, quindi scegli un valore maggiore di 0 per un output più fluido.

## Salvare Word con la forma

Persistere il documento finalizza tutte le modifiche. Il metodo `save` scrive un file `.docx` che qualsiasi elaboratore di testi moderno può aprire.

```python
# Step 5: Save the document to see the result
output_path = "output.docx"   # Adjust the path as needed
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Quando apri `output.docx`, vedrai un rettangolo posizionato a un pollice dall'angolo in alto a sinistra, con un'ombra nera morbida spostata di due punti verso destra e verso il basso. La sfocatura dell'ombra fa sembrare la forma sollevata dalla pagina.

**Consiglio professionale:** Se devi generare molti documenti in un ciclo, riutilizza la stessa istanza `Document` e svuota il suo corpo tra un'iterazione e l'altra per ridurre il consumo di memoria.

## Varianti comuni e risoluzione dei problemi

| Situazione | Cosa cambiare | Motivo |
|------------|----------------|--------|
| Colore ombra diverso | `shadow.color = aw.Color.red` | Usa i colori del brand o evidenzia forme importanti. |
| Offset ombra più grande | Aumenta `shadow.offset_x`/`offset_y` | Enfatizza la profondità per mock‑up UI. |
| Nessuna ombra | Ometti la riga `shape.shadow = shadow` | Utile per report minimalisti. |
| Esportare in PDF invece di DOCX | `doc.save("output.pdf")` | Il PDF è ideale per distribuzione in sola lettura. |

Se la forma non appare, verifica di aggiungerla alla sezione corretta (`get_first_section()`) e che il documento venga salvato dopo le modifiche.

## Esempio completo, eseguibile

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Create a new blank document
doc = aw.Document()

# Add a rectangle shape
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
shape.width = aw.ConvertUtil.inch_to_point(2)
shape.height = aw.ConvertUtil.inch_to_point(1)
shape.left = aw.ConvertUtil.inch_to_point(1)
shape.top = aw.ConvertUtil.inch_to_point(1)

# Configure and apply a shadow
shadow = ShadowEffect()
shadow.blur = 5.0
shadow.offset_x = 2.0
shadow.offset_y = 2.0
shadow.color = aw.Color.black
shape.shadow = shadow

# Save the document
output_path = "output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Eseguendo lo script si genera `output.docx` contenente il rettangolo con un'ombra morbida. Apri il file in Microsoft Word per confermare che l'effetto visivo corrisponda alla descrizione.

## Conclusione

Ora sai come **creare una forma rettangolare**, **come aggiungere una forma** a un documento Word, **applicare un'ombra alla forma**, **impostare la sfocatura dell'ombra** e infine **salvare Word con la forma** usando Aspose.Words for Python. Lo stesso schema può essere esteso ad altri tipi di forma, colori ed effetti, offrendoti il pieno controllo sulla grafica del documento senza dipendere dall'automazione di Office.

**Passi successivi**

- Sperimenta con `Shape.fill` per aggiungere sfondi a gradiente o immagine.  
- Usa gli oggetti `Paragraph` per inserire testo all'interno del rettangolo.  
- Combina più forme per costruire diagrammi complessi, poi esporta in PDF per la distribuzione.  

Sentiti libero di adattare il codice alle tue esigenze di reporting o templating, e condividi i tuoi risultati nei commenti!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}