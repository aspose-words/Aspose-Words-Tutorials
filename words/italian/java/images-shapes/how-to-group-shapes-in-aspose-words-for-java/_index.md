---
category: general
date: 2026-10-20
description: Come raggruppare le forme in Aspose.Words per Java – impara come inserire
  una forma rettangolare, raggrupparle e salvare il documento in una guida unica.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- how to insert rectangle
language: it
lastmod: 2026-10-20
og_description: Come raggruppare le forme in Aspose.Words per Java. Questo tutorial
  mostra come inserire una forma rettangolare, raggrupparle e esportare il risultato.
og_image_alt: Screenshot of a Word document showing two grouped rectangle shapes created
  with Aspose.Words for Java
og_title: Come raggruppare le forme in Aspose.Words per Java – guida passo passo
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: How to group shapes in Aspose.Words for Java – learn how to insert
    rectangle shape, group them, and save the document in a single guide.
  headline: How to group shapes in Aspose.Words for Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- shape manipulation
title: Come raggruppare le forme in Aspose.Words per Java
url: /it/java/images-shapes/how-to-group-shapes-in-aspose-words-for-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come raggruppare le forme in Aspose.Words per Java

Se hai bisogno di **come raggruppare le forme** in un documento Word usando Aspose.Words per Java, questa guida ti mostra l’intero flusso di lavoro. Imparerai a **inserire forma rettangolare**, aggiungere un secondo rettangolo, raggruppare le due forme e, infine, salvare il file—tutto con codice chiaro e eseguibile.

Raggruppare le forme è utile quando vuoi spostare, ruotare o formattare più disegni come un’unica unità. Che tu stia creando un modello di report, un diagramma o un volantino personalizzato, padroneggiare il raggruppamento delle forme ti fa risparmiare tempo e mantiene coerente il layout.

In questo tutorial:

* Creerai un nuovo `Document` e un `DocumentBuilder`.
* **Come inserire forme rettangolari** con dimensioni precise.
* Raggrupperai i rettangoli in un `GroupShape`.
* Salverai il documento e verificherai il risultato.

> **Prerequisito** – Devi avere Aspose.Words per Java (v23.12 o successiva) aggiunto al tuo progetto. Gli utenti Maven possono includere la dipendenza mostrata di seguito.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

---

## Cosa ti servirà

| Elemento | Motivo |
|----------|--------|
| Java 17+ | Funzionalità moderne del linguaggio e migliori prestazioni |
| Aspose.Words per Java | Fornisce le API `DocumentBuilder`, `Shape` e `GroupShape` |
| Un IDE (IntelliJ IDEA, Eclipse, VS Code, ecc.) | Per compilare ed eseguire l’esempio |
| Permessi di scrittura su una cartella | Il documento verrà salvato su disco |

---

## Come inserire una forma rettangolare

Il primo passo è creare un `Document` e un `DocumentBuilder`. Il builder ti offre metodi come `insertShape` per posizionare oggetti di disegno.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle (100 × 50 points).
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Optional: give the rectangle a fill color for visibility.
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Step 3: Insert the second rectangle (80 × 40 points).
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // The two rectangles are currently independent objects.
        // Below we will group them together.
```

> **Perché è importante** – Usare `insertShape` è il modo standard **come inserire forme rettangolari** in Aspose.Words. Aggiunge automaticamente la forma al paragrafo corrente del documento, così non devi gestire manualmente OpenXML a basso livello.

---

## Regolare le posizioni dei rettangoli (opzionale)

Se il secondo rettangolo necessita di una posizione personalizzata rispetto al primo, puoi modificare le proprietà `left` e `top`. Questo passaggio è opzionale ma spesso necessario per un layout diagramma preciso.

```java
        // Optional: reposition the second rectangle 20 points to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        // Optional: align the top edges.
        rectangle2.setTop(rectangle1.getTop());
