---
category: general
date: 2026-09-24
description: Scopri come creare un documento Word vuoto in Java e raggruppare forme
  come rettangoli e linee usando Aspose.Words. Include codice passo‑passo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shapes
- add rectangle shape
- group shapes in word
- set shape size
language: it
lastmod: 2026-09-24
og_description: Crea un documento Word vuoto in Java e impara come raggruppare le
  forme, aggiungere una forma rettangolare e impostare le dimensioni della forma con
  Aspose.Words.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Crea un documento Word vuoto e raggruppa le forme in Java – guida passo
  passo
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create a blank Word document in Java and group shapes
    like rectangles and lines using Aspose.Words. Includes step‑by‑step code.
  headline: How to create a blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Come creare un documento Word vuoto e raggruppare le forme in Java
url: /it/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un documento Word vuoto e raggruppare forme in Java

Se hai bisogno di **creare un documento Word vuoto** e poi organizzare più oggetti di disegno, questa guida ti mostra esattamente come fare. Utilizzando Aspose.Words per Java puoi inserire una forma di gruppo, aggiungere una forma rettangolare, disegnare una linea e controllare la dimensione e la posizione di ogni forma—tutto in un unico programma eseguibile.

Seguirai ogni passaggio, dall'inizializzazione del documento al salvataggio del `.docx` finale. Alla fine comprenderai **come raggruppare forme**, **aggiungere una forma rettangolare** e **impostare la dimensione della forma** in modo che i tuoi file Word appaiano esattamente come previsto.

## Prerequisiti

