---
"description": "Scopri come aggiungere filigrane ai documenti in Aspose.Words per Java. Personalizza filigrane di testo e immagini per documenti dall'aspetto professionale."
"linktitle": "Utilizzo di filigrane nei documenti"
"second_title": "API di elaborazione dei documenti Java Aspose.Words"
"title": "Utilizzo di filigrane nei documenti in Aspose.Words per Java"
"url": "/it/java/document-conversion-and-export/using-watermarks-to-documents/"
"weight": 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Utilizzo di filigrane nei documenti in Aspose.Words per Java


## Introduzione all'aggiunta di filigrane ai documenti in Aspose.Words per Java

In questo tutorial, esploreremo come aggiungere filigrane ai documenti utilizzando l'API Aspose.Words per Java. Le filigrane sono un modo utile per etichettare i documenti con testo o immagini per indicarne lo stato, la riservatezza o altre informazioni rilevanti. In questa guida tratteremo sia le filigrane testuali che quelle con immagini.

## Impostazione di Aspose.Words per Java

Prima di iniziare ad aggiungere filigrane ai documenti, dobbiamo configurare Aspose.Words per Java. Segui questi passaggi per iniziare:

1. Scarica Aspose.Words per Java da [Qui](https://releases.aspose.com/words/java/).
2. Aggiungi la libreria Aspose.Words per Java al tuo progetto Java.
3. Importa le classi necessarie nel tuo codice Java.

Ora che abbiamo impostato la libreria, procediamo ad aggiungere le filigrane.

## Aggiunta di filigrane di testo

Le filigrane di testo sono una scelta comune quando si desidera aggiungere informazioni testuali ai documenti. Ecco come aggiungere una filigrana di testo utilizzando Aspose.Words per Java:

```java
// Crea un'istanza di Documento
Document doc = new Document("Document.docx");

// Definisci TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Imposta il testo e le opzioni della filigrana
doc.getWatermark().setText("Test", options);

// Salva il documento con la filigrana
doc.save("DocumentWithWatermark.docx");
```

## Aggiunta di filigrane alle immagini

Oltre alle filigrane di testo, puoi anche aggiungere filigrane di immagini ai tuoi documenti. Ecco come aggiungere una filigrana di immagini:

```java
// Crea un'istanza di Documento
Document doc = new Document("Document.docx");

// Carica l'immagine per la filigrana
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Imposta la dimensione e la posizione della filigrana
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Aggiungere la filigrana al documento
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Salva il documento con la filigrana
doc.save("DocumentWithImageWatermark.docx");
```

## Personalizzazione delle filigrane

È possibile personalizzare le filigrane modificandone l'aspetto e la posizione. Per le filigrane di testo, è possibile modificare il carattere, le dimensioni, il colore e il layout. Per le filigrane di immagini, è possibile modificarne le dimensioni e la posizione, come illustrato negli esempi precedenti.

## Rimozione delle filigrane

Per rimuovere le filigrane da un documento, puoi utilizzare il seguente codice:

```java
// Crea un'istanza di Documento
Document doc = new Document("DocumentWithWatermark.docx");

// Rimuovi la filigrana
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Salva il documento senza la filigrana
doc.save("DocumentWithoutWatermark.docx");
```


## Conclusione

In questo tutorial abbiamo imparato come aggiungere filigrane ai documenti utilizzando Aspose.Words per Java. Che si tratti di aggiungere filigrane testuali o di immagini, Aspose.Words fornisce gli strumenti per personalizzarle e gestirle in modo efficiente. È anche possibile rimuovere le filigrane quando non sono più necessarie, garantendo documenti puliti e professionali.

## Domande frequenti

### Come posso cambiare il font di una filigrana di testo?

Per cambiare il carattere di una filigrana di testo, modificare il `setFontFamily` proprietà nella `TextWatermarkOptions`. Per esempio:

```java
options.setFontFamily("Times New Roman");
```

### Posso aggiungere più filigrane a un singolo documento?

Sì, puoi aggiungere più filigrane a un documento creandone più `Shape` oggetti con impostazioni diverse e aggiungerli al documento.

### È possibile ruotare una filigrana?

Sì, puoi ruotare una filigrana impostando `setRotation` proprietà nella `Shape` oggetto. I valori positivi ruotano la filigrana in senso orario, mentre i valori negativi la ruotano in senso antiorario.

### Come posso rendere una filigrana semitrasparente?

Per rendere una filigrana semitrasparente, impostare `setSemitransparent` proprietà a `true` nel `TextWatermarkOptions`.

### Posso aggiungere filigrane a sezioni specifiche di un documento?

Sì, è possibile aggiungere filigrane a sezioni specifiche di un documento scorrendo le sezioni e aggiungendo la filigrana alle sezioni desiderate.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}