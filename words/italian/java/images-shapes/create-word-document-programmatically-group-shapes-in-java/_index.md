---
category: general
date: 2026-09-21
description: Crea un documento Word programmaticamente usando Java. Impara come raggruppare
  le forme in Word, inserire una forma rettangolare, impostare le dimensioni della
  forma e aggiungere forme a un documento Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to group shapes in word
- how to insert rectangle shape
- add shapes to word document
- set shape size word
language: it
lastmod: 2026-09-21
og_description: 'Crea un documento Word programmaticamente con Java: questa guida
  mostra come raggruppare le forme in Word, inserire forme rettangolari, impostare
  le dimensioni delle forme e aggiungere forme a un documento Word.'
og_image_alt: Screenshot of a Java program creating a Word document with grouped shapes
og_title: Crea un documento Word programmaticamente, raggruppa le forme in Java
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically using Java. Learn how to group
    shapes in Word, insert a rectangle shape, set shape size, and add shapes to a
    Word document.
  headline: Create word document programmatically, group shapes in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Word automation
- Shapes
title: Crea un documento Word programmaticamente, raggruppa le forme in Java
url: /it/java/images-shapes/create-word-document-programmatically-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea documento Word programmaticamente, raggruppa forme in Java

Se hai bisogno di **creare un documento Word programmaticamente**, questa guida ti accompagna passo passo verso una soluzione completa. Vedrai come **raggruppare forme in Word**, inserire un rettangolo, impostarne le dimensioni e aggiungere altre forme—tutto usando Java e la libreria Aspose.Words per Java.

Il tutorial copre ogni fase, dalla configurazione del progetto al salvataggio del file .docx finale. Alla fine sarai in grado di generare un documento Word che contiene un rettangolo e un'immagine avvolti all'interno di un unico gruppo, rendendo facile spostarli o ridimensionarli insieme. Non è necessaria alcuna esperienza pregressa con l'API Aspose.Words, ma dovresti avere un ambiente di sviluppo Java di base.

## Prerequisiti

* Java Development Kit (JDK) 8 o più recente  
* Maven o Gradle per la gestione delle dipendenze  
* Aspose.Words per Java 23.9 (o l'ultima versione) – la libreria è gratuita per la valutazione  
* Un file immagine (ad es., `sample.jpg`) collocato in una directory nota  

Avere questi elementi pronti garantisce che il codice venga eseguito senza configurazioni aggiuntive.

## Passo 1: Configura il progetto e importa Aspose.Words

Crea un progetto Maven (o aggiungi la dipendenza al tuo `pom.xml` esistente):

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Se preferisci Gradle, aggiungi quanto segue a `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:23.9'
```

Dopo che la dipendenza è stata risolta, importa le classi necessarie nel tuo file sorgente Java:

```java
import com.aspose.words.*;
import java.io.File;
```

## Passo 2: Crea il documento Word programmaticamente

La prima operazione in qualsiasi scenario di automazione è istanziare un oggetto `Document` e un `DocumentBuilder`. Il builder semplifica l'inserimento di testo, immagini e forme.

```java
public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

A questo punto il documento esiste solo in memoria. Ora puoi iniziare ad aggiungere forme.

## Passo 3: Inserisci una forma rettangolare – come inserire una forma rettangolare

Un rettangolo è una `Shape` di base con `ShapeType.RECTANGLE`. Controlli le sue dimensioni con `setWidth`, `setHeight` e la posizioni con `setTop` e `setLeft`.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);
        rectangle.setTop(10.0);
        rectangle.setLeft(10.0);

        // Optional: give the rectangle a visible fill and line color
        rectangle.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
        rectangle.getStrokeColor().setColor(java.awt.Color.DARK_GRAY);
```

**Perché è importante:** Impostare esplicitamente dimensione e posizione (`set shape size word`) garantisce che il rettangolo appaia esattamente dove ti aspetti, indipendentemente dal layout predefinito del documento.

## Passo 4: Inserisci un'immagine – aggiungi forme al documento Word

Il `DocumentBuilder` può inserire un'immagine direttamente da un percorso file. Dopo l'inserimento, puoi riposizionare l'immagine proprio come qualsiasi altra forma.

```java
        // Insert an image; replace the path with your own image location
        String imagePath = "YOUR_DIRECTORY/sample.jpg";
        if (!new File(imagePath).exists()) {
            throw new IllegalArgumentException("Image file not found: " + imagePath);
        }
        Shape picture = builder.insertImage(imagePath);
        picture.setTop(70.0);
        picture.setLeft(10.0);
```

Sia il rettangolo sia l'immagine sono ora forme indipendenti all'interno del documento.

## Passo 5: Raggruppa le forme – come raggruppare forme in Word

Raggruppare le forme è utile quando desideri spostarle o ridimensionarle come un'unica unità. Aspose.Words fornisce un contenitore `GroupShape` a questo scopo.

```java
        // Create a GroupShape that will contain the rectangle and the picture
        GroupShape group = builder.insertGroupShape();

        // Append the rectangle and picture to the group
        group.appendChild(rectangle);
        group.appendChild(picture);
```

Quando il gruppo viene salvato, Word tratta i due figli come un unico oggetto logico. Potrai successivamente selezionare il gruppo e trascinarlo, e sia il rettangolo sia l'immagine seguiranno il movimento.

## Passo 6: Salva il documento

Infine, scrivi il documento su disco. Il percorso deve essere scrivibile dal processo Java.

```java
        // Save the document with the grouped shapes
        String outputPath = "YOUR_DIRECTORY/GroupShapeExample.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Eseguendo il metodo `main` viene generato un file chiamato **GroupShapeExample.docx**. Aprilo in Microsoft Word per vedere un rettangolo e un'immagine bloccati insieme all'interno di un gruppo. Selezionando il gruppo potrai muovere entrambi gli oggetti simultaneamente, confermando che il raggruppamento è riuscito.

## Output previsto

* Un file Word (`GroupShapeExample.docx`) situato nella directory che hai specificato.  
* All'interno del file, un rettangolo (riempimento grigio chiaro) appare nell'angolo in alto a sinistra, e l'immagine si trova subito sotto di esso.  
* Entrambi gli oggetti fanno parte di un unico gruppo, quindi trascinando uno si muove anche l'altro.

## Varianti comuni e casi limite

| Situazione | Raccomandazione |
|------------|-----------------|
| **Different image formats** | Aspose.Words supports PNG, BMP, GIF, and TIFF. Use the appropriate file extension in `insertImage`. |
| **Negative dimensions** | The API throws `ArgumentException`. Always validate width and height before calling `setWidth` / `setHeight`. |
| **Large documents** | Grouping many shapes can increase file size. Consider merging shapes into a single picture when performance matters. |
| **Word version compatibility** | GroupShape works with Word 2007 (`.docx`) and later. For older `.doc` files, the group will be flattened. |
| **Dynamic positioning** | Use calculations based on page size (`doc.getFirstSection().getPageSetup().getPageWidth()`) if you need adaptive placement. |

**Consiglio professionale:** After creating the group, you can change

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}