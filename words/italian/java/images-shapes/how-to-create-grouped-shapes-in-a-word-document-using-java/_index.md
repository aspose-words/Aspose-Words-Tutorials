---
category: general
date: 2026-10-13
description: Scopri come creare forme raggruppate in Word con Java. Questa guida ti
  mostra come inserire una forma di gruppo, aggiungere una linea al gruppo e raggruppare
  più forme in tutto il documento.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create grouped shapes
- add line to group
- group multiple shapes word
- insert group shape
language: it
lastmod: 2026-10-13
og_description: Crea forme raggruppate in Word con Java. Segui questo tutorial completo
  per inserire una forma di gruppo, aggiungere una linea al gruppo e raggruppare più
  forme nei documenti Word.
og_image_alt: Screenshot of a Word document showing created grouped shapes
og_title: Crea forme raggruppate in Word con Java – guida passo passo
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to create grouped shapes in Word with Java. This guide shows
    you how to insert group shape, add line to group, and group multiple shapes word‑wide.
  headline: How to create grouped shapes in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Come creare forme raggruppate in un documento Word usando Java
url: /it/java/images-shapes/how-to-create-grouped-shapes-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare forme raggruppate in un documento Word usando Java

Se hai bisogno di **creare forme raggruppate** in un file Microsoft Word da Java, questo tutorial ti guida attraverso l’intero processo. Vedrai come **inserire una forma di gruppo**, posizionare un rettangolo e una linea nello stesso contenitore e, infine, salvare il documento con la grafica raggruppata.

Raggruppare le forme consente di spostare, ridimensionare o formattare più oggetti di disegno come un’unica unità—perfetto per diagrammi, flowchart o decorazioni personalizzate della pagina. Alla fine di questa guida sarai in grado di **aggiungere linea al gruppo**, **raggruppare più forme word** nei documenti e riutilizzare la stessa tecnica per qualsiasi numero di forme.

## Prerequisiti

- Java 17 o versioni successive installate sulla tua macchina di sviluppo.  
- Una licenza di Aspose.Words for Java (o una valutazione gratuita).  
- Un progetto Maven o Gradle dove poter aggiungere la dipendenza Aspose.Words:

```xml
<!-- Maven example -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

Non sono necessarie librerie aggiuntive.

## Passo 1: Inserire il contenitore della forma di gruppo

Il primo passo è **inserire una forma di gruppo** nel documento. Questo contenitore conterrà tutte le forme successive.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // The rest of the code will add shapes to this group
```

`builder.insertGroupShape()` crea un oggetto `Shape` vuoto di tipo `GROUPSHAPE`. Pensalo come una tela trasparente che può contenere altri oggetti di disegno.

## Passo 2: Aggiungere un rettangolo al gruppo

Un rettangolo spesso funge da sfondo visivo per un gruppo di forme.

```java
        // Create a rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        rectangleShape.setLeft(0);      // X‑coordinate inside the group
        rectangleShape.setTop(0);       // Y‑coordinate inside the group

        // Append the rectangle to the group container
        groupShape.appendChild(rectangleShape);
```

Impostare `Left` e `Top` a `0` posiziona il rettangolo nell’angolo in alto a sinistra del gruppo. Puoi modificare questi valori per spostare la forma all’interno del gruppo.

## Passo 3: **Aggiungere linea al gruppo** – creare una forma linea

Ora **aggiungiamo linea al gruppo**. La linea apparirà sotto il rettangolo.

```java
        // Create a line shape
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);   // length of the line
        lineShape.setTop(60);      // vertical position (60 points down)

        // Append the line to the same group
        groupShape.appendChild(lineShape);
```

La proprietà `Top` sposta la linea di 60 punti sotto il rettangolo, creando un layout semplice impilato. Puoi anche impostare `Left` se ti serve uno spostamento orizzontale.

## Passo 4: Salvare il documento con le forme raggruppate

