---
category: general
date: 2026-08-01
description: Raggruppa forme in Word con Java usando Aspose.Words. Scopri come raggruppare
  le forme e inserire rapidamente una forma rettangolare con un esempio di codice
  completo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- insert rectangle shape
- Aspose.Words Java
- shape grouping tutorial
- Word document automation
language: it
lastmod: 2026-08-01
og_description: Raggruppa le forme in Word usando Java. Questa guida mostra come raggruppare
  le forme, inserire una forma rettangolare e salvare un DOCX con Aspose.Words.
og_image_alt: Screenshot of grouped shapes in a Word document created with Java
og_title: Raggruppa forme in Word con Java – Guida completa alla programmazione
schemas:
- author: Aspose
  dateModified: '2026-08-01'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to group
    shapes and insert rectangle shape quickly with a full code example.
  headline: Group Shapes in Word with Java – Complete Step-by-Step Guide
  type: TechArticle
- description: Group shapes in Word with Java using Aspose.Words. Learn how to group
    shapes and insert rectangle shape quickly with a full code example.
  name: Group Shapes in Word with Java – Complete Step-by-Step Guide
  steps:
  - name: 1. Can I group more than two shapes?
    text: 'Absolutely. Just pass a larger array to `insertGroupShape`:'
  - name: 2. What if I need to change the group’s position after creation?
    text: 'Use the group’s `setLeft` and `setTop` methods, just like any other shape:'
  - name: 3. How do I apply a border or fill to the whole group?
    text: The group itself can have formatting, but it doesn’t affect the children
      directly. If you want a common border, wrap the shapes in a rectangle shape
      first, then group everything. Alternatively, iterate over each child shape and
      set the same `fillColor` or `strokeWeight`.
  - name: 4. Does `setHidden(true)` affect printing?
    text: Hidden shapes are **not** printed by default in Word, which can be useful
      for watermarks or template markers. If you need the shape to print but stay
      invisible on screen, you’ll have to use a different approach (e.g., set its
      opacity to 0%).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Raggruppare forme in Word con Java – Guida completa passo passo
url: /it/java/images-shapes/group-shapes-in-word-with-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Raggruppare forme in Word con Java – Guida completa passo passo

Se hai bisogno di **raggruppare forme in Word** usando Java, questa guida è ciò che fa per te. Che tu stia costruendo un generatore di report o un motore di template dinamico, raggruppare le forme rende i documenti più curati e mantiene insieme le grafiche correlate.

Nei prossimi minuti vedrai esattamente **come raggruppare le forme** e **inserire oggetti forma rettangolo** con Aspose.Words, oltre a una serie di consigli pratici che ti salvano da errori comuni. Pronto a trasformare quei rettangoli e ellissi sparsi in un gruppo ordinato? Immergiamoci.

## Cosa copre questo tutorial

* I prerequisiti minimi (Java 17+, Aspose.Words 24.10 o successivo).  
* Un programma Java completo e eseguibile che crea un documento Word, inserisce un rettangolo e un'ellisse, li raggruppa, nasconde il gruppo se lo desideri e salva il file.  
* Perché ogni chiamata API è importante, non solo cosa fa.  
* Gestione dei casi limite per versioni più vecchie di Aspose.Words e per il raggruppamento di più di due forme.  
* Output previsto e un modo rapido per verificare il risultato.

Al termine potrai inserire questo snippet in qualsiasi progetto Java e iniziare a raggruppare forme in Word senza dover setacciare documentazione sparsa.

---

## Prerequisiti

| Requisito | Perché è importante |
|-----------|----------------------|
| **Java 17+** | Funzionalità moderne del linguaggio e migliori prestazioni. |
| **Aspose.Words for Java 24.10+** | Il metodo `setHidden` usato più avanti esiste solo a partire da questa versione. |
| **Un progetto Maven o Gradle** | Rende la gestione delle dipendenze indolore. |
| **Un IDE (IntelliJ, Eclipse, VS Code)** | Utile per test rapidi, ma qualsiasi editor di testo va bene. |