```

> **Consiglio professionale:** tutte le misure sono in punti (1 pt ≈ 1/72 in). Usa `convertPointsToPixels` se ti servono valori in pixel per calcoli basati su UI.

---

## Come raggruppare le forme

Ora che i rettangoli esistono, puoi inserirli all’interno di un `GroupShape`. Il raggruppamento fa sì che i due rettangoli si comportino come un unico oggetto—spostare, ruotare o formattare il gruppo influenzerà entrambe le forme.

```java
        // Step 4: Insert an empty GroupShape.
        GroupShape group = builder.insertGroupShape();

        // Step 5: Add the rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Optional: set a border for the whole group.
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);
```

> **Perché il raggruppamento funziona** – `GroupShape` eredita da `Shape`, quindi puoi trattare il gruppo esattamente come qualsiasi altro oggetto di disegno. Quando chiami `appendChild`, le forme vengono rimosse dalla loro posizione originale e diventano figli del gruppo.

---

## Salvataggio del documento contenente le forme raggruppate

Infine, scrivi il documento su disco. Il file conterrà un unico `GroupShape` con due rettangoli al suo interno.

```java
        // Step 6: Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Risultato atteso

Apri `GroupShape.docx` in Microsoft Word:

* Vedrai due rettangoli (blu e verde) posizionati fianco a fianco.
* Selezionando uno dei rettangoli, verrà selezionato l’intero gruppo—trascinandolo si spostano entrambi insieme.
* Il gruppo ha un sottile bordo rosso, a conferma dell’applicazione delle proprietà di `GroupShape`.

Se fai clic con il tasto destro sul gruppo e scegli **Group → Ungroup**, i rettangoli tornano a forme indipendenti, dimostrando che l’operazione di raggruppamento è reversibile.

---

## Variazioni comuni e casi particolari

| Situazione | Come gestirla |
|------------|---------------|
| **Più di due forme** | Inserisci ogni forma, poi aggiungile tutte allo stesso `GroupShape`. |
| **Tipi di forma diversi** (ad es., ellisse, immagine) | Usa `builder.insertShape(ShapeType.ELLIPSE, …)` o `builder.insertImage(...)` prima di aggiungere. |
| **Ridimensionare il gruppo** | Chiama `group.setWidth(newWidth)` o `group.setHeight(newHeight)`; i figli si ridimensionano proporzionalmente. |
| **Ruotare il gruppo** | `group.setRotationAngle(45);` ruota l’intera collezione attorno al suo centro. |
| **Preservare le posizioni originali** | Salva `left`/`top` di ogni forma prima del raggruppamento e ripristinali dopo lo sganciamento, se necessario. |

---

## Esempio completo, eseguibile

Di seguito trovi la classe Java completa che puoi copiare‑incollare nel tuo IDE. Include tutti gli import, la gestione degli errori e i commenti per chiarezza.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert the first rectangle (100 × 50 points) and give it a blue fill.
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Insert the second rectangle (80 × 40 points) with a green fill.
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // Optional positioning – move the second rectangle 20 pt to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        rectangle2.setTop(rectangle1.getTop());

        // Insert an empty group shape.
        GroupShape group = builder.insertGroupShape();

        // Add both rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Style the group (red border, 1.5 pt weight).
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);

        // Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

Esegui il programma, apri il `GroupShape.docx` risultante e vedrai i rettangoli raggruppati esattamente come descritto.

---

## Conclusione

Ora sai **come raggruppare le forme** in Aspose.Words per Java, dalla creazione del documento all’inserimento di forme rettangolari, alla regolazione delle loro posizioni e, infine, al raggruppamento con `GroupShape`. Questa tecnica ti permette di trattare più disegni come un’unica entità, semplificando le regolazioni di layout e la coerenza visiva.

**Passi successivi**

* Esplora **come inserire forme rettangolari** con diversi pattern di riempimento o bordi.
* Combina **inserire forma rettangolare** con caselle di testo per creare diagrammi etichettati.
* Sperimenta con la rotazione o il ridimensionamento del gruppo per produrre grafiche più complesse.

Sentiti libero di adattare il codice ad altri tipi di forma, gruppi più grandi o scenari di generazione dinamica di documenti. Buona programmazione!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche illustrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell’API e a esplorare approcci alternativi di implementazione nei tuoi progetti.

- [Insert Rectangle Shape in Java – Group and Position Shapes](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [how to insert group shape in Java – Complete Guide](/words/english/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/)
- [How to Set Shadow on a Shape in Aspose.Words – Complete Guide](/words/english/java/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}