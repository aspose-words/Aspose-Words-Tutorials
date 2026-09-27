---
category: general
date: 2026-09-27
description: Crea un documento Word vuoto in Java e raggruppa le forme usando Aspose.Words.
  Impara a impostare la dimensione della forma, il colore di riempimento della forma
  e ad aggiungere un figlio al gruppo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- set shape size
- set shape fill color
- append child to group
language: it
lastmod: 2026-09-27
og_description: Crea un documento Word vuoto in Java con Aspose.Words. Questo tutorial
  mostra come raggruppare le forme in Word, impostare le dimensioni della forma, impostare
  il colore di riempimento della forma e aggiungere un figlio al gruppo.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Crea un documento Word vuoto e raggruppa le forme in Java – guida passo
  passo
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create a blank Word document in Java and group shapes using Aspose.Words.
    Learn to set shape size, set shape fill color, and append child to group.
  headline: How to create blank word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Come creare un documento Word vuoto e raggruppare le forme in Java
url: /it/java/images-shapes/how-to-create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un documento Word vuoto e raggruppare forme in Java

Se hai bisogno di **creare un documento Word vuoto** programmaticamente, questa guida ti mostra esattamente come farlo con Aspose.Words per Java. Imparerai anche a **raggruppare forme in Word**, impostare la dimensione di ciascuna forma, applicare un colore di riempimento e **aggiungere un figlio al gruppo** in modo che gli oggetti si comportino come un’unica unità.

Lavorare con i file Word dal codice ti evita la formattazione manuale e ti consente di generare report, contratti o brochure di marketing automaticamente. Alla fine di questo tutorial avrai un programma Java eseguibile che produce un file `.docx` contenente un rettangolo blu e un'immagine, entrambi raggruppati insieme.

## Prerequisiti

Prima di iniziare, assicurati di avere:

- Java 17 (o qualsiasi JDK recente) installato.
- Maven o Gradle per gestire le dipendenze.
- Una licenza Aspose.Words per Java (la valutazione gratuita è sufficiente per i test).
- Un file immagine di esempio (ad es., `sample.jpg`) posizionato in una cartella a cui puoi fare riferimento dal codice.

> **Suggerimento:** Conserva i file immagine in una directory `resources` e caricali con `ClassLoader.getResourceAsStream` per evitare percorsi assoluti hard‑coded.

## Passo 1: Creare un documento Word vuoto e aggiungere un GroupShape

Il primo passo è istanziare un nuovo oggetto `Document`, che rappresenta un file Word vuoto, e quindi inserire un `GroupShape`. Il gruppo servirà da contenitore per tutte le forme che aggiungerai in seguito.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();                     // create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape();     // group shapes in word
```

*Perché è importante:* Un `GroupShape` ti consente di spostare, ruotare o formattare più forme insieme, il che è essenziale per layout complessi come diagrammi o filigrane.

## Passo 2: Inserire un rettangolo e **impostare la dimensione della forma**

Successivamente, crea un rettangolo, definisci le sue dimensioni e aggiungilo al gruppo. Questo dimostra l'operazione **impostare la dimensione della forma**.

```java
        // Step 2: Create a rectangle shape, configure its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);                         // set shape size – width 100 points
        rectangle.setHeight(50.0);                         // set shape size – height 50 points
        rectangle.setFillColor(java.awt.Color.BLUE);      // set shape fill color to blue
        group.appendChild(rectangle);                     // append child to group
```

*Spiegazione:* `setWidth` e `setHeight` controllano la dimensione esatta della forma in punti (1 punto = 1/72 di pollice). Regola questi valori in base alle esigenze del tuo layout.

## Passo 3: **Impostare il colore di riempimento della forma** per il rettangolo

Lo sfondo del rettangolo viene impostato su blu tramite `setFillColor`. Puoi usare qualsiasi costante `java.awt.Color` o creare un colore RGB personalizzato.

```java
        // The fill color was already applied in the previous step.
        // If you need a different color later, just call setFillColor again:
        // rectangle.setFillColor(new java.awt.Color(255, 165, 0)); // orange
```

*Perché è utile:* I colori di riempimento aiutano a distinguere visivamente gli oggetti, soprattutto quando in seguito esporti il documento in PDF o lo stampi.

## Passo 4: Inserire un'immagine e **aggiungere un figlio al gruppo**

Ora aggiungi un'immagine allo stesso `GroupShape`. L'immagine viene inserita tramite `DocumentBuilder.insertImage`, quindi aggiunta al gruppo in modo che si sposti insieme al rettangolo.

```java
        // Step 4: Insert an image and add it to the same group
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        group.appendChild(picture);                       // append child to group
```

*Caso limite:* Se il percorso dell'immagine è errato, Aspose.Words genera una `FileNotFoundException`. Usa un percorso relativo o carica l'immagine dalle risorse per evitare questo problema.

## Passo 5: **Salvare il documento con le forme raggruppate**

Infine, scrivi il documento su disco. Il file risultante conterrà il rettangolo e l'immagine raggruppati insieme.

```java
        // Step 5: Save the document with the grouped shapes
        doc.save("YOUR_DIRECTORY/GroupShape.docx");       // creates the blank word document with grouped shapes
    }
}
```

### Output previsto

- Un file chiamato `GroupShape.docx` appare nella directory specificata.
- Aprendo il file in Microsoft Word si vede una pagina vuota con un rettangolo blu e l'immagine scelta, entrambi selezionati come un unico oggetto (puoi spostarli o ridimensionarli insieme).

![crea documento word vuoto con forme raggruppate](/images/grouped-shapes.png "crea documento word vuoto con forme raggruppate")

*Lo screenshot sopra dimostra le forme finali raggruppate all'interno del nuovo documento Word.*

## Variazioni comuni e consigli aggiuntivi

| Situazione | Come gestirla |
|------------|----------------|
| **Immagini multiple** | Inserisci ogni immagine con `builder.insertImage` e chiama `group.appendChild(picture)` per ciascuna. |
| **Tipi di forma diversi** | Usa `ShapeType.OVAL`, `ShapeType.LINE`, ecc., quando crei l'oggetto `Shape`. |
| **Modificare la posizione del gruppo** | Dopo aver aggiunto tutti i figli, imposta `group.setLeft(x)` e `group.setTop(y)` per spostare l'intero gruppo. |
| **Esportare in PDF** | Chiama `doc.save("output.pdf")` dopo il raggruppamento; il PDF manterrà il raggruppamento. |
| **Applicazione della licenza** | Se utilizzi la versione di valutazione, apparirà una filigrana. Installa una licenza valida per rimuoverla. |

## Conclusione

Ora sai come **creare un documento Word vuoto**, inserire un **GroupShape**, **impostare la dimensione della forma**, **impostare il colore di riempimento della forma** e **aggiungere un figlio al gruppo** usando Aspose.Words per Java. Questo modello ti permette di costruire layout complessi e programmabili che possono essere modificati successivamente in Word o esportati in altri formati.

Successivamente, esplora come **raggruppare forme in Word** con caselle di testo, aggiungere collegamenti ipertestuali alle forme o automatizzare la generazione di report multi‑pagina. Gli stessi principi si applicano: crea forme aggiuntive, configura le loro proprietà e aggiungile allo stesso gruppo.

Buona programmazione!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}