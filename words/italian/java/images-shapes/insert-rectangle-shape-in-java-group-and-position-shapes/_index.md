---
category: general
date: 2026-07-26
description: Inserisci una forma rettangolare in Java usando Aspose.Words. Scopri
  come impostare le dimensioni della forma, posizionare la forma e come raggruppare
  le forme in un file DOCX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- set shape size
- position shape
- how to group shapes
- how to add rectangle
language: it
lastmod: 2026-07-26
og_description: Inserisci una forma rettangolare in Java per creare grafiche DOCX
  ricche. Segui questa guida passo‑passo per impostare le dimensioni della forma,
  posizionare la forma e raggruppare le forme senza sforzo.
og_image_alt: Screenshot showing a rectangle shape inserted and grouped in a Java‑generated
  Word document
og_title: Inserisci forma rettangolare in Java – Padroneggia raggruppamento e posizionamento
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert rectangle shape in Java using Aspose.Words. Learn how to set
    shape size, position shape, and how to group shapes in a DOCX file.
  headline: Insert Rectangle Shape in Java – Group and Position Shapes
  type: TechArticle
tags:
- Aspose.Words
- Java
- Shapes
- DOCX
title: Inserisci forma rettangolare in Java – Raggruppa e posiziona le forme
url: /it/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserire Forma Rettangolare in Java – Raggruppare e Posizionare le Forme

Hai mai dovuto **inserire una forma rettangolare** in un documento Word mentre scrivi codice Java? Non sei l’unico: gli sviluppatori che creano report, fatture o template personalizzati si trovano spesso di fronte a questo ostacolo. La buona notizia è che, con poche righe di Aspose.Words per Java, puoi **inserire una forma rettangolare**, **impostare le dimensioni della forma**, **posizionare la forma** e persino **come raggruppare le forme** in modo che si muovano come un’unica unità.

In questa guida percorreremo l’intero processo, dalla creazione di un documento vuoto al salvataggio di un `.docx` che contiene due rettangoli ordinatamente raggruppati. Alla fine saprai **come aggiungere rettangoli**, controllare le loro dimensioni, posizionarli esattamente dove desideri e raggrupparli in un gruppo riutilizzabile. Non sono necessarie librerie esterne oltre a Aspose.Words, e il codice funziona con Java 8‑plus.

## Prerequisiti

- Java 8 o versione successiva installata (io uso JDK 17, ma qualsiasi cosa supporti Maven va bene)
- Aspose.Words per Java 23.9 o successiva – aggiungi la dipendenza al tuo `pom.xml` o scarica il JAR
- Una conoscenza di base della sintassi Java (se sai scrivere un metodo `main`, sei a posto)
- Un IDE o editor di testo a tua scelta (IntelliJ IDEA, Eclipse, VS Code…)

> **Pro tip:** Se usi Maven, la dipendenza è così:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Ora che abbiamo impostato le basi, immergiamoci nel codice.

## Inserire Forma Rettangolare e Impostarne le Dimensioni

La prima cosa da fare è creare un nuovo `Document` e un `DocumentBuilder`. Il builder è la tua “penna” che disegna le forme sulla pagina. Di seguito **inseriamo una forma rettangolare** e subito **impostiamo le dimensioni della forma** a 100 × 80 punti.

```java
import com.aspose.words.*;

public class GroupedRectanglesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder to add content
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape(400, 200);
        // The group itself is 400×200 points – adjust as needed

        // ---------- First rectangle ----------
        // Insert rectangle shape
        Shape rectangle1 = new Shape(document, ShapeType.RECTANGLE);
        // Set shape size
        rectangle1.setWidth(100);
        rectangle1.setHeight(80);
        // Position shape inside the group
        rectangle1.setLeft(20);   // 20 points from the left edge of the group
        rectangle1.setTop(30);    // 30 points from the top edge of the group
        // Add the rectangle to the group
        group.appendChild(rectangle1);
```

Nota come le chiamate `setWidth`/`setHeight` **impostano le dimensioni della forma** in punti (1 pt ≈ 1/72 pollice). Puoi anche usare `setSize` se preferisci un unico metodo, ma le chiamate esplicite rendono l’intento cristallino.

## Posizionare la Forma nella Pagina

Dopo aver creato il primo rettangolo, dobbiamo **posizionare la forma** del secondo in modo che non si sovrapponga al primo. Il posizionamento funziona allo stesso modo: imposti le proprietà `Left` e `Top` relative all’origine del gruppo.

```java
        // ---------- Second rectangle ----------
        Shape rectangle2 = new Shape(document, ShapeType.RECTANGLE);
        rectangle2.setWidth(120);
        rectangle2.setHeight(60);
        // Position this rectangle a bit farther to the right and lower down
        rectangle2.setLeft(150);
        rectangle2.setTop(50);
        group.appendChild(rectangle2);
```