Aggiungi la dipendenza Maven di Aspose.Words al tuo `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

Se preferisci Gradle, l'equivalente è:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

---

## Passo 1: Creare un nuovo documento e un builder

Per prima cosa creiamo un `Document` vuoto e un `DocumentBuilder`. Il builder è il motore che ci permette di inserire forme, testo e molto altro.

```java
// Step 1: Create a new empty document and a builder to work with it.
Document doc = new Document();                     // The container for all Word content.
DocumentBuilder builder = new DocumentBuilder(doc); // Fluent API to add elements.
```

*Perché questo passo?*  
`Document` rappresenta l'intero file DOCX, mentre `DocumentBuilder` fornisce un'API comoda basata su cursore. Senza un builder dovresti manipolare manualmente le collezioni di nodi a basso livello—qualcosa di cui è facile sbagliare.

---

## Passo 2: Inserire una forma rettangolo (e un'ellisse)

Ora aggiungiamo le due forme di base che vogliamo raggruppare. Nota la chiamata **insert rectangle shape**—questa è esattamente la parola chiave secondaria che stavi cercando.

```java
// Step 2: Insert two simple shapes – a rectangle and an ellipse.
Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
Shape ellipseShape   = builder.insertShape(ShapeType.ELLIPSE, 100, 50);
```

Alcune cose da tenere a mente:

* La larghezza (`100`) e l'altezza (`50`) sono misurate in punti (1 pt ≈ 1/72 in). Regolale per adattarle al tuo layout.  
* Il rettangolo viene disegnato per primo, quindi di default si trova dietro l'ellisse. Se ti serve l'ordine opposto, inserisci prima l'ellisse.  
* Entrambe le forme ereditano la formattazione corrente del builder (colore, stile linea). Puoi personalizzarle prima del raggruppamento se lo desideri.

---

## Passo 3: Come raggruppare forme con Aspose.Words

Ecco il cuore del tutorial—**come raggruppare forme**. L'API `insertGroupShape` accetta un array di forme esistenti e restituisce una nuova `Shape` che rappresenta il gruppo.

```java
// Step 3: Group the two shapes together using the InsertGroupShape API.
Shape groupShape = builder.insertGroupShape(new Shape[] { rectangleShape, ellipseShape });
```

Perché usare un gruppo?  

* Un gruppo si sposta come un'unica unità, preservando il posizionamento relativo.  
* Puoi applicare trasformazioni (rotazione, scala) all'intero insieme con una sola chiamata.  
* Il raggruppamento semplifica le modifiche successive—sgruppa più tardi se devi regolare gli elementi singoli.

---

## Passo 4 (Opzionale): Nascondere il gruppo dalla visualizzazione del documento

Se non vuoi che il gruppo appaia quando l'utente apre il documento in Word, puoi nasconderlo. Questo passo è opzionale ma utile per grafiche di sfondo o filigrane.

```java
// Step 4: (Optional) Hide the group so it does not appear in the document view.
groupShape.setHidden(true);   // Requires Aspose.Words 24.10 or later
```

**E se stai usando una versione più vecchia di Aspose.Words?**  
Il metodo `setHidden` non compila. In tal caso puoi ottenere un effetto simile impostando la proprietà `WrapType` della forma a `NONE` e spostandola dietro lo strato di testo:

```java
groupShape.setWrapType(WrapType.NONE);
groupShape.getParagraph().getParagraphFormat().setStyleIdentifier(StyleIdentifier.BACKGROUND);
```

È un po' più verboso, ma mantiene comunque il gruppo fuori dalla vista del lettore.

---

## Passo 5: Salvare il documento

Infine, scrivi il documento su disco. Cambia il percorso dove desideri che il file venga salvato.

```java
// Step 5: Save the document with the grouped shapes.
doc.save("YOUR_DIRECTORY/GroupShapeResult.docx");
```

Quando apri `GroupShapeResult.docx` in Microsoft Word, vedrai un rettangolo e un'ellisse ordinatamente raggruppati. Se hai impostato `setHidden(true)`, il gruppo sarà invisibile nell'editor ma comunque presente nel file (utile per elaborazioni programmatiche successive).

---

## Esempio completo funzionante

Mettendo tutto insieme, ecco la classe Java completa e autonoma che puoi copiare‑incollare nel tuo progetto:

```java
import com.aspose.words.*;

