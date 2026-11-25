---
category: general
date: 2026-11-25
description: Come raggruppare le forme in Word usando Java e come impostare le dimensioni
  delle forme in un file DOCX con Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- how to set shape dimensions
- set shape size word
language: it
lastmod: 2026-11-25
og_description: Come raggruppare le forme in Word con l'API Aspose.Words per Java
  e impostare rapidamente la dimensione della forma. Segui la soluzione completa passo
  dopo passo.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Come raggruppare le forme in Word e impostare le loro dimensioni – Guida
  Java
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  headline: How to group shapes in Word and set their dimensions programmatically
  type: TechArticle
- description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  name: How to group shapes in Word and set their dimensions programmatically
  steps:
  - name: Expected output
    text: '* A Word document (`GroupShape.docx`) with one page. * A `GroupShape` containing
      a 100 × 50 pt rectangle and an 80 × 80 pt ellipse. * Selecting either shape
      selects the whole group.'
  - name: How to change the position of the grouped shapes?
    text: 'After creating the `GroupShape`, you can set its `left` and `top` properties:'
  - name: What if I need to add more than two shapes?
    text: '`GroupShape` works like any other container node. Call `groupShape.appendChild(yourShape)`
      for each additional shape. The API does not limit the number of children.'
  - name: Can I apply style (fill color, line weight) to individual shapes?
    text: 'Yes. Each `Shape` object exposes formatting properties:'
  - name: Does the code work with older Aspose.Words versions?
    text: The `insertGroupShape` method was introduced in version 24.9. If you are
      on an earlier version, you’ll need to create a `GroupShape` manually via the
      node tree, which is more involved. Upgrading is the recommended path.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- shapes
title: Come raggruppare le forme in Word e impostare le loro dimensioni programmaticamente
url: /it/java/images-shapes/how-to-group-shapes-in-word-and-set-their-dimensions-program/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come raggruppare forme in Word e impostare le loro dimensioni programmaticamente

Se hai bisogno di **come raggruppare forme in Word** e controllare le loro dimensioni esatte, questa guida ti mostra una soluzione completa e pronta all'uso. Utilizzando Aspose.Words per Java puoi creare un rettangolo, un'ellisse, aggiungerli a un `GroupShape` e poi **come impostare le dimensioni della forma** come larghezza e altezza in un unico file DOCX.

Imparerai a:

* Creare un nuovo documento Word da zero.  
* Inserire un `GroupShape` (nuova API nella versione 24.9).  
* Aggiungere un rettangolo e un'ellisse al gruppo.  
* **Impostare la dimensione della forma in Word** con precisione usando `setWidth` e `setHeight`.  
* Salvare il documento su disco.

Non è necessario alcuno strumento esterno—basta Java 17+, Maven e la libreria Aspose.Words per Java.

## Prerequisiti

* Java Development Kit 17 o successivo.  
* Maven (o Gradle) per la gestione delle dipendenze.  
* Aspose.Words per Java 24.9 o successivo (l'API `GroupShape` è stata introdotta nella 24.9).  
* Familiarità di base con la sintassi Java e i concetti di programmazione orientata agli oggetti.

Se non hai ancora aggiunto Aspose.Words al tuo progetto, includi la seguente dipendenza Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Passo 1: Creare un nuovo documento e un DocumentBuilder

La classe `Document` rappresenta l'intero file Word, mentre `DocumentBuilder` fornisce un modo comodo per aggiungere contenuti.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Perché questo passo?*  
Creare un nuovo `Document` ti offre una tela pulita. `DocumentBuilder` è l'assistente di alto livello che ti permette di inserire paragrafi, tabelle e, in questo caso, forme.

## Passo 2: Inserire un GroupShape (nuova API nella versione 24.9)

Un `GroupShape` funziona come un contenitore; qualsiasi forma aggiunta diventa parte dello stesso gruppo visivo.

```java
        // Step 2: Insert a GroupShape (new API in version 24.9)
        GroupShape groupShape = builder.insertGroupShape();
```

*Perché usare `GroupShape`?*  
Raggruppare le forme semplifica lo spostamento, la rotazione o l'applicazione di formattazioni a più oggetti contemporaneamente. L'API è stata aggiunta nella 24.9, quindi le versioni precedenti non compileranno questa riga.

## Passo 3: Creare un rettangolo, impostarne le dimensioni e aggiungerlo al gruppo

Qui dimostriamo **come impostare le dimensioni della forma** per un rettangolo.

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);   // height in points
        groupShape.appendChild(rectangle);