Se ti chiedi perché usiamo `setLeft` invece di `setX`, è perché Aspose.Words adotta il classico sistema di coordinate Windows GDI—`Left` è lo spostamento orizzontale, `Top` è lo spostamento verticale. Modificando questi valori puoi perfezionare il layout senza impazzire con tabelle o paragrafi.

## Come Raggruppare le Forme

Potresti chiederti: “Perché preoccuparsi di un gruppo?” Il raggruppamento ha senso quando vuoi che le forme si muovano insieme, ruotino come un’unica unità o condividano uno stile comune. Nello snippet sopra abbiamo già creato un `GroupShape` tramite `builder.insertGroupShape`. Quel oggetto è essenzialmente un contenitore—pensalo come una cartella che contiene altri file di forma.

> **Perché è importante:** Se in seguito decidi di aggiungere una didascalia o ruotare l’intero diagramma, devi modificare solo il gruppo, non ogni rettangolo singolarmente.

## Come Aggiungere un Rettangolo a un Gruppo

L’operazione di **come aggiungere un rettangolo** al gruppo consiste semplicemente nel chiamare `group.appendChild(rectangle)`. Dietro le quinte Aspose.Words aggiorna la collezione interna del gruppo e ricalcola automaticamente il bounding box, così il gruppo continua a rispettare la larghezza e altezza dichiarate.

```java
        // At this point the group already contains both rectangles.
        // You can also set the group’s border or fill if you like.
        group.getShapeStyle().setLineColor(Color.BLACK);
        group.getShapeStyle().setFillColor(Color.LIGHTGRAY);
```

Puoi sperimentare con altri `ShapeType`—`ShapeType.ELLIPSE`, `ShapeType.TRIANGLE`, ecc.—e lo stesso schema `appendChild` funziona.

## Salvare il Documento

Infine, persistiamo il documento su disco. Il percorso può essere assoluto o relativo; assicurati solo che la cartella esista.

```java
        // Step 5: Save the document containing the grouped shapes
        String outPath = "output/GroupShape.docx";
        document.save(outPath);
        System.out.println("Document saved to: " + outPath);
    }
}
```

Quando apri `GroupShape.docx` in Microsoft Word, vedrai due rettangoli affiancati, entrambi bloccati all’interno di una casella grigio‑chiaro. Selezionando la casella grigia verranno evidenziati entrambi i rettangoli contemporaneamente—la prova che **come raggruppare le forme** funziona davvero.

![Grouped rectangles in a Word document](placeholder-image.png){: .center-image alt="Esempio di inserimento di forma rettangolare che mostra due rettangoli raggruppati in un file DOCX generato da Java"}

*Testo alternativo dell’immagine (SEO):* **esempio di inserimento di forma rettangolare che mostra due rettangoli raggruppati in un file DOCX generato da Java**.

## Output Atteso

- Un file `GroupShape.docx` situato nella cartella `output`.
- All’interno del documento: un gruppo di 400 × 200 pt contenente due rettangoli (100 × 80 pt e 120 × 60 pt) posizionati rispettivamente a (20, 30) e (150, 50).
- Il gruppo ha un bordo nero sottile e un riempimento grigio‑chiaro, rendendo il raggruppamento visivamente evidente.

Apri il file e prova a trascinare la casella grigia—entrambi i rettangoli dovrebbero muoversi insieme. Se non lo fanno, ricontrolla di aver chiamato `group.appendChild` per ciascuna forma.

## Problemi Comuni & Casi Limite

| Problema | Perché accade | Soluzione |
|----------|---------------|-----------|
| **I rettangoli appaiono fuori dalla pagina** | I valori `Left`/`Top` superano le dimensioni del gruppo | Aumenta la dimensione del gruppo (`insertGroupShape(width, height)`) o riduci gli offset |
| **Il gruppo scompare dopo il salvataggio** | Le proprietà `Width`/`Height` del gruppo sono impostate a 0 | Fornisci dimensioni diverse da zero quando chiami `insertGroupShape` |
| **I colori della forma sono errati** | Il riempimento predefinito è trasparente; Word lo può visualizzare come bianco | Imposta esplicitamente `setFillColor` o usa `ShapeStyle` |
| **Eccezione `ArgumentOutOfRangeException`** | Uso di coordinate negative | Mantieni `Left` e `Top` non negativi |

Affrontare questi aspetti fin dall’inizio ti salva da mal di testa del tipo “perché la mia forma scompare?” che molti principianti incontrano.

## Riepilogo & Prossimi Passi

Abbiamo coperto l’intero ciclo di vita di **inserire forma rettangolare** in Java: creazione del documento, **impostare le dimensioni della forma**, **posizionare la forma**, **come raggruppare le forme**, e **come aggiungere un rettangolo** a quel gruppo. L’esempio completo, eseguibile, è nel blocco di codice sopra, e puoi incollarlo direttamente in un progetto Maven per vedere il risultato.

Cosa fare dopo? Prova a sperimentare con:

- Aggiungere testo all’interno di ciascun rettangolo tramite


## Cosa Dovresti Imparare Dopo?


I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell’API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}