public class GroupShapeTutorial {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert two simple shapes – a rectangle and an ellipse.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        Shape ellipseShape   = builder.insertShape(ShapeType.ELLIPSE, 100, 50);

        // Step 3: Group the two shapes together using the InsertGroupShape API.
        Shape groupShape = builder.insertGroupShape(new Shape[] { rectangleShape, ellipseShape });

        // Step 4: (Optional) Hide the group so it does not appear in the document view.
        groupShape.setHidden(true);   // Requires Aspose.Words 24.10 or later

        // Step 5: Save the document with the grouped shapes.
        doc.save("YOUR_DIRECTORY/GroupShapeResult.docx");
    }
}
```

**Output previsto:** Un file chiamato `GroupShapeResult.docx` contenente un unico gruppo che contiene un rettangolo riempito di blu e un'ellisse con contorno rosso (colori predefiniti). Se apri il documento, selezioni il gruppo e fai clic destro → **Group → Ungroup**, vedrai riapparire le due forme originali.

---

## Domande frequenti & casi limite

### 1. Posso raggruppare più di due forme?

Assolutamente. Basta passare un array più grande a `insertGroupShape`:

```java
Shape triangle = builder.insertShape(ShapeType.TRIANGLE, 80, 80);
Shape[] manyShapes = new Shape[] { rectangleShape, ellipseShape, triangle };
Shape bigGroup = builder.insertGroupShape(manyShapes);
```

L'API scala linearmente; l'unica limitazione è la memoria per gruppi estremamente grandi.

### 2. Come faccio a cambiare la posizione del gruppo dopo la creazione?

Usa i metodi `setLeft` e `setTop` del gruppo, proprio come per qualsiasi altra forma:

```java
groupShape.setLeft(150);
groupShape.setTop(200);
```

Poiché il gruppo si comporta come una singola forma, tutte le forme figlie si spostano insieme.

### 3. Come applico un bordo o un riempimento all'intero gruppo?

Il gruppo stesso può avere formattazione, ma non influisce direttamente sui figli. Se vuoi un bordo comune, avvolgi le forme in una forma rettangolo prima di raggrupparle, oppure itera su ogni forma figlia e imposta lo stesso `fillColor` o `strokeWeight`.

### 4. `setHidden(true)` influisce sulla stampa?

Le forme nascoste **non** vengono stampate di default in Word, il che può essere utile per filigrane o marcatori di template. Se hai bisogno che la forma venga stampata ma rimanga invisibile sullo schermo, dovrai usare un approccio diverso (ad esempio impostare l'opacità a 0%).

---

## Consigli professionali dal campo

* **Dai un nome alle tue forme** – `groupShape.setName("HeaderGraphics");` rende il debug più semplice quando recuperi le forme per nome.  
* **Riutilizza il builder** – Dopo aver inserito un gruppo, il cursore del builder resta dove è stato posizionato il gruppo, così puoi continuare ad aggiungere paragrafi subito dopo senza dover resettare la posizione.  
* **Proteggi la versione** – Se distribuisci una libreria che potrebbe girare su versioni più vecchie di Aspose.Words, avvolgi la chiamata `setHidden` in un try‑catch per `NoSuchMethodError` e ricorri al trucco `WrapType.NONE` mostrato prima.  
* **Suggerimento di performance** – Quando generi migliaia

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi con spiegazioni passo passo per aiutarti a padroneggiare ulteriori funzionalità dell'API e a esplorare approcci alternativi nei tuoi progetti.

- [Utilizzare le forme del documento in Aspose.Words per Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Creare documento Word Java – Aggiungere forma rettangolo con effetto ombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Rendering di forme in Aspose.Words per Java](/words/english/java/rendering-documents/rendering-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}