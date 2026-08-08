---
category: general
date: 2026-08-07
description: Crea un documento Word vuoto con forme raggruppate in Java usando Aspose.Words.
  Scopri come raggruppare le forme, impostare le dimensioni delle forme e aggiungere
  forme a Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shape
- group shapes word
- set shape size
- add shapes to word
language: it
lastmod: 2026-08-07
og_description: Crea un documento Word vuoto con forme raggruppate in Java. Segui
  questa guida per impostare le dimensioni delle forme, aggiungere forme a Word e
  imparare a raggruppare le forme.
og_image_alt: Create blank Word document with grouped shapes using Aspose.Words for
  Java
og_title: Crea un documento Word vuoto con forme raggruppate – tutorial Java
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create blank Word document with grouped shapes in Java using Aspose.Words.
    Learn how to group shape, set shape size, and add shapes to Word.
  headline: Create blank Word document with grouped shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word Automation
- Shapes
title: Crea un documento Word vuoto con forme raggruppate in Java
url: /it/java/images-shapes/create-blank-word-document-with-grouped-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea un documento Word vuoto con forme raggruppate in Java

Se hai bisogno di **creare un documento Word vuoto** che contenga diverse forme disposte come un’unica unità, questo tutorial ti mostra esattamente come fare. Vedrai un esempio completo e eseguibile che dimostra **come raggruppare oggetti shape**, regolare le loro dimensioni e **aggiungere forme a Word** usando Aspose.Words per Java.

La guida percorre ogni passaggio—dalla configurazione del progetto al salvataggio del file .docx finale—così potrai copiare il codice direttamente nella tua applicazione. Non sono necessari riferimenti esterni e la soluzione funziona con Aspose.Words 23.9 o versioni successive.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* Java 17 (o qualsiasi JDK supportato)
* Maven o Gradle per la gestione delle dipendenze
* Una licenza Aspose.Words per Java (o una chiave di valutazione temporanea)
* Un file immagine di esempio (ad es. `sample.jpg`) posizionato in una directory nota

Se manca uno di questi elementi, installalo prima; il resto del tutorial presume che l’ambiente sia pronto.

## Passo 1: Aggiungi Aspose.Words al tuo progetto

Aggiungi la dipendenza Aspose.Words al tuo `pom.xml` (Maven) o `build.gradle` (Gradle). Questa libreria fornisce le classi `Document`, `DocumentBuilder`, `GroupShape` e `Shape` utilizzate più avanti.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:23.9'
```

**Perché è importante:** senza la libreria, nessuna delle API di elaborazione Word è disponibile e non puoi **creare un documento Word vuoto** programmaticamente.

## Passo 2: Crea un documento Word vuoto

La prima azione concreta è istanziare un oggetto `Document`, che rappresenta un **documento Word vuoto** in memoria.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new, empty document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*`Document()`* crea un **documento Word vuoto** con impostazioni predefinite (pagina A4, margini di default). Il relativo `DocumentBuilder` ti consente di inserire contenuti nella posizione corrente del cursore.

## Passo 3: Inserisci una forma di gruppo (come raggruppare le forme)

Una *forma di gruppo* funge da contenitore per altre forme. In questo passaggio imparerai **come raggruppare le forme** in modo che si muovano insieme.

```java
        // Insert a group shape with a width of 300 points and height of 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

Il metodo `insertGroupShape` posiziona il contenitore nella posizione del cursore del builder. Il raggruppamento è essenziale quando vuoi trattare più disegni come un’unica entità—questo è il nucleo della funzionalità **group shapes word**.

## Passo 4: Crea un rettangolo e imposta la sua dimensione

Ora aggiungi un rettangolo al gruppo. Questo dimostra **impostare la dimensione della forma**, necessario per un layout preciso.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // set shape width
        rectangle.setHeight(50.0);   // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Append rectangle to the group
        group.appendChild(rectangle);
