---
category: general
date: 2026-11-25
description: Aggiungi un'ombra alla forma in un documento Word con Python. Scopri
  come inserire una forma rettangolare in Word e applicare un'ombra trasparente usando
  Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- insert rectangle shape word
- how to create word document python
- Aspose.Words Python
- shape formatting Python
language: it
lastmod: 2026-11-25
og_description: Aggiungi un'ombra alla forma in un documento Word usando Python. Questo
  tutorial mostra come inserire una forma rettangolare in Word e impostare un'ombra
  trasparente al 30 % con Aspose.Words.
og_image_alt: Add shadow to shape example in a Word document created by Python
og_title: Aggiungi un'ombra alla forma in un documento Word con Python – guida passo
  passo
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Add shadow to shape in a Word document with Python. Learn how to insert
    rectangle shape in Word and apply a transparent shadow using Aspose.Words.
  headline: How to add shadow to shape in a Word document using Python
  type: TechArticle
tags:
- Python
- Aspose.Words
- Word automation
title: Come aggiungere l'ombra a una forma in un documento Word usando Python
url: /it/python/images-shapes/how-to-add-shadow-to-shape-in-a-word-document-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come aggiungere un'ombra a una forma in un documento Word usando Python

Se devi **aggiungere un'ombra a una forma** in un documento Word, questa guida ti mostra una soluzione completa e funzionante. Vedrai come creare un file Word, inserire una forma rettangolare e applicare un'ombra trasparente al 30 % — tutto con la libreria Aspose.Words per Python.

Lavorare programmaticamente con i documenti Word ti libera dalla formattazione manuale e ti consente di generare report, contratti o volantini di marketing su larga scala. Alla fine di questo tutorial sarai in grado di rispondere a “**come creare un documento Word con Python**” con un esempio di codice pronto all'uso.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* Python 3.8 o versioni successive installate.
* Una licenza attiva di Aspose.Words per Python (la versione di prova gratuita è sufficiente per la valutazione).
* Il pacchetto `aspose-words` installato tramite `pip install aspose-words`.
* Una cartella in cui il file di output possa essere scritto (sostituisci `YOUR_DIRECTORY` nel codice).

Non sono richieste dipendenze aggiuntive.

## Passo 1: Creare un nuovo documento Word

Il primo passo è istanziare un oggetto `Document`. Questo oggetto rappresenta l'intero file .docx in memoria.

```python
import aspose.words as aw

# Create an empty Word document
doc = aw.Document()
# DocumentBuilder provides a convenient API for adding content
builder = aw.DocumentBuilder(doc)
```

`DocumentBuilder` funziona come un cursore virtuale. Quando chiami i suoi metodi, la libreria inserisce gli elementi corrispondenti nella posizione corrente del cursore.

## Passo 2: Inserire una forma rettangolare

Successivamente **inserisci una forma rettangolare** usando il metodo `insert_shape` del builder. Il metodo richiede il tipo di forma e le sue dimensioni in punti (1 punto = 1/72 di pollice).

```python
# Insert a rectangle shape that is 100 points wide and 50 points tall
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)
```

Puoi modificare le dimensioni per adattarle al tuo design. Il rettangolo diventa parte del livello di disegno del documento, il che significa che potrai in seguito modificare il riempimento, il contorno o l'ombra.

## Passo 3: Accedere al formato ombra della forma

Ogni oggetto di disegno espone una proprietà `shadow_format` che controlla l'aspetto dell'ombra. Recuperala così da poter regolare trasparenza, offset, sfocatura e colore.

```python
# Get the ShadowFormat object for the rectangle
shadow = shape.shadow_format
```

A questo punto la forma ha l'ombra predefinita (nessuna ombra). L'oggetto `ShadowFormat` contiene tutti i parametri necessari per creare un effetto realistico.

## Passo 4: Rendere l'ombra trasparente al 30 %

La trasparenza è espressa come valore compreso tra `0` (completamente opaco) e `1` (completamente trasparente). Impostandola a `0.3` ottieni un'ombra al 30 % trasparente, spesso sufficiente per aggiungere profondità senza sovrastare il testo.

```python
# Apply a 30 % transparent shadow
shadow.transparency = 0.3
# Optional: adjust other shadow properties for a nicer look
shadow.visible = True               # Ensure the shadow is turned on
shadow.distance = 4                 # Distance of the shadow from the shape (points)
shadow.blur = 4                     # Amount of blur applied to the shadow
shadow.color = aw.Color.black       # Shadow color
```

Queste proprietà aggiuntive non sono obbligatorie, ma illustrano come è possibile perfezionare l'effetto. Il flag `visible` è essenziale; se lo dimentichi, l'ombra non apparirà anche se le altre impostazioni sono configurate.

