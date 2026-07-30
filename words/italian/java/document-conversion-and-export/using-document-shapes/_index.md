---
date: 2025-12-14
description: Impara come **inserire una forma immagine** con Aspose.Words per Java.
  Questa guida ti mostra come aggiungere forme, creare forme casella di testo, posizionare
  forme nelle tabelle, impostare il rapporto d'aspetto della forma e aggiungere forme
  di richiamo.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Uso delle forme del documento in Aspose.Words per Java
url: /it/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Come **inserire una forma immagine** con Aspose.Words per Java

In questo tutorial completo scoprirai come **inserire una forma immagine** nei documenti Word usando Aspose.Words per Java. Che tu stia creando report, materiale di marketing o moduli interattivi, le forme ti consentono di aggiungere callout, pulsanti, caselle di testo, filigrane e persino SmartArt. Ti guideremo passo passo, spiegheremo perché usare una determinata forma e forniremo snippet di codice pronti all'uso.

## Risposte rapide
- **Qual è il modo principale per aggiungere una forma?** Usa `DocumentBuilder.insertShape` o crea un'istanza `Shape` e aggiungila all'albero del documento.  
- **Posso inserire un'immagine come forma?** Sì – chiama `builder.insertImage` e poi tratta la `Shape` restituita come qualsiasi altra.  
- **Come mantengo il rapporto d'aspetto di una forma?** Imposta `shape.setAspectRatioLocked(true)` o `false` a seconda delle tue esigenze.  
- **È possibile raggruppare le forme?** Assolutamente – avvolgile in un `GroupShape` e inserisci il gruppo come un unico nodo.  
- **I diagrammi SmartArt funzionano con Aspose.Words?** Sì, puoi rilevare e aggiornare le forme SmartArt programmaticamente.

## Cos'è **inserire una forma immagine**?
Una *forma immagine* è un elemento visivo che contiene grafica raster o vettoriale all'interno di un documento Word. In Aspose.Words, un'immagine è rappresentata da un oggetto `Shape`, che ti offre il pieno controllo su dimensione, posizione, rotazione e avvolgimento.

## Perché usare le forme nei tuoi documenti?
- **Impatto visivo:** Le forme attirano l'attenzione sulle informazioni chiave.  
- **Interattività:** Pulsanti e callout possono essere collegati a URL o segnalibri.  
- **Flessibilità di layout:** Posiziona le grafiche con precisione usando coordinate assolute o relative.  
- **Automazione:** Genera layout complessi senza modifiche manuali.

## Prerequisiti
- Java Development Kit (JDK 8 o superiore)  
- Libreria Aspose.Words per Java (scaricabile dal sito ufficiale)  
- Conoscenza di base di Java e programmazione orientata agli oggetti  

Puoi scaricare la libreria qui: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

## Come **aggiungere una forma** – Inserire un GroupShape
Un `GroupShape` ti consente di trattare più forme come un'unica unità. È utile per spostare o formattare più elementi insieme.

```java
Document doc = new Document();
doc.ensureMinimum();

GroupShape groupShape = new GroupShape(doc);
Shape accentBorderShape = new Shape(doc, ShapeType.ACCENT_BORDER_CALLOUT_1);
accentBorderShape.setWidth(100.0);
accentBorderShape.setHeight(100.0);

groupShape.appendChild(accentBorderShape);

Shape actionButtonShape = new Shape(doc, ShapeType.ACTION_BUTTON_BEGINNING);
actionButtonShape.setLeft(100.0);
actionButtonShape.setWidth(100.0);
actionButtonShape.setHeight(200.0);

groupShape.appendChild(actionButtonShape);

groupShape.setWidth(200.0);
groupShape.setHeight(200.0);
groupShape.setCoordSize(new Dimension(200, 200));

DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertNode(groupShape);

doc.save("Your Directory Path" + "WorkingWithShapes.AddGroupShape.docx");
```

## Crea **forma casella di testo**
Una casella di testo è un contenitore che può contenere testo formattato. Puoi anche ruotarla per un aspetto dinamico.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertShape(ShapeType.TEXT_BOX, RelativeHorizontalPosition.PAGE, 100.0,
    RelativeVerticalPosition.PAGE, 100.0, 50.0, 50.0, WrapType.NONE);

shape.setRotation(30.0);
builder.writeln();

shape = builder.insertShape(ShapeType.TEXT_BOX, 50.0, 50.0);
shape.setRotation(30.0);

OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);

