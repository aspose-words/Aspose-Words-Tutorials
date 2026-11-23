---
category: general
date: 2026-11-22
description: Aggiungi una forma rettangolare in un documento Word con Java, imposta
  le dimensioni della forma, raggruppa più forme e aggiungi la forma al gruppo in
  modo efficiente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add rectangle shape
- set shape size
- group multiple shapes
- set shape dimensions
- append shape to group
language: it
lastmod: 2026-11-22
og_description: Aggiungi una forma rettangolare in un documento Word usando Java,
  quindi imposta le dimensioni della forma, raggruppa più forme e aggiungi la forma
  al gruppo in un unico flusso di lavoro.
og_image_alt: Screenshot showing a rectangle shape added and grouped in a Word document
  using Java
og_title: Aggiungi forma rettangolare e raggruppa forme in Java – guida completa
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  headline: Add rectangle shape and group shapes in Java
  type: TechArticle
- description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  name: Add rectangle shape and group shapes in Java
  steps:
  - name: Insert the rectangle shape
    text: The rectangle is the first visual element we want to place inside the document.
      By using the `Shape` constructor with `ShapeType.RECTANGLE`, you get a fully
      editable object.
  - name: Set shape size and dimensions
    text: Set shape size and dimensions
  - name: Create a group shape container
    text: '```java // Step 6: Create a group shape that will hold the rectangle and
      other shapes GroupShape groupShape = builder.insertGroupShape(); ```'
  - name: Append shape to group
    text: Append shape to group
  - name: Save the document
    text: '```java // Save the result to a new file doc.save("output.docx"); } } ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shape manipulation
title: Aggiungi forma rettangolare e raggruppa le forme in Java
url: /it/java/images-shapes/add-rectangle-shape-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aggiungere forma rettangolare e raggruppare forme in Java

Se devi **aggiungere una forma rettangolare** a un documento Word con Java, questa guida ti accompagna passo passo. Imparerai anche come **impostare le dimensioni della forma**, **raggruppare più forme** e **aggiungere una forma al gruppo** senza uscire dall'IDE.

Lavorare con grafica vettoriale all'interno di un file DOCX spesso sembra gestire API separate. Alla fine di questo tutorial avrai un programma autonomo che crea un rettangolo, un'ellisse e qualsiasi altra forma necessaria, quindi le raggruppa affinché si muovano come un unico oggetto. Non sono necessari strumenti esterni oltre a Aspose.Words per Java.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* Java 17 o versioni successive installate.
* Maven 3.8+ (o Gradle) per gestire le dipendenze.
* Una licenza valida di Aspose.Words per Java (la versione di valutazione è sufficiente per i test).
* Un IDE come IntelliJ IDEA o VS Code, anche se qualsiasi editor di testo andrà bene.

Questi requisiti consentono al codice di compilare ed eseguire in qualsiasi ambiente di sviluppo moderno.

## Passo 1: Configurare il progetto Maven

Crea un nuovo progetto Maven o aggiungi la dipendenza Aspose.Words a un `pom.xml` esistente:

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>shape‑demo</artifactId>
  <version>1.0.0</version>

  <dependencies>
    <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.12</version>
    </dependency>
  </dependencies>
</project>
```

La dipendenza scarica tutte le classi necessarie per la manipolazione dei documenti, inclusi `Document`, `DocumentBuilder`, `Shape` e `GroupShape`. Maven scaricherà automaticamente i JAR quando eseguirai `mvn compile`.

## Passo 2: Caricare il documento e creare un DocumentBuilder

Un `DocumentBuilder` fornisce l'API fluida per inserire contenuti. Carica un DOCX esistente o inizia da un documento vuoto:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document or create a new one
        Document doc = new Document("input.docx");          // replace with your path
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Creare il builder in anticipo ti fornisce un cursore posizionato all'inizio del documento, pronto per l'inserimento di forme.

## Aggiungere forma rettangolare a un documento Word

### Passo 3: Inserire la forma rettangolare

Il rettangolo è il primo elemento visivo che vogliamo posizionare nel documento. Utilizzando il costruttore `Shape` con `ShapeType.RECTANGLE`, ottieni un oggetto completamente modificabile.

```java
        // Step 3: Insert a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        // The shape is not yet sized; we will set its dimensions next.
```

Aggiungere il rettangolo a questo punto non influisce sul layout finché non ne definisci le dimensioni e lo aggiungi a un contenitore.

### Impostare dimensioni e misure della forma

#### Passo 4: Definire larghezza e altezza

Impostare le dimensioni della forma determina come appare nella pagina. I valori di larghezza e altezza sono misurati in punti (1 pt = 1/72 in).

```java
        // Step 4: Set shape size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

Puoi regolare questi numeri per soddisfare i requisiti del tuo design. Gli stessi metodi si applicano a qualsiasi istanza di `Shape`, così da poterli riutilizzare per cerchi, frecce o disegni personalizzati.

#### Passo 5: Inserire il rettangolo nel documento

