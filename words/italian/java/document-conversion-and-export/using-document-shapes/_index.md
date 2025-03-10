---
title: Utilizzo delle forme del documento in Aspose.Words per Java
linktitle: Utilizzo delle forme del documento
second_title: API di elaborazione dei documenti Java Aspose.Words
description: Sblocca la potenza delle forme dei documenti in Aspose.Words per Java. Impara a creare documenti visivamente accattivanti con esempi passo dopo passo.
weight: 14
url: /it/java/document-conversion-and-export/using-document-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utilizzo delle forme del documento in Aspose.Words per Java


## Introduzione all'utilizzo delle forme del documento in Aspose.Words per Java

In questa guida completa, ci addentreremo nel mondo delle forme dei documenti in Aspose.Words per Java. Le forme sono elementi essenziali quando si tratta di creare documenti visivamente accattivanti e interattivi. Che tu debba aggiungere callout, pulsanti, immagini o filigrane, Aspose.Words per Java fornisce gli strumenti per farlo in modo efficiente. Esploriamo come usare queste forme passo dopo passo con esempi di codice sorgente.

## Introduzione alle forme dei documenti

 Prima di buttarci nel codice, impostiamo il nostro ambiente. Assicurati di avere Aspose.Words for Java integrato nel tuo progetto. Se non lo hai già fatto, puoi scaricarlo dal sito web di Aspose[Scarica Aspose.Words per Java](https://releases.aspose.com/words/java/)

## Aggiungere forme ai documenti

### Inserimento di un GroupShape

 UN`GroupShape` consente di raggruppare più forme insieme. Ecco come puoi creare e inserire un`GroupShape`:

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

### Inserimento di una forma di casella di testo

 Per inserire una forma di casella di testo, puoi utilizzare`insertShape` metodo come mostrato nell'esempio seguente:

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

## Manipolazione delle proprietà delle forme

### Gestione del rapporto di aspetto

Puoi controllare se il rapporto di aspetto di una forma è bloccato o meno. Ecco come sbloccare il rapporto di aspetto di una forma:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

### Posizionamento di una forma in una cella della tabella

Se hai bisogno di posizionare una forma all'interno di una cella di una tabella, puoi farlo con il seguente codice:

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
watermark.isLayoutInCell(true); // Visualizza la forma all'esterno della cella della tabella se verrà inserita in una cella.
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

## Lavorare con le forme SmartArt

### Rilevamento delle forme SmartArt

È possibile rilevare le forme SmartArt in un documento utilizzando il seguente codice:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Aggiornamento dei disegni SmartArt

Per aggiornare i disegni SmartArt all'interno di un documento, utilizzare il seguente codice:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Conclusione

In questa guida, abbiamo esplorato il mondo delle forme dei documenti in Aspose.Words per Java. Hai imparato come aggiungere varie forme ai tuoi documenti, manipolarne le proprietà e lavorare con le forme SmartArt. Con questa conoscenza, puoi creare documenti visivamente accattivanti e interattivi con facilità.

## Domande frequenti

### Che cos'è Aspose.Words per Java?

Aspose.Words for Java è una libreria Java che consente agli sviluppatori di creare, modificare e convertire documenti Word in modo programmatico. Fornisce un'ampia gamma di funzionalità e strumenti per lavorare con documenti in vari formati.

### Come posso scaricare Aspose.Words per Java?

 È possibile scaricare Aspose.Words per Java dal sito web di Aspose seguendo questo link:[Scarica Aspose.Words per Java](https://releases.aspose.com/words/java/)

### Quali sono i vantaggi dell'utilizzo delle forme dei documenti?

Le forme dei documenti aggiungono elementi visivi e interattività ai tuoi documenti, rendendoli più coinvolgenti e informativi. Con le forme, puoi creare callout, pulsanti, immagini, filigrane e altro, migliorando l'esperienza utente complessiva.

### Posso personalizzare l'aspetto delle forme?

Sì, puoi personalizzare l'aspetto delle forme regolandone le proprietà, come dimensione, posizione, rotazione e colore di riempimento. Aspose.Words per Java fornisce ampie opzioni per la personalizzazione delle forme.

### Aspose.Words per Java è compatibile con SmartArt?

Sì, Aspose.Words per Java supporta le forme SmartArt, consentendo di lavorare con diagrammi e grafici complessi nei documenti.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