```java
        // Save the document to a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

Quando apri `GroupShapeDemo.docx` in Microsoft Word, vedrai un unico gruppo che contiene sia il rettangolo sia la linea. Selezionare il gruppo ti permette di spostare entrambe le forme insieme, dimostrando che hai **raggruppato più forme word** con successo.

## Esempio completo, eseguibile

Di seguito il programma completo con tutti gli import e la gestione degli errori. Copialo nel tuo IDE, sostituisci `YOUR_DIRECTORY` con un percorso di cartella esistente e avvialo.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // Step 3: Add a rectangle to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);
        rectangleShape.setHeight(50);
        rectangleShape.setLeft(0);
        rectangleShape.setTop(0);
        groupShape.appendChild(rectangleShape);

        // Step 4: Add a line to the group
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);
        lineShape.setTop(60);
        groupShape.appendChild(lineShape);

        // Step 5: Save the document
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

### Output previsto

- Un file chiamato `GroupShapeDemo.docx` appare nella cartella di destinazione.  
- Aprendo il file in Word si vede un unico oggetto raggruppato contenente un rettangolo in alto e una linea sotto.  
- Trascinando il gruppo, entrambe le forme si muovono insieme, confermando che hai **creato forme raggruppate** con successo.

## Consigli e problemi comuni

- **Pro tip:** Se devi ruotare o formattare singole forme all’interno del gruppo, chiama i rispettivi setter (`setRotation`, `getFill().setForeColor`, ecc.) prima di aggiungerle al gruppo. Il gruppo manterrà queste proprietà visive.  
- **Attenzione a:** Dimenticare di impostare la proprietà `Top` per la linea può farla sovrapporre al rettangolo, rendendo il gruppo ingombrante.  
- **Caso limite:** Quando aggiungi più di due forme, ricorda che le coordinate di ciascun figlio sono relative all’origine del gruppo (0,0). Pianifica il layout di conseguenza.  
- **Nota sulle prestazioni:** Raggruppare un gran numero di forme (centinaia) può aumentare leggermente la dimensione del file, ma semplifica le modifiche successive in Word.

## Come **raggruppare più forme word** nei documenti programmaticamente

Il modello mostrato sopra—creare un contenitore di gruppo, configurare ogni forma figlia e aggiungerla—funziona per qualsiasi numero di forme: cerchi, immagini, caselle di testo, ecc. Basta ripetere i passaggi “creare forma → impostare proprietà → aggiungere” prima di chiamare `doc.save()`.

Se devi **aggiungere linea al gruppo** dopo che il gruppo contiene già altre forme, puoi recuperare il gruppo esistente con:

```java
Shape existingGroup = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                                 .stream()
                                 .filter(s -> ((Shape) s).getShapeType() == ShapeType.GROUPSHAPE)
                                 .findFirst()
                                 .orElseThrow(() -> new IllegalStateException("No group found"));
existingGroup.appendChild(lineShape);
```

Questo dimostra che è possibile modificare un gruppo in qualsiasi momento del ciclo di vita del documento.

## Conclusione

Ora sai come **creare forme raggruppate** in un documento Word usando Java e Aspose.Words. Inserendo una **forma di gruppo**, **aggiungendo linea al gruppo** e **raggruppando più forme word**, puoi costruire disegni complessi che si comportano come un unico oggetto—ideale per diagrammi, modelli e generazione automatica di report.

Prosegui esplorando questi argomenti correlati:

- **Applicare stili alle forme raggruppate** – impara a impostare colori di riempimento, bordi ed effetti per tutti i figli contemporaneamente.  
- **Esportare forme raggruppate in PDF** – scopri come lo stesso gruppo viene mantenuto quando converti il documento.  
- **Animare le forme con VBA** – combina i gruppi generati in Java con macro Word per documenti interattivi.

Sentiti libero di sperimentare con diversi tipi di forma, dimensioni e posizioni. Il raggruppamento ti offre la flessibilità di trattare molti oggetti come uno solo, semplificando sia il codice sia l’interazione dell’utente. Buona programmazione!

## Cosa dovresti imparare dopo?


I tutorial seguenti coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell’API ed esplorare approcci alternativi nei tuoi progetti.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}