## Passo 5: Salvare il documento per visualizzare il risultato

Infine, scrivi il documento su disco. Aprire il file `.docx` risultante in Microsoft Word o in qualsiasi visualizzatore compatibile mostra il rettangolo con l'ombra trasparente applicata.

```python
# Save the document to the desired location
output_path = r"YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Quando apri `output.docx`, vedrai un semplice rettangolo con una leggera ombra grigia spostata verso il basso‑destra. La trasparenza del 30 % fa apparire la forma sollevata dalla pagina.

![Add shadow to shape example](placeholder-image.png){: .align-center alt="Esempio di aggiunta di ombra a una forma in un documento Word creato con Python"}

## Script completo, eseguibile

Unire tutti i pezzi fornisce uno script autonomo che puoi copiare, incollare ed eseguire immediatamente.

```python
import aspose.words as aw

def create_word_with_shadow(output_path: str):
    """
    Creates a Word document that contains a rectangle shape
    with a 30 % transparent shadow.
    """
    # Step 1: Initialize document and builder
    doc = aw.Document()
    builder = aw.DocumentBuilder(doc)

    # Step 2: Insert rectangle shape
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)

    # Step 3: Access shadow format
    shadow = shape.shadow_format

    # Step 4: Configure shadow properties
    shadow.visible = True
    shadow.transparency = 0.3
    shadow.distance = 4
    shadow.blur = 4
    shadow.color = aw.Color.black

    # Step 5: Save the document
    doc.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    # Replace with a valid folder on your machine
    create_word_with_shadow(r"YOUR_DIRECTORY/output.docx")
```

**Output previsto:** L'apertura del `output.docx` generato mostra una singola pagina con un rettangolo che proietta un'ombra leggera e semi‑trasparente. Non è necessaria alcuna formattazione aggiuntiva.

## Varianti comuni e casi limite

| Situazione | Come adattare il codice |
|------------|--------------------------|
| **Tipo di forma diverso** (ad es., ellisse) | Cambia `aw.drawing.ShapeType.RECTANGLE` in `aw.drawing.ShapeType.ELLIPSE`. |
| **Colore ombra personalizzato** | Imposta `shadow.color = aw.Color.from_argb(255, 128, 0, 0)` per un'ombra rossastra. |
| **Forme multiple** | Chiama `builder.insert_shape` più volte; ogni chiamata restituisce un oggetto `Shape` separato che puoi stilizzare indipendentemente. |
| **Salvataggio come PDF** | Sostituisci `doc.save(output_path)` con `doc.save(output_path.replace('.docx', '.pdf'))` e usa l'estensione `.pdf`. |
| **Esecuzione senza licenza** | La versione di prova gratuita aggiunge una filigrana alla prima pagina. Acquista una licenza per rimuoverla in produzione. |

Queste varianti dimostrano che lo stesso schema — creare un documento, inserire una forma, regolare `shadow_format`, salvare — copre la maggior parte degli scenari di automazione.

## Suggerimenti e best practice

* **Riutilizza il builder**: Mantieni una singola istanza di `DocumentBuilder` per l'intero documento per evitare creazioni di oggetti non necessarie.
* **Rilascia le risorse**: Nei servizi a lunga esecuzione, chiama `doc.dispose()` dopo il salvataggio per liberare la memoria nativa.
* **Convalida l'output**: Usa `doc.validate(aw.ValidationType.FULL_VALIDATION)` prima del salvataggio se devi garantire la conformità allo standard Open XML.
* **Compatibilità di versione**: Il codice funziona con Aspose.Words per Python ≥ 22.9. Assicurati che il tuo pacchetto sia aggiornato con `pip install --upgrade aspose-words`.

## Conclusione

Ora sai come **aggiungere un'ombra a una forma** in un documento Word usando Python. Seguendo i cinque passaggi — creare un documento, **inserire una forma rettangolare**, configurare l'ombra e salvare — puoi automatizzare la generazione di documenti curati per report, fatture o materiale di marketing.  

Da qui potresti esplorare altre opzioni di formattazione come riempimenti a gradiente, avvolgimento del testo o la conversione del documento in PDF. Ognuno di questi argomenti si basa sugli stessi concetti di `DocumentBuilder` e formattazione delle forme introdotti in questo tutorial.

Buona programmazione e goditi la profondità visiva che una semplice ombra può dare ai tuoi documenti Word automatizzati!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci alternativi nei tuoi progetti.

- [Come creare una forma rettangolare in un documento Word usando Python](/words/english/python-net/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/)
- [Aggiungere ombra a una forma in Python – Tutorial completo Aspose.Words](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [Creare un documento Word vuoto e aggiungere ombra a una forma – Guida completa Python](/words/english/python-net/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-pyth/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}