doc.save("Your Directory Path" + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## Imposta **rapporto d'aspetto della forma**
A volte è necessario che una forma si estenda liberamente, altre volte vuoi mantenere le sue proporzioni originali. Controllare il rapporto d'aspetto è semplice.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Posiziona **forma in una tabella**
Incorporare una forma all'interno di una cella di tabella può essere utile per i layout dei report. L'esempio seguente crea una tabella e poi inserisce una forma in stile filigrana che si estende su tutta la pagina.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

builder.startTable();
builder.getRowFormat().setHeight(100.0);
builder.getRowFormat().setHeightRule(HeightRule.EXACTLY);

for (int i = 0; i < 31; i++) {
    if (i != 0 && i % 7 == 0)
        builder.endRow();

    builder.insertCell();
    builder.write("Cell contents");
}

builder.endTable();

Shape watermark = new Shape(doc, ShapeType.TEXT_PLAIN_TEXT);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
watermark.isLayoutInCell(true); // Display the shape outside of the table cell if it will be placed into a cell.
watermark.setWidth(300.0);
watermark.setHeight(70.0);
watermark.setHorizontalAlignment(HorizontalAlignment.CENTER);
watermark.setVerticalAlignment(VerticalAlignment.CENTER);
watermark.setRotation(-40);
watermark.setFillColor(Color.GRAY);
watermark.setStrokeColor(Color.GRAY);
watermark.getTextPath().setText("watermarkText");
watermark.getTextPath().setFontFamily("Arial");
watermark.setName("WaterMark_{Guid.NewGuid()}");
watermark.setWrapType(WrapType.NONE);

Run run = (Run) doc.getChildNodes(NodeType.RUN, true).get(doc.getChildNodes(NodeType.RUN, true).getCount() - 1);
builder.moveTo(run);
builder.insertNode(watermark);

doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010);
doc.save("Your Directory Path" + "WorkingWithShapes.LayoutInCell.docx");
```

## Aggiungi **forma callout**
Una forma callout è perfetta per evidenziare note o avvertimenti. Sebbene il codice sopra mostri già un `ACCENT_BORDER_CALLOUT_1`, puoi sostituire il `ShapeType` con qualsiasi variante di callout per adattarla al tuo design.

## Lavorare con le forme SmartArt

### Rilevare le forme SmartArt
I diagrammi SmartArt possono essere identificati programmaticamente, consentendoti di elaborarli o sostituirli secondo necessità.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Aggiornare i disegni SmartArt
Una volta rilevati, puoi aggiornare la grafica SmartArt per riflettere eventuali modifiche ai dati.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Problemi comuni e suggerimenti
- **Forma non visualizzata:** Assicurati che la forma sia inserita dopo il nodo di destinazione usando `builder.insertNode`.  
- **Rotazione inattesa:** Ricorda che la rotazione è applicata attorno al centro della forma; regola `setLeft`/`setTop` se necessario.  
- **Rapporto d'aspetto bloccato:** Per impostazione predefinita, molte forme bloccano il loro rapporto d'aspetto; chiama `setAspectRatioLocked(false)` per allungare liberamente.  
- **Rilevamento SmartArt fallito:** Verifica di utilizzare una versione di Aspose.Words che supporti SmartArt (v24+).

## Domande frequenti

**Q:** What is Aspose.Words for Java?  
**A:** Aspose.Words for Java è una libreria Java che consente agli sviluppatori di creare, modificare e convertire documenti Word in modo programmatico. Offre un'ampia gamma di funzionalità e strumenti per lavorare con documenti in vari formati.

**Q:** How can I download Aspose.Words for Java?  
**A:** Puoi scaricare Aspose.Words per Java dal sito web di Aspose seguendo questo link: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

**Q:** What are the benefits of using document shapes?  
**A:** Le forme nei documenti aggiungono elementi visivi e interattività, rendendoli più coinvolgenti e informativi. Con le forme, puoi creare callout, pulsanti, immagini, filigrane e altro, migliorando l'esperienza dell'utente.

**Q:** Can I customize the appearance of shapes?  
**A:** Sì, puoi personalizzare l'aspetto delle forme regolando le loro proprietà come dimensione, posizione, rotazione e colore di riempimento. Aspose.Words per Java offre ampie opzioni per la personalizzazione delle forme.

**Q:** Is Aspose.Words for Java compatible with SmartArt?  
**A:** Sì, Aspose.Words per Java supporta le forme SmartArt, consentendoti di lavorare con diagrammi e grafiche complesse nei tuoi documenti.

---

**Last Updated:** 2025-12-14  
**Tested With:** Aspose.Words for Java 24.12 (latest)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}