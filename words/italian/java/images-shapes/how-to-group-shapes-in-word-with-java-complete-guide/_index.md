---
category: general
date: 2026-10-16
description: Impara a raggruppare le forme in Word usando Java. Questo tutorial mostra
  come aggiungere una forma rettangolare, impostare le dimensioni e le misure della
  forma e salvare il documento.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- set shape dimensions
- rectangle shape code
language: it
lastmod: 2026-10-16
og_description: Raggruppa le forme in Word usando Java. Aggiungi una forma rettangolare,
  imposta le dimensioni e le misure della forma e crea documenti professionali in
  modo programmatico.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Raggruppa forme in Word con Java – guida passo passo
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  headline: How to group shapes in Word with Java – complete guide
  type: TechArticle
- description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  name: How to group shapes in Word with Java – complete guide
  steps:
  - name: Expected output
    text: '- A file named **GroupShapeDemo.docx** appears in the project folder. -
      Opening the file in Word shows two shapes (a rectangle and an ellipse) that
      are grouped together. - Dragging either shape moves the whole group, confirming
      that **group shapes in word** works as intended.'
  - name: Pro tip
    text: 'When you need to **set shape dimensions** based on dynamic data (e.g.,
      a barcode length), calculate the width/height in points first:'
  - name: What’s next?
    text: '- Explore **add rectangle shape** variations such as rounded corners (`ShapeType.RECTANGLE`
      with `setCornerRadius`). - Combine **group shapes in word** with tables or charts
      for richer documents. - Look into the Aspose.Words API for **text wrapping**
      (`shape.setWrapType(WrapType.SQUARE)`) to control'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Come raggruppare le forme in Word con Java – guida completa
url: /it/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come raggruppare forme in Word con Java – guida completa

Se hai bisogno di **raggruppare forme in Word** programmaticamente, questo tutorial ti fornisce una soluzione pronta all'uso. Vedrai come **aggiungere una forma rettangolare**, regolare le sue dimensioni, impostare le dimensioni della forma e, infine, salvare un file DOCX che contiene un rettangolo raggruppato e un'ellisse.

Raggruppare forme in Word è utile per costruire diagrammi complessi, creare componenti grafiche riutilizzabili o semplicemente tenere insieme oggetti correlati quando il documento viene modificato in seguito. Il codice utilizza la libreria Aspose.Words for Java, che funziona con qualsiasi JDK recente e non richiede l'installazione di Microsoft Word.

## Prerequisiti

Prima di iniziare, assicurati di avere:

| Requisito | Motivo |
|-------------|--------|
| Java 17 (o successiva) | La libreria è destinata a runtime Java moderni. |
| Aspose.Words for Java (ultima versione) | Fornisce le classi `Document`, `DocumentBuilder`, `GroupShape` e `Shape` usate nell'esempio. |
| Un IDE o uno strumento di build (Maven/Gradle) | Per compilare ed eseguire il campione. |
| Conoscenza di base della sintassi Java | Necessaria per comprendere il flusso del codice. |

Aggiungi la dipendenza Aspose.Words al tuo progetto. Per Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version> <!-- Use the latest version -->
</dependency>
```

Oppure per Gradle:

```gradle
implementation 'com.aspose:aspose-words:23.10'
```

## Panoramica della soluzione

Il tutorial segue un chiaro schema **problema → soluzione → spiegazione**:

1. **Crea un nuovo documento Word** e ottieni un `DocumentBuilder`.  
2. **Inserisci un contenitore `GroupShape`** che conterrà più forme.  
3. **Aggiungi un rettangolo**, imposta larghezza/altezza (passo **set shape size**) e collegalo al gruppo.  
4. **Aggiungi un'ellisse**, posizionala all'interno dello stesso gruppo e imposta anche le sue dimensioni.  
5. **Salva** il documento su disco.

Ogni passaggio include il **perché** del codice, così capirai cosa fa l'API e come adattarla ad altri scenari.

## Passo 1: Crea il documento e un DocumentBuilder

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to work with it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Perché è importante:** `Document` rappresenta l'intero file DOCX, mentre `DocumentBuilder` è un helper che ti consente di inserire contenuti senza gestire i nodi a basso livello. Creandoli per primi ottieni una tela pulita per tutte le operazioni successive sulle forme.

## Passo 2: Inserisci un contenitore GroupShape

```java
        // Step 2: Insert a GroupShape container that will hold multiple shapes
        GroupShape groupShape = builder.insertGroupShape();
```

Un `GroupShape` funziona come una **cartella** per gli oggetti di disegno. Quando sposti, ruoti o elimini il gruppo, tutte le forme figlie seguono automaticamente. Questo è il cuore del **group shapes in word**.

## Passo 3: Aggiungi una forma rettangolare – il codice della forma rettangolare

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape width in points
        rectangleShape.setHeight(50);   // set shape height in points
        groupShape.appendChild(rectangleShape);
```

