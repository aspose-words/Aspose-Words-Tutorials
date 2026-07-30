---
date: 2025-12-18
description: Scopri come aggiungere una filigrana ai documenti con Aspose.Words per
  Java, includendo un esempio di filigrana immagine, cambiare il colore della filigrana,
  impostare la trasparenza della filigrana e rimuovere la filigrana dal documento.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Come aggiungere una filigrana ai documenti usando Aspose.Words per Java
url: /it/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Come aggiungere una filigrana ai documenti usando Aspose.Words per Java

## Introduzione all'aggiunta di filigrane ai documenti in Aspose.Words per Java

In questo tutorial imparerai **come aggiungere una filigrana** ai documenti Word con Aspose.Words per Java. Le filigrane sono un modo rapido per etichettare un file come confidenziale, bozza o approvato, e possono essere basate su testo o su immagine. Vedremo come configurare la libreria, creare filigrane di testo e di immagine, personalizzare il loro aspetto (inclusa la modifica del colore della filigrana e l'impostazione della trasparenza), e persino rimuovere una filigrana da un documento quando non è più necessaria.

## Risposte rapide
- **Che cos'è una filigrana?** Un overlay semitrasparente (testo o immagine) che appare dietro il contenuto principale del documento.  
- **Posso aggiungere più filigrane?** Sì – crea diversi oggetti `Shape` e aggiungili alle sezioni desiderate.  
- **Come cambio il colore della filigrana?** Regola la proprietà `Color` in `TextWatermarkOptions`.  
- **Esiste un esempio di filigrana immagine?** Vedi la sezione “Aggiunta di filigrane immagine” qui sotto.  
- **È necessaria una licenza per rimuovere una filigrana?** È richiesta una licenza valida di Aspose.Words per l'uso in produzione.

## Configurazione di Aspose.Words per Java

Prima di iniziare ad aggiungere filigrane ai documenti, dobbiamo configurare Aspose.Words per Java. Segui questi passaggi per iniziare:

1. Scarica Aspose.Words per Java da [here](https://releases.aspose.com/words/java/).  
2. Aggiungi la libreria Aspose.Words per Java al tuo progetto Java.  
3. Importa le classi necessarie nel tuo codice Java.

Ora che la libreria è configurata, immergiamoci nella creazione effettiva della filigrana.

## Aggiunta di filigrane di testo

Le filigrane di testo sono una scelta comune quando vuoi aggiungere informazioni testuali ai tuoi documenti. Ecco come puoi aggiungere una filigrana di testo usando Aspose.Words per Java:

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Define TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Set the watermark text and options
doc.getWatermark().setText("Test", options);

// Save the document with the watermark
doc.save("DocumentWithWatermark.docx");
```

**Perché è importante:** Modificando `setFontFamily`, `setFontSize` e `setColor` puoi **cambiare il colore della filigrana** per adattarlo al tuo brand, e `setSemitransparent(true)` ti consente di **impostare la trasparenza della filigrana** per un effetto discreto.

## Aggiunta di filigrane immagine

Oltre alle filigrane di testo, puoi anche aggiungere filigrane immagine ai tuoi documenti. Di seguito trovi un **esempio di filigrana immagine** che dimostra come incorporare un logo PNG o un timbro:

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Load the image for the watermark
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Set the watermark size and position
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Add the watermark to the document
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Save the document with the watermark
doc.save("DocumentWithImageWatermark.docx");
```

Puoi ripetere questo blocco con immagini o posizioni diverse per **aggiungere più filigrane** a un unico file.

## Personalizzazione delle filigrane

Puoi personalizzare le filigrane regolando il loro aspetto e la loro posizione. Per le filigrane di testo, puoi modificare il carattere, la dimensione, il colore e il layout. Per le filigrane immagine, puoi modificare dimensione, rotazione e allineamento come mostrato negli esempi precedenti.

## Rimozione delle filigrane

Se devi **rimuovere il contenuto della filigrana** dal documento, il codice seguente scorre tutte le forme e elimina quelle identificate come filigrane:

```java
// Create a Document instance
Document doc = new Document("DocumentWithWatermark.docx");

// Remove the watermark
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Save the document without the watermark
doc.save("DocumentWithoutWatermark.docx");
```

## Casi d'uso comuni e consigli

- **Bozze confidenziali:** Applica una filigrana di testo semitrasparente come “CONFIDENTIAL”.  
- **Branding:** Usa una filigrana immagine che contenga il logo della tua azienda.  
- **Filigrane specifiche per sezione:** Scorri `doc.getSections()` e aggiungi una filigrana solo alle sezioni che scegli.  
- **Consiglio di prestazioni:** Riutilizza la stessa istanza di `TextWatermarkOptions` quando applichi la stessa filigrana a molti documenti.

## Domande frequenti

### Come posso cambiare il carattere di una filigrana di testo?

Per cambiare il carattere di una filigrana di testo, modifica la proprietà `setFontFamily` in `TextWatermarkOptions`. Ad esempio:

```java
options.setFontFamily("Times New Roman");
```

### Posso aggiungere più filigrane a un singolo documento?

Sì, puoi aggiungere più filigrane a un documento creando più oggetti `Shape` con impostazioni diverse e aggiungendoli al documento.

### È possibile ruotare una filigrana?

Sì, puoi ruotare una filigrana impostando la proprietà `setRotation` nell'oggetto `Shape`. I valori positivi ruotano la filigrana in senso orario, mentre i valori negativi la ruotano in senso antiorario.

### Come posso rendere una filigrana semitrasparente?

Per rendere una filigrana semitrasparente, imposta la proprietà `setSemitransparent` su `true` in `TextWatermarkOptions`.

### Posso aggiungere filigrane a sezioni specifiche di un documento?

Sì, puoi aggiungere filigrane a sezioni specifiche di un documento iterando sulle sezioni e aggiungendo la filigrana alle sezioni desiderate.

---

**Ultimo aggiornamento:** 2025-12-18  
**Testato con:** Aspose.Words per Java 24.12  
**Autore:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}