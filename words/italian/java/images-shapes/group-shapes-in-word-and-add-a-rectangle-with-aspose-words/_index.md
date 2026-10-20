---
category: general
date: 2026-09-11
description: Raggruppa le forme in Word e aggiungi una forma rettangolare usando Aspose.Words
  per Java. Scopri come impostare le dimensioni della forma, raggruppare gli oggetti
  e salvare il documento.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- how to group shapes
- how to add rectangle
language: it
lastmod: 2026-09-11
og_description: Raggruppa le forme in Word e aggiungi una forma rettangolare usando
  Aspose.Words per Java. Questo tutorial mostra come impostare le dimensioni della
  forma, raggruppare le forme e esportare il documento.
og_image_alt: Screenshot showing grouped shapes in a Word document
og_title: Raggruppa forme in Word – aggiungi rettangolo con Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  headline: Group shapes in Word and add a rectangle with Aspose.Words
  type: TechArticle
- description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  name: Group shapes in Word and add a rectangle with Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17 or later installed. * Maven or Gradle to manage dependencies.
      * A valid Aspose.Words for Java license (or a free evaluation key). * An image
      file (`sample.png`) placed in a known directory (replace `YOUR_DIRECTORY` with
      your actual path).'
  - name: Add a group shape
    text: A group shape is a container that can hold other shapes. Think of it as
      a folder for drawing objects.
  - name: How to add rectangle
    text: The code above demonstrates **how to add rectangle** by creating a `Shape`
      instance with `ShapeType.RECTANGLE` and then appending it to the `GroupShape`.
      This pattern works for any other shape type (e.g., `ELLIPSE`, `POLYLINE`).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Raggruppa forme in Word e aggiungi un rettangolo con Aspose.Words
url: /it/java/images-shapes/group-shapes-in-word-and-add-a-rectangle-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Raggruppare forme in Word e aggiungere un rettangolo con Aspose.Words

Se hai bisogno di **raggruppare forme in Word** aggiungendo programmaticamente un rettangolo, questa guida ti fornisce una soluzione completa, pronta all'uso. Vedrai esattamente come inserire una forma di gruppo, aggiungere una forma rettangolare, impostare le dimensioni della forma e infine salvare il documento per visualizzare immediatamente il risultato.

Lavorare con documenti Word spesso significa disporre più oggetti—immagini, grafici o semplici forme geometriche—in un'unica unità logica. Raggruppare quegli oggetti rende più semplice spostarli, ruotarli o formattarli insieme. In questo tutorial tratteremo anche **come aggiungere forme rettangolari** e **impostare le dimensioni della forma** per un controllo di layout perfetto.

## Cosa imparerai

* Come creare un nuovo documento Word con Aspose.Words per Java.  
* **Come raggruppare forme** in modo che si comportino come un unico oggetto.  
* **Aggiungere forma rettangolare** a un gruppo e inserire un'immagine nello stesso gruppo.  
* **Impostare le dimensioni della forma** sia per il rettangolo sia per l'immagine.  
* Salvare il documento e aprirlo in Microsoft Word per verificare il risultato.

### Prerequisiti

* Java 17 o versioni successive installate.  
* Maven o Gradle per gestire le dipendenze.  
* Una licenza valida di Aspose.Words per Java (o una chiave di valutazione gratuita).  
* Un file immagine (`sample.png`) collocato in una directory nota (sostituisci `YOUR_DIRECTORY` con il tuo percorso effettivo).

---

## Come raggruppare forme in Word usando Aspose.Words

Il primo passo è creare un `Document` e un `DocumentBuilder`. Il builder ti offre un'API comoda per inserire forme, testo e altri elementi.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Initialize the document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Perché è importante:** `DocumentBuilder` lavora direttamente con l'oggetto `Document` sottostante, consentendoti di inserire forme senza gestire manualmente collezioni di nodi a basso livello.

### Aggiungere una forma di gruppo

Una forma di gruppo è un contenitore che può contenere altre forme. Pensala come una cartella per oggetti di disegno.

```java
        // Insert an empty group shape – this will hold the rectangle and the picture
        GroupShape group = builder.insertGroupShape();
```

Il metodo `insertGroupShape()` crea un nodo `GroupShape` e lo restituisce così puoi aggiungere forme figlie in seguito.  

---

## Aggiungere una forma rettangolare al gruppo

Ora **aggiungeremo una forma rettangolare** al gruppo creato in precedenza. Il rettangolo servirà da sfondo o bordo per l'immagine.

