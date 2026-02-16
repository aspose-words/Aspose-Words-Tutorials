---
date: 2026-02-16
description: Scopri come creare una casella di testo, aggiungere una filigrana di
  parole, raggruppare più forme, impostare il rapporto d'aspetto della forma e posizionare
  la forma in una cella di tabella usando Aspose.Words per Java.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Come creare una casella di testo e utilizzare le forme del documento in Aspose.Words
  per Java
url: /it/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Utilizzare le forme di documento in Aspose.Words per Java

## Introduzione all'utilizzo delle forme di documento in Aspose.Words per Java

In questa guida completa, **imparerai a creare oggetti text box** e altre forme potenti con Aspose.Words per Java. Le forme ti consentono di arricchire i documenti Word con callout, pulsanti, filigrane, SmartArt e altro ancora, rendendoli visivamente accattivanti e interattivi. Esamineremo esempi pratici, dall'inserimento di una semplice text box al raggruppamento di più forme, impostazione dei rapporti d'aspetto e posizionamento delle forme all'interno delle celle di una tabella.

## Risposte rapide
- **Qual è il modo principale per aggiungere una text box?** Usa `DocumentBuilder.insertShape(ShapeType.TEXT_BOX, …)`.
- **Posso raggruppare più forme insieme?** Sì – crea un `GroupShape` e aggiungi le forme figlie.
- **Come blocco o sblocco il rapporto d'aspetto di una forma?** Chiama `shape.setAspectRatioLocked(true/false)`.
- **È possibile aggiungere una filigrana con una forma?** Assolutamente – inserisci una `Shape` con `TEXT_PLAIN_TEXT` e imposta il riempimento/tratto.
- **I diagrammi SmartArt funzionano con Aspose.Words?** Sì – rileva con `shape.hasSmartArt()` e aggiorna tramite `shape.updateSmartArtDrawing()`.

## Cos'è una text box e perché creare forme text box?

Una text box è un contenitore che può contenere testo formattato, immagini o altre forme. Utilizzare **create text box** nella tua automazione ti permette di posizionare contenuti fluttuanti ovunque nella pagina, perfetti per annotazioni, callout o elementi decorativi senza alterare il flusso principale del documento.

## Come aggiungere una forma

Prima di immergerti nel codice, assicurati che Aspose.Words per Java sia referenziato nel tuo progetto. Se non l'hai ancora aggiunto, scarica la libreria dal sito ufficiale:

[Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### Aggiungere forme ai documenti

## Come raggruppare più forme

Un `GroupShape` ti consente di trattare diverse forme individuali come un'unica unità—utile per spostarle o ruotarle insieme.

### Inserimento di un GroupShape

Di seguito trovi un esempio completo che crea un gruppo, aggiunge due forme diverse e inserisce il gruppo nel documento.

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

## Come creare una text box (create text box)

### Inserimento di una forma Text Box

Il metodo `insertShape` rende semplice aggiungere una text box. L'esempio seguente mostra due modi per posizionare e ruotare una text box.

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

## Come impostare il rapporto d'aspetto di una forma

### Gestione del rapporto d'aspetto

A volte è necessario far allungare una forma senza preservare le proporzioni originali. Il frammento seguente dimostra come sbloccare il rapporto d'aspetto di una forma immagine.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Come posizionare una forma in una cella di tabella

### Posizionamento di una forma all'interno di una cella di tabella

Di seguito trovi un esempio passo‑passo che costruisce una tabella, quindi inserisce una forma filigrana posizionata rispetto alla pagina ma che può anche essere inserita in una cella.

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

## Lavorare con le forme SmartArt

### Rilevare forme SmartArt

Puoi trovare programmaticamente gli oggetti SmartArt in un documento usando il metodo `hasSmartArt()`.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Aggiornare i disegni SmartArt

Una volta individuate le forme SmartArt, puoi aggiornare i loro dati di disegno interni con `updateSmartArtDrawing()`.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Conclusione

In questa guida abbiamo trattato come **create text box** oggetti, raggruppare più forme, regolare i rapporti d'aspetto, incorporare forme all'interno di celle di tabella, aggiungere filigrane e lavorare con diagrammi SmartArt usando Aspose.Words per Java. Queste tecniche ti consentono di creare documenti Word riccamente formattati e interattivi in modo programmatico.

## FAQ

### Cos'è Aspose.Words per Java?

Aspose.Words per Java è una libreria Java che consente agli sviluppatori di creare, modificare e convertire documenti Word in modo programmatico. Offre un'ampia gamma di funzionalità e strumenti per lavorare con documenti in vari formati.

### Come posso scaricare Aspose.Words per Java?

Puoi scaricare Aspose.Words per Java dal sito Aspose seguendo questo link: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### Quali sono i vantaggi dell'utilizzo delle forme di documento?

Le forme di documento aggiungono elementi visivi e interattività ai tuoi documenti, rendendoli più coinvolgenti e informativi. Con le forme, puoi creare callout, pulsanti, immagini, filigrane e molto altro, migliorando l'esperienza complessiva dell'utente.

### Posso personalizzare l'aspetto delle forme?

Sì, puoi personalizzare l'aspetto delle forme regolando le loro proprietà come dimensione, posizione, rotazione e colore di riempimento. Aspose.Words per Java fornisce ampie opzioni per la personalizzazione delle forme.

### Aspose.Words per Java è compatibile con SmartArt?

Sì, Aspose.Words per Java supporta le forme SmartArt, consentendoti di lavorare con diagrammi e grafici complessi nei tuoi documenti.

## Domande frequenti

**Q: Posso combinare una text box con un'immagine all'interno della stessa forma?**  
A: Sì. Inserisci un'immagine nella forma text box usando `builder.insertImage()` dopo aver creato la forma, quindi regola il layout secondo necessità.

**Q: Come faccio a garantire che una filigrana appaia dietro tutto il contenuto del documento?**  
A: Imposta il `WrapType` della forma su `NONE` e regola `RelativeHorizontalPosition` e `RelativeVerticalPosition` su `PAGE`. Questo posiziona la filigrana dietro il flusso principale.

**Q: È possibile animare una forma raggruppata in Word?**  
A: Sebbene Aspose.Words possa creare e raggruppare forme, le funzionalità di animazione non sono supportate perché dipendono dalle capacità dell'interfaccia di Word.

**Q: Quale versione di Aspose.Words è necessaria per il supporto di SmartArt?**  
A: Il rilevamento e l'aggiornamento di SmartArt sono disponibili a partire da Aspose.Words 20.9 per Java e versioni successive.

**Q: La libreria gestisce efficacemente documenti di grandi dimensioni con molte forme?**  
A: Sì. Usa `doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010)` o versioni successive per migliorare le prestazioni su documenti con molte forme.

---

**Last Updated:** 2026-02-16  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}