- **add rectangle shape** – Il costruttore `Shape` riceve `ShapeType.RECTANGLE`, che indica ad Aspose.Words di renderizzare un contorno rettangolare.  
- **set shape size** – `setWidth` e `setHeight` definiscono le **shape dimensions** in punti (1 pt = 1/72 in). Questo è il modo più comune per controllare le dimensioni visive.  
- **Why we use `appendChild`** – Attacca il rettangolo al `GroupShape` in modo che si muova insieme al gruppo.

## Passo 4: Aggiungi un'ellisse e posizionala all'interno del gruppo

```java
        // Step 4: Create an ellipse, set its size and position inside the group, then add it
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);      // set shape width
        ellipseShape.setHeight(80);     // set shape height (making it a circle)
        ellipseShape.setLeft(120);      // position relative to the group container
        groupShape.appendChild(ellipseShape);
```

L'ellisse dimostra **set shape dimensions** oltre un semplice rettangolo. Chiamando `setLeft`, controlli lo spostamento orizzontale all'interno del gruppo, utile quando disponi più oggetti.

## Passo 5: Salva il documento

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

Quando apri *GroupShapeDemo.docx* in Microsoft Word, vedrai un rettangolo e un'ellisse bloccati insieme all'interno di un unico gruppo. Selezionando una delle due forme, verrà selezionato l'intero gruppo—esattamente ciò che ti aspetti quando **group shapes in word**.

## Esempio completo, eseguibile

Mettendo insieme tutti i pezzi, ecco il file sorgente completo che puoi copiare nel tuo IDE:

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will hold the rectangle and ellipse
        GroupShape groupShape = builder.insertGroupShape();

        // Add a rectangle (add rectangle shape) and define its size (set shape size)
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        groupShape.appendChild(rectangleShape);

        // Add an ellipse, set its dimensions, and position it inside the group
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);
        ellipseShape.setHeight(80);
        ellipseShape.setLeft(120);      // horizontal offset relative to the group
        groupShape.appendChild(ellipseShape);

        // Save the document to the local file system
        document.save("GroupShapeDemo.docx");
    }
}
```

### Output previsto

- Un file chiamato **GroupShapeDemo.docx** appare nella cartella del progetto.  
- Aprendo il file in Word si vedono due forme (un rettangolo e un'ellisse) che sono raggruppate insieme.  
- Trascinando una delle forme si sposta l'intero gruppo, confermando che **group shapes in word** funziona come previsto.

## Varianti comuni e casi limite

| Scenario | Cosa cambiare | Perché |
|----------|----------------|-----|
| **Tipi di forma diversi** (es. triangolo) | Usa `ShapeType.TRIANGLE` o qualsiasi altro valore enum quando costruisci `Shape`. | Consente di creare diagrammi più complessi. |
| **Impostare il colore di riempimento** | Chiama `shape.getFillColor().setColor(Color.BLUE);` dopo aver creato la forma. | Migliora l'aspetto visivo senza influire sul raggruppamento. |
| **Ruotare il gruppo** | `groupShape.setRotationAngle(45);` | Ruota tutte le forme figlie insieme, utile per icone. |
| **Aggiungere testo all'interno di una forma** | `shape.appendChild(new Paragraph(document));` poi aggiungi un `Run` con testo. | Fa sì che la forma funzioni come etichetta o callout. |
| **Salvare su uno stream** | `ByteArrayOutputStream out = new ByteArrayOutputStream(); document.save(out, SaveFormat.DOCX);` | Utile per servizi web che restituiscono direttamente il documento. |

### Consiglio professionale

Quando devi **set shape dimensions** in base a dati dinamici (es. la lunghezza di un codice a barre), calcola prima larghezza/altezza in punti:

```java
double inches = 2.5;
int points = (int)(inches * 72); // 1 inch = 72 points
shape.setWidth(points);
```

In questo modo eviti valori hard‑coded e mantieni il codice adattabile.

## Conclusione

Ora sai come **group shapes in Word** usando Java, come **add rectangle shape**, e come **set shape size** e **set shape dimensions** con codice conciso e pronto per la produzione. Seguendo i passaggi sopra, puoi creare gruppi grafici riutilizzabili, inserirli in report automatizzati o costruire strumenti di diagrammazione personalizzati senza mai aprire Word manualmente.

### Cosa fare dopo?

- Esplora le varianti di **add rectangle shape** come gli angoli arrotondati (`ShapeType.RECTANGLE` con `setCornerRadius`).  
- Combina **group shapes in word** con tabelle o grafici per documenti più ricchi.  
- Approfondisci l'API Aspose.Words per **text wrapping** (`shape.setWrapType(WrapType.SQUARE)`) per controllare come il testo circostante interagisce con le tue grafiche raggruppate.

Sentiti libero di sperimentare, adattare il **rectangle shape code**, e condividere i tuoi risultati.

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}