```java
        // Create a rectangle shape with a specific size
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points
        rectangle.setHeight(50.0);   // height in points
        rectangle.setFillColor(java.awt.Color.LIGHT_GRAY);
        rectangle.setStrokeColor(java.awt.Color.DARK_GRAY);
        rectangle.setStrokeWeight(1.0);
        // Append the rectangle to the group
        group.appendChild(rectangle);
```

> **Suggerimento:** Impostare `FillColor` e `StrokeColor` rende il rettangolo visibile nel documento finale. Se ometti queste proprietà, la forma potrebbe apparire trasparente.

### Come aggiungere un rettangolo

Il codice sopra dimostra **come aggiungere un rettangolo** creando un'istanza `Shape` con `ShapeType.RECTANGLE` e poi aggiungendola al `GroupShape`. Questo schema funziona per qualsiasi altro tipo di forma (ad es., `ELLIPSE`, `POLYLINE`).

---

## Impostare le dimensioni della forma per rettangolo e immagine

Dimensionare correttamente garantisce che il rettangolo e l'immagine siano allineati correttamente. Qui **impostiamo le dimensioni della forma** anche per l'immagine che inseriremo subito dopo.

```java
        // Insert an image and set its size
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.png");
        picture.setWidth(100.0);   // match rectangle width
        picture.setHeight(50.0);   // match rectangle height
        // Append the picture to the same group
        group.appendChild(picture);
```

Sia il rettangolo sia l'immagine ora condividono le stesse dimensioni (100 × 50 punti). Poiché appartengono allo stesso gruppo, spostare o ruotare il gruppo influenzerà entrambe le forme contemporaneamente.

> **Perché abbinare le dimensioni?** Allineare le dimensioni garantisce che l'immagine si trovi ordinatamente all'interno del rettangolo, creando un effetto “immagine incorniciata” pulito.

---

## Salvare il documento e visualizzare il risultato

Infine, scriviamo il documento su disco. Aprendo il file in Microsoft Word vedrai le forme raggruppate come un unico oggetto selezionabile.

```java
        // Save the document – the group will appear as one object in Word
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved successfully.");
    }
}
```

Quando apri `output.docx`, vedrai un rettangolo con l'immagine al suo interno. Cliccando sulla forma vengono selezionati sia il rettangolo sia l'immagine perché sono **raggruppati**.

![group shapes in word example](https://example.com/images/group-shapes-word.png "group shapes in word example")

*Testo alternativo immagine:* *group shapes in word example* – un documento Word che mostra un rettangolo e un'immagine raggruppati.

---

## Domande frequenti e gestione dei casi limite

| Domanda | Risposta |
|----------|----------|
| **E se ho bisogno di una dimensione diversa per l'immagine?** | Regola `picture.setWidth()` e `picture.setHeight()` dopo l'inserimento. Il rettangolo può mantenere la sua dimensione originale, oppure puoi ridimensionarlo per farlo corrispondere. |
| **Posso aggiungere altre forme allo stesso gruppo?** | Sì. Chiama `group.appendChild(newShape)` per qualsiasi oggetto `Shape` aggiuntivo. |
| **Come ruoto l'intero gruppo?** | Usa `group.setRotationAngle(double angleInRadians)`. La rotazione si applica a tutte le forme figlie. |
| **Cosa succede se il file immagine è mancante?** | `insertImage` lancia `FileNotFoundException`. Avvolgi la chiamata in un blocco try‑catch e fornisci una forma segnaposto di riserva. |
| **È possibile separare il gruppo in seguito?** | Chiama `group.removeAllChildren()` per staccare i figli, quindi reinseriscili nel documento singolarmente. |

---

## Conclusione

Ora disponi di un esempio completo e eseguibile che mostra **come raggruppare forme in Word**, **aggiungere una forma rettangolare**, **impostare le dimensioni della forma** e **salvare** il documento usando Aspose.Words per Java. Raggruppando il rettangolo e l'immagine, puoi spostarli, ridimensionarli o ruotarli come un'unica unità—esattamente ciò che richiedono molti scenari di automazione dei documenti.

Da qui potresti approfondire:

* Aggiungere caselle di testo allo stesso gruppo (`how to add rectangle`‑style text).  
* Applicare diversi pattern di riempimento o gradienti (`set shape size` combinato con lo styling).  
* Usare la stessa tecnica per raggruppare grafici, tabelle o SmartArt (`how to group shapes` su altri tipi di oggetti).  

Sentiti libero di sperimentare con altri tipi di forma, colori e opzioni di layout. Buona programmazione!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell'API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}