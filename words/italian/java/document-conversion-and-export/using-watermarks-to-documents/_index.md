---
title: Utilizzo di filigrane nei documenti in Aspose.Words per Java
linktitle: Utilizzo di filigrane nei documenti
second_title: API di elaborazione dei documenti Java Aspose.Words
description: Scopri come aggiungere filigrane ai documenti in Aspose.Words per Java. Personalizza filigrane di testo e immagini per documenti dall'aspetto professionale.
weight: 15
url: /it/java/document-conversion-and-export/using-watermarks-to-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utilizzo di filigrane nei documenti in Aspose.Words per Java


## Introduzione all'aggiunta di filigrane ai documenti in Aspose.Words per Java

In questo tutorial, esploreremo come aggiungere filigrane ai documenti utilizzando l'API Aspose.Words per Java. Le filigrane sono un modo utile per etichettare i documenti con testo o grafica per indicarne lo stato, la riservatezza o altre informazioni rilevanti. In questa guida tratteremo sia le filigrane di testo che quelle di immagine.

## Impostazione di Aspose.Words per Java

Prima di iniziare ad aggiungere filigrane ai documenti, dobbiamo configurare Aspose.Words per Java. Segui questi passaggi per iniziare:

1.  Scarica Aspose.Words per Java da[Qui](https://releases.aspose.com/words/java/).
2. Aggiungi la libreria Aspose.Words per Java al tuo progetto Java.
3. Importa le classi necessarie nel tuo codice Java.

Ora che abbiamo impostato la libreria, possiamo procedere ad aggiungere le filigrane.

## Aggiunta di filigrane di testo

Le filigrane di testo sono una scelta comune quando vuoi aggiungere informazioni testuali ai tuoi documenti. Ecco come puoi aggiungere una filigrana di testo usando Aspose.Words per Java:

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

//Imposta il testo e le opzioni della filigrana
doc.getWatermark().setText("Test", options);

// Salvare il documento con la filigrana
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

// Salvare il documento con la filigrana
doc.save("DocumentWithImageWatermark.docx");
```

## Personalizzazione delle filigrane

Puoi personalizzare le filigrane regolandone l'aspetto e la posizione. Per le filigrane di testo, puoi cambiare il font, la dimensione, il colore e il layout. Per le filigrane di immagini, puoi modificarne la dimensione e la posizione come dimostrato negli esempi precedenti.

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

// Salvare il documento senza la filigrana
doc.save("DocumentWithoutWatermark.docx");
```


## Conclusione

In questo tutorial, abbiamo imparato come aggiungere filigrane ai documenti usando Aspose.Words per Java. Che tu abbia bisogno di aggiungere filigrane di testo o di immagini, Aspose.Words fornisce gli strumenti per personalizzarle e gestirle in modo efficiente. Puoi anche rimuovere le filigrane quando non sono più necessarie, assicurandoti che i tuoi documenti siano puliti e professionali.

## Domande frequenti

### Come posso cambiare il font di una filigrana di testo?

 Per cambiare il font di una filigrana di testo, modificare il`setFontFamily` proprietà nella`TextWatermarkOptions`. Per esempio:

```java
options.setFontFamily("Times New Roman");
```

### Posso aggiungere più filigrane a un singolo documento?

 Sì, puoi aggiungere più filigrane a un documento creandone più`Shape` oggetti con impostazioni diverse e aggiungerli al documento.

### È possibile ruotare una filigrana?

 Sì, puoi ruotare una filigrana impostando`setRotation` proprietà nella`Shape` oggetto. I valori positivi ruotano la filigrana in senso orario, mentre i valori negativi la ruotano in senso antiorario.

### Come posso rendere una filigrana semitrasparente?

 Per rendere una filigrana semitrasparente, impostare`setSemitransparent`proprietà a`true` nel`TextWatermarkOptions`.

### Posso aggiungere filigrane a sezioni specifiche di un documento?

Sì, è possibile aggiungere filigrane a sezioni specifiche di un documento scorrendo le sezioni e aggiungendo la filigrana alle sezioni desiderate.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
