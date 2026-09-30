---
date: 2026-02-19
description: Scopri come creare un documento con filigrana usando Aspose.Words per
  Java e aggiungere una filigrana di immagine in Java per documenti dall'aspetto professionale.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Crea documento con filigrana usando Aspose.Words per Java
url: /it/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

.{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Crea documento con filigrana usando Aspose.Words per Java

In questo tutorial **creerai un documento con filigrana** usando l'API Aspose.Words per Java. Le filigrane—sia di testo che di immagine—ti aiutano a etichettare un file come confidenziale, bozza o approvato, e possono essere applicate programmaticamente a qualsiasi documento Word. Ti guideremo nella configurazione della libreria, nell'aggiunta di filigrane di testo e immagine, nella personalizzazione del loro aspetto e anche nella rimozione quando non sono più necessarie.

## Risposte rapide
- **Che cosa fa una filigrana?** Sovrappone testo o un'immagine su ogni pagina per indicare lo stato o il branding.  
- **Quale libreria aggiunge filigrane in Java?** Aspose.Words per Java fornisce supporto integrato per le filigrane.  
- **Posso aggiungere una filigrana immagine?** Sì—usa la classe `Shape` e l'approccio `add image watermark java`.  
- **La filigrana è semitrasparente?** Puoi controllare l'opacità tramite `setSemitransparent` per le filigrane di testo.  
- **Ho bisogno di una licenza?** Una prova gratuita funziona per i test; è necessaria una licenza commerciale per la produzione.

## Cos'è una filigrana e perché usarla?

Una filigrana è una sovrapposizione leggera—testuale o grafica—aggiunta a ogni pagina di un documento. È comunemente usata per indicare **confidenzialità**, **stato bozza** o **branding** senza modificare il contenuto sottostante. Aggiungere filigrane programmaticamente garantisce coerenza su grandi lotti di file e fa risparmiare tempo rispetto alla modifica manuale.

## Configurare Aspose.Words per Java

Prima di iniziare ad aggiungere filigrane, assicurati che la libreria sia pronta nel tuo progetto:

1. Scarica Aspose.Words per Java da [here](https://releases.aspose.com/words/java/).  
2. Aggiungi il JAR scaricato (o la dipendenza Maven/Gradle) al classpath del tuo progetto.  
3. Importa le classi necessarie nel tuo file sorgente Java:

```java
import com.aspose.words.*;
import java.awt.Color;
import java.nio.file.*;
```

Ora che la libreria è configurata, immergiamoci nel codice effettivo della filigrana.

## Come aggiungere una filigrana di testo

Le filigrane di testo sono ideali per etichettare un documento come “CONFIDENTIAL” o “DRAFT”. Il frammento seguente mostra un modo pulito per **creare documento con filigrana** usando `TextWatermarkOptions`.

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

### Personalizzare la filigrana di testo
- **Famiglia e dimensione del font** – modifica `setFontFamily` e `setFontSize`.  
- **Colore** – usa qualsiasi `java.awt.Color`.  
- **Layout** – scegli `HORIZONTAL`, `DIAGONAL`, ecc.  
- **Trasparenza** – attiva `setSemitransparent(true)` per un aspetto più leggero.

## Come aggiungere una filigrana immagine (add image watermark java)

Le filigrane immagine sono perfette per loghi o grafiche personalizzate. Di seguito trovi l'esempio **add image watermark java** che inserisce un PNG al centro di ogni pagina.

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

### Suggerimenti per le filigrane immagine
- **Ridimensiona** usando `setWidth` / `setHeight` per adattare la pagina.  
- **Posizione** può essere centrata o allineata a qualsiasi margine usando `RelativeHorizontalPosition` / `RelativeVerticalPosition`.  
- **Trasparenza** può essere applicata regolando il canale alfa dell'immagine prima del caricamento.

## Come rimuovere le filigrane

Quando un documento non ha più bisogno di una filigrana, puoi eliminarla programmaticamente. Il codice qui sotto itera su tutte le forme e rimuove quelle che contengono “Watermark” nel loro nome.

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

## Problemi comuni e risoluzione

- **Filigrana mancante dopo il salvataggio** – assicurati di chiamare `doc.save()` dopo aver impostato la filigrana.  
- **Immagine non visualizzata** – verifica che il percorso dell'immagine sia corretto e che il file sia in un formato supportato (PNG, JPEG, BMP).  
- **Trasparenza non applicata** – `setSemitransparent(true)` funziona solo per le filigrane di testo; per le immagini, modifica il canale alfa del PNG.  
- **Sezioni multiple** – se il tuo documento ha diverse sezioni, aggiungi la filigrana al corpo di ciascuna sezione o usa `doc.getWatermark().setText(...)` che la applica globalmente.

## Domande Frequenti

**D: Come posso cambiare il font di una filigrana di testo?**  
R: Modifica la proprietà `setFontFamily` in `TextWatermarkOptions`, ad esempio `options.setFontFamily("Times New Roman");`.

**D: Posso aggiungere più filigrane a un singolo documento?**  
R: Sì. Crea più oggetti `Shape` (per le immagini) o chiama `doc.getWatermark().setText(...)` con opzioni diverse per ogni filigrana.

**D: È possibile ruotare una filigrana?**  
R: Per le filigrane immagine, imposta la rotazione sull'oggetto `Shape` con `watermark.setRotation(angle)`. Per le filigrane di testo, usa la proprietà `setLayout` (ad esempio `WatermarkLayout.DIAGONAL`).

**D: Come posso rendere una filigrana semitrasparente?**  
R: Imposta `options.setSemitransparent(true)` in `TextWatermarkOptions`. Per le immagini, regola l'opacità dell'immagine prima del caricamento.

**D: Posso aggiungere filigrane a sezioni specifiche di un documento?**  
R: Sì. Itera su `doc.getSections()` e aggiungi la filigrana solo alle sezioni desiderate.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Ultimo aggiornamento:** 2026-02-19  
**Testato con:** Aspose.Words for Java 24.12 (latest)  
**Autore:** Aspose