Ora che il rettangolo ha una dimensione, posizionalo nella pagina. Il metodo `insertShape` di `DocumentBuilder` aggiunge la forma nella posizione corrente del cursore.

```java
        // Insert the rectangle at the builder’s current position
        builder.insertShape(rectangle);
```

A questo punto il rettangolo appare da solo nella pagina. I passaggi successivi mostrano come combinarlo con altre forme.

## Raggruppare più forme insieme

Raggruppare le forme consente di spostarle, ruotarle o ridimensionarle come un'unica unità. È particolarmente utile per creare diagrammi complessi.

### Passo 6: Creare un contenitore di gruppo di forme

```java
        // Step 6: Create a group shape that will hold the rectangle and other shapes
        GroupShape groupShape = builder.insertGroupShape();
```

La chiamata `insertGroupShape` aggiunge un contenitore vuoto al documento. Qualsiasi forma aggiunta a questo contenitore diventa parte del gruppo.

### Aggiungere forma al gruppo

#### Passo 7: Aggiungere il rettangolo al gruppo

```java
        // Append the previously created rectangle to the group
        groupShape.appendChild(rectangle);
```

L'aggiunta sposta il rettangolo dal corpo del documento alla collezione interna del gruppo. Il rettangolo ora rispetta le trasformazioni del gruppo.

#### Passo 8: Aggiungere un'ellisse a scopo dimostrativo

```java
        // Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(80);
        ellipse.setHeight(80);
        groupShape.appendChild(ellipse);
```

L'ellisse condivide lo stesso spazio di coordinate del rettangolo, così puoi allinearle visivamente regolando le proprietà `setLeft` e `setTop` se necessario.

### Passo 9: Salvare il documento

```java
        // Save the result to a new file
        doc.save("output.docx");
    }
}
```

Eseguendo il programma viene generato `output.docx`. Apri il file in Microsoft Word o LibreOffice; vedrai un rettangolo e un'ellisse raggruppati insieme. Selezionando una delle forme, l'intero gruppo viene evidenziato, confermando che **aggiungere forma al gruppo** è riuscito.

![Add rectangle shape example in Java](image.png){alt="Esempio di aggiunta di forma rettangolare in Java"}

*Lo screenshot mostra il rettangolo e l'ellisse all'interno di un unico gruppo, pronti per la manipolazione congiunta.*

## Perché questo approccio è importante

* **Fonte unica di verità** – Tutte le proprietà della forma sono impostate prima della creazione del gruppo, evitando glitch di layout.
* **Riutilizzabilità** – Gli stessi metodi `setWidth`/`setHeight` funzionano per qualsiasi forma, così puoi estendere l'esempio a frecce, stelle o SVG personalizzati.
* **Prestazioni** – Il raggruppamento riduce il numero di oggetti di disegno che il renderer di Word deve gestire, migliorando la velocità di apertura per documenti di grandi dimensioni.
* **Manutenibilità** – Tenendo insieme la logica di creazione e raggruppamento delle forme, gli sviluppatori futuri possono modificare le dimensioni o aggiungere nuove forme senza dover cercare in codice non correlato.

## Varianti comuni e casi limite

| Scenario | Regolazione |
|----------|------------|
| **Unità diverse** | Usa la conversione `PointsToPixels` o imposta `Shape.setWrapType(WrapType.INLINE)` per posizionamento inline. |
| **Ruotare il gruppo** | Chiama `groupShape.setRotation(45);` per ruotare tutte le forme figlie di 45°. |
| **Aggiungere testo a una forma** | Usa `Shape.setText("Label");` dopo aver impostato la dimensione. |
| **Dimensionamento dinamico** | Recupera le dimensioni della pagina tramite `doc.getFirstSection().getPageSetup().getPageWidth()` e calcola le dimensioni delle forme proporzionalmente. |

Queste varianti illustrano come il modello di base — **aggiungere forma rettangolare**, **impostare dimensione della forma**, **raggruppare più forme**, **aggiungere forma al gruppo** — si adatti a molte esigenze reali.

## Conclusione

Ora sai come **aggiungere una forma rettangolare** a un documento Word usando Java, **impostare le dimensioni della forma**, **raggruppare più forme** e **aggiungere una forma al gruppo** in modo pulito e manutenibile. L'esempio completo si compila in una singola classe eseguibile, e il file DOCX risultante dimostra l'output previsto.

Da qui puoi esplorare:

* Aggiungere etichette di testo o collegamenti ipertestuali a ciascuna forma.
* Annidare gruppi per costruire diagrammi gerarchici.
* Esportare il documento in PDF mantenendo i gruppi di forme.

Sentiti libero di sperimentare con dimensioni, colori e tipi di forma aggiuntivi. Padroneggiare la manipolazione delle forme apre la porta alla generazione automatica di report, diagrammi dinamici e esperienze documentali ricche — tutto direttamente dal codice Java.

## Cosa dovresti imparare in seguito?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Insert Rectangle Shape in Java – Group and Position Shapes](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [How to create and insert ellipse and rectangle shapes inside a group shape in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Create rectangle shape in a Word document using Java](/words/english/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}