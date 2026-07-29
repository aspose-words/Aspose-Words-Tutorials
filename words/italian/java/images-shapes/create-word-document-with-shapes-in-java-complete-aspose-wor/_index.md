---
category: general
date: 2026-07-29
description: Crea un documento Word in Java usando Aspose.Words. Impara a inserire
  una forma rettangolare, raggruppare le forme in Word e salvare rapidamente il documento
  come docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
- add shapes to word
language: it
lastmod: 2026-07-29
og_description: Crea un documento Word in Java con Aspose.Words. Inserisci una forma
  rettangolare, raggruppa le forme in Word e salva il documento come docx in pochi
  minuti.
og_image_alt: Screenshot showing how to create word document with grouped shapes using
  Java
og_title: Crea documento Word con forme – Tutorial Java Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  headline: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  name: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  steps:
  - name: '## Create Word Document with Shapes Using Aspose.Words'
    text: The first thing you need is an empty Word file to work with. Aspose.Words
      makes this a one‑liner.
  - name: '## Insert Rectangle Shape and Other Shapes'
    text: Now we’ll add a blue rectangle and a green ellipse. The rectangle demonstrates
      the **insert rectangle shape** keyword, while the ellipse shows that you can
      mix shape types freely.
  - name: '## Group Shapes in Word for Easy Manipulation'
    text: Having two separate objects is fine, but often you want to move them together.
      That’s where **group shapes in word** shines.
  - name: '## Save Document as DOCX and Verify Output'
    text: Finally, we persist the file. This step fulfills the **save document as
      docx** requirement.
  - name: '## Full Working Example and Common Pitfalls'
    text: Below is the complete, ready‑to‑run Java class. Copy‑paste it into your
      project, adjust the output folder, and hit *Run*.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Crea documento Word con forme in Java – Guida completa ad Aspose.Words
url: /it/java/images-shapes/create-word-document-with-shapes-in-java-complete-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea documento Word con forme in Java – Guida completa Aspose.Words

Ti sei mai chiesto come **create word document** in modo programmatico e arricchirlo con grafiche personalizzate? Non sei l’unico. Che tu debba generare un report con sezioni evidenziate o progettare un volantino al volo, padroneggiare la gestione delle forme in Word può farti risparmiare ore di lavoro manuale.

In questo tutorial percorreremo passo passo le istruzioni per **create word document** usando Aspose.Words per Java, **insert rectangle shape**, **group shapes in Word**, e infine **save document as docx**. Alla fine avrai un esempio completamente eseguibile da inserire in qualsiasi progetto.

## Cosa imparerai

- Un nuovo file Word generato interamente da codice Java.  
- Due forme distinte (un rettangolo e un’ellisse) aggiunte alla pagina.  
- Quelle forme raggruppate insieme con l’API **group shapes in word**, facendole comportare come un unico oggetto.  
- Il file salvato su disco come un normale `.docx` che si apre in Microsoft Word senza problemi.  

Nessuno strumento esterno, nessun trucco XML complicato—solo Java tipizzato pulito e Aspose.Words.

---

## Prerequisiti

Prima di iniziare, assicurati di avere:

1. **Java Development Kit (JDK) 8 o superiore** – il codice è destinato a Java 8+.  
2. **Aspose.Words for Java** JAR (puoi scaricare l’ultima versione dal repository Maven Central).  
3. Un IDE modesto (IntelliJ IDEA, Eclipse, o anche un semplice editor di testo).  

Se hai tutto questo, ottimo—iniziamo.

---

## Implementazione passo‑passo

Di seguito suddividiamo il processo in passaggi di dimensioni gestibili. Ogni passaggio include uno snippet di codice, una breve spiegazione e un suggerimento che potresti non trovare nella documentazione ufficiale.

### ## Create Word Document with Shapes Using Aspose.Words

La prima cosa di cui hai bisogno è un file Word vuoto su cui lavorare. Aspose.Words lo rende un’operazione a una riga.

```java
// Step 1: Initialise a blank document and a DocumentBuilder
Document doc = new Document();                 // Represents the Word file
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Perché è importante:**  
`Document` è il contenitore di tutto—testo, tabelle, immagini e forme. `DocumentBuilder` è l’assistente amichevole che ti permette di aggiungere contenuti senza dover gestire oggetti a basso livello. Pensalo come una penna che scrive direttamente sulla pagina.

> **Pro tip:** Se prevedi di partire da un modello (ad esempio, la carta intestata aziendale), sostituisci `new Document()` con `new Document("template.docx")`.

### ## Insert Rectangle Shape and Other Shapes

Ora aggiungeremo un rettangolo blu e un’ellisse verde. Il rettangolo dimostra la keyword **insert rectangle shape**, mentre l’ellisse mostra che puoi mescolare liberamente i tipi di forma.

```java
// Step 2: Insert a rectangle shape (100x50 points) and set its appearance
Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
rect.setLeft(50);                               // X‑coordinate in points
rect.setTop(50);                                // Y‑coordinate in points
rect.getFill().setColor(java.awt.Color.BLUE);  // Fill color