```

*Perché impostare le dimensioni?* Chiamare esplicitamente `setWidth` e `setHeight` garantisce che il rettangolo appaia esattamente come previsto, indipendentemente dagli stili di forma predefiniti del documento.

## Passo 5: Inserisci un’immagine e aggiungila al gruppo

L’inserimento di un’immagine mostra un altro caso d’uso comune per **add shapes to word**. L’immagine diventa parte dello stesso gruppo, muovendosi insieme al rettangolo.

```java
        // Insert an image at the current cursor position
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        picture.setLeft(150.0);   // position inside the group
        picture.setTop(30.0);     // position inside the group

        // Append picture to the group
        group.appendChild(picture);
```

Se il file immagine è mancante, Aspose.Words genera un’eccezione. Un suggerimento pratico è verificare il percorso in anticipo:

```java
        File imgFile = new File("YOUR_DIRECTORY/sample.jpg");
        if (!imgFile.exists()) {
            throw new IllegalArgumentException("Image file not found: " + imgFile.getAbsolutePath());
        }
```

## Passo 6: Salva il documento contenente le forme raggruppate

Infine, persisti il **documento Word vuoto** (ora popolato con una forma di gruppo) su disco.

```java
        // Save the document as a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

Quando apri `GroupShapeDemo.docx` in Microsoft Word, vedrai un unico oggetto raggruppato che contiene un rettangolo e un’immagine. Selezionando qualsiasi parte del gruppo, l’intero contenitore si sposta, confermando che le forme sono state correttamente **raggruppate**.

### Output previsto

* Un file chiamato `GroupShapeDemo.docx` nella directory specificata.
* L’apertura del file mostra un contenitore di 300 × 200 punti con:
  * Un rettangolo di 100 × 50 punti posizionato a (20, 20).
  * Un’immagine posizionata a (150, 30) all’interno dello stesso contenitore.

## Casi limite e variazioni

| Situazione | Come gestirla |
|------------|---------------|
| **Dimensione pagina diversa** | Chiama `doc.getFirstSection().getPageSetup().setPaperSize(PaperSize.A5);` prima di inserire il gruppo. |
| **Gruppi multipli** | Ripeti i passi 3‑5 con una nuova istanza `GroupShape`; ogni gruppo può essere posizionato indipendentemente. |
| **Rotazione delle forme** | Usa `shape.setRotationAngle(45.0);` per ruotare un rettangolo o un’immagine prima di aggiungerlo al gruppo. |
| **Forme non‑immagine** | Crea oggetti `Shape` di tipo `ShapeType.ELLIPSE`, `ShapeType.LINE`, ecc., e aggiungili come il rettangolo. |
| **Immagini di grandi dimensioni** | Scala l’immagine con `picture.setWidth(80.0); picture.setHeight(60.0);` per mantenere il gruppo entro i suoi limiti originali. |

Queste variazioni ti consentono di adattare il modello di base a una vasta gamma di scenari di generazione di documenti.

## Consigli pratici dall’esperienza

* **Pro tip:** Imposta `RelativeHorizontalPosition` e `RelativeVerticalPosition` del gruppo su `RelativeHorizontalPosition.PAGE` e `RelativeVerticalPosition.PAGE` se vuoi che il gruppo rimanga ancorato alla pagina anziché al cursore.
* **Attenzione a:** Aggiungere una forma che supera le dimensioni del gruppo; la forma verrà tagliata in Word. Regola la dimensione del gruppo con `group.setWidth()` e `group.setHeight()` di conseguenza.
* **Nota sulle prestazioni:** Se generi molti documenti in un ciclo, riutilizza un’unica istanza `DocumentBuilder` e chiama `doc.clone()` per ridurre l’overhead di creazione degli oggetti.

## Conclusione

Ora sai come **creare un documento Word vuoto** che contenga una collezione raggruppata di forme usando Aspose.Words per Java. Il tutorial ha coperto l’intero flusso di lavoro: impostare la libreria, creare il documento, inserire un gruppo, **impostare la dimensione della forma**, **add shapes to word**, e salvare il risultato.

Da qui puoi esplorare funzionalità più avanzate come il raggruppamento di grafici, l’applicazione di stili a forme individuali o l’esportazione del documento in PDF. Ognuno di questi argomenti si basa sugli stessi principi dimostrati in questa guida.

---


## Cosa dovresti imparare dopo?


I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell’API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}