```

*Perché impostare esplicitamente larghezza e altezza?*  
Word memorizza le dimensioni delle forme in punti. Chiamando `setWidth` e `setHeight` controlli l'esatta occupazione visiva, fondamentale quando serve un layout preciso o quando si esporta in PDF.

## Passo 4: Creare un'ellisse, impostarne le dimensioni e aggiungerla allo stesso gruppo

La stessa tecnica **imposta dimensione forma Word** funziona per qualsiasi tipo di forma.

```java
        // Step 4: Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(document, ShapeType.ELLIPSE);
        ellipse.setWidth(80.0);
        ellipse.setHeight(80.0);
        groupShape.appendChild(ellipse);
```

*Perché aggiungere l'ellisse allo stesso `GroupShape`?*  
Entrambe le forme si muoveranno insieme come un'unica unità. Questo è utile per creare icone, loghi o diagrammi complessi che devono rimanere allineati.

## Passo 5: Salvare il documento con le forme raggruppate

Infine, persisti il file DOCX su disco.

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShape.docx");
    }
}
```

L'esecuzione di questo programma produce un file chiamato **GroupShape.docx** che contiene un rettangolo e un'ellisse raggruppati. Quando apri il file in Microsoft Word, vedrai le due forme comportarsi come un unico oggetto—puoi trascinarle, ridimensionarle o ruotarle insieme.

### Output previsto

* Un documento Word (`GroupShape.docx`) con una pagina.  
* Un `GroupShape` contenente un rettangolo 100 × 50 pt e un'ellisse 80 × 80 pt.  
* Selezionando una delle forme, viene selezionato l'intero gruppo.

## Domande comuni e casi particolari

### Come modificare la posizione delle forme raggruppate?

Dopo aver creato il `GroupShape`, puoi impostare le proprietà `left` e `top`:

```java
groupShape.setLeft(150.0);
groupShape.setTop(200.0);
```

Queste coordinate sono anch'esse misurate in punti.

### E se devo aggiungere più di due forme?

`GroupShape` funziona come qualsiasi altro nodo contenitore. Chiama `groupShape.appendChild(yourShape)` per ogni forma aggiuntiva. L'API non limita il numero di figli.

### Posso applicare stile (colore di riempimento, spessore linea) alle singole forme?

Sì. Ogni oggetto `Shape` espone proprietà di formattazione:

```java
rectangle.getFillColor().setColor(Color.BLUE);
ellipse.getStroke().setWeight(2.0);
```

### Il codice funziona con versioni più vecchie di Aspose.Words?

Il metodo `insertGroupShape` è stato introdotto nella versione 24.9. Se utilizzi una versione precedente, dovrai creare manualmente un `GroupShape` tramite l'albero dei nodi, operazione più complessa. L'aggiornamento è il percorso consigliato.

## Consigli professionali

* **Usa i punti per coerenza** – L'unità interna di Word è il punto (1/72 pollice). Convertire da pixel o centimetri può portare a dimensioni inattese.  
* **Raggruppa prima di posizionare** – Posiziona il `GroupShape` dopo aver aggiunto tutti i suoi figli; altrimenti potresti dover ricalcolare gli offset.  
* **Riutilizza il DocumentBuilder** – Puoi inserire più gruppi nello stesso documento spostando il cursore del builder (`builder.moveTo`) prima di ogni chiamata a `insertGroupShape`.

## Conclusione

Ora disponi di un esempio completo, end‑to‑end, di **come raggruppare forme in Word** e **come impostare le dimensioni delle forme** usando Aspose.Words per Java. Il tutorial ha coperto la creazione di un documento, l'inserimento di un `GroupShape`, l'aggiunta di un rettangolo e di un'ellisse, l'impostazione della loro dimensione esatta e il salvataggio del risultato.  

Da qui puoi esplorare:

* Aggiungere caselle di testo o immagini allo stesso gruppo.  
* Animare le forme raggruppate con le funzionalità di SmartArt di Word (tramite l'API).  
* Esportare le forme raggruppate in PDF o SVG per l'uso web.

Sentiti libero di sperimentare con diversi tipi di forma, dimensioni e posizioni—il raggruppamento ti offre un controllo potente su layout complessi nei documenti Word.

## Cosa dovresti imparare dopo?


I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell'API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [How to create a blank Word document and group shapes in Java](/words/english/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/)
- [How to group shapes in Word with Java – complete guide](/words/english/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}