// Step 3: Insert an ellipse shape (80x80 points) and configure it
Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
ellipse.setLeft(180);
ellipse.setTop(30);
ellipse.getFill().setColor(java.awt.Color.GREEN);
```

**Cosa succede dietro le quinte?**  
Ogni chiamata a `insertShape` crea un oggetto `Shape` e lo aggiunge automaticamente al paragrafo corrente. I metodi `setLeft`/`setTop` posizionano la forma rispetto ai margini della pagina, misurati in punti (1 pt = 1/72 in). Modificando questi numeri puoi collocare le forme dove preferisci.

> **Domanda comune:** *Posso aggiungere un’immagine invece di un colore solido?*  
> Assolutamente—basta sostituire il colore di riempimento con un’immagine usando `shape.getFill().setImage("path/to/image.png")`.

### ## Group Shapes in Word for Easy Manipulation

Avere due oggetti separati va bene, ma spesso vuoi spostarli insieme. È qui che **group shapes in word** brilla.

```java
// Step 4: Create a GroupShape container and add the two shapes
GroupShape group = builder.insertGroupShape(); // Starts an empty group
group.appendChild(rect);
group.appendChild(ellipse);

// Step 5: Reposition the whole group as a single entity
group.setLeft(100);
group.setTop(150);
```

**Perché raggruppare?**  
Quando le forme sono raggruppate, qualsiasi trasformazione—spostamento, rotazione, ridimensionamento—si applica all’intera collezione. Questo replica il comportamento che ottieni quando selezioni manualmente più forme nell’interfaccia di Word e premi *Group*. Inoltre semplifica il codice successivo perché devi modificare un solo oggetto invece di molti.

> **Caso limite:** Se in seguito devi separare il gruppo, chiama `group.getParentNode().removeChild(group)` e reinserisci i figli singolarmente.

### ## Save Document as DOCX and Verify Output

Infine, persistenza del file. Questo passaggio soddisfa il requisito **save document as docx**.

```java
// Step 6: Write the document to disk as a .docx file
String outputPath = "output/GroupShapeExample.docx";
doc.save(outputPath, SaveFormat.DOCX);
System.out.println("Document saved successfully to " + outputPath);
```

**Cosa aspettarsi:**  
Apri il file generato `GroupShapeExample.docx` in Microsoft Word. Vedrai un rettangolo blu e un’ellisse verde, ordinatamente raggruppati. Trascina il gruppo—entrambe le forme si muovono insieme, proprio come ti aspetteresti dall’interfaccia.

> **Suggerimento:** Usa `SaveFormat.PDF` se ti serve una versione PDF; lo stesso codice funziona senza modifiche.

### ## Full Working Example and Common Pitfalls

Di seguito trovi la classe Java completa, pronta per l’esecuzione. Copiala nel tuo progetto, regola la cartella di output e premi *Run*.

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle shape and set its position and fill color
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rect.setLeft(50);
        rect.setTop(50);
        rect.getFill().setColor(java.awt.Color.BLUE);

        // Step 3: Insert a second ellipse shape and configure its position and fill color
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
        ellipse.setLeft(180);
        ellipse.setTop(30);
        ellipse.getFill().setColor(java.awt.Color.GREEN);

        // Step 4: Group the two shapes together using the new GroupShape API
        GroupShape group = builder.insertGroupShape();
        group.appendChild(rect);
        group.appendChild(ellipse);

        // Step 5: Optionally reposition the entire group as a single object
        group.setLeft(100);
        group.setTop(150);

        // Step 6: Save the document containing the grouped shapes
        String outPath = "output/GroupShapeExample.docx";
        doc.save(outPath, SaveFormat.DOCX);
        System.out.println("Document saved successfully to " + outPath);
    }
}
```

#### Problemi comuni e come evitarli

| Problema | Perché accade | Soluzione |
|----------|---------------|-----------|
| **`NullPointerException` su `builder`** | Dimenticare di istanziare `DocumentBuilder` dopo aver creato `Document`. | Assicurati che `new DocumentBuilder(doc)` venga eseguito prima di inserire qualsiasi forma. |
| **Le forme appaiono fuori pagina** | Uso di valori in pixel anziché in punti, o mancata considerazione dei margini. | Ricorda che Aspose.Words si aspetta punti; 72 pt = 1 in. Regola `setLeft`/`setTop` di conseguenza. |
| **Il gruppo scompare dopo il salvataggio** | Aggiunta di forme al gruppo *dopo* che il gruppo è stato salvato. | Raggruppa sempre prima di chiamare `doc.save()`. |
| **File non trovato al salvataggio** | La directory di output non esiste. | Crea la directory programmaticamente (`new File("output").mkdirs();`) o utilizza un percorso esistente. |

---

## Conclusione

Abbiamo appena **create word document** da zero, **add shapes to word**, **insert rectangle shape**, **group shapes in word**, e infine **save document as docx**—tutto con poche righe di Java. La potenza di Aspose.Words risiede nel suo modello di oggetti chiaro; puoi trattare un file Word come una tela, dipingere su di essa con forme e poi esportarlo dove ti serve.

Ti senti avventuroso? Prova a sostituire il rettangolo con una stella, aggiungi testo all’interno delle forme usando `Shape.getTextBox()`, o sperimenta la rotazione (`shape.setRotationAngle(45)`). L’API è ricca e le possibilità praticamente infinite.

Hai domande su scenari più avanzati—come collegare forme a segnalibri o esportare in PDF con font incorporati? Lascia un commento qui sotto e approfondiremo insieme. Buon coding!

## What Should You Learn Next?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell’API e a esplorare approcci alternativi nei tuoi progetti.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}