- Java 17 o successivo (il codice si compila con qualsiasi JDK recente)
- Libreria Aspose.Words per Java (scarica dal [sito Aspose](https://products.aspose.com/words/java))
- Un IDE o uno strumento di build (Maven/Gradle) che possa aggiungere il JAR di Aspose.Words al classpath
- Conoscenza di base della sintassi Java

> **Suggerimento professionale:** Usa Maven per la gestione delle dipendenze; aggiungi `com.aspose:aspose-words:23.12` (o l'ultima versione) al tuo `pom.xml`.

## Passo 1: Creare un documento Word vuoto

Il primo compito è **creare un documento Word vuoto**. Questo ti fornisce una tela pulita su cui potrai inserire forme in seguito.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document document = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Perché è importante:* Un oggetto `Document` rappresenta l'intero file `.docx`. Iniziare con un documento vuoto garantisce che nessuna formattazione nascosta interferisca con le forme che aggiungerai.

## Passo 2: Inserire una forma di gruppo – il contenitore per più oggetti

Una **forma di gruppo** agisce come un contenitore che ti permette di spostare, ridimensionare o ruotare più forme insieme. Questo è il fulcro di **come raggruppare forme** in Word.

```java
        // Insert a group shape of width 300 points and height 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

*Spiegazione:* Il metodo `insertGroupShape` crea un oggetto `GroupShape` e lo posiziona nella posizione corrente del cursore. Tutte le forme successive che `appendChild` a questo gruppo saranno trattate come un'unica unità.

## Passo 3: Aggiungere una forma rettangolare e impostarne le dimensioni

Ora **aggiungiamo una forma rettangolare** al gruppo e **impostiamo con precisione le dimensioni della forma**.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);   // set shape width
        rectangle.setHeight(100.0);  // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Add the rectangle to the group
        group.appendChild(rectangle);
```

*Perché è necessario impostare le dimensioni della forma:* Larghezza e altezza controllano come il rettangolo appare sulla pagina. I metodi `setLeft` e `setTop` posizionano il rettangolo rispetto all'origine del gruppo, fornendoti un controllo di layout pixel‑perfect.

## Passo 4: Aggiungere una forma linea e configurarne le dimensioni

Una linea è un altro oggetto di disegno comune. Applicheremo una logica simile a **add rectangle shape** a una linea, mostrando che gli stessi principi di dimensionamento si applicano.

```java
        // Create a line shape
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);   // line length
        line.setHeight(0.0);    // height is zero for a horizontal line
        line.setLeft(20.0);
        line.setTop(130.0);

        // Add the line to the same group
        group.appendChild(line);
```

*Punto chiave:* Anche se una linea non ha altezza, usi comunque `setWidth` per definire la sua lunghezza. Il posizionamento (`setLeft`, `setTop`) segue lo stesso sistema di coordinate delle altre forme.

## Passo 5: Salvare il documento con le forme raggruppate

Infine, conserva le modifiche salvando il documento. Questo produce un file `.docx` che puoi aprire in Microsoft Word per verificare il risultato.

```java
        // Save the document to disk
        document.save("GroupShapeDemo.docx");
    }
}
```

**Output previsto:** Aprendo `GroupShapeDemo.docx` si vede una pagina vuota contenente un rettangolo e una linea raggruppati. Selezionando una delle forme si seleziona l'intero gruppo, permettendoti di spostarle insieme.

## Domande comuni e gestione dei casi limite

| Question | Answer |
|----------|--------|
| *Posso aggiungere più di due forme al gruppo?* | Sì. Chiama `group.appendChild(yourShape)` per ogni forma aggiuntiva. |
| *E se ho bisogno di un'unità diversa (ad esempio centimetri) per le dimensioni?* | Aspose.Words utilizza i punti (1 punto = 1/72 di pollice). Converti usando `Points = centimeters * 28.3465`. |
| *Il gruppo manterrà il layout quando il documento viene aperto su un altro computer?* | Assolutamente. Tutti i dati di dimensione e posizione sono memorizzati nel file `.docx`, rendendo il layout portabile. |
| *Come faccio a separare le forme in seguito?* | Recupera l'oggetto `GroupShape`, quindi itera su `group.getChildNodes(NodeType.SHAPE, true)` e sposta ogni figlio fuori dal gruppo. |
| *E se devo ruotare l'intero gruppo?* | Usa `group.setRotationAngle(double angleInDegrees)` prima di salvare. |

## Esempio completo, eseguibile

Di seguito trovi il programma completo che puoi copiare‑incollare nel tuo IDE. Include tutti gli import necessari e i commenti.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape (container)
        GroupShape group = builder.insertGroupShape(300.0, 200.0);

        // Step 3: Add a rectangle shape and set its size
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);
        rectangle.setHeight(100.0);
        rectangle.setLeft(20.0);
        rectangle.setTop(20.0);
        group.appendChild(rectangle);

        // Step 4: Add a line shape and configure its dimensions
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);
        line.setHeight(0.0);
        line.setLeft(20.0);
        line.setTop(130.0);
        group.appendChild(line);

        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

Esegui il programma, apri `GroupShapeDemo.docx` in Microsoft Word e vedrai le forme raggruppate esattamente come descritto.

## Conclusione

Ora sai come **creare un documento Word vuoto**, **raggruppare forme in Word**, **aggiungere una forma rettangolare** e **impostare le dimensioni della forma** utilizzando Aspose.Words per Java. Inserendo le forme all'interno di un `GroupShape`, ottieni il pieno controllo sul posizionamento collettivo, sul ridimensionamento e sulla rotazione—perfetto per diagrammi, flowchart o grafiche personalizzate incorporate in report automatizzati.

**Passi successivi:**  
- Esplora **come raggruppare forme** con oggetti più complessi come immagini o caselle di testo.  
- Sperimenta con `setRotationAngle` per ruotare l'intero gruppo.  
- Combina questa tecnica con la stampa unione per generare documenti personalizzati che includono grafiche brandizzate.

Sentiti libero di adattare il codice per i tuoi progetti e condividi i tuoi risultati nei commenti!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea forma rettangolare in Word con Java – Guida completa](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Crea documento Word Java – Aggiungi forma rettangolare con effetto ombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Crea forma di gruppo in documento Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}